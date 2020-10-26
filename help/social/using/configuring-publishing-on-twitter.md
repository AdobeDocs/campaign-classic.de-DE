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
translation-type: ht
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: ht
source-wordcount: '798'
ht-degree: 100%

---


# Konfigurieren der Veröffentlichung auf Twitter{#configuring-publishing-on-twitter}

Damit Adobe Campaign Tweets an Ihre Twitter-Konten senden kann, müssen Sie für diese Konten Schreibzugriff an Adobe Campaign delegieren. Gehen Sie hierzu wie folgt vor:

* Erstellen Sie ein Twitter-Konto.
* Erstellen Sie ein Twitter-Testkonto für den Testversand.
* Erstellen Sie eine Twitter-Anwendung pro Twitter-Konto.
* Erstellen Sie für jede Twitter-Anwendung einen neuen Dienst vom Typ **[!UICONTROL Twitter]**.

![](assets/social_diagram_twitter_service.png)

## Voraussetzungen {#prerequisites}

Erstellen Sie zunächst ein oder mehrere Twitter-Konten, an die Ihre Tweets gesendet werden sollen.

Um ein Twitter-Konto zu erstellen, navigieren Sie zu [https://twitter.com ](https://twitter.com).

## Testkonto in Twitter erstellen {#creating-a-test-account-on-twitter}

Es wird außerdem empfohlen, ein privates Twitter-Konto zu erstellen, das für den Tweet-Testversand verwendet werden kann (weitere Informationen hierzu finden Sie unter [Testversand](../../social/using/publishing-on-twitter.md#sending-the-proof)):

* Erstellen Sie ein neues Twitter-Konto.
* Klicken Sie auf das Menü in der oberen rechten Ecke und wählen Sie **[!UICONTROL Einstellungen]**.
* Wählen Sie den Tab **[!UICONTROL Sicherheit und Datenschutz]** und aktivieren Sie das Kästchen **[!UICONTROL Meine Tweets schützen]**.
* Klicken Sie unten auf der Seite auf die Schaltfläche **[!UICONTROL Änderungen speichern]**.

![](assets/social_twitter_test_page.png)

## Anwendung auf Twitter erstellen {#creating-an-application-on-twitter}

Damit Adobe Campaign Tweets an Ihre Twitter-Konten senden kann, müssen Sie pro Twitter-Konto eine Twitter-Anwendung erstellen. Gehen Sie hierzu wie folgt vor:

1. Melden Sie sich bei Ihrem Twitter-Konto an.
1. Geben Sie folgende Adresse in Ihren Browser ein: [https://apps.twitter.com/](https://apps.twitter.com/).
1. Klicken Sie dann auf der rechten Seite auf die Schaltfläche **[!UICONTROL Neue App erstellen]**.

   ![](assets/social_create_twitter_app_001.png)

1. Der Assistent führt Sie durch den Prozess.

   Damit die Anwendung Adobe Campaign erlaubt, Tweets an Ihr Konto zu senden, rufen Sie den Tab **[!UICONTROL Berechtigungen]** der Anwendung auf und wählen Sie die Option **[!UICONTROL Lesen und Schreiben]** im Bereich **[!UICONTROL Zugriff]**. Auf dem Tab **[!UICONTROL Einstellungen]** müssen Sie außerdem das Feld **[!UICONTROL Callback-URL]** leer lassen.

   ![](assets/social_create_twitter_app_002.png)

## Schreibzugriff an Adobe Campaign delegieren {#delegating-write-access-to-adobe-campaign}

Für jede Twitter-Anwendung müssen Sie einen eigenen **[!UICONTROL Twitter]**-Dienst erstellen, der die Anwendungseinstellungen enthält.

Dieser Schritt erfordert gleichzeitigen Zugriff auf Ihre Adobe Campaign-Konsole und einen Internet-Browser, der bei Ihrem Twitter-Konto angemeldet ist:

* **Twitter**: Wählen Sie die zuvor erstellte Anwendung aus ([https://dev.twitter.com/apps](https://dev.twitter.com/apps)) und klicken Sie auf den Tab **[!UICONTROL Schlüssel und Zugriffstoken]**.

   ![](assets/social_twitter_service_002.png)

* **Adobe Campaign**: Wechseln Sie zur Rubrik **[!UICONTROL Profile und Zielgruppen]**, klicken Sie auf den Link **[!UICONTROL Dienste und Abonnements]** und klicken Sie auf die Schaltfläche **[!UICONTROL Erstellen]**.

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
   * Wählen Sie den Tab **[!UICONTROL Twitter-Seite]**. Das Twitter-Konto sollte angezeigt werden.

      ![](assets/social_twitter_service_010.png)

1. Wählen Sie im Feld **[!UICONTROL Besucherordner]** den Besucherordner aus, in dem die Follower erstellt werden sollen. Weitere Informationen hierzu finden Sie im Abschnitt [Grundprinzip](../../social/using/publishing-on-twitter.md#operating-principle). Standardmäßig werden Follower im Stammordner des Ordners **[!UICONTROL Besucher]** erstellt.

   ![](assets/social_twitter_service_010_b.png)

1. Kopieren Sie auf Twitter den Inhalt der Felder **[!UICONTROL Consumer Key (API Key)]** und **[!UICONTROL Consumer Secret (API Secret)]** und fügen Sie ihn in die Felder **[!UICONTROL Consumer Key]** und **[!UICONTROL Consumer Secret]** der Konsole ein.

   ![](assets/social_twitter_service_012.png)

1. Kopieren Sie auf Twitter den Inhalt der Felder **[!UICONTROL Zugriffstoken]** und **[!UICONTROL Zugriffstoken-Geheimnis]** und fügen Sie ihn in die Felder **[!UICONTROL Zugriffstoken]** und **[!UICONTROL Zugriffstoken-Geheimnis]** der Konsole ein.

   ![](assets/social_twitter_service_013.png)

1. Klicken Sie in der Adobe Campaign-Konsole auf **[!UICONTROL Speichern]**. Die Delegierung des Schreibzugriffs an Adobe Campaign ist nun abgeschlossen.

   ![](assets/social_twitter_service_014.png)

>[!NOTE]
>
>Sie müssen einen **[!UICONTROL Twitter]**-Dienst pro Twitter-Anwendung erstellen.

Der Workflow für die **[!UICONTROL Twitter-Konto-Synchronisation]** sorgt für das Synchronisieren von Twitter-Konten in Adobe Campaign. Weitere Informationen hierzu finden Sie unter [Facebook-Seiten-Synchronisation](../../social/using/publishing-on-facebook-walls.md#synchronizing-facebook-pages).

## Twitter-Konto-Synchronisation {#synchronizing-twitter-accounts}

>[!IMPORTANT]
>
>Damit der Workflow die Liste der Twitter-Abonnenten wiederherstellen kann, muss im Bearbeitungsbereich des mit dem Konto verknüpften Dienstes das Feld für die **[!UICONTROL Twitter-Konto-Synchronisation]** markiert sein. Weitere Informationen hierzu finden Sie unter [Delegieren von Schreibzugriff an Adobe Campaign](#delegating-write-access-to-adobe-campaign).

Mit dem Workflow für die **[!UICONTROL Twitter-Konto-Synchronisation]**, der über den Knoten **[!UICONTROL Administration > Betreibung > Technische Workflows > Social Marketing]** aufgerufen wird, können Sie zuvor mit Adobe Campaign konfigurierte Twitter-Konten synchronisieren. Standardmäßig wird dieser Workflow jeden Donnerstag um 7.30 Uhr ausgelöst.

>[!NOTE]
>
>Der Workflow kann jederzeit durch Ausführung der erwarteten Aufgabenverarbeitung gestartet werden. Sie können auch die Planung bearbeiten, um die Häufigkeit der Auslösung des Workflows zu ändern. Weiterführende Informationen zur Planung finden Sie in [diesem Abschnitt](../../workflow/using/scheduler.md).

Sie können nun Tweets an Ihre Twitter-Konten und Direktnachrichten an Ihre Follower senden. Weiterführende Informationen finden Sie unter [Veröffentlichen auf Twitter](../../social/using/publishing-on-twitter.md).
