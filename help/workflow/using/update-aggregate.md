---
title: Aggregat-Update
seo-title: Aggregat-Update
description: Aggregat-Update
seo-description: null
page-status-flag: never-activated
uuid: 34ae42e1-da34-43be-b219-0b3b872177b3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: 031f8d5d-940c-4a4c-97e7-ad4ef61983c1
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Aggregat-Update{#update-aggregate}

Aggregate werden zu Berichtszwecken auf Kubikebene definiert. Beim Konfigurieren eines Aggregats ist eine **[!UICONTROL Workflow]** Registerkarte verfügbar.

Detaillierte Erläuterungen zu Cubes und der Verwendung von Aggregaten in Adobe Campaign finden Sie im entsprechenden [Abschnitt](../../reporting/using/concepts-and-methodology.md#calculating-and-using-aggregates).

The **[!UICONTROL Update aggregate]** activity lets you select the update mode to apply: full or partial.

Standardmäßig wird das Aggregat bei jeder Ausführung vollständig aktualisiert. Bei Auswahl der teilweisen Aktualisierung sind mithilfe des entsprechenden Links die Aktualisierungsbedingungen zu definieren.

![](assets/s_advuser_cube_agregate_05.png)

**Gute Praxis**: Eine **[!UICONTROL Scheduler]** Aktivität kann verwendet werden, um die Häufigkeit von Berechnungsaktualisierungen anzugeben.

![](assets/s_advuser_cube_agregate_04.png)

