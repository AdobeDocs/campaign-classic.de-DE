---
solution: Campaign Classic
product: campaign
title: Elemente und Attribute
description: Elemente und Attribute
audience: configuration
content-type: reference
topic-tags: schema-reference
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '6019'
ht-degree: 2%

---


# Elemente und Attribute {#elements-and-attributes}

Beim Bearbeiten eines Schemas ist ein auf dem Quellcode-Schema basierendes Genehmigungssystem (xtk:srcSchema) verfügbar. Beim Aktualisieren der Datenbank mit dem Befehl &quot;Datenbankstruktur aktualisieren...&quot; können auch einige Fehler erkannt werden. Assistent.

Standardmäßig sind in Adobe Campaign-Schemas alle booleschen Typattribute &quot;false&quot;. Um sie zu aktivieren, müssen Sie das Attribut im Schema angeben und dessen Wert auf &quot;true&quot;setzen.

## `<attribute>` Element {#attribute--element}

### Inhaltsmodell {#content-model}

attribute:==help

### Attribute {#attributes}

_operation (string), advanced (boolean), applyIf (string), autoIncrement (boolean), gehörtTo (string), dataPolicy (string), dbEnum (string), defOnDuplicate (boolean), default (string), desc (string), edit (string), enum (string), expr (string), feature (string), Date (boolean), img (string), inout (string), label (string), length (string), localizable (boolean), name (MNTOKEN), notNull (boolean), pkgStatus (string), ref (string), required (boolean), sql (boolean), sqlDefault (string), sqlname (string), sqltable (string), Zielgruppe (MNTOKEN), Vorlage (string), translatedDefault (string), translationExpr (string), type (MNTOKEN), user (boolean), userEnum (string), visibleIf (string), xml (boolean)

### Eltern {#parents}

`<element>`

### Kinder {#children}

`<help>`

### Beschreibung {#description}

`<attribute>` -Elemente können Sie ein Feld in der Datenbank definieren.

### Verwendung und Kontext {#use-and-context-of-use}

`<attribute>` -Elemente in einem `<element>` Element deklariert werden.

Die Reihenfolge, in der `<attribute>` Elemente in einer Datenbank definiert werden, wirkt sich nicht auf die Felderstellungssequenz in der Datenbank aus `<srcschema>` . Die Erstellungsreihenfolge ist alphabetisch.

### Attributbeschreibung {#attribute-description}

* **_operation (string)**: definiert den Typ des Schreibens in der Datenbank.

   Dieses Attribut wird hauptsächlich beim Erweitern von vordefinierten Schemas verwendet.

   Barrierefreie Werte sind:

   * &quot;none&quot;: Aussöhnung allein. Das bedeutet, dass Adobe Campaign das Element wiederherstellt, ohne es zu aktualisieren, oder einen Fehler erzeugt, wenn es nicht vorhanden ist.
   * &quot;insertOrUpdate&quot;: mit Einfügen aktualisieren. Das bedeutet, dass Adobe Campaign das Element aktualisiert oder erstellt, wenn es nicht vorhanden ist.
   * &quot;insert&quot;: Einfügen. Das bedeutet, dass Adobe Campaign das Element einfügt, ohne zu prüfen, ob es vorhanden ist.
   * &quot;update&quot;: aktualisieren. Das bedeutet, dass Adobe Campaign das Element aktualisiert oder einen Fehler erzeugt, wenn es nicht vorhanden ist.
   * &quot;delete&quot;: löschen. Das bedeutet, dass Adobe Campaign Elemente wiederherstellt und löscht.

* **advanced (boolean)**: Wenn diese Option aktiviert ist (@advanced=&quot;true&quot;), können Sie das Attribut auf der Liste der verfügbaren Felder ausblenden, auf die Sie zur Konfiguration einer Liste in einem Formular zugreifen können.
* **applyIf (Zeichenfolge)**: Mit diesem Attribut können Sie Felder optional machen. Das `<attribute>` Element wird bei der Aktualisierung der Datenbank berücksichtigt, wenn die Einschränkung eingehalten wird. &quot;applyIf&quot;erhält einen XTK-Ausdruck.
* **autoIncrement (boolean)**: Wenn diese Option aktiviert ist, wird das Feld zu einem Zähler. Auf diese Weise können Sie einen Wert (meist IDs) erhöhen. (externe Verwendung)
* **assignTo (string)**: nimmt den Namen und den Namensraum der Tabelle, die das Feld gemeinsam verwendet, und füllt das Schema, in dem das Attribut deklariert wird. (nur in a verwendet `<schema>`).
* **dataPolicy (Zeichenfolge)**: ermöglicht Ihnen, Genehmigungsbeschränkungen für im SQL- oder XML-Feld zulässige Werte festzulegen. Die Werte für dieses Attribut lauten:

   * &quot;none&quot;: no value
   * &quot;smartCase&quot;: Großbuchstabe
   * &quot;lowerCase&quot;: Kleinbuchstabe
   * &quot;upperCase&quot;: Großbuchstabe
   * &quot;email&quot;: E-Mail-Adresse
   * &quot;phone&quot;: Telefonnummer
   * &quot;identifier&quot;: Bezeichnername
   * &quot;resIdentifier&quot;: Dateiname

* **dbEnum (Zeichenfolge)**: erhält den internen Namen einer &quot;geschlossenen&quot;Auflistung. Die Werte für die Auflistung müssen in der `<srcschema>`definiert werden.
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

* **ref (string)**: Dieses Attribut definiert einen Verweis auf ein `<attribute>` Element, das von mehreren Schemas gemeinsam verwendet wird (Definition Factoring). Die Definition wird nicht in das aktuelle Schema kopiert.
* **erforderlich (Boolescher Wert)**: Wenn dieses Attribut aktiviert ist (@required=&quot;true&quot;), wird das Feld in der Oberfläche markiert. Die Beschriftung des Felds wird in Formularen rot dargestellt.
* **sql (boolean)**: Wenn dieses Attribut aktiviert ist (@sql=&quot;true&quot;), erzwingt es die Datenspeicherung des SQL-Attributs, selbst wenn das Element, das das Attribut enthält, die Eigenschaft xml=&quot;true&quot; hat.
* **sqlDefault (Zeichenfolge)**: Mit diesem Attribut können Sie den Standardwert definieren, der bei der Aktualisierung der Datenbank berücksichtigt wird, wenn das Attribut &quot;@notNull&quot;aktiviert ist. Wenn dieses Attribut nach der Attributerstellung hinzugefügt wird, ändert sich das Verhalten des Schemas auch für die neuen Datensätze nicht. Um das Schema zu ändern und den Wert für neue Datensätze zu aktualisieren, müssen Sie das Attribut löschen und erneut erstellen.
* **sqlname (Zeichenfolge)**: des Felds während der Tabellenerstellung. Wenn &quot;@sqlname&quot;nicht angegeben ist, wird standardmäßig der Wert des Attributs &quot;@name&quot;verwendet. Wenn das Schema in die Datenbank geschrieben wird, werden je nach Feldtyp automatisch Präfixe hinzugefügt.
* **template (string)**: Dieses Attribut definiert einen Verweis auf ein `<attribute>` Element, das von mehreren Schemas gemeinsam verwendet wird. Die Definition wird automatisch in das aktuelle Schema kopiert.
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

