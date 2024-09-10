---
product: campaign
title: Standardbereitstellung
description: Standardbereitstellung
feature: Installation, Architecture, Deployment
audience: installation
content-type: reference
topic-tags: deployment-types-
exl-id: 4df126fa-4a6e-46a7-af6e-1e2e97f0072e
source-git-commit: 0fba6a2ad4ffa864e2f726f241aa9d7cd39072a6
workflow-type: tm+mt
source-wordcount: '836'
ht-degree: 6%

---

# Standardbereitstellung{#standard-deployment}



Für diese Konfiguration sind drei Computer erforderlich:

* einen Anwendungsserver im LAN für die Endbenutzer (Vorbereitung von Kampagnen, Berichterstellung usw.),
* Zwei Frontserver in der DMZ hinter einem Lastverteiler.

Die beiden Server in der DMZ verarbeiten Tracking, Mirrorseiten und Sendungen und sind für hohe Verfügbarkeit redundant.

Der Anwendungsserver im LAN dient den Endbenutzern und führt alle wiederkehrenden Prozesse (Workflow-Engine) durch. Wenn also Spitzenlasten auf den Frontalservern erreicht werden, sind die Anwender der Anwendung nicht betroffen.

Der Datenbankserver kann auf einem anderen Computer als diesen drei gehostet werden. Andernfalls ist es für den Anwendungsserver und den Datenbankserver erforderlich, denselben Computer innerhalb des LAN freizugeben, solange das Betriebssystem von Adobe Campaign (Linux oder Windows) unterstützt wird.

Die allgemeine Kommunikation zwischen Servern und Prozessen erfolgt gemäß dem folgenden Schema:

![](assets/s_001_ncs_install_standardconfig.png)

Diese Art der Konfiguration kann eine große Anzahl von Empfängern (500.000 bis 1.000.000) verarbeiten, da der Datenbankserver (und die verfügbare Bandbreite) der Hauptbegrenzungsfaktor ist.

## Funktionen {#features}

### Vorteile {#advantages}

* Failover-Funktionalität: die Möglichkeit, Prozesse bei einem Hardwareproblem auf dem anderen Computer zu wechseln.
* Bessere Gesamtleistung, da die MTA- und Umleitungsfunktionen auf beiden Computern hinter einem Lastverteiler bereitgestellt werden können. Mit zwei aktiven MTAs und ausreichend Bandbreite ist es möglich, Übertragungsraten von rund 100.000 E-Mails pro Stunde zu erreichen.

## Installation und Konfiguration {#installation-and-configuration-steps}

### Voraussetzungen {#prerequisites}

* JDK auf allen drei Computern,
* Webserver (IIS, Apache) an beiden Fronten,
* Zugriff auf einen Datenbankserver auf allen drei Computern,
* über POP3 zugängliches Bounce-Postfach,
* Erstellung von zwei DNS-Aliassen:

   * die erste, die der Öffentlichkeit zur Verfolgung und zum Verweis auf den Lastenausgleich an einer virtuellen IP-Adresse (VIP) zur Verfügung gestellt wird und die dann an die beiden Frontalserver verteilt wird,
   * die zweite, die den internen Benutzern für den Zugriff über die Konsole angezeigt wird und auf denselben Anwendungsserver verweist.

