---
product: campaign
title: Elemente und Attribute
description: Elemente und Attribute
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: 8a079bb8-3f53-4144-a065-5bd402649cc7
source-git-commit: 34404fbe935e68f3cc11d937839209443ad4ca60
workflow-type: tm+mt
source-wordcount: '89'
ht-degree: 12%

---

# Compute-string-Element {#compute-string--element}

![](../../../assets/v7-only.svg)

## Inhaltsmodell {#content-model-1}

compute-string:==EMPTY

## Attribute {#attributes-1}

@expr

## Übergeordnete Elemente {#parents-1}

`<element>`

## Untergeordnetes Element {#children-1}

Kein(e)

## Beschreibung {#description-1}

Die `<compute-string>` -Element ermöglicht es Ihnen, eine auf einem XTK-Ausdruck basierende Zeichenfolge zu generieren, um in der Benutzeroberfläche eine &quot;integrierte&quot;Bezeichnung anzuzeigen, die auf mehreren Werten basiert.

## Verwendung und Verwendungskontext {#use-and-context-of-use-1}

Wenn nicht `<compute-string>` definiert wird, wird ein `<compute-string>` -Element standardmäßig mit den Werten des Primärschlüssels im Schema eingegeben.

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
