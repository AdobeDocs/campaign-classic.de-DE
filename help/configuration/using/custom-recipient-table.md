---
title: Info zum Adobe Campaign Classic-Datenmodell
description: In diesem Dokument werden die Grundlagen des Adobe Campaign Classic-Datenmodells beschrieben.
page-status-flag: never-activated
uuid: faddde15-59a1-4d2c-8303-5b3e470a0c51
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: schema-reference
discoiquuid: 5957b39e-c2c6-40a2-b81a-656e9ff7989c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 65affa58a66090c3bffc837fdbd85aa46338bd3e

---


# Verwenden einer benutzerdefinierten Empfängertabelle{#custom-recipient-table}

Beim Entwerfen Ihres Adobe Campaign-Datenmodells können Sie die [vordefinierte Empfängertabelle](../../configuration/using/default-recipient-table.md)verwenden oder eine nicht standardmäßige Empfängertabelle zur Speicherung Ihrer Marketing-Profile erstellen.

Wenn Ihr Datenmodell nicht zur empfängerorientierten Struktur passt, können Sie andere Tabellen als Targeting-Dimension in Adobe Campaign einrichten. Dies kann z. B. relevant sein, wenn Sie Haushalte, Konten (wie Mobiltelefone) und Unternehmen/Sites als Ziel auswählen müssen und nicht nur Empfänger.

>[!NOTE]
>
>In diesem Fall müssen Sie eine neue [Zielzuordnung](../../configuration/using/target-mapping.md)erstellen.

Alle bei der Verwendung einer benutzerdefinierten Empfängertabelle erforderlichen Prinzipien und Schritte werden in diesem [Abschnitt](../../configuration/using/about-custom-recipient-table.md)beschrieben.

Die Verwendung einer benutzerdefinierten Empfängertabelle bietet folgende Vorteile:

## Flexibles Datenmodell {#flexible-data-model}

Die vordefinierte Empfängertabelle ist nutzlos, wenn Sie die meisten der begünstigten Tabellenfelder nicht benötigen oder wenn das Datenmodell nicht empfängerzentriert ist.

## Skalierbarkeit {#scalability}

Große Volumes erfordern eine optimierte Tabelle mit wenigen Feldern, um ein effizientes Design zu gewährleisten. Die vordefinierte Empfängertabelle hätte zu viele nutzlose Felder, was sich auf die Leistung und mangelnde Effizienz auswirken könnte.

## Datenposition {#data-location}

Wenn sich Daten auf einer externen vorhandenen Marketingdatenbank befinden, ist möglicherweise zu viel Aufwand erforderlich, um die vordefinierte Empfängertabelle zu verwenden. Die Erstellung einer neuen Struktur auf der Grundlage einer vorhandenen Struktur ist einfacher.

## Einfache Migration {#easy-migration}

Es ist keine Wartung erforderlich, um zu überprüfen, ob alle Erweiterungen nach der Aktualisierung noch gültig sind.

>[!IMPORTANT]
>
>Die Verwendung einer benutzerdefinierten Empfängertabelle ist für fortgeschrittene Benutzer reserviert und unterliegt bestimmten Einschränkungen. Weiterführende Informationen hierzu finden Sie in diesem Abschnitt.
