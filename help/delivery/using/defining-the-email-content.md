---
product: campaign
title: Definieren des E-Mail-Inhalts in Adobe Campaign Classic
description: Hier erfahren Sie, wie Sie mit Adobe Campaign den E-Mail-Inhalt definieren können.
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
feature: Email Design
role: User
hide: true
exl-id: 46212929-fd2d-44a2-897e-35f98e88af36
TQID: https://experienceleague.adobe.com/NWs-NqNfnkyoj0XJfy5-BvKwJofom-V0iSQJI3-F-38
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: a075b2c1-7748-4328-b7f6-343aa314616aid: b631758a-142d-425f-b9aa-f756d85cb979id: c858a28b-ea19-49b0-8d48-828717fad89c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2: id: e0eb8757-182f-49f3-94a4-1587d16f5094id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
subfeature_v2: id: e95a583b-fcfa-4524-8666-46a29c828119id: c8da4fdd-eb94-4751-a43c-f82733fb2d6eid: d5bbe3da-ba85-4242-817e-54f7c4b943e0id: f4da0e76-df77-451e-ad61-21afb7bd8810
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 2055
ht-degree: 100%

---

# Definieren des E-Mail-Inhalts {#defining-the-email-content}

## Absender {#sender}

Klicken Sie auf **[!UICONTROL Von]**, um den Namen und die Adresse des Absenders zu konfigurieren.

![](assets/s_ncs_user_wizard_email02.png)

In diesem Fenster können Sie alle Informationen eingeben, die für das Erstellen von E-Mail-Nachrichten-Headern erforderlich sind. Diese Informationen können personalisiert werden. Verwenden Sie dazu die Schaltflächen rechts neben den Eingabefeldern, um Personalisierungsfelder einzufügen.

Informationen zum Einfügen und Verwenden von Personalisierungsfeldern finden Sie im Abschnitt [Über die Personalisierung](about-personalization.md).

>[!NOTE]
>
>* Die Absenderadresse wird standardmäßig auch als Antwortadresse verwendet.
>* Header-Parameter dürfen nicht leer sein. Standardmäßig enthalten Sie die Werte, die beim Konfigurieren des Bereitstellungsassistenten eingegeben werden. Weiterführende Informationen finden Sie in [diesem Abschnitt](../../installation/using/deploying-an-instance.md).
>* Die Angabe der Absenderadresse ist für den E-Mail-Versand zwingend erforderlich (gemäß RFC-Standard).
>* Adobe Campaign führt eine Syntax-Prüfung der angegebenen E-Mail-Adressen durch.

>[!CAUTION]
>
>Um Probleme mit der Zustellbarkeit zu vermeiden, müssen die E-Mail-Konten vorhanden sein und überwacht werden, die den für Sendungen und Antworten angegebenen Adressen entsprechen. Wenden Sie sich an Ihre Systemadministratorin bzw. Ihren Systemadministrator.

## Nachrichtenbetreff {#message-subject}

Der Betreff der Nachricht wird im gleichnamigen Feld konfiguriert. Sie können ihn direkt im Feld eingeben oder auf den Link **[!UICONTROL Betreff]** klicken, um ein Script zu erfassen. Die Personalisierungsschaltfläche ermöglicht die Einfügung eines Datenbankfeldes.

>[!IMPORTANT]
>
>Die Angabe des Betreffs der Nachricht ist zwingend erforderlich.

![](assets/s_ncs_user_wizard_email_object.png)

Der Inhalt von Personalisierungsfeldern wird beim Versand der Nachrichten durch die im Empfängerprofil gespeicherten Werte ersetzt.

In oben stehender Nachricht wurde beispielsweise der Betreff der Nachricht für jeden Empfänger entsprechend seiner Profildaten personalisiert.

>[!NOTE]
>
>Die Verwendung von Personalisierungsfeldern wird im Abschnitt [Über die Personalisierung](about-personalization.md) beschrieben.

Mit dem Popup-Fenster **[!UICONTROL Emoticon einfügen]** können Sie auch Emoticons zu Ihrer Betreffzeile hinzufügen.

## Nachrichteninhalt {#message-content}

>[!IMPORTANT]
>
>Aus Datenschutzgründen empfehlen wir die Verwendung von HTTPS für alle externen Ressourcen.

Der eigentliche Nachrichteninhalt wird im unteren Bereich des Versandkonfigurationsfensters erfasst.

