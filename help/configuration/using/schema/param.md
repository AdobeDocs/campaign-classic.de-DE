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
source-wordcount: '175'
ht-degree: 10%

---


# param element {#param--element}

## Inhaltsmodell {#content-model-12}

param:==help

## Attribute {#attributes-12}

* @_operation (Zeichenfolge)
* @desc (Zeichenfolge)
* @enum (Zeichenfolge)
* @inout (Zeichenfolge)
* @label (Zeichenfolge)
* @localizable (Zeichenfolge)
* @name (MNTOKEN)
* @Namensraum (MNTOKEN)
* @type (Zeichenfolge)

## Eltern {#parents-12}

`<parameters>`

## Kinder {#children-12}

`<help>`

## Beschreibung {#description-12}

Mit diesem Element können Sie einen Parameter zum Aufrufen einer SOAP-Methode definieren.

## Attributbeschreibung {#attribute-description-12}

* **desc (Zeichenfolge)**: Beschreibung, die das  `<param>` Element betrifft.
* **inout (Zeichenfolge)**: Dieses Attribut definiert, ob sich der Parameter am Eingang (in) oder an der Ausgabe (out) des SOAP-Aufrufs befindet. Wenn dieses Attribut nicht angegeben ist, lautet der Standardparameter input (&quot;@inout=in&quot;).
* **label (Zeichenfolge)**:  `<param>` label
* **localizable (Zeichenfolge)**: Wenn es aktiviert ist, weist dieses Attribut das Erfassungswerkzeug an, den Wert des Attributs &quot;@label&quot;für die Übersetzung wiederherzustellen (interne Verwendung).
* **name (MNTOKEN)**: interner Name der  `<param>`
* **type (string)**: Dieses Attribut definiert den Typ des  `<param>` Elements

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
   * dublette
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

## Beispiele {#examples-9}

Definition der Einstellung &quot;serviceName&quot; für den Zeichenfolgentyp:

```
<param desc="Name of the information service(s) (separated with commas)"
               name="serviceName" type="string" inout="in"/>
```
