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
source-wordcount: '89'
ht-degree: 11%

---


# compute-string element {#compute-string--element}

## Inhaltsmodell {#content-model-1}

compute-string:==EMPTY

## Attribute {#attributes-1}

@expr

## Eltern {#parents-1}

`<element>`

## Kinder {#children-1}

Ohne

## Beschreibung {#description-1}

Mit dem `<compute-string>`-Element können Sie eine auf einem XTK-Ausdruck basierende Zeichenfolge generieren, um eine &quot;integrierte&quot;Beschriftung in der Schnittstelle basierend auf mehreren Werten anzuzeigen.

## Verwendung und Kontext der Verwendung von {#use-and-context-of-use-1}

Wenn kein `<compute-string>`-Element definiert ist, wird standardmäßig ein `<compute-string>`-Element mit den Werten des primären Schlüssels im Schema eingegeben.

## Attributbeschreibung {#attribute-description-1}

* **expr (Zeichenfolge)**: XTK- und/oder Xpath-Ausdruck

## Beispiele {#examples-1}

```
<compute-string expr="@label + Iif(@code='','', ' (' + [folder/@label] + ')')"/>  
<compute-string expr="ToString([@centralCatalog-id]) + ',' + ToString([@localOrgUnit-id])" />
```

Ergebnis der auf einem Empfänger berechneten Zeichenfolge: &quot;John Doe (john.doe@aol.com)&quot;:

```
<element name="recipient">
<compute-string expr="@lastName + ' ' + @firstName +' (' + @email + ')'
"/>
...
</element>
```
