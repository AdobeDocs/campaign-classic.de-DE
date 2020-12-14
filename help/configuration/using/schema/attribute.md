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
source-wordcount: '1553'
ht-degree: 1%

---


# attribute element {#attribute--element}

## Inhaltsmodell {#content-model}

attribute:==help

## Attribute {#attributes}

_operation (string), advanced (boolean), applyIf (string), autoIncrement (boolean), gehörtTo (string), dataPolicy (string), dbEnum (string), defOnDuplicate (boolean), default (string), desc (string), edit (string), enum (string), expr (string), feature (string), Date (boolean), img (string), inout (string), label (string), length (string), localizable (boolean), name (MNTOKEN), notNull (boolean), pkgStatus (string), ref (string), required (boolean), sql (boolean), sqlDefault (string), sqlname (string), sqltable (string), Zielgruppe (MNTOKEN), Vorlage (string), translatedDefault (string), translationExpr (string), type (MNTOKEN), user (boolean), userEnum (string), visibleIf (string), xml (boolean)

## Eltern {#parents}

`<element>`

## Kinder {#children}

`<help>`

## Beschreibung {#description}

`<attribute>` -Elemente können Sie ein Feld in der Datenbank definieren.

## Verwendung und Kontext der Verwendung von {#use-and-context-of-use}

`<attribute>` -Elemente in einem  `<element>` Element deklariert werden.

Die Sequenz, in der `<attribute>`-Elemente in einem `<srcschema>` definiert sind, hat keine Auswirkungen auf die Felderstellungssequenz in der Datenbank. Die Erstellungsreihenfolge ist alphabetisch.

## Attributbeschreibung {#attribute-description}

* **_operation (string)**: definiert den Typ des Schreibens in der Datenbank.

   Dieses Attribut wird hauptsächlich beim Erweitern von vordefinierten Schemas verwendet.

   Barrierefreie Werte sind:

   * &quot;none&quot;: Aussöhnung allein. Das bedeutet, dass Adobe Campaign das Element wiederherstellt, ohne es zu aktualisieren, oder einen Fehler erzeugt, wenn es nicht vorhanden ist.
   * &quot;insertOrUpdate&quot;: mit Einfügen aktualisieren. Das bedeutet, dass Adobe Campaign das Element aktualisiert oder erstellt, wenn es nicht vorhanden ist.
   * &quot;insert&quot;: Einfügen. Das bedeutet, dass Adobe Campaign das Element einfügt, ohne zu prüfen, ob es vorhanden ist.
   * &quot;update&quot;: aktualisieren. Das bedeutet, dass Adobe Campaign das Element aktualisiert oder einen Fehler erzeugt, wenn es nicht vorhanden ist.
   * &quot;delete&quot;: löschen. Das bedeutet, dass Adobe Campaign Elemente wiederherstellt und löscht.

* **advanced (boolean)**: Wenn diese Option aktiviert ist (@advanced=&quot;true&quot;), können Sie das Attribut auf der Liste der verfügbaren Felder ausblenden, auf die Sie zur Konfiguration einer Liste in einem Formular zugreifen können.
* **applyIf (Zeichenfolge)**: Mit diesem Attribut können Sie Felder optional machen. Das `<attribute>`-Element wird bei der Aktualisierung der Datenbank berücksichtigt, wenn die Einschränkung eingehalten wird. &quot;applyIf&quot;erhält einen XTK-Ausdruck.
* **autoIncrement (boolean)**: Wenn diese Option aktiviert ist, wird das Feld zu einem Zähler. Auf diese Weise können Sie einen Wert (meist IDs) erhöhen. (externe Verwendung)
* **assignTo (string)**: nimmt den Namen und den Namensraum der Tabelle, die das Feld gemeinsam verwendet, und füllt das Schema, in dem das Attribut deklariert wird. (wird nur in einem `<schema>` verwendet).
* **dataPolicy (Zeichenfolge)**: ermöglicht Ihnen, Genehmigungsbeschränkungen für im SQL- oder XML-Feld zulässige Werte festzulegen. Die Werte für dieses Attribut lauten:

   * &quot;none&quot;: no value
   * &quot;smartCase&quot;: Großbuchstabe
   * &quot;lowerCase&quot;: Kleinbuchstabe
   * &quot;upperCase&quot;: Großbuchstabe
   * &quot;email&quot;: E-Mail-Adresse
   * &quot;phone&quot;: Telefonnummer
   * &quot;identifier&quot;: Bezeichnername
   * &quot;resIdentifier&quot;: Dateiname

