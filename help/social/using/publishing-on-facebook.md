---
title: Veröffentlichen auf Facebook
seo-title: Veröffentlichen auf Facebook
description: Veröffentlichen auf Facebook
seo-description: null
page-status-flag: never-activated
uuid: f15170fa-0e7d-4913-81d6-0072c1ece482
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: social
content-type: reference
topic-tags: publishing-on-facebook-twitter
discoiquuid: 335cf2de-1874-4e48-9538-f0937641cf96
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 963aaa81971a8883b944bfcf4d1a00d729627916

---


# Veröffentlichen auf Facebook{#publishing-on-facebook}

Nach Abschluss der Konfiguration können Sie mit Social Marketing Veröffentlichungen auf den Wänden Ihrer Facebook-Seiten veröffentlichen.

## Einschränkungen {#limitations}

Die folgenden Einschränkungen gelten für Facebook.

* Nachrichten dürfen nicht länger als 1.000 Zeichen sein.
* HTML wird nicht unterstützt.

## Versand erstellen {#creating-the-delivery}

Erstellen Sie eine neue Bereitstellung mithilfe der **[!UICONTROL Publish to a brand page]** Bereitstellungsvorlage.

![](assets/social_facebook_delivery_001.png)

## Hauptzielgruppe auswählen {#selecting-the-main-target}

Sie müssen die Seite(n) auswählen, auf der/denen Sie Ihre Veröffentlichung veröffentlichen möchten.

1. Klicken Sie auf den **[!UICONTROL To]** Link.

   ![](assets/social_facebook_delivery_010.png)

1. Click the **[!UICONTROL Add]** button.

   ![](assets/social_facebook_delivery_011.png)

1. Auswählen **[!UICONTROL A Facebook page]**.

   ![](assets/social_facebook_delivery_012.png)

1. Wählen Sie im **[!UICONTROL Folder]** Feld den Dienstordner aus, der die Facebook-Seite enthält. Standardmäßig werden Seiten im Stammordner des **[!UICONTROL Facebook]** Dienstordners gespeichert. Wählen Sie dann die Facebook-Seite aus, auf der Sie posten möchten.

   ![](assets/social_facebook_delivery_013.png)

## Testversand-Zielgruppe auswählen {#selecting-the-proof-target}

