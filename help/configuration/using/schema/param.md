---
product: campaign
title: Schemaelemente und -attribute - param-Element
description: Parameterelement
feature: Schema Extension
exl-id: d8960a2e-6900-4346-9f06-e7dd9d7b5139
TQID: https://experienceleague.adobe.com/fiMkJtGU90FP-G6BJhTnIrgBJ39uIJaakqKD49EhXS0
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 177
ht-degree: 12%

---

# Parameterelement {#param--element}


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
* @namespace (MNTOKEN)
* @type (Zeichenfolge)

## Übergeordnete Elemente {#parents-12}

`<parameters>`

## Untergeordnetes Element {#children-12}

`<help>`

## Beschreibung {#description-12}

Mit diesem Element können Sie einen Parameter zum Aufrufen einer SOAP-Methode definieren.

## Attributbeschreibung {#attribute-description-12}

* **desc (Zeichenfolge)**: Beschreibung, die das `<param>` betrifft.
* **inout (Zeichenfolge)** Dieses Attribut definiert, ob sich der Parameter an der Eingabe (in) oder Ausgabe (out) des SOAP-Aufrufs befindet. Wenn dieses Attribut nicht angegeben wird, ist der Standardparameter input (“@inout=in„).
* **label (Zeichenfolge)**: `<param>` label
* **Localizable (String)**: Wenn es aktiviert ist, weist dieses Attribut das Sammlungs-Tool an, den Wert des Attributs &quot;@label“ für die Übersetzung abzurufen (interne Verwendung).
* **name (MNTOKEN)**: Interner Name des `<param>`
* **type (Zeichenfolge)** Dieses Attribut definiert den Typ `<param>` Elements

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
   * Lang
   * Memo
   * MNTOKEN
   * Prozent
   * Primärschlüssel
   * Kurz
   * Zeichenfolge
   * time
   * timespan
   * uuid

## Beispiele {#examples-9}

Definition der eingehenden Einstellung „serviceName“ vom Typ String:

```
<param desc="Name of the information service(s) (separated with commas)"
               name="serviceName" type="string" inout="in"/>
```
