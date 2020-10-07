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
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '540'
ht-degree: 100%

---


# Benutzeroberfläche des Inhaltseditors{#content-editor-interface}

## Bearbeitungsfenster {#editing-window}

Das Bearbeitungsfenster des DCE besteht aus drei Bereichen. Darin können Sie den Inhalt ansehen, ändern und dessen Status überprüfen.

![](assets/dce_decoupe_window_nb.png)

1. Im **oberen** Bereich werden Nachrichten für den Benutzer angezeigt. Hier sind Hinweise zum Status der Webanwendung oder zum gerade erstellten Versand sowie Warnhinweise und Fehlernachrichten in Verbindung mit dem Inhalt zu sehen. Weitere Informationen hierzu finden Sie unter [HTML-Inhaltsstatus](../../web/using/content-editing-best-practices.md#html-content-statuses).
1. Der **linke** Bereich des Fensters ermöglicht die Bearbeitung des Inhalts. Hier kann der Benutzer direkt über die sich öffnende Symbolleiste z. B. einen Link in ein Bild einfügen, die Schriftart ändern und ein Feld löschen. Weitere Informationen hierzu finden Sie unter [Formulare bearbeiten](../../web/using/editing-content.md#editing-forms).
1. Im **rechten** Bereich des Fensters befindet sich das Steuerfeld. In diesem Bereich werden die Optionen des Editors gruppiert dargestellt, vor allem jene zur Konfiguration der Seitenüberschrift und allgemeine Optionen für Bausteine. Hier können Sie beispielsweise einen Rand hinzufügen, ein Datenbankfeld mit einem Eingabefeld verknüpfen und auf die Eigenschaften einer Web-Seite zugreifen. Weitere Informationen hierzu finden Sie in den Abschnitten [Globale Optionen](#global-options) und [Inhalt bearbeiten](../../web/using/editing-content.md).

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

* Mit dem Symbol **Als Vorlage speichern** können Sie den aktuellen Inhalt als Vorlage speichern. Geben Sie dazu den Titel und den internen Namen der Vorlage ein. Vorlagen werden im Knoten **[!UICONTROL Ressourcen > Vorlagen > Inhaltsvorlagen]** gespeichert.

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

* Anzeige für einen oder mehrere Blöcke festlegen, siehe [Sichtbarkeitsbedingung definieren](../../web/using/editing-content.md#defining-a-visibility-condition),
* Ränder und Rahmen angeben, siehe [Rahmen und Hintergründe hinzufügen ](../../web/using/editing-content.md#adding-a-border-and-background),
* Bildattribute (Größe, Beschriftung) festlegen, siehe [Bildeigenschaften bearbeiten](../../web/using/editing-content.md#editing-image-properties),
* Datenbank mit einem Formularelement (Eingabefeld, Checkbox) verknüpfen, siehe [Dateneigenschaften für ein Formular ändern](../../web/using/editing-content.md#changing-the-data-properties-for-a-form),
* Einen Teil eines Formulars obligatorisch machen, siehe [Dateneigenschaften für ein Formular ändern](../../web/using/editing-content.md#changing-the-data-properties-for-a-form),
* Eine Aktion für eine Schaltfläche hinzufügen , siehe [Eine Aktion zu einer Schaltfläche hinzufügen](../../web/using/editing-content.md#adding-an-action-to-a-button).

## Symbolleiste für die Inhaltsbearbeitung {#content-toolbar}

Diese Symbolleiste ist ein **Pop-up-Element** in der Benutzeroberfläche des DCE, das je nach ausgewähltem Baustein unterschiedliche Funktionen aufweist.

>[!CAUTION]
>
>Mit gewissen Funktionen der Symbolleiste können Sie den HTML-Inhalt formatieren. Wenn die betroffene Seite jedoch ein CSS-Stylesheet enthält, können sich die **Anweisungen** des Stylesheets als **vorrangig** erweisen.

