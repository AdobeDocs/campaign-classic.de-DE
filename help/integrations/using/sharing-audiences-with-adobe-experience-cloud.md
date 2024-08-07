---
product: campaign
title: Freigabe von Zielgruppen mit Adobe Experience Cloud
description: Freigabe von Zielgruppen mit Adobe Experience Cloud
feature: Audiences
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
audience: integrations
content-type: reference
topic-tags: audience-sharing
exl-id: 1c90e913-3375-476c-ab60-89f20239eb0d
source-git-commit: b11185da8236d6100d98eabcc9dc1cf2cffa70af
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 100%

---

# Freigabe von Zielgruppen mit Adobe Experience Cloud {#sharing-audiences-with-adobe-experience-cloud}


>[!CAUTION]
>
>Um Audiences für Adobe Experience Cloud-Lösungen freizugeben, müssen Sie Adobe Identity Management System implementieren. [Weitere Informationen zu IMS](../../integrations/using/about-adobe-id.md).

Mit Adobe Campaign können Sie Zielgruppen und Segmente für Adobe Experience Cloud-Dienste freigeben. Dazu sind zwei Optionen verfügbar:

1. Senden Sie Adobe Experience Platform-Segmentdaten an Adobe Campaign. Zur Implementierung dieser Integration müssen Sie Ihre Echtzeit-Kundendatenplattform mit Campaign (RTCDP) verbinden. [Weiterführende Informationen finden Sie in diesem Abschnitt](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign.html?lang=de){target="_blank"}.

1. Integrieren Sie **Adobe Campaign** mit **Experience Cloud Audiences** oder **Adobe Audience Manager**. Anschließend können Sie:

   * Import von Audiences/Segmenten aus den verschiedenen Lösungen der Adobe Experience Cloud in Adobe Campaign. Der Import von Audiences erfolgt in Adobe Campaign in Listen.

   * Export von Listen in Form von freigegebenen Adobe Experience Cloud-Zielgruppen. Diese Zielgruppen können dann in anderen von Ihnen genutzten Adobe Experience Cloud-Lösungen genutzt werden. Der Export von Zielgruppen erfolgt innerhalb eines Workflows im Anschluss an eine Zielgruppenbestimmung mithilfe der dedizierten Aktivität **[!UICONTROL Aktualisierung freigegebener Zielgruppen]**.

Diese Integration unterstützt zwei Arten von Adobe Experience Cloud-IDs:

* **Besucher-ID**: Dieser Kennungstyp ermöglicht die Abstimmung der Adobe Experience Cloud-Besucher mit den Adobe Campaign-Empfängern.
* **Declared ID**: Dieser Kennungstyp ermöglicht die Abstimmung aller Datentypen mit Elementen aus der Adobe Campaign-Datenbank. Er wird in Adobe Campaign als vordefinierter Abstimmschlüssel dargestellt.

  >[!NOTE]
  >
  > Eine Declared ID-Datenquelle kann jetzt auch mit der Integration von Experience Cloud Assets verwendet werden.
  >
