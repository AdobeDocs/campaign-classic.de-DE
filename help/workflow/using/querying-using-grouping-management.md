---
title: Abfrage mit Gruppierungsbedingungen
description: Erfahren Sie, wie Sie mit Gruppierungsbedingungen Abfragen durchführen können
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
source-wordcount: '309'
ht-degree: 100%

---


# Abfrage mit Gruppierungsbedingungen {#querying-using-grouping-management}

Im folgenden Beispiel werden die E-Mail-Domains gesucht, die bei früheren Sendungen mehr als 30-mal kontaktiert wurden.

* Welche Tabelle soll ausgewählt werden?

   Die Empfängertabelle (nms:recipient)

* Felder, die als Ausgabespalten verwendet werden sollen?

   E-Mail-Domain und Primärschlüssel (mit Zählung)

* Nach welchen Kriterien werden die Daten gruppiert?

   Nach E-Mail-Domain mit einer Primärschlüsselanzahl von über 30. Hierfür wird die Funktion **[!UICONTROL Gruppierungen verwalten (GROUP BY + HAVING)]** ) verwendet, welche sowohl die Gruppierung (&quot;group by&quot;) als auch die Filterung (&quot;having&quot;) der Daten erlaubt, die gruppiert wurden.****

Gehen Sie wie folgt vor:

1. Öffnen Sie das **[!UICONTROL generische Abfragetool]** und wählen Sie die Empfängertabelle (**nms:recipient**).

   ![](assets/query_editor_02.png)

1. Wählen Sie im Fenster **[!UICONTROL Zu extrahierende Daten]** das Feld **[!UICONTROL E-Mail-Domain]** aus und konfigurieren Sie eine Zählung des Felds **[!UICONTROL Primärschlüssel]**.****

   Weiterführende Informationen zu Primärschlüsselzählungen finden Sie in [diesem Abschnitt](../../platform/using/defining-filter-conditions.md#building-expressions).

1. Kreuzen Sie die Option **[!UICONTROL Gruppierungen verwalten (GROUP BY + HAVING)]** an.

   ![](assets/query_editor_nveau_29.png)

1. Ordnen Sie im Fenster **[!UICONTROL Sortierung]** die E-Mail-Domains in absteigender Reihenfolge. Kreuzen Sie hierfür in der Spalte **[!UICONTROL Absteigende Sortierung]** die Option **[!UICONTROL Ja]** an. Klicken Sie anschließend auf **[!UICONTROL Weiter]**.

   ![](assets/query_editor_nveau_70.png)

1. Wählen Sie im Fenster **[!UICONTROL Datenfilter]** die Option **[!UICONTROL Filterbedingungen]** und klicken Sie im Fenster **[!UICONTROL Zielelement]** auf **[!UICONTROL Weiter]**.
1. Klicken Sie im Fenster **[!UICONTROL Gruppierung der Daten]** auf **[!UICONTROL Hinzufügen]** und wählen Sie das Feld **[!UICONTROL E-Mail-Domain]** aus.

   Die Gruppierung (GROUP BY) erfolgt an dieser Stelle. Das Fenster wird nur angezeigt, wenn die Option **[!UICONTROL Gruppierungen verwalten (GROUP BY + HAVING)]** angekreuzt wurde.

   ![](assets/query_editor_blocklist_04.png)

1. Geben Sie anschließend im Fenster **[!UICONTROL Gruppierbedingung]** eine Primärschlüsselanzahl von über 30 an. So werden nur die E-Mail-Domains ausgegeben, die mehr als 30-mal kontaktiert wurden.

   Dieses Fenster wird ebenfalls nur angezeigt, wenn die Option **[!UICONTROL Gruppierungen verwalten (GROUP BY + HAVING)]** angekreuzt wurde. Hier erfolgt die Filterung des Ergebnisses der Gruppierung (HAVING).

   ![](assets/query_editor_blocklist_05.png)

1. Da in unserem Beispiel keine spezielle Formatierung erforderlich ist, können Sie im Fenster **[!UICONTROL Datenformatierung]** direkt auf **[!UICONTROL Weiter]** klicken.
1. Klicken Sie anschließend auf **[!UICONTROL Datenvorschau starten]**. Das Ergebnis zeigt nur eine E-Mail-Domain, die mehr als 30-mal kontaktiert wurde.

   ![](assets/query_editor_blocklist_06.png)
