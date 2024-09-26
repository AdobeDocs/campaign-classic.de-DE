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

# attribute element {#attribute--element}

![](../../../assets/v7-only.svg)

## Inhaltsmodell {#content-model}

attribute:==help

## Attribute {#attributes}

_operation (string), advanced (boolean), applyIf (string), autoIncrement (boolean), gehörtTo (string), dataPolicy (string), dbEnum (string), defOnDuplicate (boolean), default (string), desc (string), edit (string), enum (string), expr (string), feature (string), Date (boolean), img (string), inout (string), label (string), length (string), localizable (boolean), name (MNTOKEN), notNull (boolean), pkgStatus (string), ref (string), required (boolean), sql (boolean), sqlDefault (string), sqlname (string), sqltable (string), target (MNTOKEN), template (string), translationDefault (string), translatedExpr (string), type (MNTOKEN), user (boolean), userEnum (string), visibleIf (string), xml (boolean).

## Eltern {#parents}

`<element>`

## Untergeordnetes Element {#children}

`<help>`

## Beschreibung {#description}

Mit den Elementen `<attribute>` können Sie ein Feld in der Datenbank definieren.

## Verwendung und Verwendungskontext {#use-and-context-of-use}

`<attribute>` -Elemente müssen in einem `<element>` -Element deklariert werden.

Die Reihenfolge, in der `<attribute>` -Elemente in einem `<srcschema>` definiert sind, wirkt sich nicht auf die Reihenfolge der Felderstellung in der Datenbank aus. Die Erstellungssequenz ist alphabetisch.

## Attributbeschreibung {#attribute-description}

* **_operation (string)**: definiert den Schreibtyp in der Datenbank.

  Dieses Attribut wird hauptsächlich bei der Erweiterung von nativen Schemata verwendet.

  Die verfügbaren Werte sind:

   * &quot;none&quot;: Abstimmung allein. Das bedeutet, dass Adobe Campaign das Element wiederherstellt, ohne es zu aktualisieren, oder einen Fehler erzeugt, wenn es nicht vorhanden ist.
   * &quot;insertOrUpdate&quot;: Update mit Einfügung. Das bedeutet, dass Adobe Campaign das Element aktualisiert oder erstellt, falls es nicht vorhanden ist.
   * &quot;insert&quot;: insert. Das bedeutet, dass Adobe Campaign das Element einfügt, ohne zu überprüfen, ob es vorhanden ist.
   * &quot;update&quot;: update. Das bedeutet, dass Adobe Campaign das Element aktualisiert oder einen Fehler erzeugt, wenn es nicht vorhanden ist.
   * &quot;Löschen&quot;: Löschen. Dies bedeutet, dass Adobe Campaign Elemente wiederherstellt und löscht.

* **advanced (boolesch)**: Wenn diese Option aktiviert ist (@advanced=&quot;true&quot;), können Sie das Attribut in der Liste der verfügbaren Felder ausblenden, auf die zum Konfigurieren einer Liste in einem Formular zugegriffen werden kann.
* **applyIf (string)**: Mit diesem Attribut können Sie Felder optional machen. Das Element `<attribute>` wird bei der Aktualisierung der Datenbank berücksichtigt, wenn die Einschränkung eingehalten wird. &quot;applyIf&quot;erhält einen XTK-Ausdruck.
* **autoIncrement (boolean)**: Wenn diese Option aktiviert ist, wird das Feld zu einem Zähler. Auf diese Weise können Sie einen Wert (meist IDs) erhöhen. (externe Verwendung)
* **gehörtTo (Zeichenfolge)**: Nimmt den Namen und den Namespace der Tabelle, die das Feld gemeinsam verwendet, und füllt das Schema aus, in dem das Attribut deklariert wird. (wird nur in einem `<schema>` verwendet).
* **dataPolicy (string)**: Ermöglicht die Angabe von Genehmigungsbeschränkungen für die im SQL- oder XML-Feld zulässigen Werte. Die Werte für dieses Attribut sind:

   * &quot;none&quot;: kein Wert
   * &quot;smartCase&quot;: erste Buchstaben Großbuchstaben
   * &quot;lowerCase&quot;: Kleinbuchstaben
   * &quot;upperCase&quot;: Großbuchstaben
   * &quot;email&quot;: email address
   * &quot;phone&quot;: Telefonnummer
   * &quot;identifier&quot;: Identifikationsname
   * &quot;resIdentifier&quot;: Dateiname

