---
solution: Campaign Classic
product: campaign
title: Verzweigung
description: Erfahren Sie mehr über die Workflow-Aktivität "Verzweigung"
audience: workflow
content-type: reference
topic-tags: flow-control-activities
translation-type: tm+mt
source-git-commit: e5f718908d0bb6893e54c51700865ecda09c80db
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 54%

---


# Verzweigung{#fork}

Mit der **[!UICONTROL Verzweigungsaktivität]** können Sie mehrfache ausgehende Transitionen erstellen, um mehrere Aktivitäten unabhängig voneinander im selben Workflow durchzuführen.

Beispielsweise können Sie die Aktivität nach einer Abfrage verwenden, um zwei parallele Aktionen auszuführen:

* Speichern Sie das Ergebnis der Abfrage in einer Audience,
* Führen Sie eine Segmentierung für das Ergebnis aus, um mehrere Sendungen durchzuführen.

Sie können die Aktivität auch im Rahmen der Automatisierung der Inhaltserstellung und des Versands verwenden, um die Zielgruppenberechnung und Inhaltserstellung gleichzeitig zu starten. Ein spezielles Anwendungsbeispiel wird in [diesem Abschnitt](../../delivery/using/automating-via-workflows.md#creating-the-delivery-and-its-content) beschrieben.

>[!IMPORTANT]
>
>Ausgehende Transitionen, die nach einer **[!UICONTROL Fork]**-Aktivität **hinzugefügt wurden, werden nicht gleichzeitig ausgeführt.** Dieses Verhalten kann sich auf die Leistung des Workflows auswirken. Verwenden Sie diese Aktivität, wenn Sie mehrere Aktivitäten unabhängig ausführen müssen und sie dann zusammenführen müssen, bevor Sie den Rest des Workflows ausführen.

Um die Aktivität **[!UICONTROL Gabel]** zu konfigurieren, öffnen Sie sie, um die Nummer und die Beschriftung der ausgehenden Transitionen zu definieren.

![](assets/s_user_segmentation_fork.png)

Anschließend können Sie jede ausgehende Transition konfigurieren und sie dann gegebenenfalls mit einer [AND-join](../../workflow/using/and-join.md)-Aktivität verbinden. Auf diese Weise wird der Rest des Workflows erst ausgeführt, wenn die ausgehenden Transitionen der **[!UICONTROL Gabel]**-Aktivität abgeschlossen sind.
