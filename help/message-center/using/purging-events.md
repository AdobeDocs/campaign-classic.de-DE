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
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Ereignislöschung{#purging-events}

Die Dauer der Speicherung der Ereignisse in der Datenbank kann ebenfalls über den Softwareverteilungs-Assistenten konfiguriert werden.

Die Ereignisbereinigung wird automatisch vom **[!UICONTROL Database cleanup]** Arbeitsablauf durchgeführt. Dieser Arbeitsablauf löscht die Ereignisse, die in den Ausführungsinstanzen und -ereignissen empfangen und gespeichert wurden, die auf einer Steuerelementinstanz archiviert wurden.

Um die Bereinigungsparameter zu ändern, nutzen Sie die aufsteigenden und absteigenden Pfeile.

Bereinigungsparameter in Kontrollinstanzen:

![](assets/messagecenter_delete_events_001.png)

Bereinigungsparamter in Ausführungsinstanzen:

![](assets/messagecenter_delete_events_002.png)

Weiterführende Informationen zum Datenbankbereinigungs-Workflows finden Sie in [diesem Abschnitt](../../production/using/database-cleanup-workflow.md).
