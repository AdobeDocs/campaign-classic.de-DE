---
product: campaign
title: Elemente und Attribute - Attributelement
description: Elemente und Attribute
feature: Schema Extension
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: e4d34f56-b065-4dce-8974-11dc2767873a
source-git-commit: 728848eab059fc669c241346a2ff1feebd79222c
workflow-type: tm+mt
source-wordcount: '1573'
ht-degree: 1%

---

# Attributelement {#attribute--element}

![](../../../assets/v7-only.svg)

## Inhaltsmodell {#content-model}

attribute:==help

## Attribute {#attributes}

_operation (String), Advanced (Boolesch), ApplicableIf (String), autoIncrement (Boolesch), Belonto (String), dataPolicy (String), dbEnum (String), DefOnDuplicate (Boolesch), Default (String), desc (String), edit (String), enum (String), expr (String), Feature (String), featureDate (Boolesch), img (String), inout (String), label (String), length (String), lokalisierbar (Boolesch), Name (MTOKEN), notNull (boolean), pkgStatus (string), ref (string), required (boolean), sql (boolean), sqlDefault (string), sqlname (string), sqltable (string), target (MNTOKEN), template (string), translatedDefault (string), translatedExpr (string), type (MNTOKEN), user (boolean), userEnum (string), visibleIf (string), xml (boolean)

## Übergeordnete Elemente {#parents}

`<element>`

## Untergeordnetes Element {#children}

`<help>`

## Beschreibung {#description}

Mit `<attribute>` können Sie ein Feld in der Datenbank definieren.

## Verwendung und Nutzungskontext {#use-and-context-of-use}

`<attribute>` müssen in einem `<element>` deklariert werden.

Die Reihenfolge, in der `<attribute>` Elemente in einer `<srcschema>` definiert werden, hat keinen Einfluss auf die Sequenz der Felderstellung in der Datenbank. Die Erstellungssequenz ist alphabetisch.

## Attributbeschreibung {#attribute-description}

* **_operation (Zeichenfolge)**: definiert den Typ des Schreibens in der Datenbank.

  Dieses Attribut wird hauptsächlich bei der Erweiterung von vordefinierten Schemata verwendet.

  Folgende Werte sind verfügbar:

   * „none“: Aussöhnung allein. Dies bedeutet, dass Adobe Campaign das Element wiederherstellt, ohne es zu aktualisieren oder einen Fehler zu erzeugen, wenn es nicht existiert.
   * „insertOrUpdate“: Mit dem Einfügen aktualisieren. Das bedeutet, dass Adobe Campaign das Element aktualisiert oder erstellt, wenn es nicht vorhanden ist.
   * „INSERT“: Einfügen. Dies bedeutet, dass Adobe Campaign das Element einfügt, ohne zu überprüfen, ob es vorhanden ist.
   * „UPDATE“: Aktualisieren. Das bedeutet, dass Adobe Campaign das Element aktualisiert oder einen Fehler generiert, wenn es nicht vorhanden ist.
   * „delete“: Löschung. Dies bedeutet, dass Adobe Campaign Elemente wiederherstellt und löscht.

* **Erweitert (Boolesch)**: Wenn diese Option aktiviert ist (@advanced=„true„), können Sie das Attribut in der Liste der verfügbaren Felder ausblenden, die zum Konfigurieren einer Liste in einem Formular verfügbar sind.
* **applicableIf (Zeichenfolge)**: Mit diesem Attribut können Sie Felder optional machen. Das `<attribute>` Element wird bei der Aktualisierung der Datenbank berücksichtigt, wenn die Einschränkung eingehalten wird. „applicableIf“ empfängt einen XTK-Ausdruck.
* **autoIncrement (Boolesch)**: Wenn diese Option aktiviert ist, wird das Feld zu einem Zähler. Auf diese Weise können Sie einen Wert (hauptsächlich IDs) inkrementieren. (externe Verwendung)
* **BelongsTo (Zeichenfolge)**: Nimmt den Namen und den Namespace der Tabelle, die das Feld freigibt, und füllt das Schema, in dem das Attribut deklariert wird. (nur in einem `<schema>` verwendet).
* **dataPolicy (Zeichenfolge)**: Ermöglicht es Ihnen, Validierungseinschränkungen für Werte anzugeben, die im SQL- oder XML-Feld zulässig sind. Die Werte für dieses Attribut sind:

   * „none“: kein Wert
   * „smartCase“: Großbuchstaben der ersten Buchstaben
   * „lowercase“: nur Kleinbuchstaben
   * „upperCase“: Großbuchstaben
   * „email“: E-Mail-Adresse
   * „Telefon“: Telefonnummer
   * „identifier“: Kennungsname
   * „resIdentifier“: Dateiname

