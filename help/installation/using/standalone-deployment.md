---
product: campaign
title: Eigenständige Bereitstellung
description: Eigenständige Bereitstellung
feature: Installation, Architecture, Deployment
audience: installation
content-type: reference
topic-tags: deployment-types-
exl-id: 194366ab-fd9f-4431-9163-ae16c1f96db2
source-git-commit: 1be1528d657537786c430ea9c8bdb3aad58ba20d
workflow-type: tm+mt
source-wordcount: '1079'
ht-degree: 4%

---

# Eigenständige Bereitstellung{#standalone-deployment}



Diese Konfiguration umfasst alle Komponenten auf demselben Computer:

* Anwendungsprozess (Web),
* Versandprozess (mta),
* Umleitungsprozess (Tracking),
* Workflow-Prozess und geplante Aufgaben (wfserver),
* Bounce-Message-Prozess (inMail),
* Statistikverfahren (stat).

Die allgemeine Kommunikation zwischen den Prozessen erfolgt nach folgendem Schema:

![](assets/s_900_ncs_install_standaloneconfig.png)

Diese Art der Konfiguration kann bei der Verwaltung von Listen mit weniger als 100.000 Empfängern und beispielsweise mit den folgenden Softwareschichten ausgeführt werden:

* Linux,
* Apache,
* PostgreSQL,
* Qmail.

Mit zunehmendem Volumen verschiebt eine Variante dieser Architektur den Datenbankserver auf einen anderen Computer, um die Leistung zu verbessern.

>[!NOTE]
>
>Ein bestehender Datenbankserver kann auch verwendet werden, wenn er über ausreichende Ressourcen verfügt.

## Funktionen {#features}

### Vorteile {#advantages}

* Vollständig eigenständige und niedrige Konfigurationskosten (keine abrechnungsfähigen Lizenzen erforderlich, wenn die unten aufgeführte Open-Source-Software verwendet wird).
* Vereinfachte Installation und Netzwerkkonfiguration.

### Nachteile {#disadvantages}

* Ein kritischer Computer im Falle eines Vorfalls.
* Begrenzte Bandbreite bei der Ausstrahlung von Nachrichten (unserer Erfahrung nach etwa zehntausend Mails pro Stunde).
* Potenzielle Verlangsamung der Anwendung bei der Übertragung.
* Der Anwendungsserver muss von außen verfügbar sein (z. B. während er sich in der DMZ befindet), da er den Weiterleitungsserver hostet.

## Installation und Konfiguration {#installation-and-configuration-steps}

### Voraussetzungen {#prerequisites}

* JDK
* Webserver (IIS, Apache),
* Zugriff auf einen Datenbankserver,
* über POP3 zugängliches Bounce-Postfach,
* Erstellung von zwei DNS-Aliassen:

   * die erste, die der Öffentlichkeit zur Verfolgung und zum Verweis auf den Computer in seiner öffentlichen IP-Adresse zur Verfügung gestellt wird;
   * den zweiten Alias, der internen Benutzern für den Konsolenzugriff zur Verfügung gestellt wird und auf denselben Computer verweist.

* Firewall zum Öffnen von SMTP (25), DNS (53), HTTP (80), HTTPS (443), SQL (1521 für Oracle, 5432 für PostgreSQL usw.) Ports. Weitere Informationen finden Sie unter [Netzwerkkonfiguration](../../installation/using/network-configuration.md).

In den folgenden Beispielen sind die Parameter der Instanz:

* Name der Instanz: **demo**
* DNS-Maske: **console.campaign.net&#42;** (nur für Client-Konsolenverbindungen und für Berichte)
* Datenbank: **campaign:demo@dbsrv**

### Installation und Konfiguration (ein Computer) {#installing-and-configuring--single-machine-}

