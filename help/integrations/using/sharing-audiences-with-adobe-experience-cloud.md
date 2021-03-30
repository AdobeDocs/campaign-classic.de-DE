---
solution: Campaign Classic
product: campaign
title: Zielgruppenfreigabe mit Adobe Marketing Cloud
description: Zielgruppenfreigabe mit Adobe Marketing Cloud
audience: integrations
content-type: reference
topic-tags: audience-sharing
translation-type: tm+mt
source-git-commit: 40abbf1f981331b8a19d3607c57624aac22c91f2
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 78%

---


# Zielgruppenfreigabe mit Adobe Marketing Cloud{#sharing-audiences-with-adobe-experience-cloud}

>[!CAUTION]
>
>Um Audiences für Adobe Experience Cloud-Lösungen freizugeben, müssen Sie Adobe Identity Management System implementieren. [Weitere Informationen zu IMS](../../integrations/using/about-adobe-id.md).

Mit Adobe Campaign können Sie Audiences und Segmente für Adobe Experience Cloud-Lösungen und Core Services freigeben. Dazu sind zwei Optionen verfügbar:

1. Senden Sie Adobe Experience Platform-Segmentdaten an Adobe Campaign. Zur Implementierung dieser Integration müssen Sie Ihre Echtzeit-Kundendatenplattform mit Campaign (RTCDP) verbinden. [Weitere Informationen finden Sie in diesem Abschnitt](https://docs.adobe.com/content/help/de-DE/experience-platform/rtcdp/destinations/destinations-cat/adobe-destinations/adobe-campaign-destination.html).


1. Integrieren Sie **Adobe Campaign** und **People Core Service** (auch **Profiles &amp; Audiences Core Service** genannt) oder Adobe Audience Manager. Anschließend können Sie:

   * Import von Zielgruppen/Segmenten aus den verschiedenen Lösungen der Adobe Experience Cloud in Adobe Campaign. Der Import von Zielgruppen erfolgt in Adobe Campaign in Listen.

   * Export von Listen in Form von Adobe-Experience-Cloud-Zielgruppen. Diese Zielgruppen können dann in den anderen von Ihnen verwendeten Lösungen der Adobe Experience Cloud genutzt werden. Der Export von Zielgruppen erfolgt innerhalb eines Workflows im Anschluss an eine Zielgruppenbestimmung mithilfe der dedizierten Aktivität **[!UICONTROL Aktualisierung freigegebener Zielgruppe]**.

Diese Integration unterstützt zwei Arten von Adobe Experience Cloud-Kennungen:

* **Visitor ID**: Dieser Kennungstyp ermöglicht die Abstimmung der Adobe-Experience-Cloud-Besucher mit den Adobe-Campaign-Empfängern.
* **Declared ID**: Dieser Kennungstyp ermöglicht die Abstimmung beliebiger Datentypen mit Elementen der Adobe-Campaign-Datenbank. In Adobe Campaign nimmt er die Form eines zuvor definierten Abstimmschlüssels an.

   >[!NOTE]
   >
   > Deklarierte ID-Datenquelle kann jetzt auch mit der Integration des Hauptdienstes People verwendet werden.
   >
   >Wenn Sie die Integration des Hauptdiensts People verwenden und die Integration des Audience Managers hinzufügen möchten, benötigen Sie die Hilfe eines Adobe Audience Manager-Beraters, um zu vermeiden, dass alle beim Übergang zur Verwendung dieser deklarierten ID-Datenquelle in einem Adobe Audience Manager-Kontext erfassten ID-Synchronisierungen verloren gehen.
