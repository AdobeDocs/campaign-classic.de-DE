---
title: Unternehmensbereitstellung
seo-title: Unternehmensbereitstellung
description: Unternehmensbereitstellung
seo-description: null
page-status-flag: never-activated
uuid: 2c2b5cef-86cb-4cb5-801a-ca6afeae90bb
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: deployment-types-
discoiquuid: 066d0ac1-033c-467b-aa6c-43a97ecd8632
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 6b631f8456ad1f61cec1630334d76752f6af9866

---


# Unternehmensbereitstellung{#enterprise-deployment}

Dies ist die umfassendste Konfiguration. Er baut auf der Standardkonfiguration auf, um mehr Sicherheit und Verfügbarkeit zu gewährleisten:

* dedizierte Umleitungsserver hinter einem HTTP- oder TCP-Lastenausgleich, um Skalierbarkeit und Verfügbarkeit zu gewährleisten,
* zwei Anwendungsserver zur Verbesserung der Durchsatz- und Ausfallsicherheit (Fehlertoleranz), die im LAN isoliert sind.

Die allgemeine Kommunikation zwischen Servern und Prozessen erfolgt gemäß dem folgenden Schema:

![](assets/s_901_ncs_install_enterpriseconfig.png)

Bei dieser Konfiguration kann der erwartete Durchsatz 100.000 Mails pro Stunde bei entsprechender Bandbreite und Abstimmung überschreiten.

## Funktionen {#features}

### Vorteile {#advantages}

* Optimierte Sicherheit: Auf dem Computer in der DMZ werden nur die Server installiert, die von außen offen gelegt werden müssen.
* Hohe Verfügbarkeit ist einfacher sicherzustellen: Nur der von außen sichtbare Computer muss mit hoher Verfügbarkeit verwaltet werden.

### Nachteile {#disadvantages}

Höhere Hardware- und Verwaltungskosten.

### Empfohlene Ausrüstung {#recommended-equipment}

* Anwendungsserver: 2 GHz Quadcore-CPU, 4 GB RAM, Software RAID 1 80 GB SATA-Festplatte.
* Umleitungsserver: 2 GHz Quadcore-CPU, 4 GB RAM, Software RAID 1 80 GB SATA-Festplatte.

>[!NOTE]
>
>Es ist möglich, einen vorhandenen Lastenausgleich für Traffic zu den Umleitungsservern wiederzuverwenden.

## Installation und Konfigurationsschritte {#installation-and-configuration-steps}

### Voraussetzungen {#prerequisites}

* JDK auf beiden Anwendungsservern,
* Webserver (IIS, Apache) an beiden Frontalstellen,
* Zugriff auf einen Datenbankserver auf beiden Anwendungsservern,
* Absprungkasten, der über POP3 erreichbar ist,
* Erstellen von zwei DNS-Aliasen auf dem Lastenausgleich:

   * die erste, die der Öffentlichkeit zur Verfolgung und zum Verweis auf den Lastenausgleich an einer virtuellen IP-Adresse (VIP) zur Verfügung gestellt wird und die dann an die beiden Frontserver verteilt wird,
   * die zweite, die den internen Benutzern für den Zugriff über die Konsole offen steht und auf einen Lastenausgleich auf einer virtuellen IP-Adresse (VIP) verweist und die dann an die beiden Anwendungsserver verteilt wird.

