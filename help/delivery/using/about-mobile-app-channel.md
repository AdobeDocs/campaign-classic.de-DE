---
product: campaign
title: Über den Mobile-App-Kanal in Adobe Campaign Classic
description: Dieser Abschnitt enthält allgemeine Informationen zum Mobile-App-Kanal in Adobe Campaign Classic.
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
exl-id: c3b0406f-f652-42f4-ad0d-23fb719cd1b6
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '676'
ht-degree: 94%

---

# Erste Schritte mit dem Mobile-App-Kanal{#about-mobile-app-channel}

![](../../assets/common.svg)

Der **Mobile-App-Kanal** bietet die Möglichkeit, mithilfe von Apps über Adobe Campaign personalisierte Push-Benachrichtigungen auf iOS- und Android-Geräte zu senden.

>[!CAUTION]
>
>In diesem Dokument wird beschrieben, wie Sie Ihre Mobile App mit der Adobe Campaign-Plattform integrieren können. Es enthält weder Informationen zum Erstellen der Mobile App noch zum Konfigurieren der Anwendung für die Verwaltung von Benachrichtigungen. Weitere Informationen finden Sie in der offiziellen Apple-[Dokumentation](https://developer.apple.com/) sowie der offiziellen Android-[Dokumentation](https://developer.android.com/index.html).

Zwei Versandkanäle stehen zur Verfügung:

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

Adobe Campaign ist mit HTTP/2-APNs kompatibel. Weitere Informationen zu den Konfigurationsschritten finden Sie in [diesem Abschnitt](configuring-the-mobile-application.md).

Allgemeine Informationen zum Erstellen eines Versands finden Sie in [diesem Abschnitt](steps-about-delivery-creation-steps.md).

## Datenpfad {#data-path}

Die unten stehenden Schemata verdeutlichen den Austausch von Daten zwischen Mobile Apps und Adobe Campaign. Drei Akteure sind an diesem Prozess beteiligt:

* Mobile App
* Benachrichtigungsdienst - APNS (Apple Push Notification Service) bei iOS und FCM (Firebase Cloud Messaging) bei Android
* Adobe Campaign

Der Benachrichtigungsprozess besteht aus drei großen Schritten: Speicherung der App in Adobe Campaign (Abonnement-Erhebung), Versand und Tracking.

### Schritt 1: Abonnement-Erhebung {#step-1--subscription-collection}

Die Mobile App wird vom Nutzer im App Store oder bei Google Play heruntergeladen. Die Mobile App enthält u. a. die Verbindungsparameter (Zertifikat bei iOS und Projektschlüssel bei Android) sowie den Integrationsschlüssel. Beim ersten Start der Mobile App werden je nach Konfiguration vom Benutzer gewisse Registrierungsdaten abgefragt (@userKey, beispielsweise eine E-Mail-Adresse oder eine Kundennummer). Gleichzeitig ruft die Mobile App beim Benachrichtigungs-Service eine Benachrichtigungskennung (Push-ID) ab. Alle diese Daten (Verbindungsparameter, Integrationsschlüssel, Benachrichtigungskennung, userKey) werden an Adobe Campaign übermittelt.

![](assets/nmac_register_view.png)

### Schritt 2: Versand {#step-2--delivery}

Die Marketingabteilung erstellt einen Versand mit den jeweiligen App-Abonnenten als Zielgruppe. Der Versandprozess übermittelt dem Benachrichtigungsdienst die Verbindungsparameter (Zertifikat bei iOS und Projektschlüssel bei Android), die Benachrichtigungskennung (Push-ID) und den Inhalt der Benachrichtigung. Der Benachrichtigungsdienst sendet die Benachrichtigungen an die Mobilgeräte der Zielgruppenempfänger.

Folgende Informationen werden an Adobe Campaign gemeldet:

* Nur Android: Anzahl an Geräten, auf denen die Benachrichtigung angezeigt wurde (Impressions);
* Android und iOS: Anzahl an Klicks auf die Benachrichtigung.

![](assets/nmac_delivery_view.png)

Der Adobe Campaign-Server muss in der Lage sein, den APN-Server über Port 443 für den iOS HTTP/2-Connector zu kontaktieren. 

Verwenden Sie folgende Befehle, um die korrekte Funktionsweise zu testen:

* Für Tests:

   ```
   api.development.push.apple.com:443
   ```

* In Produktion:

   ```
   api.push.apple.com:443
   ```

Mit dem iOS-HTTP/2-Connector müssen der MTA und der Webserver in der Lage sein, die APNS an Port 443 zu kontaktieren.

Wenn Sie den iOS HTTP/2-Connector über einen Proxy verwenden müssen, lesen Sie diese [Seite](../../installation/using/file-res-management.md#proxy-connection-configuration).
