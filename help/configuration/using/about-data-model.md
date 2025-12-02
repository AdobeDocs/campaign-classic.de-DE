---
product: campaign
title: Erste Schritte mit dem Campaign Classic-Datenmodell
description: Erfahren Sie, wie Sie das Datenmodell von Campaign erweitern, Schemata bearbeiten, APIs verwenden und vieles mehr
feature: Data Model, Configuration
role: Developer
exl-id: 655b5928-b005-442f-b026-2f1b0c1abb99
source-git-commit: 9f5205ced6b8d81639d4d0cb6a76905a753cddac
workflow-type: tm+mt
source-wordcount: '985'
ht-degree: 25%

---

# Erste Schritte mit dem Campaign-Datenmodell{#about-data-model}

Das konzeptionelle Datenmodell der Adobe Campaign-Datenbank besteht aus einer Reihe integrierter Tabellen und deren Interaktion. Die wichtigsten Tabellen und Konzepte sind auf dieser Seite aufgeführt.

## Übersicht {#data-model-overview}

Adobe Campaign stützt sich auf eine relationale Datenbank, die miteinander verknüpfte Tabellen enthält. Die Grundstruktur des Adobe Campaign-Datenmodells lässt sich wie folgt beschreiben.

### Empfängertabelle {#recipient-table}

Das Datenmodell basiert auf einer Haupttabelle, die standardmäßig die Empfängertabelle (**NmsRecipient**) ist. Diese Tabelle ermöglicht eine Speicherung aller Marketing-Profile.

