---
product: campaign
title: Datenbankstruktur aktualisieren
description: Datenbankstruktur aktualisieren
feature: Configuration
role: Data Engineer, Developer
exl-id: 6c1e061b-8636-4285-8d83-97474544d252
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '151'
ht-degree: 57%

---

# Datenbankstruktur aktualisieren{#updating-the-database-structure}



Um die an den Schemata vorgenommenen Änderungen anzuwenden, starten Sie den Datenbankaktualisierungs-Assistenten. Auf diesen Assistenten können Sie über **[!UICONTROL Tools > Erweitert > Datenbankstruktur aktualisieren]** zugreifen. Er prüft, ob die physische Struktur der Datenbank mit ihrer logischen Beschreibung übereinstimmt, und führt die SQL-Aktualisierungs-Scripts aus.

![](assets/d_ncs_integration_schema_update.png)

Die Module in der Datenbank werden automatisch ausgefüllt und aktiviert.

![](assets/d_ncs_integration_schema_update_select.png)

Die Optionen **[!UICONTROL Gespeicherte Prozeduren hinzufügen]** und **[!UICONTROL Initialisierungsdaten importieren]** werden verwendet, um die ersten SQL-Skripte und die bei der Erstellung der Datenbank ausgeführten Datenpackages zu starten.

Sie können einen Datensatz aus einem externen Datenpaket importieren. Wählen Sie dazu **[!UICONTROL Package importieren]** aus und geben Sie die XML-Datei des Pakets ein.

Führen Sie die Schritte aus und sehen Sie sich das SQL-Script für Datenbank-Update an:

![](assets/d_ncs_integration_schema_update2.png)

>[!NOTE]
>
>Es befindet sich in einem Bearbeitungsfeld und kann geändert werden, indem SQL-Code gelöscht oder hinzugefügt wird.

Starten Sie anschließend das Datenbank-Update:

![](assets/d_ncs_integration_schema_update3.png)
