---
product: campaign
title: Aggregat berechnen
description: Erfahren Sie, wie Sie Aggregate in Abfragen berechnen
feature: Workflows
hide: true
exl-id: 5b05788f-498b-4a84-bdde-2852900f0129
TQID: https://experienceleague.adobe.com/hr3jxs4JCrcPXdGBGN8I9edBG4FIg1AakOmWaN-Zplk
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
subfeature_v2: id: ee25c34b-ea50-427b-9369-ba0a160f7d70id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22fid: d1110311-2ca4-442b-be37-088a6db845ee
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 245
ht-degree: 62%

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

1. Konfigurieren Sie im Fenster **[!UICONTROL Zu extrahierende Daten]** wie im vorangehenden Beispiel eine Primärschlüssel-Zählung. Fügen Sie das Feld **[!UICONTROL Geschlecht]** zu den Ausgabespalten hinzu. Kreuzen Sie die Option **[!UICONTROL Gruppieren]** der Spalte **[!UICONTROL Geschlecht]** an. Auf diese Weise werden die Empfänger nach Geschlecht angeordnet.

   ![](assets/query_editor_nveau_27.png)

1. In diesem Beispiel ist keine **[!UICONTROL Sortierung]** erforderlich. Sie können somit direkt auf **[!UICONTROL Weiter]** klicken.
1. Konfigurieren Sie einen Datenfilter. Hier möchten Sie die Auswahl auf Kontakte beschränken, die in London leben.

   ![](assets/query_editor_22.png)

   >[!NOTE]
   >
   >Bei Werten wird zwischen Groß- und Kleinschreibung unterschieden. Wenn der Wert „London“ in die Bedingung ohne Großbuchstaben eingegeben wird und die Empfängerliste das Wort „London“ mit einem Großbuchstaben enthält, schlägt die Abfrage fehl.

1. Auch im Fenster **[!UICONTROL Datenformatierung]** können Sie direkt auf **[!UICONTROL Weiter]** klicken.
1. Klicken Sie anschließend auf **[!UICONTROL Datenvorschau starten]**.

   Es gibt drei separate Werte für jede Sortierung nach Geschlecht: **2** für weiblich, **1** für männlich und **0** wenn das Geschlecht unbekannt ist. In diesem Beispiel enthält die Liste 10 Frauen, 16 Männer und 2 Personen, deren Geschlecht nicht bekannt ist.

   ![](assets/query_editor_agregat_04.png)
