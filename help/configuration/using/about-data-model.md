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
source-git-commit: 2ce2a1a55e244180a4e62d6f3b5a5ed5bb8aff6e

---


# Info zum Kampagnen-Classic-Datenmodell{#about-data-model}

In diesem Abschnitt werden die Grundlagen des Adobe Campaign Classic-Datenmodells beschrieben, um ein besseres Verständnis der integrierten Kampagnentabellen und deren Interaktion zu erhalten.

Das konzeptionelle Datenmodell der Adobe Campaign-Datenbank besteht aus einer Reihe integrierter Tabellen und deren Interaktion.

Um die Beschreibung der einzelnen Tabellen aufzurufen, gehen Sie zu **[!UICONTROL Admin > Configuration > Data schemas]**, wählen Sie eine Ressource aus der Liste aus und klicken Sie auf die **[!UICONTROL Documentation]** Registerkarte.

![](assets/data-model_documentation-tab.png)

Weitere Informationen zur Standardbeschreibung des Campaign Classic-Datenmodells finden Sie in diesem [Dokument](https://final-docs.campaign.adobe.com/doc/AC/en/technicalResources/_Datamodel_Description_of_the_main_tables.html).

Die physische und logische Struktur der in der Anwendung übertragenen Daten wird in XML beschrieben. Es folgt einer für Adobe Campaign spezifischen Grammatik, einem Schema. Weitere Informationen zu Adobe Campaign-Schemata finden Sie in diesem [Abschnitt](../../configuration/using/about-schema-reference.md).

## Übersicht {#data-model-overview}

Adobe Campaign nutzt eine relationale Datenbank, die Tabellen enthält, die miteinander verknüpft sind.

Die grundlegende Struktur des Adobe Campaign-Datenmodells kann wie folgt beschrieben werden.

## Empfängertabelle {#recipient-table}

Das Datenmodell basiert auf einer Haupttabelle, die standardmäßig in der Empfängertabelle (**NmsRecipient**) aufgeführt ist. Diese Tabelle ermöglicht die Speicherung aller Marketing-Profile.

Weitere Informationen zur Tabelle Empfänger finden Sie in diesem [Abschnitt](../../configuration/using/default-recipient-table.md).

## Auslieferungstabelle {#delivery-table}

Das Datenmodell enthält auch einen Teil, der alle Marketingaktivitäten speichert. Normalerweise ist es der Liefertisch (**NmsDelivery**). Jeder Datensatz in dieser Tabelle stellt eine Bereitstellungsaktion oder eine Bereitstellungsvorlage dar. Es enthält alle erforderlichen Parameter für die Ausführung von Auslieferungen wie Ziel, Inhalt usw.

## Protokolle {#log-tables}

Ein anderer Teil des Datenmodells ermöglicht die temporäre Speicherung aller Protokolle, die mit der Ausführung der Kampagnen verbunden sind.

Lieferprotokolle sind alle Nachrichten, die über alle Kanäle an Empfänger oder Geräte gesendet werden. Die Tabelle der Hauptlieferungsprotokolle (**NmsBroadLog**) enthält die Lieferprotokolle für alle Empfänger.
In der Tabelle mit den Hauptverfolgungsprotokollen (**NmsTrackingLog**) werden die Verfolgungsprotokolle für alle Empfänger gespeichert. Die Verfolgungsprotokolle beziehen sich auf Reaktionen von Empfängern, wie E-Mail-Öffnungen und Klicks. Jede Reaktion entspricht einem Verfolgungsprotokoll.
Auslieferungs- und Verfolgungsprotokolle werden nach einem bestimmten Zeitraum gelöscht, der in Adobe Campaign angegeben ist und geändert werden kann. Daher wird dringend empfohlen, die Stämme regelmäßig zu exportieren.

## Technische Tabellen {#technical-tables}

Schließlich besteht ein Teil des Datenmodells aus technischen Daten, die für den Anwendungsprozess verwendet werden, einschließlich Operatoren und Benutzerrechte (**NmsGroup**), Ordner (**XtkFolder**).