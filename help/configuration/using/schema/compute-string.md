---
product: campaign
title: Elemente und Attribute - Compute-String-Element
description: Compute-String Element
feature: Schema Extension
exl-id: 8a079bb8-3f53-4144-a065-5bd402649cc7
source-git-commit: 254c89490fefa5d405bcecd2f1781df46450a873
workflow-type: tm+mt
source-wordcount: '90'
ht-degree: 5%

---

# Compute-String Element {#compute-string--element}


## Inhaltsmodell {#content-model-1}

compute-string:==EMPTY

## Attribute {#attributes-1}

@expr

## Übergeordnete Elemente {#parents-1}

`<element>`

## Untergeordnetes Element {#children-1}

Kein(e)

## Beschreibung {#description-1}

Mit dem `<compute-string>` können Sie eine Zeichenfolge generieren, die auf einem XTK-Ausdruck basiert, um eine auf mehreren Werten basierende „erstellte“ Kennzeichnung in der Schnittstelle anzuzeigen.

## Verwendung und Nutzungskontext {#use-and-context-of-use-1}

Wenn kein `<compute-string>` definiert ist, wird standardmäßig ein `<compute-string>` mit den Werten des Primärschlüssels im Schema eingegeben.

## Attributbeschreibung {#attribute-description-1}

* **expr (Zeichenfolge)**: XTK- und/oder Xpath-Ausdruck

## Beispiele {#examples-1}

```
<compute-string expr="@label + Iif(@code='','', ' (' + [folder/@label] + ')')"/>  
<compute-string expr="ToString([@centralCatalog-id]) + ',' + ToString([@localOrgUnit-id])" />
```

Ergebnis der für einen Empfänger berechneten Zeichenfolge: „Martin Müller (john.doe@aol.com)“:

```
<element name="recipient">
<compute-string expr="@lastName + ' ' + @firstName +' (' + @email + ')'
"/>
...
</element>
```
