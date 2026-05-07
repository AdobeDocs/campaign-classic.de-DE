---
product: campaign
title: Anwendungsbeispiel für A/B-Tests
description: Erfahren Sie anhand eines speziellen Anwendungsbeispiels, wie Sie A/B-Tests durchführen
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
feature: A/B Testing
role: User
exl-id: 4eb139a0-5342-4084-9f6d-d736e05bf1c6
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 65%

---

# AB-Tests: A/B-Tests für diesen Anwendungsfall {#ab-testing-use-case}

In diesem Anwendungsbeispiel werden wir zwei E-Mail-Versandinhalte mithilfe eines Zielgruppen-Workflows vergleichen. Nachricht und Text sind bei beiden Sendungen identisch, nur das Layout ändert sich.

Die Zielpopulation wird in drei Gruppen unterteilt: zwei Testgruppen und die restliche Population. An jede Testgruppe wird eine andere Version des Versands gesendet.

Nach dem Versand ist eine 5-tägige Wartezeit konfiguriert, bevor die Ergebnisse der besten Öffnungsraten gesammelt werden. Der Inhalt des Versands mit der höchsten Punktzahl wird dann von einem Script wiederhergestellt und an die Population gesendet, die nicht als Testgruppe verwendet wurde.

Bitte beachten Sie, dass die Kriterien, die entscheiden, welcher Versand der beste ist, an Ihre Bedürfnisse angepasst werden können. Dabei kann es sich um die Öffnungsrate, die Clickthrough-Rate, die Abonnementrate, die Reaktionsrate usw. handeln.

Darüber hinaus betrifft der in diesem Anwendungsfall beschriebene Test nur zwei Sendungen, Sie können aber so viele Versionen wie nötig testen. Fügen Sie dem Workflow einfach Aktivitäten hinzu.

Die wichtigsten Schritte zur Durchführung dieses Anwendungsbeispiels sind:

* [Schritt 1: Zielgruppen-Workflow erstellen](a-b-testing-uc-targeting-workflow.md)
* [Schritt 2: Testpopulation konfigurieren](a-b-testing-uc-population-samples.md)
* [Schritt 3: Zwei Versandvorlagen erstellen](a-b-testing-uc-delivery-templates.md)
* [Schritt 4: Sendungen im Workflow konfigurieren](a-b-testing-uc-configuring-deliveries.md)
* [Schritt 5: Script erstellen](a-b-testing-uc-script.md)
* [Schritt 6: Endgültigen Versand festlegen](a-b-testing-uc-final-delivery.md)
* [Schritt 7: Workflow starten](a-b-testing-uc-start-workflow.md)
* [Schritt 8: Ergebnis analysieren](a-b-testing-uc-analyzing.md)

**Verwandte Themen:**

* [Erste Schritte mit A/B-Tests](get-started-a-b-testing.md)
* [A/B-Tests konfigurieren](configuring-a-b-testing.md)
