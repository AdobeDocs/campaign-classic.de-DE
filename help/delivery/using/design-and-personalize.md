---
title: Personalisierte Inhalte erstellen
seo-title: Build personalized content
page-status-flag: never-activated
uuid: a540efc7-105d-4c7f-a2ee-ade4d22b3445
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
discoiquuid: 0cbc4e92-482f-4dac-a1fb-b738e7127938
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c804745ae58a9bded885ac5aef32f019f43e82be
workflow-type: tm+mt
source-wordcount: '1280'
ht-degree: 43%

---


# Build personalized content {#build-personalized-content}

When designing your message content, try to avoid common issues that could prevent you from executing your delivery. Most of the time, possible errors are related to [personalization](../../delivery/using/about-personalization.md), [formatting](../../delivery/using/defining-the-email-content.md#message-content) and [images](../../delivery/using/defining-the-email-content.md#adding-images).

## Optimize personalization {#optimize-personalization}

To avoid common issues that could prevent you from executing your delivery and to improve your recipients&#39; experience, Adobe Campaign enables you to personalize your messages.

Sie können Empfänger-Daten verwenden, die in der Adobe Campaign-Datenbank gespeichert oder über Tracking, Landingpages, Abonnement usw. erfasst werden.
Personalization basics are presented in [this section](../../delivery/using/personalization-fields.md).

Stellen Sie sicher, dass Ihr Nachrichteninhalt korrekt aufgebaut ist, um oft mit der Personalisierung in Verbindung stehende Probleme zu verhindern.

**Tips**: In personalization fields coming from external files provided by third-party vendors, external HTML content can be wrong. To avoid this, check syntax, use of tags, characters, etc. For example, an Adobe Campaign personalization tag always has the following form: &lt;%=table.field%>. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../delivery/using/about-personalization.md).

Die falsche Verwendung von Parametern in Gestaltungsbausteinen kann Probleme verursachen. Variablen in JavaScript sollten beispielsweise folgendermaßen verwendet werden:

    &lt;%
    
    var brand = &quot;xxx&quot;
    
    %>

For more on personalization blocks, refer to the [this section](../../delivery/using/personalization-blocks.md).

