---
product: campaign
title: Erste Schritte mit Quellen und Zielen
description: Weitere Informationen zu Quellen und Zielen in Adobe Experience Platform
feature: Experience Platform Integration
audience: integrations
content-type: reference
exl-id: 8cee52c7-ea56-4701-8ebb-eb18afffea51
TQID: https://experienceleague.adobe.com/xPpBR6NrQ315FIw1beLnw4c0gyLzEoYWzIXDljDg9H4
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: a075b2c1-7748-4328-b7f6-343aa314616aid: d5ef99fa-df0c-4153-bf94-105ad0724167
subfeature_v2: id: c3bf7e1e-1db5-4c72-9293-e2f0b1ab73d0id: eb007b6d-6e57-46ab-9485-3f24d6102304
topic_v2: id: c1579802-ddd4-4214-8a91-97b2066abe11id: e1e0219c-f879-479f-8427-888ed2a6e9c2
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 313
ht-degree: 100%

---

# Arbeiten mit Quellen und Zielen {#rtcdp}



## Über Quellen und Ziele

Mit Adobe Experience Platform können Sie Daten zwischen Campaign Classic und der Adobe Echtzeit-Kundendatenplattform (RTCDP) austauschen. Auf diese Weise können Sie Adobe Experience Platform-Zielgruppen in Ihren Campaign-Workflows auswählen und dann Daten, die sich auf diese Zielgruppen beziehen, wie Sendungen, Öffnungen und Klicks, an Adobe Real-Time Customer Data Platform zurücksenden.

* Mit **Zielen** können Sie Adobe Experience Platform-Zielgruppen in Campaign Classic aufnehmen. Auf diese Weise können Sie bekannte und unbekannte Daten für Ihre Marketing-Kampagnen aktivieren.
* Mit **Quellen** exportieren Sie Campaign Classic-Daten (z. B. Sendungen, Öffnungen und Klicks) nach Adobe Experience Platform. Auf diese Weise können Sie Daten, die Sie aus unterschiedlichen Quellen erfassen, an einem Ort zusammenfassen und die daraus gewonnenen Erkenntnisse nutzen.

>[!IMPORTANT]
>
>Beachten Sie bei dieser Integration die Einschränkungen für die SFTP-Datenspeicherung, für die Datenbank-Datenspeicherung und für aktive Profile gemäß Ihrem Adobe Campaign-Vertrag.

Eine detaillierte Übersicht über die Adobe Echtzeit-Kundendatenplattform, Ziele und Quellen finden Sie auf diesen Seiten:

* [Adobe Real-Time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/overview.html?lang=de)
* [Dokumentation zu Zielen](https://experienceleague.adobe.com/docs/experience-platform/destinations/home.html?lang=de)
* [Dokumentation zu Quellen](https://experienceleague.adobe.com/docs/experience-platform/sources/home.html?lang=de)

## Campaign Classic mit Adobe Experience Platform verbinden

Um Daten zwischen Adobe Experience Platform und Campaign Classic austauschen zu können, müssen Sie zunächst Adobe Campaign als **Ziel** und in Adobe Experience Platform Ihren AWS-S3- oder Azure-Blob-Speicherort als **Quelle** verbinden.

Nachdem die Connectoren konfiguriert wurden, können Sie mithilfe von Workflows einen Datenimport oder -export in Campaign Classic einrichten.

![](assets/rtcdp-schema.png)

Weitere Informationen zum Einrichten dieser Import- und Exportprozesse finden Sie in den folgenden Abschnitten:

* [Adobe Experience Platform-Segmente in Campaign aufnehmen](../../integrations/using/ingest-aep-data.md)
* [Daten von Campaign nach Adobe Experience Platform exportieren](../../integrations/using/export-campaign-data.md)
