---
product: campaign
title: Benutzeroberfläche des Inhaltseditors
description: Benutzeroberfläche des Inhaltseditors
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
feature: Web Apps, Web Forms, Landing Pages, Email Design
exl-id: cb76f3dc-7f3a-49de-89cb-c106865ecb17
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 56%

---

# Benutzeroberfläche des Inhaltseditors{#content-editor-interface}



## Bearbeitungsfenster {#editing-window}

Das DCE-Bearbeitungsfenster ist in drei verschiedene Abschnitte unterteilt. Sie ermöglichen es Ihnen, den Status des Inhalts anzuzeigen, zu ändern und zu überprüfen.

![](assets/dce_decoupe_window_nb.png)

1. Der **Oben**-Bereich ist ein Anzeigebereich für Meldungen an den Benutzer. Diese Meldungen geben den Status der Web-Anwendung für den erstellten Versand sowie Warnungen und Fehlermeldungen im Zusammenhang mit dem Inhalt an. Weitere Informationen hierzu finden Sie unter [HTML-Inhaltsstatus](content-editing-best-practices.md#html-content-statuses).
1. Der Bereich auf **linken** des Fensters ist der Bereich für die Bearbeitung von Inhalten. Von diesem Bereich aus kann der Benutzer mithilfe der Popup-Symbolleiste direkt mit dem Inhalt interagieren: Einfügen eines Links in ein Bild, Ändern der Schriftart, Löschen eines Felds usw. Weitere Informationen hierzu finden Sie unter [ von Formularen](editing-content.md#editing-forms).
1. Der Bereich **rechts** Fensters ist der Bereich „Systemsteuerung“. In diesem Bereich werden die verschiedenen Optionen für den Editor gruppiert, insbesondere jene, die mit der Konfiguration der Seitenüberschrift und allgemeiner Optionen für einen Block zusammenhängen: Hinzufügen eines Rahmens, Verknüpfen eines Datenbankfelds mit einem Eingabefeld, Zugreifen auf Web-Seiteneigenschaften usw. Weitere Informationen hierzu finden Sie in den Abschnitten [Globale Optionen](#global-options) und [Bearbeiten von ](editing-content.md)&quot;.

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

* Mit **Symbol „Als** speichern“ können Sie den aktuellen Inhalt als Vorlage speichern. Sie müssen den Titel und den internen Namen für die Vorlage eingeben. Vorlagen werden im Knoten **[!UICONTROL Ressourcen > Vorlagen > Inhaltsvorlagen]** gespeichert.

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

Im Bereich rechts im Editor werden die wichtigsten Optionen gruppiert, mit denen Sie auf den Inhalt reagieren können. Um diese Optionen anzuzeigen, müssen Sie einen Block auswählen: Die Art dieser Optionen hängt vom ausgewählten Block ab.

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
