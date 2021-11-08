---
product: campaign
title: Datenbankstruktur aktualisieren
description: Datenbankstruktur aktualisieren
audience: configuration
content-type: reference
topic-tags: editing-schemas
exl-id: 6c1e061b-8636-4285-8d83-97474544d252
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '151'
ht-degree: 49%

---

# Datenbankstruktur aktualisieren{#updating-the-database-structure}

![](../../assets/v7-only.svg)

Um die Änderungen an den Schemas anzuwenden, starten Sie den Datenbankaktualisierungs-Assistenten. Auf diesen Assistenten kann über **[!UICONTROL Tools > Erweitert > Datenbankstruktur aktualisieren]** . Er prüft, ob die physische Struktur der Datenbank mit ihrer logischen Beschreibung übereinstimmt, und führt die SQL-Aktualisierungs-Scripts aus.

![](assets/d_ncs_integration_schema_update.png)

Die Module in der Datenbank werden automatisch ausgefüllt und aktiviert.

![](assets/d_ncs_integration_schema_update_select.png)

Die **[!UICONTROL Gespeicherte Prozeduren hinzufügen]** und **[!UICONTROL Initialisierungsdaten importieren]** -Optionen werden verwendet, um die ursprünglichen SQL-Skripte und die bei der Erstellung der Datenbank ausgeführten Datenpackages zu starten.

Sie können einen Datensatz aus einem externen Datenpaket importieren. Wählen Sie dazu **[!UICONTROL Package importieren]** und geben Sie die XML-Datei des Pakets ein.

Führen Sie die Schritte aus und sehen Sie sich das SQL-Script für Datenbank-Update an:

![](assets/d_ncs_integration_schema_update2.png)

>[!NOTE]
>
>Es befindet sich in einem Bearbeitungsfeld und kann geändert werden, indem SQL-Code gelöscht oder hinzugefügt wird.

Starten Sie anschließend das Datenbank-Update:

![](assets/d_ncs_integration_schema_update3.png)
