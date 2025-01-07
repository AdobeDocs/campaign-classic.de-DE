---
product: campaign
title: Schemaelemente und -attribute - Bedingungselement
description: Bedingungselement
feature: Schema Extension
exl-id: 71e98d45-3660-4d86-a5ca-8e55ae5896eb
source-git-commit: 254c89490fefa5d405bcecd2f1781df46450a873
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 5%

---

# Bedingungselement {#condition--element}


## Inhaltsmodell {#content-model-2}

condition:==EMPTY

## Attribute {#attributes-2}

* @boolOperator (Zeichenfolge)
* @enabledIf (Zeichenfolge)
* @expr (Zeichenfolge)

## Übergeordnete Elemente {#parents-2}

`<sysfilter>`

## Untergeordnetes Element {#children-2}

Kein(e)

## Beschreibung {#description-2}

Mit diesem Element können Sie eine Filterbedingung definieren.

## Verwendung und Nutzungskontext {#use-and-context-of-use-2}

Ein `<sysfiler>` kann mehrere Filterbedingungen enthalten.

## Attributbeschreibung {#attribute-description-2}

* **boolOperator (Zeichenfolge)**: Wenn mehrere `<conditions>` innerhalb desselben `<sysfilter>` definiert sind, ermöglicht Ihnen dieses Attribut das Kombinieren. Standardmäßig lautet die logische Verknüpfung zwischen `<condition>` Elementen „AND“. Mit dem Attribut &quot;@boolOperator“ können Sie Links vom Typ „OR“ und „AND“ kombinieren.
* **enabledIf (Zeichenfolge)**: Bedingungsaktivierungstest.
* **expr (Zeichenfolge)**: ein XTK-Ausdruck.

## Beispiele {#examples-2}

```
<sysfilter>
  <condition enabledIf="hasNamedRight('admin')=false" expr="@city=[currentOperator/location/@city]" />
</sysfilter>
```
