---
solution: Campaign Classic
product: campaign
title: Enterprise-Bereitstellung
description: Enterprise-Bereitstellung
audience: installation
content-type: reference
topic-tags: deployment-types-
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1263'
ht-degree: 2%

---


# Enterprise-Bereitstellung{#enterprise-deployment}

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

## Installationsschritte und Konfigurationsschritte {#installation-and-configuration-steps}

### Voraussetzungen {#prerequisites}

* JDK auf beiden Anwendungsservern,
* Webserver (IIS, Apache) an beiden Frontalstellen,
* Zugriff auf einen Datenbankserver auf beiden Anwendungsservern,
* Absprungkasten, der über POP3 erreichbar ist,
* Erstellen von zwei DNS-Aliasen auf dem Lastenausgleich:

   * die erste öffentlich zugänglich gemacht wird, um den Lastenausgleich zu verfolgen und auf eine virtuelle IP-Adresse (VIP) zu verweisen, und die dann an die beiden Frontserver verteilt wird,
   * die zweite, die den internen Benutzern für den Zugriff über die Konsole offen steht und auf einen Lastenausgleich auf einer virtuellen IP-Adresse (VIP) zeigt und die dann an die beiden Anwendungsserver verteilt wird.

* Firewall zum Öffnen von STMP (25), DNS (53), HTTP (80), HTTPS (443), SQL (1521 für Oracle, 5432 für PostgreSQL usw.) Ports. Weitere Informationen finden Sie im Abschnitt [Datenbankzugriff](../../installation/using/network-configuration.md#database-access).

>[!CAUTION]
>
>Wenn Ihre Anwendungsserver auf eine einzige Datenbankinstanz verweisen, wird nach dem Import eines Standardpakets auf einer Instanz das im Paket enthaltene Schema nicht auf der anderen Instanz geladen.
>  
>Wenn Ihre Anwendungsserver auf eine einzige Datenbankinstanz verweisen, wird das Schema nach dem Ändern des Schemas auf einer Instanz nicht auf der anderen geladen.
>
>Um diese Probleme wiederherzustellen, müssen Sie den Prozess &quot;web@default&quot;in der zweiten Instanz neu starten, in der ein Fehler aufgetreten ist.

### Installieren und Konfigurieren des Anwendungsservers 1 {#installing-and-configuring-the-application-server-1}

In den folgenden Beispielen sind die Parameter der Instanz:

* Name der Instanz: demo
* DNS-Maske: tracking.Kampagne.net*, console.Kampagne.net* (der Anwendungsserver verarbeitet die URLs für Client-Konsolenverbindungen und -Berichte sowie für Mirrorseiten und Abmeldungen)
* Sprache: englisch
* Datenbank: kampagne:demo@dbsrv

Die Schritte zum Installieren des ersten Servers sind:

1. Befolgen Sie die Installationsanweisungen für den Adobe Campaign-Server: **nlserver** -Paket unter Linux oder **setup.exe** unter Windows.

   Weitere Informationen dazu finden Sie unter [Voraussetzungen für die Installation der Kampagne unter Linux](../../installation/using/prerequisites-of-campaign-installation-in-linux.md) (Linux) und [Voraussetzungen für die Kampagne unter Windows](../../installation/using/prerequisites-of-campaign-installation-in-windows.md) (Windows).

1. Sobald der Adobe Campaign-Server installiert ist, führen Sie einen Beginn des Anwendungsservers (Web) mit dem Befehl **nlserver web -tomcat** durch (das Webmodul ermöglicht Ihnen, den Beginn von Tomcat im eigenständigen Webservermodus, der auf Port 8080 überwacht, durchzuführen) und stellen Sie sicher, dass die Tomcat-Beginn korrekt sind:

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

   * Für Linux: [Erster Beginn des Servers](../../installation/using/installing-packages-with-linux.md#first-start-up-of-the-server)
   * Windows: [Erster Beginn des Servers](../../installation/using/installing-the-server.md#first-start-up-of-the-server)

1. Ändern Sie das **interne** Kennwort mithilfe des Befehls:

   ```
   nlserver config -internalpassword
   ```

   For more on this, refer to [Internal identifier](../../installation/using/campaign-server-configuration.md#internal-identifier).

1. Erstellen Sie die **Demo** -Instanz mit den DNS-Masken zur Verfolgung (in diesem Fall **tracking.Kampagne.net**) und Zugriff auf Client-Konsolen (in diesem Fall **console.Kampagne.net**). Es gibt zwei Möglichkeiten, dies zu tun:

   * Erstellen Sie die Instanz über die Konsole:

      ![](assets/install_create_new_connexion.png)

      Weitere Informationen finden Sie unter [Erstellen einer Instanz und Anmelden](../../installation/using/creating-an-instance-and-logging-on.md).

      oder

   * Erstellen Sie die Instanz mithilfe der Befehlszeilen:

      ```
      nlserver config -addinstance:demo/tracking.campaign.net*,console.campaign.net*
      ```

      For more on this, refer to [Creating an instance](../../installation/using/command-lines.md#creating-an-instance).

1. Bearbeiten Sie die Datei &quot; **config-demo.xml** &quot;(erstellt über den vorherigen Befehl und befindet sich neben der Datei &quot; **config-default.xml** &quot;), überprüfen Sie, ob die Prozesse &quot; **mta** &quot;(Versand), &quot; **wfserver** &quot;(Workflow), &quot; **inMail** **** **** &quot;(rebound mails) und &quot;σ&quot;(Statistik) aktiviert sind, und konfigurieren Sie dann die Adresse der AppAppApp Statistikserver:

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

1. Bearbeiten Sie die **Datei &quot;serverConf.xml** &quot;und geben Sie die Domäne des Versands an. Geben Sie dann die IP- (oder Host-)Adressen der DNS-Server an, die vom MTA-Modul verwendet werden, um die DNS-Abfragen des MX-Typs zu beantworten.

   ```
   <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
   ```

   >[!NOTE]
   >
   >Die Parameter **nameServers** werden nur unter Windows verwendet.

   For more on this, refer to [Campaign server configuration](../../installation/using/campaign-server-configuration.md).

1. Kopieren Sie das Programm zum Einrichten der Clientkonsole (**setup-client-7.XX**, **YYYY.exe** für v7 oder **setup-client-6.XX**, **YYYY.exe** für v6.1) in den Ordner **/datakit/nl/eng/jsp** .

   Weitere Informationen finden Sie in den folgenden Abschnitten:

   * Für Linux: [Client-Konsolenverfügbarkeit unter Linux](../../installation/using/client-console-availability-for-linux.md)
   * Windows: [Client-Konsolenverfügbarkeit für Windows](../../installation/using/client-console-availability-for-windows.md).

1. Beginn des Adobe Campaign-Servers (**net Beginn nlserver6** in Windows, **/etc/init.d/nlserver6 Beginn** in Linux) und führen Sie den Befehl **nlserver pdump** erneut aus, um zu überprüfen, ob alle aktivierten Module vorhanden sind.

   >[!NOTE]
   >
   >Ab 20.1 wird empfohlen, stattdessen den folgenden Befehl zu verwenden (für Linux): **systemctl Beginn nlserver**


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

   Mit diesem Befehl können Sie auch die Versionsnummer und die Build-Nummer des auf dem Adobe Campaign installierten Servers kennen.

1. Testen Sie das **nlserver-Webmodul** unter Verwendung der URL: [https://console.campaign.net/nl/jsp/logon.jsp](https://tracking.campaign.net/r/test).

   Mit dieser URL können Sie auf die Downloadseite für das Client-Setup-Programm zugreifen.

   Geben Sie die **interne** Anmeldung und das zugehörige Kennwort ein, wenn Sie die Seite &quot;Zugriffskontrolle&quot;aufrufen.

   ![](assets/s_ncs_install_access_client.png)

   Weitere Informationen finden Sie in den folgenden Abschnitten:

   * Für Linux: [Client-Konsolenverfügbarkeit unter Linux](../../installation/using/client-console-availability-for-linux.md)
   * Windows: [Client-Konsolenverfügbarkeit für Windows](../../installation/using/client-console-availability-for-windows.md)

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

1. Bearbeiten Sie die Datei &quot; **config-demo.xml** &quot;(erstellt über den vorherigen Befehl und befindet sich neben der Datei &quot; **config-default.xml** &quot;), überprüfen Sie, ob die Prozesse &quot; **mta** &quot;(Versand), &quot; **wfserver** &quot;(Workflow), &quot; **inMail** **** **** &quot;(rebound mails) und &quot;σ&quot;(Statistik) aktiviert sind, und konfigurieren Sie dann die Adresse der AppAppApp Statistikserver:

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

1. Bearbeiten Sie die Datei &quot; **serverConf.xml** &quot;und füllen Sie die DNS-Konfiguration des MTA-Moduls aus:

   ```
   <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
   ```

   >[!NOTE]
   >
   >Der Parameter **nameServers** wird nur unter Windows verwendet.

   For more on this, refer to [Campaign server configuration](../../installation/using/campaign-server-configuration.md).

1. Beginn der Adobe Campaign-Server.

   Weitere Informationen finden Sie in den folgenden Abschnitten:

   * Für Linux: [Erster Beginn des Servers](../../installation/using/installing-packages-with-linux.md#first-start-up-of-the-server)
   * Windows: [Erster Beginn des Servers](../../installation/using/installing-the-server.md#first-start-up-of-the-server)

### Installieren und Konfigurieren der Frontserver {#installing-and-configuring-the-frontal-servers}

Die Installations- und Konfigurationsverfahren sind auf beiden Computern identisch.

Zusammenfassend sind folgende Etappen zu durchlaufen:

1. Installieren Sie den Adobe Campaign-Server,
1. Befolgen Sie die in den folgenden Abschnitten beschriebenen Webserver-Integrationsschritte (IIS, Apache):

   * For Linux: [Integration into a Web server for Linux](../../installation/using/integration-into-a-web-server-for-linux.md),
   * For Windows: [Integration into a Web server for Windows](../../installation/using/integration-into-a-web-server-for-windows.md).

1. Kopieren Sie die **Dateien &quot;config-demo.xml** &quot;und &quot; **serverConf.xml** &quot;, die während der Installation erstellt wurden. Aktivieren Sie in der Datei &quot; **demo.xml** &quot;den **trackinglogd** -Prozess und deaktivieren Sie die **Prozesse &quot;mta**&quot;, &quot; **inmail**&quot;, &quot; **wfserver** **** &quot;und &quot;stat&quot;.
1. Bearbeiten Sie die Datei &quot; **serverConf.xml** &quot;und füllen Sie die redundanten Tracking-Server in den Parametern der Umleitung aus:

   ```
   <spareServer enabledIf="$(hostname)!='front_srv1'" id="1" url="https://front_srv1:8080"/>
   <spareServer enabledIf="$(hostname)!='front_srv2'" id="2" url="https://front_srv2:8080"/>
   ```

1. Beginn der Website und Testen der Umleitung von der URL: [https://tracking.campaign.net/r/test](https://tracking.campaign.net/r/test)

   Der Browser sollte die folgenden Meldungen anzeigen (je nach URL, die vom Lastenausgleich umgeleitet wird):

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="front_srv1"/>
   ```

   oder

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="front_srv2"/>
   ```

   Weitere Informationen finden Sie in den folgenden Abschnitten:

   * Für Linux: [Webserver starten und Konfiguration](../../installation/using/integration-into-a-web-server-for-linux.md#launching-the-web-server-and-testing-the-configuration)testen,
   * Windows: [Starten des Webservers und Testen der Konfiguration](../../installation/using/integration-into-a-web-server-for-windows.md#launching-the-web-server-and-testing-the-configuration).

1. Beginn des Adobe Campaign-Servers.

