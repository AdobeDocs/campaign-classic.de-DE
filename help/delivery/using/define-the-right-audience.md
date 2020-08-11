---
title: Definieren der richtigen Audience
seo-title: Definieren der richtigen Audience
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
source-wordcount: '478'
ht-degree: 36%

---


# Definieren der richtigen Audience {#define-the-right-audience}

Die Bestimmung der Zielgruppen ist besonders wichtig. Gehen Sie bei der Erstellung Ihrer Kontaktlisten sorgfältig vor, testen Sie Ihre E-Mails in den gängigsten E-Mail-Clients und Mobilgeräten und stellen Sie sicher, dass Ihre Verteilerlisten aktuell sind (und keine unbekannten oder veralteten Adressen enthalten). Sie können auch Testsendungen vornehmen, um einen vollständigen Validierungszyklus durchzuführen.

Weitere Informationen zu Zielgruppen [in diesem Abschnitt](../../delivery/using/steps-defining-the-target-population.md)

## Zielgruppe der richtigen Audience {#target-the-right-audience}

Wenn Ihr Inhalt fertiggestellt ist, müssen Sie sorgfältig auswählen, wer Ihre Nachricht erhalten soll.

Damit Ihr Versand erfolgreich ist, möchten Sie die relevantesten personalisierten Inhalte an die richtigen Empfänger senden. Mit Adobe Campaign können Sie die genaueste Zielgruppe erstellen: Sie können Empfänger nach Alter, lokale Anpassung, Kaufdatum, Link in einem vorherigen Versand usw. auswählen. With Adobe Campaign, you can also define test profiles, control groups and seed addresses to make sure your target is correct.

## Zielgruppen-Mappings {#target-mappings}

In Campaign Classic, by default, delivery templates target **Recipients**. Adobe Campaign offers other target mappings for your deliveries, that you can change based on your needs.

For example, you can deliver to visitors whose profiles have been collected via social networks or to visitors who are subscribed to an information service.

Diese Zuordnungen werden [in diesem Abschnitt](../../delivery/using/selecting-a-target-mapping.md)dargestellt.

Sie können auch ein benutzerdefiniertes Zielgruppen-Mapping erstellen und verwenden. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../configuration/using/target-mapping.md).

## Externe Empfänger {#external-recipients}

Sie können die Bereitstellung an Empfänger durchführen, die in einer externen Datei gespeichert und nicht in der Datenbank gespeichert sind. Learn more [in this section](../../delivery/using/steps-defining-the-target-population.md#selecting-external-recipients).

## An Ihre Abonnenten senden {#send-to-subscribers}

Um Nachrichten an die Abonnenten eines Newsletters zu senden, können Sie die Abonnenten direkt an den entsprechenden Informationsdienst Zielgruppe. Learn more [in this section](../../delivery/using/managing-subscriptions.md#delivering-to-the-subscribers-of-a-service).


## Testversand-Empfänger und Testadressen {#test-recipients-seed-addresses}

Nutzen Sie Testsendungen, bevor Sie Ihre Nachricht an die Hauptzielgruppe senden.

Stellen Sie sicher, dass Sie die entsprechenden Testversand-Empfänger auswählen, da sie das Formular und den Inhalt der Nachricht überprüfen. The steps for defining the proof recipients are presented [in this section](../../delivery/using/steps-defining-the-target-population.md#selecting-the-proof-target).

Seed addresses are used to target recipients who do not match the defined target criteria in order to test a delivery before sending to the main target. Sie werden [in diesem Abschnitt](../../delivery/using/about-seed-addresses.md)vorgestellt.

## Deduplizieren von Adressen {#deduplicate-addresses}

Vermeiden Sie doppelte E-Mail-Adressen, da sich dies auf Ihre Zielgruppe auswirken kann:

* Wenn eine Zielgruppe geteilt wird, kann es vorkommen, dass dieselbe Nachricht öfter als ein Mal gesendet wird.

* Wenn sich ein Empfänger nach dem Erhalt einer Nachricht abmeldet, könnten an sein dupliziertes Profil weiterhin Nachrichten gesendet werden.

Die Deduplizierung von Adressen schützt Ihre Reputation und gewährleistet eine gute Quarantäneverwaltung.

Learn more [in this use case](../../workflow/using/deduplication.md#example--identify-the-duplicates-before-a-delivery).

## Index email addresses {#index-addresses}

Um die Performance der in der Anwendung verwendeten SQL-Abfragen zu optimieren, kann ein Index vom Hauptelement des Datenschemas deklariert werden.

The steps for adding an index to the email address are presented [in this section](../../configuration/using/database-mapping.md#indexed-fields).
