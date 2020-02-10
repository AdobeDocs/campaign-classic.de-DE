---
title: Anwendungsbeispiele
seo-title: Anwendungsbeispiele
description: Anwendungsbeispiele
seo-description: null
page-status-flag: never-activated
uuid: 86762d94-2a7d-4053-980b-c699a58a021d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: analyzing-populations
discoiquuid: 691eea2c-bffc-4520-91c8-43798eece916
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: af768da6ee8cc0ca2ea1f24f297239b974c113a5

---


# Anwendungsbeispiele{#use-cases}

## Populationen analysieren {#analyzing-a-population}

Im unten stehenden Beispiel wird mithilfe des Assistenten zur deskriptiven Analyse die Zielgruppe einer Newsletter-Serie untersucht.

Die Durchführungsschritte werden im Nachstehenden beschrieben, die verschiedenen Optionen und ihre Beschreibungen werden in den anderen Abschnitten dieses Kapitels ausführlich dargestellt.

### Zu analysierende Population identifizieren {#identifying-the-population-to-analyze}

In unserem Beispiel werden die Zielgruppen der im Ordner **Newsletter** enthaltenen Sendungen untersucht.

Wählen Sie dazu die gewünschten Auslieferungen aus, klicken Sie mit der rechten Maustaste und wählen Sie **[!UICONTROL Action > Explore the target...]**.

![](assets/reporting_quick_start_1.png)

### Zu realisierenden Analysetyp wählen {#selecting-a-type-of-analysis}

