---
product: campaign
title: Erste Schritte mit dem SMS-Kanal
description: Erste Schritte mit dem SMS-Kanal
feature: SMS
role: User
exl-id: 6fc2ab09-8ea7-4865-88ad-bd45eee68958
TQID: https://experienceleague.adobe.com/bk-HUOGv3u60NzOnXD0huo74lBJJuiBOaOJeGmPa2E4
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: a075b2c1-7748-4328-b7f6-343aa314616a
  - id: b631758a-142d-425f-b9aa-f756d85cb979
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 484
ht-degree: 100%

---

# Erste Schritte mit dem SMS-Kanal{#sms-channel}

Verwenden Sie Adobe Campaign, um Textnachrichten an die Mobilgeräte Ihrer Kundinnen und Kunden zu senden. Im SMS-Editor können Sie Nachrichten im Textformat erstellen, personalisieren und in der Vorschau anzeigen.

SMS ist ein direkter und höchst effektiver Kanal, um Ihre Benutzenden überall zu erreichen. Mit hohen Öffnungsraten und einem nahezu sofortigen Versand ist SMS ideal für zeitkritische Warnhinweise, Transaktions-Updates und kurze Werbenachrichten. Verwenden Sie SMS, um Ihre kanalübergreifende Strategie zu ergänzen und eine wirkungsvolle Echtzeit-Kommunikation bereitzustellen. In der [Dokumentation zu Adobe Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/sms/sms.html?lang=de){target=_blank} erfahren Sie, wie Sie den SMS-Kanal effektiv konfigurieren und verwenden.

Im Zuge der Umstellung von Campaign v7 auf v8 wurde der Campaign Classic-Dokumentationssatz optimiert und neu organisiert. Allgemeine Funktionen sind jetzt nur noch in der Dokumentation zu Campaign v8 verfügbar.

>[!BEGINTABS]

>[!TAB Dokumentation zum SMS-Kanal]

Weitere Informationen zum SMS-Kanal finden Sie in der [Dokumentation zu Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/sms/sms.html?lang=de){target=_blank}.


[![Bild](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/sms/sms.html?lang=de){target=_blank}


>[!TAB Erstellung eines SMS-Versands]

Die wichtigsten Schritte zur Erstellung eines SMS-Versands finden Sie in der **Dokumentation zu Campaign v8**:

* [SMS-Kanal – Überblick](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/sms/sms.html?lang=de){target="_blank"}: Erfahren Sie, wie Sie Textnachrichten an die Mobilgeräte Ihrer Kundinnen und Kunden senden können.
* [Erstellen eines SMS-Versands](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/send/sms/create-sms/create-sms){target="_blank"}: Entdecken Sie die verschiedenen Schritte, die zum Erstellen eines neuen SMS-Versands erforderlich sind.
* [Definieren des Inhalts](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/send/sms/create-sms/sms-content){target="_blank"}: Erfahren Sie, wie Sie den Inhalt Ihrer SMS-Nachrichten personalisieren können.
* [Auswählen der Zielgruppe](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/send/sms/create-sms/sms-audience){target="_blank"}: Die Hauptzielgruppe wird aus der Adobe Campaign-Datenbank extrahiert. Sie kann auch in einer externen Datei gespeichert werden.
* [SMS-Testversand](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/send/sms/validate-sms/sms-proofs): Die Einrichtung eines Validierungszyklus für den Versand ist unerlässlich. Vergewissern Sie sich, dass Ihr Inhalt genehmigt wurde, bevor dieser an Ihre Zielgruppe gesendet wird.
* [Senden an die Zielgruppe](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/sms/validate-sms/sms-send.html?lang=de): Nach Validierung Ihrer SMS können Sie diese nun an die entsprechende Zielgruppe senden.
* [Überwachen und Nachverfolgen einer SMS](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/send/sms/sms-monitor): Es ist wichtig, den Versand Ihrer SMS zu überwachen, um die Effizienz Ihrer Marketing-Kampagnen sicherzustellen.


>[!TAB SMS-Konfiguration]

Auf folgenden Seiten erfahren Sie mehr über die SMS-Konfiguration. Diese Seiten sind spezifisch für Campaign v7.

* [Eigenständige Konfiguration](sms-set-up.md): Erfahren Sie, wie Sie den SMS-Kanal in einer eigenständigen Instanz konfigurieren.
* [Mid-Sourcing-Konfiguration](sms-set-up-mid.md): Erfahren Sie, wie Sie mit Mid-Servern an ein Mobiltelefon senden.
* [SMS-Connector](sms-protocol.md): Erfahren Sie mehr über das Protokoll und die Einstellungen des SMS-Connectors.
* [Zusätzliche Konfiguration](sms-send.md): Erfahren Sie mehr über die erweiterten Parameter und andere zusätzliche Konfigurationen.
* [Fehlerbehebung](troubleshooting-sms.md): Wir haben eine Reihe potenzieller Probleme und deren Lösungen aufgelistet.

>[!ENDTABS]



<!--
Use Adobe Campaign to send personalized SMS messages.

Before starting sending SMS:

* Make sure recipient profiles contain at least a mobile phone in their profile.
* Learn more about the Adobe Campaign [Delivery best practices](delivery-best-practices.md).

The key steps to send a SMS are as follows:

* [Configure the SMS channel](sms-set-up.md)
* [Create a SMS delivery](sms-create.md)
* [Define the audience](sms-create.md#selecting-the-target-population)
* [Define the SMS content](sms-create.md#defining-the-sms-content)
* [Send, monitor and track SMS](sms-send.md)
* [Troubleshoot](troubleshooting-sms.md)

In addition, you need to be familiar with SMS protocol and settings. Walk through the connection set up between Adobe Campaign and a SMPP provider in [this document](sms-protocol.md)

For global information on how to create a delivery, refer to [this section](steps-about-delivery-creation-steps.md).

>[!NOTE]
>
>Adobe Campaign also lets you submit notifications on mobile terminals, via its **Adobe Campaign Mobile App Channel (NMAC)** option. 
> 
>For more on this, refer to the [Get started with mobile app channel](about-mobile-app-channel.md) section.
-->