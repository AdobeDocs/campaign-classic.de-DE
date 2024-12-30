---
product: campaign
title: Elemente und Attribute - dbindex-Element
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

dbindex:==keyField

## Attribute {#attributes-3}

* @_operation (Zeichenfolge)
* @applicableIf (Zeichenfolge)
* @label (Zeichenfolge)
* @name (MNTOKEN)
* @unique (Boolesch)

## Übergeordnete Elemente {#parents-3}

`<element>`

## Untergeordnetes Element {#children-3}

`<keyfield>`

## Beschreibung {#description-3}

Mit diesem Element können Sie einen mit einer Tabelle verknüpften Index definieren.

## Verwendung und Nutzungskontext {#use-and-context-of-use-3}

Es ist möglich, mehrere Indizes zu definieren. Ein Index kann auf ein oder mehrere Felder der Tabelle verweisen. Die Indexdeklaration folgt normalerweise der Definition des Hauptschemaelements.

Die Reihenfolge der in einem `<dbindex>` definierten `<keyfield>` ist sehr wichtig. Die erste `<keyfield>` muss das Indexierungskriterium sein, auf dem die Abfragen hauptsächlich basieren.

Der Name des Index in der Datenbank wird berechnet, indem der Tabellenname und der Indexname verkettet werden. Beispiel: Tabellenname „Sample“, Namespace „Cus“, Indexname „MyIndex“-> Name des Indexfelds während der Indexerstellungsabfrage: „CusSample_myIndex“.

## Attributbeschreibung {#attribute-description-3}

* **_operation (Zeichenfolge)**: definiert den Typ des Schreibens in der Datenbank.

  Dieses Attribut wird hauptsächlich bei der Erweiterung von vordefinierten Schemata verwendet.

  Folgende Werte sind verfügbar:

   * „none“: Aussöhnung allein. Dies bedeutet, dass Adobe Campaign das Element wiederherstellt, ohne es zu aktualisieren oder einen Fehler zu erzeugen, wenn es nicht existiert.
   * „insertOrUpdate“: Mit dem Einfügen aktualisieren. Das bedeutet, dass Adobe Campaign das Element aktualisiert oder erstellt, wenn es nicht vorhanden ist.
   * „INSERT“: Einfügen. Dies bedeutet, dass Adobe Campaign das Element einfügt, ohne zu überprüfen, ob es vorhanden ist.
   * „UPDATE“: Aktualisieren. Das bedeutet, dass Adobe Campaign das Element aktualisiert oder einen Fehler generiert, wenn es nicht vorhanden ist.
   * „delete“: Löschung. Dies bedeutet, dass Adobe Campaign Elemente wiederherstellt und löscht.

* **applicableIf (Zeichenfolge)**: Bedingung für die Berücksichtigung des Index - empfängt einen XTK-Ausdruck.
* **label (Zeichenfolge)**: Indexbezeichnung.
* **name (MNTOKEN)**: eindeutiger Indexname.
* **unique (boolean)**: Wenn diese Option aktiviert ist (@unique=„true„), garantiert das Attribut die Eindeutigkeit des Index in allen seinen Feldern.

## Beispiele {#examples-3}

Erstellung eines Index für das Feld „id“ (Das Attribut &quot;@unique“ im `<dbindex>`-Element Trigger, die das SQL-Schlüsselwort „UNIQUE“ hinzufügen, wenn der Index in der Datenbank erstellt wird (Abfrage)).

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

Erstellen eines zusammengesetzten Index für die Felder &quot;@mail“ und &quot;@phoneNumber“:

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
