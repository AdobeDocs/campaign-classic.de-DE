---
product: campaign
title: Verwalten und Konfigurieren des Analyseberichts
description: Verwalten und Konfigurieren des Analyseberichts
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
feature: Reporting, Monitoring
exl-id: d133efec-33e1-4711-a90f-e40385059386
source-git-commit: 5e062f9dbdf6c148e442ac10dbb12cf72ba0179b
workflow-type: tm+mt
source-wordcount: '891'
ht-degree: 100%

---

# Verwalten und Konfigurieren des Analyseberichts {#processing-a-report}

## Analyseberichte speichern {#saving-an-analysis-report}

Wenn Sie über die entsprechenden Berechtigungen verfügen, können Sie einen erstellten Analysebericht speichern oder ihn in den Formaten Excel, PDF oder OpenDocument exportieren.

Um Ihren Bericht zu speichern, klicken Sie auf **[!UICONTROL Speichern]** und benennen Sie den Bericht.

Aktivieren Sie die Option **[!UICONTROL Auch die Daten speichern]**, wenn Sie einen Verlauf Ihres Berichts speichern und die zum Zeitpunkt der Speicherung zugrunde liegenden Daten später wieder aufrufen möchten. Weitere Informationen hierzu finden Sie im Abschnitt [Archivieren von Analyseberichten](#archiving-analysis-reports).

Mit Aktivierung der Option **[!UICONTROL Bericht freigeben]** wird der Bericht für andere Benutzer zugänglich.

![](assets/s_ncs_user_report_wizard_010.png)

Sobald der Bericht gespeichert ist, kann er zur Erzeugung anderer Analyseberichte verwendet werden:

![](assets/s_ncs_user_report_wizard_08a.png)

Um den Bericht zu ändern, öffnen Sie den Knoten **[!UICONTROL Administration > Konfiguration > Berichte]** des Navigationsbaums (oder den ersten Ordner vom Typ „Berichte“, für den der Benutzer Schreibrechte hat). Weitere Informationen hierzu finden Sie unter [Konfigurieren des Layouts eines beschreibenden Analyseberichts](#configuring-the-layout-of-a-descriptive-analysis-report).

## Zusätzliche Einstellungen für Analyseberichte {#analysis-report-additional-settings}

Nachdem Sie einen Analysebericht gespeichert haben, können Sie seine Eigenschaften ändern und auf weitere Optionen zugreifen.

![](assets/s_ncs_user_report_wizard_08b.png)

Diese Optionen entsprechen denen von Standardberichten. Sie werden auf [dieser Seite](../../reporting/using/properties-of-the-report.md) beschrieben.

## Konfigurieren des Layouts eines beschreibenden Analyseberichts {#configuring-the-layout-of-a-descriptive-analysis-report}

Sie können die Anzeige und Anordnung Ihrer Daten in den Grafiken und Tabellen anpassen. Gehen Sie hierzu ausgehend vom Explorer in den Tab **[!UICONTROL Bearbeiten]** des Berichts, den Sie anpassen möchten.

### Anzeigemodus des Analyseberichts {#analysis-report-display-mode}

Wenn Sie einen Bericht basierend auf der Vorlage **[!UICONTROL Qualitative Verteilung]** erstellen, sind die Anzeigemodi Tabelle und Grafik standardmäßig ausgewählt. Wenn Sie nur einen der beiden Anzeigemodi verwenden möchten, wählen Sie den anderen ab: Nur der Tab des beibehaltenen Anzeigemodus bleibt verfügbar.

![](assets/s_ncs_advuser_report_display_01.png)

Wenn Sie im Nachhinein im Bericht Daten aus einem anderen Schema verwenden möchten, klicken Sie auf **[!UICONTROL Link auswählen]** und wählen Sie eine andere Tabelle der Datenbank aus.

![](assets/s_ncs_advuser_report_display_02.png)

### Anzeigeparameter des Analyseberichts {#analysis-report-display-settings}

Sie können den Namen der Statistiken und Zwischensummen anzeigen oder ausblenden und die Ausrichtung der Statistiken wählen.

![](assets/s_ncs_advuser_report_display_05.png)

Der Titel der Statistiken kann bei der Erstellung bestimmt werden.

![](assets/s_ncs_advuser_report_display_06.png)

Der angegebene Titel erscheint im Bericht.

![](assets/s_ncs_advuser_report_display_07.png)

Wenn Sie die Anzeigeoption der Titel und Zwischensummen jedoch abwählen, erscheinen diese nicht im Bericht. Der Name erscheint dennoch beim Überfahren einer Zelle der Tabelle mit dem Mauszeiger in einer QuickInfo.

![](assets/s_ncs_advuser_report_display_08.png)

Die Statistiken werden standardmäßig in Zeilen angezeigt. Um die Ausrichtung zu ändern, wählen Sie die gewünschte Option in der Dropdown-Liste aus.

![](assets/s_ncs_advuser_report_wizard_035a.png)

Im nachstehenden Beispiel werden die Statistiken in Spalten angezeigt:

![](assets/s_ncs_advuser_report_wizard_035.png)

### Anordnung der Daten in Analyseberichten {#analysis-report-data-layout}

Die Anordnung der Daten kann direkt in den Analyse-Tabellen angepasst werden. Machen Sie hierzu einen Rechtsklick auf die betreffende Variable. Wählen Sie eine der folgenden, im Kontextmenü verfügbaren Optionen aus:

* **[!UICONTROL Pivotieren]**: ändert die Achse der ausgewählten Variable;
* **[!UICONTROL Nach oben]**/**[!UICONTROL Nach unten]**: kehrt die Zeilen-Reihenfolge der Variablen in um;
* **[!UICONTROL Nach rechts verschieben]**/**[!UICONTROL Nach links verschieben]**: kehrt die Spalten-Reihenfolge der Variablen um;
* **[!UICONTROL Umkehren]**: kehrt die Achsen der Variablen um;
* **[!UICONTROL Von A bis Z sortieren]**: sortiert die Werte der Variable in aufsteigender Reihenfolge;
* **[!UICONTROL Von Z bis A sortieren]**: sortiert die Werte der Variable in absteigender Reihenfolge.

  ![](assets/s_ncs_advuser_report_wizard_016.png)

Um zur ursprünglichen Anzeige zurückzukehren, aktualisieren Sie die Ansicht.

### Grafikoptionen in Analyseberichten {#analysis-report-chart-options}

Auch die Anzeige der Daten einer Grafik kann vom Benutzer angepasst werden. Klicken Sie hierzu bei der Grafiktyp-Auswahl auf den Link **[!UICONTROL Grafikparameter...]**.

![](assets/s_ncs_advuser_report_wizard_3c.png)

Folgende Optionen stehen zur Verfügung:

* Im oberen Abschnitt des Fensters kann der Anzeigebereich der Grafik verändert werden.
* Standardmäßig werden die Titel in der Grafik angezeigt. Um sie auszublenden, deaktivieren Sie die Option **[!UICONTROL Werte anzeigen]**.
* Die Option **[!UICONTROL Werte kumulieren]** ermöglicht das Addieren der unterschiedlichen, von einer Serie zur anderen zurückgegebenen Werte.
* Die Legende der Grafik kann durch Deaktivieren der entsprechenden Option ausgeblendet werden. Die Legende wird standardmäßig außerhalb der Grafik oben rechts angezeigt.

  Die Legende kann auch über der Grafik angezeigt werden, um den Anzeigebereich zu sparen. Wählen Sie dazu die Option **[!UICONTROL In die Grafik einschließen]**

  Wählen Sie eine senkrechte oder vertikale Ausrichtung in der Dropdown-Liste **[!UICONTROL Legendenposition]** aus.

  ![](assets/s_ncs_advuser_report_wizard_3d.png)

## Exportieren eines Analyseberichts {#exporting-an-analysis-report}

Um Analyseberichte zu exportieren, wählen Sie in der Dropdown-Liste das gewünschte Ausgabeformat aus.

![](assets/s_ncs_user_report_wizard_09.png)

Weiterführende Informationen hierzu finden Sie auf dieser [Seite](../../reporting/using/actions-on-reports.md).

## Erneute Verwendung von bestehenden Berichten und Analysen {#re-using-existing-reports-and-analyses}

Sie können Berichte zur deskriptiven Analyse von Daten erstellen, indem Sie vorhandene, bereits in Adobe Campaign gespeicherte Berichte verwenden. Dieser Verwendungsmodus ist möglich, wenn die Analysen gespeichert oder die Berichte dahingehend erstellt und konfiguriert wurden, dass sie für den Assistenten für deskriptive Analysen zugänglich sind.

Informationen zum Speichern deskriptiver Analysen finden Sie unter [Analyseberichte speichern](#saving-an-analysis-report).

Um einen deskriptiven Analysebericht zu erstellen, muss der Assistent für deskriptive Analysen über einen Workflow oder das Menü **[!UICONTROL Werkzeuge > Deskriptive Analyse]** ausgeführt werden.

1. Wählen Sie **[!UICONTROL Existierende Analysen und Berichte]** aus und klicken Sie auf **[!UICONTROL Weiter]**.
1. Die Liste der verfügbaren Berichte wird angezeigt. Klicken Sie auf den Berichttitel, um ihn zu erzeugen.

   ![](assets/s_ncs_user_report_wizard_01.png)

## Archivieren von Analyseberichten {#archiving-analysis-reports}

Wenn Sie eine deskriptive Analyse basierend auf einer existierenden Analyse erstellen, haben Sie die Möglichkeit, Verläufe zu erstellen. Dies erlaubt die Speicherung der Daten von einer Analyse zur anderen und den Vergleich der unterschiedlichen Ergebnisse Ihrer Berichte.

Gehen Sie wie folgt vor, um einen Verlauf zu erstellen:

1. Öffnen Sie eine existierende Analyse oder erstellen Sie einen neuen Assistenten für deskriptive Analysen.
1. Klicken Sie auf die Schaltfläche zur Erstellung eines Verlaufs in der Symbolleiste und bestätigen Sie Ihre Auswahl, wie im folgenden Beispiel:

   ![](assets/reporting_descriptive_historize_icon.png)

1. Über die entsprechende Schaltfläche können Sie auf frühere Analysen zugreifen.

   ![](assets/reporting_descriptive_historize_access.png)
