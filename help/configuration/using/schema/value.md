---
product: campaign
title: Elemente und Attribute - Wertelement
description: Elemente und Attribute
feature: Schema Extension
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: bad7fb4b-43d9-4033-ae0d-cf191d89114b
source-git-commit: fd5e4bbc87a48f029a09b14ab1d927b9afe4ac52
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 4%

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

## Eltern {#parents-16}

`<enumeration>`

## Untergeordnetes Element {#children-16}

`<help>`

## Beschreibung {#description-16}

Mit diesem Element können Sie die in einer Auflistung gespeicherten Werte definieren.

## Attributbeschreibung {#attribute-description-16}

* **applyIf (string)**: Mit diesem Attribut können Sie einen Auflistungswert optional machen. Er erhält einen XTK-Ausdruck.
* **desc (string)**: Beschreibung des Auflistungswerts.
* **enabledIf (string)**: Bedingung zum Aktivieren des Auflistungswerts.
* **img (string)**: Bild, das mit der Auflistung im Formular &quot;namespace:image_name&quot;verknüpft ist. Das Bild muss auf den Anwendungsserver importiert werden.
* **label (string)**: Titel des Auflistungswerts.
* **name (string)**: Interner Name des Auflistungswerts.
* **value (string)**: Wert des Auflistungswerts. Der Werttyp wird basierend auf dem Auflistungstyp definiert. Wenn es sich bei der Auflistung um eine Auflistung vom Typ Zeichenfolge handelt, darf sie nur Zeichenfolgenwerte vom Typ Zeichenfolge enthalten.

## Beispiele {#examples-13}

```
<enumeration name="myEnum">
       <value name="One" value="1"/>
       <value name="Two" value="2"/>
    </enumeration>
```
