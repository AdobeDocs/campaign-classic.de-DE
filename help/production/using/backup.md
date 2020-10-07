---
title: Backup
seo-title: Backup
description: Backup
seo-description: null
page-status-flag: never-activated
uuid: 50134154-a671-4534-b48d-a9e2c42e8f1a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: data-processing
discoiquuid: 870ab0f2-1bd7-42e7-8d83-a08a520b6587
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 2%

---


# Backup{#backup}

Die Sicherung ist unverzichtbar, um zu vermeiden, dass Daten im Ereignis eines Problems (physisch oder systembezogen) auf einem Computer verloren gehen.

Die Daten werden an zwei unterschiedlichen Speicherorten gespeichert:

* physikalische Dateien werden in den Adobe Campaign-Verzeichnissen gespeichert,
* andere Daten in der Datenbank gespeichert werden.

Die meisten Daten befinden sich in der Datenbank. Dies entspricht 99 % der zu sichernden Informationen.

## Physikalische Dateien {#physical-files}

Die Dateien sind in mehrere Kategorien unterteilt:

* Konfigurationsdateien unter **nl6/conf**

   Dadurch können Sie Adobe Campaign sehr schnell neu konfigurieren.

* Weiterleitungsdateien ** nl6/var/`<instancename>`/redir**

   Diese befinden sich auf den Tracking-Servern (häufig als &quot;frontal&quot;bezeichnet) und beinhalten alle vorherigen Kampagnen-Umleitungen. Sie werden weiterhin von vorherigen Kampagnen verwendet.

* Protokolldateien: **nl6/var/`<instancename>`/log**

   Diese können zur Verfolgung von Problemen verwendet werden.

Die zu sichernden Verzeichnisse sind daher:

* nl6/conf

* nl6/var/`<instanceName>`/redir (für jede Instanz)

* nl6/var/`<instanceName>`/log (optional)

* nl6/var/`<instanceName>`/relais (optional)

>[!CAUTION]
>
>Die Datenbank muss unbedingt gesichert werden.

## Datenbank {#database}

Die Datenbank enthält alle in der Rich-Client-Konsole des Adobe Campaigns angezeigten Informationen sowie alle Geschäftsdaten.

Für diesen Vorgang sind Ihre Hosting-Firma und insbesondere ihre Datenbankadministratoren verantwortlich.
