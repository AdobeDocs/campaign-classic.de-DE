---
product: campaign
title: Elemente anordnen
description: Elemente anordnen
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
feature: Reporting, Monitoring
exl-id: 79d5c901-905b-4a0e-adb9-91fd6acb186f
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 66%

---

# Layout der Elemente{#element-layout}



Zusätzlich zu den verschiedenen Diagrammen, die [hier](../../reporting/using/creating-a-chart.md#chart-types-and-variants) beschrieben sind, können Sie die Anzeige anpassen und Elemente zu den Berichtsseiten hinzufügen.

Sie können Container verwenden: Mithilfe dieser Elemente können Sie mehrere Elemente einer Seite verknüpfen und ihr Layout in Spalten und/oder Zellen konfigurieren. Weitere Informationen zu ihrer Verwendung finden Sie unter [diesem Abschnitt](../../web/using/defining-web-forms-layout.md#creating-containers).

Sie können das Layout des Berichts in der Seite konfigurieren (an der Wurzel des Navigationsbaums) und es für jeden Container überschreiben. Sowohl Seiten als auch Container sind in Spalten organisiert. Nur statische Elemente und Grafiken sind in Zellen organisiert.

## Definieren der Optionen für jede Seite {#defining-the-options-for-each-page}

Für jede Berichtseite können unterschiedliche Optionen konfiguriert werden.

Der Tab **[!UICONTROL Allgemein]** erlaubt es, den Titel der Seite zu ändern, die Positionierung der Legenden zu wählen und die Navigation zwischen den verschiedenen Seiten des Berichts zu konfigurieren.

![](assets/s_ncs_advuser_report_wizard_022.png)

Die **[!UICONTROL Titel]** -Feld können Sie den Titel in der Kopfzeile der Berichtsseite personalisieren. Der Titel des Fensters kann über die **[!UICONTROL Eigenschaften]** des Berichts. Weitere Informationen hierzu finden Sie unter [Header und Footer hinzufügen](#adding-a-header-and-a-footer).

Die **[!UICONTROL Anzeigeeinstellungen]** Mit den Optionen können Sie die Position der Kontrollbeschriftung innerhalb einer Berichtseite auswählen und die Anzahl der Spalten auf der Seite definieren. Weitere Informationen zum Seitenlayout finden Sie im Abschnitt **Elementlayout** Abschnitt [diesem Abschnitt](../../web/using/defining-web-forms-layout.md#positioning-the-fields-on-the-page).

Wählen Sie die verschiedenen Optionen im **[!UICONTROL Durchsuchen]** -Abschnitt verwenden, um das Browsen von einer Berichtseite zu einer anderen zu erlauben. Wenn die Variable **[!UICONTROL Nächste Seite deaktivieren]** oder **[!UICONTROL Vorherige Seite deaktivieren]** ausgewählt ist, wird die **[!UICONTROL Nächste]** und **[!UICONTROL Vorherige]** -Schaltflächen auf der Berichtsseite verschwinden.

## Hinzufügen einer Kopf- und einer Fußzeile {#adding-a-header-and-a-footer}

Die Berichtseigenschaften bieten die Möglichkeit, Layout-Elemente wie einen Fenstertitel oder den HTML-Inhalt des Headers und des Footers zu konfigurieren.

Klicken Sie hierzu auf die Schaltfläche **[!UICONTROL Eigenschaften]** des Berichts.

![](assets/reporting_properties.png)

Im Tab **[!UICONTROL Seite]** kann die Anzeige angepasst werden.

![](assets/s_ncs_advuser_report_properties_04.png)

Der in diesem Tab konfigurierte Inhalt wird auf allen Seiten des Berichts sichtbar sein.

Im Untertab **[!UICONTROL Texte]** lassen sich variable Inhalte konfigurieren. Diese werden im Übersetzungszyklus berücksichtigt, wenn der Bericht in verschiedenen Sprachen angeboten wird.

Sie können hierzu eine Liste mit Textfragmenten erstellen und diesen jeweils eine Kennung zuordnen:

![](assets/s_ncs_advuser_report_properties_04a.png)

Fügen Sie die Kennungen in den HTML-Inhalt des Berichts ein:

![](assets/s_ncs_advuser_report_properties_04b.png)

Sie werden bei der Anzeige des Berichts automatisch durch den entsprechenden Inhalt ersetzt.

Diese Funktion ermöglicht es, wie bei HTML-Texten die im Bericht verwendeten Texte zu zentralisieren und ihre Übersetzungen zu erzeugen: Die in diesem Tab erstellten Texte werden automatisch von dem in Adobe Campaign integrierten Übersetzungstool abgerufen.
