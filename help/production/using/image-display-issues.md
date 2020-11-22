---
solution: Campaign Classic
product: campaign
title: Probleme mit der Bildanzeige
description: Probleme mit der Bildanzeige
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 6%

---


# Probleme mit der Bildanzeige{#image-display-issues}

Wenn Bildanzeigeprobleme in einer gesendeten Meldung auftreten, können Gründe mit einem schlechten Standort in Verbindung gebracht werden:

* die Speicherorte stimmen möglicherweise nicht überein oder die Bilder wurden möglicherweise nicht korrekt an den Duplikat-Tracking-Server gesendet: Überprüfen Sie Ihre Konfiguration.
* Bilder befinden sich möglicherweise nicht im Ordner &quot;öffentliche Ressource&quot;auf der Marketing-Instanz: Laden Sie die Bilder in Ihren Ressourcenordner hoch, um das Problem zu lösen.
* wenn Sie in einer Mid-Sourcing-Architektur arbeiten: Beim Senden von Testversänden werden die Bilder ohne Fehler hochgeladen (Informationen werden in den Analysen-Protokollen angezeigt).

Fehlerbehebung:

1. Senden Sie einen Testversand, der die Bilder anzeigt.
1. Überprüfen Sie, ob die Ressourcenkonfiguration in der Instanzeinrichtung korrekt ist.
1. Überprüfen Sie den Ordner &quot;öffentliche Ressourcen&quot;oder - falls er sich nicht im Ordner &quot;öffentliche Ressourcen&quot;befindet - den Ordner, auf den im Versand verwiesen wird.

