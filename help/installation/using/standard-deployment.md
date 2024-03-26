---
product: campaign
title: Standardbereitstellung
description: Standardbereitstellung
feature: Installation, Architecture, Deployment
badge-v7-only: label="v7" type="Informative" tooltip="Gilt nur für Campaign Classic v7"
audience: installation
content-type: reference
topic-tags: deployment-types-
exl-id: 4df126fa-4a6e-46a7-af6e-1e2e97f0072e
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '843'
ht-degree: 7%

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

Führen Sie die Schritte aus, um eine eigenständige Instanz vom Adobe Campaign-Anwendungsserver zur Erstellung der Datenbank zu installieren (Schritt 12). Siehe Abschnitt [Installation und Konfiguration (ein Computer)](../../installation/using/standalone-deployment.md#installing-and-configuring--single-machine-).

Da es sich bei dem Computer nicht um einen Tracking-Server handelt, sollten Sie die Integration mit dem Webserver nicht berücksichtigen.

In den folgenden Beispielen sind die Parameter der Instanz:

* Name der Instanz: **Demo**
* DNS-Maske: **console.campaign.net&#42;** (nur für Client-Konsolenverbindungen und für Berichte)
* Sprache: Englisch
* Datenbank: **campaign:demo@dbsrv**

### Installieren der beiden Frontserver {#installing-the-two-frontal-servers}

Die Installation und Konfiguration sind auf beiden Computern identisch.

Zusammenfassend sind folgende Etappen zu durchlaufen:

1. Installieren Sie den Adobe Campaign-Server.

   Weitere Informationen hierzu finden Sie unter [Voraussetzungen für die Installation von Campaign unter Linux](../../installation/using/prerequisites-of-campaign-installation-in-linux.md) (Linux) und [Voraussetzungen für die Installation von Campaign unter Windows](../../installation/using/prerequisites-of-campaign-installation-in-windows.md) (Windows).

1. Befolgen Sie das in den folgenden Abschnitten beschriebene Verfahren zur Webserverintegration (IIS, Apache):

   * Für Linux: [Integration in einen Webserver für Linux](../../installation/using/integration-into-a-web-server-for-linux.md)
   * Windows: [Integration in einen Webserver für Windows](../../installation/using/integration-into-a-web-server-for-windows.md)

1. Erstellen Sie die **Demo** -Instanz. Dazu gibt es zwei Möglichkeiten:

   * Erstellen Sie die Instanz über die Konsole:

     ![](assets/install_create_new_connexion.png)

     Weitere Informationen hierzu finden Sie unter [Erstellen einer Instanz und Anmelden](../../installation/using/creating-an-instance-and-logging-on.md).

     oder

   * Erstellen Sie die Instanz mithilfe der Befehlszeilen:

     ```
     nlserver config -addinstance:demo/tracking.campaign.net*
     ```

     Weitere Informationen hierzu finden Sie unter [Erstellen einer Instanz](../../installation/using/command-lines.md#creating-an-instance).

   Der Name der Instanz entspricht dem des Anwendungsservers.

   Die Verbindung zum Server mit der **nlserver web** -Modul (Mirrorseiten, Abmeldung) wird über die URL des Lastenausgleichs (tracking.campaign.net) durchgeführt.

1. Ändern Sie die **intern** auf denselben wie der Anwendungsserver.

   Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../installation/using/configuring-campaign-server.md#internal-identifier).

1. Verknüpfen Sie die Datenbank mit der Instanz:

   ```
   nlserver config -setdblogin:PostgreSQL:campaign:demo@dbsrv -instance:demo
   ```

1. Im **config-default.xml** und **config-demo.xml** -Dateien, aktivieren Sie die **Web**, **trackinglogd** und **mta** Module.

   Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../installation/using/configuring-campaign-server.md#enabling-processes).

1. Bearbeiten Sie die **serverConf.xml** Datei und füllen Sie:

   * die DNS-Konfiguration des MTA-Moduls:

     ```
     <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
     ```

     >[!NOTE]
     >
     >Die **nameServers** wird nur unter Windows verwendet.

     Weitere Informationen hierzu finden Sie unter [Versandeinstellungen](configure-delivery-settings.md).

   * die redundanten Tracking-Server in Umleitungsparametern:

     ```
     <spareServer enabledIf="$(hostname)!='front_srv1'" id="1" url="https://front_srv1:8080"/>
     <spareServer enabledIf="$(hostname)!='front_srv2'" id="2" url="https://front_srv2:8080"/>
     ```

     Weitere Informationen hierzu finden Sie unter [Redundantes Tracking](configuring-campaign-server.md#redundant-tracking).

1. Starten Sie die Website und testen Sie die Weiterleitung über die URL: [https://tracking.campaign.net/r/test](https://tracking.campaign.net/r/test).

   Der Browser sollte die folgenden Meldungen anzeigen (je nach URL, die vom Lastenausgleich umgeleitet wird):

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="front_srv1"/>
   ```

   oder

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="front_srv2"/>
   ```

   Weiterführende Informationen hierzu finden Sie in den folgenden Abschnitten:

   * Für Linux: [Webserver starten und Konfiguration testen](../../installation/using/integration-into-a-web-server-for-linux.md#launching-the-web-server-and-testing-the-configuration)
   * Windows: [Webserver starten und Konfiguration testen](../../installation/using/integration-into-a-web-server-for-windows.md#launching-the-web-server-and-testing-the-configuration)

1. Starten Sie den Adobe Campaign-Server.
1. Stellen Sie in der Adobe Campaign-Konsole mithilfe der **admin** ohne Kennwort anmelden und den Softwareverteilungs-Assistenten starten.

   Weitere Informationen hierzu finden Sie unter [Bereitstellen einer Instanz](../../installation/using/deploying-an-instance.md).

   Die Konfiguration ist mit einer eigenständigen Instanz identisch, abgesehen von der Konfiguration des Tracking-Moduls.

1. Füllen Sie die externe URL (die des Lastenausgleichs) für die Umleitung und die internen URLs der beiden Frontalserver.

   Weitere Informationen hierzu finden Sie unter [Tracking-Konfiguration](../../installation/using/deploying-an-instance.md#tracking-configuration).

   ![](assets/d_ncs_install_tracking2.png)

   >[!NOTE]
   >
   >Wir verwenden die vorhandene Instanz der beiden zuvor erstellten Tracking-Server und verwenden die **intern** anmelden.