Gehen Sie wie folgt vor:

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

   * Für Linux: [Erststart des Servers](../../installation/using/installing-packages-with-linux.md#first-start-up-of-the-server),
   * Für Windows: [Erster Start des Servers](../../installation/using/installing-the-server.md#first-start-up-of-the-server).

1. Ändern Sie das Kennwort für **internal** mithilfe des Befehls:

   ```
   nlserver config -internalpassword
   ```

   Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../installation/using/configuring-campaign-server.md#internal-identifier).

1. Erstellen Sie die Instanz **demo** mit den DNS-Masken für das Tracking (in diesem Fall **tracking.campaign.net**) und greifen Sie auf die Client-Konsolen zu (in diesem Fall **console.campaign.net**). Dazu gibt es zwei Möglichkeiten:

   * Erstellen Sie die Instanz über die Konsole:

     ![](assets/install_create_new_connexion.png)

     Weitere Informationen hierzu finden Sie unter [Erstellen einer Instanz und Anmelden](../../installation/using/creating-an-instance-and-logging-on.md).

     oder

   * Erstellen Sie die Instanz mithilfe der Befehlszeilen:

     ```
     nlserver config -addinstance:demo/tracking.campaign.net*,console.campaign.net*
     ```

     Weitere Informationen hierzu finden Sie unter [Instanz erstellen](../../installation/using/command-lines.md#creating-an-instance).

1. Bearbeiten Sie die Datei &quot;**config-demo.xml**&quot;(erstellt im vorherigen Schritt neben &quot;**config-default.xml**&quot;) und stellen Sie sicher, dass die Prozesse &quot;**mta**&quot;(delivery), &quot;**wfserver**&quot;(workflow), &quot;**inMail**&quot;(Bounce-Mails) und &quot;**&quot;(statistics) aktiviert sind.** Konfigurieren Sie dann die Adresse des Statistikservers:

   ```
   <?xml version='1.0'?>
   <serverconf>  
     <shared>    
       <!-- add lang="eng" to dataStore to force English for the instance -->    
       <dataStore hosts="tracking.campaign.net*,console.campaign.net*">      
         <mapping logical="*" physical="default"/>    
       </dataStore>  </shared>  
       <mta autoStart="true" statServerAddress="localhost"/>
       <wfserver autoStart="true"/>  
       <inMail autoStart="true"/>  
       <sms autoStart="false"/>  
       <listProtect autoStart="false"/>
   </serverconf>
   ```

   Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../installation/using/configuring-campaign-server.md#enabling-processes).

1. Bearbeiten Sie die Datei &quot;**serverConf.xml**&quot;, geben Sie die Bereitstellungsdomäne an und geben Sie dann die IP- (oder Host-)Adressen der DNS-Server an, die vom MTA-Modul zur Beantwortung von DNS-Abfragen vom MX-Typ verwendet werden.

   ```
   <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
   ```

   >[!NOTE]
   >
   >Der Parameter **nameServers** wird nur in Windows verwendet.

   Weitere Informationen hierzu finden Sie unter [Konfiguration des Campaign-Servers](../../installation/using/configuring-campaign-server.md).

1. Kopieren Sie das Client Console-Setup-Programm **setup-client-7.XXX.exe** in den Ordner **/datakit/nl/eng/jsp** . [Weitere Informationen](../../installation/using/client-console-availability-for-windows.md).

1. Befolgen Sie das in den folgenden Abschnitten beschriebene Verfahren zur Webserverintegration (IIS, Apache):

   * Für Linux: [Integration in einen Webserver für Linux](../../installation/using/integration-into-a-web-server-for-linux.md)
   * Für Windows: [Integration in einen Webserver für Windows](../../installation/using/integration-into-a-web-server-for-windows.md)

1. Starten Sie die Website und testen Sie die Umleitung mithilfe der URL: https://tracking.campaign.net/r/test.

   Der Browser muss die folgende Meldung anzeigen:

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="localhost"/>
   ```

   Weiterführende Informationen hierzu finden Sie in den folgenden Abschnitten:

   * Für Linux: [Starten des Webservers und Testen der Konfiguration](../../installation/using/integration-into-a-web-server-for-linux.md#launching-the-web-server-and-testing-the-configuration)
   * Für Windows: [Starten des Webservers und Testen der Konfiguration](../../installation/using/integration-into-a-web-server-for-windows.md#launching-the-web-server-and-testing-the-configuration)

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

1. Testen Sie das Modul **nlserver web** mithilfe der URL: https://console.campaign.net/nl/jsp/logon.jsp

   Diese URL ermöglicht Ihnen den Zugriff auf die Download-Seite für das Client-Setup-Programm.

   Geben Sie den **internen** Login und das zugehörige Kennwort ein, wenn Sie auf die Seite &quot;Zugriffskontrolle&quot;gelangen. [Weitere Informationen](../../installation/using/client-console-availability-for-windows.md).

   ![](assets/s_ncs_install_access_client.png)

1. Starten Sie die Adobe Campaign-Clientkonsole (von der vorherigen Downloadseite aus oder bei einer Windows-Installation direkt auf dem Server), legen Sie die Server-Verbindungs-URL auf https://console.campaign.net fest und verbinden Sie sich mit dem Anmeldenamen **internal** .

   Weitere Informationen finden Sie auf [dieser Seite](../../installation/using/creating-an-instance-and-logging-on.md) und [in diesem Abschnitt](../../installation/using/configuring-campaign-server.md#internal-identifier).

   Der Datenbankerstellungs-Assistent wird angezeigt, wenn Sie sich zum ersten Mal anmelden:

   ![](assets/s_ncs_install_db_oracle_creation01.png)

   Führen Sie die Schritte im Assistenten aus und erstellen Sie die Datenbank, die der Verbindungsinstanz zugeordnet ist.

   Weitere Informationen hierzu finden Sie unter [Datenbank erstellen und konfigurieren](../../installation/using/creating-and-configuring-the-database.md).

   Melden Sie sich nach der Erstellung der Datenbank ab.

1. Melden Sie sich mit der Anmeldung **admin** ohne Kennwort wieder bei der Clientkonsole an und starten Sie den Softwareverteilungs-Assistenten ( Menü **[!UICONTROL Tools > Erweitert]** ), um die Konfiguration der Instanz abzuschließen.

   Weitere Informationen hierzu finden Sie unter [Bereitstellen einer Instanz](../../installation/using/deploying-an-instance.md).

   Die wichtigsten Parameter sind:

   * E-Mail-Versand: Absender- und Antwortadressen sowie das Fehlerpostfach für Bounce Messages.
   * Tracking: Füllen Sie die für die Weiterleitung verwendete externe URL und die interne URL aus, klicken Sie auf **Registrierung auf dem/den Tracking-Server(n)** und validieren Sie sie dann auf der **Demo** -Instanz des Tracking-Servers.

     Weitere Informationen hierzu finden Sie unter [Tracking-Konfiguration](../../installation/using/deploying-an-instance.md#tracking-configuration).

     ![](assets/s_ncs_install_deployment_wiz_09.png)

     Da der Adobe Campaign-Server sowohl als Anwendungsserver als auch als Weiterleitungsserver verwendet wird, ist die interne URL, die zum Erfassen von Trackinglogs und Übertragungs-URLs verwendet wird, eine direkte interne Verbindung zu Tomcat (https://localhost:8080).

   * Bounce-Verwaltung: Geben Sie die Parameter zur Verarbeitung der Bounce Message an (berücksichtigen Sie nicht den Abschnitt **Nicht verarbeitete Bounce Messages** ).
   * Zugriff von: Geben Sie die beiden URLs für Berichte, Webformulare und Mirrorseiten an.

     ![](assets/d_ncs_install_web_url.png)
