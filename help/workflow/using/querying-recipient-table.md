---
product: campaign
title: Abfrage der Empfängertabelle
description: Erfahren Sie, wie Sie die Empfängertabelle abfragen
feature: Query Editor, Workflows
exl-id: 5b037798-b092-4c98-9f6a-4af7fc7941c6
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 77%

---

# Abfrage der Empfängertabelle {#querying-recipient-table}



In diesem Beispiel werden die Namen und E-Mail-Adressen der Empfänger gesucht, deren E-Mail-Domain &quot;web.de&quot; ist und die nicht in Berlin wohnen.

* Welche Tabelle soll ausgewählt werden?

  Die Empfängertabelle (nms:recipient)

* Felder, die als Ausgabespalten verwendet werden sollen

  E-Mail, Name, Wohnort und Kundennummer

* Nach welchen Kriterien sind die Empfänger zu filtern?

  Nach Wohnort und E-Mail-Domain

* Wird das Ergebnis sortiert?

  Ja, nach **[!UICONTROL Kundennummer]** und **[!UICONTROL Nachname]**.

Gehen Sie wie folgt vor:

1. Klicks **[!UICONTROL Tools > Generischer Abfrageeditor...]** und wählen Sie **Empfänger** (**nms:recipient**). Klicken Sie anschließend auf **[!UICONTROL Nächste]**.
1. Wählen Sie: **[!UICONTROL Nachname]**, **[!UICONTROL Vorname]**, **[!UICONTROL Email]**, **[!UICONTROL Ort]** und **[!UICONTROL Kontonummer]**. Diese Felder werden zu **[!UICONTROL Ausgabespalten]**. Klicken Sie anschließend auf **[!UICONTROL Nächste]**.

   ![](assets/query_editor_03.png)

1. Sortieren Sie die Spalten in der gewünschten Reihenfolge. Hier möchten wir die Kundennummern in absteigender Reihenfolge und die Namen in alphabetischer Reihenfolge sortieren. Klicken Sie anschließend auf **[!UICONTROL Nächste]**.

   ![](assets/query_editor_04.png)

1. Wählen Sie im Fenster **[!UICONTROL Datenfilter]** die Option **[!UICONTROL Filterbedingungen]** aus, um die Abfrageergebnisse einzuschränken, und klicken Sie auf **[!UICONTROL Weiter]**.
1. Das Fenster **[!UICONTROL Zielelement]** dient der Konfiguration der Filterbedingungen.

   Definieren Sie die folgende Filterbedingung: Empfänger, deren E-Mail-Domain gleich &quot;orange.co.uk&quot; ist. Wählen Sie dazu **E-Mail-Domain (@email)** im **[!UICONTROL Ausdruck]** Spalte, wählen **gleich** im **[!UICONTROL Operator]** und geben Sie &quot;orange.co.uk&quot;in der **[!UICONTROL Wert]** Spalte.

   ![](assets/query_editor_05.png)

1. Bei Bedarf können Sie die Schaltfläche **[!UICONTROL Werteverteilung]** auswählen. Dann werden die in der Datenbank enthaltenen E-Mail-Domains und deren Häufigkeit angezeigt. Auch alle anderen Domains werden angezeigt, da der Filter noch nicht aktiv ist.

   Die Zusammenfassung der Abfrage wird unten im Fenster angezeigt, hier also **E-Mail-Domain gleich web.de**.

1. Klicken Sie nun auf **[!UICONTROL Vorschau]**, um die Ergebnisse der Abfrage zum bisherigen Zeitpunkt anzusehen. Es werden nur Empfänger angezeigt, deren E-Mail-Domain &quot;web.de&quot; ist.

   ![](assets/query_editor_nveau_17.png)

1. Ändern Sie die Abfrage, um nur die Empfänger anzuzeigen, die nicht in Berlin wohnen.

   Wählen Sie **[!UICONTROL Ort (location/@city)]** in der Spalte **[!UICONTROL Ausdruck]**, den Operator **[!UICONTROL ungleich]** und geben Sie **[!UICONTROL Berlin]** in der Spalte **[!UICONTROL Wert]** ein.

   ![](assets/query_editor_08.png)

1. Im Fenster **[!UICONTROL Datenformatierung]** können Sie die Anzeigereihenfolge der Ausgabespalten festlegen. Benutzen Sie die Pfeile, um die Zeile &quot;Ort&quot; nach oben unmittelbar unter &quot;Kundennummer&quot; zu verschieben.

   Entfernen Sie das Kreuz aus der &quot;Vorname&quot;-Checkbox, um dieses Feld im Ergebnis nicht anzuzeigen.

   ![](assets/query_editor_nveau_15.png)

1. Im letzten Schritt, der **[!UICONTROL Datenvorschau]**, wird das Abfrageergebnis berechnet. Klicken Sie hierfür auf **[!UICONTROL Datenvorschau starten]**.

   Im Tab **[!UICONTROL Ergebnis in Spalten]** wird das Ergebnis der Abfrage in Spaltenform angezeigt.

   Die Ergebnistabelle enthält alle Empfänger, deren E-Mail-Domain &quot;web.de&quot; ist, und die nicht in Berlin wohnen. Die Vornamen werden nicht angezeigt, da diese Spalte im verangehenden Schritt abgewählt wurde. Die Kundennummern wurden in absteigender Reihenfolge sortiert.

   ![](assets/query_editor_nveau_12.png)

   Im Tab **[!UICONTROL XML-Ergebnis]** können Sie das Ergebnis im XML-Format einsehen.

   ![](assets/query_editor_nveau_13.png)

   Klicken Sie auf **[!UICONTROL Erzeugte SQL-Abfragen]**, um die SQL-Entsprechung der Abfrage anzusehen.

   ![](assets/query_editor_nveau_14.png)
