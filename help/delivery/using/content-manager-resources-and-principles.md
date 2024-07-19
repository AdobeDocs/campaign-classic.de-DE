---
product: campaign
title: Ressourcen und Grundlagen des Content-Manager-Moduls
description: Ressourcen und Grundlagen des Content-Manager-Moduls
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
feature: Templates
role: User, Developer, Data Engineer
exl-id: ade3f1d1-2235-4148-9b6f-721d3f521a15
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 100%

---

# Ressourcen und Grundlagen des Content-Manager-Moduls{#content-manager-resources-and-principles}


Für jeden Inhalt muss eine Veröffentlichungsvorlage mit entsprechenden Umwandlungsvorlagen erstellt werden.

Die Struktur der Inhalte wird in XML-Dokumenten festgeschrieben. Die eigentliche Erstellung des Inhalts erfolgt über Eingabeschnittstellen in der Adobe-Campaign-Clientkonsole oder über einen Web-Browser. Inhalte können außerdem automatisch durch Abruf von XML-Streams oder durch Aggregation von Daten aus einer Datenbank eingefügt werden.

Es ist die Kombination aus einem XML-Dokument mit XSL-Stylesheets oder JavaScript-Templates, die die automatische Umwandlung des Inhalts in die verschiedenen Formate (HTML, Text) der Veröffentlichungsvorlage ermöglicht.

![](assets/d_ncs_content_process.png)

Für die Konfiguration des Inhalts werden die folgenden Ressourcen benötigt:

* Datenschemata: Beschreibung der XML-Inhaltsstruktur. Weitere Informationen dazu finden Sie im Abschnitt [Datenschemata](data-schemas.md).
* Formulare: Erstellen von Bildschirmen zur Dateneingabe. Weitere Informationen hierzu finden Sie im Abschnitt [Formulare](input-forms.md).
* Bilder: Bilder, die in Formularen verwendet werden. Weitere Informationen hierzu finden Sie im Abschnitt [Hintergrundbild und Symbole](formatting.md#image-management).
* Stylesheets: Formatieren von Ausgabedokumenten mit XSLT-Sprache. Weitere Informationen hierzu finden Sie im Abschnitt [Formatierung](formatting.md).
* JavaScript-Vorlagen: Formatieren von Ausgabedokumenten mit JavaScript-Sprache. Weitere Informationen hierzu finden Sie im Abschnitt [Veröffentlichungsvorlagen](publication-templates.md).
* JavaScript-Codes: JavaScript-Codes für Datenaggregation. Weitere Informationen hierzu finden Sie im Abschnitt [Aggregator](publication-templates.md#aggregator).
* Veröffentlichungsvorlagen: Definieren von Veröffentlichungsvorlagen. Weitere Informationen hierzu finden Sie im Abschnitt [Veröffentlichungsvorlagen](publication-templates.md).
* Inhalt: Inhaltsinstanzen, die erstellt und veröffentlicht werden sollen. Weitere Informationen hierzu finden Sie unter [Verwendung von Inhaltsvorlagen](using-a-content-template.md).
