---
product: campaign
title: Erstellen eines LINE-Versands
description: Erfahren Sie, wie Sie LINE-Nachrichten erstellen
feature: Line App
exl-id: 1baaabbd-9fd7-4d9b-b78e-d2a559d7dddb
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '1320'
ht-degree: 100%

---

# Erstellen eines LINE-Versands{#line-channel}

![](../../assets/common.svg)

[!DNL LINE] ist eine Anwendung, die Instant Messaging sowie Sprach- und Videoanrufe kostenlos zur Verfügung stellt. Sie ist für alle Mobile-Betriebssysteme sowie für PCs verfügbar.

Ebenfalls möglich ist die Kombination von [!DNL LINE] mit dem Transaktionsnachrichten-Modul. Dadurch können Echtzeitnachrichten über die auf Endbenutzergeräten installierte [!DNL LINE]-Mobile-App versendet werden. Weiterführende Informationen hierzu finden Sie auf dieser [Seite](../../message-center/using/transactional-messaging-architecture.md#transactional-messaging-and-line).

![](assets/line_message.png)

Die Schritte zur Verwendung des [!DNL LINE]-Kanals lauten wie folgt:

1. [Einrichten des LINE-Kanals](#setting-up-line-channel)
1. [Erstellen eines Versands](#creating-the-delivery)
1. [Konfigurieren des Inhaltstyps](#defining-the-content)
1. [Monitoring des Versands (Tracking, Quarantänen, Berichte etc.)](#accessing-reports)

## Einrichten des LINE-Kanals {#setting-up-line-channel}

Bevor Sie ein [!DNL LINE]-Konto und ein externes Konto erstellen, müssen Sie zunächst das LINE-Package auf Ihrer Instanz installieren. Weiterführende Informationen dazu finden Sie in [diesem Abschnitt](../../installation/using/installing-campaign-standard-packages.md#line-package).

Zunächst müssen Sie ein [!DNL LINE]-Konto erstellen, das Sie anschließend mit Adobe Campaign verknüpfen. Dies ermöglicht es Ihnen schließlich, [!DNL LINE]-Nachrichten an Benutzer zu senden, die Ihr [!DNL LINE]-Konto ihrer Mobile App hinzugefügt haben. Externe Konten sowie das [!DNL LINE]-Konto können nur vom funktionalen Administrator der Plattform verwaltet werden.

Näheres dazu, wie Sie ein [!DNL LINE]-Konto erstellen und konfigurieren, finden Sie in der [LINE-Entwicklerdokumentation](https://developers.line.me/).

### Erstellen und Konfigurieren des LINE-Service {#configure-line-service}

So erstellen Sie einen [!DNL LINE]-Dienst:

1. Wählen Sie auf der Startseite von Adobe Campaign Classic den Tab **[!UICONTROL Profile und Zielgruppen]** aus.

1. Wählen Sie im Menü auf der linken Seite **[!UICONTROL Dienste und Abonnements]** und danach **[!UICONTROL Erstellen]** aus.

   ![](assets/line_service_1.png)

1. Geben Sie für Ihren neuen Dienst einen **[!UICONTROL Titel]** und einen **[!UICONTROL internen Namen]** an.

1. Wählen Sie **[!UICONTROL LINE]** aus der Dropdown-Liste **[!UICONTROL Typ]** aus.

   ![](assets/line_service_2.png)

1. Wählen Sie **[!UICONTROL Speichern]** aus.

Weiterführende Informationen zu Abonnements und Diensten finden Sie unter [Abonnements verwalten](managing-subscriptions.md).

### Konfigurieren des externen LINE-Kontos {#configure-line-external}

Nachdem Sie den Dienst [!DNL LINE] erstellt haben, müssen Sie das externe Konto von [!DNL LINE] in Adobe Campaign konfigurieren:

1. Gehen Sie im Navigationsbaum in das Menü **[!UICONTROL Administration]** > **[!UICONTROL Plattform]** > **[!UICONTROL Externe Konten]**.

1. Wählen Sie das native externe Konto **[!UICONTROL LINE V2-Routing]** aus.

   ![](assets/line_config.png)

1. Wählen Sie in Ihrem externen Konto den Tab **[!UICONTROL LINE]** aus, um mit der Konfiguration Ihres externen Kontos zu beginnen. Füllen Sie die folgenden Felder aus:

   ![](assets/line_config_2.png)

   * **[!UICONTROL Alias des Kanals]**: In Ihrem [!DNL LINE]-Konto finden Sie diesen unter **[!UICONTROL Channels]** > **[!UICONTROL Technical configuration]**.
   * **[!UICONTROL Kennung des Kanals]**: In Ihrem [!DNL LINE]-Konto finden Sie diese unter **[!UICONTROL Channels]** > **[!UICONTROL Basic Information panel]**.
   * **[!UICONTROL Geheimschlüssel des Kanals]**: In Ihrem [!DNL LINE]-Konto finden Sie diesen unter **[!UICONTROL Channels]** > **[!UICONTROL Basic Information panel]**.
   * **[!UICONTROL Zugriffs-Token]**: In Ihrem [!DNL LINE]-Konto finden Sie diesen im Entwicklerportal oder durch Auswahl der Schaltfläche **[!UICONTROL Zugriffs-Token abrufen]**.
   * **[!UICONTROL Ablaufdatum des Zugriffstokens]**: dient der Angabe des Zugriffstoken-Ablaufdatums.
   * **[!UICONTROL LINE-Abonnement-Dienst]**: dient der Angabe des Dienstes, für den die Nutzer angemeldet werden.

1. Wählen Sie nach Abschluss der Konfiguration **[!UICONTROL Speichern]**.

1. Navigieren Sie vom **[!UICONTROL Explorer]** aus zu **[!UICONTROL Administration]** > **[!UICONTROL Betreibung]** > **[!UICONTROL Technische Workflows]** > **[!UICONTROL LINE-Workflows]**, um zu prüfen, ob die Workflows **[!UICONTROL Aktualisierung des LINE-V2-Zugriffstokens (updateLineAccessToken)]** und **[!UICONTROL Bereinigung der gesperrten LINE-Benutzer (deleteBlockedLineUsers)]** gestartet wurden.

[!DNL LINE] ist jetzt in Adobe Campaign konfiguriert. Sie können mit der Erstellung und Durchführung von LINE-Sendungen an Abonnenten beginnen.

## Erstellen eines LINE-Versands {#creating-the-delivery}

>[!NOTE]
>
>Wenn Sie einen [!DNL LINE]-Versand erstmals an einen neuen Empfänger senden, müssen Sie die offizielle LINE-Nachricht mit den Nutzungsbedingungen und dem Einverständnis zum Erhalt des Versands hinzufügen. Sie finden den Text der offiziellen Nachricht unter [folgendem Link](https://terms.line.me/OA_privacy/).

Gehen Sie wie folgt vor, um einen [!DNL LINE]-Versand zu erstellen:

1. Verwenden Sie im Tab **[!UICONTROL Kampagnen]** **[!UICONTROL Sendungen]** und danach die Schaltfläche **[!UICONTROL Erstellen]**.

   ![](assets/line_message_07.png)

1. Wählen Sie die Versandvorlage **[!UICONTROL LINE V2-Versand]** aus.

   ![](assets/line_message_01.png)

1. Geben Sie für Ihren Versand einen **[!UICONTROL Titel]**, einen **[!UICONTROL Versand-Code]** und eine **[!UICONTROL Beschreibung]** ein. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](steps-create-and-identify-the-delivery.md#identifying-the-delivery).

1. Bestätigen Sie durch Verwendung der Schaltfläche **[!UICONTROL Fortfahren]** die Versanderstellung.

1. Wählen Sie im Versand-Editor **[!UICONTROL An]** aus, um die Empfänger Ihres [!DNL LINE]-Versands auszuwählen. Die Zielgruppenbestimmung erfolgt auf Basis von **[!UICONTROL Besucherabonnements (nms:visitorSub)]**.

   Weitere Informationen hierzu finden Sie unter [Zielpopulationen identifizieren](steps-defining-the-target-population.md).

   ![](assets/line_message_08.png)

1. Wählen Sie mit **[!UICONTROL Hinzufügen]** die **[!UICONTROL Zielgruppe des Versands]** aus.

   ![](assets/line_message_09.png)

1. Wählen Sie aus, ob [!DNL LINE]-Abonnenten direkt als Zielgruppe adressiert oder Benutzer abhängig von ihrem [!DNL LINE]-Abonnement adressiert werden sollen, und wählen Sie **[!UICONTROL Weiter]**. In diesem Beispiel haben wir **[!UICONTROL Nach LINE-V2-Abonnement]** ausgewählt.

1. Wählen Sie **[!UICONTROL Line-V2]** in der Dropdown-Liste **[!UICONTROL Ordner]** und dann Ihren [!DNL LINE]-Dienst aus. Wählen Sie **[!UICONTROL Beenden]** und anschließend **[!UICONTROL OK]**, um mit der Personalisierung Ihres Versands zu beginnen.

   ![](assets/line_message_10.png)

1. Wählen Sie im Versand-Editor **[!UICONTROL Hinzufügen]**, um eine oder mehrere Nachrichten hinzuzufügen und den **[!UICONTROL Inhaltstyp]** festzulegen.

   Weiterführende Informationen zu den verschiedenen verfügbaren **[!UICONTROL Inhaltstypen]** finden Sie unter [Festlegen des Inhaltstyps](#defining-the-content).

   ![](assets/line_message_11.png)

1. Nach Abschluss der Konfiguration Ihres Versands können Sie ihn an die zuvor bestimmte Zielgruppe senden.

   Weiterführende Informationen dazu, wie Sie einen Versand durchführen, finden Sie unter [Senden von Nachrichten](sending-messages.md).

1. Rufen Sie im Anschluss an den Versand Ihrer Nachricht den zugehörigen Bericht auf, um die Wirkung Ihres Versands zu messen.

   Weiterführende Informationen zu [!DNL LINE]-Berichten finden Sie unter [Zugriff auf Berichte](#accessing-reports).

## Festlegen des Inhaltstyps {#defining-the-content}

Um den Inhalt eines [!DNL LINE]-Versands festzulegen, müssen Sie Ihrem Versand zunächst einen Nachrichtentyp hinzufügen. Ein [!DNL LINE]-Versand kann bis zu fünf Nachrichten enthalten.

Es stehen drei Nachrichtentypen zur Auswahl:

* [Textnachrichten](#configuring-a-text-message-delivery)
* [Bild und Link](#configuring-an-image-and-link-delivery)
* [Video-Nachricht](#configuring-a-video-message-delivery)

### Konfigurieren eines Textnachrichten-Versands {#configuring-a-text-message-delivery}

>[!NOTE]
>
>Über die Syntax `<%@ include option='NmsServer_URL' %>/webApp/APP3?id=<%=escapeUrl(cryptString(visitor.id))%>` können Sie in einer LINE-Nachricht einen Link zu einer Web-Anwendung einfügen.

Bei einem [!DNL LINE]-Versand vom Typ **[!UICONTROL Textnachrichten]** handelt es sich um eine Nachricht, die in Textform an die Empfänger gesendet wird.

![](assets/line_message_02.png)

Die Konfiguration dieses Nachrichtentyps ist mit der Konfiguration von **[!UICONTROL Text]** in einer E-Mail vergleichbar. Weiterführende Informationen hierzu finden Sie auf [dieser Seite](defining-the-email-content.md#message-content).

### Konfiguration eines Bild-und-Link-Versands {#configuring-an-image-and-link-delivery}

Bei einem Versand vom Typ **[!UICONTROL Bild und Link]** handelt es sich um eine Nachricht in Form eines Bildes, das eine oder mehrere URLs enthalten kann.[!DNL LINE]

Dabei können folgende Elemente verwendet werden:

* **[!UICONTROL Personalisiertes Bild]**

   >[!NOTE]
   >
   >Über die Variable **%SIZE%** lässt sich die Anzeige entsprechend der Bildschirmgröße der Mobilgeräte der Nachrichtenempfänger optimieren.

   ![](assets/line_message_04.png)

* **[!UICONTROL Bild-URL]** nach Bildschirmgröße des Geräts

   ![](assets/line_message_03.png)

   Über die Option **[!UICONTROL Bilder nach Bildschirmgröße des Geräts definieren]** stehen verschiedene Bildauflösungen zur Verfügung, anhand derer Sie die Darstellung des Versands auf Mobilgeräten optimieren können. Es werden nur Bilder unterstützt, die die gleiche Höhe und Breite aufweisen.

   Bilder können entsprechend der Bildschirmgröße definiert werden:

   * 1040 px
   * 700 px
   * 460 px
   * 300 px
   * 240 px

   >[!CAUTION]
   >
   >Die Größe 1040 x 1040 Pixel ist für LINE-Bilder mit Links zwingend.

   Fügen Sie dann Alternativtext hinzu, der auf dem Mobilgerät des Empfängers angezeigt wird.

* **[!UICONTROL Links]**

   Im Bereich **[!UICONTROL Links]** können Sie verschiedene Layouts auswählen, entsprechend denen Ihr Bild in mehrere anklickbare Bereiche unterteilt wird. Anschließend können Sie jedem von ihnen eine spezifische **[!UICONTROL Link-URL]** zuweisen.

   ![](assets/line_message_05.png)

### Konfigurieren eines Videonachrichten-Versands {#configuring-a-video-message-delivery}

Beim [!DNL LINE]-Versand vom Typ **[!UICONTROL Video-Nachricht]** handelt es sich um eine Nachricht, die an Empfänger in Form eines Videos gesendet wird, das eine URL enthalten kann.

Im Feld **[!UICONTROL URL des Vorschaubilds]** können Sie die URL eines Vorschaubilds hinzufügen. Für diese besteht eine Zeichenbeschränkung von 1.000. Es werden die Formate JPEG und PNG unterstützt, wobei eine Beschränkung der Dateigröße von 1 MB besteht.

Im Feld **[!UICONTROL URL des Videobilds]** können Sie die URL Ihrer Videodatei hinzufügen. Für diese besteht eine Zeichenbeschränkung von 1.000. Es wird nur das MP4-Format unterstützt, wobei eine Beschränkung der Dateigröße von 200 MB besteht.

Beachten Sie, dass abhängig von der Breite und Höhe des Videos dessen Ränder bei der Wiedergabe auf einigen Geräten u. U. abgeschnitten sind.

![](assets/line_message_06.png)

## Zugriff auf Berichte {#accessing-reports}

Im Anschluss an den Versand können Sie Ihre [!DNL LINE]-Berichte über das Menü **[!UICONTROL Kampagnenverwaltung]** > **[!UICONTROL Sendungen]** im **[!UICONTROL Explorer]** aufrufen.

>[!NOTE]
>
>Die Tracking-Berichte liefern eine Auswertung der Klickrate. Die Öffnungsrate wird bei [!DNL LINE] nicht berücksichtigt.

![](assets/line_reports_01.png)

Rufen Sie für Berichte zum [!DNL LINE]-Dienst das Menü **[!UICONTROL Profile und Zielgruppen]** > **[!UICONTROL Dienste und Abonnements]** > **[!UICONTROL LINE V2]** im Tab **[!UICONTROL Explorer]** auf. Wählen Sie anschließend das Symbol **[!UICONTROL Berichte]** im [!DNL LINE]-Dienst aus.

![](assets/line_reports.png)

## Beispiel: Erstellung und Versand einer personalisierten LINE-Nachricht {#example--create-and-send-a-personalized-line-message}

In diesem Beispiel wird aufgezeigt, wie Sie eine Textnachricht und ein Bild, die je nach Empfänger personalisiert werden, erstellen und konfigurieren können.

1. Erstellen Sie Ihren [!DNL LINE]-Versand, indem Sie die Schaltfläche **[!UICONTROL Erstellen]** im Tab **[!UICONTROL Kampagnen]** auswählen.

   ![](assets/line_usecase.png)

1. Wählen Sie die LINE-Versandvorlage **[!UICONTROL LINE V2-Bereitstellung]** aus und benennen Sie Ihren Versand.

   ![](assets/line_usecase_01.png)

1. Wählen Sie im Konfigurationsfenster Ihres Versands Ihre Zielpopulation aus.

   Weiterführende Informationen hierzu finden Sie unter [Zielpopulationen identifizieren](steps-defining-the-target-population.md).

   ![](assets/line_usecase_02.png)

1. Wählen Sie **[!UICONTROL Hinzufügen]** aus, um Ihre Nachricht zu erstellen, und wählen Sie danach den **[!UICONTROL Inhaltstyp]** aus.

   Hier möchten wir zunächst eine **[!UICONTROL Textnachricht]** erstellen.

   ![](assets/line_usecase_03.png)

1. Platzieren Sie den Cursor an der Position, an der der personalisierte Text eingefügt werden soll, wählen Sie das Symbol für die Dropdown-Liste und danach **[!UICONTROL Besucher]** > **[!UICONTROL Vorname]** aus.

   ![](assets/line_usecase_05.png)

1. Gehen Sie ebenso vor, um ein Bild hinzuzufügen, indem Sie **[!UICONTROL Bild und Link]** in der Dropdown-Liste **[!UICONTROL Nachrichtentyp]** auswählen.

   Fügen Sie Ihre **[!UICONTROL Bild-URL]** hinzu.

   ![](assets/line_usecase_07.png)

1. Wählen Sie im Bereich **[!UICONTROL Links]** das Layout aus, gemäß dem Ihr Bild in mehrere anklickbare Bereiche unterteilt wird.

1. Weisen Sie jedem Bereich des Bildes eine URL zu.

   ![](assets/line_usecase_08.png)

1. Speichern Sie Ihren Versand und verwenden Sie die Schaltfläche **[!UICONTROL Senden]**, um den Versand zu analysieren und ihn anschließend an die Zielgruppe zu senden.

   Der Versand wird an die Zielgruppe gesendet:

   ![](assets/line_usecase_06.png)

