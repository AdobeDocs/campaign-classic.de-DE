---
product: campaign
title: Probleme mit Trackinglogs
description: Probleme mit Trackinglogs
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 58656aa1-aa95-451f-80b8-9e2d28223056
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '69'
ht-degree: 13%

---

# Probleme mit Trackinglogs{#tracking-logs-issues}

![](../../assets/v7-only.svg)

Es kann mehrere Gründe dafür geben, dass Trackinglogs nicht weitergeleitet werden. Es wird empfohlen, die folgenden Informationen zu überprüfen:

* **Stellt die** Tracking **Workflow hat Fehler?**

   Siehe [Technische Workflows überwachen](../../workflow/using/monitoring-technical-workflows.md).

   ![](assets/tracking_scheduled_task.png)

* **Ist das Modul** trackinglogd **auf dem Server ausgeführt werden?**

   Siehe [Protokolldateien](../../production/using/log-files.md).

* **Wurden Änderungen vorgenommen?**

   Mit dem Tracking-Alias kann ein Verbindungsverlust mit den Servern Trigger werden.
