---
title: Eigenständige Bereitstellung
seo-title: Eigenständige Bereitstellung
description: Eigenständige Bereitstellung
seo-description: null
page-status-flag: never-activated
uuid: 48ce793e-cb9f-4102-898f-758512cb9bf2
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: deployment-types-
discoiquuid: 9834638f-a8bb-4969-9f8d-99b8d9fdb1ca
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 6b631f8456ad1f61cec1630334d76752f6af9866

---


# Eigenständige Bereitstellung{#standalone-deployment}

Diese Konfiguration umfasst alle Komponenten auf demselben Computer:

* Antragsprozess (Web),
* Lieferprozess (Metadaten),
* Umleitungsprozess (Verfolgung),
* Workflow-Prozess und geplante Aufgaben (wfserver),
* Absprung-Mail-Prozess (inMail),
* statistischer Prozess (STAT).

Die Kommunikation zwischen den Prozessen erfolgt insgesamt nach folgendem Schema:

![](assets/s_900_ncs_install_standaloneconfig.png)

Diese Art der Konfiguration kann ausgeführt werden, wenn Listen mit weniger als 100.000 Empfängern verwaltet werden, zum Beispiel mit den folgenden Softwareschichten:

* Linux,
* Apache,
* PostgreSQL,
* Qmail.

Mit zunehmendem Volumen wird der Datenbankserver durch eine Variante dieser Architektur auf einen anderen Computer übertragen, um die Leistung zu verbessern.

>[!NOTE]
>
>Ein bestehender Datenbankserver kann auch verwendet werden, wenn er über ausreichende Ressourcen verfügt.

## Funktionen {#features}

### Vorteile {#advantages}

* Vollständig eigenständige und niedrige Konfigurationskosten (keine abrechnungsfähigen Lizenzen erforderlich, wenn die unten aufgeführte Open-Source-Software verwendet wird).
* Vereinfachte Installation und Netzwerkkonfiguration.

### Nachteile {#disadvantages}

* Ein kritischer Computer im Falle eines Vorfalls.
* Begrenzte Bandbreite bei der Übertragung von Nachrichten (nach unserer Erfahrung etwa mehrere zehntausend Mails pro Stunde).
* Potenzielle Verlangsamung der Anwendung bei der Übertragung.
* Der Anwendungsserver muss von außen verfügbar sein (z. B. während er sich in der DMZ befindet), da er den Umleitungsserver hostet.

## Installation und Konfigurationsschritte {#installation-and-configuration-steps}

### Voraussetzungen {#prerequisites}

* JDK,
* Webserver (IIS, Apache),
* Zugriff auf einen Datenbankserver,
* Absprungkasten, der über POP3 erreichbar ist,
* Erstellung von zwei DNS-Aliasen:

   * die erstmalige Exposition gegenüber der Öffentlichkeit zur Verfolgung und zum Hinweis auf den Computer über sein öffentliches IP;
   * der zweite Alias, der internen Benutzern für den Konsolenzugriff zur Verfügung steht und auf denselben Computer verweist.

* Firewall zum Öffnen von STMP (25), DNS (53), HTTP (80), HTTPS (443), SQL (1521 für Oracle, 5432 für PostgreSQL usw.) Ports. Weitere Informationen finden Sie unter [Netzwerkkonfiguration](../../installation/using/network-configuration.md).

In den folgenden Beispielen sind die Parameter der Instanz:

* Name der Instanz: **Demo**
* DNS-Maske: **console.campaign.net*** (nur für Client-Konsolenverbindungen und für Berichte)
* Datenbank: **Kampagne:demo@dbsrv**

### Installieren und Konfigurieren (Einzelcomputer) {#installing-and-configuring--single-machine-}