* Firewall konfiguriert zum Öffnen von STMP (25), DNS (53), HTTP (80), HTTPS (443), SQL (1521 für Oracle, 5432 für PostgreSQL usw.) Ports. Weitere Informationen finden Sie im Abschnitt [Datenbankzugriff](../../installation/using/network-configuration.md#database-access).

### Anwendungsserver installieren {#installing-the-application-server}

Führen Sie die Schritte aus, um eine eigenständige Instanz vom Adobe Campaign-Anwendungsserver zur Erstellung der Datenbank zu installieren (Schritt 12). Siehe [Installieren und Konfigurieren (einzelner Computer)](../../installation/using/standalone-deployment.md#installing-and-configuring--single-machine-).

Da es sich bei dem Computer nicht um einen Tracking-Server handelt, sollten Sie die Integration mit dem Webserver nicht berücksichtigen.

In den folgenden Beispielen sind die Parameter der Instanz:

* Name der Instanz: **demo**
* DNS-Maske: **console.campaign.net&#42;** (nur für Client-Konsolenverbindungen und für Berichte)
* Sprache: Englisch
* Datenbank: **campaign:demo@dbsrv**

### Installieren der beiden Frontserver {#installing-the-two-frontal-servers}

Die Installation und Konfiguration sind auf beiden Computern identisch.

Zusammenfassend sind folgende Etappen zu durchlaufen:

1. Installieren Sie den Adobe Campaign-Server.

   Weitere Informationen hierzu finden Sie unter [Voraussetzungen für die Campaign-Installation unter Linux](../../installation/using/prerequisites-of-campaign-installation-in-linux.md) (Linux) und [Voraussetzungen für die Campaign-Installation unter Windows](../../installation/using/prerequisites-of-campaign-installation-in-windows.md) (Windows).

1. Befolgen Sie das in den folgenden Abschnitten beschriebene Verfahren zur Webserverintegration (IIS, Apache):

   * Für Linux: [Integration in einen Webserver für Linux](../../installation/using/integration-into-a-web-server-for-linux.md)
   * Für Windows: [Integration in einen Webserver für Windows](../../installation/using/integration-into-a-web-server-for-windows.md)

1. Erstellen Sie die Instanz **demo** . Dazu gibt es zwei Möglichkeiten:

   * Erstellen Sie die Instanz über die Konsole:

     ![](assets/install_create_new_connexion.png)

     Weitere Informationen hierzu finden Sie unter [Erstellen einer Instanz und Anmelden bei](../../installation/using/creating-an-instance-and-logging-on.md).

     oder

   * Erstellen Sie die Instanz mithilfe der Befehlszeilen:

     ```
     nlserver config -addinstance:demo/tracking.campaign.net*
     ```

     Weitere Informationen hierzu finden Sie unter [Instanz erstellen](../../installation/using/command-lines.md#creating-an-instance).

   Der Name der Instanz entspricht dem des Anwendungsservers.

   Die Verbindung zum Server mit dem Modul **nlserver web** (Mirrorseiten, Abmeldung) erfolgt über die URL des Lastenausgleichs (tracking.campaign.net).

1. Ändern Sie die Einstellung für **internal** in die Einstellung des Anwendungsservers.

   Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../installation/using/configuring-campaign-server.md#internal-identifier).

1. Verknüpfen Sie die Datenbank mit der Instanz:

   ```
   nlserver config -setdblogin:PostgreSQL:campaign:demo@dbsrv -instance:demo
   ```

1. Aktivieren Sie in den Dateien **config-default.xml** und **config-demo.xml** die Module **web**, **trackinglogd** und **mta**.

   Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../installation/using/configuring-campaign-server.md#enabling-processes).

1. Bearbeiten Sie die Datei **serverConf.xml** und füllen Sie Folgendes aus:

   * die DNS-Konfiguration des MTA-Moduls:

     ```
     <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
     ```

     >[!NOTE]
     >
     >Der Parameter **nameServers** wird nur in Windows verwendet.

     Weitere Informationen hierzu finden Sie unter [Versandeinstellungen](configure-delivery-settings.md).

   * die redundanten Tracking-Server in Umleitungsparametern:

     ```
     <spareServer enabledIf="$(hostname)!='front_srv1'" id="1" url="https://front_srv1:8080"/>
     <spareServer enabledIf="$(hostname)!='front_srv2'" id="2" url="https://front_srv2:8080"/>
     ```

     Weitere Informationen hierzu finden Sie unter [Redundant tracking](configuring-campaign-server.md#redundant-tracking).

1. Starten Sie die Website und testen Sie die Weiterleitung von der URL: [https://tracking.campaign.net/r/test](https://tracking.campaign.net/r/test).

   Der Browser sollte die folgenden Meldungen anzeigen (je nach URL, die vom Lastenausgleich umgeleitet wird):

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="front_srv1"/>
   ```

   oder

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="front_srv2"/>
   ```

   Weiterführende Informationen hierzu finden Sie in den folgenden Abschnitten:

   * Für Linux: [Starten des Webservers und Testen der Konfiguration](../../installation/using/integration-into-a-web-server-for-linux.md#launching-the-web-server-and-testing-the-configuration)
   * Für Windows: [Starten des Webservers und Testen der Konfiguration](../../installation/using/integration-into-a-web-server-for-windows.md#launching-the-web-server-and-testing-the-configuration)

1. Starten Sie den Adobe Campaign-Server.
1. Verbinden Sie sich in der Adobe Campaign-Konsole mit der Anmeldung **admin** ohne Kennwort und starten Sie den Softwareverteilungs-Assistenten.

   Weitere Informationen hierzu finden Sie unter [Bereitstellen einer Instanz](../../installation/using/deploying-an-instance.md).

   Die Konfiguration ist mit einer eigenständigen Instanz identisch, abgesehen von der Konfiguration des Tracking-Moduls.

1. Füllen Sie die externe URL (die des Lastenausgleichs) für die Umleitung und die internen URLs der beiden Frontalserver.

   Weitere Informationen hierzu finden Sie unter [Tracking-Konfiguration](../../installation/using/deploying-an-instance.md#tracking-configuration).

   ![](assets/d_ncs_install_tracking2.png)

   >[!NOTE]
   >
   >Wir verwenden die vorhandene Instanz der beiden zuvor erstellten Tracking-Server und verwenden die **interne** -Anmeldung.
