---
solution: Campaign Classic
product: campaign
title: Elemente und Attribute
description: Elemente und Attribute
audience: configuration
content-type: reference
topic-tags: schema-reference
translation-type: tm+mt
source-git-commit: 922257b157f8d76d6e703b0510ff689d1aa4d067
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 2%

---


# dbindex-Element {#dbindex--element}

## Inhaltsmodell {#content-model-3}

dbindex:==keyfield

## Attribute {#attributes-3}

* @_operation (Zeichenfolge)
* @applyIf (Zeichenfolge)
* @label (Zeichenfolge)
* @name (MNTOKEN)
* @unique (boolean)

## Eltern {#parents-3}

`<element>`

## Kinder {#children-3}

`<keyfield>`

## Beschreibung {#description-3}

Mit diesem Element können Sie einen mit einer Tabelle verknüpften Index definieren.

## Verwendung und Kontext der Verwendung von {#use-and-context-of-use-3}

Es ist möglich, mehrere Indizes zu definieren. Ein Index kann auf ein oder mehrere Felder der Tabelle verweisen. Die Indexdeklaration entspricht in der Regel der Definition des Hauptelements Schema.

Die Reihenfolge der `<keyfield>`-Elemente, die in einem `<dbindex>` definiert sind, ist sehr wichtig. Das erste `<keyfield>` muss das Indexierungskriterium sein, auf dem die Abfragen hauptsächlich basieren.

Der Name des Indexes in der Datenbank wird durch Verkettung des Namens der Tabelle und des Indexnamens berechnet. Beispiel: Tabellenname &quot;Beispiel&quot;, Namensraum &quot;Cus&quot;, Indexname &quot;MyIndex&quot;-> Name des Indexfelds bei der Indexerstellung bei der Abfrage: &quot;CusSample_myIndex&quot;.

## Attributbeschreibung {#attribute-description-3}

* **_operation (string)**: definiert den Typ des Schreibens in der Datenbank.

   Dieses Attribut wird hauptsächlich beim Erweitern von vordefinierten Schemas verwendet.

   Barrierefreie Werte sind:

   * &quot;none&quot;: Aussöhnung allein. Das bedeutet, dass Adobe Campaign das Element wiederherstellt, ohne es zu aktualisieren, oder einen Fehler erzeugt, wenn es nicht vorhanden ist.
   * &quot;insertOrUpdate&quot;: mit Einfügen aktualisieren. Das bedeutet, dass Adobe Campaign das Element aktualisiert oder erstellt, wenn es nicht vorhanden ist.
   * &quot;insert&quot;: Einfügen. Das bedeutet, dass Adobe Campaign das Element einfügt, ohne zu prüfen, ob es vorhanden ist.
   * &quot;update&quot;: aktualisieren. Das bedeutet, dass Adobe Campaign das Element aktualisiert oder einen Fehler erzeugt, wenn es nicht vorhanden ist.
   * &quot;delete&quot;: löschen. Das bedeutet, dass Adobe Campaign Elemente wiederherstellt und löscht.

* **applyIf (Zeichenfolge)**: Bedingung für die Berücksichtigung des Indexes - erhält einen XTK-Ausdruck.
* **label (Zeichenfolge)**: Indexbeschriftung.
* **name (MNTOKEN)**: eindeutiger Indexname.
* **eindeutig (boolean)**: Wenn diese Option aktiviert ist (@unique=&quot;true&quot;), garantiert das Attribut die Eindeutigkeit des Indexes in allen Feldern.

## Beispiele {#examples-3}

Erstellen eines Indexes im Feld &quot;id&quot;. (das Attribut &quot;@unique&quot;auf den Triggern `<dbindex>`, die das SQL-Schlüsselwort &quot;UNIQUE&quot;hinzufügen, wenn der Index in der Abfrage erstellt wird).

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

Erstellen eines Composite-Index in den Feldern &quot;@mail&quot;und &quot;@phoneNumber&quot;:

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
