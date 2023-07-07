---
product: campaign
title: Elemente und Attribute - Attributelement
description: Elemente und Attribute
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: e4d34f56-b065-4dce-8974-11dc2767873a
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '1555'
ht-degree: 1%

---

# attribute element {#attribute--element}

![](../../../assets/v7-only.svg)

## Inhaltsmodell {#content-model}

attribute:==help

## Attribute {#attributes}

_operation (string), advanced (boolean), applyIf (string), autoIncrement (boolean), gehörtTo (string), dataPolicy (string), dbEnum (string), defOnDuplicate (boolean), default (string), desc (string), edit (string), enum (string), expr (string), feature (string), Date (boolean), img (string), inout (string), label (string), length (string), localizable (boolean), name (MNTOKEN), notNull (boolean), pkgStatus (string), ref (string), required (boolean), sql (boolean), sqlDefault (string), sqlname (string), sqltable (string), target (MNTOKEN), template (string), translationDefault (string), translatedExpr (string), type (MNTOKEN), user (boolean), userEnum (string), visibleIf (string), xml (boolean).

## Übergeordnete Elemente {#parents}

`<element>`

## Untergeordnetes Element {#children}

`<help>`

## Beschreibung {#description}

`<attribute>` -Elemente können Sie ein Feld in der Datenbank definieren.

## Verwendung und Verwendungskontext {#use-and-context-of-use}

`<attribute>` -Elemente in einer `<element>` -Element.

Die Sequenz, in der `<attribute>` -Elemente in einer `<srcschema>` hat keine Auswirkungen auf die Reihenfolge der Felderstellung in der Datenbank. Die Erstellungssequenz ist alphabetisch.

## Attributbeschreibung {#attribute-description}

* **_operation (string)**: definiert den Typ des Schreibens in der Datenbank.

  Dieses Attribut wird hauptsächlich bei der Erweiterung von nativen Schemata verwendet.

  Barrierefreie Werte sind:

   * &quot;none&quot;: Abstimmung. Das bedeutet, dass Adobe Campaign das Element wiederherstellt, ohne es zu aktualisieren, oder einen Fehler erzeugt, wenn es nicht vorhanden ist.
   * &quot;insertOrUpdate&quot;: durch Einfügen aktualisiert werden. Das bedeutet, dass Adobe Campaign das Element aktualisiert oder erstellt, falls es nicht vorhanden ist.
   * &quot;insert&quot;: einfügen. Das bedeutet, dass Adobe Campaign das Element einfügt, ohne zu überprüfen, ob es vorhanden ist.
   * &quot;update&quot;: aktualisieren. Das bedeutet, dass Adobe Campaign das Element aktualisiert oder einen Fehler erzeugt, wenn es nicht vorhanden ist.
   * &quot;delete&quot;: Löschen. Dies bedeutet, dass Adobe Campaign Elemente wiederherstellt und löscht.

* **advanced (boolean)**: Wenn diese Option aktiviert ist (@advanced=&quot;true&quot;), können Sie das Attribut in der Liste der verfügbaren Felder ausblenden, auf die für die Konfiguration einer Liste in einem Formular zugegriffen werden kann.
* **applyIf (string)**: Mit diesem Attribut können Sie Felder optional machen. Die `<attribute>` -Element bei der Aktualisierung der Datenbank berücksichtigt werden, wenn die Beschränkung eingehalten wird. &quot;applyIf&quot;erhält einen XTK-Ausdruck.
* **autoIncrement (boolean)**: Wenn diese Option aktiviert ist, wird das Feld zu einem Zähler. Auf diese Weise können Sie einen Wert (meist IDs) erhöhen. (externe Verwendung)
* **gehörtTo (Zeichenfolge)**: nimmt den Namen und Namespace der Tabelle, die das Feld gemeinsam verwendet, und füllt das Schema aus, in dem das Attribut deklariert wird. (wird nur in einer `<schema>`).
* **dataPolicy (Zeichenfolge)**: ermöglicht es Ihnen, Genehmigungseinschränkungen für die im SQL- oder XML-Feld zulässigen Werte anzugeben. Die Werte für dieses Attribut sind:

   * &quot;none&quot;: kein Wert
   * &quot;smartCase&quot;: Großbuchstaben
   * &quot;lowerCase&quot;: Kleinbuchstabe
   * &quot;upperCase&quot;: Großbuchstaben
   * &quot;email&quot;: E-Mail-Adresse
   * &quot;phone&quot;: Telefonnummer
   * &quot;identifier&quot;: Identifikationsname
   * &quot;resIdentifier&quot;: Dateiname

