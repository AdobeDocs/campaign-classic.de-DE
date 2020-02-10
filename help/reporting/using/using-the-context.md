---
title: Kontext verwenden
seo-title: Kontext verwenden
description: Kontext verwenden
seo-description: null
page-status-flag: never-activated
uuid: ac8c7068-d640-4934-b7f5-bc91b98eab4c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: creating-new-reports
discoiquuid: 72fe6df0-0271-48f9-bd6d-bb1ff25fbdf3
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Kontext verwenden{#using-the-context}

Wenn Sie Daten in Form von **[!UICONTROL tables]** oder **[!UICONTROL charts]** darstellen möchten, können sie aus zwei Quellen stammen: eine neue Abfrage (siehe [Definieren eines direkten Datenfilters](#defining-a-direct-filter-on-data)) oder den Berichtskontext (siehe [Verwenden von Kontextdaten](#using-context-data)).

## Direkten Datenfilter definieren {#defining-a-direct-filter-on-data}

### Datenfilter {#filtering-data}

Die Verwendung einer **[!UICONTROL Query]** Typaktivität ist beim Erstellen eines Berichts nicht zwingend erforderlich. Daten können direkt in den Tabellen und Diagrammen gefiltert werden, aus denen der Bericht besteht.

This enables you to select the data to display in the report directly via the **[!UICONTROL Page]** activity of the report.

To do this, click the **[!UICONTROL Filter data...]** link in the **[!UICONTROL Data]** tab: this link lets you access the expressions editor to define a query on the data to be analyzed.

![](assets/reporting_filter_data_from_page.png)

### Beispiel: Filter in einer Grafik {#example--use-a-filter-in-a-chart}

Im folgenden Beispiel soll die Grafik nur die Profile der Empfänger anzeigen, die in Deutschland leben und im laufenden Jahr Einkäufe getätigt haben.

Um diesen Filter zu definieren, platzieren Sie eine Seite in das Diagramm und bearbeiten Sie sie. Klicken Sie auf den **[!UICONTROL Filter data]** Link und erstellen Sie den Filter, der den anzuzeigenden Daten entspricht. Mehr Informationen über die Erstellung von Abfragen in Adobe Campaign erhalten Sie in [diesem Abschnitt](../../platform/using/about-queries-in-campaign.md).

![](assets/s_ncs_advuser_report_wizard_029.png)

In unserem Beispiel wird die Verteilung der der Abfrage entsprechenden Empfänger nach Ort angezeigt.

![](assets/reporting_graph_with_2vars.png)

Die Grafik stellt sich folgendermaßen dar:

![](assets/reporting_graph_with_2vars_preview.png)

### Beispiel: Filter in einer Pivot-Tabelle {#example--use-a-filter-in-a-pivot-table}

In diesem Beispiel sollen Firmen, die nicht Adobe sind, in einer Pivot-Tabelle ohne vorangehende Abfrage gefiltert werden.

Gehen Sie wie folgt vor:

1. Positionieren Sie eine Seite im Diagramm und öffnen Sie sie.
1. Erstellen Sie eine Pivot-Tabelle.
1. Go to the **[!UICONTROL Data]** tab and select the cube to be used.
1. Click the **[!UICONTROL Filter data...]** link and define the following query to remove Adobe from the list of companies.

   ![](assets/s_ncs_advuser_report_display_03.png)

Somit werden nur die den Filterbedingungen entsprechenden Empfänger im Bericht berücksichtigt.

![](assets/s_ncs_advuser_report_display_04.png)

## Kontextdaten verwenden {#using-context-data}

To represent data in the form of a **[!UICONTROL table]** or a **[!UICONTROL chart]**, the data can come from the report context.

In the page that contains the table or the chart, the **[!UICONTROL Data]** tab lets you select the data source.

![](assets/s_ncs_advuser_report_datasource_3.png)

* Mit dieser **[!UICONTROL New query]** Option können Sie eine Abfrage zur Datenerfassung erstellen. Weitere Informationen finden Sie unter [Definieren eines direkten Datenfilters](#defining-a-direct-filter-on-data).
* Mit der **[!UICONTROL Context data]** Option können Sie die Eingabedaten verwenden: Der Kontext des Berichts fällt mit den Informationen zusammen, die im eingehenden Übergang der Seite enthalten sind, die das Diagramm oder die Tabelle enthält. Dieser Kontext kann z. B. Daten enthalten, die über eine **[!UICONTROL Query]** **[!UICONTROL Page]** Aktivität erfasst wurden, die vor der Aktivität platziert wurde und für die Sie die Tabelle und die Felder angeben müssen, die der Bericht betrifft.

Erstellen Sie in einer Abfrage-Aktivität zum Beispiel folgende Abfrage über die Empfänger:

![](assets/s_ncs_advuser_report_datasource_2.png)

Then indicate the source of the data in your report, in this case: **[!UICONTROL Data from the context]**.

Die Platzierung der Daten wird automatisch abgeleitet. Bei Bedarf können Sie den Pfad der Daten forcieren.

![](assets/s_ncs_advuser_report_datasource_4.png)

Bei der Wahl der Daten, auf die sich die Statistiken beziehen sollen, entsprechen die verfügbaren Felder den in der Abfrage angegebenen Daten.

![](assets/s_ncs_advuser_report_datasource_1.png)

