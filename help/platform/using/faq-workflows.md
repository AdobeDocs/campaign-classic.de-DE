---
product: campaign
title: Häufige Fragen zu Workflows
description: Häufig gestellte Fragen zu Campaign Classic
feature: Troubleshooting, Workflows
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: 7d1bb3c6-d056-4212-9500-75459a0046fa
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 65%

---

# Häufige Fragen zu Workflows {#workflows-faq}



Hier erfahren Sie, wie Sie Prozesse und Aufgaben mit Adobe Campaign-Workflows aufeinander abstimmen.

## Was sind die wichtigsten Schritte bei der Erstellung eines Workflows? {#what-are-the-key-steps-to-create-a-workflow-}

Wie Sie Ihren ersten Workflow erstellen, erfahren Sie in der [Dokumentation zu Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/build-a-workflow.html?lang=de){target="_blank"}: Lernen Sie Konzepte und Best Practices zum Erstellen von Workflows in Campaign kennen.

## Wie kann ich Daten in Campaign importieren? {#how-can-i-import-data-in-campaign-}

Best Practices zum Importieren von Daten finden Sie in [diesem Abschnitt](../../platform/using/import-export-best-practices.md).

## Kann ich die Ausführung von Workflows überwachen? {#can-i-monitor-workflow-execution-}

Informationen zur Überwachung der Workflow-Ausführung in Campaign finden Sie in der [ zu Campaign v8]&#x200B;(https://experienceleague.adobe.com/docs/campaign/automation/workflows/monitoring-workflows/monitor-workflow-execution
.html){target="_blank"}.

## Wie kann ich Daten in Campaign mit einem Workflow aktualisieren? {#how-can-i-update-campaign-data-with-a-workflow-}

Sie können die Daten in der Datenbank gebündelt aktualisieren, verbinden und einfügen.

Weitere Informationen finden Sie in der [Dokumentation zu Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/update-data.html?lang=de){target="_blank"}.

## Wie kann ich Daten-Management-Funktionen verwenden? {#how-can-i-leverage-data-management-capabilities-}

In Adobe Campaign können Sie eine Reihe von Aktivitäten nutzen, die mithilfe effizienter und flexibler Tools komplexe Zielgruppenbestimmungen und Anreicherungen ermöglichen. Mit Data-Management-Aktivitäten ist es möglich, eine kohärente und individuelle Kommunikation mit Kontakten zu gewährleisten, indem beispielsweise Informationen zu Verträgen, Abonnements oder Reaktionen auf vorhergehende Sendungen verwendet werden. Das Data Management erlaubt es darüber hinaus, den Lebenszyklus von Daten während der Segmentierungsprozesse zu verfolgen, insbesondere werden:

* Zielbestimmungen vereinfacht, u. a. durch Einschluss von nicht im Datamart modelisierten Daten (Erstellung neuer Tabellen: lokale Erweiterung auf jeden Zielgruppen-Workflow in Abhängigkeit von seiner Konfiguration);
* Zwischenergebnisse gespeichert und weitergegeben (interessant im Zuge der Zielbestimmung oder der Datenbankadministration);
* Zugriffe auf externe Datenbanken ermöglicht (optional), was die Berücksichtigung heterogener Datenbanken bei Zielgruppenbestimmungsprozessen zulässt.

In der Dokumentation zu Campaign v8 erfahren Sie, wie Sie komplexe Zielgruppen erstellen und Ihre Daten bearbeiten, indem Sie Workflow[Aktivitäten für das Daten-Management &#x200B;](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/wf-type/targeting-workflows.html?lang=de){target="_blank"}.

## Kann ich den Versand personalisierter Nachrichten automatisieren? {#can-i-automate-personalized-messages-sending-}

Lesen Sie die [Campaign v8-Dokumentation](https://experienceleague.adobe.com/docs/campaign/automation/workflows/use-cases/data-management/enrich-data.html?lang=de){target="_blank"} um zu erfahren, wie Sie je nach den Punkten eines Wettbewerbs personalisierte Nachrichten an Personen senden können.

## Wie kann ich eine Zielgruppe mit einem Workflow in Teilmengen unterteilen? {#how-can-i-split-an-audience-in-subsets-with-a-workflow-}

Wie Sie eine Zielgruppe in mehrere Teilmengen unterteilen, erfahren Sie in der [&#x200B; zu Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/split.html?lang=de){target="_blank"}.

## Wie kann ich Empfängerdaten durch eine externe Datei aktualisieren? {#how-can-i-update-recipient-data-from-an-external-file-}

Sie können bestimmte Felder in einer Campaign-Tabelle mit Werten aus einer externen Textdatei aktualisieren.

[Hier erfahren Sie mehr darüber](../../platform/using/import-operations-samples.md#example--enrich-the-values-with-those-of-an-external-file).

## Wie kann ich neue Empfänger identifizieren und ansprechen? {#how-can-i-identify-and-target-new-recipients-}

Lesen Sie die [Campaign v8-Dokumentation](https://experienceleague.adobe.com/docs/campaign/automation/workflows/use-cases/data-management/using-aggregates.html?lang=de){target="_blank"} um zu erfahren, wie Sie mit Aggregaten automatisch die letzten zu einer Datenbank hinzugefügten Empfänger identifizieren und ihnen eine Willkommensnachricht senden können.
