---
solution: Campaign Classic
product: campaign
title: Standardbereitstellung
description: Standardbereitstellung
audience: installation
content-type: reference
topic-tags: deployment-types-
exl-id: 4df126fa-4a6e-46a7-af6e-1e2e97f0072e
translation-type: tm+mt
source-git-commit: ae4f86f3703b9bfe7f08fd5c2580dd5da8c28cbd
workflow-type: tm+mt
source-wordcount: '832'
ht-degree: 4%

---

# Standardbereitstellung{#standard-deployment}

Für diese Konfiguration sind drei Computer erforderlich:

* Ein Anwendungsserver im LAN für die Endbenutzer (Vorbereitung von Kampagnen, Berichte usw.),
* Zwei frontale Server in der DMZ hinter einem Lastenausgleich.

Die beiden Server in der DMZ verarbeiten Tracking, Mirrorseiten und Versand und sind für hohe Verfügbarkeit redundant.

Der Anwendungsserver im LAN dient den Endbenutzern und führt alle wiederkehrenden Prozesse (Workflow-Engine) durch. Wenn also Spitzenlasten auf den Frontservern erreicht werden, sind die Anwendungsbenutzer nicht betroffen.

Der Datenbankserver kann auf einem anderen Computer als diesen drei gehostet werden. Andernfalls ist es für den Anwendungsserver und den Datenbankserver erforderlich, denselben Computer im LAN freizugeben, solange das Betriebssystem von Adobe Campaign (Linux oder Windows) unterstützt wird.

Die allgemeine Kommunikation zwischen Servern und Prozessen erfolgt gemäß dem folgenden Schema:

![](assets/s_001_ncs_install_standardconfig.png)

Diese Konfiguration kann eine große Anzahl von Empfängern (500.000 bis 1.000.000) verarbeiten, da der Datenbankserver (und die verfügbare Bandbreite) der Hauptbegrenzungsfaktor ist.

## Funktionen {#features}

### Vorteile {#advantages}

* Failover-Funktion: die Möglichkeit, Prozesse bei Hardwareproblemen auf einem anderen Computer zu wechseln.
* Bessere Gesamtleistung, da die MTA- und Umleitungsfunktionen auf beiden Computern hinter einem Lastenausgleich bereitgestellt werden können. Mit zwei aktiven MTAs und ausreichender Bandbreite ist es möglich, Übertragungsraten von etwa 100.000 Mails pro Stunde zu erreichen.

## Installations- und Konfigurationsschritte {#installation-and-configuration-steps}

### Voraussetzungen {#prerequisites}

* JDK auf allen drei Computern,
* Webserver (IIS, Apache) an beiden Frontalstellen,
* Zugriff auf einen Datenbankserver auf allen drei Computern,
* Absprungkasten, der über POP3 erreichbar ist,
* Erstellung von zwei DNS-Aliasen:

   * die erste öffentlich zugänglich gemacht wird, um den Lastenausgleich zu verfolgen und auf eine virtuelle IP-Adresse (VIP) zu verweisen, und die dann an die beiden Frontserver verteilt wird,
   * die zweite Instanz, die internen Benutzern für den Zugriff über die Konsole zur Verfügung steht und auf denselben Anwendungsserver zeigt.

