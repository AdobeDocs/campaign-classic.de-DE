---
product: campaign
title: Erste Schritte mit dem Campaign Classic-Datenmodell
description: Erfahren Sie, wie Sie das Datenmodell von Campaign erweitern, Schemata bearbeiten, APIs verwenden und vieles mehr
feature: Data Model, Configuration
role: Data Engineer, Developer
exl-id: 655b5928-b005-442f-b026-2f1b0c1abb99
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '985'
ht-degree: 25%

---

# Erste Schritte mit dem Campaign-Datenmodell{#about-data-model}

Das konzeptionelle Datenmodell der Adobe Campaign-Datenbank besteht aus einer Reihe integrierter Tabellen und deren Interaktion. Die wichtigsten Tabellen und Konzepte sind auf dieser Seite aufgeführt.

## Übersicht {#data-model-overview}

Adobe Campaign stützt sich auf eine relationale Datenbank mit Tabellen, die miteinander verknüpft sind. Die grundlegende Struktur des Adobe Campaign-Datenmodells kann wie folgt beschrieben werden:

### Empfängertabelle {#recipient-table}

Das Datenmodell beruht auf einer Haupt-Tabelle, die standardmäßig die Empfängertabelle (**NmsRecipient**) ist. Diese Tabelle ermöglicht eine Speicherung aller Marketing-Profile.

