---
product: campaign
title: Benutzeroberfläche des Inhaltseditors
description: Benutzeroberfläche des Inhaltseditors
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
feature: Web Apps, Web Forms, Landing Pages, Email Design
exl-id: cb76f3dc-7f3a-49de-89cb-c106865ecb17
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 100%

---

# Benutzeroberfläche des Inhaltseditors{#content-editor-interface}



## Bearbeitungsfenster {#editing-window}

Das Bearbeitungsfenster des DCE besteht aus drei Bereichen. Darin können Sie den Inhalt ansehen, ändern und dessen Status überprüfen.

![](assets/dce_decoupe_window_nb.png)

1. Im **oberen** Bereich werden Nachrichten für den Benutzer angezeigt. Hier sind Hinweise zum Status der Webanwendung oder zum gerade erstellten Versand sowie Warnhinweise und Fehlernachrichten in Verbindung mit dem Inhalt zu sehen. Weitere Informationen hierzu finden Sie unter [HTML-Inhaltsstatus](content-editing-best-practices.md#html-content-statuses).
1. Der **linke** Bereich des Fensters ermöglicht die Bearbeitung des Inhalts. Hier kann der Benutzer direkt über die sich öffnende Symbolleiste z. B. einen Link in ein Bild einfügen, die Schriftart ändern und ein Feld löschen. Weitere Informationen hierzu finden Sie unter [Formulare bearbeiten](editing-content.md#editing-forms).
1. Im **rechten** Bereich des Fensters befindet sich das Steuerfeld. In diesem Bereich werden die Optionen des Editors gruppiert dargestellt, vor allem jene zur Konfiguration der Seitenüberschrift und allgemeine Optionen für Bausteine. Hier können Sie beispielsweise einen Rand hinzufügen, ein Datenbankfeld mit einem Eingabefeld verknüpfen und auf die Eigenschaften einer Web-Seite zugreifen. Weitere Informationen hierzu finden Sie in den Abschnitten [Globale Optionen](#global-options) und [Inhalt bearbeiten](editing-content.md).

## Globale Optionen {#global-options}

Über den rechten oberen Bereich des Editors können Sie auf die globalen Optionen für den aktuell erstellten Inhalt zugreifen.

![](assets/dce_global_options.png)

Dort finden Sie vier Symbole:

![](assets/dce_icons_sidebar.png)

* Mit dem Symbol **Bausteine anzeigen/ausblenden** können Sie Inhaltsbausteine mit blauen Rahmen versehen (entspricht dem HTML-Tag `<div>`).

* Über das Symbol **Anderen Inhalt wählen** können Sie neuen Inhalt aus einer (bereits erstellten oder nativen) Vorlage laden.

  ![](assets/dce_popup_templatechoice.png)

  >[!CAUTION]
  >
  >Bei der Auswahl eines neuen Inhalts wird der aktuelle Inhalt automatisch ersetzt.

* Mit dem Symbol **Als Vorlage speichern** können Sie den aktuellen Inhalt als Vorlage speichern. Geben Sie den Titel und den internen Namen der Vorlage ein. Vorlagen werden im Knoten **[!UICONTROL Ressourcen > Vorlagen > Inhaltsvorlagen]** gespeichert.

  ![](assets/dce_popup_savetemplate.png)

  Nach dem Speichern ist die Vorlage verfügbar und kann für neuen Inhalt wieder ausgewählt werden.

  ![](assets/dce_create_fromtemplate.png)

* Mit dem Symbol **Seiteneigenschaften** können Sie Informationen zum Inhalt am oberen Rand der HTML-Seite auswählen.

  ![](assets/dce_popup_headerhtml.png)

  >[!NOTE]
  >
  >Diese Informationen entsprechen den HTML-Tags **`<title>`** und **`<meta>`** auf der Seite.
  >
  >Die Schlüsselwörter müssen durch Kommata getrennt sein.

## Optionen für Bausteine {#block-options}

Im rechten Bereich des Editors befinden sich die wichtigsten Optionen zum Bearbeiten des Inhalts. Diese Optionen werden nur angezeigt, wenn ein Baustein ausgewählt wird. Die Art der Optionen hängt vom ausgewählten Baustein ab.

![](assets/dce_right_section.png)

Sie haben folgende Möglichkeiten:

* Anzeige für einen oder mehrere Blöcke festlegen, siehe [Sichtbarkeitsbedingung definieren](editing-content.md#defining-a-visibility-condition),
* Ränder und Rahmen angeben, siehe [Rahmen und Hintergründe hinzufügen ](editing-content.md#adding-a-border-and-background),
* Bildattribute (Größe, Beschriftung) festlegen, siehe [Bildeigenschaften bearbeiten](editing-content.md#editing-image-properties),
* Datenbank mit einem Formularelement (Eingabefeld, Checkbox) verknüpfen, siehe [Dateneigenschaften für ein Formular ändern](editing-content.md#changing-the-data-properties-for-a-form),
* Einen Teil eines Formulars obligatorisch machen, siehe [Dateneigenschaften für ein Formular ändern](editing-content.md#changing-the-data-properties-for-a-form),
* Eine Aktion für eine Schaltfläche hinzufügen , siehe [Eine Aktion zu einer Schaltfläche hinzufügen](editing-content.md#adding-an-action-to-a-button).

## Symbolleiste für die Inhaltsbearbeitung {#content-toolbar}

Diese Symbolleiste ist ein **Pop-up-Element** in der Benutzeroberfläche des DCE, das je nach ausgewähltem Baustein unterschiedliche Funktionen aufweist.

>[!CAUTION]
>
>Gewisse Funktionen der Schaltfläche betreffen die Formatierung des HTML-Inhalts. Wenn die betroffene Seite jedoch ein CSS-Stylesheet enthält, können sich die **Anweisungen** des Stylesheets als **vorrangig** erweisen.
