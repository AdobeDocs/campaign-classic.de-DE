---
product: campaign
title: Einrichtungsschritte
description: Einrichtungsschritte
feature: Configuration
role: Data Engineer, Developer
exl-id: a5ae0b61-3377-46d9-a327-6c897eeda770
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '240'
ht-degree: 2%

---

# Einrichtungsschritte{#setup-stages}

Das Grundprinzip ist das Einfügen von Web-Tracking-Tags in bestimmte Seiten Ihrer Website.

Es gibt zwei Arten von Tags:

* **WEB**: Dieses Tag teilt Ihnen mit, ob die Seite besucht wurde.
* **TRANSAKTION**: funktioniert wie ein Web-Tag, bietet jedoch die Möglichkeit, Informationen zum generierten Geschäftsvolumen hinzuzufügen, z. B. Transaktionsbetrag, Anzahl der gekauften Artikel usw.

Gehen Sie wie folgt vor, um diese Tags einzurichten:

1. Identifizieren Sie die Seiten, die Sie verfolgen möchten, und bestimmen Sie deren Typ (WEB oder TRANSACTION).
1. Ermitteln Sie, welche zusätzlichen Informationen Sie erfassen möchten, und erweitern Sie das Schema **nms:webTrackingLog** mit der Beschreibung dieser Informationen. Standardmäßig kann dieses Schema die Transaktionsmengen und die Anzahl der Elemente pro Transaktion speichern.
1. Erstellen der Webtracking-Tags. Dazu gibt es zwei Möglichkeiten:

   * Fügen Sie die URLs, die diesen Seiten entsprechen, in Ihre Adobe Campaign-Plattform ein, generieren Sie die zugehörigen Web-Tracking-Tags und extrahieren Sie sie (aus dem Knoten **[!UICONTROL Kampagnenausführung>Ressourcen > Web-Tracking-Tags]** der Clientkonsole).
   * Erstellen Sie die Webtrackingtags selbst im Modus &quot;On-the-fly-Erstellung&quot;: Die den Seiten entsprechenden URLs werden automatisch in Ihre Adobe Campaign-Plattform eingefügt.

1. Fügen Sie diese Tags statisch oder dynamisch zu den Seiten hinzu, die Sie verfolgen möchten.

   >[!NOTE]
   >
   >Alle WEBtypen-Tags können so hinzugefügt werden, wie sie zu den Seiten Ihrer Site gehören. TRANSAKTIONS-Tags müssen dynamisch geändert oder hinzugefügt werden, um zusätzliche Informationen (Menge, Elemente usw.) zu enthalten.

**Beispiel**:

```
<script type="text/javascript">
var _f = "nmsWebTracking"
var _t = window.location.href.match(/.*://[^/]*(/[^?#&]*)/)[1] + "|w|" + _f
document.write("<img height='0' width='0' alt='' src='" +
window.location.protocol + "//tsupport/r/" +
Math.random().toString() + "?tagid=" + escape(_t) + "'/>")
</script>
```
