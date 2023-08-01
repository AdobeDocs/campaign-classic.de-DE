---
product: campaign
title: Schemaelemente und Attribute - Element verknüpfen
description: join-Element
feature: Schema Extension
exl-id: a7ca0300-d250-429c-8ae1-2ae7dee82cf5
source-git-commit: fd5e4bbc87a48f029a09b14ab1d927b9afe4ac52
workflow-type: tm+mt
source-wordcount: '213'
ht-degree: 2%

---

# join-Element {#join--element}

![](../../../assets/v7-only.svg)

## Inhaltsmodell {#content-model-7}

join:==EMPTY

## Attribute {#attributes-7}

* @dstFilterExpr (Zeichenfolge)
* @xpath-dst (string)
* @xpath-src (Zeichenfolge)

## Eltern {#parents-7}

`<element>`

## Untergeordnetes Element {#children-7}

Kein(e)

## Beschreibung {#description-7}

Ermöglicht die Definition der Felder, die eine Verknüpfung zwischen SQL-Tabellen herstellen.

## Verwendung und Verwendungskontext {#use-and-context-of-use-5}

A `<join>`  -Element kann nur verwendet werden, wenn das übergeordnete Element  `<element>`  -Element vom Typ &#39;link&#39; ist. Das bedeutet, dass für das übergeordnete Element das Attribut &quot;@type=link&quot;deklariert sein muss.

Es ist nicht erforderlich, den Namen und Namespace der Remote-Tabelle im `<join>`  -Element. Sie müssen im übergeordneten Element angegeben werden  `<element>`.

Standardmäßig werden Links am Ende des Schemas definiert.

Wenn die Variable `<join>` -Element bei der Definition des Relationstypelements nicht angegeben ist, wird der Link automatisch auf die Primärschlüssel der beiden Tabellen gesetzt.

## Attributbeschreibung {#attribute-description-7}

* **dstFilterExpr (Zeichenfolge)**: Mit diesem Attribut können Sie die Anzahl der zulässigen Werte in der Remote-Tabelle einschränken.
* **xpath-dst (Zeichenfolge)**: Dieses Attribut erhält einen Xpath (@name -Attribut der Remote-Tabelle).
* **xpath-src (Zeichenfolge)**: Dieses Attribut erhält einen Xpath (@name -Attribut im aktuellen Schema).

## Beispiele {#examples-6}

Relation zwischen dem Feld &#39;email&#39; der aktuellen Tabelle und dem Feld &quot;@company-id&quot; der Remote-Tabelle:

```
<join xpath-dst="@compagny-id" xpath-src="@email"/>
```

Gefilterter Link zur Tabelle &quot;cus:Country&quot;, basierend auf dem Inhalt des Felds &quot;@country&quot;, das den Wert &quot;EN&quot; enthalten muss:

```
<element name="StockEN" type="link" label="MyLink" target="cus:Stock">
   <join xpath-dst="@country" xpath-src="@code" dstFilterExpr="@country = 'EN'"/>
 </element>
```
