---
product: campaign
title: Elemente und Attribute - Compute-String-Element
description: Compute-String Element
feature: Schema Extension
exl-id: 8a079bb8-3f53-4144-a065-5bd402649cc7
TQID: 'https://experienceleague.adobe.com/vLSA9oDdBg-0sElc6QlusY-YviNyRU8Fq6yXRrFrN1g'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
    internal-label: Schemas
subfeature_v2:
  - id: a72a22e0-8c8d-4019-ba42-3f2644aa91a3
    internal-label: Schema extension
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '95'
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