* **dbEnum (Zeichenfolge)**: erhält den internen Namen einer &quot;geschlossenen&quot;Auflistung. Die Werte für die Auflistung müssen in `<srcschema>` definiert werden.
* **defOnDuplicate (boolean)**: Wenn dieses Attribut aktiviert ist, wird bei der Duplizierung eines Datensatzes der (in &quot;@default&quot;definierte) Standardwert automatisch erneut auf den Datensatz angewendet.
* **default (Zeichenfolge)**: können Sie den Wert des Standardfelds definieren (Aufruf einer Funktion, Standardwert). Dieses Attribut erhält einen XTK-Ausdruck.
* **desc (Zeichenfolge)**: können Sie eine Beschreibung des Attributs einfügen. Diese Beschreibung wird in der Statusleiste der Benutzeroberfläche angezeigt.
* **edit (string)**: Dieses Attribut gibt den Typ der Eingabe an, die im mit dem Schema verknüpften Formular verwendet wird.
* **enum (Zeichenfolge)**: erhält den Namen der Auflistung, die mit dem Feld verknüpft ist. Die Auflistung kann in dasselbe Schema oder in ein Remote-Schema eingefügt werden.
* **expr (Zeichenfolge)**: definiert einen Ausdruck zur Feldvorberechnung. Dieses Attribut empfängt einen Xpath- oder XTK-Ausdruck.
* **Funktion (Zeichenfolge)**: definiert ein Kennzeichenfeld: Diese Felder dienen zum Erweitern der Daten in einer vorhandenen Tabelle, jedoch mit Datenspeicherung in einer Anhang-Tabelle. Akzeptierte Werte sind:

   * &quot;shared&quot;: der Inhalt in einer freigegebenen Tabelle nach Datentyp gespeichert wird
   * &quot;dediziert&quot;: der Inhalt in einer speziellen Tabelle gespeichert wird

   Die Tabellen mit SQL-Eigenschaften werden automatisch anhand des charakteristischen Typs erstellt:

   * dediziert: `Ft_[name_of_the_schema_containing_the_characteristic]_[name_of_the_characteristic]`
   * shared: `Ft_[type_of_key_of_the_schema_containing_the_characteristic]_[type_of_the_characteristic]`

   Es gibt zwei Arten von Eigenschaftenfeldern: einfache oà¹-Felder, bei denen ein einzelner Wert für das Merkmal autorisiert ist, und bei denen das Merkmal mit einem Collection-Element verknüpft ist, das mehrere Werte enthalten kann.

   Wenn ein Merkmal in einem Schema definiert ist, muss dieses Schema einen Hauptschlüssel haben, der auf einem einzigen Feld basiert (Composite-Schlüssel sind nicht autorisiert).

