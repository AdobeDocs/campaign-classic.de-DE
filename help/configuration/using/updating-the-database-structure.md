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
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 10%

---


# Datenbankstruktur aktualisieren{#updating-the-database-structure}

Um die vorgenommenen Änderungen auf die Schema anzuwenden, starten Sie den Datenbankaktualisierungsassistenten. Auf diesen Assistenten können Sie über **[!UICONTROL Tools > Erweitert > Datenbankstruktur]** aktualisieren zugreifen. Es prüft, ob die physische Struktur der Datenbank mit der logischen Beschreibung übereinstimmt, und führt die SQL-Aktualisierungsskripte aus.

![](assets/d_ncs_integration_schema_update.png)

Die Module in der Datenbank werden automatisch ausgefüllt und aktiviert.

![](assets/d_ncs_integration_schema_update_select.png)

Die **[!UICONTROL Hinzufügen gespeicherten Prozeduren]** und die Optionen **[!UICONTROL Initialisierungsdaten]** importieren werden verwendet, um die ersten SQL-Skripte und die beim Erstellen der Datenbank ausgeführten Datenpackagen zu starten.

Sie können einen Datensatz aus einer externen Datenpackage importieren. Wählen Sie dazu &quot;Paket **[!UICONTROL importieren&quot;]** und geben Sie die XML-Datei des Pakets ein.

Führen Sie die Schritte aus und führen Sie die Ansicht des SQL-Datenbankupdates durch:

![](assets/d_ncs_integration_schema_update2.png)

>[!NOTE]
>
>Dies befindet sich in einem Bearbeitungsfeld und kann geändert werden, um SQL-Code zu löschen oder hinzuzufügen.

Starten Sie anschließend die Datenbankaktualisierung:

![](assets/d_ncs_integration_schema_update3.png)