* **dbEnum (Zeichenfolge)**: empfängt den internen Namen einer &quot;geschlossenen&quot; Auflistung. Die Auflistungswerte müssen im Abschnitt `<srcschema>`.
* **defOnDuplicate (boolesch)**: Wenn dieses Attribut aktiviert ist, wird bei der Duplizierung eines Datensatzes der (in @default definierte) Standardwert automatisch erneut auf den Datensatz angewendet.
* **default (string)**: ermöglicht die Definition des Werts des Standardfelds (Aufruf einer Funktion, Standardwert). Dieses Attribut erhält einen XTK-Ausdruck.
* **desc (Zeichenfolge)**: ermöglicht das Einfügen einer Beschreibung des Attributs. Diese Beschreibung wird in der Statusleiste der Benutzeroberfläche angezeigt.
* **edit (string)**: Dieses Attribut gibt den Typ der Eingabe an, die in dem mit dem Schema verknüpften Formular verwendet wird.
* **enum (string)**: erhält den Namen der mit dem Feld verknüpften Auflistung. Die Auflistung kann im selben Schema oder in ein Remote-Schema eingefügt werden.
* **expr (Zeichenfolge)**: definiert einen Ausdruck für die Feldvorberechnung. Dieses Attribut empfängt einen Xpath oder einen XTK-Ausdruck.
* **Funktion (Zeichenfolge)**: definiert ein Merkmalfeld: Diese Felder dienen zur Erweiterung der Daten in einer vorhandenen Tabelle, jedoch mit Speicherung in einer Tabelle im Anhang. Zulässige Werte sind:

   * &quot;shared&quot;: Der Inhalt wird in einer freigegebenen Tabelle nach Datentyp gespeichert.
   * &quot;dediziert&quot;: Der Inhalt wird in einer eigenen Tabelle gespeichert.

  SQL-Eigenschaftstabellen werden automatisch basierend auf dem charakteristischen Typ erstellt:

   * dediziert: `Ft_[name_of_the_schema_containing_the_characteristic]_[name_of_the_characteristic]`
   * shared: `Ft_[type_of_key_of_the_schema_containing_the_characteristic]_[type_of_the_characteristic]`

  Es gibt zwei Arten von Eigenschaftenfeldern: einfache¹-Felder, bei denen ein einzelner Wert für das Merkmal autorisiert ist, und ein¹-Multiple-Choice-Feld, bei dem das Merkmal mit einem Kollektionselement verknüpft ist, das mehrere Werte enthalten kann.

  Wenn ein Merkmal in einem Schema definiert ist, muss dieses Schema über einen Hauptschlüssel verfügen, der auf einem einzelnen Feld basiert (zusammengesetzte Schlüssel sind nicht autorisiert).

* **featureDate (boolean)**: Attribut im Zusammenhang mit dem Feld &quot;@feature&quot;. Wenn der Wert &quot;true&quot;ist, können Sie feststellen, wann der Wert zuletzt aktualisiert wurde.
* **img (Zeichenfolge)**: können Sie einen Pfad für ein Bild definieren, das mit einem Feld verknüpft ist (Namespace + Bildname) (Beispiel: img=&quot;cus:mypicture.jpg&quot;). Das Bild muss physisch auf den Anwendungsserver importiert werden.
* **label (string)**: -Beschriftung, die mit dem Feld verknüpft ist, hauptsächlich für den Benutzer in der Benutzeroberfläche bestimmt. Damit können Sie Benennungsbeschränkungen vermeiden.
* **length (Zeichenfolge)**: max. Anzahl der Zeichen für einen Wert des SQL-Felds vom Typ &quot;String&quot;. Wenn das Attribut &quot;@length&quot;nicht angegeben ist, erstellt Adobe Campaign automatisch ein Feld für 255 Zeichen.
* **localizable (boolean)**: Wenn es aktiviert ist, weist dieses Attribut das Tool zur Sammlung an, den Wert des Attributs &quot;@label&quot;für die Übersetzung abzurufen (interne Verwendung).
* **name (MNTOKEN)**: Name des Attributs, das mit dem Namen des Felds in der Tabelle übereinstimmt. Der Wert des Attributs &quot;@name&quot;muss kurz sein, vorzugsweise auf Englisch, und den XML-Benennungsbeschränkungen entsprechen.

  Beim Schreiben des Schemas in die Datenbank werden dem Feldnamen von Adobe Campaign automatisch Präfixe hinzugefügt:

   * &quot;i&quot;: -Präfix für den Typ &quot;Ganzzahl&quot;.
   * &quot;d&quot;: -Präfix für den Typ &quot;double&quot;.
   * &quot;s&quot;: -Präfix für den Zeichenfolgentyp.
   * &quot;ts&quot;: -Präfix für den Typ &quot;Datum&quot;.

  Um den Namen des Felds in der Tabelle vollständig zu definieren, verwenden Sie beim Definieren eines Attributs die Option &quot;@sqlname&quot;.

