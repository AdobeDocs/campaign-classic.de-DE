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
source-git-commit: 4ac96bf0e54268832b84b17c3cc577af038cc712

---


# Über den Mobile-App-Kanal{#about-mobile-app-channel}

>[!CAUTION]
>
>In diesem Dokument wird der Vorgang zur Integration Ihrer mobilen Anwendung mit der Adobe Campaign-Plattform beschrieben. Es werden keine Informationen zum Erstellen der mobilen Anwendung oder zum Konfigurieren der Anwendung zum Verwalten von Benachrichtigungen bereitgestellt. If you would like further information on this, refer to the official Apple [documentation](https://developer.apple.com/) and Android [documentation](https://developer.android.com/index.html).

Die folgenden Abschnitte enthalten Informationen, die sich speziell auf den mobilen App-Kanal beziehen.

 Globale Informationen zum Erstellen einer Bereitstellung finden Sie in[diesem Abschnitt](../../delivery/using/steps-about-delivery-creation-steps.md).

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
>* Sie müssen sicherstellen, dass die an eine mobile Anwendung gesendeten Benachrichtigungen die von Apple (Apple Push Notification Service) und Google (Firebase Cloud Messaging) festgelegten Voraussetzungen und Bedingungen erfüllen.
>* In manchen Ländern ist es gesetzlich vorgeschrieben, die Benutzer Ihrer Mobile Apps über die Natur und den Zweck der erhobenen Daten zu unterrichten. Prüfen Sie die jeweiligen gesetzlichen Regelungen.


Der Arbeitsablauf **[!UICONTROL NMAC opt-out management]** (mobileAppOptOutMgt) aktualisiert Benachrichtigungen zu Abonnements auf Mobilgeräten. For more information on this workflow, refer to the [Workflows guide](../../workflow/using/mobile-app-channel.md).

Adobe Campaign ist mit binären und HTTP/2 APNS kompatibel. Weitere Informationen zu den Konfigurationsschritten finden Sie im Abschnitt [Konfigurieren einer mobilen Anwendung in Adobe Campaign](../../delivery/using/configuring-the-mobile-application.md) .

## Datenfluss {#data-path}

Die unten stehenden Schemata verdeutlichen den Austausch von Daten zwischen Mobile Apps und Adobe Campaign. Drei Akteure sind an diesem Prozess beteiligt:

* Mobile App
* Benachrichtigungsdienst - APNS (Apple Push Notification Service) bei iOS und FCM (Firebase Cloud Messaging) bei Android
* Adobe Campaign

Der Benachrichtigungsprozess besteht aus drei großen Schritten: Speicherung der App in Adobe Campaign (Abonnement-Erhebung), Versand und Tracking.

### 1. Schritt: Abonnement-Erhebung {#step-1--subscription-collection}

Die Mobile App wird vom Nutzer im App Store oder bei Google Play heruntergeladen. Die App enthält u. a. die Verbindungsparameter (Zertifikat bei iOS und Projektschlüssel bei Android) sowie den Integrationsschlüssel. Beim ersten Start der App werden je nach Konfiguration vom Benutzer gewisse Registrierungsdaten abgefragt (@userKey, beispielsweise eine E-Mail-Adresse oder eine Kundennummer). Gleichzeitig ruft die App beim Benachrichtigungsdienst eine Benachrichtigungskennung (Push-ID) ab. Alle diese Daten (Verbindungsparameter, Integrationsschlüssel, Benachrichtigungskennung, userKey) werden an Adobe Campaign übermittelt.

![](assets/nmac_register_view.png)

### 2. Schritt: Versand {#step-2--delivery}

Die Marketingabteilung erstellt einen Versand mit den jeweiligen App-Abonnenten als Zielgruppe. Der Versandprozess übermittelt dem Benachrichtigungsdienst die Verbindungsparameter (Zertifikat bei iOS und Projektschlüssel bei Android), die Benachrichtigungskennung (Push-ID) und den Inhalt der Benachrichtigung. Der Benachrichtigungsdienst sendet die Benachrichtigungen an die Mobilgeräte der Zielgruppenempfänger.

Folgende Informationen werden an Adobe Campaign gemeldet:

* Nur Android: Anzahl an Geräten, auf denen die Benachrichtigung angezeigt wurde (Impressions);
* Android und iOS: Anzahl an Klicks auf die Benachrichtigung.

![](assets/nmac_delivery_view.png)

Der Adobe-Campaign-Server muss den APNS auf folgenden Ports kontaktieren können:

* 2195 (Sendung) und 2186 (Feedback-Service) für den binären iOS-Connector
* 443 für den iOS-HTTP/2-Connector

Verwenden Sie folgende Befehle, um die korrekte Funktionsweise zu testen:

* Für Tests:

   ```
   telnet gateway.sandbox.push.apple.com
   ```

* In Produktion:

   ```
   telnet gateway.push.apple.com
   ```

Wenn ein binärer iOS-Connector verwendet wird, muss der APNS vom MTA und Webserver auf dem Port 2195 (Sendung) und vom Workflow-Server auf dem Port 2196 (Feedback-Service) kontaktiert werden können.

Wenn ein iOS-HTTP/2-Connector verwendet wird, muss der APNS vom MTA, Webserver und Workflow-Server auf dem Port 443 kontaktiert werden können.

