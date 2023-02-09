---
product: campaign
title: Schemaelemente und Attribute - Schlüsselelement
description: Schlüsselelement
exl-id: 3d0ef574-27a3-40f2-91a0-70e9583d9980
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 8%

---

# Schlüsselelement {#key--element}

![](../../../assets/v7-only.svg)

## Inhaltsmodell {#content-model-8}

key:==keyfield

## Attribute {#attributes-8}

* @allowEmptyPart (boolean)
* @applyIf (string)
* @internal (boolean)
* @label (string)
* @name (MNTOKEN)
* @noDbIndex (boolean)

## Übergeordnete Elemente {#parents-8}

`<element>`

## Untergeordnetes Element {#children-8}

`<keyfield>`

## Beschreibung {#description-8}

Mit diesem Element können Sie einen Schlüssel definieren, um einen Datensatz in der Tabelle zu identifizieren.

Eine Tabelle muss mindestens einen Schlüssel haben.

## Verwendung und Verwendungskontext {#use-and-context-of-use-6}

In der Regel werden Schlüssel nach dem Hauptelement des Schemata und der Indizes deklariert.

Ein Schlüssel wird als Verbund bezeichnet, wenn er mehrere Felder enthält (d. h. mehrere `<keyfield>` Kinder). Verwenden Sie keinen zusammengesetzten Schlüssel, um einen Primärschlüssel zu definieren.

Wenn das Hauptelement des Schemas das Attribut &quot;@autopk=true&quot; enthält, ist der Primärschlüssel eindeutig. Pro Schema kann nur ein Primärschlüssel verwendet werden.

Die ersten 1000 Kennungen sind reserviert. Wenn also ein Wertebereich für Schlüssel definiert werden muss, beginnen Sie bei 1000.

## Attributbeschreibung {#attribute-description-8}

* **allowEmptyPart (boolean)**: bei zusammengesetzten Schlüsseln wird dieser Schlüssel als gültig betrachtet, wenn dieses Attribut aktiviert ist, wenn mindestens einer seiner Schlüssel nicht leer ist. Ist dies der Fall, ist der leere Nennwert &quot;0&quot;(boolescher Wert oder für alle Typen numerischer Daten). Standardmäßig müssen alle Schlüssel, aus denen ein zusammengesetzter Schlüssel besteht, eingegeben werden.
* **applyIf (string)**: Mit diesem Attribut können Sie den Schlüssel optional machen. Sie definiert die Bedingung, nach der die Schlüsseldefinition angewendet wird. Dieses Attribut erhält einen XTK-Ausdruck.
* **internal (boolean)**: Wenn es aktiviert ist, informiert Adobe Campaign über das primäre Schlüsselattribut.
* **label (string)**: Titel des Schlüssels.
* **name (MNTOKEN)**: interner Name des Schlüssels.
* **noDbIndex (boolean)**: Wenn sie aktiviert ist (noDbIndex=&quot;true&quot;), wird das dem Schlüssel entsprechende Feld nicht indiziert.

## Beispiele {#examples-------}

Deklaration eines zusammengesetzten Schlüssels, der das Leeren des Felds &quot;@expr&quot;oder &quot;alias&quot;zulässt:

```
<key name="node" allowEmptyPart="true">
  <keyfield xpath="@expr"/>
   <keyfield xpath="@alias"/>
 </key>
```

Deklaration eines Primärschlüssels im Feld &quot;Name&quot;des STRING-Typs in einer `<srcschema>`  und der entsprechenden SQL-Abfrage:

```
 
<key name="PrimaryKey" internal="true">  
  <keyfield xpath="@name"/>
</key>

CREATE UNIQUE INDEX Schema_PrimaryKey ON Schema(sName);
```
