---
product: campaign
title: Erstellen des Datenschemas für FDA
description: Erfahren Sie, wie Sie das Datenschema für FDA erstellen
feature: Installation, Instance Settings, Federated Data Access
exl-id: 8702499b-1700-4d1f-a0e0-f7a9dfb4b88f
TQID: 'https://experienceleague.adobe.com/eC7jDm92g943ymcfEQjaeevS7qzIJWJR0zCtnP2Ny7o'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
    internal-label: Schemas
  - id: 7f0a1ee5-eeb8-5478-a9cd-b1896f033118
    internal-label: Instance Settings
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
subfeature_v2:
  - id: cfc95e9b-b035-4403-a6a9-b27a8a053a37
    internal-label: PI
  - id: e656c701-3899-4db3-989c-de0980ddfffa
    internal-label: Installation
  - id: ee3dfd63-9a21-4961-9f24-ea3385284a21
    internal-label: Federated Data Access
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 39%
---
# Erstellen des Datenschemas {#creating-the-data-schema}



So erstellen Sie ein Schema für eine externe Datenbank:

1. Klicken Sie auf die Schaltfläche **[!UICONTROL Neu]** über der Liste der Datenschemata und wählen Sie **[!UICONTROL Auf externe Daten zugreifen]**.

   ![](assets/wf_new_schema_fda.png)

1. Geben Sie einen **[!UICONTROL Namespace]** und **[!UICONTROL Name]** für das Schema ein und wählen Sie das **[!UICONTROL Externes Konto]** aus, das die Verbindung zur Datenbank ermöglicht. Dies ermöglicht den Zugriff auf die Liste der in der externen Datenbank verfügbaren Tabellen.

   ![](assets/wf_new_schema_select_table_fda.png)

1. Wählen Sie im Feld **[!UICONTROL Tabellenname]** die Tabelle aus, die die zu erfassenden Daten enthält.

   Bei Snowflake können Sie hier Ihre Ansichten auswählen, ob dem Datenbankbenutzer die richtigen Berechtigungen gewährt wurden. Beachten Sie, dass Adobe Campaign bei Verwendung von Ansichten das XML-Schema nicht automatisch generieren kann, sondern selbst erstellen muss. Weitere Informationen zu Ansichten finden Sie in der [Dokumentation zu Snowflake](https://docs.snowflake.com/en/user-guide/views-introduction.html).

   ![](assets/wf_new_schema_select_table_fda.png)

1. Klicken Sie zur Bestätigung auf **[!UICONTROL OK]**. Adobe Campaign erkennt die Struktur der ausgewählten Tabelle automatisch und erstellt das logische Schema. Beachten Sie, dass Adobe Campaign keine Verknüpfungen generiert.

1. Klicken Sie auf **[!UICONTROL Speichern]**, um die Erstellung zu bestätigen.

   >[!CAUTION]
   >
   >Bei Snowflake ist ein Primärschlüssel obligatorisch.

   ![](assets/wf_new_schema_generate_fda.png)

Die Indexe werden beim Mapping einer Tabelle automatisch erstellt (Standard- oder FDA-Mapping).
