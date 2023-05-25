---
product: campaign
title: Anwendungsbeispiel für A/B-Tests
description: Erfahren Sie anhand eines speziellen Anwendungsbeispiels, wie Sie A/B-Tests durchführen
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: A/B Testing
exl-id: 4eb139a0-5342-4084-9f6d-d736e05bf1c6
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: ht
source-wordcount: '246'
ht-degree: 100%

---

# A/B-Test dieses Anwendungsfalls {#ab-testing-use-case}



Im vorliegenden Anwendungsbeispiel wird ein Zielgruppen-Workflow verwendet, um zwei Inhaltsversionen zu vergleichen. Der Text ist jeweils derselbe, nur die Aufmachung unterscheidet sich.

Die Zielpopulation wird in drei Gruppen aufgeteilt: zwei Testgruppen und die restliche Population. An jede Testgruppe wird eine andere Version des Versands gesendet.

Nach dem Versand ist eine 5-tägige Wartezeit konfiguriert, bevor die Ergebnisse der besten Öffnungsraten gesammelt werden. Der Inhalt des Versands mit der höchsten Punktzahl wird dann von einem Script wiederhergestellt und an die Population gesendet, die nicht als Testgruppe verwendet wurde.

Die Auswahl der Siegerversion kann je nach Bedarf nach verschiedenen Kriterien erfolgen. Hierbei kann es sich beispielsweise um die Öffnungsrate, Klickrate, Anmelderate oder Reaktivität handeln.

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
