---
product: campaign
title: Zurücksetzen auf die vorherige Version
description: Erfahren Sie, wie Sie zur vorherigen Version zurückkehren.
feature: Upgrade
audience: migration
content-type: reference
topic-tags: rollback
hide: true
hidefromtoc: true
exl-id: 5120a7c4-3760-48d9-94da-d587d333e8d8
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '124'
ht-degree: 0%

---

# Zurücksetzen auf die vorherige Version{#about-rollback}



Nach einer Migration müssen Sie bei Problemen möglicherweise zur vorherigen Version von Campaign zurückkehren.

Das Rollback-Verfahren hängt von Ihrer ursprünglichen Version von Campaign ab.

Im Folgenden finden Sie das Verfahren zum Wiederherstellen einer v6.1 von v7.

1. Stellen Sie die Sicherung der Datenbank wieder her und stellen Sie sie wieder her.
1. Wiederherstellen der **Adobe Campaign v6.back** Ordner (**nl6.back** in Linux) umbenennen. **Adobe Campaign v6** (**nl6** in Linux) und stellen Sie ihn wieder an seinem ursprünglichen Speicherort her.
1. Konfigurieren Sie IIS neu, indem Sie die Überwachungsanschlüsse neu zuweisen, um die Integration von Adobe Campaign v6.1 auf IIS-Website-Ebene wiederherzustellen.
1. Beenden Sie den Adobe Campaign v7-Dienst.
1. Starten Sie IIS neu.
1. Starten Sie den Adobe Campaign v6.1-Dienst neu.

<!--
	
## Restore to Campaign v6.02

Here is the procedure to restore a v6.02 from a v7.

1. Recover the backup of the database and restore it.
1. Recover the **Neolane v6.back** folder (**nl6.back** in Linux), rename it to **Neolane v6** (**nl6** in Linux) and restore it to its original location.
1. Re-configure IIS by re-assigning the listen ports to re-establish the integration of Adobe Campaign v6.02 at IIS Website level.
1. Stop the Adobe Campaign v6.1 service.
1. Re-start IIS.
1. Restart the Adobe Campaign v6.02 service.

## Restore to Campaign v5.11

Here is the procedure to restore a v5.11 from a v7.

1. Recover the backup of the database and restore it.
1. Recover the **Neolane v5.back** folder (**nl5.back** in Linux), rename it to **Neolane v5** (**nl5** in Linux) and restore it to its original location.
1. Re-configure IIS by re-assigning the listen ports to re-establish the integration of Neolane v5 at IIS Website level.
1. Stop the Adobe Campaign v7 service.
1. Re-start IIS.
1. Re-start the Adobe Campaign v5 service.

-->