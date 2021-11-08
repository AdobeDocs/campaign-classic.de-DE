---
product: campaign
title: Freigabe von Audiences mit Adobe Experience Cloud
description: Zielgruppenfreigabe mit Adobe Marketing Cloud
audience: integrations
content-type: reference
topic-tags: audience-sharing
exl-id: 1c90e913-3375-476c-ab60-89f20239eb0d
source-git-commit: bd9f035db1cbad883e1f27fe901e34dfbc9c1229
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 100%

---

# Freigabe von Audiences mit Adobe Experience Cloud{#sharing-audiences-with-adobe-experience-cloud}

![](../../assets/common.svg)

>[!CAUTION]
>
>Um Audiences für Adobe Experience Cloud-Lösungen freizugeben, müssen Sie Adobe Identity Management System implementieren. [Weitere Informationen zu IMS](../../integrations/using/about-adobe-id.md).

Mit Adobe Campaign können Sie Audiences und Segmente für Adobe Experience Cloud-Lösungen und Core Services freigeben. Dazu sind zwei Optionen verfügbar:

1. Senden Sie Adobe Experience Platform-Segmentdaten an Adobe Campaign. Zur Implementierung dieser Integration müssen Sie Ihre Echtzeit-Kundendatenplattform mit Campaign (RTCDP) verbinden. [Weitere Informationen finden Sie in diesem Abschnitt](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign.html?lang=de).


1. Integrieren Sie **Adobe Campaign** und **People Core Service** (auch **Profiles &amp; Audiences Core Service** genannt) oder Adobe Audience Manager. Anschließend können Sie:

   * Import von Audiences/Segmenten aus den verschiedenen Lösungen der Adobe Experience Cloud in Adobe Campaign. Der Import von Audiences erfolgt in Adobe Campaign in Listen.

   * Export von Listen in Form von Adobe Experience Cloud-Audiences. Diese Audiences können dann in den anderen von Ihnen verwendeten Lösungen der Adobe Experience Cloud genutzt werden. Der Export von Audiences erfolgt innerhalb eines Workflows im Anschluss an eine Audience-Bestimmung mithilfe der dedizierten Aktivität **[!UICONTROL Aktualisierung freigegebener Zielgruppe]**.

Diese Integration unterstützt zwei Arten von Adobe Experience Cloud-Kennungen:

* **Besucher-ID**: Dieser Kennungstyp ermöglicht die Abstimmung der Adobe Experience Cloud-Besucher mit den Adobe Campaign-Empfängern.
* **Declared ID**: Dieser Kennungstyp ermöglicht die Abstimmung aller Datentypen mit Elementen aus der Adobe Campaign-Datenbank. Er wird in Adobe Campaign als vordefinierter Abstimmschlüssel dargestellt.

   >[!NOTE]
   >
   > Eine Declared ID-Datenquelle kann jetzt auch mit der Integration des People Core Service verwendet werden.
   >
   >Wenn Sie die People Core Service-Integration verwenden und die Audience Manager-Integration hinzufügen möchten, benötigen Sie die Hilfe eines Adobe Audience Manager-Beraters, um zu vermeiden, dass alle ID-Synchronisationen verloren gehen, die beim Wechsel zu dieser Declared ID-Datenquelle in einem Adobe Audience Manager-Kontext erfasst wurden.
