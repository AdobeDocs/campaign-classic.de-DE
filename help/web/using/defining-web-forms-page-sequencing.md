---
title: Seitenreihenfolge eines Webformulars definieren
seo-title: Seitenreihenfolge eines Webformulars definieren
description: Seitenreihenfolge eines Webformulars definieren
seo-description: null
page-status-flag: never-activated
uuid: 297fad62-d806-4bd8-9b8c-313c20344ab0
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: web-forms
discoiquuid: 85bf3244-6896-43e7-96b8-84c45c282fec
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c9c9d5f96856ce9e19571bad032d2bf04eaa60bd

---


# Seitenreihenfolge eines Webformulars definieren{#defining-web-forms-page-sequencing}

Ein Formular kann eine oder mehrere Seiten enthalten. Es wird mithilfe eines Diagramms erstellt, in dem Sie die Möglichkeit haben, Seiten und Etappen wie Tests, Skriptausführungen, Speicherung und Sprünge aneinanderzureihen. Der Diagrammerstellungsmodus entspricht dem eines Workflows.

## Die Schaltflächen &quot;Weiter&quot; und &quot;Zurück&quot;{#about-previous-page-and-next-page}

Sie können die Schaltflächen **[!UICONTROL Next]** oder **[!UICONTROL Previous]** Schaltflächen für jede Seite löschen. Wählen Sie dazu die betreffende Seite aus und wählen Sie die Option **[!UICONTROL Disable next page]** oder **[!UICONTROL Disallow returning to the previous page]** .

![](assets/s_ncs_admin_survey_no_next_page.png)

