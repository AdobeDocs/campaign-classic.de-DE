---
title: Best Practices für das Reporting
description: Best Practices für Kampagne Berichte
page-status-flag: never-activated
uuid: 09de6a17-b3a7-4543-b672-b0a21653aa75
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: reporting-in-adobe-campaign
discoiquuid: 904961e0-7dff-4350-8d5d-e4bdd368b3ff
translation-type: tm+mt
source-git-commit: 2a82493deada11cb22ef37d215b6eae8274ce890
workflow-type: tm+mt
source-wordcount: '839'
ht-degree: 85%

---


# Best Practices des Berichte{#best-practices-reporting}

## Bedarfsanalyse{#analyzing-needs}

Welches Reporting-Tool jeweils zum Einsatz kommt, hängt von der Menge der auszuwertenden Daten, ihrer Komplexität und dem gewünschten Berichtstyp ab.

Zur Optimierung von Erstellung, Verwendung und Beständigkeit eines Berichts müssen zunächst die Bedarfe genau bestimmt werden. Diese erste Analyse ermöglicht es, den zu verwendenden Berichtstyp sowie den passenden Erstellungsmodus zu finden. Sie sollte in folgenden Schritten durchgeführt werden:

1. Bedarf identifizieren

   Zunächst muss genau bestimmt werden, was im Bericht angezeigt werden und wozu er dienen soll (Monitoring, Analyse, Datenexport etc.).

   Adobe Campaign bietet zahlreiche Reporting-Funktionen.

   Sie können zum Beispiel:

   * Untersuchen Sie die Daten in der Datenbank und definieren Sie Messungen. Weiterführende Informationen finden Sie [in diesem Abschnitt](../../reporting/using/about-cubes.md)
   * hinzufügen Indikatoren zu einem vorhandenen Bericht. Weiterführende Informationen finden Sie [in diesem Abschnitt](../../reporting/using/about-reports-creation-in-campaign.md)
   * Ansicht der Daten in der Datenbank. Weiterführende Informationen finden Sie [in diesem Abschnitt](../../reporting/using/about-descriptive-analysis.md)
   * Erstellen Sie einen neuen Versand-Bericht. Weiterführende Informationen finden Sie [in diesem Abschnitt](../../reporting/using/about-reports-creation-in-campaign.md)),
   * Export data from the Adobe Campaign database (via a workflow, refer to [this section](../../workflow/using/about-workflows.md)
   * Erstellen Sie eine Pivot-Tabelle. Weiterführende Informationen finden Sie [in diesem Abschnitt](../../reporting/using/creating-a-table.md#creating-a-breakdown-or-pivot-table)
   * Untersuchen Sie aggregierte Daten. Weiterführende Informationen finden Sie [in diesem Abschnitt](../../reporting/using/about-cubes.md)
   * Verwenden Sie einen Assistenten, um Daten zu analysieren. Weiterführende Informationen finden Sie [in diesem Abschnitt](../../reporting/using/about-descriptive-analysis.md)
   * Analysieren Sie große Datenmengen. Weiterführende Informationen finden Sie [in diesem Abschnitt](../../reporting/using/about-reports-creation-in-campaign.md)

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

* Bei Verwendung des Marketing Analytics-Moduls dürfen die Daten des Berichte 10 Millionen Zeilen nicht überschreiten.

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

* Arbeiten Sie an Ihrem Datenmodell: Indexierte Felder müssen hauptsächlich zur Verbesserung der Berechnungsformeln verwendet werden.

   Zur einfachen Erkennung von indexierten Feldern ist in Adobe Campaign der Sortierungspfeil neben den Spaltentiteln rot unterstrichen, wenn das Feld indexiert ist.

   For more on indexes, refer to [this section](../../configuration/using/data-model-best-practices.md#indexes).

* Stellen Sie sicher, dass der Bericht skalierbar ist: kann das Datenvolumen im Laufe der Zeit erheblich ansteigen.

   Zudem können sich die in den Testphasen bewegten Volumen bedeutend vom tatsächlichen Produktionsvolumen unterscheiden. Testphasen dürfen daher nicht vernachlässigt werden.

   Schließlich müssen die Fristen der Datenbereinigung bekannt sein und bei Bedarf angepasst werden, um die Informationsverarbeitung zu erleichtern.

   Weitere Informationen zur Bereinigung und Datenspeicherung finden Sie in [diesem Abschnitt](../../configuration/using/data-model-best-practices.md#data-retention).

### Berichtexport {#exporting-reports}

Die mit dem Export von Berichten zusammenhängenden Empfehlungen finden sich in [diesem Abschnitt](../../reporting/using/actions-on-reports.md#exporting-a-report).
