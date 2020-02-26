---
title: Konfigurieren der Veröffentlichung auf Twitter
seo-title: Konfigurieren der Veröffentlichung auf Twitter
description: Konfigurieren der Veröffentlichung auf Twitter
seo-description: null
page-status-flag: never-activated
uuid: 88867881-fb59-4f0d-862e-537d498e9aef
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: social
content-type: reference
topic-tags: configuration
discoiquuid: 9d74ed9c-0055-4556-a205-6e5fea11816b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 963aaa81971a8883b944bfcf4d1a00d729627916

---


# Konfigurieren der Veröffentlichung auf Twitter{#configuring-publishing-on-twitter}

Damit Adobe Campaign Tweets an Ihre Twitter-Konten senden kann, müssen Sie den Schreibzugriff für diese Konten an Adobe Campaign delegieren. Wenden Sie dazu die folgenden Konfigurationsschritte an:

* Erstellen Sie ein Twitter-Konto.
* Erstellen Sie ein Twitter-Testkonto zum Senden von Proofs.
* Erstellen Sie eine Twitter-Anwendung pro Twitter-Konto.
* Erstellen Sie für jede Twitter-Anwendung einen neuen **[!UICONTROL Twitter]** Typ-Dienst.

![](assets/social_diagram_twitter_service.png)

## Voraussetzungen {#prerequisites}

Erstellen Sie zunächst ein oder mehrere Twitter-Konten, an die Ihre Tweets gesendet werden sollen.

