---
solution: Campaign Classic
product: campaign
title: Über diesen Verwendungsfall
description: Erfahren Sie, wie Sie A/B-Tests mit einem speziellen Anwendungsfall durchführen.
audience: delivery
content-type: reference
topic-tags: a-b-testing
translation-type: tm+mt
source-git-commit: 50a10e16f320a67cb4ad0e31c1cbe8a9365b7887
workflow-type: tm+mt
source-wordcount: '244'
ht-degree: 30%

---


# Über diesen Verwendungsfall {#about-use-case}

Im vorliegenden Anwendungsbeispiel wird ein Zielgruppen-Workflow verwendet, um zwei Inhaltsversionen zu vergleichen. Der Text ist jeweils derselbe, nur die Aufmachung unterscheidet sich.

Die Zielgruppe ist in drei Gruppen unterteilt: zwei Testgruppen und die übrige Population. An jede Testgruppe wird eine andere Version des Versands gesendet.

Nach dem Versand wird eine Wartezeit von 5 Tagen konfiguriert, bevor die Ergebnisse der besten offenen Tarife erfasst werden. Der Inhalt des Versands mit dem höchsten Ergebnis wird dann durch ein Skript wiederhergestellt und an die Population gesendet, die nicht als Testgruppe verwendet wurde.

Die Auswahl der Siegerversion kann je nach Bedarf nach verschiedenen Kriterien erfolgen. Hierbei kann es sich beispielsweise um die Öffnungsrate, Klickrate, Anmelderate oder die Reaktivität handeln.

Darüber hinaus betraf der in diesem Anwendungsfall beschriebene Test nur zwei Versand, aber Sie können so viele Versionen wie nötig testen. Fügen Sie dem Workflow einfach Aktivitäten hinzu.

Die wichtigsten Schritte zur Durchführung dieses Anwendungsfalls sind:

* [Schritt 1: Erstellen eines Targeting-Workflows](../../delivery/using/a-b-testing-uc-targeting-workflow.md)
* [Schritt 2: Populationsmuster konfigurieren](../../delivery/using/a-b-testing-uc-population-samples.md)
* [Schritt 3: Zwei Versandvorlagen erstellen](../../delivery/using/a-b-testing-uc-delivery-templates.md)
* [Schritt 4: Versand im Workflow konfigurieren](../../delivery/using/a-b-testing-uc-configuring-deliveries.md)
* [Schritt 5: Skript erstellen](../../delivery/using/a-b-testing-uc-script.md)
* [Schritt 6: Definieren des endgültigen Versands](../../delivery/using/a-b-testing-uc-final-delivery.md)
* [Schritt 7: Beginn des Workflows](../../delivery/using/a-b-testing-uc-start-workflow.md)
* [Schritt 8: Ergebnis analysieren](../../delivery/using/a-b-testing-uc-analyzing.md)

**Verwandte Themen:**

* [Erste Schritte mit A/B-Tests](../../delivery/using/get-started-a-b-testing.md)
* [Konfigurieren von A/B-Tests](../../delivery/using/configuring-a-b-testing.md)
