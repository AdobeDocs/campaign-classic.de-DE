---
solution: Campaign Classic
product: campaign
title: Probleme mit Trackinglogs
description: Probleme mit Trackinglogs
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '69'
ht-degree: 13%

---


# Probleme mit Trackinglogs{#tracking-logs-issues}

Es kann mehrere Gründe dafür geben, dass Trackinglogs nicht weitergeleitet werden. Es wird empfohlen, die folgenden Informationen zu überprüfen:

* Hat der **Tracking** -Arbeitsablauf Fehler?

   Siehe [Technischen Workflows](../../workflow/using/monitoring-technical-workflows.md)zur Überwachung.

   ![](assets/tracking_scheduled_task.png)

* Wird das Modul **trackinglogd** auf dem Server ausgeführt?

   Siehe [Protokolldateien](../../production/using/log-files.md).

* Wurden Änderungen vorgenommen? Sie können mithilfe des Verfolgungsalias einen Verlust der Verbindung zu den Servern auslösen.

