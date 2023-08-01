---
product: campaign
title: Elemente und Attribute - Compute-String-Element
description: Compute-string-Element
feature: Schema Extension
exl-id: 8a079bb8-3f53-4144-a065-5bd402649cc7
source-git-commit: fd5e4bbc87a48f029a09b14ab1d927b9afe4ac52
workflow-type: tm+mt
source-wordcount: '90'
ht-degree: 5%

---

# Compute-string-Element {#compute-string--element}

![](../../../assets/v7-only.svg)

## Inhaltsmodell {#content-model-1}

compute-string:==EMPTY

## Attribute {#attributes-1}

@expr

## Eltern {#parents-1}

`<element>`

## Untergeordnetes Element {#children-1}

Kein(e)

## Beschreibung {#description-1}

Die `<compute-string>` -Element ermöglicht es Ihnen, eine auf einem XTK-Ausdruck basierende Zeichenfolge zu generieren, um in der Benutzeroberfläche eine &quot;integrierte&quot;Bezeichnung anzuzeigen, die auf mehreren Werten basiert.

## Verwendung und Verwendungskontext {#use-and-context-of-use-1}

Wenn nicht `<compute-string>` definiert wird, wird ein `<compute-string>` -Element standardmäßig mit den Werten des Primärschlüssels im Schema eingegeben.

## Attributbeschreibung {#attribute-description-1}

* **expr (Zeichenfolge)**: XTK- und/oder Xpath-Ausdruck

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