## `<compute-string>` Element {#compute-string--element}

### Inhaltsmodell {#content-model-1}

compute-string:==EMPTY

### Attribute {#attributes-1}

@expr

### Eltern {#parents-1}

`<element>`

### Kinder {#children-1}

Keiner

### Beschreibung {#description-1}

Mit dem `<compute-string>` Element können Sie eine auf einem XTK-Ausdruck basierende Zeichenfolge erstellen, um eine &quot;integrierte&quot;Beschriftung auf der Benutzeroberfläche anzuzeigen, die auf mehreren Werten basiert.

### Verwendung und Kontext {#use-and-context-of-use-1}

Wenn kein Element definiert `<compute-string>` ist, wird standardmäßig ein `<compute-string>` Element mit den Werten des Primärschlüssels im Schema eingegeben.

### Attributbeschreibung {#attribute-description-1}

* **expr (Zeichenfolge)**: XTK- und/oder Xpath-Ausdruck

### Beispiele {#examples-1}

```
<compute-string expr="@label + Iif(@code='','', ' (' + [folder/@label] + ')')"/>  
<compute-string expr="ToString([@centralCatalog-id]) + ',' + ToString([@localOrgUnit-id])" />
```

Ergebnis der auf einem Empfänger berechneten Zeichenfolge: &quot;John Doe (john.doe@aol.com)&quot;:

```
<element name="recipient">
<compute-string expr="@lastName + ' ' + @firstName +' (' + @email + ')'
"/>
...
</element>
```

## `<condition>` Element {#condition--element}

### Inhaltsmodell {#content-model-2}

Bedingung:==EMPTY

### Attribute {#attributes-2}

* @boolOperator (Zeichenfolge)
* @enabledIf (Zeichenfolge)
* @expr (Zeichenfolge)

### Eltern {#parents-2}

`<sysfilter>`

### Kinder {#children-2}

Keiner

### Beschreibung {#description-2}

Mit diesem Element können Sie eine Filterbedingung definieren.

### Verwendung und Kontext {#use-and-context-of-use-2}

Ein `<sysfiler>` Element kann mehrere Filterbedingungen enthalten.

### Attributbeschreibung {#attribute-description-2}

* **boolOperator (Zeichenfolge)**: Wenn mehrere Elemente innerhalb desselben `<conditions>` Elements definiert `<sysfilter>` sind, können Sie sie mit diesem Attribut kombinieren. Standardmäßig lautet die logische Verknüpfung zwischen `<condition>` Elementen &quot;AND&quot;. Mit dem Attribut &quot;@boolOperator&quot;können Sie Links vom Typ &quot;OR&quot;und &quot;AND&quot;kombinieren.
* **enabledIf (Zeichenfolge)**: aktivierung der Bedingung.
* **expr (Zeichenfolge)**: ein XTK-Ausdruck.

### Beispiele {#examples-2}

```
<sysfilter>
  <condition enabledIf="hasNamedRight('admin')=false" expr="@city=[currentOperator/location/@city]" />
</sysfilter>
```

## `<dbindex>` Element {#dbindex--element}

### Inhaltsmodell {#content-model-3}

dbindex:==keyfield

### Attribute {#attributes-3}

* @_operation (Zeichenfolge)
* @applyIf (Zeichenfolge)
* @label (Zeichenfolge)
* @name (MNTOKEN)
* @unique (boolean)

### Eltern {#parents-3}

`<element>`

### Kinder {#children-3}

`<keyfield>`

### Beschreibung {#description-3}

Mit diesem Element können Sie einen mit einer Tabelle verknüpften Index definieren.

### Verwendung und Kontext {#use-and-context-of-use-3}

Es ist möglich, mehrere Indizes zu definieren. Ein Index kann auf ein oder mehrere Felder der Tabelle verweisen. Die Indexdeklaration entspricht in der Regel der Definition des Hauptelements Schema.

Die Reihenfolge der `<keyfield>` Elemente, die in einem definiert sind, `<dbindex>` ist sehr wichtig. Das erste `<keyfield>` muss das Indexierungskriterium sein, auf dem die Abfragen hauptsächlich basieren.

Der Name des Indexes in der Datenbank wird durch Verkettung des Namens der Tabelle und des Indexnamens berechnet. Beispiel: Tabellenname &quot;Beispiel&quot;, Namensraum &quot;Cus&quot;, Indexname &quot;MyIndex&quot;-> Name des Indexfelds bei der Indexerstellung bei der Abfrage: &quot;CusSample_myIndex&quot;.

### Attributbeschreibung {#attribute-description-3}

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

### Beispiele {#examples-3}

Erstellen eines Indexes im Feld &quot;id&quot;. (Das Attribut &quot;@unique&quot;im `<dbindex>` Element löst das Hinzufügen des SQL-Schlüsselworts &quot;UNIQUE&quot;aus, wenn der Index in der Abfrage erstellt wird).

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

## `<element>` Element {#element--element}

### Inhaltsmodell {#content-model-4}

element:==(attribute | compute-string | dbindex | default | element | help | join | Schlüssel | sysFilter | translatedDefault)

### Attribute {#attributes-4}

_operation (string), advanced (boolean), Aggregat (string), applyIf (string), autopk (boolean), gehörtTo (string), convDate (string), dataPolicy (string), dataSource (string), dbEnum (string), defOnDuplicate (boolean), default (string), desc (string), display Field (boolean), doesNotSupportDiff (boolean), edit (string), emptyKeyValue (string), enum (string), enumImage (string), developSchemaTarget (string), expr (string), externalJoin (boolean), feature (string), featureDate (boolean), filterPath (string), folderLink string), folderModel (string), folderProcess (string), fullLoad (boolean), hierarchisch (boolean), hierarchischPath (string), img (string), Inout (string), Integrität (string), label (string), labelSingular (string), length (string), localizable (boolean), name (MNTOKEN), noDb Index (boolean), noKey (boolean), ordered (boolean), overflow table (boolean), pkSequence (string), pkgStatus (string), ref (string), required (boolean), revAdvanced (boolean), revCardinality (string), revDesc (string), revExternalJoin (boolean) ean), revIntegrity (string), revLabel (string), revLink (string), revTarget (string), revVisibleIf (string), sql (boolean), sqlname (string), sqltable (string), tableSpace (string), tableSpaceIndex (string), Zielgruppe (MNTOKEN), template (string), temporaryTable (boolean), translatedDefault (string), translatedExpr (string), type (MNTOKEN), unbound (boolean), user (boolean), userEnum (string), visibleIf (string), xml (boolean), xmlChildren (boolean)

### Eltern {#parents-4}

