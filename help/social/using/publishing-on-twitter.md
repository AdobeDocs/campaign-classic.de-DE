---
title: Veröffentlichen auf Twitter
seo-title: Veröffentlichen auf Twitter
description: Veröffentlichen auf Twitter
seo-description: null
page-status-flag: never-activated
uuid: 405bce50-a63c-4bd3-8f03-c71809bb1cfd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: social
content-type: reference
topic-tags: publishing-on-facebook-twitter
discoiquuid: 2dc278ce-477c-493d-8abb-8bbdf2e988a5
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20174427735b90129cd4cbd9ee1ba5fd705fa302

---


# Veröffentlichen auf Twitter{#publishing-on-twitter}

## Veröffentlichen auf Ihren Twitter-Konten {#publishing-on-your-twitter-accounts}

Nach Abschluss der Konfiguration können Sie mit Social Marketing Tweets an Ihre Twitter-Konten senden.

### Einschränkungen {#limitations}

Die folgenden Einschränkungen sind Beschränkungen, die Twitter inhärent sind.

* Die Meldung darf nicht länger als 140 Zeichen sein.
* HTML-Format wird nicht unterstützt.

### Versand erstellen {#creating-the-delivery}

Erstellen Sie eine neue Bereitstellung basierend auf der **[!UICONTROL Tweet (twitter)]** Bereitstellungsvorlage.

![](assets/social_twitter_delivery_001.png)

### Hauptzielgruppe auswählen {#selecting-the-main-target}

Wählen Sie die Konten aus, an die Sie Tweets senden möchten.

1. Klicken Sie auf den **[!UICONTROL To]** Link.

   ![](assets/social_twitter_delivery_002.png)

1. Click the **[!UICONTROL Add]** button.

   ![](assets/social_twitter_delivery_006.png)

1. Auswählen **[!UICONTROL A Twitter account]**.

   ![](assets/social_twitter_delivery_007.png)

1. Wählen Sie im **[!UICONTROL Folder]** Feld den Dienstordner aus, der das Twitter-Konto enthält. Wählen Sie dann das Twitter-Konto aus, an das Sie Ihren Tweet senden möchten.

   ![](assets/social_twitter_delivery_011.png)

### Auswählen des Ziels des Nachweises {#selecting-the-target-of-the-proof}

