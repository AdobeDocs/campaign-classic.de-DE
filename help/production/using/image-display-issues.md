---
product: campaign
title: Probleme mit der Bildanzeige
description: Probleme mit der Bildanzeige
feature: Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="Gilt nur für Campaign Classic v7"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 62fa491e-3e83-422b-bcde-2bae2c1b676e
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '140'
ht-degree: 11%

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
