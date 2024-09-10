---
product: campaign
title: Elemente und Attribute - Schemaelement
description: Elemente und Attribute
feature: Schema Extension
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: bc4329b4-d272-4d32-bdaa-290cb9912af4
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 1%

---

# Schemaelement {#srcschema--element}

![](../../../assets/v7-only.svg)

## Inhaltsmodell {#content-model-14}

srcSchema:==(attribute | createdBy | data | element | enumeration | help | Benutzeroberfläche | methods | modifiedBy)

## Attribute {#attributes-14}

created (datetime), createdBy-id (long), desc (string), entitySchema (string), extendedSchema (string), img (string), implements (string), label (string), labelSingular (string), lastModified (datetime), library (boolean), mappingType (string), modifiedBy-id (long), name (string), (Zeichenfolge), useRecycleBin (boolean), view (boolean), xtkschema (string)

## Eltern {#parents-14}

Kein(e)

## Untergeordnetes Element {#children-14}

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

Die `<srcschema>` ist das Stammelement eines Schemas. Dies ist der Eingabepunkt für die Definition des Schemas.

## Verwendung und Verwendungskontext {#use-and-context-of-use-9}

Die Schemadarstellung ist in [Über die Schemareferenz](../../../configuration/using/about-schema-reference.md) und in [Schemastruktur](../../../configuration/using/schema-structure.md) verfügbar.

## Attributbeschreibung {#attribute-description-14}

* **created (datetime)**: Dieses Attribut enthält Informationen zum Datum und zur Uhrzeit der Schemaerstellung. Es enthält das Formular &quot;Datum/Uhrzeit&quot;. Die angezeigten Werte werden vom Server übernommen. Die Uhrzeit wird im UTC-Format angezeigt.
* **createdBy-id (long)**: ist die Kennung des Operators, der das Schema erstellt hat.
* **desc (string)**: Schemabeschreibung
* **entitySchema (string)**: Basisschema, auf dem Syntax und Genehmigung basieren (standardmäßig für Adobe Campaign: xtk:srcSchema). Wenn Sie das aktuelle Schema speichern, validiert Adobe Campaign seine Grammatik mit dem im Attribut @xtkschema deklarierten Schema.
* **extendedSchema (string)**: empfängt den Namen des nativen Schemas, auf dem die aktuelle Schemaerweiterung basiert. Das Formular lautet &quot;namespace:name&quot;.
* **img (string)**: Symbol, das mit dem Schema verknüpft ist (kann im Assistenten zur Schemaerstellung definiert werden).
* **label (string)**: Schemakennung.
* **labelSingular (string)**: label (singular) zur Anzeige in der Benutzeroberfläche.
* **lastModified (datetime)**: Dieses Attribut enthält Informationen zum Datum und zur Uhrzeit der letzten Änderung. Es enthält das Formular &quot;Datum/Uhrzeit&quot;. Die angezeigten Werte werden vom Server übernommen. Die Uhrzeit wird im UTC-Format angezeigt.
* **library (boolean)**: Verwendung des Schemas als Bibliothek und nicht als Entität. Dieses Schema kann daher durch andere Schemata referenziert werden, die den Attributen &quot;@ref&quot; und &quot;@template&quot; entsprechen.
* **mappingType (string)**:

   * &quot;sql&quot;: Datenbank-Mapping
   * &quot;textFile&quot;: Textdateizuordnung
   * &quot;xmlFile&quot;: Textdateizuordnung im XML-Format
   * &quot;binaryFile&quot;: Binärdateizuordnung

* **modifiedBy-id (long)**: entspricht der Kennung des Operators, der das Schema geändert hat.
* **name (string)**: eindeutiger Schemaname.
* **namespace (string)**: Namespace des Schemas (Standard: nms, xtk, nl). Beim Erstellen eines neuen Schemas für ein Projekt wird empfohlen, einen dedizierten Namespace zu verwenden.
* **useRecycleBin (boolescher Wert)**: Aktiviert die Abfallfunktion in der Anwendung. Gelöschte Datensätze werden vor der endgültigen Löschung in den Papierkorb gelegt. Diese Funktion ist nur im Versandmodus verfügbar.
* **view (boolean)**: Wenn es aktiviert ist (@view=&quot;true&quot;), wird das Schema als Ansicht verwendet. Der Assistent zur Aktualisierung der Datenbankstruktur berücksichtigt das Schema nicht. Diese Option wird hauptsächlich für die Referenzierung externer Tabellen verwendet.
* **xtkschema (string)**: Name des Schemas, das die Schemakompgrammatik definiert (standardmäßig xtk:srcSchema).

## Beispiele {#examples-11}

`<srcschema>` -Element des vordefinierten Schemas &quot;nms:delivery&quot;

```
<srcSchema desc="Defines all the settings of a delivery (or delivery template)."  
           entitySchema="xtk:srcSchema" img="nms:campaign.png" implements="xtk:persist" 
           label="Diffusions" labelSingular="Diffusion" md5="DCD2164CD0276B1DCA6E1C9E2A75EC04"
           name="delivery" namespace="nms" useRecycleBin="true" xtkschema="xtk:srcSchema">
```
