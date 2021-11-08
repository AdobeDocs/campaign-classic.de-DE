---
product: campaign
title: Backup
description: Backup
audience: production
content-type: reference
topic-tags: data-processing
exl-id: e5ef6aba-dc22-4c8d-9fbb-13d507181b65
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 2%

---

# Backup{#backup}

![](../../assets/v7-only.svg)

Eine Sicherung ist unerlässlich, um zu verhindern, dass Daten im Falle eines (physischen oder systembezogenen) Problems auf einem Computer verloren gehen.

Die Daten werden an zwei verschiedenen Speicherorten gespeichert:

* physische Dateien werden in den Adobe Campaign-Verzeichnissen gespeichert;
* andere Daten in der Datenbank gespeichert werden.

Die meisten Daten befinden sich in der Datenbank. Dies entspricht 99 % der zu sichernden Informationen.

## Physische Dateien {#physical-files}

Dateien sind in mehrere Kategorien unterteilt:

* Konfigurationsdateien im **nl6/conf**

   Damit können Sie Adobe Campaign sehr schnell neu konfigurieren.

* Weiterleitungsdateien ** nl6/var/`<instancename>`/redir*

   Diese befinden sich auf den Tracking-Servern (häufig als &quot;frontal&quot; bezeichnet) und umfassen alle vorherigen Kampagnen-Umleitungen. Sie werden weiterhin von früheren Kampagnen verwendet.

* Protokolldateien: **nl6/var/`<instancename>`/log**

   Diese können zur Verfolgung von Problemen verwendet werden.

Die zu sichernden Verzeichnisse sind daher:

* nl6/conf

* nl6/var/`<instanceName>`/redir (für jede Instanz)

* nl6/var/`<instanceName>`/log (optional)

* nl6/var/`<instanceName>`/relay (optional)

>[!IMPORTANT]
>
>Es ist wichtig, die Datenbank zu sichern.

## Datenbank {#database}

Die Datenbank enthält alle in der Rich-Client-Konsole von Adobe Campaign angezeigten Informationen sowie alle Geschäftsdaten.

Für diesen Vorgang sind Ihr Hosting-Unternehmen und insbesondere dessen Datenbankadministratoren verantwortlich.
