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
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 7%

---

# Backup{#backup}

Eine Sicherung ist unerlässlich, um Datenverluste im Falle eines Problems (physisch oder systembedingt) auf einem Computer zu vermeiden.

Die Daten werden an zwei separaten Speicherorten gespeichert:

* Physische Dateien werden in den Adobe Campaign-Verzeichnissen gespeichert.
* Andere Daten werden in der Datenbank gespeichert.

Die meisten Daten befinden sich in der Datenbank. Dies entspricht 99 % der zu sichernden Informationen.

## Physische Dateien {#physical-files}

Die Dateien sind in verschiedene Kategorien unterteilt:

* Konfigurationsdateien, gespeichert in **nl6/conf**, ermöglichen es Ihnen, Adobe Campaign sehr schnell neu zu konfigurieren.

* Weiterleitungsdateien, die in **nl6/var/`<instance-name>`/redir** gespeichert sind, befinden sich auf den Tracking-Servern (oft als „frontal“ bezeichnet) und enthalten alle vorherigen Kampagnenumleitungen. Sie werden weiterhin von vorherigen Kampagnen verwendet.

* Protokolldateien, die in **nl6/var/`<instance-name>`/log** gespeichert sind, können zur Verfolgung von Problemen verwendet werden.

Die zu sichernden Verzeichnisse sind daher:

* nl6/conf

* nl6/var/`<instance-name>`/redir (für jede Instanz)

* nl6/var/`<instance-name>`/log (optional)

* NL6/VAR/`<instance-name>`/Relais (optional)


## Datenbank {#database}

>[!IMPORTANT]
>
>Es ist zwingend erforderlich, die Datenbank zu sichern.


Die -Datenbank enthält alle in der Rich-Client-Konsole von Adobe Campaign angezeigten Informationen sowie alle Branchendaten.

Für diesen Vorgang ist Ihr Hosting-Unternehmen und insbesondere dessen Datenbankadministratoren verantwortlich.
