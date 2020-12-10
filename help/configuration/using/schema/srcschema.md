---
solution: Campaign Classic
product: campaign
title: Elemente und Attribute
description: Elemente und Attribute
audience: configuration
content-type: reference
topic-tags: schema-reference
translation-type: tm+mt
source-git-commit: c366326f6a439dabaa42fdd799ec2e55c180a929
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 2%

---


# `<srcschema>` Element {#srcschema--element}

## Inhaltsmodell {#content-model-14}

srcSchema:==(attribute | createdBy | data | element | Auflistung | help | Schnittstelle | Methoden | modifyBy)

## Attribute {#attributes-14}

created (datetime), createdBy-id (long), desc (string), entitySchema (string), extendedSchema (string), img (string), implements (string), label (string), labelSingular (string), lastModified (datetime), library (boolean), mappingType (string), modifyBy-id (long), name (string), Namensraum,  (Zeichenfolge), useRecycleBin (boolean), Ansicht (boolean), xtkschema (Zeichenfolge)

## Eltern {#parents-14}

Ohne

## Kinder {#children-14}

* `<attribute>`
* `<createdby>`
* `<data>`
* `<element>`
* `<enumeration>`
* `<help>`
* `<interface>`
* `<methods>`
* `<modifiedby>`

## Beschreibung {#description-14}

`<srcschema>` ist das Stammelement eines Schemas. Es ist der Eingabepunkt für die Definition des Schemas.

## Verwendung und Kontext der Verwendung von {#use-and-context-of-use-9}

Die Darstellung des Schemas ist unter [Info zum Schema](../../../configuration/using/about-schema-reference.md) und [Schema](../../../configuration/using/schema-structure.md) verfügbar.

## Attributbeschreibung {#attribute-description-14}

* **created (dattime)**: Dieses Attribut enthält Informationen zum Datum und zur Uhrzeit der Erstellung des Schemas. Es enthält das Formular &quot;Date Time&quot;. Die angezeigten Werte werden vom Server übernommen. Die Uhrzeit wird im UTC-Format angezeigt.
* **createdBy-id (long)**: ist die Kennung des Operators, der das Schema erstellt hat.
* **desc (Zeichenfolge)**: Beschreibung des Schemas
* **entitySchema (Zeichenfolge)**: Basis-Schema, auf dem Syntax und Genehmigung basieren (zum Adobe Campaign standardmäßig): xtk:srcSchema). Wenn Sie das aktuelle Schema speichern, genehmigt Adobe Campaign seine Grammatik mit dem im @xtkschema-Attribut deklarierten Schema.
* **extendedSchema (Zeichenfolge)**: erhält den Namen des vordefinierten Schemas, auf dem die aktuelle Schema-Erweiterung basiert. Das Formular lautet &quot;Namensraum:Name&quot;.
* **img (Zeichenfolge)**: mit dem Schema verknüpft ist (kann im Assistenten zum Erstellen von Schemas definiert werden).
* **label (Zeichenfolge)**: Beschriftung des Schemas.
* **labelSingular (Zeichenfolge)**: Beschriftung (Singular) für die Anzeige in der Schnittstelle.
* **lastModified (datetime)**: Dieses Attribut enthält Informationen zum Datum und zur Uhrzeit der letzten Änderung. Es enthält das Formular &quot;Date Time&quot;. Die angezeigten Werte werden vom Server übernommen. Die Uhrzeit wird im UTC-Format angezeigt.
* **library (boolean)**: Verwendung des Schemas als Bibliothek und nicht als Entität. Dieses Schema kann daher von anderen Schemas mithilfe der Attribute &quot;@ref&quot;und &quot;@template&quot;referenziert werden.
* **mappingType (Zeichenfolge)**:

   * &quot;sql&quot;: Datenbankzuordnung
   * &quot;textFile&quot;: Textdateizuordnung
   * &quot;xmlFile&quot;: Textdateizuordnung im XML-Format
   * &quot;inaryFile&quot;: Binäre Dateizuordnung

* **modifyBy-id (long)**: entspricht der Kennung des Operators, der das Schema geändert hat.
* **name (Zeichenfolge)**: eindeutiger Name des Schemas.
* **namensraum (Zeichenfolge)**: namensraum des Schemas (Standard: nms, xtk, nl). Beim Erstellen eines neuen Schemas für ein Projekt wird empfohlen, einen eigenen Namensraum zu verwenden.
* **useRecycleBin (boolean)**: Aktiviert die Funktion &quot;Papierkorb&quot;in der Anwendung. Gelöschte Datensätze werden vor der endgültigen Löschung in den Papierkorb gelegt. Diese Funktion ist nur im Versand-Modus verfügbar.
* **ansicht (boolean)**: Wenn es aktiviert ist (@Ansicht=&quot;true&quot;), wird das Schema als Ansicht verwendet. Der Assistent zum Aktualisieren der Datenbankstruktur berücksichtigt das Schema nicht. Diese Option wird hauptsächlich für den Verweis auf externe Tabellen verwendet.
* **xtkschema (Zeichenfolge)**: Name des Schemas, das die Schema-Grammatik definiert (standardmäßig xtk:srcSchema).

## Beispiele {#examples-11}

`<srcschema>` -Element des Schemas &quot;nms:Versand&quot;

```
<srcSchema desc="Defines all the settings of a delivery (or delivery template)."  
           entitySchema="xtk:srcSchema" img="nms:campaign.png" implements="xtk:persist" 
           label="Diffusions" labelSingular="Diffusion" md5="DCD2164CD0276B1DCA6E1C9E2A75EC04"
           name="delivery" namespace="nms" useRecycleBin="true" xtkschema="xtk:srcSchema">
```