`<srcschema>`

`<element>`

### Kinder {#children-4}

* `<attribute>`
* `<compute-string>`
* `<dbindex>`
* `<default>`
* `<element>`
* `<help>`
* `<join>`
* `<key>`
* `<sysfilter>`
* `<translateddefault>`

### Beschreibung {#description-4}

In Adobe Campaign gibt es vier `<element>` Elementtypen:

* Stamm `<element>` : definiert den Namen der SQL-Tabelle, die dem Schema entspricht.
* Struktur `<element>` : definiert eine Gruppe von `<element>` oder `<attribute>` Elementen.
* Link `<element>` : definiert einen Link. Diese Elemente müssen das Attribut &quot;@type=link&quot;enthalten.
* XML `<element>` : definiert ein Textfeld vom Typ &quot;mData&quot;. Dieses Element muss das Attribut &quot;@type=xml&quot;enthalten.

### Attributbeschreibung {#attribute-description-4}

* **_operation (string)**: definiert den Typ des Schreibens in der Datenbank.

   Dieses Attribut wird hauptsächlich beim Erweitern von vordefinierten Schemas verwendet.

   Barrierefreie Werte sind:

   * &quot;none&quot;: Aussöhnung allein. Das bedeutet, dass Adobe Campaign das Element wiederherstellt, ohne es zu aktualisieren, oder einen Fehler erzeugt, wenn es nicht vorhanden ist.
   * &quot;insertOrUpdate&quot;: mit Einfügen aktualisieren. Das bedeutet, dass Adobe Campaign das Element aktualisiert oder erstellt, wenn es nicht vorhanden ist.
   * &quot;insert&quot;: Einfügen. Das bedeutet, dass Adobe Campaign das Element einfügt, ohne zu prüfen, ob es vorhanden ist.
   * &quot;update&quot;: aktualisieren. Das bedeutet, dass Adobe Campaign das Element aktualisiert oder einen Fehler erzeugt, wenn es nicht vorhanden ist.
   * &quot;delete&quot;: löschen. Das bedeutet, dass Adobe Campaign Elemente wiederherstellt und löscht.

* **advanced (boolean)**: Wenn diese Option aktiviert ist (@advanced=&quot;true&quot;), können Sie das Attribut auf der Liste der verfügbaren Felder ausblenden, auf die Sie zur Konfiguration einer Liste in einem Formular zugreifen können.
* **aggregat (Zeichenfolge)**: können Sie die Definition eines Begriffs `<element>` über ein anderes Schema kopieren. Dieses Attribut erhält eine Schema-Deklaration in Form eines &quot;Namensraum:name&quot;.
* **applyIf (Zeichenfolge)**: Bedingung für die Anwendung des Indexes. Dieses Attribut erhält einen XTK-Ausdruck.
* **autopk (boolean)**: Wenn diese Option aktiviert ist (autopk=&quot;true&quot;), wird automatisch ein eindeutiger Schlüssel definiert. Diese Option kann nur für das Hauptelement des Schemas verwendet werden. Warnung: Adobe Campaign garantiert nur, dass der generierte Schlüssel eindeutig ist. Es ist nicht garantiert, dass die Schlüsselwerte nacheinander und inkrementell sind.
* **dataPolicy (Zeichenfolge)**: ermöglicht Ihnen die Angabe von Genehmigungsbeschränkungen für die im SQL-Feld zulässigen Werte. Die Werte für dieses Attribut lauten:

   * &quot;none&quot;: no value
   * &quot;smartCase&quot;: Großbuchstabe
   * &quot;lowerCase&quot;: Kleinbuchstabe
   * &quot;upperCase&quot;: Großbuchstabe
   * &quot;email&quot;: E-Mail-Adresse
   * &quot;phone&quot;: Telefonnummer
   * &quot;identifier&quot;: Bezeichnername
   * &quot;resIdentifier&quot;: Dateiname

* **dbEnum (Zeichenfolge)**: erhält den internen Namen einer &quot;geschlossenen&quot;Auflistung. Die Werte für die Auflistung müssen in der `<srcschema>`definiert werden.
* **defOnDuplicate (boolean)**: Wenn dieses Attribut aktiviert ist, wird bei der Duplizierung eines Datensatzes der (in &quot;@default&quot;definierte) Standardwert automatisch erneut auf den Datensatz angewendet.
* **default (Zeichenfolge)**: ermöglicht die Definition des Elementverhaltens (Aufruf einer Funktion, Standardwert). Dieses Attribut erhält einen XTK-Ausdruck.
* **desc (Zeichenfolge)**: können Sie eine Beschreibung des Elements einfügen. Diese Beschreibung wird in der Statusleiste der Benutzeroberfläche angezeigt.
* **displayAsField (boolean)**: Wenn dieses Attribut aktiviert ist, `<element>` wird ein &quot;Link&quot;-Typ als Feld in der Ansicht der Schema (&quot;Struktur&quot;, Registerkarte &quot;Struktur&quot;) angezeigt. Auf diese Weise können Sie einen Link als lokales Feld anzeigen und das Verhalten während einer Abfrage ändern. Wenn das Element in der SELECT-Anweisung einer Abfrage gefunden wird, wird der Wert der Link-Zielgruppe verwendet. Wenn das Element im WO einer Abfrage gefunden wird, wird der zugrunde liegende Schlüssel des Links verwendet.
* **edit (string)**: Dieses Attribut gibt den Typ der Eingabe an, die im mit dem Schema verknüpften Formular verwendet wird.
* **enum (Zeichenfolge)**: erhält den Namen der Auflistung, die mit dem Feld verknüpft ist. Die Auflistung kann in dasselbe Schema oder in ein Remote-Schema eingefügt werden.
* **expr (Zeichenfolge)**: Dieses Attribut definiert ein berechnetes Feld, für das keine Definition in der Tabelle gespeichert ist. Es empfängt einen Xpath- oder einen XTK-Ausdruck (Zeichenfolge).
* **externalJoin (boolean)**: externe Verknüpfung in einem Element vom Typ &quot;Link&quot;.
* **Funktion (Zeichenfolge)**: definiert ein Kennzeichenfeld: Diese Felder dienen zum Erweitern der Daten in einer vorhandenen Tabelle, jedoch mit Datenspeicherung in einer Anhang-Tabelle. Akzeptierte Werte sind:

   * &quot;shared&quot;: der Inhalt in einer freigegebenen Tabelle nach Datentyp gespeichert wird
   * &quot;dediziert&quot;: der Inhalt in einer speziellen Tabelle gespeichert wird

   Die Tabellen mit SQL-Eigenschaften werden automatisch anhand des charakteristischen Typs erstellt:

   * dediziert: `Ft_[name_of_the_schema_containing_the_characteristic]_[name_of_the_characteristic]`
   * shared: `Ft_[type_of_key_of_the_schema_containing_the_characteristic]_[type_of_the_characteristic]`

   Es gibt zwei Arten von Eigenschaftenfeldern: einfache Felder, in denen ein einzelner Wert für das Merkmal autorisiert ist, und Mehrfachauswahlfelder, in denen das Merkmal mit einem Collection-Element verknüpft ist, das mehrere Werte enthalten kann.

   Wenn ein Merkmal in einem Schema definiert ist, muss dieses Schema einen Hauptschlüssel haben, der auf einem einzigen Feld basiert (Composite-Schlüssel sind nicht autorisiert).