Sie können diese Schaltflächen durch Links ersetzen. Siehe [Einfügen von HTML-Inhalten](../../web/using/static-elements-in-a-web-form.md#inserting-html-content).

## Sprung einfügen {#inserting-a-jump}

The **[!UICONTROL Jump]** object gives access to another page or another form when the user clicks **[!UICONTROL Next]**.

Folgende Zielorte sind möglich:

* Eine andere Seite des Formulars. Wählen Sie dazu die gewünschte Seite aus **[!UICONTROL Internal activity]** und geben Sie sie wie folgt an:

   ![](assets/s_ncs_admin_jump_param1.png)

* Ein anderes Formular. To do this, select the **[!UICONTROL Explicit]** option and specify the destination form.

   ![](assets/s_ncs_admin_jump_param2.png)

* Der Zielort kann in einer Variablen gespeichert sein. Wählen Sie ihn in diesem Fall aus der Dropdown-Liste wie unten gezeigt aus.

   ![](assets/s_ncs_admin_jump_param3.png)

* The **[!UICONTROL Comment]** tab lets you enter information that will be visible by the operator when they click the object in the diagram.

   ![](assets/s_ncs_admin_survey_jump_comment.png)

## Example: accessing another form according to a parameter of the URL {#example--accessing-another-form-according-to-a-parameter-of-the-url}

Im folgenden Beispiel soll ein Webformular konfiguriert werden, das nach der Validierung abhängig vom Parameter der URL ein anderes Formular anzeigt. Gehen Sie dazu folgendermaßen vor:

1. Insert a jump at the end of a form: this replaces the **[!UICONTROL End]** box.

   ![](assets/s_ncs_admin_survey_jump_sample1.png)

1. Fügen Sie in den Formulareigenschaften einen Parameter (**next**) hinzu, der in einer lokalen Variablen (**next**) gespeichert ist. Lokale Variablen werden unter [Speichern von Daten in einer lokalen Variablen](../../web/using/web-forms-answers.md#storing-data-in-a-local-variable)beschrieben.

   ![](assets/s_ncs_admin_survey_jump_sample2.png)

1. Edit the **[!UICONTROL Jump]** object, select the **[!UICONTROL Stored in a variable]** option and select the **next** variable from the drop-down box.

   ![](assets/s_ncs_admin_survey_jump_sample3.png)

1. Die Versand-URL muss den internen Namen des Zielformulars enthalten, z. B.:

   ```
   https://[myserver]/webForm/APP62?&next=APP22
   ```

   When the user clicks the **[!UICONTROL Approve]** button, form **APP22** is displayed.

## Link zu einer anderen Seite des Formulars einfügen {#inserting-a-link-to-another-page-of-the-form}

Sie können Links zu anderen Seiten des Formulars einfügen. Fügen Sie dazu der Seite ein statisches **[!UICONTROL Link]** Typelement hinzu. Weitere Informationen finden Sie unter [Einfügen eines Links](../../web/using/static-elements-in-a-web-form.md#inserting-a-link).

## Bedingte Anzeige von Seiten {#conditional-page-display}

### Auf Grundlage der Antworten anzeigen {#display-based-on-responses}

Mit dem **[!UICONTROL Test]** Feld können Sie die Reihenfolge der Seiten in einem Formular festlegen. Damit können Sie je nach Testergebnis verschiedene Verzweigungslinien definieren. Auf diese Weise können Sie je nach den Antworten der Benutzer unterschiedliche Seiten anzeigen.

Sie können beispielsweise eine andere Seite für Kunden anzeigen, die bereits online bestellt haben, und eine andere für diejenigen, die mehr als zehn Bestellungen aufgegeben haben. Fügen Sie dazu auf der ersten Seite des Formulars ein **[!UICONTROL Number]** Eingabefeld ein, in dem der Benutzer angeben kann, wie viele Bestellungen er aufgegeben hat.

![](assets/s_ncs_admin_survey_test_ex0.png)

Diese Informationen können entweder in einem Datenbankfeld oder einer lokalen Variablen gespeichert werden.

>[!NOTE]
>
>Die Speichermodi sind in den [Antwortspeicherfeldern](../../web/using/web-forms-answers.md#response-storage-fields)ausführlich beschrieben.

In unserem Beispiel soll eine Variable verwendet werden:

![](assets/s_ncs_admin_survey_test_ex1.png)

Fügen Sie im Diagramm des Formulars eine Test-Komponente ein, um die Bedingungen zu definieren. Für jede Bedingung wird am Ausgang der Test-Komponente eine neue Abzweigung hinzugefügt.

![](assets/s_ncs_admin_survey_test_ex2.png)

Wählen Sie die **[!UICONTROL Activate the default branching]** Option aus, um einen Übergang hinzuzufügen, wenn keine der Bedingungen wahr ist. Diese Option ist unnötig, wenn jeder mögliche Fall von den festgelegten Bedingungen abgedeckt wird.

Definieren Sie dann die Seitenreihenfolge, wenn eine der Bedingungen wahr ist, zum Beispiel:

![](assets/s_ncs_admin_survey_test_ex3.png)

### Auf Basis von Parametern anzeigen {#display-based-on-parameters}

Sie können die Seitensequenzierung auch entsprechend den Initialisierungsparametern des Webformulars oder den in der Datenbank gespeicherten Werten personalisieren. Siehe Parameter für die [Formular-URL](../../web/using/defining-web-forms-properties.md#form-url-parameters).

## Skripts hinzufügen {#adding-scripts}

Mit dem Objekt **[!UICONTROL Script]** können Sie ein JavaScript-Element direkt einfügen, z. B. um den Wert eines Felds zu ändern, um Daten aus der Datenbank abzurufen oder um eine Adobe Campaign-API aufzurufen.

## Endseite anpassen {#personalizing-the-end-page}

Sie müssen eine Endseite am Ende des Diagramms platzieren. Die Endseite wird angezeigt, wenn der Benutzer auf die **[!UICONTROL Approve]** Schaltfläche im Webformular klickt.

To personalize this page, double-click **[!UICONTROL End]** and enter the content of the page in the central editor.

![](assets/s_ncs_admin_survey_end_page_edit.png)

* Sie können vorhandene HTML-Inhalte kopieren und einfügen. Klicken Sie dazu auf **[!UICONTROL Display source code]** und fügen Sie den HTML-Code ein.
* Sie können eine externe URL verwenden. Wählen Sie dazu die entsprechende Option aus und geben Sie die URL der anzuzeigenden Seite ein.

