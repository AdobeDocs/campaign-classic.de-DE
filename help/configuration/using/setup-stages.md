---
title: Einrichtungsschritte
seo-title: Einrichtungsschritte
description: Einrichtungsschritte
seo-description: null
page-status-flag: never-activated
uuid: 4111a805-95ab-4e26-be51-2db1e5c20f57
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
discoiquuid: 76174374-af73-4da0-b62b-6979bca0102b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Einrichtungsschritte{#setup-stages}

Das Grundprinzip ist das Einfügen von Web-Tracking-Tags in bestimmte Seiten Ihrer Website.

Es gibt zwei Arten von Tags:

* **WEB**: Dieses Tag zeigt Ihnen an, ob die Seite besucht wurde.
* **TRANSAKTION**: funktioniert wie ein Web-Tag, jedoch mit der Möglichkeit, Informationen über das generierte Geschäftsvolumen hinzuzufügen, zum Beispiel (Transaktionssumme, Anzahl der gekauften Artikel usw.).

Wenden Sie die folgenden Schritte an, um diese Tags einzurichten:

1. Identifizieren Sie die Seiten, die Sie verfolgen möchten, und bestimmen Sie deren Typ (WEB oder TRANSACTION).
1. Bestimmen Sie, welche zusätzlichen Informationen Sie erfassen möchten, und erweitern Sie das Schema **nms:webTrackingLog** mit der Beschreibung dieser Informationen. Standardmäßig kann dieses Schema die Transaktionsbeträge und die Anzahl der Elemente pro Transaktion speichern.
1. Erstellen der Web-Tracking-Tags. Es gibt zwei Möglichkeiten:

   * Fügen Sie die URLs, die diesen Seiten entsprechen, in Ihre Adobe Campaign-Plattform ein, generieren und extrahieren Sie dann die entsprechenden Web-Tracking-Tags (vom **[!UICONTROL Campaign execution>Resources>Web tracking tags]** Knoten der Client-Konsole).
   * Erstellen Sie die Web-Tracking-Tags selbst im Modus &quot;On-the-fly-Erstellung&quot;: die URLs, die diesen Seiten entsprechen, werden automatisch in Ihre Adobe Campaign-Plattform eingefügt.

1. Fügen Sie diese Tags statisch oder dynamisch auf den Seiten hinzu, die Sie verfolgen möchten.

   >[!NOTE]
   >
   >Alle WEB-Tags können so hinzugefügt werden, wie sie zu den Seiten Ihrer Site gehören. TRANSACTION-Tags müssen dynamisch geändert oder hinzugefügt werden, um die zusätzlichen Informationen (Menge, Elemente usw.) zu enthalten.

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

