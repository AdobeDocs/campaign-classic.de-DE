---
product: campaign
title: Zugriff auf externe Datenbanken
description: Zugriff auf externe Datenbanken
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 8702499b-1700-4d1f-a0e0-f7a9dfb4b88f
source-git-commit: d2d0ff575edbee18febb5ec895fcec1e0ae34de7
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 45%

---

# Erstellen des Datenschemas {#creating-the-data-schema}

![](../../assets/v7-only.svg)

So erstellen Sie ein Schema für eine externe Datenbank:

1. Klicken Sie auf die Schaltfläche **[!UICONTROL Neu]** über der Liste der Datenschemata und wählen Sie **[!UICONTROL Auf externe Daten zugreifen]**.

   ![](assets/wf_new_schema_fda.png)

1. Geben Sie einen **[!UICONTROL Namespace]** und  **[!UICONTROL Name]** für das Schema und wählen Sie die **[!UICONTROL Externes Konto]** , wodurch eine Verbindung zur Datenbank hergestellt wird. Dies ermöglicht den Zugriff auf die Liste der in der externen Datenbank verfügbaren Tabellen.

   ![](assets/wf_new_schema_select_table_fda.png)

1. Aus dem **[!UICONTROL Tabellenname]** auswählen, wählen Sie die Tabelle aus, die die abzurufenden Daten enthält.

   Mit Snowflake können Sie hier Ihre Ansichten auswählen, wenn dem Datenbankbenutzer die richtigen Berechtigungen erteilt wurden. Beachten Sie, dass bei der Verwendung von Ansichten Adobe Campaign das XML-Schema nicht automatisch generieren kann und Sie es selbst erstellen müssen. Weitere Informationen zu Ansichten finden Sie unter [Dokumentation zu Snowflaken](https://docs.snowflake.com/en/user-guide/views-introduction.html).

   ![](assets/wf_new_schema_select_table_fda.png)

1. Klicken Sie zur Bestätigung auf **[!UICONTROL OK]**. Adobe Campaign erkennt die Struktur der ausgewählten Tabelle automatisch und erstellt das logische Schema. Beachten Sie, dass Adobe Campaign keine Verknüpfungen generiert.

1. Klicken Sie auf **[!UICONTROL Speichern]**, um die Erstellung zu bestätigen.

   >[!CAUTION]
   >
   >Bei Snowflake ist ein Primärschlüssel obligatorisch.

   ![](assets/wf_new_schema_generate_fda.png)

Die Indexe werden beim Mapping einer Tabelle automatisch erstellt (Standard- oder FDA-Mapping).
