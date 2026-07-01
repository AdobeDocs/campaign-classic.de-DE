---
product: campaign
title: Schnittmenge
description: Schnittmenge
feature: Workflows, Targeting Activity
hide: true
exl-id: f426bf02-9899-49eb-b699-728d51b57c64
TQID: https://experienceleague.adobe.com/mc1GRKb345bJX0ConrlwvLbPeeFK8YLDQIhs2Gp7h68
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
subfeature_v2:
  - id: ee25c34b-ea50-427b-9369-ba0a160f7d70
  - id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22f
  - id: d1110311-2ca4-442b-be37-088a6db845ee
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 443
ht-degree: 100%

---

# Schnittmenge{#intersection}

>[!CONTEXTUALHELP]
>id="ac_workflow_intersection"
>title="Aktivität &quot;Schnittmenge&quot;"
>abstract="Eine Aktivität des Typs &quot;Schnittmenge&quot; erzeugt eine Zielgruppe aus der Schnittmenge der empfangenen Zielgruppen. Über eine Schnittmenge lassen sich nur die Populationen extrahieren, die in allen eingehenden Aktivitätsergebnissen enthalten sind."

Die Aktivität **Schnittmenge** erzeugt ausgehend von den eingehenden Aktivitäten eine neue Population.

Über eine Schnittmenge lassen sich nur die Populationen extrahieren, die in allen eingehenden Aktivitätsergebnissen enthalten sind. Die Zielgruppe wird mit allen eingehenden Ergebnissen erstellt. Alle vorherigen Aktivitäten müssen daher abgeschlossen sein, bevor die Schnittmenge ausgeführt werden kann. Um diese Aktivität zu konfigurieren, müssen Sie einen Titel für sie sowie die Optionen für das Ergebnis eingeben.

![](assets/s_user_segmentation_inter.png)

Weitere Informationen zur Konfiguration und Verwendung der Schnittmengenaktivität finden Sie unter [Gemeinsame Daten aus Populationen extrahieren (Schnittmenge)](targeting-data.md#extracting-joint-data--intersection-).

Aktivieren Sie die Option **[!UICONTROL Komplement erzeugen]**, wenn Sie auch die nicht in der Schnittmenge enthaltene Population verwenden möchten. Das Komplement enthält die Vereinigung der Ergebnisse aller eingehenden Aktivitäten abzüglich der Schnittmenge. Die Aktivität weist somit, wie unten abgebildet, eine zusätzliche ausgehende Transition auf:

![](assets/s_user_segmentation_inter_compl.png)

## Anwendungsbeispiel für eine Schnittmenge {#intersection-example}

Im vorliegenden Beispiel werden drei Abfragen erstellt. Gesucht werden die in jeder der drei Populationen enthaltenen Empfänger. Diese sollen in einer Liste gespeichert werden. Gehen Sie wie folgt vor:

1. Schließen Sie eine **[!UICONTROL Schnittmenge]** an drei Abfrageaktivitäten an.

   Im vorliegenden Beispiel ruft die erste Abfrage alle männlichen Empfänger ab, die zweite alle Empfänger, die in Berlin leben, die dritte alle Empfänger zwischen 18 und 30 Jahre.

1. Konfigurieren Sie die Schnittmenge. Wählen Sie als Abstimmoption **[!UICONTROL Nur die Schlüssel]**, da im vorliegenden Beispiel die aus den Abfragen stammenden Populationen homogen sind.
1. Falls Sie in den Abfragen Zusatzdaten verwenden, können Sie sich dafür entscheiden, nur gemeinsame Daten beizubehalten, indem Sie die entsprechende Option ankreuzen.
1. Kreuzen Sie die Option **[!UICONTROL Komplement erzeugen]** an, wenn Sie die Ergebnisse der Abfragen (abzüglich der Schnittmenge) im weiteren Verlauf des Workflows verwenden möchten.
1. Fügen Sie nach dem Ergebnis der Schnittmenge eine Aktivität des Typs „Listen-Update“ hinzu. Sie können ein Listen-Update auch einem Komplement hinzufügen, wenn Sie dies möchten.
1. Führen Sie den Workflow aus. Hier entsprechen zwei Empfangende gleichzeitig allen drei eingegebenen Abfragen. Das Komplement besteht aus bis zu fünf Empfangenden, die nur einer oder zwei der drei Abfragen entsprechen.

   Das Ergebnis der Schnittmenge wird an das erste Listen-Update gesendet. Wenn Sie sich für die Verwendung des Komplements entschieden haben, wird es auch an das zweite Listen-Update gesendet.

   ![](assets/intersection_example.png)

## Eingabeparameter {#input-parameters}

* tableName
* schema

Jedes eingehende Ereignis muss eine durch diese Parameter definierte Zielgruppe angeben.

## Ausgabeparameter {#output-parameters}

* tableName
* schema
* recCount

Anhand der drei Werte lässt sich die durch die Schnittmenge ermittelte Zielgruppe identifizieren. **[!UICONTROL tableName]** ist der Name der Tabelle, die die Zielgruppenidentifizierungen enthält, **[!UICONTROL schema]** ist das Schema der Population, (i. d. R. **[!UICONTROL nms:recipient]**) und **[!UICONTROL recCount]** ist die Anzahl an Elementen in der Tabelle.

