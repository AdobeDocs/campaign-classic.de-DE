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
source-git-commit: 87966db35779f0e6a4b09a1a3ba1c30d4d002518

---


# About the Campaign data model{#about-data-model}

In diesem Abschnitt werden die Grundlagen des Adobe Campaign Classic-Datenmodells beschrieben, um ein besseres Verständnis der integrierten Campaign-Tabellen und ihrer Interaktion zu erhalten.

Das konzeptionelle Datenmodell der Adobe Campaign-Datenbank besteht aus einer Reihe integrierter Tabellen und deren Interaktion.

Um die Tabellenbeschreibung aufzurufen, wählen Sie in der Liste eine Ressource aus **[!UICONTROL Admin > Configuration > Data schemas]** und klicken Sie auf die **[!UICONTROL Documentation]** Registerkarte.

![](assets/data-model_documentation-tab.png)

Weitere Informationen zur Standardbeschreibung des Campaign Classic-Datenmodells finden Sie in diesem [Abschnitt](../../configuration/using/data-model-description.md).

Die physische und logische Struktur der in der Anwendung übertragenen Daten wird in XML beschrieben. Es folgt einer für Adobe Campaign spezifischen Grammatik, einem so genannten Schema. Weitere Informationen zu Adobe Campaign-Schemas finden Sie in diesem [Abschnitt](../../configuration/using/about-schema-reference.md).

## Übersicht {#data-model-overview}

Adobe Campaign nutzt eine relationale Datenbank, die Tabellen enthält, die miteinander verknüpft sind. Die grundlegende Struktur des Adobe Campaign-Datenmodells kann wie folgt beschrieben werden.

