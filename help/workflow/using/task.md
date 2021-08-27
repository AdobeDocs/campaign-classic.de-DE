---
product: campaign
title: Aufgabe
description: Erfahren Sie mehr über die Workflow-Aktivität "Aufgabe".
audience: workflow
content-type: reference
topic-tags: flow-control-activities
exl-id: 8549bf8c-ba23-44cb-95f2-c50f2d0f5479
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '105'
ht-degree: 78%

---

# Aufgabe{#task}

![](../../assets/common.svg)

>[!AVAILABILITY]
>
>:warning: Diese Funktion ist nur in Campaign Classic v7 verfügbar. [Weitere Informationen](../../mrm/using/creating-and-managing-tasks.md)   

In Kampagnen-Workflows können mithilfe einer **[!UICONTROL Aufgabe]** zwei mögliche Szenarien definiert werden: Das erste kommt zum Tragen, wenn die Aufgabe beendet (im Sinn von erfüllt und wenn erforderlich validiert) wurde, das zweite, wenn die Aufgabe nicht beendet wurde. Dies ist beispielsweise der Fall, wenn der Benutzer die Erfüllung abgelehnt hat oder wenn sie überfällig ist.

![](assets/mrm_task_in_workflow.png)

Die Konfiguration und Funktionsweise einer Aufgabe wird im [Campaign Classic v7-Handbuch](../../mrm/using/creating-and-managing-tasks.md) beschrieben.

![](assets/wkf_task_activity.png)

In der Option **[!UICONTROL Ressourcen]** können die für die Erfüllung der Aufgabe verantwortlichen Benutzer sowie Angaben zu ihrer Validierung gemacht werden. Die Zurückweisung einer erfüllten Aufgabe durch den Validierungsverantwortlichen zieht nicht automatisch die Aktivierung der Transition &#39;Nicht beendet&#39; nach sich.
