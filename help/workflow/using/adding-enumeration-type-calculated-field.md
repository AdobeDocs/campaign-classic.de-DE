---
product: campaign
title: Hinzufügen eines berechneten Felds vom Typ "Aufzählung"
description: Erfahren Sie, wie Sie ein berechnetes Feld vom Typ "Aufzählung" hinzufügen
audience: workflow
content-type: reference
topic-tags: use-cases
feature: Workflows, Data Management
hide: true
hidefromtoc: true
exl-id: 3f606d3a-0af5-4315-bb08-1b21a71f1721
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '520'
ht-degree: 93%

---

# Hinzufügen eines berechneten Felds vom Typ &quot;Aufzählung&quot; {#adding-an-enumeration-type-calculated-field}



In der folgenden Abfrage wird ein **[!UICONTROL berechnetes Auflistungsfeld]** hinzugefügt. In der Ergebnisanzeige soll eine Spalte erzeugt werden, die das Geschlecht der Empfänger anzeigt: männlich (1), weiblich (2) oder unbestimmt (0).

* Welche Tabelle soll ausgewählt werden?

  Die Empfängertabelle (nms:recipient)

* Felder, die als Ausgabespalten verwendet werden sollen?

  Nachname, Vorname, Geschlecht

* Nach welchen Kriterien sind die Informationen zu filtern?

  Nach der Sprache der Empfänger

Gehen Sie wie folgt vor:

1. Öffnen Sie das **[!UICONTROL generische Abfragetool]** und wählen Sie die Empfängertabelle (nms:recipient).
1. Wählen Sie im Fenster **[!UICONTROL Zu extrahierende Daten]** die Felder **[!UICONTROL Nachname]**, **[!UICONTROL Vorname]** und **[!UICONTROL Geschlecht]**.

   ![](assets/query_editor_nveau_73.png)

1. In diesem Beispiel ist keine **[!UICONTROL Sortierung]** erforderlich. Sie können somit direkt auf **[!UICONTROL Weiter]** klicken.
1. Wählen Sie dann im **[!UICONTROL Datenfilter]**-Fenster die Option **[!UICONTROL Filterbedingungen]**.
1. Konfigurieren Sie im Fenster **[!UICONTROL Zielelement]** eine Bedingung, die als Ergebnis alle deutschsprachigen Empfänger ausgibt.

   ![](assets/query_editor_nveau_74.png)

1. Klicken Sie dann im Fenster **[!UICONTROL Datenformatierung]** auf die Schaltfläche **[!UICONTROL Berechnetes Feld hinzufügen]**.

   ![](assets/query_editor_nveau_75.png)

1. Wählen Sie im Feld **[!UICONTROL Typ]** des Fensters **[!UICONTROL Definition eines berechneten Export-Feldes]** die Option **[!UICONTROL Auflistungen]** aus.

   Definieren Sie die Spalte, auf die sich das neue berechnete Feld beziehen soll. Wählen Sie hierzu aus der Dropdown-Liste des Felds **[!UICONTROL Quellspalte]** die Spalte **[!UICONTROL Geschlecht]** aus. Die Zielwerte beziehen sich auf diese Spalte **[!UICONTROL Geschlecht]**.

   ![](assets/query_editor_nveau_76.png)

   Konfigurieren Sie **Quellwert** und **Zielwert**. Der Zielwert erleichtert die Lesbarkeit des Abfrageergebnisses, d. h. des Geschlechts der Empfänger (0, 1 oder 2).

   Klicken Sie für jedes Quell- und Zielwertpaar auf **[!UICONTROL Hinzufügen]** rechts oberhalb der **[!UICONTROL Liste der Auflistungswerte]**:

   * Geben Sie bei **[!UICONTROL Quellwert]** in neue Zeilen jeweils die dem Geschlecht entsprechenden Zahlenwerte ein (0, 1 und 2).
   * Geben Sie bei **[!UICONTROL Zielwert]** die den Zahlen entsprechende Bedeutung ein: &quot;Unbestimmt&quot; bei &quot;0&quot;, &quot;Männlich&quot; bei &quot;1&quot; und &quot;Weiblich&quot; bei &quot;2&quot;.

   Kreuzen Sie die Option **[!UICONTROL Quellwert]** beibehalten an und

   klicken Sie auf **[!UICONTROL OK]**, um die Konfiguration des berechneten Felds abzuschließen.

   ![](assets/query_editor_nveau_77.png)

1. Klicken Sie im Fenster **[!UICONTROL Datenformatierung]** auf **[!UICONTROL Weiter]**.
1. Nun können Sie die **[!UICONTROL Datenvorschau starten]**.

   Die berechnete Spalte zeigt an, welchem Geschlecht die drei Werte 0, 1 und 2 entsprechen:

   * 0 für &quot;Unbestimmt&quot;
   * 1 für &quot;Männlich&quot;
   * 2 für &quot;Weiblich&quot;

   ![](assets/query_editor_nveau_78.png)

   Wenn Sie beispielsweise in der **[!UICONTROL Liste der Auflistungswerte]** das Geschlecht „2“ nicht eingeben und die Funktion **[!UICONTROL Warnhinweis generieren und fortfahren]** des Feldes **[!UICONTROL Andernfalls]** ausgewählt ist, erhalten Sie ein Warnprotokoll. Dieses Protokoll zeigt an, dass das Geschlecht „2“ (weiblich) nicht eingegeben wurde. Dieser Hinweis wird im Bereich **[!UICONTROL Beim Export erzeugte Logs]** des Datenvorschaufensters angezeigt.

   ![](assets/query_editor_nveau_79.png)

   Nehmen wir ein anderes Beispiel und gehen wir davon aus, dass der Auflistungswert „2“ nicht eingegeben wurde. Wählen Sie die Funktion **[!UICONTROL Fehler erzeugen und Zeile ablehnen]** aus: Alle Empfänger mit „Geschlecht 2“ melden Anomalien, und die anderen Informationen in der Zeile (Vor- und Nachname usw.) werden nicht exportiert. Im Feld **[!UICONTROL Beim Export erzeugte Logs]** des Datenvorschaufensters wird eine entsprechende Fehlernachricht ausgegeben. Dieses Protokoll zeigt an, dass der Auflistungswert „2“ nicht eingegeben wurde.

   ![](assets/query_editor_nveau_80.png)
