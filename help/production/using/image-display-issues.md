---
title: Bildanzeigeprobleme
seo-title: Bildanzeigeprobleme
description: Bildanzeigeprobleme
seo-description: null
page-status-flag: never-activated
uuid: 8fc51459-ee46-4c05-8011-f0651e6b451b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: dfccfe8c-b826-4648-9a0b-23d7e6a4808a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Bildanzeigeprobleme{#image-display-issues}

Wenn Bildanzeigeprobleme in einer gesendeten Meldung auftreten, können Gründe mit einem schlechten Standort in Verbindung gebracht werden:

* die Speicherorte stimmen möglicherweise nicht überein oder Bilder wurden möglicherweise nicht korrekt auf den Tracking-Server übertragen: Überprüfen Sie Ihre Konfiguration.
* Bilder befinden sich möglicherweise nicht im Ordner für öffentliche Ressourcen auf der Marketing-Instanz: Laden Sie die Bilder in Ihren Ressourcenordner hoch, um das Problem zu lösen.
* wenn Sie in einer Midsourcing-Architektur arbeiten: Beim Senden von Nachweisen werden Bilder ohne Fehler hochgeladen (Informationen werden in den Analyseprotokollen angezeigt).

Fehlerbehebung:

1. Senden Sie einen Beweis, der die Bilder anzeigt.
1. Überprüfen Sie, ob die Ressourcenkonfiguration im Instanzsetup korrekt ist.
1. Überprüfen Sie den Ordner für öffentliche Ressourcen oder - wenn er sich nicht im Ordner für öffentliche Ressourcen befindet - den Ordner, auf den bei der Bereitstellung verwiesen wird.

