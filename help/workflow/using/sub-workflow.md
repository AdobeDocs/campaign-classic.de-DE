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
translation-type: ht
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# Unter-Workflow{#sub-workflow}

Mit der Aktivität **[!UICONTROL Unter-Workflow]** kann die Ausführung eines anderen Workflows gestartet und dessen Ergebnis zur weiteren Verwendung abgerufen werden. Dies ermöglicht komplexe, aber dennoch übersichtliche Workflow-Konstruktionen.

Sie können in einem einzigen Workflow mehrere Unter-Workflows starten. Unter-Workflows werden synchron ausgeführt.

>[!NOTE]
>
>Damit der Unter-Workflow korrekt ausgeführt wird, darf nur ein einziger Sprung vom Typ &quot;Ziel&quot; mit der niedrigsten Nummer und ein einziger Sprung vom Typ &quot;Start&quot; mit der höchsten Nummer vorhanden sein. Wenn beispielsweise Sprünge vom Typ &quot;Start&quot; mit einer Priorität von 1, 2 und 3 vorhanden sind, sollte nur ein Sprung vom Typ &quot;Start&quot; mit einer Priorität von 3 vorhanden sein.

1. Erstellen Sie einen Workflow, den Sie als Unter-Workflow in einem anderen Workflow verwenden möchten.
1. Fügen Sie zu Beginn des Workflows die Aktivität **[!UICONTROL Sprung (Ziel)]** mit der Priorität 1 ein. Wenn Sie mehrere Sprünge vom Typ &quot;Ziel&quot; haben, verwendet Adobe Campaign den Ziel-Sprung mit der niedrigsten Nummer.

   Fügen Sie am Ende des Workflows die Aktivität **[!UICONTROL Sprung (Start)]** mit der Priorität 2 ein. Wenn Sie mehrere Sprünge vom Typ &quot;Start&quot; haben, verwendet Adobe Campaign den Start-Sprung mit der höchsten Nummer.

   ![](assets/subworkflow_jumps.png)

   >[!NOTE]
   >
   >Wenn die Unter-Workflow-Aktivität einen Workflow startet, der mehrere **[!UICONTROL Sprung]**-Aktivitäten aufweist, wird der Unter-Workflow zwischen dem Sprung vom Typ &quot;Ziel&quot; mit der kleinsten Nummer und dem Sprung vom Typ &quot;Start&quot; mit der höchsten Nummer ausgeführt.

1. Vervollständigen und speichern Sie diesen Unter-Workflow.
1. Erstellen Sie einen &quot;Master&quot;-Workflow.
1. Fügen Sie die Aktivität **[!UICONTROL Unter-Workflow]** ein und öffnen Sie sie.
1. Wählen Sie in der Dropdown-Liste der **[!UICONTROL Workflow-Vorlagen]** den gewünschten Workflow aus.

   ![](assets/subworkflow_selection.png)

1. Es besteht auch die Möglichkeit, ein Konfigurationsscript hinzuzufügen, um die Funktionsweise des referenzierten Workflows anzupassen.
1. Wählen Sie **[!UICONTROL OK]** aus. Aus dem ausgewählten Workflow wird automatisch eine ausgehende Transition mit dem Titel der Aktivität **[!UICONTROL Sprung (Start)]** erstellt.

   ![](assets/subworkflow_outbound.png)

1. Führen Sie den Workflow aus.

Nach Ausführung befindet sich der Workflow, der als Unter-Workflow gestartet wurde, im Status **[!UICONTROL In Bearbeitung]**, was Folgendes bedeutet:

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

Anhand der drei Werte lässt sich die durch den Ausschluss ermittelte Zielgruppe identifizieren. **[!UICONTROL tableName]** ist der Name der Tabelle, welche die Kennungen der Zielgruppenempfänger enthält, **[!UICONTROL schema]** ist das Schema der Population, (i. d. R. nms:recipient) und **[!UICONTROL recCount]** ist die Anzahl an Elementen in der Tabelle.

* targetSchema

Dieser Wert bezeichnet das Schema der Arbeitstabelle. Dieser Parameter ist für alle Transitionen mit **[!UICONTROL tableName]** und **[!UICONTROL schema]** gültig.
