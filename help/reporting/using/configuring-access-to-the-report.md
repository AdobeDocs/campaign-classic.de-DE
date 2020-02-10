---
title: Berichtanzeige konfigurieren
seo-title: Berichtanzeige konfigurieren
description: Berichtanzeige konfigurieren
seo-description: null
page-status-flag: never-activated
uuid: d32d9805-f84f-457f-b37b-a8278642336a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: creating-new-reports
discoiquuid: dd50ca25-8fa2-48fa-84cc-a63e476701a0
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Berichtanzeige konfigurieren{#configuring-access-to-the-report}

## Anzeigekontext von Berichten {#report-display-context}

Definieren Sie den Anzeigekontext des Berichts in der Adobe Campaign-Plattform mithilfe der **[!UICONTROL Display]** Registerkarte. Der Zugriff auf einen Bericht hängt von der Art der Auswahl, den Anzeigebedingungen und den Zugriffsberechtigungen ab.

### Auswahltyp {#selection-type}

Der Zugriff auf den Bericht kann auf einen bestimmten Kontext oder Angebotsbereich beschränkt werden, z. B. auf eine Bereitstellung, einen Empfänger, eine Auswahl von Empfängern usw. Dieser Zugriff wird im **[!UICONTROL Selection type]** Abschnitt der **[!UICONTROL Display]** Registerkarte konfiguriert.

![](assets/s_ncs_advuser_report_visibility_4.png)

* **[!UICONTROL Single selection]** : auf den Bericht kann nur zugegriffen werden, wenn eine bestimmte Entität ausgewählt ist.
* **[!UICONTROL Multiple selection]** : auf den Bericht zugreifen, wenn mehrere Entitäten ausgewählt sind.
* **[!UICONTROL Global]** : Der Zugriff auf den Bericht erfolgt über die Liste der verfügbaren Berichte im Universum &quot;Berichte&quot;.

### Anzeigereihenfolge {#display-sequence}

The **[!UICONTROL Sequence]** field lets you enter a numeric value that specifies the display sequence of the report in the list.

Die Berichte werden standardmäßig anhand dieses Feldes nach Relevanz geordnet. Der Bericht mit dem höchsten Wert gilt als am relevantesten.

Sie können eine beliebige Skala verwenden, zum Beispiel von 1 bis 10, von 0 bis 100 oder von -10 bis 10.

### Anzeigebedingungen {#display-conditions}

Die Anzeige des Berichts kann auch mittels einer Abfrage an Bedingungen geknüpft werden.

![](assets/s_ncs_advuser_report_visibility_5.png)

Im unten stehenden Beispiel ist die Anzeigebedingung, dass der Hauptkanal der Kampagne E-Mail ist.

![](assets/s_ncs_advuser_report_visibility_6.png)

Wenn es sich beim Hauptkanal der Kampagne um Briefpost handelt, wird der Bericht nicht in den Berichten der Kampagne verfügbar sein.

### Zugriffsberechtigung {#access-authorization}

Es besteht die Möglichkeit, den Bericht mit anderen Benutzern zu teilen.

Um den Bericht barrierefrei zu machen, wählen Sie die **[!UICONTROL Report shared with other operators]** Option aus. Wenn diese Option nicht ausgewählt ist, kann nur der Operator, der den Bericht erstellt hat, auf den Bericht zugreifen.

Der Bericht kann auch mit bestimmten Benutzern oder Benutzergruppen geteilt werden, indem sie im Bereich der Berechtigungen hinzugefügt werden.

![](assets/s_ncs_advuser_report_visibility_8.png)

### Filteroptionen definieren {#defining-the-filtering-options}

The **[!UICONTROL Reports]** universe displays all available reports in the platform and for which the connected operator has an access right.

Sie werden standardmäßig nach Relevanz sortiert, es stehen jedoch andere Filtertypen zur Verfügung: nach Alphabet, Alter etc.

Sie können die Anzeige auch nach den Berichtkategorien filtern:

![](assets/report_ovv_select_type.png)

To define the category of a report, select it via the **[!UICONTROL Display]** tab, as shown below:

![](assets/report_select_category.png)

Sie können eine neue Kategorie erfassen, die dann in die Liste der verfügbaren Kategorien aufgenommen wird. Die entsprechende Auflistung wird automatisch aktualisiert.

## Verknüpfung zu einem Bericht erstellen {#creating-a-link-to-a-report-}

Sie können einen Bericht über einen spezifischen Knoten im Navigationsbaum wie eine Liste, einen Empfänger, einen Versand o. Ä. zugänglich machen. Erstellen Sie hierzu einfach eine Verknüpfung zum betreffenden Bericht und geben Sie die Entität an, in der dieser verfügbar gemacht werden soll.

Als Beispiel wird im Folgenden eine Verknüpfung eines Berichts zu einer Empfängerliste erstellt.

1. Klicken Sie auf **[!UICONTROL New]** und wählen Sie **[!UICONTROL Create a link to an existing report]** im Assistenten zur Berichterstellung aus.

   ![](assets/s_ncs_advuser_report_wizard_link_01.png)

1. Wählen Sie mithilfe der Dropdown-Liste den Bericht aus, für den Sie eine Verknüpfung erstellen möchten. Im vorliegenden Beispiel wird der Bericht **Kunden/Interessenten pro Land** gewählt.

   ![](assets/s_ncs_advuser_report_wizard_link_02.png)

1. Geben Sie den Titel an und wählen Sie das Schema aus. Im Beispiel wird die Tabelle der Empfängerlisten gewählt.

   ![](assets/s_ncs_advuser_report_wizard_link_03.png)

   Dies bedeutet, dass der Bericht von jeder Empfängerliste aus zugänglich sein wird und die Statistiken basierend auf den in der markierten Liste enthaltenen Empfängern berechnet werden.

1. Speichern Sie den Bericht und öffnen Sie ihn.
1. Geben Sie den Verbindungsschlüssel an. Im Beispiel handelt es sich um den Fremdschlüssel der &#39;Ordner&#39;-Relation.

   ![](assets/s_ncs_advuser_report_wizard_link_04.png)

1. Publizieren Sie Ihren Bericht.
1. Go to one of your recipient lists and click the **[!UICONTROL Reports]** link: the report you have just created is accessible.

   ![](assets/s_ncs_advuser_report_wizard_link_05.png)

## Berichtvorschau {#preview-of-the-report}

Before publishing your report, make sure it is displayed correctly in the **[!UICONTROL Preview]** tab.

![](assets/s_ncs_advuser_report_preview_01.png)

To display the preview of the report, select the **[!UICONTROL Global]** or the **[!UICONTROL Selection]** option.

Diese beiden Optionen werden basierend auf den Anzeigeeinstellungen des Berichts ausgewählt. Ist die Anzeigeeinstellung **[!UICONTROL Global]** so müssen Sie die **[!UICONTROL Global]** Vorschauoption auswählen. Wenn die Anzeigeeinstellungen **[!UICONTROL Single selection]** oder **[!UICONTROL Multiple selection]** die **[!UICONTROL Selection]** Vorschauoption aktiviert sind, muss sie ausgewählt werden.

Weitere Informationen finden Sie unter [Berichtsanzeigekontext](#report-display-context).

Es stehen zudem Parameter zur Verfügung, die eine Kontrolle der Fehler ermöglicht. Der Parameter **_uuid** ist Teil der URL des Berichts. Sie können ihm die Parameter **&amp;_preview** oder **&amp;_debug** hinzufügen.

Die Funktionsweise dieser Parameter wird im Abschnitt zur Definition von **Webformular-Eigenschaften** des Kapitels [Webformulare](../../web/using/about-web-forms.md) beschrieben.

## Berichtpublikation {#publishing-the-report}

Das Veröffentlichen des Berichts ist obligatorisch, um ihn für andere Operatoren freizugeben und in der Liste der verfügbaren Berichte anzuzeigen (siehe auch [Berichtsanzeigekontext](#report-display-context)). Dieser Vorgang muss bei jeder Änderung des Berichts erneut durchgeführt werden.

1. Open the publishing wizard by clicking **[!UICONTROL Publish]** in the toolbar.

   ![](assets/s_ncs_advuser_report_publish_01.png)

1. Klicken Sie **[!UICONTROL Start]** zum Veröffentlichen auf .

   ![](assets/s_ncs_advuser_report_publish_02.png)

1. Click the **[!UICONTROL Enlarge]** icon to open the report in a web browser.

