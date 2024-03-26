---
product: campaign
title: Abfrage mit einer Viele-zu-viele-Beziehung
description: Erfahren Sie, wie Sie mit einer Viele-zu-viele-Beziehung Abfragen durchführen können
badge-v7-only: label="v7" type="Informative" tooltip="Gilt nur für Campaign Classic v7"
feature: Query Editor, Workflows
exl-id: e1d40ba1-2493-45c1-bd54-af9cb332028d
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '482'
ht-degree: 64%

---

# Abfrage mit einer Viele-zu-viele-Beziehung {#querying-using-a-many-to-many-relationship}



In diesem Beispiel werden die Empfänger gesucht, die innerhalb der letzten sieben Tage nicht kontaktiert wurden.

Außerdem wird die Konfiguration eines von einem Sammlungselement (orangefarbener Knoten) ausgehenden Filters gezeigt. Auf Sammlungselemente kann im Fenster **[!UICONTROL Feldauswahl]** zugegriffen werden.

* Welche Tabelle soll ausgewählt werden?

  Die Empfängertabelle (**nms:recipient**)

* Felder, die als Ausgabespalten verwendet werden sollen?

  Primärschlüssel, Nachname, Vorname und E-Mail

* Nach welchen Kriterien sind die Empfänger zu filtern?

  Nach den Versandlogs der Empfänger, bis 7 Tage vor dem Tagesdatum

Gehen Sie wie folgt vor:

1. Öffnen Sie das generische Abfragetool und wählen Sie die Empfängertabelle (**[!UICONTROL nms:recipient]**).
1. Wählen Sie im Fenster **[!UICONTROL Zu extrahierende Daten]** die Felder **[!UICONTROL Primärschlüssel]**, **[!UICONTROL Vorname]**, **[!UICONTROL Nachname]** und **[!UICONTROL E-Mail]**.

   ![](assets/query_editor_nveau_33.png)

1. Ordnen Sie im Sortierfenster die Nachnamen in alphabetischer Reihenfolge.

   ![](assets/query_editor_nveau_34.png)

1. Wählen Sie dann im **[!UICONTROL Datenfilter]**-Fenster die Option **[!UICONTROL Filterbedingungen]**.
1. Anschließend wird im Fenster **[!UICONTROL Zielelement]** in zwei Schritten die gesuchte Filterbedingung erstellt. Es handelt sich bei dem auszuwählenden Kollektionselement um eine n:n-Relation.

   * Wählen Sie also im **[!UICONTROL Ausdruck]**-Feld das durch einen orangefarbenen Knoten symbolisierte Sammlungselement **[!UICONTROL Versandlogs der Empfänger (broadLog)]**.

     ![](assets/query_editor_nveau_67.png)

     In diesem Fall ist der zu wählende Operator **[!UICONTROL nicht wie]** und es wird kein Wert angegeben.

   * Der Inhalt der zweiten Filterbedingung hängt von der ersten ab. Hier wird die **[!UICONTROL Ereignisdatum]** direkt im Feld **[!UICONTROL Versandlogs der Empfänger]** -Tabelle, da ein Link zu dieser Tabelle vorhanden ist.

     ![](assets/query_editor_nveau_36.png)

     Auswählen **[!UICONTROL Ereignisdatum]** mit dem **[!UICONTROL größer als oder gleich]** Operator. Wählen Sie die **[!UICONTROL DaysAgo (7)]** -Wert. Klicken Sie dazu auf **[!UICONTROL Ausdruck bearbeiten]** im **[!UICONTROL Wert]** -Feld. Im **[!UICONTROL Formeltyp]** auswählen **[!UICONTROL Datumsfunktionen]** und **[!UICONTROL Aktuelles Datum minus n Tage]**, wobei &quot;7&quot;als Wert angegeben wird.

     ![](assets/query_editor_nveau_37.png)

     Hiermit ist die Konfiguration der Filterbedingung abgeschlossen.

     ![](assets/query_editor_nveau_38.png)

1. Im **[!UICONTROL Datenformatierung]** -Fenster die Nachnamen in Großbuchstaben ändern. Klicken Sie auf **[!UICONTROL Nachname]** in der **[!UICONTROL Transformation]** und wählen Sie **[!UICONTROL Alles in Großbuchstaben]** im Dropdown-Menü.

   ![](assets/query_editor_nveau_39.png)

1. Verwenden Sie die Funktion **[!UICONTROL Berechnetes Feld hinzufügen]**, um eine neue Spalte zu erstellen.

   Fügen Sie in diesem Beispiel ein berechnetes Feld mit dem Vor- und Nachnamen der Empfänger in einer Spalte hinzu. Klicken Sie auf **[!UICONTROL Berechnetes Feld hinzufügen]** -Funktion. Im **[!UICONTROL Definition eines berechneten Felds exportieren]** ein Fenster, einen Titel und einen internen Namen eingeben und die **[!UICONTROL JavaScript-Ausdruck]** Typ. Geben Sie dann den folgenden Ausdruck ein:

   ```
   var rep = source._firstName+" - "+source._lastName
   return rep
   ```

   ![](assets/query_editor_nveau_40.png)

   Klicks **[!UICONTROL OK]**. Die **[!UICONTROL Datenformatierung]** -Fenster konfiguriert wurde.

   Weiterführende Informationen zum Hinzufügen berechneter Felder finden Sie in diesem Abschnitt.

1. Im Fenster **[!UICONTROL Datenvorschau]** können Sie das Ergebnis prüfen. Es werden die Empfänger angezeigt, die innerhalb der letzten sieben Tage vor dem aktuellen Tagesdatum nicht kontaktiert worden sind. Die Nachnamen sind in Großbuchstaben und alphabetisch geordnet. Eine weitere Spalte zeigt Vor- und Nachnamen in einem Feld an.

   ![](assets/query_editor_nveau_41.png)
