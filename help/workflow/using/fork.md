---
solution: Campaign Classic
product: campaign
title: Verzweigung
description: Erfahren Sie mehr über die Workflow-Aktivität "Verzweigung"
audience: workflow
content-type: reference
topic-tags: flow-control-activities
translation-type: tm+mt
source-git-commit: 3eecc16442a11849c12819cf83392f60c5b82a13
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 16%

---


# Verzweigung{#fork}

Mit der Aktivität **[!UICONTROL Gabel]** können Sie mehrere ausgehende Transitionen erstellen, um mehrere Aktivitäten unabhängig im selben Arbeitsablauf durchzuführen.

Beispielsweise können Sie die Aktivität nach einer Abfrage verwenden, um zwei parallele Aktionen auszuführen:

* Speichern Sie das Ergebnis der Abfrage in einer Audience,
* Führen Sie eine Segmentierung für das Ergebnis aus, um mehrere Versand zu senden.

Sie können die Aktivität auch im Zusammenhang mit der Inhaltserstellung und der Automatisierung des Versands zum Senden verwenden, um die Zielgruppe und Inhaltserstellung parallel zu starten. Ein spezielles Anwendungsbeispiel ist in [diesem Abschnitt](../../delivery/using/automating-via-workflows.md#creating-the-delivery-and-its-content) verfügbar.

>[!WARNING]
>
>Beachten Sie, dass die ausgehenden Transitionen, die nach einer Fork-Aktivität hinzugefügt wurden, nicht gleichzeitig ausgeführt werden.
>
>Die Aktivität sollte daher nicht verwendet werden, um die Leistung des Workflows zu verbessern, sondern um mehrere Aktivitäten unabhängig auszuführen und sie gegebenenfalls zu verbinden, bevor der Rest des Workflows ausgeführt wird.

Um die Aktivität zu konfigurieren, öffnen Sie sie und definieren Sie die Anzahl und Beschriftung der gewünschten ausgehenden Transitionen.

![](assets/s_user_segmentation_fork.png)

Anschließend können Sie jede ausgehende Transition konfigurieren und sie dann gegebenenfalls mit einer [AND-join](../../workflow/using/and-join.md)-Aktivität verbinden. Auf diese Weise wird der Rest des Workflows erst ausgeführt, nachdem die ausgehenden Transitionen der **[!UICONTROL Gabel]**-Aktivität abgeschlossen sind.
