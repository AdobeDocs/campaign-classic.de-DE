---
product: campaign
title: Best Practices für das Reporting
description: Best Practices für Kampagnenberichte
feature: Reporting, Monitoring
badge: label="v7" type="Informative" tooltip="Gilt nur für Campaign Classic v7"
exl-id: 0c7f00f3-b16d-41c5-a7b1-f5a59201bf8c
TQID: https://experienceleague.adobe.com/0NZ2bS4K-X1okyD-snv-pBDekzNqmFV5soF-qUOOVKo
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: a658c786-869b-4194-a780-2594d663adda
subfeature_v2:
  - id: af6750fd-3c1b-4ad2-9fe3-99e81510998d
  - id: fcb46c0f-76e1-48bc-9dd0-fcf9d97526cf
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
  - id: c2be0313-b3ae-45e0-b454-d20bf54b23f2
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
  - id: ebde5b41-29c9-4f5e-9ef6-1197e85409e3
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 857
ht-degree: 66%

---

# Best Practices für das Reporting{#best-practices-reporting}



## Bedarfsanalyse{#analyzing-needs}

Welches Reporting-Tool jeweils zum Einsatz kommt, hängt von der Menge der auszuwertenden Daten, ihrer Komplexität und dem gewünschten Berichtstyp ab.

Um die Erstellung, Verwendung und Dauerhaftigkeit eines Berichts zu optimieren, müssen Sie sich die Bedürfnisse, die Sie erfüllen möchten, genau ansehen. Mit dieser ersten Analyse können Sie den zu erstellenden Berichtstyp und den besten Erstellungsmodus ermitteln. Gehen Sie wie folgt vor, um den Bericht zu erstellen:

