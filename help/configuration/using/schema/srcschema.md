---
product: campaign
title: Elemente und Attribute - srcschema-Element
description: Elemente und Attribute
feature: Schema Extension
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: bc4329b4-d272-4d32-bdaa-290cb9912af4
source-git-commit: 254c89490fefa5d405bcecd2f1781df46450a873
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 1%

---

# srcSchema-Element {#srcschema--element}


## Inhaltsmodell {#content-model-14}

srcSchema:==(attribute | createdBy | Daten | Element | Auflistung | Hilfe | Schnittstelle | Methoden | modifiedBy)

## Attribute {#attributes-14}

created (datetime), createdBy-id (long), desc (string), entitySchema (string), extendedSchema (string), img (string), implements (string), label (string), labelSingular (string), lastModified (datetime), Library (boolean), mappingType (string), modifiedBy-id (long), name (string), namespace (string), useRecycleBin (boolean), view (boolean), xtkschema (string)

## Übergeordnete Elemente {#parents-14}

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

Die `<srcschema>` ist das Stammelement eines Schemas. Dies ist der Eingangspunkt für die Definition des Schemas.

## Verwendung und Nutzungskontext {#use-and-context-of-use-9}

Die Schemapräsentation ist unter &quot;[&#x200B; Schemareferenz“ &#x200B;](../../../configuration/using/about-schema-reference.md) &quot;[&quot; &#x200B;](../../../configuration/using/schema-structure.md).

## Attributbeschreibung {#attribute-description-14}

* **created (dateTime)**: Dieses Attribut liefert Informationen zum Datum und zur Uhrzeit der Schemaerstellung. Es hat ein „Datum/Uhrzeit“-Formular. Die angezeigten Werte werden vom Server übernommen. Die Uhrzeit wird im UTC-Format angezeigt.
* **createdBy-id (long)**: Bezeichner des Benutzers, der das Schema erstellt hat.
* **desc (Zeichenfolge)**: Schemabeschreibung
* **entitySchema (Zeichenfolge)**: Basisschema, auf dem Syntax und Genehmigung basieren (standardmäßig für Adobe Campaign: xtk:srcSchema). Wenn Sie das aktuelle Schema speichern, genehmigt Adobe Campaign dessen Grammatik anhand des im @xtkschema deklarierten Schemas.
* **extendedSchema (Zeichenfolge)**: Empfängt den Namen des vordefinierten Schemas, auf dem die aktuelle Schemaerweiterung basiert. Das Formular lautet „namespace:name“.
* **img (Zeichenfolge)**: Symbol, das mit dem Schema verknüpft ist (kann im Assistenten zur Schemaerstellung definiert werden).
* **label (Zeichenfolge)**: Schemakennzeichnung.
* **labelSingular (Zeichenfolge)**: Bezeichnung (im Singular) für die Anzeige in der Benutzeroberfläche.
* **lastModified (datetime)**: Dieses Attribut liefert Informationen zum Datum und zur Uhrzeit der letzten Änderung. Es hat ein „Datum/Uhrzeit“-Formular. Die angezeigten Werte werden vom Server übernommen. Die Uhrzeit wird im UTC-Format angezeigt.
* **library (boolean)**: Verwendung des Schemas als Bibliothek und nicht als Entität. Dieses Schema kann daher dank der Attribute &quot;@ref“ und &quot;@template“ von anderen Schemata referenziert werden.
* **mappingType (Zeichenfolge)**:

   * „SQL“: Datenbank-Mapping
   * „textFile“: Textdatei-Zuordnung
   * „xmlFile“: Textdatei-Mapping im XML-Format
   * „binaryFile“: Binärdatei-Mapping

* **modifiedBy-id (long)**: stimmt mit der Kennung des Benutzers überein, der das Schema geändert hat.
* **name (Zeichenfolge)**: Eindeutiger Schemaname.
* **namespace (String)**: Namespace des Schemas (Standard: nms, xtk, nl). Beim Erstellen eines neuen Schemas für ein Projekt empfehlen wir die Verwendung eines dedizierten Namespace.
* **useRecycleBin (Boolescher Wert**: Aktiviert die Papierkorb-Funktion in der Anwendung. Gelöschte Datensätze werden vor dem endgültigen Löschen in den Papierkorb gelegt. Diese Funktion ist nur im Modus „Versand“ verfügbar.
* **view (boolean)**: Wenn es aktiviert ist (@view=„true„), wird das Schema als Ansicht verwendet. Der Assistent zum Aktualisieren der Datenbankstruktur berücksichtigt das Schema nicht. Diese Option wird hauptsächlich zum Referenzieren externer Tabellen verwendet.
* **xtkSchema (Zeichenfolge)**: Name des Schemas, das die Schemagrammatik definiert (standardmäßig xtk:srcSchema).

## Beispiele {#examples-11}

`<srcschema>` des vorkonfigurierten Schemas „nms:delivery“

```
<srcSchema desc="Defines all the settings of a delivery (or delivery template)."  
           entitySchema="xtk:srcSchema" img="nms:campaign.png" implements="xtk:persist" 
           label="Diffusions" labelSingular="Diffusion" md5="DCD2164CD0276B1DCA6E1C9E2A75EC04"
           name="delivery" namespace="nms" useRecycleBin="true" xtkschema="xtk:srcSchema">
```
