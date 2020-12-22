---
solution: Campaign Classic
product: campaign
title: Ereignislöschung
description: Ereignislöschung
audience: message-center
content-type: reference
topic-tags: instance-configuration
translation-type: tm+mt
source-git-commit: 5bc6c8a824929c6a61cf562fc961e5bdd1867837
workflow-type: tm+mt
source-wordcount: '90'
ht-degree: 78%

---


# Ereignislöschung{#purging-events}

Sie können den [Bereitstellungsassistenten](../../production/using/database-cleanup-workflow.md#deployment-wizard) verwenden, um zu konfigurieren, wie lange die Daten in der Datenbank gespeichert werden sollen.

Die Bereinigung der Ereignisse wird automatisch vom Workflow [](../../production/using/database-cleanup-workflow.md)Datenbankbereinigung durchgeführt. Es handelt sich dabei um die in den Ausführungsinstanzen empfangenen und gespeicherten sowie die in der Kontrollinstanz mit Verlauf gespeicherten Ereignisse.

Um die Bereinigungsparameter zu ändern, nutzen Sie die aufsteigenden und absteigenden Pfeile.

Bereinigungsparameter in Kontrollinstanzen:

![](assets/messagecenter_delete_events_001.png)

Bereinigungsparamter in Ausführungsinstanzen:

![](assets/messagecenter_delete_events_002.png)

Weiterführende Informationen zum Datenbankbereinigungs-Workflows finden Sie in [diesem Abschnitt](../../production/using/database-cleanup-workflow.md).
