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
source-wordcount: '101'
ht-degree: 9%

---


# keyfield element {#keyfield--element}

## Inhaltsmodell {#content-model-9}

keyfield:==EMPTY

## Attribute {#attributes-9}

* @xlink (MNTOKEN)
* @xpath (MNTOKEN)

## Eltern {#parents-9}

`<key>`  ,  `<dbindex />`

## Kinder {#children-9}

Ohne

## Beschreibung {#description-9}

Dieses Element definiert die Felder, die in einen Index oder Schlüssel integriert werden sollen.

## Attributbeschreibung {#attribute-description-9}

* **xlink (MNTOKEN)**: können Sie automatisch auf Fremdschlüssel verweisen, die in der Verknüpfung für eine Beziehungstabelle (N-N-Link) definiert sind.
* **xpath (MNTOKEN)**: Definition eines Indexes oder eines Schlüssels für ein  `<attribute>`  Element. Dieses Attribut erhält einen Xpath, der den Pfad zum Schema-Attribut definiert, das den Schlüssel oder den Index definiert.

## Beispiele {#examples-}

Auswahl des Felds &quot;sName&quot;in einem Index mit einem Xpath auf &quot;@name&quot;:

```
<keyfield xpath="@name"/>
```
