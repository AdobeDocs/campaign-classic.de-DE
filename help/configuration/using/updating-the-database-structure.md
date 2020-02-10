---
title: Datenbankstruktur aktualisieren
seo-title: Datenbankstruktur aktualisieren
description: Datenbankstruktur aktualisieren
seo-description: null
page-status-flag: never-activated
uuid: 084dcc7b-f890-4dff-a322-c9a8f1d614b8
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: b82ae459-30b5-4a1c-91cc-5c7b8f128333
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Datenbankstruktur aktualisieren{#updating-the-database-structure}

Um die Änderungen an den Schemata anzuwenden, starten Sie den Assistenten zum Aktualisieren der Datenbank. Auf diesen Assistenten können Sie über **[!UICONTROL Tools > Advanced > Update database structure]** zugreifen. Es prüft, ob die physische Struktur der Datenbank mit der logischen Beschreibung übereinstimmt, und führt die SQL-Aktualisierungsskripte aus.

![](assets/d_ncs_integration_schema_update.png)

Die Module in der Datenbank werden automatisch ausgefüllt und aktiviert.

![](assets/d_ncs_integration_schema_update_select.png)

Die **[!UICONTROL Add stored procedures]** und **[!UICONTROL Import initialization data]** -Optionen werden zum Starten der anfänglichen SQL-Skripte und der beim Erstellen der Datenbank ausgeführten Datenpakete verwendet.

Sie können einen Datensatz aus einem externen Datenpaket importieren. Wählen Sie dazu die XML-Datei des Pakets aus **[!UICONTROL Import a package]** und geben Sie sie ein.

Führen Sie die folgenden Schritte aus und zeigen Sie das SQL-Skript für die Datenbankaktualisierung an:

![](assets/d_ncs_integration_schema_update2.png)

>[!NOTE]
>
>Dies befindet sich in einem Bearbeitungsfeld und kann geändert werden, um SQL-Code zu löschen oder hinzuzufügen.

Starten Sie anschließend die Datenbankaktualisierung:

![](assets/d_ncs_integration_schema_update3.png)

