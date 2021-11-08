---
product: campaign
title: Einrichtungsschritte
description: Einrichtungsschritte
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
exl-id: a5ae0b61-3377-46d9-a327-6c897eeda770
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '240'
ht-degree: 2%

---

# Einrichtungsschritte{#setup-stages}

![](../../assets/v7-only.svg)

Das Grundprinzip ist das Einfügen von Web-Tracking-Tags in bestimmte Seiten Ihrer Website.

Es gibt zwei Arten von Tags:

* **WEB**: Dieses Tag gibt an, ob die Seite besucht wurde.
* **TRANSAKTION**: funktioniert wie ein Web-Tag, bietet jedoch die Möglichkeit, Informationen zum generierten Geschäftsvolumen hinzuzufügen (z. B. Transaktionsbetrag, Anzahl der gekauften Artikel usw.).

Gehen Sie wie folgt vor, um diese Tags einzurichten:

1. Identifizieren Sie die Seiten, die Sie verfolgen möchten, und bestimmen Sie deren Typ (WEB oder TRANSACTION).
1. Bestimmen Sie, welche zusätzlichen Informationen Sie erfassen möchten, und erweitern Sie die **nms:webTrackingLog** Schema mit der Beschreibung dieser Informationen. Standardmäßig kann dieses Schema die Transaktionsmengen und die Anzahl der Elemente pro Transaktion speichern.
1. Erstellen der Webtracking-Tags. Dazu gibt es zwei Möglichkeiten:

   * Fügen Sie die URLs, die diesen Seiten entsprechen, in Ihre Adobe Campaign-Plattform ein, generieren Sie dann die zugehörigen Web-Tracking-Tags und extrahieren Sie diese (aus dem **[!UICONTROL Kampagnenausführung > Ressourcen > Webtracking-Tags]** -Knoten der Client-Konsole).
   * Erstellen Sie die Webtracking-Tags selbst im Modus &quot;On-the-fly-Erstellung&quot;: Die URLs, die diesen Seiten entsprechen, werden automatisch in Ihre Adobe Campaign-Plattform eingefügt.

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
