---
product: campaign
title: Elemente und Attribute
description: Elemente und Attribute
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: 8a079bb8-3f53-4144-a065-5bd402649cc7
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '89'
ht-degree: 12%

---

# compute-string element {#compute-string--element}

## Inhaltsmodell {#content-model-1}

compute-string:==EMPTY

## Attribute {#attributes-1}

@expr

## Übergeordnete Elemente {#parents-1}

`<element>`

## Untergeordnetes Element {#children-1}

Keine

## Beschreibung {#description-1}

Mit dem Element `<compute-string>` können Sie eine Zeichenfolge generieren, die auf einem XTK-Ausdruck basiert und eine &quot;integrierte&quot;Bezeichnung in der Benutzeroberfläche anzeigt, die auf mehreren Werten basiert.

## Verwendung und Kontext der Verwendung von {#use-and-context-of-use-1}

Wenn kein `<compute-string>` definiert ist, wird standardmäßig ein `<compute-string>` -Element mit den Werten des Primärschlüssels im Schema eingegeben.

## Attributbeschreibung {#attribute-description-1}

* **expr (Zeichenfolge)**: XTK-/oder Xpath-Ausdruck

## Beispiele {#examples-1}

```
<compute-string expr="@label + Iif(@code='','', ' (' + [folder/@label] + ')')"/>  
<compute-string expr="ToString([@centralCatalog-id]) + ',' + ToString([@localOrgUnit-id])" />
```

Ergebnis der für einen Empfänger berechneten Zeichenfolge: &quot;John Doe (john.doe@aol.com)&quot;:

```
<element name="recipient">
<compute-string expr="@lastName + ' ' + @firstName +' (' + @email + ')'
"/>
...
</element>
```
