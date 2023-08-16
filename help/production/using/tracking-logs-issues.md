---
product: campaign
title: Probleme mit Trackinglogs
description: Probleme mit Trackinglogs
feature: Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="Gilt nur für Campaign Classic v7"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 58656aa1-aa95-451f-80b8-9e2d28223056
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '76'
ht-degree: 21%

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
