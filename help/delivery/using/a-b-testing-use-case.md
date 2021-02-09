---
solution: Campaign Classic
product: campaign
title: Über diesen Verwendungsfall
description: Erfahren Sie, wie Sie A/B-Tests mit einem speziellen Anwendungsfall durchführen.
audience: delivery
content-type: reference
topic-tags: a-b-testing
translation-type: tm+mt
source-git-commit: 346b72d522c947b2a2552176b910ded8d622f3ab
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 31%

---


# Über diesen Verwendungsfall {#about-use-case}

Im vorliegenden Anwendungsbeispiel wird ein Zielgruppen-Workflow verwendet, um zwei Inhaltsversionen zu vergleichen. Der Text ist jeweils derselbe, nur die Aufmachung unterscheidet sich.

Die Zielgruppe ist in drei Gruppen unterteilt: zwei Testgruppen und die übrige Population. An jede Testgruppe wird eine andere Version des Versands gesendet.

Nach dem Versand wird eine Wartezeit von 5 Tagen konfiguriert, bevor die Ergebnisse der besten offenen Tarife erfasst werden. Der Inhalt des Versands mit dem höchsten Ergebnis wird dann durch ein Skript wiederhergestellt und an die Population gesendet, die nicht als Testgruppe verwendet wurde.

Die Auswahl der Siegerversion kann je nach Bedarf nach verschiedenen Kriterien erfolgen. Hierbei kann es sich beispielsweise um die Öffnungsrate, Klickrate, Anmelderate oder die Reaktivität handeln.

Darüber hinaus betraf der in diesem Anwendungsfall beschriebene Test nur zwei Versand, aber Sie können so viele Versionen wie nötig testen. Fügen Sie dem Workflow einfach Aktivitäten hinzu.

Die wichtigsten Schritte zur Durchführung dieses Anwendungsfalls sind:

* [Schritt 1: Erstellen eines Targeting-Workflows](#step-1--creating-a-targeting-workflow)
* [Schritt 2: Populationsmuster konfigurieren](#step-2--configuring-population-samples)
* [Schritt 3: Zwei Versandvorlagen erstellen](#step-3--creating-two-delivery-templates)
* [Schritt 4: Versand im Workflow konfigurieren](#step-4--configuring-the-deliveries-in-the-workflow)
* [Schritt 5: Skript erstellen](#step-5--creating-the-script)
* [Schritt 7: Beginn des Workflows](#step-7--starting-the-workflow)
* [Schritt 8: Analysieren Sie das Ergebnis](#step-8--analyzing-the-result).

**Verwandte Themen:**

* [Erste Schritte mit A/B-Tests](../../delivery/using/get-started-a-b-testing.md)
* [Konfigurieren von A/B-Tests](../../delivery/using/configuring-a-b-testing.md)
