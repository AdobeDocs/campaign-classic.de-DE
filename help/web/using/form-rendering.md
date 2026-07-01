---
product: campaign
title: Formular-Rendering
description: Formular-Rendering
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
feature: Web Forms
exl-id: 723a6c47-5323-4914-a014-58be493852cc
TQID: https://experienceleague.adobe.com/zLf1lFV9vVIHcEbfO5UrFo92epuVlfMUWrl64SqNfCQ
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: c5474392-5419-4296-9e41-f6f4ce4f6e9bid: a4671286-a59f-47e3-b97b-90627a1977d5
topic_v2: id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
subfeature_v2: id: f391046b-0cf3-4e76-bd3b-97fe06654506id: ed29abcd-b6a8-4d4b-ab8b-b7e746973281id: d7be2b01-dc9c-40f7-aace-a151707504ed
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 1055
ht-degree: 100%

---

# Formular-Rendering{#form-rendering}



## Vorlage zum Formular-Rendering auswählen {#selecting-the-form-rendering-template}

Mit den Formulareinstellungen können Sie die Vorlage auswählen, die zum Generieren der Seiten verwendet wird. Um darauf zuzugreifen, klicken Sie auf die Schaltfläche **[!UICONTROL Eigenschaften]** in der Symbolleiste mit den Formulardetails und wählen Sie die Registerkarte **[!UICONTROL Rendering]** aus. Standardmäßig stehen verschiedene Vorlagen (Stylesheets) zur Verfügung.

![](assets/s_ncs_admin_survey_rendering_select.png)

Im unteren Bereich des Editors können Sie sich das Rendering der ausgewählten Vorlage ansehen.

Mit der Zoom-Funktion können Sie die ausgewählte Vorlage bearbeiten.

![](assets/s_ncs_admin_survey_render_edit.png)

Sie können diese Vorlagen ändern oder überschreiben. Wählen Sie dazu den Link **[!UICONTROL Seitenlayout...]** aus und passen Sie die Einstellungen an.

![](assets/s_ncs_admin_survey_render_edit_param.png)

Sie haben folgende Möglichkeiten:

* Das als Logo verwendete Bild und dessen Größe ändern
* Den Pfad für den Zugriff auf das Vorschaubild für Benutzer festlegen, die diese Rendering-Vorlage auswählen.

Mit dem Tab **[!UICONTROL Headers/Footers]** können Sie die Informationen ändern, die in der Kopf- und Fußzeile jeder Formularseite steht, die auf dieser Vorlage basiert.

![](assets/s_ncs_admin_survey_render_edit_header.png)

Jede Zeile des Bereichs **[!UICONTROL Seitenkopf]** und **[!UICONTROL Seitenfuß]** entspricht einer Zeile auf der HTML-Seite. Wählen Sie **[!UICONTROL Hinzufügen]**, um eine neue Zeile zu erstellen.

Wählen Sie eine vorhandene Zeile und danach die Schaltfläche **[!UICONTROL Detail]** aus, um sie zu bearbeiten.

![](assets/s_ncs_admin_survey_render_edit_header_detail.png)

Verwenden Sie die jeweiligen Tabs, um den Inhalt der Zeile zu ändern, Rahmen hinzuzufügen und die Schriftart-Attribute anzupassen. Bestätigen Sie diese Änderungen mit **[!UICONTROL OK]**.

Mit den Feldern **[!UICONTROL Position]** können Sie die Position der Elemente im Seiten-Header und -Footer definieren.

![](assets/s_ncs_admin_survey_render_edit_header_position.png)

