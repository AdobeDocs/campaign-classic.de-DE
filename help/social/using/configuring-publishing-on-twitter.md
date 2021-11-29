---
product: campaign
title: Konfigurieren der Veröffentlichung auf Twitter
description: Konfigurieren der Veröffentlichung auf Twitter
audience: social
content-type: reference
topic-tags: configuration
exl-id: 2d2a6e32-587d-4a7b-ba1c-d9140da53f64
source-git-commit: d11c918213e72fe4bf6adb464e516fac19b63d54
workflow-type: tm+mt
source-wordcount: '784'
ht-degree: 60%

---

# Konfigurationsschritte zur Veröffentlichung auf Twitter{#configuring-publishing-on-twitter}

![](../../assets/v7-only.svg)

Damit Adobe Campaign Tweets an Ihre Twitter-Konten senden kann, müssen Sie für diese Konten Schreibzugriff an Adobe Campaign delegieren. Gehen Sie hierzu wie folgt vor:

* Erstellen Sie ein Twitter-Konto.
* Erstellen Sie ein Twitter-Testkonto für den Testversand.
* Erstellen Sie eine Twitter-Anwendung pro Twitter-Konto.
* Erstellen Sie für jede Twitter-Anwendung einen neuen Dienst vom Typ **[!UICONTROL Twitter]**.

![](assets/social_diagram_twitter_service.png)

## Voraussetzungen {#prerequisites}

Erstellen Sie zunächst ein oder mehrere Twitter-Konten, an die Ihre Tweets gesendet werden sollen.