* **featureDate (boolean)**: -Attribut, das mit dem Charakteristikumsfeld &quot;@feature&quot;verknüpft ist. Wenn der Wert &quot;true&quot;ist, können Sie feststellen, wann der Wert zuletzt aktualisiert wurde.
* **img (Zeichenfolge)**: können Sie einen Pfad für ein Bild definieren, das mit einem Feld verknüpft ist (Namensraum und Bildname) (Beispiel: img=&quot;cus:mypicture.jpg&quot;). Das Bild muss physisch auf den Anwendungsserver importiert werden.
* **label (Zeichenfolge)**: -Beschriftung, die mit dem Feld verknüpft ist, meist für den Benutzer in der Oberfläche bestimmt. Damit können Sie Benennungsbeschränkungen vermeiden.
* **length (Zeichenfolge)**: max. Anzahl der Zeichen für einen Wert des SQL-Felds vom Typ &quot;string&quot;. Wenn das Attribut &quot;@length&quot;nicht angegeben ist, erstellt Adobe Campaign automatisch ein Feld für 255 Zeichen.
* **localizable (boolean)**: Wenn es aktiviert ist, weist dieses Attribut das Erfassungswerkzeug an, den Wert des Attributs &quot;@label&quot;für die Übersetzung wiederherzustellen (interne Verwendung).
* **name (MNTOKEN)**: Name des Attributs, das mit dem Namen des Felds in der Tabelle übereinstimmt. Der Wert des Attributs &quot;@name&quot;muss kurz sein, vorzugsweise auf Englisch, und den XML-Benennungsbeschränkungen entsprechen.

   Wenn das Schema in die Datenbank geschrieben wird, werden dem Feldnamen automatisch Präfixe per Adobe Campaign hinzugefügt:

   * &quot;i&quot;: Präfix für den Integer-Typ.
   * &quot;d&quot;: Präfix für den Typ &quot;Dublette&quot;.
   * &quot;s&quot;: Präfix für den Zeichenfolgen-Typ.
   * &quot;ts&quot;: Präfix für den Typ &quot;Datum&quot;.

   Um den Namen des Felds in der Tabelle vollständig zu definieren, verwenden Sie beim Definieren eines Attributs die Option &quot;@sqlname&quot;.

* **notNull (boolean)**: können Sie das Verhalten von Adobe Campaign in Bezug auf die Verwaltung von NULL-Datensätzen in der Datenbank neu definieren. Numerische Felder sind standardmäßig nicht null, und die Felder für den Datumstyp können null sein.
* **pkgStatus (Zeichenfolge)**: bei Paketexporten werden Werte in Abhängigkeit vom Wert von &quot;@pkgStatus&quot;berücksichtigt:

   * &quot;immer&quot;: immer vorhanden
   * &quot;never&quot;: niemals vorhanden
   * &quot;default (or nothing)&quot;: der Wert wird exportiert, es sei denn, es handelt sich um den Standardwert oder um ein internes Feld, das nicht mit anderen Instanzen kompatibel ist.