* **dbEnum (string)**: empfängt den internen Namen einer &quot;geschlossenen&quot; Auflistung. Die Auflistungswerte müssen im `<srcschema>` definiert werden.
* **defOnDuplicate (boolesch)**: Wenn dieses Attribut aktiviert ist, wird bei der Duplizierung eines Datensatzes der Standardwert (definiert in @default) automatisch erneut auf den Datensatz angewendet.
* **default (string)**: Ermöglicht die Definition des Werts im Standardfeld (Aufruf einer Funktion, Standardwert). Dieses Attribut erhält einen XTK-Ausdruck.
* **desc (string)**: ermöglicht das Einfügen einer Beschreibung des Attributs. Diese Beschreibung dient dazu, zu verstehen, wofür das Element verwendet wird und wofür es verwendet wird. Sie können es im Formular anzeigen.
* **edit (string)**: Dieses Attribut gibt den Typ der Eingabe an, die in dem mit dem Schema verknüpften Formular verwendet wird.
* **enum (string)**: empfängt den Namen der mit dem Feld verknüpften Auflistung. Die Auflistung kann im selben Schema oder in ein Remote-Schema eingefügt werden.
* **expr (string)**: definiert einen Ausdruck für die Feldberechnung. Dieses Attribut empfängt einen Xpath oder einen XTK-Ausdruck.
* **feature (string)**: definiert ein Merkmalfeld: Diese Felder werden zum Erweitern der Daten in einer vorhandenen Tabelle verwendet, jedoch mit Speicherung in einer Anhang-Tabelle. Zulässige Werte sind:

   * &quot;shared&quot;: Der Inhalt wird in einer freigegebenen Tabelle je Datentyp gespeichert.
   * &quot;dediziert&quot;: Der Inhalt wird in einer speziellen Tabelle gespeichert

  SQL-Eigenschaftstabellen werden automatisch basierend auf dem charakteristischen Typ erstellt:

   * dediziert: `Ft_[name_of_the_schema_containing_the_characteristic]_[name_of_the_characteristic]`
   * shared: `Ft_[type_of_key_of_the_schema_containing_the_characteristic]_[type_of_the_characteristic]`

  Es gibt zwei Arten von Eigenschaftenfeldern: einfache à<sup>1</sup> -Felder, bei denen ein einzelner Wert für das Merkmal autorisiert ist, und Multiple-Choice-Felder, bei denen das Merkmal mit einem Kollektionselement verknüpft ist, das mehrere Werte enthalten kann.<sup></sup>

  Wenn ein Merkmal in einem Schema definiert ist, muss dieses Schema über einen Hauptschlüssel verfügen, der auf einem einzelnen Feld basiert (zusammengesetzte Schlüssel sind nicht autorisiert).

