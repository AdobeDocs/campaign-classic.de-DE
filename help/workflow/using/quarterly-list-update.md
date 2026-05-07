---
product: campaign
title: Vierteljährliches Listen-Update mithilfe einer inkrementellen Abfrage
description: In diesem Anwendungsfall dient eine inkrementelle Abfrage zur automatischen Aktualisierung einer Empfängerliste
feature: Workflows
hide: true
exl-id: 0d3e7046-313a-42a6-9155-3365e8d60bac
source-git-commit: 720a5f4edf534788f7fd143a476c25e58a6f1586
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 39%

---

# Vierteljährliches Listen-Update mithilfe einer inkrementellen Abfrage {#quarterly-list-update}



Im folgenden Beispiel wird eine [inkrementelle Abfrage](incremental-query.md) verwendet, um eine Empfängerliste automatisch zu aktualisieren. Diese Empfänger werden im Rahmen von saisonalen Marketing-Kampagnen angesprochen.

Da diese Kampagnen zu Beginn jeder Saison gestartet werden, um relevante sportliche Aktivitäten anzubieten, werden diese Listen jedes Quartal aktualisiert. Ein Empfänger darf von dieser Kampagne jedoch nur einmal alle 9 Monate angesprochen werden. Auf diese Weise können Sie die Eignungshäufigkeit des Empfängers ausgleichen und Aktivitäten für verschiedene Jahreszeiten im Laufe der Jahre anbieten.

![](assets/incremental_query_example.png)

1. Erstellen Sie einen neuen Workflow und positionieren Sie eine inkrementelle Abfrage mit anschließendem Listen-Update im Diagramm.
1. Konfigurieren Sie in der Aktivität die Registerkarte **[!UICONTROL Inkrementelle Abfrage]** (wie im Abschnitt [Erstellen einer Abfrage](query.md#creating-a-query) beschrieben).
1. Wählen Sie die Registerkarte **[!UICONTROL Planung und Verlauf]** und geben Sie dann einen Verlauf von 270 Tagen an. Ein bereits kontaktierter Empfänger wird für einen Zeitraum von 270 Tagen bzw. etwa 9 Monaten nicht mehr kontaktiert.

   Klicken Sie dann auf die Schaltfläche **[!UICONTROL Ändern...]**.

1. Da die Liste jeweils zu Saisonbeginn aktualisiert werden soll, muss als Häufigkeit **[!UICONTROL Monatlich]** ausgewählt werden.
1. Auf dem nächsten Bildschirm wählen Sie März, Juni, September und Dezember. Wählen Sie den 20. des Monats und dann die Uhrzeit aus, zu der Sie den Workflow starten möchten.
1. Geben Sie abschließend den Gültigkeitszeitraum der Abfrage an. Im vorliegenden Beispiel wurde **[!UICONTROL Dauerhaft gültig]** ausgewählt.

   ![](assets/incremental_query_example_2.png)

1. Konfigurieren Sie nun die Aktivität Listen-Update (wie im Abschnitt [&#128279;](list-update.md)Listen-Update beschrieben).

Der Workflow wird daher automatisch kurz vor Beginn jeder Staffel gestartet. Die Liste wird mit neuen geeigneten Empfängern aktualisiert, um die Angebote zu erhalten.
