---
product: campaign
title: Schemaelemente und -attribute - Schlüsselelement
description: Schlüsselelement
feature: Schema Extension
exl-id: 3d0ef574-27a3-40f2-91a0-70e9583d9980
TQID: https://experienceleague.adobe.com/5LDW8-4YjfDebSOFq6ON8c0ulQQsGGjmRbek67G4Ml4
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
subfeature_v2: []
source-git-commit: bb41e9407ab5853b0194bb325bbf3f17bc3ea232
workflow-type: tm+mt
source-wordcount: 322
ht-degree: 8%

---

# Schlüsselelement {#key--element}


## Inhaltsmodell {#content-model-8}

key:==keyField

## Attribute {#attributes-8}

* @allowEmptyPart (Boolesch)
* @applicableIf (Zeichenfolge)
* @internal (Boolesch)
* @label (Zeichenfolge)
* @name (MNTOKEN)
* @noDbIndex (Boolesch)

## Übergeordnete Elemente {#parents-8}

`<element>`

## Untergeordnetes Element {#children-8}

`<keyfield>`

## Beschreibung {#description-8}

Mit diesem Element können Sie einen Schlüssel zur Identifizierung eines Datensatzes in der Tabelle definieren.

Eine Tabelle muss mindestens einen Schlüssel haben.

## Verwendung und Nutzungskontext {#use-and-context-of-use-6}

In der Regel werden Schlüssel nach dem Hauptelement des Schemata und der Indizes deklariert.

Ein Schlüssel wird als zusammengesetzter Schlüssel bezeichnet, wenn er mehrere Felder (d. h. mehrere `<keyfield>` untergeordnete Elemente) enthält. Verwenden Sie keinen zusammengesetzten Schlüssel zum Definieren eines Primärschlüssels.

Wenn das Hauptelement des Schemas das Attribut &quot;@autopk=true“ enthält, ist der Primärschlüssel eindeutig. Pro Schema kann nur ein Primärschlüssel verwendet werden.

Die ersten 1.000 Kennungen sind reserviert. Wenn also ein Wertebereich für Schlüssel definiert werden muss, beginnen Sie bei 1.000.

## Attributbeschreibung {#attribute-description-8}

* **allowEmptyPart (boolean)**: Bei zusammengesetzten Schlüsseln wird der Schlüssel als gültig betrachtet, wenn mindestens einer der Schlüssel nicht leer ist, wenn dieses Attribut aktiviert ist. Wenn dies der Fall ist, ist der leere Begriffswert „0“ (boolesch oder für alle Arten numerischer Daten). Standardmäßig müssen alle Schlüssel eingegeben werden, aus denen sich ein zusammengesetzter Schlüssel zusammensetzt.
* **applicableIf (Zeichenfolge)**: Mit diesem Attribut können Sie den Schlüssel optional machen. Sie definiert die Bedingung, gemäß der die Schlüsseldefinition angewendet wird. Dieses Attribut erhält einen XTK-Ausdruck.
* **Intern (Boolesch)**: Wenn es aktiviert ist, informiert dieses Attribut Adobe Campaign darüber, dass der Schlüssel „primary“ ist.
* **label (Zeichenfolge)**: Bezeichnung des Schlüssels.
* **name (MNTOKEN)**: Interner Name des Schlüssels.
* **noDbIndex (Boolescher Wert)**: Wenn er aktiviert ist (noDbIndex=„true„), wird das Feld, das dem Schlüssel entspricht, nicht indiziert.

## Beispiele {#examples-------}

Deklaration eines zusammengesetzten Schlüssels, der die Leerung des Felds &quot;@expr“ oder „Alias“ zulässt:

```
<key name="node" allowEmptyPart="true">
  <keyfield xpath="@expr"/>
   <keyfield xpath="@alias"/>
 </key>
```

Deklaration eines Primärschlüssels im Feld „Name“ vom Typ STRING in einer `<srcschema>` und der entsprechenden SQL-Abfrage:

```
 
<key name="PrimaryKey" internal="true">  
  <keyfield xpath="@name"/>
</key>

CREATE UNIQUE INDEX Schema_PrimaryKey ON Schema(sName);
```
