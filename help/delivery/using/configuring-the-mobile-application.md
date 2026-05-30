---
product: campaign
title: Konfigurieren der Mobile App für iOS in Adobe Campaign
description: Erfahren Sie, wie Sie Ihre Mobile App für iOS einrichten
feature: Push
role: User, Developer
level: Intermediate, Experienced
hide: true
exl-id: 67eee1c5-a918-46b9-875d-7c3c71c00635
TQID: https://experienceleague.adobe.com/GupiG2H4tr3aUKc265ABDhVXpiZBFr9IzG-0s4pxwmU
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: c5474392-5419-4296-9e41-f6f4ce4f6e9bid: b631758a-142d-425f-b9aa-f756d85cb979id: c858a28b-ea19-49b0-8d48-828717fad89c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2: id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
subfeature_v2: id: e95a583b-fcfa-4524-8666-46a29c828119id: c8da4fdd-eb94-4751-a43c-f82733fb2d6eid: d5bbe3da-ba85-4242-817e-54f7c4b943e0id: f4da0e76-df77-451e-ad61-21afb7bd8810
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 645
ht-degree: 88%

---

# Konfigurationsschritte für iOS {#configuring-the-mobile-application-in-adobe-campaign-ios}

Nachdem das Paket installiert ist, können Sie in Adobe Campaign Classic die Einstellungen für Ihre iOS-Mobile-App festlegen.

Die wichtigsten Schritte sind:

