---
title: Ressourcen und Grundlagen des Content-Manager-Moduls
seo-title: Ressourcen und Grundlagen des Content-Manager-Moduls
description: Ressourcen und Grundlagen des Content-Manager-Moduls
seo-description: null
page-status-flag: never-activated
uuid: 3560e392-129a-471d-a211-05481cdda224
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: content-management
discoiquuid: b22b3abb-6fe5-4f4d-93fc-0d00d426edb6
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7dbc876fae0bde78e3088ee1ab986cd09e9bcc38

---


# Ressourcen und Grundlagen des Content-Manager-Moduls{#content-manager-resources-and-principles}

Für jeden Inhalt muss eine Publikationsvorlage mit entsprechenden Umwandlungsvorlagen erstellt werden.

Die Struktur der Inhalte wird in XML-Dokumenten festgeschrieben. Die eigentliche Erstellung des Inhalts erfolgt über Eingabeschnittstellen in der Adobe-Campaign-Clientkonsole oder über einen Web-Browser. Inhalte können außerdem automatisch durch Abruf von XML-Streams oder durch Aggregation von Daten aus einer Datenbank eingefügt werden.

Es ist die Kombination aus einem XML-Dokument mit XSL-Stylesheets oder JavaScript-Templates, die die automatische Umwandlung des Inhalts in die verschiedenen Formate (HTML, Text) der Publikationsvorlage ermöglicht.

![](assets/d_ncs_content_process.png)

Für die Konfiguration des Inhalts werden die folgenden Ressourcen benötigt:

* Datenschemata: Beschreibung der XML-Inhaltsstruktur. For more on this, refer to [Data schemas](../../delivery/using/data-schemas.md).
* Formulare zur Dateneingabe: Aufbau von Dateneingabebildschirmen. For more on this, refer to [Input forms](../../delivery/using/input-forms.md).
* Bilder: Bilder, die in Dateneingabeformularen verwendet werden. For more on this, refer to [Image management](../../delivery/using/formatting.md#image-management).
* Stylesheets: Formatieren von Ausgabedokumenten mit XSLT-Sprache. For more on this, refer to [Formatting](../../delivery/using/formatting.md).
* JavaScript-Vorlagen: Formatieren von Ausgabedokumenten mit JavaScript-Sprache. For more on this, refer to [Publication templates](../../delivery/using/publication-templates.md).
* JavaScript-Codes: JavaScript-Codes für die Datenaggregation. For more on this, refer to [Aggregator](../../delivery/using/publication-templates.md#aggregator).
* Veröffentlichungsvorlagen: Definition von Vorlagen für Veröffentlichungen. For more on this, refer to [Publication templates](../../delivery/using/publication-templates.md).
* Inhalt: Inhaltsinstanzen, die erstellt und veröffentlicht werden sollen. Weitere Informationen finden Sie unter [Verwenden einer Inhaltsvorlage](../../delivery/using/using-a-content-template.md).
