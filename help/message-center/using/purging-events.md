---
solution: Campaign Classic
product: campaign
title: Ereignislöschung
description: Ereignislöschung
audience: message-center
content-type: reference
topic-tags: instance-configuration
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '90'
ht-degree: 100%

---


# Ereignislöschung{#purging-events}

Die Dauer der Speicherung der Ereignisse in der Datenbank kann ebenfalls über den Softwareverteilungs-Assistenten konfiguriert werden.

Die Bereinigung der Ereignisse wird automatisch vom Workflow **[!UICONTROL Datenbankbereinigung]** durchgeführt. Es handelt sich dabei um die in den Ausführungsinstanzen empfangenen und gespeicherten sowie die in der Kontrollinstanz mit Verlauf gespeicherten Ereignisse.

Um die Bereinigungsparameter zu ändern, nutzen Sie die aufsteigenden und absteigenden Pfeile.

Bereinigungsparameter in Kontrollinstanzen:

![](assets/messagecenter_delete_events_001.png)

Bereinigungsparamter in Ausführungsinstanzen:

![](assets/messagecenter_delete_events_002.png)

Weiterführende Informationen zum Datenbankbereinigungs-Workflows finden Sie in [diesem Abschnitt](../../production/using/database-cleanup-workflow.md).
