---
product: campaign
title: Veröffentlichen auf Facebook
description: Hier erfahren Sie, wie Sie auf Facebook Veröffentlichungen vornehmen können
audience: social
content-type: reference
topic-tags: publishing-on-facebook-twitter
exl-id: 84d6cb2e-c7f9-43d7-a98c-22613d456193
source-git-commit: b5334de18eca8fc1147ae0c42fe23a6932bf71d2
workflow-type: tm+mt
source-wordcount: '1243'
ht-degree: 100%

---

# Veröffentlichen auf Facebook{#publishing-on-facebook}

![](../../assets/v7-only.svg)

Nach Abschluss der Konfiguration können Sie mit Social-Media-Marketing Inhalte auf Ihren Facebook-Seiten veröffentlichen.

## Einschränkungen {#limitations}

Die folgenden Einschränkungen gelten für Facebook.

* Nachrichten dürfen nicht länger als 1.000 Zeichen sein.
* HTML wird nicht unterstützt.

## Erstellen des Versands {#creating-the-delivery}

Erstellen Sie mit der Versandvorlage **[!UICONTROL Auf einer Markenseite veröffentlichen]** einen neuen Versand.

![](assets/social_facebook_delivery_001.png)

## Auswählen der Hauptzielgruppe       {#selecting-the-main-target}

Wählen Sie die Seiten aus, auf denen Sie Ihre Veröffentlichung posten möchten.

1. Wählen Sie den Link **[!UICONTROL An]** aus.

   ![](assets/social_facebook_delivery_010.png)

1. Klicken Sie auf die Schaltfläche **[!UICONTROL Hinzufügen]**.

   ![](assets/social_facebook_delivery_011.png)

1. Wählen Sie **[!UICONTROL Facebook-Seite]** aus.

   ![](assets/social_facebook_delivery_012.png)

1. Wählen Sie im Feld **[!UICONTROL Ordner]** den Dienstordner aus, der die Facebook-Seite enthält. Standardmäßig werden Seiten im Stammordner des **[!UICONTROL Facebook]**-Dienstordners gespeichert. Wählen Sie dann die Facebook-Seite aus, auf der Sie posten möchten.

   ![](assets/social_facebook_delivery_013.png)

## Auswählen der Zielgruppe für den Testversand {#selecting-the-proof-target}

