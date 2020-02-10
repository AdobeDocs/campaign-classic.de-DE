---
title: Aggregat berechnen
description: Erfahren Sie, wie Sie Aggregationsrechnungen in Abfragen durchführen
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


# Aggregat berechnen {#performing-aggregate-computing}

In diesem Beispiel wird die Anzahl der Empfänger gesucht, die in Berlin wohnen, geordnet nach Geschlecht.

* Welche Tabelle soll ausgewählt werden?

   Die Empfängertabelle (**nms:recipient**)

* Welche Felder sollen in der Ausgabespalte ausgewählt werden?

   Primärschlüssel (mit Zählung) und Geschlecht

* Nach welchen Kriterien sind die Empfänger zu filtern?

   Empfänger, die in Berlin wohnhaft sind

Gehen Sie wie folgt vor:

1. Definieren Sie in **[!UICONTROL Data to extract]** diesem Beispiel eine Anzahl für den Primärschlüssel (wie im vorherigen Beispiel gezeigt). Fügen Sie das **[!UICONTROL Gender]** Feld in der Spalte &quot;Ausgabe&quot;hinzu. Aktivieren Sie die **[!UICONTROL Group]** Option in der **[!UICONTROL Gender]** Spalte. Auf diese Weise werden die Empfänger nach Geschlecht gruppiert.

   ![](assets/query_editor_nveau_27.png)

1. In the **[!UICONTROL Sorting]** window, click **[!UICONTROL Next]**: no sorting is necessary here.
1. Konfigurieren Sie nun die Filterbedingung. Hier soll die Auswahl auf Empfänger beschränkt werden, die in Berlin wohnen.

   ![](assets/query_editor_22.png)

   >[!NOTE]
   >
   >Bei der Angabe von Werten ist die Groß- und Kleinschreibung zu beachten. Wenn Sie z. B. &#39;berlin&#39; eingeben, die Stadt Berlin in der Empfängerliste jedoch großgeschrieben ist, wird die Abfrage keine Ergebnisse ausgeben.

1. In the **[!UICONTROL Data formatting]** window, click **[!UICONTROL Next]**: no formatting is required for this example.
1. Klicken Sie im Vorschaufenster auf **[!UICONTROL Launch data preview]**.

   Bei einer Sortierung nach Geschlecht sind drei verschiedene Werte möglich: **2** für weiblich, **1** für männlich und **0**, wenn das Geschlecht nicht angegeben wurde. Diese Liste enthält 31 Frauen, 38 Männer und 1 Person ohne Geschlechtsangabe.

   ![](assets/query_editor_agregat_04.png)