* Firewall zum Öffnen von STMP (25), DNS (53), HTTP (80), HTTPS (443), SQL (1521 für Oracle, 5432 für PostgreSQL usw.) Ports. Weitere Informationen finden Sie im Abschnitt [Datenbankzugriff](../../installation/using/network-configuration.md#database-access).

### Installieren des Anwendungsservers {#installing-the-application-server}

Führen Sie die Schritte aus, um eine eigenständige Instanz vom Adobe Campaign-Anwendungsserver bis zur Erstellung der Datenbank zu installieren (Schritt 12). Weitere Informationen finden Sie unter [Installation und Konfiguration (Einzelcomputer)](../../installation/using/standalone-deployment.md#installing-and-configuring--single-machine-).

Da der Computer kein Tracking-Server ist, sollten Sie die Integration mit dem Webserver nicht berücksichtigen.

In den folgenden Beispielen sind die Parameter der Instanz:

* Name der Instanz: **demo**
* DNS-Maske: **console.Kampagne.net*** (nur für Client-Konsolenverbindungen und für Berichte)
* Sprache: englisch
* Datenbank: **Kampagne:demo@dbsrv**

### Installieren der beiden Frontserver {#installing-the-two-frontal-servers}

Der Installations- und Konfigurationsvorgang ist auf beiden Computern identisch.

Zusammenfassend sind folgende Etappen zu durchlaufen:

1. Installieren Sie den Adobe Campaign-Server.

   Weitere Informationen hierzu finden Sie unter [Voraussetzungen für die Installation der Kampagne unter Linux](../../installation/using/prerequisites-of-campaign-installation-in-linux.md) (Linux) und [Voraussetzungen für die Installation der Kampagne unter Windows](../../installation/using/prerequisites-of-campaign-installation-in-windows.md) (Windows).

1. Folgen Sie dem Webserver-Integrationsverfahren (IIS, Apache), das in den folgenden Abschnitten beschrieben wird:

   * Für Linux: [Integration in einen Webserver für Linux](../../installation/using/integration-into-a-web-server-for-linux.md)
   * Windows: [Integration in einen Webserver für Windows](../../installation/using/integration-into-a-web-server-for-windows.md)

1. Erstellen Sie die Instanz **demo**. Es gibt zwei Möglichkeiten, dies zu tun:

   * Erstellen Sie die Instanz über die Konsole:

      ![](assets/install_create_new_connexion.png)

      Weitere Informationen finden Sie unter [Erstellen einer Instanz und Anmelden](../../installation/using/creating-an-instance-and-logging-on.md).

      or

   * Erstellen Sie die Instanz mithilfe der Befehlszeilen:

      ```
      nlserver config -addinstance:demo/tracking.campaign.net*
      ```

      Weitere Informationen hierzu finden Sie unter [Erstellen einer Instanz](../../installation/using/command-lines.md#creating-an-instance).
   Der Name der Instanz ist identisch mit dem des Anwendungsservers.

   Die Serververbindung mit dem Modul **nlserver web** (Mirrorseiten, Abmeldung) wird über die URL des Lastenausgleichers (tracking.Kampagne.net) hergestellt.

1. Ändern Sie **internal** in die Einstellung des Anwendungsservers.

   Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../installation/using/configuring-campaign-server.md#internal-identifier).

1. Verknüpfen Sie die Datenbank mit der Instanz:

   ```
   nlserver config -setdblogin:PostgreSQL:campaign:demo@dbsrv -instance:demo
   ```

1. Aktivieren Sie in den Modulen **config-default.xml** und **config-demo.xml** die Module **web**, **trackinglogd** und **mta**.

   Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../installation/using/configuring-campaign-server.md#enabling-processes).

1. Bearbeiten Sie die Datei **serverConf.xml** und füllen Sie Folgendes aus:

   * die DNS-Konfiguration des MTA-Moduls:

      ```
      <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
      ```

      >[!NOTE]
      >
      >Der Parameter **nameServers** wird nur unter Windows verwendet.

      Weitere Informationen finden Sie unter [Versand settings](configure-delivery-settings.md).

   * die redundanten Tracking-Server in den Umleitungsparametern:

      ```
      <spareServer enabledIf="$(hostname)!='front_srv1'" id="1" url="https://front_srv1:8080"/>
      <spareServer enabledIf="$(hostname)!='front_srv2'" id="2" url="https://front_srv2:8080"/>
      ```

      Weitere Informationen finden Sie unter [Redundante Verfolgung](configuring-campaign-server.md#redundant-tracking).

1. Beginn der Website und Testen der Umleitung von der URL: [https://tracking.campaign.net/r/test](https://tracking.campaign.net/r/test).

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

1. Beginn des Adobe Campaign-Servers.
1. Stellen Sie in der Adobe Campaign-Konsole eine Verbindung mit der Anmeldung **admin** ohne Kennwort her und starten Sie den Bereitstellungsassistenten.

   Weitere Informationen finden Sie unter [Bereitstellen einer Instanz](../../installation/using/deploying-an-instance.md).

   Die Konfiguration ist mit einer eigenständigen Instanz identisch, abgesehen von der Konfiguration des Verfolgungsmoduls.

1. Füllen Sie die externe URL (die des Lastenausgleichs) für die Umleitung und die internen URLs der beiden Frontserver.

   Weitere Informationen finden Sie unter [Tracking-Konfiguration](../../installation/using/deploying-an-instance.md#tracking-configuration).

   ![](assets/d_ncs_install_tracking2.png)

   >[!NOTE]
   >
   >Wir verwenden die vorhandene Instanz der beiden zuvor erstellten Tracking-Server und verwenden die Anmeldung **internal**.