1. [Konfigurieren des externen iOS-Kontos](#configuring-external-account-ios)
1. [Konfigurieren des iOS-Service](#configuring-ios-service)
1. [Integrieren der iOS-Mobile-App in Campaign](#creating-ios-app)

Anschließend können Sie [eine Push-Benachrichtigung für iOS-Geräte erstellen](create-notifications-ios.md).

## Konfigurieren des externen iOS-Kontos {#configuring-external-account-ios}

Bei iOS sendet der iOS-HTTP/2-Connector Benachrichtigungen an HTTP/2-APNS.

Gehen Sie wie folgt vor, um diesen Connector zu konfigurieren:

1. Gehen Sie zu **[!UICONTROL Administration > Plattform > Externe Konten]**.
1. Wählen Sie das externe Konto **[!UICONTROL iOS-Routing]** aus.
1. Füllen Sie im Tab **[!UICONTROL Connector]** das Feld **[!UICONTROL Zugriffs-URL auf den Connector]** mit der folgenden URL aus: `http://localhost:8080/nms/jsp/iosHTTP2.jsp`

   ![](assets/nmac_connectors.png)

1. Wählen Sie **[!UICONTROL Speichern]** aus.

Ihr iOS-Connector ist jetzt konfiguriert. Sie können mit dem Einrichten Ihres Dienstes beginnen.

## Konfigurieren des iOS-Service {#configuring-ios-service}

>[!CAUTION]
>
>Die Anwendung muss für Push-Aktionen konfiguriert worden sein, BEVOR eine Integration in das Adobe SDK erfolgt.
>
>Sollte dies nicht der Fall sein, besuchen Sie bitte [diese Seite](https://developer.apple.com/documentation/usernotifications).

1. Klicken Sie im Knoten **[!UICONTROL Profile und Zielgruppen > Dienste und Abonnements]** auf die Schaltfläche **[!UICONTROL Neu]**.

   ![](assets/nmac_service_1.png)

1. Bestimmen Sie einen **[!UICONTROL Titel]** und einen **[!UICONTROL internen Namen]**.
1. Wählen Sie im Feld **[!UICONTROL Typ]** die Option **[!UICONTROL Mobile App]**.

   >[!NOTE]
   >
   >Das standardmäßige Zielgruppen-Mapping für **[!UICONTROL abonnierte Anwendungen (nms:appSubscriptionRcp)]** ist mit der Empfängertabelle verknüpft. Wenn Sie ein anderes Zielgruppen-Mapping verwenden möchten, müssen Sie ein neues Zielgruppen-Mapping erstellen und es im Feld **[!UICONTROL Zielgruppen-Mapping]** des Dienstes eingeben. Weiterführende Informationen zur Erstellung des Zielgruppen-Mappings finden Sie im [Konfigurationshandbuch](../../configuration/using/about-custom-recipient-table.md).

   ![](assets/nmac_ios.png)

1. Klicken Sie dann auf die Schaltfläche **[!UICONTROL Hinzufügen]**, um den Anwendungstyp auszuwählen.

   ![](assets/nmac_service_2.png)

1. Erstellen Sie Ihre iOS-Mobile-Apps für Entwicklung und Produktion. Weitere Informationen hierzu finden Sie in [diesem Abschnitt](configuring-the-mobile-application.md#creating-ios-app).

## Erstellen einer iOS-Mobile-App {#creating-ios-app}

Erstellen Sie nach der Erstellung Ihres Services Ihre iOS-Mobile-App in Campaign. Gehen Sie wie folgt vor:

1. Klicken Sie in Ihrem neu erstellten Dienst auf die Schaltfläche **[!UICONTROL Hinzufügen]**, um den Anwendungstyp auszuwählen.

   ![](assets/nmac_service_2.png)

1. Das folgende Fenster wird angezeigt. Wählen Sie **[!UICONTROL iOS-Anwendung erstellen]** und beginnen Sie, indem Sie den **[!UICONTROL Titel]** eingeben.

   ![](assets/nmac_ios_2.png)

1. Als Option können Sie bei Bedarf den Inhalt einer Push-Nachricht mit einigen **[!UICONTROL Anwendungsvariablen]** anreichern. Diese sind vollständig anpassbar und Teil der Nachrichten-Payload, die an das Mobilgerät gesendet wird.
Im folgenden Beispiel fügen wir &quot;**mediaURl** und **mediaExt** hinzu, um eine Rich-Push-Benachrichtigung zu erstellen, und stellen dann der Anwendung das Bild bereit, das in der Benachrichtigung angezeigt werden soll.

   ![](assets/nmac_ios_3.png)

1. Auf der Registerkarte **[!UICONTROL Abonnementparameter]** können Sie das Mapping mit einer Erweiterung des Schemas **[!UICONTROL Abonnierte Anwendungen (nms:appsubscriptionRcp)]** definieren.

   >[!NOTE]
   >
   >Vergewissern Sie sich, dass Sie nicht dasselbe Zertifikat sowohl für die Entwicklungsversion (Sandbox) als auch für die Produktionsversion der Anwendung verwenden.

1. Auf dem Tab **[!UICONTROL Töne]** können Sie einen abzuspielenden Ton festlegen. Klicken Sie auf **[!UICONTROL Hinzufügen]** und füllen Sie das Feld **[!UICONTROL Interner Name]** aus, das den Namen der in die Anwendung eingebetteten Datei oder den Namen des Systemtons enthalten muss.

1. Klicken Sie auf **[!UICONTROL Weiter]**, um mit dem Konfigurieren der Entwicklungsanwendung zu beginnen.

1. Stellen Sie sicher, dass in Adobe Campaign und im Anwendungs-Code derselbe **[!UICONTROL Integrationsschlüssel]** definiert ist (über das SDK). <!--For more on this, refer to [this page](integrating-campaign-sdk-into-the-mobile-application.md).--> Mit diesem programmspezifischen Integrationsschlüssel können Sie die Mobile App mit der Adobe Campaign-Plattform verknüpfen.

   >[!NOTE]
   >
   > Der **[!UICONTROL Integrationsschlüssel]** kann mit einem Zeichenfolgenwert vollständig angepasst werden, muss jedoch mit dem im SDK angegebenen Schlüssel identisch sein.

1. Wählen Sie im Feld **[!UICONTROL Anwendungssymbol]** ein vordefiniertes Symbol aus, um die Mobile App in Ihrem Dienst zu personalisieren.

1. Wählen Sie den **[!UICONTROL Authentifizierungsmodus]** aus.

   ![](assets/nmac_ios_5.png)

   Zwei Modi sind verfügbar:

   * (Empfohlen) **[!UICONTROL Token-basierte Authentifizierung]**: Füllen Sie die APNs-Verbindungseinstellungen **[!UICONTROL Schlüssel-ID]**, **[!UICONTROL Team-ID]** und **[!UICONTROL Paket-ID]** aus und wählen Sie dann Ihr p8-Zertifikat, indem Sie auf **[!UICONTROL Privaten Schlüssel eingeben…]** klicken. Weitere Informationen zur **[!UICONTROL Token-basierten Authentifizierung]** finden Sie in der [Dokumentation zu Apple](https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_token-based_connection_to_apns){target="_blank"}.

   * **[!UICONTROL Zertifikatbasierte Authentifizierung]**: Klicken Sie auf **[!UICONTROL Zertifikat eingeben…]**. Wählen Sie dann Ihren p12-Schlüssel und geben Sie das Passwort ein, das der Entwickler bzw. die Entwicklerin der Mobile App bereitgestellt hat.

   >[!NOTE]
   >
   > Adobe empfiehlt die Verwendung der **[!UICONTROL Token-basierten Authentifizierung]** für Ihre iOS-Konfiguration, da die P8-Authentifizierungsschlüssel neuer und sicherer sind.

1. Klicken Sie auf die Schaltfläche **[!UICONTROL Verbindung testen]**, um Ihre Konfiguration zu validieren.

1. Nun können Sie die Produktionsanwendung konfigurieren, indem Sie auf **[!UICONTROL Weiter]** klicken und nach dem gleichen Verfahren wie oben beschrieben vorgehen.


1. Klicken Sie auf **[!UICONTROL Beenden]**.

Ihre iOS-Mobile-App kann jetzt in Campaign Classic verwendet werden.