Weitere Informationen zur Empfängertabelle finden Sie [diesem Abschnitt](#default-recipient-table).

### Versandtabelle {#delivery-table}

Das Datenmodell enthält auch einen Teil, der dem Speichern aller Marketing-Aktivitäten dient. Normalerweise handelt es sich dabei um die Versandtabelle (**NmsDelivery**). Jeder Datensatz in dieser Tabelle stellt eine Versandaktion oder Versandvorlage dar. Er enthält alle erforderlichen Parameter zum Ausführen von Sendungen wie Zielgruppe, Inhalt usw.

### Protokolltabellen {#log-tables}

Ein anderer Teil des Datenmodells ermöglicht es, vorübergehend alle Protokolle zu speichern, die mit der Ausführung der Kampagnen verbunden sind.

Versand-Logs sind sämtliche Nachrichten, die über alle Kanäle hinweg an Empfänger oder Geräte gesendet werden. Die Haupttabelle der Versandlogs (**NmsBroadLog**) enthält die Versandlogs für alle Empfänger.
Die Haupt-Trackinglog-Tabelle (**NmsTrackingLog**) speichert die Trackinglogs für alle Empfänger. Die Trackinglogs beziehen sich auf Reaktionen von Empfängern wie E-Mail-Öffnungen und Klicks. Jede Reaktion entspricht einem Trackinglog.
Versand-Logs und Trackinglogs werden nach einem bestimmten Zeitraum gelöscht, der in Adobe Campaign angegeben und änderbar ist. Daher wird dringend empfohlen, die Logs regelmäßig zu exportieren.

### Technische Tabellen {#technical-tables}

Schließlich besteht ein Teil des Datenmodells aus technischen Daten, die für den jeweiligen Prozess verwendet werden, einschließlich Benutzer- und Benutzerrechten (**NmsGroup**), Ordnern (**XtkFolder**).

## Verwenden der integrierten Empfängertabelle {#default-recipient-table}

Die integrierte Empfängertabelle in Adobe Campaign bietet einen guten Ausgangspunkt für die Erstellung Ihres Datenmodells. Sie verfügt über eine Reihe vordefinierter Felder und Tabellenrelationen, die leicht erweitert werden können. Dies ist besonders dann nützlich, wenn Sie vor allem auf Empfänger abzielen, da sie für ein einfaches Empfänger-orientiertes Datenmodell geeignet ist.

Die Verwendung der integrierten Empfängertabelle bietet folgende Vorteile:

* Arbeiten mit integrierten Funktionen wie Abonnements, Testadressenlisten und mehr.
* Bereitstellen einer Marketing-Datenbank mit einem Empfänger-orientierten Datenmodell.
* Schnellere Implementierung.
* Einfache Wartung durch Support und Partner.

Es ist jedoch möglich, die Empfängertabelle zu erweitern. Die Anzahl der Felder oder Links in der Tabelle lässt sich jedoch nicht verringern.

>[!IMPORTANT]
>
>Es wird empfohlen, keine Felder in der Empfängertabelle zu löschen (auch wenn sie nutzlos sind), da dies zu Fehlern in den integrierten Modulen führen kann.

Da die Empfängertabelle Teil des Produkts ist, ändern sich sowohl die Tabelle als auch die zugehörige Form, wenn sich das Produkt ändert. Daher ist zusätzliche Wartung erforderlich, um zu überprüfen, ob alle Erweiterungen nach dem Upgrade noch gültig sind.

## Datenmodell erweitern {#extending-data-model}

Wenn Sie mit Adobe Campaign beginnen, müssen Sie das Standarddatenmodell evaluieren, um zu prüfen, welche Tabelle am besten zur Speicherung Ihrer Marketing-Daten geeignet ist.

Bei Bedarf können Sie die standardmäßige Empfängertabelle mit den vordefinierten Feldern verwenden, wie in ([ Abschnitt) ](#default-recipient-table).

Bei Bedarf können Sie sie mit zwei Verfahren erweitern:

* Erweitern einer vorhandenen Tabelle mit neuen Feldern. Sie können der Empfängertabelle beispielsweise ein neues Feld „Treue“ hinzufügen.
* Erstellen Sie eine neue Tabelle, z. B. eine Tabelle „Einkauf“, in der alle von den einzelnen Profilen der Datenbank getätigten Käufe aufgelistet sind, und verknüpfen Sie sie mit der Empfängertabelle.

Weitere Informationen zum Konfigurieren von Erweiterungsschemata zur Erweiterung des konzeptionellen Datenmodells finden Sie unter [Über die Schemabearbeitung](../../configuration/using/about-schema-edition.md).

>[!IMPORTANT]
>
>Die Erweiterung des Datenmodells ist erfahrenen Benutzern vorbehalten.

## Verwenden einer benutzerdefinierten Empfängertabelle {#custom-recipient-table}

Beim Entwerfen Ihres Adobe Campaign-Datenmodells können Sie die [integrierte Empfängertabelle) verwenden ](#default-recipient-table) oder eine [benutzerdefinierte Empfängertabelle) ](../../configuration/using/about-custom-recipient-table.md), um Ihre Marketing-Profile zu speichern.

Wenn Ihr Datenmodell nicht zur empfängerorientierten Struktur passt, können Sie in Adobe Campaign andere Tabellen als Zielgruppendimension einrichten. Dies kann beispielsweise relevant sein, wenn Sie Haushalte, Konten (wie Mobiltelefone) und Unternehmen/Websites anstatt nur Empfänger ansprechen möchten.

>[!NOTE]
>
>In diesem Fall müssen Sie ein neues „Zielgruppen[Mapping“ ](../../configuration/using/target-mapping.md).

Alle Prinzipien und Schritte, die bei der Verwendung einer benutzerdefinierten Empfängertabelle erforderlich sind, werden in [diesem Abschnitt) ](../../configuration/using/about-custom-recipient-table.md).

Die Verwendung einer benutzerdefinierten Empfängertabelle bietet folgende Vorteile:

* **Flexibles Datenmodell** - Die integrierte Empfängertabelle ist nutzlos, wenn Sie die meisten Empfängertabellenfelder nicht benötigen oder wenn das Datenmodell nicht empfängerzentriert ist.

* **Skalierbarkeit** - Für ein effizientes Design sind große Datenmengen mit einer optimierten Tabelle und wenigen Feldern erforderlich. Die integrierte Empfängertabelle enthält zu viele nutzlose Felder, was sich auf die Leistung auswirken und die Effizienz beeinträchtigen könnte.

* **Datenspeicherort** - Wenn sich Daten in einer externen, vorhandenen Marketing-Datenbank befinden, kann es zu viel Aufwand erfordern, die integrierte Empfängertabelle zu verwenden. Die Erstellung einer neuen auf einer vorhandenen Struktur basierenden ist einfacher.

* **Einfache Migration** - Es ist keine Wartung erforderlich, um zu überprüfen, ob alle Erweiterungen beim Upgrade noch gültig sind.

>[!IMPORTANT]
>
>Die Verwendung einer benutzerdefinierten Empfängertabelle ist erfahrenen Benutzern vorbehalten und unterliegt einigen Einschränkungen. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../configuration/using/about-custom-recipient-table.md).

## Verwandte Themen

Weitere Informationen zum Campaign-Datenmodell finden Sie in den folgenden Abschnitten:

* **Beschreibung der Haupttabellen** - Weitere Informationen zur standardmäßigen Campaign Classic-Datenmodellbeschreibung finden Sie [diesem Abschnitt](../../configuration/using/data-model-description.md).

* **Vollständige Beschreibung jeder Tabelle** - Um die vollständige Beschreibung jeder Tabelle aufzurufen, navigieren Sie zu **[!UICONTROL Admin > Konfiguration > Datenschemata]** wählen Sie eine Ressource aus der Liste und klicken Sie auf die Registerkarte **[!UICONTROL Dokumentation]**.

  ![](assets/data-model_documentation-tab.png)


* **Campaign-Schemata** - Die physische und logische Struktur der im Programm übertragenen Daten wird in XML beschrieben. Sie folgt einer Adobe Campaign-spezifischen Grammatik namens „Schema“. Weitere Informationen zu Adobe Campaign-Schemata finden Sie [ (diesem Abschnitt](../../configuration/using/about-schema-reference.md).

* **Best Practices für Datenmodelle** - Erfahren Sie mehr über die Architektur von Campaign-Datenmodellen und die zugehörigen Best Practices in [diesem Abschnitt](../../configuration/using/data-model-best-practices.md#data-model-architecture).
