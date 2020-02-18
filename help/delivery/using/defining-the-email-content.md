---
title: Definieren des E-Mail-Inhalts in Adobe Campaign Classic
description: Erfahren Sie, wie Sie den E-Mail-Inhalt mit Adobe Campaign Classic definieren.
page-status-flag: never-activated
uuid: ddcc2e3b-e251-4a7a-a22a-28701522839f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-emails
discoiquuid: 2ea2747f-957f-41a9-a03f-20c03fa99116
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 4ac96bf0e54268832b84b17c3cc577af038cc712

---


# E-Mail-Inhalt erstellen{#defining-the-email-content}

## Absender {#sender}

To define the name and address of the sender which will appear in the header of messages sent, click the **[!UICONTROL From]** link.

![](assets/s_ncs_user_wizard_email02.png)

In dem sich öffnenden Fenster werden alle im E-Mail-Header angezeigten Informationen erfasst. Diese können vom Benutzer individuell gestaltet werden. Nutzen Sie hierfür die Personalisierungsfelder, die über die Schaltflächen rechts der Eingabefelder eingefügt werden.

To find out how to insert and use personalization fields, refer to [About personalization](../../delivery/using/about-personalization.md) section.

>[!NOTE]
>
>* Die Absenderadresse wird standardmäßig auch als Antwortadresse verwendet.
>* Die E-Mail-Header-Parameter müssen zwingend angegeben werden. Standardmäßig sind die Werte, die bei der Konfiguration des Softwareverteilungs-Assistenten angegeben wurden, vorausgefüllt. Weiterführende Informationen finden Sie im [Installationshandbuch](../../installation/using/deploying-an-instance.md).
>* Die Angabe der Absenderadresse ist für den E-Mail-Versand zwingend erforderlich (gemäß RFC-Standard).
>* Adobe Campaign führt eine Syntax-Prüfung der angegebenen E-Mail-Adressen durch.


>[!CAUTION]
>
>Im Rahmen der durch Internet-Serviceanbieter (ISP) zur Eindämmung unerwünschter E-Mails (SPAM) durchgeführten Kontrollen empfiehlt Adobe Campaign, dass die als Absender- und Antwortadresse angegebenen E-Mail-Konten tatsächlich existieren. Wenden Sie sich diesbezüglich bitte an den Administrator Ihres E-Mail-Programms.

## Nachrichtenbetreff {#message-subject}

Der Betreff der Nachricht wird im entsprechenden Feld konfiguriert. Sie können sie direkt in das Feld eingeben oder auf den **[!UICONTROL Subject]** Link klicken, um ein Skript einzugeben. Über den Personalisierungslink können Sie Datenbankfelder in den Betreff einfügen.

>[!CAUTION]
>
>Die Angabe des Betreffs der Nachricht ist zwingend erforderlich.

![](assets/s_ncs_user_wizard_email_object.png)

Der Inhalt von Personalisierungsfeldern wird beim Versand der Nachrichten durch die im Empfängerprofil gespeicherten Werte ersetzt.

In oben stehender Nachricht wurde beispielsweise der Betreff der Nachricht für jeden Empfänger entsprechend seiner Profildaten personalisiert.

>[!NOTE]
>
>The use of personalization fields is presented in [About personalization](../../delivery/using/about-personalization.md).

## Nachrichteninhalt {#message-content}

>[!CAUTION]
>
>Aus Datenschutzgründen wird empfohlen, HTTPS für alle externen Ressourcen zu verwenden.

Der eigentliche Nachrichteninhalt wird im unteren Bereich des Versandkonfigurationsfensters erfasst.

