---
title: Berichtbearbeitung
seo-title: Berichtbearbeitung
description: Berichtbearbeitung
seo-description: null
page-status-flag: never-activated
uuid: af8f1101-135f-49ce-bada-bd19fe32053b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: analyzing-populations
discoiquuid: 667746cb-b553-4a71-8523-6b2695047ab6
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 62b2f1f6cfcaadd10880d428b8b94d73d2addcdb

---


# Verwenden eines Analyseberichts{#processing-a-report}

## Analyseberichte speichern {#saving-an-analysis-report}

Wenn Sie über die entsprechenden Berechtigungen verfügen, können Sie einen erstellten Analysebericht speichern oder ihn in den Formaten Excel, PDF oder OpenDocument exportieren.

To save your report, click **[!UICONTROL Save]** and give your report a label.

Wählen Sie diese Option, **[!UICONTROL Also save data]** wenn Sie einen Verlauf Ihres Berichts erstellen möchten, und sehen Sie die Werte des Berichts zum Zeitpunkt des Speicherns. For more on this, refer to [Archiving analysis reports](#archiving-analysis-reports).

Mit dieser **[!UICONTROL Share this report]** Option können andere Operatoren auf den Bericht zugreifen.

![](assets/s_ncs_user_report_wizard_010.png)

Sobald der Bericht gespeichert ist, kann er zur Erzeugung anderer Analyseberichte verwendet werden:

![](assets/s_ncs_user_report_wizard_08a.png)

Um Änderungen an diesem Bericht vorzunehmen, bearbeiten Sie den **[!UICONTROL Administration > Configuration > Adobe Campaign tree reports]** Knoten der Adobe-Kampagnenstruktur (oder den ersten &quot;Berichte&quot;-Ordner, für den der Operator über Bearbeitungsrechte verfügt). Weitere Informationen finden Sie unter Layout eines beschreibenden Analyseberichts [konfigurieren](#configuring-the-layout-of-a-descriptive-analysis-report).

## Zusätzliche Einstellungen für Analyseberichte {#analysis-report-additional-settings}

Nachdem Sie einen Analysebericht gespeichert haben, können Sie seine Eigenschaften ändern und auf weitere Optionen zugreifen.

![](assets/s_ncs_user_report_wizard_08b.png)

Diese Optionen entsprechen denen von Standardberichten. Sie werden auf [dieser Seite](../../reporting/using/properties-of-the-report.md) beschrieben.

## Anzeige deskriptiver Berichte anpassen {#configuring-the-layout-of-a-descriptive-analysis-report}

Sie können die Anzeige und das Layout Ihrer Daten in den Diagrammen und Tabellen der beschreibenden Analyse personalisieren. Auf alle Optionen wird über die Adobe-Kampagnenstruktur auf der **[!UICONTROL Edit]** Registerkarte jedes Berichts zugegriffen.

### Anzeigemodus des Analyseberichts {#analysis-report-display-mode}

Wenn Sie einen Bericht mit der **[!UICONTROL qualitative distribution]** Vorlage erstellen, werden standardmäßig die Anzeigemodi &quot;Tabelle&quot;und &quot;Diagramm&quot;ausgewählt. Wenn Sie nur einen Anzeigemodus verwenden möchten, deaktivieren Sie das entsprechende Kontrollkästchen. Das bedeutet, dass nur die Registerkarte des aktivierten Anzeigemodus verfügbar ist.

![](assets/s_ncs_advuser_report_display_01.png)

To change the schema of the report, click the **[!UICONTROL Select the link]** and select another table from the database.

![](assets/s_ncs_advuser_report_display_02.png)

### Anzeigeparameter des Analyseberichts {#analysis-report-display-settings}

Sie können den Namen der Statistiken und Zwischensummen anzeigen oder ausblenden und die Ausrichtung der Statistiken wählen.

![](assets/s_ncs_advuser_report_display_05.png)

Der Titel der Statistiken kann bei der Erstellung bestimmt werden.

![](assets/s_ncs_advuser_report_display_06.png)

Der angegebene Titel erscheint im Bericht.

![](assets/s_ncs_advuser_report_display_07.png)

Wenn Sie die Anzeigeoption der Titel und Zwischensummen jedoch abwählen, erscheinen diese nicht im Bericht. Der Name erscheint dennoch beim Überfahren einer Zelle der Tabelle mit dem Mauszeiger.

![](assets/s_ncs_advuser_report_display_08.png)

Die Statistiken werden standardmäßig in Zeilen angezeigt. Um die Ausrichtung zu ändern, wählen Sie die gewünschte Option in der Dropdown-Liste aus.

![](assets/s_ncs_advuser_report_wizard_035a.png)

Im nachstehenden Beispiel werden die Statistiken in Spalten angezeigt:

![](assets/s_ncs_advuser_report_wizard_035.png)

### Anordnung der Daten in Analyseberichten {#analysis-report-data-layout}

Die Anordnung der Daten kann direkt in den Analyse-Tabellen angepasst werden. Machen Sie hierzu einen Rechtsklick auf die betreffende Variable. Wählen Sie eine der folgenden, im Kontextmenü verfügbaren Optionen aus:

* **[!UICONTROL Pivot]** , um die Achse der Variablen zu ändern.
* **[!UICONTROL Up]** / **[!UICONTROL Down]** , um die Variablen in Zeilen zu tauschen.
* **[!UICONTROL Move to the right]** / **[!UICONTROL Move to the left]** , um die Variablen in Spalten auszutauschen.
* **[!UICONTROL Turn]** , um die Variablenachsen umzukehren.
* **[!UICONTROL Sort from A to Z]** , um die Variablenwerte niedrig bis hoch zu sortieren.
* **[!UICONTROL Sort from Z to A]** , um die Variablenwerte hoch bis niedrig zu sortieren.

   ![](assets/s_ncs_advuser_report_wizard_016.png)

Um zur ursprünglichen Anzeige zurückzukehren, aktualisieren Sie die Ansicht.

### Grafikoptionen in Analyseberichten {#analysis-report-chart-options}

Es ist möglich, die Anzeige der Daten im Diagramm zu personalisieren. Klicken Sie dazu auf den **[!UICONTROL Variables...]** Link, der während der Auswahlphase des Diagrammtyps verfügbar ist.

![](assets/s_ncs_advuser_report_wizard_3c.png)

Folgende Optionen stehen zur Verfügung:

* Im oberen Abschnitt des Fensters kann der Anzeigebereich der Grafik verändert werden.
* Standardmäßig werden Beschriftungen im Diagramm angezeigt. Sie können sie ausblenden, indem Sie die **[!UICONTROL Show values]** Option deaktivieren.
* The **[!UICONTROL Accumulate values]** option lets you add up values from one series to another.
* Die Legende der Grafik kann durch Deaktivieren der entsprechenden Option ausgeblendet werden. Die Legende wird standardmäßig außerhalb der Grafik oben rechts angezeigt.

   The legend can also be displayed on top of the chart in order to save on display space. To do this, select the option **[!UICONTROL Include in the chart]**

   Select the vertical and horizontal alignment in the **[!UICONTROL Caption position]** drop-down list.

   ![](assets/s_ncs_advuser_report_wizard_3d.png)

## Analyseberichte exportieren {#exporting-an-analysis-report}

Um Analyseberichte zu exportieren, wählen Sie in der Dropdown-Liste das gewünschte Ausgabeformat aus.

![](assets/s_ncs_user_report_wizard_09.png)

Weiterführende Informationen hierzu finden Sie auf dieser [Seite](../../reporting/using/actions-on-reports.md).

## Existierende Analysen und Berichte erneut verwenden {#re-using-existing-reports-and-analyses}

Sie können neue Berichte mit deskriptiven Analysen auf bereits existierenden, in Adobe Campaign gespeicherten Berichten basieren. Dieser Verwendungsmodus ist möglich, wenn die Analysen gespeichert oder die Berichte dahingehend erstellt und konfiguriert wurden, dass sie für den Assistenten zugänglich sind.

Informationen zum Speichern aussagekräftiger Analysen finden Sie unter [Speichern eines Analyseberichts](#saving-an-analysis-report).

To create descriptive analysis reports, the descriptive analysis wizard must be executed via a workflow transition or via the **[!UICONTROL Tools > Descriptive analysis]** menu.

1. Wählen Sie **[!UICONTROL Existing analyses and reports]** und klicken Sie auf **[!UICONTROL Next]**.
1. Die Liste der verfügbaren Berichte wird angezeigt. Klicken Sie auf den Berichttitel, um ihn zu erzeugen.

   ![](assets/s_ncs_user_report_wizard_01.png)

## Analyseberichte archivieren {#archiving-analysis-reports}

Wenn Sie eine deskriptive Analyse basierend auf einer existierenden Analyse erstellen, haben Sie die Möglichkeit, Verläufe zu erstellen. Dies erlaubt die Speicherung der Daten von einer Analyse zur anderen und den Vergleich der unterschiedlichen Ergebnisse Ihrer Berichte.

Gehen Sie wie folgt vor, um einen Verlauf zu erstellen:

1. Öffnen Sie eine existierende Analyse oder erstellen Sie einen neuen Analyse-Bericht.
1. Klicken Sie auf die Schaltfläche zur Erstellung eines Verlaufs in der Symbolleiste und bestätigen Sie Ihre Auswahl, wie im folgenden Beispiel:

   ![](assets/reporting_descriptive_historize_icon.png)

1. Über die entsprechende Schaltfläche können Sie auf frühere Analysen zugreifen.

   ![](assets/reporting_descriptive_historize_access.png)

