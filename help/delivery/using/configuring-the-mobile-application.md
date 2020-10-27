---
title: iOS-Mobilanwendung in Adobe Campaign konfigurieren
description: Erfahren Sie, wie Sie Ihre Mobilanwendung für iOS einrichten
page-status-flag: never-activated
uuid: aff1a4a0-34e7-4ce0-9eb3-30a8de1380f2
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
discoiquuid: 7b5a1ad6-da5a-4cbd-be51-984c07c8d0b3
translation-type: tm+mt
source-git-commit: 16985c1ddcd380cfc1ca4960b35bb5e78628f464
workflow-type: tm+mt
source-wordcount: '944'
ht-degree: 67%

---


# Konfigurationsschritte für iOS {#configuring-the-mobile-application-in-adobe-campaign-ios}

Nachdem das Paket installiert wurde, können Sie Ihre iOS-App-Einstellungen in Adobe Campaign Classic definieren.

>[!NOTE]
>
>Informationen zum Konfigurieren der App für Android und zum Erstellen eines Versands für Android finden Sie in diesem [Abschnitt](../../delivery/using/configuring-the-mobile-application-android.md).

## Configuring iOS external account {#configuring-external-account-ios}

Bei iOS sendet der iOS-HTTP/2-Connector Benachrichtigungen an die HTTP/2-APNs.

Gehen Sie wie folgt vor, um diesen Connector zu konfigurieren:

