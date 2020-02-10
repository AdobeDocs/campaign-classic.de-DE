---
title: Advanced parameters
seo-title: Advanced parameters
description: Advanced parameters
seo-description: null
page-status-flag: never-activated
uuid: 9453d291-921b-4a03-80d1-2c8295f9a986
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: advanced-management
discoiquuid: f66f1ff5-3601-4eb8-b05d-6f99164890ae
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# Erweiterte Parameter{#advanced-parameters}

The properties screen of an activity has an **[!UICONTROL Advanced]** tab that lets you define a behavior in case of errors, the execution period for the activity; and lets you enter an initialization script. Es gibt zwei Versionen dieser Registerkarte:

* a simplified version (for **[!UICONTROL Start]** and **[!UICONTROL End]** activities for instance)

   ![](assets/wf-advanced-basic.png)

* a more detailed version (for the **[!UICONTROL Query]** activity, for instance)

   ![](assets/wf-advanced-full.png)

The fields to be entered in the **[!UICONTROL Advanced]** tab are detailed in the following sections.

## Name {#name}

Dieses Feld enthält den internen Namen der Aktivität.

## Bild {#image}

In diesem Feld können Sie das mit einer Aktivität verknüpfte Bild ändern. Weitere Informationen finden Sie unter: Verwalten [von Aktivitätsbildern](../../workflow/using/managing-activity-images.md).

## Ausführung {#execution}

Definieren Sie hier die Art der Aufgabenausführung. Drei Optionen stehen zur Verfügung:

In der Regel werden diese Optionen im Diagramm durch Rechtsklick auf die Aktivität ausgewählt.

* **[!UICONTROL Normal]** - die Aufgabe wird ausgeführt.
* **[!UICONTROL Do not activate]**: Diese Aufgabe und alle folgenden Aufgaben (in derselben Verzweigung) werden nicht ausgeführt.
* **[!UICONTROL Activate but do not execute]**: Diese Aufgabe und alle folgenden Aufgaben (in derselben Verzweigung) werden automatisch beendet. Dies kann nützlich sein, wenn Sie beim Starten der Aufgabe dort sein möchten. Um die Aufgabe manuell auszuführen, klicken Sie mit der rechten Maustaste auf die Aktivität und wählen Sie **[!UICONTROL Normal execution]**.

## Affinität {#affinity}

Mit diesem Feld können Sie die Ausführung einer Aktivität auf einem bestimmten Computer erzwingen. For more on this, refer to: [Managing propensity](../../workflow/using/managing-propensity.md).

## Max. execution period {#max--execution-period}

In diesem Feld können Sie eine Warnung einstellen, wenn die Aufgabe zu lange dauert. Der Workflow-Vorgang wird dadurch nicht beeinflusst. Wenn die Aufgabe noch nicht abgeschlossen ist, wenn die Aufgabe beendet **[!UICONTROL Max. execution period]** ist, wird auf der **[!UICONTROL Instance monitoring]** Seite eine Warnung für diesen Workflow angezeigt. Auf diese Seite wird über die **[!UICONTROL Monitoring]** Registerkarte der Homepage zugegriffen.

## Verhalten {#behavior}

In diesem Feld wird das Verhalten des Workflows im Fall von asynchronen Aufgaben bestimmt. Zwei Optionen stehen zur Verfügung:

* **[!UICONTROL Several tasks authorized]**: mehrere Aufgaben gleichzeitig ausgeführt werden können, auch wenn die erste nicht abgeschlossen ist.
* **[!UICONTROL The current task has priority]**: Aufgaben, die derzeit ausgeführt werden, haben Vorrang. Solange eine Aufgabe ausgeführt wird, wird keine andere Aufgabe ausgeführt.

## Time zone {#time-zone}

In diesem Feld können Sie die Zeitzone der Aktivität auswählen. Weitere Informationen: Verwalten [von Zeitzonen](../../workflow/using/managing-time-zones.md).

## Fehler {#in-case-of-errors}

In diesem Feld wird angegeben, wie mit Fehlern umgegangen werden soll. Zwei Optionen stehen zur Verfügung:

* **[!UICONTROL Stop the process]**: der Workflow automatisch beendet wird.  Der Status ändert sich in **[!UICONTROL Failed]**. Sobald das Problem gelöst ist, starten Sie den Workflow neu.
* **[!UICONTROL Ignore]**: Diese Aufgabe und alle folgenden Aufgaben (in derselben Verzweigung) werden nicht ausgeführt. Dies kann bei wiederkehrenden Aufgaben nützlich sein. Wenn in der Verzweigung ein Scheduler flussaufwärts platziert ist, beginnt er wie gewohnt am nächsten Ausführungsdatum.

## Initialisierungsscript {#initialization-script}

In diesem Feld können Sie Variablen initialisieren oder Aktivitätseigenschaften ändern. Weitere Informationen finden Sie unter: [JavaScript-Skripten und -Vorlagen](../../workflow/using/javascript-scripts-and-templates.md).

## Kommentar {#comment}

The **[!UICONTROL Comment]** field is a free field that lets you add a description.
