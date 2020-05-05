---
title: Häufig gestellte Fragen zum Testen und Senden
seo-title: Nachrichten validieren, senden und tracken
description: Häufig gestellte Fragen zu Campaign Classic
page-status-flag: never-activated
uuid: 3f719ac2-cc26-4fb0-adda-84666c8c38e1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
discoiquuid: 16dbe423-018f-4666-9901-2120a8dc609a
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: 8ef56aa04a3ecc94e9e3dda24562760d6a93739d

---


# Nachrichten validieren, senden und tracken {#validate-send-track}

## Test und Validierung {#test-and-validate-before-sending}

Hier erfahren Sie, wie Sie in Adobe Campaign Tests und Validierungen vor dem Nachrichtenversand durchführen.

### Was ist die Versandanalyse? {#what-is-the-delivery-analysis-}

Im Zuge der Versandanalyse wird die Zielpopulation berechnet und der Versandinhalt vorbereitet. Nach Abschluss der Analyse kann der Versand gestartet werden. In Logs kann überprüft werden, ob alle Verfahren korrekt ablaufen.

[Hier erfahren Sie mehr darüber](../../delivery/using/steps-validating-the-delivery.md).

### Warum sollte ich Testsendungen durchführen? {#why-should-i-create-proofs-}

Adobe empfiehlt dringend einen Testversand, um den Versand durch die Validierungsverantwortlichen zu überprüfen, bevor er an die Hauptzielgruppe gesendet wird. Damit können Inhalt, Personalisierung und Versandparameter geprüft werden.

[Hier erfahren Sie mehr darüber](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof). Sie können sich auch [dieses Video](https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/getting-started/managing-seed-and-proofs.html) ansehen.

### Wie werden Testadressen in Adobe Campaign verwendet? {#how-to-use-seed-addresses-in-adobe-campaign-}

Testadressen ermöglichen den Versand an Empfänger, die nicht den vorliegenden Zielgruppenkriterien entsprechen. Sie können auf Versand- oder Kampagnenebene importiert oder erstellt werden und werden der Zielgruppe hinzugefügt. Bei Briefsendungen werden sie zum Zeitpunkt der Extraktion in das Ausgabedokument geschrieben.

Testadressen bieten folgende Möglichkeiten:

* Fehlende Werte werden durch Empfängerdaten aus der Zielgruppe ersetzt (Zufallsauswahl). So ist es beispielsweise möglich in Testadressen nur die E-Mail-Adresse anzugeben.
* Bei Workflows mit Datamanagement-Funktionen können die im Versand genutzten zusätzlichen Daten auf Ebene der Testadressen angegeben werden, um den entsprechenden Wert zu erzwingen. Auf diese Weise umgeht man die zufällige Wertersetzung.

[Hier erfahren Sie mehr zu Testadressen](../../delivery/using/about-seed-addresses.md).

### Wie kann ich vor dem Versand einen Validierungsprozess einrichten? {#how-can-i-set-up-an-approval-process-before-sending-messages-}

Um eventuelle Konfigurationsfehler zu erkennen, ist es empfehlenswert, Ihre Sendungen einem Validierungszyklus zu unterziehen. Auf diese Weise können Sie den Inhalt wiederholt von Testempfängern prüfen lassen. Schalten Sie nach jeder Änderung einen neuen Testversand, um den Inhalt abschließend validieren zu lassen.

