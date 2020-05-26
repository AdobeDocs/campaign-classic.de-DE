---
title: Häufige Fragen zu Workflows
seo-title: Automatisieren von Prozessen und Datenverwaltung mit Workflows
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
translation-type: tm+mt
source-git-commit: b369a17fabc55607fc6751e7909e1a1cb3cd4201
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 100%

---


# Häufige Fragen zu Workflows {#workflows-faq}

Hier erfahren Sie, wie Sie Prozesse und Aufgaben mit Adobe Campaign-Workflows aufeinander abstimmen.

## Was sind die wichtigsten Schritte bei der Erstellung eines Workflows? {#what-are-the-key-steps-to-create-a-workflow-}

[Hier erfahren Sie, wie Sie Ihren ersten Workflow erstellen](../../workflow/using/building-a-workflow.md): Lesen Sie über Konzepte und Best Practices zum Erstellen von Workflows in Campaign.

## Wie kann ich Daten in Campaign importieren? {#how-can-i-import-data-in-campaign-}

[In diesem Abschnitt](../../workflow/using/importing-data.md) erfahren Sie Best Practices für den Import mit einem Campaign-Workflow.

## Kann ich die Ausführung von Workflows überwachen? {#can-i-monitor-workflow-execution-}

Informationen zur Überwachung der Workflow-Ausführung in Campaign [finden Sie auf dieser Seite](../../workflow/using/starting-a-workflow.md).

## Wie kann ich Daten in Campaign mit einem Workflow aktualisieren? {#how-can-i-update-campaign-data-with-a-workflow-}

Sie können die Daten in der Datenbank gebündelt aktualisieren, verbinden und einfügen.

[Hier erfahren Sie mehr darüber](../../workflow/using/update-data.md).

## Wie kann ich Data-Management-Funktionen verwenden? {#how-can-i-leverage-data-management-capabilities-}

In Adobe Campaign können Sie eine Reihe von Aktivitäten nutzen, die mithilfe effizienter und flexibler Tools komplexe Zielgruppenbestimmungen und Anreicherungen ermöglichen. Mit Data-Management-Aktivitäten ist es möglich, eine kohärente und individuelle Kommunikation mit Kontakten zu gewährleisten, indem beispielsweise Informationen zu Verträgen, Abonnements oder Reaktionen auf vorhergehende Sendungen verwendet werden. Das Data Management erlaubt es darüber hinaus, den Lebenszyklus von Daten während der Segmentierungsprozesse zu verfolgen, insbesondere werden:

* Zielbestimmungen vereinfacht, u. a. durch Einschluss von nicht im Datamart modelisierten Daten (Erstellung neuer Tabellen: lokale Ausdehnung auf jeden Zielgruppen-Workflow in Abhängigkeit von seiner Konfiguration);
* Zwischenergebnisse gespeichert und weitergegeben (interessant im Zuge der Zielbestimmung oder der Datenbankadministration);
* Zugriffe auf externe Datenbanken ermöglicht (optional), was die Berücksichtigung heterogener Datenbanken bei Zielbestimmungsprozessen zulässt.

[Hier erfahren Sie mehr](../../workflow/using/targeting-data.md#data-management) zur Erstellung komplexer Zielgruppen und zur Bearbeitung Ihrer Daten durch die Kombination von Data-Management-Workflow-Aktivitäten.

## Kann ich den Versand personalisierter Nachrichten automatisieren? {#can-i-automate-personalized-messages-sending-}

Lesen Sie [dieses Anwendungsbeispiel](../../workflow/using/enriching-data.md) zum Versand personalisierter Nachrichten an Personen entsprechend ihren Punkten in einem Wettbewerb.

## Wie kann ich eine Audience mit einem Workflow in Teilmengen unterteilen? {#how-can-i-split-an-audience-in-subsets-with-a-workflow-}

[In diesem Abschnitt](../../workflow/using/split.md) erfahren Sie, wie Sie eine Zielgruppe in mehrere Teilmengen unterteilen.

## Wie kann ich Empfängerdaten durch eine externe Datei aktualisieren? {#how-can-i-update-recipient-data-from-an-external-file-}

Sie können bestimmte Felder in einer Campaign-Tabelle mit Werten aus einer externen Textdatei aktualisieren.

[Hier erfahren Sie mehr darüber](../../platform/using/importing-data.md#example--enrich-the-values-with-those-of-an-external-file).

## Wie kann ich neue Empfänger identifizieren und ansprechen? {#how-can-i-identify-and-target-new-recipients-}

[In diesem Anwendungsbeispiel](../../workflow/using/using-aggregates.md) wird erklärt, wie Sie mit Aggregaten automatisch die letzten zu einer Datenbank hinzugefügten Empfänger erkennen und ihnen eine Willkommensnachricht senden können.
