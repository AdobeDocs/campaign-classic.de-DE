---
product: campaign
title: Probleme mit Trackinglogs
description: Probleme mit Trackinglogs
feature: Monitoring
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 58656aa1-aa95-451f-80b8-9e2d28223056
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '71'
ht-degree: 14%

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
