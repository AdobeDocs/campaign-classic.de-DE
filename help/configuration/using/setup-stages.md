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
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 3%

---


# Einrichtungsschritte{#setup-stages}

Das Grundprinzip ist das Einfügen von Web-Trackingtagen in bestimmte Seiten Ihrer Website.

Es gibt zwei Arten von Tags:

* **WEB**: Dieses Tag zeigt Ihnen an, ob die Seite besucht wurde.
* **TRANSAKTION**: funktioniert wie ein Web-Tag, jedoch mit der Möglichkeit, Informationen über das generierte Geschäftsvolumen hinzuzufügen, zum Beispiel (Transaktionssumme, Anzahl der gekauften Artikel usw.).

Wenden Sie die folgenden Schritte an, um diese Tags einzurichten:

1. Identifizieren Sie die Seiten, die Sie verfolgen möchten, und bestimmen Sie deren Typ (WEB oder TRANSACTION).
1. Bestimmen Sie, welche zusätzlichen Informationen Sie erfassen möchten, und erweitern Sie das **nms:webTrackingLog** -Schema mit der Beschreibung dieser Informationen. In diesem Schema können die Transaktionsbeträge und die Anzahl der Elemente pro Transaktion standardmäßig gespeichert werden.
1. Erstellen der Web-Trackingtag. Es gibt zwei Möglichkeiten, dies zu tun:

   * Fügen Sie die entsprechenden URLs in Ihre Adobe Campaign-Plattform ein, generieren und extrahieren Sie dann die zugehörigen Web-Trackingtag (aus dem Knoten **[!UICONTROL Kampagne-Ausführung > Resources > Webtrackingtags]** der Client-Konsole).
   * Erstellen Sie die Web-Trackingtag selbst im &quot;on-the-fly&quot;-Erstellungsmodus: die URLs, die diesen Seiten entsprechen, werden automatisch in Ihre Adobe Campaign-Plattform eingefügt.

1. hinzufügen Sie diese Tags statisch oder dynamisch auf den Seiten, die Sie verfolgen möchten.

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

