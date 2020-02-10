---
title: Wiederherstellen von Version 5.11
seo-title: Wiederherstellen von Version 5.11
description: Wiederherstellen von Version 5.11
seo-description: null
page-status-flag: never-activated
uuid: 4480c97c-5845-483c-a17b-644f05783b4e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: rollback
discoiquuid: ef778333-8e50-402b-9a69-78ac94497c67
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 9482a99c3be164651b3428179388cb0a8a75783f

---


# Wiederherstellen von Version 5.11{#restoring-v}

Im Folgenden finden Sie das Verfahren zum Wiederherstellen einer Version 5.11 von v7.

1. Stellen Sie die Sicherung der Datenbank wieder her und stellen Sie sie wieder her.
1. Stellen Sie den **Ordner &quot;Neolane v5.back** &quot;(**nl5.back** unter Linux) wieder her, benennen Sie ihn in &quot; **Neolane v5** &quot;(**nl5** unter Linux) um und stellen Sie ihn an seinem ursprünglichen Speicherort wieder her.
1. Konfigurieren Sie IIS neu, indem Sie die Listen-Ports neu zuweisen, um die Integration von Neolane v5 auf IIS-Website-Ebene wiederherzustellen.
1. Beenden Sie den Adobe Campaign v7-Dienst.
1. Starten Sie IIS neu.
1. Starten Sie den Adobe Campaign v5-Dienst neu.