Im ersten Schritt der Assistenzkraft können Sie die zu verwendende beschreibende Analysevorlage auswählen.  Adobe Campaign bietet standardmäßig zwei Vorlagen: **[!UICONTROL Qualitative distribution]** und **[!UICONTROL Quantitative distribution]**. For more on this refer to the [Configuring the qualitative distribution template](../../reporting/using/using-the-descriptive-analysis-wizard.md#configuring-the-qualitative-distribution-template) section. Die verschiedenen Renderings werden im Abschnitt [Info zur beschreibenden Analyse](../../reporting/using/about-descriptive-analysis.md) dargestellt.

Wählen Sie in diesem Beispiel die **[!UICONTROL Qualitative distribution]** Vorlage aus und wählen Sie eine Anzeige mit einem Diagramm und einer Tabelle (Array). Geben Sie dem Bericht einen Namen (&quot;Deskriptive Analyse&quot;) und klicken Sie auf **[!UICONTROL Next]**.

![](assets/reporting_descriptive_quickstart_step_1.png)

### Anzuzeigende Variablen auswählen {#selecting-the-variables-to-display}

Im nächsten Schritt werden die in der Tabelle anzuzeigenden Daten ausgewählt.

Klicken Sie auf den **[!UICONTROL Add...]** Link, um die Variable auszuwählen, die die anzuzeigenden Daten enthält. Hier wollen wir die Städte unserer Empfänger in einer Zeile anzeigen:

![](assets/reporting_descriptive_quickstart_step_2.png)

Die Spalten sollen den jeweiligen Einkaufsbetrag der Empfänger anzeigen. In unserem Beispiel werden die Beträge im Feld **Online-Bestellungen 2014** aggregiert.

Hier wollen wir das Ergebnis-Targeting definieren, um ihre Darstellung zu verdeutlichen. Wählen Sie dazu die Option **[!UICONTROL Manual]** Binnen und legen Sie die Berechnungsklassen für die anzuzeigenden Segmente fest:

![](assets/reporting_descriptive_quickstart_step_2a.png)

Klicken Sie dann auf **[!UICONTROL Ok]**, um die Konfiguration zu bestätigen.

Nach der Festlegung der Zeilen und Spalten können Sie sie über die Symbolleiste verändern, verschieben oder löschen.

![](assets/reporting_descriptive_quickstart_step_2b.png)

### Anzeigeformat bestimmen {#defining-the-display-format}

Im folgenden Schritt des Assistenten wird der zu erzeugende Grafiktyp festgelegt.

In diesem Beispiel wird das Histogramm gewählt.

![](assets/reporting_descriptive_quickstart_step_3.png)

Mögliche Konfigurationen der verschiedenen Grafiken sind im Abschnitt [Optionen](../../reporting/using/processing-a-report.md#analysis-report-chart-options) des Analyseberichts aufgeführt.

### Zu berechnende Statistiken konfigurieren {#configuring-the-statistic-to-calculate}

Geben Sie anschließend die mit den abgerufenen Daten durchzuführenden Berechnungen an. Der Analyse-Assistent führt standardmäßig eine einfache Zählung der Werte durch.

In diesem Fenster können Sie die Liste der zu berechnenden Statistiken bestimmen.

![](assets/reporting_descriptive_quickstart_step_4.png)

Um eine neue Statistik zu erstellen, klicken Sie auf die **[!UICONTROL Add]** Schaltfläche. For more on this, refer to [Statistics calculation](../../reporting/using/using-the-descriptive-analysis-wizard.md#statistics-calculation).

### Berichte anzeigen und nutzen {#viewing-and-using-the-report}

Im letzten Schritt des Assistenten werden Tabelle und Grafik angezeigt.

Sie können Daten über die Symbolleiste oberhalb der Tabelle speichern, exportieren oder drucken. For more on this, refer to [Processing a report](../../reporting/using/processing-a-report.md).

![](assets/reporting_descriptive_quickstart_step_5.png)

## Qualitative Datenanalyse {#qualitative-data-analysis}

### Beispiel: Anzeige als Grafik {#example-of-a-chart-display}

**Ziel**: Erzeugung eines Analyseberichts über die Standorte von Interessenten und Kunden.

1. Open the descriptive analysis wizard and select **[!UICONTROL Chart]** only.

   ![](assets/s_ncs_user_report_wizard_05a.png)

   Click **[!UICONTROL Next]** to approve this step.

1. Then select the **[!UICONTROL 2 variables]** option and specify that the **[!UICONTROL First variable (abscissa)]** will refer to recipient status (prospects/customers) and the second variable will refer to the country.
1. Select **[!UICONTROL Cylinders]** as a type.

   ![](assets/s_ncs_user_report_wizard_05.png)

1. Klicken Sie auf **[!UICONTROL Next]** und lassen Sie die Standardstatistik **[!UICONTROL Simple count]** unverändert.
1. Click **[!UICONTROL Next]** to display the report.

   ![](assets/s_ncs_user_report_wizard_04.png)

   Um die genaue Anzahl an Kunden oder Interessenten für ein Land zu kennen, überfahren Sie die entsprechende Säule mit dem Mauszeiger.

1. Über die Legende können Sie die Anzeige einzelner Länder aktivieren oder deaktivieren.

   ![](assets/s_ncs_user_report_wizard_06png.png)

### Beispiel: Anzeige als Tabelle {#example-of-a-table-display}

**Ziel**: Analyse der E-Mail-Domains unterschiedlicher Firmen.

1. Open the descriptive analysis wizard and select the **[!UICONTROL Array]** display mode only.

   ![](assets/s_ncs_user_report_wizard_03a.png)

   Click the **[!UICONTROL Next]** button to approve this step.

1. Select the **[!UICONTROL Company]** variable as a column and the **[!UICONTROL Email domain]** variable as a row.
1. Keep the **[!UICONTROL By rows]** option for statistics orientation: the statistic calculation will be displayed to the right of the **[!UICONTROL Email domain]** variable.

   ![](assets/s_ncs_user_report_wizard_03b.png)

   Click **[!UICONTROL Next]** to approve this step.

1. Geben Sie dann die zu berechnenden Statistiken ein: die Standardanzahl beibehalten und eine neue Statistik erstellen. Klicken Sie dazu auf **[!UICONTROL Add]** und wählen Sie **[!UICONTROL Total percentage distribution]** als Operator aus.

   ![](assets/s_ncs_user_report_wizard_03.png)

1. Geben Sie der Statistik zur besseren Lesbarkeit der Berichtsinhalte einen Titel.

   ![](assets/s_ncs_user_report_wizard_014.png)

1. Click **[!UICONTROL Next]** to display the report.

   ![](assets/s_ncs_user_report_wizard_06.png)

1. Nachdem der Analysebericht erstellt wurde, können Sie die Anzeige an Ihre Anforderungen anpassen, ohne die Konfiguration zu ändern. Sie können beispielsweise die Achsen wechseln: Klicken Sie mit der rechten Maustaste auf die Domänennamen und wählen Sie **[!UICONTROL Turn]** im Kontextmenü.

   ![](assets/s_ncs_user_report_wizard_07.png)

   Die Tabelle stellt nun die Ergebnisse folgendermaßen dar:

   ![](assets/s_ncs_user_report_wizard_07a.png)

## Quantitative Datenanalyse {#quantitative-data-analysis}

**Ziel**: Erzeugung eines Berichts zur quantitativen Analyse des Empfängeralters.

1. Open the descriptive analysis wizard and select **[!UICONTROL Quantitative distribution]** from the drop-down list.

   ![](assets/s_ncs_user_report_wizard_011a.png)

   Click the **[!UICONTROL Next]** button to approve this step.

1. Wählen Sie die **[!UICONTROL Age]** Variable aus und geben Sie deren Bezeichnung ein. Geben Sie an, ob es sich um eine Ganzzahl handelt, und klicken Sie dann auf **[!UICONTROL Next]**.

   ![](assets/s_ncs_user_report_wizard_011.png)

1. Löschen Sie die **[!UICONTROL Deciles]**- **[!UICONTROL Distribution]** und **[!UICONTROL Sum]** -Statistiken: sie werden hier nicht gebraucht.

   ![](assets/s_ncs_user_report_wizard_012.png)

1. Click **[!UICONTROL Next]** to display the report.

   ![](assets/s_ncs_user_report_wizard_013.png)

## Analyse der Zielgruppe einer Workflow-Transition {#analyzing-a-transition-target-in-a-workflow}

**Ziel**: Erzeugung von Berichten über die Population eines Zielgruppen-Workflows.

1. Öffnen Sie einen Zielgruppen-Workflow Ihrer Wahl.
1. Machen Sie einen Rechtsklick auf eine Transition, die auf die Empfängertabelle zeigt.
1. Select **[!UICONTROL Analyze target]** in the drop-down menu to open the descriptive analysis window.

   ![](assets/s_ncs_user_report_wizard_from_transision.png)

1. An dieser Stelle können Sie entweder die **[!UICONTROL Existing analyses and reports]** Option auswählen und zuvor erstellte Berichte verwenden (siehe [Wiederverwenden vorhandener Berichte und Analysen](../../reporting/using/processing-a-report.md#re-using-existing-reports-and-analyses)) oder eine neue beschreibende Analyse erstellen. Lassen Sie dazu die **[!UICONTROL New descriptive analysis from a template]** Option standardmäßig aktiviert.

   Die weitere Konfiguration entspricht der der zuvor dargestellten deskriptiven Analysen.

### Empfehlungen zur Analyse von Zielgruppen {#target-analyze-recommendations}

Die Analyse einer Zielgruppe in einem Workflow setzt voraus, dass die Population noch in der Transition präsent ist. Wenn der Workflow gestartet wurde, kann es sein, dass die Transition und damit die Population bereinigt wird. Sie haben folgende Möglichkeiten, eine Analyse durchzuführen:

* die Transition von ihrer Zielaktivität lösen und den Workflow starten, um sie zu aktivieren. Sobald die Transition blinkt, können Sie den Assistenten wie gewohnt starten.

   ![](assets/s_ncs_user_report_wizard_018.png)

* Ändern Sie die Eigenschaften des Workflows, indem Sie die **[!UICONTROL Keep the result of interim populations between two executions]** Option auswählen. Auf diese Weise können Sie eine Analyse des Übergangs Ihrer Wahl starten, auch wenn der Workflow abgeschlossen ist.

   ![](assets/s_ncs_user_report_wizard_020.png)

   Wenn die Transition von der Population bereinigt wurde, fordert eine entsprechende Fehlernachricht dazu auf, die besagte Option zu aktivieren, bevor der Analyse-Assistent gestartet wird.

   ![](assets/s_ncs_user_report_wizard_019.png)

>[!CAUTION]
>
>Die **[!UICONTROL Keep the result of interim populations between two executions]** Option darf nur in Entwicklungsphasen verwendet werden, aber nie für eine Umgebung in der Produktion.\
>Die zwischenzeitlichen Populationen werden nach Erreichen ihrer Haltungsfrist automatisch bereinigt. Dieser Termin wird auf der **[!UICONTROL Execution]** Registerkarte &quot;Workflow-Eigenschaften&quot;angegeben.

## Analyse der Empfänger-Trackinglogs {#analyzing-recipient-tracking-logs}

Mithilfe des Assistenten der deskriptiven Analyse können auch Berichte über andere Arbeitstabellen als die Empfängertabelle erzeugt werden. Sie können zum Beispiel Versandlogs analysieren.

Im folgenden Beispiel wird die Reaktionsrate der Empfänger von Newslettern untersucht.

Gehen Sie hierzu wie folgt vor:

1. Öffnen Sie den Assistenten für die deskriptive Analyse über das **[!UICONTROL Tools > Descriptive analysis]** Menü und ändern Sie die Standard-Arbeitstabelle. Wählen Sie **[!UICONTROL Recipient tracking log]** und fügen Sie einen Filter hinzu, um Proofs auszuschließen und Newsletter einzuschließen.

   ![](assets/reporting_descriptive_sample_tracking_1.png)

   Select a table display and click **[!UICONTROL Next]**.

1. Geben Sie im nächsten Schritt an, dass die Analyse sich auf Sendungen bezieht.

   ![](assets/reporting_descriptive_sample_tracking_2.png)

   Im vorliegenden Beispiel werden die Sendungen in der ersten Spalte angezeigt.

1. Löschen Sie die Standard-Zählung und erstellen Sie die drei Statistiken, die in der Tabelle angezeigt werden sollen:

   Im Beispiel soll die Tabelle für jeden Newsletter folgende Informationen anzeigen: die Anzahl der Öffnungen, die Anzahl der Klicks und die Reaktionsrate (in Prozent).

1. Fügen Sie eine Statistik hinzu, um die Anzahl der Klicks zu zählen: Erstellen Sie den entsprechenden im Tab **[!UICONTROL Filter]** Filter.

   ![](assets/reporting_descriptive_sample_tracking_3.png)

1. Then click the **[!UICONTROL General]** tab to rename the statistics label and alias:

   ![](assets/reporting_descriptive_sample_tracking_4.png)

1. Fügen Sie eine zweite Statistik hinzu, um die Anzahl der Öffnungen zu zählen:

   ![](assets/reporting_descriptive_sample_tracking_5.png)

1. Then click the **[!UICONTROL General]** tab to rename the statistics label and its alias:

   ![](assets/reporting_descriptive_sample_tracking_6.png)

1. Add the third statistic and select the **[!UICONTROL Calculated field]** operator to measure the reactivity rate.

   ![](assets/reporting_descriptive_sample_tracking_7.png)

   Go to the **[!UICONTROL User function]** field and enter the following formula:

   ```
   @clic / @open * 100
   ```

   Passen Sie den Titel der Statistik wie unten gezeigt an:

   ![](assets/reporting_descriptive_sample_tracking_8.png)

   Finally, specify whether the values are shown as a percentage: to do this, uncheck the **[!UICONTROL Default formatting]** option in the **[!UICONTROL Advanced]** tab and select **[!UICONTROL Percentage]** without a decimal point.

   ![](assets/reporting_descriptive_sample_tracking_10.png)

1. Click **[!UICONTROL Next]** to display the report.

   ![](assets/reporting_descriptive_sample_tracking_9.png)

## Analyse der Versand-Ausschlusslogs {#analyzing-delivery-exclusion-logs}

Wenn die Analyse eine Lieferung betrifft, können Sie die ausgeschlossene Population analysieren. Wählen Sie dazu die zu analysierenden Auslieferungen aus und klicken Sie mit der rechten Maustaste auf das **[!UICONTROL Action > Explore exclusions]** Menü.

![](assets/reporting_descriptive_exclusion_menu.png)

Daraufhin öffnet sich der Analyse-Assistent. Die Analyse bezieht sich automatisch auf die Ausschlusslogs.

Sie können beispielsweise die Domains der ausgeschlossenen Adressen nach Ausschlussdatum anzeigen lassen:

![](assets/reporting_descriptive_exclusion_sample.png)

Dies ergibt einen Bericht dieser Art:

![](assets/reporting_descriptive_exclusion_result.png)

