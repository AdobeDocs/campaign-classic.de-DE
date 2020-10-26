---
title: Die richtige Zielgruppe festlegen
seo-title: Die richtige Zielgruppe festlegen
page-status-flag: never-activated
uuid: a540efc7-105d-4c7f-a2ee-ade4d22b3445
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
discoiquuid: 0cbc4e92-482f-4dac-a1fb-b738e7127938
translation-type: ht
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: ht
source-wordcount: '478'
ht-degree: 100%

---


# Die richtige Zielgruppe festlegen {#define-the-right-audience}

Die Bestimmung der Zielgruppen ist besonders wichtig. Gehen Sie bei der Erstellung Ihrer Kontaktlisten sorgfältig vor, testen Sie Ihre E-Mails in den gängigsten E-Mail-Clients, Smartphones und Tablets und stellen Sie sicher, dass Ihre Verteilerlisten aktuell sind (und keine unbekannten oder veralteten Adressen enthalten). Sie können auch Testsendungen vornehmen, um einen vollständigen Validierungszyklus durchzuführen.

Weiterführende Informationen zu Zielgruppen finden Sie in [diesem Abschnitt](../../delivery/using/steps-defining-the-target-population.md).

## Ansprechen der richtigen Zielgruppe {#target-the-right-audience}

Wenn Ihr Inhalt fertiggestellt ist, müssen Sie sorgfältig auswählen, wer Ihre Nachricht erhalten soll.

Um einen erfolgreichen Versand durchzuführen, müssen Sie möglichst relevanten personalisierten Inhalt an die richtigen Empfänger senden. Mit Adobe Campaign können Sie eine präzise Zielgruppe bestimmen, indem Sie die Empfänger nach Alter, Ort, Einkäufen, Klicks auf frühere Sendungen usw. auswählen. Sie können mit Adobe Campaign auch Testprofile und Kontrollgruppen definieren und Testsendungen durchführen, um sicherzustellen, dass Sie die richtige Zielgruppe erreichen.

## Zielgruppen-Mappings {#target-mappings}

Standardmäßig werden bei Campaign Classic mit Versandvorlagen **Empfänger** angesprochen. Adobe Campaign ermöglicht aber auch andere Zielgruppen-Mappings für Ihre Sendungen, die Sie entsprechend Ihren Anforderungen anpassen können.

So können Sie beispielsweise Nachrichten an Benutzer senden, deren Profile Sie über soziale Netzwerke erfasst haben oder die einen Informationsdienst abonniert haben.

Diese Zuordnungen (Mapping) werden [in diesem Abschnitt](../../delivery/using/selecting-a-target-mapping.md) dargestellt.

Sie können auch ein benutzerdefiniertes Zielgruppen-Mapping erstellen und verwenden. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../configuration/using/target-mapping.md).

## Externe Empfänger {#external-recipients}

Sie können Nachrichten an Empfänger senden, die in einer externen Datei anstatt in der Datenbank gespeichert sind. Weiterführende Informationen finden Sie [in diesem Abschnitt](../../delivery/using/steps-defining-the-target-population.md#selecting-external-recipients).

## Versand an Ihre Abonnenten {#send-to-subscribers}

Um den Abonnenten eines Newsletters Nachrichten zu senden, können Sie die Abonnenten des jeweiligen Informationsdienstes direkt anschreiben. Weiterführende Informationen finden Sie [in diesem Abschnitt](../../delivery/using/managing-subscriptions.md#delivering-to-the-subscribers-of-a-service).


## Testversand-Empfänger und Testadressen {#test-recipients-seed-addresses}

Nutzen Sie Testsendungen, bevor Sie Ihre Nachricht an die Hauptzielgruppe senden.

Achten Sie darauf, geeignete Testversand-Empfänger auszuwählen, da diese die Form und den Inhalt Ihrer Nachricht validieren. Die Schritte zum Festlegen der Testversand-Empfänger werden [in diesem Abschnitt](../../delivery/using/steps-defining-the-target-population.md#selecting-the-proof-target) beschrieben.

Testadressen werden verwendet, um Nachrichten an Empfänger zu senden, die nicht den definierten Kriterien der Zielgruppe entsprechen, damit eine Nachricht getestet werden kann, bevor sie an die Hauptzielgruppe gesendet wird. Sie werden [in diesem Abschnitt](../../delivery/using/about-seed-addresses.md) dargestellt.

## Deduplizieren von Adressen {#deduplicate-addresses}

Vermeiden Sie doppelte E-Mail-Adressen, da sich dies auf Ihre Zielgruppe auswirken kann:

* Wenn eine Zielgruppe geteilt wird, kann es vorkommen, dass dieselbe Nachricht öfter als ein Mal gesendet wird.

* Wenn sich ein Empfänger nach dem Erhalt einer Nachricht abmeldet, könnten an sein dupliziertes Profil weiterhin Nachrichten gesendet werden.

Die Deduplizierung von Adressen schützt Ihre Reputation und gewährleistet eine gute Quarantäneverwaltung.

Weitere Informationen finden Sie [in diesem Anwendungsbeispiel](../../workflow/using/deduplication.md#example--identify-the-duplicates-before-a-delivery).

## Indizieren von E-Mail-Adressen {#index-addresses}

Um die Performance der in der Anwendung verwendeten SQL-Abfragen zu optimieren, kann ein Index vom Hauptelement des Datenschemas deklariert werden.

Eine Anleitung zum Hinzufügen eines Index zu den E-Mail-Adressen finden Sie [in diesem Abschnitt](../../configuration/using/database-mapping.md#indexed-fields).
