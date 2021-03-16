---
solution: Campaign Classic
product: campaign
title: Über den Mobile-App-Kanal in Adobe Campaign Classic
description: Dieser Abschnitt enthält allgemeine Informationen zum Mobile-App-Kanal in Adobe Campaign Classic.
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
translation-type: ht
source-git-commit: 22f44f5723ab35e95caa438583fe06314c763ba1
workflow-type: ht
source-wordcount: '677'
ht-degree: 100%

---


# Über den Mobile-App-Kanal{#about-mobile-app-channel}

>[!CAUTION]
>
>In diesem Dokument wird beschrieben, wie Sie Ihre Mobile App mit der Adobe Campaign-Plattform integrieren können. Es enthält weder Informationen zum Erstellen der Mobile App noch zum Konfigurieren der Anwendung für die Verwaltung von Benachrichtigungen. Weitere Informationen finden Sie in der offiziellen Apple-[Dokumentation](https://developer.apple.com/) sowie der offiziellen Android-[Dokumentation](https://developer.android.com/index.html).

Die folgenden Abschnitte enthalten Informationen, die sich speziell auf den Mobile-App-Kanal beziehen.

Allgemeine Informationen zum Erstellen eines Versands finden Sie in [diesem Abschnitt](../../delivery/using/steps-about-delivery-creation-steps.md).

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
>* Stellen Sie sicher, dass die an Mobile Apps gesendeten Benachrichtigungen den von Apple (Apple Push Notification Service) bzw. Google (Firebase Cloud Messaging) gestellten Anforderungen entsprechen.
>* Warnung: In manchen Ländern ist es gesetzlich vorgeschrieben, die Benutzer Ihrer Mobile Apps über die Art der erhobenen Daten und den Zweck der Erhebung zu informieren. Prüfen Sie die jeweiligen gesetzlichen Regelungen.


Der Workflow **[!UICONTROL NMAC Opt-out Management]** (mobileAppOptOutMgt) aktualisiert das Abmelden von Benachrichtigungen auf Smartphones und Tablets. Weitere Informationen zu diesem Workflow finden Sie in der [Liste der technischen Workflows](../../workflow/using/about-technical-workflows.md).

Adobe Campaign ist mit HTTP/2-APNs kompatibel. Weitere Informationen zu den Konfigurationsschritten finden Sie im Abschnitt [Konfiguration einer Mobile App in Adobe Campaign](../../delivery/using/configuring-the-mobile-application.md).

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

Der Adobe Campaign-Server muss in der Lage sein, den APN-Server über Port 443 für den iOS HTTP/2-Connector zu kontaktieren. 

Verwenden Sie folgende Befehle, um die korrekte Funktionsweise zu testen:

* Für Tests:

   ```
   telnet gateway.sandbox.push.apple.com
   ```

* In Produktion:

   ```
   telnet gateway.push.apple.com
   ```

Mit dem iOS HTTP/2-Connector müssen der MTA, der Webserver und der Workflow-Server in der Lage sein, die APNs über Port 443 zu kontaktieren.

