---
product: campaign
title: Backup
description: Backup
feature: Monitoring
badge-v7-prem: label="On-Premise und Hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Gilt nur für Hybrid- und On-Premise-Bereitstellungen"
audience: production
content-type: reference
topic-tags: data-processing
exl-id: e5ef6aba-dc22-4c8d-9fbb-13d507181b65
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 6%

---

# Backup{#backup}

Eine Sicherung ist unerlässlich, um zu verhindern, dass Daten im Falle eines (physischen oder systembezogenen) Problems auf einem Computer verloren gehen.

Die Daten werden an zwei verschiedenen Speicherorten gespeichert:

* physische Dateien werden in den Adobe Campaign-Verzeichnissen gespeichert;
* andere Daten in der Datenbank gespeichert werden.

Die meisten Daten befinden sich in der Datenbank. Dies entspricht 99 % der zu sichernden Informationen.

## Physische Dateien {#physical-files}

Dateien sind in mehrere Kategorien unterteilt:

* Konfigurationsdateien, gespeichert in **nl6/conf** können Sie Adobe Campaign sehr schnell neu konfigurieren.

* Weiterleitungsdateien, gespeichert in  **nl6/var/`<instance-name>`/redir**, befinden sich auf den Tracking-Servern (häufig als &quot;frontal&quot;bezeichnet) und schließen alle vorherigen Kampagnen-Umleitungen ein. Sie werden weiterhin von früheren Kampagnen verwendet.

* Protokolldateien, gespeichert in **nl6/var/`<instance-name>`/log**, kann zur Verfolgung von Problemen verwendet werden.

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
