---
solution: Campaign Classic
product: campaign
title: Probleme mit der Bildanzeige
description: Probleme mit der Bildanzeige
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 50f95d7156e7104d90fa7a31eea30711b9c11bbf
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 6%

---


# Probleme mit der Bildanzeige{#image-display-issues}

Wenn Bildanzeigeprobleme in einer gesendeten Meldung auftreten, können Gründe mit einem schlechten Standort in Verbindung gebracht werden:

* Die Speicherorte stimmen ggf. nicht überein oder die Bilder wurden nicht korrekt an den Duplikat-Tracking-Server gesendet: Überprüfen Sie Ihre Konfiguration.
* Bilder befinden sich möglicherweise nicht im Ordner öffentliche Ressource auf der Marketing-Instanz: Laden Sie die Bilder in Ihren Ressourcenordner hoch, um das Problem zu lösen.
* Wenn Sie in einer Mid-Sourcing-Architektur arbeiten: Beim Senden von Testversänden werden die Bilder ohne Fehler hochgeladen (Informationen werden in den Analysen-Protokollen angezeigt).

Fehlerbehebung:

1. Senden Sie einen Testversand, der die Bilder anzeigt.
1. Überprüfen Sie, ob die Ressourcenkonfiguration in der Instanzeinrichtung korrekt ist.
1. Überprüfen Sie den Ordner &quot;öffentliche Ressourcen&quot;oder, falls nicht, den Ordner &quot;öffentliche Ressourcen&quot;, den im Versand referenzierten Ordner.
