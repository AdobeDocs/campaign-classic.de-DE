---
title: Informationen zum mobilen App-Kanal in Adobe Campaign Classic
description: Dieser Abschnitt enthält allgemeine Informationen zum mobilen App-Kanal in Adobe Campaign Classic.
page-status-flag: never-activated
uuid: e8d26b33-dc7c-4abd-956a-92f419a117e1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
discoiquuid: 6b3fe8b9-dae6-4f8e-83e1-3376c0fe72a5
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c581f22261af7e083f6bd47e603d17d2d71e7ce6

---


# Über den Mobile-App-Kanal{#about-mobile-app-channel}

>[!CAUTION]
>
>Diese Dokumentation beschreibt den Prozess der Integration Ihrer Mobile App mit der Adobe-Campaign-Plattform. Sie enthält keine Informationen zur Erstellung der App und zur Benachrichtigungskonfiguration. Entsprechende Informationen finden Sie in den offiziellen Dokumentationen von Apple ([https://developer.apple.com/](https://developer.apple.com/)) und Android ([https://developer.android.com/index.html](https://developer.android.com/index.html)).

Die folgenden Abschnitte enthalten Informationen, die sich speziell auf den mobilen App-Kanal beziehen. Globale Informationen zum Erstellen einer Bereitstellung finden Sie in[diesem Abschnitt](../../delivery/using/steps-about-delivery-creation-steps.md).

Der Mobile-Kanal (**Mobile App Channel**) bietet die Möglichkeit, mithilfe von Apps aus Adobe Campaign personalisierte Benachrichtigungen auf iOS- und Android-Geräte zu senden. Zwei Kanäle stehen zur Auswahl:

* iOS-Kanal zum Versand von Mitteilungen an Mobilgeräte mit Apple--Betriebssystem.

   ![](assets/nmac_intro_2.png)

* Android-Kanal zum Versand von Nachrichten an Mobilgeräte mit Android-Betriebssystem.

   ![](assets/nmac_intro_1.png)

Diesen Kanälen entsprechen zwei Versandaktivitäten in den Kampagnen-Workflows:

![](assets/nmac_intro_3.png)

>[!NOTE]
>
>Zwei Transaktionsnachrichten-Vorlagen stehen auch für den Transaktionsnachrichtenversand zur Verfügung.

Sie können das Verhalten der Anwendung dahingehend konfigurieren, dass dem Empfänger beim Antippen der Benachrichtigung der zum jeweiligen Anwendungskontext passende Bildschirm angezeigt wird. Zum Beispiel:

* Im Falle einer Lieferbenachrichtigung wird bei Klick auf die Mitteilung eine Seite mit Informationen zur Sendungsverfolgung angezeigt.
* Im Falle eines Warenkorbs, für den der Kunde schließlich keine Bestellung aufgegeben hat, kann eine Mitteilung versendet werden, die den Empfänger durch Antippen direkt auf das entsprechende Produkt weiterleitet.

>[!CAUTION]
>
>* Stellen Sie sicher, dass die an Mobile Apps gesendeten Benachrichtigungen den von Apple (Apple Push Notification Service) bzw. Google (Google Cloud Messaging) gestellten Anforderungen entsprechen.
>* In manchen Ländern ist es gesetzlich vorgeschrieben, die Benutzer Ihrer Mobile Apps über die Natur und den Zweck der erhobenen Daten zu unterrichten. Prüfen Sie die jeweiligen gesetzlichen Regelungen.


Der Arbeitsablauf **[!UICONTROL NMAC opt-out management]** (mobileAppOptOutMgt) aktualisiert Benachrichtigungen zu Abonnements auf Mobilgeräten. For more information on this workflow, refer to the [Workflows guide](../../workflow/using/mobile-app-channel.md).

Adobe Campaign ist mit binären und HTTP/2 APNS kompatibel. Weitere Informationen zu den Konfigurationsschritten finden Sie im Abschnitt [Connectors](../../delivery/using/setting-up-mobile-app-channel.md#connectors) .
