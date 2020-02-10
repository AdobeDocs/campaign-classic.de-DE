---
title: Schnittmenge
seo-title: Schnittmenge
description: Schnittmenge
seo-description: null
page-status-flag: never-activated
uuid: a8ff7a66-6c12-4e3c-ad45-d11b34ca64ff
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: d0dd9c74-aad5-452e-a11d-c231dacd2aec
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# Schnittmenge{#intersection}

Die Aktivität **Schnittmenge** erzeugt ausgehend von den eingehenden Aktivitäten eine neue Population.

Dabei werden nur die in jeder der eingehenden Aktivitäten enthaltenen Populationen extrahiert. Die Zielgruppe wird aus allen eingehenden Ergebnissen erstellt, dies bedeutet, dass die vorgeschalteten Aktivitäten beendet sein müssen, bevor die Schnittmenge ausgeführt werden kann. Konfigurieren Sie die Aktivität, indem Sie einen Titel vergeben und die Optionen bezüglich des Ergebnisses auswählen.

![](assets/s_user_segmentation_inter.png)

Weitere Informationen zum Konfigurieren und Verwenden der Schnittstellenaktivität finden Sie unter Gemeinsame Daten [extrahieren (Schnittmenge)](../../workflow/using/targeting-data.md#extracting-joint-data--intersection-).

Markieren Sie die **[!UICONTROL Generate complement]** Option, wenn Sie die verbleibende Population verarbeiten möchten. Die Ergänzung enthält die Zusammenstellung der Ergebnisse aller eingehenden Aktivitäten abzüglich der Schnittmenge. Anschließend wird der Aktivität ein zusätzlicher Auslandsübergang wie folgt hinzugefügt:

![](assets/s_user_segmentation_inter_compl.png)

## Anwendungsbeispiel {#intersection-example}

Im vorliegenden Beispiel werden drei Abfragen erstellt. Gesucht werden die in jeder der drei Populationen enthaltenen Empfänger. Diese sollen in einer Liste gespeichert werden. Gehen Sie wie folgt vor:

1. After three simple queries, insert an **[!UICONTROL Intersection]** -type activity.

   Im vorliegenden Beispiel ruft die erste Abfrage alle männlichen Empfänger ab, die zweite alle Empfänger, die in Berlin leben, die dritte alle Empfänger zwischen 18 und 30 Jahre.

1. Konfigurieren Sie die Schnittmenge. To do this, select the **[!UICONTROL Keys only]** reconciliation method since the populations resulting from the queries contain consistent data.
1. Falls Sie in den Abfragen Zusatzdaten verwenden, können Sie sich dafür entscheiden, nur gemeinsame Daten beizubehalten, indem Sie die entsprechende Option ankreuzen.
1. If you wish to use the rest of the data (in regard to the queries but not their intersection), check the **[!UICONTROL Generate complement]** box.
1. Schließen Sie an die Schnittmengenaktivität und gegebenenfalls auch an das Komplement jeweils ein Listen-Update an.
1. Starten Sie den Workflow. Im vorliegenden Beispiel sind zwei Empfänger in allen drei eingehenden Abfragen enthalten. Das Komplement enthält die fünf Empfänger, die nur in einer oder zwei der drei Abfragen vorkommen.

   Das Ergebnis der Schnittmenge wird an die erste Listen-Update-Aktivität übermittelt. Das Ergebnis des Komplements wird an die zweite Listen-Update-Aktivität gesandt.

   ![](assets/intersection_example.png)

## Eingabeparameter {#input-parameters}

* tableName
* schema

Jedes eingehende Ereignis muss eine durch diese Parameter definierte Zielgruppe angeben.

## Ausgabeparameter {#output-parameters}

* tableName
* schema
* recCount

Dieser Satz von drei Werten identifiziert das Ziel, das sich aus der Schnittmenge ergibt. **[!UICONTROL tableName]** ist der Name der Tabelle, die die Zielkennungen aufzeichnet, das Schema der Population (normalerweise **[!UICONTROL schema]****[!UICONTROL nms:recipient]** **[!UICONTROL recCount]** ) und die Anzahl der Elemente in der Tabelle.
