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
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Versand (fortlaufend){#continuous-delivery}

Ein **fortlaufender Versand** bietet die Möglichkeit, Empfänger zu existierenden Versandaktionen hinzuzufügen. Auf diese Weise wird das wiederholte Erstellen von identischen Sendungen vermieden. Dies ist insbesondere für Benachrichtigungen, die regelmäßig, aber nicht zu planbaren Zeitpunkten versendet werden, interessant. In der Versandvorlage kann ein Script zur Berechnung des jeweiligen Titels (und des Kampagnenordners) definiert werden, sodass bei Berechnung eines noch nicht existierenden Titels der Versand automatisch erstellt wird.

![](assets/edit_diffusion_fil.png)

Die **[!UICONTROL Process errors]** Option zeigt einen bestimmten Übergang an, der aktiviert wird, wenn ein Fehler erzeugt wird. In diesem Fall wird der Workflow nicht in den Fehlermodus versetzt und fährt mit der Ausführung fort.

Dies gilt für Fehler des Dateisystems (Datei kann nicht verschoben werden, Zugriff auf das Verzeichnis nicht möglich usw.).

Fehler, die aus der Konfiguration der Aktivität resultieren, beispielsweise durch Angabe von ungültigen Werten (z. B. inexistentes Verzeichnis), werden nicht verarbeitet.

## Eingabeparameter {#input-parameters}

* tableName
* schema

Jedes eingehende Ereignis muss eine durch diese Parameter definierte Zielgruppe angeben.

Nur, wenn die **[!UICONTROL Specified by the inbound event]** Option ausgewählt ist.

## Ausgabeparameter {#output-parameters}

* tableName
* schema
* recCount

Dieser Satz von drei Werten identifiziert das Ziel, das sich aus der on-the-fly-Bereitstellung ergibt. **[!UICONTROL tableName]** ist der Name der Tabelle, in der die Bezeichner des Ziels gespeichert werden, das Schema der Population (normalerweise nms:empfänger) und die Anzahl der Elemente in der Tabelle **[!UICONTROL schema]** ist **[!UICONTROL recCount]** dies.

Die Transition des Komplements weist die gleichen Parameter auf.
