---
product: campaign
title: Konfigurieren der Mobile App für Android in Adobe Campaign
description: Erfahren Sie, wie Sie Ihre Mobile App für Android einrichten.
badge-v7-only: label="v7" type="Informative" tooltip="Gilt nur für Campaign Classic v7"
feature: Push
role: User, Developer
exl-id: 32c35e61-d0a3-478f-b73b-396e2becf7f9
source-git-commit: 92c79e7050124bc707f4d6b87c7952016586002c
workflow-type: tm+mt
source-wordcount: '953'
ht-degree: 100%

---

# Konfigurationsschritte für Android

Nachdem das Paket installiert ist, können Sie die Einstellungen Ihrer Android-Mobile-App in Adobe Campaign Classic festlegen.

Die wichtigsten Schritte sind:

1. [Konfigurieren des externen Android-Kontos](#configuring-external-account-android)
1. [Konfigurieren des Android-Service](#configuring-android-service)
1. [Erstellen der Mobile App in Campaign](#creating-android-app)
1. [Erweitern des App-Schemas um zusätzliche Daten](#extend-subscription-schema)

Anschließend können Sie eine [Rich-Benachrichtigung für Android erstellen](create-notifications-android.md).

>[!IMPORTANT]
>
>Einige wichtige Änderungen am FCM-Dienst (Android Firebase Cloud Messaging) werden 2024 veröffentlicht und können sich auf Ihre Implementierung von Adobe Campaign auswirken. Ihre Konfiguration der Anmeldedienste für Android-Push-Nachrichten muss möglicherweise aktualisiert werden, um diese Änderung zu unterstützen. Sie können dies bereits überprüfen und Maßnahmen ergreifen. Weitere Informationen finden Sie in dieser [Technote zu Adobe Campaign v8](https://experienceleague.adobe.com/docs/campaign/technotes-ac/tn-new/push-technote.html?lang=de){target="_blank"}.


## Konfigurieren des externen Android-Kontos {#configuring-external-account-android}

Für Android sind zwei Connectoren verfügbar:

* Der V1-Connector, der pro untergeordnetem MTA eine Verbindung ermöglicht.
* Der V2-Connector, der gleichzeitige Verbindungen zum FCM-Server ermöglicht, um den Durchsatz zu erhöhen.

Wählen Sie den jeweiligen Connector folgendermaßen aus:

1. Gehen Sie zu **[!UICONTROL Administration > Plattform > Externe Konten]**.
1. Wählen Sie das externe Konto **[!UICONTROL Android-Routing]** aus.
1. Füllen Sie im **[!UICONTROL Connector]**-Tab das Feld **[!UICONTROL Connector-JavaScript]** aus:

   Für Android V2: https://localhost:8080/nms/jsp/androidPushConnectorV2.js

   >[!NOTE]
   >
   > Sie können das Feld auch wie folgt konfigurieren: https://localhost:8080/nms/jsp/androidPushConnector.js; wir empfehlen Ihnen jedoch, Version 2 des Connectors zu verwenden.

   ![](assets/nmac_connectors3.png)

1. Für Android V2 ist ein zusätzlicher Parameter in der Adobe-Server-Konfigurationsdatei (serverConf.xml) verfügbar:

   * **maxGCMConnectPerChild**: Maximale Anzahl paralleler HTTP-Abfragen bei FCM durch jeden untergeordneten Server (standardmäßig acht).

## Konfigurieren des Android-Service {#configuring-android-service}

![](assets/do-not-localize/how-to-video.png) [Erfahren Sie im Video, wie Sie einen Android-Dienst konfigurieren](https://experienceleague.adobe.com/docs/campaign-classic-learn/getting-started-with-push-notifications-for-android/configuring-an-android-service-in-campaign.html?lang=de#configuring-an-android-service-and-creating-an-android-mobile-application-in-campaign){target="_blank"}.

1. Klicken Sie im Knoten **[!UICONTROL Profile und Zielgruppen > Dienste und Abonnements]** auf die Schaltfläche **[!UICONTROL Neu]**.

   ![](assets/nmac_service_1.png)

1. Bestimmen Sie einen **[!UICONTROL Titel]** und einen **[!UICONTROL internen Namen]**.
1. Wählen Sie im Feld **[!UICONTROL Typ]** die Option **[!UICONTROL Mobile App]**.

   >[!NOTE]
   >
   >Das standardmäßige Zielgruppen-Mapping für **[!UICONTROL abonnierte Anwendungen (nms:appSubscriptionRcp)]** ist mit der Empfängertabelle verknüpft. Wenn Sie ein anderes Zielgruppen-Mapping verwenden möchten, müssen Sie ein neues Zielgruppen-Mapping erstellen und es im Feld **[!UICONTROL Zielgruppen-Mapping]** des Dienstes eingeben. Weiterführende Informationen zur Erstellung des Zielgruppen-Mappings finden Sie in [diesem Abschnitt](../../configuration/using/about-custom-recipient-table.md).

   ![](assets/nmac_ios.png)

1. Klicken Sie dann auf die Schaltfläche **[!UICONTROL Hinzufügen]**, um den Anwendungstyp auszuwählen.

   ![](assets/nmac_service_2.png)

1. Erstellen Sie Ihre Android-Mobile-App. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](configuring-the-mobile-application-android.md#creating-android-app).

## Android-Mobile-App erstellen {#creating-android-app}

Nachdem Sie den Dienst erstellt haben, müssen Sie jetzt Ihre Android-Mobile-App erstellen:

1. Klicken Sie in Ihrem neu erstellten Dienst auf die Schaltfläche **[!UICONTROL Hinzufügen]**, um den Anwendungstyp auszuwählen.

   ![](assets/nmac_service_2.png)

1. Wählen Sie **[!UICONTROL Android-Anwendung erstellen]** aus und geben Sie einen **[!UICONTROL Titel]** ein.

   ![](assets/nmac_android.png)

1. Stellen Sie sicher, dass in Adobe Campaign und im Anwendungs-Code derselbe **[!UICONTROL Integrationsschlüssel]** definiert ist (über das SDK). Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](integrating-campaign-sdk-into-the-mobile-application.md).

   >[!NOTE]
   >
   > Der **[!UICONTROL Integrationsschlüssel]** kann mit einem Zeichenfolgenwert vollständig angepasst werden, muss jedoch mit dem im SDK angegebenen Schlüssel identisch sein.

1. Wählen Sie die **[!UICONTROL API-Version]** aus: HTTP Version 1 oder HTTP (frühere Version). Näheres zu diesen Konfigurationen finden Sie in [diesem Abschnitt](#select-api-version).

1. Füllen Sie die Felder für **[!UICONTROL Verbindungsparameter für Firebase Cloud Messaging for Android]** aus.

1. Klicken Sie auf **[!UICONTROL Beenden]** und danach auf **[!UICONTROL Speichern]**. Ihre Android-Anwendung kann jetzt in Campaign Classic verwendet werden.

Standardmäßig speichert Adobe Campaign einen Schlüssel im Feld **[!UICONTROL User-Kennung]** (@userKey) der Tabelle **[!UICONTROL Abonnentenanwendungen (nms:appSubscriptionRcp)]**. Mit diesem Schlüssel können Sie ein Abonnement mit einem Empfänger verknüpfen. Um zusätzliche Daten (z. B. einen komplexen Abstimmschlüssel) zu erfassen, müssen Sie die folgende Konfiguration übernehmen:

### Konfigurieren der API-Version{#select-api-version}

>[!IMPORTANT]
>
>Einige wichtige Änderungen am FCM-Dienst (Android Firebase Cloud Messaging) werden 2024 veröffentlicht und können sich auf Ihre Implementierung von Adobe Campaign auswirken. Im Rahmen der kontinuierlichen Bemühungen von Google, seine Dienste zu verbessern, werden die veralteten FCM-APIs am **20. Juni 2024** eingestellt. Weitere Informationen finden Sie in dieser [Technote zu Adobe Campaign v8](https://experienceleague.adobe.com/docs/campaign/technotes-ac/tn-new/push-technote.html?lang=de){target="_blank"}.

Nachdem Sie einen Dienst und eine neue Mobile App erstellt haben, müssen Sie Ihre Mobile App entsprechend der ausgewählten API-Version konfigurieren. Die **HTTP-API (veraltet)** sollte nicht ausgewählt werden, da sie von Google nicht mehr unterstützt wird.

Gehen Sie wie folgt vor, um die HTTP v1-API-Version zu konfigurieren:

1. Wählen Sie im Fenster des **[!UICONTROL Mobile-App-Assistenten]** die Option **[!UICONTROL HTTP v1]** aus der Dropdown-Liste **[!UICONTROL API-Version]** aus.

1. Klicken Sie auf **[!UICONTROL Projekt-JSON-Datei zum Extrahieren der Projektdetails laden...]**, um Ihre JSON-Schlüsseldatei direkt zu laden. Weitere Informationen dazu, wie Sie die JSON-Datei extrahieren, finden Sie auf [dieser Seite](https://firebase.google.com/docs/admin/setup#initialize-sdk).

   Sie können auch die folgenden Details manuell eingeben:
   * **[!UICONTROL Projektkennung]**
   * **[!UICONTROL Privater Schlüssel]**
   * **[!UICONTROL Client-E-Mail]**

   ![](assets/nmac_android_10.png)

1. Klicken Sie auf **[!UICONTROL Verbindung testen]**, um zu prüfen, ob Ihre Konfiguration korrekt ist und ob der Marketing-Server Zugriff auf den FCM-Server hat.

   >[!CAUTION]
   >
   >Bei Mid-Sourcing-Bereitstellungen wird mit der Schaltfläche **[!UICONTROL Verbindung testen]** nicht geprüft, ob der MID-Server Zugriff auf den FCM-Server hat.

   ![](assets/nmac_android_11.png)

1. Bei Bedarf können Sie die Inhalte von Push-Nachrichten mit bestimmten **[!UICONTROL Anwendungsvariablen]** anreichern. Diese sind vollständig anpassbar und Teil der an das mobile Gerät gesendeten Nachrichten-Payload.

1. Klicken Sie auf **[!UICONTROL Beenden]** und danach auf **[!UICONTROL Speichern]**. Ihre Android-Anwendung kann jetzt in Campaign Classic verwendet werden.

Im Folgenden finden Sie die FCM-Payload-Namen, mit denen Sie Ihre Push-Benachrichtigung weiter personalisieren können:

| Nachrichtentyp | Konfigurierbares Nachrichtenelement (FCM-Payload-Name) | Konfigurierbare Optionen (Name der FCM-Payload) |
|:-:|:-:|:-:|
| Datennachricht | K. A. | validate_only |
| Benachrichtigungsinhalt | title, body, android_channel_id, icon, sound, tag, color, click_action, image, ticker, sticky, visibility, notification_priority, notification_count <br> | validate_only |

## Erweitern des appsubscriptionRcp-Schemas {#extend-subscription-schema}

![](assets/do-not-localize/how-to-video.png) [Erfahren Sie im Video, wie Sie das appsubscriptionRcp-Schema erweitern](https://experienceleague.adobe.com/docs/campaign-classic-learn/getting-started-with-push-notifications-for-android/extending-the-app-subscription-schema.html?lang=de#extending-the-app-subscription-schema-to-personalize-push-notifications)

Sie müssen die **appsubscriptionRcp** erweitern, um in der Campaign-Datenbank neue zusätzliche Felder zum Speichern von Parametern aus der App zu definieren. Diese Felder werden beispielsweise für die Personalisierung verwendet. Gehen Sie dazu wie folgt vor:

1. Erstellen Sie eine Erweiterung des Schemas **[!UICONTROL Abonnentenanwendungen (nms:appsubscriptionRcp)]** und definieren Sie die neuen Felder. Weitere Informationen zur Erweiterung eines Schemas finden Sie auf [dieser Seite](../../configuration/using/about-schema-edition.md)

1. Geben Sie im Tab **[!UICONTROL Abonnementparameter]** das Mapping an.

   >[!CAUTION]
   >
   >Stellen Sie sicher, dass die Parameterbezeichnungen im Tab **[!UICONTROL Abonnementparameter]** mit denen im Anwendungs-Code übereinstimmen. Weitere Informationen finden Sie in [diesem Abschnitt](integrating-campaign-sdk-into-the-mobile-application.md).
