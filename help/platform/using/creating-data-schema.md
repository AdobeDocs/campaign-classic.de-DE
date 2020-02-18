---
title: Zugriff auf externe Datenbanken
seo-title: Zugriff auf externe Datenbanken
description: Zugriff auf externe Datenbanken
seo-description: null
page-status-flag: never-activated
uuid: b84359b9-c584-431d-80d5-71146d9b6854
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dd3d14cc-5153-428d-a98a-32b46f0fe811
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 9a26ec7ed1c8463270ac9f97079f49e00d5b258e

---


# Erstellen des Datenschemas {#creating-the-data-schema}

So erstellen Sie ein Schema in einer externen Datenbank:

1. Klicken Sie auf die **[!UICONTROL New]** Schaltfläche über der Liste der Datenschemata und wählen Sie **[!UICONTROL Access external data]**.

   ![](assets/wf_new_schema_fda.png)

1. Geben Sie für das Schema einen Namen und eine Beschreibung ein und wählen Sie das externes Konto aus, über das die Verbindung mit der Datenbank hergestellt werden soll. Dadurch erhalten Sie Zugriff auf die Liste mit den in der externen Datenbank verfügbaren Tabellen. Wählen Sie die Tabelle aus, die die Daten enthält, die abgerufen werden sollen.

   ![](assets/wf_new_schema_select_table_fda.png)

1. Klicken Sie **[!UICONTROL OK]** zur Bestätigung. Adobe Campaign erkennt automatisch die Struktur der ausgewählten Tabelle und generiert das logische Schema. Beachten Sie, dass Adobe Campaign keine Links generiert.

1. Click **[!UICONTROL Save]** to confirm creation.

   >[!CAUTION]
   >
   >Bei Schneeflocken ist ein Primärschlüssel obligatorisch.

   ![](assets/wf_new_schema_generate_fda.png)

Die Indexe werden beim Mapping einer Tabelle automatisch erstellt (Standard- oder FDA-Mapping).