Auf der **[!UICONTROL Target of the proofs]** Registerkarte können Sie die Facebook-Seite definieren, die Sie zum Testen von Auslieferungen verwenden möchten, bevor Sie diese senden. Es wird empfohlen, hierfür eine eigene private Facebook-Seite zu erstellen. Weitere Informationen zum Erstellen einer privaten Facebook-Seite finden Sie unter [Erstellen einer Facebook-Testseite](../../social/using/publishing-on-facebook-walls.md#creating-a-test-facebook-page). Um das Proof-Ziel auszuwählen, wenden Sie die gleichen Schritte wie für das Hauptziel an: [Auswählen des Hauptziels](#selecting-the-main-target).

![](assets/social_facebook_delivery_004.png)

>[!NOTE]
>
>Wenn Sie dieselbe Facebook-Testseite für alle Auslieferungen verwenden, können Sie das Proof-Ziel in der **[!UICONTROL Publish to a brand page]** Bereitstellungsvorlage speichern, auf die über den **[!UICONTROL Resources > Templates > Delivery templates]** Knoten zugegriffen wird. Das Proof-Ziel wird bei jeder neuen Auslieferung standardmäßig eingegeben.

## Audience definieren {#defining-the-audience}

Wenn Sie lokale Segmente verwenden möchten, um den Typ der für die Veröffentlichung autorisierten Öffentlichkeit zu verfeinern, empfehlen wir, eine Facebook-Seite pro Segment zu erstellen (z. B.: Adobe Campaign Paris, Adobe Campaign London usw.).

Es ist jedoch auch möglich, die von Facebook verwendeten Zielgruppenfilter zu verwenden. Die **[!UICONTROL Audience]** Registerkarte des **[!UICONTROL Select target window]** Fensters enthält vier Filter:

* **[!UICONTROL Country]**
* **[!UICONTROL Regions]**
* **[!UICONTROL Cities]**
* **[!UICONTROL Languages]**

>[!IMPORTANT]
>
>Verwenden Sie diese Funktion mit Vorsicht. In Bereitstellungsberichten berücksichtigt der **[!UICONTROL Number of fans]** Indikator diese Facebook-Filter nicht.
>
>Facebook kann die Liste der Zielgruppenfilter sowie deren Werte ändern.

## Definieren des Nachrichteninhalts {#defining-message-content}

Wählen Sie den Veröffentlichungstyp über das **[!UICONTROL Content type]** Dropdownmenü aus.

![](assets/social_facebook_delivery_006.png)

Folgende Arten von Lieferungen sind verfügbar:

* a **[!UICONTROL Status]**
* a **[!UICONTROL Status with a link]**
* a **[!UICONTROL Status with a YouTube link]**
* a **[!UICONTROL Photo album]**

### Veröffentlichen eines Status {#publishing-a-status}

Eine Statustypbereitstellung kann nur Text enthalten, wie im folgenden Beispiel:

![](assets/social_create_facebook_wall_post_004.png)

Geben Sie den Veröffentlichungsstatus in der Eingabezone ein.

![](assets/social_facebook_delivery_015.png)

### Veröffentlichen eines Status mit einem Link {#publishing-a-status-with-a-link}

Eine Statuszustellung mit einem Link kann Text, Bilder und einen Link enthalten. Im folgenden Abschnitt wird die Symmetrie zwischen den Feldern im Bearbeitungsbildschirm für die Bereitstellung und der endgültigen Veröffentlichung auf Facebook erläutert:

![](assets/social_facebook_delivery_007.png)

Geben Sie die verschiedenen Felder ein:

>[!IMPORTANT]
>
>Alle URLs müssen mit **&quot;http://&quot;** oder **&quot;https://&quot;** beginnen.

1. Geben Sie in das **[!UICONTROL Status]** Feld den Text ein, der unter dem Namen der Seite angezeigt wird.
1. Geben Sie im **[!UICONTROL Name]** Feld den Titel der Veröffentlichung ein.
1. Geben Sie in das **[!UICONTROL Link]** Feld die URL ein, auf die die Veröffentlichung verweist.

   >[!NOTE]
   >
   >Wenn Sie das **[!UICONTROL Link]** Feld zur URL einer Facebook-Anwendung hinzufügen möchten, um es zu bewerben, empfehlen wir, es an die Anzeigekriterien für Smartphones anzupassen:
   >
   >1. Wählen Sie die Facebook-Anwendung [https://developers.facebook.com/apps](https://developers.facebook.com/apps)und dann die **[!UICONTROL Settings > Basic]** Registerkarte.
   >1. Geben Sie das **[!UICONTROL Namespace]** Feld ein.
   >1. Geben Sie das **[!UICONTROL Mobile Site URL]** Feld ein: Wenn ein Benutzer auf dem Smartphone auf den Link zur Veröffentlichung klickt, wird er automatisch von Facebook zu der in diesem Feld definierten URL weitergeleitet.
   >1. Erstellen Sie Ihre Webanwendung, damit die Facebook-Anzeige als Funktion des verwendeten Geräts (Smartphone oder PC) personalisiert wird.
   >1. Wechseln Sie über die Adobe Campaign-Konsole zum **[!UICONTROL Link]** Feld der Veröffentlichung und geben Sie die URL des **[!UICONTROL Canvas page]** Felds ein.


1. Geben Sie in das **[!UICONTROL Image]** Feld die URL des Bildes ein, das links neben der Veröffentlichung angezeigt wird.

   >[!IMPORTANT]
   >
   >Das Bild muss auf einer öffentlichen Internetseite gehostet werden, damit Facebook es hochladen kann.

1. Geben Sie in das **[!UICONTROL Caption]** Feld den Text ein, der am Ende der Veröffentlichung angezeigt werden soll.
1. Gehen Sie zum **[!UICONTROL Description]** Feld und geben Sie den Text ein, der unter dem Titel angezeigt werden soll.

![](assets/social_facebook_delivery_005.png)

### Veröffentlichen eines Status mit einem YouTube-Link {#publishing-a-status-with-a-youtube-link}

Mit diesem Inhaltstyp können Sie einen Link zu einem YouTube-Video veröffentlichen. Wie ein Status mit einem regulären Link können Sie auch einen Status, einen Namen, eine Beschriftung, eine Beschreibung und einen zusätzlichen Link definieren. Das Bild wird automatisch von Facebook hinzugefügt. Die Symmetrien zwischen den Feldern des Bearbeitungsbildschirms für die Bereitstellung und der endgültigen Veröffentlichung auf Facebook sind nachfolgend aufgeführt:

![](assets/social_facebook_delivery_youtube_1.png)

Geben Sie die verschiedenen Felder ein:

>[!CAUTION]
>
>Alle URLs müssen mit **&quot;http://&quot;** oder **&quot;https://&quot;** beginnen.

1. Geben Sie in das **[!UICONTROL Status]** Feld den Text ein, der unter dem Namen der Seite angezeigt wird.
1. Geben Sie im **[!UICONTROL Name]** Feld den Titel der Veröffentlichung ein.
1. Geben Sie in das **[!UICONTROL Video code]** Feld den Code des YouTube-Videos ein. Für den Link &quot;https://www.youtube.com/watch?v=abc123456&#39;&quot;lautet der Videocode beispielsweise &quot;abc123456&quot;.
1. Geben Sie in das **[!UICONTROL Caption]** Feld den Text ein, der am Ende der Veröffentlichung angezeigt werden soll.
1. Gehen Sie zum **[!UICONTROL Description]** Feld und geben Sie den Text ein, der unter dem Titel angezeigt werden soll.

![](assets/social_facebook_delivery_youtube.png)

### Veröffentlichen eines Fotoalbums {#publishing-a-photo-album}

Mit diesem Inhaltstyp können Sie ein Fotoalbum veröffentlichen. Sie können einen Namen und eine Beschreibung für das Album sowie eine Beschriftung für jedes Foto hinzufügen. Die Symmetrien zwischen den Feldern des Bearbeitungsbildschirms für die Bereitstellung und der endgültigen Veröffentlichung auf Facebook sind nachfolgend aufgeführt:

![](assets/social_facebook_delivery_photos_1.png)

Geben Sie die verschiedenen Felder ein:

1. Start by entering the **[!UICONTROL Album name]**.
1. Geben Sie dann das Bild ein, das über den Fotos angezeigt werden **[!UICONTROL Description]** soll.
1. Um ein Foto hinzuzufügen, klicken Sie auf die **[!UICONTROL Add]** Schaltfläche, wählen Sie das Foto aus und klicken Sie auf **[!UICONTROL Open]**.
1. Jedem Foto kann eine Bildunterschrift hinzugefügt werden.

![](assets/social_facebook_delivery_photos.png)

## Vorschau {#previewing}

Auf der **[!UICONTROL Preview]** Registerkarte können Sie die Darstellung der Veröffentlichung anzeigen.

1.  Klicken Sie auf die **[!UICONTROL Preview]** Registerkarte.
1. Klicken Sie auf das **[!UICONTROL Test personalization]** Dropdownmenü und wählen Sie **[!UICONTROL Service]**.
1. Wählen Sie im **[!UICONTROL Folder]** Feld den Dienstordner aus, der Ihre Facebook-Seiten enthält. Standardmäßig werden Seiten im Stammordner des **[!UICONTROL Facebook]** Dienstordners gespeichert.
1. Wählen Sie die Facebook-Seite aus, auf der Sie die Vorschau testen möchten.

![](assets/social_facebook_delivery_008.png)

>[!NOTE]
>
>Die Vorschau unterscheidet sich möglicherweise geringfügig von der endgültigen Facebook-Veröffentlichung. Es wird dringend empfohlen, vor der endgültigen Lieferung einen Nachweis für eine genaue Wiedergabe der Veröffentlichung zu senden. Siehe [Senden des Nachweises](#sending-the-proof).

## Tracking-Konfiguration {#configuring-tracking}

Die Verfolgung kann in den Bereitstellungsberichten und auf der **[!UICONTROL Edit > Tracking]** Registerkarte der Bereitstellung und des Dienstes angezeigt werden.

Klicks auf die in der Bereitstellung enthaltene URL werden von Adobe Campaign gemessen. Die Anzahl der Klicks auf die **[!UICONTROL Like]** Schaltfläche, die Anzahl der Kommentare und die Anzahl der Fans werden von Facebook gemessen.

Die Verfolgungskonfiguration ist dieselbe wie bei einer E-Mail-Auslieferung. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../delivery/using/monitoring-a-delivery.md).

>[!NOTE]
>
>In der **[!UICONTROL Publish to a brand page]** Bereitstellungsvorlage ist die Verfolgung standardmäßig aktiviert.

## Senden des Nachweises {#sending-the-proof}

Wir empfehlen dringend, vor der endgültigen Auslieferung einen Nachweis Ihrer Veröffentlichung zu senden, um die genaue Wiedergabe der Veröffentlichung auf einer privaten Facebook-Testseite anzuzeigen. Weitere Informationen zum Erstellen einer privaten Facebook-Testseite finden Sie unter [Erstellen einer Facebook-Testseite](../../social/using/publishing-on-facebook-walls.md#creating-a-test-facebook-page). Die Schritte zur Auswahl des Zielnachweises werden unter [Auswählen des Proof-Ziels](#selecting-the-proof-target)beschrieben.

Der Zustellnachweis ist mit den E-Mail-Zustellungen identisch. Siehe [diesen Abschnitt](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

## Senden der Nachricht {#sending-the-message}

1. Nachdem der Inhalt genehmigt wurde, klicken Sie auf die **[!UICONTROL Send]** Schaltfläche.
1. Wählen Sie **[!UICONTROL Deliver as soon as possible]** und klicken Sie auf die **[!UICONTROL Analyze]** Schaltfläche.

   >[!NOTE]
   >
   >Mit dieser **[!UICONTROL Postpone the delivery]** Option können Sie die Lieferung auf ein späteres Datum verschieben.

   ![](assets/social_facebook_delivery_009.png)

1. Überprüfen Sie nach Abschluss der Analyse das Ergebnis.
1. Klicken Sie auf **[!UICONTROL Confirm delivery]** und dann auf **[!UICONTROL Yes]**.

   ![](assets/social_facebook_delivery_016.png)

