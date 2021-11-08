---
product: campaign
title: Elemente und Attribute
description: Elemente und Attribute
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: 8207868c-25ff-4ca9-afdd-41b324c7ac0d
source-git-commit: 34404fbe935e68f3cc11d937839209443ad4ca60
workflow-type: tm+mt
source-wordcount: '47'
ht-degree: 25%

---

# help-Element {#help--element}

![](../../../assets/v7-only.svg)

## Inhaltsmodell {#content-model-6}

help:==EMPTY

## Attribute {#attributes-6}

Kein(e)

## Übergeordnete Elemente {#parents-6}

`<srcschema>`  ,  `<element>`   ,   `<attribute>`    ,    `<enumeration>`     ,     `<value>`      ,     `<param />`,      `<method />`

## Untergeordnetes Element {#children-6}

Kein(e)

## Beschreibung {#description-6}

Dieses Element ermöglicht die Beschreibung einer `<element>`  oder  `<attribute>`   -Element. Sie darf nur Text enthalten und wird in XML in der Datenbank gespeichert.

## Attributbeschreibung {#attribute-description-6}

Dieses Element hat keine Attribute.

## Beispiele {#examples-5}

```
<method name="CheckOperation" static="true"
      <helpchecks the validity of a campaign</help
...
</method> 
```
