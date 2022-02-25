---
product: campaign
title: Erste Schritte mit Cubes
description: Erste Schritte mit Cubes
feature: Reporting
exl-id: ade4c857-9233-4bc8-9ba1-2fec84b7c3e6
source-git-commit: 81716a30a57d3ed8542b329d5fb9b0443fd4bf31
workflow-type: ht
source-wordcount: '735'
ht-degree: 100%

---

# Erste Schritte mit Cubes{#about-cubes}

![](../../assets/common.svg)

Die Analyse von Daten aus der Datenbank ist mithilfe des Moduls **Marketing Analytics** möglich. Damit können Daten analysiert und gemessen, Statistiken berechnet sowie die Erstellung und Berechnung von Berichten vereinfacht und optimiert werden. Ergänzend bietet Marketing Analytics die Möglichkeit, Berichte zu erstellen und darin Zielpopulationen zu konstruieren. Letztere können daraufhin in Listen gespeichert und z. B. als Zielgruppen von Sendungen in Adobe Campaign genutzt werden.

Cubes werden zur Erzeugung von bestimmten nativen Berichten genutzt, insbesondere in den Versandberichten (Versand-, Klick-, Öffnungsverfolgung etc.). Auf Cubes basierende Berichte dürfen standardmäßig nur für Datenvolumen unter 5 Millionen Zeilen genutzt werden.

Dies ermöglicht es, die Kapazitäten zur Datenexploration und -analyse optimal zu nutzen. Gleichzeitig wird die Konfiguration der Berichte und Tabellen für den Endbenutzer vereinfacht: Es muss nur ein existierender, vollständig konfigurierter Cube bei der Bericht- oder Tabellenerstellung ausgewählt werden, um dessen Berechnungen, Kennzahlen und Statistiken zu übernehmen.

Nach ihrer Erstellung und Konfiguration werden die Cubes in den Abfrage-Aktivitäten der Berichte und Webanwendungen genutzt. Sie können außerdem in Pivot-Tabellen verwendet und verändert werden.

>[!CAUTION]
>
>**Marketing Analytics** ist ein Adobe-Campaign-Modul. Es muss auf Ihrer Instanz installiert sein, damit Sie die unten beschriebenen Funktionen nutzen können.

Verwenden Sie das Marketing Analytics-Modul von Campaign, um:

1. Cubes zu erstellen

   * Daten zu aggregieren und in einer Arbeitstabelle zu speichern, um Indikatoren auf der Grundlage von Benutzeranforderungen im Voraus zu berechnen,
   * das in den verschiedenen Berechnungen der Berichte und Abfragen bewegte Datenenvolumen zu reduzieren und dadurch die Berechnungszeit der Indikatoren deutlich zu optimieren,
   * den Zugriff auf die Daten zu vereinfachen und den Benutzern die Möglichkeit zu geben, die Daten (ob voraggregiert oder nicht) in Abhängigkeit von verschiedenen Dimensionen zu bearbeiten.

   Weiterführende Informationen hierzu finden Sie unter [Erstellen von Indikatoren](../../reporting/using/creating-indicators.md).

1. Erstellen von Pivot-Tabellen

   * berechnete Daten und konfigurierte Kennzahlen zu analysieren,
   * die anzuzeigenden Daten sowie ihren Anzeigemodus auszuwählen,
   * die verwendeten Kennzahlen und Indikatoren zu personalisieren,
   * Benutzern mit nichttechnischem Hintergrund interaktive Tools zur Analyse anzubieten.

   Weitere Informationen hierzu finden Sie unter [Verwenden von Cubes zur Datenanalyse](../../reporting/using/using-cubes-to-explore-data.md).

1. Die Erstellung von Abfragen über in einem Cube berechnete und aggregierte Daten.
1. Die Identifizierung von Populationen und deren Referenzierung in Listen.

## Terminologie {#terminology}

Unten finden Sie eine Liste der spezifischen Begriffe bei der Arbeit mit Cubes.

* **Cube** – Ein Cube ist eine Darstellung mehrdimensionaler Informationen: Er bietet Endnutzern Strukturen für die interaktive Datenanalyse.

* **Faktentabelle/-schema** – Die Faktentabelle (oder das Faktenschema) enthält die Roh- oder Elementardaten, auf denen die Analysen basieren. Hierbei handelt es sich hauptsächlich um Tabellen mit großen Volumen (möglicherweise mit verknüpften Tabellen) und potenziell langen Berechnungen. Die Broadlog- oder die Bestelltabelle sind Beispiele für Faktentabellen.

* **Dimension** – Mit Dimensionen können Sie Daten in Gruppen unterteilen: Nach ihrer Erstellung dienen die Dimensionen als Analyseachsen. In den meisten Fällen werden für eine bestimmte Dimension mehrere Ebenen definiert. Für eine zeitliche Dimension beispielsweise sind die Ebenen Monate, Tage, Stunden, Minuten usw. Dieser Satz von Ebenen stellt die Dimensionshierarchie dar und ermöglicht verschiedene Ebenen der Datenanalyse.

* **Klassierung** – Für einige Felder können Sie eine Klassierung definieren, um Werte zu gruppieren und die Lesbarkeit der Informationen zu vereinfachen. Die Klassierung wird auf Ebenen angewendet. Es wird empfohlen, eine Klassierung zu definieren, wenn es viele verschiedene mögliche Werte gibt.

* **Kennzahlen** – Gängige Kennzahlen sind Summe, Durchschnitt, Maximum, Minimum, Standardabweichung etc. Kennzahlen können berechnet werden: Zum Beispiel bezeichnet die Annahmerate eines Angebots das Verhältnis der Anzahl der unterbreiteten Angebote verglichen mit der Anzahl der angenommenen Angebote.

## Arbeitsbereich Cube {#cube-workspace}

Cubes befinden sich im Knoten **[!UICONTROL Administration > Konfiguration > Cubes]**.

![](assets/s_advuser_cube_node.png)

Die hauptsächlichen Verwendungskontexte der Cubes sind folgende:

* Datenexporte können direkt in einem Bericht durchgeführt werden, der im Tab **[!UICONTROL Berichte]** der Adobe Campaign-Plattform konzipiert wurde.

   Erstellen Sie hierzu einen neuen Bericht und wählen Sie den zu verwendenden Cube.

   ![](assets/cube_create_new.png)

   Cubes stellen Vorlagen dar, auf deren Basis Berichte erstellt werden. Klicken Sie nach der Auswahl einer Vorlage auf die Schaltfläche **[!UICONTROL Erstellen]**, um den entsprechenden Bericht zu konfigurieren und zu visualisieren.

   Sie können die Kennzahlen anpassen, den Anzeigemodus ändern oder eine Tabelle konfigurieren und dann den Bericht über die zentrale Schaltfläche erzeugen.

   ![](assets/cube_display_new.png)

* Referenzierung in **[!UICONTROL Abfrage]**-Aktivitäten von Berichten zur Nutzung der Cube-Indikatoren:

   ![](assets/s_advuser_query_using_a_cube.png)

* Sie können außerdem eine auf einem Cube basierte Pivot-Tabelle in eine beliebige Seite eines Berichts einfügen. Referenzieren Sie hierzu den zu verwendenden Cube im Tab **[!UICONTROL Daten]** der Pivot-Tabelle der betreffenden Seite.

   ![](assets/s_advuser_cube_in_report.png)

   Weitere Informationen hierzu finden Sie unter [Erkunden der Daten in einem Bericht](../../reporting/using/using-cubes-to-explore-data.md#exploring-the-data-in-a-report).