* **dbEnum (Zeichenfolge)**: Empfängt den internen Namen einer „geschlossenen“ Auflistung. Die Auflistungswerte müssen in der `<srcschema>` definiert werden.
* **defOnDuplicate (Boolescher Wert)**: Wenn dieses Attribut aktiviert wird, wird beim Duplizieren eines Datensatzes der Standardwert (definiert in @default) automatisch erneut auf den Datensatz angewendet.
* **default (Zeichenfolge)** ermöglicht die Definition des Werts des Standardfelds (Aufruf einer Funktion, Standardwert). Dieses Attribut erhält einen XTK-Ausdruck.
* **desc (Zeichenfolge)**: Hiermit können Sie eine Beschreibung des Attributs einfügen. Diese Beschreibung wird verwendet, um zu verstehen, was das -Element ist und wofür es verwendet wird. Sie können sie im Formular anzeigen.
* **edit (Zeichenfolge)** Dieses Attribut gibt den Typ der Eingabe an, die in dem mit dem Schema verknüpften Formular verwendet wird.
* **enum (Zeichenfolge)**: Empfängt den Namen der mit dem Feld verknüpften Auflistung. Die Auflistung kann in dasselbe Schema oder in ein Remote-Schema eingefügt werden.
* **expr (Zeichenfolge)**: Definiert einen Ausdruck für die Feldvorberechnung. Dieses Attribut empfängt einen Xpath oder einen XTK-Ausdruck.
* **Feature (String)** definiert ein Merkmalsfeld: Diese Felder werden zur Erweiterung der Daten in einer vorhandenen Tabelle verwendet, jedoch mit Speicherung in einer Anhang-Tabelle. Akzeptierte Werte sind:

   * „Freigegeben“: Der Inhalt wird pro Datentyp in einer freigegebenen Tabelle gespeichert
   * „Dediziert“: Der Inhalt wird in einer dedizierten Tabelle gespeichert

  SQL-Merkmalstabellen werden automatisch auf Basis des Merkmalstyps erstellt:

   * Dediziert: `Ft_[name_of_the_schema_containing_the_characteristic]_[name_of_the_characteristic]`
   * Freigegeben: `Ft_[type_of_key_of_the_schema_containing_the_characteristic]_[type_of_the_characteristic]`

  Es gibt zwei Arten von Merkmalsfeldern: einfache oà<sup>1</sup> Felder, in denen ein einzelner Wert für das Merkmal zulässig ist, und oà<sup>1</sup> Multiple-Choice-Felder, in denen das Merkmal mit einem Sammlungselement verknüpft ist, das mehrere Werte enthalten kann.

  Wenn ein Merkmal in einem Schema definiert ist, muss dieses Schema einen Hauptschlüssel haben, der auf einem einzelnen Feld basiert (zusammengesetzte Schlüssel sind nicht zulässig).

