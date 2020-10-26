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
translation-type: ht
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: ht
source-wordcount: '219'
ht-degree: 100%

---


# Zielgruppenfreigabe mit Adobe Marketing Cloud{#sharing-audiences-with-adobe-experience-cloud}

>[!NOTE]
>
>Für diese Integration muss IMS implementiert sein. Näheres dazu erfahren Sie im Abschnitt zu [IMS](../../integrations/using/about-adobe-id.md).

Adobe Campaign erlaubt den Austausch und die Freigabe von Zielgruppen/Segmenten mit der Adobe Marketing Cloud und Core Services. Konkret bietet die Integration von **Adobe Campaign** mit **People core service** (auch **Profiles &amp; Audiences Core Service** genannt) oder Adobe Audience Manager folgende Möglichkeiten:

* Import von Zielgruppen/Segmenten aus den verschiedenen Lösungen der Adobe Experience Cloud in Adobe Campaign. Der Import von Zielgruppen erfolgt in Adobe Campaign in Listen.
* Export von Listen in Form von Adobe-Experience-Cloud-Zielgruppen. Diese Zielgruppen können dann in den anderen von Ihnen verwendeten Lösungen der Adobe Experience Cloud genutzt werden. Der Export von Zielgruppen erfolgt innerhalb eines Workflows im Anschluss an eine Zielgruppenbestimmung mithilfe der dedizierten Aktivität **[!UICONTROL Aktualisierung freigegebener Zielgruppe]**.

>[!CAUTION]
>
>Der Zielgruppenimport in Adobe Campaign kann je nach der Art der Daten rechtlichen Beschränkungen unterliegen.

Die Integration unterstützt zwei Arten von Adobe-Experience-Cloud-Kennungen:

* **Visitor ID**: Dieser Kennungstyp ermöglicht die Abstimmung der Adobe-Experience-Cloud-Besucher mit den Adobe-Campaign-Empfängern.
* **Declared ID**: Dieser Kennungstyp ermöglicht die Abstimmung beliebiger Datentypen mit Elementen der Adobe-Campaign-Datenbank. In Adobe Campaign nimmt er die Form eines zuvor definierten Abstimmschlüssels an.
