---
product: campaign
title: Definieren des E-Mail-Inhalts in Adobe Campaign Classic
description: Hier erfahren Sie, wie Sie mit Adobe Campaign den E-Mail-Inhalt definieren können.
badge-v7: label="v7" type="Informative" tooltip="Gilt für Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Gilt auch für Campaign v8"
feature: Email Design
exl-id: 46212929-fd2d-44a2-897e-35f98e88af36
source-git-commit: 728fc285fbd562003199c53339899bbc4441bfc6
workflow-type: ht
source-wordcount: '2029'
ht-degree: 100%

---

# Definieren des E-Mail-Inhalts {#defining-the-email-content}

## Absender {#sender}

Klicken Sie auf **[!UICONTROL Von]**, um den Namen und die Adresse des Absenders zu konfigurieren.

![](assets/s_ncs_user_wizard_email02.png)

In dem sich öffnenden Fenster werden alle im E-Mail-Header angezeigten Informationen erfasst. Diese können vom Benutzer individuell gestaltet werden. Nutzen Sie hierfür die Personalisierungsfelder, die über die Schaltflächen rechts der Eingabefelder eingefügt werden.

Informationen zum Einfügen und Verwenden von Personalisierungsfeldern finden Sie im Abschnitt [Über die Personalisierung](about-personalization.md).

>[!NOTE]
>
>* Die Absenderadresse wird standardmäßig auch als Antwortadresse verwendet.
>* Die Header-Parameter dürfen nicht leer sein. Standardmäßig enthalten sie die Werte, die beim Konfigurieren des Bereitstellungsassistenten eingegeben werden. Weiterführende Informationen finden Sie in [diesem Abschnitt](../../installation/using/deploying-an-instance.md).
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