Um ein Twitter-Konto zu erstellen, gehen Sie zu [https://twitter.com](https://twitter.com).

## Testkonto auf Twitter erstellen {#creating-a-test-account-on-twitter}

Es wird außerdem empfohlen, ein privates Twitter-Konto zu erstellen, das zum Senden von Tweet-Proofs verwendet werden kann (weitere Informationen hierzu finden Sie unter [Senden des Tests](../../social/using/publishing-on-twitter.md#sending-the-proof)):

* Erstellen Sie ein neues Twitter-Konto.
* Klicken Sie auf das Menü in der oberen rechten Ecke und wählen Sie **[!UICONTROL Settings]**.
* Wählen Sie die **[!UICONTROL Security and privacy]** Registerkarte und aktivieren Sie das **[!UICONTROL Protect my Tweets]** Kontrollkästchen.
* Klicken Sie auf die **[!UICONTROL Save Changes]** Schaltfläche unten auf der Seite.

![](assets/social_twitter_test_page.png)

## Erstellen einer Anwendung auf Twitter {#creating-an-application-on-twitter}

Damit Adobe Campaign Tweets an Ihre Twitter-Konten senden kann, müssen Sie eine Twitter-Anwendung pro Twitter-Konto erstellen. Gehen Sie hierzu wie folgt vor:

1. Melden Sie sich bei Ihrem Twitter-Konto an.
1. Geben Sie folgende Adresse in Ihren Internetbrowser ein: [https://apps.twitter.com/](https://apps.twitter.com/).
1. Klicken Sie dann auf die **[!UICONTROL Create New App]** Schaltfläche rechts.

   ![](assets/social_create_twitter_app_001.png)

1. Der Assistent führt Sie durch den Prozess.

   Damit diese Anwendung es Adobe Campaign ermöglicht, Tweets an Ihr Konto zu senden, gehen Sie zur **[!UICONTROL Permissions]** Registerkarte der Anwendung und wählen Sie **[!UICONTROL Read and Write]** für den **[!UICONTROL Access]** Abschnitt aus. Auf der **[!UICONTROL Settings]** Registerkarte müssen Sie das **[!UICONTROL Callback URL]** Feld auch leer lassen.

   ![](assets/social_create_twitter_app_002.png)

## Delegieren von Schreibzugriff auf Adobe Campaign {#delegating-write-access-to-adobe-campaign}

Für jede Twitter-Anwendung müssen Sie einen anderen **[!UICONTROL Twitter]** Typdienst erstellen, der die Anwendungseinstellungen enthält.

Dieser Schritt erfordert gleichzeitigen Zugriff auf Ihre Adobe Campaign-Konsole und einen Internetbrowser, der bei Ihrem Twitter-Konto angemeldet ist:

* **Twitter**: Wählen Sie die zuvor erstellte Anwendung aus ([https://dev.twitter.com/apps](https://dev.twitter.com/apps)) und klicken Sie auf die **[!UICONTROL Keys and Access Tokens]** Registerkarte.

   ![](assets/social_twitter_service_002.png)

* **Adobe Campaign**: gehen Sie zum **[!UICONTROL Profiles and targets]** Universum, klicken Sie auf den **[!UICONTROL Services and Subscriptions]** Link und klicken Sie auf die **[!UICONTROL Create]** Schaltfläche.

   ![](assets/social_twitter_service_007.png)

1. Select the **[!UICONTROL Twitter]** type.

   ![](assets/social_twitter_service_008.png)

   >[!NOTE]
   >
   >The **[!UICONTROL Synchronize subscriptions]** option is enabled by default. Wenn das Kontrollkästchen aktiviert ist, stellt der Arbeitsablauf für die Synchronisierung von Twitter-Konten (siehe [Synchronisieren von Twitter-Konten](#synchronizing-twitter-accounts)) die Liste der Twitter-Follower wieder her, sodass Sie ihnen Direktnachrichten senden können (siehe [Senden von Direktnachrichten an Abonnenten](../../social/using/publishing-on-twitter.md#sending-direct-messages-to-subscribers)). Wenn Sie die Liste der Follower nicht wiederherstellen möchten, deaktivieren Sie dieses Kontrollkästchen.

1. Geben Sie die Bezeichnung und den internen Namen des Dienstes ein.

   ![](assets/social_twitter_service_009.png)

   >[!IMPORTANT]
   >
   >Der Name **[!UICONTROL Internal name]** des Dienstes muss mit dem Namen des Twitter-Kontos identisch sein. Gehen Sie wie folgt vor, um sicherzustellen, dass keine Eintragsfehler auftreten.

   * Click the **[!UICONTROL Save]** button.
   * Klicken Sie in der Übersicht der Dienste auf den soeben erstellten Twitter-Dienst.
   * Wählen Sie die **[!UICONTROL Twitter page]** Registerkarte. Das Twitter-Konto sollte angezeigt werden.

      ![](assets/social_twitter_service_010.png)

1. Wählen Sie im **[!UICONTROL Visitor folder]** Feld den Besucherordner aus, in dem die Follower erstellt werden sollen. For more on this, refer to [Operating principle](../../social/using/publishing-on-twitter.md#operating-principle). Standardmäßig werden Follower im Stammordner des **[!UICONTROL Visitors]** Ordners erstellt.

   ![](assets/social_twitter_service_010_b.png)

1. Kopieren Sie auf Twitter den Inhalt der **[!UICONTROL Consumer Key (API Key)]** und der **[!UICONTROL Consumer Secret (API Secret)]** Felder und fügen Sie ihn in die Felder **[!UICONTROL Consumer key]** und **[!UICONTROL Consumer secret]** Felder der Konsole ein.

   ![](assets/social_twitter_service_012.png)

1. Kopieren Sie auf Twitter den Inhalt der **[!UICONTROL Access Token]** und der **[!UICONTROL Access Token Secret]** Felder und fügen Sie ihn in die Felder **[!UICONTROL Access token]** und **[!UICONTROL Access token secret]** Felder der Konsole ein.

   ![](assets/social_twitter_service_013.png)

1. Klicken Sie in der Adobe Campaign-Konsole auf **[!UICONTROL Save]**. Die Übertragung des Schreibzugriffs auf Adobe Campaign ist nun abgeschlossen.

   ![](assets/social_twitter_service_014.png)

>[!NOTE]
>
>Pro Twitter-Anwendung müssen Sie einen **[!UICONTROL Twitter]** Diensttyp erstellen.

Der **[!UICONTROL Twitter account Synchronization]** Arbeitsablauf synchronisiert Twitter-Konten in Adobe Campaign. Weitere Informationen finden Sie unter [Synchronisieren von Facebook-Seiten](../../social/using/publishing-on-facebook-walls.md#synchronizing-facebook-pages).

## Synchronisieren von Twitter-Konten {#synchronizing-twitter-accounts}

>[!IMPORTANT]
>
>Damit der Workflow die Liste der Twitter-Abonnenten wiederherstellen kann, muss das **[!UICONTROL Twitter account synchronization]** Kontrollkästchen im Bearbeitungsbereich des mit dem Konto verknüpften Dienstes aktiviert werden. Weitere Informationen finden Sie unter [Delegieren von Schreibzugriff auf Adobe Campaign](#delegating-write-access-to-adobe-campaign).

Mit dem **[!UICONTROL Twitter account synchronization]** Workflow, auf den über den **[!UICONTROL Administration > Production > Technical workflows > Managing social networks]** Knoten zugegriffen wird, können Sie zuvor mit Adobe Campaign konfigurierte Twitter-Konten synchronisieren. Standardmäßig wird dieser Workflow jeden Donnerstag um 7:30 Uhr ausgelöst.

>[!NOTE]
>
>Der Workflow kann jederzeit durch Ausführung der erwarteten Aufgabenverarbeitung gestartet werden. Sie können den Zeitplan auch bearbeiten, um die Häufigkeit der Auslösung des Workflows zu ändern. For more on the scheduler, refer to [this section](../../workflow/using/scheduler.md).

Sie können nun Tweets an Ihre Twitter-Konten und Direktnachrichten an Ihre Follower senden. Weitere Informationen finden Sie unter: [Veröffentlichen auf Twitter](../../social/using/publishing-on-twitter.md).
