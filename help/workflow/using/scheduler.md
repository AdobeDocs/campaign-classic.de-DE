---
title: Planung
seo-title: Planung
description: Planung
seo-description: null
page-status-flag: never-activated
uuid: e814b978-2edd-442e-9334-9633bc9ec63a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: flow-control-activities
discoiquuid: 093dbe8a-494f-4fe7-8614-3bf58486e34c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 707352334144df86ae82aa51d595ae6bc751d1f2

---


# Planung{#scheduler}

Die **Planung** ist eine persistente Aufgabe, die ihre ausgehende Transition zum konfigurierten Zeitpunkt aktiviert.

The **[!UICONTROL Scheduler]** activity should be considered as a scheduled start. daher sind die gleichen Regeln zu beachten wie für die **[!UICONTROL Start]**-Aktivität. So darf die Planung beispielsweise keine eingehende Transition aufweisen.

Es wird empfohlen, Workflows nicht öfter als alle 15 Minuten auszuführen, da die Gesamtleistung des Systems beeinträchtigt werden kann und Blöcke in der Datenbank entstehen können.

Verwenden Sie beim Erstellen Ihres Workflows nicht mehr als eine **[!UICONTROL Scheduler]** Aktivität pro Zweig. For more on this, refer to: [Using activities](../../workflow/using/workflow-best-practices.md#using-activities).

The scheduler defines the activation schedule of the transition. To configure it, double-click the graphical object, then click **[!UICONTROL Change...]**

![](assets/s_user_segmentation_scheduler.png)

In den folgenden Schritten des Assistenten lassen sich die Frequenz der Ausführungen und die Gültigkeit der Aktivität festlegen. Gehen Sie wie folgt vor:

1. Select the activation frequency and click **[!UICONTROL Next]**.

   ![](assets/s_user_segmentation_scheduler2.png)

1. Geben Sie die Tage und Uhrzeit der Ausführung an. Die zur Verfügung stehenden Parameter hängen von der im ersten Schritt ausgewählten Häufigkeit ab. Wenn Sie die Aktivität mehrmals täglich aktivieren, sind folgende Optionen verfügbar:

   ![](assets/s_user_segmentation_scheduler3.png)

1. Definieren Sie im nächsten Schritt die Gültigkeit der Planung oder die maximale Anzahl an Ausführungen.

   ![](assets/s_user_segmentation_scheduler4.png)

1. Check the configuration and click **[!UICONTROL Finish]** to save.

   ![](assets/s_user_segmentation_scheduler5.png)

Die Verwendung einer Scheduler-Aktivität kann dazu führen, dass mehrere Ausführungen eines Workflows gleichzeitig ausgeführt werden. Beispielsweise könnte die Workflow-Ausführung stündlich ausgelöst werden, manchmal aber länger als eine Stunde dauern. Wenn der Workflow bereits ausgeführt wird, ist es empfehlenswert, den Start einer weiteren Ausführung zu überspringen. Weitere Informationen dazu, wie Sie die gleichzeitige Ausführung eines Workflows verhindern können, finden Sie auf [dieser Seite](../../workflow/using/monitoring-workflow-execution.md#preventing-simultaneous-multiple-executions).

Es ist des Weiteren zu beachten, dass die Transition u. U. mit mehreren Stunden Verspätung aktiviert werden kann, wenn der Workflow eine Aufgabe ausführt, die über einen längeren Zeitraum läuft (z. B. ein Import) oder wenn das wfserver-Modul für eine gewisse Dauer inaktiv war. In diesem Fall ist es empfehlenswert, die Ausführung der von der Planung aktivierten Aufgabe auf einen bestimmten Zeitraum zu beschränken.
