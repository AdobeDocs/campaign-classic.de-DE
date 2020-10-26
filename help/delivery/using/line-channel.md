---
title: LINE-Kanal
seo-title: LINE-Kanal
description: LINE-Kanal
seo-description: null
page-status-flag: never-activated
uuid: 94b4e044-3f5d-42a6-b249-29f417386156
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-messages-on-mobiles
discoiquuid: 1d3cc650-3c79-4a1d-b2bc-e7eb6d59d2f1
translation-type: ht
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: ht
source-wordcount: '1164'
ht-degree: 100%

---


# LINE-Kanal{#line-channel}

LINE ist ein kostenfreier Dienst für Instant Messaging, VoIP und Video, der auf Smartphones (iPhone, Android, Windows Phone, BlackBerry, Nokia) und auf PC genutzt werden kann. Adobe Campaign ermöglicht Ihnen den Versand von LINE-Nachrichten.

LINE ist nur für On-Premise-Installationen oder Managed Services verfügbar.

LINE kann auch mit dem Transaktionsnachrichten-Modul kombiniert werden, sodass Echtzeitnachrichten über die auf den Mobilgeräten der Konsumenten installierten LINE-App gesendet werden können. Weiterführende Informationen dazu finden Sie auf dieser [Seite](../../message-center/using/transactional-messaging-architecture.md#transactional-messaging-and-line).

![](assets/line_message.png)

Die folgenden Abschnitte enthalten Informationen, die speziell für den LINE-Kanal gelten. Allgemeine Informationen zum Erstellen einer Sendung finden Sie in [diesem Abschnitt](../../delivery/using/steps-about-delivery-creation-steps.md).

Wie bei anderen Kanälen haben Sie bei Verwendung des LINE-Kanals folgende Möglichkeiten:

1. Versanderstellung
1. Konfiguration des Nachrichteninhalts
1. Zielgruppe bestimmen
1. Nachrichtenversand
1. Versandverfolgung (Tracking, Quarantänen, Berichte etc.).

## LINE-Kanal einrichten {#setting-up-line-channel}

### Erstellung eines LINE-Kontos und eines externen Kontos {#creating-a-line-account-and-an-external-account-}

>[!NOTE]
>
>Vor der Erstellung eines LINE-Kontos und eines externen Kontos müssen Sie das LINE-Package auf Ihrer Instanz installieren. Weiterführende Informationen dazu finden Sie im Installationshandbuch im Abschnitt [LINE](../../installation/using/installing-campaign-standard-packages.md#line-package).

Sie müssen zunächst ein LINE-Konto erstellen und dieses mit Adobe Campaign verknüpfen, damit Sie LINE-Nachrichten an diejenigen Benutzer senden können, die Ihr LINE-Konto in ihrer Mobile App hinzugefügt haben. Externe Konten und das LINE-Konto können nur vom funktionalen Administrator der Plattform verwaltet werden.

Weiterführende Informationen zur Erstellung und Konfiguration eines LINE-Kontos finden Sie unter folgendem Link [https://developers.line.me/](https://developers.line.me/).

Weitere Informationen zur Erstellung und Konfiguration eines LINE-Dienstes finden Sie im Abschnitt [Abonnements verwalten](../../delivery/using/managing-subscriptions.md).

![](assets/line_service.png)

Gehen Sie wie folgt vor, um ein externes Konto zu erstellen:

1. Gehen Sie im Navigationsbaum in das Menü **Administration** > **Plattform** > **Externe Konten**.
1. Erstellen Sie ein neues Konto mithilfe der Schaltfläche **Neu**.

   ![](assets/line_config.png)

1. Füllen Sie die Felder **Titel** und **Interner Name** aus.
1. Wählen Sie im Feld **[!UICONTROL Typ]** die Option &quot;Routing&quot; und im Feld **Kanal** die Option &quot;LINE&quot;.
1. Wählen Sie **[!UICONTROL Speichern]** aus, um ein externes LINE-Konto zu erstellen.
1. Ein **LINE**-Personalisierungsfeld wird daraufhin unter dem Symbol **Allgemein** angezeigt. Füllen Sie die folgenden Felder aus:

   ![](assets/line_config_2.png)

   * **Alias des Kanals**: Entnehmen Sie diese Information dem Tab **[!UICONTROL Channels]** > **[!UICONTROL Technical configuration]** Ihres LINE-Kontos.
   * **Kennung des Kanals**: Entnehmen Sie die Kennung dem Tab **Channels** > **Basic Information panel** Ihres LINE-Kontos.
   * **Geheimschlüssel des Kanals**: Entnehmen Sie den Geheimschlüssel dem Tab **Channels** > **Basic Information panel** Ihres LINE-Kontos.
   * **Zugriffstoken**: wird über Ihr LINE-Konto im Entwicklerportal oder durch Klicken auf die Schaltfläche **[!UICONTROL Zugriffstoken abrufen]** bereitgestellt.
   * **Ablaufdatum des Zugriffstokens**: dient der Angabe des Zugriffstoken-Ablaufdatums.
   * **LINE-Abonnement-Dienst**: dient der Angabe des Dienstes, für den die Nutzer angemeldet werden.

>[!NOTE]
>
>Es ist zu überprüfen, dass die Workflows **[!UICONTROL Aktualisierung des LINE-Zugriffstokens (updateLineAccessToken)]** und **[!UICONTROL Bereinigung der gesperrten LINE-Benutzer (deleteBlockedLineUsers)]** gestartet sind. Verwenden Sie hierfür ausgehend vom Explorer das Menü **[!UICONTROL Administration > Betreibung > Technische Workflows > LINE-Workflows]**, um den Status der Workflows zu überprüfen.

## Versand erstellen {#creating-the-delivery}

Gehen Sie wie folgt vor, um einen **LINE**-Versand zu erstellen:

>[!NOTE]
>
>Allgemeine Methoden zur Versanderstellung finden Sie in [diesem Abschnitt](../../delivery/using/steps-about-delivery-creation-steps.md).

1. Verwenden Sie im Tab **[!UICONTROL Kampagnen]** **[!UICONTROL Sendungen]** und danach die Schaltfläche **[!UICONTROL Erstellen]**.
1. Wählen Sie im sich öffnenden Fenster die Versandvorlage **[!UICONTROL LINE V2-Bereitstellung]**.

   ![](assets/line_message_01.png)

1. Geben Sie für Ihren Versand einen Titel, einen Code und eine Beschreibung ein. Weiterführende Informationen dazu finden Sie in [diesem Abschnitt](../../delivery/using/steps-create-and-identify-the-delivery.md#identifying-the-delivery).
1. Bestätigen Sie durch Verwendung der Schaltfläche **[!UICONTROL Fortfahren]** die Versanderstellung.

## Nachrichteninhalt konfigurieren {#defining-the-content}

Um den Inhalt eines LINE-Versands zu definieren, fügen Sie zu Ihrem Versand zunächst einen Nachrichtentyp hinzu. Jeder LINE-Versand kann maximal fünf Nachrichten enthalten.

Sie können aus zwei Nachrichtentypen auswählen:

* Textnachrichten
* Bild und Link

### Konfiguration eines Textnachrichten-Versands {#configuring-a-text-message-delivery}

Bei einem LINE-Versand vom Typ **Textnachrichten** handelt es sich um eine Nachricht, die in Textform an Empfänger gesendet wird.

![](assets/line_message_02.png)

Die Konfiguration dieses Nachrichtentyps ähnelt der Konfiguration des **Text**-Formats in einer E-Mail. Lesen Sie für weiterführende Informationen diese [Seite](../../delivery/using/defining-the-email-content.md#message-content).

### Konfiguration eines Bild-und-Link-Versands {#configuring-an-image-and-link-delivery}

Bei einem LINE-Versand vom Typ **Bild und Link** handelt es sich um eine Nachricht in Form eines Bildes, das eine oder mehrere URLs enthalten kann.

Dabei können folgende Elemente verwendet werden:

* **Personalisiertes Bild**

   >[!NOTE]
   >
   >Sie können die Variable **%SIZE%** verwenden: Mithilfe dieser Variable lässt sich die Anzeige je nach Bildschirmgröße der Mobilgeräte von Nachrichtenempfängern optimieren.

   ![](assets/line_message_04.png)

* **Bild-URL**

   ![](assets/line_message_03.png)

   Bild-URLs dienen der Verwendung von Bildern mit unterschiedlicher Auflösung, um die Sichtbarkeit der Sendung auf unterschiedlichen Mobilgeräten zu optimieren. Nur Bilder mit derselben Breite und Höhe werden unterstützt:

   Bilder können entsprechend der Bildschirmgröße definiert werden:

   * 1040 px
   * 700 px
   * 460 px
   * 300 px
   * 240 px

   >[!NOTE]
   >
   >Die Größe 1040 x 1040 Pixel ist für LINE-Bilder mit Links zwingend.

   Fügen Sie dann Alternativtext hinzu, der auf dem Mobilgerät des Empfängers angezeigt wird.

* **[!UICONTROL Links]**

   ![](assets/line_message_05.png)

   Im Bereich **[!UICONTROL Links]** können Sie aus unterschiedlichen Layouts wählen, durch die Ihr Bild in mehrere anklickbare Bereiche unterteilt wird. Sie können dann zu jedem Bereich einen eigenen Link hinzufügen.

>[!NOTE]
>
>Die Syntax &lt;%@ include option=&#39;NmsServer_URL&#39; %>/webApp/APP3?id=&lt;%=escapeUrl(cryptString(visitor.id))%> ermöglicht es, einen WebApp-Link in eine LINE-Nachricht einzuschließen.

### Empfehlungen   {#recommendations}

* Wenn Sie einen LINE-Versand erstmals an einen neuen Empfänger senden, sind Sie verpflichtet, die offizielle LINE-Mitteilung hinzuzufügen, in der die Nutzungsbedingungen sowie die Einverständniserklärung enthalten sind. Der offizielle Text ist unter folgendem Link verfügbar: [https://terms.line.me/OA_privacy/](https://terms.line.me/OA_privacy/sp?lang=fr).

## Zielgruppe bestimmen {#selecting-the-target-population}

Die Auswahl der Empfänger eines LINE-Versands ist mit der Definition der Empfänger eines E-Mail-Versands vergleichbar. Weitere Informationen hierzu finden Sie unter [Zielpopulationen identifizieren](../../delivery/using/steps-defining-the-target-population.md).

Die Zielgruppenbestimmung ist auf **Besucher** ausgerichtet.

## Nachrichten senden {#sending-messages}

Nach Abschluss der Konfiguration Ihres Versands können Sie ihn an die zuvor bestimmte Zielgruppe senden.

Das Senden eines LINE-Versands ist mit dem Senden eines E-Mail-Versands vergleichbar. Weitere Informationen zum Senden finden Sie unter [Nachrichten senden](../../delivery/using/sending-messages.md).

## Zugriff auf Berichte {#accessing-reports}

Der Zugriff auf LINE-Dienst-Berichte ist im Explorer über das Menü **[!UICONTROL Profile und Zielgruppen > Dienste und Abonnements > LINE]** möglich. Klicken Sie dann im gewünschten Dienst auf das **[!UICONTROL Berichte]**-Symbol.

![](assets/line_reports.png)

Der Zugriff auf LINE-Sendungen betreffende Berichte ist im Explorer über das Menü **[!UICONTROL Kampagnenverwaltung > Sendungen]** möglich. Wählen Sie den gewünschten Versand aus. Beachten Sie, dass in den Trackingberichten Klickraten angezeigt werden. LINE berücksichtigt keine Öffnungsraten.

![](assets/line_reports_01.png)

## Beispiel: Erstellung und Versand einer personalisierten LINE-Nachricht {#example--create-and-send-a-personalized-line-message}

In diesem Beispiel wird aufgezeigt, wie Sie eine Textnachricht und ein Bild, die je nach Empfänger personalisiert werden, erstellen und konfigurieren können.

1. Erstellen Sie unter Verwendung der Schaltfläche **[!UICONTROL Erstellen]** im Menü **[!UICONTROL Kampagnen]** einen neuen Versand.

   ![](assets/line_usecase.png)

1. Wählen Sie die LINE-Versandvorlage **[!UICONTROL LINE V2-Bereitstellung]** aus und benennen Sie Ihren Versand.

   ![](assets/line_usecase_01.png)

1. Wählen Sie im Konfigurationsfenster Ihres Versands Ihre Zielpopulation aus.

   ![](assets/line_usecase_02.png)

1. Wählen Sie **[!UICONTROL Hinzufügen]** aus, um Ihre Nachricht zu erstellen, und wählen Sie danach **[!UICONTROL Nachrichtentyp]** aus.

   Hier möchten wir zunächst eine Textnachricht erstellen.

   ![](assets/line_usecase_03.png)

1. Platzieren Sie den Cursor an der Stelle, an der der personalisierte Text eingefügt werden soll, und wählen Sie das Symbol der Dropdown-Liste und danach **[!UICONTROL Besucher > Vorname]** aus.

   ![](assets/line_usecase_05.png)

1. Gehen Sie ebenso vor, um ein Bild hinzuzufügen, indem Sie **[!UICONTROL Bild und Link]** in der Dropdown-Liste **[!UICONTROL Nachrichtentyp]** auswählen.

   Fügen Sie Ihre Bild-URL hinzu.

   ![](assets/line_usecase_07.png)

1. Wählen Sie im Bereich **[!UICONTROL Links]** das Layout aus, gemäß dem Ihr Bild in mehrere anklickbare Bereiche unterteilt wird.
1. Weisen Sie jedem Bereich des Bildes eine URL zu.

   ![](assets/line_usecase_08.png)

1. Speichern Sie Ihren Versand und verwenden Sie die Schaltfläche **[!UICONTROL Senden]**, um den Versand zu analysieren und ihn anschließend an die Zielgruppe zu senden.

   Der Versand wird an die Zielgruppe gesendet:

   ![](assets/line_usecase_06.png)