Gehen Sie wie folgt vor:

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

   * Für Linux: [Erststart des Servers](../../installation/using/installing-packages-with-linux.md#first-start-up-of-the-server),
   * Windows: [Erststart des Servers](../../installation/using/installing-the-server.md#first-start-up-of-the-server).

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

1. Bearbeiten Sie die Datei &quot; **config-demo.xml** &quot;(die im vorherigen Schritt neben &quot; **config-default.xml**&quot;erstellt wurde) und stellen Sie sicher, dass die Prozesse **mta** (Bereitstellung), **wfserver** (Workflow), **inMail** (Absprungmails) und **** inTestStartStern (Statistik) aktiviert sind. Konfigurieren Sie dann die Adresse des Statistikservers:

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

   For more on this, refer to [Enabling processes](../../installation/using/campaign-server-configuration.md#enabling-processes).

1. Bearbeiten Sie die Datei &quot; **serverConf.xml** &quot;und geben Sie die Bereitstellungsdomäne an. Geben Sie dann die IP- (oder Host-)Adressen der DNS-Server an, die vom MTA-Modul zur Beantwortung von DNS-Anfragen vom MX-Typ verwendet werden.

   ```
   <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
   ```

   >[!NOTE]
   >
   >Der Parameter **nameServers** wird nur unter Windows verwendet.

   For more on this, refer to [Campaign server configuration](../../installation/using/campaign-server-configuration.md).

1. Kopieren Sie das Setup-Programm für die Client-Konsole (**setup-client-7.XX**, **YYY.exe** für v7 oder **setup-client-6.XX**, **YYYY.exe** für v6.1) in den Ordner **/datakit/nl/eng/jsp** .

   Weitere Informationen finden Sie in den folgenden Abschnitten:

   * Für Linux: Verfügbarkeit der [Client-Konsole für Linux](../../installation/using/client-console-availability-for-linux.md)
   * Windows: Verfügbarkeit der [Client-Konsole für Windows](../../installation/using/client-console-availability-for-windows.md)

1. Folgen Sie dem Webserver-Integrationsverfahren (IIS, Apache), das in den folgenden Abschnitten beschrieben wird:

   * Für Linux: Integration [in einen Webserver für Linux](../../installation/using/integration-into-a-web-server-for-linux.md)
   * Windows: Integration [in einen Webserver für Windows](../../installation/using/integration-into-a-web-server-for-windows.md)

1. Starten Sie die Website und testen Sie die Umleitung mithilfe der URL: https://tracking.campaign.net/r/test.

   Der Browser muss die folgende Meldung anzeigen:

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="localhost"/>
   ```

   Weitere Informationen finden Sie in den folgenden Abschnitten:

   * Für Linux: Webserver [starten und Konfiguration testen](../../installation/using/integration-into-a-web-server-for-linux.md#launching-the-web-server-and-testing-the-configuration)
   * Windows: Webserver [starten und Konfiguration testen](../../installation/using/integration-into-a-web-server-for-windows.md#launching-the-web-server-and-testing-the-configuration)

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

1. Testen Sie das **nlserver-Webmodul** unter Verwendung der URL: https://console.campaign.net/nl/jsp/logon.jsp

   Mit dieser URL können Sie auf die Download-Seite für das Client-Setup-Programm zugreifen.

   Geben Sie die **interne** Anmeldung und das zugehörige Kennwort ein, wenn Sie die Seite zur Zugriffssteuerung aufrufen.

   ![](assets/s_ncs_install_access_client.png)

   Weitere Informationen finden Sie in den folgenden Abschnitten:

   * Für Linux: Verfügbarkeit der [Client-Konsole für Linux](../../installation/using/client-console-availability-for-linux.md)
   * Windows: Verfügbarkeit der [Client-Konsole für Windows](../../installation/using/client-console-availability-for-windows.md)

1. Starten Sie die Adobe Campaign-Client-Konsole (von der vorherigen Downloadseite oder bei einer Windows-Installation direkt auf dem Server), setzen Sie die Server-Verbindungs-URL auf https://console.campaign.net und stellen Sie mithilfe der **internen** Anmeldung eine Verbindung her.

   Siehe [Erstellen einer Instanz und Anmelden](../../installation/using/creating-an-instance-and-logging-on.md) und [Interne ID](../../installation/using/campaign-server-configuration.md#internal-identifier).

   Der Assistent zum Erstellen der Datenbank wird angezeigt, wenn Sie sich zum ersten Mal anmelden:

   ![](assets/s_ncs_install_db_oracle_creation01.png)

   Führen Sie die Schritte im Assistenten aus und erstellen Sie die mit der Verbindungsinstanz verknüpfte Datenbank.

   Weitere Informationen finden Sie unter [Erstellen und Konfigurieren der Datenbank](../../installation/using/creating-and-configuring-the-database.md).

   Sobald die Datenbank erstellt wurde, melden Sie sich ab.

1. Melden Sie sich ohne Kennwort mit der **Admin** -Anmeldung bei der Client-Konsole an und starten Sie den Bereitstellungsassistenten ( **[!UICONTROL Tools > Advanced]** Menü), um die Konfiguration der Instanz abzuschließen.

   Weitere Informationen finden Sie unter [Bereitstellen einer Instanz](../../installation/using/deploying-an-instance.md).

   Die folgenden Hauptparameter sind festzulegen:

   * E-Mail-Auslieferung: Absender- und Antwortadressen und das Fehlerpostfach für Absprungmail.
   * Verfolgung: Füllen Sie die externe URL, die für die Umleitung verwendet wird, und die interne URL, klicken Sie auf **Registrierung auf dem/den Tracking-Server(en)** und validieren Sie sie dann in der **Demo** -Instanz des Tracking-Servers.

      For more on this, refer to [Tracking configuration](../../installation/using/deploying-an-instance.md#tracking-configuration).

      ![](assets/s_ncs_install_deployment_wiz_09.png)

      Da der Adobe Campaign-Server sowohl als Anwendungsserver als auch als Weiterleitungsserver verwendet wird, ist die interne URL, die zum Erfassen von Verfolgungsprotokollen und Transfer-URLs verwendet wird, eine direkte interne Verbindung zu Tomcat (https://localhost:8080).

   * Absprungverwaltung: Geben Sie die Parameter für die Verarbeitung der Absprungmail ein (berücksichtigen Sie nicht den Abschnitt **Unverarbeitete Absprungmeldungen** ).
   * Zugriff von: Geben Sie die beiden URLs für Berichte, Webformulare und Spiegelseiten an.

      ![](assets/d_ncs_install_web_url.png)

