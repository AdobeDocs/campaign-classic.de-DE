---
solution: Campaign Classic
product: campaign
title: Ereignislöschung
description: Ereignislöschung
audience: message-center
content-type: reference
topic-tags: instance-configuration
translation-type: ht
source-git-commit: 5bc6c8a824929c6a61cf562fc961e5bdd1867837
workflow-type: ht
source-wordcount: '90'
ht-degree: 100%

---


# Ereignislöschung{#purging-events}

Die Dauer der Speicherung der Ereignisse in der Datenbank kann über den [Implementierungsassistenten](../../production/using/database-cleanup-workflow.md#deployment-wizard) konfiguriert werden.

Die Bereinigung der Ereignisse wird automatisch vom [Datenbankbereinigungs-Workflow](../../production/using/database-cleanup-workflow.md) durchgeführt. Gelöscht werden dabei die in den Ausführungsinstanzen empfangenen und gespeicherten Ereignisse sowie die in der Kontrollinstanz archivierten Ereignisse.

Um die Bereinigungsparameter zu ändern, nutzen Sie die aufsteigenden und absteigenden Pfeile.

Bereinigungsparameter in Kontrollinstanzen:

![](assets/messagecenter_delete_events_001.png)

Bereinigungsparamter in Ausführungsinstanzen:

![](assets/messagecenter_delete_events_002.png)

Weiterführende Informationen zum Datenbankbereinigungs-Workflows finden Sie in [diesem Abschnitt](../../production/using/database-cleanup-workflow.md).
