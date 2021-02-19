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
ht-degree: 100%

---


# Verzweigung{#fork}

Mit der **[!UICONTROL Verzweigungsaktivität]** können Sie mehrfache ausgehende Transitionen erstellen, um mehrere Aktivitäten unabhängig voneinander im selben Workflow durchzuführen.

Beispielsweise können Sie die Aktivität nach einer Abfrage verwenden, um zwei parallele Aktionen auszuführen:

* Speichern Sie das Ergebnis der Abfrage in einer Audience,
* Führen Sie eine Segmentierung für das Ergebnis aus, um mehrere Sendungen durchzuführen.

Sie können die Aktivität auch im Rahmen der Automatisierung der Inhaltserstellung und des Versands verwenden, um die Zielgruppenberechnung und Inhaltserstellung gleichzeitig zu starten. Ein spezielles Anwendungsbeispiel wird in [diesem Abschnitt](../../delivery/using/automating-via-workflows.md#creating-the-delivery-and-its-content) beschrieben.

>[!IMPORTANT]
>
>Ausgehende Transitionen, die nach einer **[!UICONTROL Verzweigungsaktivität]** hinzugefügt werden, werden **nicht** gleichzeitig ausgeführt. Dieses Verhalten kann sich auf die Leistung des Workflows auswirken. Verwenden Sie diese Aktivität, wenn Sie mehrere Aktivitäten unabhängig voneinander ausführen und dann zusammenführen möchten, bevor Sie den Rest des Workflows ausführen.

Um die Aktivität **[!UICONTROL Verzweigung]** zu konfigurieren, öffnen Sie sie und definieren Sie die Anzahl und Bezeichnung der gewünschten ausgehenden Transitionen.

![](assets/s_user_segmentation_fork.png)

Anschließend können Sie die einzelnen ausgehenden Transitionen konfigurieren und dann gegebenenfalls mithilfe der Aktivität [Und-Verknüpfung](../../workflow/using/and-join.md) verknüpfen. Auf diese Weise wird der Rest des Workflows erst ausgeführt, nachdem die ausgehenden Transitionen der **[!UICONTROL Verzweigungsaktivität]** abgeschlossen sind.
