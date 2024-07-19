---
product: campaign
title: Schemaelemente und Attribute - Bedingungselement
description: Bedingungselement
feature: Schema Extension
exl-id: 71e98d45-3660-4d86-a5ca-8e55ae5896eb
source-git-commit: fd5e4bbc87a48f029a09b14ab1d927b9afe4ac52
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 5%

---

# Bedingungselement {#condition--element}

![](../../../assets/v7-only.svg)

## Inhaltsmodell {#content-model-2}

Bedingung:==EMPTY

## Attribute {#attributes-2}

* @boolOperator (Zeichenfolge)
* @enabledIf (Zeichenfolge)
* @expr (string)

## Eltern {#parents-2}

`<sysfilter>`

## Untergeordnetes Element {#children-2}

Kein(e)

## Beschreibung {#description-2}

In diesem Element können Sie eine Filterbedingung definieren.

## Verwendung und Verwendungskontext {#use-and-context-of-use-2}

Ein `<sysfiler>` -Element kann mehrere Filterbedingungen enthalten.

## Attributbeschreibung {#attribute-description-2}

* **boolOperator (Zeichenfolge)**: Wenn mehrere `<conditions>` innerhalb desselben `<sysfilter>`-Elements definiert sind, können Sie sie mit diesem Attribut kombinieren. Standardmäßig ist die logische Verknüpfung zwischen `<condition>` -Elementen &quot;AND&quot;. Mit dem Attribut &quot;@boolOperator&quot; können Sie Links vom Typ &quot;OR&quot; und &quot;AND&quot; kombinieren.
* **enabledIf (Zeichenfolge)**: Bedingungsaktivierungstest.
* **expr (string)**: ein XTK-Ausdruck.

## Beispiele {#examples-2}

```
<sysfilter>
  <condition enabledIf="hasNamedRight('admin')=false" expr="@city=[currentOperator/location/@city]" />
</sysfilter>
```