* **featureDate (boolean)**: Attribut, das mit dem Feld &quot;@feature&quot;verknüpft ist. Wenn der Wert &quot;true&quot;ist, können Sie feststellen, wann der Wert zuletzt aktualisiert wurde.
* **img (string)**: ermöglicht die Angabe eines Pfads für ein Bild, das mit einem Feld verknüpft ist (namespace + image name) (Beispiel: img=&quot;cus:mypicture.jpg&quot;). Das Bild muss physisch auf den Anwendungsserver importiert werden.
* **label (string)**: mit dem Feld verknüpfte Bezeichnung, die hauptsächlich für den Benutzer in der Benutzeroberfläche bestimmt ist. Damit können Sie Benennungsbeschränkungen vermeiden.
* **length (string)**: max. Anzahl der Zeichen für einen Wert des SQL-Felds vom Typ &quot;String&quot;. Wenn das Attribut &quot;@length&quot;nicht angegeben ist, erstellt Adobe Campaign automatisch ein Feld für 255 Zeichen.
* **lokalisierbar (boolesch)**: Wenn es aktiviert ist, weist dieses Attribut das Sammlungs-Tool an, den Wert des Attributs &quot;@label&quot;für die Übersetzung abzurufen (interne Verwendung).
* **name (MNTOKEN)**: Name des Attributs, das mit dem Namen des Felds in der Tabelle übereinstimmt. Der Wert des Attributs &quot;@name&quot;muss kurz sein, vorzugsweise auf Englisch, und den XML-Benennungsbeschränkungen entsprechen.

  Beim Schreiben des Schemas in die Datenbank werden dem Feldnamen von Adobe Campaign automatisch Präfixe hinzugefügt:

   * &quot;i&quot;: Präfix für den Typ &quot;integer&quot;.
   * &quot;d&quot;: Präfix für den Typ &quot;double&quot;.
   * &quot;s&quot;: Präfix für den Zeichenfolgentyp.
   * &quot;ts&quot;: Präfix für den Typ &quot;Datum&quot;.

  Um den Namen des Felds in der Tabelle vollständig zu definieren, verwenden Sie beim Definieren eines Attributs die Option &quot;@sqlname&quot;.

* **notNull (boolesch)**: ermöglicht Ihnen, das Verhalten von Adobe Campaign bezüglich der Verwaltung von NULL-Datensätzen in der Datenbank neu zu definieren. Numerische Felder sind standardmäßig nicht null und Felder vom Typ Zeichenfolge und Datum können null sein.
* **pkgStatus (string)**: Bei Package-Exporten werden Werte in Abhängigkeit vom Wert von &quot;@pkgStatus&quot;berücksichtigt:

   * &quot;always&quot;: immer vorhanden
   * &quot;never&quot;: niemals präsent
   * &quot;default (oder nichts)&quot;: Der Wert wird exportiert, es sei denn, es handelt sich um den Standardwert oder um ein internes Feld, das nicht mit anderen Instanzen kompatibel ist.