* **featureDate (boolean)**: -Attribut, das mit dem Charakteristikumsfeld &quot;@feature&quot;verknüpft ist. Wenn der Wert &quot;true&quot;ist, können Sie feststellen, wann der Wert zuletzt aktualisiert wurde.
* **filterPath (string)**: Dieses Attribut empfängt einen Xpath und ermöglicht Ihnen, einen Filter für ein Feld zu definieren.
* **folderLink (Zeichenfolge)**: Dieses Attribut erhält den Namen des Links, über den Sie die Dateien wiederherstellen können, die Entitäten enthalten.
* **folderModel (string)**: definiert den Ordnertyp, der die Entitäts-Datenspeicherung aktiviert. Dieses Attribut ist nur definiert, wenn &quot;@folderLink&quot;vorhanden ist.
* **folderProcess (string)**: definiert den Link, unter dem Entitätsmodellinstanzen gespeichert werden. Dieses Attribut ist nur definiert, wenn &quot;@folderLink&quot;vorhanden ist.
* **fullLoad (boolean)**: Dieses Attribut erzwingt die Anzeige aller Datensätze in einer Tabelle während der Feldauswahl in einem Formular.
* **img (Zeichenfolge)**: empfängt den Pfad eines Bildes, das mit einem Element verknüpft ist. Der Wert dieses Attributs ist vom Typ &quot;Namensraum:Name des Bilds&quot;. Beispiel: img=&quot;cus:myImage.jpg&quot;. Das Bild muss physisch auf den Anwendungsserver importiert werden.
* **integer (Zeichenfolge)**: Referenzintegrität des Vorkommens der Quelltabelle in Richtung der Zielgruppe.

   Barrierefreie Werte sind:

   * &quot;definieren&quot;: Adobe Campaign löscht die Entität nicht, wenn sie über den Link referenziert wird
   * &quot;normal&quot;: Wenn Sie das Quellvorkommen löschen, werden die Schlüssel des Links beim Auftreten der Zielgruppe initialisiert (Standardmodus). Bei diesem Integritätsmodus werden alle Fremdschlüssel initialisiert
   * &quot;own&quot;: Löschen des Quellvorkommens löscht das Löschen des Vorkommens der Zielgruppe
   * &quot;Kopie&quot;: ähnlich wie &quot;eigene&quot;(bei Löschung) oder Duplikate (bei Vervielfältigung)
   * &quot;neutral&quot;: tut nichts

* **label (Zeichenfolge)**: Elementbezeichnung.
* **labelSingular (Zeichenfolge)**: label (Singular form) des Elements, das in einigen Teilen der Oberfläche verwendet wird.
* **length (Zeichenfolge)**: max. Anzahl der Zeichen, die für einen Wert des SQL-Felds vom Typ &quot;String&quot;autorisiert sind.
* **localizable (boolean)**: Wenn es aktiviert ist, weist dieses Attribut das Erfassungswerkzeug an, den Wert des Attributs &quot;@label&quot;für die Übersetzung wiederherzustellen (interne Verwendung).
* **name (MNTOKEN)**: interner Name des Elements, das mit dem Namen der Tabelle übereinstimmt. Der Wert des Attributs &quot;@name&quot;muss kurz sein, vorzugsweise in Englisch, und mit XML verknüpfte Benennungsbeschränkungen einhalten.

   Wenn das Schema in die Datenbank geschrieben wird, werden dem Feldnamen automatisch Präfixe per Adobe Campaign hinzugefügt.

   * &quot;i&quot;: Präfix für den Integer-Typ.
   * &quot;d&quot;: Präfix für den Typ &quot;Dublette&quot;.
   * &quot;s&quot;: Präfix für den Zeichenfolgen-Typ.
   * &quot;ts&quot;: Präfix für den Typ &quot;Datum&quot;.

   Um den Tabellennamen autonom zu definieren, müssen Sie das Attribut &quot;@sqltable&quot;in der Definition des Hauptelements Schema verwenden.

* **noDbIndex (boolean)**: können Sie angeben, dass das Element nicht indiziert werden soll.
* **geordnet (boolean)**: Wenn das Attribut aktiviert ist (ordered=&quot;true&quot;), behält Adobe Campaign die Elementdeklarationssequenz in einem XML-Collection-Element bei.
* **pkSequence (Zeichenfolge)**: erhält den Namen der Sequenz, die für die Berechnung eines automatisch inkrementellen Schlüssels verwendet wird. Dieses Attribut kann nur verwendet werden, wenn im Stammelement des Schemas ein Schlüssel für die automatische Inkrementierung definiert ist.
* **pkgStatus (Zeichenfolge)**: bei Paketexporten werden Werte in Abhängigkeit vom Wert dieses Attributs berücksichtigt:

   * &quot;immer&quot;: das Element immer vorhanden ist
   * &quot;never&quot;: das Element nie vorhanden ist
   * &quot;default (or nothing)&quot;: das Element wird exportiert, es sei denn, es ist das Standardelement oder kein internes Feld und ist nicht mit anderen Instanzen kompatibel

* **ref (string)**: Dieses Attribut definiert einen Verweis auf ein >element>-Element, das von mehreren Schemas gemeinsam verwendet wird (Definition Factoring). Die Definition wird nicht in das aktuelle Schema kopiert.
* **erforderlich (Boolescher Wert)**: Wenn dieses Attribut aktiviert ist (@required=&quot;true&quot;), wird das Feld in der Oberfläche markiert. Die Beschriftung des Felds wird in Formularen rot dargestellt.
* **revAdvanced (boolean)**: bei Aktivierung gibt dieses Attribut an, dass der umgekehrte Link ein &quot;erweiterter&quot;Link ist.
* **revCardinality (Zeichenfolge)**: Dieses Attribut definiert die Kardinalität eines Links zwischen zwei Tabellen. Es wird in einem &quot;Link&quot;-Typ verwendet `<element>`.

   Mögliche Werte:

   * &quot;single&quot; : Einfacher 1-1-Typ-Link
   * &quot;ungebunden&quot;: Sammlungslink für 1-N-Typ

   Wenn das Attribut bei der Linkerstellung nicht angegeben wird, ist die Kardinalität standardmäßig 1-N.