Um ein Twitter-Konto zu erstellen, navigieren Sie zu [https://twitter.com](https://twitter.com){target=&quot;_blank&quot;}.

## Testkonto in Twitter erstellen {#creating-a-test-account-on-twitter}

Erstellen Sie ein privates Twitter-Konto, das zum Senden verwendet werden kann. [Tweet-Testsendungen](../../social/using/publishing-on-twitter.md#sending-the-proof). Gehen Sie wie folgt vor, um ein privates Twitter-Konto zu erstellen:

1. Erstellen Sie ein neues Twitter-Konto.
1. Zugriff auf das Konto  **[!UICONTROL Einstellungen]**.
1. Navigieren Sie zu **[!UICONTROL Datenschutz und Sicherheit]** und **[!UICONTROL Zielgruppe und Tagging]** und überprüfen Sie die **[!UICONTROL Protect Ihre Tweets]** -Option. Ihre Tweets und andere Kontoinformationen sind nur für Personen sichtbar, die Ihnen folgen.

![](assets/social_twitter_test_page.png)

## Erstellen einer Anwendung in Twitter {#creating-an-application-on-twitter}

Damit Adobe Campaign Tweets an Ihre Twitter-Konten senden kann, müssen Sie pro Twitter-Konto eine Twitter-Anwendung erstellen. Gehen Sie hierzu wie folgt vor:

1. Melden Sie sich bei Ihrem Twitter-Konto an.
1. Geben Sie folgende Adresse in Ihren Browser ein: [https://developer.twitter.com/en/apps](https://developer.twitter.com/en/apps).
1. Klicken Sie anschließend auf **[!UICONTROL App erstellen]** rechts.

   ![](assets/social_create_twitter_app_001.png)

1. Der Assistent führt Sie durch den Prozess.

   Damit die Anwendung Adobe Campaign erlaubt, Tweets an Ihr Konto zu senden, rufen Sie den Tab **[!UICONTROL Berechtigungen]** der Anwendung auf und wählen Sie die Option **[!UICONTROL Lesen und Schreiben]** im Bereich **[!UICONTROL Zugriff]**. Auf dem Tab **[!UICONTROL Einstellungen]** müssen Sie außerdem das Feld **[!UICONTROL Callback-URL]** leer lassen.

   ![](assets/social_create_twitter_app_002.png)

## Schreibzugriff an Adobe Campaign delegieren {#delegating-write-access-to-adobe-campaign}

Für jede Twitter-Anwendung müssen Sie einen eigenen **[!UICONTROL Twitter]**-Dienst erstellen, der die Anwendungseinstellungen enthält.

Dieser Schritt erfordert gleichzeitigen Zugriff auf Ihre Adobe Campaign-Konsole und einen Internet-Browser, der bei Ihrem Twitter-Konto angemeldet ist:

* in **Twitter**: von [diese Seite](https://developer.twitter.com/en/portal/projects-and-apps), wählen Sie die zuvor erstellte App aus und bearbeiten Sie die **App-Berechtigungen**.

   ![](assets/social_twitter_service_002.png)

   Bearbeiten Sie die **Schlüssel und Token** Registerkarte , um auf Ihre App-Details zuzugreifen.

* in **Adobe Campaign**: gehen Sie zu **[!UICONTROL Profile und Zielgruppen]** klicken Sie auf die **[!UICONTROL Dienste und Abonnements]** und klicken Sie auf **[!UICONTROL Erstellen]** Schaltfläche.

   ![](assets/social_twitter_service_007.png)

1. Wählen Sie den Typ **[!UICONTROL Twitter]**.

   ![](assets/social_twitter_service_008.png)

   >[!NOTE]
   >
   >Die Option **[!UICONTROL Abonnements synchronisieren]** ist standardmäßig aktiviert. Wenn das Kästchen aktiviert ist, stellt der Workflow zur Synchronisierung von Twitter-Konten (siehe [Twitter-Konto-Synchronisation](#synchronizing-twitter-accounts)) die Liste der Twitter-Follower wieder her, sodass Sie ihnen Direktnachrichten senden können (siehe [Direktnachrichten an Abonnenten senden](../../social/using/publishing-on-twitter.md#sending-direct-messages-to-subscribers)). Wenn Sie die Liste der Follower nicht wiederherstellen möchten, deaktivieren Sie dieses Kästchen.

1. Geben Sie den Titel und den internen Namen des Dienstes ein.

   ![](assets/social_twitter_service_009.png)

   >[!IMPORTANT]
   >
   >Der **[!UICONTROL Interne Name]** des Dienstes muss mit dem Namen des Twitter-Kontos identisch sein. Gehen Sie wie folgt vor, um sicherzustellen, dass keine Eingabefehler auftreten.

   * Wählen Sie die Schaltfläche **[!UICONTROL Speichern]** aus.
   * Klicken Sie in der Übersicht der Dienste auf den soeben erstellten Twitter-Dienst.

   <!-- * Select the **[!UICONTROL Twitter page]** tab. The Twitter account should be displayed. 
    
      ![](assets/social_twitter_service_010.png)-->

1. Im **[!UICONTROL Besucherordner]** -Feld den Ordner auswählen, in dem die Follower erstellt werden sollen. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../social/using/publishing-on-twitter.md#operating-principle). Standardmäßig werden Follower im **[!UICONTROL Besucher]** Ordner.

   ![](assets/social_twitter_service_010_b.png)

1. Kopieren Sie in Twitter den Inhalt der **[!UICONTROL Consumer Key (API Key)]** und **[!UICONTROL Kundengeheimnis (API-Geheimnis)]** und fügen Sie sie in das **[!UICONTROL Consumer key]** und **[!UICONTROL Verbrauchergeheimnis]** Felder der Campaign-Clientkonsole.

   ![](assets/social_twitter_service_012.png)

1. Kopieren Sie in Twitter den Inhalt der **[!UICONTROL Zugriffstoken]** und **[!UICONTROL Geheimer Zugriffstoken]** und fügen Sie sie in das **[!UICONTROL Zugriffstoken]** und **[!UICONTROL Zugriffstoken-Geheimnis]** Felder der Campaign-Clientkonsole.

   ![](assets/social_twitter_service_013.png)

1. Klicken Sie in der Campaign-Clientkonsole auf **[!UICONTROL Speichern]**. Sie haben jetzt Schreibzugriff auf Adobe Campaign delegiert.

   ![](assets/social_twitter_service_014.png)

>[!NOTE]
>
>Sie müssen eine **[!UICONTROL Twitter]** Service pro Twitter-Anwendung.

Der Workflow für die **[!UICONTROL Twitter-Konto-Synchronisation]** sorgt für das Synchronisieren von Twitter-Konten in Adobe Campaign. Weitere Informationen hierzu finden Sie auf [dieser Seite](../../social/using/publishing-on-facebook-walls.md#synchronizing-facebook-pages).

## Twitter-Konten synchronisieren {#synchronizing-twitter-accounts}

>[!IMPORTANT]
>
>Damit der Workflow die Liste der Twitter-Abonnenten wiederherstellen kann, muss im Bearbeitungsbereich des mit dem Konto verknüpften Dienstes das Feld für die **[!UICONTROL Twitter-Konto-Synchronisation]** markiert sein. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](#delegating-write-access-to-adobe-campaign).

Mit dem Workflow für die **[!UICONTROL Twitter-Konto-Synchronisation]**, der über den Knoten **[!UICONTROL Administration > Betreibung > Technische Workflows > Social Marketing]** aufgerufen wird, können Sie zuvor mit Adobe Campaign konfigurierte Twitter-Konten synchronisieren. Standardmäßig wird dieser Workflow jeden Donnerstag um 7.30 Uhr ausgelöst.

>[!NOTE]
>
>Sie können den Workflow jederzeit starten, indem Sie die erwartete Aufgabenverarbeitung ausführen. Sie können auch die Planung bearbeiten, um die Häufigkeit der Auslösung des Workflows zu ändern. Weiterführende Informationen zur Planung finden Sie in [diesem Abschnitt](../../workflow/using/scheduler.md).

Sie können nun Tweets an Ihre Twitter-Konten und Direktnachrichten an Ihre Follower senden. Weitere Informationen hierzu finden Sie auf [dieser Seite](../../social/using/publishing-on-twitter.md).
