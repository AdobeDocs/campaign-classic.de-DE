---
product: campaign
title: Erste Schritte mit dem SMS-Kanal
description: Erste Schritte mit dem SMS-Kanal
feature: SMS
role: User
exl-id: 6fc2ab09-8ea7-4865-88ad-bd45eee68958
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: ht
source-wordcount: '382'
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
* [SMS-Testversand](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/send/sms/validate-sms/sms-proofs): Die Einrichtung eines Validierungszyklus für den Versand ist unerlässlich.
Vergewissern Sie sich, dass Ihr Inhalt genehmigt wurde, bevor dieser an Ihre Zielgruppe gesendet wird.
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