* **revDesc (Zeichenfolge)**: Dieses Attribut erhält eine Beschreibung, die mit dem anderen Link verknüpft ist.
* **revExternalJoin (boolean)**: Wenn dieses Attribut aktiviert ist, können Sie die externe Verbindung zum anderen Link erzwingen.
* **revIntegrity (Zeichenfolge)**: Dieses Attribut definiert die Integrität des Schemas Zielgruppe. Es werden dieselben Werte wie das Attribut &quot;@integer&quot;autorisiert. Standardmäßig gibt Adobe Campaign diesem Attribut den &quot;normalen&quot;Wert zu.
* **revLabel (Zeichenfolge)**: Beschriftung des Gegenlinks.
* **revLink (Zeichenfolge)**: Name des anderen Links. Lautet der Wert &quot;_KEINE_&quot;, wird im Schema &quot;Ziel&quot;kein gegenteiliger Link erstellt.
* **revTarget (Zeichenfolge)**: zielgruppe des gegenteiligen Links.
* **sql (boolean)**: Wenn dieses Attribut aktiviert ist (@sql=&quot;true&quot;), erzwingt es die Datenspeicherung des SQL-Elements, auch wenn das Element die Eigenschaft xml=&quot;true&quot; hat.
* **sqlname (Zeichenfolge)**: Name des Felds bei der Tabellenerstellung. Wenn &quot;@sqlname&quot;nicht angegeben ist, wird der Wert des Attributs &quot;@name&quot;standardmäßig verwendet. Beim Schreiben des Schemas in die Tabelle werden je nach Feldtyp automatisch Präfixe hinzugefügt.
* **sqltable (Zeichenfolge)**: für das Hauptelement des Schemas, überschreibt dieses Attribut den standardmäßig generierten Namen der SQL-Tabelle. Wenn &quot;@sqltable&quot;nicht angegeben ist, wird der Standardname wie folgt strukturiert: namensraum (Groß-/Kleinschreibung des ersten Buchstabens) gefolgt vom Wert des SrcSchema &quot;@name&quot;.
* **tableSpace (Zeichenfolge)**: Mit diesem Attribut können Sie eine neue Datenspeicherung für Tablespace für eine Tabelle angeben (gültig im Stammverzeichnis `<element>`).
* **tableSpaceIndex (Zeichenfolge)**: Mit diesem Attribut können Sie einen neuen Tabellenraum für die Index-Datenspeicherung angeben (gültig im Stammverzeichnis `<element>`).
* **zielgruppe (MNTOKEN)**: erhält beim Erstellen einer Verknüpfung zwischen Tabellen den Namen des Schemas Zielgruppe. Dieses Attribut ist nur für Elemente des Typs &quot;Link&quot;aktiv.
* **template (string)**: Dieses Attribut definiert einen Verweis auf ein `<element>` Element, das von mehreren Schemas gemeinsam verwendet wird. Die Definition wird automatisch in das aktuelle Schema kopiert.
* **translateDefault (Zeichenfolge)**: Wenn ein Attribut &quot;@default&quot;gefunden wird, können Sie mit &quot;@translatedDefault&quot;einen Ausdruck neu definieren, der mit dem in &quot;@default&quot;definierten übereinstimmt und vom Übersetzungstool erfasst wird (interner Einsatz).
* **translationExpr (Zeichenfolge)**: Wenn ein Attribut &quot;@expr&quot;gefunden wird, können Sie mit dem Attribut &quot;@translatedExpr&quot;einen Ausdruck neu definieren, der mit dem in &quot;@expr&quot;definierten übereinstimmt und vom Übersetzungstool erfasst wird (interne Verwendung).
* **type (MNTOKEN)**: definiert den Typ der im Element gespeicherten Daten.

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

