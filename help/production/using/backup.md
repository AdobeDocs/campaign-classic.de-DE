---
product: campaign
title: Backup
description: Backup
feature: Monitoring
badge-v7-prem: label="Nur On-Premise/Hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Gilt nur für Hybrid- und On-Premise-Bereitstellungen"
audience: production
content-type: reference
topic-tags: data-processing
exl-id: e5ef6aba-dc22-4c8d-9fbb-13d507181b65
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 7%

---

# Backup{#backup}

Eine Sicherung ist unerlässlich, um zu verhindern, dass Daten im Falle eines (physischen oder systembezogenen) Problems auf einem Computer verloren gehen.

Die Daten werden an zwei verschiedenen Speicherorten gespeichert:

* physische Dateien werden in den Adobe Campaign-Verzeichnissen gespeichert;
* andere Daten in der Datenbank gespeichert werden.

Die meisten Daten befinden sich in der Datenbank. Dies entspricht 99 % der zu sichernden Informationen.

## Physische Dateien {#physical-files}

Dateien sind in mehrere Kategorien unterteilt:

* Konfigurationsdateien, die in **nl6/conf** gespeichert sind, ermöglichen eine sehr schnelle Neukonfiguration von Adobe Campaign.

* Weiterleitungsdateien, die in **nl6/var/`<instance-name>`/redir** gespeichert sind, befinden sich auf den Tracking-Servern (häufig als &quot;frontal&quot;bezeichnet) und beinhalten alle vorherigen Kampagnenumleitungen. Sie werden weiterhin von früheren Kampagnen verwendet.

* Protokolldateien, die in **nl6/var/`<instance-name>`/log** gespeichert sind, können zur Verfolgung von Problemen verwendet werden.

Die zu sichernden Verzeichnisse sind daher:

* nl6/conf

* nl6/var/`<instance-name>`/redir (für jede Instanz)

* nl6/var/`<instance-name>`/log (optional)

* nl6/var/`<instance-name>`/relay (optional)


## Datenbank {#database}

>[!IMPORTANT]
>
>Es ist unbedingt erforderlich, die Datenbank zu sichern.


Die Datenbank enthält alle in der Rich-Client-Konsole von Adobe Campaign angezeigten Informationen sowie alle Geschäftsdaten.

Für diesen Vorgang sind Ihr Hosting-Unternehmen und insbesondere dessen Datenbankadministratoren verantwortlich.