Nachrichten werden standardmäßig im HTML- oder Textformat gesendet, je nach Empfängereinstellung. Es wird empfohlen, Inhalte in beiden Formaten zu erstellen, um sicherzustellen, dass Nachrichten in jedem Mailsystem korrekt angezeigt werden können. Weitere Informationen finden Sie unter [Auswählen von Nachrichtenformaten](#selecting-message-formats).

* Um einen HTML-Inhalt zu importieren, verwenden Sie die **[!UICONTROL Open]** Schaltfläche. Sie können den Quellcode auch direkt in die **[!UICONTROL Source]** Unterregisterkarte einfügen.

   Wenn Sie den [Digital Content Editor](../../web/using/about-campaign-html-editor.md) (DCE) verwenden, lesen Sie den Abschnitt zur [Auswahl einer Inhaltsvorlage](../../web/using/use-case--creating-an-email-delivery.md#step-3---selecting-a-content).

   >[!CAUTION]
   >
   >Der HTML-Inhalt muss vorab erstellt und anschließend in Adobe Campaign importiert werden. Der HTML-Editor ist nicht für die Inhaltserstellung vorgesehen.

   Auf der **[!UICONTROL Preview]** Unterregisterkarte können Sie die Wiedergabe der einzelnen Inhalte eines Empfängers anzeigen. Die Personalisierungsfelder und die bedingten Elemente des Inhalts werden durch die entsprechenden Informationen für das ausgewählte Profil ersetzt.

   Über die verschiedenen Schaltflächen der Symbolleiste haben Sie Zugriff auf die Standard-Parameter für die Seitenaufmachung im HTML-Format.

   ![](assets/s_ncs_user_wizard_email01_138.png)

   Sie können Bilder in Nachrichten aus einer lokalen Datei oder aus einer Bildbibliothek in Adobe Campaign einfügen. Klicken Sie dazu auf das **[!UICONTROL Image]** Symbol und wählen Sie die entsprechende Option aus.

   ![](assets/s_ncs_user_wizard_email01_18.png)

   Auf Bibliotheksbilder kann über den **[!UICONTROL Resources>Online>Public resources]** Ordner in der Ordnerstruktur zugegriffen werden. Siehe auch [Hinzufügen von Bildern](#adding-images).

   Die letzte Schaltfläche in der Symbolleiste dient der Einfügung von Personalisierungsfeldern.

   >[!NOTE]
   >
   >The use of personalization fields is presented in [About personalization](../../delivery/using/about-personalization.md).

   Auf den Registerkarten unten auf der Seite können Sie den HTML-Code der erstellten Seite anzeigen und die Wiedergabe der Nachricht mit ihrer Personalisierung anzeigen. Um diese Anzeige zu starten, klicken Sie auf **[!UICONTROL Preview]** und wählen Sie einen Empfänger über die Schaltfläche in der Symbolleiste **[!UICONTROL Test personalization]** aus. Sie können einen Empfänger aus den definierten Zielen auswählen oder einen anderen Empfänger auswählen.

   ![](assets/s_ncs_user_wizard_email01_139.png)

   Sie haben die Möglichkeit, die HTML-Nachricht zu validieren und den Inhalt des E-Mail-Headers zu prüfen.

   ![](assets/s_ncs_user_wizard_email01_140.png)

* Um einen Textinhalt zu importieren, verwenden Sie die **[!UICONTROL Open]** Schaltfläche oder die **[!UICONTROL Text Content]** Registerkarte, um den Inhalt der Nachricht einzugeben, wenn sie im Textformat angezeigt wird. Verwenden Sie die Symbolleistenschaltflächen, um auf Aktionen für den Inhalt zuzugreifen. Über die letzte Schaltfläche können Sie Personalisierungsfelder einfügen.

   ![](assets/s_ncs_user_wizard_email01_141.png)

   As for the HTML format click the **[!UICONTROL Preview]** tab at the bottom of the page to view the rendering of the message with its personalization.

   ![](assets/s_ncs_user_wizard_email01_142.png)

## Wahl des Nachrichtenformats {#selecting-message-formats}

Sie können das Format der gesendeten E-Mail-Nachrichten ändern. Bearbeiten Sie dazu die Bereitstellungseigenschaften und klicken Sie auf die **[!UICONTROL Delivery]** Registerkarte.

![](assets/s_ncs_user_wizard_email_param.png)

Im unteren Bereich des Fensters haben Sie die Wahl zwischen:

* **[!UICONTROL Use recipient preferences]** (Standardmodus)

   The message format is defined according to the data stored in the recipient profile and stored by default in the **[!UICONTROL email format]** field (@emailFormat). Falls ein Empfänger Nachrichten in einem bestimmten Format erhalten möchte, werden sie in diesem Format gesendet. Wenn das Feld nicht ausgefüllt ist, wird eine mehrteilige alternative Meldung gesendet (siehe unten).

* **[!UICONTROL Let recipient mail client choose the most appropriate format]**

   Die Nachricht enthält beide Formate: Text und HTML. Das beim Empfänger angezeigte Format hängt von der Konfiguration des E-Mail-Programms ab (Multipart-Alternative).

   >[!CAUTION]
   >
   >Bei dieser Option werden beide Versionen des Dokuments gesendet. Der hierdurch erhöhte Kapazitätsverbrauch kann den Versanddurchsatz beeinträchtigen.

* **[!UICONTROL Send all messages in text format]**

   Die Nachricht wird im Textformat gesendet. Das HTML-Format wird nicht gesendet, sondern nur für die Mirrorseite verwendet, auf die ein Empfänger gelangt, wenn er auf den entsprechenden Link in der Nachricht klickt.

## Definieren interaktiver Inhalte {#amp-for-email-format}

Mit Adobe Campaign können Sie das neue interaktive [AMP für E-Mail](https://amp.dev/about/email/) -Format ausprobieren, das das Senden dynamischer E-Mails unter bestimmten Bedingungen ermöglicht.

Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../delivery/using/defining-interactive-content.md).

## Inhaltsverwaltung (Content Management){#using-content-management}

Sie können den Inhalt der Bereitstellung mithilfe der Inhaltsverwaltungsformulare direkt im Bereitstellungsassistenten definieren. Zu diesem Zweck müssen Sie auf der Registerkarte der Bereitstellungseigenschaften auf die Veröffentlichungsvorlage des zu verwendenden Inhaltsmanagements verweisen **[!UICONTROL Advanced]** .

![](assets/s_ncs_content_in_delivery.png)

Ein zusätzlicher Tab erlaubt nun die Erstellung eines Inhalts, der automatisch den Regeln des Content Managements entsprechend formatiert und integriert wird.

![](assets/s_ncs_content_in_delivery_edition_tab.png)

>[!NOTE]
>
>For further information about content management in Adobe Campaign, refer to [this section](../../delivery/using/about-content-management.md).

## Bilder hinzufügen {#adding-images}

E-Mail-Zustellungen im HTML-Format können Bilder enthalten. From the delivery wizard, you can import an HTML page containing images or insert images directly using the HTML editor via the **[!UICONTROL Image]** icon.

Diese Bilder können:

* lokal gespeichert sein oder von einem Server abgerufen werden;
* aus der Bibliothek der öffentlichen Ressourcen in Adobe Campaign stammen;

   Öffentliche Ressourcen können über den **[!UICONTROL Resources > Online]** Knoten der Adobe Campaign-Hierarchie aufgerufen werden. Sie sind in einer Bibliothek gruppiert und können in E-Mail-Nachrichten eingeschlossen werden, können aber auch für Kampagnen, Aufgaben oder für die Inhaltsverwaltung verwendet werden.

* Weiterführende Informationen zu freigegebenen Assets in Adobe Experience Cloud finden Sie in [diesem Abschnitt](../../integrations/using/sharing-assets-with-adobe-experience-cloud.md).

>[!CAUTION]
>
>Um E-Mails über den Versand-Assistenten mit Bildern zu versehen, muss die Konfiguration der Adobe-Campaign-Instanz die Verwaltung öffentlicher Ressourcen zulassen. Dies wird im Softwareverteilungs-Assistenten festgelegt. In [diesem Abschnitt](../../installation/using/deploying-an-instance.md) finden Sie weiterführende Hinweise zur Konfiguration.

Mit dem Auslieferungsassistenten können Sie lokale Bilder oder Bilder, die in der Bibliothek gespeichert sind, zum Inhalt von Nachrichten hinzufügen. Klicken Sie dazu in der Symbolleiste für HTML-Inhalt auf die **[!UICONTROL Image]** Schaltfläche .

![](assets/s_ncs_user_image_from_library.png)

Um von den Empfängern gesehen werden zu können, müssen die Bilder auf einem extern zugänglichen Server gespeichert werden.

To manage images via the delivery wizard, you must click the **[!UICONTROL Tracking & Images]** icon in the toolbar.

![](assets/s_ncs_user_email_del_img_param.png)

Wählen Sie **[!UICONTROL Upload images]** auf der **[!UICONTROL Images]** Registerkarte aus. Sie können dann auswählen, ob die Bilder in die E-Mail-Nachricht aufgenommen werden sollen.

![](assets/s_ncs_user_email_del_img_upload.png)

* Sie können Bilder manuell hochladen, ohne auf die Auslieferungsanalyse zu warten. To do this, click the **[!UICONTROL Upload images now]** link.
* Sie können einen anderen Pfad für den Zugriff auf die Bilder auf dem Tracking-Server angeben. Geben Sie zu diesem Zweck die Datei in das **[!UICONTROL Image URL]** Feld ein. Dieser Wert setzt den in den Parametern des Installationsassistenten definierten Wert außer Kraft.

Wenn Sie im Versand-Assistenten einen HTML-Inhalt öffnen, der Bilder mit relativen Pfadnamen enthält, wird Ihnen je nach Versandparametern vorgeschlagen, die Bilder sofort online zu stellen.

![](assets/s_ncs_user_email_del_img_local.png)

>[!CAUTION]
>
>Die Bildpfade werden entweder durch manuelles Online-Stellen der Bilder oder beim Senden der Nachrichten geändert.

**Beispiel: Versand einer Nachricht mit Bildern{#example--sending-a-message-with-images}**

Es soll folgende Versandnachricht mit vier Bildern erstellt werden:

![](assets/s_ncs_user_images_in_delivery_wiz_1.png)

These images come from a local directory or Web site as you can verify from the **[!UICONTROL Source]** tab.

![](assets/s_ncs_user_images_in_delivery_wiz_2.png)

Click the **[!UICONTROL Tracking & Images]** icon and then the **[!UICONTROL Images]** tab to start detecting images in the message.

Für jedes erkannte Bild können Sie den Status prüfen:

* If an image is stored locally or located on another server, even if this server is visible from the outside (on an internet site, for example), it will be detected as **[!UICONTROL Not yet online]**.
* The images are detected as **[!UICONTROL Already online]** if they were uploaded earlier while creating another delivery.
* In the deployment wizard, you can define URLs for which image detection is not enabled: uploading these images will be **[!UICONTROL Skipped]**.

>[!NOTE]
>
>Images are identified by their content and not by their access paths. This means that an image uploaded previously under a different name or in a different directory will be detected as **[!UICONTROL Already online]**.

Bilder werden im Zuge der Nachrichtenanalyse auf den Server geladen, um von außerhalb zugänglich zu sein. Dies gilt nicht für lokal gespeicherte Bilder, die im Vorfeld hochzuladen sind.

Sie können die Vorbereitungen vorantreiben und Bilder hochladen, damit sie von anderen Adobe Campaign-Operatoren angezeigt werden können. Dies kann hilfreich sein, wenn Sie zusammenarbeiten. Klicken Sie dazu auf , **[!UICONTROL Upload the images straightaway...]** um die Bilder auf den Server hochzuladen.

![](assets/s_ncs_user_images_in_delivery_wiz_3.png)

>[!NOTE]
>
>Dies löst die Änderung der Bild-URLs und insbesondere der Namen der Bilder aus.

Once the images are online, you can view changes to their names and paths from the **[!UICONTROL Source]** tab of the message.

![](assets/s_ncs_user_images_in_delivery_wiz_4.png)

Wenn Sie **[!UICONTROL Include the images in the email]** diese Option wählen, können Sie festlegen, welche Bilder in die entsprechende Spalte aufgenommen werden sollen.

![](assets/s_ncs_user_images_in_delivery_wiz_5.png)

>[!NOTE]
>
>Wenn in der Nachricht lokale Bilder enthalten sind, ist die Änderung des Quellcodes der Nachricht zu bestätigen.

## Barcode in eine E-Mail einfügen{#inserting-a-barcode-in-an-email}

Die Barcode-Lösung bietet die Möglichkeit, verschiedene ein- oder zweidimensionale Code-Typen in den gängigsten Normen zu erstellen.

Barcodes können in Form eines Bitmaps dynamisch mithilfe eines durch Kundenkriterien definierten Werts erzeugt werden. Personalisierte Barcodes lassen sich dann über E-Mails in Marketingkampagnen integrieren. Der Empfänger kann die Nachricht ausdrucken und sie dem Unternehmen (z. B. bei einem Zahlvorgang) zum Scannen vorlegen.

To insert a barcode into an email, place the cursor in the content where you want to display it, then click the personalization button. Select **[!UICONTROL Include > Barcode...]**.

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
1. Mit dem **[!UICONTROL Value]** Feld können Sie den Wert des Barcodes definieren. Ein Wert kann mit einem bestimmten Angebot übereinstimmen und die Funktion eines Kriteriums sein. Es kann sich dabei um den Wert eines Datenbankfelds handeln, das mit den Kunden verknüpft ist.

   Dieses Beispiel zeigt einen EAN-8-Barcode, dem die Kontonummer eines Empfängers hinzugefügt wurde. Um diese Kontonummer hinzuzufügen, klicken Sie auf die Personalisierungsschaltfläche rechts neben dem **[!UICONTROL Value]** Feld und wählen Sie **[!UICONTROL Recipient > Account number]**.

   ![](assets/barcode_insert_15.png)

1. The **[!UICONTROL Height]** field lets you configure the height of the barcode without changing its width, by altering the amount of space between each bar.

   Bitte beachten Sie, dass keine einschränkende Kontrolle Ihrer Eingaben in Bezug auf den Barcode-Typ erfolgt. Sollte ein falscher oder nicht kompatibler Wert eingegeben werden, sehen Sie dies erst in der **Vorschau**. In diesem Fall ist der Barcode rot durchkreuzt.

   >[!NOTE]
   >
   >Der einem Barcode zugeteilte Wert ist vom Typ abhängig. So muss beispielsweise ein EAN-8-Barcode genau acht Ziffern enthalten.
   >
   >Mit der Personalisierungsschaltfläche rechts neben dem **[!UICONTROL Value]** Feld können Sie zusätzlich zu dem Wert selbst Daten hinzufügen. Dadurch wird der Barcode angereichert, sofern er vom Barcode-Standard akzeptiert wird.
   >
   >For example, if you are using a GS1-128 type barcode and want to enter the account number of a recipient in addition to the value, click the personalization button and select **[!UICONTROL Recipient > Account number]**. If the account number of the selected recipient is entered correctly, the barcode takes it into account.

Nachdem diese Elemente konfiguriert wurden, können Sie Ihre E-Mail abschließen und senden. Um Fehler zu vermeiden, sollten Sie stets sicherstellen, dass Ihr Inhalt korrekt angezeigt wird, bevor Sie eine Bereitstellung durchführen, indem Sie auf die **[!UICONTROL Preview]** Registerkarte klicken.

![](assets/barcode_insert_10.png)

>[!NOTE]
>
>Sollte ein Barcode-Wert sich als ungültig erweisen, erscheint das entsprechende Bild in der Vorschau rot durchkreuzt.

![](assets/barcode_insert_11.png)

## E-Mail-Versand auf japanische Mobiltelefone {#sending-emails-on-japanese-mobiles}

### E-Mail-Formate für japanische Mobiltelefone {#email-formats-for-japanese-mobiles}

Adobe Campaign unterstützt drei spezifische Formate für E-Mails auf japanischen Mobiltelefonen für den japanischen Markt: **Deco-mail** (DoCoMo Mobiltelefone), **Decore Mail** (Softbank Mobiltelefone) und **Decoration Mail** (KDDI AU Mobiltelefone). Diese Formate unterliegen verschiedenen Einschränkungen hinsichtlich Kodierung, Struktur und Größe. Weiterführende Informationen zu Einschränkungen und Empfehlungen finden Sie in [diesem Abschnitt](#limitations-and-recommendations).

In order for the recipient to correctly receive messages in one of these formats, we recommend selecting **[!UICONTROL Deco-mail (DoCoMo)]**, **[!UICONTROL Decore Mail (Softbank)]** or **[!UICONTROL Decoration Mail (KDDI AU)]** in the corresponding profile:

![](assets/deco-mail_03.png)

However, if you leave the **[!UICONTROL Email format]** option as **[!UICONTROL Unknown]**, **[!UICONTROL HTML]** or **[!UICONTROL Text]**, Adobe Campaign will automatically detect (when sending the email) the Japanese format to use so that the message is correctly displayed.

Dieses automatische Erkennungssystem basiert auf der Liste vordefinierter Domänen, die im **[!UICONTROL Management of Email Formats]** E-Mail-Regelsatz definiert sind. Weitere Informationen zum Verwalten von E-Mail-Formaten finden Sie auf [dieser Seite](../../installation/using/email-deliverability.md#managing-email-formats).

### Einschränkungen und Empfehlungen {#limitations-and-recommendations}

Der E-Mail-Versand an Mobiltelefone unter Vertrag mit japanischen Anbietern (Softbank, DoCoMo, KDDI AU) unterliegt gewissen Einschränkungen.

Aus diesem Grund müssen Sie:

* ausschließlich Bilder im JPEG- oder GIF-Format verwenden;
* einen Versand erstellen, bei dem die Summe aus Text und HTML in keinem Fall 10.000 Bytes übersteigt (für KDDI AU und DoCoMo);
* Bilder verwenden, deren Gesamtgröße vor der Kodierung weniger als 100 KB beträgt;
* in einer Nachricht nicht mehr als 20 Bilder verwenden;
* ein reduziertes HTML-Format verwenden (für jeden Anbieter steht eine begrenzte Anzahl an Tags zur Verfügung).

>[!NOTE]
>
>Bei der Erstellung von Nachrichten sind die für die jeweiligen Anbieter spezifischen Einschränkungen zu berücksichtigen. Weiterführende Informationen dazu finden Sie hier:
>
>* Weiterführende Informationen zu DoCoMo finden Sie auf [dieser Seite](https://www.nttdocomo.co.jp/service/developer/make/content/deco_mail/index.html).
>* Weiterführende Informationen zu KDDI AU finden Sie auf [dieser Seite](https://www.au.com/ezfactory/tec/spec/decorations/template.html).
>* Weiterführende Informationen zu Softbank finden Sie auf [dieser Seite](https://www.support.softbankmobile.co.jp/partner/home_tech3/index.cfm).


### E-Mail-Inhalt testen {#testing-the-email-content}

#### Nachricht in der Vorschau betrachten {#previewing-the-message}

In Adobe Campaign haben Sie die Möglichkeit zu prüfen, ob das Format Ihrer Nachricht dem Versand an japanische Mobiltelefone angepasst ist.

Sobald Sie Ihren Inhalt erstellt und den Betreff der E-Mail angegeben haben, können Sie Anzeige und Formatierung der Nachricht kontrollieren.

Auf der **[!UICONTROL Preview]** Registerkarte des Fensters zur Inhaltsbearbeitung können Sie durch Klicken auf **[!UICONTROL More... > Deco-mail diagnostic]** Folgendes tun:

* prüfen, ob die Tags des HTML-Inhalts den mit dem japanischen Format einhergehenden Einschränkungen entsprechen;
* prüfen, ob die Anzahl an Bildern in der Nachricht nicht die durch das Format vorgegebene Höchstgrenze von maximal 20 Bildern überschreitet;
* prüfen, ob die Gesamtgröße nicht den Grenzwert von 100 KB übersteigt.

   ![](assets/deco-mail_06.png)

#### Typologieregel ausführen {#running-typology-rule}

In addition to the previewing diagnosis, a second check is carried out when sending a proof or a delivery: a specific typology rule, **[!UICONTROL Deco-mail check]**, is started during the analysis.

>[!CAUTION]
>
>This typology rule is only executed if at least one of the recipients is configured to receive emails in **[!UICONTROL Deco-mail (DoCoMo)]**, **[!UICONTROL Decore Mail (Softbank)]** or **[!UICONTROL Decoration Mail (KDDI AU)]** format.

Mithilfe dieser Regel können Sie sich vergewissern, ob bei der Sendung die von den japanischen Anbietern vorgegebenen [Formateinschränkungen](#limitations-and-recommendations) respektiert werden, insbesondere im Hinblick auf die Gesamtgröße der E-Mail, die jeweilige Größe ihrer HTML- und Textanteile, die Anzahl an Bildern in der Nachricht sowie die Tags des HTML-Inhalts.

#### Testversand durchführen {#sending-proofs}

Sie können Testsendungen durchführen, um Ihren Versand zu testen. Wenn Sie dabei Ersatzadressen verwenden, geben Sie bitte die Adressen ein, die dem E-Mail-Format des verwendeten Profils entsprechen.

Beispielsweise können Sie die Adresse eines Profils durch test@softbank.ne.jp ersetzen, wenn das E-Mail-Format für dieses Profil zuvor in **[!UICONTROL Decore Mail (Softbank)]** ) definiert wurde.

![](assets/deco-mail_05.png)

### Nachrichten senden {#sending-messages}

Für den Versand einer E-Mail an Empfänger mit japanischen E-Mail-Formaten mit Campaign haben Sie zwei Möglichkeiten:

* Erstellen Sie zwei Sendungen, eine nur für japanische Empfänger und die andere für alle anderen Empfänger. Weitere Informationen dazu finden Sie in [diesem Abschnitt](#designing-a-specific-delivery-for-japanese-formats).
* Erstellen Sie einen einzigen Versand und Adobe Campaign erkennt das Format automatisch. Weitere Informationen dazu finden Sie in [diesem Abschnitt](#designing-a-delivery-for-all-formats).

#### Spezifischen Versand für japanische Formate erstellen {#designing-a-specific-delivery-for-japanese-formats}

Erstellen Sie einen Workflow mit zwei Sendungen: einen Versand, der für japanische Mobiltelefone bestimmt ist, und einen zweiten für Empfänger mit einem Standard-E-Mail-Format.

To do this, use the **[!UICONTROL Split]** activity in your workflow and define the Japanese email formats (Deco-mail, Decoration Mail and Decore Mail) as filtering conditions.

![](assets/deco-mail_08.png)

![](assets/deco-mail_07.png)

#### Versand für alle Formate erstellen {#designing-a-delivery-for-all-formats}

When Adobe Campaign dynamically manages the formats according to the domain (profiles with email formats defined as **[!UICONTROL Unknown]**, **[!UICONTROL HTML]** or **[!UICONTROL Text]** ), you can send the same delivery to all of your recipients.

Der Nachrichteninhalt wird sowohl für Empfänger mit japanischen Mobiltelefonen als auch für Standardempfänger korrekt angezeigt.

>[!CAUTION]
>
>Beachten Sie die Einschränkungen, denen die verschiedenen japanischen Formate (Deco-mail, Decoration Mail und Decore Mail) unterliegen. Weiterführende Informationen zu Einschränkungen finden Sie in [diesem Abschnitt](#limitations-and-recommendations).
