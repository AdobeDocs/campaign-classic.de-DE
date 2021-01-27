---
solution: Campaign Classic
product: campaign
title: Vierteljährliches Listen-Update mithilfe einer inkrementellen Abfrage
description: In diesem Anwendungsfall dient eine inkrementelle Abfrage zur automatischen Aktualisierung einer Empfängerliste.
audience: workflow
content-type: reference
topic-tags: targeting-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 100%

---


# Vierteljährliches Listen-Update mithilfe einer inkrementellen Abfrage {#quarterly-list-update}

Im folgenden Beispiel wird eine [inkrementelle Abfrage](../../workflow/using/incremental-query.md) verwendet, um eine Empfängerliste automatisch zu aktualisieren. Diese wird regelmäßig im Rahmen saisonaler Marketing-Kampagnen verwendet.

Jeweils zu Beginn einer neuen Saison werden geeignete sportliche Aktivitäten beworben. Dies bedeutet, dass die Listen einmal pro Quartal aktualisiert werden. Die Empfänger sollen jedoch im Rahmen dieser Kampagne nur einmal alle neun Monate angesprochen werden. Auf diese Weise wird eine eventuelle Werbemüdigkeit durch den Empfänger vermieden und sichergestellt, dass er im Laufe der Zeit Angebote für verschiedene Jahreszeiten erhält.

![](assets/incremental_query_example.png)

1. Erstellen Sie einen neuen Workflow und positionieren Sie eine inkrementelle Abfrage mit anschließendem Listen-Update im Diagramm.
1. Konfigurieren Sie in der Aktivität den Tab **[!UICONTROL Inkrementelle Abfrage]** (wie im Abschnitt [Abfragen erstellen](../../workflow/using/query.md#creating-a-query) beschrieben).
1. Gehen Sie in den Tab **[!UICONTROL Planung &amp; Verlauf]** und geben Sie einen Verlaufsumfang von 270 Tagen an. Ein bereits angesprochener Empfänger wird innerhalb der nächsten 270 Tage, also ungefähr 9 Monate, nicht mehr im Rahmen dieser Kampagne kontaktiert.

   Klicken Sie dann auf die Schaltfläche **[!UICONTROL Ändern...]**.

1. Da die Liste jeweils zu Saisonbeginn aktualisiert werden soll, muss als Häufigkeit **[!UICONTROL Monatlich]** ausgewählt werden.
1. Wählen Sie im nächsten Bildschirm die Monate März, Juni, September und Dezember aus. Geben Sie als Tag den 20. des Monats an und die Uhrzeit, an der der Workflow gestartet werden soll.
1. Geben Sie abschließend den Gültigkeitszeitraum der Abfrage an. Im vorliegenden Beispiel wurde **[!UICONTROL Dauerhaft gültig]** ausgewählt.

   ![](assets/incremental_query_example_2.png)

1. Konfigurieren Sie nun die Aktivität Listen-Update (wie im Abschnitt ](../../workflow/using/list-update.md)Listen-Update[ beschrieben).

Der Workflow startet automatisch zu jedem Saisonbeginn und die Liste wird jeweils mit den neuen Angebotsempfängern aktualisiert.
