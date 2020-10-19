---
title: Erweiterte Funktionen
description: Erweiterte Funktionen
page-status-flag: never-activated
uuid: 4dbf4750-0226-4f96-98d8-ec49b20374ac
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: creating-new-reports
discoiquuid: 0c264783-2775-4ec6-8d49-cd9a45a18d60
translation-type: tm+mt
source-git-commit: 2a82493deada11cb22ef37d215b6eae8274ce890
workflow-type: tm+mt
source-wordcount: '647'
ht-degree: 54%

---


# Erweiterte Funktionen{#advanced-functionalities}

Als technischer Benutzer können Sie zusätzlich zu den [allgemeinen Eigenschaften](../../reporting/using/properties-of-the-report.md)erweiterte Funktionen zur Konfiguration Ihrer Berichte nutzen, z. B.:

* Erstellen Sie komplexe Abfragen zur Verarbeitung von Daten in einer **Script** -Aktivität. [mehr dazu](#script-activity)

* hinzufügen eines externen Skripts, das auf Server- oder Clientseite ausgeführt wird. [mehr dazu](#external-script)

* Rufen Sie einen Bericht mit einer **Sprung** -Aktivität auf. [mehr dazu](#calling-up-another-report)

* hinzufügen einem Bericht einen URL-Parameter, um ihn leichter zugänglich zu machen. [mehr dazu](#calling-up-another-report)

* hinzufügen Variablen, die im Kontext des Berichts verwendet werden. [mehr dazu](#adding-variables)

## Arbeiten mit Skripten {#adding-a-script}

### Externe Skripten referenzieren {#external-script}

Sie können auf JavaScript-Codes verweisen, die beim Aufrufen der Berichtsseite auf Client- und/oder Serverseite ausgeführt werden.

Gehen Sie dazu wie folgt vor:

1. Edit the [report properties](../../reporting/using/properties-of-the-report.md) and click the **[!UICONTROL Scripts]**.
1. Klicken Sie auf **[!UICONTROL Hinzufügen]** und wählen Sie das zu referenzierende Script aus.
1. Bestimmen Sie anschließend den Ausführungsmodus.

   Wenn Sie mehrere Scripts hinzufügen, können Sie deren Ausführungsreihenfolge mithilfe der Pfeile in der Symbolleiste verändern.

   ![](assets/reporting_custom_js.png)

Für eine normale Ausführung auf Clientseite müssen die referenzierten Skripten in JavaScript geschrieben werden und mit gängigen Browsern kompatibel sein. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../web/using/web-forms-answers.md).

### Adding a Script activity {#script-activity}

Verwenden Sie beim [Entwerfen Ihres Berichts](../../reporting/using/creating-a-new-report.md#modelizing-the-chart)die **[!UICONTROL Script]** -Aktivität, um Daten zu verarbeiten und ganz einfach komplexe Abfragen zu erstellen, die keine SQL-Sprache aktivieren. Sie können Ihre Abfrage direkt im Skriptfenster eingeben.

Auf dem Tab **[!UICONTROL Texte]** können Sie Text-Strings definieren. Diese können dann mit der folgenden Syntax verwendet werden: **$(Identifier)**. Weitere Informationen zur Verwendung von Texten finden Sie unter [Header und Footer hinzufügen](../../reporting/using/element-layout.md#adding-a-header-and-a-footer).

>[!CAUTION]
>
>Es wird DRINGEND davon abgeraten, JavaScript-Code zur Erstellung von Aggregaten zu verwenden.

Wenn Sie einen Berichtsverlauf erstellen möchten, fügen Sie Ihrer JavaScript-Abfrage die folgende Zeile hinzu, um die Verlaufsdaten beizubehalten:

```
if( ctx.@_historyId.toString().length == 0 )
```

Andernfalls werden nur aktuelle Daten angezeigt.

## Hinzufügen eines URL-Parameters {#defining-additional-settings}

The **[!UICONTROL Parameters]** tab of the [report properties](../../reporting/using/properties-of-the-report.md) lets you define additional settings for the report: these settings will be passed into the URL during the call up.

>[!CAUTION]
>
>Diese Parameter sollten aus Sicherheitsgründen mit Vorsicht benutzt werden.

Gehen Sie wie folgt vor, um einen neuen Parameter zu erstellen:

1. Klicken Sie auf die Schaltfläche **[!UICONTROL Hinzufügen]** und erfassen Sie den Namen des Parameters.

   ![](assets/s_ncs_advuser_report_properties_09a.png)

1. Geben Sie an, ob es sich um einen obligatorischen Parameter handeln soll.

1. Wählen Sie den zu erstellenden Parameter aus: **[!UICONTROL Filter]** oder **[!UICONTROL Variable]**.

   Die Option **[!UICONTROL Entitäten filtern]** ermöglicht die Nutzung eines Datenbank-Feldes als Parameter.

   ![](assets/s_ncs_advuser_report_properties_09b.png)

   Die Daten werden direkt auf Ebene der Entität abgerufen: **ctx/recipient/@account**.

   Über die Option **[!UICONTROL Variable]** kann eine Variable erstellt oder ausgewählt werden, die als URL-Parameter übergeben und auf Ebene der Filter genutzt werden kann.

Mit **[!UICONTROL Antwort-HTTP-Headers]** können Sie Clickjacking verhindern, wenn Sie die Seite Ihres Berichts mit iframe in eine HTML-Seite einschließen. Zur Vermeidung von Clickjacking können Sie das Verhalten **[!UICONTROL X-Frame-Options-Header]** auswählen:

* **[!UICONTROL Keiner]**: Der Bericht enthält keinen **[!UICONTROL X-Frame-Options-Header]**.
* **[!UICONTROL Identisch mit Ursprung]**: Standardmäßig für neue Berichte und erneut veröffentlichte Berichte festgelegt. Der Host-Name entspricht der URL des Berichts.
* **[!UICONTROL Ablehnen]**: Der Bericht kann nicht mit iframe in eine HTML-Seite eingefügt werden.

![](assets/s_ncs_advuser_report_properties_09c.png)

## Variablen hinzufügen {#adding-variables}

Der Tab **[!UICONTROL Variablen]** enthält die Liste der im Bericht konfigurierten Variablen. Diese werden im Kontext des Berichts aufgeführt und können in den Berechnungen verwendet werden.

Klicken Sie auf die Schaltfläche **[!UICONTROL Hinzufügen]**, um eine neue Variable zu erstellen.

Um die Parameter einer Variablen einzusehen, markieren Sie sie und klicken Sie auf die Schaltfläche **[!UICONTROL Detail...]**.

![](assets/s_ncs_advuser_report_properties_10.png)

## Verwendungsfall: Variablen und Parameter in einem Bericht verwenden

Im folgenden Videobeispiel erfahren Sie, wie Sie einen Parameter &quot;_type&quot;hinzufügen, um je nach Attributwert verschiedene Ansichten eines Berichts zu erstellen.

![](assets/do-not-localize/how-to-video.png) [Mehr zu dieser Funktion erfahren Sie im Video.](https://helpx.adobe.com/campaign/classic/how-to/add-url-parameter-in-acv6.html?playlist=/ccx/v1/collection/product/campaign/classic/segment/business-practitioners/explevel/intermediate/applaunch/how-to-4/collection.ccx.js&amp;ref=helpx.adobe.com).


## Andere Berichte aufrufen {#calling-up-another-report}

A **Jump** activity is like a transition without an arrow: it lets you go from one activity to another or access another report.
