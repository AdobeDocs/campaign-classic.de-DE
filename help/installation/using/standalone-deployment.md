---
product: campaign
title: Eigenständige Freigabe
description: Eigenständige Freigabe
audience: installation
content-type: reference
topic-tags: deployment-types-
exl-id: 194366ab-fd9f-4431-9163-ae16c1f96db2
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '1088'
ht-degree: 6%

---

# Eigenständige Freigabe{#standalone-deployment}

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
* Begrenzte Bandbreite bei der Ausstrahlung von Nachrichten (unserer Erfahrung nach etwa zehntausende von E-Mails pro Stunde).
* Potenzielle Verlangsamung der Anwendung bei der Übertragung.
* Der Anwendungsserver muss von außen verfügbar sein (z. B. während er sich in der DMZ befindet), da er den Weiterleitungsserver hostet.

## Installations- und Konfigurationsschritte {#installation-and-configuration-steps}

### Voraussetzungen {#prerequisites}

* JDK,
* Webserver (IIS, Apache),
* Zugriff auf einen Datenbankserver,
* über POP3 zugängliches Bounce-Postfach,
* Erstellung von zwei DNS-Aliassen:

   * die erste, die der Öffentlichkeit zur Verfolgung und zum Verweis auf den Computer in seiner öffentlichen IP-Adresse zur Verfügung gestellt wird;
   * den zweiten Alias, der internen Benutzern für den Konsolenzugriff zur Verfügung gestellt wird und auf denselben Computer verweist.

* Firewall zum Öffnen von SMTP (25), DNS (53), HTTP (80), HTTPS (443), SQL (1521 für Oracle, 5432 für PostgreSQL usw.) Ports. Weitere Informationen finden Sie unter [Netzwerkkonfiguration](../../installation/using/network-configuration.md).

In den folgenden Beispielen sind die Parameter der Instanz:

* Name der Instanz: **demo**
* DNS-Maske: **console.campaign.net*** (nur für Client-Konsolenverbindungen und für Berichte)
* Datenbank: **campaign:demo@dbsrv**

### Installation und Konfiguration (Einzelmaschine) {#installing-and-configuring--single-machine-}

Gehen Sie wie folgt vor:

1. Befolgen Sie das Installationsverfahren für den Adobe Campaign-Server: **nlserver**-Paket unter Linux oder **setup.exe** unter Windows.

   Weitere Informationen hierzu finden Sie unter [Voraussetzungen für die Campaign-Installation unter Linux](../../installation/using/prerequisites-of-campaign-installation-in-linux.md) (Linux) und [Voraussetzungen für die Campaign-Installation unter Windows](../../installation/using/prerequisites-of-campaign-installation-in-windows.md) (Windows).