* **notNull (boolesch)**: ermöglicht Ihnen, das Verhalten von Adobe Campaign bezüglich der Verwaltung von NULL-Datensätzen in der Datenbank neu zu definieren. Numerische Felder sind standardmäßig nicht null und Felder vom Typ Zeichenfolge und Datum können null sein.
* **pkgStatus (Zeichenfolge)**: Bei Package-Exporten werden Werte in Abhängigkeit vom Wert des &quot;@pkgStatus&quot; berücksichtigt:

   * &quot;always&quot;: immer vorhanden
   * &quot;never&quot;: niemals präsent
   * &quot;default (oder nichts)&quot;: Der Wert wird exportiert, es sei denn, es handelt sich um den Standardwert oder um kein internes Feld, das nicht mit anderen Instanzen kompatibel ist.

* **ref (string)**: Dieses Attribut definiert einen Verweis auf eine `<attribute>` -Element, das von mehreren Schemas gemeinsam verwendet wird (Definition-Factoring). Die Definition wird nicht in das aktuelle Schema kopiert.
* **erforderlich (boolesch)**: Wenn dieses Attribut aktiviert ist (@required=&quot;true&quot;), wird das Feld in der Benutzeroberfläche hervorgehoben. Die Beschriftung des Felds wird in Formularen rot dargestellt.
* **sql (boolesch)**: Wenn dieses Attribut aktiviert ist (@sql=&quot;true&quot;), wird die Speicherung des SQL-Attributs erzwungen, selbst wenn das Element, das das Attribut enthält, die Eigenschaft xml=&quot;true&quot; aufweist.
* **sqlDefault (string)**: Mit diesem Attribut können Sie den Standardwert definieren, der für die Aktualisierung der Datenbank berücksichtigt wird, wenn das Attribut @notNull aktiviert ist. Wenn dieses Attribut nach der Attributerstellung hinzugefügt wird, ändert sich auch das Schemaverhalten für die neuen Datensätze nicht. Um das Schema zu ändern und den Wert für neue Datensätze zu aktualisieren, müssen Sie das Attribut löschen und erneut erstellen.
* **sqlname (string)**: des Felds während der Tabellenerstellung. Wenn @sqlname nicht angegeben ist, wird standardmäßig der Wert des Attributs &quot;@name&quot; verwendet. Wenn das Schema in die Datenbank geschrieben wird, werden je nach Feldtyp automatisch Präfixe hinzugefügt.
* **template (string)**: Dieses Attribut definiert einen Verweis auf eine `<attribute>` -Element, das von mehreren Schemas gemeinsam genutzt wird. Die Definition wird automatisch in das aktuelle Schema kopiert.
* **translateDefault (string)**: Wenn ein &quot;@default&quot;-Attribut gefunden wird, können Sie mit &quot;@translationDefault&quot;einen Ausdruck neu definieren, der mit dem in &quot;@default&quot;definierten Ausdruck übereinstimmt, der vom Übersetzungs-Tool erfasst werden soll (interne Verwendung).
* **translateExpr (Zeichenfolge)**: Wenn das Attribut &quot;@expr&quot; vorhanden ist, können Sie mit dem Attribut &quot;@translationExpr&quot; einen Ausdruck neu definieren, der mit dem in @expr definierten Ausdruck übereinstimmt, der vom Übersetzungstool (interne Verwendung) erfasst werden soll.
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
   * percent
   * primarykey
   * short
   * Zeichenfolge
   * Zeit
   * timespan
   * uuid

  Wenn das Attribut &quot;@type&quot;leer gelassen wird, verknüpft Adobe Campaign standardmäßig eine Zeichenfolge (STRING) mit einer Länge von 100 Zeichen mit dem Feld.

  Wenn das Feld vom Typ STRING ist und der Name des Felds nicht durch das Attribut &quot;@sqlname&quot; angegeben wird, wird dem Namen des Felds in der Datenbank automatisch ein &quot;s&quot; vorangestellt. Dieser Betriebsmodus ähnelt den Feldern vom Typ INTEGER (i), DOUBLE (d) und DATES (ts).

* **userEnum (Zeichenfolge)**: empfängt den internen Namen einer &quot;open&quot;-Auflistung. Die Werte der Auflistung können vom Benutzer in der Benutzeroberfläche definiert werden.
* **visibleIf (Zeichenfolge)**: definiert eine Bedingung in Form eines XTK-Ausdrucks, um das Attribut ein- oder auszublenden.

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

Beispiel mit einem &quot;@applyIf&quot;: Das Attribut &quot;enthält&quot;wird nur erstellt, wenn die Anzahl der Länder größer als 20 ist.

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
