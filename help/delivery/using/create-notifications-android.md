---
product: campaign
title: Push-Benachrichtigung für Android-Geräte erstellen
description: Erfahren Sie, wie Sie Push-Benachrichtigungen für Android erstellen.
badge-v7-only: label="v7" type="Informative" tooltip="Gilt nur für Campaign Classic v7"
feature: Push
role: User, Developer, Data Engineer
exl-id: 13ccc5d6-4355-42ba-80dc-30a45d3b69a4
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: ht
source-wordcount: '823'
ht-degree: 100%

---

# Erstellen von Benachrichtigungen für Android{#create-notificaations-android}

Verwenden Sie Adobe Campaign, um Push-Benachrichtigungen an Android-Geräte zu senden. Allgemeine Methoden zur Versanderstellung finden Sie in [diesem Abschnitt](steps-about-delivery-creation-steps.md).

Erstellen Sie zunächst einen neuen Versand:

![](assets/nmac_delivery_1.png)

Bei Firebase Cloud Messaging stehen Ihnen zwei Nachrichtentypen zur Auswahl:

* **[!UICONTROL Datennachricht]** – wird von der Client-Mobile-App verarbeitet.
  <br>Nachrichten werden direkt an die Mobile App gesendet, die die Android-Benachrichtigung erstellt und auf dem Gerät anzeigt. Datennachrichten enthalten nur die von Ihnen definierten Anwendungsvariablen.

* **[!UICONTROL Benachrichtigungsinhalt]** – wird automatisch vom FCM SDK verarbeitet.
  <br> FCM übernimmt für die Client-Mobile-App automatisch das Anzeigen der Nachricht auf den Geräten Ihrer Benutzer. Benachrichtigungsinhalte enthalten einen vordefinierten Satz von Parametern und Optionen, können aber mit benutzerspezifischen Anwendungsvariablen weiter personalisiert werden.

