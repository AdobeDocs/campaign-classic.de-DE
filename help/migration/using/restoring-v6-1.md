---
title: Wiederherstellen von Version 6.1
seo-title: Wiederherstellen von Version 6.1
description: Wiederherstellen von Version 6.1
seo-description: null
page-status-flag: never-activated
uuid: 3fb71b6f-4d70-4814-a885-4d414a542eca
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: rollback
discoiquuid: e510482c-a56d-4254-90f8-19bd5c545e30
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 9482a99c3be164651b3428179388cb0a8a75783f

---


# Wiederherstellen von Version 6.1{#restoring-v}

Im Folgenden finden Sie das Verfahren zum Wiederherstellen einer Version 6.1 von v7.

1. Stellen Sie die Sicherung der Datenbank wieder her und stellen Sie sie wieder her.
1. Stellen Sie den Ordner **Adobe Campaign v6.back** (**nl6.back** in Linux) wieder her, benennen Sie ihn in **Adobe Campaign v6** (**nl6** in Linux) um und stellen Sie ihn an seinem ursprünglichen Speicherort wieder her.
1. Konfigurieren Sie IIS neu, indem Sie die Listen-Ports neu zuweisen, um die Integration von Adobe Campaign v6.1 auf IIS-Website-Ebene wiederherzustellen.
1. Beenden Sie den Adobe Campaign v7-Dienst.
1. Starten Sie IIS neu.
1. Starten Sie den Adobe Campaign v6.1-Dienst neu.