1. Gehen Sie zu **[!UICONTROL Administration > Plattform > Externe Konten]**.
1. Wählen Sie das externe Konto **[!UICONTROL iOS-Routing]** aus.
1. In the **[!UICONTROL Connector]** tab, fill in the **[!UICONTROL Access URL of the connector]** field with the following URL: ```http://localhost:8080/nms/jsp/iosHTTP2.jsp```

   >[!NOTE]
   >
   > Ab Kampagne 20.3 wird der ältere iOS-Binäranschluss nicht mehr unterstützt. Wenn Sie diesen Connector verwenden, müssen Sie Ihre Implementierung entsprechend anpassen. [Mehr dazu](https://helpx.adobe.com/campaign/kb/migrate-to-http2.html)

   ![](assets/nmac_connectors.png)

1. Wählen Sie **[!UICONTROL Speichern]** aus.

Ihr iOS-Connector ist jetzt konfiguriert. Sie können mit dem Einrichten Ihres Dienstes beginnen.

## Konfigurieren des iOS-Dienstes {#configuring-ios-service}

>[!CAUTION]
>
>Bevor Sie die SDK integrieren, ist sicherzustellen, dass die Anwendungen für den Versand von Push-Benachrichtigungen konfiguriert wurden.
>
>Sollte dies nicht der Fall sein, besuchen Sie [diese Seite](https://developer.apple.com/library/archive/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/).

1. Klicken Sie im Knoten **[!UICONTROL Profile und Zielgruppen > Dienste und Abonnements]** auf die Schaltfläche **[!UICONTROL Neu]**.

   ![](assets/nmac_service_1.png)

1. Bestimmen Sie einen **[!UICONTROL Titel]** und einen **[!UICONTROL internen Namen]**.
1. Wählen Sie im Feld **[!UICONTROL Typ]** die Option **[!UICONTROL Mobile App]**.

   >[!NOTE]
   >
   >Das standardmäßig vorgeschlagene Zielgruppen-Mapping **[!UICONTROL Abonnierte Anwendungen (nms:appSubscriptionRcp)]** bezieht sich auf die Empfängertabelle. Sie haben die Möglichkeit, im Feld **[!UICONTROL Zielgruppen-Mapping]** des Dienstes ein anderes, zuvor erstelltes Mapping anzugeben. Weiterführende Informationen hierzu finden Sie im [Konfigurationshandbuch](../../configuration/using/about-custom-recipient-table.md).

   ![](assets/nmac_ios.png)

1. Klicken Sie dann auf die Schaltfläche **[!UICONTROL Hinzufügen]**, um den Anwendungstyp auszuwählen.

   ![](assets/nmac_service_2.png)

1. Erstellen Sie Ihre iOS-Entwicklungs- und -Produktionsanwendungen. Weiterführende Informationen hierzu finden Sie in diesem [Abschnitt](../../delivery/using/configuring-the-mobile-application.md#creating-ios-app).

## Erstellen der mobilen iOS-Anwendung {#creating-ios-app}

Nachdem Sie den Dienst erstellt haben, müssen Sie jetzt Ihre iOS-Anwendung erstellen:

1. Klicken Sie in Ihrem neu erstellten Dienst auf die Schaltfläche **[!UICONTROL Hinzufügen]** , um den Anwendungstyp auszuwählen.

   ![](assets/nmac_service_2.png)

1. Das folgende Fenster wird angezeigt. Wählen Sie **[!UICONTROL iOS-Anwendung erstellen]** und beginnen Sie, indem Sie den **[!UICONTROL Titel]** eingeben.

   ![](assets/nmac_ios_2.png)

1. Bei Bedarf können Sie Inhalte von Push-Nachrichten mit bestimmten **[!UICONTROL Anwendungsvariablen]** anreichern. Diese sind vollständig anpassbar; ein Teil der Payload der Nachricht wird an das Mobilgerät gesendet.
Im folgenden Beispiel werden **mediaURl** und **mediaExt** hinzugefügt, um Rich-Push-Benachrichtigungen zu erstellen. Danach wird der Anwendung das Bild bereitgestellt, das in der Benachrichtigung angezeigt werden soll.

   ![](assets/nmac_ios_3.png)

1. Auf dem Tab **[!UICONTROL Abonnementparameter]** können Sie das Mapping mit einer Erweiterung des Schemas **[!UICONTROL Abonnierte Anwendungen (nms:appsubscriptionRcp)]** definieren.

   >[!NOTE]
   >
   >Vergewissern Sie sich, dass Sie nicht dasselbe Zertifikat sowohl für die Entwicklungsversion (Sandbox) als auch für die Produktionsversion der Anwendung verwenden.

1. Auf dem Tab **[!UICONTROL Töne]** können Sie einen abzuspielenden Ton festlegen. Klicken Sie auf **[!UICONTROL Hinzufügen]** und füllen Sie das Feld **[!UICONTROL Interner Name]** aus, das den Namen der in die Anwendung eingebetteten Datei oder den Namen des Systemtons enthalten muss.

1. Klicken Sie auf **[!UICONTROL Weiter]**, um mit dem Konfigurieren der Entwicklungsanwendung zu beginnen.

1. Stellen Sie sicher, dass in Adobe Campaign und im Anwendungs-Code derselbe **[!UICONTROL Integrationsschlüssel]** definiert ist (über das SDK). Weiterführende Informationen finden Sie unter [Integration des Campaign SDK in Mobile Apps](../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md). Mit diesem anwendungsspezifischen Integrationsschlüssel können Sie die Mobile App mit der Adobe Campaign-Plattform verbinden.

   >[!NOTE]
   >
   > Der **[!UICONTROL Integrationsschlüssel]** kann mit einem Zeichenfolgenwert vollständig angepasst werden, muss jedoch mit dem im SDK angegebenen Schlüssel identisch sein.

1. Select one of the out-of-the-box icons from the **[!UICONTROL Application icon]** field to personalize mobile application in your service.

1. Wählen Sie den **[!UICONTROL Authentifizierungsmodus]**. Beachten Sie, dass Sie den Authentifizierungsmodus jederzeit später auf der Registerkarte &quot; **[!UICONTROL Zertifikat]** &quot;Ihrer mobilen Anwendung ändern können.
   * **[!UICONTROL Zertifikatbasierte Authentifizierung]**: Klicken Sie auf Zertifikat **[!UICONTROL eingeben...]**  Wählen Sie dann Ihren p12-Schlüssel und geben Sie das vom Entwickler der Mobilanwendung bereitgestellte Kennwort ein.
   * **[!UICONTROL Token-basierte Authentifizierung]**: Füllen Sie die Verbindungseinstellungen **[!UICONTROL Key ID]**, **[!UICONTROL Team-ID]** und **[!UICONTROL Bündel-ID]** aus und wählen Sie dann Ihr p8-Zertifikat aus, indem Sie auf den privaten Schlüssel **[!UICONTROL eingeben]** klicken. Weitere Informationen zur **[!UICONTROL Token-basierten Authentifizierung]** finden Sie in der [Apple-Dokumentation](https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_token-based_connection_to_apnsToken-based).

   >[!NOTE]
   >
   > Adobe empfiehlt die Verwendung der **[!UICONTROL Token-basierten Authentifizierung]** für Ihre iOS-Konfiguration, da dieser Authentifizierungsmodus besser gesichert ist und nicht an den Ablauf des Zertifikats gebunden ist.

   ![](assets/nmac_ios_4.png)

1. Sie können **[!UICONTROL Verbindung testen]** auswählen, um zu prüfen, ob die Verbindung erfolgreich hergestellt wurde.

1. Klicken Sie auf **[!UICONTROL Weiter]**, um mit der Konfiguration der Produktionsanwendung zu beginnen, und führen Sie die oben beschriebenen Schritte aus.

   ![](assets/nmac_ios_5.png)

1. Klicken Sie auf **[!UICONTROL Beenden]**.

Ihre iOS-Anwendung kann jetzt in Campaign Classic verwendet werden.

## Creating an iOS rich notification {#creating-ios-delivery}

iOS 10 oder höher ermöglicht die Erstellung von Rich-Benachrichtigungen. Adobe Campaign kann mithilfe von Variablen Benachrichtigungen versenden, durch die das Gerät eine Rich-Benachrichtigung anzeigen kann.

Erstellen Sie dann einen neuen Versand und verknüpfen Sie ihn mit der von Ihnen erstellten Mobile App.

1. Gehen Sie zu **[!UICONTROL Kampagnenverwaltung]** > **[!UICONTROL Sendungen]**.

1. Klicken Sie auf **[!UICONTROL Neu]**.

   ![](assets/nmac_android_3.png)

1. Wählen Sie **[!UICONTROL iOS-Versand (iOS)]** aus der Dropdown-Liste **[!UICONTROL Versandvorlage]**. Fügen Sie Ihrem Versand einen **[!UICONTROL Titel]** hinzu.

1. Klicken Sie auf **[!UICONTROL An]**, um die Zielpopulation zu definieren. Standardmäßig wird das Zielgruppen-Mapping **[!UICONTROL Abonnierte Anwendung]** angewendet. Klicken Sie auf **[!UICONTROL Hinzufügen]**, um den zuvor erstellten Dienst auszuwählen.

   ![](assets/nmac_ios_9.png)

1. Wählen Sie im Fenster **[!UICONTROL Zieltyp]** die Option **[!UICONTROL Abonnenten einer iOS-Mobile-App (iPhone, iPad)]** und klicken Sie auf **[!UICONTROL Weiter]**.

1. Wählen Sie in der Dropdown-Liste **[!UICONTROL Dienst]** den zuvor erstellten Dienst und dann die gewünschte Zielgruppe aus und klicken Sie auf **[!UICONTROL Beenden]**.
Die **[!UICONTROL Anwendungsvariablen]** werden je nachdem, was bei den Konfigurationsschritten hinzugefügt wurde, automatisch hinzugefügt.

   ![](assets/nmac_ios_6.png)

1. Bearbeiten Sie Ihre Rich-Benachrichtigung.

   ![](assets/nmac_ios_7.png)

1. Aktivieren Sie im Fenster zur Benachrichtigungsbearbeitung die Option **[!UICONTROL Veränderlicher Inhalt]** an. Dadurch kann die Mobile App Medieninhalte herunterladen.

1. Klicken Sie auf **[!UICONTROL Speichern]** und führen Sie den Versand durch.

Auf iOS-Mobilgeräten der Abonnenten sollten das Bild und die Web-Seite in der Push-Benachrichtigung angezeigt werden.

![](assets/nmac_ios_8.png)
