---
product: campaign
title: Zurücksetzen auf die vorherige Version
description: Erfahren Sie, wie Sie zur vorherigen Version zurückkehren.
audience: migration
content-type: reference
topic-tags: rollback
exl-id: 5120a7c4-3760-48d9-94da-d587d333e8d8
source-git-commit: 8610d29a3df1080f1622a2cb3685c0961fb40092
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 0%

---

# Zurücksetzen auf die vorherige Version{#about-rollback}

![](../../assets/v7-only.svg)

Nach einer Migration müssen Sie bei Problemen möglicherweise zur vorherigen Version von Campaign zurückkehren.

Das Rollback-Verfahren hängt von Ihrer ursprünglichen Version von Campaign ab.

## Wiederherstellen auf Campaign v6.1

Im Folgenden finden Sie das Verfahren zum Wiederherstellen einer v6.1 von v7.

1. Stellen Sie die Sicherung der Datenbank wieder her und stellen Sie sie wieder her.
1. Wiederherstellen der **Adobe Campaign v6.back** Ordner (**nl6.back** in Linux) umbenennen. **Adobe Campaign v6** (**nl6** in Linux) und stellen Sie ihn wieder an seinem ursprünglichen Speicherort her.
1. Konfigurieren Sie IIS neu, indem Sie die Überwachungsanschlüsse neu zuweisen, um die Integration von Adobe Campaign v6.1 auf IIS-Website-Ebene wiederherzustellen.
1. Beenden Sie den Adobe Campaign v7-Dienst.
1. Starten Sie IIS neu.
1. Starten Sie den Adobe Campaign v6.1-Dienst neu.

## Wiederherstellen auf Campaign v6.02

Hier finden Sie das Verfahren zum Wiederherstellen einer v6.02 von einer v7.

1. Stellen Sie die Sicherung der Datenbank wieder her und stellen Sie sie wieder her.
1. Wiederherstellen der **Neolane v6.back** Ordner (**nl6.back** in Linux) umbenennen. **Neolane v6** (**nl6** in Linux) und stellen Sie ihn wieder an seinem ursprünglichen Speicherort her.
1. Konfigurieren Sie IIS neu, indem Sie die Überwachungsanschlüsse neu zuweisen, um die Integration von Adobe Campaign v6.02 auf IIS-Website-Ebene wiederherzustellen.
1. Beenden Sie den Adobe Campaign v6.1-Dienst.
1. Starten Sie IIS neu.
1. Starten Sie den Adobe Campaign v6.02-Dienst neu.

## Wiederherstellen auf Campaign v5.11

Hier finden Sie das Verfahren zum Wiederherstellen einer Version 5.11 von v7.

1. Stellen Sie die Sicherung der Datenbank wieder her und stellen Sie sie wieder her.
1. Wiederherstellen der **Neolane v5.back** Ordner (**nl5.back** in Linux) umbenennen. **Neolane v5** (**nl5** in Linux) und stellen Sie ihn wieder an seinem ursprünglichen Speicherort her.
1. Konfigurieren Sie IIS neu, indem Sie die Überwachungsanschlüsse neu zuweisen, um die Integration von Neolane v5 auf IIS-Website-Ebene wiederherzustellen.
1. Beenden Sie den Adobe Campaign v7-Dienst.
1. Starten Sie IIS neu.
1. Starten Sie den Adobe Campaign v5-Dienst neu.
