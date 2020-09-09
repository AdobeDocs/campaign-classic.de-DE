---
title: Optimieren des Nachrichtenversands
seo-title: Optimieren des Nachrichtenversands
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
translation-type: ht
source-git-commit: 5e6ecd636ee0b2199808c03b2fd898a194f0c1ea
workflow-type: ht
source-wordcount: '749'
ht-degree: 100%

---


# Versand optimieren {#optimize-delivery}

Bevor Sie mit dem Erstellen von Sendungen beginnen, können Sie mehrere Maßnahmen treffen, um den vorgelagerten Versandprozess zu optimieren.

Im folgenden Abschnitt werden Best Practices und empfohlene Verfahren für die optimale Konfiguration von Adobe Campaign erläutert. Durch die Einhaltung dieser Empfehlungen vermeiden Sie mögliche Probleme später im Prozess.

## Leistung der Plattform

Mehrere Faktoren können die Server-Leistung direkt beeinflussen und die Plattform verlangsamen:

* Anzahl und Art der Personalisierungselemente: Durch Personalisierung in E-Mails werden Daten für jeden Empfänger aus der Datenbank abgerufen. Bei vielen Personalisierungselementen erhöht sich dadurch die Datenmenge, die zur Vorbereitung des Versands benötigt wird.  Weiterführende Informationen zur Personalisierung finden Sie in [diesem Abschnitt](../../delivery/using/about-personalization.md).

* Auslastung des Servers: Wenn der Marketing-Server viele verschiedene Aufgaben gleichzeitig ausführt, kann die Leistung verlangsamt werden. Der Marketing-Server muss alle eingehenden und ausgehenden Daten für alle Sendungen koordinieren, um sicherzustellen, dass die Daten korrekt sind und rechtzeitig gesendet werden.

   **Tipp**: Koordinieren Sie die zeitliche Durchführung von Sendungen mit anderen Team-Mitgliedern, um eine optimale Leistung zu gewährleisten.

