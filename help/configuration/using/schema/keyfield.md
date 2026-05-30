---
product: campaign
title: Schemaelemente und -attribute - keyField-Element
description: Schlüsselfeldelement
feature: Schema Extension
exl-id: fb0862f9-5dcc-49f2-b99b-9822aaf3a680
TQID: https://experienceleague.adobe.com/tVWLlgg97dREZZHvUW81FhDVhS-uNvUHlbhH0YBrAdY
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
subfeature_v2: []
source-git-commit: bb41e9407ab5853b0194bb325bbf3f17bc3ea232
workflow-type: tm+mt
source-wordcount: 104
ht-degree: 4%

---

# Schlüsselfeldelement {#keyfield--element}


## Inhaltsmodell {#content-model-9}

keyfield:==EMPTY

## Attribute {#attributes-9}

* @xlink (MNTOKEN)
* @xpath (MNTOKEN)

## Übergeordnete Elemente {#parents-9}

`<key>`  ,  `<dbindex />`

## Untergeordnetes Element {#children-9}

Kein(e)

## Beschreibung {#description-9}

Dieses Element definiert die Felder, die in einen Index oder einen Schlüssel integriert werden sollen.

## Attributbeschreibung {#attribute-description-9}

* **xlink (MNTOKEN)**: ermöglicht die automatische Referenzierung von Fremdschlüsseln, die im Join für eine Beziehungstabelle definiert sind (N-N-Link).
* **xpath (MNTOKEN)**: Definition eines Index oder Schlüssels für ein `<attribute>`. Dieses Attribut erhält einen XPath, der den Pfad zum Schemaattribut definiert, das den Schlüssel oder den Index definiert.

## Beispiele {#examples-}

Auswahl des Felds „sName“ in einem Index mit einem Xpath zu &quot;@name“:

```
<keyfield xpath="@name"/>
```
