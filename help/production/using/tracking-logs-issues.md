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

* **Führt die** Tracking **Workflow hat Fehler?**

  Siehe Abschnitt [Technische Workflows überwachen](../../workflow/using/monitoring-technical-workflows.md).

  ![](assets/tracking_scheduled_task.png)

* **Ist das Modul** trackinglogd **auf dem Server ausgeführt werden?**

  Siehe Abschnitt [Protokolldateien](../../production/using/log-files.md).

* **Wurden Änderungen vorgenommen?**

  Mit dem Tracking-Alias kann ein Verbindungsverlust mit den Servern Trigger werden.
