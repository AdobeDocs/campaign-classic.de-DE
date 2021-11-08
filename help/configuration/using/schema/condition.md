---
product: campaign
title: Elemente und Attribute
description: Elemente und Attribute
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: 71e98d45-3660-4d86-a5ca-8e55ae5896eb
source-git-commit: 34404fbe935e68f3cc11d937839209443ad4ca60
workflow-type: tm+mt
source-wordcount: '93'
ht-degree: 11%

---

# Bedingungselement {#condition--element}

![](../../../assets/v7-only.svg)

## Inhaltsmodell {#content-model-2}

Bedingung:==EMPTY

## Attribute {#attributes-2}

* @boolOperator (Zeichenfolge)
* @enabledIf (Zeichenfolge)
* @expr (string)

## Übergeordnete Elemente {#parents-2}

`<sysfilter>`

## Untergeordnetes Element {#children-2}

Kein(e)

## Beschreibung {#description-2}

In diesem Element können Sie eine Filterbedingung definieren.

## Verwendung und Verwendungskontext {#use-and-context-of-use-2}

One `<sysfiler>`  -Element kann mehrere Filterbedingungen enthalten.

## Attributbeschreibung {#attribute-description-2}

* **boolOperator (Zeichenfolge)**: wenn mehrere `<conditions>` innerhalb desselben  `<sysfilter>` -Element enthält, können Sie sie mithilfe dieses Attributs kombinieren. Standardmäßig befindet sich die logische Verknüpfung zwischen `<condition>` -Elemente ist &quot;AND&quot;. Mit dem Attribut &quot;@boolOperator&quot; können Sie Links vom Typ &quot;OR&quot; und &quot;AND&quot; kombinieren.
* **enabledIf (Zeichenfolge)**: Bedingungsaktivierungstest.
* **expr (Zeichenfolge)**: ein XTK-Ausdruck.

## Beispiele {#examples-2}

```
<sysfilter>
  <condition enabledIf="hasNamedRight('admin')=false" expr="@city=[currentOperator/location/@city]" />
</sysfilter>
```
