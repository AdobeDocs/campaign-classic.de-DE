---
title: Best Practices für das Reporting
description: Best Practices für Kampagnenberichte
page-status-flag: never-activated
uuid: 09de6a17-b3a7-4543-b672-b0a21653aa75
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: reporting-in-adobe-campaign
discoiquuid: 904961e0-7dff-4350-8d5d-e4bdd368b3ff
translation-type: ht
source-git-commit: 2a82493deada11cb22ef37d215b6eae8274ce890
workflow-type: ht
source-wordcount: '839'
ht-degree: 100%

---


# Best Practices für das Reporting{#best-practices-reporting}

## Bedarfsanalyse{#analyzing-needs}

Welches Reporting-Tool jeweils zum Einsatz kommt, hängt von der Menge der auszuwertenden Daten, ihrer Komplexität und dem gewünschten Berichtstyp ab.

Zur Optimierung von Erstellung, Verwendung und Beständigkeit eines Berichts müssen zunächst die Bedarfe genau bestimmt werden. Diese erste Analyse ermöglicht es, den zu verwendenden Berichtstyp sowie den passenden Erstellungsmodus zu finden. Sie sollte in folgenden Schritten durchgeführt werden:

1. Bedarf identifizieren

   Zunächst muss genau bestimmt werden, was im Bericht angezeigt werden und wozu er dienen soll (Monitoring, Analyse, Datenexport etc.).

   Adobe Campaign bietet zahlreiche Reporting-Funktionen.

   Sie können zum Beispiel:

   * Daten der Datenbank durchsuchen und Kennzahlen definieren. Weiterführende Informationen finden Sie [in diesem Abschnitt](../../reporting/using/about-cubes.md)
   * Indikatoren einem vorhandenen Bericht hinzufügen. Weiterführende Informationen finden Sie [in diesem Abschnitt](../../reporting/using/about-reports-creation-in-campaign.md)
   * die Daten in der Datenbank anzeigen. Weiterführende Informationen finden Sie [in diesem Abschnitt](../../reporting/using/about-descriptive-analysis.md)
   * Einen neuen Versandbericht erstellen. Weiterführende Informationen finden Sie [in diesem Abschnitt](../../reporting/using/about-reports-creation-in-campaign.md)),
   * Daten aus der Adobe-Campaign-Datenbank exportieren (mithilfe eines Workflows; siehe [diesen Abschnitt](../../workflow/using/about-workflows.md))
   * Eine Pivot-Tabelle erstellen. Weiterführende Informationen finden Sie [in diesem Abschnitt](../../reporting/using/creating-a-table.md#creating-a-breakdown-or-pivot-table)
   * Aggregierte Daten untersuchen. Weiterführende Informationen finden Sie [in diesem Abschnitt](../../reporting/using/about-cubes.md)
   * Einen Assistenten verwenden, um Daten zu analysieren. Weiterführende Informationen finden Sie [in diesem Abschnitt](../../reporting/using/about-descriptive-analysis.md)
   * Große Datenmengen analysieren. Weiterführende Informationen finden Sie [in diesem Abschnitt](../../reporting/using/about-reports-creation-in-campaign.md)

1. Zielgruppe des Berichts identifizieren

   Stellen Sie anschließend fest, für wen der Bericht, den Sie erstellen möchten, gedacht ist, wer ihn einsehen kann und in welchem Modus er angezeigt wird (in einem Browser, in Adobe Campaign, für eine bestimmte Anwendung oder die gesamte Plattform etc.).

   Sie können den Berichtzugriff zulassen für:

   * alle Adobe-Campaign-Benutzer,
   * Benutzer, die Berechtigungen zum Zugriff auf eine Marketingkampagne haben,
   * einen einzelnen Benutzer für punktuelle Einsichten,
   * alle Benutzer mit Webzugriff etc.

   Beachten Sie in diesem Zusammenhang auch eventuelle Problematiken bezüglich Zugriffsberechtigungen und Sicherheit.

1. Inhalt des Berichts definieren

   Bestimmen Sie, welcher Datentyp in Ihrem Bericht angezeigt werden soll: Indikatoren eines Versands, Profile der Datenbank etc.

   Sie sollten zudem die Art der verwendeten Daten (einfach, aus einer Berechnung stammend, besonders umfangreich etc.), ihre Lokalisierung (in Adobe Campaign oder einem externen System), ihr Volumen sowie ihre Aktualisierungshäufigkeit kennen, um die Berechnungsintervalle festzulegen (täglich, wöchentlich, in Echtzeit).

   Datenvolumen und -aktualisierung können gegebenenfalls die Anzeige des Berichts beeinträchtigen. Um Verzögerungen u. Ä. zu vermeiden, sollten entsprechende Problematiken zuvor aufmerksam überprüft werden. In diesem Zusammenhang wird empfohlen, Aggregate zu erstellen, um bestimmte Daten außerhalb des Berichts vorzuberechnen. Tracking- und Versandlogs enthaltende Tabellen können beispielsweise Millionen von Datensätzen erreichen: Diese Daten müssen in Workflows aggregiert werden, um in Berichten genutzt werden zu können.

## Berichterstellung optimieren{#optimizing-report-creation}

### Datenvolumen {#data-volume}

Um optimale Leistungen zu erreichen, dürfen die bewegten Datenvolumen nicht zu groß sein.

Folgendes ist zu beachten:

* Die Berechnungszeit eines Berichts darf niemals fünf Minuten überschreiten.

   Wenn bei kleinen Datenvolumen die Berechnung des Berichts in der Konzeptionsphase 60 Sekunden überschreitet, muss die angewendete Methode überdacht werden.

* Bei der Verwendung von Marketing Analytics dürfen die gemeldeten Daten 10 Millionen Zeilen nicht überschreiten.

Zudem wird empfohlen, Aggregate nachts bei wenig beanspruchter Datenbank zu berechnen und die aggregierten Daten direkt in den Berichten zu verwenden. Die Aggregate werden über dedizierte Data-Management-Workflows erstellt (SQL-Abfragen).

Sie haben auch die Möglichkeit, die Berichte nachts zu berechnen und automatisch einen Verlauf erstellen zu lassen, der jederzeit eingesehen werden kann. Diese Vorgehensweise vermeidet ebenfalls eine Überlastung der Datenbank.

### Abfragen {#queries}

Es wird empfohlen, JavaScript-Anschlussvorgänge zu vermeiden und ihnen SQL-Abfragen vorzuziehen. Wenn nötig, verwenden Sie eine Script-Aktivität in einem Workflow und löschen Sie die für die Berechnung verwendeten Daten. Nutzen Sie außerdem die Verlaufsdaten, um die Bearbeitungszeit zu verkürzen.

In diesem Fall lautet die Syntax wie folgt:

```
if(string(ctx@_historyId)!==""))
```

Die Abfragen, die die in den Berichten anzuzeigenden Daten abrufen, dürfen nicht zu komplex sein, insbesondere wenn sie sich auf die gesamte Datenbank beziehen. Zur Leistungsverbesserung kann es nützlich sein, die Daten vor Ausführung der Abfrage zu filtern: Die Berechnungen betreffen dann nur einen Teil der Daten.

### Leistungen {#performances}

Die oben stehenden Empfehlungen erlauben es, die Berechnung der Berichte zu optimieren.

Adobe Campaign empfiehlt Ihnen zusätzlich die folgenden Verbesserungsmöglichkeiten:

* Bearbeitung des Datenmodells: Vorrangige Verwendung indexierter Felder, um die Berechnungsleistungen zu verbessern.

   Zur einfachen Erkennung von indexierten Feldern ist in Adobe Campaign der Sortierungspfeil neben den Spaltentiteln rot unterstrichen, wenn das Feld indexiert ist.

   Weiterführende Informationen zu Indizes finden Sie in [diesem Abschnitt](../../configuration/using/data-model-best-practices.md#indexes).

* Sicherstellung, dass der Bericht skalierbar ist: Das Datenvolumen kann im Laufe der Zeit erheblich wachsen.

   Zudem können sich die in den Testphasen bewegten Volumen bedeutend vom tatsächlichen Produktionsvolumen unterscheiden. Testphasen dürfen daher nicht vernachlässigt werden.

   Schließlich müssen die Fristen der Datenbereinigung bekannt sein und bei Bedarf angepasst werden, um die Informationsverarbeitung zu erleichtern.

   Weiterführende Informationen zur Bereinigung und Datenspeicherung finden Sie in [diesem Abschnitt](../../configuration/using/data-model-best-practices.md#data-retention).

### Berichtexport {#exporting-reports}

Die mit dem Export von Berichten zusammenhängenden Empfehlungen finden sich in [diesem Abschnitt](../../reporting/using/actions-on-reports.md#exporting-a-report).