* **featureDate (boolesch)**: Mit dem Merkmalsfeld &quot;@feature“ verknüpftes Attribut. Wenn der Wert „true“ lautet, können Sie damit herausfinden, wann der Wert zuletzt aktualisiert wurde.
* **img (Zeichenfolge)**: Hiermit können Sie einen Pfad für ein Bild definieren, das mit einem Feld verknüpft ist (Namespace + Bildname) (Beispiel: img=„cus:mypicture.jpg„). Physisch muss das Bild auf den Anwendungsserver importiert werden.
* **label (Zeichenfolge)**: Der dem Feld zugeordnete Titel, der hauptsächlich für die Benutzerin oder den Benutzer in der Benutzeroberfläche bestimmt ist. Auf diese Weise können Sie Namensbeschränkungen vermeiden.
* **length (Zeichenfolge)**: max. Anzahl der Zeichen für einen Wert des SQL-Feldes vom Typ „Zeichenfolge“. Wenn das Attribut &quot;@length“ nicht angegeben ist, erstellt Adobe Campaign automatisch ein Feld für 255 Zeichen.
* **Localizable (Boolescher Wert)**: Wenn es aktiviert ist, weist dieses Attribut das Sammlungs-Tool an, den Wert des Attributs &quot;@label“ für die Übersetzung abzurufen (interne Verwendung).
* **name (MNTOKEN)**: Name des Attributs, das mit dem Namen des Felds in der Tabelle übereinstimmt. Der Wert des Attributs &quot;@name“ muss kurz sein, vorzugsweise in englischer Sprache, und den XML-Benennungsbeschränkungen entsprechen.

  Wenn das Schema in die Datenbank geschrieben wird, werden dem Feldnamen von Adobe Campaign automatisch Präfixe hinzugefügt:

   * „i“: Präfix für den Typ „integer“.
   * „D“: Präfix für den Typ „double“.
   * „s“: Präfix für den String-Typ.
   * „ts“: Präfix für den Typ „date“.

  Um den Namen des Felds in der Tabelle vollständig zu definieren, verwenden Sie die Option &quot;@sqlname“ beim Definieren eines Attributs.

* **notNull (boolesch)**: ermöglicht es Ihnen, das Verhalten von Adobe Campaign in Bezug auf die Verwaltung von NULL-Datensätzen in der Datenbank neu zu definieren. Standardmäßig sind numerische Felder nicht null und Felder vom Typ Zeichenfolge und Datum können null sein.
* **pkgStatus (Zeichenfolge)**: Beim Package-Export werden Werte abhängig vom Wert des &quot;@pkgStatus“ berücksichtigt:

   * „Always“: immer vorhanden
   * „Nie“: Nie vorhanden
   * „Standardwert (oder nichts)“: Der Wert wird exportiert, es sei denn, es handelt sich um den Standardwert oder um ein nicht internes Feld, das mit anderen Instanzen nicht kompatibel wäre.

* **ref (Zeichenfolge)** Dieses Attribut definiert einen Verweis auf ein `<attribute>`, das von mehreren Schemata gemeinsam genutzt wird (Definition-Factoring). Die Definition wird nicht in das aktuelle Schema kopiert.
* **required (boolean)**: Wenn dieses Attribut aktiviert ist (@required=„true„), wird das Feld in der Benutzeroberfläche hervorgehoben. Die Beschriftung des Felds wird in den Formularen rot angezeigt.
* **sql (Boolescher Wert)**: Wenn dieses Attribut aktiviert ist (@sql=„true„), wird die Speicherung des SQL-Attributs erzwungen, auch wenn das Element, das das Attribut enthält, die Eigenschaft xml=„true“ aufweist.
* **sqlDefault (Zeichenfolge)**: Mit diesem Attribut können Sie den Standardwert definieren, der bei der Aktualisierung der Datenbank berücksichtigt wird, wenn das Attribut @notNull aktiviert ist. Wenn dieses Attribut nach der Erstellung des Attributs hinzugefügt wird, ändert sich das Schemaverhalten auch bei den neuen Datensätzen nicht. Um das Schema zu ändern und den Wert für neue Datensätze zu aktualisieren, müssen Sie das Attribut löschen und erneut erstellen.
* **sqlname (Zeichenfolge)**: des Felds bei der Tabellenerstellung. Wenn @sqlname nicht angegeben ist, wird standardmäßig der Wert des Attributs &quot;@name“ verwendet. Wenn das Schema in die Datenbank geschrieben wird, werden Präfixe je nach Feldtyp automatisch hinzugefügt.
* **template (Zeichenfolge)** Dieses Attribut definiert einen Verweis auf ein `<attribute>`, das von mehreren Schemata gemeinsam genutzt wird. Die Definition wird automatisch in das aktuelle Schema kopiert.
* **translatedDefault (Zeichenfolge)**: Wenn das Attribut &quot;@default“ gefunden wird, können Sie mit dem Attribut &quot;@translatedDefault“ einen Ausdruck neu definieren, sodass er mit dem in @default definierten Ausdruck übereinstimmt, der vom Übersetzungs-Tool erfasst werden soll (interne Verwendung).
* **translatedExpr (Zeichenfolge)**: Wenn ein Attribut &quot;@expr“ vorhanden ist, können Sie mit dem Attribut &quot;@translatedExpr“ einen Ausdruck neu definieren, damit er mit dem in @expr definierten Ausdruck übereinstimmt, der vom Übersetzungs-Tool erfasst werden soll (interne Verwendung).
* **type (MNTOKEN)**: Feldtyp.

  Feldtypen sind generisch. Je nach installiertem Datenbanktyp ändert Adobe Campaign den definierten Typ in einen Wert, der für die bei der Strukturaktualisierung installierte Datenbank spezifisch ist.

  Liste der verfügbaren Typen:

   * BELIEBIGE
   * Eimer
   * Klecks
   * Boolesch
   * Byte
   * CDATA
   * datetime
   * datetimets
   * datetimenotz
   * date
   * double
   * Aufzählung
   * float
   * HTML
   * int64
   * link
   * lang
   * Memo
   * MNTOKEN
   * Prozent
   * Primärschlüssel
   * Short
   * Zeichenfolge
   * time
   * timespan
   * uuid

  Wenn das Attribut &quot;@type“ leer gelassen wird, verknüpft Adobe Campaign standardmäßig eine Zeichenfolge (STRING) mit einer Länge von 100 mit dem Feld.

  Wenn es sich um ein Feld vom Typ STRING handelt und der Name des Felds nicht durch das Vorhandensein des Attributs &quot;@sqlname“ angegeben wird, wird dem Namen des Felds in der Datenbank automatisch ein „s“ vorangestellt. Dieser Betriebsmodus ähnelt den Feldern vom Typ GANZZAHL (i), DOPPELT (d) und DATUM (ts).