Standardmäßig werden die Nachrichten den Angaben des Empfängers entsprechend im HTML- oder Textformat versandt. Um die korrekte Anzeige in allen E-Mail-Systemen zu gewährleisten, wird empfohlen, jeweils sowohl HTML- als auch Textinhalte zu erstellen. Weitere Informationen hierzu finden Sie unter [Wahl des Nachrichtenformats](email-parameters.md#selecting-message-formats).

* Verwenden Sie die Schaltfläche **[!UICONTROL Öffnen]**, um HTML-Inhalt zu importieren. Sie haben auch die Möglichkeit, den Quellcode direkt in den Tab **[!UICONTROL Quelle]** einzufügen.

  Wenn Sie den [Digital Content Editor](../../web/using/about-campaign-html-editor.md) (DCE) verwenden, lesen Sie den Abschnitt zur [Auswahl einer Inhaltsvorlage](../../web/using/use-case--creating-an-email-delivery.md#step-3---selecting-a-content).

  >[!IMPORTANT]
  >
  >Der HTML-Inhalt muss vorab erstellt und anschließend in Adobe Campaign importiert werden. Der HTML-Editor ist nicht für die Inhaltserstellung vorgesehen.

  Der Tab **[!UICONTROL Vorschau]** ermöglicht es, das Rendering für einen Empfänger zu simulieren. Die Personalisierungsfelder und die bedingten Elemente des Inhalts werden durch die im ausgewählten Profil gespeicherten Informationen ersetzt.

  Über die verschiedenen Schaltflächen der Symbolleiste haben Sie Zugriff auf die Standard-Parameter für die Seitenaufmachung im HTML-Format.

  ![](assets/s_ncs_user_wizard_email01_138.png)

  Durch Klick auf die Schaltfläche **[!UICONTROL Bild]** können Sie beispielsweise Bilder aus einer lokalen Datei oder aus der in Adobe Campaign enthaltenen Bibliothek einfügen.

  ![](assets/s_ncs_user_wizard_email01_18.png)

  Zugriff auf die Bilder aus der Bibliothek besteht über den Ordner **[!UICONTROL Ressourcen > Online > Öffentliche Ressourcen]** des Ordnerbaums. Siehe auch [Bilder hinzufügen](#adding-images).

  Die letzte Schaltfläche in der Symbolleiste dient der Einfügung von Personalisierungsfeldern.

  >[!NOTE]
  >
  >Die Verwendung von Personalisierungsfeldern wird im Abschnitt [Über die Personalisierung](about-personalization.md) beschrieben.

  Die Tabs am unteren Seitenrand ermöglichen die Anzeige des HTML-Quellcodes der in Erstellung begriffenen Seite und des Renderings der Nachricht beim Empfänger inklusive Personalisierung. Klicken Sie hierfür auf den Tab **[!UICONTROL Vorschau]** und wählen Sie über die Symbolleisten-Schaltfläche **[!UICONTROL Personalisierung testen...]** einen Empfänger aus. Sie können dabei einen beliebigen oder einen in der Zielgruppe enthaltenen Empfänger wählen.

  ![](assets/s_ncs_user_wizard_email01_139.png)

  Sie haben die Möglichkeit, die HTML-Nachricht zu validieren und den Inhalt des E-Mail-Headers zu prüfen.

  ![](assets/s_ncs_user_wizard_email01_140.png)

* Verwenden Sie die Schaltfläche **[!UICONTROL Öffnen]**, um Textinhalt zu importieren. Sie haben auch die Möglichkeit, den Inhalt im Tab **[!UICONTROL Textinhalt]** direkt zu erfassen. Über die verschiedenen Schaltflächen der Symbolleiste können Sie die Textaufmachung ändern. Die letzte Schaltfläche in der Symbolleiste dient der Einfügung von Personalisierungsfeldern.

  ![](assets/s_ncs_user_wizard_email01_141.png)

  Der Tab **[!UICONTROL Vorschau]** am unteren Seitenrand ermöglicht die Anzeige des Renderings der Nachricht beim Empfänger inklusive Personalisierung.

  ![](assets/s_ncs_user_wizard_email01_142.png)


## Definieren interaktiver Inhalte {#amp-for-email-format}

Mit Adobe Campaign können Sie das neue interaktive Format [AMP für E-Mail](https://amp.dev/de/about/email/) testen, das unter bestimmten Bedingungen das Senden dynamischer E-Mails ermöglicht.

Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](defining-interactive-content.md).

## Verwenden von Content-Management {#using-content-management}

Wenn Sie den Inhalt Ihres Versands mithilfe des Content Managements erstellen, ist es erforderlich, die zu verwendende Inhaltsvorlage in den Versandeigenschaften im **[!UICONTROL Erweitert]**-Tab des Versand-Assistenten anzugeben.

![](assets/s_ncs_content_in_delivery.png)

Ein zusätzlicher Tab erlaubt nun die Erstellung eines Inhalts, der automatisch den Regeln des Content Managements entsprechend formatiert und integriert wird.

![](assets/s_ncs_content_in_delivery_edition_tab.png)

>[!NOTE]
>
>Weitere Informationen zum Content Management in Adobe Campaign finden Sie in [diesem Abschnitt](about-content-management.md).

## Einfügen von Emoticons {#inserting-emoticons}

Sie können Emoticons in Ihren E-Mail-Inhalt einfügen.

1. Klicken Sie auf das Symbol **[!UICONTROL Emoticon einfügen]**.
1. Wählen Sie im Popup-Fenster ein Emoticon aus.

   ![](assets/emoticon_4.png)

1. Klicken Sie danach auf die Schaltfläche **[!UICONTROL Schließen]**.

Informationen zum Anpassen der Emoticon-Liste finden Sie auf dieser [Seite](customizing-emoticon-list.md).

## Hinzufügen von Bildern {#adding-images}

E-Mail-Sendungen im HTML-Format können Bilder enthalten. Sie können im Versand-Assistenten entweder eine fertige HTML-Seite mit Bildern importieren oder Bilder im HTML-Editor über das Symbol **[!UICONTROL Bild]** einfügen.


### Schutzmechanismen {#img-guardrails}

Um Leistungsprobleme zu vermeiden, dürfen die in den E-Mails enthaltenen Bilder nicht größer als 100 KB sein. Diese standardmäßig festgelegte Beschränkung kann in der Option `NmsDelivery_MaxDownloadedImageSize` geändert werden. Adobe empfiehlt jedoch dringend, große Bilder in E-Mail-Sendungen zu vermeiden.

Weitere Informationen finden Sie in der [Liste der Campaign Classic-Optionen](../../installation/using/configuring-campaign-options.md#delivery).

### Bildtypen {#img-types}

Diese Bilder können:

* lokal gespeichert sein oder von einem Server abgerufen werden;
* aus der Bibliothek der öffentlichen Ressourcen in Adobe Campaign stammen;

  Auf öffentliche Ressourcen kann im Knoten **[!UICONTROL Ressourcen > Online > Öffentliche Ressourcen]** des Navigationsbaums zugegriffen werden. Sie sind in einer Bibliothek zusammengefasst und können in E-Mails, Kampagnen, Aufgaben und dem Content Management verwendet werden.

* Weiterführende Informationen zu freigegebenen Assets in Adobe Experience Cloud finden Sie in [diesem Abschnitt](../../integrations/using/sharing-assets-with-adobe-experience-cloud.md).

### Einfügen und Verwalten von Bildern {#manage-images}

Der Versand-Assistent bietet die Möglichkeit, lokale oder in der Bibliothek enthaltene Bilder in den Inhalt der Nachrichten einzuschließen. Wählen Sie hierfür die Schaltfläche **[!UICONTROL Bild]** in der Symbolleiste des HTML-Inhalts aus.

![](assets/s_ncs_user_image_from_library.png)

>[!IMPORTANT]
>
>Um von den Empfängern gesehen werden zu können, müssen die Bilder auf einem extern zugänglichen Server gespeichert werden.

So verwalten Sie Bilder über den Versand-Assistenten:

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

Die Bilder stammen aus einem lokalen Verzeichnis oder von einer Webseite, wie Sie im **[!UICONTROL Quelle]**-Tab feststellen können.

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

Es besteht die Möglichkeit, das Online-Stellen der Bilder vorzuziehen, damit beispielsweise andere Adobe-Campaign-Benutzer im Rahmen gemeinsamer Versandprojekte darauf zugreifen können. Wählen Sie hierfür die Option **[!UICONTROL Online-Stellen der Bilder]** und klicken Sie auf den Link , um den Upload der Bilder auf den Server zu starten.

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

Barcodes können in Form eines Bitmaps dynamisch mithilfe eines durch Kundenkriterien definierten Werts erzeugt werden. Personalisierte Barcodes lassen sich dann über E-Mails in Marketingkampagnen integrieren. Der Empfänger kann die Nachricht ausdrucken und sie dem Unternehmen (z. B. bei einem Zahlvorgang) zum Scannen vorlegen.

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

   * Bei der Wahl eines QR-Codes ist die anzuwendende Fehlerkorrektur anzugeben. Die Quote bezeichnet den zu wiederholenden Informationsanteil und damit eine mehr oder weniger ausgeprägte Toleranz bei partieller Unlesbarkeit.

     ![](assets/barcode_insert_06.png)

     Beispiel eines QR-Codes:

     ![](assets/barcode_insert_12.png)

1. Geben Sie die gewünschte Größe des Barcodes an. Durch Angabe eines Faktors von x1 bis x10 kann die Größe angepasst werden.
1. Das Feld **[!UICONTROL Wert]** dient der Bestimmung des Barcode-Werts. Dieser kann einem Sonderangebot entsprechen oder durch eine Bedingungsfunktion definiert werden, beispielsweise den Wert eines kundenbezogenen Datenbankfelds.

   Unten stehendes Beispiel zeigt einen EAN-8-Barcode, in dem die Kundennummer eines Empfängers enthalten ist. Klicken Sie auf die Personalisierungsschaltfläche rechts vom Feld **[!UICONTROL Wert]** und wählen Sie die Option **[!UICONTROL Empfänger > Kundennummer]**.

   ![](assets/barcode_insert_15.png)

1. Im Feld **[!UICONTROL Höhe]** können Sie die Höhe des Barcodes anpassen, ohne die Breite und somit die Abstände zwischen den Balken zu verändern.

   Bitte beachten Sie, dass keine einschränkende Kontrolle Ihrer Eingaben in Bezug auf den Barcode-Typ erfolgt. Sollte ein falscher oder nicht kompatibler Wert eingegeben werden, sehen Sie dies erst in der **Vorschau**. In diesem Fall ist der Barcode rot durchkreuzt.

   >[!NOTE]
   >
   >Der einem Barcode zugeteilte Wert ist vom Typ abhängig. So muss beispielsweise ein EAN-8-Barcode genau acht Ziffern enthalten.
   >
   >Die Personalisierungsschaltfläche rechts vom **[!UICONTROL Wert]**-Feld ermöglicht das Hinzufügen von den Wert ergänzenden Daten. Diese reichern den Barcode an, sofern der Barcode-Typ dies zulässt.
   >
   >Wenn Sie beispielsweise einen GS1-128-Barcode verwenden und zusätzlich zum Wert die Kundennummer des Empfängers angeben möchten, klicken Sie auf die Personalisierungsschaltfläche und wählen Sie die Option **[!UICONTROL Empfänger > Kundennummer]**. Wenn die Kundennummer des Empfängers korrekt in der Datenbank gespeichert ist, wird sie im Barcode berücksichtigt.

Bevor Sie den Versand starten, prüfen Sie im **[!UICONTROL Vorschau]**-Tab, dass der Inhalt wie gewünscht angezeigt wird.

![](assets/barcode_insert_10.png)

>[!NOTE]
>
>Sollte ein Barcode-Wert sich als ungültig erweisen, erscheint das entsprechende Bild in der Vorschau rot durchkreuzt.

![](assets/barcode_insert_11.png)
