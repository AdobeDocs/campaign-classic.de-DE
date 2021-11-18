---
product: campaign
title: Über Webtracking
description: Über Webtracking
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
exl-id: 91c31703-75e6-47a4-a877-35682dd687a9
source-git-commit: f000cb8bae164c22d1ede15db4e763cf50530674
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 4%

---

# Über Webtracking{#about-web-tracking}

![](../../assets/v7-only.svg)

Zusätzlich zur standardmäßigen Verfolgung, die das Verhalten eines Internetbenutzers anzeigt, der in einer E-Mail-Nachricht auf einen Link klickt, können Sie mit der Adobe Campaign-Plattform Informationen darüber sammeln, wie Internetbenutzer auf Ihrer Website surfen. Diese Datenerfassung wird vom Webtracking-Modul durchgeführt.

Wenn ein Internetbenutzer von einem bestimmten Versand aus auf einen verfolgten Link in einer E-Mail klickt, speichert der kontaktierte Weiterleitungsserver ein Sitzungs-Cookie mit der Broadlog-Kennung (broadlogId) und der Versandkennung (deliveryId).

Der Webclient sendet dieses Cookie dann jedes Mal an den Server, wenn der Benutzer eine Seite besucht, die ein Webtrackingtag enthält. Dies wird während der gesamten Sitzung fortgesetzt, d. h. bis der Web-Client geschlossen wird.

Der Weiterleitungsserver erfasst auf diese Weise die folgenden Daten:

* URL der angezeigten Seite über eine als Parameter gesendete Kennung,
* den Versand, von dem aus die Webseite über das Sitzungs-Cookie besucht wurde,
* Kennung des Internetbenutzers, der über das Sitzungs-Cookie geklickt hat,
* zusätzliche Informationen, z. B. das generierte Geschäftsvolumen.

Das folgende Diagramm zeigt die Phasen des Dialogfelds zwischen dem Client und den verschiedenen Servern.

![](assets/d_ncs_integration_webtracking_structure1.png)
