---
title: Hosting-Modelle
seo-title: Hosting-Modelle
description: Hosting-Modelle
seo-description: null
page-status-flag: never-activated
uuid: a9e035d9-326b-4e14-8f05-a22fe38d172b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: architecture-and-hosting-models
discoiquuid: 3175b9ab-e305-4f19-8267-d6172fa07a2a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 46f5bfb41bfe9c938ac0ffa767ead3e47a32047d

---


# Hosting-Modelle{#hosting-models}

Adobe Campaign bietet eine Auswahl von drei Hostingmodellen, die Flexibilität und Freiheit bieten, das beste Modell oder Modell für Geschäftsanforderungen auszuwählen.

>[!NOTE]
>
>Hauptinstallations- und Konfigurationsschritte können nur von Adobe für Bereitstellungen ausgeführt werden, die von Adobe gehostet werden. Zum Konfigurieren der Server- und Instanzkonfigurationsdateien. Weitere Informationen zu den Hauptunterschieden zwischen den Bereitstellungsmodi finden Sie in [diesem Artikel](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html). Wenn Sie über ein gehostetes oder hybrides Modell verfügen, lesen Sie bitte diesen [Abschnitt](../../installation/using/about-hybrid-and-hosted-models.md).

* **Managed Services (gehostet)**

   Adobe Campaign kann als verwalteter Dienst bereitgestellt werden: Alle Komponenten von Adobe Campaign, einschließlich der Benutzeroberfläche, der Ausführungsmanagement-Engine und der Kampagnendatenbank des Kunden, werden vollständig von Adobe gehostet, einschließlich E-Mail-Ausführung, Spiegelseiten, Tracking-Server und extern ausgerichteten Webkomponenten wie Abmelden von Seiten/Voreinstellungscenter und Einstiegsseiten. Adobe weist in der Cloud bis zu drei Instanzen zu: Entwicklung, Test/Phase und Produktion. Die Installations- und Konfigurationsschritte für dieses Hostmodell werden in diesem [Abschnitt](../../installation/using/hosted-model.md)beschrieben.

   ![](assets/deployment_hosted.png)

* **Vor-Ort**

   Adobe Campaign kann lokal bereitgestellt werden: Alle Komponenten von Adobe Campaign, einschließlich der Benutzeroberfläche, der Ausführungsverwaltungsmaschine und der Datenbank, befinden sich im Rechenzentrum des Kunden. In diesem Bereitstellungsmodell verwaltet der Kunde alle Software- und Hardwareaktualisierungen und -aktualisierungen. Ein dedizierter Datenbankadministrator muss Wartungs- und Optimierungsaufgaben ausführen, um die Verwaltung der Kampagneninstanzen sicherzustellen.

   ![](assets/deployment_onpremise.png)

* **Hybrid**

   Bei der Bereitstellung als Hybridmodell befindet sich die Adobe Campaign-Lösungssoftware lokal auf der Kundensite und die Ausführungsverwaltung wird als Cloud-Service von Adobe bereitgestellt. Die Marketing-Instanz von Adobe Campaign wird innerhalb der Firewall eines Kunden installiert, sodass persönliche identifizierbare Informationen (PII) intern bleiben und nur Daten, die zur Personalisierung von E-Mails erforderlich sind, zur E-Mail-Ausführung an die Cloud gesendet werden. Die in der Cloud gehostete Ausführungsinstanz empfängt die Anfragen von der On-Premise-Instanz zum Senden von E-Mails. Diese Instanz personalisiert alle E-Mails und gibt sie aus. In der Cloud werden keine Daten jeglicher Art dauerhaft gespeichert. Die Installations- und Konfigurationsschritte für dieses Hostmodell werden in diesem [Abschnitt](../../installation/using/hybrid-model.md)beschrieben.

   ![](assets/deployment_hybrid.png)

