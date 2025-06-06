---
product: campaign
title: Erstellen personalisierter Inhalte
description: Erfahren Sie, wie Sie personalisierte Inhalte in Adobe Campaign-Sendungen erstellen
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
feature: Email Design, Personalization
role: User
hide: true
hidefromtoc: true
exl-id: 5bf727d2-83b1-4a99-be25-041eee8d234c
source-git-commit: aa78a51ebea49f98ef7edad7e87a99a680f02b69
workflow-type: tm+mt
source-wordcount: '1298'
ht-degree: 100%

---

# Erstellen personalisierter Inhalte {#build-personalized-content}

Versuchen Sie beim Entwerfen Ihres Nachrichteninhalts gängige Probleme zu vermeiden, die den Versand verhindern könnten. Meist betreffen Fehler die [Personalisierung](about-personalization.md), die [Formatierung](defining-the-email-content.md#message-content) und [Bilder](defining-the-email-content.md#adding-images).

## Optimieren der Personalisierung {#optimize-personalization}

Um allgemeine Probleme bei der Zustellung Ihrer Nachrichten zu verhindern und das Benutzererlebnis zu verbessern, können Sie Ihre Nachrichten in Adobe Campaign personalisieren.

Sie können die Empfängerdaten verwenden, die in der Adobe Campaign-Datenbank gespeichert sind oder mithilfe von Tracking, Landingpages, Abonnements etc. erfasst wurden.
Die Grundlagen der Personalisierung werden in [diesem Abschnitt](personalization-fields.md) dargestellt.

Stellen Sie sicher, dass Ihr Nachrichteninhalt korrekt aufgebaut ist, um oft mit der Personalisierung in Verbindung stehende Probleme zu verhindern.

**Tipps**: Der externe HTML-Inhalt, der in Personalisierungsfeldern bereitgestellt wird und von externen Dateien von Drittanbietern stammt, kann falsch sein. Um das zu vermeiden, prüfen Sie die Syntax, die Verwendung von Tags, Zeichen usw. Ein Adobe Campaign-Personalisierungs-Tag sieht stets wie folgt aus: &lt;%=table.field%>. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](about-personalization.md).

Die falsche Verwendung von Parametern in Gestaltungsbausteinen kann Probleme verursachen. Variablen in JavaScript sollten beispielsweise folgendermaßen verwendet werden:

    &lt;%
    
    var brand = &quot;xxx&quot;
    
    %>

Weitere Informationen zu Gestaltungsbausteinen finden Sie in [diesem Abschnitt](personalization-blocks.md).

