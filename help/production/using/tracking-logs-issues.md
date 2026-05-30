---
product: campaign
title: Probleme mit Trackinglogs
description: Probleme mit Trackinglogs
feature: Monitoring
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 58656aa1-aa95-451f-80b8-9e2d28223056
TQID: https://experienceleague.adobe.com/9u8xqAINLPKmeptZOZf94Ms-GiEciCL4nFBaw7SjRss
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2: id: c1579802-ddd4-4214-8a91-97b2066abe11
feature_v2: []
subfeature_v2: id: c03a11ff-bdf9-4e5b-b279-f468b4293464id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 81
ht-degree: 32%

---

# Probleme mit Trackinglogs{#tracking-logs-issues}



Es kann mehrere Gründe dafür geben, dass Trackinglogs nicht weitergeleitet werden. Es wird empfohlen, die folgenden Informationen zu überprüfen:

* **Enthält der** Tracking **-Workflow Fehler?**

Weitere Informationen finden Sie in der [Dokumentation zu Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/monitoring-workflows/monitor-technical-workflows.html?lang=de){target="_blank"}.

![](assets/tracking_scheduled_task.png)

* **Läuft das Modul** trackinglogd **auf dem Server?**

  Siehe [Protokolldateien](../../production/using/log-files.md).

* **Wurden Änderungen vorgenommen?**

  Sie können einen Verbindungsverlust zu den Servern durch die Verwendung des Tracking-Alias in Trigger bringen.