You can prepare personalization data in a workflow to improve delivery preparation analysis. This should be used specially if the personalization data come from an external table through Federated Data Access (FDA). This option is described in this [this section](../../delivery/using/personalization-fields.md#optimizing-personalization)

## Build optimized content {#optimize-content}

Beachten Sie beim Erstellen Ihrer E-Mails die folgenden allgemeinen Best Practices.

* Halten Sie das Design einfach

* Denken Sie an Benutzer mit Mobilgeräten

* Vermeiden Sie vollständig bildbasierte E-Mails

* Verwenden Sie E-Mail-sichere Schriftarten

* Kodieren Sie Sonderzeichen

### Betreff

Work on the [subject line](../../delivery/using/defining-the-email-content.md#message-content) to improve open rates:

* Vermeiden Sie einen zu langen Betreff. Verwenden Sie maximal 50 Zeichen

* Vermeiden Sie die wiederholte Verwendung von Wörtern wie „gratis“ oder „Angebot“, die als Spam angesehen werden könnten

* Vermeiden Sie Großbuchstaben und Sonderzeichen wie &quot;!&quot;, &quot;£&quot;, &quot;€&quot;, &quot;$&quot;

### Mirrorseite

Schließen Sie immer einen Link zur Mirrorseite ein. Die bevorzugte Position ist der Anfang der E-Mail. [Mehr dazu](../../delivery/using/sending-messages.md#generating-the-mirror-page)

### Abmelde-Link

The unsubscription link is essential. It must be visible and valid, and the form must be functional. By default, when the message is analyzed, a [typology rule](../../delivery/using/steps-validating-the-delivery.md#validation-process-with-typologies) checks whether an opt-out link has been included and generates a warning if it is missing.

**Tipp**: Da menschliches Versagen immer möglich ist, überprüfen Sie vor jedem Senden, ob der Ausschluss-Link korrekt funktioniert. Achten Sie beispielsweise beim Senden des Testversands darauf, dass der Link gültig ist, dass das Formular online ist und dass das Feld Diesen Empfänger nicht mehr kontaktieren in Ja geändert wird.

Hier erfahren Sie, wie Sie einen Ausschluss-Link [in diesen Abschnitt](../../delivery/using/personalization-blocks.md#personalization-blocks-example)einfügen.

### Größe der E-Mail

To avoid performance or deliverability issues, the recommended maximum size of an email is about **35KB**. To check the message size, go the **[!UICONTROL Preview]** tab and choose a test profile. Nach der Erstellung der Nachricht wird deren Größe in der Ecke rechts oben dargestellt.

Um Ihre E-Mail unter dem Grenzwert zu halten, beachten Sie Folgendes:

* Entfernen redundanter oder nicht verwendeter Stile

* Verschieben eines Teils des E-Mail-Inhalts in eine Landingpage

* Code minimieren

Testen Sie alle Änderungen vor dem endgültigen Senden

### Länge der SMS

Standardmäßig kommt in Bezug auf die maximal zulässige Zeichenanzahl einer SMS der Mobilfunkstandard GSM (Global System for Mobile Communications) zur Anwendung. SMS, die das GSM-Alphabet verwenden, sind auf 160 Zeichen begrenzt oder auf 153 Zeichen pro SMS bei Nachrichten, die in mehreren Teilen gesendet werden.

Transliteration bezeichnet in einer SMS die Ersetzung eines Zeichens durch ein anderes, wenn das ursprüngliche Zeichen nicht von GSM unterstützt wird. Die Verwendung von Personalisierungsfeldern im SMS-Inhalt führt u. U. dazu, dass nicht von GSM unterstützte Zeichen eingefügt werden. Sie können die Transliteration von Zeichen zulassen, indem Sie die entsprechende Option im Tab mit den Parametern des SMPP-Kanals des entsprechenden **[!UICONTROL externen Kontos]** aktivieren.
Learn more [in this section](../../delivery/using/sms-channel.md#creating-an-smpp-external-account).

**Tipps**:

* Aktivieren Sie die Transliteration nicht, wenn Sie alle Zeichen Ihrer SMS beibehalten möchten, um beispielsweise Eigennamen unverändert zu übermitteln.

* Sollte Ihre SMS jedoch eine hohe Anzahl an Zeichen enthalten, die vom GSM-Standard nicht unterstützt werden, aktivieren Sie die Transliteration, um Ihre Versandkosten zu begrenzen.

Learn more [in this section](../../delivery/using/sms-channel.md#about-character-transliteration).

## Überprüfen der Formatierung {#formatting}

Um häufige Formatierungsfehler zu vermeiden, prüfen Sie folgende Elemente:

* Richtige **Datumsformatierung**: Adobe Campaign bietet Funktionen zur Datumsformatierung für die JavaScript-Vorlagen und XSL-Stylesheets. [Mehr dazu](../../delivery/using/formatting.md#date-display)

* Verwendung **autorisierter Zeichen** in E-Mails: Die Liste der gültigen Zeichen für E-Mail-Adressen wird in der Option &quot;XtkEmail_Characters&quot;definiert. Hier erfahren Sie, wie Sie auf die Optionen [in der Kampagne zugreifen können](../../installation/using/configuring-campaign-options.md). Um Sonderzeichen korrekt handhaben zu können, muss Adobe Campaign in Unicode installiert sein.

* Konfiguration der **E-Mail-Authentifizierung**: Stellen Sie sicher, dass die E-Mail-Kopfzeilen die DKIM-Signatur enthalten. Mit der DKIM-Authentifizierung (Domain Keys Identified Mail) kann der Empfänger-E-Mail-Server überprüfen, ob eine Nachricht tatsächlich von der Person oder Organisation gesendet wurde, von der er behauptet, sie wurde gesendet, und ob der Inhalt der Nachricht zwischen dem Zeitpunkt des ursprünglichen Versands (und dem &quot;Signieren&quot; von DKIM) und dem Zeitpunkt des Eingangs geändert wurde. Dieser Standard verwendet in der Regel die Domäne im Header &quot;Von&quot;oder &quot;Absender&quot;. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../delivery/using/technical-recommendations.md#dkim).

### Responsive E-Mail-Design

Responsives E-Mail-Design stellt sicher, dass eine auf jedem Gerät optimal angezeigt wird.

* Verwenden Sie responsive E-Mail-HTML anstelle von Web-HTML

* Verwenden Sie den Vorschaumodus und Testsendungen, um das Rendering auf möglichst vielen Geräten zu testen

* The Adobe Campaign Classic Digital Content Editor (DCE) module includes some responsive design formatted templates for mobile available via **[!UICONTROL Resources]** > **[!UICONTROL Templates]** > **[!UICONTROL Content templates]**. Weitere Informationen [in diesem Artikel](https://theblog.adobe.com/responsive-email-design-101/)

## Verwalten von Bildern {#manage-images}

Befolgen Sie bei der Verwendung von Bildern die unten stehenden Richtlinien.

### Blockieren von Bildern verhindern

Manche E-Mail-Clients blockieren Bilder standardmäßig. Einstellungen können aber auch vom Benutzer so konfiguriert werden, dass Bilder blockiert werden, um den Datenverbrauch zu reduzieren. Wenn also keine Bilder heruntergeladen werden, kann die gesamte Nachricht verloren gehen. Um dies zu vermeiden:

* Achten Sie auf eine ausgewogene Mischung aus Bild und Text. Vermeiden Sie vollständig bildbasierte E-Mails.

* Wenn in einem Bild Text enthalten sein muss, verwenden Sie „alt“ (formatierten Alternativtext) oder „title text“ (Titeltext), um die Botschaft richtig zu übermitteln. Gestalten Sie „alt“/„title text“, um sein Erscheinungsbild zu verbessern.

* Vermeiden Sie eine Verwendung von Hintergrundbildern, da diese von einigen E-Mail-Clients nicht unterstützt werden.

### Bilder reaktionsfähig machen

Verwenden Sie responsive, in der Größe veränderbare Bilder. Beachten Sie, dass sich dies auf die Kosten auswirken kann, da die Erstellung länger dauert.

### Absolute Bildreferenzen verwenden

Um von außen darauf zugreifen zu können, müssen die in E-Mails verwendeten Bilder und öffentliche Ressourcen, die mit Kampagnen verknüpft sind, auf einem extern zugänglichen Server vorhanden sein.

* Sie können prüfen, ob die Instanzkonfiguration die öffentliche Ressource-Verwaltung aktiviert. [Mehr dazu](../../installation/using/deploying-an-instance.md#managing-public-resources)

* From the delivery wizard, you can import an HTML page containing images or insert images directly using the HTML editor via the **[!UICONTROL Image]** icon. [Mehr dazu](../../delivery/using/defining-the-email-content.md#adding-images)

* Wenn keine Bilder dargestellt werden, prüfen Sie, ob die Bilder auf dem Server verfügbar sind. Klicken Sie dazu in Ihrem Versand auf den Tab Quelle. Suchen Sie Ihre Bilder und kopieren Sie die URL eines jeden Bildes in einen Web-Browser. Wenn die Bilder nicht dargestellt werden, kontaktieren Sie Ihren IT-Administrator oder den Drittanbieter, der Ihnen den Versandinhalt bereitgestellt hat.

## Sehen Sie sich Ihre Nachricht in der Vorschau an {#preview-msg}

Adobe empfiehlt, eine Vorschau Ihrer Nachricht anzuzeigen, um deren Personalisierung und die Anzeige Ihres Versands durch Ihre Empfänger zu überprüfen.

* Im Versand-Wazard können Sie auf der Unterregisterkarte &quot; **[!UICONTROL Vorschau]** &quot;die Wiedergabe der einzelnen Inhalte für einen Empfänger Ansicht haben. Die Personalisierungsfelder und bedingten Inhaltselemente werden durch die entsprechenden Informationen für das ausgewählte Profil ersetzt. [Mehr dazu](../../delivery/using/defining-the-email-content.md#message-content)

* Die Vorschauerzeugung löst automatisch die Durchführung einer Anti-Spam-Prüfung aus. Überprüfen Sie auf der Unterregisterkarte **[!UICONTROL Vorschau]** den Spam- [Assassin](../../delivery/using/spamassassin.md) -Scoring.  Klicken Sie auf **[!UICONTROL Mehr...]** um mehr über die Warnung zu erfahren.  Vergewissern Sie sich zuvor, dass SpamAssassin auf dem Adobe Campaign-Anwendungsserver korrekt installiert und konfiguriert ist. [Mehr dazu](../../installation/using/configuring-spamassassin.md)