1. Bedarf identifizieren

   Zunächst muss genau bestimmt werden, was im Bericht angezeigt werden und wozu er dienen soll (Monitoring, Analyse, Datenexport etc.).

   Adobe Campaign bietet eine breite Palette von Berichtskapazitäten. Es ist wichtig, Ihren Bedarf zu analysieren, um die am besten geeignete Funktion zu identifizieren.

   Sie können zum Beispiel:

   * Daten der Datenbank durchsuchen und Kennzahlen definieren. Weiterführende Informationen finden Sie [in diesem Abschnitt](../../reporting/using/ac-cubes.md)
   * Indikatoren einem vorhandenen Bericht hinzufügen. Weiterführende Informationen finden Sie [in diesem Abschnitt](../../reporting/using/about-reports-creation-in-campaign.md)
   * die Daten in der Datenbank anzeigen. Weiterführende Informationen finden Sie [in diesem Abschnitt](../../reporting/using/about-descriptive-analysis.md)
   * Einen neuen Versandbericht erstellen. Weiterführende Informationen finden Sie [in diesem Abschnitt](../../reporting/using/about-reports-creation-in-campaign.md)),
   * Daten aus der Adobe Campaign-Datenbank exportieren (mithilfe eines Workflows; siehe [diesen Abschnitt](../../workflow/using/about-workflows.md))
   * Eine Pivot-Tabelle erstellen. Weiterführende Informationen finden Sie [in diesem Abschnitt](../../reporting/using/creating-a-table.md#creating-a-breakdown-or-pivot-table)
   * Aggregierte Daten untersuchen. Weiterführende Informationen finden Sie [in diesem Abschnitt](../../reporting/using/ac-cubes.md)
   * Verwenden Sie einen Assistenten, um Daten zu analysieren. Weiterführende Informationen finden Sie [in diesem Abschnitt](../../reporting/using/about-descriptive-analysis.md)
   * Große Datenmengen analysieren. Weiterführende Informationen finden Sie [in diesem Abschnitt](../../reporting/using/about-reports-creation-in-campaign.md)

1. Zielpopulation des Berichts identifizieren

   Stellen Sie anschließend fest, für wen der Bericht, den Sie erstellen möchten, gedacht ist, wer ihn einsehen kann und in welchem Modus er angezeigt wird (in einem Browser, in Adobe Campaign, für eine bestimmte Anwendung oder die gesamte Plattform usw.).

   Sie können den Berichtzugriff zulassen für:

   * alle Adobe Campaign-Benutzer,
   * Benutzer, die Berechtigungen zum Zugriff auf eine Marketing-Kampagne haben,
   * einen einzelnen Benutzer für punktuelle Einsichten,
   * alle Benutzer mit Webzugriff etc.

   Beachten Sie in diesem Zusammenhang auch eventuelle Problematiken bezüglich Zugriffsberechtigungen und Sicherheit.

1. Inhalt des Berichts definieren

   Bestimmen Sie, welcher Datentyp in Ihrem Bericht angezeigt werden soll: Versandindikatoren, Profile der Datenbank etc.

   Sie sollten zudem die Art der verwendeten Daten (einfach, aus einer Berechnung stammend, besonders umfangreich etc.), ihre Lokalisierung (in Adobe Campaign oder einem externen System), ihr Volumen sowie ihre Aktualisierungshäufigkeit kennen, um die Berechnungsintervalle festzulegen (täglich, wöchentlich, in Echtzeit).

   Die Probleme im Zusammenhang mit Datenmengen und Aktualisierungen müssen sorgfältig untersucht werden, um Probleme bei der Anzeige von Berichten zu vermeiden, insbesondere in Bezug auf die Zeit. Es wird daher empfohlen, Aggregate zu erstellen, um einige Daten außerhalb des Berichts vorab zu berechnen. Tabellen, die die Tracking- und Versandlogs enthalten, können Millionen von Datensätzen enthalten: Das bedeutet, dass die Daten über einen Workflow aggregiert werden müssen, damit sie in einem Bericht verwendet werden können.

## Optimieren des Berichts-Designs{#optimizing-report-creation}

### Datenvolumen {#data-volume}

Um optimale Performance zu erreichen, dürfen die bewegten Datenvolumen nicht zu groß sein.

Folgendes ist zu beachten:

* Die Berechnungszeit eines Berichts darf niemals fünf Minuten überschreiten.

  Wenn bei kleinen Datenvolumen die Berechnung des Berichts in der Konzeptionsphase 60 Sekunden überschreitet, muss die angewendete Methode überdacht werden.

* Bei der Verwendung von Marketing Analytics dürfen die gemeldeten Daten 10 Millionen Zeilen nicht überschreiten.

Es wird außerdem empfohlen, die Aggregate nachts zu berechnen und diese aggregierten Daten direkt in den Berichten zu verwenden. Diese Aggregate müssen über dedizierte Daten-Management-Workflows (SQL-Abfragen) erstellt werden.

Sie haben auch die Möglichkeit, die Berichte nachts zu berechnen und automatisch einen Verlauf erstellen zu lassen, der jederzeit eingesehen werden kann. Diese Vorgehensweise vermeidet ebenfalls eine Überlastung der Datenbank.

### Abfragen {#queries}

Es wird empfohlen, nach Möglichkeit SQL-Abfragen zu verwenden und eine Nachbearbeitung in JavaScript zu vermeiden. Verwenden Sie bei Bedarf eine Script -Aktivität in einem Workflow und löschen Sie die für die Berechnung verwendeten Daten. Sie können auch archivierte Daten verwenden, um die Verarbeitungszeit zu beschleunigen.

In diesem Fall lautet die Syntax wie folgt:

```
if(string(ctx@_historyId)!==""))
```

Abfragen, mit denen Sie die in den Berichten angezeigten Daten erfassen können, dürfen nicht zu komplex sein, insbesondere dann nicht, wenn sie auf alle Daten in der Datenbank angewendet werden. Um die Leistung zu verbessern, kann es nützlich sein, die Daten zu filtern, bevor diese Abfragen ausgeführt werden: Dies bedeutet, dass die Berechnung nur einen Teil der Daten betrifft.

### Performance {#performances}

Die oben stehenden Empfehlungen erlauben es, die Berechnung der Berichte zu optimieren.

Adobe Campaign empfiehlt Ihnen zusätzlich die folgenden Verbesserungsmöglichkeiten:

* Bearbeitung des Datenmodells: Verwendung indizierter Felder vorrangig zum Verbessern der Berechnungsformeln.

  Zur einfachen Erkennung von indexierten Feldern ist in Adobe Campaign der Sortierungspfeil neben den Spaltentiteln rot unterstrichen, wenn das Feld indexiert ist.

  Weiterführende Informationen zu Indizes finden Sie in [diesem Abschnitt](../../configuration/using/data-model-best-practices.md#indexes).

* Sicherstellung, dass der Bericht skalierbar ist: Das Datenvolumen kann im Laufe der Zeit erheblich wachsen.

  Ebenso kann das während der Testphasen bearbeitete Datenvolumen vom tatsächlichen Datenvolumen in der Produktion abweichen. Daher sind Testphasen wichtig.

  Schließlich müssen die Fristen der Datenbereinigung bekannt sein und bei Bedarf angepasst werden, um die Informationsverarbeitung zu erleichtern.

  Weiterführende Informationen zur Bereinigung und Datenspeicherung finden Sie in [diesem Abschnitt](../../configuration/using/data-model-best-practices.md#data-retention).

### Exportieren der Berichte {#exporting-reports}

Die mit dem Export von Berichten zusammenhängenden Empfehlungen finden sich in [diesem Abschnitt](../../reporting/using/actions-on-reports.md#exporting-a-report).
