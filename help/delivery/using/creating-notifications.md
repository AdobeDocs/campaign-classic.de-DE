---
title: Benachrichtigungen erstellen
seo-title: Benachrichtigungen erstellen
description: Benachrichtigungen erstellen
seo-description: null
page-status-flag: never-activated
uuid: fb1862df-e616-4147-a642-dc867bc983b5
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
discoiquuid: 345af5c2-c852-4086-8ed0-ff3e7e402e04
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b78db689958c9b240da9a0315060fe63bcb48e0a

---


# Benachrichtigungen erstellen{#creating-notifications}

Dieser Abschnitt beschreibt die spezifischen Elemente eines Benachrichtigungsversands für iOS- oder Android-Geräte. Allgemeine Methoden zur Versanderstellung finden Sie in [diesem Abschnitt](../../delivery/using/steps-about-delivery-creation-steps.md).

Erstellen Sie zunächst einen neuen Versand:

![](assets/nmac_delivery_1.png)

## Versand von Benachrichtigungen auf iOS-Geräte {#sending-notifications-on-ios}

1. Wählen Sie die **[!UICONTROL Deliver on iOS]** Bereitstellungsvorlage aus.

   ![](assets/nmac_delivery_ios_1.png)

1. To define the target of the notification, click the **[!UICONTROL To]** link, then click **[!UICONTROL Add]**.

   ![](assets/nmac_delivery_ios_2.png)

   >[!NOTE]
   >
   >Die detaillierten Schritte zur Auswahl der Zielpopulation eines Versands finden Sie in [diesem Abschnitt](../../delivery/using/steps-defining-the-target-population.md).
   >
   >For more on the use of personalization fields, refer to [About personalization](../../delivery/using/about-personalization.md).
   >
   >For more on the inclusion of a seed list, refer to [About seed addresses](../../delivery/using/about-seed-addresses.md).

1. Wählen Sie **[!UICONTROL Subscribers of an iOS mobile application (iPhone, iPad)]** den Dienst, der für Ihre Mobilanwendung relevant ist (in diesem Fall Neotrips), und wählen Sie dann die iOS-Version der Anwendung aus.

   ![](assets/nmac_delivery_ios_3.png)

1. Wählen Sie den Benachrichtigungstyp aus: **[!UICONTROL Alert]**, **[!UICONTROL Badge]** oder **[!UICONTROL Alert and badge]** oder **[!UICONTROL Silent Push]**.

   ![](assets/nmac_delivery_ios_4.png)

   >[!NOTE]
   >
   >Der **Silent Push**-Modus ist ab iOS-Version 7 verfügbar und ermöglicht den Versand einer &quot;stillen&quot; Benachrichtigung an eine Mobile App. Der Benutzer wird über die Ankunft der Benachrichtigung nicht in Kenntnis gesetzt, da diese direkt an die Anwendung übermittelt wird.

