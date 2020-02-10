---
title: Unter-Workflow
seo-title: Unter-Workflow
description: Unter-Workflow
seo-description: null
page-status-flag: never-activated
uuid: c952633f-1aca-44cf-bb50-a67e9b086030
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: flow-control-activities
discoiquuid: a4441820-1b3d-4bac-a6e3-1c9c14466d19
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# Unter-Workflow{#sub-workflow}

Mit der **[!UICONTROL Sub-workflow]** Aktivität können Sie die Ausführung eines anderen Workflows auslösen und das Ergebnis wiederherstellen. Mit dieser Aktivität können Sie komplexe Arbeitsabläufe mit einer vereinfachten Oberfläche verwenden.

Sie können in einem einzigen Workflow mehrere Unter-Workflows starten. Unter-Workflows werden synchron ausgeführt.

>[!NOTE]
>
>Damit der Unter-Workflow korrekt ausgeführt wird, darf nur ein einziger Sprung vom Typ &quot;Ziel&quot; mit der niedrigsten Nummer und ein einziger Sprung vom Typ &quot;Start&quot; mit der höchsten Nummer vorhanden sein. Wenn beispielsweise Sprünge vom Typ &quot;Start&quot; mit einer Priorität von 1, 2 und 3 vorhanden sind, sollte nur ein Sprung vom Typ &quot;Start&quot; mit einer Priorität von 3 vorhanden sein.

1. Erstellen Sie einen Workflow, den Sie als Unter-Workflow in einem anderen Workflow verwenden möchten.
1. Fügen Sie eine **[!UICONTROL Jump (end point)]** Aktivität mit der Priorität 1 am Anfang des Workflows ein. Wenn Sie mehrere Sprünge vom Typ &quot;Ankunft&quot;haben, verwendet Adobe Campaign den Springen &quot;Ankunft&quot;mit der niedrigsten Zahl.

   Fügen Sie am Ende des Workflows eine **[!UICONTROL Jump (start point)]** Aktivität mit der Priorität 2 ein. Wenn Sie mehrere &quot;Start&quot;-Jumps haben, verwendet Adobe Campaign den &quot;Start&quot;-Sprung mit der höchsten Anzahl.

   ![](assets/subworkflow_jumps.png)

   >[!NOTE]
   >
   >If the sub-workflow activity references a workflow with several **[!UICONTROL Jump]** activities, the sub-workflow is executed between the &quot;arrival&quot; type jump with the lowest number and the &quot;start&quot; type jump with the highest number.

1. Vervollständigen und speichern Sie diesen Unter-Workflow.
1. Erstellen Sie einen &quot;Master&quot;-Workflow.
1. Insert a **[!UICONTROL Sub-workflow]** activity and open it.
1. Select the workflow that you want to use from the **[!UICONTROL Workflow template]** drop-down list.

   ![](assets/subworkflow_selection.png)

1. Es besteht auch die Möglichkeit, ein Konfigurationsscript hinzuzufügen, um die Funktionsweise des referenzierten Workflows anzupassen.
1. Klicks **[!UICONTROL Ok]**. It will automatically create an outbound transition with the label of the **[!UICONTROL Jump (start point)]** activity from the selected workflow.

   ![](assets/subworkflow_outbound.png)

1. Führen Sie den Workflow aus.

Once run, the workflow that was called as a sub-workflow is still in **[!UICONTROL Being edited]** status, which means the following:

* Sie können mit der rechten Maustaste nicht auf die Transitionen klicken, um die Zielgruppe anzuzeigen.
* Es kann kein Zwischenergebnis der Populationsgröße angezeigt werden.
* Logs werden im Master-Workflow unter der Bezeichnung &quot;subworkflow&quot; aufgeführt.

Dieser Workflow ist nur eine Vorlage. Beim Aufruf im Master-Workflow wird ein neuer Unter-Workflow auf Basis dieser Vorlage angelegt.

## Eingabeparameter (optional) {#input-parameters--optional-}

* tableName
* schema

Jedes eingehende Ereignis muss eine durch diese Parameter definierte Zielgruppe angeben.

## Ausgabeparameter {#output-parameters}

* tableName
* schema
* recCount

Dieser Satz von drei Werten identifiziert die Zielgruppe der Abfrage. **[!UICONTROL tableName]** ist der Name der Tabelle, in der die Zielkennungen aufgezeichnet werden, das Schema der Population (normalerweise nms:empfänger) und die Anzahl der Elemente in der Tabelle **[!UICONTROL schema]** ist **[!UICONTROL recCount]** dies.

* targetSchema

Dieser Wert ist das Schema der Arbeitstabelle. Dieser Parameter ist für alle Übergänge mit **[!UICONTROL tableName]** und gültig **[!UICONTROL schema]**.
