---
product: campaign
title: Definieren der richtigen Zielgruppe
description: Best Practices bei der Auswahl einer Zielgruppe
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
feature: Audiences
role: User
hide: true
exl-id: c0533148-b027-4158-9b95-8d2df769e963
TQID: https://experienceleague.adobe.com/bA0bwsoCEGaC0-R64f08j8vLzGFDI7hhN3rFYnKdRWA
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 554
ht-degree: 100%

---

# Definieren der richtigen Zielgruppe {#define-the-right-audience}

Die Bestimmung der Zielpopulation ist besonders wichtig. Gehen Sie bei der Erstellung Ihrer Listen sorgfältig vor, testen Sie Ihre E-Mails in den gängigsten E-Mail-Clients sowie auf den gängigsten Mobilgeräten und stellen Sie sicher, dass Ihre E-Mail-Listen aktuell sind (und keine unbekannten oder veralteten Adressen enthalten). Sie können auch Testsendungen vornehmen, um einen vollständigen Validierungszyklus durchzuführen.

Weitere Informationen zu Zielpopulationen finden Sie in diesem Abschnitt der [Dokumentation zu Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/create-message.html?lang=de){target="_blank"}.

## Ansprechen der richtigen Zielgruppe {#target-the-right-audience}

Wenn Ihr Inhalt fertiggestellt ist, müssen Sie sorgfältig auswählen, wer Ihre Nachricht erhalten soll.

Um einen erfolgreichen Versand durchzuführen, müssen Sie möglichst relevanten personalisierten Inhalt an die richtigen Empfänger senden. Mit Adobe Campaign können Sie eine äußerst präzise Zielgruppe erstellen: Sie können die Empfängerinnen und Empfänger beispielsweise nach Alter, Ort, Kaufverhalten und Klicks auf Links in früheren Sendungen auswählen. Mit Adobe Campaign können Sie Testprofile, Kontrollgruppen und Testadressen definieren, um sicherzustellen, dass Ihre Zielgruppe korrekt ist.

## Zielgruppen-Mappings {#target-mappings}

Standardmäßig werden bei Campaign Classic mit Versandvorlagen **Empfänger** angesprochen. Adobe Campaign ermöglicht aber auch andere Zielgruppen-Mappings für Ihre Sendungen, die Sie entsprechend Ihren Anforderungen anpassen können.

So können Sie beispielsweise Nachrichten an Benutzer senden, deren Profile Sie über soziale Netzwerke erfasst haben oder die einen Informationsdienst abonniert haben.

Diese Zuordnungen werden in der [Dokumentation zu Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/audience/add-profiles/target-mappings.html?lang=de){target="_blank"} erläutert.

Sie können auch ein benutzerdefiniertes Zielgruppen-Mapping erstellen und verwenden. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../configuration/using/target-mapping.md).

## Externe Empfänger {#external-recipients}

Sie können Nachrichten an Empfangende senden, die in einer externen Datei anstatt in der Datenbank gespeichert sind. Weitere Informationen finden Sie in der [Dokumentation zu Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/create-message.html?lang=de#selecting-external-recipients){target="_blank"}.

## Versand an Ihre Abonnenten {#send-to-subscribers}

Um den Abonnenten eines Newsletters Nachrichten zu senden, können Sie die Abonnenten des jeweiligen Informationsdienstes direkt anschreiben. Weiterführende Informationen finden Sie [in diesem Abschnitt](managing-subscriptions.md#delivering-to-the-subscribers-of-a-service).


## Testversand-Empfänger und Testadressen {#test-recipients-seed-addresses}

Nutzen Sie Testsendungen, bevor Sie Ihre Nachricht an die Hauptzielgruppe senden.

Achten Sie darauf, geeignete Testversand-Empfänger auszuwählen, da diese die Form und den Inhalt Ihrer Nachricht validieren. Die Schritte zum Definieren der Empfängerinnen und Empfänger des Testversands werden in der [Dokumentation zu Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/create-message.html?lang=de#select-the-proof-target){target="_blank"} erläutert.

Testadressen werden verwendet, um Nachrichten an Empfänger zu senden, die nicht den definierten Kriterien der Zielgruppe entsprechen, damit eine Nachricht getestet werden kann, bevor sie an die Hauptzielgruppe gesendet wird. Sie werden [in diesem Abschnitt](about-seed-addresses.md) dargestellt.

## Deduplizieren von Adressen {#deduplicate-addresses}

Vermeiden Sie doppelte E-Mail-Adressen, da sich dies auf Ihre Zielgruppe auswirken kann:

* Wenn eine Zielgruppe geteilt wird, kann es vorkommen, dass dieselbe Nachricht öfter als ein Mal gesendet wird.

* Wenn sich ein Empfänger nach dem Erhalt einer Nachricht abmeldet, könnten an sein dupliziertes Profil weiterhin Nachrichten gesendet werden.

Die Deduplizierung von Adressen schützt Ihre Reputation und gewährleistet eine gute Quarantäneverwaltung.

**Verwandte Themen:**

* [Aktivität „Deduplizierung“](../../workflow/using/deduplication.md).
* [Anwendungsfall: Verwenden der Zusammenführungsfunktion der Aktivität &quot;Deduplizierung&quot;](../../workflow/using/deduplication-merge.md)

## Indizieren von E-Mail-Adressen {#index-addresses}

Um die Performance der in der Anwendung verwendeten SQL-Abfragen zu optimieren, kann ein Index vom Hauptelement des Datenschemas deklariert werden.

Eine Anleitung zum Hinzufügen eines Index zu den E-Mail-Adressen finden Sie [in diesem Abschnitt](../../configuration/using/database-mapping.md#indexed-fields).
