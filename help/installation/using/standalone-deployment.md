---
product: campaign
title: Eigenständige Bereitstellung
description: Eigenständige Bereitstellung
feature: Installation, Architecture, Deployment
audience: installation
content-type: reference
topic-tags: deployment-types-
exl-id: 194366ab-fd9f-4431-9163-ae16c1f96db2
source-git-commit: 0fba6a2ad4ffa864e2f726f241aa9d7cd39072a6
workflow-type: tm+mt
source-wordcount: '1079'
ht-degree: 4%

---

# Eigenständige Bereitstellung{#standalone-deployment}



Diese Konfiguration umfasst alle Komponenten auf demselben Computer:

* Anwendungsprozess (Web),
* Versandprozess (MTA),
* Weiterleitungsprozess (Tracking),
* Workflow-Prozess und geplante Aufgaben (wfserver),
* Bounce-Message-Prozess (inMail),
* In: Statistics Process (stat).

Die gesamte Kommunikation zwischen den Prozessen erfolgt nach folgendem Schema:

![](assets/s_900_ncs_install_standaloneconfig.png)

Diese Art der Konfiguration kann bei der Verwaltung von Listen mit weniger als 100.000 Empfängerinnen und Empfängern und beispielsweise mit den folgenden Software-Ebenen ausgeführt werden:

* Linux,
* Apache,
* PostgreSQL,
* Qmail.

Wenn das Volumen wächst, verschiebt eine Variante dieser Architektur den Datenbank-Server auf einen anderen Computer, um die Leistung zu verbessern.

>[!NOTE]
>
>Ein bestehender Datenbank-Server kann auch verwendet werden, wenn er über ausreichende Ressourcen verfügt.

## Funktionen {#features}

### Vorteile {#advantages}

* Vollständig eigenständige und niedrige Konfigurationskosten (keine kostenpflichtigen Lizenzen erforderlich, wenn die unten aufgeführte Open-Source-Software verwendet wird).
* Vereinfachte Installation und Netzwerkkonfiguration.

### Nachteile {#disadvantages}

* Ein kritischer Computer im Falle eines Vorfalls.
* Begrenzte Bandbreite bei der Übertragung von Nachrichten (erfahrungsgemäß rund zehntausende E-Mails pro Stunde).
* Potenzielle Verlangsamung der Anwendung bei der Übertragung.
* Der Anwendungs-Server muss von außen verfügbar sein (z. B. während er sich in der DMZ befindet), da er den Umleitungsserver hostet.

## Installations- und Konfigurationsschritte {#installation-and-configuration-steps}

### Voraussetzungen {#prerequisites}

* JDK,
* Webserver (IIS, Apache),
* Zugriff auf einen Datenbank-Server,
* Bounce-Postfach über POP3 zugänglich,
* Erstellung von zwei DNS-Aliassen:

   * das erste Gerät, das der Öffentlichkeit zur Verfolgung und zum Verweisen auf den Computer auf seiner öffentlichen IP-Adresse zur Verfügung gestellt wird;
   * Der zweite Alias, der internen Benutzern für den Konsolenzugriff bereitgestellt wird und auf denselben Computer verweist.

* Firewall konfiguriert, um SMTP (25)-, DNS (53)-, HTTP (80)-, HTTPS (443)-, SQL (1521 für Oracle, 5432 für PostgreSQL usw.)-Ports zu öffnen. Weitere Informationen finden Sie unter [Netzwerkkonfiguration](../../installation/using/network-configuration.md).

In den folgenden Beispielen sind die Parameter der -Instanz:

* Name der Instanz: **demo**
* DNS-Maske: **console.campaign.net&#42;** (nur für Client-Konsolenverbindungen und für Berichte)
* Datenbank: **campaign:demo@dbsrv**

### Installieren und Konfigurieren (ein Computer) {#installing-and-configuring--single-machine-}

