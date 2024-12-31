---
product: campaign
title: Probleme mit Trackinglogs
description: Probleme mit Trackinglogs
feature: Monitoring
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 58656aa1-aa95-451f-80b8-9e2d28223056
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '69'
ht-degree: 13%

---

# Probleme mit Trackinglogs{#tracking-logs-issues}



Es kann mehrere Gründe dafür geben, dass Trackinglogs nicht weitergeleitet werden. Es wird empfohlen, die folgenden Informationen zu überprüfen:

* **Enthält der** Tracking **-Workflow Fehler?**

  Siehe [Überwachen technischer Workflows](../../workflow/using/monitoring-technical-workflows.md).

  ![](assets/tracking_scheduled_task.png)

* **Läuft das Modul** trackinglogd **auf dem Server?**

  Siehe [Protokolldateien](../../production/using/log-files.md).

* **Wurden Änderungen vorgenommen?**

  Sie können einen Verbindungsverlust zu den Servern durch die Verwendung des Tracking-Alias in Trigger bringen.
