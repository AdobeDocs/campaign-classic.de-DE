---
product: campaign
title: Hosting-Modelle
description: Hosting-Modelle von Campaign
feature: Installation, Architecture, Deployment
role: Architect
level: Beginner
exl-id: a06b1365-d487-4df1-8f4a-7268b871a427
source-git-commit: a38d53f4b37aadbc53446b5e399af2eae56c12af
workflow-type: tm+mt
source-wordcount: '615'
ht-degree: 0%

---

# Hosting-Modelle{#hosting-models}



Adobe Campaign bietet drei Hosting-Modelle, die Flexibilität und Freiheit bieten, das beste Modell auszuwählen, oder Modelle, die den Geschäftsanforderungen entsprechen.

>[!NOTE]
>
>Bei Adobe-gehosteten Umgebungen können die Haupt-Installations- und Konfigurationsschritte nur durch Adobe ausgeführt werden, z. B. das Konfigurieren des Servers und das Anpassen der Konfigurationsdateien der Instanz. Weitere Informationen zu den Hauptunterschieden zwischen den Bereitstellungsmodi finden Sie auf [dieser Seite](../../installation/using/capability-matrix.md).

## Managed Services/gehostet

Adobe Campaign kann as a Managed Service bereitgestellt werden: Alle Komponenten von Adobe Campaign, einschließlich Benutzeroberfläche, Ausführungsverwaltungsmodul und Campaign-Datenbank des Kunden, werden vollständig per Adobe gehostet, einschließlich E-Mail-Ausführung, Mirrorseiten, Tracking-Server und extern orientierten Webkomponenten wie Abmelde-Seite/Voreinstellungszentrum und Landingpages.

![](assets/deployment_hosted.png)

Als gehosteter Kunde werden die meisten Installations- und Konfigurationsschritte von Adobe ausgeführt. Sie können auf die folgenden Abschnitte zugreifen, um Ihre Implementierung anzupassen:

