---
product: campaign
title: Elemente und Attribute
description: Elemente und Attribute
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: a7ca0300-d250-429c-8ae1-2ae7dee82cf5
source-git-commit: 34404fbe935e68f3cc11d937839209443ad4ca60
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 5%

---

# join-Element {#join--element}

![](../../../assets/v7-only.svg)

## Inhaltsmodell {#content-model-7}

join:==EMPTY

## Attribute {#attributes-7}

* @dstFilterExpr (Zeichenfolge)
* @xpath-dst (string)
* @xpath-src (Zeichenfolge)

## Übergeordnete Elemente {#parents-7}

`<element>`

## Untergeordnetes Element {#children-7}

Keine

## Beschreibung {#description-7}

Ermöglicht die Definition der Felder, die eine Verknüpfung zwischen SQL-Tabellen herstellen.

## Verwendung und Verwendungskontext {#use-and-context-of-use-5}

Ein Element `<join>` kann nur verwendet werden, wenn das übergeordnete Element `<element>` vom Typ &quot;Link&quot;ist. Das bedeutet, dass für das übergeordnete Element das Attribut &quot;@type=link&quot;deklariert sein muss.

Es ist nicht erforderlich, den Namen und Namespace der Remote-Tabelle im Element `<join>` anzugeben. Sie müssen im übergeordneten `<element>` angegeben werden.

Standardmäßig werden Links am Ende des Schemas definiert.

Wenn das Element `<join>` bei der Definition des Relationstypelements nicht angegeben ist, wird der Link automatisch in die Primärschlüssel der beiden Tabellen eingefügt.

## Attributbeschreibung {#attribute-description-7}

* **dstFilterExpr (Zeichenfolge)**: Mit diesem Attribut können Sie die Anzahl der zulässigen Werte in der Remote-Tabelle einschränken.
* **xpath-dst (string)**: Dieses Attribut erhält einen Xpath (@name -Attribut der Remote-Tabelle).
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
