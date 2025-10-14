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

* einen Anwendungs-Server innerhalb des LAN für die Endbenutzer (Vorbereitung von Kampagnen, Reporting usw.),
* Zwei Frontserver in der DMZ hinter einem Load-Balancer.

Die beiden Server in der DMZ verwalten Tracking, Mirror-Seiten und Versand und sind für hohe Verfügbarkeit redundant.

Der Anwendungs-Server im LAN bedient die Endbenutzer und führt alle wiederkehrenden Prozesse (Workflow-Engine) aus. Wenn also Spitzenlasten auf den Frontservern erreicht werden, sind die Programmbenutzer nicht betroffen.

Der Datenbankserver kann auf einem anderen Computer als diesen drei gehostet werden. Andernfalls müssen Anwendungs- und Datenbankserver denselben Computer im LAN gemeinsam nutzen, solange das Betriebssystem von Adobe Campaign (Linux oder Windows) unterstützt wird.

Die allgemeine Kommunikation zwischen Servern und Prozessen erfolgt gemäß dem folgenden Schema:

![](assets/s_001_ncs_install_standardconfig.png)

Diese Art der Konfiguration kann eine große Anzahl von Empfängern (500.000 bis 1.000.000) verarbeiten, da der Datenbank-Server (und die verfügbare Bandbreite) der wichtigste Begrenzungsfaktor sind.

## Funktionen {#features}

### Vorteile {#advantages}

* Failover-Funktionalität: die Möglichkeit, Prozesse auf einen Computer umzustellen, wenn auf dem anderen Computer ein Hardwareproblem auftritt.
* Bessere Gesamtleistung, da die MTA- und Umleitungsfunktionen auf beiden Computern hinter einem Lastenausgleich bereitgestellt werden können. Mit zwei aktiven MTAs und ausreichender Bandbreite lassen sich Übertragungsraten im Bereich von 100.000 Mails pro Stunde erreichen.

## Installations- und Konfigurationsschritte {#installation-and-configuration-steps}

### Voraussetzungen {#prerequisites}

* JDK auf allen drei Computern,
* Webserver (IIS, Apache) auf beiden Fronten,
* Zugriff auf einen Datenbank-Server auf allen drei Computern,
* Bounce-Postfach über POP3 zugänglich,
* Erstellung von zwei DNS-Aliassen:

   * die erste öffentlich zugängliche, zur Verfolgung und zum Verweisen auf den Lastenausgleich über eine virtuelle IP-Adresse (VIP), die dann an die beiden Frontserver verteilt wird,
   * Die zweite wird den internen Benutzern für den Zugriff über die Konsole bereitgestellt und verweist auf denselben Anwendungsserver.

