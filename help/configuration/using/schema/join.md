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
source-wordcount: '210'
ht-degree: 5%

---


# `<join>` Element {#join--element}

## Inhaltsmodell {#content-model-7}

join:==EMPTY

## Attribute {#attributes-7}

* @dstFilterExpr (Zeichenfolge)
* @xpath-dst (Zeichenfolge)
* @xpath-src (Zeichenfolge)

## Eltern {#parents-7}

`<element>`

## Kinder {#children-7}

Ohne

## Beschreibung {#description-7}

Hiermit können Sie die Felder definieren, die eine Verbindung zwischen SQL-Tabellen erstellen.

## Verwendung und Kontext der Verwendung von {#use-and-context-of-use-5}

Ein `<join>`-Element kann nur verwendet werden, wenn das übergeordnete `<element>`-Element vom Typ &#39;link&#39; ist. Das bedeutet, dass für das übergeordnete Element das Attribut &quot;@type=link&quot;deklariert sein muss.

Es ist nicht erforderlich, den Namen und den Namensraum der Remote-Tabelle im `<join>`-Element anzugeben. Sie müssen im übergeordneten Element `<element>` angegeben werden.

Standardmäßig werden Links am Ende des Schemas definiert.

Wenn das Element `<join>` bei der Definition des Linktypelements nicht angegeben ist, wird der Link automatisch auf den primären Schlüsseln beider Tabellen platziert.

## Attributbeschreibung {#attribute-description-7}

* **dstFilterExpr (Zeichenfolge)**: Mit diesem Attribut können Sie die Anzahl der zulässigen Werte in der Remote-Tabelle einschränken.
* **xpath-dst (Zeichenfolge)**: Dieses Attribut erhält einen Xpath (@name-Attribut der Remote-Tabelle).
* **xpath-src (Zeichenfolge)**: Dieses Attribut erhält einen Xpath (@name-Attribut im aktuellen Schema).

## Beispiele {#examples-6}

Link zwischen dem Feld &quot;E-Mail&quot;der aktuellen Tabelle und dem Feld &quot;@company-id&quot;der Remote-Tabelle:

```
<join xpath-dst="@compagny-id" xpath-src="@email"/>
```

Gefilterter Link zur Tabelle &quot;cus:Country&quot;basierend auf dem Inhalt des Felds &quot;@country&quot;, das den Wert &quot;EN&quot;enthalten muss:

```
<element name="StockEN" type="link" label="MyLink" target="cus:Stock">
   <join xpath-dst="@country" xpath-src="@code" dstFilterExpr="@country = 'EN'"/>
 </element>
```
