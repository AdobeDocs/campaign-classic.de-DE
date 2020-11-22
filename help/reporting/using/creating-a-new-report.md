---
solution: Campaign Classic
product: campaign
title: Neue Berichte erstellen
description: Wichtige Schritte zum Erstellen eines neuen Berichts
audience: reporting
content-type: reference
topic-tags: creating-new-reports
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '961'
ht-degree: 100%

---


# Neue Berichte erstellen{#creating-a-new-report}

Gehen Sie wie folgt vor, um einen Bericht zu erstellen:

1. Öffnen Sie den Adobe-Campaign-Explorer und wählen Sie im Knoten **[!UICONTROL Administration > Konfiguration]** den Ordner **[!UICONTROL Berichte]** aus.
1. Klicken Sie auf die Schaltfläche **[!UICONTROL Neu]** rechts oberhalb der Liste der Berichte.
1. Wählen Sie **[!UICONTROL Neuen Bericht basierend auf einer Vorlage erstellen]** aus und klicken Sie auf **[!UICONTROL Weiter]**.

   ![](assets/s_ncs_advuser_report_wizard_new_01.png)

1. Wählen Sie die Berichtvorlage in der Dropdown-Liste aus.

   * Anhand der Vorlage **[!UICONTROL Erweiterter Bericht]** kann ein mithilfe eines Diagramms konfigurierter Bericht erstellt werden.
   * Der Bericht **[!UICONTROL Qualitative Verteilung]** ermöglicht die Erzeugung von Statistiken über alle Datentypen (z. B. Firmennamen, E-Mail-Domains etc.).
   * Der Bericht **[!UICONTROL Quantitative Verteilung]** ermöglicht Statistiken über Daten, die gemessen oder gezählt werden können (Rechnungsbetrag, Alter der Empfänger etc.).

   Nähere Informationen über diese Berichtvorlagen erhalten Sie in [diesem Abschnitt](../../reporting/using/about-descriptive-analysis.md).

1. Erfassen Sie den Namen des Berichts und seine Beschreibung in den entsprechenden Feldern. Geben Sie das **[!UICONTROL Schema]** an, auf das sich der Bericht beziehen soll.

   ![](assets/s_ncs_advuser_report_wizard_020.png)

1. Speichern Sie den Bericht.

## Gestaltung des Diagramms {#modelizing-the-chart}

Nach der Speicherung des Berichts wird dieser angezeigt. Sie können nun das Diagramm Ihres Berichts erstellen.

![](assets/s_ncs_user_report_wizard_021.png)

Das Berichtdiagramm besteht aus einer linearen Aneinanderreihung von Aktivitäten.

![](assets/s_ncs_advuser_report_wizard_031.png)

Diese werden untereinander durch Pfeile - sogenannte Transitionen - verbunden.

![](assets/s_ncs_advuser_report_wizard_032.png)

Um den Bericht entsprechend seiner Art und seines Verwendungskontexts zu konstruieren, müssen zunächst die nützlichen Elemente und ihre logische Aneinanderreihung identifiziert werden.

1. Nutzen Sie die **[!UICONTROL Beginn]**-Aktivität, um den ersten, zur Erstellung des Berichts auszuführenden Vorgang darzustellen. Diese Aktivität kann in jedem Bericht nur einmal verwendet werden.

   Wenn das Diagramm eine Schleife enthält, ist die &quot;Beginn&quot;-Aktivität obligatorisch.

1. Fügen Sie eine oder mehrere **[!UICONTROL Abfrage]**-Aktivitäten hinzu, um die für die Erstellung des Berichts nützlichen Daten abzurufen. Die Daten können direkt über eine Abfrage eines Schemas der Datenbank, eine importierte Liste oder einen existierenden Cube abgerufen werden.

   Weitere Informationen finden Sie unter [Zu analysierende Daten abrufen](../../reporting/using/collecting-data-to-analyze.md).

   Diese Daten werden je nach Seitenkonfiguration im Bericht angezeigt oder nicht.

