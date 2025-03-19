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



Dies ist die vollständigste Konfiguration. Sie baut auf der Standardkonfiguration auf, um die Sicherheit und Verfügbarkeit zu erhöhen:

* dedizierte Weiterleitungsserver hinter einem HTTP- oder TCP-Lastenausgleich für Skalierbarkeit und Verfügbarkeit,
* zwei Anwendungsserver für verbesserte Durchsatz- und Failover-Funktionalität (Fehlertoleranz), die im LAN isoliert sind.

Die allgemeine Kommunikation zwischen Servern und Prozessen erfolgt gemäß dem folgenden Schema:

![](assets/s_901_ncs_install_enterpriseconfig.png)

Mit dieser Art von Konfiguration kann der erwartete Durchsatz 100.000 E-Mails pro Stunde bei entsprechender Bandbreite und Abstimmung überschreiten.

## Funktionen {#features}

### Vorteile {#advantages}

* Optimierte Sicherheit: Nur Server, die nach außen hin offen gelegt werden müssen, werden auf dem Computer in der DMZ installiert.
* Hohe Verfügbarkeit ist einfacher zu gewährleisten: Nur der von außen sichtbare Computer muss mit Blick auf hohe Verfügbarkeit verwaltet werden.

### Nachteile {#disadvantages}

Höhere Hardware- und Verwaltungskosten.

### Empfohlene Ausrüstung {#recommended-equipment}

* Anwendungsserver: Quad-Core CPU mit 2 GHz, 4 GB RAM, Software-RAID 1 SATA-Festplatte mit 80 GB.
* Weiterleitungsserver: Quad-Core CPU mit 2 GHz, 4 GB RAM, Software-RAID 1 SATA-Festplatte mit 80 GB.

>[!NOTE]
>
>Es ist möglich, einen vorhandenen Lastenausgleich für den Traffic an die Umleitungsserver wiederzuverwenden.

## Installations- und Konfigurationsschritte {#installation-and-configuration-steps}

### Voraussetzungen {#prerequisites}

* JDK auf beiden Anwendungsservern,
* Webserver (IIS, Apache) auf beiden Fronten,
* Zugriff auf einen Datenbankserver auf beiden Anwendungsservern,
* Bounce-Postfach über POP3 zugänglich,
* Erstellung von zwei DNS-Aliassen im Lastenausgleich:

   * die erste öffentlich zugängliche, zur Verfolgung und zum Verweisen auf den Lastenausgleich über eine virtuelle IP-Adresse (VIP), die dann an die beiden Frontserver verteilt wird,
   * Die zweite wird den internen Benutzern für den Zugriff über die Konsole bereitgestellt und verweist auf einen Lastenausgleich auf einer virtuellen IP-Adresse (VIP), die dann an die beiden Anwendungsserver verteilt wird.