>[!NOTE]
>
>Weitere Informationen zur Campaign-Datenmodellarchitektur und entsprechenden Best Practices finden Sie in diesem [Abschnitt](../../configuration/using/data-model-best-practices.md#data-model-architecture).

### Empfänger {#recipient-table}

Das Datenmodell basiert auf einer Haupt-Tabelle, die standardmäßig in der Empfänger-Tabelle (**NmsRecipient**) aufgeführt ist. Diese Tabelle ermöglicht die Speicherung aller Marketing-Profil.

Weitere Informationen zur Empfänger-Tabelle finden Sie in diesem [Abschnitt](#default-recipient-table).

### Versand {#delivery-table}

Das Datenmodell enthält auch einen Teil, der alle Marketing-Aktivitäten speichert. Normalerweise ist es der Versand-Tisch (**NmsDelivery**). Jeder Datensatz in dieser Tabelle stellt eine Versand- oder Versandvorlage dar. Es enthält alle erforderlichen Parameter zum Ausführen von Versänden wie Zielgruppe, Inhalt usw.

### Protokolle {#log-tables}

Ein anderer Teil des Datenmodells ermöglicht die temporäre Speicherung aller Protokolle, die mit der Ausführung der Campaign verbunden sind.

Versandlogs sind Nachrichten, die über alle Kanal an Empfänger oder Geräte gesendet werden. Die Haupt-Tabelle mit Versandlogs (**NmsBroadLog**) enthält die Versandlogs für alle Empfänger.
Die Haupt-Tabelle &quot;Trackinglogs&quot;(**NmsTrackingLog**) speichert die Trackinglogs für alle Empfänger. Die Trackinglogs beziehen sich auf Reaktionen von Empfängern wie E-Mail-Öffnungen und Klicks. Jede Reaktion entspricht einem Verfolgungsprotokoll.
Versandlogs und Trackinglogs werden nach einem bestimmten Zeitraum gelöscht, der in Adobe Campaign angegeben ist und geändert werden kann. Daher wird dringend empfohlen, die Stämme regelmäßig zu exportieren.

### Technische Tabellen {#technical-tables}

Schließlich besteht ein Teil des Datenmodells aus technischen Daten, die für den Anwendungsprozess verwendet werden, einschließlich Operatoren und Benutzerrechte (**NmsGroup**), Ordner (**XtkFolder**).

## Verwenden der Standardtabelle Empfänger {#default-recipient-table}

Die vordefinierte Empfänger-Tabelle in Adobe Campaign bietet einen guten Ausgangspunkt zum Erstellen Ihres Datenmodells. Es verfügt über eine Reihe vordefinierter Felder und Tabellenlinks, die leicht erweitert werden können. Dies ist besonders dann nützlich, wenn Sie hauptsächlich auf Empfänger abzielen, da es zu einem einfachen Empfänger-orientierten Datenmodell passt.

Die Verwendung der Standardtabelle des Empfängers bietet folgende Vorteile:

* Standardmäßige Funktionen wie Abonnements, Seed-Listen, Umfragen, Social usw.
* Bereitstellung einer Marketingdatenbank mit einem Empfänger-orientierten Datenmodell.
* Schnellere Implementierung.
* Einfache Wartung durch Support und Partner.

Es ist jedoch möglich, die Tabelle zu erweitern, jedoch nicht die Anzahl der Empfänger oder Links in der Tabelle zu verringern.

>[!IMPORTANT]
>
>Es wird empfohlen, keine Empfänger (auch wenn sie nutzlos sind) in der Tabelle zu löschen, da dies zu Fehlern in den integrierten Modulen führen kann.

Da die Produkttabelle Teil des Empfängers ist, werden auch die Tabelle und das zugehörige Formular weiterentwickelt, sobald sich das Produkt ändert. Daher ist eine zusätzliche Wartung erforderlich, um zu überprüfen, ob Erweiterungen nach der Aktualisierung noch gültig sind.

## Erweitern des Datenmodells {#extending-data-model}

Wenn Sie mit Adobe Campaign beginnen, müssen Sie das Standarddatenmodell bewerten, um zu überprüfen, welche Tabelle am besten zur Speicherung Ihrer Marketingdaten geeignet ist.

Falls relevant, können Sie die Standarddatentabelle mit den vordefinierten Empfängern verwenden, wie in diesem [Abschnitt](#default-recipient-table)beschrieben.

Bei Bedarf können Sie ihn um zwei Mechanismen erweitern:

* Erweitern einer vorhandenen Tabelle mit neuen Feldern Sie können der Tabelle &quot;Empfänger&quot;beispielsweise ein neues Feld &quot;Kundentreue&quot;hinzufügen.
* Erstellen Sie eine neue Tabelle, z. B. eine &quot;Einkaufstabelle&quot;, in der alle von den einzelnen Profilen der Datenbank getätigten Käufe aufgelistet sind, und verknüpfen Sie diese mit der Tabelle &quot;Empfänger&quot;.

Weitere Informationen zum Konfigurieren von Erweiterungsschemas zur Erweiterung des konzeptionellen Datenmodells finden Sie unter [Grundlagen zur Schema-Edition](../../configuration/using/about-schema-edition.md).

>[!IMPORTANT]
>
>Die Erweiterung des Datenmodells ist für fortgeschrittene Benutzer reserviert.

## Verwenden einer benutzerdefinierten Empfänger-Tabelle {#custom-recipient-table}

Beim Entwerfen Ihres Adobe Campaign-Datenmodells können Sie die [vordefinierte Tabelle](#default-recipient-table)für den Empfänger verwenden oder eine nicht standardmäßige Empfänger-Tabelle erstellen, um Ihre Marketing-Profil zu speichern.

Wenn Ihr Datenmodell nicht in die Empfänger-orientierte Struktur passt, können Sie andere Tabellen als Zielgruppendimension in Adobe Campaign einrichten. Dies kann z. B. relevant sein, wenn Sie Haushalte, Konten (wie Mobiltelefone) und Firmen/Sites Zielgruppe benötigen, anstatt einfach nur Empfänger.

>[!NOTE]
>
>In diesem Fall müssen Sie ein neues [Zielgruppen-Mapping](../../configuration/using/target-mapping.md)erstellen.

In diesem [Abschnitt](../../configuration/using/about-custom-recipient-table.md)werden alle für die Verwendung einer benutzerdefinierten Tabelle erforderlichen Prinzipien und Schritte beschrieben.

Die Verwendung einer Tabelle mit benutzerdefinierten Empfängern bietet folgende Vorteile:

### Flexibles Datenmodell {#flexible-data-model}

Die vordefinierte Empfänger-Tabelle ist nutzlos, wenn Sie die meisten Empfänger-Tabellenfelder nicht benötigen oder wenn das Datenmodell nicht vom Empfänger zentriert ist.

### Skalierbarkeit {#scalability}

Große Volumes erfordern eine optimierte Tabelle mit wenigen Feldern, um ein effizientes Design zu gewährleisten. Die vordefinierte Tabelle mit Empfängern hätte zu viele nutzlose Felder, was sich auf die Leistung und mangelnde Effizienz auswirken könnte.

### Datenposition {#data-location}

Wenn sich Daten auf einer externen, vorhandenen Marketingdatenbank befinden, ist möglicherweise zu viel Aufwand erforderlich, um die vordefinierte Empfänger-Tabelle zu verwenden. Die Erstellung einer neuen Struktur auf der Grundlage einer vorhandenen Struktur ist einfacher.

### Einfache Migration {#easy-migration}

Es ist keine Wartung erforderlich, um zu überprüfen, ob alle Erweiterungen nach der Aktualisierung noch gültig sind.

>[!IMPORTANT]
>
>Die Verwendung einer Tabelle mit benutzerdefiniertem Empfänger ist für fortgeschrittene Benutzer reserviert und unterliegt bestimmten Einschränkungen. Weiterführende Informationen hierzu finden Sie in diesem Abschnitt.
