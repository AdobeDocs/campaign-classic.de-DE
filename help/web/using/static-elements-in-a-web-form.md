---
product: campaign
title: Statische Elemente in einem Webformular
description: Statische Elemente in einem Webformular
feature: Web Forms
exl-id: 364d90af-4b18-4104-8b6a-be80cfde3b0b
source-git-commit: b6f1556cf49492cefaf61c29a058584b0ccee16a
workflow-type: ht
source-wordcount: '1074'
ht-degree: 100%

---

# Statische Elemente in einem Webformular{#static-elements-in-a-web-form}

![](../../assets/common.svg)

Sie können Elemente, mit denen der Benutzer keine Interaktion hat, in die Seiten des Formulars einfügen; dies sind statische Elemente wie Bilder, HTML-Inhalte, eine horizontale Leiste oder ein Hypertext-Link. Diese Elemente werden über die erste Schaltfläche in der Symbolleiste erstellt, indem Sie **[!UICONTROL Statische Elemente]** auswählen.

![](assets/s_ncs_admin_survey_add_static_element.png)

Folgende Feldtypen sind verfügbar:

* Wert auf der Basis der zuvor eingegebenen Antworten (im Kontext des Formulars) oder der Datenbank.
* Hypertext-Link, HTML, horizontaler Balken. Siehe [HTML-Inhalt einfügen](#inserting-html-content).
* Bild, das in der Ressourcenbibliothek oder auf einem für Benutzer zugänglichen Server gespeichert ist. Siehe [Bilder einfügen](#inserting-images).
* Script, das Client- und/oder Server-seitig ausgeführt wird. Es muss in JavaScript verfasst und mit den gängigen Browsern kompatibel sein, um die korrekte Ausführung beim Client zu gewährleisten.

   >[!NOTE]
   >
   >Auf der Serverseite kann das Script die in der [Campaign JSAPI-Dokumentation](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=de) definierten Funktionen verwenden.

## HTML-Inhalt einfügen {#inserting-html-content}

Sie können in eine Formularseite HTML-Inhalte einfügen, wie z. B. Hypertext-Links, Bilder, formatierte Absätze, Videos usw.

Mit dem HTML-Editor können Sie den Inhalt eingeben, der in die Formularseite eingefügt werden soll. Um den Editor zu öffnen, klicken Sie auf **[!UICONTROL Statische Elemente]** > **[!UICONTROL HTML]**.

Sie können Inhalte direkt eingeben und formatieren oder das Fenster mit dem Quellcode öffnen, um externen Code einzukopieren. Wählen Sie dazu das erste Symbol in der Symbolleiste aus, um zum Quellcode-Modus zu wechseln.

![](assets/s_ncs_admin_survey_html_editor.png)

Um ein Datenbankfeld einzufügen, verwenden Sie die Personalisierungs-Schaltfläche.

![](assets/webapp_perso_button_in_html.png)

>[!NOTE]
>
>Die im HTML-Editor eingegebenen Strings werden nur übersetzt, wenn sie im Unter-Tab **[!UICONTROL Texte]** definiert sind. Ansonsten werden sie nicht erfasst. Weitere Informationen finden Sie unter [Webformular übersetzen](translating-a-web-form.md).

### Links einfügen {#inserting-a-link}

Füllen Sie im Bearbeitungsfenster die Felder wie im folgenden Beispiel gezeigt aus:

Um einen Hypertext-Link hinzuzufügen, gehen Sie zu **[!UICONTROL Statische Elemente]** > **[!UICONTROL Link]**.

![](assets/s_ncs_admin_survey_add_link.png)

* Im **[!UICONTROL Titel]** wird der Inhalt des Hypertext-Links so dargestellt, wie er auf der Formularseite erscheinen wird.
* Die **[!UICONTROL URL]** ist die gewünschte Adresse, z. B.: [https://www.adobe.com](https://www.adobe.com) für eine Website oder [info@adobe.com](mailto:info@adobe.com), um eine Nachricht zu senden.
* Im Feld **[!UICONTROL Fenster]** können Sie im Fall einer Website einen Anzeigemodus für den Link auswählen. Sie können den Link in einem neuen Fenster, dem aktuellen Fenster oder einem anderen Fenster öffnen.
* Sie können einen ToolTip wie unten gezeigt hinzufügen:

   ![](assets/s_ncs_admin_survey_send_an_email.png)

* Der Link kann als Schaltfläche oder Bild dargestellt werden. Wählen Sie dazu im Feld **[!UICONTROL Typ]** den Typ der Anzeige aus.

### Link-Typen {#types-of-links}

Standardmäßig sind Links mit einer Aktion vom Typ &quot;URL&quot; verknüpft, sodass eine URL-Zieladresse im URL-Feld eingegeben werden kann.

![](assets/s_ncs_admin_survey_link_url.png)

Sie können auch andere Aktionen für den Link definieren, sodass der Benutzer durch Anklicken des Links folgende Aktionen ausführen kann:

* Die Seite aktualisieren

   Wählen Sie dazu im Dropdown-Fenster des Felds **[!UICONTROL Aktion]** die Option **[!UICONTROL Seite aktualisieren]** aus.

   ![](assets/s_ncs_admin_survey_link_refresh.png)

* Die nächste/vorherige Seite anzeigen

   Wählen Sie dazu im Dropdown-Fenster des Felds **[!UICONTROL Aktion]** die Option **[!UICONTROL Nächste Seite]** oder **[!UICONTROL Vorherige Seite]** aus.

   ![](assets/s_ncs_admin_survey_link_next.png)

   Sie können die Schaltflächen **[!UICONTROL Weiter]** und/oder **[!UICONTROL Zurück]** verbergen, wenn diese durch einen Link ersetzt werden sollen. Weiterführende Informationen dazu finden Sie auf dieser [Seite](defining-web-forms-page-sequencing.md).

   Der Link ersetzt die standardmäßig verwendete Schaltfläche **[!UICONTROL Weiter]**.

   ![](assets/s_ncs_admin_survey_link_next_ex.png)

* Eine weitere Seite anzeigen

   Mit der Option **[!UICONTROL Transition aktivieren]** können Sie eine bestimmte Seite anzeigen, die mit der im Feld **[!UICONTROL Transition]** ausgewählten ausgehenden Transition verknüpft ist.

   ![](assets/s_ncs_admin_survey_link_viral.png)

   Standardmäßig hat eine Seite nur eine einzige ausgehende Transition. Um neue Transitionen zu erstellen, wählen Sie wie unten gezeigt die Seite und danach im Bereich **[!UICONTROL Ausgehende Transitionen]** die Schaltfläche **[!UICONTROL Hinzufügen]** aus:

   ![](assets/s_ncs_admin_survey_add_transition.png)

   Im Diagramm sieht dies so aus:

   ![](assets/s_ncs_admin_survey_add_transition_graph.png)

   >[!NOTE]
   >
   >Weitere Informationen zur Seitenreihenfolge in einem Webformular finden Sie unter [Seitenreihenfolge eines Webformulars definieren](defining-web-forms-page-sequencing.md).

### HTML-Inhalt personalisieren {#personalizing-html-content}

Sie können den HTML-Inhalt einer Formularseite mit auf einer vorherigen Seite erfassten Daten personalisieren. So können Sie beispielsweise ein Webformular für eine Kfz-Versicherung erstellen, auf deren erster Seite Sie die Möglichkeit bieten, Kontaktinformationen und die Automarke einzugeben.

![](assets/s_ncs_admin_survey_tag_ctx_1.png)

Mit Personalisierungsfeldern können Sie den Benutzernamen und die ausgewählte Marke nochmals auf der nächsten Seite einfügen. Die zu verwendende Syntax hängt vom Speichermodus der Informationen ab. Weitere Informationen hierzu finden Sie unter [Erfasste Informationen verwenden](web-forms-answers.md#using-collected-information).

>[!NOTE]
>
>Aus Sicherheitsgründen wird der in die Formel **`<%=`** eingegebene Wert durch Maskierungszeichen ersetzt.

In unserem Beispiel werden der Vor- und Nachname des Empfängers in einem Feld der Datenbank gespeichert, während das Automodell in einer Variablen gespeichert wird. Die Syntax der personalisierten Nachricht auf Seite 2 sieht folgendermaßen aus:

![](assets/webapp_perso_vars_include.png)

```
<P>Welcome <%= ctx.recipient.@firstName %> <%= ctx.recipient.@lastName %>,</P>
<P>To start your customized study, please select your car <%=ctx.vars.marque%> and its year of purchase.</P>
```

Das Ergebnis sieht folgendermaßen aus:

![](assets/s_ncs_admin_survey_tag_ctx_2.png)

### Textvariablen verwenden {#using-text-variables}

Im Tab **[!UICONTROL Text]** können Sie Variablenfelder erstellen, die in HTML zwischen den Zeichen &lt;%= und %> mit der folgenden Syntax verwendet werden können: **$(IDENTIFIER)**.

Verwenden Sie diese Methode zur einfachen Lokalisierung Ihrer Strings. Siehe [Webformular übersetzen](translating-a-web-form.md).

Sie können beispielsweise das Feld **Kontakt** erstellen. Damit haben Sie die Möglichkeit, den String „Datum des letzten Kontakts:“ im HTML-Inhalt anzuzeigen. Gehen Sie dazu wie folgt vor:

1. Wählen Sie den Tab **[!UICONTROL Text]** des HTML-Texts aus.
1. Wählen Sie das Symbol **[!UICONTROL Hinzufügen]** aus.
1. Geben Sie in der Spalte **[!UICONTROL Kennung]** den Namen der Variablen ein.
1. Geben Sie in der Spalte **[!UICONTROL Text]** den Standardwert ein.

   ![](assets/s_ncs_admin_survey_html_text.png)

1. Geben Sie im HTML-Inhalt diese Textvariable mithilfe der Syntax **&lt;%= $(Contact) %>** ein.

   ![](assets/s_ncs_admin_survey_html_content.png)

   >[!CAUTION]
   >
   >Wenn Sie diese Zeichen in den HTML-Editor eingeben, werden die Felder **&lt;** und **** durch deren Maskierungszeichen ersetzt. In diesem Fall müssen Sie den Quellcode korrigieren, indem Sie auf das Symbol **[!UICONTROL Quellcode anzeigen]** des HTML-Texteditors klicken.

1. Öffnen Sie den Titel **[!UICONTROL Vorschau]** des Formulars, um den in HTML eingegebenen Wert anzuzeigen:

   ![](assets/s_ncs_admin_survey_html_content_preview.png)

Mit diesem Verfahren können Sie den Text von Web-Formularen nur einmal festlegen und Übersetzungen mit dem integrierten Übersetzungs-Tool verwalten. Weitere Informationen finden Sie unter [Web-Formular übersetzen](translating-a-web-form.md).

## Bilder einfügen {#inserting-images}

Um in Formulare Bilder einzufügen, müssen diese auf einem Server gespeichert werden, auf den von außen zugegriffen werden kann.

Wählen Sie das Menü **[!UICONTROL Statische Elemente]** > **[!UICONTROL Bild]** aus. 

Wählen Sie die Quelle des Bildes aus, das eingefügt werden soll: Es kann in einer öffentlichen Ressourcen-Bibliothek oder auf einem externen, von außen zugreifbaren Server gespeichert sein.

![](assets/s_ncs_admin_survey_add_img.png)

Wenn das Bild aus einer Bibliothek stammt, wählen Sie es in der Dropdown-Liste des Felds aus. Wenn es in einer externen Datei gespeichert ist, geben Sie den Zugriffspfad ein. Der Titel wird angezeigt, wenn Sie den Cursor über das Bild bewegen (entspricht einem ALT-Feld in HTML) oder wenn das Bild nicht dargestellt wird.

Das Bild kann im mittleren Bereich des Editors angezeigt werden.
