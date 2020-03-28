---
title: Versand (fortlaufend)
seo-title: Versand (fortlaufend)
description: Versand (fortlaufend)
seo-description: null
page-status-flag: never-activated
uuid: af8b4582-299e-47f9-9819-987b35db94ab
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: 9d80be19-8dde-4278-ab5f-23f364fe422e
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Versand (fortlaufend){#continuous-delivery}

Ein **fortlaufender Versand** bietet die Möglichkeit, Empfänger zu existierenden Versandaktionen hinzuzufügen. Auf diese Weise wird das wiederholte Erstellen von identischen Sendungen vermieden. Dies ist insbesondere für Benachrichtigungen, die regelmäßig, aber nicht zu planbaren Zeitpunkten versendet werden, interessant. In der Versandvorlage kann ein Script zur Berechnung des jeweiligen Titels (und des Kampagnenordners) definiert werden, sodass bei Berechnung eines noch nicht existierenden Titels der Versand automatisch erstellt wird.

![](assets/edit_diffusion_fil.png)

Dank der Option **[!UICONTROL Fehler verarbeiten]** erscheint eine spezifische Transition, wenn ein Fehler auftritt. In diesem Fall wird die Ausführung des Workflows nicht ausgesetzt, sondern fortgeführt.

Dies gilt für Fehler des Dateisystems (Datei kann nicht verschoben werden, Zugriff auf das Verzeichnis nicht möglich usw.).

Fehler, die aus der Konfiguration der Aktivität resultieren, beispielsweise durch Angabe von ungültigen Werten (z. B. inexistentes Verzeichnis), werden nicht verarbeitet.

## Eingabeparameter {#input-parameters}

* tableName
* schema

Jedes eingehende Ereignis muss eine durch diese Parameter definierte Zielgruppe angeben.

Dies gilt nur, wenn die Option **[!UICONTROL Wird durch das Eingangsereignis angegeben]** angekreuzt wurde.

## Ausgabeparameter {#output-parameters}

* tableName
* schema
* recCount

Anhand der drei Werte lässt sich die durch den wiederkehrenden Versand ermittelte Zielgruppe identifizieren. **[!UICONTROL tableName]** ist der Name der Tabelle, welche die Kennungen der Zielgruppenempfänger enthält, **[!UICONTROL schema]** ist das Schema der Population, (i. d. R. nms:recipient) und **[!UICONTROL recCount]** ist die Anzahl an Elementen in der Tabelle.

Die Transition des Komplements weist die gleichen Parameter auf.
