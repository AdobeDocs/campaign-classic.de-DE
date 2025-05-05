---
product: campaign
title: Über Marketing-Kampagnen
description: Entwerfen, Optimieren, Ausführen und Analysieren von Marketing-Kampagnen
role: User
feature: Campaigns
exl-id: 07cfa2b3-4e70-437a-ad5f-15fbfe717d5c
source-git-commit: dd6bcb16fe41b6a3f1e3f5aaf2f753b29ad4bc1d
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 100%

---

# Orchestrieren von Marketing-Kampagnen{#designing-marketing-campaigns}

Adobe Campaign umfasst mehrere Lösungen, mit denen Sie Kampagnen personalisieren und auf allen Online- und Offline-Kanälen versenden können. Sie können Marketing-Kampagnen erstellen, konfigurieren, ausführen und analysieren. Die Anwendung stellt somit ein einheitliches Kontrollzentrum dar, über das alle Marketing-Kampagnen verwaltet werden können.

Kampagnen umfassen Aktionen (Sendungen) und Prozesse (Import oder Extraktion von Dateien) sowie Ressourcen (Marketing-Dokumente, Versandentwürfe). Sie werden in Marketing-Kampagnen verwendet. Kampagnen sind Teil eines Programms und Programme Teil eines Kampagnenplans.

Weitere Informationen zum Kampagnen-Management finden Sie in der [Dokumentation zu Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/campaigns/campaigns.html?lang=de){target=_blank}.

![](assets/do-not-localize/campaign.jpg){width="40%"}

Lernen Sie die wichtigsten Schritte zur Kampagnenverwaltung kennen:

* [Erste Schritte](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/set-up-campaigns.html?lang=de){target=_blank}: Erfahren Sie mit schrittweisen Anleitungen, wie Sie eine Marketing-Kampagne in Adobe Campaign erstellen und ausführen.

* [Erstellen der ersten Kampagne](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/marketing-campaign-create.html?lang=de){target=_blank}: Erfahren Sie, wie Sie die Logik zur Orchestrierung von Kampagnen planen und einrichten. In einer Kampagne werden alle Elemente im Zusammenhang mit einer Marketing-Kampagne zusammengefasst: Versand, Zielgruppenbestimmungsregeln, Kosten, Exportdateien, zugehörige Dokumente usw.

* [Senden von Nachrichten in einer Kampagne](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/marketing-campaign-deliveries.html?lang=de){target=_blank}: Orchestrieren Sie kanalübergreifende Sendungen in den Kampagnen: Optimieren Sie mit Adobe Campaign die Kommunikation durch personalisierte E-Mails, SMS, Push-Benachrichtigungen und In-App-Nachrichten.

![](assets/do-not-localize/add-on.jpg){width="40%"}

Für die Kampagnenverwaltung stehen drei Add-ons zur Verfügung:

* [Kampagnenoptimierung](https://experienceleague.adobe.com/docs/campaign/automation/campaign-optimization/campaign-typologies.html?lang=de){target=_blank}: Mit diesem Modul können Sie den Versand von Nachrichten steuern, filtern und überwachen. Auf diese Weise werden ein ideal auf Kundenbedürfnisse abgestimmter Nachrichtenversand sowie eine kohärente Unternehmenskommunikation sichergestellt.

* [Marketing Resource Management](https://experienceleague.adobe.com/docs/campaign/automation/mrm/about-marketing-resource-management.html?lang=de){target=_blank}: Dieses Modul ermöglicht die Steuerung von Marketing-Aktionen in einem partizipativen Modus durch eine vollständige Verwaltung und Echtzeitverfolgung von Aufgaben, Budgets und verwendeten Marketing-Ressourcen.

* [Verteiltes Marketing](https://experienceleague.adobe.com/docs/campaign/automation/distributed-marketing/about-distributed-marketing.html?lang=de){target=_blank}: Dieses Modul ermöglicht die Steuerung von Marketing-Aktionen in einem partizipativen Modus durch eine vollständige Verwaltung und Echtzeitverfolgung von Aufgaben, Budgets und verwendeten Marketing-Ressourcen.

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

>[!VIDEO](https://video.tv.adobe.com/v/326572?quality=12&captions=ger)

Additional Campaign Classic how-to videos are available [here](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=de).

-->