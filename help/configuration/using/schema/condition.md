---
solution: Campaign Classic
product: campaign
title: Elemente und Attribute
description: Elemente und Attribute
audience: configuration
content-type: reference
topic-tags: schema-reference
translation-type: tm+mt
source-git-commit: 922257b157f8d76d6e703b0510ff689d1aa4d067
workflow-type: tm+mt
source-wordcount: '93'
ht-degree: 10%

---


# Conditionelement {#condition--element}

## Inhaltsmodell {#content-model-2}

Bedingung:==EMPTY

## Attribute {#attributes-2}

* @boolOperator (Zeichenfolge)
* @enabledIf (Zeichenfolge)
* @expr (Zeichenfolge)

## Eltern {#parents-2}

`<sysfilter>`

## Kinder {#children-2}

Kein

## Beschreibung {#description-2}

Mit diesem Element können Sie eine Filterbedingung definieren.

## Verwendung und Kontext der Verwendung von {#use-and-context-of-use-2}

Ein `<sysfiler>`-Element kann mehrere Filterbedingungen enthalten.

## Attributbeschreibung {#attribute-description-2}

* **boolOperator (Zeichenfolge)**: Wenn mehrere Elemente innerhalb desselben  `<conditions>` Elements definiert   `<sysfilter>` sind, können Sie sie mit diesem Attribut kombinieren. Standardmäßig ist die logische Verknüpfung zwischen `<condition>`-Elementen &quot;AND&quot;. Mit dem Attribut &quot;@boolOperator&quot;können Sie Links vom Typ &quot;OR&quot;und &quot;AND&quot;kombinieren.
* **enabledIf (Zeichenfolge)**: Aktivierung der Bedingung.
* **expr (Zeichenfolge)**: ein XTK-Ausdruck.

## Beispiele {#examples-2}

```
<sysfilter>
  <condition enabledIf="hasNamedRight('admin')=false" expr="@city=[currentOperator/location/@city]" />
</sysfilter>
```
