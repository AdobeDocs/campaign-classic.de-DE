---
product: campaign
title: Schemaelemente und Attribute - keyfield-Element
description: keyfield-Element
feature: Schema Extension
exl-id: fb0862f9-5dcc-49f2-b99b-9822aaf3a680
source-git-commit: fd5e4bbc87a48f029a09b14ab1d927b9afe4ac52
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 4%

---

# keyfield-Element {#keyfield--element}

![](../../../assets/v7-only.svg)

## Inhaltsmodell {#content-model-9}

keyfield:==EMPTY

## Attribute {#attributes-9}

* @xlink (MNTOKEN)
* @xpath (MNTOKEN)

## Eltern {#parents-9}

`<key>`  ,  `<dbindex />`

## Untergeordnetes Element {#children-9}

Kein(e)

## Beschreibung {#description-9}

Dieses Element definiert die Felder, die in einen Index oder einen Schlüssel integriert werden sollen.

## Attributbeschreibung {#attribute-description-9}

* **xlink (MNTOKEN)**: referenziert automatisch Fremdschlüssel, die im Join für eine Relationstabelle definiert sind (N-N-Link).
* **xpath (MNTOKEN)**: Definition eines Index oder eines Schlüssels auf einem `<attribute>`  -Element. Dieses Attribut erhält einen Xpath , der den Pfad zum Schemaattribut definiert, das den Schlüssel oder den Index definiert.

## Beispiele {#examples-}

Auswahl des Felds &quot;sName&quot;in einem Index mit Xpath auf &quot;@name&quot;:

```
<keyfield xpath="@name"/>
```
