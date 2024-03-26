---
product: campaign
title: Elemente und Attribute - Dbindex-Element
description: dbindex-Element
feature: Schema Extension
exl-id: d7d1e427-12e0-4f07-9e01-d184dbe2ebf1
source-git-commit: fd5e4bbc87a48f029a09b14ab1d927b9afe4ac52
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 1%

---

# dbindex-Element {#dbindex--element}

![](../../../assets/v7-only.svg)

## Inhaltsmodell {#content-model-3}

dbindex:==keyfield

## Attribute {#attributes-3}

* @_operation (string)
* @applyIf (string)
* @label (string)
* @name (MNTOKEN)
* @unique (boolean)

## Eltern {#parents-3}

`<element>`

## Untergeordnetes Element {#children-3}

`<keyfield>`

## Beschreibung {#description-3}

Mit diesem Element können Sie einen mit einer Tabelle verknüpften Index definieren.

## Verwendung und Verwendungskontext {#use-and-context-of-use-3}

Es ist möglich, mehrere Indizes zu definieren. Ein Index kann auf ein oder mehrere Felder der Tabelle verweisen. Die Indexdeklaration folgt in der Regel der Definition des Hauptschemaelements.

Die Reihenfolge der `<keyfield>` -Elemente, die in `<dbindex>` ist sehr wichtig. Die erste `<keyfield>` muss das Indexierungskriterium sein, auf dem die Abfragen hauptsächlich basieren.

Der Name des Index in der Datenbank wird durch Verkettung des Tabellennamens und des Indexnamens berechnet. Beispiel: Tabellenname &quot;Sample&quot;, Namespace &quot;Cus&quot;, Indexname &quot;MyIndex&quot;-> Name des Indexfelds bei der Indexerstellung. Abfrage: &quot;CusSample_myIndex&quot;.

## Attributbeschreibung {#attribute-description-3}

* **_operation (string)**: definiert den Schreibtyp in der Datenbank.

  Dieses Attribut wird hauptsächlich bei der Erweiterung von nativen Schemata verwendet.

  Die verfügbaren Werte sind:

   * &quot;none&quot;: Abstimmung allein. Das bedeutet, dass Adobe Campaign das Element wiederherstellt, ohne es zu aktualisieren, oder einen Fehler erzeugt, wenn es nicht vorhanden ist.
   * &quot;insertOrUpdate&quot;: Update mit Einfügung. Das bedeutet, dass Adobe Campaign das Element aktualisiert oder erstellt, falls es nicht vorhanden ist.
   * &quot;insert&quot;: insert. Das bedeutet, dass Adobe Campaign das Element einfügt, ohne zu überprüfen, ob es vorhanden ist.
   * &quot;update&quot;: update. Das bedeutet, dass Adobe Campaign das Element aktualisiert oder einen Fehler erzeugt, wenn es nicht vorhanden ist.
   * &quot;Löschen&quot;: Löschen. Dies bedeutet, dass Adobe Campaign Elemente wiederherstellt und löscht.

* **applyIf (string)**: Bedingung für die Berücksichtigung des Index - empfängt einen XTK-Ausdruck.
* **label (string)**: Indexbezeichnung.
* **name (MNTOKEN)**: eindeutiger Indexname.
* **unique (boolean)**: Wenn diese Option aktiviert ist (@unique=&quot;true&quot;), garantiert das Attribut die Eindeutigkeit des Index in allen Feldern.

## Beispiele {#examples-3}

Erstellung eines Index im Feld &quot;id&quot;. (Attribut &quot;@unique&quot; im `<dbindex>` Element-Trigger, die das SQL-Schlüsselwort &quot;UNIQUE&quot; hinzufügen, wenn der Index in der Datenbank erstellt wird (Abfrage).

```
<element label="Sample" name="Sample">
  <dbindex name="myIndex" label="My index on the ID field" unique="true" applicableIf="HasPackage('nms:social')">
      <keyfield xpath="@id"/>
  </dbindex>
    <attribute name="id" type="long"/>
</element>          
```

```
ALTER TABLE CusSample ADD iSampleId INTEGER;
UPDATE CusSample SET iSampleId = 0;
ALTER TABLE CusSample ALTER COLUMN iSampleId SET Default 0;
ALTER TABLE CusSample ALTER COLUMN iSampleId SET NOT NULL; 
CREATE UNIQUE INDEX CusSample_myIndex ON CusSample(iSampleId);
```

Erstellung eines zusammengesetzten Index für die Felder &quot;@mail&quot; und &quot;@phoneNumber&quot;:

```
<element label="NewSchemaUser" name="NewSchemaUser">
  <dbindex name="myIndex" label="My composite index">
         <keyfield xpath="@email"/>
         <keyfield xpath="@phone"/>
  </dbindex>
  
  <attribute name="email" type="string"/>
  <attribute name="phone" type="string"/>
</element>      
```

```
CREATE INDEX DocNewSchemaUser_myIndex ON DocNewSchemaUser(sEmail, sPhone);
```
