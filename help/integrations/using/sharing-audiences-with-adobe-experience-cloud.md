---
title: Zielgruppenfreigabe mit Adobe Marketing Cloud
seo-title: Zielgruppenfreigabe mit Adobe Marketing Cloud
description: Zielgruppenfreigabe mit Adobe Marketing Cloud
seo-description: null
page-status-flag: never-activated
uuid: 24ac3463-69ab-48b4-85e0-4fe1948bf5ed
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: audience-sharing
discoiquuid: 8f295058-5a78-4512-9bdf-d5f022457e10
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 418a36cd51106dae2b4201c8b5abda9b05285a18

---


# Zielgruppenfreigabe mit Adobe Marketing Cloud{#sharing-audiences-with-adobe-experience-cloud}

>[!NOTE]
>
>Für diese Integration muss IMS implementiert sein. Näheres dazu erfahren Sie im Abschnitt zu [IMS](../../integrations/using/about-adobe-id.md).

Adobe Campaign erlaubt den Austausch und die Freigabe von Zielgruppen/Segmenten mit der Adobe Marketing Cloud und Core Services. Konkret bietet die Integration von **Adobe Campaign** mit **People core service** (auch **Profiles &amp; Audiences Core Service** genannt) oder Adobe Audience Manager folgende Möglichkeiten:

* Import von Zielgruppen/Segmenten aus den verschiedenen Lösungen der Adobe Experience Cloud in Adobe Campaign. Der Import von Zielgruppen erfolgt in Adobe Campaign in Listen.
* Exportieren von Listen in Form freigegebener Zielgruppen in Adobe Experience Cloud. Diese Zielgruppen können in den verschiedenen Adobe Experience Cloud-Lösungen verwendet werden, die Sie verwenden. Audiences can be exported after targeting in a workflow, using a dedicated **[!UICONTROL Update shared audience]** activity.

>[!CAUTION]
>
>Der Zielgruppenimport in Adobe Campaign kann je nach der Art der Daten rechtlichen Beschränkungen unterliegen.

Die Integration unterstützt zwei Arten von Adobe-Experience-Cloud-Kennungen:

* **Visitor ID**: Dieser Kennungstyp ermöglicht die Abstimmung der Adobe-Experience-Cloud-Besucher mit den Adobe-Campaign-Empfängern.
* **Declared ID**: Dieser Kennungstyp ermöglicht die Abstimmung beliebiger Datentypen mit Elementen der Adobe-Campaign-Datenbank. In Adobe Campaign nimmt er die Form eines zuvor definierten Abstimmschlüssels an.