* Firewall konfiguriert, um STMP (25)-, DNS (53)-, HTTP (80)-, HTTPS (443)-, SQL (1521 für Oracle, 5432 für PostgreSQL usw.)-Ports zu öffnen. Weitere Informationen finden Sie im Abschnitt [Datenbankzugriff](../../installation/using/network-configuration.md#database-access).

>[!CAUTION]
>
>Wenn Ihre Anwendungs-Server auf eine einzelne Datenbankinstanz verweisen, wird nach dem Import eines Standardpakets auf einer Instanz das im Paket enthaltene Schema nicht auf der anderen Instanz geladen.
>  
>Wenn Ihre Anwendungs-Server auf eine einzelne Datenbankinstanz verweisen, wird das Schema nach dem Ändern des Schemas auf einer Instanz nicht auf der anderen Instanz geladen.
>
>Um diese Probleme zu beheben, müssen Sie den Prozess &quot;web@default&quot; auf der zweiten Instanz neu starten, in der der Fehler aufgetreten ist.

### Installieren und Konfigurieren des Anwendungsservers 1 {#installing-and-configuring-the-application-server-1}

In den folgenden Beispielen sind die Parameter der -Instanz:

* Name der Instanz: demo
* DNS-Maske: tracking.campaign.net&#42;, console.campaign.net&#42; (der Anwendungs-Server verarbeitet die URLs für Verbindungen und Berichte der Client-Konsole sowie für Mirror-Seiten und Abmeldeseiten)
* Sprache: Englisch
* Datenbank: campaign:demo@dbsrv

Die Schritte zur Installation des ersten Servers sind:

1. Befolgen Sie die Installationsanweisungen für den Adobe Campaign-Server: **nlserver**-Paket unter Linux oder **setup.exe** unter Windows.

   Weitere Informationen hierzu finden Sie unter [Voraussetzungen für die Campaign-Installation unter Linux](../../installation/using/prerequisites-of-campaign-installation-in-linux.md) (Linux) und [Voraussetzungen für die Campaign-Installation unter Windows](../../installation/using/prerequisites-of-campaign-installation-in-windows.md) (Windows).

1. Nach der Installation des Adobe Campaign-Servers starten Sie den Anwendungs-Server (Web) mit dem Befehl **nlserver web -tomcat** (das Web-Modul ermöglicht es Ihnen, Tomcat im Standalone-Webserver-Modus zu starten und auf Port 8080 zu überwachen) und stellen sicher, dass Tomcat korrekt startet:

   ```sql
   12:08:18 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   12:08:18 >   Starting Web server module (pid=28505, tid=-1225184768)...
   12:08:18 >   Tomcat started
   12:08:18 >   Server started
   ```


   >[!NOTE]
   >
   >Bei der ersten Ausführung des Web-Moduls werden die Dateien **config-default.xml** und **serverConf.xml** im Verzeichnis **conf** im Installationsordner erstellt. Alle in der Datei **serverConf.xml** verfügbaren Parameter werden in diesem [Abschnitt](../../installation/using/the-server-configuration-file.md) aufgeführt.

   Drücken Sie **Strg+C**, um den Server anzuhalten.

   Weiterführende Informationen hierzu finden Sie in den folgenden Abschnitten:

   * Für Linux: [Erster Serverstart](../../installation/using/installing-packages-with-linux.md#first-start-up-of-the-server)
   * Für Windows: [Erster Serverstart](../../installation/using/installing-the-server.md#first-start-up-of-the-server)

1. Ändern Sie das **internal**-Kennwort mithilfe des Befehls :

   ```
   nlserver config -internalpassword
   ```

   Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../installation/using/configuring-campaign-server.md#internal-identifier).

1. Erstellen Sie die **demo**-Instanz mit den DNS-Masken für das Tracking (in diesem Fall **tracking.campaign.net**) und den Zugriff auf Client-Konsolen (in diesem Fall **console.campaign.net**). Dazu gibt es zwei Möglichkeiten:

   * Erstellen Sie die Instanz über die Konsole:

     ![](assets/install_create_new_connexion.png)

     Weitere Informationen hierzu finden Sie unter [Instanz erstellen und anmelden](../../installation/using/creating-an-instance-and-logging-on.md).

     oder

   * Erstellen Sie die Instanz mithilfe von Befehlszeilen:

     ```
     nlserver config -addinstance:demo/tracking.campaign.net*,console.campaign.net*
     ```

     Weitere Informationen hierzu finden Sie unter [Instanz erstellen](../../installation/using/command-lines.md#creating-an-instance).

1. Bearbeiten Sie die Datei **config-demo.xml** (die mit dem vorherigen Befehl erstellt wurde und sich neben der Datei **config-default.xml** befindet) und überprüfen Sie, ob die **mta** (Versand), **wfserver** (Workflow), **inMail** (Rebound-E-Mails) und **stat** (Statistik) aktiviert sind. Konfigurieren Sie dann die Adresse des **App** Statistikservers:

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

1. Bearbeiten Sie die Datei **serverConf.xml** und geben Sie die Bereitstellungs-Domain an. Geben Sie dann die IP-Adressen (oder Host-Adressen) der DNS-Server an, die vom MTA-Modul zur Beantwortung von DNS-Abfragen vom Typ MX verwendet werden.

   ```xml
   <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
   ```

   >[!NOTE]
   >
   >Der **nameServers**-Parameter wird nur unter Windows verwendet.

   Weitere Informationen hierzu finden Sie unter [Campaign-Server-](../../installation/using/configuring-campaign-server.md).

1. Kopieren Sie das Setup-Programm der Client **Konsole (setup-client-7.XX**, **YYYY.exe** in den Ordner **/datakit/nl/eng/jsp**. [Weitere Informationen](../../installation/using/client-console-availability-for-windows.md).

1. Starten Sie den Adobe Campaign-Server (**net start nlserver6** unter Windows, **/etc/init.d/nlserver6 start** unter Linux) und führen Sie den Befehl **nlserver pdump** erneut aus, um das Vorhandensein aller aktivierten Module zu überprüfen.

   >[!NOTE]
   >
   >Ab 20.1 wird empfohlen, stattdessen den folgenden Befehl zu verwenden (für Linux): **systemctl start nlserver**


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

   Dieser Befehl informiert auch über die Version und Build-Nummer des auf dem Computer installierten Adobe Campaign-Servers.

1. Testen Sie das **nlserver web**-Modul mit der URL: [https://console.campaign.net/nl/jsp/logon.jsp](https://tracking.campaign.net/r/test).

   Diese URL ermöglicht den Zugriff auf die Download-Seite für das Client-Setup-Programm. [Weitere Informationen](../../installation/using/client-console-availability-for-windows.md).

   Geben Sie den **internen** Login und das zugehörige Passwort ein, wenn Sie die Zugangssteuerungsseite erreichen.

   ![](assets/s_ncs_install_access_client.png)

### Installieren und Konfigurieren des Anwendungsservers 2 {#installing-and-configuring-the-application-server-2}

Gehen Sie wie folgt vor:

1. Installieren Sie den Adobe Campaign-Server.
1. Kopieren Sie die Dateien der erstellten Instanz auf den Anwendungs-Server 1.

   Wir behalten den gleichen Instanznamen wie der Anwendungsserver 1 bei.

1. Ändern Sie **Intern** auf denselben Wert wie Anwendungsserver 1.
1. Verknüpfen der Datenbank mit der Instanz:

   ```
   nlserver config -setdblogin:PostgreSQL:campaign:demo@dbsrv -instance:demo
   ```

1. Bearbeiten Sie die Datei **config-demo.xml** (die mit dem vorherigen Befehl erstellt wurde und sich neben der Datei **config-default.xml** befindet) und überprüfen Sie, ob die **mta** (Versand), **wfserver** (Workflow), **inMail** (Rebound-E-Mails) und **stat** (Statistik) aktiviert sind. Konfigurieren Sie dann die Adresse des **App** Statistikservers:

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

1. Bearbeiten Sie die Datei **serverConf.** und füllen Sie die DNS-Konfiguration des MTA-Moduls auf:

   ```xml
   <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
   ```

   >[!NOTE]
   >
   >Der **nameServers**-Parameter wird nur unter Windows verwendet.

   Weitere Informationen hierzu finden Sie unter [Campaign-Server-](../../installation/using/configuring-campaign-server.md).

1. Adobe Campaign-Server starten.

   Weiterführende Informationen hierzu finden Sie in den folgenden Abschnitten:

   * Für Linux: [Erster Serverstart](../../installation/using/installing-packages-with-linux.md#first-start-up-of-the-server)
   * Für Windows: [Erster Serverstart](../../installation/using/installing-the-server.md#first-start-up-of-the-server)

### Frontserver installieren und konfigurieren {#installing-and-configuring-the-frontal-servers}

Die Installations- und Konfigurationsverfahren sind auf beiden Computern identisch.

Zusammenfassend sind folgende Etappen zu durchlaufen:

1. Installieren des Adobe Campaign-Servers
1. Befolgen Sie die in den folgenden Abschnitten beschriebenen Schritte zur Webserver-Integration (IIS, Apache):

   * Für Linux: [Integration in einen Webserver für Linux](../../installation/using/integration-into-a-web-server-for-linux.md),
   * Für Windows: [Integration in einen Webserver für Windows](../../installation/using/integration-into-a-web-server-for-windows.md).

1. Kopieren Sie die **config-demo.xml** und **serverConf.xml** Dateien, die während der Installation erstellt wurden. Aktivieren Sie in **Datei „config-demo.**&quot; den **trackinglogd**-Prozess und deaktivieren Sie die **mta**-, **inmail**-, **wfserver**- und **stat**-Prozesse.
1. Bearbeiten Sie die Datei **serverConf.xml** und füllen Sie die redundanten Tracking-Server in den Parametern der Umleitung auf:

   ```xml
   <spareServer enabledIf="$(hostname)!='front_srv1'" id="1" url="https://front_srv1:8080"/>
   <spareServer enabledIf="$(hostname)!='front_srv2'" id="2" url="https://front_srv2:8080"/>
   ```

1. Starten Sie die Website und testen Sie die Umleitung über die URL: [https://tracking.campaign.net/r/test](https://tracking.campaign.net/r/test)

   Der Browser sollte die folgenden Meldungen anzeigen (abhängig von der URL, die vom Load-Balancer umgeleitet wird):

   ```xml
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="front_srv1"/>
   ```

   oder

   ```xml
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="front_srv2"/>
   ```

   Weiterführende Informationen hierzu finden Sie in den folgenden Abschnitten:

   * Für Linux: [Webserver starten und Konfiguration testen](../../installation/using/integration-into-a-web-server-for-linux.md#launching-the-web-server-and-testing-the-configuration),
   * Für Windows: [Webserver starten und Konfiguration ](../../installation/using/integration-into-a-web-server-for-windows.md#launching-the-web-server-and-testing-the-configuration).

1. Adobe Campaign-Server starten.
