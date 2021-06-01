---
product: campaign
title: Elemente und Attribute
description: Elemente und Attribute
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: 71e98d45-3660-4d86-a5ca-8e55ae5896eb
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '93'
ht-degree: 11%

---

# Bedingungselement {#condition--element}

## Inhaltsmodell {#content-model-2}

Bedingung:==EMPTY

## Attribute {#attributes-2}

* @boolOperator (Zeichenfolge)
* @enabledIf (Zeichenfolge)
* @expr (string)

## Übergeordnete Elemente {#parents-2}

`<sysfilter>`

## Untergeordnetes Element {#children-2}

Keine

## Beschreibung {#description-2}

In diesem Element können Sie eine Filterbedingung definieren.

## Verwendung und Kontext der Verwendung von {#use-and-context-of-use-2}

Ein `<sysfiler>` -Element kann mehrere Filterbedingungen enthalten.

## Attributbeschreibung {#attribute-description-2}

* **boolOperator (string)**: Wenn mehrere  `<conditions>` Elemente innerhalb desselben   `<sysfilter>` Elements definiert sind, können Sie sie mit diesem Attribut kombinieren. Standardmäßig ist die logische Verknüpfung zwischen `<condition>` -Elementen &quot;AND&quot;. Mit dem Attribut &quot;@boolOperator&quot; können Sie Links vom Typ &quot;OR&quot; und &quot;AND&quot; kombinieren.
* **enabledIf (Zeichenfolge)**: Bedingungsaktivierungstest.
* **expr (Zeichenfolge)**: ein XTK-Ausdruck.

## Beispiele {#examples-2}

```
<sysfilter>
  <condition enabledIf="hasNamedRight('admin')=false" expr="@city=[currentOperator/location/@city]" />
</sysfilter>
```
