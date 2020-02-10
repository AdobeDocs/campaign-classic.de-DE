---
title: Abfrage mit Gruppierungsbedingungen
description: Erfahren Sie, wie Sie mithilfe der Gruppenverwaltung Abfragen durchführen
page-status-flag: never-activated
uuid: 0556d53e-0fdf-47b3-b1e0-b52e85e0c662
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 7e5605c8-78f2-4011-b317-96a59c699848
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: cf7c90f0ea9fbce3a4fd53f24189617cbd33fc40

---


# Abfrage mit Gruppierungsbedingungen {#querying-using-grouping-management}

Im folgenden Beispiel werden die E-Mail-Domains gesucht, die bei früheren Sendungen mehr als 30-mal kontaktiert wurden.

* Welche Tabelle soll ausgewählt werden?

   Die Empfängertabelle (nms:recipient)

* Felder, die als Ausgabespalten verwendet werden sollen?

   E-Mail-Domain und Primärschlüssel (mit Zählung)

* Nach welchen Kriterien werden die Daten gruppiert?

   Basierend auf E-Mail-Domäne mit einer Anzahl von Primärschlüsseln über 30. Dieser Vorgang wird nach **[!UICONTROL Group by + Having]** Wahl durchgeführt. **[!UICONTROL Group by + Having]** können Sie Daten gruppieren (&quot;Gruppieren nach&quot;) und eine Auswahl dessen treffen, was gruppiert wurde (&quot;haben&quot;).

Gehen Sie wie folgt vor:

1. Open the **[!UICONTROL Generic query editor]** and choose the Recipient table (**nms:recipient**).

   ![](assets/query_editor_02.png)

1. Wählen Sie im **[!UICONTROL Data to extract]** Fenster die Felder **[!UICONTROL Email domain]** und **[!UICONTROL Primary key]** aus. Führen Sie eine Zählung für das **[!UICONTROL Primary key]** Feld aus.

   Weiterführende Informationen zu Primärschlüsselzählungen finden Sie in [diesem Abschnitt](../../platform/using/defining-filter-conditions.md#building-expressions).

1. Markieren Sie das **[!UICONTROL Handle groupings (GROUP BY + HAVING)]** Kästchen.

   ![](assets/query_editor_nveau_29.png)

1. Sortieren Sie im **[!UICONTROL Sorting]** Fenster E-Mail-Domänen in absteigender Reihenfolge. Dazu checken Sie **[!UICONTROL Yes]** die **[!UICONTROL Descending sort]** Spalte ein. Klicks **[!UICONTROL Next]**.

   ![](assets/query_editor_nveau_70.png)

1. Wählen Sie **[!UICONTROL Data filtering]** in **[!UICONTROL Filtering conditions]**. Gehen Sie zum **[!UICONTROL Target elements]** Fenster und klicken Sie auf **[!UICONTROL Next]**.
1. Wählen Sie im **[!UICONTROL Data grouping]** Fenster die **[!UICONTROL Email domain]** durch Klicken auf **[!UICONTROL Add]**.

   Dieses Fenster für die Datengruppierung wird nur angezeigt, wenn das **[!UICONTROL Handle groupings (GROUP BY + HAVING]**)-Feld markiert wurde.

   ![](assets/query_editor_blacklist_04.png)

1. In the **[!UICONTROL Grouping condition]** window, indicate a primary key count greater than 30 since we only want email domains targeted more than 30 times to be returned as results.

   This window appears when the **[!UICONTROL Manage groupings (GROUP BY + HAVING)]** box was checked: this is where the grouping result is filtered (HAVING).

   ![](assets/query_editor_blacklist_05.png)

1. Klicken Sie im **[!UICONTROL Data formatting]** Fenster auf **[!UICONTROL Next]**: hier ist keine Formatierung erforderlich.
1. In the data preview window, click **[!UICONTROL Launch data preview]**: here, three different email domains targeted over 30 times are returned.

   ![](assets/query_editor_blacklist_06.png)
