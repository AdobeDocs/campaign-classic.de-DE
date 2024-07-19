---
product: campaign
title: Enterprise-Bereitstellung
description: Enterprise-Bereitstellung
feature: Installation, Architecture, Deployment
audience: installation
content-type: reference
topic-tags: deployment-types-
exl-id: 38c14010-203a-47ab-b23d-6f431dab9a88
source-git-commit: 1be1528d657537786c430ea9c8bdb3aad58ba20d
workflow-type: tm+mt
source-wordcount: '1218'
ht-degree: 7%

---

# Enterprise-Bereitstellung{#enterprise-deployment}



Dies ist die vollständigste Konfiguration. Sie baut auf der Standardkonfiguration auf, um mehr Sicherheit und Verfügbarkeit zu gewährleisten:

* dedizierte Umleitungsserver hinter einem HTTP- oder TCP-Lastenausgleich zur Skalierbarkeit und Verfügbarkeit,
* zwei Anwendungsserver für verbesserte Durchsatz- und Failover-Funktionalität (Fehlertoleranz), die im LAN isoliert sind.

Die allgemeine Kommunikation zwischen Servern und Prozessen erfolgt gemäß dem folgenden Schema:

![](assets/s_901_ncs_install_enterpriseconfig.png)

Bei dieser Art der Konfiguration kann der erwartete Durchsatz 100.000 E-Mails pro Stunde bei angemessener Bandbreite und Abstimmung überschreiten.

## Funktionen {#features}

### Vorteile {#advantages}

* Optimierte Sicherheit: Nur die Server, die von außen verfügbar gemacht werden müssen, werden auf dem Computer in der DMZ installiert.
* Hohe Verfügbarkeit einfacher zu gewährleisten: Nur der von außen sichtbare Computer muss mit hoher Verfügbarkeit verwaltet werden.

### Nachteile {#disadvantages}

Höhere Hardware- und Verwaltungskosten.

### Empfohlene Ausrüstung {#recommended-equipment}

* Anwendungsserver: 2-GHz-Quad-Core-CPU, 4 GB RAM, Software RAID 1-80-GB-SATA-Festplatte.
* Umleitungsserver: 2-GHz-Quad-Core-CPU, 4 GB RAM, Software RAID 1-80-GB-SATA-Festplatte.

>[!NOTE]
>
>Es ist möglich, einen vorhandenen Lastenausgleich für Traffic zu den Umleitungsservern wiederzuverwenden.

## Installation und Konfiguration {#installation-and-configuration-steps}

### Voraussetzungen {#prerequisites}

* JDK auf beiden Anwendungsservern,
* Webserver (IIS, Apache) an beiden Fronten,
* Zugriff auf einen Datenbankserver auf beiden Anwendungsservern,
* über POP3 zugängliches Bounce-Postfach,
* Erstellung von zwei DNS-Aliassen auf dem Lastenausgleich:

   * die erste, die der Öffentlichkeit zur Verfolgung und zum Verweis auf den Lastenausgleich an einer virtuellen IP-Adresse (VIP) zur Verfügung gestellt wird und die dann an die beiden Frontalserver verteilt wird,
   * die zweite, die den internen Benutzern für den Zugriff über die Konsole angezeigt wird und auf einen Lastenausgleich auf einer virtuellen IP-Adresse (VIP) verweist, der dann an die beiden Anwendungsserver verteilt wird.