1. Nachdem der Adobe Campaign-Server installiert ist, starten Sie den Anwendungsserver (Web) mit dem Befehl **nlserver web -tomcat** (das Webmodul ermöglicht es Ihnen, Tomcat im eigenständigen Webservermodus zu starten, der auf Port 8080 lauscht) und sicherzustellen, dass Tomcat ordnungsgemäß gestartet wird:

   ```
   12:08:18 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   12:08:18 >   Starting Web server module (pid=28505, tid=-1225184768)...
   12:08:18 >   Tomcat started
   12:08:18 >   Server started
   ```

   >[!NOTE]
   >
   >Beim ersten Ausführen des Webmoduls werden die Dateien **config-default.xml** und **serverConf.xml** im Ordner **conf** unter dem Installationsordner erstellt. Alle in **serverConf.xml** verfügbaren Parameter sind in diesem [Abschnitt](../../installation/using/the-server-configuration-file.md) aufgeführt.

   Drücken Sie **Strg+C**, um den Server zu stoppen.

   Weiterführende Informationen hierzu finden Sie in den folgenden Abschnitten:

   * Für Linux: [Erststart des Servers](../../installation/using/installing-packages-with-linux.md#first-start-up-of-the-server),
   * Windows: [Erststart des Servers](../../installation/using/installing-the-server.md#first-start-up-of-the-server).

1. Ändern Sie das Kennwort **internal** mithilfe des Befehls:

   ```
   nlserver config -internalpassword
   ```

   Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../installation/using/configuring-campaign-server.md#internal-identifier).

1. Erstellen Sie die Instanz **demo** mit den DNS-Masken für das Tracking (in diesem Fall **tracking.campaign.net**) und greifen Sie auf Clientkonsolen zu (in diesem Fall **console.campaign.net**). Dazu gibt es zwei Möglichkeiten:

   * Erstellen Sie die Instanz über die Konsole:

      ![](assets/install_create_new_connexion.png)

      Weitere Informationen hierzu finden Sie unter [Erstellen einer Instanz und Anmelden](../../installation/using/creating-an-instance-and-logging-on.md).

      or

   * Erstellen Sie die Instanz mithilfe der Befehlszeilen:

      ```
      nlserver config -addinstance:demo/tracking.campaign.net*,console.campaign.net*
      ```

      Weitere Informationen hierzu finden Sie unter [Instanz erstellen](../../installation/using/command-lines.md#creating-an-instance).

1. Bearbeiten Sie die Datei **config-demo.xml** (die im vorherigen Schritt neben **config-default.xml** erstellt wurde) und stellen Sie sicher, dass die Datei **mta** (delivery), **wfserver** (workflow), **inMail** (Bounce ) und **stat** (statistics) Prozesse aktiviert sind. Konfigurieren Sie dann die Adresse des Statistikservers:

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

1. Bearbeiten Sie die Datei **serverConf.xml** und geben Sie die Bereitstellungsdomäne an. Geben Sie dann die IP- (oder Host-)Adressen der DNS-Server an, die vom MTA-Modul zur Beantwortung von DNS-Abfragen vom MX-Typ verwendet werden.

   ```
   <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
   ```

   >[!NOTE]
   >
   >Der Parameter **nameServers** wird nur in Windows verwendet.

   Weitere Informationen hierzu finden Sie unter [Campaign-Serverkonfiguration](../../installation/using/configuring-campaign-server.md).

1. Kopieren Sie das Clientkonsole-Installationsprogramm (**setup-client-7.XX**, **YYYY.exe** für v7 oder **setup-client-6.XX**, **YYYY.exe** für v6.1) in **/datakit/nl eng/jsp** Ordner. [Weitere Informationen](../../installation/using/client-console-availability-for-windows.md).

1. Befolgen Sie das in den folgenden Abschnitten beschriebene Verfahren zur Webserverintegration (IIS, Apache):

   * Für Linux: [Integration in einen Webserver für Linux](../../installation/using/integration-into-a-web-server-for-linux.md)
   * Windows: [Integration in einen Webserver für Windows](../../installation/using/integration-into-a-web-server-for-windows.md)

1. Starten Sie die Website und testen Sie die Umleitung mithilfe der URL: https://tracking.campaign.net/r/test

   Der Browser muss die folgende Meldung anzeigen:

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="localhost"/>
   ```

   Weiterführende Informationen hierzu finden Sie in den folgenden Abschnitten:

   * Für Linux: [Starten des Webservers und Testen der Konfiguration](../../installation/using/integration-into-a-web-server-for-linux.md#launching-the-web-server-and-testing-the-configuration)
   * Windows: [Starten des Webservers und Testen der Konfiguration](../../installation/using/integration-into-a-web-server-for-windows.md#launching-the-web-server-and-testing-the-configuration)

1. Starten Sie den Adobe Campaign-Server (**net start nlserver6** in Windows, **/etc/init.d/nlserver6 start** in Linux) und führen Sie den Befehl **nlserver pdump** erneut aus, um zu überprüfen, ob alle aktivierten Module vorhanden sind.

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

   Mit diesem Befehl erfahren Sie auch die Version und die Build-Nummer des auf dem Computer installierten Adobe Campaign-Servers.

1. Testen Sie das Modul **nlserver web** mithilfe der URL: https://console.campaign.net/nl/jsp/logon.jsp

   Diese URL ermöglicht Ihnen den Zugriff auf die Download-Seite für das Client-Setup-Programm.

   Geben Sie die **interne**-Anmeldung und das zugehörige Kennwort ein, wenn Sie die Seite &quot;Zugriffskontrolle&quot;erreichen. [Weitere Informationen](../../installation/using/client-console-availability-for-windows.md).

   ![](assets/s_ncs_install_access_client.png)

1. Starten Sie die Adobe Campaign-Clientkonsole (von der vorherigen Download-Seite aus oder werden Sie bei einer Windows-Installation direkt auf den Server gestartet), setzen Sie die Server-Verbindungs-URL auf https://console.campaign.net und verbinden Sie sich mit dem **internal**-Login.

   Weitere Informationen finden Sie auf [dieser Seite](../../installation/using/creating-an-instance-and-logging-on.md) und [diesem Abschnitt](../../installation/using/configuring-campaign-server.md#internal-identifier).

   Der Datenbankerstellungs-Assistent wird angezeigt, wenn Sie sich zum ersten Mal anmelden:

   ![](assets/s_ncs_install_db_oracle_creation01.png)

   Führen Sie die Schritte im Assistenten aus und erstellen Sie die Datenbank, die der Verbindungsinstanz zugeordnet ist.

   Weitere Informationen hierzu finden Sie unter [Datenbank erstellen und konfigurieren](../../installation/using/creating-and-configuring-the-database.md).

   Melden Sie sich nach der Erstellung der Datenbank ab.

1. Melden Sie sich mit der **admin**-Anmeldung ohne Kennwort wieder an und starten Sie den Softwareverteilungs-Assistenten ( **[!UICONTROL Tools > Erweitert]** -Menü), um die Konfiguration der Instanz abzuschließen.

   Weitere Informationen hierzu finden Sie unter [Bereitstellen einer Instanz](../../installation/using/deploying-an-instance.md).

   Die wichtigsten Parameter sind:

   * E-Mail-Versand: Absender- und Antwortadressen sowie das Fehlerpostfach für Bounce Messages.
   * Tracking: Füllen Sie die externe URL, die für die Weiterleitung verwendet wird, und die interne URL aus, klicken Sie auf **Registrierung auf dem/den Tracking-Server(s)** und validieren Sie sie dann auf der **demo**-Instanz des Tracking-Servers.

      Weitere Informationen hierzu finden Sie unter [Tracking-Konfiguration](../../installation/using/deploying-an-instance.md#tracking-configuration).

      ![](assets/s_ncs_install_deployment_wiz_09.png)

      Da der Adobe Campaign-Server sowohl als Anwendungsserver als auch als Weiterleitungsserver verwendet wird, ist die interne URL, die zum Erfassen von Trackinglogs und Transfer-URLs verwendet wird, eine direkte interne Verbindung zu Tomcat (https://localhost:8080).

   * Bounce-Verwaltung: Geben Sie die Parameter für die Verarbeitung der Bounce Message ein (berücksichtigen Sie nicht den Abschnitt **Nicht verarbeitete Bounce Messages** ).
   * Zugriff über: Geben Sie die beiden URLs für Berichte, Webformulare und Mirrorseiten an.

      ![](assets/d_ncs_install_web_url.png)
