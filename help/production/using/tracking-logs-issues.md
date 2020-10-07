---
title: Probleme mit Trackinglogs
seo-title: Probleme mit Trackinglogs
description: Probleme mit Trackinglogs
seo-description: null
page-status-flag: never-activated
uuid: 996869c4-7ffe-4fcc-9555-1d8b65e93e87
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: 1b9ff479-4847-408d-a5c2-9a164805081f
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '72'
ht-degree: 16%

---


# Probleme mit Trackinglogs{#tracking-logs-issues}

Es kann mehrere Gründe dafür geben, dass Trackinglogs nicht weitergeleitet werden. Es wird empfohlen, die folgenden Informationen zu überprüfen:

* Hat der **Tracking** -Arbeitsablauf Fehler?

   Siehe [Technischen Workflows](../../workflow/using/monitoring-technical-workflows.md)zur Überwachung.

   ![](assets/tracking_scheduled_task.png)

* Wird das Modul **trackinglogd** auf dem Server ausgeführt?

   Siehe [Protokolldateien](../../production/using/log-files.md).

* Wurden Änderungen vorgenommen? Sie können mithilfe des Verfolgungsalias einen Verlust der Verbindung zu den Servern auslösen.

