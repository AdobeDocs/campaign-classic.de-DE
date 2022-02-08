---
product: campaign
title: Schemaelemente und -attribute
description: help-Element
exl-id: 8207868c-25ff-4ca9-afdd-41b324c7ac0d
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '47'
ht-degree: 12%

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