Gehen Sie wie folgt vor:

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

   * Für Linux: [Erster Start des Servers](../../installation/using/installing-packages-with-linux.md#first-start-up-of-the-server),
   * Für Windows: [Erster Serverstart](../../installation/using/installing-the-server.md#first-start-up-of-the-server).

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

1. Bearbeiten Sie die Datei **config-demo.xml** (die im vorherigen Schritt neben **config-default.xml** erstellt wurde) und stellen Sie sicher, dass die **mta** (Versand), **wfserver** (Workflow), **inMail** (Bounce-Mails) und **stat** (Statistiken) aktiviert sind. Konfigurieren Sie dann die Adresse des Statistikservers:

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

1. Bearbeiten Sie die Datei **serverConf.xml** und geben Sie die Bereitstellungs-Domain an. Geben Sie dann die IP-Adressen (oder Host-Adressen) der DNS-Server an, die vom MTA-Modul zur Beantwortung von DNS-Abfragen vom Typ MX verwendet werden.

   ```
   <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
   ```

   >[!NOTE]
   >
   >Der **nameServers**-Parameter wird nur unter Windows verwendet.

   Weitere Informationen hierzu finden Sie unter [Campaign-Server-](../../installation/using/configuring-campaign-server.md).

1. Kopieren Sie das Setup-Programm der Client **Konsole (setup-client-7.XXX.exe** in den Ordner **/datakit/nl/eng/jsp**. [Weitere Informationen](../../installation/using/client-console-availability-for-windows.md).

1. Befolgen Sie das in den folgenden Abschnitten beschriebene Verfahren zur Webserver-Integration (IIS, Apache):

   * Für Linux: [Integration in einen Webserver für Linux](../../installation/using/integration-into-a-web-server-for-linux.md)
   * Für Windows: [Integration in einen Webserver für Windows](../../installation/using/integration-into-a-web-server-for-windows.md)

1. Starten Sie die Website und testen Sie die Umleitung über die URL: https://tracking.campaign.net/r/test.

   Der Browser muss die folgende Meldung anzeigen:

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="localhost"/>
   ```

   Weiterführende Informationen hierzu finden Sie in den folgenden Abschnitten:

   * Für Linux: [Webserver starten und Konfiguration testen](../../installation/using/integration-into-a-web-server-for-linux.md#launching-the-web-server-and-testing-the-configuration)
   * Für Windows: [Webserver starten und Konfiguration testen](../../installation/using/integration-into-a-web-server-for-windows.md#launching-the-web-server-and-testing-the-configuration)

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

1. Testen Sie das **nlserver web**-Modul mit der URL: https://console.campaign.net/nl/jsp/logon.jsp

   Diese URL ermöglicht den Zugriff auf die Download-Seite für das Client-Setup-Programm.

   Geben Sie den **internen** Login und das zugehörige Passwort ein, wenn Sie die Zugangssteuerungsseite erreichen. [Weitere Informationen](../../installation/using/client-console-availability-for-windows.md).

   ![](assets/s_ncs_install_access_client.png)

1. Starten Sie die Adobe Campaign-Client-Konsole (von der vorherigen Download-Seite aus oder starten Sie sie für eine Windows-Installation direkt auf dem Server), setzen Sie die Server-Verbindungs-URL auf https://console.campaign.net und stellen Sie mithilfe der **Internal**-Anmeldung eine Verbindung her.

   Siehe [diese Seite](../../installation/using/creating-an-instance-and-logging-on.md) und [diesen Abschnitt](../../installation/using/configuring-campaign-server.md#internal-identifier).

   Der Assistent zur Datenbankerstellung wird angezeigt, wenn Sie sich zum ersten Mal anmelden:

   ![](assets/s_ncs_install_db_oracle_creation01.png)

   Führen Sie die Schritte im Assistenten aus und erstellen Sie die mit der Verbindungsinstanz verknüpfte Datenbank.

   Weitere Informationen hierzu finden Sie unter [ und Konfiguration der Datenbank](../../installation/using/creating-and-configuring-the-database.md).

   Melden Sie sich nach der Erstellung der Datenbank ab.

1. Melden Sie sich über die Option **admin** ohne Kennwort wieder bei der Client-Konsole an und starten Sie den Bereitstellungsassistenten (Menü **[!UICONTROL Tools > Erweitert]**), um die Konfiguration der Instanz abzuschließen.

   Weitere Informationen hierzu finden Sie unter &quot;[ einer Instanz](../../installation/using/deploying-an-instance.md).

   Die wichtigsten festzulegenden Parameter sind:

   * E-Mail-Versand: Absender- und Antwortadressen sowie das Fehlerpostfach für Bounce Messages.
   * Tracking: Füllen Sie die für die Weiterleitung verwendete externe URL und die interne URL aus, klicken Sie auf **Registrierung auf den/den Tracking-Servern** und validieren Sie sie dann auf der **Demo**-Instanz des Tracking-Servers.

     Weitere Informationen hierzu finden Sie unter [Tracking-Konfiguration](../../installation/using/deploying-an-instance.md#tracking-configuration).

     ![](assets/s_ncs_install_deployment_wiz_09.png)

     Da der Adobe Campaign-Server sowohl als Anwendungs- als auch als Weiterleitungsserver verwendet wird, stellt die interne URL zur Erfassung von Trackinglogs und zur Übertragung von URLs eine direkte interne Verbindung zu Tomcat (https://localhost:8080) dar.

   * Bounce-Management: Geben Sie die Parameter für die Handhabung von Bounce Messages ein (berücksichtigen Sie nicht **Abschnitt** Unverarbeitete Bounce Messages).
   * Zugriff von: Geben Sie die beiden URLs für Berichte an: Web-Formulare und Mirrorseiten.

     ![](assets/d_ncs_install_web_url.png)
