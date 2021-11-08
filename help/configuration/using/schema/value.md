---
product: campaign
title: Elemente und Attribute
description: Elemente und Attribute
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: bad7fb4b-43d9-4033-ae0d-cf191d89114b
source-git-commit: 34404fbe935e68f3cc11d937839209443ad4ca60
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 6%

---

# Wert-Element {#value--element}

![](../../../assets/v7-only.svg)

## Inhaltsmodell {#content-model-16}

value:==help

## Attribute {#attributes-16}

* @applyIf (string)
* @desc (string)
* @enabledIf (Zeichenfolge)
* @img (string)
* @label (string)
* @name (string)
* @value (string)

## Übergeordnete Elemente {#parents-16}

`<enumeration>`

## Untergeordnetes Element {#children-16}

`<help>`

## Beschreibung {#description-16}

Mit diesem Element können Sie die in einer Auflistung gespeicherten Werte definieren.

## Attributbeschreibung {#attribute-description-16}

* **applyIf (string)**: Mit diesem Attribut können Sie einen Auflistungswert optional machen. Er erhält einen XTK-Ausdruck.
* **desc (Zeichenfolge)**: Beschreibung des Auflistungswerts.
* **enabledIf (Zeichenfolge)**: -Bedingung zum Aktivieren des Auflistungswerts.
* **img (Zeichenfolge)**: Bild, das mit der Auflistung im Formular &quot;namespace:image_name&quot;verknüpft ist. Das Bild muss auf den Anwendungsserver importiert werden.
* **label (string)**: Titel des Auflistungswerts.
* **name (string)**: interner Name des Auflistungswerts.
* **value (string)**: -Wert des Auflistungswerts. Der Werttyp wird basierend auf dem Auflistungstyp definiert. Wenn es sich bei der Auflistung um eine Auflistung vom Typ Zeichenfolge handelt, darf sie nur Zeichenfolgenwerte vom Typ Zeichenfolge enthalten.

## Beispiele {#examples-13}

```
<enumeration name="myEnum">
       <value name="One" value="1"/>
       <value name="Two" value="2"/>
    </enumeration>
```