Über den Tab **[!UICONTROL Testversand-Zielgruppe]** können Sie die Facebook-Seite festlegen, die Sie zum Testen der Sendungen verwenden möchten, bevor Sie diese abschicken. Es wird empfohlen, hierfür eine eigene private Facebook-Seite zu erstellen. Weitere Informationen zum Erstellen einer privaten Facebook-Seite finden Sie auf [dieser Seite](../../social/using/publishing-on-facebook-walls.md#creating-a-test-facebook-page). Gehen Sie zur Auswahl der Zielgruppe für den Testversand genauso vor wie zur Auswahl der Hauptzielgruppe. [Weitere Informationen](#selecting-the-main-target)

![](assets/social_facebook_delivery_004.png)

>[!NOTE]
>
>Wenn Sie dieselbe Facebook-Testseite für alle Sendungen verwenden, können Sie die Testversand-Zielgruppe in der Versandvorlage **[!UICONTROL Auf einer Markenseite veröffentlichen]** speichern, auf die über den Knoten **[!UICONTROL Ressourcen > Vorlagen > Versandvorlagen]** zugegriffen werden kann. Die Testversand-Zielgruppe wird dann standardmäßig bei jedem neuen Versand eingegeben.

## Definieren der Audience {#defining-the-audience}

Wenn Sie lokale Segmente verwenden möchten, um zu verfeinern, welcher Teil der Öffentlichkeit die Veröffentlichung anzeigen darf, empfehlen wir, eine Facebook-Seite pro Segment zu erstellen (z. B.: Adobe Campaign Paris, Adobe Campaign London usw.).

Es ist jedoch auch möglich, die von Facebook verwendeten Zielgruppenfilter zu verwenden. Der Tab **[!UICONTROL Zielgruppe]** des Fensters **[!UICONTROL Auswahl der Zielgruppe]** enthält vier Filter:

* **[!UICONTROL Country]**
* **[!UICONTROL Regionen]**
* **[!UICONTROL Städte]**
* **[!UICONTROL Sprachen]**

>[!CAUTION]
>
>Verwenden Sie diese Funktion mit Vorsicht. In Versandberichten berücksichtigt die **[!UICONTROL Anz. Fans]** diese Facebook-Filter nicht.
>
>Facebook kann die Liste der Zielgruppenfilter sowie deren Werte ändern.

## Definieren des Nachrichteninhalts {#defining-message-content}

Wählen Sie den Veröffentlichungstyp über das Dropdown-Menü **[!UICONTROL Inhaltstyp]** aus.

![](assets/social_facebook_delivery_006.png)

Folgende Versandtypen sind möglich:

* **[!UICONTROL Status]**
* **[!UICONTROL Status mit Link]**
* **[!UICONTROL Status mit YouTube-Link]**
* **[!UICONTROL Fotoalbum]**

### Veröffentlichen eines Status {#publishing-a-status}

Ein Versand vom Typ „Status“ kann nur Text enthalten, wie im folgenden Beispiel:

![](assets/social_create_facebook_wall_post_004.png)

Geben Sie den Veröffentlichungsstatus in das Eingabefeld ein.

![](assets/social_facebook_delivery_015.png)

### Veröffentlichen eines Status mit einem Link {#publishing-a-status-with-a-link}

Ein Versand vom Typ „Status mit Link“ kann Text, Bilder und einen Link enthalten. Im folgenden Abschnitt wird die Symmetrie zwischen den Feldern des Bearbeitungsbildschirms des Versands und der endgültigen Veröffentlichung auf Facebook erläutert:

![](assets/social_facebook_delivery_007.png)

Geben Sie die verschiedenen Felder ein:

>[!CAUTION]
>
>Alle URLs müssen mit **„http://“** oder **„https://“** beginnen.

1. Geben Sie im Feld **[!UICONTROL Status]** den Text ein, der unter dem Namen der Seite angezeigt werden soll.
1. Geben Sie im Feld **[!UICONTROL Name]** den Titel der Veröffentlichung ein.
1. Geben Sie im Feld **[!UICONTROL Link]** die URL ein, auf die die Veröffentlichung verweist.

   >[!NOTE]
   >
   >Wenn Sie das Feld **[!UICONTROL Link]** zur URL einer Facebook-Anwendung hinzufügen möchten, um für diese zu werben, empfehlen wir, es an die Anzeigekriterien für Smartphones anzupassen:
   >
   >1. Wählen Sie die Facebook-Anwendung [https://developers.facebook.com/apps](https://developers.facebook.com/apps) aus und klicken Sie auf den Tab **[!UICONTROL Einstellungen > Einfach]**.
   >1. Geben Sie das Feld **[!UICONTROL Namespace]** ein.
   >1. Geben Sie das Feld **[!UICONTROL Mobile Site-URL]** ein: Wenn ein Benutzer auf dem Smartphone auf den Link zur Veröffentlichung klickt, wird er automatisch von Facebook zu der in diesem Feld definierten URL weitergeleitet.
   >1. Erstellen Sie Ihre Webanwendung so, dass die Facebook-Anzeige in Abhängigkeit vom verwendeten Gerät (Smartphone oder PC) personalisiert wird.
   >1. Wechseln Sie über die Adobe Campaign-Konsole zum Feld **[!UICONTROL Link]** der Veröffentlichung und geben Sie die URL des Feldes **[!UICONTROL Arbeitsfläche]** ein.


1. Geben Sie im Feld **[!UICONTROL Bild]** die URL des Bildes ein, das links neben der Veröffentlichung angezeigt wird.

   >[!CAUTION]
   >
   >Das Bild muss auf einer öffentlichen Internet-Seite gehostet werden, damit Facebook es hochladen kann.

1. Geben Sie im Feld **[!UICONTROL Legende]** den Text ein, der am Ende der Veröffentlichung angezeigt werden soll.
1. Gehen Sie zum Feld **[!UICONTROL Beschreibung]** und geben Sie den Text ein, der unter dem Titel angezeigt werden soll.

![](assets/social_facebook_delivery_005.png)

### Veröffentlichen eines Status mit einem YouTube-Link {#publishing-a-status-with-a-youtube-link}

Mit diesem Inhaltstyp können Sie einen Link zu einem YouTube-Video veröffentlichen. Genau wie bei einem Status mit einem regulären Link können Sie einen Status, einen Namen, eine Beschriftung, eine Beschreibung und einen zusätzlichen Link definieren. Das Bild wird von Facebook automatisch hinzugefügt. Die Symmetrien zwischen den Feldern des Bearbeitungsbildschirms des Versands und der endgültigen Veröffentlichung auf Facebook sind nachfolgend aufgeführt:

![](assets/social_facebook_delivery_youtube_1.png)

Geben Sie die verschiedenen Felder ein:

>[!CAUTION]
>
>Alle URLs müssen mit **„http://“** oder **„https://“** beginnen.

1. Geben Sie im Feld **[!UICONTROL Status]** den Text ein, der unter dem Namen der Seite angezeigt werden soll.
1. Geben Sie im Feld **[!UICONTROL Name]** den Titel der Veröffentlichung ein.
1. Geben Sie im Feld **[!UICONTROL Video-Code]** den Code des YouTube-Videos ein. Für den Link &quot;https://www.youtube.com/watch?v=abc123456&quot; lautet der Video-Code beispielsweise &quot;abc123456&quot;.
1. Geben Sie im Feld **[!UICONTROL Legende]** den Text ein, der am Ende der Veröffentlichung angezeigt werden soll.
1. Gehen Sie zum Feld **[!UICONTROL Beschreibung]** und geben Sie den Text ein, der unter dem Titel angezeigt werden soll.

![](assets/social_facebook_delivery_youtube.png)

### Veröffentlichen eines Fotoalbums {#publishing-a-photo-album}

Mit diesem Inhaltstyp können Sie ein Fotoalbum veröffentlichen. Sie können einen Namen und eine Beschreibung für das Album sowie eine Beschriftung für jedes Foto hinzufügen. Die Symmetrien zwischen den Feldern des Bearbeitungsbildschirms des Versands und der endgültigen Veröffentlichung auf Facebook sind nachfolgend aufgeführt:

![](assets/social_facebook_delivery_photos_1.png)

Geben Sie die verschiedenen Felder ein:

1. Beginnen Sie mit der Eingabe des **[!UICONTROL Albumnamens]**.
1. Geben Sie dann die **[!UICONTROL Beschreibung]** ein, die über den Fotos angezeigt werden soll.
1. Um ein Foto hinzuzufügen, klicken Sie auf die Schaltfläche **[!UICONTROL Hinzufügen]**, wählen Sie das Foto aus und klicken Sie auf **[!UICONTROL Öffnen]**.
1. Jedem Foto kann eine Beschriftung hinzugefügt werden.

![](assets/social_facebook_delivery_photos.png)

## Vorschau {#previewing}

Im Tab **[!UICONTROL Vorschau]** können Sie das Rendering der Veröffentlichung anzeigen.

1. Klicken Sie auf den **[!UICONTROL Vorschau]**-Tab.
1. Klicken Sie auf das Dropdown-Menü **[!UICONTROL Personalisierung testen]** und wählen Sie **[!UICONTROL Dienst]** aus.
1. Wählen Sie im Feld **[!UICONTROL Ordner]** den Dienstordner aus, der Ihre Facebook-Seiten enthält. Standardmäßig werden Seiten im Stammordner des **[!UICONTROL Facebook]**-Dienstordners gespeichert.
1. Wählen Sie die Facebook-Seite aus, auf der Sie die Vorschau testen möchten.

![](assets/social_facebook_delivery_008.png)

>[!NOTE]
>
>Die Vorschau unterscheidet sich möglicherweise geringfügig von der endgültigen Facebook-Veröffentlichung. Es wird dringend empfohlen, vor dem endgültigen Versand einen Testversand abzuschicken, um ein genaues Rendering der Veröffentlichung zu sehen. [Weitere Informationen](#sending-the-proof).

## Konfigurieren des Trackings {#configuring-tracking}

Tracking kann in den Versandberichten und im Tab **[!UICONTROL Bearbeiten > Tracking]** des Versands und des Dienstes eingesehen werden.

Adobe Campaign misst die Klicks auf die im Versand enthaltene URL. Die Anzahl der Klicks auf die Schaltfläche **[!UICONTROL Gefällt mir]**, die Anzahl der Kommentare und die Anzahl der Fans werden von Facebook gemessen.

Die Tracking-Konfiguration ist dieselbe wie bei einem E-Mail-Versand. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../delivery/using/about-delivery-monitoring.md).

>[!NOTE]
>
>In der Versandvorlage **[!UICONTROL Auf einer Markenseite veröffentlichen]** ist Tracking standardmäßig aktiviert.

## Durchführen des Testversands {#sending-the-proof}

Es wird dringend empfohlen, vor dem endgültigen Versand Ihrer Veröffentlichung einen Testversand durchzuführen, um auf einer privaten Facebook-Testseite genau zu sehen, wie die Veröffentlichung gerendert wird. Weitere Informationen zum Erstellen einer privaten Facebook-Testseite finden Sie auf [dieser Seite](../../social/using/publishing-on-facebook-walls.md#creating-a-test-facebook-page). Die Schritte zur Auswahl des Testversands werden in [diesem Abschnitt](#selecting-the-proof-target) genau beschrieben.

Der Testversand ist mit dem E-Mail-Versand identisch. Siehe [diesen Abschnitt](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

## Senden der Nachricht {#sending-the-message}

1. Nachdem der Inhalt validiert wurde, klicken Sie auf die Schaltfläche **[!UICONTROL Senden]**.
1. Wählen Sie **[!UICONTROL Sendungen schnellstmöglich abschicken]** aus und klicken Sie auf die Schaltfläche **[!UICONTROL Analysieren]**.

   >[!NOTE]
   >
   >Mit der Option **[!UICONTROL Versand terminieren]** können Sie den Versand auf einen späteren Zeitpunkt verschieben.

   ![](assets/social_facebook_delivery_009.png)

1. Überprüfen Sie nach Abschluss der Analyse das Ergebnis.
1. Klicken Sie auf **[!UICONTROL Absendung bestätigen]** und dann auf **[!UICONTROL Ja]**.

   ![](assets/social_facebook_delivery_016.png)