Weitere Informationen zu Firebase Cloud Messaging-Nachrichtentypen finden Sie in der [FCM-Dokumentation](https://firebase.google.com/docs/cloud-messaging/concept-options#notifications_and_data_messages).

## Datennachricht erstellen {#creating-data-message}

1. Gehen Sie zu **[!UICONTROL Kampagnenverwaltung]** > **[!UICONTROL Sendungen]**.

1. Klicken Sie auf **[!UICONTROL Neu]**.

   ![](assets/nmac_android_3.png)

1. Wählen Sie **[!UICONTROL Android-Versand (Android)]** aus der Dropdown-Liste **[!UICONTROL Versandvorlage]**. Fügen Sie Ihrem Versand einen **[!UICONTROL Titel]** hinzu.

1. Klicken Sie auf **[!UICONTROL An]**, um die Zielpopulation zu definieren. Standardmäßig wird das Zielgruppen-Mapping **[!UICONTROL Abonnierte Anwendung]** angewendet. Klicken Sie auf **[!UICONTROL Hinzufügen]**, um Ihren Dienst auszuwählen.

   ![](assets/nmac_android_7.png)

1. Wählen Sie im Fenster **[!UICONTROL Zieltyp]****** die Option &quot;Abonnenten einer Android-Mobile-App&quot; aus und klicken Sie auf **[!UICONTROL Weiter]**.

1. Wählen Sie aus der Dropdown-Liste **[!UICONTROL Dienst]** den zuvor erstellten Dienst und dann die Anwendung aus. Klicken Sie anschließend auf **[!UICONTROL Beenden]**.
Die **[!UICONTROL Anwendungsvariablen]** werden je nachdem, was bei den Konfigurationsschritten hinzugefügt wurde, automatisch hinzugefügt.

   ![](assets/nmac_android_6.png)

1. Wählen Sie **[!UICONTROL Datennachricht]** als **[!UICONTROL Nachrichtentyp]** aus.

1. Bearbeiten Sie Ihre Rich-Benachrichtigung.

   ![](assets/nmac_android_5.png)

1. Bei Bedarf können Sie den zuvor konfigurierten **[!UICONTROL Anwendungsvariablen]** Informationen hinzufügen. **[!UICONTROL Anwendungsvariablen]** müssen im Android-Dienst konfiguriert werden und sind Teil der an das Mobilgerät gesendeten Nachrichten-Payload.

1. Klicken Sie auf **[!UICONTROL Speichern]** und führen Sie den Versand durch.

Auf den Android-Mobilgeräten der Abonnenten sollten das Bild und die Webseite in der Push-Benachrichtigung angezeigt werden.

![](assets/nmac_android_4.png)

## Erstellen von Benachrichtigungsinhalten {#creating-notification-message}

>[!NOTE]
>
>Zusätzliche Optionen für Benachrichtigungsinhalte sind nur bei der HTTP v1-API-Konfiguration verfügbar. Weitere Informationen hierzu finden Sie in [diesem Abschnitt](configuring-the-mobile-application-android.md#android-service-httpv1).

![](assets/do-not-localize/how-to-video.png) [Erfahren Sie im Video, wie Sie eine Android-Push-Benachrichtigung erstellen](https://experienceleague.adobe.com/docs/campaign-classic-learn/getting-started-with-push-notifications-for-android/configuring-and-sending-push-notifications.html?lang=de#additional-resources)

1. Gehen Sie zu **[!UICONTROL Kampagnenverwaltung]** > **[!UICONTROL Sendungen]**.

1. Klicken Sie auf **[!UICONTROL Neu]**.

   ![](assets/nmac_android_3.png)

1. Wählen Sie **[!UICONTROL Android-Versand (Android)]** aus der Dropdown-Liste **[!UICONTROL Versandvorlage]**. Fügen Sie Ihrem Versand einen **[!UICONTROL Titel]** hinzu.

1. Klicken Sie auf **[!UICONTROL An]**, um die Zielpopulation zu definieren. Standardmäßig wird das Zielgruppen-Mapping **[!UICONTROL Abonnierte Anwendung]** angewendet. Klicken Sie auf **[!UICONTROL Hinzufügen]**, um Ihren Dienst auszuwählen.

   ![](assets/nmac_android_7.png)

1. Wählen Sie im Fenster **[!UICONTROL Zieltyp]****** die Option &quot;Abonnenten einer Android-Mobile-App&quot; aus und klicken Sie auf **[!UICONTROL Weiter]**.

1. Wählen Sie aus der Dropdown-Liste **[!UICONTROL Dienst]** den zuvor erstellten Dienst und dann die Anwendung aus. Klicken Sie anschließend auf **[!UICONTROL Beenden]**.

   ![](assets/nmac_android_6.png)

1. Wählen Sie **[!UICONTROL Benachrichtigungsinhalt]** als **[!UICONTROL Nachrichtentyp]** aus.

1. Geben Sie einen Titel an und bearbeiten Sie Ihre Nachricht. Personalisieren Sie Ihre Push-Benachrichtigung über die **[!UICONTROL Benachrichtigungsoptionen]**:

   * **[!UICONTROL Kennung des Kanals]**: Legt die Kennung des Kanals Ihrer Benachrichtigung fest. Die Mobile App muss einen Kanal mit dieser Kennung erstellen, bevor eine Benachrichtigung mit dieser Kanalkennung empfangen werden kann.
   * **[!UICONTROL Ton]**: Legt den Ton fest, der abgespielt werden soll, wenn das Gerät Ihre Benachrichtigung empfängt.
   * **[!UICONTROL Farbe]**: Legt die für das Symbol der Benachrichtigung verwendete Farbe fest.
   * **[!UICONTROL Symbol]**: Legt das Symbol fest, das für die Benachrichtigung auf den Geräten Ihrer Profile angezeigt werden soll.
   * **[!UICONTROL Tag]**: Legt die Kennung fest, die zum Ersetzen bestehender Benachrichtigungen in der Benachrichtigungsablage verwendet werden soll.
   * **[!UICONTROL Klick-Aktion]**: Legt die Aktion fest, die für das Klicken eines Benutzers auf Ihre Benachrichtigung zugewiesen ist.

   Weitere Informationen zu den **[!UICONTROL Benachrichtigungsoptionen]** und dazu, wie diese Felder auszufüllen sind, finden Sie in der [FCM-Dokumentation](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#androidnotification).

   ![](assets/nmac_android_8.png)

1. Wenn Ihre Anwendung mit dem HTTP v1-API-Protokoll konfiguriert ist, können Sie Ihre Push-Benachrichtigung mit den folgenden **[!UICONTROL zusätzlichen HTTP v1-Optionen]** weiter personalisieren:

   * **[!UICONTROL Ticker]**: Legt den Ticker-Text Ihrer Benachrichtigung fest. Nur verfügbar bei Geräten mit Android 5.0 Lollipop.
   * **[!UICONTROL Bild]**: Legt die URL des Bilds fest, das in Ihrer Benachrichtigung angezeigt werden soll.
   * **[!UICONTROL Anzahl der Benachrichtigungen]**: Legt die Zahl der neuen ungelesenen Informationen fest, die direkt auf dem Mobile-App-Symbol angezeigt werden.
   * **[!UICONTROL Sticky]**: Auf &quot;Wahr&quot; oder &quot;Falsch&quot; setzen. Bei der Einstellung &quot;Falsch&quot; wird die Benachrichtigung automatisch geschlossen, wenn der Benutzer darauf klickt. Bei der Einstellung &quot;Wahr&quot; wird die Benachrichtigung weiter angezeigt, wenn der Benutzer darauf klickt.
   * **[!UICONTROL Benachrichtigungspriorität]**: Sie können für Ihre Benachrichtigung die Prioritätsstufen &quot;Standard&quot;, &quot;Minimum&quot;, &quot;Niedrig&quot; oder &quot;Hoch&quot; festlegen. Weitere Informationen hierzu finden Sie in der [FCM-Dokumentation](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#NotificationPriority).
   * **[!UICONTROL Sichtbarkeit]**: Sie können für Ihre Benachrichtigung die Sichtbarkeitsstufen &quot;Öffentlich&quot;, &quot;Privat&quot; oder &quot;Geheim&quot; festlegen. Weitere Informationen hierzu finden Sie in der [FCM-Dokumentation](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#visibility).

   Weitere Informationen zu den **[!UICONTROL zusätzlichen HTTP v1-Optionen]** und dazu, wie diese Felder auszufüllen sind, finden Sie in der [FCM-Dokumentation](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#androidnotification).

   ![](assets/nmac_android_9.png)

1. Bei Bedarf können Sie den zuvor konfigurierten **[!UICONTROL Anwendungsvariablen]** Informationen hinzufügen. **[!UICONTROL Anwendungsvariablen]** müssen im Android-Dienst konfiguriert werden und sind Teil der an das Mobilgerät gesendeten Nachrichten-Payload.

1. Klicken Sie auf **[!UICONTROL Speichern]** und führen Sie den Versand durch.

Auf den Android-Mobilgeräten der Abonnenten sollten das Bild und die Webseite in der Push-Benachrichtigung angezeigt werden.