* Firewall zum Öffnen von STMP (25), DNS (53), HTTP (80), HTTPS (443), SQL (1521 für Oracle, 5432 für PostgreSQL usw.) Ports. Weitere Informationen finden Sie im Abschnitt [Datenbankzugriff](../../installation/using/network-configuration.md#database-access).

>[!CAUTION]
>
>Wenn Ihre Anwendungsserver auf eine einzige Datenbankinstanz verweisen, wird nach dem Import eines Standardpakets auf einer Instanz das im Paket enthaltene Schema nicht auf der anderen Instanz geladen.
>  
>Wenn Ihre Anwendungsserver auf eine einzige Datenbankinstanz verweisen, wird das Schema nach dem Ändern des Schemas auf einer Instanz nicht auf der anderen Instanz geladen.
>
>Um diese Probleme wiederherzustellen, müssen Sie den Prozess &quot;web@default&quot;in der zweiten Instanz neu starten, in der ein Fehler aufgetreten ist.

### Installieren und Konfigurieren des Anwendungsservers 1 {#installing-and-configuring-the-application-server-1}

In den folgenden Beispielen sind die Parameter der Instanz:

* Name der Instanz: demo
* DNS-Maske: tracking.campaign.net*, console.campaign.net* (der Anwendungsserver verarbeitet die URLs für Client-Konsolenverbindungen und Berichte sowie für Spiegelseiten und Abmeldeseiten)
* Sprache: englisch
* Datenbank: campaign:demo@dbsrv

Die Schritte zum Installieren des ersten Servers sind:

1. Befolgen Sie die Installationsanweisungen für den Adobe Campaign-Server: **nlserver** -Paket unter Linux oder **setup.exe** unter Windows.

   Weitere Informationen finden Sie unter [Voraussetzungen für die Campaign-Installation unter Linux](../../installation/using/prerequisites-of-campaign-installation-in-linux.md) (Linux) und [Voraussetzungen für die Campaign-Installation unter Windows](../../installation/using/prerequisites-of-campaign-installation-in-windows.md) (Windows).

1. Nachdem der Adobe Campaign-Server installiert wurde, starten Sie den Anwendungsserver (Web) mit dem Befehl **nlserver web -tomcat** (das Webmodul ermöglicht es Ihnen, Tomcat im eigenständigen Webservermodus zu starten, der auf Port 8080 überwacht) und sicherzustellen, dass Tomcat richtig gestartet wird:

   ```
   12:08:18 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   12:08:18 >   Starting Web server module (pid=28505, tid=-1225184768)...
   12:08:18 >   Tomcat started
   12:08:18 >   Server started
   ```


   >[!NOTE]
   >
   >Beim ersten Ausführen des Webmoduls werden die Dateien &quot; **config-default.xml** &quot;und &quot; **serverConf.xml** &quot;im Ordner &quot; **conf** &quot;im Installationsordner erstellt. Alle in der Datei **serverConf.xml** verfügbaren Parameter sind in diesem [Abschnitt](../../installation/using/the-server-configuration-file.md)aufgeführt.

   Drücken Sie **Strg+C** , um den Server zu beenden.

   Weitere Informationen finden Sie in den folgenden Abschnitten:

   * Für Linux: [Erststart des Servers](../../installation/using/installing-packages-with-linux.md#first-start-up-of-the-server)
   * Windows: [Erststart des Servers](../../installation/using/installing-the-server.md#first-start-up-of-the-server)

1. Ändern Sie das **interne** Kennwort mithilfe des Befehls:

   ```
   nlserver config -internalpassword
   ```

   For more on this, refer to [Internal identifier](../../installation/using/campaign-server-configuration.md#internal-identifier).

1. Erstellen Sie die **Demo** -Instanz mit den DNS-Masken zur Verfolgung (in diesem Fall **tracking.campaign.net**) und Zugriff auf Client-Konsolen (in diesem Fall **console.campaign.net**). Es gibt zwei Möglichkeiten:

   * Erstellen Sie die Instanz über die Konsole:

      ![](assets/install_create_new_connexion.png)

      Weitere Informationen finden Sie unter [Erstellen einer Instanz und Anmelden](../../installation/using/creating-an-instance-and-logging-on.md).

      or

   * Erstellen Sie die Instanz mithilfe der Befehlszeilen:

      ```
      nlserver config -addinstance:demo/tracking.campaign.net*,console.campaign.net*
      ```

      For more on this, refer to [Creating an instance](../../installation/using/command-lines.md#creating-an-instance).

1. Bearbeiten Sie die Datei &quot; **config-demo.xml** &quot;(die über den vorherigen Befehl erstellt wurde und sich neben der Datei &quot; **config-default.xml** &quot;befindet), überprüfen Sie, ob die Prozesse &quot; **mta** (Bereitstellung)&quot;, &quot; **wfserver** (Workflow)&quot;, &quot; **inMail** &quot;(rebound mails) und &quot;Direktstatistik&quot;(Statistik) aktiviert sind, und konfigurieren Sie dann die Adresse der AppAppAppApp **** **** server:

   ```
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

   For more on this, refer to [Enabling processes](../../installation/using/campaign-server-configuration.md#enabling-processes).

1. Bearbeiten Sie die Datei &quot; **serverConf.xml** &quot;und geben Sie die Bereitstellungsdomäne an. Geben Sie dann die IP- (oder Host-)Adressen der DNS-Server an, die vom MTA-Modul zur Beantwortung von DNS-Anfragen vom MX-Typ verwendet werden.

   ```
   <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
   ```

   >[!NOTE]
   >
   >Die Parameter **nameServers** werden nur unter Windows verwendet.

   For more on this, refer to [Campaign server configuration](../../installation/using/campaign-server-configuration.md).

1. Kopieren Sie das Setup-Programm für die Client-Konsole (**setup-client-7.XX**, **YYY.exe** für v7 oder **setup-client-6.XX**, **YYYY.exe** für v6.1) in den Ordner **/datakit/nl/eng/jsp** .

   Weitere Informationen finden Sie in den folgenden Abschnitten:

   * Für Linux: Verfügbarkeit der [Client-Konsole für Linux](../../installation/using/client-console-availability-for-linux.md)
   * Windows: Verfügbarkeit der [Client-Konsole für Windows](../../installation/using/client-console-availability-for-windows.md).

1. Starten Sie den Adobe Campaign-Server (**net start nlserver6** in Windows, **/etc/init.d/nlserver6 start** in Linux) und führen Sie den Befehl **nlserver pdump** erneut aus, um zu prüfen, ob alle aktivierten Module vorhanden sind.

   >[!NOTE]
   >
   >Ab 20.1 wird empfohlen, stattdessen den folgenden Befehl zu verwenden (für Linux): nlserver **systemctl start**


   ```
   12:09:54 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   syslogd@default (7611) - 9.2 MB
   stat@demo (5988) - 1.5 MB
   inMail@demo (7830) - 11.9 MB
   watchdog (27369) - 3.1 MB
   mta@demo (7831) - 15.6 MB
   wfserver@demo (7832) - 11.5 MB
   web@default (28671) - 40.5 MB
   ```

   Mit diesem Befehl können Sie auch die Version und die Build-Nummer des Adobe Campaign-Servers kennen, der auf dem Computer installiert ist.

1. Testen Sie das **nlserver-Webmodul** unter Verwendung der URL: [https://console.campaign.net/nl/jsp/logon.jsp](https://tracking.campaign.net/r/test).

   Mit dieser URL können Sie auf die Download-Seite für das Client-Setup-Programm zugreifen.

   Geben Sie die **interne** Anmeldung und das zugehörige Kennwort ein, wenn Sie die Seite zur Zugriffssteuerung aufrufen.

   ![](assets/s_ncs_install_access_client.png)

   Weitere Informationen finden Sie in den folgenden Abschnitten:

   * Für Linux: Verfügbarkeit der [Client-Konsole für Linux](../../installation/using/client-console-availability-for-linux.md)
   * Windows: Verfügbarkeit der [Client-Konsole für Windows](../../installation/using/client-console-availability-for-windows.md)

### Installieren und Konfigurieren des Anwendungsservers 2 {#installing-and-configuring-the-application-server-2}

Gehen Sie wie folgt vor:

1. Installieren Sie den Adobe Campaign-Server.
1. Kopieren Sie die Dateien der erstellten Instanz auf den Anwendungsserver 1.

   Der Instanzname des Anwendungsservers 1 bleibt unverändert.

1. Ändern Sie die **internen** Werte in die Einstellung für Anwendungsserver 1.
1. Verknüpfen Sie die Datenbank mit der Instanz:

   ```
   nlserver config -setdblogin:PostgreSQL:campaign:demo@dbsrv -instance:demo
   ```

1. Bearbeiten Sie die Datei &quot; **config-demo.xml** &quot;(die über den vorherigen Befehl erstellt wurde und sich neben der Datei &quot; **config-default.xml** &quot;befindet), überprüfen Sie, ob die Prozesse &quot; **mta** (Bereitstellung)&quot;, &quot; **wfserver** (Workflow)&quot;, &quot; **inMail** &quot;(rebound mails) und &quot;Direktstatistik&quot;(Statistik) aktiviert sind, und konfigurieren Sie dann die Adresse der AppAppAppApp **** **** server:

   ```
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

   For more on this, refer to [Enabling processes](../../installation/using/campaign-server-configuration.md#enabling-processes).

1. Bearbeiten Sie die Datei **serverConf.xml** und füllen Sie die DNS-Konfiguration des MTA-Moduls aus:

   ```
   <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
   ```

   >[!NOTE]
   >
   >Der Parameter **nameServers** wird nur unter Windows verwendet.

   For more on this, refer to [Campaign server configuration](../../installation/using/campaign-server-configuration.md).

1. Starten Sie die Adobe Campaign-Server.

   Weitere Informationen finden Sie in den folgenden Abschnitten:

   * Für Linux: [Erststart des Servers](../../installation/using/installing-packages-with-linux.md#first-start-up-of-the-server)
   * Windows: [Erststart des Servers](../../installation/using/installing-the-server.md#first-start-up-of-the-server)

### Installieren und Konfigurieren der Frontserver {#installing-and-configuring-the-frontal-servers}

Die Installations- und Konfigurationsverfahren sind auf beiden Computern identisch.

Zusammenfassend sind folgende Etappen zu durchlaufen:

1. Installieren Sie den Adobe Campaign-Server,
1. Befolgen Sie die in den folgenden Abschnitten beschriebenen Webserver-Integrationsschritte (IIS, Apache):

   * Für Linux: [Integration in einen Webserver für Linux](../../installation/using/integration-into-a-web-server-for-linux.md),
   * Windows: [Integration in einen Webserver für Windows](../../installation/using/integration-into-a-web-server-for-windows.md).

1. Kopieren Sie die **Dateien &quot;config-demo.xml** &quot;und &quot; **serverConf.xml** &quot;, die während der Installation erstellt wurden. Aktivieren Sie in der Datei &quot; **demo.xml** &quot;den **trackinglogd** -Prozess und deaktivieren Sie die **Prozesse &quot;mta**&quot;, &quot; **inmail**&quot;, &quot; **wfserver** **** &quot;und &quot;stat&quot;.
1. Bearbeiten Sie die Datei &quot; **serverConf.xml** &quot;und füllen Sie die redundanten Tracking-Server in die Parameter der Umleitung:

   ```
   <spareServer enabledIf="$(hostname)!='front_srv1'" id="1" url="https://front_srv1:8080"/>
   <spareServer enabledIf="$(hostname)!='front_srv2'" id="2" url="https://front_srv2:8080"/>
   ```

1. Starten Sie die Website und testen Sie die Umleitung von der URL: [https://tracking.campaign.net/r/test](https://tracking.campaign.net/r/test)

   Der Browser sollte die folgenden Meldungen anzeigen (je nach URL, die vom Lastenausgleich umgeleitet wird):

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="front_srv1"/>
   ```

   or

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="front_srv2"/>
   ```

   Weitere Informationen finden Sie in den folgenden Abschnitten:

   * Für Linux: Webserver [starten und Konfiguration](../../installation/using/integration-into-a-web-server-for-linux.md#launching-the-web-server-and-testing-the-configuration)testen,
   * Windows: Webserver [starten und die Konfiguration](../../installation/using/integration-into-a-web-server-for-windows.md#launching-the-web-server-and-testing-the-configuration)testen.

1. Starten Sie den Adobe Campaign-Server.

