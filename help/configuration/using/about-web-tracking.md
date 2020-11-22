---
solution: Campaign Classic
product: campaign
title: Über Webtracking
description: Über Webtracking
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 4%

---


# Über Webtracking{#about-web-tracking}

Neben der standardmäßigen Verfolgung, die das Verhalten eines Internetbenutzers zeigt, der auf einen Link in einer E-Mail klickt, können Sie über die Adobe Campaign-Plattform Informationen darüber sammeln, wie Internetbenutzer auf Ihrer Website surfen. Diese Datenerfassung wird vom Web-Verfolgungsmodul durchgeführt.

Wenn ein Internetbenutzer auf einen verfolgten Link in einer E-Mail von einem bestimmten Versand aus klickt, speichert der kontaktierte Weiterleitungsserver ein Sitzungs-Cookie mit der Broadlog-ID (breitlogId) und der Versand-ID (deliveryId).

Der Webclient sendet dieses Cookie dann jedes Mal an den Server, wenn der Benutzer eine Seite besucht, die einen Web-Trackingtag enthält. Dies wird während der gesamten Sitzung fortgesetzt, d. h. bis der Webclient geschlossen wird.

Der Weiterleitungsserver erfasst auf diese Weise die folgenden Daten:

* URL der angezeigten Seite mit einer als Parameter gesendeten Kennung,
* der Versand, von dem aus die Webseite über das Sitzungs-Cookie besucht wurde,
* Kennung des Internetnutzers, der über das Sitzungs-Cookie auf die Schaltfläche geklickt hat,
* zusätzliche Informationen, z. B. das generierte Geschäftsvolumen.

Das folgende Diagramm zeigt die Phasen des Dialogs zwischen dem Client und den verschiedenen Servern.

![](assets/d_ncs_integration_webtracking_structure1.png)

