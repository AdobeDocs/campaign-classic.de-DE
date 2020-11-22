---
solution: Campaign Classic
product: campaign
title: Zurücksetzen auf vorherige Version
description: Hier erfahren Sie, wie Sie die frühere Version wiederherstellen.
audience: migration
content-type: reference
topic-tags: rollback
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 0%

---


# Zurücksetzen auf vorherige Version{#about-rollback}

Nach einer Migration müssen Sie bei Problemen möglicherweise die vorherige Version der Kampagne wiederherstellen.

Der Rollback-Vorgang hängt von Ihrer ursprünglichen Version der Kampagne ab.

## Wiederherstellen von v6.1

Im Folgenden finden Sie das Verfahren zum Wiederherstellen einer Version 6.1 von v7.

1. Stellen Sie die Sicherung der Datenbank wieder her und stellen Sie sie wieder her.
1. Stellen Sie den Ordner &quot; **Adobe Campaign v6.back** &quot;(**nl6.back** unter Linux) wieder her, benennen Sie ihn in **Adobe Campaign v6** (**nl6** unter Linux) um und stellen Sie ihn an seinem ursprünglichen Speicherort wieder her.
1. Konfigurieren Sie IIS neu, indem Sie die Listen-Ports neu zuweisen, um die Integration von Adobe Campaign v6.1 auf IIS-Website-Ebene wiederherzustellen.
1. Beenden Sie den Adobe Campaign v7-Dienst.
1. IIS erneut Beginn.
1. Starten Sie den Adobe Campaign v6.1-Dienst neu.

## Wiederherstellen auf Kampagne v6.02

Im Folgenden finden Sie das Verfahren zum Wiederherstellen einer Version v6.02 von v7.

1. Stellen Sie die Sicherung der Datenbank wieder her und stellen Sie sie wieder her.
1. Stellen Sie den Ordner **Neolane v6.back** (**nl6.back** in Linux) wieder her, benennen Sie ihn in **Neolane v6** (**nl6** in Linux) um und stellen Sie ihn an seinem ursprünglichen Speicherort wieder her.
1. Konfigurieren Sie IIS neu, indem Sie die Listen-Ports neu zuweisen, um die Integration von Adobe Campaign v6.02 auf IIS-Website-Ebene wiederherzustellen.
1. Beenden Sie den Dienst Adobe Campaign v6.1.
1. IIS erneut Beginn.
1. Starten Sie den Dienst Adobe Campaign v6.02 neu.

## Wiederherstellen auf Kampagne v5.11

Im Folgenden finden Sie das Verfahren zum Wiederherstellen einer Version 5.11 von v7.

1. Stellen Sie die Sicherung der Datenbank wieder her und stellen Sie sie wieder her.
1. Stellen Sie den **Ordner &quot;Neolane v5.back** &quot;(**nl5.back** unter Linux) wieder her, benennen Sie ihn in &quot; **Neolane v5** &quot;(**nl5** unter Linux) um und stellen Sie ihn an seinem ursprünglichen Speicherort wieder her.
1. Konfigurieren Sie IIS neu, indem Sie die Listen-Ports neu zuweisen, um die Integration von Neolane v5 auf IIS-Website-Ebene wiederherzustellen.
1. Beenden Sie den Adobe Campaign v7-Dienst.
1. IIS erneut Beginn.
1. Beginn Sie den Adobe Campaign v5-Dienst erneut.