Nachrichten werden standardmäßig im HTML- oder Textformat gesendet, je nach Voreinstellung der Empfängerin bzw. des Empfängers. Wir empfehlen Inhalte in beiden Formaten zu erstellen, damit Nachrichten in jedem E-Mail-System korrekt angezeigt werden können. Weitere Informationen hierzu finden Sie unter [Wahl des Nachrichtenformats](email-parameters.md#selecting-message-formats).

* Verwenden Sie die Schaltfläche **[!UICONTROL Öffnen]**, um HTML-Inhalt zu importieren. Sie haben auch die Möglichkeit, den Quell-Code direkt in die Unterregisterkarte **[!UICONTROL Quelle]** einzufügen.

  Wenn Sie den [Digital Content Editor](../../web/using/about-campaign-html-editor.md) (DCE) verwenden, lesen Sie den Abschnitt zur [Auswahl einer Inhaltsvorlage](../../web/using/use-case-creating-an-email-delivery.md#step-3---selecting-a-content).

  >[!IMPORTANT]
  >
  >Der HTML-Inhalt muss vorab erstellt und anschließend in Adobe Campaign importiert werden. Der HTML-Editor ist nicht für die Inhaltserstellung vorgesehen.

  In der Unterregisterkarte **[!UICONTROL Vorschau]** können Sie das Rendering der einzelnen Inhalte für eine Empfängerin bzw. einen Empfänger anzeigen. Die Personalisierungsfelder und bedingten Inhaltselemente werden durch die entsprechenden Informationen für das ausgewählte Profil ersetzt.

  Über die verschiedenen Schaltflächen der Symbolleiste haben Sie Zugriff auf die Standard-Parameter für die Seitenaufmachung im HTML-Format.

  ![](assets/s_ncs_user_wizard_email01_138.png)

  Sie können Bilder aus einer lokalen Datei oder aus einer Bildbibliothek in Adobe Campaign in Nachrichten einfügen. Klicken Sie dazu auf das Symbol **[!UICONTROL Bild]** und wählen Sie die entsprechende Option aus.

  ![](assets/s_ncs_user_wizard_email01_18.png)

  Zugriff auf die Bilder aus der Bibliothek besteht über den Ordner **[!UICONTROL Ressourcen > Online > Öffentliche Ressourcen]** des Ordnerbaums. Siehe auch [Bilder hinzufügen](#adding-images).

  Die letzte Schaltfläche in der Symbolleiste dient der Einfügung von Personalisierungsfeldern.

  >[!NOTE]
  >
  >Die Verwendung von Personalisierungsfeldern wird im Abschnitt [Über die Personalisierung](about-personalization.md) beschrieben.

  In den Registerkarten am unteren Seitenrand können Sie den HTML-Code der zu erstellenden Seite anzeigen und das Rendering der Nachricht mit ihrer Personalisierung anzeigen. Klicken Sie hierfür auf die Registerkarte **[!UICONTROL Vorschau]** und wählen Sie über die Symbolleisten-Schaltfläche **[!UICONTROL Personalisierung testen...]** eine Empfängerin bzw. einen Empfänger aus. Sie können eine Empfängerin bzw. einen Empfänger aus der/den definierten Zielgruppe(n) auswählen oder eine andere Empfängerin bzw. einen anderen Empfänger auswählen.

  ![](assets/s_ncs_user_wizard_email01_139.png)

  Sie können die HTML-Nachricht valdieren. Sie können auch den Inhalt des E-Mail-Headers anzeigen.

  ![](assets/s_ncs_user_wizard_email01_140.png)

* Verwenden Sie zum Importieren von Textinhalten die Schaltfläche **[!UICONTROL Öffnen]** oder die Registerkarte **[!UICONTROL Textinhalt]**, um den Inhalt einer im Textformat angezeigten Nachricht einzugeben.Verwenden Sie die Schaltflächen der Symbolleiste, um auf Aktionen im Inhalt zuzugreifen. Mit der letzten Schaltfläche können Sie Personalisierungsfelder einfügen.

  ![](assets/s_ncs_user_wizard_email01_141.png)

  Der Tab **[!UICONTROL Vorschau]** am unteren Seitenrand ermöglicht die Anzeige des Renderings der Nachricht beim Empfänger inklusive Personalisierung.

  ![](assets/s_ncs_user_wizard_email01_142.png)


## Definieren interaktiver Inhalte {#amp-for-email-format}

Mit Adobe Campaign können Sie das neue interaktive Format [AMP für E-Mail](https://amp.dev/de/about/email/) testen, das unter bestimmten Bedingungen das Senden dynamischer E-Mails ermöglicht.

Weitere Informationen hierzu finden Sie in der [ Dokumentation zu Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/defining-interactive-content.html?lang=de){target="_blank"}.

## Verwenden von Content-Management {#using-content-management}

Sie können den Inhalt des Versands mithilfe der Content-Management-Formulare direkt im Versandassistenten definieren. Die zu verwendende Veröffentlichungsvorlage für den Inhalt muss in den Versandeigenschaften auf der Registerkarte **[!UICONTROL Erweitert]** angegeben werden.

![](assets/s_ncs_content_in_delivery.png)

Eine zusätzliche Registerkarte erlaubt nun die Erstellung von Inhalten, die automatisch entsprechend den Regeln des Content-Managements formatiert und integriert werden.

![](assets/s_ncs_content_in_delivery_edition_tab.png)

>[!NOTE]
>
>Weitere Informationen zum Content-Management in Adobe Campaign finden Sie in [diesem Abschnitt](about-content-management.md).

## Einfügen von Emoticons {#inserting-emoticons}

Sie können Emoticons in Ihren E-Mail-Inhalt einfügen.

1. Klicken Sie auf das Symbol **[!UICONTROL Emoticon einfügen]**.
1. Wählen Sie im Popup-Fenster ein Emoticon aus.

   ![](assets/emoticon_4.png)

1. Klicken Sie danach auf die Schaltfläche **[!UICONTROL Schließen]**.

Informationen zum Anpassen der Emoticon-Liste finden Sie auf dieser [Seite](customizing-emoticon-list.md).

## Hinzufügen von Bildern {#adding-images}

E-Mail-Sendungen im HTML-Format können Bilder enthalten. Sie können eine HTML-Seite mit Bildern über den Versandassistenten importieren oder Bilder direkt mithilfe des HTML-Editors über das **[!UICONTROL Bildsymbol]** einfügen.


### Schutzmechanismen {#img-guardrails}

Um Performance-Probleme zu vermeiden, dürfen die in den E-Mails enthaltenen Bilder nicht größer als 100 KB sein. Diese standardmäßig festgelegte Beschränkung kann in der Option `NmsDelivery_MaxDownloadedImageSize` geändert werden. Adobe empfiehlt jedoch dringend, große Bilder in E-Mail-Sendungen zu vermeiden.

Weitere Informationen finden Sie in der [Liste der Campaign Classic-Optionen](../../installation/using/configuring-campaign-options.md#delivery).

### Bildtypen {#img-types}

Diese Bilder können:

* lokal gespeichert sein oder von einem Server abgerufen werden;
* aus der Bibliothek der öffentlichen Ressourcen in Adobe Campaign stammen;

  Auf öffentliche Ressourcen kann über den Knoten **[!UICONTROL Ressourcen > Online]** der Adobe Campaign-Hierarchie zugegriffen werden. Sie sind in einer Bibliothek zusammengefasst und können in E-Mail-Nachrichten eingefügt und auch für Kampagnen oder Aufgaben bzw. für das Content-Management verwendet werden.

* Ein für Adobe Experience Cloud freigegebenes Asset. Weitere Informationen finden Sie in [diesem Abschnitt](../../integrations/using/sharing-assets-with-adobe-experience-cloud.md).

### Einfügen und Verwalten von Bildern {#manage-images}

Der Versandassistent bietet die Möglichkeit, lokale oder in der Bibliothek enthaltene Bilder in den Inhalt der Nachrichten einzuschließen. Wählen Sie hierfür die Schaltfläche **[!UICONTROL Bild]** in der Symbolleiste des HTML-Inhalts aus.

![](assets/s_ncs_user_image_from_library.png)

>[!IMPORTANT]
>
>Um von den Empfängern gesehen werden zu können, müssen die Bilder auf einem extern zugänglichen Server gespeichert werden.

So verwalten Sie Bilder über den Versandassistenten:

1. Klicken Sie in der Symbolleiste auf das Symbol **[!UICONTROL Tracking &amp; Bilder]**.
   ![](assets/s_ncs_user_email_del_img_param.png)

1. Wählen Sie die Option **[!UICONTROL Bilder hochladen]** auf dem Tab **[!UICONTROL Bilder]**.
1. Dann können Sie festlegen, ob die Bilder in die E-Mail-Nachricht eingeschlossen werden sollen.
   ![](assets/s_ncs_user_email_del_img_upload.png)

* Sie können Bilder manuell hochladen, ohne die Versandanalyse abwarten zu müssen. Klicken Sie dazu auf den Link **[!UICONTROL Bilder sofort online stellen...]**.
* Sie können einen anderen Pfad für Zugriff auf die Bilder auf dem Tracking-Server angeben. Geben Sie dazu einen Pfad in das Feld **[!UICONTROL URL der Bilder]** ein. Dieser Wert setzt den in den Parametern des Installationsassistenten definierten Wert außer Kraft.

Wenn Sie im Versandassistenten HTML-Inhalte mit eingebundenen Bildern öffnen, erhalten Sie eine Nachricht, die Ihnen die Möglichkeit gibt, die Bilder gemäß den Versandparametern sofort hochzuladen.

![](assets/s_ncs_user_email_del_img_local.png)

>[!IMPORTANT]
>
> Die Bild-URLs werden beim manuellen Hochladen oder beim Senden von Nachrichten geändert.
> 

### Anwendungsfall: Versand einer Nachricht mit Bildern {#uc-images}

Hier ist ein Beispiel für einen Versand mit vier Bildern zu sehen:

![](assets/s_ncs_user_images_in_delivery_wiz_1.png)

Die Bilder stammen aus einem lokalen Verzeichnis oder von einer Website, wie Sie im **[!UICONTROL Quelle]**-Tab feststellen können.

![](assets/s_ncs_user_images_in_delivery_wiz_2.png)

Wählen Sie das Symbol **[!UICONTROL Tracking &amp; Bilder]** und dann den Tab **[!UICONTROL Bilder]** aus, um die Erkennung der in der Nachricht enthaltenen Bilder zu starten.

Für jedes erkannte Bild können Sie den Status prüfen:

* Lokale oder auf anderen Servern gespeicherte Bilder werden als **[!UICONTROL Noch nicht online]** gekennzeichnet, auch wenn der Server von außerhalb zugänglich ist (beispielsweise bei Bildern einer Webseite).
* Bilder werden als **[!UICONTROL Bereits online]** gekennzeichnet, wenn Sie zuvor, z. B. bei Erstellung eines anderen Versands, online gestellt wurden.
* Im Bereitstellungassistenten können Sie URLs angeben, die bei der Bilderkennung nicht berücksichtigt werden sollen. Das Online-Stellen dieser Bilder wird demnach **[!UICONTROL Ignoriert]**.

>[!NOTE]
>
>Ein Bild wird über seinen Inhalt und nicht seinen Namen oder Pfad identifiziert. Daher wird auch ein Bild, das zuvor bereits unter einem anderen Namen oder aus einem anderen Verzeichnis online gestellt wurde, als **[!UICONTROL Bereits online]** erkannt.

Bilder werden im Zuge der Nachrichtenanalyse auf den Server geladen, um von außerhalb zugänglich zu sein. Dies gilt nicht für lokal gespeicherte Bilder, die im Vorfeld hochzuladen sind.

Sie können Arbeit im Voraus erledigen und Bilder hochladen, sodass sie von anderen Adobe Campaign-Benutzenden angezeigt werden können.Dies kann bei der Zusammenarbeit nützlich sein. Wählen Sie hierfür die Option **[!UICONTROL Bilder sofort online stellen…]** und klicken Sie auf den Link, um den Upload der Bilder auf den Server zu starten.

![](assets/s_ncs_user_images_in_delivery_wiz_3.png)

>[!NOTE]
>
>Dies löst die Änderung der Bild-URLs und insbesondere der Namen der Bilder aus.

Sobald die Bilder online sind, können Sie die Namens- und Pfadänderungen im **[!UICONTROL Quelle]**-Tab der Nachricht prüfen.

![](assets/s_ncs_user_images_in_delivery_wiz_4.png)

Durch Ankreuzen der Option **[!UICONTROL Bilder in die E-Mail einschließen (multipart related)]** haben Sie die Möglichkeit, in der entsprechenden Spalte für jedes Bild anzugeben, ob es in die E-Mail eingeschlossen werden soll oder nicht.

![](assets/s_ncs_user_images_in_delivery_wiz_5.png)

>[!NOTE]
>
>Wenn in der Nachricht lokale Bilder enthalten sind, ist die Änderung des Quellcodes der Nachricht zu bestätigen.

## Einfügen eines personalisierten Barcodes{#insert-a-barcode}

Die Barcode-Lösung bietet die Möglichkeit, verschiedene ein- oder zweidimensionale Code-Typen in den gängigsten Normen zu erstellen.

Es ist möglich, einen Barcode dynamisch als Bitmap unter Verwendung eines Werts zu generieren, der mithilfe von Kundenkriterien definiert wurde. Personalisierte Barcodes können in E-Mail-Kampagnen aufgenommen werden. Die Empfängerin bzw. der Empfänger kann die Nachricht drucken und sie dem ausstellenden Unternehmen zum Scannen vorlegen (z. B. beim Auschecken).

Positionieren Sie den Cursor im Inhalt an der Stelle, an der der Barcode eingefügt werden soll, und klicken Sie auf die Personalisierungsschaltfläche. Wählen Sie **[!UICONTROL Einfügen > Barcode...]**.

![](assets/barcode_insert_14.png)

Konfigurieren Sie dann die verschiedenen Elemente je nach Bedarf:

1. Wählen Sie den Barcode-Typ aus.

   * Für das 1D-Format stehen in Adobe Campaign folgende Typen zur Verfügung: Codabar, Code 128, GS1-128 (vormals EAN-128), UPC-A, UPC-E, ISBN, EAN-8, Code39, Interleaved 2 of 5, POSTNET und Royal Mail (RM4SCC).

     Beispiel eines 1D-Barcodes:

     ![](assets/barcode_insert_08.png)

   * Die Typen DataMatrix und PDF417 betreffen das 2D-Format.

     Beispiel eines 2D-Barcodes:

     ![](assets/barcode_insert_09.png)

   * Wählen Sie zum Einfügen eines QR-Codes seinen Typ aus und geben Sie die anzuwendende Fehlerkorrekturrate an. Diese Rate definiert die Menge der wiederholten Informationen und die Toleranz bei Verschlechterung.

     ![](assets/barcode_insert_06.png)

     Beispiel eines QR-Codes:

     ![](assets/barcode_insert_12.png)

1. Geben Sie die gewünschte Größe des Barcodes an. Durch Angabe eines Faktors von x1 bis x10 kann die Größe angepasst werden.
1. Im Feld **[!UICONTROL Wert]** können Sie den Wert des Barcodes definieren. Dieser kann einem Sonderangebot entsprechen und die Funktion von Kriterien übernehmen. Es kann sich um einen Wert eines mit den Kundinnen und Kunden verknüpften Datenbankfelds handeln.

   Unten stehendes Beispiel zeigt einen EAN-8-Barcode, in dem die Kundennummer eines Empfängers enthalten ist. Klicken Sie auf die Personalisierungsschaltfläche rechts vom Feld **[!UICONTROL Wert]** und wählen Sie die Option **[!UICONTROL Empfänger > Kundennummer]**.

   ![](assets/barcode_insert_15.png)

1. Im Feld **[!UICONTROL Höhe]** können Sie die Höhe des Barcodes anpassen, ohne die Breite und somit die Abstände zwischen den Balken zu verändern.

   Es erfolgt keine einschränkende Kontrolle Ihrer Eingaben in Bezug auf den Barcode-Typ. Sollte ein falscher oder nicht kompatibler Wert eingegeben werden, sehen Sie dies erst in der **Vorschau**. In diesem Fall ist der Barcode rot durchkreuzt.

   >[!NOTE]
   >
   >Der einem Barcode zugewiesene Wert hängt von seinem Typ ab. Beispielsweise muss ein EAN-8-Typ genau 8 Ziffern haben.
   >
   >Die Personalisierungsschaltfläche rechts vom Feld **[!UICONTROL Wert]** ermöglicht das Hinzufügen von Daten zusätzlich zum Wert selbst. Dadurch wird der Barcode angereichert, sofern dies vom Barcode-Standard akzeptiert wird.
   >
   >Wenn Sie beispielsweise einen GS1-128-Barcode verwenden und zusätzlich zum Wert die Kontonummer einer Empfängerin bzw. eines Empfängers angeben möchten, klicken Sie auf die Personalisierungsschaltfläche und wählen Sie die Option **[!UICONTROL Empfänger > Kundennummer]**. Wenn die Kontonummer der ausgewählten Empfängerin bzw. des ausgewählten Empfängers korrekt eingegeben wird, wird sie vom Barcode berücksichtigt.

Nachdem diese Elemente konfiguriert wurden, können Sie Ihre E-Mail abschließen und senden. Um Fehler zu vermeiden, sollten Sie vor dem Versand stets sicherstellen, dass Ihr Inhalt korrekt angezeigt wird. Klicken Sie hierzu auf die Registerkarte **[!UICONTROL Vorschau]**.

![](assets/barcode_insert_10.png)

>[!NOTE]
>
>Sollte ein Barcode-Wert sich als ungültig erweisen, erscheint das entsprechende Bild in der Vorschau rot durchkreuzt.

![](assets/barcode_insert_11.png)