* Workflow-Ausführung: Die Überwachung Ihrer Workflows ist unverzichtbar, um Probleme mit der Leistung der Plattform zu vermeiden. Befolgen Sie die [in diesem Dokument](../../workflow/using/workflow-best-practices.md#execution-and-performance) aufgeführten Richtlinien.

* Als gehosteter Kunde können Sie die Funktionen des [Campaign Control Panels](https://docs.adobe.com/content/help/de-DE/control-panel/using/discover-control-panel/key-features.html) nutzen, um Ihre Plattform mit Hilfe der [Leistungsüberwachungsfunktionen](https://docs.adobe.com/content/help/de-DE/control-panel/using/performance-monitoring/about-performance-monitoring.html) zu überwachen.

## Prüfen der Netzwerkkonfiguration {#network-config}

Um den Versand großer Mengen von E-Mails zu optimieren und zu verhindern, dass Sie für einen Spammer gehalten werden, achten Sie auf eine ordnungsgemäße Netzwerkkonfiguration, mit der nicht versucht wird, die Identität des Servers zu verbergen.

**Tipp**: Verwenden Sie eine transparente Absenderadresse entsprechend der Website Ihrer Marke. Nehmen wir an, das Unternehmen TravelAgency verwaltet die Hotelkette Valentino. Für seine Website verwendet es die Domain valentino.com. Um das Valentino-Hotel in Paris zu bewerben, verwendet es die Subdomain paris.valentino.com. Eine entsprechende Absenderadresse könnte deshalb hotel@paris.valentino.com lauten.

## Verwaltung der Zustellbarkeit {#deliverability-management}

Sie müssen die Zustellbarkeitsrate Ihrer Nachrichten steigern, damit Ihre Nachrichten in die Empfängerpostfächer zugestellt und nicht als unzustellbar zurückgesendet oder als Spam gekennzeichnet werden.

* Was ist Zustellbarkeit?

   * Sie bezeichnet die Faktoren, die darüber bestimmen, ob eine E-Mail vom Server eines Empfängers akzeptiert wird. ISPs (Internet Service Provider) filtern E-Mails heraus, die sie als Spam erachten, oder verhindern das Herunterladen von Bildern. Wenn sie feststellen, dass von einer Domain zu viele E-Mails gesendet werden, begrenzen sie die Anzahl der von diesem Absender akzeptierten E-Mails.

   * Konzentrieren Sie sich bei der Zustellbarkeit Ihrer E-Mail auf vier Hauptkategorien: Datenqualität, Nachricht und Inhalt, Versandinfrastruktur und Reputation. Detailliertere Informationen zu diesem Thema finden Sie in [diesem Abschnitt](../../delivery/using/about-deliverability.md).

* Wenden Sie die [in diesem Dokument](../../delivery/using/deliverability-key-points.md) beschriebenen Empfehlungen an.

* Setzen Sie sich mit Ihrem Adobe-Support-Mitarbeiter in Verbindung, wenn Sie Hilfe benötigen.

## Quarantäneverwaltung {#quarantine-management}

Achten Sie in Ihrem eigenen Interesse auf eine gute Quarantäneverwaltung.

Wenn Sie auf einer neuen Plattform erstmals E-Mails versenden, verwenden Sie möglicherweise eine Liste mit fehlerhaften Adressen. Wenn Sie Nachrichten an ungültige Adressen oder an Honeypot-Adressen (Postfächer, die ausschließlich der Täuschung von Spammern dienen) senden, mindert dies die Reputation Ihrer Plattform. Mit einer guten Quarantäneverwaltung können Sie die Adressqualität pflegen, verhindern, dass Sie von ISPs auf eine Blockierungsliste gesetzt werden, und Ihre Fehlerrate senken, was den Versand beschleunigt und den Durchsatz erhöht.

**Tipps**

* Adobe empfiehlt den Import ungültiger Adressen in die Quarantänetabelle über **[!UICONTROL Administration]** > **[!UICONTROL Kampagnenverwaltung]** > **[!UICONTROL Unzustellbarkeitsverwaltung]** > **[!UICONTROL Adressen unzustellbarer Sendungen]**.

* Empfänger, deren Adressen sich in Quarantäne befinden, werden zum Zeitpunkt der Versandanalyse standardmäßig ausgeschlossen und fließen somit nicht in die Berechnung der Zielgruppe ein. Dies beschleunigt die Zustellung, da sich die Fehlerrate maßgeblich auf die Zustellgeschwindigkeit auswirkt. Eine E-Mail-Adresse kann zum Beispiel unter Quarantäne gestellt werden, weil das Postfach voll ist oder die Adresse nicht existiert. [Mehr dazu](#identifying-quarantined-addresses-for-a-delivery)

* Adobe Campaign verwaltet fehlerhafte Adressen je nach zurückgegebenem Fehlertyp. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../delivery/using/understanding-quarantine-management.md).


* Teilweise werden E-Mails von Providern automatisch als Spam eingestuft, wenn die Anzahl ungültiger Adressen zu hoch ist. Durch die Quarantäne können Sie also vermeiden, von diesen Anbietern auf eine Blockierungsliste gesetzt zu werden.

* Die Quarantäneverwaltung hilft Ihnen auch, die Kosten des SMS-Versands zu senken, indem fehlerhafte Telefonnummern aus dem Versand ausgeschlossen werden.

## Anmeldemöglichkeit mit doppelter Bestätigung (Double opt-in){#double-opt-in}

Um den Nachrichtenversand an ungültige Adressen zu vermeiden, unnütze Kommunikation zu minimieren und die Reputation des Absenders zu schützen, empfiehlt Adobe die doppelte Anmeldung zur Bestätigung eines Abonnements. Damit können Sie sicherstellen, dass sich ein Empfänger absichtlich angemeldet hat.

Einzelheiten zur Implementierung dieses Mechanismus sind in [diesem Abschnitt](../../web/using/use-cases--web-forms.md) beschrieben.
