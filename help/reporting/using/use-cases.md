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
translation-type: ht
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: ht
source-wordcount: '1422'
ht-degree: 100%

---


# Anwendungsbeispiele{#use-cases}

## Populationen analysieren {#analyzing-a-population}

Im unten stehenden Beispiel wird mithilfe des Assistenten zur deskriptiven Analyse die Zielgruppe einer Newsletter-Serie untersucht.

Die Durchführungsschritte werden im Nachstehenden beschrieben, die verschiedenen Optionen und ihre Beschreibungen werden in den anderen Abschnitten dieses Kapitels ausführlich dargestellt.

### Zu analysierende Population identifizieren {#identifying-the-population-to-analyze}

In unserem Beispiel werden die Zielgruppen der im Ordner **Newsletter** enthaltenen Sendungen untersucht.

Markieren Sie hierzu die betreffenden Sendungen und wählen Sie per Rechtsklick im Kontextmenü **[!UICONTROL Aktion > Ergebnis analysieren...]** aus.

![](assets/reporting_quick_start_1.png)

### Zu realisierenden Analysetyp wählen {#selecting-a-type-of-analysis}

Im ersten Schritt des Assistenten können Sie die zu verwendende deskriptive Analysevorlage auswählen. Adobe Campaign bietet standardmäßig zwei Vorlagen: **[!UICONTROL Qualitative Verteilung]** und **[!UICONTROL Quantitative Verteilung]**. Lesen Sie diesbezüglich den Abschnitt [Vorlage „Quantitative Verteilung“ konfigurieren](../../reporting/using/using-the-descriptive-analysis-wizard.md#configuring-the-qualitative-distribution-template). Die verschiedenen Renderings werden im Abschnitt [Über die deskriptive Analyse](../../reporting/using/about-descriptive-analysis.md) dargestellt.

Wählen Sie für das Beispiel die Vorlage **[!UICONTROL Qualitative Verteilung]** und eine Anzeige mit Grafik und Tabelle aus. Nennen Sie den Bericht &quot;Meine deskriptive Analyse&quot; und klicken Sie auf die Schaltfläche **[!UICONTROL Weiter]**.

![](assets/reporting_descriptive_quickstart_step_1.png)

### Anzuzeigende Variablen auswählen {#selecting-the-variables-to-display}

Im nächsten Schritt werden die in der Tabelle anzuzeigenden Daten ausgewählt.

Klicken Sie auf den Link **[!UICONTROL Hinzufügen]**, um die Variable auszuwählen, die die anzuzeigenden Daten enthält. In unserem Beispiel sollen die Wohnorte der Versandempfänger in Zeilen angezeigt werden:

![](assets/reporting_descriptive_quickstart_step_2.png)

Die Spalten sollen den jeweiligen Einkaufsbetrag der Empfänger anzeigen. In unserem Beispiel werden die Beträge im Feld **Online-Bestellungen 2014** aggregiert.

Die Bestimmung einer Klassierung erlaubt eine übersichtliche Anzeige der Ergebnisse. Wählen Sie die Option **[!UICONTROL Manuell]** aus und geben Sie Begrenzungen für die Berechnung der anzuzeigenden Segmente an:

![](assets/reporting_descriptive_quickstart_step_2a.png)

Klicken Sie dann auf **[!UICONTROL OK]**, um die Konfiguration zu bestätigen.

Nach der Festlegung der Zeilen und Spalten können Sie sie über die Symbolleiste verändern, verschieben oder löschen.

![](assets/reporting_descriptive_quickstart_step_2b.png)

### Anzeigeformat bestimmen {#defining-the-display-format}

Im folgenden Schritt des Assistenten wird der zu erzeugende Grafiktyp festgelegt.

In diesem Beispiel wird das Histogramm gewählt.

![](assets/reporting_descriptive_quickstart_step_3.png)

Mögliche Konfigurationen der verschiedenen Grafiken werden im Abschnitt [Grafikoptionen in Analyseberichten](../../reporting/using/processing-a-report.md#analysis-report-chart-options) aufgeführt.

### Zu berechnende Statistiken konfigurieren {#configuring-the-statistic-to-calculate}

Geben Sie anschließend die mit den abgerufenen Daten durchzuführenden Berechnungen an. Der Analyse-Assistent führt standardmäßig eine einfache Zählung der Werte durch.

In diesem Fenster können Sie die Liste der zu berechnenden Statistiken bestimmen.

![](assets/reporting_descriptive_quickstart_step_4.png)

Um eine neue Statistik zu erstellen, klicken Sie auf die Schaltfläche **[!UICONTROL Hinzufügen]**. Weitere Informationen hierzu finden Sie im Abschnitt [Statistikberechnung](../../reporting/using/using-the-descriptive-analysis-wizard.md#statistics-calculation).

### Berichte anzeigen und nutzen {#viewing-and-using-the-report}

Im letzten Schritt des Assistenten werden Tabelle und Grafik angezeigt.

Sie können Daten über die Symbolleiste oberhalb der Tabelle speichern, exportieren oder drucken. Weitere Informationen finden Sie unter [Berichtbearbeitung](../../reporting/using/processing-a-report.md).

![](assets/reporting_descriptive_quickstart_step_5.png)

## Qualitative Datenanalyse {#qualitative-data-analysis}

### Beispiel: Anzeige als Grafik {#example-of-a-chart-display}

**Ziel**: Erzeugung eines Analyseberichts über die Standorte von Interessenten und Kunden.

1. Öffnen Sie den Analyse-Assistenten und wählen Sie nur den Anzeigemodus **[!UICONTROL Grafik]** aus.

   ![](assets/s_ncs_user_report_wizard_05a.png)

   Klicken Sie zur Bestätigung auf **[!UICONTROL Weiter]**.

1. Wählen Sie anschließend die Option **[!UICONTROL 2 Variablen]** und geben Sie an, dass sich die **[!UICONTROL erste Variable (Abzisse)]** auf den Empfängerstatus (Interessenten/Kunden) bezieht und die zweite auf das Land.
1. Wählen Sie den Grafiktyp **[!UICONTROL Histogramm]**.

   ![](assets/s_ncs_user_report_wizard_05.png)

1. Klicken Sie auf **[!UICONTROL Weiter]** und behalten Sie die Standardstatistik bei: **[!UICONTROL Einfache Zählung]**.
1. Klicken Sie auf **[!UICONTROL Weiter]**, um den Bericht anzuzeigen.

   ![](assets/s_ncs_user_report_wizard_04.png)

   Um die genaue Anzahl an Kunden oder Interessenten für ein Land zu kennen, überfahren Sie die entsprechende Säule mit dem Mauszeiger.

1. Über die Legende können Sie die Anzeige einzelner Länder aktivieren oder deaktivieren.

   ![](assets/s_ncs_user_report_wizard_06png.png)

### Beispiel: Anzeige als Tabelle {#example-of-a-table-display}

**Ziel**: Analyse der E-Mail-Domains unterschiedlicher Firmen.

1. Öffnen Sie den Analyse-Assistenten und wählen Sie nur den Anzeigemodus **[!UICONTROL Tabelle]** aus.

   ![](assets/s_ncs_user_report_wizard_03a.png)

   Klicken Sie zur Bestätigung auf die Schaltfläche **[!UICONTROL Weiter]**.

1. Wählen Sie die Variable **[!UICONTROL Firma]** in Spalten und die Variable **[!UICONTROL E-Mail-Domain]** in Zeilen aus.
1. Lassen Sie die Option **[!UICONTROL In Zeilen]** für die Ausrichtung der Statistiken: Die Berechnung der Statistik wird rechts von der Variable **[!UICONTROL E-Mail-Domain]** angezeigt.

   ![](assets/s_ncs_user_report_wizard_03b.png)

   Klicken Sie zur Bestätigung auf **[!UICONTROL Weiter]**.

1. Geben Sie anschließend die zu berechnenden Statistiken an: Behalten Sie die Standard-Zählung bei und erstellen Sie eine neue Statistik. Klicken Sie hierzu auf **[!UICONTROL Hinzufügen]** und wählen Sie die Funktion **[!UICONTROL Verteilung in Prozent über die Gesamtheit]**.

   ![](assets/s_ncs_user_report_wizard_03.png)

1. Geben Sie der Statistik zur besseren Lesbarkeit der Berichtsinhalte einen Titel.

   ![](assets/s_ncs_user_report_wizard_014.png)

1. Klicken Sie auf **[!UICONTROL Weiter]**, um den Bericht anzuzeigen.

   ![](assets/s_ncs_user_report_wizard_06.png)

1. Sobald der Analysebericht erzeugt wurde, können Sie seine Anzeige Ihren Bedürfnissen entsprechend anpassen, ohne seine Konfiguration zu ändern. Sie haben beispielsweise die Möglichkeit, die Achsen zu vertauschen: Machen Sie hierzu einen Rechtsklick auf die die Domänen enthaltende Zeile und wählen Sie im Kontextmenü **[!UICONTROL Umkehren]**.

   ![](assets/s_ncs_user_report_wizard_07.png)

   Die Tabelle stellt nun die Ergebnisse folgendermaßen dar:

   ![](assets/s_ncs_user_report_wizard_07a.png)

## Quantitative Datenanalyse {#quantitative-data-analysis}

**Ziel**: Erzeugung eines Berichts zur quantitativen Analyse des Empfängeralters.

1. Öffnen Sie den Assistenten zur deskriptiven Analyse und wählen Sie die Analysevorlage **[!UICONTROL Quantitative Verteilung]** aus.

   ![](assets/s_ncs_user_report_wizard_011a.png)

   Klicken Sie zur Bestätigung auf die Schaltfläche **[!UICONTROL Weiter]**.

1. Wählen Sie anschließend die Variable **[!UICONTROL Alter]** aus und benennen Sie sie. Geben Sie an, dass es sich um einen Integer handelt und klicken Sie dann auf **[!UICONTROL Weiter]**.

   ![](assets/s_ncs_user_report_wizard_011.png)

1. Löschen Sie unnötige Statistiken, hier **[!UICONTROL Dezile]**, **[!UICONTROL Verteilung]** und **[!UICONTROL Summe]**.

   ![](assets/s_ncs_user_report_wizard_012.png)

1. Klicken Sie auf **[!UICONTROL Weiter]**, um den Bericht anzuzeigen.

   ![](assets/s_ncs_user_report_wizard_013.png)

## Analyse der Zielgruppe einer Workflow-Transition {#analyzing-a-transition-target-in-a-workflow}

**Ziel**: Erzeugung von Berichten über die Population eines Zielgruppen-Workflows.

1. Öffnen Sie einen Zielgruppen-Workflow Ihrer Wahl.
1. Machen Sie einen Rechtsklick auf eine Transition, die auf die Empfängertabelle zeigt.
1. Wählen Sie im Kontextmenü **[!UICONTROL Ergebnis analysieren...]** aus, um den Assistenten zur deskriptiven Analyse zu öffnen.

   ![](assets/s_ncs_user_report_wizard_from_transision.png)

1. An dieser Stelle können Sie entweder die Option **[!UICONTROL Existierende Analysen und Berichte erneut verwenden]** auswählen und zuvor erstellte Berichte nutzen (siehe [Existierende Analysen und Berichte erneut verwenden ](../../reporting/using/processing-a-report.md#re-using-existing-reports-and-analyses)) oder eine neue deskriptive Analyse erstellen. Lassen Sie dazu die Option **[!UICONTROL Neue deskriptive Analyse basierend auf einer Vorlage]** standardmäßig aktiviert.

   Die weitere Konfiguration entspricht der der zuvor dargestellten deskriptiven Analysen.

### Empfehlungen zur Analyse von Zielgruppen {#target-analyze-recommendations}

Die Analyse einer Zielgruppe in einem Workflow setzt voraus, dass die Population noch in der Transition präsent ist. Wenn der Workflow gestartet wurde, kann es sein, dass die Transition und damit die Population bereinigt wird. Sie haben folgende Möglichkeiten, eine Analyse durchzuführen:

* die Transition von ihrer Zielaktivität lösen und den Workflow starten, um sie zu aktivieren. Sobald die Transition blinkt, können Sie den Assistenten wie gewohnt starten.

   ![](assets/s_ncs_user_report_wizard_018.png)

* in den Eigenschaften des Workflows die Option **[!UICONTROL Zwischen zwei Ausführungen die ermittelte Population festhalten]** aktivieren. Auf diese Weise können Sie auch nach Abschluss des Workflows eine Analyse auf der Transition Ihrer Wahl starten.

   ![](assets/s_ncs_user_report_wizard_020.png)

   Wenn die Transition von der Population bereinigt wurde, fordert eine entsprechende Fehlernachricht dazu auf, die besagte Option zu aktivieren, bevor der Analyse-Assistent gestartet wird.

   ![](assets/s_ncs_user_report_wizard_019.png)

>[!CAUTION]
>
>Die Option **[!UICONTROL Zwischen zwei Ausführungen die ermittelte Population festhalten]** darf nur in Entwicklungsphasen und niemals in einer Produktionsumgebung verwendet werden.\
>Die betreffenden Populationen werden automatisch bereinigt, sobald ihre Beibehaltungsdauer abgelaufen ist. Diese Dauer wird im Tab **[!UICONTROL Ausführung]** der Workflow-Eigenschaften festgelegt.

## Analyse der Empfänger-Trackinglogs {#analyzing-recipient-tracking-logs}

Mithilfe des Assistenten der deskriptiven Analyse können auch Berichte über andere Arbeitstabellen als die Empfängertabelle erzeugt werden. Sie können zum Beispiel Versandlogs analysieren.

Im folgenden Beispiel wird die Reaktionsrate der Empfänger von Newslettern untersucht.

Gehen Sie hierzu wie folgt vor:

1. Öffnen Sie den Analyse-Assistenten über das Menü **[!UICONTROL Werkzeuge > Deskriptive Analyse...]** und ändern Sie die standardmäßige Arbeitstabelle: Wählen Sie **[!UICONTROL Trackinglogs der Empfänger]** aus. Fügen Sie einen Filter hinzu, damit die Analyse sich nur auf Newsletter bezieht und Testsendungen ausschließt.

   ![](assets/reporting_descriptive_sample_tracking_1.png)

   Wählen Sie nur den Tabellen-Anzeigemodus aus und klicken Sie auf **[!UICONTROL Weiter]**.

1. Geben Sie im nächsten Schritt an, dass die Analyse sich auf Sendungen bezieht.

   ![](assets/reporting_descriptive_sample_tracking_2.png)

   Im vorliegenden Beispiel werden die Sendungen in der ersten Spalte angezeigt.

1. Löschen Sie die Standard-Zählung und erstellen Sie die drei Statistiken, die in der Tabelle angezeigt werden sollen:

   Im Beispiel soll die Tabelle für jeden Newsletter folgende Informationen anzeigen: die Anzahl der Öffnungen, die Anzahl der Klicks und die Reaktionsrate (in Prozent).

1. Fügen Sie eine Statistik hinzu, um die Anzahl der Klicks zu zählen: Erstellen Sie den entsprechenden Filter im Tab **[!UICONTROL Filter]**.

   ![](assets/reporting_descriptive_sample_tracking_3.png)

1. Gehen Sie dann in den Tab **[!UICONTROL Allgemein]**, um den Titel der Statistik und ihren Alias anzupassen:

   ![](assets/reporting_descriptive_sample_tracking_4.png)

1. Fügen Sie eine zweite Statistik hinzu, um die Anzahl der Öffnungen zu zählen:

   ![](assets/reporting_descriptive_sample_tracking_5.png)

1. Gehen Sie dann in den Tab **[!UICONTROL Allgemein]**, um den Titel der Statistik und ihren Alias anzupassen:

   ![](assets/reporting_descriptive_sample_tracking_6.png)

1. Fügen Sie eine letzte Statistik hinzu und wählen Sie die Funktion **[!UICONTROL Berechnetes Feld]** aus, um die Reaktionsrate zu messen.

   ![](assets/reporting_descriptive_sample_tracking_7.png)

   Erfassen Sie im Feld **[!UICONTROL Benutzerfunktion]** die folgende Formel:

   ```
   @clic / @open * 100
   ```

   Passen Sie den Titel der Statistik wie unten gezeigt an:

   ![](assets/reporting_descriptive_sample_tracking_8.png)

   Geben Sie schließlich an, dass die Werte in Prozent angezeigt werden sollen: Deaktivieren Sie hierzu die Option **[!UICONTROL Standardformatierung]** des Tabs **[!UICONTROL Erweitert]** und wählen Sie **[!UICONTROL Prozent]** ohne Dezimalstelle aus.

   ![](assets/reporting_descriptive_sample_tracking_10.png)

1. Klicken Sie auf **[!UICONTROL Weiter]**, um den Bericht anzuzeigen.

   ![](assets/reporting_descriptive_sample_tracking_9.png)

## Analyse der Versand-Ausschlusslogs {#analyzing-delivery-exclusion-logs}

Wenn sich die Analyse auf einen Versand bezieht, besteht die Möglichkeit, die ausgeschlossene Population zu analysieren. Markieren Sie hierzu die zu analysierenden Sendungen und wählen Sie per Rechtsklick im Kontextmenü **[!UICONTROL Aktion > Ausschlüsse analysieren...]** aus.

![](assets/reporting_descriptive_exclusion_menu.png)

Daraufhin öffnet sich der Analyse-Assistent. Die Analyse bezieht sich automatisch auf die Ausschlusslogs.

Sie können beispielsweise die Domains der ausgeschlossenen Adressen nach Ausschlussdatum anzeigen lassen:

![](assets/reporting_descriptive_exclusion_sample.png)

Dies ergibt einen Bericht dieser Art:

![](assets/reporting_descriptive_exclusion_result.png)

