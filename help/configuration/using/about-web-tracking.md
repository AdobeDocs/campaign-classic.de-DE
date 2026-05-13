---
product: campaign
title: Über Webtracking
feature: Configuration, Instance Settings
description: Über Webtracking
role: User, Developer
exl-id: 91c31703-75e6-47a4-a877-35682dd687a9
TQID: https://experienceleague.adobe.com/FfA6FEH5WP2JJGVR4BhpjO19Yj4mt8irvyJLwuzCThs
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 192
ht-degree: 4%

---

# Über Webtracking{#about-web-tracking}

Zusätzlich zum Standard-Tracking, das das Verhalten eines Internetbenutzers anzeigt, der auf einen Link in einer E-Mail-Nachricht klickt, können Sie mit der Adobe Campaign-Plattform Informationen darüber sammeln, wie Internetbenutzer Ihre Website durchsuchen. Diese Datenerfassung wird vom Webtrackingmodul durchgeführt.

Wenn ein Internetnutzer bei einem bestimmten Versand auf einen getrackten Link in einer E-Mail klickt, hinterlegt der kontaktierte Weiterleitungsserver ein Sitzungs-Cookie, das die Broadlog-Kennung (broadlogId) und die Versandkennung (deliveryId) enthält.

Der Webclient sendet dieses Cookie dann jedes Mal an den Server, wenn der Benutzer eine Seite mit einem Webtracking-Tag besucht. Dies erfolgt während der gesamten Sitzung, d. h. bis der Webclient geschlossen wird.

Der Weiterleitungs-Server erfasst auf diese Weise die folgenden Daten:

* URL der aufgerufenen Seite über eine als Parameter gesendete Kennung
* den Versand, von dem aus die Web-Seite über das Sitzungs-Cookie besucht wurde,
* Kennung des Internetnutzers, der über das Sitzungs-Cookie geklickt hat,
* Zusätzliche Informationen wie das generierte Geschäftsvolumen.

Das folgende Diagramm zeigt die Phasen des Dialogs zwischen dem Client und den verschiedenen Servern.

![](assets/d_ncs_integration_webtracking_structure1.png)