* **ungebunden (boolean)**: Wenn das Attribut aktiviert ist (unbound=&quot;true&quot;), wird der Link als Collection-Element für eine 1-N-Kardinalität deklariert.
* **userEnum (Zeichenfolge)**: erhält den internen Namen einer &quot;offenen&quot;Auflistung. Auflistungen können vom Benutzer in der Benutzeroberfläche definiert werden.
* **xml (boolean)**: Wenn diese Option aktiviert ist, werden alle im Element definierten Werte in XML in einem Feld vom Typ &quot;mData&quot;gespeichert. Das bedeutet, dass diese Felder nicht gefiltert oder sortiert werden.
* **xmlChildren (boolean)**: erzwingt die Datenspeicherung für jedes Kind ( `<element>  or  <attribute>   ) of the   <element>    element in an XML document.   </element>  </attribute> </element>`

## `<enumeration>` Element {#enumeration--element}

### Inhaltsmodell {#content-model-5}

auflistung:==(help| value)

### Attribute {#attributes-5}

* @basetype (Zeichenfolge)
* @default (Zeichenfolge)
* @desc (Zeichenfolge)
* @label (Zeichenfolge)
* @name (Zeichenfolge)
* @template (Zeichenfolge)

### Eltern {#parents-5}

`<srcschema>`

### Kinder {#children-5}

* `<help>`
* `<value>`

### Beschreibung {#description-5}

Mit diesem Element können wir eine Auflistung definieren. Eine Auflistung gehört zu dem Schema, in dem sie definiert ist, ist jedoch über ein anderes Schema verfügbar.

### Verwendung und Kontext {#use-and-context-of-use-4}

Auflistungen werden am Beginn eines Schemas definiert (bevor das Hauptelement definiert wird).

### Attributbeschreibung {#attribute-description-5}

* **basetype (Zeichenfolge)**: Typ der in der Auflistung gespeicherten Werte.

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
   * DOMDocument
   * DOMElement
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

* **default (Zeichenfolge)**: Standardwert. Der Standardwert kann auch einer der in der Auflistung definierten Werte sein.
* **desc (Zeichenfolge)**: Beschreibung der Auflistung.
* **label (Zeichenfolge)**: Beschriftung der Auflistung.
* **name (Zeichenfolge)**: interner Name der Auflistung.
* **template (string)**: Dieses Attribut definiert einen Verweis auf ein `<enumeration>` Element, das von mehreren Schemas gemeinsam verwendet wird. Die Definition wird automatisch in das aktuelle Schema kopiert.

### Beispiele {#examples-4}

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

Definition einer Auflistung mit einem Standardwert:

```
 <enumeration basetype="byte" default="email" name="canal">
    <value label="Email" name="email" value="0"/> 
    <value label="Téléphone" name="phone" value="1"/>
    <value label="Call Center" name="callcenter" value="2"/>
 </enumeration>
```

## `<help>` Element {#help--element}

### Inhaltsmodell {#content-model-6}

help:==EMPTY

### Attribute {#attributes-6}

Keiner

### Eltern {#parents-6}

`<srcschema>`  ,  `<element>`   ,   `<attribute>`    ,    `<enumeration>`     ,     `<value>`      ,     `<param />`,      `<method />`

### Kinder {#children-6}

Keiner

### Beschreibung {#description-6}

Mit diesem Element können Sie ein `<element>` oder `<attribute>` -Element beschreiben. Es darf nur Text enthalten und wird in XML in der Datenbank gespeichert.

### Attributbeschreibung {#attribute-description-6}

Dieses Element hat keine Attribute.

### Beispiele {#examples-5}

```
<method name="CheckOperation" static="true"
      <helpchecks the validity of a campaign</help
...
</method> 
```

## `<join>` Element {#join--element}

### Inhaltsmodell {#content-model-7}

join:==EMPTY

### Attribute {#attributes-7}

* @dstFilterExpr (Zeichenfolge)
* @xpath-dst (Zeichenfolge)
* @xpath-src (Zeichenfolge)

### Eltern {#parents-7}

`<element>`

### Kinder {#children-7}

Keiner

### Beschreibung {#description-7}

Hiermit können Sie die Felder definieren, die eine Verbindung zwischen SQL-Tabellen erstellen.

### Verwendung und Kontext {#use-and-context-of-use-5}

Ein `<join>` Element kann nur verwendet werden, wenn das übergeordnete `<element>` Element vom Typ &quot;link&quot;ist. Das bedeutet, dass für das übergeordnete Element das Attribut &quot;@type=link&quot;deklariert sein muss.

Es ist nicht erforderlich, den Namen und den Namensraum der Remote-Tabelle im `<join>` Element anzugeben. Sie müssen im übergeordneten Element angegeben werden `<element>`.

Standardmäßig werden Links am Ende des Schemas definiert.

Wenn das `<join>` Element bei der Definition des Linktypelements nicht angegeben ist, wird der Link automatisch auf den primären Schlüsseln beider Tabellen platziert.

### Attributbeschreibung {#attribute-description-7}

* **dstFilterExpr (Zeichenfolge)**: Mit diesem Attribut können Sie die Anzahl der zulässigen Werte in der Remote-Tabelle einschränken.
* **xpath-dst (Zeichenfolge)**: Dieses Attribut erhält einen Xpath (@name-Attribut der Remote-Tabelle).
* **xpath-src (Zeichenfolge)**: Dieses Attribut erhält einen Xpath (@name-Attribut im aktuellen Schema).

### Beispiele {#examples-6}

Link zwischen dem Feld &quot;E-Mail&quot;der aktuellen Tabelle und dem Feld &quot;@company-id&quot;der Remote-Tabelle:

```
<join xpath-dst="@compagny-id" xpath-src="@email"/>
```

Gefilterter Link zur Tabelle &quot;cus:Country&quot;basierend auf dem Inhalt des Felds &quot;@country&quot;, das den Wert &quot;EN&quot;enthalten muss:

```
<element name="StockEN" type="link" label="MyLink" target="cus:Stock">
   <join xpath-dst="@country" xpath-src="@code" dstFilterExpr="@country = 'EN'"/>
 </element>
```

## `<key>` Element {#key--element}

### Inhaltsmodell {#content-model-8}

key:==keyfield

### Attribute {#attributes-8}

* @allowEmptyPart (boolean)
* @applyIf (Zeichenfolge)
* @internal (boolean)
* @label (Zeichenfolge)
* @name (MNTOKEN)
* @noDbIndex (boolean)

### Eltern {#parents-8}

`<element>`

### Kinder {#children-8}

`<keyfield>`

### Beschreibung {#description-8}

Mit diesem Element können Sie einen Schlüssel zur Identifizierung eines Datensatzes in der Tabelle definieren.

Eine Tabelle muss mindestens einen Schlüssel haben.

### Verwendung und Kontext {#use-and-context-of-use-6}

In der Regel werden Schlüssel nach dem Hauptelement des Schemas und den Indizes deklariert.

Ein Schlüssel wird als &quot;Composite&quot;bezeichnet, wenn er mehrere Felder enthält (d. h. mehrere `<keyfield>` untergeordnete Felder). Verwenden Sie keinen zusammengesetzten Schlüssel, um einen primären Schlüssel zu definieren.

Wenn das Hauptelement des Schemas das Attribut &quot;@autopk=true&quot;enthält, ist der Primärschlüssel eindeutig. Wir können nur einen Primärschlüssel pro Schema haben.

Die ersten 1000 Bezeichner sind reserviert. Wenn also ein Wertebereich für Schlüssel definiert werden muss, ist der Beginn bei 1000.

### Attributbeschreibung {#attribute-description-8}

* **allowEmptyPart (boolean)**: bei einem zusammengesetzten Schlüssel, wenn dieses Attribut aktiviert ist, wird der Schlüssel als gültig betrachtet, wenn mindestens einer der Schlüssel nicht leer ist. Ist dies der Fall, ist der leere Vorgabewert &quot;0&quot;(boolesch oder für alle Arten numerischer Daten). Standardmäßig müssen alle Schlüssel, aus denen ein Composite-Schlüssel besteht, eingegeben werden.
* **applyIf (Zeichenfolge)**: Mit diesem Attribut können Sie den Schlüssel optional machen. Er definiert die Bedingung, nach der die Schlüsseldefinition angewendet wird. Dieses Attribut erhält einen XTK-Ausdruck.
* **internal (boolean)**: Wenn es aktiviert ist, zeigt dieses Attribut Adobe Campaign an, dass der Schlüssel primär ist.
* **label (Zeichenfolge)**: Beschriftung des Schlüssels.
* **name (MNTOKEN)**: interner Name des Schlüssels.
* **noDbIndex (boolean)**: Wenn es aktiviert ist (noDbIndex=&quot;true&quot;), wird das Feld, das dem Schlüssel entspricht, nicht indiziert.

### Beispiele {#examples-------}

Deklaration eines zusammengesetzten Schlüssels, der das Feld &quot;@expr&quot;oder &quot;alias&quot;leer lässt:

```
<key name="node" allowEmptyPart="true">
  <keyfield xpath="@expr"/>
   <keyfield xpath="@alias"/>
 </key>
```

Erklärung eines Primärschlüssels im Feld &quot;Name&quot; des STRING-Typs in einer `<srcschema>` und der entsprechenden SQL-Abfrage:

```
 
<key name="PrimaryKey" internal="true">  
  <keyfield xpath="@name"/>
</key>

CREATE UNIQUE INDEX Schema_PrimaryKey ON Schema(sName);
```

## `<keyfield>` Element {#keyfield--element}

### Inhaltsmodell {#content-model-9}

keyfield:==EMPTY

### Attribute {#attributes-9}

* @xlink (MNTOKEN)
* @xpath (MNTOKEN)

### Eltern {#parents-9}

`<key>`  ,  `<dbindex />`

### Kinder {#children-9}

Keiner

### Beschreibung {#description-9}

Dieses Element definiert die Felder, die in einen Index oder Schlüssel integriert werden sollen.

### Attributbeschreibung {#attribute-description-9}

* **xlink (MNTOKEN)**: können Sie automatisch auf Fremdschlüssel verweisen, die in der Verknüpfung für eine Beziehungstabelle (N-N-Link) definiert sind.
* **xpath (MNTOKEN)**: Definition eines Indexes oder eines Schlüssels für ein `<attribute>` Element. Dieses Attribut erhält einen Xpath, der den Pfad zum Schema-Attribut definiert, das den Schlüssel oder den Index definiert.

### Beispiele {#examples-}

Auswahl des Felds &quot;sName&quot;in einem Index mit einem Xpath auf &quot;@name&quot;:

```
<keyfield xpath="@name"/>
```

## `<method>` Element {#method--element}

### Inhaltsmodell {#content-model-10}

Methode:==( help | Parameter)

### Attribute {#attributes-10}

* @_operation (Zeichenfolge)
* @access (Zeichenfolge)
* @const (boolean)
* @hidden (boolean)
* @label (Zeichenfolge)
* @library (string)
* @name (MNTOKEN)
* @pkonly (boolean)
* @static (boolean)

### Eltern {#parents-10}

`<methods>`  ,  `<interface />`

### Kinder {#children-10}

* `<help>`
* `<parameters>`

### Beschreibung {#description-10}

Mit diesem Element können Sie eine SOAP-Methode definieren.

### Verwendung und Kontext {#use-and-context-of-use-7}

SOAP-Methoden ermöglichen Anwendungsprozesse.

Die &quot;@library&quot;ist erforderlich, um eine neue Methode zu deklarieren (nicht native): der Namensraum und der Bibliotheksname sind unabhängig vom Namensraum und vom Namen des Schemas, in dem die Deklaration enthalten ist.

### Attributbeschreibung {#attribute-description-10}

* **access (Zeichenfolge)**: Dieses Attribut definiert die Zugriffskontrolle für die Verwendung der Methode. Wenn dieses Attribut fehlt, ist die Identifizierung obligatorisch. Verfügbare Werte sind: &#39;anonymous&#39;, &#39;admin&#39; und &#39;sql&#39;.
* **const (boolean)**: Wenn es aktiviert ist, bedeutet dieses Attribut, dass die deklarierte Methode die Entität ändert
* **label (Zeichenfolge)**: Bezeichnung der Methode.
* **library (string)**: Diese Methode ist nicht nativ für die Anwendung. Dieses Attribut nimmt den Wert der Methodenbibliothek ein, in der die Methodendefinition gefunden wird (nms:mylibrary.js).
* **name (MNTOKEN)**: eindeutiger Methodenname.
* **statisch (boolean)**: Wenn dieses Attribut aktiviert ist, wird die Methode als autonom betrachtet, müssen alle Parameter bei Aufruf der Methode angegeben werden.

### Beispiele {#examples-7}

Definition der Out-of-the-Box-Methode &quot;Abonnieren&quot;:

```
 
<method name="Subscribe" static="true">
      <help>Creation of update of a recipient's subscription to an information service</help>
      <parameters>
        <param desc="Name of the information service(s) (separated with commas)"
               name="serviceName" type="string"/>
        <param desc="Recipient to subscribe and possibly create" name="recipient"
               type="DOMElement"/>
        <param desc="Create the recipient if they don't exist" name="create" type="boolean"/>
      </parameters>     
    </method>
```

## `<methods>` Element {#methods--element}

### Inhaltsmodell {#content-model-11}

Methoden:==Methode

### Attribute {#attributes-11}

Keiner

### Eltern {#parents-11}

`<srcschema>`

### Kinder {#children-11}

method

### Beschreibung {#description-11}

Mit diesem Element können Sie ein `<method>` Element definieren. Die Angabe einer Methode ist obligatorisch.

### Attributbeschreibung {#attribute-description-11}

Dieses Element hat keine Attribute.

### Beispiele {#examples-8}

```
<methods async="true"
...// definition of one or more <method
</methods>
```

## `<param>` Element {#param--element}

### Inhaltsmodell {#content-model-12}

param:==help

### Attribute {#attributes-12}

* @_operation (Zeichenfolge)
* @desc (Zeichenfolge)
* @enum (Zeichenfolge)
* @inout (Zeichenfolge)
* @label (Zeichenfolge)
* @localizable (Zeichenfolge)
* @name (MNTOKEN)
* @Namensraum (MNTOKEN)
* @type (Zeichenfolge)

### Eltern {#parents-12}

`<parameters>`

### Kinder {#children-12}

`<help>`

### Beschreibung {#description-12}

Mit diesem Element können Sie einen Parameter zum Aufrufen einer SOAP-Methode definieren.

### Attributbeschreibung {#attribute-description-12}

* **desc (Zeichenfolge)**: Beschreibung, die das `<param>` Element betrifft.
* **inout (Zeichenfolge)**: Dieses Attribut definiert, ob sich der Parameter am Eingang (in) oder an der Ausgabe (out) des SOAP-Aufrufs befindet. Wenn dieses Attribut nicht angegeben ist, lautet der Standardparameter input (&quot;@inout=in&quot;).
* **label (Zeichenfolge)**: `<param>` label
* **localizable (Zeichenfolge)**: Wenn es aktiviert ist, weist dieses Attribut das Erfassungswerkzeug an, den Wert des Attributs &quot;@label&quot;für die Übersetzung wiederherzustellen (interne Verwendung).
* **name (MNTOKEN)**: interner Name der `<param>`
* **type (string)**: Dieses Attribut definiert den Typ des `<param>` Elements

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
   * DOMDocument
   * DOMElement
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

### Beispiele {#examples-9}

Definition der Einstellung &quot;serviceName&quot; für den Zeichenfolgentyp:

```
<param desc="Name of the information service(s) (separated with commas)"
               name="serviceName" type="string" inout="in"/>
```

## `<parameters>` Element {#parameters--element}

### Inhaltsmodell {#content-model-13}

parameters:==param

### Attribute {#attributes-13}

Keiner

### Eltern {#parents-13}

`<method>`

### Kinder {#children-13}

`<param>`

### Beschreibung {#description-13}

Dieses Element definiert eine Gruppe von `<parameter>` Elementen.

### Verwendung und Kontext {#use-and-context-of-use-8}

Dieses Element ist obligatorisch, auch für ein einzelnes `<param>` untergeordnetes Element des `<method>` Elements.

### Attributbeschreibung {#attribute-description-13}

Keiner

### Beispiele {#examples-10}

```
<parameters
... //definition of one or more <param
</parameters>
```

## `<srcschema>` Element {#srcschema--element}

### Inhaltsmodell {#content-model-14}

srcSchema:==(attribute | createdBy | data | element | Auflistung | help | Schnittstelle | Methoden | modifyBy)

### Attribute {#attributes-14}

created (datetime), createdBy-id (long), desc (string), entitySchema (string), extendedSchema (string), img (string), implements (string), label (string), labelSingular (string), lastModified (datetime), library (boolean), mappingType (string), modifyBy-id (long), name (string), Namensraum,  (Zeichenfolge), useRecycleBin (boolean), Ansicht (boolean), xtkschema (Zeichenfolge)

### Eltern {#parents-14}

Keiner

### Kinder {#children-14}

* `<attribute>`
* `<createdby>`
* `<data>`
* `<element>`
* `<enumeration>`
* `<help>`
* `<interface>`
* `<methods>`
* `<modifiedby>`

### Beschreibung {#description-14}

Das `<srcschema>` ist das Stammelement eines Schemas. Es ist der Eingabepunkt für die Definition des Schemas.

### Verwendung und Kontext {#use-and-context-of-use-9}

Die Präsentation zum Schema finden Sie unter [Informationen zu Schema-Referenz](../../configuration/using/about-schema-reference.md) und [Schema-Struktur](../../configuration/using/schema-structure.md).

### Attributbeschreibung {#attribute-description-14}

* **created (dattime)**: Dieses Attribut enthält Informationen zum Datum und zur Uhrzeit der Erstellung des Schemas. Es enthält das Formular &quot;Date Time&quot;. Die angezeigten Werte werden vom Server übernommen. Die Uhrzeit wird im UTC-Format angezeigt.
* **createdBy-id (long)**: ist die Kennung des Operators, der das Schema erstellt hat.
* **desc (Zeichenfolge)**: Beschreibung des Schemas
* **entitySchema (Zeichenfolge)**: Basis-Schema, auf dem Syntax und Genehmigung basieren (zum Adobe Campaign standardmäßig): xtk:srcSchema). Wenn Sie das aktuelle Schema speichern, genehmigt Adobe Campaign seine Grammatik mit dem im @xtkschema-Attribut deklarierten Schema.
* **extendedSchema (Zeichenfolge)**: erhält den Namen des vordefinierten Schemas, auf dem die aktuelle Schema-Erweiterung basiert. Das Formular lautet &quot;Namensraum:Name&quot;.
* **img (Zeichenfolge)**: mit dem Schema verknüpft ist (kann im Assistenten zum Erstellen von Schemas definiert werden).
* **label (Zeichenfolge)**: Beschriftung des Schemas.
* **labelSingular (Zeichenfolge)**: Beschriftung (Singular) für die Anzeige in der Schnittstelle.
* **lastModified (datetime)**: Dieses Attribut enthält Informationen zum Datum und zur Uhrzeit der letzten Änderung. Es enthält das Formular &quot;Date Time&quot;. Die angezeigten Werte werden vom Server übernommen. Die Uhrzeit wird im UTC-Format angezeigt.
* **library (boolean)**: Verwendung des Schemas als Bibliothek und nicht als Entität. Dieses Schema kann daher von anderen Schemas mithilfe der Attribute &quot;@ref&quot;und &quot;@template&quot;referenziert werden.
* **mappingType (Zeichenfolge)**:

   * &quot;sql&quot;: Datenbankzuordnung
   * &quot;textFile&quot;: Textdateizuordnung
   * &quot;xmlFile&quot;: Textdateizuordnung im XML-Format
   * &quot;inaryFile&quot;: Binäre Dateizuordnung

