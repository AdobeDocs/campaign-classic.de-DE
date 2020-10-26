---
title: Ereignislöschung
seo-title: Ereignislöschung
description: Ereignislöschung
seo-description: null
page-status-flag: never-activated
uuid: bbce6813-dfa8-418c-9b52-06e814c15265
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: instance-configuration
discoiquuid: 2f643080-93b4-4c9f-80cf-b1770b149e6c
translation-type: ht
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: ht
source-wordcount: '92'
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
