---
product: campaign
title: Schemaelemente und -attribute
description: Bedingungselement
exl-id: 71e98d45-3660-4d86-a5ca-8e55ae5896eb
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '93'
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
