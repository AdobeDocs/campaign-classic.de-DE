---
product: campaign
title: Schemaelemente und -attribute
description: Auflistungselement
exl-id: 4cd67278-2623-4508-9a9f-9007c6a5f8ac
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 7%

---

# Auflistungselement {#enumeration--element}

![](../../../assets/v7-only.svg)

## Inhaltsmodell {#content-model-5}

enumeration:==(help| value)

## Attribute {#attributes-5}

* @basetype (string)
* @default (string)
* @desc (string)
* @label (string)
* @name (string)
* @template (string)

## Übergeordnete Elemente {#parents-5}

`<srcschema>`

## Untergeordnetes Element {#children-5}

* `<help>`
* `<value>`

## Beschreibung {#description-5}

Mit diesem Element können wir eine Werteauflistung definieren. Eine Auflistung gehört zu dem Schema, in dem sie definiert ist, kann jedoch über ein anderes Schema aufgerufen werden.

## Verwendung und Verwendungskontext {#use-and-context-of-use-4}

Auflistungen werden zu Beginn eines Schemas definiert (bevor das Hauptelement definiert wird).

## Attributbeschreibung {#attribute-description-5}

* **basetype (string)**: Typ der in der Auflistung gespeicherten Werte.

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
   * DOMDocument
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
   * percent
   * primarykey
   * short
   * Zeichenfolge
   * Zeit
   * timespan
   * uuid

* **default (string)**: Standardwert. Der Standardwert kann auch einer der in der Auflistung definierten Werte sein.
* **desc (Zeichenfolge)**: Auflistungsbeschreibung.
* **label (string)**: Auflistungsbezeichnung.
* **name (string)**: interner Name der Auflistung.
* **template (string)**: Dieses Attribut definiert einen Verweis auf eine `<enumeration>` -Element, das von mehreren Schemas gemeinsam genutzt wird. Die Definition wird automatisch in das aktuelle Schema kopiert.

## Beispiele {#examples-4}

Beispiel für Auflistungswerte, deren Werte in der Datenbank gespeichert sind:

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
