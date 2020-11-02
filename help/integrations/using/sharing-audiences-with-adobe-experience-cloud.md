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
translation-type: tm+mt
source-git-commit: 4b98c23f4120cbea6dd54cd68b61202e74bee3e1
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 62%

---


# Zielgruppenfreigabe mit Adobe Marketing Cloud{#sharing-audiences-with-adobe-experience-cloud}

>[!CAUTION]
>
>Um Audiencen mit Adobe Experience Cloud-Lösungen zu teilen, müssen Sie das Identity Management-System der Adobe implementieren. [Erfahren Sie mehr über das IMS](../../integrations/using/about-adobe-id.md).

Mit Adobe Campaign können Sie Audiencen und Segmente für Adobe Experience Cloud-Lösungen und Hauptdienste freigeben. Es stehen zwei Optionen zur Verfügung:

1. Senden Sie Adobe Experience Platform-Segmentdaten an Adobe Campaign. Zur Implementierung dieser Integration müssen Sie Ihre Echtzeit-Kundendatenplattform mit der Kampagne (RTCDP) verbinden. [Weiterführende Informationen finden Sie in diesem Abschnitt](https://docs.adobe.com/content/help/de-DE/experience-platform/rtcdp/destinations/destinations-cat/adobe-destinations/adobe-campaign-destination.html).


1. Integrate **Adobe Campaign** with **People core service** (also known as **Profiles &amp; Audiences core service**) or Adobe Audience Manager. Anschließend können Sie:

   * Import von Zielgruppen/Segmenten aus den verschiedenen Lösungen der Adobe Experience Cloud in Adobe Campaign. Der Import von Zielgruppen erfolgt in Adobe Campaign in Listen.

   * Export von Listen in Form von Adobe-Experience-Cloud-Zielgruppen. Diese Zielgruppen können dann in den anderen von Ihnen verwendeten Lösungen der Adobe Experience Cloud genutzt werden. Der Export von Zielgruppen erfolgt innerhalb eines Workflows im Anschluss an eine Zielgruppenbestimmung mithilfe der dedizierten Aktivität **[!UICONTROL Aktualisierung freigegebener Zielgruppe]**.

Diese Integration unterstützt zwei Arten von Adobe Experience Cloud-IDs:

* **Visitor ID**: Dieser Kennungstyp ermöglicht die Abstimmung der Adobe-Experience-Cloud-Besucher mit den Adobe-Campaign-Empfängern.
* **Declared ID**: Dieser Kennungstyp ermöglicht die Abstimmung beliebiger Datentypen mit Elementen der Adobe-Campaign-Datenbank. In Adobe Campaign nimmt er die Form eines zuvor definierten Abstimmschlüssels an.