* **modifyBy-id (long)**: entspricht der Kennung des Operators, der das Schema geändert hat.
* **name (Zeichenfolge)**: eindeutiger Name des Schemas.
* **namensraum (Zeichenfolge)**: namensraum des Schemas (Standard: nms, xtk, nl). Beim Erstellen eines neuen Schemas für ein Projekt wird empfohlen, einen eigenen Namensraum zu verwenden.
* **useRecycleBin (boolean)**: Aktiviert die Funktion &quot;Papierkorb&quot;in der Anwendung. Gelöschte Datensätze werden vor der endgültigen Löschung in den Papierkorb gelegt. Diese Funktion ist nur im Versand-Modus verfügbar.
* **ansicht (boolean)**: Wenn es aktiviert ist (@Ansicht=&quot;true&quot;), wird das Schema als Ansicht verwendet. Der Assistent zum Aktualisieren der Datenbankstruktur berücksichtigt das Schema nicht. Diese Option wird hauptsächlich für den Verweis auf externe Tabellen verwendet.
* **xtkschema (Zeichenfolge)**: Name des Schemas, das die Schema-Grammatik definiert (standardmäßig xtk:srcSchema).

### Beispiele {#examples-11}

`<srcschema>` -Element des Schemas &quot;nms:Versand&quot;

