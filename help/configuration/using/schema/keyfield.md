---
product: campaign
title: Schemaelemente und -attribute - keyField-Element
description: Schlüsselfeldelement
feature: Schema Extension
exl-id: fb0862f9-5dcc-49f2-b99b-9822aaf3a680
source-git-commit: 254c89490fefa5d405bcecd2f1781df46450a873
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 4%

---

# Schlüsselfeldelement {#keyfield--element}


## Inhaltsmodell {#content-model-9}

keyfield:==EMPTY

## Attribute {#attributes-9}

* @xlink (MNTOKEN)
* @xpath (MNTOKEN)

## Übergeordnete Elemente {#parents-9}

`<key>` , `<dbindex />`

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
