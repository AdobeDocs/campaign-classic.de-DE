---
solution: Campaign Classic
product: campaign
title: Hosting-Modelle
description: Hosting-Modelle für Discover-Kampagnen
feature: Overview
role: Architect
level: Beginner
translation-type: tm+mt
source-git-commit: 09bd634142f643206c38ac5f881302a5d489ecaf
workflow-type: tm+mt
source-wordcount: '626'
ht-degree: 3%

---


# Hosting-Modelle{#hosting-models}

Adobe Campaign Angebots verfügt über drei Hostingmodelle, die Flexibilität bieten und frei wählen können, welches Modell am besten geeignet ist, oder Modelle, die auf Geschäftsanforderungen zugeschnitten sind.

>[!NOTE]
>
>Bei Adobe gehosteten Umgebung können Hauptinstallations- und Konfigurationsschritte nur durch Adobe ausgeführt werden, z. B. durch Konfiguration des Servers und Anpassen der Instanzkonfigurationsdateien. Weitere Informationen zu den Hauptunterschieden zwischen den Bereitstellungsmodi finden Sie auf [dieser Seite](../../installation/using/capability-matrix.md).

## Managed Services/Hosted

Adobe Campaign kann als verwalteter Dienst bereitgestellt werden: Alle Komponenten von Adobe Campaign, einschließlich der Benutzeroberfläche, der Ausführungsmanagement-Engine und der Kundendatenbank, werden vollständig per Adobe gehostet, einschließlich E-Mail-Ausführung, Mirrorseiten, Tracking-Server und extern ausgerichteten Webkomponenten, wie z. B. das Abmelden von Seiten-/Voreinstellungscenter und Landingpages.

![](assets/deployment_hosted.png)

Als gehosteter Kunde werden die meisten Installations- und Konfigurationsschritte von der Adobe ausgeführt. Sie können auf die folgenden Abschnitte zugreifen, um Ihre Implementierung anzupassen:

* Konfigurieren Sie die Tracking- und Mirrorseite-URLs pro Marke. Transaktionsnachrichten finden Sie in [diesem Abschnitt](../../message-center/using/configuring-multibranding.md).
* Installieren Sie die Client-Konsole: verweisen Sie auf [diesen Abschnitt](../../installation/using/installing-the-client-console.md).
* Weitere Informationen zu den Werkzeugen und Best Practices für die Bereitstellung finden Sie in der [detaillierten Dokumentation](../../delivery/using/about-deliverability.md).
* Optionen für die Kampagne konfigurieren: verweisen Sie auf [diesen Abschnitt](../../installation/using/configuring-campaign-options.md).
* CRM-Connectors konfigurieren: verweisen Sie auf [diesen Abschnitt](../../platform/using/crm-connectors.md).

## On-Premise

Adobe Campaign kann vor Ort bereitgestellt werden: alle Komponenten von Adobe Campaign, einschließlich der Benutzeroberfläche, der Ausführungsmanagement-Engine und der Datenbank, befinden sich im Rechenzentrum des Kunden. In diesem Bereitstellungsmodell verwaltet der Kunde alle Software- und Hardwareaktualisierungen und -aktualisierungen. Ein dedizierter Datenbankadministrator muss Aufgaben zur Wartung und Optimierung durchführen, um die Kampagne-Instanzverwaltung sicherzustellen.

![](assets/deployment_onpremise.png)

Vor der Bereitstellung von Campaign Classic müssen Sie als lokaler Kunde folgende Voraussetzungen und Empfehlungen erfüllen:

