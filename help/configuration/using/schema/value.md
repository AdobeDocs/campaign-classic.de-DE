---
product: campaign
title: Elemente und Attribute - Wertelement
description: Elemente und Attribute
feature: Schema Extension
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: bad7fb4b-43d9-4033-ae0d-cf191d89114b
source-git-commit: 254c89490fefa5d405bcecd2f1781df46450a873
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 4%

---

# Wertelement {#value--element}


## Inhaltsmodell {#content-model-16}

value:==help

## Attribute {#attributes-16}

* @applicableIf (Zeichenfolge)
* @desc (Zeichenfolge)
* @enabledIf (Zeichenfolge)
* @img (Zeichenfolge)
* @label (Zeichenfolge)
* @name (Zeichenfolge)
* @value (Zeichenfolge)

## Übergeordnete Elemente {#parents-16}

`<enumeration>`

## Untergeordnetes Element {#children-16}

`<help>`

## Beschreibung {#description-16}

Mit diesem Element können Sie die in einer Auflistung gespeicherten Werte definieren.

## Attributbeschreibung {#attribute-description-16}

* **applicableIf (Zeichenfolge)**: Mit diesem Attribut können Sie einen Auflistungswert optional machen. Sie erhält einen XTK-Ausdruck.
* **desc (Zeichenfolge)**: Beschreibung des Auflistungswerts.
* **enabledIf (Zeichenfolge)**: Bedingung für die Aktivierung des Auflistungswerts.
* **img (Zeichenfolge)**: Bild, das mit der Auflistung im Formular „namespace:image_name“ verknüpft ist. Das Bild muss auf den Anwendungsserver importiert werden.
* **label (Zeichenfolge)**: Bezeichnung des Auflistungswerts.
* **name (Zeichenfolge)**: Interner Name des Auflistungswerts.
* **value (Zeichenfolge)**: Wert des -Auflistungswerts. Der Typ des Werts wird anhand des Typs der Auflistung definiert. Wenn die Auflistung vom Typ Zeichenfolge ist, darf sie nur Zeichenfolgenwerte enthalten.

## Beispiele {#examples-13}

```
<enumeration name="myEnum">
       <value name="One" value="1"/>
       <value name="Two" value="2"/>
    </enumeration>
```