* Konfigurieren Sie Tracking- und Mirrorseiten-URLs pro Marke. Transaktionsnachrichten finden Sie in [diesem Abschnitt](../../message-center/using/additional-configurations.md#configuring-multibranding).
* Installieren Sie die Clientkonsole: siehe [diesen Abschnitt](../../installation/using/installing-the-client-console.md).
* Weitere Informationen zu den Zustellbarkeits-Tools und Best Practices finden Sie in der [detaillierten Dokumentation](../../delivery/using/about-deliverability.md).
* Kampagnenoptionen konfigurieren: Siehe [diesen Abschnitt](../../installation/using/configuring-campaign-options.md).
* CRM-Connectoren konfigurieren: siehe [diesen Abschnitt](../../platform/using/crm-connectors.md).

## On-Premise

Adobe Campaign kann vor Ort bereitgestellt werden: Alle Komponenten von Adobe Campaign, einschließlich Benutzeroberfläche, Ausführungsmanagement-Engine und Datenbank, befinden sich im Rechenzentrum des Kunden. In diesem Bereitstellungsmodell verwaltet der Kunde alle Software- und Hardwareaktualisierungen und -aktualisierungen. Ein dedizierter Datenbankadministrator muss Wartungs- und Optimierungsaufgaben durchführen, um die Verwaltung der Campaign-Instanz sicherzustellen.

![](assets/deployment_onpremise.png)

Als On-Premise-Kunde müssen Sie vor der Bereitstellung von Campaign Classic folgende Voraussetzungen und Empfehlungen beachten:

* Lesen Sie die [Kompatibilitätsmatrix](../../rn/using/compatibility-matrix.md) , in der alle Versionen der für Adobe Campaign unterstützten Systeme und Komponenten aufgelistet sind.
* Lesen Sie je nach Umgebung die Voraussetzungen für Windows](../../installation/using/prerequisites-of-campaign-installation-in-windows.md) und [für Linux](../../installation/using/prerequisites-of-campaign-installation-in-linux.md) durch.[
* In diesem Abschnitt ](../../installation/using/database.md) erhalten Sie Empfehlungen zu Datenbankmotoren [.
* Überprüfen Sie, ob die erforderlichen Datenbankzugriffsebenen auf dem Server installiert sind und über das Adobe Campaign-Konto darauf zugegriffen werden kann. [Weitere Informationen](../../installation/using/application-server.md).
* Konfigurieren Sie Ihre Netzwerke, da einige Prozesse mit anderen kommunizieren oder auf LAN und Internet zugreifen müssen. Dies bedeutet, dass einige TCP-Ports für diese Prozesse offen sein müssen. [Erfahren Sie mehr](../../installation/using/network-configuration.md) über die Anforderungen an die Netzwerkkonfiguration.
* Lesen Sie [Checkliste für Sicherheit und Datenschutz in Campaign](https://helpx.adobe.com/de/campaign/kb/acc-security.html).
* Lesen Sie die allgemeinen Richtlinien zur Schätzung der Hardwareanforderungen für die On-Premise-Implementierung [in diesem Artikel](https://helpx.adobe.com/de/campaign/kb/hardware-sizing-guide.html).

## Hybrid

Bei der Bereitstellung als Hybridmodell befindet sich die Adobe Campaign-Lösungssoftware lokal auf der Kundenseite und die Ausführungsverwaltung wird als Cloud-Service von Adobe bereitgestellt. Die Adobe Campaign-Marketinginstanz wird innerhalb der Firewall eines Kunden installiert, sodass personenbezogene Daten (PII) intern aufbewahrt werden und nur Daten zur Personalisierung von E-Mails an die Cloud zur Ausführung von E-Mails gesendet werden. Die in der Cloud gehostete Ausführungsinstanz empfängt die Anfragen von der On-Premise-Instanz zum Versand von E-Mails. Diese Instanz personalisiert alle E-Mails und stellt sie bereit. In der Cloud werden keine Daten jeglicher Art dauerhaft gespeichert.

![](assets/deployment_hybrid.png)

Als Hybrid-Kunde werden die meisten Installations- und Konfigurationsschritte von Adobe ausgeführt. Sie können auf die folgenden Abschnitte zugreifen, um Ihre Implementierung anzupassen:

* Transaktionsnachrichten konfigurieren: siehe [diesen Abschnitt](../../message-center/using/transactional-messaging-architecture.md).
* Konfigurieren Sie Tracking- und Mirrorseiten-URLs pro Marke. Transaktionsnachrichten finden Sie in [diesem Abschnitt](../../message-center/using/additional-configurations.md#configuring-multibranding).
* Installieren Sie die Clientkonsole: siehe [diesen Abschnitt](../../installation/using/installing-the-client-console.md).
* Installieren Sie integrierte Pakete: siehe [diesen Abschnitt](../../installation/using/installing-campaign-standard-packages.md).
* Zustellbarkeit: Konfigurieren Sie die [MX-Regeln](../../installation/using/email-deliverability.md#mx-configuration) und die [E-Mail-Formate](../../installation/using/email-deliverability.md#managing-email-formats). Weitere Informationen zu den Zustellbarkeits-Tools und Best Practices finden Sie in der [detaillierten Dokumentation](../../delivery/using/about-deliverability.md).
* Kampagnenoptionen konfigurieren: Siehe [diesen Abschnitt](../../installation/using/configuring-campaign-options.md).
* Externe Datenbank konfigurieren (Federated Data Access): siehe [diesen Abschnitt](../../installation/using/about-fda.md).
* CRM-Connectoren konfigurieren: siehe [diesen Abschnitt](../../platform/using/crm-connectors.md).
* Weitere Informationen zu Mid-Sourcing-Bereitstellungsgrundsätzen finden Sie in [diesem Abschnitt](../../installation/using/mid-sourcing-deployment.md).
