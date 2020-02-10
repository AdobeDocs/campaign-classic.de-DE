---
title: Elemente anordnen
seo-title: Elemente anordnen
description: Elemente anordnen
seo-description: null
page-status-flag: never-activated
uuid: 60dc80d9-f81b-48ce-9341-f975daaf5ebc
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: creating-new-reports
discoiquuid: 8fdda764-3e42-4972-a9c9-63567588931e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 209ac4d81d2d27c264ee6b288bcb7fcb1900ffc5

---


# Elemente anordnen{#element-layout}

In addition to the various charts detailed here: [Chart types and variants](../../reporting/using/creating-a-chart.md#chart-types-and-variants), you can adapt the display and add elements to the report page(s).

Sie können beispielsweise Container verwenden: Diese ermöglichen es, mehrere Elemente einer Seite zu gruppieren und in Spalten oder Zellen anzuordnen. Nähere Informationen zu ihrer Konfiguration werden in [diesem Abschnitt](../../web/using/defining-web-forms-layout.md#creating-containers) erläutert.

Sie können das Layout des Berichts in der Seite konfigurieren (an der Wurzel des Navigationsbaums) und es für jeden Container überschreiben. Sowohl Seiten als auch Container sind in Spalten organisiert. Nur statische Elemente und Grafiken sind in Zellen organisiert.

## Optionen jeder Seite festlegen {#defining-the-options-for-each-page}

Für jede Berichtseite können unterschiedliche Optionen konfiguriert werden.

The **[!UICONTROL General]** tab lets you change the title of the page, as well as configure legend positions and browsing between the report pages.

![](assets/s_ncs_advuser_report_wizard_022.png)

Im **[!UICONTROL Title]** Feld können Sie die Bezeichnung in der Kopfzeile der Berichtsseite personalisieren. Der Titel des Fensters kann über das **[!UICONTROL Properties]** Fenster des Berichts konfiguriert werden. Weitere Informationen finden Sie unter [Hinzufügen einer Kopf- und Fußzeile](#adding-a-header-and-a-footer).

Mit den **[!UICONTROL Display settings]** Optionen können Sie die Position der Kontrolltitel in einer Berichtsseite auswählen und die Anzahl der Spalten auf der Seite definieren. Weitere Informationen zum Seitenlayout finden Sie im Abschnitt **Elementlayout** in [diesem Abschnitt](../../web/using/defining-web-forms-layout.md#positioning-the-fields-on-the-page).

Wählen Sie die verschiedenen Optionen im **[!UICONTROL Browse]** Abschnitt aus, um das Browsen von einer Berichtsseite zu einer anderen zu autorisieren. Wenn die Option **[!UICONTROL Disable next page]** oder die **[!UICONTROL Disable previous page]** Option ausgewählt ist, werden die Schaltflächen **[!UICONTROL Next]** und **[!UICONTROL Previous]** die Schaltflächen auf der Berichtsseite ausgeblendet.

## Header und Footer hinzufügen {#adding-a-header-and-a-footer}

Die Berichtseigenschaften bieten die Möglichkeit, Layout-Elemente wie einen Fenstertitel oder den HTML-Inhalt des Headers und des Footers zu konfigurieren.

To access the properties window, click the **[!UICONTROL Properties]** button of the report.

![](assets/reporting_properties.png)

The **[!UICONTROL Page]** tab enables you to personalize your display.

![](assets/s_ncs_advuser_report_properties_04.png)

Der in diesem Tab konfigurierte Inhalt wird auf allen Seiten des Berichts sichtbar sein.

The **[!UICONTROL Texts]** sub-tab enables you to define variable content: it will be taken into account during the translation cycle if the report is designed for use in several languages.

Sie können hierzu eine Liste mit Textfragmenten erstellen und diesen jeweils eine Kennung zuordnen:

![](assets/s_ncs_advuser_report_properties_04a.png)

Fügen Sie die Kennungen in den HTML-Inhalt des Berichts ein:

![](assets/s_ncs_advuser_report_properties_04b.png)

Sie werden bei der Anzeige des Berichts automatisch durch den entsprechenden Inhalt ersetzt.

Diese Funktion ermöglicht es, wie bei HTML-Texten die im Bericht verwendeten Texte zu zentralisieren und ihre Übersetzungen zu erzeugen: Die in diesem Tab erstellten Texte werden automatisch von dem in Adobe Campaign integrierten Übersetzungstool abgerufen.
