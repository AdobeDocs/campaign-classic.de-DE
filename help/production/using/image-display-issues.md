---
product: campaign
title: Probleme mit der Bildanzeige
description: Probleme mit der Bildanzeige
feature: Monitoring
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 62fa491e-3e83-422b-bcde-2bae2c1b676e
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 6%

---

# Probleme mit der Bildanzeige{#image-display-issues}



Wenn bei einer gesendeten Nachricht Probleme mit der Bildanzeige auftreten, können die Gründe mit einer fehlerhaften Position in Zusammenhang stehen:

* Die Standorte stimmen möglicherweise nicht überein oder Bilder wurden möglicherweise nicht korrekt an den duplizierten Tracking-Server gesendet: Überprüfen Sie Ihre Konfiguration.
* Bilder befinden sich möglicherweise nicht im Ordner der öffentlichen Ressource auf der Marketing-Instanz: Laden Sie die Bilder in Ihren Ressourcenordner hoch, um das Problem zu beheben.
* Wenn Sie in einer Mid-Sourcing-Architektur arbeiten: Prüfen Sie, ob Bilder beim Versand von Testsendungen fehlerfrei hochgeladen werden (Informationen werden in den Analyseprotokollen angezeigt).

Fehlerbehebung:

1. Senden Sie einen Testversand, der die Bilder anzeigt.
1. Überprüfen Sie, ob die Ressourcenkonfiguration in der Instanzeinrichtung korrekt ist.
1. Überprüfen Sie den Ordner der öffentlichen Ressourcen oder, falls er sich nicht im Ordner der öffentlichen Ressourcen befindet, den im Versand referenzierten Ordner.
