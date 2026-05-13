---
product: campaign
title: Ressourcen und Grundlagen des Content-Manager-Moduls
description: Ressourcen und Grundlagen des Content-Manager-Moduls
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
feature: Templates
role: User, Developer
exl-id: ade3f1d1-2235-4148-9b6f-721d3f521a15
TQID: https://experienceleague.adobe.com/xWBOrnm4v7N3XOVvOcPNqngz0cDvvT39tI3xJVKdFZg
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: ce44533e-8ec8-4e11-a9e9-78b0fe561832
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 247
ht-degree: 79%

---

# Ressourcen und Grundlagen des Content-Manager-Moduls{#content-manager-resources-and-principles}


Für jeden Inhalt muss eine Veröffentlichungsvorlage mit entsprechenden Umwandlungsvorlagen erstellt werden.

Ein Inhaltsbaustein ist zur Datenspeicherung in einem XML-Dokument strukturiert. Eine Bearbeitungsschnittstelle wird verwendet, um den Inhalt über die Adobe Campaign-Client-Konsole oder einen Webbrowser einzugeben. Der Inhalt kann auch automatisch über die Erfassung von XML-Datenflüssen oder aggregierten Daten in einer Datenbank eingegeben werden.

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
