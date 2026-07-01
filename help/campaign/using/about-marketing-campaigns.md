---
product: campaign
title: Über Marketing-Kampagnen
description: Entwerfen, Optimieren, Ausführen und Analysieren von Marketing-Kampagnen
role: User
feature: Campaigns
exl-id: 07cfa2b3-4e70-437a-ad5f-15fbfe717d5c
TQID: https://experienceleague.adobe.com/rxyAXKDrxdMJWdXAwbbkleIoRHf03mvC5sHZbXZ1H5M
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: a075b2c1-7748-4328-b7f6-343aa314616aid: afa4204e-6d08-4e29-bc35-26aafb656d48
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2: id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
subfeature_v2: id: f863efa9-030c-4466-a2b8-a52aea6b722c
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 362
ht-degree: 100%

---

# Orchestrieren von Marketing-Kampagnen{#designing-marketing-campaigns}

Adobe Campaign umfasst mehrere Lösungen, mit denen Sie Kampagnen personalisieren und auf allen Online- und Offline-Kanälen versenden können. Sie können Marketing-Kampagnen erstellen, konfigurieren, ausführen und analysieren. Die Anwendung stellt somit ein einheitliches Kontrollzentrum dar, über das alle Marketing-Kampagnen verwaltet werden können.

Kampagnen umfassen Aktionen (Sendungen) und Prozesse (Import oder Extraktion von Dateien) sowie Ressourcen (Marketing-Dokumente, Versandentwürfe). Sie werden in Marketing-Kampagnen verwendet. Kampagnen sind Teil eines Programms und Programme Teil eines Kampagnenplans.

Weitere Informationen zur Kampagnenverwaltung finden Sie in der [Dokumentation zu Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/campaigns/campaigns.html?lang=de){target=_blank}.

![](assets/do-not-localize/campaign.jpg){width="40%"}

Lernen Sie die wichtigsten Schritte zur Kampagnenverwaltung kennen:

* [Erste Schritte](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/set-up-campaigns.html?lang=de){target=_blank}: Erfahren Sie Schritt für Schritt, wie Sie eine Marketing-Kampagne in Adobe Campaign erstellen und ausführen.

* [Erstellen der ersten Kampagne](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/marketing-campaign-create.html?lang=de){target=_blank}: Erfahren Sie, wie Sie die Logik zur Orchestrierung Ihrer Kampagnen planen und einrichten. In einer Kampagne werden alle Elemente im Zusammenhang mit einer Marketing-Kampagne zusammengefasst: Versand, Zielgruppenbestimmungsregeln, Kosten, Exportdateien, zugehörige Dokumente usw.

* [Senden von Sendungen in Kampagnen](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/marketing-campaign-deliveries.html?lang=de){target=_blank}: Orchestrieren Sie Ihre kanalübergreifenden Sendungen in Ihren Kampagnen: Optimieren Sie mit Adobe Campaign Ihre Kommunikation durch personalisierte E-Mails, SMS, Push-Benachrichtigungen und In-App-Nachrichten.

![](assets/do-not-localize/add-on.jpg){width="40%"}

Für die Kampagnenverwaltung stehen drei Add-ons zur Verfügung:

* [Kampagnenoptimierung](https://experienceleague.adobe.com/docs/campaign/automation/campaign-optimization/campaign-typologies.html?lang=de){target=_blank}: Mit diesem Modul können Sie Sendungen steuern, filtern und überwachen. Auf diese Weise werden ein ideal auf Kundenbedürfnisse abgestimmter Nachrichtenversand sowie eine kohärente Unternehmenskommunikation sichergestellt.

* [Marketing Ressource Management](https://experienceleague.adobe.com/docs/campaign/automation/mrm/about-marketing-resource-management.html?lang=de){target=_blank}: Dieses Modul ermöglicht die Steuerung kollaborativer Marketing-Aktionen durch eine vollständige Verwaltung und Echtzeit-Nachverfolgung von Aufgaben, Budgets und verwendeten Marketing-Ressourcen.

* [Dezentrales Marketing](https://experienceleague.adobe.com/docs/campaign/automation/distributed-marketing/about-distributed-marketing.html?lang=de){target=_blank}: Dieses Modul ermöglicht die Steuerung kollaborativer Marketing-Aktionen durch eine vollständige Verwaltung und Echtzeit-Nachverfolgung von Aufgaben, Budgets und verwendeten Marketing-Ressourcen.

<!--

Adobe Campaign lets you define, optimize, execute and analyze communications and marketing campaigns. Adobe Campaign acts like a unified order and execution center for marketing strategies. For more on this, refer to [Access campaigns](../../distributed/using/accessing-campaigns.md) and [Create marketing campaigns](../../campaign/using/setting-up-marketing-campaigns.md).

In addition, the **Marketing Resource Management (MRM)** module lets you control marketing actions in a collaborative mode by providing complete management and real-time tracking of the tasks, budgets and marketing resources involved. The Marketing Resource Management lets you optimize and regulate the management of internal and external processes, resources and marketing campaigns, as well as third party relations (agencies, printers, etc.). For more on this, refer to [this section](../../mrm/using/about-marketing-resource-management.md).

>[!NOTE]
>
>For more on the Adobe Campaign core functionalities, refer t [this section](../../platform/using/about-adobe-campaign-classic.md) section.  
>Capabilities related to population targeting, message personalization and message delivery on the various channels are detailed in [this section](../../delivery/using/steps-about-delivery-creation-steps.md).

![](assets/do-not-localize/how-to-video.png) [Discover marketing campaigns keys concepts in video](#video)

## Core concepts {#core-concepts}

The following concepts need to be known in the context of Campaign:

* **Campaign**

  A campaign centralizes all the elements related to a marketing campaign: deliveries, targeting rules, costs, export files, related documents, etc. Each campaign is attached to a program.

  For more on this, refer to [Adding a campaign](../../campaign/using/setting-up-marketing-campaigns.md#adding-a-campaign).

* **Program**

  A program lets you define marketing actions for a calendar period: launch, canvassing, loyalty, etc. Each program contains campaigns linked to a calendar, which provides an overall view.

* **Plan**

  The marketing plan can contain multiple programs. It is linked to a calendar period, has an allocated budget and can also be linked up to documents and objectives.

  For more on this, refer to [Campaign calendar](../../campaign/using/accessing-marketing-campaigns.md#campaign-calendar).

* **Workflow**

  A campaign workflow contains the same activities as for all workflows but is specific to the campaign. It enables you to create and configure deliveries for all available channels.

  For more on this, refer to [this section](../../campaign/using/marketing-campaign-deliveries.md#building-the-main-target-in-a-workflow).

* **Objectives**

  Within the campaign, program or plan, you can state a list of objectives. These are quantified values to be reached. At the end of the campaign, program or plan, the MRM module lets you compare the objectives and results in dedicated reports.

* **Delivery outline**

  A delivery outline is a structured description of a delivery. Every delivery can refer to a delivery outline which contains, for example, the related offers, documents to be attached, or a link to stores. An offer can be referenced in the delivery according to the delivery outline selected.

  For more on this, refer to [this section](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline).

## Tutorial {#video}

This video presents the key concepts of marketing campaigns.

>[!VIDEO](https://video.tv.adobe.com/v/35131?quality=12)

Additional Campaign Classic how-to videos are available [here](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html).

-->