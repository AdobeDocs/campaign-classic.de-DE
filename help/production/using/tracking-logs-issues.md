---
product: campaign
title: Probleme mit Trackinglogs
description: Probleme mit Trackinglogs
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 58656aa1-aa95-451f-80b8-9e2d28223056
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '69'
ht-degree: 13%

---

# Probleme mit Trackinglogs{#tracking-logs-issues}

Es kann mehrere Gründe dafür geben, dass Trackinglogs nicht weitergeleitet werden. Es wird empfohlen, die folgenden Informationen zu überprüfen:

* **Hat der****Tracking-Workflow Fehler?**

   Siehe [Technische Workflows überwachen](../../workflow/using/monitoring-technical-workflows.md).

   ![](assets/tracking_scheduled_task.png)

* **Wird das Modul****trackinglogdrunning auf dem Server ausgeführt?**

   Siehe [Protokolldateien](../../production/using/log-files.md).

* **Wurden Änderungen vorgenommen?**

   Mit dem Tracking-Alias kann ein Verbindungsverlust mit den Servern Trigger werden.
