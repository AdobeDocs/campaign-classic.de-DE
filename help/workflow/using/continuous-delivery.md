---
solution: Campaign Classic
product: campaign
title: Versand (fortlaufend)
description: Versand (fortlaufend)
audience: workflow
content-type: reference
topic-tags: action-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 100%

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

## Einrichten eines Versands (fortlaufend)

In diesem Abschnitt wird beschrieben, wie Sie einen Versand (fortlaufend) einrichten.

Beim **fortlaufenden Versand** können Sie einem bestehenden Versand neue Empfänger hinzufügen, sodass Sie nicht jedes Mal einen neuen Versand erstellen müssen, wenn ein neuer Empfänger hinzugefügt wird. Sie können die kreativen Inhalte direkt im Kampagnen-Workflow aktualisieren, wodurch die Vorlage im Ressourcen-Ordner für Versandvorlagen aktualisiert wird.

Bei einem fortlaufenden Versand wird EIN Versand erstellt. Versandlogs (Broadlog) und Trackinglogs, die auf diesen Versand verweisen, werden bei jeder Ausführung hinzugefügt.

![Versand (fortlaufend)](assets/delivery_continuous.jpg)

In diesem Video wird gezeigt, wie man einen fortlaufenden Versand mit einer inkrementellen Abfrage konfiguriert.

>[!VIDEO](https://video.tv.adobe.com/v/25039?quality=12)
