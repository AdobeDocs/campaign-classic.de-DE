---
product: campaign
title: Elemente und Attribute - sysfilter-Element
description: Elemente und Attribute
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: a0069688-fd05-42e9-91dd-adc10bea3461
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '45'
ht-degree: 17%

---

# sysfilter-Element {#sysfilter--element}

![](../../../assets/v7-only.svg)

## Inhaltsmodell {#content-model-15}

sysFilter:==condition

## Attribute {#attributes-15}

Kein(e)

## Übergeordnete Elemente {#parents-15}

`<element>`

## Untergeordnetes Element {#children-15}

`<condition>`

## Beschreibung {#description-15}

Mit diesem Element können Sie einen Filter definieren.

## Attributbeschreibung {#attribute-description-15}

Dieses Element hat keine Attribute.

## Beispiele {#examples-12}

Definition eines Filters mit einer Bedingung für das Attribut @name :

```
<sysFilter>
      <condition expr="@name ='Doe'"/>
  <sysFilter>
```
