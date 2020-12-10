---
solution: Campaign Classic
product: campaign
title: Elemente und Attribute
description: Elemente und Attribute
audience: configuration
content-type: reference
topic-tags: schema-reference
translation-type: tm+mt
source-git-commit: 1818bd2aeb60689b2ce0e59cb0bd157f000de513
workflow-type: tm+mt
source-wordcount: '42'
ht-degree: 26%

---


# `<sysfilter>` Element {#sysfilter--element}

## Inhaltsmodell {#content-model-15}

sysFilter:==Bedingung

## Attribute {#attributes-15}

Ohne

## Eltern {#parents-15}

`<element>`

## Kinder {#children-15}

`<condition>`

## Beschreibung {#description-15}

Mit diesem Element können Sie einen Filter definieren.

## Attributbeschreibung {#attribute-description-15}

Dieses Element hat keine Attribute.

## Beispiele {#examples-12}

Definition eines Filters mit einer Bedingung für das @name-Attribut:

```
<sysFilter>
      <condition expr="@name ='Doe'"/>
  <sysFilter>
```
