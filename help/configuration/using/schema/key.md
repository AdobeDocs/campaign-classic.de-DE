---
solution: Campaign Classic
product: campaign
title: Elemente und Attribute
description: Elemente und Attribute
audience: configuration
content-type: reference
topic-tags: schema-reference
translation-type: tm+mt
source-git-commit: 1818bd2aeb60689b2ce0e59cb0bd157f000de513
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 3%

---


# `<key>` Element {#key--element}

## Inhaltsmodell {#content-model-8}

key:==keyfield

## Attribute {#attributes-8}

* @allowEmptyPart (boolean)
* @applyIf (Zeichenfolge)
* @internal (boolean)
* @label (Zeichenfolge)
* @name (MNTOKEN)
* @noDbIndex (boolean)

## Eltern {#parents-8}

`<element>`

## Kinder {#children-8}

`<keyfield>`

## Beschreibung {#description-8}

Mit diesem Element können Sie einen Schlüssel zur Identifizierung eines Datensatzes in der Tabelle definieren.

Eine Tabelle muss mindestens einen Schlüssel haben.

## Verwendung und Kontext der Verwendung von {#use-and-context-of-use-6}

In der Regel werden Schlüssel nach dem Hauptelement des Schemas und den Indizes deklariert.

Ein Schlüssel wird als Composite bezeichnet, wenn er mehrere Felder enthält (d. h. mehrere `<keyfield>` untergeordnete Felder). Verwenden Sie keinen zusammengesetzten Schlüssel, um einen primären Schlüssel zu definieren.

Wenn das Hauptelement des Schemas das Attribut &quot;@autopk=true&quot;enthält, ist der Primärschlüssel eindeutig. Wir können nur einen Primärschlüssel pro Schema haben.

Die ersten 1000 Bezeichner sind reserviert. Wenn also ein Wertebereich für Schlüssel definiert werden muss, ist der Beginn bei 1000.

## Attributbeschreibung {#attribute-description-8}

* **allowEmptyPart (boolean)**: bei einem zusammengesetzten Schlüssel, wenn dieses Attribut aktiviert ist, wird der Schlüssel als gültig betrachtet, wenn mindestens einer der Schlüssel nicht leer ist. Ist dies der Fall, ist der leere Vorgabewert &quot;0&quot;(boolesch oder für alle Arten numerischer Daten). Standardmäßig müssen alle Schlüssel, aus denen ein Composite-Schlüssel besteht, eingegeben werden.
* **applyIf (Zeichenfolge)**: Mit diesem Attribut können Sie den Schlüssel optional machen. Er definiert die Bedingung, nach der die Schlüsseldefinition angewendet wird. Dieses Attribut erhält einen XTK-Ausdruck.
* **internal (boolean)**: Wenn es aktiviert ist, zeigt dieses Attribut Adobe Campaign an, dass der Schlüssel primär ist.
* **label (Zeichenfolge)**: Beschriftung des Schlüssels.
* **name (MNTOKEN)**: interner Name des Schlüssels.
* **noDbIndex (boolean)**: Wenn es aktiviert ist (noDbIndex=&quot;true&quot;), wird das Feld, das dem Schlüssel entspricht, nicht indiziert.

## Beispiele {#examples-------}

Deklaration eines zusammengesetzten Schlüssels, der das Feld &quot;@expr&quot;oder &quot;alias&quot;leer lässt:

```
<key name="node" allowEmptyPart="true">
  <keyfield xpath="@expr"/>
   <keyfield xpath="@alias"/>
 </key>
```

Deklaration eines Primärschlüssels im Feld &quot;Name&quot; des STRING-Typs in einer `<srcschema>` und der entsprechenden SQL-Abfrage:

```
 
<key name="PrimaryKey" internal="true">  
  <keyfield xpath="@name"/>
</key>

CREATE UNIQUE INDEX Schema_PrimaryKey ON Schema(sName);
```
