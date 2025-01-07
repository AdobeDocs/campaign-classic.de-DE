---
product: campaign
title: Schemaelemente und -attribute - join-Element
description: Verknüpfungsglied
feature: Schema Extension
exl-id: a7ca0300-d250-429c-8ae1-2ae7dee82cf5
source-git-commit: 254c89490fefa5d405bcecd2f1781df46450a873
workflow-type: tm+mt
source-wordcount: '213'
ht-degree: 2%

---

# Verknüpfungsglied {#join--element}


## Inhaltsmodell {#content-model-7}

join:==EMPTY

## Attribute {#attributes-7}

* @dstFilterExpr (Zeichenfolge)
* @xpath-dst (Zeichenfolge)
* @xpath-src (Zeichenfolge)

## Übergeordnete Elemente {#parents-7}

`<element>`

## Untergeordnetes Element {#children-7}

Kein(e)

## Beschreibung {#description-7}

Ermöglicht die Definition der Felder, die eine Verbindung zwischen SQL-Tabellen herstellen.

## Verwendung und Nutzungskontext {#use-and-context-of-use-5}

Ein `<join>` kann nur verwendet werden, wenn das übergeordnete `<element>` vom Typ „link“ ist. Das bedeutet, dass für das übergeordnete Element das Attribut &quot;@type=link“ deklariert sein muss.

Es ist nicht erforderlich, den Namen und den Namespace der Remote-Tabelle im `<join>` anzugeben. Sie müssen im übergeordneten `<element>` angegeben werden.

Standardmäßig werden Links am Ende des Schemas definiert.

Wenn das `<join>` bei der Definition des Elements vom Typ Relation nicht angegeben wird, wird die Relation automatisch auf den Primärschlüsseln beider Tabellen platziert.

## Attributbeschreibung {#attribute-description-7}

* **dstFilterExpr (Zeichenfolge)**: Mit diesem Attribut können Sie die Anzahl der zulässigen Werte in der Remote-Tabelle einschränken.
* **xpath-dst (Zeichenfolge)**: Dieses Attribut empfängt einen Xpath (@name Attribut der Remote-Tabelle).
* **xpath-src (Zeichenfolge)**: Dieses Attribut empfängt einen Xpath (@name Attribut im aktuellen Schema).

## Beispiele {#examples-6}

Relation zwischen dem Feld „E-Mail“ der aktuellen Tabelle und dem Feld &quot;@compagny-id“ der Remote-Tabelle:

```
<join xpath-dst="@compagny-id" xpath-src="@email"/>
```

Link zur Tabelle „cus:country“ gefiltert, basierend auf dem Inhalt des Feldes &quot;@country“, das den Wert „en“ enthalten muss:

```
<element name="StockEN" type="link" label="MyLink" target="cus:Stock">
   <join xpath-dst="@country" xpath-src="@code" dstFilterExpr="@country = 'EN'"/>
 </element>
```
