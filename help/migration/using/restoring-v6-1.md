---
title: Wiederherstellen von v6.1
seo-title: Wiederherstellen von v6.1
description: Wiederherstellen von v6.1
seo-description: null
page-status-flag: never-activated
uuid: 3fb71b6f-4d70-4814-a885-4d414a542eca
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: rollback
discoiquuid: e510482c-a56d-4254-90f8-19bd5c545e30
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '88'
ht-degree: 9%

---


# Wiederherstellen von v6.1{#restoring-v}

Im Folgenden finden Sie das Verfahren zum Wiederherstellen einer Version 6.1 von v7.

1. Stellen Sie die Sicherung der Datenbank wieder her und stellen Sie sie wieder her.
1. Stellen Sie den Ordner &quot; **Adobe Campaign v6.back** &quot;(**nl6.back** unter Linux) wieder her, benennen Sie ihn in **Adobe Campaign v6** (**nl6** unter Linux) um und stellen Sie ihn an seinem ursprünglichen Speicherort wieder her.
1. Konfigurieren Sie IIS neu, indem Sie die Listen-Ports neu zuweisen, um die Integration von Adobe Campaign v6.1 auf IIS-Website-Ebene wiederherzustellen.
1. Beenden Sie den Adobe Campaign v7-Dienst.
1. IIS erneut Beginn.
1. Starten Sie den Adobe Campaign v6.1-Dienst neu.