* **userEnum (Zeichenfolge)**: Empfängt den internen Namen einer „offenen“ Auflistung. Die Werte der Auflistung können vom Benutzer in der -Schnittstelle definiert werden.
* **visibleIf (Zeichenfolge)**: Definiert eine Bedingung in Form eines XTK-Ausdrucks, um das Attribut ein- oder auszublenden.

  >[!IMPORTANT]
  >
  >Das Attribut ist ausgeblendet, aber auf seine Daten kann weiterhin zugegriffen werden.

* **xml (boolesch)**: Wenn diese Option aktiviert ist, verfügen die Werte des Felds nicht über ein verknüpftes SQL-Feld. Adobe Campaign erstellt ein Textfeld vom Typ „mData“ für die Speicherung von Datensätzen. Das bedeutet, dass es bei diesen Feldern keine Filterung oder Sortierung gibt.

### Beispiele {#examples}

Beispiel für Auflistungswerte, deren Werte in der Datenbank gespeichert sind:

```
    <enumeration name="myEnum">
       <value name="One" value="1"/>
       <value name="Two" value="2"/>
    </enumeration>

    <element label="Sample" name="Sample">
       <attribute dbEnum="myEnum" length="100" name="Number" required="true" type="string"/>
    </element>     
```

Deklaration eines XML-Feldes mit &quot;@datapolicy“:

```
<attribute dataPolicy="phone" desc="Mobile number" label="Mobile"
     length="32" name="mobilePhone" sqlname="sMobilePhone" type="string"/>
```

Beispiel mit einem &quot;@applicableIf“: Das Attribut „contains“ wird nur erstellt, wenn die Anzahl der Länder größer als 20 ist.

```
<attribute length="100" name="Continent" type="string" applicableIf="@country > 20"/>
```

Beispiel mit &quot;@feature“ vom Typ „shared“:

```
<attribute name="field1" label="Field 1" type="long" feature="shared"/>
<attribute name="field1" label="Field 1" type="long" feature="shared" sqlname="126" sqltable="Ft_Content_Long"/>
```

Beispiel mit &quot;@feature“ vom Typ „dediziert“:

```
<attribute name="field1" label="Field 1" type="long" feature="dedicated"/>
<attribute name="field1" label="Field 1" type="long" feature="dedicated" sqlname="sField1" sqltable="Ft_recipient_field1"/>
```
