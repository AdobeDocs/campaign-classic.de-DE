---
product: campaign
title: Elemente und Attribute
description: Elemente und Attribute
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: fb0862f9-5dcc-49f2-b99b-9822aaf3a680
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '101'
ht-degree: 10%

---

# keyfield element {#keyfield--element}

## Inhaltsmodell {#content-model-9}

keyfield:==EMPTY

## Attribute {#attributes-9}

* @xlink (MNTOKEN)
* @xpath (MNTOKEN)

## Übergeordnete Elemente {#parents-9}

`<key>`  ,  `<dbindex />`

## Untergeordnetes Element {#children-9}

Keine

## Beschreibung {#description-9}

Dieses Element definiert die Felder, die in einen Index oder einen Schlüssel integriert werden sollen.

## Attributbeschreibung {#attribute-description-9}

* **xlink (MNTOKEN)**: ermöglicht die automatische Referenzierung von Fremdschlüsseln, die im Join für eine Relationstabelle definiert sind (N-N-Link).
* **xpath (MNTOKEN)**: Definition eines Index oder eines Schlüssels für ein  `<attribute>`  Element. Dieses Attribut erhält einen Xpath , der den Pfad zum Schemaattribut definiert, das den Schlüssel oder den Index definiert.

## Beispiele {#examples-}

Auswahl des Felds &quot;sName&quot;in einem Index mit Xpath auf &quot;@name&quot;:

```
<keyfield xpath="@name"/>
```