* Firewall konfiguriert zum Öffnen von STMP (25), DNS (53), HTTP (80), HTTPS (443), SQL (1521 für Oracle, 5432 für PostgreSQL usw.) Ports. Weitere Informationen finden Sie im Abschnitt [Datenbankzugriff](../../installation/using/network-configuration.md#database-access).

>[!CAUTION]
>
>Wenn Ihre Anwendungsserver auf eine einzige Datenbankinstanz verweisen, wird nach dem Import eines Standardpakets auf einer Instanz das im Paket enthaltene Schema nicht auf der anderen Instanz geladen.
>  
>Wenn Ihre Anwendungsserver auf eine einzige Datenbankinstanz verweisen, wird das Schema nach dem Ändern des Schemas auf einer Instanz nicht auf die andere Instanz geladen.
>
>Um diese Probleme wiederherzustellen, müssen Sie den Prozess &quot;web@default&quot;auf der zweiten Instanz neu starten, bei der ein Fehler aufgetreten ist.

### Installieren und Konfigurieren des Anwendungsservers 1 {#installing-and-configuring-the-application-server-1}

In den folgenden Beispielen sind die Parameter der Instanz:

* Name der Instanz: demo
* DNS-Maske: tracking.campaign.net&#42;, console.campaign.net&#42; (der Anwendungsserver verarbeitet die URLs für Clientkonsolen-Verbindungen und -Berichte sowie für Mirrorseiten und Abmeldeseiten)
* Sprache: Englisch
* Datenbank: campaign:demo@dbsrv

Die Schritte zur Installation des ersten Servers sind:

1. Folgen Sie dem Installationsverfahren für den Adobe Campaign-Server: Paket **nlserver** unter Linux oder Paket **setup.exe** unter Windows.

   Weitere Informationen hierzu finden Sie unter [Voraussetzungen für die Campaign-Installation unter Linux](../../installation/using/prerequisites-of-campaign-installation-in-linux.md) (Linux) und [Voraussetzungen für die Campaign-Installation unter Windows](../../installation/using/prerequisites-of-campaign-installation-in-windows.md) (Windows).

1. Nachdem der Adobe Campaign-Server installiert ist, starten Sie den Anwendungsserver (Web) mit dem Befehl **nlserver web -tomcat** (das Webmodul ermöglicht Ihnen, Tomcat im eigenständigen Webservermodus zu starten, der Port 8080 überwacht) und stellen Sie sicher, dass Tomcat ordnungsgemäß gestartet wird:

   ```sql
   12:08:18 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   12:08:18 >   Starting Web server module (pid=28505, tid=-1225184768)...
   12:08:18 >   Tomcat started
   12:08:18 >   Server started
   ```


   >[!NOTE]
   >
   >Wenn das Webmodul zum ersten Mal ausgeführt wird, werden die Dateien &quot;**config-default.xml**&quot;und &quot;**serverConf.xml**&quot;im Ordner &quot;**conf**&quot;im Installationsordner erstellt. Alle in **serverConf.xml** verfügbaren Parameter sind in diesem [Abschnitt](../../installation/using/the-server-configuration-file.md) aufgeführt.

   Drücken Sie **Strg+C** , um den Server zu stoppen.

   Weiterführende Informationen hierzu finden Sie in den folgenden Abschnitten:

   * Für Linux: [Erststart des Servers](../../installation/using/installing-packages-with-linux.md#first-start-up-of-the-server)
   * Windows: [Erster Start des Servers](../../installation/using/installing-the-server.md#first-start-up-of-the-server)

1. Ändern Sie das Kennwort für **internal** mithilfe des Befehls:

   ```
   nlserver config -internalpassword
   ```

   Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../installation/using/configuring-campaign-server.md#internal-identifier).

1. Erstellen Sie die Instanz **demo** mit den DNS-Masken für das Tracking (in diesem Fall **tracking.campaign.net**) und greifen Sie auf die Client-Konsolen zu (in diesem Fall **console.campaign.net**). Dazu gibt es zwei Möglichkeiten:

   * Erstellen Sie die Instanz über die Konsole:

     ![](assets/install_create_new_connexion.png)

     Weitere Informationen hierzu finden Sie unter [Erstellen einer Instanz und Anmelden bei](../../installation/using/creating-an-instance-and-logging-on.md).

     oder

   * Erstellen Sie die Instanz mithilfe der Befehlszeilen:

     ```
     nlserver config -addinstance:demo/tracking.campaign.net*,console.campaign.net*
     ```

     Weitere Informationen hierzu finden Sie unter [Instanz erstellen](../../installation/using/command-lines.md#creating-an-instance).

1. Bearbeiten Sie die Datei &quot;**config-demo.xml**&quot;(erstellt über den vorherigen Befehl und befindet sich neben der Datei &quot;**config-default.xml**&quot;), überprüfen Sie, ob die Dateien &quot;**mta**&quot;(delivery), &quot;**wfserver**&quot;(workflow), &quot;**inMail**&quot;(rebound mails) und &quot;**stat1}&quot;(statistics) Prozesse aktiviert sind, konfigurieren Sie dann die Adresse des Statistikservers** app **:**

   ```xml
   <?xml version='1.0'?>
   <serverconf>  
     <shared>    
       <!-- add lang="eng" to dataStore to force English for the instance -->    
       <dataStore hosts="tracking.campaign.net*,console.campaign.net*">      
         <mapping logical="*" physical="default"/>    
       </dataStore>  </shared>  
       <mta autoStart="true" statServerAddress="app">
       <wfserver autoStart="true"/>  
       <inMail autoStart="true"/>  
       <sms autoStart="false"/>  
       <listProtect autoStart="false"/>
   </serverconf>
   ```

   Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../installation/using/configuring-campaign-server.md#enabling-processes).

1. Bearbeiten Sie die Datei &quot;**serverConf.xml**&quot;, geben Sie die Bereitstellungsdomäne an und geben Sie dann die IP- (oder Host-)Adressen der DNS-Server an, die vom MTA-Modul zur Beantwortung von DNS-Abfragen vom MX-Typ verwendet werden.

   ```xml
   <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
   ```

   >[!NOTE]
   >
   >Die Parameter **nameServers** werden nur unter Windows verwendet.

   Weitere Informationen hierzu finden Sie unter [Konfiguration des Campaign-Servers](../../installation/using/configuring-campaign-server.md).

1. Kopieren Sie das Client Console-Setup-Programm **setup-client-7.XX**, **YYY.exe** in den Ordner **/datakit/nl/eng/jsp** . [Weitere Informationen](../../installation/using/client-console-availability-for-windows.md).

1. Starten Sie den Adobe Campaign-Server (**net start nlserver6** in Windows, **/etc/init.d/nlserver6 start** in Linux) und führen Sie den Befehl **nlserver pdump** erneut aus, um zu überprüfen, ob alle aktivierten Module vorhanden sind.

   >[!NOTE]
   >
   >Ab Version 20.1 wird empfohlen, stattdessen den folgenden Befehl zu verwenden (für Linux): **systemctl start nlserver**


   ```sql
   12:09:54 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   syslogd@default (7611) - 9.2 MB
   stat@demo (5988) - 1.5 MB
   inMail@demo (7830) - 11.9 MB
   watchdog (27369) - 3.1 MB
   mta@demo (7831) - 15.6 MB
   wfserver@demo (7832) - 11.5 MB
   web@default (28671) - 40.5 MB
   ```

   Mit diesem Befehl erfahren Sie auch die Version und die Build-Nummer des auf dem Computer installierten Adobe Campaign-Servers.

1. Testen Sie das Modul **nlserver web** mit der URL: [https://console.campaign.net/nl/jsp/logon.jsp](https://tracking.campaign.net/r/test).

   Diese URL ermöglicht Ihnen den Zugriff auf die Download-Seite für das Client-Setup-Programm. [Weitere Informationen](../../installation/using/client-console-availability-for-windows.md).

   Geben Sie den **internen** Login und das zugehörige Kennwort ein, wenn Sie auf die Seite &quot;Zugriffskontrolle&quot;gelangen.

   ![](assets/s_ncs_install_access_client.png)

### Installation und Konfiguration des Anwendungsservers 2 {#installing-and-configuring-the-application-server-2}

Gehen Sie wie folgt vor:

1. Installieren Sie den Adobe Campaign-Server.
1. Kopieren Sie die Dateien der von Ihnen erstellten Instanz auf den Anwendungsserver 1.

   Wir behalten denselben Instanznamen wie der Anwendungsserver 1 bei.

1. Ändern Sie die Einstellung für **internal** auf den gleichen Wert wie für den Anwendungsserver 1.
1. Verknüpfen Sie die Datenbank mit der Instanz:

   ```
   nlserver config -setdblogin:PostgreSQL:campaign:demo@dbsrv -instance:demo
   ```

1. Bearbeiten Sie die Datei &quot;**config-demo.xml**&quot;(erstellt über den vorherigen Befehl und befindet sich neben der Datei &quot;**config-default.xml**&quot;), überprüfen Sie, ob die Dateien &quot;**mta**&quot;(delivery), &quot;**wfserver**&quot;(workflow), &quot;**inMail**&quot;(rebound mails) und &quot;**stat1}&quot;(statistics) Prozesse aktiviert sind, konfigurieren Sie dann die Adresse des Statistikservers** app **:**

   ```xml
   <?xml version='1.0'?>
   <serverconf>  
     <shared>    
       <!-- add lang="eng" to dataStore to force English for the instance -->    
       <dataStore hosts="tracking.campaign.net*,console.campaign.net*">      
         <mapping logical="*" physical="default"/>    
       </dataStore>  </shared>  
       <mta autoStart="true" statServerAddress="app">
       <wfserver autoStart="true"/>  
       <inMail autoStart="true"/>  
       <sms autoStart="false"/>  
       <listProtect autoStart="false"/>
   </serverconf>
   ```

   Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../installation/using/configuring-campaign-server.md#enabling-processes).

1. Bearbeiten Sie die Datei **serverConf.xml** und füllen Sie die DNS-Konfiguration des MTA-Moduls aus:

   ```xml
   <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
   ```

   >[!NOTE]
   >
   >Der Parameter **nameServers** wird nur in Windows verwendet.

   Weitere Informationen hierzu finden Sie unter [Konfiguration des Campaign-Servers](../../installation/using/configuring-campaign-server.md).

1. Starten Sie die Adobe Campaign-Server.

   Weiterführende Informationen hierzu finden Sie in den folgenden Abschnitten:

   * Für Linux: [Erststart des Servers](../../installation/using/installing-packages-with-linux.md#first-start-up-of-the-server)
   * Windows: [Erster Start des Servers](../../installation/using/installing-the-server.md#first-start-up-of-the-server)

### Installieren und Konfigurieren der Frontserver {#installing-and-configuring-the-frontal-servers}

Die Installations- und Konfigurationsverfahren sind auf beiden Computern identisch.

Zusammenfassend sind folgende Etappen zu durchlaufen:

1. Installieren Sie den Adobe Campaign-Server,
1. Befolgen Sie die in den folgenden Abschnitten beschriebenen Schritte zur Webserverintegration (IIS, Apache):

   * Für Linux: [Integration in einen Webserver für Linux](../../installation/using/integration-into-a-web-server-for-linux.md),
   * Für Windows: [Integration in einen Webserver für Windows](../../installation/using/integration-into-a-web-server-for-windows.md).

1. Kopieren Sie die Dateien **config-demo.xml** und **serverConf.xml** , die während der Installation erstellt wurden. Aktivieren Sie in der Datei **config-demo.xml** den Prozess **trackinglogd** und deaktivieren Sie die Prozesse **mta**, **inmail**, **wfserver** und **stat**.
1. Bearbeiten Sie die Datei **serverConf.xml** und füllen Sie die redundanten Tracking-Server in die Parameter der Umleitung:

   ```xml
   <spareServer enabledIf="$(hostname)!='front_srv1'" id="1" url="https://front_srv1:8080"/>
   <spareServer enabledIf="$(hostname)!='front_srv2'" id="2" url="https://front_srv2:8080"/>
   ```

1. Starten Sie die Website und testen Sie die Umleitung von der URL: [https://tracking.campaign.net/r/test](https://tracking.campaign.net/r/test)

   Der Browser sollte die folgenden Meldungen anzeigen (je nach URL, die vom Lastenausgleich umgeleitet wird):

   ```xml
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="front_srv1"/>
   ```

   oder

   ```xml
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="front_srv2"/>
   ```

   Weiterführende Informationen hierzu finden Sie in den folgenden Abschnitten:

   * Für Linux: [Starten des Webservers und Testen der Konfiguration](../../installation/using/integration-into-a-web-server-for-linux.md#launching-the-web-server-and-testing-the-configuration),
   * Für Windows: [Starten des Webservers und Testen der Konfiguration](../../installation/using/integration-into-a-web-server-for-windows.md#launching-the-web-server-and-testing-the-configuration).

1. Starten Sie den Adobe Campaign-Server.