1. Geben Sie im **[!UICONTROL Title]** Feld die Bezeichnung des Titels ein, der in der Benachrichtigung angezeigt werden soll. Sie wird nur in der Liste der Benachrichtigungen angezeigt, die im Benachrichtigungscenter verfügbar sind. Mit diesem Feld können Sie den Wert des **title** -Parameters der iOS-Benachrichtigungs-Payload definieren.
1. If you use the HTTP/2 connector, you can add a subtitle (value of the **subtitle** parameter of the iOS notification payload). Weitere Informationen finden Sie im Abschnitt [Konfigurieren der mobilen Anwendung in Adobe Campaign](../../delivery/using/configuring-the-mobile-application.md) .
1. Geben Sie dann den **[!UICONTROL Message]** und den **[!UICONTROL Value of the badge]** basierend auf dem ausgewählten Benachrichtigungstyp ein.

   ![](assets/nmac_delivery_ios_5.png)

   >[!NOTE]
   >
   >Sie können zum Inhalt Ihrer Benachrichtigung Emojis hinzufügen. Gehen Sie hierzu auf eine Website mit Emojis ([Beispiel](https://www.utf8-chartable.de/unicode-utf8-table.pl?start=9728)), kopieren Sie ein Emoji und fügen Sie es direkt in den Inhaltseditor ein. Unter Windows 7 werden einige Emojis im Editor möglicherweise nicht korrekt angezeigt (viereckiges Symbol), in der endgültigen E-Mail sollten sie aber korrekt erscheinen. Die Darstellungsmöglichkeit von Emojis hängt vom jeweiligen Betriebssystem des Geräts ab. Wir empfehlen eine Testsendung, um sicherzustellen, dass der Versand korrekt dargestellt wird.

   >[!NOTE]
   >
   >**[!UICONTROL Badge]** und **[!UICONTROL Alert and badge]** Typbenachrichtigungen ermöglichen es Ihnen, den Wert des Zeichens (die Zahl über dem Logo der mobilen Anwendung) zu ändern. Um das Zeichen zu aktualisieren, müssen Sie einfach 0 als Wert eingeben. Wenn das Feld leer ist, ändert sich der Kennzeichnungswert nicht.

1. Mit der **[!UICONTROL Action button]** können Sie eine Beschriftung für die Aktionsschaltfläche definieren, die in den Warnhinweisen angezeigt wird (Feld **action_loc_key** der Nutzlast). Wenn Ihre iOS-Anwendung lokalisierbare Zeichenfolgen (**Localizable.strings**) verwaltet, geben Sie den entsprechenden Schlüssel in dieses Feld ein. Wenn Ihre Anwendung nicht lokalisierbaren Text verwaltet, geben Sie die Beschriftung ein, die auf der Aktionsschaltfläche angezeigt werden soll. Weitere Informationen zu lokalisierbaren Zeichenfolgen finden Sie in der [Apple-Dokumentation](https://developer.apple.com/library/archive/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/CreatingtheNotificationPayload.html#//apple_ref/doc/uid/TP40008194-CH10-SW1) .
1. In the **[!UICONTROL Play a sound]** field, select the sound to be played by the mobile terminal when the notification is received.

   >[!NOTE]
   >
   >Sounds müssen in die Anwendung eingeschlossen und beim Erstellen des Dienstes definiert werden. Siehe [Konfigurieren des externen iOS-Kontos](../../delivery/using/configuring-the-mobile-application.md#configuring-external-account-ios).

1. Geben Sie in das **[!UICONTROL Application variables]** Feld den Wert der einzelnen Variablen ein. Mit Anwendungsvariablen können Sie das Benachrichtigungsverhalten definieren: Sie können beispielsweise einen bestimmten Anwendungsbildschirm konfigurieren, der angezeigt wird, wenn der Benutzer die Benachrichtigung aktiviert.

   >[!NOTE]
   >
   >Anwendungsvariablen müssen im Code der mobilen Anwendung definiert und bei der Diensterstellung eingegeben werden. For more on this, refer to: [Configuring a mobile application in Adobe Campaign](../../delivery/using/configuring-the-mobile-application.md).

1. Once the notification is configured, click the **[!UICONTROL Preview]** tab to preview the notification.

   ![](assets/nmac_intro_2.png)

   >[!NOTE]
   >
   >Der Hinweisstil (Banner oder Hinweis) ist in Adobe Campaign nicht im Vorhinein festgelegt. Er hängt von der vom Benutzer in den iOS-Einstellungen gewählten Konfiguration ab. Adobe Campaign ermöglicht es jedoch, eine Vorschau der Benachrichtigung in jedem Stil anzuzeigen. Verwenden Sie den unten rechts im Bildschirm gelegenen Pfeil, um von einem Stil zum anderen zu wechseln.
   >
   >In der Vorschau wird das Erscheinungsbild von iOS 10 verwendet.

Testsendungen und der endgültige Start des Versands werden analog zum E-Mail-Versand durchgeführt.

Nach Absenden der Nachrichten können Sie den Versand beobachten und verfolgen, siehe diese Abschnitte:

* [Quarantäne für Push-Benachrichtigungen](../../delivery/using/understanding-quarantine-management.md#push-notification-quarantines)
* [Sendungen beobachten](../../delivery/using/monitoring-a-delivery.md)
* [Ursachen von fehlgeschlagenen Sendungen](../../delivery/using/understanding-delivery-failures.md)

## Versand von Benachrichtigungen auf Android-Geräte {#sending-notifications-on-android}

1. Wählen Sie zunächst die **[!UICONTROL Deliver on Android (android)]** Bereitstellungsvorlage aus.

   ![](assets/nmac_delivery_android_1.png)

1. To define the target of the notification, click the **[!UICONTROL To]** link, then click **[!UICONTROL Add]**.

   ![](assets/nmac_delivery_android_2.png)

1. Select **[!UICONTROL Subscribers of an Android mobile application]**, choose the service relevant to your mobile application (Neotrips, in this case), then select the Android version of the application.

   ![](assets/nmac_delivery_android_3.png)

1. Erfassen Sie den Inhalt der Benachrichtigung.

   ![](assets/nmac_delivery_android_4.png)

   >[!NOTE]
   >
   >Sie können zum Inhalt Ihrer Benachrichtigung Emojis hinzufügen. Gehen Sie hierzu auf eine Website mit Emojis ([Beispiel](https://www.utf8-chartable.de/unicode-utf8-table.pl?start=9728)), kopieren Sie ein Emoji und fügen Sie es direkt in den Inhaltseditor ein. Unter Windows 7 werden einige Emojis im Editor möglicherweise nicht korrekt angezeigt (viereckiges Symbol), in der endgültigen E-Mail sollten sie aber korrekt erscheinen. Die Darstellungsmöglichkeit von Emojis hängt vom jeweiligen Betriebssystem des Geräts ab. Wir empfehlen eine Testsendung, um sicherzustellen, dass der Versand korrekt dargestellt wird.

1. Geben Sie in das **[!UICONTROL Application variables]** Feld den Wert der einzelnen Variablen ein. Mit Anwendungsvariablen können Sie das Benachrichtigungsverhalten definieren: Sie können beispielsweise einen bestimmten Anwendungsbildschirm konfigurieren, der angezeigt wird, wenn der Benutzer die Benachrichtigung aktiviert.

   >[!NOTE]
   >
   >Anwendungsvariablen müssen im Code der mobilen Anwendung definiert und bei der Diensterstellung eingegeben werden. For more on this, refer to: [Configuring a mobile application in Adobe Campaign](../../delivery/using/configuring-the-mobile-application.md).

1. Once the notification is configured, click the **[!UICONTROL Preview]** tab to preview the notification.

   ![](assets/nmac_intro_1.png)

Testsendungen und der endgültige Start des Versands werden analog zum E-Mail-Versand durchgeführt.

Die detaillierten Schritte zur Validierung und zum Versand von Nachrichten finden Sie in den folgenden Abschnitten:

* [Versand validieren](../../delivery/using/steps-validating-the-delivery.md)
* [Versenden der Nachrichten](../../delivery/using/steps-sending-the-delivery.md)

Nach Absenden der Nachrichten können Sie den Versand beobachten und verfolgen, siehe diese Abschnitte:

* [Quarantäne für Push-Benachrichtigungen](../../delivery/using/understanding-quarantine-management.md#push-notification-quarantines)
* [Sendungen beobachten](../../delivery/using/monitoring-a-delivery.md)
* [Ursachen von fehlgeschlagenen Sendungen](../../delivery/using/understanding-delivery-failures.md)
