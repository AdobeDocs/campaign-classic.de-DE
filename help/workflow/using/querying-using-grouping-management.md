---
product: campaign
title: Abfrage mit Gruppierungsverwaltung
description: Erfahren Sie, wie Sie Abfragen mit Hilfe der Gruppierungsverwaltung durchführen können
feature: Query Editor, Workflows
hide: true
exl-id: 23bccb48-60ab-46c9-be26-2fa35243d61e
TQID: https://experienceleague.adobe.com/jQoIc-ceJgiBqFrlPgDR1nm7PpcqLJedI36hnBQHrl0
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
subfeature_v2:
  - id: ee25c34b-ea50-427b-9369-ba0a160f7d70
  - id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22f
  - id: d1110311-2ca4-442b-be37-088a6db845ee
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 312
ht-degree: 100%

---

# Abfrage mit Gruppierungsverwaltung {#querying-using-grouping-management}



Im folgenden Beispiel werden die E-Mail-Domains gesucht, die bei früheren Sendungen mehr als 30-mal kontaktiert wurden.

* Welche Tabelle soll ausgewählt werden?

  Die Empfängertabelle (nms:recipient)

* Felder, die als Ausgabespalten verwendet werden sollen?

  E-Mail-Domain und Primärschlüssel (mit Zählung)

* Nach welchen Kriterien werden die Daten gruppiert?

  Nach E-Mail-Domain mit einer Anzahl von über 30 Primärschlüsseln. Dieser Vorgang wird mit der Option **[!UICONTROL Group by + Having]** ausgeführt. **[!UICONTROL Group by + Having]** ermöglicht die Gruppierung von Daten („group by“) und die Auswahl dessen, was gruppiert ist („having“).

Gehen Sie wie folgt vor:

1. Öffnen Sie das **[!UICONTROL generische Abfragetool]** und wählen Sie die Empfängertabelle (**nms:recipient**).

   ![](assets/query_editor_02.png)

1. Im Fenster **[!UICONTROL Zu extrahierende Daten]** wählen Sie die Felder **[!UICONTROL E-Mail-Domain]** und **[!UICONTROL Primärschlüssel]** aus. Führen Sie eine Zählung des Felds **[!UICONTROL Primärschlüssel]** durch.

   Weiterführende Informationen zu Primärschlüsselzählungen finden Sie in [diesem Abschnitt](../../platform/using/adobe-campaign-workspace.md#about-queries-in-campaign).

1. Kreuzen Sie die Option **[!UICONTROL Gruppierungen verwalten (GROUP BY + HAVING)]** an.

   ![](assets/query_editor_nveau_29.png)

1. Ordnen Sie im Fenster **[!UICONTROL Sortierung]** die E-Mail-Domains in absteigender Reihenfolge. Kreuzen Sie hierfür in der Spalte **[!UICONTROL Absteigende Sortierung]** die Option **[!UICONTROL Ja]** an. Klicken Sie auf **[!UICONTROL Weiter]**.

   ![](assets/query_editor_nveau_70.png)

1. Wählen Sie dann im Fenster **[!UICONTROL Datenfilter]** die Option **[!UICONTROL Filterbedingungen]**. Wechseln Sie zum Fenster **[!UICONTROL Zielelemente]** und klicken Sie auf **[!UICONTROL Weiter]**.
1. Klicken Sie im Fenster **[!UICONTROL Gruppierung der Daten]** auf **[!UICONTROL Hinzufügen]** und wählen Sie das Feld **[!UICONTROL E-Mail-Domain]** aus.

   Das Datengruppierungsfenster wird nur angezeigt, wenn die Option **[!UICONTROL Gruppierungen verwalten (GROUP BY + HAVING])** aktiviert wurde.

   ![](assets/query_editor_blocklist_04.png)

1. Geben Sie anschließend im Fenster **[!UICONTROL Gruppierbedingung]** eine Primärschlüsselanzahl von über 30 an. So werden nur die E-Mail-Domains ausgegeben, die mehr als 30-mal kontaktiert wurden.

   Dieses Fenster wird ebenfalls nur angezeigt, wenn die Option **[!UICONTROL Gruppierungen verwalten (GROUP BY + HAVING)]** angekreuzt wurde. Hier erfolgt die Filterung des Ergebnisses der Gruppierung (HAVING).

   ![](assets/query_editor_blocklist_05.png)

1. Da in unserem Beispiel keine spezielle Formatierung erforderlich ist, können Sie im Fenster **[!UICONTROL Datenformatierung]** direkt auf **[!UICONTROL Weiter]** klicken.
1. Klicken Sie anschließend auf **[!UICONTROL Datenvorschau starten]**. Das Ergebnis zeigt nur eine E-Mail-Domain, die mehr als 30-mal kontaktiert wurde.

   ![](assets/query_editor_blocklist_06.png)
