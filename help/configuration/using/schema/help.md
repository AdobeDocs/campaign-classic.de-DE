---
product: campaign
title: Schemaelemente und -attribute - Hilfeelement
description: Hilfe-Element
feature: Schema Extension
exl-id: 8207868c-25ff-4ca9-afdd-41b324c7ac0d
TQID: 'https://experienceleague.adobe.com/R-Oa0H6l19qOU9KamHyVFrOWqBOw9uB2ISm2OYdQDrM'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
    internal-label: Schemas
subfeature_v2:
  - id: a72a22e0-8c8d-4019-ba42-3f2644aa91a3
    internal-label: Schema extension
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '56'
ht-degree: 23%
---
# Hilfe-Element {#help--element}


## Inhaltsmodell {#content-model-6}

help:==EMPTY

## Attribute {#attributes-6}

Kein(e)

## Übergeordnete Elemente {#parents-6}

`<srcschema>`  ,  `<element>`   ,   `<attribute>`    ,    `<enumeration>`     ,     `<value>`      ,     `<param />`,      `<method />`

## Untergeordnetes Element {#children-6}

Kein(e)

## Beschreibung {#description-6}

Mit diesem Element können Sie ein `<element>` oder `<attribute>` Element beschreiben. Sie darf nur Text enthalten und wird in XML in der Datenbank gespeichert.

## Attributbeschreibung {#attribute-description-6}

Dieses Element hat keine Attribute.

## Beispiele {#examples-5}

```
<method name="CheckOperation" static="true"
      <helpchecks the validity of a campaign</help
...
</method> 
```
