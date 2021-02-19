---
solution: Campaign Classic
product: campaign
title: Erste Schritte mit dem Campaign Classic-Datenmodell
description: Erfahren Sie, wie Sie das Datenmodell der Campaign erweitern, Schemata bearbeiten, APIs verwenden und vieles mehr
audience: configuration
content-type: reference
topic-tags: schema-reference
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '988'
ht-degree: 6%

---


# Erste Schritte mit dem Kampagne-Datenmodell{#about-data-model}

Das konzeptionelle Datenmodell der Adobe Campaign-Datenbank besteht aus einer Reihe integrierter Tabellen und deren Interaktion. Die wichtigsten Tabellen und Konzepte sind auf dieser Seite aufgelistet.

## Übersicht {#data-model-overview}

Adobe Campaign stützt sich auf eine relationale Datenbank, die Tabellen enthält, die miteinander verknüpft sind. Die Grundstruktur des Adobe Campaign-Datenmodells kann wie folgt beschrieben werden.

### Empfänger table {#recipient-table}

Das Datenmodell basiert auf einer Haupt-Tabelle, die standardmäßig in der Empfänger-Tabelle (**NmsRecipient**) aufgeführt ist. Diese Tabelle ermöglicht die Speicherung aller Marketing-Profil.

Weitere Informationen zur Tabelle &quot;Empfänger&quot;finden Sie unter [dieser Abschnitt](#default-recipient-table).

### Versand table {#delivery-table}

Das Datenmodell enthält auch einen Teil, der alle Marketing-Aktivitäten speichert. In der Regel ist dies die Versand-Tabelle (**NmsDelivery**). Jeder Datensatz in dieser Tabelle stellt eine Versand- oder Versandvorlage dar. Es enthält alle erforderlichen Parameter zum Ausführen von Versänden wie Zielgruppe, Inhalt usw.

### Protokolle Tabellen {#log-tables}

Ein anderer Teil des Datenmodells ermöglicht die temporäre Speicherung aller Protokolle, die mit der Ausführung der Kampagnen verbunden sind.

Versandlogs sind Nachrichten, die über alle Kanal an Empfänger oder Geräte gesendet werden. Die Haupt-Tabelle mit Versandlogs (**NmsBroadLog**) enthält die Versandlogs für alle Empfänger.
Die Haupt-Tabelle mit Trackinglogs (**NmsTrackingLog**) speichert die Trackinglogs für alle Empfänger. Die Trackinglogs beziehen sich auf Reaktionen von Empfängern wie E-Mail-Öffnungen und Klicks. Jede Reaktion entspricht einem Verfolgungsprotokoll.
Versandlogs und Trackinglogs werden nach einem bestimmten Zeitraum gelöscht, der im Adobe Campaign angegeben ist und geändert werden kann. Daher wird dringend empfohlen, die Stämme regelmäßig zu exportieren.

### Technische Tabellen {#technical-tables}

Schließlich besteht ein Teil des Datenmodells aus technischen Daten, die für den Anwendungsprozess verwendet werden, einschließlich Operatoren und Benutzerrechten (**NmsGroup**), Ordnern (**XtkFolder**).

## Verwenden der standardmäßigen Empfängertabelle {#default-recipient-table}

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

Wenn Sie mit Adobe Campaign beginnen, müssen Sie das Standarddatenmodell bewerten, um zu prüfen, welche Tabelle am besten zur Speicherung Ihrer Marketingdaten geeignet ist.

Falls relevant, können Sie die Standardtabelle für Empfänger mit den vordefinierten Feldern verwenden, wie in [diesem Abschnitt](#default-recipient-table) beschrieben.

Bei Bedarf können Sie ihn um zwei Mechanismen erweitern:

* Erweitern einer vorhandenen Tabelle mit neuen Feldern Sie können der Tabelle &quot;Empfänger&quot;beispielsweise ein neues Feld &quot;Kundentreue&quot;hinzufügen.
* Erstellen Sie eine neue Tabelle, z. B. eine &quot;Einkaufstabelle&quot;, in der alle von den einzelnen Profilen der Datenbank getätigten Käufe aufgelistet sind, und verknüpfen Sie diese mit der Tabelle &quot;Empfänger&quot;.

Weitere Informationen zum Konfigurieren von Erweiterungsschemas zur Erweiterung des konzeptionellen Datenmodells finden Sie unter [Informationen zur Schema-Edition](../../configuration/using/about-schema-edition.md).

>[!IMPORTANT]
>
>Die Erweiterung des Datenmodells ist für fortgeschrittene Benutzer reserviert.

## Verwenden einer benutzerdefinierten Empfängertabelle {#custom-recipient-table}

Beim Entwerfen Ihres Adobe Campaign-Datenmodells können Sie die vordefinierte Tabelle [des Empfängers](#default-recipient-table) verwenden oder eine Tabelle [des benutzerdefinierten Empfängers](../../configuration/using/about-custom-recipient-table.md) erstellen, um Ihre Marketing-Profil zu speichern.

Wenn Ihr Datenmodell nicht in die Empfänger-orientierte Struktur passt, können Sie andere Tabellen als Zielgruppendimension innerhalb von Adobe Campaign einrichten. Dies kann z. B. relevant sein, wenn Sie Haushalte, Konten (wie Mobiltelefone) und Firmen/Sites Zielgruppe benötigen, anstatt einfach nur Empfänger.

>[!NOTE]
>
>In diesem Fall müssen Sie ein neues [Zielgruppen-Mapping](../../configuration/using/target-mapping.md) erstellen.

Alle bei der Verwendung einer Tabelle mit benutzerdefiniertem Empfänger erforderlichen Prinzipien und Schritte sind in [diesem Abschnitt ](../../configuration/using/about-custom-recipient-table.md) beschrieben.

Die Verwendung einer Tabelle mit benutzerdefinierten Empfängern bietet folgende Vorteile:

* **Flexibles Datenmodell** : Die vordefinierte Empfänger-Tabelle ist nutzlos, wenn Sie die meisten Empfänger-Tabellenfelder nicht benötigen oder wenn das Datenmodell nicht auf Empfänger ausgerichtet ist.

* **Skalierbarkeit**  - Große Volumes erfordern eine optimierte Tabelle mit wenigen Feldern, um ein effizientes Design zu gewährleisten. Die vordefinierte Tabelle mit Empfängern hätte zu viele nutzlose Felder, was sich auf die Leistung und mangelnde Effizienz auswirken könnte.

* **Datenspeicherort** : Wenn sich Daten auf einer externen vorhandenen Marketingdatenbank befinden, ist möglicherweise zu viel Aufwand erforderlich, um die vordefinierte Empfänger-Tabelle zu verwenden. Die Erstellung einer neuen Struktur auf der Grundlage einer vorhandenen Struktur ist einfacher.

* **Einfache Migration** : Es ist keine Wartung erforderlich, um zu überprüfen, ob alle Erweiterungen nach der Aktualisierung noch gültig sind.

>[!IMPORTANT]
>
>Die Verwendung einer Tabelle mit benutzerdefiniertem Empfänger ist für fortgeschrittene Benutzer reserviert und unterliegt bestimmten Einschränkungen. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../configuration/using/about-custom-recipient-table.md).

## Verwandte Themen

Weitere Informationen zum Datenmodell der Kampagne finden Sie in den folgenden Abschnitten:

* **Beschreibung der Haupttabellen**  - Weitere Informationen zur Beschreibung des Standarddatenmodells des Campaign Classic finden Sie in  [diesem Abschnitt](../../configuration/using/data-model-description.md).

* **Vollständige Tabellenbeschreibung** : Um die vollständige Tabellenbeschreibung aufzurufen, gehen Sie zu  **[!UICONTROL Admin > Konfiguration > Datenelemente]**, wählen Sie eine Schema aus der Liste und klicken Sie auf die Registerkarte  **** Dokumentation.

   ![](assets/data-model_documentation-tab.png)


* **Schema**  der Kampagne: Die physische und logische Struktur der in der Anwendung übertragenen Daten wird in XML beschrieben. Sie folgt einer Adobe Campaign-spezifischen Grammatik namens „Schema“. Für weitere Informationen zu Adobe Campaign-Schemas lesen Sie [diesen Abschnitt](../../configuration/using/about-schema-reference.md).

* **Best Practices**  für Datenmodelle - Erfahren Sie mehr über die Kampagne-Datenmodellarchitektur und zugehörige Best Practices in  [diesem Abschnitt](../../configuration/using/data-model-best-practices.md#data-model-architecture).
