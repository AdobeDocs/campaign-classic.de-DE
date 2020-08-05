---
title: Best Practices für Kampagne Versand
seo-title: Best Practices beim Versand
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
source-git-commit: 4548eda6f87566398ddf19131b777012cbf8917b
workflow-type: tm+mt
source-wordcount: '4408'
ht-degree: 46%

---


# Best Practices beim Versand {#delivery-best-practices}

Erfahren Sie, welche Best Practices beim Design von Versänden und beim Senden mit Adobe Campaign gelten.

## Versand optimieren {#optimize-delivery}

Bevor Sie mit dem Erstellen von Sendungen beginnen, können Sie mehrere Maßnahmen treffen, um den vorgelagerten Versandprozess zu optimieren.

Im folgenden Abschnitt werden Best Practices und empfohlene Verfahren für die optimale Konfiguration von Adobe Campaign erläutert. Durch die Einhaltung dieser Empfehlungen vermeiden Sie mögliche Probleme später im Prozess.

### Leistung der Plattform

Mehrere Faktoren können die Server-Leistung direkt beeinflussen und die Plattform verlangsamen:

* Anzahl und Typ der Personalisierungselemente: Personalisierung in E-Mails ruft Daten für jeden Empfänger aus der Datenbank ab. Bei vielen Personalisierungselementen erhöht sich dadurch die Datenmenge, die zur Vorbereitung des Versands benötigt wird.  Learn more about personalization in [this section](../../delivery/using/about-personalization.md)

* Laden des Servers: Wenn der Marketingserver viele verschiedene Aufgaben gleichzeitig verarbeitet, kann dies die Leistung verlangsamen. Der Marketingserver muss alle eingehenden und ausgehenden Daten für alle Versand koordinieren, um sicherzustellen, dass die Daten korrekt und pünktlich sind.

   **TIPP** - Um dies zu vermeiden, koordinieren Sie die Planung der Versand mit den anderen Teammitgliedern, um die beste Leistung zu gewährleisten.