Sie können die Personalisierungsdaten in einem Workflow vorbereiten, um die Analyse der Versandvorbereitung zu verbessern. Dies sollte insbesondere dann verwendet werden, wenn die Personalisierungsdaten über Federated Data Access (FDA) aus einer externen Tabelle stammen. Diese Option wird in diesem [Abschnitt beschrieben](personalization-fields.md#optimizing-personalization).

## Erstellen optimierter Inhalte {#optimize-content}

Beachten Sie beim Erstellen Ihrer E-Mails die folgenden allgemeinen Best Practices.

* Halten Sie das Design einfach.

* Denken Sie an Benutzer mit Smartphones und Tablets.

* Vermeiden Sie vollständig bildbasierte E-Mails.

* Verwenden Sie E-Mail-sichere Schriftarten.

* Kodieren Sie Sonderzeichen.

### Betreff

Achten Sie besonders auf den [Betreff](defining-the-email-content.md#message-content), um die Öffnungsraten zu verbessern:

* Vermeiden Sie einen zu langen Betreff. Verwenden Sie maximal 50 Zeichen.

* Vermeiden Sie die wiederholte Verwendung von Wörtern wie „gratis“ oder „Angebot“, die als Spam angesehen werden könnten.

* Vermeiden Sie Großbuchstaben und Sonderzeichen wie „!“, „£“, „€“ oder „$“.

### Mirrorseite

Beziehen Sie stets einen Link zur Mirrorseite ein. Die bevorzugte Position ist am Anfang der E-Mail – [Weitere Informationen](sending-messages.md#generating-the-mirror-page)

### Abmelde-Link

Ein Abmelde-Link muss unbedingt vorhanden sein. Er muss gut sichtbar und gültig sein, und das Formular muss funktionieren. Bei der Analyse einer Nachricht wird standardmäßig durch eine [Typologieregel](steps-validating-the-delivery.md#validation-process-with-typologies) überprüft, ob ein Abmelde-Link vorhanden ist. Ist dies nicht der Fall, wird ein Warnhinweis generiert.

**Tipp**: Da menschliche Fehler immer möglich sind, prüfen Sie vor jedem Versand, ob der Abmelde-Link ordnungsgemäß funktioniert. Achten Sie beispielsweise beim Testversand darauf, dass der Link gültig ist, das Formular online ist und dass sich das Feld „Diese Person nicht mehr kontaktieren“ auf „Ja“ ändert.

[In diesem Abschnitt](personalization-blocks.md#personalization-blocks-example) erfahren Sie, wie man einen Ausschluss-Link einfügt.

### Größe der E-Mail

Um Performance- oder Zustellbarkeitsprobleme zu vermeiden, wird eine E-Mail mit einer maximalen Größe von **35 KB** empfohlen. Um die Nachrichtengröße zu überprüfen, wählen Sie auf der Registerkarte **[!UICONTROL Vorschau]** ein Testprofil aus. Nach der Erstellung der Nachricht wird deren Größe in der Ecke rechts oben dargestellt.

Um Ihre E-Mail unter dem Grenzwert zu halten, beachten Sie Folgendes:

* Entfernen Sie redundante oder nicht verwendete Stile.

* Verschieben Sie einen Teil des E-Mail-Inhalts auf eine Landingpage.

* Minimieren Sie den Code.

Testen Sie alle Änderungen vor dem endgültigen Senden.

### Länge der SMS

Standardmäßig kommt in Bezug auf die maximal zulässige Zeichenanzahl einer SMS der Mobilfunkstandard GSM (Global System for Mobile Communications) zur Anwendung. SMS, die das GSM-Alphabet verwenden, sind auf 160 Zeichen begrenzt oder auf 153 Zeichen pro SMS bei Nachrichten, die in mehreren Teilen gesendet werden.

Die Transliteration besteht darin, ein Zeichen einer SMS durch ein anderes zu ersetzen, wenn dieses Zeichen vom GSM-Standard nicht berücksichtigt wird. Beachten Sie, dass durch das Einfügen von Personalisierungsfeldern in den Inhalt Ihrer SMS-Nachricht Zeichen eingeführt werden können, die von der GSM-Kodierung nicht berücksichtigt werden. Sie können die Transliteration von Zeichen zulassen, indem Sie das entsprechende Kästchen auf der Registerkarte „SMPP-Kanaleinstellungen“ des entsprechenden **[!UICONTROL externen Kontos]** markieren.
Weiterführende Informationen finden Sie [in diesem Abschnitt](sms-set-up.md#creating-an-smpp-external-account).

**Tipps**:

* Aktivieren Sie die Transliteration nicht, wenn Sie alle Zeichen Ihrer SMS beibehalten möchten, um beispielsweise Eigennamen unverändert zu übermitteln.

* Sollte Ihre SMS jedoch eine hohe Anzahl an Zeichen enthalten, die vom GSM-Standard nicht unterstützt werden, aktivieren Sie die Transliteration, um Ihre Versandkosten zu begrenzen.

Weiterführende Informationen finden Sie [in diesem Abschnitt](sms-set-up.md#about-character-transliteration).

## Überprüfen der Formatierung {#formatting}

Um häufige Formatierungsfehler zu vermeiden, prüfen Sie folgende Elemente:

* Richtige **Datumsformatierung**: Adobe Campaign bietet Formatierungsfunktionen für Datumsangaben in JavaScript-Vorlagen und XSL-Stylesheets – [Weitere Informationen](formatting.md#date-display)

* Verwendung **autorisierter Zeichen** in E-Mails: Eine Liste gültiger Zeichen für E-Mail-Adressen finden Sie in der Option „XtkEmail_Characters“. Informationen zum Zugriff auf Campaign-Optionen finden Sie [in diesem Abschnitt](../../installation/using/configuring-campaign-options.md). Um Sonderzeichen richtig zu handhaben, muss Adobe Campaign in Unicode installiert sein.

* Konfiguration der **E-Mail-Authentifizierung**: Achten Sie darauf, dass die E-Mail-Header die DKIM-Signatur enthalten. Durch Authentifizierung per DKIM (Domain Keys Identified Mail) kann der E-Mail-Empfangsserver überprüfen, ob eine Nachricht tatsächlich von der angegebenen Person oder der angegebenen Entität gesendet wurde. Ferner kann festgestellt werden, ob der Nachrichteninhalt zwischen dem Versandzeitpunkt („signiert“ mit DKIM) und dem Empfangszeitpunkt verändert wurde. Bei diesem Standard wird in der Regel die Domain im „Von“- oder „Absender“-Header angegeben. Weitere Informationen finden Sie im [Adobe-Handbuch mit den Best Practices zur Zustellbarkeit](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html?lang=de#authentication).

### Responsives E-Mail-Design

Responsives E-Mail-Design stellt sicher, dass eine E-Mail auf jedem Gerät optimal angezeigt wird.

* Verwenden Sie responsive E-Mail-HTML anstelle von Web-HTML.

* Verwenden Sie den Vorschaumodus und Testsendungen, um das Rendering auf möglichst vielen Geräten zu testen.

* Das DCE-Modul (Digital Content Editor) von Adobe Campaign Classic enthält einige im responsiven Design formatierte Vorlagen. Gehen Sie dazu zu **[!UICONTROL Ressourcen]** > **[!UICONTROL Vorlagen]** > **[!UICONTROL Inhaltsvorlagen]**.

## Verwalten von Bildern {#manage-images}

Befolgen Sie bei der Verwendung von Bildern die unten stehenden Richtlinien.

### Verhindern der Bildblockierung

Manche E-Mail-Clients blockieren Bilder standardmäßig. Einstellungen können aber auch vom Benutzer so konfiguriert werden, dass Bilder blockiert werden, um den Datenverbrauch zu reduzieren. Wenn keine Bilder heruntergeladen werden, kann die gesamte Nachricht verloren gehen. Um dies zu vermeiden:

* Achten Sie auf eine ausgewogene Mischung aus Bild und Text. Vermeiden Sie vollständig bildbasierte E-Mails.

* Wenn in einem Bild Text enthalten sein muss, verwenden Sie „alt“ (formatierten Alternativtext) oder „title text“ (Titeltext), um die Botschaft richtig zu übermitteln. Gestalten Sie „alt“/„title text“, um sein Erscheinungsbild zu verbessern.

* Vermeiden Sie eine Verwendung von Hintergrundbildern, da diese von einigen E-Mail-Clients nicht unterstützt werden.

### Verwenden responsiver Bilder

Verwenden Sie responsive, in der Größe veränderbare Bilder. Beachten Sie, dass sich dies auf die Kosten auswirken kann, da die Erstellung länger dauert.

### Verwenden absoluter Bildreferenzen

Damit Empfänger auf die Bilder zugreifen können, müssen die in E-Mails und öffentlichen Ressourcen verwendeten Bilder, die mit Kampagnen verknüpft sind, auf einem extern zugänglichen Server gespeichert sein.

* Sie können überprüfen, ob durch die Instanzenkonfiguration die Verwaltung öffentlicher Ressourcen ermöglicht wird – [Weitere Informationen](../../installation/using/deploying-an-instance.md#managing-public-resources)

* Sie können eine HTML-Seite mit Bildern über den Versandassistenten importieren oder Bilder direkt mithilfe des HTML-Editors über das **[!UICONTROL Bildsymbol]** einfügen. [Weitere Informationen](defining-the-email-content.md#adding-images)

* Wenn keine Bilder dargestellt werden, prüfen Sie, ob die Bilder auf dem Server verfügbar sind. Klicken Sie dazu in Ihrem Versand auf den Tab „Quelle“. Suchen Sie Ihre Bilder und kopieren Sie die URL eines jeden Bildes in einen Web-Browser. Wenn die Bilder nicht dargestellt werden, kontaktieren Sie Ihren IT-Administrator oder den Drittanbieter, der Ihnen den Versandinhalt bereitgestellt hat.

## Sehen Sie sich Ihre Nachricht in der Vorschau an {#preview-msg}

Adobe empfiehlt eine Vorschau Ihrer Nachricht, um die Personalisierung zu überprüfen und festzustellen, wie Ihre Empfängerinnen und Empfänger den Versand sehen werden.

* Im Versandassistenten können Sie auf der Unterregisterkarte **[!UICONTROL Vorschau]** das Rendering der einzelnen Inhalte für eine Empfängerin oder einen Empfänger anzeigen. Die Personalisierungsfelder und bedingten Inhaltselemente werden durch die entsprechenden Informationen für das ausgewählte Profil ersetzt.  [Weitere Informationen](defining-the-email-content.md#message-content)

* Die Vorschauerzeugung löst automatisch die Durchführung einer Anti-Spam-Prüfung aus. Überprüfen Sie auf der Unterregisterkarte **[!UICONTROL Vorschau]** die Spam-Bewertung von [SpamAssassin](spamassassin.md). Klicken Sie auf **[!UICONTROL Details...]**, um mehr über die Warnung zu erfahren. Stellen Sie zuvor sicher, dass SpamAssassin auf dem Adobe Campaign-Anwendungs-Server ordnungsgemäß installiert und konfiguriert ist – [Weitere Informationen](../../installation/using/configuring-spamassassin.md)
