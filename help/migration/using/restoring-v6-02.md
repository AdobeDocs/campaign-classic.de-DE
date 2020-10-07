---
title: Wiederherstellen von v6.02
seo-title: Wiederherstellen von v6.02
description: Wiederherstellen von v6.02
seo-description: null
page-status-flag: never-activated
uuid: df21209b-4825-42fa-a303-f383f872abb5
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: rollback
discoiquuid: 4f65ba19-e9f0-4425-b640-f27c61394859
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '86'
ht-degree: 9%

---


# Wiederherstellen von v6.02{#restoring-v}

Im Folgenden finden Sie das Verfahren zum Wiederherstellen einer Version v6.02 von v7.

1. Stellen Sie die Sicherung der Datenbank wieder her und stellen Sie sie wieder her.
1. Stellen Sie den Ordner **Neolane v6.back** (**nl6.back** in Linux) wieder her, benennen Sie ihn in **Neolane v6** (**nl6** in Linux) um und stellen Sie ihn an seinem ursprünglichen Speicherort wieder her.
1. Konfigurieren Sie IIS neu, indem Sie die Listen-Ports neu zuweisen, um die Integration von Adobe Campaign v6.02 auf IIS-Website-Ebene wiederherzustellen.
1. Beenden Sie den Dienst Adobe Campaign v6.1.
1. IIS erneut Beginn.
1. Starten Sie den Dienst Adobe Campaign v6.02 neu.