* **ref (string)**: Dieses Attribut definiert einen Verweis auf ein  `<attribute>` Element, das von mehreren Schemas gemeinsam verwendet wird (Definition Factoring). Die Definition wird nicht in das aktuelle Schema kopiert.
* **erforderlich (Boolescher Wert)**: Wenn dieses Attribut aktiviert ist (@required=&quot;true&quot;), wird das Feld in der Oberfläche markiert. Die Beschriftung des Felds wird in Formularen rot dargestellt.
* **sql (boolean)**: Wenn dieses Attribut aktiviert ist (@sql=&quot;true&quot;), erzwingt es die Datenspeicherung des SQL-Attributs, selbst wenn das Element, das das Attribut enthält, die Eigenschaft xml=&quot;true&quot; hat.
* **sqlDefault (Zeichenfolge)**: Mit diesem Attribut können Sie den Standardwert definieren, der bei der Aktualisierung der Datenbank berücksichtigt wird, wenn das Attribut &quot;@notNull&quot;aktiviert ist. Wenn dieses Attribut nach der Attributerstellung hinzugefügt wird, ändert sich das Verhalten des Schemas auch für die neuen Datensätze nicht. Um das Schema zu ändern und den Wert für neue Datensätze zu aktualisieren, müssen Sie das Attribut löschen und erneut erstellen.
* **sqlname (Zeichenfolge)**: des Felds während der Tabellenerstellung. Wenn &quot;@sqlname&quot;nicht angegeben ist, wird standardmäßig der Wert des Attributs &quot;@name&quot;verwendet. Wenn das Schema in die Datenbank geschrieben wird, werden je nach Feldtyp automatisch Präfixe hinzugefügt.
* **template (string)**: Dieses Attribut definiert einen Verweis auf ein  `<attribute>` Element, das von mehreren Schemas gemeinsam verwendet wird. Die Definition wird automatisch in das aktuelle Schema kopiert.
* **translateDefault (Zeichenfolge)**: Wenn ein Attribut &quot;@default&quot;gefunden wird, können Sie mit &quot;@translatedDefault&quot;einen Ausdruck neu definieren, der mit dem in &quot;@default&quot;definierten übereinstimmt und vom Übersetzungstool erfasst wird (interner Einsatz).
* **translationExpr (Zeichenfolge)**: Wenn ein Attribut &quot;@expr&quot;vorhanden ist, können Sie mit dem Attribut &quot;@translatedExpr&quot;einen Ausdruck neu definieren, der mit dem in &quot;@expr&quot;definierten übereinstimmt und vom Übersetzungstool erfasst wird (interner Einsatz).
* **type (MNTOKEN)**: Feldtyp.

   Feldtypen sind generisch. Je nach installiertem Datenbanktyp ändert Adobe Campaign den definierten Typ in einen Datenbankwert, der während der Strukturaktualisierung installiert wird.

   Liste der verfügbaren Typen:

   * BELIEBIGE
   * bin
   * blob
   * boolean
   * Byte
   * CDATA
   * datetime
   * datetimetz
   * datetimenotz
   * date
   * dublette
   * enum
   * float
   * html
   * int64
   * link
   * long
   * memo
   * MNTOKEN
   * percent
   * primarykey
   * short
   * Zeichenfolge
   * Zeit
   * Zeitspanne
   * uuid

   Wenn das Attribut &quot;@type&quot;leer gelassen wird, verknüpft Adobe Campaign standardmäßig eine Zeichenfolge (STRING) mit einer Länge von 100 Zeichen mit dem Feld.

   Wenn das Feld vom STRING-Typ ist und der Feldname nicht durch das Attribut &quot;@sqlname&quot;angegeben wird, wird dem Namen des Felds in der Datenbank automatisch ein &quot;s&quot;vorangestellt. Dieser Betriebsmodus ist mit den Feldern des Typs INTEGER (i), DUBLETTE (d) und DATES (ts) vergleichbar.

* **userEnum (Zeichenfolge)**: erhält den internen Namen einer &quot;offenen&quot;Auflistung. Die Werte der Auflistung können vom Benutzer in der Benutzeroberfläche definiert werden.
* **visibleIf (Zeichenfolge)**: definiert eine Bedingung in Form eines XTK-Ausdrucks zum Ein- oder Ausblenden des Attributs.

   >[!IMPORTANT]
   >
   >Das Attribut ist ausgeblendet, es können jedoch weiterhin auf seine Daten zugegriffen werden.

* **xml (boolean)**: Wenn diese Option aktiviert ist, haben die Feldwerte kein verknüpftes SQL-Feld. Adobe Campaign erstellt ein Textfeld vom Typ &quot;mData&quot;für die Datenspeicherung von Datensätzen. Das bedeutet, dass diese Felder nicht gefiltert oder sortiert werden.

### Beispiele {#examples}

Beispiel für Auflistungen, deren Werte in der Datenbank gespeichert werden:

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

Beispiel mit &quot;@feature&quot;vom Typ &quot;dedizierte&quot;Zeichen:

```
<attribute name="field1" label="Field 1" type="long" feature="dedicated"/>
<attribute name="field1" label="Field 1" type="long" feature="dedicated" sqlname="sField1" sqltable="Ft_recipient_field1"/>
```
