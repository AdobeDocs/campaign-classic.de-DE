---
solution: Campaign Classic
product: campaign
title: Hosting-Modelle
description: Hosting-Modelle für Discover-Kampagnen
audience: installation
content-type: reference
topic-tags: architecture-and-hosting-models
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 1%

---


# Hosting-Modelle{#hosting-models}

Adobe Campaign Angebots verfügt über drei Hostingmodelle, die Flexibilität bieten und frei wählen können, welches Modell am besten geeignet ist, oder Modelle, die auf Geschäftsanforderungen zugeschnitten sind.

>[!NOTE]
>
>Bei Adobe gehosteten Umgebung können Hauptinstallations- und Konfigurationsschritte nur durch Adobe ausgeführt werden, z. B. durch Konfiguration des Servers und Anpassen der Instanzkonfigurationsdateien. Weitere Informationen zu den Hauptunterschieden zwischen den Bereitstellungsmodi finden Sie auf [dieser Seite](../../installation/using/capability-matrix.md).

* **Managed Services (gehostet)**

   Adobe Campaign kann als verwalteter Dienst bereitgestellt werden: Alle Komponenten von Adobe Campaign, einschließlich der Benutzeroberfläche, der Ausführungsmanagement-Engine und der Kundendatenbank, werden vollständig per Adobe gehostet, einschließlich E-Mail-Ausführung, Mirrorseiten, Tracking-Server und extern ausgerichteten Webkomponenten, wie z. B. das Abmelden von Seiten-/Voreinstellungscenter und Landingpages. Adobe weist bis zu drei Instanzen in der Cloud zu: Entwicklung, Test/Phase und Produktion. Die Installations- und Konfigurationsschritte für dieses Hostmodell werden [in diesem Abschnitt](../../installation/using/hosted-model.md)beschrieben.

   ![](assets/deployment_hosted.png)

* **On-Premise**

   Adobe Campaign kann vor Ort bereitgestellt werden: alle Komponenten von Adobe Campaign, einschließlich der Benutzeroberfläche, der Ausführungsmanagement-Engine und der Datenbank, befinden sich im Rechenzentrum des Kunden. In diesem Bereitstellungsmodell verwaltet der Kunde alle Software- und Hardwareaktualisierungen und -aktualisierungen. Ein dedizierter Datenbankadministrator muss Aufgaben zur Wartung und Optimierung durchführen, um die Kampagne-Instanzverwaltung sicherzustellen. In [diesem Abschnitt](../../installation/using/before-starting.md)werden Bereitstellungsrichtlinien für lokale Kunden vorgestellt.

   ![](assets/deployment_onpremise.png)

* **Hybrid**

   Bei der Bereitstellung als Hybridmodell befindet sich die Adobe Campaign-Lösungssoftware vor Ort am Kundenstandort und die Ausführungsverwaltung wird als Cloud-Service per Adobe bereitgestellt. Die Adobe Campaign-Marketinginstanz wird innerhalb der Firewall eines Kunden installiert, sodass persönliche identifizierbare Informationen (PII) intern bleiben und nur Daten, die zur Personalisierung von E-Mails erforderlich sind, zur E-Mail-Ausführung an die Cloud gesendet werden. Die in der Cloud gehostete Ausführungsinstanz empfängt die Anfragen der On-Premise-Instanz zum Senden von E-Mails. Diese Instanz personalisiert alle E-Mails und gibt sie aus. In der Cloud werden keine Daten jeglicher Art dauerhaft gespeichert. Die Installations- und Konfigurationsschritte für dieses Hostmodell werden [in diesem Abschnitt](../../installation/using/hybrid-model.md)beschrieben.

   ![](assets/deployment_hybrid.png)

