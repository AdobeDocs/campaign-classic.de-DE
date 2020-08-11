---
title: Versand der Nachricht optimieren
seo-title: Optimize message delivery
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
source-git-commit: 5e6ecd636ee0b2199808c03b2fd898a194f0c1ea
workflow-type: tm+mt
source-wordcount: '749'
ht-degree: 50%

---


# Versand optimieren {#optimize-delivery}

Bevor Sie mit dem Erstellen von Sendungen beginnen, können Sie mehrere Maßnahmen treffen, um den vorgelagerten Versandprozess zu optimieren.

Im folgenden Abschnitt werden Best Practices und empfohlene Verfahren für die optimale Konfiguration von Adobe Campaign erläutert. Durch die Einhaltung dieser Empfehlungen vermeiden Sie mögliche Probleme später im Prozess.

## Leistung der Plattform

Mehrere Faktoren können die Server-Leistung direkt beeinflussen und die Plattform verlangsamen:

* The number and type of personalization elements: personalization in emails pulls data out of the database for each recipient. Bei vielen Personalisierungselementen erhöht sich dadurch die Datenmenge, die zur Vorbereitung des Versands benötigt wird.  Learn more about personalization in [this section](../../delivery/using/about-personalization.md)

* Laden des Servers: Wenn der Marketingserver viele verschiedene Aufgaben gleichzeitig verarbeitet, kann dies die Leistung verlangsamen. Der Marketingserver muss alle eingehenden und ausgehenden Daten für alle Versand koordinieren, um sicherzustellen, dass die Daten korrekt und pünktlich sind.

   **TIPP** - Um dies zu vermeiden, koordinieren Sie die Planung der Versand mit den anderen Teammitgliedern, um die beste Leistung zu gewährleisten.

* Workflow-Ausführung: Die Überwachung Ihrer Workflows ist unverzichtbar, um Probleme mit der Plattformleistung zu vermeiden. Befolgen Sie die [in diesem Dokument](../../workflow/using/workflow-best-practices.md#execution-and-performance)aufgeführten Richtlinien.

* Als gehosteter Kunde können Sie mithilfe der Funktionen der [Kampagne Control Panel-Funktion](https://docs.adobe.com/content/help/de-DE/control-panel/using/discover-control-panel/key-features.html) Ihre Plattform überwachen und dabei die [Leistungsüberwachung](https://docs.adobe.com/content/help/en/control-panel/using/performance-monitoring/about-performance-monitoring.html) nutzen.

## Prüfen der Netzwerkkonfiguration {#network-config}

Um den Versand großer Mengen von E-Mails zu optimieren und zu verhindern, dass Sie für einen Spammer gehalten werden, achten Sie auf eine ordnungsgemäße Netzwerkkonfiguration, mit der nicht versucht wird, die Identität des Servers zu verbergen.

**Tipp**:  Verwenden Sie eine transparente Absenderadresse, die der Website Ihrer Marke entspricht. Die TravelAgency-Firma verwaltet beispielsweise die Hotelkette Valentino. Für seine Website verwendet es die Domain valentino.com. Um das Valentino-Hotel in Paris zu bewerben, verwendet es die Subdomain paris.valentino.com. Eine entsprechende Absenderadresse könnte deshalb hotel@paris.valentino.com lauten.

## Verwaltung der Zustellbarkeit {#deliverability-management}

Sie müssen die Zustellbarkeitsrate Ihrer Nachrichten steigern, damit Ihre Nachrichten in die Empfängerpostfächer zugestellt und nicht als unzustellbar zurückgesendet oder als Spam gekennzeichnet werden.

* Was ist Lieferbarkeit?

   * Es bezieht sich auf die Faktoren einer E-Mail, die bestimmen, ob sie vom Server des Empfängers akzeptiert werden kann. ISPs (Internet-Dienstleister) filtern E-Mails, die sie als SPAM identifizieren, oder blockieren das Herunterladen von Bildern. Wenn sie feststellen, dass eine bestimmte Domäne zu viele E-Mails sendet, legen sie eine Begrenzung für die Anzahl der E-Mails fest, die sie von diesem Absender akzeptieren.

   * Konzentrieren Sie sich bei der Zustellbarkeit Ihrer E-Mail auf vier Hauptkategorien: Datenqualität, Nachricht und Inhalt, Versandinfrastruktur und Reputation. Einen tieferen Tauchgang zu diesem Thema finden Sie in [diesem Abschnitt](../../delivery/using/about-deliverability.md).

* Wenden Sie die [in diesem Dokument](../../delivery/using/deliverability-key-points.md)beschriebenen Empfehlungen an.

* Wenden Sie sich zwecks Hilfe an Ihren Kundenbetreuer.

## Quarantäneverwaltung {#quarantine-management}

Achten Sie in Ihrem eigenen Interesse auf eine gute Quarantäneverwaltung.

Wenn Sie auf einer neuen Plattform erstmals E-Mails versenden, verwenden Sie möglicherweise eine Liste mit fehlerhaften Adressen. Wenn Sie Nachrichten an ungültige Adressen oder an Honeypot-Adressen (Postfächer, die ausschließlich der Täuschung von Spammern dienen) senden, mindert dies die Reputation Ihrer Plattform. Good quarantine management processes help to: maintain address quality, avoid block list by internet access providers, and reduce your error rate, speeding up deliveries and throughput.

**Tipps**

* If you have a list of invalid addresses, Adobe recommends importing it to the quarantine table, through **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]** > **[!UICONTROL Non deliverables and addresses]**.

* Die Empfänger, deren Adressen unter Quarantäne gestellt werden, werden während der Analyse des Versands standardmäßig ausgeschlossen: sie sind nicht zielgerichtet. Dies beschleunigt die Zustellung, da sich die Fehlerrate maßgeblich auf die Zustellgeschwindigkeit auswirkt. Eine E-Mail-Adresse kann zum Beispiel unter Quarantäne gestellt werden, weil das Postfach voll ist oder die Adresse nicht existiert. [Mehr dazu](#identifying-quarantined-addresses-for-a-delivery)

* Adobe Campaign verwaltet falsche Adressen je nach Typ des zurückgegebenen Fehlers. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../delivery/using/understanding-quarantine-management.md).


* Teilweise werden E-Mails von Providern automatisch als Spam eingestuft, wenn die Anzahl ungültiger Adressen zu hoch ist. Durch die Quarantäne können Sie also vermeiden, von diesen Anbietern auf eine Blockierungsliste gesetzt zu werden.

* Die Verwaltung der Quarantänen wird auch dazu beitragen, die Kosten für die SMS-Versendung zu senken, indem falsche Telefonnummern von Versänden ausgeschlossen werden.

## Anmeldemöglichkeit mit doppelter Bestätigung (Double opt-in){#double-opt-in}

Um den Nachrichtenversand an ungültige Adressen zu vermeiden, unnütze Kommunikation zu minimieren und die Reputation des Absenders zu schützen, empfiehlt Adobe die doppelte Anmeldung zur Bestätigung eines Abonnements. Damit können Sie sicherstellen, dass sich ein Empfänger absichtlich angemeldet hat.

Einzelheiten zur Implementierung dieses Mechanismus sind in [diesem Abschnitt](../../web/using/use-cases--web-forms.md)beschrieben.
