---
title: Erweiterte Funktionen
seo-title: Erweiterte Funktionen
description: Erweiterte Funktionen
seo-description: null
page-status-flag: never-activated
uuid: 4dbf4750-0226-4f96-98d8-ec49b20374ac
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: creating-new-reports
discoiquuid: 0c264783-2775-4ec6-8d49-cd9a45a18d60
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: af768da6ee8cc0ca2ea1f24f297239b974c113a5

---


# Erweiterte Funktionen{#advanced-functionalities}

## Script hinzufügen {#adding-a-script}

### Script-Aktivität {#script-activity}

Diese Aktivität ermöglicht es, Daten zu bearbeiten und auf einfache Weise komplexe Abfragen zu erstellen, die mit SQL nicht möglich sind.

Geben Sie einfach Ihre Abfrage im Script-Fenster ein.

Auf der **[!UICONTROL Texts]** Registerkarte können Sie Textzeichenfolgen definieren.  Sie können dann mit der folgenden Syntax verwendet werden: **$(Bezeichner)**. Weitere Informationen zur Verwendung von Texten finden Sie unter [Hinzufügen einer Kopf- und Fußzeile](../../reporting/using/element-layout.md#adding-a-header-and-a-footer).

>[!CAUTION]
>
>Es wird DRINGEND davon abgeraten, JavaScript-Code zur Erstellung von Aggregaten zu verwenden.

Wenn Sie einen Berichtsverlauf erstellen möchten, fügen Sie Ihrer JavaScript-Abfrage die folgende Zeile hinzu, um die Verlaufsdaten beizubehalten:

```
if( ctx.@_historyId.toString().length == 0 )
```

Andernfalls werden die aktuellen Daten angezeigt.

### Externe Scripts {#external-script}

Es besteht die Möglichkeit, ein externes Script hinzuzufügen, das server- und/oder clientseitig ausgeführt wird. Gehen Sie hierzu wie folgt vor:

1. Öffnen Sie die Eigenschaften des Berichts und klicken Sie auf den Tab **[!UICONTROL Scripts]**.
1. Click **[!UICONTROL Add]** and select the script to be referenced.
1. Bestimmen Sie anschließend den Ausführungsmodus.

   Wenn Sie mehrere Scripts hinzufügen, können Sie deren Ausführungsreihenfolge mithilfe der Pfeile in der Symbolleiste verändern.

   ![](assets/reporting_custom_js.png)

## Andere Berichte aufrufen {#calling-up-another-report}

### Sprung-Aktivität {#jump-activity}

Ein Sprung ist wie eine Transition ohne Pfeil: Er ermöglicht den Übergang von einer Aktivität zur anderen oder den Zugriff auf einen anderen Bericht.
