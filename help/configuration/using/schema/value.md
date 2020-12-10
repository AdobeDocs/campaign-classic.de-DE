---
solution: Campaign Classic
product: campaign
title: Elemente und Attribute
description: Elemente und Attribute
audience: configuration
content-type: reference
topic-tags: schema-reference
translation-type: tm+mt
source-git-commit: 1818bd2aeb60689b2ce0e59cb0bd157f000de513
workflow-type: tm+mt
source-wordcount: '146'
ht-degree: 6%

---


# `<value>` Element {#value--element}

## Inhaltsmodell {#content-model-16}

value:==help

## Attribute {#attributes-16}

* @applyIf (Zeichenfolge)
* @desc (Zeichenfolge)
* @enabledIf (Zeichenfolge)
* @img (Zeichenfolge)
* @label (Zeichenfolge)
* @name (Zeichenfolge)
* @value (Zeichenfolge)

## Eltern {#parents-16}

`<enumeration>`

## Kinder {#children-16}

`<help>`

## Beschreibung {#description-16}

Mit diesem Element können Sie die in einer Auflistung gespeicherten Werte definieren.

## Attributbeschreibung {#attribute-description-16}

* **applyIf (Zeichenfolge)**: Mit diesem Attribut können Sie einen Auflistung-Wert als optional definieren. Es erhält einen XTK-Ausdruck.
* **desc (Zeichenfolge)**: Beschreibung der Auflistung.
* **enabledIf (Zeichenfolge)**: Bedingung zum Aktivieren des Auflistung-Werts.
* **img (Zeichenfolge)**: Bild, das mit der Auflistung im Formular &quot;Namensraum:image_name&quot;verknüpft ist. Das Bild muss auf den Anwendungsserver importiert werden.
* **label (Zeichenfolge)**: Beschriftung des Auflistung-Werts.
* **name (Zeichenfolge)**: interner Name des Wertes der Auflistung.
* **Wert (Zeichenfolge)**: Wert der Auflistung. Der Werttyp wird basierend auf dem Typ der Auflistung definiert. Wenn die Auflistung vom Zeichenfolgentyp ist, darf sie nur Zeichenfolgentypwerte enthalten.

## Beispiele {#examples-13}

```
<enumeration name="myEnum">
       <value name="One" value="1"/>
       <value name="Two" value="2"/>
    </enumeration>
```
