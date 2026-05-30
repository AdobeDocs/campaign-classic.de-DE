---
product: campaign
title: Probleme mit der Bildanzeige
description: Probleme mit der Bildanzeige
feature: Monitoring
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 62fa491e-3e83-422b-bcde-2bae2c1b676e
TQID: https://experienceleague.adobe.com/aBPQb0Yp8o7goe2CS4h6ydnZV5gjPYINHMxGcc-d140
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
feature_v2: []
subfeature_v2:
  - id: c03a11ff-bdf9-4e5b-b279-f468b4293464
  - id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 134
ht-degree: 6%

---

# Probleme mit der Bildanzeige{#image-display-issues}



Wenn in einer gesendeten Nachricht Probleme mit der Bildanzeige auftreten, können Gründe mit einer fehlerhaften Position verknüpft sein:

* Speicherorte stimmen möglicherweise nicht überein oder Bilder wurden möglicherweise nicht korrekt an den doppelten Tracking-Server gepusht: Überprüfen Sie Ihre Konfiguration.
* Bilder befinden sich möglicherweise nicht im Ordner „Öffentliche Ressourcen“ der Marketing-Instanz: Laden Sie die Bilder in Ihren Ressourcenordner hoch, um das Problem zu beheben.
* Wenn Sie in einer Mid-Sourcing-Architektur arbeiten: Beim Senden von Testsendungen werden die Scheckbilder fehlerfrei hochgeladen (Informationen werden in den Analyseprotokollen angezeigt).

Fehlerbehebung:

1. Senden Sie einen Testversand, der die Bilder anzeigt.
1. Überprüfen Sie, ob die Ressourcenkonfiguration in der Instanz korrekt ist.
1. Überprüfen Sie den Ordner mit öffentlichen Ressourcen oder, falls dieser nicht im Ordner mit öffentlichen Ressourcen enthalten ist, den im Versand referenzierten Ordner.