* Workflow-Ausführung: Die Überwachung Ihrer Workflows ist unverzichtbar, um Probleme mit der Plattformleistung zu vermeiden. Befolgen Sie die [in diesem Dokument](../../workflow/using/workflow-best-practices.md#execution-and-performance)aufgeführten Richtlinien.

* Als gehosteter Kunde können Sie mithilfe der Funktionen der [Kampagne Control Panel-Funktion](https://docs.adobe.com/content/help/de-DE/control-panel/using/discover-control-panel/key-features.html) Ihre Plattform überwachen und dabei die [Leistungsüberwachung](https://docs.adobe.com/content/help/en/control-panel/using/performance-monitoring/about-performance-monitoring.html) nutzen.

### Prüfen der Netzwerkkonfiguration {#network-config}

Um den Versand großer Mengen von E-Mails zu optimieren und zu verhindern, dass Sie für einen Spammer gehalten werden, achten Sie auf eine ordnungsgemäße Netzwerkkonfiguration, mit der nicht versucht wird, die Identität des Servers zu verbergen.

**Tipp**:  Verwenden Sie eine transparente Absenderadresse, die der Website Ihrer Marke entspricht. Die TravelAgency-Firma verwaltet beispielsweise die Hotelkette Valentino. Für seine Website verwendet es die Domain valentino.com. Um das Valentino-Hotel in Paris zu bewerben, verwendet es die Subdomain paris.valentino.com. Eine entsprechende Absenderadresse könnte deshalb hotel@paris.valentino.com lauten.

### Verwaltung der Zustellbarkeit {#deliverability-management}

Sie müssen die Zustellbarkeitsrate Ihrer Nachrichten steigern, damit Ihre Nachrichten in die Empfängerpostfächer zugestellt und nicht als unzustellbar zurückgesendet oder als Spam gekennzeichnet werden.

* Was ist Lieferbarkeit?

   * Es bezieht sich auf die Faktoren einer E-Mail, die bestimmen, ob sie vom Server des Empfängers akzeptiert werden kann. ISPs (Internet-Dienstleister) filtern E-Mails, die sie als SPAM identifizieren, oder blockieren das Herunterladen von Bildern. Wenn sie feststellen, dass eine bestimmte Domäne zu viele E-Mails sendet, legen sie eine Begrenzung für die Anzahl der E-Mails fest, die sie von diesem Absender akzeptieren.

   * Konzentrieren Sie sich bei der Zustellbarkeit Ihrer E-Mail auf vier Hauptkategorien: Datenqualität, Nachricht und Inhalt, Versandinfrastruktur und Reputation. Einen tieferen Tauchgang zu diesem Thema finden Sie in [diesem Abschnitt](../../delivery/using/about-deliverability.md).

* Wenden Sie die [in diesem Dokument](../../delivery/using/deliverability-key-points.md)beschriebenen Empfehlungen an.

* Wenden Sie sich zwecks Hilfe an Ihren Kundenbetreuer.

### Quarantäneverwaltung {#quarantine-management}

Achten Sie in Ihrem eigenen Interesse auf eine gute Quarantäneverwaltung.

Wenn Sie auf einer neuen Plattform erstmals E-Mails versenden, verwenden Sie möglicherweise eine Liste mit fehlerhaften Adressen. Wenn Sie Nachrichten an ungültige Adressen oder an Honeypot-Adressen (Postfächer, die ausschließlich der Täuschung von Spammern dienen) senden, mindert dies die Reputation Ihrer Plattform. Gute Verwaltungsprozesse für Quarantänen tragen dazu bei, die Adressqualität zu erhalten, die Blockierungsliste durch Internetzugangsanbieter zu vermeiden und die Fehlerquote zu reduzieren, wodurch Versand und Durchsatz schneller werden.

**Tipps**

* If you have a list of invalid addresses, Adobe recommends importing it to the quarantine table, through **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]** > **[!UICONTROL Non deliverables and addresses]**.

* Die Empfänger, deren Adressen unter Quarantäne gestellt werden, werden während der Analyse des Versands standardmäßig ausgeschlossen: sie sind nicht zielgerichtet. Dies beschleunigt die Zustellung, da sich die Fehlerrate maßgeblich auf die Zustellgeschwindigkeit auswirkt. Eine E-Mail-Adresse kann zum Beispiel unter Quarantäne gestellt werden, weil das Postfach voll ist oder die Adresse nicht existiert. [Mehr dazu](#identifying-quarantined-addresses-for-a-delivery)

* Adobe Campaign verwaltet falsche Adressen je nach Typ des zurückgegebenen Fehlers. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../delivery/using/understanding-quarantine-management.md).


* Teilweise werden E-Mails von Providern automatisch als Spam eingestuft, wenn die Anzahl ungültiger Adressen zu hoch ist. Durch die Quarantäne können Sie also vermeiden, von diesen Anbietern auf eine Blockierungsliste gesetzt zu werden.

* Die Verwaltung der Quarantänen wird auch dazu beitragen, die Kosten für die SMS-Versendung zu senken, indem falsche Telefonnummern von Versänden ausgeschlossen werden.

### Anmeldemöglichkeit mit doppelter Bestätigung (Double opt-in){#double-opt-in}

Um den Nachrichtenversand an ungültige Adressen zu vermeiden, unnütze Kommunikation zu minimieren und die Reputation des Absenders zu schützen, empfiehlt Adobe die doppelte Anmeldung zur Bestätigung eines Abonnements. Damit können Sie sicherstellen, dass sich ein Empfänger absichtlich angemeldet hat.

Einzelheiten zur Implementierung dieses Mechanismus sind in [diesem Abschnitt](../../web/using/use-cases--web-forms.md)beschrieben.

## Verwenden von Vorlagen {#use-templates}

Versandvorlagen ermöglichen eine effiziente Nutzung, da sie für die häufigsten Aktivitäten vordefinierte Szenarien enthalten. Mit Vorlagen können Marketing-Experten rasch neue Kampagnen bei minimaler Anpassung bereitstellen.

Learn more about delivery templates in [this section](../../delivery/using/creating-a-delivery-template.md).

### Erste Schritte mit Versandvorlagen {#gs-templates}

A [delivery template](../../delivery/using/creating-a-delivery-template.md) enables you to define once a set of technical and functional properties that suit your needs and that can be reused for future deliveries. Sie können dann bei Bedarf Zeit sparen und Versand standardisieren.

Wenn Sie mehrere Marken in Adobe Campaign verwalten, empfiehlt Adobe die Zuweisung einer Subdomain pro Marke. Eine Bank kann beispielsweise für jede ihrer regionalen Niederlassungen über eine Subdomain verfügen. Wenn eine Bank die Domäne &quot;bluebank.com&quot;besitzt, können ihre Subdomänen @ny.bluebank.com, @ma.bluebank.com, @ca.bluebank.com usw. sein. Mit einer Versandvorlage pro Subdomain können Sie stets die richtigen vorkonfigurierten Parameter für jede Marke verwenden, um Fehler zu verhindern und Zeit zu sparen.

**Tipp**:  Um Konfigurationsfehler in Campaign Standard zu vermeiden, sollten Sie eine native Vorlage mit Duplikat versehen und deren Eigenschaften ändern, anstatt eine neue Vorlage zu erstellen.

### Konfigurieren von Adressen

* Die Angabe der Absenderadresse ist für den E-Mail-Versand zwingend erforderlich.

* Einige ISPs (Internet-Dienstleister) prüfen die Gültigkeit der Absenderadresse, bevor sie Nachrichten annehmen.

* Eine schlecht geformte Adresse kann dazu führen, dass sie vom empfangenden Server abgelehnt wird. Sie müssen sicherstellen, dass eine korrekte Adresse angegeben wird.

* Die Adresse muss die Identität eines Absenders enthalten. Die Domain muss im Besitz des Absenders und auf ihn registriert sein.

* Adobe empfiehlt, E-Mail-Konten zu erstellen, die der Absender- und Antwortadresse entsprechen. Wenden Sie sich diesbezüglich bitte an den Administrator Ihres E-Mail-Programms.

Gehen Sie wie folgt vor, um Adressen in der Benutzeroberfläche der Kampagne zu konfigurieren:

1. In the [delivery template](../../delivery/using/creating-a-delivery-template.md), click the **[!UICONTROL From]** link. Füllen Sie im Fenster **[!UICONTROL Parameter des E-Mail-Headers]** die folgenden Felder aus:

   ![](assets/d_best_practices_email_header.png)

1. Stellen Sie im Feld **[!UICONTROL Sender address]** sicher, dass die Adressdomäne mit der Subdomäne übereinstimmt, die Sie an Adobe delegiert haben. Sie können den Teil ändern, der dem &quot;@&quot; vorausgeht, nicht aber die Domänenadresse.

1. Verwenden Sie im Feld &quot; **[!UICONTROL Von]** &quot;einen Namen, der von den Empfängern leicht identifiziert werden kann, z. B. den Namen Ihrer Marke, um die Öffnungsrate Ihrer Versand zu erhöhen. Um den Empfänger noch besser zu gestalten, können Sie den Namen einer Person hinzufügen, z.B. &quot;Emma von Megastore&quot;.

1. In den Textfeldern **[!UICONTROL Antwort-Adresse]** wird standardmäßig die Adresse des Absenders für Antworten verwendet. Adobe empfiehlt jedoch die Verwendung einer vorhandenen echten Adresse wie der Kundenbetreuung Ihrer Marke. In diesem Fall kann die Kundenunterstützung die Antwort dann bearbeiten, wenn ein Empfänger eine Antwort sendet.

### Einrichten einer Kontrollgruppe

Sobald der Versand durchgeführt wurde, können Sie das Verhalten der ausgeschlossenen Empfänger mit den Empfängern vergleichen, die den Versand erhalten haben. Anschließend können Sie die Effizienz Ihrer Kampagnen messen. Weitere Informationen zu Kontrollgruppen finden Sie [in diesem Abschnitt](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group).

Um eine Kontrollgruppe einzurichten, klicken Sie auf den Link **[!UICONTROL An]** . Wählen Sie im Fenster &quot;Zielgruppe **** auswählen&quot;die Registerkarte &quot; **[!UICONTROL Kontrollgruppe]** &quot;aus. Sie können einen Teil der Zielgruppe extrahieren, z. B. ein 5 %-Zufallsstichprobe.

![](assets/d_best_practices_control_group.png)

### Typologien zur Anwendung von Filtern oder Kontrollregeln

Eine Typologie enthält Regeln, die in der Analysephase vor dem Versand einer Nachricht angewendet werden.

In the **[!UICONTROL Typology]** tab of the template&#39;s properties, change the default typology according to your needs.

Um beispielsweise den ausgehenden Traffic besser zu steuern, können Sie festlegen, welche IP-Adressen verwendet werden können, indem Sie eine Affinität pro Subdomäne definieren und eine Typologie pro Affinität erstellen. Die Affinitäten werden in der Konfigurationsdatei der Instanz definiert. Wenden Sie sich an Ihren Adobe Campaign-Administrator.

For more on typologies, refer to [this section](../../campaign/using/about-campaign-typologies.md).

## Design und Personalisierung {#design-and-personalize}

Versuchen Sie beim Entwerfen des Nachrichteninhalts, gängige Probleme zu vermeiden, die die Ausführung Ihres Versands verhindern könnten. In den meisten Fällen beziehen sich mögliche Fehler auf [Personalisierung](../../delivery/using/about-personalization.md), [Formatierung](../../delivery/using/defining-the-email-content.md#message-content) und [Bilder](../../delivery/using/defining-the-email-content.md#adding-images).

### Optimieren der Personalisierung {#optimize-personalization}

Um häufige Probleme zu vermeiden, die die Ausführung Ihres Versands verhindern könnten, und um die Benutzerfreundlichkeit Ihrer Empfänger zu verbessern, können Sie mit Adobe Campaign Ihre Nachrichten personalisieren.

Sie können Empfänger-Daten verwenden, die in der Adobe Campaign-Datenbank gespeichert oder über Tracking, Landingpages, Abonnement usw. erfasst werden.
Die Grundlagen der Personalisierung werden in [diesem Abschnitt](../../delivery/using/personalization-fields.md)vorgestellt.

Stellen Sie sicher, dass Ihr Nachrichteninhalt korrekt aufgebaut ist, um oft mit der Personalisierung in Verbindung stehende Probleme zu verhindern.

**Tipps**: Bei Personalisierungsfeldern, die von externen Dateien stammen, die von Drittanbietern bereitgestellt werden, kann es vorkommen, dass externe HTML-Inhalte falsch sind. Um dies zu vermeiden, überprüfen Sie die Syntax, die Verwendung von Tags, Zeichen usw. Beispielsweise hat ein Adobe Campaign-Personalisierungs-Tag immer das folgende Formular: &lt;%=table.field%>. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../delivery/using/about-personalization.md).

Die falsche Verwendung von Parametern in Gestaltungsbausteinen kann Probleme verursachen. Variablen in JavaScript sollten beispielsweise folgendermaßen verwendet werden:

    &lt;%
    
    var brand = &quot;xxx&quot;
    
    %>

For more on personalization blocks, refer to the [this section](../../delivery/using/personalization-blocks.md).

Sie können Personalisierungsdaten in einem Arbeitsablauf vorbereiten, um die Analyse zur Vorbereitung von Versänden zu verbessern. Dies sollte besonders dann verwendet werden, wenn die Personalisierungsdaten von einer externen Tabelle über Federated Data Access (FDA) stammen. Diese Option wird in diesem [Abschnitt beschrieben](../../delivery/using/personalization-fields.md#optimizing-personalization)

### Optimierten Inhalt erstellen {#optimize-content}

Beachten Sie beim Erstellen Ihrer E-Mails die folgenden allgemeinen Best Practices.

* Halten Sie das Design einfach

* Denken Sie an Benutzer mit Mobilgeräten

* Vermeiden Sie vollständig bildbasierte E-Mails

* Verwenden Sie E-Mail-sichere Schriftarten

* Kodieren Sie Sonderzeichen

**Betreffzeile** - Arbeiten über die [Betreffzeile](../../delivery/using/defining-the-email-content.md#message-content) zur Verbesserung der offenen Tarife:

* Vermeiden Sie einen zu langen Betreff. Verwenden Sie maximal 50 Zeichen

* Vermeiden Sie die wiederholte Verwendung von Wörtern wie „gratis“ oder „Angebot“, die als Spam angesehen werden könnten

* Vermeiden Sie Großbuchstaben und Sonderzeichen wie &quot;!&quot;, &quot;£&quot;, &quot;€&quot;, &quot;$&quot;

**Mirrorseite** - Fügen Sie immer einen Link zur Mirrorseite hinzu. Die bevorzugte Position ist der Anfang der E-Mail. [Mehr dazu](../../delivery/using/sending-messages.md#generating-the-mirror-page)

**Link** zur Abmeldung - Der Link zur Abmeldung ist unverzichtbar. Es muss sichtbar und gültig sein, und das Formular muss funktionsfähig sein. By default, when the message is analyzed, a [typology rule](../../delivery/using/steps-validating-the-delivery.md#validation-process-with-typologies) checks whether an opt-out link has been included and generates a warning if it is missing.

**Tipp**: Da menschliches Versagen immer möglich ist, überprüfen Sie vor jedem Senden, ob der Ausschluss-Link korrekt funktioniert. Achten Sie beispielsweise beim Senden des Testversands darauf, dass der Link gültig ist, dass das Formular online ist und dass das Feld Diesen Empfänger nicht mehr kontaktieren in Ja geändert wird.

Hier erfahren Sie, wie Sie einen Ausschluss-Link [in diesen Abschnitt](../../delivery/using/personalization-blocks.md#personalization-blocks-example)einfügen.

**E-Mail-Größe** - Um Leistungs- oder Bereitstellungsprobleme zu vermeiden, wird eine E-Mail-Maximalgröße von etwa **35 KB** empfohlen. To check the message size, go the **[!UICONTROL Preview]** tab and choose a test profile. Nach der Erstellung der Nachricht wird deren Größe in der Ecke rechts oben dargestellt.

Um Ihre E-Mail unter dem Grenzwert zu halten, beachten Sie Folgendes:

* Entfernen redundanter oder nicht verwendeter Stile

* Verschieben eines Teils des E-Mail-Inhalts in eine Landingpage

* Code minimieren

Testen Sie alle Änderungen vor dem endgültigen Senden

**Länge der SMS**

Standardmäßig kommt in Bezug auf die maximal zulässige Zeichenanzahl einer SMS der Mobilfunkstandard GSM (Global System for Mobile Communications) zur Anwendung. SMS, die das GSM-Alphabet verwenden, sind auf 160 Zeichen begrenzt oder auf 153 Zeichen pro SMS bei Nachrichten, die in mehreren Teilen gesendet werden.

Transliteration bezeichnet in einer SMS die Ersetzung eines Zeichens durch ein anderes, wenn das ursprüngliche Zeichen nicht von GSM unterstützt wird. Die Verwendung von Personalisierungsfeldern im SMS-Inhalt führt u. U. dazu, dass nicht von GSM unterstützte Zeichen eingefügt werden. Sie können die Transliteration von Zeichen zulassen, indem Sie die entsprechende Option im Tab mit den Parametern des SMPP-Kanals des entsprechenden **[!UICONTROL externen Kontos]** aktivieren.
Learn more [in this section](../../delivery/using/sms-channel.md#creating-an-smpp-external-account).

**Tipps**:

* Aktivieren Sie die Transliteration nicht, wenn Sie alle Zeichen Ihrer SMS beibehalten möchten, um beispielsweise Eigennamen unverändert zu übermitteln.

* Sollte Ihre SMS jedoch eine hohe Anzahl an Zeichen enthalten, die vom GSM-Standard nicht unterstützt werden, aktivieren Sie die Transliteration, um Ihre Versandkosten zu begrenzen.

Learn more [in this section](../../delivery/using/sms-channel.md#about-character-transliteration).

### Überprüfen der Formatierung {#formatting}

Um häufige Formatierungsfehler zu vermeiden, prüfen Sie folgende Elemente:

* Richtige **Datumsformatierung**: Adobe Campaign bietet Funktionen zur Datumsformatierung für die JavaScript-Vorlagen und XSL-Stylesheets. [Mehr dazu](../../delivery/using/formatting.md#date-display)

* Verwendung **autorisierter Zeichen** in E-Mails: Die Liste der gültigen Zeichen für E-Mail-Adressen wird in der Option &quot;XtkEmail_Characters&quot;definiert. Hier erfahren Sie, wie Sie auf die Optionen [in der Kampagne zugreifen können](../../installation/using/configuring-campaign-options.md). Um Sonderzeichen korrekt handhaben zu können, muss Adobe Campaign in Unicode installiert sein.

* Konfiguration der **E-Mail-Authentifizierung**: Stellen Sie sicher, dass die E-Mail-Kopfzeilen die DKIM-Signatur enthalten. Mit der DKIM-Authentifizierung (Domain Keys Identified Mail) kann der Empfänger-E-Mail-Server überprüfen, ob eine Nachricht tatsächlich von der Person oder Organisation gesendet wurde, von der er behauptet, sie wurde gesendet, und ob der Inhalt der Nachricht zwischen dem Zeitpunkt des ursprünglichen Versands (und dem &quot;Signieren&quot; von DKIM) und dem Zeitpunkt des Eingangs geändert wurde. Dieser Standard verwendet in der Regel die Domäne im Header &quot;Von&quot;oder &quot;Absender&quot;. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../delivery/using/technical-recommendations.md#dkim).

* **Responsives E-Mail-Design stellt sicher, dass eine E-Mail auf jedem Gerät optimal angezeigt wird.**

   * Verwenden Sie responsive E-Mail-HTML anstelle von Web-HTML.

   * Verwenden Sie den Vorschaumodus und Testsendungen, um das Rendering auf möglichst vielen Geräten zu testen.

   * The Adobe Campaign Classic Digital Content Editor (DCE) module includes some responsive design formatted templates for mobile available via **[!UICONTROL Resources]** > **[!UICONTROL Templates]** > **[!UICONTROL Content templates]**. Weitere Informationen finden Sie [in diesem Artikel](https://theblog.adobe.com/responsive-email-design-101/).



### Verwalten von Bildern {#manage-images}

Befolgen Sie bei der Verwendung von Bildern die unten stehenden Richtlinien.

* **Blockieren** von Bildern verhindern: Einige E-Mail-Clients blockieren standardmäßig Bilder, andere Benutzer ändern ihre Einstellungen, um Bilder zum Speichern bei der Datenverwendung zu blockieren. Wenn also keine Bilder heruntergeladen werden, kann die gesamte Nachricht verloren gehen. Um dies zu vermeiden:

   * Achten Sie auf eine ausgewogene Mischung aus Bild und Text. Vermeiden Sie vollständig bildbasierte E-Mails.

   * Wenn in einem Bild Text enthalten sein muss, verwenden Sie „alt“ (formatierten Alternativtext) oder „title text“ (Titeltext), um die Botschaft richtig zu übermitteln. Gestalten Sie „alt“/„title text“, um sein Erscheinungsbild zu verbessern.

   * Vermeiden Sie eine Verwendung von Hintergrundbildern, da diese von einigen E-Mail-Clients nicht unterstützt werden.

* **Bilder reaktionsfähig** machen - Versuchen Sie, Bilder reaktionsfähig und anpassbar zu machen. Beachten Sie, dass sich dies auf die Kosten auswirken kann, da die Erstellung länger dauert.

* **Absolute Bildreferenzen** verwenden - Um von außen darauf zugreifen zu können, müssen die in E-Mails verwendeten Bilder und öffentliche Ressourcen, die mit Kampagnen verknüpft sind, auf einem extern zugänglichen Server vorhanden sein.

   * Sie können prüfen, ob die Instanzkonfiguration die öffentliche Ressource-Verwaltung aktiviert. [Mehr dazu](../../installation/using/deploying-an-instance.md#managing-public-resources)

   * From the delivery wizard, you can import an HTML page containing images or insert images directly using the HTML editor via the **[!UICONTROL Image]** icon. [Mehr dazu](../../delivery/using/defining-the-email-content.md#adding-images)

   * Wenn keine Bilder dargestellt werden, prüfen Sie, ob die Bilder auf dem Server verfügbar sind. Klicken Sie dazu in Ihrem Versand auf den Tab Quelle. Suchen Sie Ihre Bilder und kopieren Sie die URL eines jeden Bildes in einen Web-Browser. Wenn die Bilder nicht dargestellt werden, kontaktieren Sie Ihren IT-Administrator oder den Drittanbieter, der Ihnen den Versandinhalt bereitgestellt hat.

### Sehen Sie sich Ihre Nachricht in der Vorschau an {#preview-msg}

Adobe empfiehlt, eine Vorschau Ihrer Nachricht anzuzeigen, um deren Personalisierung und die Anzeige Ihres Versands durch Ihre Empfänger zu überprüfen.

* Im Versand-Wazard können Sie auf der Unterregisterkarte &quot; **[!UICONTROL Vorschau]** &quot;die Wiedergabe der einzelnen Inhalte für einen Empfänger Ansicht haben. Die Personalisierungsfelder und bedingten Inhaltselemente werden durch die entsprechenden Informationen für das ausgewählte Profil ersetzt. [Mehr dazu](../../delivery/using/defining-the-email-content.md#message-content)

* Die Vorschauerzeugung löst automatisch die Durchführung einer Anti-Spam-Prüfung aus. Überprüfen Sie auf der Unterregisterkarte **[!UICONTROL Vorschau]** den Spam- [Assassin](../../delivery/using/spamassassin.md) -Scoring.  Klicken Sie auf **[!UICONTROL Mehr...]** um mehr über die Warnung zu erfahren.  Vergewissern Sie sich zuvor, dass SpamAssassin auf dem Adobe Campaign-Anwendungsserver korrekt installiert und konfiguriert ist. [Mehr dazu](../../installation/using/configuring-spamassassin.md)

## Definieren der richtigen Zielgruppe {#define-the-right-target}

Die Bestimmung der Zielgruppen ist besonders wichtig. Gehen Sie bei der Erstellung Ihrer Kontaktlisten sorgfältig vor, testen Sie Ihre E-Mails in den gängigsten E-Mail-Clients und Mobilgeräten und stellen Sie sicher, dass Ihre Verteilerlisten aktuell sind (und keine unbekannten oder veralteten Adressen enthalten). Sie können auch Testsendungen vornehmen, um einen vollständigen Validierungszyklus durchzuführen.

Weitere Informationen zu Zielgruppen [in diesem Abschnitt](../../delivery/using/steps-defining-the-target-population.md)

### Zielgruppe der richtigen Audience {#target-the-right-audience}

Wenn Ihr Inhalt fertiggestellt ist, müssen Sie sorgfältig auswählen, wer Ihre Nachricht erhalten soll.

Damit Ihr Versand erfolgreich ist, möchten Sie die relevantesten personalisierten Inhalte an die richtigen Empfänger senden. Mit Adobe Campaign können Sie die genaueste Zielgruppe erstellen: Sie können Empfänger nach Alter, lokale Anpassung, Kaufdatum, Link in einem vorherigen Versand usw. auswählen. Mit Adobe Campaign können Sie auch Testergebnisse, Profil, Kontrollgruppen und Testadressen definieren, um sicherzustellen, dass die Zielgruppe korrekt ist.

### Zielgruppen-Mappings {#target-mappings}

In Campaign Classic werden Versandvorlagen standardmäßig als **Empfänger** der Zielgruppe angezeigt. Adobe Campaign Angebot andere Zielgruppen-Mapping für Ihre Versand, die Sie je nach Ihren Bedürfnissen ändern können.

Sie können beispielsweise Besucher, deren Profil über soziale Netzwerke erfasst wurden, oder Besucher, die einen Informationsdienst abonniert haben, bereitstellen.

Diese Zuordnungen werden [in diesem Abschnitt](../../delivery/using/selecting-a-target-mapping.md)dargestellt.

Sie können auch ein benutzerdefiniertes Zielgruppen-Mapping erstellen und verwenden. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../configuration/using/target-mapping.md).

### Externe Empfänger {#external-recipients}

Sie können die Bereitstellung an Empfänger durchführen, die in einer externen Datei gespeichert und nicht in der Datenbank gespeichert sind. Learn more [in this section](../../delivery/using/steps-defining-the-target-population.md#selecting-external-recipients).

### An Ihre Abonnenten senden {#send-to-subscribers}

Um Nachrichten an die Abonnenten eines Newsletters zu senden, können Sie die Abonnenten direkt an den entsprechenden Informationsdienst Zielgruppe. Learn more [in this section](../../delivery/using/managing-subscriptions.md#delivering-to-the-subscribers-of-a-service).


### Testversand-Empfänger und Testadressen {#test-recipients-seed-addresses}

Nutzen Sie Testsendungen, bevor Sie Ihre Nachricht an die Hauptzielgruppe senden.

Stellen Sie sicher, dass Sie die entsprechenden Testversand-Empfänger auswählen, da sie das Formular und den Inhalt der Nachricht überprüfen. Die Schritte zum Definieren der Testversand-Empfänger werden [in diesem Abschnitt](../../delivery/using/steps-defining-the-target-population.md#selecting-the-proof-target)beschrieben.

Testadressen werden zur Zielgruppe von Empfängern verwendet, die nicht den definierten Kriterien für die Zielgruppe entsprechen, um einen Versand zu testen, bevor er an die Haupt-Zielgruppe gesendet wird. Sie werden [in diesem Abschnitt](../../delivery/using/about-seed-addresses.md)vorgestellt.

### Deduplizieren von Adressen {#deduplicate-addresses}

Vermeiden Sie doppelte E-Mail-Adressen, da sich dies auf Ihre Zielgruppe auswirken kann:

* Wenn eine Zielgruppe geteilt wird, kann es vorkommen, dass dieselbe Nachricht öfter als ein Mal gesendet wird.

* Wenn sich ein Empfänger nach dem Erhalt einer Nachricht abmeldet, könnten an sein dupliziertes Profil weiterhin Nachrichten gesendet werden.

Die Deduplizierung von Adressen schützt Ihre Reputation und gewährleistet eine gute Quarantäneverwaltung.

Weitere Informationen finden Sie [in diesem Anwendungsfall](../../workflow/using/deduplication.md#example--identify-the-duplicates-before-a-delivery).


### Index-E-Mail-Adressen {#index-addresses}

Um die Performance der in der Anwendung verwendeten SQL-Abfragen zu optimieren, kann ein Index vom Hauptelement des Datenschemas deklariert werden.

Die Schritte zum Hinzufügen eines Indexes zur E-Mail-Adresse werden [in diesem Abschnitt](../../configuration/using/database-mapping.md#indexed-fields)beschrieben.

## Vor dem Senden alle Prüfungen durchführen {#perform-all-checks}

Wenn Ihre Nachricht fertig ist, prüfen Sie, ob ihr Inhalt auf allen Geräten richtig dargestellt wird, und stellen Sie sicher, dass sie keine Fehler wie falsche Personalisierung oder defekte Links enthält.

Prüfen Sie vor dem Nachrichtenversand außerdem, ob die Parameter und die Konfiguration dem Versand entsprechen.

### Warum Validierung der Schlüssel ist {#validation-is-key}

Bevor Sie einen Versand durchführen, müssen Sie sicherstellen, dass Ihre Empfänger tatsächlich die Nachricht erhalten, die Sie ihnen senden möchten. Zu diesem Zweck müssen Sie den Nachrichteninhalt und die Versandparameter validieren.

Auf diese Weise können Sie mögliche Fehler erkennen und beheben, bevor Sie sie an Ihre Haupt-Zielgruppe senden.

Die Schritte zum Validieren eines Versands werden [in diesem Abschnitt](../../delivery/using/steps-validating-the-delivery.md)beschrieben.

### Inbox Rendering {#inbox-and-email-rendering}

Mit Inbox Rendering können Sie sich eine Vorschau Ihrer Nachrichten in den gängigsten E-Mail-Clients ansehen, Inhalt und Reputation überprüfen und feststellen, wie Empfänger Ihre Nachrichten lesen.

**Tipps**:

* Sie können sich ansehen, wie Nachrichten je nach verwendetem Empfangsmedium (Mobilgeräte, Web-Clients etc.) beim Empfänger dargestellt werden.

* Fähigkeiten zum Inbox Rendering sind entscheidend, um festzustellen, ob Ihre E-Mail-Kampagnen erfolgreich durch die Filter der großen ISPs (Internet Service Providers) und Webmail-Dienste befördert werden. Diese Tools senden vorab eine Kopie einer E-Mail an ein Netzwerk von Test-Posteingängen, damit Sie sehen, wie eine Nachricht in diesen Diensten dargestellt wird. Manche dieser Tools bieten auch Berichte und Code-Korrektur-Möglichkeiten, mit denen Sie Fehler rasch erkennen und beheben und so die Zustellbarkeit verbessern können.

Learn more [in this section](../../delivery/using/inbox-rendering.md).

### Nachrichten in Testsendungen {#proof-messages}

Mit Testsendungen können Sie den Abmelde-Link, die Mirrorseite und andere Links testen, die Nachricht validieren, die Anzeige von Bildern überprüfen, mögliche Fehler erkennen etc. Außerdem können Sie Ihr Design und die Darstellung auf verschiedenen Geräten testen.

Learn more [in this section](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

### Einrichten von A/B-Test-Sendungen {#a-b-testing-deliveries}

Wenn mehrere Versionen von Inhalten für den E-Mail-Versand vorhanden sind, können Sie mithilfe von A/B-Tests feststellen, welche Version die größte Auswirkung auf die Zielkontakte hat.

**Tipps**:

* Senden Sie die unterschiedlichen Versionen an einige Ihrer Empfänger

* Wählen Sie die Version mit der höchsten Erfolgsquote aus und senden Sie sie an die restliche Zielgruppe

Learn more [in this section](../../workflow/using/a-b-testing.md).

### Nachrichtenzustellung überprüfen {#make-sure-your-message-is-delivered}

Optimieren Sie Ihre Möglichkeiten und nutzen Sie die Funktionen von Adobe Campaign Classic, um sicherzustellen, dass Ihre Nachricht tatsächlich bei den entsprechenden Empfängern ankommt.

**Führen Sie einen Validierungsprozess** durch - Sie können einen vollständigen Validierungsprozess definieren, an dem Adobe Campaign-Operatoren und -Gruppen beteiligt sind, um sowohl die Zielgruppe als auch den Inhalt der Nachricht zu validieren. Dadurch wird eine vollständige Überwachung und Kontrolle der verschiedenen Prozesse der Kampagne gewährleistet: Targeting, Inhalt, Budget, Extraktion und Senden eines Testversands. Je nach Berechtigung werden Benutzer benachrichtigt, erhalten Testsendungen und können die Nachricht validieren oder ablehnen. Learn more [in this section](../../campaign/using/marketing-campaign-approval.md#approval-process).

**Schübe** verwenden - Sie können das mit Schüben gesendete Volumen schrittweise erhöhen. Dadurch wird verhindert, dass Ihre Nachrichten als Spam markiert werden oder wenn Sie die Anzahl der Nachrichten pro Tag einschränken möchten. Mit Schüben können Sie Sendungen in mehrere Teilsendungen unterteilen, anstatt große Mengen von Nachrichten gleichzeitig zu senden. Learn more [in this section](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves).

**Nachrichten** mit Priorität - Sie können die Versandbestellung für Ihre Versand festlegen, indem Sie die Prioritätsstufe angeben. Gehen Sie dabei folgendermaßen vor:

1. Bearbeiten Sie die Versandeigenschaften und wählen Sie den Tab **[!UICONTROL Versand]** aus.

1. Bestimmen Sie dann die Dringlichkeit von **[!UICONTROL Sehr niedrig]** bis **[!UICONTROL Sehr hoch]**.

>[!NOTE]
>
>Es ist nicht möglich, die Reihenfolge des Sendens von Nachrichten innerhalb eines Versands zu definieren.

**IP-Affinitäten** einrichten - Zur besseren Steuerung des ausgehenden SMTP-Traffics können Sie Affinitäten verwalten, indem Sie festlegen, welche spezifischen IP-Adressen für jede Affinität verwendet werden können. Damit können Sie die Zustellung von E-Mails auf bestimmte Geräte oder IP-Adressen begrenzen. So können Sie beispielsweise eine Affinität pro Land oder Sub-Domain verwenden. Dann können Sie für jedes Land eine Typologie erstellen und jede Affinität mit der entsprechenden Typologie verbinden.

Sie haben folgende Möglichkeiten:

* Definieren Sie die IP-Affinitäten in der Konfigurationsdatei &quot;serverConf.xml&quot;. [Mehr dazu](../../installation/using/configuring-campaign-server.md#managing-outbound-smtp-traffic-with-affinities)

* Deklarieren Sie für jedes IPAffinity-Element die zu verwendenden IP-Adressen. [Mehr dazu](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use)

* Verwenden Sie in der [Typologie](../../campaign/using/about-campaign-typologies.md) Ihrer Wahl das Feld **[!UICONTROL Verwalten von Affinitäten mit IP-Adressen]** , um Versand mit dem Versand-Server (MTA) zu verknüpfen, der die genannte Affinität verwaltet. [Mehr dazu](../../campaign/using/applying-rules.md#control-outgoing-smtp-traffic).

* Prüfen Sie nach dem Versand der E-Mail den Header, um festzustellen, von welcher IP-Adresse aus der Versand erfolgte. Ihr E-Mail-Administrator ist Ihnen beim Feststellen der Header-Informationen behilflich.

>[!NOTE]
>
>Die meisten dieser Schritte können nur von einem erfahrenen Benutzer ausgeführt werden.

**Typologien** verwenden - Sie können Typologieregeln verwenden, um einen Teil der Zielgruppe aufgrund bestimmter Kriterien auszuschließen. Auf diese Weise werden ein ideal auf Kundenbedürfnisse abgestimmter Nachrichtenversand sowie eine kohärente Unternehmenskommunikation sichergestellt. Beispielsweise können Sie minderjährige Empfänger aus der Zielgruppe Ihres Newsletters herausfiltern. Weitere Informationen finden Sie [in diesem Beispiel](../../campaign/using/filtering-rules.md).

**Vermeiden von Attachments** - Attachments bleiben einer der gängigsten Vektoren für die Verbreitung von Malware, besonders wenn sie als Massenversand gesendet werden. Fügen Sie in die Nachricht einen sicheren Link ein, anstatt ein Dokument anzuhängen. Dadurch wird eine zusätzliche Sicherheitsebene gewährleistet, um eine unbeabsichtigte Weiterverteilung zu verhindern, und die Wahrscheinlichkeit, dass die Nachricht aus Gründen der Nachrichtengröße oder der Sicherheit an den Inbound-E-Mail-Gateways zurückgewiesen wird, wird erheblich verringert.

## Tracken und Beobachten {#track-and-monitor}

Sie haben auf die Senden-Schaltfläche geklickt? Lassen Sie uns sehen, was dann passiert. Nach dem Versand der Nachrichten ermöglicht es Ihnen Adobe Campaign die gesendeten Nachrichten zu verfolgen und festzustellen, wie Ihre Empfänger auf darauf reagieren. Dadurch können Sie den zukünftigen Versand verbessern und Ihre nächsten Kampagnen optimieren.

### Sendungen beobachten {#monitoring-deliveries}

Um Ihre Kampagnen steuern zu können, müssen Sie zunächst sichergehen, dass Ihre Nachricht bei Ihren Empfängern tatsächlich angekommen ist.

Von Kampagne Versand Dashboard aus können Sie die verarbeiteten Meldungen und Versand-Prüfprotokolle überprüfen.
In den Versand-Logs können Sie den Status der Nachrichten feststellen. [Mehr dazu](../../delivery/using/monitoring-a-delivery.md#delivery-dashboard).

Was passiert, wenn die Nachrichten nicht gesendet werden und ihr Status weiterhin **Ausstehend** lautet?

* Der Prozess wartet auf die Verfügbarkeit von Ressourcen. Möglicherweise wurde der MTA noch nicht gestartet.
Überprüfen Sie, ob Ihre mta@instance auf Ihren MTA-Servern gestartet wurden, und Beginn Sie ggf. das MTA-Modul. [Mehr dazu](../../production/using/administration.md).

* Möglicherweise wird für den Versand eine Affinität verwendet, die in der Sendeinstanz noch nicht konfiguriert wurde.
Tipp: Prüfen Sie die Konfiguration der Traffic-Verwaltung (IP-Affinität). Weiterführende Informationen dazu finden Sie im Abschnitt Ausgehenden SMTP-Traffic steuern.

>[!NOTE]
>
>Diese Schritte können nur von einem erfahrenen Benutzer ausgeführt werden.

### Tracking {#tracking-deliveries}

Um das Verhalten Ihrer Empfänger besser zu kennen, können Sie nachverfolgen, wie sie auf einen Versand reagieren: Empfang, Öffnen, Klicks auf Links, Abmeldungen usw. In Campaign Classic werden diese Informationen auf der Registerkarte &quot;Verfolgung&quot;der Empfänger, auf die der Versand abzielt, und auf der Registerkarte &quot;Verfolgung&quot;des Versands angezeigt. In Campaign Standard wird er auf der Registerkarte &quot;Trackinglogs&quot;des Versands angezeigt.

**Tipp**: Die Nachrichtenverfolgung ist standardmäßig aktiviert. Um URLs zu konfigurieren, wählen Sie im unteren Bereich des Versand-Assistenten die Option &quot;URLs anzeigen&quot;. Für jede URL der Nachricht können Sie festlegen, ob die Verfolgung aktiviert werden soll.

Weitere Informationen hierzu finden Sie im Abschnitt [Konfigurieren der Verfolgung](../../delivery/using/how-to-configure-tracked-links.md) und in der Beschreibung der [Trackingindikatoren](../../reporting/using/delivery-reports.md#tracking-indicators) .

### Versandleistung {#delivery-performances}

Um die Geschwindigkeit der Nachrichtenzustellung zu messen, können Sie den Versanddurchsatz kontrollieren. Zur Messung der Versandgeschwindigkeit von Nachrichten werden zwei Kennzahlen herangezogen: Anzahl an gesendeten Nachrichten pro Stunde und die gesendete Datenmenge in Bits pro Sekunde. Weiterführende Informationen dazu finden Sie im Abschnitt [Versanddurchsatz](../../reporting/using/global-reports.md#delivery-throughput).

**Tipps**:

* Bewahren Sie auf der Instanz keine fehlgeschlagenen Sendungen auf, da dadurch temporäre Tabellen gespeichert werden, was wiederum die Leistung beeinträchtigt.

* Entfernen Sie nicht mehr benötigte Sendungen und inaktive Empfänger aus der Datenbank, um eine hohe Qualität der Adressen zu gewährleisten.

* Planen Sie nicht die gleichzeitige Durchführung umfangreicher Sendungen. Beachten Sie, dass es 5 bis 10 Minuten dauern kann, bis die Last gleichmäßig über das System verteilt wurde.

### Fehlerbehebung beim Versand {#delivery-troubleshooting}

Bei Problemen mit Versänden können spezifische Aktionen durchgeführt werden:

* [Probleme mit der Lieferbarkeit](../../production/using/performance-and-throughput-issues.md#deliverability_issues)

* [Probleme mit der Bildanzeige](../../production/using/image-display-issues.md)

* [Leistungsprobleme bei Versänden](../../delivery/using/monitoring-a-delivery.md#performance_issues)

* [Probleme](../../production/using/temporary-files.md) mit temporären Dateien - nur *lokale Kunden*
