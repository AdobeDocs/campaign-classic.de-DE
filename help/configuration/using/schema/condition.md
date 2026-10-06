---
product: campaign
title: Schemaelemente und -attribute - Bedingungselement
description: Bedingungselement
feature: Schema Extension
exl-id: 71e98d45-3660-4d86-a5ca-8e55ae5896eb
TQID: 'https://experienceleague.adobe.com/Jx8bLCt1UEqAZDm0cSuexx25js-e5xTsvkeSMzVCUHw'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
    internal-label: Schemas
subfeature_v2:
  - id: a72a22e0-8c8d-4019-ba42-3f2644aa91a3
    internal-label: Schema extension
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
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
