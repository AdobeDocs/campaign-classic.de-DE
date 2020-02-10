---
title: Informationen zur Webverfolgung
seo-title: Informationen zur Webverfolgung
description: Informationen zur Webverfolgung
seo-description: null
page-status-flag: never-activated
uuid: 59d18ffb-c26e-4571-8364-5e85ec587349
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
discoiquuid: 38ba9be9-dabc-41d4-878c-d772955301fe
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Informationen zur Webverfolgung{#about-web-tracking}

Neben der standardmäßigen Verfolgung, die das Verhalten eines Internetbenutzers anzeigt, der auf einen Link in einer E-Mail klickt, können Sie mit der Adobe Campaign-Plattform Informationen darüber sammeln, wie Internetbenutzer auf Ihrer Website surfen. Diese Datenerfassung wird vom Webverfolgungsmodul durchgeführt.

Wenn ein Internetbenutzer von einer bestimmten Zustellung aus auf einen verfolgten Link in einer E-Mail klickt, speichert der kontaktierte Weiterleitungsserver ein Sitzungs-Cookie mit der Broadlog-ID (breitlogId) und der Zustellkennung (deliveryId).

Der Webclient sendet dieses Cookie dann jedes Mal an den Server, wenn der Benutzer eine Seite besucht, die ein Web-Tracking-Tag enthält. Dies wird während der gesamten Sitzung fortgesetzt, d. h. bis der Webclient geschlossen wird.

Der Weiterleitungsserver erfasst auf diese Weise die folgenden Daten:

* URL der angezeigten Seite mit einer als Parameter gesendeten Kennung,
* die Bereitstellung, von der aus die Webseite über das Sitzungs-Cookie besucht wurde,
* Kennung des Internetnutzers, der über das Sitzungs-Cookie auf die Schaltfläche geklickt hat,
* zusätzliche Informationen, z. B. das generierte Geschäftsvolumen.

Das folgende Diagramm zeigt die Phasen des Dialogs zwischen dem Client und den verschiedenen Servern.

![](assets/d_ncs_integration_webtracking_structure1.png)