* Firewall konfiguriert, um STMP (25)-, DNS (53)-, HTTP (80)-, HTTPS (443)-, SQL (1521 für Oracle, 5432 für PostgreSQL usw.)-Ports zu öffnen. Weitere Informationen finden Sie im Abschnitt [Datenbankzugriff](../../installation/using/network-configuration.md#database-access).

### Installieren des Anwendungsservers {#installing-the-application-server}

Führen Sie die Schritte aus, um eine eigenständige Instanz vom Adobe Campaign-Anwendungsserver zur Datenbankerstellung zu installieren (Schritt 12). Siehe [Installieren und Konfigurieren (ein Computer)](../../installation/using/standalone-deployment.md#installing-and-configuring--single-machine-).

Da der Computer kein Trackingserver ist, berücksichtigen Sie nicht die Integration mit dem Webserver.

In den folgenden Beispielen sind die Parameter der -Instanz:

* Name der Instanz: **demo**
* DNS-Maske: **console.campaign.net&#42;** (nur für Client-Konsolenverbindungen und für Berichte)
* Sprache: Englisch
* Datenbank: **campaign:demo@dbsrv**

### Installation der beiden Frontserver {#installing-the-two-frontal-servers}

Der Installations- und Konfigurationsvorgang ist auf beiden Computern identisch.

Zusammenfassend sind folgende Etappen zu durchlaufen:

1. Installieren Sie den Adobe Campaign-Server.

   Weitere Informationen hierzu finden Sie unter [Voraussetzungen für die Campaign-Installation unter Linux](../../installation/using/prerequisites-of-campaign-installation-in-linux.md) (Linux) und [Voraussetzungen für die Campaign-Installation unter Windows](../../installation/using/prerequisites-of-campaign-installation-in-windows.md) (Windows).

1. Befolgen Sie das in den folgenden Abschnitten beschriebene Verfahren zur Webserver-Integration (IIS, Apache):

   * Für Linux: [Integration in einen Webserver für Linux](../../installation/using/integration-into-a-web-server-for-linux.md)
   * Für Windows: [Integration in einen Webserver für Windows](../../installation/using/integration-into-a-web-server-for-windows.md)

1. Erstellen Sie die **Demo**-Instanz. Dazu gibt es zwei Möglichkeiten:

   * Erstellen Sie die Instanz über die Konsole:

     ![](assets/install_create_new_connexion.png)

     Weitere Informationen hierzu finden Sie unter [Instanz erstellen und anmelden](../../installation/using/creating-an-instance-and-logging-on.md).

     oder

   * Erstellen Sie die Instanz mithilfe von Befehlszeilen:

     ```
     nlserver config -addinstance:demo/tracking.campaign.net*
     ```

     Weitere Informationen hierzu finden Sie unter [Instanz erstellen](../../installation/using/command-lines.md#creating-an-instance).

   Der Name der Instanz entspricht dem Namen des Anwendungsservers.

   Die Verbindung zum Server mit dem **nlserver web**-Modul (Mirrorseiten, Abmeldung) erfolgt über die URL des Lastenausgleichs (tracking.campaign.net).

1. Ändern Sie **Intern** auf denselben Wert wie der Anwendungs-Server.

   Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../installation/using/configuring-campaign-server.md#internal-identifier).

1. Verknüpfen der Datenbank mit der Instanz:

   ```
   nlserver config -setdblogin:PostgreSQL:campaign:demo@dbsrv -instance:demo
   ```

1. Aktivieren Sie in den **config-default.xml** und **config-demo.xml** die **web**, **trackinglogd** und **mta**-Module.

   Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../installation/using/configuring-campaign-server.md#enabling-processes).

1. Bearbeiten Sie die Datei **serverConf.xml** und füllen Sie:

   * DNS-Konfiguration des MTA-Moduls:

     ```
     <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
     ```

     >[!NOTE]
     >
     >Der **nameServers**-Parameter wird nur unter Windows verwendet.

     Weitere Informationen hierzu finden Sie unter [Versandeinstellungen](configure-delivery-settings.md).

   * Die redundanten Tracking-Server in den Weiterleitungsparametern:

     ```
     <spareServer enabledIf="$(hostname)!='front_srv1'" id="1" url="https://front_srv1:8080"/>
     <spareServer enabledIf="$(hostname)!='front_srv2'" id="2" url="https://front_srv2:8080"/>
     ```

     Weitere Informationen hierzu finden Sie unter [Redundantes Tracking](configuring-campaign-server.md#redundant-tracking).

1. Starten Sie die Website und testen Sie die Umleitung über die URL: [https://tracking.campaign.net/r/test](https://tracking.campaign.net/r/test).

   Der Browser sollte die folgenden Meldungen anzeigen (abhängig von der URL, die vom Load-Balancer umgeleitet wird):

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="front_srv1"/>
   ```

   oder

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="front_srv2"/>
   ```

   Weiterführende Informationen hierzu finden Sie in den folgenden Abschnitten:

   * Für Linux: [Webserver starten und Konfiguration testen](../../installation/using/integration-into-a-web-server-for-linux.md#launching-the-web-server-and-testing-the-configuration)
   * Für Windows: [Webserver starten und Konfiguration testen](../../installation/using/integration-into-a-web-server-for-windows.md#launching-the-web-server-and-testing-the-configuration)

1. Adobe Campaign-Server starten.
1. Stellen Sie in der Adobe Campaign-Konsole eine Verbindung mit dem **admin** her, melden Sie sich ohne Kennwort an und starten Sie den Bereitstellungsassistenten.

   Weitere Informationen hierzu finden Sie unter &quot;[&#x200B; einer Instanz](../../installation/using/deploying-an-instance.md).

   Die Konfiguration ist mit der Konfiguration einer eigenständigen Instanz identisch, abgesehen von der Konfiguration des Tracking-Moduls.

1. Füllen Sie die externe URL (die des Lastenausgleichs) für die Umleitung und die internen URLs der beiden Frontserver.

   Weitere Informationen hierzu finden Sie unter [Tracking-Konfiguration](../../installation/using/deploying-an-instance.md#tracking-configuration).

   ![](assets/d_ncs_install_tracking2.png)

   >[!NOTE]
   >
   >Wir verwenden die vorhandene Instanz der beiden zuvor erstellten Tracking-Server und verwenden die **interne** Anmeldung.