* **ref (string)**: Dieses Attribut definiert einen Verweis auf ein `<attribute>` -Element, das von mehreren Schemas gemeinsam verwendet wird (Definition-Factoring). Die Definition wird nicht in das aktuelle Schema kopiert.
* **erforderlich (boolesch)**: Wenn dieses Attribut aktiviert ist (@required=&quot;true&quot;), wird das Feld in der Benutzeroberfläche hervorgehoben. Die Beschriftung des Felds wird in Formularen rot dargestellt.
* **sql (boolean)**: Wenn dieses Attribut aktiviert ist (@sql=&quot;true&quot;), erzwingt es die Speicherung des SQL-Attributs, selbst wenn das Element, das das Attribut enthält, die Eigenschaft xml=&quot;true&quot; aufweist.
* **sqlDefault (string)**: Mit diesem Attribut können Sie den Standardwert definieren, der für die Aktualisierung der Datenbank berücksichtigt wird, wenn das Attribut @notNull aktiviert ist. Wenn dieses Attribut nach der Attributerstellung hinzugefügt wird, ändert sich auch das Schemaverhalten für die neuen Datensätze nicht. Um das Schema zu ändern und den Wert für neue Datensätze zu aktualisieren, müssen Sie das Attribut löschen und erneut erstellen.
* **sqlname (string)**: des Felds bei der Tabellenerstellung. Wenn @sqlname nicht angegeben ist, wird standardmäßig der Wert des Attributs &quot;@name&quot; verwendet. Wenn das Schema in die Datenbank geschrieben wird, werden je nach Feldtyp automatisch Präfixe hinzugefügt.
* **template (string)**: Dieses Attribut definiert einen Verweis auf ein `<attribute>` -Element, das von mehreren Schemas gemeinsam genutzt wird. Die Definition wird automatisch in das aktuelle Schema kopiert.
* **translatedDefault (string)**: Wenn ein &quot;@default&quot;-Attribut gefunden wird, können Sie mit &quot;@translationDefault&quot;einen Ausdruck neu definieren, der mit dem in &quot;@default&quot;definierten Ausdruck übereinstimmt, der vom Übersetzungs-Tool erfasst werden soll (interne Verwendung).
* **translatedExpr (string)**: Wenn ein &quot;@expr&quot;-Attribut vorhanden ist, können Sie mit dem &quot;@translationExpr&quot;-Attribut einen Ausdruck neu definieren, der mit dem in @expr definierten Ausdruck übereinstimmt, der vom Übersetzungs-Tool erfasst werden soll (interne Verwendung).
* **type (MNTOKEN)**: Feldtyp.

  Feldtypen sind generisch. Je nach installiertem Datenbanktyp ändert Adobe Campaign den definierten Typ in einen Wert, der für die bei der Strukturaktualisierung installierte Datenbank spezifisch ist.

  Liste der verfügbaren Typen:

   * BELIEBIGE
   * bin
   * blob
   * Boolesch
   * Byte
   * CDATA
   * datetime
   * datetimetz
   * datetimenotz
   * date
   * double
   * enum
   * float
   * html
   * int64
   * link
   * long
   * Memo
   * MNTOKEN
   * Prozent
   * primarykey
   * short
   * Zeichenfolge
   * time
   * timespan
   * uuid

  Wenn das Attribut &quot;@type&quot;leer gelassen wird, verknüpft Adobe Campaign standardmäßig eine Zeichenfolge (STRING) mit einer Länge von 100 Zeichen mit dem Feld.

  Wenn das Feld vom Typ STRING ist und der Name des Felds nicht durch das Attribut &quot;@sqlname&quot; angegeben wird, wird dem Namen des Felds in der Datenbank automatisch ein &quot;s&quot; vorangestellt. Dieser Betriebsmodus ähnelt den Feldern vom Typ INTEGER (i), DOUBLE (d) und DATES (ts).

* **userEnum (string)**: empfängt den internen Namen einer &quot;open&quot;-Auflistung. Die Werte der Auflistung können vom Benutzer in der Benutzeroberfläche definiert werden.
* **visibleIf (string)**: definiert eine Bedingung in Form eines XTK-Ausdrucks, um das Attribut anzuzeigen oder auszublenden.

  >[!IMPORTANT]
  >
  >Das Attribut ist ausgeblendet, es können jedoch weiterhin auf seine Daten zugegriffen werden.

* **xml (boolesch)**: Wenn diese Option aktiviert ist, verfügen die Werte des Felds nicht über ein verknüpftes SQL-Feld. Adobe Campaign erstellt ein Feld vom Typ &quot;mData&quot; für die Speicherung von Datensätzen. Dies bedeutet, dass diese Felder nicht gefiltert oder sortiert werden.

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

Deklaration eines XML-Felds mit &quot;@datapolicy&quot;:

```
<attribute dataPolicy="phone" desc="Mobile number" label="Mobile"
     length="32" name="mobilePhone" sqlname="sMobilePhone" type="string"/>
```

Beispiel mit &quot;@applyIf&quot;: Das Attribut &quot;contains&quot; wird nur erstellt, wenn die Anzahl der Länder größer als 20 ist.

```
<attribute length="100" name="Continent" type="string" applicableIf="@country > 20"/>
```

Beispiel mit &quot;@feature&quot;vom Typ &quot;shared&quot;:

```
<attribute name="field1" label="Field 1" type="long" feature="shared"/>
<attribute name="field1" label="Field 1" type="long" feature="shared" sqlname="126" sqltable="Ft_Content_Long"/>
```

Beispiel mit &quot;@feature&quot;vom Typ &quot;dediziert&quot;:

```
<attribute name="field1" label="Field 1" type="long" feature="dedicated"/>
<attribute name="field1" label="Field 1" type="long" feature="dedicated" sqlname="sField1" sqltable="Ft_recipient_field1"/>
```
