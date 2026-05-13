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
TQID: https://experienceleague.adobe.com/MGzMyGtmzaVGZy6oWHcirPPdSSpu9YYcuR30KIVZ9bc
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: d5ef99fa-df0c-4153-bf94-105ad0724167
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 256
ht-degree: 87%

---

# Freigabe von Zielgruppen mit Adobe Experience Cloud {#sharing-audiences-with-adobe-experience-cloud}


>[!CAUTION]
>
>Um Zielgruppen für Adobe Experience Cloud-Lösungen freizugeben, müssen Sie Adobe Identity Management System implementieren. [Weitere Informationen zu IMS](../../integrations/using/about-adobe-id.md).

Mit Adobe Campaign können Sie Zielgruppen und Segmente für Adobe Experience Cloud-Dienste freigeben. Dazu sind zwei Optionen verfügbar:

1. Senden Sie Adobe Experience Platform-Segmentdaten an Adobe Campaign. Zur Implementierung dieser Integration müssen Sie Ihre Echtzeit-Kundendatenplattform mit Campaign (RTCDP) verbinden. [Weitere Informationen finden Sie in diesem Abschnitt](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign.html?lang=de){target="_blank"}.

1. Integrieren Sie **Adobe Campaign** mit **Experience Cloud Audiences** oder **Adobe Audience Manager**. Anschließend können Sie:

   * Importieren Sie freigegebene Audiences/Segmente aus verschiedenen Adobe Experience Cloud-Lösungen in Adobe Campaign. Zielgruppen können über Listen in Adobe Campaign importiert werden.

   * Exportieren Sie Listen in Form von freigegebenen Adobe Experience Cloud-Zielgruppen. Diese Zielgruppen können dann in den anderen von Ihnen verwendeten Adobe Experience Cloud-Lösungen genutzt werden. Der Export von Zielgruppen erfolgt innerhalb eines Workflows im Anschluss an eine Zielgruppenbestimmung mithilfe der dedizierten Aktivität **[!UICONTROL Aktualisierung freigegebener Zielgruppen]**.

Diese Integration unterstützt zwei Arten von Adobe Experience Cloud-IDs:

* **Besucher-ID**: Dieser Kennungstyp ermöglicht die Abstimmung der Adobe Experience Cloud-Besucher mit den Adobe Campaign-Empfängern.
* **Declared ID**: Dieser Kennungstyp ermöglicht die Abstimmung aller Datentypen mit Elementen aus der Adobe Campaign-Datenbank. Er wird in Adobe Campaign als vordefinierter Abstimmschlüssel dargestellt.

  >[!NOTE]
  >
  > Eine Declared ID-Datenquelle kann jetzt auch mit der Integration von Experience Cloud Assets verwendet werden.
  >
