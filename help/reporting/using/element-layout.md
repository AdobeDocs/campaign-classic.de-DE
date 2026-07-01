---
product: campaign
title: Elemente anordnen
description: Elemente anordnen
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
feature: Reporting, Monitoring
exl-id: 79d5c901-905b-4a0e-adb9-91fd6acb186f
TQID: https://experienceleague.adobe.com/do7CqEaE2v7cdpI-mXZ2AQ6L4nsyDnEzEXdC-zHEcs4
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
feature_v2:
  - id: c309ee4e-82e4-4f7e-b608-ef345678c34e
subfeature_v2:
  - id: b3a4149f-2b3a-44d1-894e-e3ac4c77fb47
  - id: cfda811a-e413-43a4-adf0-7370888f5cfc
  - id: afe938ea-bc18-44a4-a3fb-03e1031466cb
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 442
ht-degree: 100%

---

# Layout der Elemente{#element-layout}



Zusätzlich zu den verschiedenen Diagrammen, die [hier](../../reporting/using/creating-a-chart.md#chart-types-and-variants) beschrieben sind, können Sie die Anzeige anpassen und Elemente zu den Berichtsseiten hinzufügen.

Sie können beispielsweise Container verwenden: Diese ermöglichen es, mehrere Elemente einer Seite zu gruppieren und in Spalten oder Zellen anzuordnen. Nähere Informationen zu ihrer Konfiguration werden in [diesem Abschnitt](../../web/using/defining-web-forms-layout.md#creating-containers) erläutert.

Sie können das Berichts-Layout am Stamm der Baumstruktur konfigurieren und für jeden Container überschreiben. Die Seiten werden in Spalten sortiert. Container werden auch in Spalten sortiert. Nur die statischen und grafischen Elemente werden in Zellen sortiert.

## Definieren der Optionen für jede Seite {#defining-the-options-for-each-page}

Für jede Berichtseite können unterschiedliche Optionen konfiguriert werden.

Der Tab **[!UICONTROL Allgemein]** erlaubt es, den Titel der Seite zu ändern, die Positionierung der Legenden zu wählen und die Navigation zwischen den verschiedenen Seiten des Berichts zu konfigurieren.

![](assets/s_ncs_advuser_report_wizard_022.png)

Im Feld **[!UICONTROL Titel]** kann der Titel angepasst werden, der im Header der Berichtseite angezeigt wird. Der Titel des Fensters lässt sich in den **[!UICONTROL Eigenschaften]** des Berichts angegeben. Weitere Informationen hierzu finden Sie unter [Header und Footer hinzufügen](#adding-a-header-and-a-footer).

Die Optionen der **[!UICONTROL Anzeigeparameter]** ermöglichen es, die Positionierung der Legende in der Seite eines Berichts sowie die Spaltenanzahl der Seite zu bestimmen. Mehr Informationen zum Layout erhalten Sie im Abschnitt **Anordnung der Elemente** in [diesem Abschnitt](../../web/using/defining-web-forms-layout.md#positioning-the-fields-on-the-page).

Konfigurieren Sie die unterschiedlichen Optionen des Abschnitts **[!UICONTROL Navigation]**, um einen Übergang zwischen den Seiten des Berichts zu erlauben oder nicht. Bei Aktivierung der Option **[!UICONTROL Rückkehr zur vorhergehenden Seite nicht zulassen]** oder der Option **[!UICONTROL Weiter zur nächsten Seite nicht zulassen]** sind die Schaltflächen **[!UICONTROL Weiter]** oder **[!UICONTROL Zurück]** in der Berichtseite nicht mehr verfügbar.

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

Wie bei HTML-Texten ermöglicht es dieser Betriebsmodus, die im Bericht verwendeten Texte zu zentralisieren und ihre Übersetzungen zu verwalten. Die in dieser Registerkarte erstellten Texte werden automatisch vom integrierten Übersetzungs-Tool von Adobe Campaign erfasst.