1. Positionieren Sie eine oder mehrere **[!UICONTROL Seite]**-Aktivitäten im Diagramm, um die grafische Darstellung der abgerufenen Daten zu konfigurieren. Sie können Tabellen, Grafiken sowie Eingabefelder einfügen und die Anzeige einer oder mehrerer Seiten oder bestimmter Seitenelemente an Bedingungen knüpfen. Der angezeigte Inhalt ist vollständig konfigurierbar.

   Weitere Informationen finden Sie unter [Statische Elemente](#static-elements).

1. Verwenden Sie die **[!UICONTROL Test]**-Aktivität, um Anzeige- oder Zugriffsbedingungen für bestimmte Daten zu definieren.

   Weitere Informationen finden Sie unter [Bedingungen zur Anzeige von Seiten definieren](../../reporting/using/defining-a-conditional-content.md#conditioning-page-display).

1. Fügen Sie bei Bedarf mithilfe der **[!UICONTROL Script]**-Aktivität benutzerdefinierte Scripts hinzu, beispielsweise um den Namen eines Berichts zu berechnen, die Anzeige der Ergebnisse in einem bestimmten Kontext zu filtern etc.

   Weitere Informationen finden Sie unter [Script-Aktivität](../../reporting/using/advanced-functionalities.md#script-activity).

1. Schließlich haben Sie die Möglichkeit, die Lesbarkeit komplexer Berichte durch das Einfügen einer oder mehrerer **[!UICONTROL Sprung]**-Aktivitäten zu verbessern. Diese ermöglichen den Übergang von einer Aktivität zu einer anderen, ohne die Transition im Bericht zu materialisieren. Die **[!UICONTROL Sprung]**-Aktivität kann auch genutzt werden, um einen anderen Bericht anzuzeigen.

   Weitere Informationen finden Sie unter [Sprung-Aktivität](../../reporting/using/advanced-functionalities.md#jump-activity).

Der Ausführungsmodus eines Berichts entspricht nicht dem eines Workflows. Beispielsweise können nicht mehrere Zweige parallel ausgeführt werden. Ein wie folgt konstruierter Bericht ist daher nicht ausführbar:

![](assets/reporting_graph_sample_ko.png)

Es ist jedoch möglich, mehrere Zweige zu positionieren, wobei nur einer von ihnen ausgeführt wird:

![](assets/reporting_graph_sample_ok.png)

## Seiten erstellen {#creating-a-page}

Der Inhalt wird über die im Diagramm platzierten Aktivitäten konfiguriert. Weitere Informationen finden Sie unter [Gestaltung des Diagramms](#modelizing-the-chart).

Doppelklicken Sie auf das Symbol einer Aktivität, um sie zu konfigurieren.

Der angezeigte Inhalt wird in Aktivitäten vom Typ **Seite** bestimmt.

Ein Bericht kann eine oder mehrere Seiten enthalten. Die Seiten werden mithilfe eines dedizierten Editors erstellt, über den ein Navigationsbaum, Eingabefelder, Auswahlfelder, statische Elemente, Diagramme oder Tabellen eingefügt werden können. Die Anordnung der Elemente erfolgt anhand von Containern. Weitere Informationen finden Sie unter [Elemente anordnen](../../reporting/using/element-layout.md).

Über die Schaltfläche &quot;Auswahldialog&quot; lassen sich verschiedene Komponenten (Radiobutton, Checkbox etc.) in die Seite einfügen.

![](assets/reporting_add_component_in_page.png)

Alternativ können Sie einen Rechtsklick auf den Knoten machen, um eine der verfügbaren Komponenten einzufügen.

![](assets/s_ncs_advuser_report_wizard_09.png)

>[!CAUTION]
>
>Wenn der Bericht für den Export im Excel-Format vorgesehen ist, sollten Sie keine komplexe HTML-Formatierung verwenden. Weitere Informationen finden Sie unter [Berichtexport](../../reporting/using/actions-on-reports.md#exporting-a-report).

Eine **[!UICONTROL Seite]** kann folgende Elemente enthalten:

* **[!UICONTROL Grafiken]** vom Typ Histogramm, Kreis- oder Kurvendiagramm etc.
* **[!UICONTROL Tabellen]** vom Typ Pivot, Gruppierungsliste oder Verteilung.
* **[!UICONTROL Eingabedialoge]** vom Typ Text oder Zahl.
* **[!UICONTROL Auswahldialoge]** vom Typ Dropdown-Liste, Checkbox, Radiobutton, Multiple Choice, Datum oder Matrix.
* **[!UICONTROL Erweiterte Dialoge]** vom Typ Link-Editor, Konstante, Ordnerauswahl.
* **[!UICONTROL Statische Elemente]** vom Typ Wert, Link, HTML, Bild etc.
* **[!UICONTROL Container]** zur Anordnung der Komponenten.

Die Konfiguration einer Seite und ihrer Elemente wird in [diesem Abschnitt](../../web/using/about-web-forms.md) erläutert.

Mithilfe der Symbolleiste können Sie Dialoge hinzufügen, löschen und so anordnen, wie sie auf den Seiten Ihres Berichts angezeigt werden sollen.

![](assets/s_ncs_advuser_report_wizard_08.png)

### Statische Elemente {#static-elements}

Statische Elemente ermöglichen die Anzeige von Informationen, grafischen Elementen oder Scripts im Bericht, mit denen der Benutzer nicht interagiert. Weitere Informationen finden Sie in [diesem Abschnitt](../../web/using/static-elements-in-a-web-form.md#inserting-html-content).

![](assets/s_advuser_report_page_activity_03.png)

### Informationen in einem Bericht filtern {#filtering-information-in-a-report}

Anhand von Eingabe- und Auswahldialogen können die im Bericht angezeigten Informationen gefiltert werden. Weitere Informationen zur Implementierung dieses Filtertyps finden Sie unter [Filteroptionen in Abfragen](../../reporting/using/collecting-data-to-analyze.md#filtering-options-in-the-queries).

Die Erstellung und Konfiguration von Eingabe- und Auswahlfeldern werden in [diesem Abschnitt](../../web/using/about-web-forms.md) beschrieben.

Sie können ein oder mehrere Eingabedialoge in Ihre Berichte integrieren. Dieser Dialogtyp ermöglicht es Ihnen beispielsweise, die angezeigten Informationen nach einem eingegebenen Wert zu filtern.

![](assets/reporting_control_text.png)

Sie können auch eine oder mehrere Auswahldialoge in Ihre Berichte integrieren. Dieser Dialogtyp ermöglicht es Ihnen, die angezeigten Informationen nach einem oder mehreren Werten zu filtern, zum Beispiel:

* über Radiobuttons und Checkboxen:

   ![](assets/reporting_radio_buttons.png)

* über eine Dropdown-Liste:

   ![](assets/reporting_control_list.png)

* über einen Kalender:

   ![](assets/reporting_control_date.png)

Sie können einen oder mehrere erweiterte Dialoge in Ihre Berichte integrieren. Dieser Dialogtyp bietet die Möglichkeit, einen Link oder eine Konstante einzufügen oder einen Ordner auszuwählen.

Im folgenden Beispiel wird der Bericht dahingehend konfiguriert, dass nur die Daten eines bestimmten Ordners des Navigationsbaums angezeigt werden:

![](assets/reporting_control_folder.png)
