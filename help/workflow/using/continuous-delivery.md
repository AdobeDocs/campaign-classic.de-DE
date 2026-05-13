---
product: campaign
title: Versand (fortlaufend)
description: Versand (fortlaufend)
feature: Workflows, Channels Activity
hide: true
exl-id: 9c228cdb-331e-476e-a24c-3c7e23add3bf
TQID: https://experienceleague.adobe.com/ed2gcvqkoOttP8-f0EJlyxWZMc5J2VaZS5FIFo-a6jA
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 377
ht-degree: 70%

---

# Versand (fortlaufend){#continuous-delivery}



Mit **Aktion** fortlaufender Versand“ können Sie einem bestehenden Versand neue Empfänger hinzufügen. Durch diesen Versand müssen Sie nicht jedes Mal einen neuen Versand erstellen. Dieser Modus ist häufig effizienter, insbesondere bei Warnungen oder Benachrichtigungen mit geringem Volumen, die bei Bedarf gesendet werden.

![](assets/do-not-localize/how-to-video.png) [Funktion im Video kennenlernen](#continuous-delivery-video).

Auf der Ebene der Versandvorlagen können Sie ein Script zur Berechnung der Beschriftung (und des Kampagnenordners) des zugehörigen Versands angeben. Wenn das Script einen Versand berechnet, der noch nicht vorhanden ist, wird er sofort erstellt.

![](assets/edit_diffusion_fil.png)

Die Option **[!UICONTROL Fehler verarbeiten]** zeigt eine bestimmte Transition an, die aktiviert wird, wenn ein Fehler erzeugt wird. In diesem Fall wechselt der Workflow nicht in den Fehlermodus und wird anschließend ausgeführt.

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

Anhand der drei Werte lässt sich die durch den unmittelbaren Versand ermittelte Zielgruppe identifizieren. **[!UICONTROL tableName]** ist der Name der Tabelle, die die Zielkennungen speichert, **[!UICONTROL schema]** ist das Schema der Population (normalerweise nms:recipient) und **[!UICONTROL recCount]** die Anzahl der Elemente in der Tabelle.

Die Transition des Komplements weist die gleichen Parameter auf.

## Einrichten eines Versands (fortlaufend)

In diesem Abschnitt wird beschrieben, wie Sie einen Versand (fortlaufend) einrichten.

Beim **fortlaufenden Versand** können Sie einem bestehenden Versand neue Empfänger hinzufügen, sodass Sie nicht jedes Mal einen neuen Versand erstellen müssen, wenn ein neuer Empfänger hinzugefügt wird. Sie können die kreativen Inhalte direkt im Kampagnen-Workflow aktualisieren, wodurch die Vorlage im Ressourcen-Ordner für Versandvorlagen aktualisiert wird.

Bei einem fortlaufenden Versand wird EIN Versand erstellt. Versandlogs (Broadlog) und Trackinglogs, die auf diesen Versand verweisen, werden bei jeder Ausführung hinzugefügt.

![Versand (fortlaufend)](assets/delivery_continuous.jpg)

## Anleitungsvideo {#continuous-delivery-video}

In diesem Video wird gezeigt, wie Sie einen fortlaufenden Versand mit einer inkrementellen Abfrage konfigurieren.

>[!VIDEO](https://video.tv.adobe.com/v/25039?quality=12)

Weitere Anleitungsvideos zu Campaign Classic finden Sie [hier](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=de).
