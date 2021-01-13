---
solution: Campaign Classic
product: campaign
title: Probleme mit Trackinglogs
description: Probleme mit Trackinglogs
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: f24642223a2ec9f3d8e78e2f7e71a55bf14b80c7
workflow-type: tm+mt
source-wordcount: '69'
ht-degree: 13%

---


# Probleme mit Trackinglogs{#tracking-logs-issues}

Es kann mehrere Gründe dafür geben, dass Trackinglogs nicht weitergeleitet werden. Es wird empfohlen, die folgenden Informationen zu überprüfen:

* **Hat der****Tracking-Workflow Fehler?**

   Weitere Informationen finden Sie unter [Überwachte Technischen Workflows](../../workflow/using/monitoring-technical-workflows.md).

   ![](assets/tracking_scheduled_task.png)

* **Ist das Modul****trackinglogdrunning auf dem Server?**

   Siehe [Protokolldateien](../../production/using/log-files.md).

* **Wurden Änderungen vorgenommen?**

   Mit dem Tracking-Alias kann ein Serververbindungsverlust Trigger werden.
