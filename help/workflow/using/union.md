---
title: Vereinigung
seo-title: Vereinigung
description: Vereinigung
seo-description: null
page-status-flag: never-activated
uuid: 987e106e-c414-4db4-a93e-96e43dc04370
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: 573021ad-1efb-4156-af6d-417737ce745a
translation-type: ht
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: ht
source-wordcount: '311'
ht-degree: 100%

---


# Vereinigung{#union}

Über eine Vereinigung lassen sich die Ergebnisse mehrerer eingehender Transitionen in einer Zielgruppe zusammenfassen. Die Zielgruppe wird aus allen eingehenden Ergebnissen erstellt, dies bedeutet, dass die vorgeschalteten Aktivitäten beendet sein müssen, bevor die Vereinigung ausgeführt werden kann.

![](assets/s_user_segmentation_union.png)

>[!NOTE]
>
>Weitere Informationen zur Konfiguration und Verwendung der Vereinigungsaktivität finden Sie unter [Populationen vereinen (Vereinigung)](../../workflow/using/targeting-data.md#combining-several-targets--union-).

## Anwendungsbeispiel {#union-example}

Im folgenden Beispiel sollen die Ergebnisse zweier Abfragen zusammengefasst werden, um eine Liste zu aktualisieren. Beide Abfragen betreffen Empfänger. Die Ergebnisse basieren also auf derselben Tabelle.

1. Schließen Sie unmittelbar an die zwei Abfragen eine **[!UICONTROL Vereinigung]** an, gefolgt von einem Listen-Update.
1. Benennen Sie die Aktivität.
1. Wählen Sie als Abstimmoption **[!UICONTROL Nur die Schlüssel]**, da im vorliegenden Beispiel die aus den Abfragen stammenden Populationen homogen sind.
1. Falls Sie in den Abfragen Zusatzdaten verwenden, können Sie sich dafür entscheiden, nur gemeinsame Daten beizubehalten.
1. Bei Bedarf können Sie außerdem die Option **[!UICONTROL Größe der erzeugten Population begrenzen]** aktivieren.

   Geben Sie in diesem Fall die Anzahl an beizubehaltenden Empfängern und die vorrangig zu berücksichtigende Abfrage an.

1. Validieren Sie die Vereinigungsaktivität und konfigurieren Sie das Listen-Update (siehe [Listen-Update](../../workflow/using/list-update.md)).
1. Starten Sie dann den Workflow. Die Anzahl an in der Ergebnismenge enthaltenen Kontakten wird angezeigt und die in der Update-Aktivität angegebene Liste wird erstellt oder aktualisiert. Letztere enthält nun alle Empfänger aus den beiden Abfragen bzw. die im vorangehenden Schritt definierte Anzahl.

   ![](assets/union_example.png)

## Eingabeparameter {#input-parameters}

* tableName
* schema

Jedes eingehende Ereignis muss eine durch diese Parameter definierte Zielgruppe angeben.

## Ausgabeparameter {#output-parameters}

* tableName
* schema
* recCount

Anhand der drei Werte lässt sich die durch die Vereinigung ermittelte Zielgruppe identifizieren. **[!UICONTROL tableName]** ist der Name der Tabelle, welche die Kennungen der Zielgruppenempfänger enthält, **[!UICONTROL schema]** ist das Schema der Population, (i. d. R. nms:recipient) und **[!UICONTROL recCount]** ist die Anzahl an Elementen in der Tabelle.
