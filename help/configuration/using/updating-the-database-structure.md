---
product: campaign
title: Datenbankstruktur aktualisieren
description: Datenbankstruktur aktualisieren
feature: Configuration
role: Developer
exl-id: 6c1e061b-8636-4285-8d83-97474544d252
source-git-commit: 9f5205ced6b8d81639d4d0cb6a76905a753cddac
workflow-type: tm+mt
source-wordcount: '151'
ht-degree: 64%

---

# Datenbankstruktur aktualisieren{#updating-the-database-structure}



Um die an den Schemata vorgenommenen Änderungen anzuwenden, starten Sie den Datenbankaktualisierungsassistenten. Auf diesen Assistenten kann über **[!UICONTROL Tools > Erweitert > Datenbank aktualisieren]** zugegriffen werden. Er prüft, ob die physische Struktur der Datenbank mit ihrer logischen Beschreibung übereinstimmt, und führt die SQL-Aktualisierungs-Scripts aus.

![](assets/d_ncs_integration_schema_update.png)

Die Module in der Datenbank werden automatisch ausgefüllt und aktiviert.

![](assets/d_ncs_integration_schema_update_select.png)

Die Optionen **[!UICONTROL Gespeicherte Prozeduren hinzufügen]** und **[!UICONTROL Initialisierungsdaten importieren]** werden verwendet, um die anfänglichen SQL-Skripte und die Datenpakete zu starten, die beim Erstellen der Datenbank ausgeführt werden.

Sie können einen Datensatz aus einem externen Datenpaket importieren. Wählen Sie dazu **[!UICONTROL Paket importieren]** und geben Sie die XML-Datei des Pakets ein.

Führen Sie die Schritte aus und sehen Sie sich das SQL-Script für Datenbank-Update an:

![](assets/d_ncs_integration_schema_update2.png)

>[!NOTE]
>
>Es befindet sich in einem Bearbeitungsfeld und kann geändert werden, indem SQL-Code gelöscht oder hinzugefügt wird.

Starten Sie anschließend das Datenbank-Update:

![](assets/d_ncs_integration_schema_update3.png)
