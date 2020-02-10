---
title: Verwenden der Tabelle Adobe Campaign Classic Empfänger
description: Erfahren Sie, wie Sie die vordefinierte Empfängertabelle in Adobe Campaign Classic beim Entwerfen Ihres Datenmodells verwenden.
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


# Erweitern des Datenmodells{#extending-data-model}

Wenn Sie mit Adobe Campaign beginnen, müssen Sie das Standarddatenmodell bewerten, um zu überprüfen, welche Tabelle am besten zur Speicherung Ihrer Marketingdaten geeignet ist.

Falls relevant, können Sie die standardmäßige Empfängertabelle mit den vordefinierten Feldern verwenden, wie in diesem [Abschnitt](../../configuration/using/default-recipient-table.md)beschrieben.

Bei Bedarf können Sie ihn um zwei Mechanismen erweitern:

* Erweitern einer vorhandenen Tabelle mit neuen Feldern Beispielsweise können Sie der Tabelle &quot;Empfänger&quot;ein neues Feld &quot;Loyalität&quot;hinzufügen.
* Erstellen Sie eine neue Tabelle, z. B. eine &quot;Kauf&quot;-Tabelle, in der alle von den einzelnen Profilen der Datenbank getätigten Käufe aufgelistet sind, und verknüpfen Sie diese mit der Empfängertabelle.

Weitere Informationen zum Konfigurieren von Erweiterungsschemata zum Erweitern des konzeptionellen Datenmodells finden Sie unter [Informationen zur Schemaausgabe](../../configuration/using/about-schema-edition.md).

>[!IMPORTANT]
>
>Die Erweiterung des Datenmodells ist für fortgeschrittene Benutzer reserviert.
