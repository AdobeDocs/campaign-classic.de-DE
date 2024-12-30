---
product: campaign
title: Elemente und Attribute - sysfilter-Element
description: Elemente und Attribute
feature: Schema Extension
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: a0069688-fd05-42e9-91dd-adc10bea3461
source-git-commit: fd5e4bbc87a48f029a09b14ab1d927b9afe4ac52
workflow-type: tm+mt
source-wordcount: '45'
ht-degree: 17%

---

# sysFilter-Element {#sysfilter--element}

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

Definition eines Filters mit einer Bedingung für das @name:

```
<sysFilter>
      <condition expr="@name ='Doe'"/>
  <sysFilter>
```
