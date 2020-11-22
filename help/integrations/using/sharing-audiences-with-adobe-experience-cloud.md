---
solution: Campaign Classic
product: campaign
title: Zielgruppenfreigabe mit Adobe Marketing Cloud
description: Zielgruppenfreigabe mit Adobe Marketing Cloud
audience: integrations
content-type: reference
topic-tags: audience-sharing
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 61%

---


# Zielgruppenfreigabe mit Adobe Marketing Cloud{#sharing-audiences-with-adobe-experience-cloud}

>[!CAUTION]
>
>Um Audiencen mit Adobe Experience Cloud-Lösungen zu teilen, müssen Sie das Identity Management-System der Adobe implementieren. [Erfahren Sie mehr über das IMS](../../integrations/using/about-adobe-id.md).

Mit Adobe Campaign können Sie Audiencen und Segmente für Adobe Experience Cloud-Lösungen und Hauptdienste freigeben. Es stehen zwei Optionen zur Verfügung:

1. Senden Sie Adobe Experience Platform-Segmentdaten an Adobe Campaign. Zur Implementierung dieser Integration müssen Sie Ihre Echtzeit-Kundendatenplattform mit der Kampagne (RTCDP) verbinden. [Weitere Informationen finden Sie in diesem Abschnitt](https://docs.adobe.com/content/help/de-DE/experience-platform/rtcdp/destinations/destinations-cat/adobe-destinations/adobe-campaign-destination.html).


1. Integrate **Adobe Campaign** with **People core service** (also known as **Profiles &amp; Audiences core service**) or Adobe Audience Manager. Anschließend können Sie:

   * Import von Zielgruppen/Segmenten aus den verschiedenen Lösungen der Adobe Experience Cloud in Adobe Campaign. Der Import von Zielgruppen erfolgt in Adobe Campaign in Listen.

   * Export von Listen in Form von Adobe-Experience-Cloud-Zielgruppen. Diese Zielgruppen können dann in den anderen von Ihnen verwendeten Lösungen der Adobe Experience Cloud genutzt werden. Der Export von Zielgruppen erfolgt innerhalb eines Workflows im Anschluss an eine Zielgruppenbestimmung mithilfe der dedizierten Aktivität **[!UICONTROL Aktualisierung freigegebener Zielgruppe]**.

Diese Integration unterstützt zwei Arten von Adobe Experience Cloud-IDs:

* **Visitor ID**: Dieser Kennungstyp ermöglicht die Abstimmung der Adobe-Experience-Cloud-Besucher mit den Adobe-Campaign-Empfängern.
* **Declared ID**: Dieser Kennungstyp ermöglicht die Abstimmung beliebiger Datentypen mit Elementen der Adobe-Campaign-Datenbank. In Adobe Campaign nimmt er die Form eines zuvor definierten Abstimmschlüssels an.