>[!NOTE]
>
>Rendering-Vorlagen befinden sich im Knoten **[!UICONTROL Administration > Konfiguration > Formular-Rendering]**.\
>Weitere Informationen hierzu finden Sie unter [Formular-Rendering anpassen](#customizing-form-rendering).

## Formular-Rendering anpassen {#customizing-form-rendering}

### Layout von Elementen ändern {#changing-the-layout-of-elements}

Sie können das Stylesheet für jedes Element des Formulars überschreiben (Eingabefelder, Bilder, Radiobuttons etc.).

Verwenden Sie dazu den Tab **[!UICONTROL Erweitert]**.

![](assets/s_ncs_admin_survey_advanced_tab.png)

Damit können Sie die folgenden Eigenschaften definieren:

* **[!UICONTROL Titelposition]**: siehe [Die Position von Titeln definieren](defining-web-forms-layout.md#defining-the-position-of-labels),
* **[!UICONTROL Titelformat]**: mit oder ohne Zeilenumbruch,
* **[!UICONTROL Zellenanzahl]** : siehe [Die Felder auf der Seite positionieren](defining-web-forms-layout.md#positioning-the-fields-on-the-page),
* **[!UICONTROL Horizontale Ausrichtung]** (links, rechts, zentriert) und **[!UICONTROL vertikale Ausrichtung]** (hoch, niedrig, Mitte),
* **[!UICONTROL Breite]** des Bereichs: Diese kann als Prozentsatz oder in em, Punkten oder Pixeln (Standardwert) ausgedrückt werden,
* Maximale **[!UICONTROL Länge]**: Maximale Anzahl erlaubter Zeichen (für Steuerelemente vom Typ Text, Zahl und Passwort),
* **[!UICONTROL Zeilen]**: Anzahl der Zeilen für einen Bereich vom Typ **[!UICONTROL Mehrzeiliger Text]**,
* **[!UICONTROL Inline-Stil]**: ermöglicht es Ihnen, das CSS-Stylesheet mit zusätzlichen Einstellungen zu überschreiben. Diese werden durch **;**-Zeichen getrennt, wie im folgenden Beispiel gezeigt:

  ![](assets/s_ncs_admin_survey_advanced_tab_inline.png)

### Header und Footer definieren {#defining-headers-and-footers}

Die Felder sind in einer Baumstruktur angeordnet, deren Stamm denselben Namen hat wie die Seite. Wählen Sie den Stamm aus, um den Namen zu ändern.

Der Titel des Fensters muss im Fenster mit den Formulareigenschaften in der Registerkarte **[!UICONTROL Seite]** eingegeben werden. Sie können dem Header oder Footer auch einen festen Inhalt hinzufügen (diese Informationen werden auf jeder Seite angezeigt). Dieser Inhalt wird wie unten gezeigt in den jeweiligen Bereich des Tabs **[!UICONTROL Texte]** eingegeben:

![](assets/s_ncs_admin_survey_titles_config.png)

### Elemente zum HTML-Header hinzufügen {#adding-elements-to-html-header}

Sie können zusätzliche Elemente zum HTML-Header einer Formularseite hinzufügen. Geben Sie dazu die Elemente auf der entsprechenden Seite im Tab **[!UICONTROL Header]** ein.

Damit können Sie beispielsweise ein Symbol referenzieren, das in der Symbolleiste der Seite angezeigt werden soll.

![](assets/webform_header_page_tab.png)

## Kontrolleinstellungen definieren {#defining-control-settings}

Wenn der Benutzer das Formular ausfüllt, wird in bestimmten Feldern je nach Format oder Konfiguration automatisch eine Überprüfung durchgeführt. Auf diese Weise können Sie bestimmte Felder obligatorisch machen (siehe [Pflichtfelder definieren](#defining-mandatory-fields)) oder das Format der eingegebenen Daten überprüfen (siehe [Datenformat überprüfen](#checking-data-format)). Prüfungen werden während der Seitengenehmigung durchgeführt (durch Klicken auf einen Link oder eine Schaltfläche, der/die eine ausgehende Transition ermöglicht).

### Pflichtfelder definieren {#defining-mandatory-fields}

Wenn Sie bestimmte Felder als Pflichtfelder festlegen möchten, wählen Sie bei der Erstellung des Felds diese Option aus.

![](assets/s_ncs_admin_survey_required_field.png)

Sollte ein Benutzer diese Seite validieren, ohne das Feld ausgefüllt zu haben, wird ihm die folgende Meldung angezeigt:

![](assets/s_ncs_admin_survey_required_default_msg.png)

Sie können diese Mitteilung anpassen, indem Sie den Link **[!UICONTROL Nachricht personalisieren, die bei geschlossenem Formular angezeigt wird...]** auswählen.

![](assets/s_ncs_admin_survey_required_custom_msg.png)

Sollte ein Benutzer diese Seite validieren, ohne das Feld ausgefüllt zu haben, wird ihm die folgende Meldung angezeigt:

![](assets/s_ncs_admin_survey_required_custom_msg2.png)

### Datenformat überprüfen {#checking-data-format}

Für Formularprüfungen, bei denen die Werte in einem vorhandenen Datenbankfeld gespeichert sind, werden die Regeln für das Speicherfeld angewendet.

Für Formularprüfungen, bei denen die Werte in einer Variablen gespeichert sind, hängen die Validierungsregeln vom Format der Variablen ab.

Sie können beispielsweise die Prüfung einer **[!UICONTROL Zahl]** einrichten, um wie unten gezeigt die Kundennummer zu speichern:

![](assets/s_ncs_admin_survey_choose_format.png)

Der Benutzer muss in diesem Fall eine ganze Zahl im Formularfeld eingeben.

## Bedingte Anzeige von Feldern definieren {#defining-fields-conditional-display}

Sie können konfigurieren, dass die Felder auf der Seite basierend auf den benutzerseitig ausgewählten Werten angezeigt werden. Dies kann auf ein Feld oder eine Gruppe von Feldern angewendet werden (wenn sie in einem Container gruppiert sind).

Sie können für jedes Element der Seite die Anzeigebedingungen im Bereich **[!UICONTROL Sichtbarkeit]** definieren.

![](assets/s_ncs_admin_survey_condition_edit.png)

Bedingungen können für die Werte in Datenbankfeldern oder Variablen festgelegt werden.

Im Feldauswahl-Fenster können Sie aus folgenden Daten auswählen:

![](assets/s_ncs_admin_survey_condition_select.png)

* Der Hauptbaum enthält die Parameter des Formularkontexts. Die Standardparameter sind Kennung (entspricht der verschlüsselten Kennung der Empfängerin bzw. des Empfängers), Sprache und Herkunft.

  Weiterführende Informationen hierzu finden Sie auf dieser [Seite](defining-web-forms-properties.md#form-url-parameters).

* Im Unterbaum **[!UICONTROL Empfänger]** befinden sich die Eingabefelder, die in das Formular eingefügt wurden und in der Datenbank gespeichert sind.

  Weitere Informationen finden Sie unter [Speichern von Daten in der Datenbank](web-forms-answers.md#storing-data-in-the-database).

* Die Unterstruktur **[!UICONTROL Variablen]** enthält die verfügbaren Variablen für dieses Formular. Weitere Informationen finden Sie unter [Daten in einer lokalen Variablen speichern](web-forms-answers.md#storing-data-in-a-local-variable).

Weitere Informationen hierzu finden Sie in diesem Anwendungsbeispiel: [Je nach den ausgewählten Werten unterschiedliche Optionen anzeigen](use-cases-web-forms.md#displaying-different-options-depending-on-the-selected-values).

Sie können auch mit dem Objekt **[!UICONTROL Test]** eine Bedingung für die Anzeige von Formularseiten festlegen. Weiterführende Informationen hierzu finden Sie auf [dieser Seite](defining-web-forms-page-sequencing.md#conditional-page-display).

## Elemente aus einem vorhandenen Formular importieren {#importing-elements-from-an-existing-form}

Es ist möglich, Felder oder Container aus anderen Web-Formularen zu importieren. Damit können Sie eine Bibliothek aus wiederverwendbaren Bausteinen erstellen, die in Formulare eingefügt werden können, z. B. Adressbaustein, Newsletter-Abonnement-Bereich usw.

Gehen Sie wie folgt vor, um ein Element in ein Formular zu importieren:

1. Bearbeiten Sie die Seite, in die Sie ein oder mehrere Elemente einfügen möchten und wählen Sie dann in der Symbolleiste **[!UICONTROL Existierenden Baustein importieren]** aus.

   ![](assets/s_ncs_admin_survey_import_block.png)

1. Wählen Sie das Webformular aus, das die zu importierenden Felder enthält, und wählen Sie die Container und Felder aus, die importiert werden sollen.

   ![](assets/s_ncs_admin_survey_import_block_selection.png)

   >[!NOTE]
   >
   >Über das Symbol **[!UICONTROL Link bearbeiten]** rechts neben dem Quell-Formularnamen können Sie das ausgewählte Webformular anzeigen.

1. Wählen Sie **[!UICONTROL OK]** aus, um das Einfügen des Elements zu bestätigen.

   ![](assets/s_ncs_admin_survey_import_block_rendering.png)
