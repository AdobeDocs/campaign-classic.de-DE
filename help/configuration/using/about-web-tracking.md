---
product: campaign
title: Über Webtracking
feature: Configuration, Instance Settings
description: Über Webtracking
role: User, Data Engineer, Developer
badge-v7-only: label="v7" type="Informative" tooltip="Gilt nur für Campaign Classic v7"
exl-id: 91c31703-75e6-47a4-a877-35682dd687a9
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '199'
ht-degree: 8%

---

# Über Webtracking{#about-web-tracking}

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
