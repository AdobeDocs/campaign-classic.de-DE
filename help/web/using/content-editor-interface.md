---
title: Benutzeroberfläche des Inhaltseditors
seo-title: Benutzeroberfläche des Inhaltseditors
description: Benutzeroberfläche des Inhaltseditors
seo-description: null
page-status-flag: never-activated
uuid: b108ea74-ae2c-4e47-bee8-12070927ba89
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: editing-html-content
dc-title: </strong> and
discoiquuid: 20c64d31-c2ed-4bc9-9f0e-46f2e0c08c88
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 707352334144df86ae82aa51d595ae6bc751d1f2

---


# Benutzeroberfläche des Inhaltseditors{#content-editor-interface}

## Bearbeitungsfenster {#editing-window}

Das Bearbeitungsfenster des DCE besteht aus drei Bereichen. Darin können Sie den Inhalt ansehen, ändern und dessen Status überprüfen.

![](assets/dce_decoupe_window_nb.png)

1. The **top** section is a display area for messages to the user. These messages indicate the status of the Web application status or the delivery being created as well as warnings and error messages related to the content. Weitere Informationen finden Sie unter [HTML-Inhaltsstatus](../../web/using/content-editing-best-practices.md#html-content-statuses).
1. The section to the **left** of the window is the area for editing content. From this area, the user can directly interact with the content using the pop-up toolbar: insert a link into an image, change the font, delete a field, etc. For more on this refer to [Editing forms](../../web/using/editing-content.md#editing-forms).
1. The section to the **right** of the window is the control panel area. This area groups the different options for the editor, particularly those related to configuring the page heading and general options for a block: add a border, link a database field with an input zone, access Web page properties, etc. Weitere Informationen finden Sie in den Abschnitten [Globale Optionen](#global-options) und [Bearbeiten von Inhalten](../../web/using/editing-content.md) .

## Globale Optionen {#global-options}

Über den rechten oberen Bereich des Editors können Sie auf die globalen Optionen für den aktuell erstellten Inhalt zugreifen.

![](assets/dce_global_options.png)

Dort finden Sie vier Symbole:

![](assets/dce_icons_sidebar.png)

* The **Display/Hide blocks** icon lets you display blue frames around the content blocks (corresponding to the `<div>` HTML tag).

* Über das Symbol **Anderen Inhalt wählen** können Sie neuen Inhalt aus einer (bereits erstellten oder nativen) Vorlage laden.

   ![](assets/dce_popup_templatechoice.png)

   >[!CAUTION]
   >
   >Bei der Auswahl eines neuen Inhalts wird der aktuelle Inhalt automatisch ersetzt.

* Mit dem Symbol &quot;Als Vorlage **** speichern&quot;können Sie den aktuellen Inhalt als Vorlage speichern. Sie müssen die Bezeichnung und den internen Namen für die Vorlage eingeben. Vorlagen werden im **[!UICONTROL Resources > Templates > Content templates]** Knoten gespeichert.

   ![](assets/dce_popup_savetemplate.png)

   Nach dem Speichern ist die Vorlage verfügbar und kann für neuen Inhalt wieder ausgewählt werden.

   ![](assets/dce_create_fromtemplate.png)

* Mit dem Symbol **Seiteneigenschaften** können Sie Informationen zum Inhalt am oberen Rand der HTML-Seite auswählen.

   ![](assets/dce_popup_headerhtml.png)

   >[!NOTE]
   >
   >This information corresponds to the **`<title>`** and **`<meta>`** HTML tags on the page.
   >
   >Die Schlüsselwörter müssen durch Kommata getrennt sein.

## Optionen für Bausteine {#block-options}

Im rechten Bereich des Editors befinden sich die wichtigsten Optionen zum Bearbeiten des Inhalts. Diese Optionen werden nur angezeigt, wenn ein Baustein ausgewählt wird. Die Art der Optionen hängt vom ausgewählten Baustein ab.

![](assets/dce_right_section.png)

Sie haben folgende Möglichkeiten:

* Legen Sie die Anzeige für einen oder mehrere Blöcke fest, siehe [Definieren einer Sichtbarkeitsbedingung](../../web/using/editing-content.md#defining-a-visibility-condition),
* Definieren Sie die Ränder und Rahmen, siehe [Hinzufügen von Rahmen und Hintergrund](../../web/using/editing-content.md#adding-a-border-and-background),
* Definieren Sie Bildattribute (Größe, Beschriftung), siehe [Bearbeiten von Bildeigenschaften](../../web/using/editing-content.md#editing-image-properties),
* Verknüpfen der Datenbank mit einem Formularelement (Eingabezone, Kontrollkästchen), siehe [Ändern der Dateneigenschaften für ein Formular](../../web/using/editing-content.md#changing-the-data-properties-for-a-form),
* Machen Sie einen Teil eines Formulars obligatorisch, siehe [Ändern der Dateneigenschaften für ein Formular](../../web/using/editing-content.md#changing-the-data-properties-for-a-form),
* Definieren Sie eine Aktion für eine Schaltfläche, siehe [Hinzufügen einer Aktion zu einer Schaltfläche](../../web/using/editing-content.md#adding-an-action-to-a-button).

## Symbolleiste für die Inhaltsbearbeitung {#content-toolbar}

Diese Symbolleiste ist ein **Pop-up-Element** in der Benutzeroberfläche des DCE, das je nach ausgewähltem Baustein unterschiedliche Funktionen aufweist.

>[!CAUTION]
>
>Mit gewissen Funktionen der Symbolleiste können Sie den HTML-Inhalt formatieren. Wenn die betroffene Seite jedoch ein CSS-Stylesheet enthält, können sich die **Anweisungen** des Stylesheets als **vorrangig** erweisen.