Auf der **[!UICONTROL Target of the proofs]** Registerkarte können Sie das Twitter-Konto definieren, das für Testauslieferungen vor der endgültigen Auslieferung verwendet werden soll. Wir empfehlen Ihnen daher, ein privates Twitter-Konto zu erstellen, das dem Senden von Proofs gewidmet ist. Weitere Informationen zum Erstellen eines privaten Twitter-Kontos finden Sie unter [Erstellen eines Testkontos auf Twitter](../../social/using/configuring-publishing-on-twitter.md#creating-a-test-account-on-twitter). Die Schritte zur Auswahl des Proof-Ziels entsprechen der zur Auswahl des Hauptziels. Siehe [Erstellen eines Testkontos auf Twitter](../../social/using/configuring-publishing-on-twitter.md#creating-a-test-account-on-twitter).

![](assets/social_twitter_delivery_004.png)

>[!NOTE]
>
>Wenn Sie für alle Auslieferungen dasselbe Twitter-Testkonto verwenden, können Sie das Proof-Ziel in der **[!UICONTROL Tweet]** Bereitstellungsvorlage speichern, die über den **[!UICONTROL Resources > Templates > Delivery templates]** Knoten aufgerufen wird. Das Proof-Ziel wird dann standardmäßig für jede neue Auslieferung eingegeben.

### Definieren des Nachrichteninhalts {#defining-the-message-content}

Geben Sie den Inhalt Ihres Tweets auf der **[!UICONTROL Content]** Registerkarte ein.

![](assets/social_twitter_delivery_005.png)

### Anzeigen der Vorschau {#viewing-the-preview}

Auf der **[!UICONTROL Preview]** Registerkarte können Sie eine Darstellung des Tweets anzeigen.

1.  Klicken Sie auf die **[!UICONTROL Preview]** Registerkarte.
1. Klicken Sie auf das **[!UICONTROL Test personalization]** Dropdownmenü und wählen Sie **[!UICONTROL Service]**.
1. Wählen Sie im **[!UICONTROL Folder]** Feld den Dienstordner aus, der Ihr Twitter-Konto enthält.
1. Wählen Sie das Twitter-Konto aus, mit dem Sie die Vorschau testen möchten.

![](assets/social_twitter_delivery_008.png)

>[!NOTE]
>
>Die Vorschau unterscheidet sich möglicherweise geringfügig vom endgültigen Tweet. Es wird dringend empfohlen, vor der endgültigen Auslieferung einen Beweis zu senden, um eine genaue Wiedergabe des Tweets anzuzeigen. Siehe [Senden des Nachweises](#sending-the-proof).

### Tracking-Konfiguration {#configuring-tracking}

Die Verfolgung kann in den Bereitstellungsberichten und auf der **[!UICONTROL Edit > Tracking]** Registerkarte der Bereitstellung und des Dienstes angezeigt werden.

Die Verfolgungskonfiguration ist dieselbe wie bei einer E-Mail-Auslieferung. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../delivery/using/monitoring-a-delivery.md).

>[!NOTE]
>
>In der **[!UICONTROL Tweet]** Bereitstellungsvorlage ist die Verfolgung standardmäßig aktiviert.

>[!CAUTION]
>
>Wir können nicht unterscheiden zwischen Robotern, die Tweets analysieren, und Benutzern, die tatsächlich klicken.

### Senden des Nachweises {#sending-the-proof}

Wir empfehlen dringend, vor der endgültigen Auslieferung einen Nachweis Ihrer Veröffentlichung zu senden, um eine exakte Darstellung der Veröffentlichung auf einer privaten Twitter-Testseite zu erhalten. Weitere Informationen zum Erstellen eines privaten Twitter-Kontos finden Sie unter [Erstellen eines Testkontos auf Twitter](../../social/using/configuring-publishing-on-twitter.md#creating-a-test-account-on-twitter). Die Schritte zur Auswahl des Proof-Ziels werden unter [Auswählen des Ziels des Proof](#selecting-the-target-of-the-proof)beschrieben.

Der Zustellnachweis ist mit den E-Mail-Zustellungen identisch. Siehe [diesen Abschnitt](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

### Senden der Nachricht {#sending-the-message}

1. Nachdem der Inhalt genehmigt wurde, klicken Sie auf die **[!UICONTROL Send]** Schaltfläche.
1. Wählen Sie **[!UICONTROL Deliver as soon as possible]** und klicken Sie auf die **[!UICONTROL Analyze]** Schaltfläche.

   >[!NOTE]
   >
   >Mit dieser **[!UICONTROL Postpone the delivery]** Option können Sie die Lieferung auf ein späteres Datum verschieben.

   ![](assets/social_twitter_delivery_012.png)

1. Überprüfen Sie nach Abschluss der Analyse das Ergebnis.
1. Klicken Sie auf **[!UICONTROL Confirm delivery]** und dann auf **[!UICONTROL Yes]**.

![](assets/social_facebook_delivery_016.png)

## Senden von Direktnachrichten an Abonnenten {#sending-direct-messages-to-subscribers}

### Grundprinzip {#operating-principle}

Der **[!UICONTROL Synchronize Twitter accounts]** Arbeitsablauf (siehe [Synchronisieren von Twitter-Konten](../../social/using/configuring-publishing-on-twitter.md#synchronizing-twitter-accounts)) stellt die Liste der Twitter-Abonnenten wieder her, sodass Sie ihnen Direktnachrichten senden können. Die wiederhergestellten Follower werden in einer bestimmten Tabelle gespeichert: die Besuchstabelle. Um die Liste der Twitter-Follower anzuzeigen, gehen Sie zum **[!UICONTROL Profiles and Targets > Visitors]** Knoten.

![](assets/social_twitter_visitors_001.png)

>[!CAUTION]
>
>Damit der Workflow die Liste der Twitter-Follower wiederherstellen kann, muss das **[!UICONTROL Synchronize Twitter accounts]** Kontrollkästchen im Bearbeitungsbildschirm des mit dem Konto verknüpften Dienstes aktiviert sein. Weitere Informationen finden Sie unter: Schreibzugriff [an Adobe Campaign](../../social/using/configuring-publishing-on-twitter.md#delegating-write-access-to-adobe-campaign)delegieren

Für jeden Follower stellt Adobe Campaign die folgenden Informationen wieder her:

* **[!UICONTROL Origin]**: Name des sozialen Netzwerks (in diesem Fall **Twitter** )
* **[!UICONTROL External ID]**: user-ID
* **[!UICONTROL User name]**: Kontoname des Benutzers
* **[!UICONTROL Full name]**: Name des Benutzers
* **[!UICONTROL Language]**: Benutzersprache
* **[!UICONTROL Number of friends]**: Anzahl der Follower
* **[!UICONTROL Time zone]**: Zeitzone des Benutzers
* **[!UICONTROL Verified]**: Dieses Feld gibt an, ob der Benutzer über ein bestätigtes Twitter-Konto verfügt

### Einschränkungen {#limitations-1}

Die folgenden Einschränkungen sind Beschränkungen, die Twitter inhärent sind.

* Die Meldung darf nicht länger als 140 Zeichen sein.
* HTML wird nicht unterstützt.
* Sie können nicht mehr als 250 Direktnachrichten pro Tag senden. Um eine Überschreitung dieses Schwellenwerts zu vermeiden, können Sie mehrere Wellen bereitstellen. Auslieferungen in Wellen werden wie E-Mail-Auslieferungen konfiguriert. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves).

### Versand erstellen {#creating-the-delivery-}

Erstellen Sie eine neue Bereitstellung basierend auf der **[!UICONTROL Tweet (Direct Message)]** Bereitstellungsvorlage.

![](assets/social_twitter_delivery_010.png)

### Hauptzielgruppe auswählen {#selecting-the-main-target-1}

Wählen Sie die Follower aus, an die Sie Ihre Direktnachricht senden möchten.

1. Klicken Sie auf den **[!UICONTROL To]** Link.

   ![](assets/social_twitter_delivery_016.png)

1. Click the **[!UICONTROL Add]** button.

   ![](assets/social_twitter_delivery_006.png)

1. Wählen Sie einen Targeting-Typ aus.

   ![](assets/social_twitter_delivery_017.png)

   * Wählen Sie **[!UICONTROL Twitter subscribers]** aus, um eine Direktnachricht an alle Kontofolger zu senden.

      >[!CAUTION]
      >
      >Sie können nicht mehr als 250 Nachrichten pro Tag senden. Wenn Ihr Twitter-Konto mehr als 250 Follower hat, empfehlen wir dringend die Bereitstellung in Wellen. Dies umfasst den gleichen Prozess wie E-Mail-Auslieferungen. Siehe [diesen Abschnitt](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves).

   * Wählen Sie **[!UICONTROL Filter conditions]** zum Definieren einer Abfrage und zum Anzeigen des Ergebnisses. Diese Option ist dieselbe wie bei E-Mail-Auslieferungen. Weitere Informationen finden Sie in [diesem Abschnitt](../../platform/using/defining-filter-conditions.md).

      ![](assets/social_twitter_delivery_018.png)

### Auswählen des Ziels des Nachweises {#selecting-the-target-of-the-proof-1}

Auf der **[!UICONTROL Target of the proofs]** Registerkarte können Sie den Follower auswählen, der den Nachweis Ihrer Direktnachricht erhält. Der Auswahlprozess entspricht dem für das Hauptziel. Siehe [Auswählen des Hauptziels](#selecting-the-main-target).

![](assets/social_twitter_delivery_020.png)

>[!NOTE]
>
>Wenn Sie alle Ihre Direktnachrichten an denselben Twitter-Follower senden möchten, können Sie das Proof-Ziel in der **[!UICONTROL Tweet (Direct Message)]** Bereitstellungsvorlage speichern, die über den **[!UICONTROL Resources > Templates > Delivery templates]** Knoten aufgerufen wird. Das Proof-Ziel wird dann standardmäßig für jede neue Auslieferung eingegeben.

### Definieren des Nachrichteninhalts {#defining-message-content-}

Geben Sie den Inhalt des Tweets auf der **[!UICONTROL Content]** Registerkarte ein.

![](assets/social_twitter_delivery_015.png)

Personalisierungsfelder können auf dieselbe Weise wie für E-Mail-Auslieferungen verwendet werden, um beispielsweise den Namen des Followers im Nachrichtentext hinzuzufügen. Content personalization is detailed in [this section](../../delivery/using/about-personalization.md).

![](assets/social_twitter_delivery_021.png)

Die folgenden Schritte sind identisch mit dem Senden eines Tweets an ein Twitter-Konto. Siehe [Veröffentlichen in Ihren Twitter-Konten](#publishing-on-your-twitter-accounts).
