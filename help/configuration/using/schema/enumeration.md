---
solution: Campaign Classic
product: campaign
title: Elemente und Attribute
description: Elemente und Attribute
audience: configuration
content-type: reference
topic-tags: schema-reference
translation-type: tm+mt
source-git-commit: 922257b157f8d76d6e703b0510ff689d1aa4d067
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 9%

---


# Auflistung element {#enumeration--element}

## Inhaltsmodell {#content-model-5}

Auflistung:==(help| value)

## Attribute {#attributes-5}

* @basetype (Zeichenfolge)
* @default (Zeichenfolge)
* @desc (Zeichenfolge)
* @label (Zeichenfolge)
* @name (Zeichenfolge)
* @template (Zeichenfolge)

## Eltern {#parents-5}

`<srcschema>`

## Kinder {#children-5}

* `<help>`
* `<value>`

## Beschreibung {#description-5}

Mit diesem Element können wir eine Auflistung definieren. Eine Auflistung gehört zu dem Schema, in dem sie definiert ist, ist jedoch über ein anderes Schema verfügbar.

## Verwendung und Kontext der Verwendung von {#use-and-context-of-use-4}

Auflistungen werden am Beginn eines Schemas definiert (bevor das Hauptelement definiert wird).

## Attributbeschreibung {#attribute-description-5}

* **basetype (Zeichenfolge)**: Typ der in der Auflistung gespeicherten Werte.

   Liste der verfügbaren Typen:

   * BELIEBIGE
   * bin
   * blob
   * boolean
   * Byte
   * CDATA
   * datetime
   * datetimetz
   * datetimenotz
   * date
   * DOMDocument
   * DOMElement
   * Dublette
   * enum
   * float
   * html
   * int64
   * link
   * long
   * memo
   * MNTOKEN
   * percent
   * primarykey
   * short
   * Zeichenfolge
   * Zeit
   * Zeitspanne
   * uuid

* **default (Zeichenfolge)**: Standardwert. Der Standardwert kann auch einer der in der Auflistung definierten Werte sein.
* **desc (Zeichenfolge)**: Beschreibung der Auflistung.
* **label (Zeichenfolge)**: Beschriftung der Auflistung.
* **name (Zeichenfolge)**: interner Name der Auflistung.
* **template (string)**: Dieses Attribut definiert einen Verweis auf ein  `<enumeration>` Element, das von mehreren Schemas gemeinsam verwendet wird. Die Definition wird automatisch in das aktuelle Schema kopiert.

## Beispiele {#examples-4}

Beispiel für Auflistungen, deren Werte in der Datenbank gespeichert werden:

```
    <enumeration name="myEnum">
       <value name="One" value="1"/>
       <value name="Two" value="2"/>
    </enumeration>

    <element label="Sample" name="Sample">
       <attribute dbEnum="myEnum" length="100" name="Number" required="true" type="string"/>
    </element>
```

Definition einer Auflistung mit einem Standardwert:

```
 <enumeration basetype="byte" default="email" name="canal">
    <value label="Email" name="email" value="0"/> 
    <value label="Téléphone" name="phone" value="1"/>
    <value label="Call Center" name="callcenter" value="2"/>
 </enumeration>
```
