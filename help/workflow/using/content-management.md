---
title: Content Management
seo-title: Content Management
description: Content Management
seo-description: null
page-status-flag: never-activated
uuid: 8d1bf84b-96e5-4d3d-9d77-42d2027a74db
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: 13b72aa1-de40-4548-835b-97e765e04e95
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# Content Management{#content-management}

Mithilfe der Aktivität **Content Management** lassen sich Inhalte erstellen und bearbeiten sowie Inhaltsdateien erzeugen. Die Inhalte können dann im Ramen einer Versandaktivität genutzt werden.

>[!CAUTION]
>
>Das Content Management ist ein optionales Modul von Adobe Campaign. Bitte prüfen Sie Ihren Lizenzvertrag.

Die Konfiguration der Aktivität gliedert sich in drei Schritte:

* **Inhalt auswählen**: Der Inhalt kann zuvor erstellt worden sein oder in der Aktivität erstellt werden.
* **Inhalt aktualisieren**: Die Aufgabe kann den Betreff des Inhalts ändern oder den gesamten XML-Inhalt importieren.
* **Auszuführende Aktion**: Der Inhalt kann gespeichert oder erzeugt werden.

   ![](assets/content_mgmt_edit.png)

   Konfiguration und Verwendung des Content Managements in Adobe Campaign werden in diesem [Abschnitt](../../delivery/using/about-content-management.md) detailliert beschrieben.

1. **Content**

   * **[!UICONTROL Specified in the transition]**

      Mit dieser Option können Sie den Inhalt verwenden, der im Übergang angegeben wurde, d. h. das Ereignis, das die Inhaltsverwaltung aktiviert, muss eine **[!UICONTROL contentId]** Variable enthalten. Diese Variable kann von einer vorherigen Inhaltsverwaltung oder einem beliebigen Skript festgelegt worden sein.

   * **[!UICONTROL Explicit]**

      Mit dieser Option können Sie einen bereits erstellten Inhalt über das **[!UICONTROL Content]** Feld auswählen. Dieses Feld ist nur sichtbar, wenn die **[!UICONTROL Explicit]** Option ausgewählt ist.

      ![](assets/content_mgmt_explicit.png)

   * **[!UICONTROL Calculated by a script]**

      Die Inhaltskennung wird durch ein Skript berechnet. Im **[!UICONTROL Script]** Feld können Sie eine JavaScript-Vorlage definieren, mit der der Bezeichner (Primärschlüssel) des Inhalts ausgewertet wird. Dieses Feld ist nur sichtbar, wenn die **[!UICONTROL Calculated by a script]** Option ausgewählt ist.

      ![](assets/content_mgmt_script.png)

   * **[!UICONTROL New, created from a publication template]**

      Erstellt einen neuen Inhalt aus einer Veröffentlichungsvorlage. Dieser neue Inhalt wird in der im **[!UICONTROL String]** Feld angegebenen Datei gespeichert. Das **[!UICONTROL Template]** Feld gibt die Veröffentlichungsvorlage an, die zum Erstellen des Inhalts verwendet werden soll.

      ![](assets/content_mgmt_new.png)

1. **Bereich Inhalt aktualisieren**

   * **[!UICONTROL Subject]**

      Hier kann der Betreff der dem Inhalt entsprechenden Versandaktion überschrieben werden.

   * **[!UICONTROL Access to data from an XML feed]**

      Mit dieser Option können Sie Inhalte aus einem XML-Dokument erstellen, das über ein XSL-Stylesheet heruntergeladen wurde. Wenn diese Option aktiviert ist, gibt das **[!UICONTROL URL]** Feld die URL des XML-Inhalts zum Herunterladen an. Mit der **[!UICONTROL XSL stylesheet]** können Sie das Stylesheet angeben, das zum Transformieren des heruntergeladenen XML-Dokuments verwendet werden soll. Diese Eigenschaft ist optional.

      ![](assets/content_mgmt_xmlcontent.png)

1. **Auszuführende Aktion**

   * **[!UICONTROL Save]**

      Der erstellte oder geänderte Inhalt wird gespeichert.

      In diesem Fall wird die ausgehende Transition einmal aktiviert. In der Variable **[!UICONTROL contentId]** wird die Kennung des Inhalts gespeichert.

   * **[!UICONTROL Generate]**

      Der Inhalt wird gespeichert und die Ausgabedateien für alle Umwandlungsvorlagen mit dem Publikationstyp &#39;Datei&#39; werden erzeugt.

      ![](assets/content_mgmt_generate.png)

      In diesem Fall wird die ausgehende Transition für jede erzeugte Datei aktiviert. In der Variable **[!UICONTROL contentId]** wird die Kennung des Inhalts und in der Variable **[!UICONTROL filename]** der Name der Datei gespeichert.

## Eingabeparameter {#input-parameters}

* contentId

Bezeichner des Inhalts, der verwendet werden soll, wenn die **[!UICONTROL Specified in the transition]** Option aktiviert ist.

## Ausgabeparameter {#output-parameters}

* contentId

   Kennung des Inhalts.

* filename

   Full name of the generated file if the selected action is **[!UICONTROL Generate]**.

## Beispiele {#examples}

Beispiele werden in diesem [Abschnitt](../../delivery/using/automating-via-workflows.md#examples) bereitgestellt.