```
<srcSchema desc="Defines all the settings of a delivery (or delivery template)."  
           entitySchema="xtk:srcSchema" img="nms:campaign.png" implements="xtk:persist" 
           label="Diffusions" labelSingular="Diffusion" md5="DCD2164CD0276B1DCA6E1C9E2A75EC04"
           name="delivery" namespace="nms" useRecycleBin="true" xtkschema="xtk:srcSchema">
```

## `<sysfilter>` Element {#sysfilter--element}

### Inhaltsmodell {#content-model-15}

sysFilter:==Bedingung

### Attribute {#attributes-15}

Keiner

### Eltern {#parents-15}

`<element>`

### Kinder {#children-15}

`<condition>`

### Beschreibung {#description-15}

Mit diesem Element können Sie einen Filter definieren.

### Attributbeschreibung {#attribute-description-15}

Dieses Element hat keine Attribute.

### Beispiele {#examples-12}

Definition eines Filters mit einer Bedingung für das @name-Attribut:

```
<sysFilter>
      <condition expr="@name ='Doe'"/>
  <sysFilter>
```

## `<value>` Element {#value--element}

### Inhaltsmodell {#content-model-16}

value:==help

### Attribute {#attributes-16}

* @applyIf (Zeichenfolge)
* @desc (Zeichenfolge)
* @enabledIf (Zeichenfolge)
* @img (Zeichenfolge)
* @label (Zeichenfolge)
* @name (Zeichenfolge)
* @value (Zeichenfolge)

### Eltern {#parents-16}

`<enumeration>`

### Kinder {#children-16}

`<help>`

### Beschreibung {#description-16}

Mit diesem Element können Sie die in einer Auflistung gespeicherten Werte definieren.

### Attributbeschreibung {#attribute-description-16}

* **applyIf (Zeichenfolge)**: Mit diesem Attribut können Sie einen Auflistung-Wert als optional definieren. Es erhält einen XTK-Ausdruck.
* **desc (Zeichenfolge)**: Beschreibung der Auflistung.
* **enabledIf (Zeichenfolge)**: Bedingung zum Aktivieren des Auflistung-Werts.
* **img (Zeichenfolge)**: Bild, das mit der Auflistung im Formular &quot;Namensraum:image_name&quot;verknüpft ist. Das Bild muss auf den Anwendungsserver importiert werden.
* **label (Zeichenfolge)**: Beschriftung des Auflistung-Werts.
* **name (Zeichenfolge)**: interner Name des Wertes der Auflistung.
* **Wert (Zeichenfolge)**: Wert der Auflistung. Der Werttyp wird basierend auf dem Typ der Auflistung definiert. Wenn die Auflistung vom Zeichenfolgentyp ist, darf sie nur Zeichenfolgentypwerte enthalten.

### Beispiele {#examples-13}

```
<enumeration name="myEnum">
       <value name="One" value="1"/>
       <value name="Two" value="2"/>
    </enumeration>
```
