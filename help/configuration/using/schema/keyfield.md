---
product: campaign
title: Schemaelemente und -attribute
description: keyfield-Element
exl-id: fb0862f9-5dcc-49f2-b99b-9822aaf3a680
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '101'
ht-degree: 4%

---

# keyfield-Element {#keyfield--element}

![](../../../assets/v7-only.svg)

## Inhaltsmodell {#content-model-9}

keyfield:==EMPTY

## Attribute {#attributes-9}

* @xlink (MNTOKEN)
* @xpath (MNTOKEN)

## Übergeordnete Elemente {#parents-9}

`<key>`  ,  `<dbindex />`

## Untergeordnetes Element {#children-9}

Kein(e)

## Beschreibung {#description-9}

Dieses Element definiert die Felder, die in einen Index oder einen Schlüssel integriert werden sollen.

## Attributbeschreibung {#attribute-description-9}

* **xlink (MNTOKEN)**: ermöglicht die automatische Referenzierung von Fremdschlüsseln, die im Join für eine Relationstabelle definiert sind (N-N-Link).
* **xpath (MNTOKEN)**: Definition eines Index oder eines Schlüssels auf einem `<attribute>`  -Element. Dieses Attribut erhält einen Xpath , der den Pfad zum Schemaattribut definiert, das den Schlüssel oder den Index definiert.

## Beispiele {#examples-}

Auswahl des Felds &quot;sName&quot;in einem Index mit Xpath auf &quot;@name&quot;:

```
<keyfield xpath="@name"/>
```