[Hier erfahren Sie mehr darüber](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

### Was ist eine Typologieregel? {#what-is-a-typology-rule-}

Um Konflikte zwischen Kampagnen zu vermeiden oder beispielsweise keinen erhöhten Werbedruck zu erzeugen, testet Adobe Campaign unterschiedliche Zusammenstellungen und Kombinationen von Sendungen. Auf diese Weise werden ein ideal auf Kundenbedürfnisse abgestimmter Nachrichtenversand sowie eine kohärente Unternehmenskommunikation sichergestellt.

[Hier erfahren Sie mehr darüber](../../campaign/using/about-campaign-typologies.md).

## Nachrichten senden {#send-your-messages}

Hier erfahren Sie, wie Sie in Adobe Campaign Nachrichten auf unterschiedlichen Kanälen senden.

### Wie kann ich E-Mails in mehreren Schüben senden? {#how-can-i-send-emails-in-waves-}

Anstatt eine Nachricht an eine große Population zu senden, können Sie [Schübe konfigurieren](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves), um Nachrichten in mehreren Teilen zu senden und dadurch eine gleichmäßige Auslastung der Kapazitäten zu gewährleisten.

### Was sind die wichtigsten Schritte bei der Erstellung einer E-Mail in Campaign? {#which-are-the-key-steps-to-create-an-email-in-campaign-}

Zunächst wird die E-Mail-Nachricht erstellt und validiert und danach gesendet. Sie können zwischen sofortigem Versand an die Hauptzielgruppe und terminiertem Versand zu einem späteren Zeitpunkt wählen. Davor können Sie auch die Zielgruppe schätzen, sofern dies erforderlich ist.

[Hier erfahren Sie mehr darüber](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

### Wie wird ein Versand terminiert? {#how-to-schedule-a-delivery-}

Sie können das Senden der Nachrichten auf einen späteren Zeitpunkt verschieben, um z. B. den Werbedruck auf eine bestimmte Population zu kontrollieren.

[Hier erfahren Sie mehr darüber](../../delivery/using/steps-sending-the-delivery.md#scheduling-the-delivery-sending).

### Kann ich zu E-Mails einen Anhang hinzufügen? {#can-i-add-an-attachment-to-emails-}

Mit Campaign Classic können Sie zu E-Mails personalisierte Anhänge hinzufügen.

[Hier erfahren Sie mehr zu E-Mail-Anhängen](../../delivery/using/attaching-files.md).

## Verfolgen von Nachrichten und Messung ihrer Wirkung {#track-your-messages-and-measure-their-impact}

Hier erfahren Sie, wie Sie nach dem Versand Ihrer Nachrichten mit Adobe Campaign deren Wirkung nachverfolgen und messen können.

### Wie kann ich getrackte Links in einem E-Mail-Versand konfigurieren? {#how-can-i-configure-tracked-links-in-an-email-delivery-}

Sie haben die Möglichkeit, für jeden Versand die Zustellung und Klicks auf enthaltene Links zu verfolgen. Auf diese Weise kann das Verhalten der Nachrichtenempfänger analysiert werden.

Sie können das Tracking für jede in der Nachricht enthaltene URL aktivieren oder deaktivieren, den Link-Titel ändern und Links zu Kategorien zusammenfassen, was beispielsweise für Berichte nützlich ist.

[Hier erfahren Sie mehr](../../delivery/using/about-message-tracking.md) über das Tracken Ihrer Nachrichten in Campaign Classic.

### Wo kann ich auf Versand- und Trackinglogs zugreifen? {#where-can-i-access-delivery-and-tracking-logs-}

[Auf dieser Seite](../../delivery/using/monitoring-a-delivery.md) erfahren Sie, wie Sie Ihre Sendungen verfolgen und das Verhalten der Empfänger erfassen.

### Wo finde ich Versandberichte? {#where-can-i-get-delivery-reports-}

Adobe Campaign verfügt über eine Reihe von Berichten zum Überwachen von Sendungen und zum Tracken Ihrer Nachrichten.

[Hier erfahren Sie mehr zu integrierten Berichten](../../reporting/using/delivery-reports.md).

### Wie qualifiziert und handhabt Adobe Campaign in Quarantäne befindliche Adressen? {#how-does-adobe-campaign-qualify-and-manage-quarantine-addresses-}

Adobe Campaign ermöglicht Ihnen die Verwaltung von Quarantäne-Adressen. Empfänger, deren Adresse in Quarantäne ist, werden standardmäßig zum Zeitpunkt der Versandanalyse ausgeschlossen und fließen somit nicht in die Berechnung der Zielgruppe ein. Eine E-Mail-Adresse kann in Quarantäne kommen, weil z. B. das Postfach voll ist oder die Adresse nicht existiert.

[Hier erfahren Sie mehr zur Quarantäneverwaltung](../../delivery/using/understanding-quarantine-management.md).