Weitere Informationen zur Empfängertabelle finden Sie in [diesem Abschnitt](#default-recipient-table).

### Versandtabelle {#delivery-table}

Das Datenmodell enthält auch einen Teil, in dem alle Marketing-Aktivitäten gespeichert werden. Normalerweise handelt es sich dabei um die Versandtabelle (**NmsDelivery**). Jeder Datensatz in dieser Tabelle stellt eine Versandaktion oder Versandvorlage dar. Er enthält alle erforderlichen Parameter zum Ausführen von Sendungen wie Zielgruppe, Inhalt usw.

### Protokolltabellen {#log-tables}

Ein anderer Teil des Datenmodells ermöglicht die zeitweilige Speicherung aller Logs, die mit der Ausführung der Kampagnen verbunden sind.

Versand-Logs sind sämtliche Nachrichten, die über alle Kanäle hinweg an Empfänger oder Geräte gesendet werden. Die Haupttabelle Versandlogs (**NmsBroadLog**) enthält die Versandlogs aller Empfänger.
Die Tabelle der Trackinglogs (**NmsTrackingLog**) speichert die Trackinglogs für alle Empfänger. Die Trackinglogs beziehen sich auf Reaktionen von Empfängern wie E-Mail-Öffnungen und Klicks. Jede Reaktion entspricht einem Trackinglog.
Versand-Logs und Trackinglogs werden nach einem bestimmten Zeitraum gelöscht, der in Adobe Campaign angegeben und änderbar ist. Daher wird dringend empfohlen, die Logs regelmäßig zu exportieren.

### Technische Tabellen {#technical-tables}

Schließlich besteht ein Teil des Datenmodells aus technischen Daten, die für den Anwendungsprozess verwendet werden, einschließlich Operatoren und Benutzerrechte (**NmsGroup**), Ordnern (**XtkFolder**).

## Verwenden der integrierten Empfängertabelle {#default-recipient-table}

Die integrierte Empfängertabelle in Adobe Campaign bietet einen guten Ausgangspunkt für die Erstellung Ihres Datenmodells. Sie verfügt über eine Reihe vordefinierter Felder und Tabellenrelationen, die leicht erweitert werden können. Dies ist besonders dann nützlich, wenn Sie vor allem auf Empfänger abzielen, da sie für ein einfaches Empfänger-orientiertes Datenmodell geeignet ist.

Die Verwendung der integrierten Empfängertabelle bietet folgende Vorteile:

* Integrierte Funktionen wie Abonnements, Seed-Listen und mehr
* Bereitstellung einer Marketing-Datenbank mit einem empfängerorientierten Datenmodell.
* Schnellere Implementierung.
* Einfache Wartung durch Support und Partner.

Es ist jedoch möglich, die Empfängertabelle zu erweitern, aber nicht die Anzahl der Felder oder Links in der Tabelle zu reduzieren.

>[!IMPORTANT]
>
>Es wird empfohlen, Felder in der Empfängertabelle nicht zu löschen (auch wenn sie nutzlos sind), da dies zu Fehlern in den integrierten Modulen führen kann.

Da die Empfängertabelle Teil des Produkts ist, entwickeln sich sowohl die Tabelle als auch das zugehörige Formular, sobald sich das Produkt ändert. Daher ist eine zusätzliche Wartung erforderlich, um sicherzustellen, dass alle Erweiterungen nach der Aktualisierung weiterhin gültig sind.

## Erweitern des Datenmodells {#extending-data-model}

Wenn Sie mit Adobe Campaign beginnen, müssen Sie das Standarddatenmodell evaluieren, um zu prüfen, welche Tabelle am besten zur Speicherung Ihrer Marketing-Daten geeignet ist.

Falls relevant, können Sie die standardmäßige Empfängertabelle mit den nativen Feldern verwenden, wie in [diesem Abschnitt](#default-recipient-table) beschrieben.

Bei Bedarf können Sie sie mit zwei Verfahren erweitern:

* Erweitern einer vorhandenen Tabelle um neue Felder. Sie können der Empfängertabelle beispielsweise ein neues Feld „Treue“ hinzufügen.
* Erstellen Sie eine neue Tabelle, z. B. eine &quot;Kauf&quot;-Tabelle, die alle von jedem Profil der Datenbank getätigten Käufe auflistet, und verknüpfen Sie sie mit der Empfängertabelle.

Weitere Informationen zum Konfigurieren von Erweiterungsschemata zum Erweitern des konzeptionellen Datenmodells finden Sie unter [Über die Schemabearbeitung](../../configuration/using/about-schema-edition.md).

>[!IMPORTANT]
>
>Die Erweiterung des Datenmodells ist erfahrenen Benutzern vorbehalten.

## Verwenden einer benutzerdefinierten Empfängertabelle {#custom-recipient-table}

Beim Entwerfen Ihres Adobe Campaign-Datenmodells können Sie die integrierte Empfängertabelle ](#default-recipient-table) von [oder eine benutzerdefinierte Empfängertabelle [3} verwenden, um Ihre Marketing-Profile zu speichern.](../../configuration/using/about-custom-recipient-table.md)

Wenn Ihr Datenmodell nicht zur empfängerorientierten Struktur passt, können Sie andere Tabellen als Zielgruppendimension in Adobe Campaign einrichten. Dies kann z. B. relevant sein, wenn Sie Haushalte, Konten (wie Mobiltelefone) und Unternehmen/Sites anvisieren müssen und nicht nur Empfänger.

>[!NOTE]
>
>In diesem Fall müssen Sie ein neues [Zielgruppen-Mapping](../../configuration/using/target-mapping.md) erstellen.

Alle Prinzipien und Schritte, die bei der Verwendung einer benutzerdefinierten Empfängertabelle erforderlich sind, werden in [diesem Abschnitt](../../configuration/using/about-custom-recipient-table.md) beschrieben.

Die Verwendung einer benutzerdefinierten Empfängertabelle bietet folgende Vorteile:

* **Flexibles Datenmodell** - Die integrierte Empfängertabelle ist nutzlos, wenn Sie die meisten Tabellenfelder der Empfänger nicht benötigen oder wenn das Datenmodell nicht empfängerzentriert ist.

* **Skalierbarkeit** - Große Volumina erfordern für ein effizientes Design eine optimierte Tabelle mit wenigen Feldern. Die integrierte Empfängertabelle hätte zu viele nutzlose Felder, was sich auf die Leistung auswirken und die Effizienz beeinträchtigen könnte.

* **Datenspeicherort** - Wenn sich Daten in einer externen vorhandenen Marketing-Datenbank befinden, kann es zu viel Aufwand erfordern, die integrierte Empfängertabelle zu verwenden. Die Erstellung einer neuen Struktur auf der Grundlage einer vorhandenen Struktur ist einfacher.

* **Einfache Migration** - Es ist keine Wartung erforderlich, um zu überprüfen, ob alle Erweiterungen nach der Aktualisierung noch gültig sind.

>[!IMPORTANT]
>
>Die Verwendung einer benutzerdefinierten Empfängertabelle ist erfahrenen Benutzern vorbehalten und unterliegt gewissen Einschränkungen. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../configuration/using/about-custom-recipient-table.md).

## Verwandte Themen

Weitere Informationen zum Campaign-Datenmodell finden Sie in diesen Abschnitten:

* **Beschreibung der Haupttabellen** - Weitere Informationen zur Standardbeschreibung des Campaign Classic-Datenmodells finden Sie in [diesem Abschnitt](../../configuration/using/data-model-description.md).

* **Vollständige Beschreibung jeder Tabelle** - Um auf die vollständige Beschreibung jeder Tabelle zuzugreifen, gehen Sie zu **[!UICONTROL Admin > Konfiguration > Datenschemata]**, wählen Sie eine Ressource aus der Liste aus und klicken Sie auf die Registerkarte **[!UICONTROL Dokumentation]** .

  ![](assets/data-model_documentation-tab.png)


* **Kampagnenschemas** - Die physische und logische Struktur der in der Anwendung übertragenen Daten wird in XML beschrieben. Sie folgt einer Adobe Campaign-spezifischen Grammatik namens „Schema“. Weitere Informationen zu Adobe Campaign-Schemata finden Sie in [diesem Abschnitt](../../configuration/using/about-schema-reference.md).

* **Best Practices für Datenmodelle** - Erfahren Sie in [diesem Abschnitt](../../configuration/using/data-model-best-practices.md#data-model-architecture) die Architektur des Datenmodells in Campaign und die entsprechenden Best Practices.
