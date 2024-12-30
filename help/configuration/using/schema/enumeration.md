---
product: campaign
title: Schemaelemente und -attribute - Auflistungselement
description: Auflistungselement
feature: Schema Extension
exl-id: 4cd67278-2623-4508-9a9f-9007c6a5f8ac
source-git-commit: fd5e4bbc87a48f029a09b14ab1d927b9afe4ac52
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 8%

---

# Auflistungselement {#enumeration--element}

![](../../../assets/v7-only.svg)

## Inhaltsmodell {#content-model-5}

enumeration:==(help| Wert)

## Attribute {#attributes-5}

* @basetype (Zeichenfolge)
* @default (Zeichenfolge)
* @desc (Zeichenfolge)
* @label (Zeichenfolge)
* @name (Zeichenfolge)
* @template (Zeichenfolge)

## Übergeordnete Elemente {#parents-5}

`<srcschema>`

## Untergeordnetes Element {#children-5}

* `<help>`
* `<value>`

## Beschreibung {#description-5}

Mit diesem Element können Sie eine Auflistung mit Werten definieren. Eine Auflistung gehört zu dem Schema, in dem sie definiert ist, ist aber über ein anderes Schema zugänglich.

## Verwendung und Nutzungskontext {#use-and-context-of-use-4}

Auflistungen werden zu Beginn eines Schemas definiert (bevor das Hauptelement definiert wird).

## Attributbeschreibung {#attribute-description-5}

* **baseType (Zeichenfolge)**: Typ der in der Auflistung gespeicherten Werte.

  Liste der verfügbaren Typen:

   * BELIEBIGE
   * Eimer
   * Klecks
   * Boolesch
   * Byte
   * CDATA
   * datetime
   * datetimets
   * datetimenotz
   * date
   * DOMDocument
   * DOMElement
   * double
   * Aufzählung
   * float
   * HTML
   * int64
   * link
   * lang
   * Memo
   * MNTOKEN
   * Prozent
   * Primärschlüssel
   * Short
   * Zeichenfolge
   * time
   * timespan
   * uuid

* **default (Zeichenfolge)**: Standardwert. Der Standardwert kann auch einer der in der Auflistung definierten Werte sein.
* **desc (Zeichenfolge)**: Beschreibung der Auflistung.
* **label (Zeichenfolge)**: Auflistungsbezeichnung.
* **name (Zeichenfolge)**: Interner Name der Auflistung.
* **template (Zeichenfolge)** Dieses Attribut definiert einen Verweis auf ein `<enumeration>`, das von mehreren Schemata gemeinsam genutzt wird. Die Definition wird automatisch in das aktuelle Schema kopiert.

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
