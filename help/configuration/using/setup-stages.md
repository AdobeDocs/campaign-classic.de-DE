---
product: campaign
title: Einrichtungsschritte
description: Einrichtungsschritte
feature: Configuration
role: Developer
exl-id: a5ae0b61-3377-46d9-a327-6c897eeda770
source-git-commit: 9f5205ced6b8d81639d4d0cb6a76905a753cddac
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 2%

---

# Einrichtungsschritte{#setup-stages}

Das Grundprinzip ist das Einfügen von Webtracking-Tags in bestimmte Seiten Ihrer Website.

Es gibt zwei Arten von Tags:

* **WEB**: Dieses Tag gibt an, ob die Seite besucht wurde.
* **TRANSACTION**: Funktioniert wie ein Web-Tag, aber mit der Möglichkeit, Informationen über das generierte Geschäftsvolumen hinzuzufügen, z. B. (Transaktionsbetrag, Anzahl der gekauften Artikel usw.).

Gehen Sie wie folgt vor, um diese Tags einzurichten:

1. Identifizieren Sie die Seiten, die Sie verfolgen möchten, und bestimmen Sie deren Typ (WEB oder TRANSAKTION).
1. Legen Sie fest, welche zusätzlichen Informationen erfasst werden sollen, und erweitern Sie das **nms:webTrackingLog**-Schema mit der Beschreibung dieser Informationen. Standardmäßig kann dieses Schema die Transaktionsbeträge und die Anzahl der Elemente pro Transaktion speichern.
1. Erstellen der Webtracking-Tags. Dazu gibt es zwei Möglichkeiten:

   * Fügen Sie die URLs für diese Seiten in Ihre Adobe Campaign-Plattform ein und generieren und extrahieren Sie dann die zugehörigen Webtracking-Tags (aus dem Knoten **[!UICONTROL Kampagnenausführung>Ressourcen>]**-Tags der Client-Konsole).
   * Erstellen Sie die Webtracking-Tags selbst im Modus „On-the-fly-Erstellung“: Die URLs zu diesen Seiten werden automatisch in Ihre Adobe Campaign-Plattform eingefügt.

1. Fügen Sie diese Tags den Seiten, die Sie verfolgen möchten, statisch oder dynamisch hinzu.

   >[!NOTE]
   >
   >Alle WEB-artigen Tags können so wie auf den Seiten Ihrer Site hinzugefügt werden. TRANSAKTIONS-Tags müssen dynamisch geändert oder hinzugefügt werden, damit sie die zusätzlichen Informationen (Betrag, Elemente usw.) enthalten.

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
