---
product: campaign
title: Anwendungsfall für AB-Tests
description: Erfahren Sie anhand eines speziellen Anwendungsbeispiels, wie Sie A/B-Tests durchführen.
audience: delivery
content-type: reference
topic-tags: a-b-testing
exl-id: 4eb139a0-5342-4084-9f6d-d736e05bf1c6
source-git-commit: 895aa2fd4fa9c7c71c0073e9be33c12d4e92c9fa
workflow-type: tm+mt
source-wordcount: '244'
ht-degree: 98%

---

# Über dieses Anwendungsbeispiel {#about-use-case}

Im vorliegenden Anwendungsbeispiel wird ein Zielgruppen-Workflow verwendet, um zwei Inhaltsversionen zu vergleichen. Der Text ist jeweils derselbe, nur die Aufmachung unterscheidet sich.

Die Zielpopulation wird in drei Gruppen aufgeteilt: zwei Testgruppen und die restliche Population. An jede Testgruppe wird eine andere Version des Versands gesendet.

Nach dem Versand ist eine 5-tägige Wartezeit konfiguriert, bevor die Ergebnisse der besten Öffnungsraten gesammelt werden. Der Inhalt des Versands mit der höchsten Punktzahl wird dann von einem Skript wiederhergestellt und an die Population gesendet, die nicht als Testgruppe verwendet wurde.

Die Auswahl der Siegerversion kann je nach Bedarf nach verschiedenen Kriterien erfolgen. Hierbei kann es sich beispielsweise um die Öffnungsrate, Klickrate, Anmelderate oder Reaktivität handeln.

Darüber hinaus betrifft der in diesem Anwendungsfall beschriebene Test nur zwei Sendungen, Sie können aber so viele Versionen wie nötig testen. Fügen Sie dem Workflow einfach Aktivitäten hinzu.

Die wichtigsten Schritte zur Durchführung dieses Anwendungsbeispiels sind:

* [Schritt 1: Zielgruppen-Workflow erstellen](../../delivery/using/a-b-testing-uc-targeting-workflow.md)
* [Schritt 2: Testpopulation konfigurieren](../../delivery/using/a-b-testing-uc-population-samples.md)
* [Schritt 3: Zwei Versandvorlagen erstellen](../../delivery/using/a-b-testing-uc-delivery-templates.md)
* [Schritt 4: Sendungen im Workflow konfigurieren](../../delivery/using/a-b-testing-uc-configuring-deliveries.md)
* [Schritt 5: Skript erstellen](../../delivery/using/a-b-testing-uc-script.md)
* [Schritt 6: Endgültigen Versand festlegen](../../delivery/using/a-b-testing-uc-final-delivery.md)
* [Schritt 7: Workflow starten](../../delivery/using/a-b-testing-uc-start-workflow.md)
* [Schritt 8: Ergebnis analysieren](../../delivery/using/a-b-testing-uc-analyzing.md)

**Verwandte Themen:**

* [Erste Schritte mit A/B-Tests](../../delivery/using/get-started-a-b-testing.md)
* [A/B-Tests konfigurieren](../../delivery/using/configuring-a-b-testing.md)
