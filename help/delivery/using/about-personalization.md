---
product: campaign
title: Erste Schritte mit der Personalisierung
description: Erfahren Sie, wie Sie Nachrichten personalisieren und bedingten Inhalt in Campaign verwenden können.
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
feature: Personalization
role: User
exl-id: 555082a2-1b62-4aa4-b80c-77b1a1ef9491
source-git-commit: a1e9fec0e9c85bf25b79e24a7432dfb45bd1a0cb
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 81%

---

# Erste Schritte mit der Personalisierung{#about-personalization}

Die mit Adobe Campaign versendeten Nachrichten können in verschiedener Hinsicht personalisiert werden. Sowohl Inhalt als auch Rendering der Mitteilungen können dem Empfängerprofil entsprechend angepasst werden. Bei E-Mail-Sendungen haben Sie die Möglichkeit, Personalisierungselemente und -bedingungen direkt in JavaScript über den **[!UICONTROL Quelle]**-Tab der Nachricht zu definieren. Im Allgemeinen ermöglicht es Ihnen Adobe Campaign:

* Das Nachrichtenformat personalisieren. Siehe [Nachrichteninhalt](defining-the-email-content.md#message-content).
* Dynamische Personalisierungsfelder einfügen. Siehe [Personalisierungsfelder](personalization-fields.md).
* Vordefinierte Personalisierungsbausteine einfügen. Siehe [Gestaltungsbausteine](personalization-blocks.md).
* Bedingte Inhalte erstellen. Siehe Abschnitt [Bedingter Inhalt](conditional-content.md).

>[!CAUTION]
>
>Bei den folgenden Variablen handelt es sich um interne Variablen, die im Rahmen der Personalisierung verwendet werden können, aber nicht abgeändert werden dürfen: **delivery**, **message**, **dataSource**, **targetData**, **provider**, **coupon**, **couponValue**, **proposition**.


Mit Adobe Campaign können Sie Ihre Sendungen personalisieren, um Nachrichten zu senden, die dem Profil und den Interessen jedes Empfängers entsprechen.

Mit Personalization können Sie Ihre Nachrichten relevanter und ansprechender gestalten. Sie können Empfängerdaten verwenden, um Inhalte anzupassen, dynamische Felder hinzuzufügen oder unterschiedliche Informationen auf Grundlage von Bedingungen anzuzeigen. In der [Dokumentation zu Adobe Campaign v8 erfahren Sie, wie Sie Personalisierungsfunktionen in Ihren Sendungen einrichten und &#x200B;](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/personalize/personalize.html?lang=de){target=_blank}.

Im Rahmen der Promotion-Initiative für Campaign v8 wurde die Dokumentation zu Campaign Classic neu strukturiert. Allgemeine Funktionen sind jetzt nur noch in der Dokumentation zu Campaign v8 verfügbar.

>[!BEGINTABS]

>[!TAB Dokumentation zur Inhaltspersonalisierung]

Weitere Informationen zur Personalisierung von Inhalten finden Sie in der [&#x200B; zu Campaign v8 &#x200B;](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/personalize/personalize.html?lang=de){target=_blank}.


[![Bild](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/personalize/personalize.html?lang=de){target=_blank}


>[!TAB Erstellung eines E-Mail-Versands]

Die wichtigsten Schritte zur Erstellung eines E-Mail-Versands finden Sie in der Dokumentation zu Campaign v8:

* [Erstellen eines E-Mail-Versands](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/send/emails/email){target="_blank"}: Erfahren Sie mehr über die verschiedenen Schritte, die zum Erstellen eines E-Mail-Versands erforderlich sind.
* [Definieren des E-Mail-Inhalts](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/send/emails/defining-the-email-content){target="_blank"}: Definieren Sie, was Ihre E-Mail enthalten soll: Absenderin bzw. Absender, Betreff, Inhalt, Bilder.
* [Definieren interaktiver Inhalte](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/send/emails/defining-interactive-content){target="_blank"}: Verwenden Sie das interaktive Format AMP für E-Mail, um dynamische E-Mails zu senden.
* [Senden von E-Mails auf japanischen Mobiltelefonen](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/send/emails/sending-emails-on-japanese-mobiles){target="_blank"}: Verwenden Sie eines der drei spezifischen japanischen Formate für E-Mails auf Mobiltelefonen.
* [Anhängen von Dateien an eine E-Mail](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/send/emails/attaching-files){target="_blank"}: Erfahren Sie mehr über die verschiedenen Methoden zum Anhängen von einer oder mehrerer Dateien an eine E-Mail.


>[!TAB E-Mail-Parameter]

Auf diesen Seiten erfahren Sie mehr über E-Mail-Parameter in der Dokumentation zu Campaign v8:

* [Link zur Mirrorseite](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/send/emails/mirror-page){target="_blank"}: Konfigurieren Sie die Mirrorseite, um sicherzustellen, dass Ihre Clients immer das beste Rendering-Erlebnis erhalten.
* [Hinzufügen einer BCC-Adresse](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/email-bcc.html?lang=de){target="_blank"}: Konfigurieren Sie Adobe Campaign so, dass eine Kopie der von der Plattform gesendeten E-Mails beibehalten wird.
* [Definieren zusätzlicher E-Mail-Parameter](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/send/emails/email-parameters){target="_blank"}: Erfahren Sie mehr über die in den Versandeigenschaften verfügbaren Optionen und Parameter.

Weitere Informationen zum Enhanced MTA finden Sie auch auf dieser [Seite](sending-with-enhanced-mta.md).

>[!ENDTABS]





<!--
Adobe Campaign lets you mass deliver personalized electronic messages to a target population.

Before starting sending emails:

* Make sure recipient profiles contain at least an email address.
* Learn more about the Adobe Campaign [Delivery best practices](delivery-best-practices.md).
* Read out these sections to learn more about Deliverability: [Deliverability management in Campaign](about-deliverability.md) and [Deliverability best practices guide](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=de).

The key steps to send an email are as follows:

* [Create an email delivery](creating-an-email-delivery.md)
* [Define the target population](steps-defining-the-target-population.md)
* [Define the email content](defining-the-email-content.md)
* [Send the email](sending-messages.md)
* [Monitor the delivery](about-delivery-monitoring.md)

The sections below provide information that is specific to the email channel. For global information on how to create a delivery, refer to [this section](steps-about-delivery-creation-steps.md).
-->