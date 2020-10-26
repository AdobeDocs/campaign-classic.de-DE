---
title: Hinzufügung eines berechneten Auflistungsfelds
description: Erfahren Sie, wie Sie ein berechnetes Auflistungsfeld hinzufügen
page-status-flag: never-activated
uuid: 0556d53e-0fdf-47b3-b1e0-b52e85e0c662
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 7e5605c8-78f2-4011-b317-96a59c699848
translation-type: ht
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: ht
source-wordcount: '495'
ht-degree: 100%

---


# Hinzufügung eines berechneten Auflistungsfelds {#adding-an-enumeration-type-calculated-field}

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

   Geben Sie an, auf welche Spalte sich das berechnete Feld beziehen soll. Wählen Sie hierzu aus der Dropdown-Liste des Felds **[!UICONTROL Quellspalte]** die Spalte **[!UICONTROL Geschlecht]** aus. Die Zielwerte beziehen sich auf diese Spalte.****

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

   Führen Sie als Abwandlung die Abfrage erneut aus und geben Sie in der **[!UICONTROL Liste der Auflistungswerte]** den Wert &quot;2&quot; nicht an. Kreuzen Sie die Funktion **[!UICONTROL Warnhinweis erzeugen und fortfahren]** des Felds **[!UICONTROL Andernfalls]** an. In diesem Fall wird eine Warnung erzeugt, die besagt, dass der Wert &quot;2&quot; (Weiblich) nicht angegeben wurde. Dieser Hinweis wird im Bereich **[!UICONTROL Beim Export erzeugte Logs]** des Datenvorschaufensters angezeigt.

   ![](assets/query_editor_nveau_79.png)

   Kreuzen Sie nun stattdessen die Funktion **[!UICONTROL Fehler erzeugen und Zeile zurückweisen]** an. Alle Empfänger des Geschlechts &quot;2&quot; werden als Fehler ausgegeben und alle anderen Informationen der Zeile (Nachname, Vorname usw.) werden ebenfalls nicht angezeigt. Im Feld **[!UICONTROL Beim Export erzeugte Logs]** des Datenvorschaufensters wird eine entsprechende Fehlernachricht ausgegeben.

   ![](assets/query_editor_nveau_80.png)
