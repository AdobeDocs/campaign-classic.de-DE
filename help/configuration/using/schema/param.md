---
product: campaign
title: Schemaelemente und Attribute - Parameter-Element
description: param-Element
feature: Schema Extension
exl-id: d8960a2e-6900-4346-9f06-e7dd9d7b5139
source-git-commit: fd5e4bbc87a48f029a09b14ab1d927b9afe4ac52
workflow-type: tm+mt
source-wordcount: '177'
ht-degree: 9%

---

# param-Element {#param--element}

![](../../../assets/v7-only.svg)

## Inhaltsmodell {#content-model-12}

param:==help

## Attribute {#attributes-12}

* @_operation (string)
* @desc (string)
* @enum (string)
* @inout (string)
* @label (string)
* @localizable (string)
* @name (MNTOKEN)
* @namespace (MNTOKEN)
* @type (string)

## Eltern {#parents-12}

`<parameters>`

## Untergeordnetes Element {#children-12}

`<help>`

## Beschreibung {#description-12}

Mit diesem Element können Sie einen Parameter zum Aufrufen einer SOAP-Methode definieren.

## Attributbeschreibung {#attribute-description-12}

* **desc (Zeichenfolge)**: Beschreibung, die sich auf die `<param>` -Element.
* **inout (Zeichenfolge)**: Dieses Attribut definiert, ob sich der Parameter an der Eingabe (in) oder Ausgabe (out) des SOAP-Aufrufs befindet. Wenn dieses Attribut nicht angegeben ist, lautet der Standardparameter input (&quot;@inout=in&quot;).
* **label (string)**: `<param>` label
* **localizable (string)**: Wenn es aktiviert ist, weist dieses Attribut das Tool zur Sammlung an, den Wert des Attributs &quot;@label&quot;für die Übersetzung abzurufen (interne Verwendung).
* **name (MNTOKEN)**: Interner Name der `<param>`
* **type (string)**: Dieses Attribut definiert den Typ von `<param>` element

  Liste der verfügbaren Typen:

   * BELIEBIGE
   * bin
   * blob
   * Boolesch
   * Byte
   * CDATA
   * datetime
   * datetimetz
   * datetimenotz
   * date
   * DOMDdocument
   * DOMElement
   * double
   * enum
   * float
   * html
   * int64
   * link
   * long
   * Memo
   * MNTOKEN
   * Prozent
   * primarykey
   * short
   * Zeichenfolge
   * time
   * timespan
   * uuid

## Beispiele {#examples-9}

Definition der Einstellung &quot;serviceName&quot; für den Zeichenfolgentyp:

```
<param desc="Name of the information service(s) (separated with commas)"
               name="serviceName" type="string" inout="in"/>
```