* Lesen Sie die [Kompatibilitätsmatrix](../../rn/using/compatibility-matrix.md), die alle Listen der zum Adobe Campaign unterstützten Systeme und Komponenten enthält.
* Lesen Sie je nach Umgebung die [Voraussetzungen für Windows](../../installation/using/prerequisites-of-campaign-installation-in-windows.md) und [Voraussetzungen für Linux](../../installation/using/prerequisites-of-campaign-installation-in-linux.md) durch.
* Erfahren Sie mehr über Empfehlungen zu Datenbankmaschinen [in diesem Abschnitt](../../installation/using/database.md).
* Überprüfen Sie, ob die erforderlichen Datenbankzugriffsebenen auf dem Server installiert sind und über das Adobe Campaign-Konto darauf zugegriffen werden kann. [Weitere Informationen](../../installation/using/application-server.md).
* Konfigurieren Sie Ihre Netzwerke, da einige Prozesse mit anderen kommunizieren oder auf LAN und Internet zugreifen müssen. Dies bedeutet, dass einige TCP-Ports für diese Prozesse geöffnet sein müssen. [Erfahren Sie ](../../installation/using/network-configuration.md) mehr über die Konfigurationsanforderungen für das Netzwerk.
* Lesen Sie die [Checkliste für die Sicherheit und den Datenschutz der Kampagne](https://helpx.adobe.com/de/campaign/kb/acc-security.html).
* Lesen Sie die allgemeinen Richtlinien zur Schätzung der Hardwareanforderungen für die lokale Bereitstellung [in diesem Artikel](https://helpx.adobe.com/de/campaign/kb/hardware-sizing-guide.html).

## Hybrid

Bei der Bereitstellung als Hybridmodell befindet sich die Adobe Campaign-Lösungssoftware vor Ort am Kundenstandort und die Ausführungsverwaltung wird als Cloud-Service per Adobe bereitgestellt. Die Adobe Campaign-Marketinginstanz wird innerhalb der Firewall eines Kunden installiert, sodass persönliche identifizierbare Informationen (PII) intern bleiben und nur Daten, die zur Personalisierung von E-Mails erforderlich sind, zur E-Mail-Ausführung an die Cloud gesendet werden. Die in der Cloud gehostete Ausführungsinstanz empfängt die Anfragen der On-Premise-Instanz zum Senden von E-Mails. Diese Instanz personalisiert alle E-Mails und gibt sie aus. In der Cloud werden keine Daten jeglicher Art dauerhaft gespeichert.

![](assets/deployment_hybrid.png)

Als Hybridkunde werden die meisten Installations- und Konfigurationsschritte von der Adobe ausgeführt. Sie können auf die folgenden Abschnitte zugreifen, um Ihre Implementierung anzupassen:

* Transaktionsnachrichten konfigurieren: verweisen Sie auf [diesen Abschnitt](../../message-center/using/transactional-messaging-architecture.md).
* Konfigurieren Sie die Tracking- und Mirrorseite-URLs pro Marke. Transaktionsnachrichten finden Sie in [diesem Abschnitt](../../message-center/using/configuring-multibranding.md).
* Installieren Sie die Client-Konsole: verweisen Sie auf [diesen Abschnitt](../../installation/using/installing-the-client-console.md).
* Integrierte Pakete installieren: verweisen Sie auf [diesen Abschnitt](../../installation/using/installing-campaign-standard-packages.md).
* Lieferbarkeit: configure [MX rules](../../installation/using/email-deliverability.md#mx-configuration) und [E-Mail-Formats](../../installation/using/email-deliverability.md#managing-email-formats). Weitere Informationen zu den Werkzeugen und Best Practices für die Bereitstellung finden Sie in der [detaillierten Dokumentation](../../delivery/using/about-deliverability.md).
* Optionen für die Kampagne konfigurieren: verweisen Sie auf [diesen Abschnitt](../../installation/using/configuring-campaign-options.md).
* Externe Datenbank konfigurieren (Federated Data Access): verweisen Sie auf [diesen Abschnitt](../../installation/using/about-fda.md).
* CRM-Connectors konfigurieren: verweisen Sie auf [diesen Abschnitt](../../platform/using/crm-connectors.md).
* Weitere Informationen zu den Grundsätzen für die Bereitstellung von Mid-Sourcing finden Sie in diesem Abschnitt [.](../../installation/using/mid-sourcing-deployment.md)
