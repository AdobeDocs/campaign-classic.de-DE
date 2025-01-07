---
product: campaign
title: Schemaelemente und -attribute - Hilfeelement
description: Hilfe-Element
feature: Schema Extension
exl-id: 8207868c-25ff-4ca9-afdd-41b324c7ac0d
source-git-commit: 254c89490fefa5d405bcecd2f1781df46450a873
workflow-type: tm+mt
source-wordcount: '49'
ht-degree: 12%

---

# Hilfe-Element {#help--element}


## Inhaltsmodell {#content-model-6}

help:==EMPTY

## Attribute {#attributes-6}

Kein(e)

## Übergeordnete Elemente {#parents-6}

`<srcschema>` , `<element>`   ,   `<attribute>`    ,    `<enumeration>`     ,     `<value>`      ,     `<param />`,      `<method />`

## Untergeordnetes Element {#children-6}

Kein(e)

## Beschreibung {#description-6}

Mit diesem Element können Sie eine `<element>` oder einen `<attribute>` beschreiben   -Element. Sie darf nur Text enthalten und wird in XML in der Datenbank gespeichert.

## Attributbeschreibung {#attribute-description-6}

Dieses Element hat keine Attribute.

## Beispiele {#examples-5}

```
<method name="CheckOperation" static="true"
      <helpchecks the validity of a campaign</help
...
</method> 
```
