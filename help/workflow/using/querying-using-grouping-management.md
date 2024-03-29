---
product: campaign
title: Abfrage mit Gruppierungsverwaltung
description: Erfahren Sie, wie Sie Abfragen mit Hilfe der Gruppierungsverwaltung durchführen können
badge-v7-only: label="v7" type="Informative" tooltip="Gilt nur für Campaign Classic v7"
feature: Query Editor, Workflows
exl-id: 23bccb48-60ab-46c9-be26-2fa35243d61e
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 82%

---

# Abfrage mit Gruppierungsverwaltung {#querying-using-grouping-management}



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

1. Im **[!UICONTROL Zu extrahierende Daten]** auswählen, wählen Sie die **[!UICONTROL E-Mail-Domain]** und **[!UICONTROL Primärer Schlüssel]** -Felder. Führen Sie eine Zählung für die **[!UICONTROL Primärer Schlüssel]** -Feld.

   Weiterführende Informationen zu Primärschlüsselzählungen finden Sie in [diesem Abschnitt](../../platform/using/defining-filter-conditions.md#building-expressions).

1. Kreuzen Sie die Option **[!UICONTROL Gruppierungen verwalten (GROUP BY + HAVING)]** an.

   ![](assets/query_editor_nveau_29.png)

1. Im **[!UICONTROL Sortierung]** -Fenster E-Mail-Domains in absteigender Reihenfolge sortieren. Überprüfen Sie hierzu die Option **[!UICONTROL Ja]** im **[!UICONTROL Absteigende Sortierung]** Spalte. Klicken Sie auf **[!UICONTROL Weiter]**.

   ![](assets/query_editor_nveau_70.png)

1. In **[!UICONTROL Datenfilterung]** auswählen **[!UICONTROL Filterbedingungen]**. Navigieren Sie zu **[!UICONTROL Zielelemente]** Fenster und klicken Sie auf **[!UICONTROL Nächste]**.
1. Klicken Sie im Fenster **[!UICONTROL Gruppierung der Daten]** auf **[!UICONTROL Hinzufügen]** und wählen Sie das Feld **[!UICONTROL E-Mail-Domain]** aus.

   Die Gruppierung (GROUP BY) erfolgt an dieser Stelle. Das Fenster wird nur angezeigt, wenn die Option **[!UICONTROL Gruppierungen verwalten (GROUP BY + HAVING)]** angekreuzt wurde.

   ![](assets/query_editor_blocklist_04.png)

1. Geben Sie anschließend im Fenster **[!UICONTROL Gruppierbedingung]** eine Primärschlüsselanzahl von über 30 an. So werden nur die E-Mail-Domains ausgegeben, die mehr als 30-mal kontaktiert wurden.

   Dieses Fenster wird ebenfalls nur angezeigt, wenn die Option **[!UICONTROL Gruppierungen verwalten (GROUP BY + HAVING)]** angekreuzt wurde. Hier erfolgt die Filterung des Ergebnisses der Gruppierung (HAVING).

   ![](assets/query_editor_blocklist_05.png)

1. Da in unserem Beispiel keine spezielle Formatierung erforderlich ist, können Sie im Fenster **[!UICONTROL Datenformatierung]** direkt auf **[!UICONTROL Weiter]** klicken.
1. Klicken Sie anschließend auf **[!UICONTROL Datenvorschau starten]**. Das Ergebnis zeigt nur eine E-Mail-Domain, die mehr als 30-mal kontaktiert wurde.

   ![](assets/query_editor_blocklist_06.png)
