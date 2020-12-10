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
source-wordcount: '2011'
ht-degree: 1%

---


# `<element>` Element {#element--element}

## Inhaltsmodell {#content-model-4}

element:==(attribute | compute-string | dbindex | default | element | help | join | Schlüssel | sysFilter | translatedDefault)

## Attribute {#attributes-4}

_operation (string), advanced (boolean), Aggregat (string), applyIf (string), autopk (boolean), gehörtTo (string), convDate (string), dataPolicy (string), dataSource (string), dbEnum (string), defOnDuplicate (boolean), default (string), desc (string), display Field (boolean), doesNotSupportDiff (boolean), edit (string), emptyKeyValue (string), enum (string), enumImage (string), developSchemaTarget (string), expr (string), externalJoin (boolean), feature (string), featureDate (boolean), filterPath (string), folderLink string), folderModel (string), folderProcess (string), fullLoad (boolean), hierarchisch (boolean), hierarchischPath (string), img (string), Inout (string), Integrität (string), label (string), labelSingular (string), length (string), localizable (boolean), name (MNTOKEN), noDb Index (boolean), noKey (boolean), ordered (boolean), overflow table (boolean), pkSequence (string), pkgStatus (string), ref (string), required (boolean), revAdvanced (boolean), revCardinality (string), revDesc (string), revExternalJoin (boolean) ean), revIntegrity (string), revLabel (string), revLink (string), revTarget (string), revVisibleIf (string), sql (boolean), sqlname (string), sqltable (string), tableSpace (string), tableSpaceIndex (string), Zielgruppe (MNTOKEN), template (string), temporaryTable (boolean), translatedDefault (string), translatedExpr (string), type (MNTOKEN), unbound (boolean), user (boolean), userEnum (string), visibleIf (string), xml (boolean), xmlChildren (boolean)

## Eltern {#parents-4}

`<srcschema>`

`<element>`

## Kinder {#children-4}

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

## Beschreibung {#description-4}

Es gibt vier Elementtypen im Adobe Campaign:`<element>`

* Stamm `<element>`: definiert den Namen der SQL-Tabelle, die dem Schema entspricht.
* Struktur `<element>` : definiert eine Gruppe von `<element>`   oder   `<attribute>`    Elemente.
* Link `<element>`: definiert einen Link. Diese Elemente müssen das Attribut &quot;@type=link&quot;enthalten.
* XML `<element>` : definiert ein Textfeld vom Typ &quot;mData&quot;. Dieses Element muss das Attribut &quot;@type=xml&quot;enthalten.

## Attributbeschreibung {#attribute-description-4}

* **_operation (string)**: definiert den Typ des Schreibens in der Datenbank.

   Dieses Attribut wird hauptsächlich beim Erweitern von vordefinierten Schemas verwendet.

   Barrierefreie Werte sind:

   * &quot;none&quot;: Aussöhnung allein. Das bedeutet, dass Adobe Campaign das Element wiederherstellt, ohne es zu aktualisieren, oder einen Fehler erzeugt, wenn es nicht vorhanden ist.
   * &quot;insertOrUpdate&quot;: mit Einfügen aktualisieren. Das bedeutet, dass Adobe Campaign das Element aktualisiert oder erstellt, wenn es nicht vorhanden ist.
   * &quot;insert&quot;: Einfügen. Das bedeutet, dass Adobe Campaign das Element einfügt, ohne zu prüfen, ob es vorhanden ist.
   * &quot;update&quot;: aktualisieren. Das bedeutet, dass Adobe Campaign das Element aktualisiert oder einen Fehler erzeugt, wenn es nicht vorhanden ist.
   * &quot;delete&quot;: löschen. Das bedeutet, dass Adobe Campaign Elemente wiederherstellt und löscht.

* **advanced (boolean)**: Wenn diese Option aktiviert ist (@advanced=&quot;true&quot;), können Sie das Attribut auf der Liste der verfügbaren Felder ausblenden, auf die Sie zur Konfiguration einer Liste in einem Formular zugreifen können.
* **aggregat (Zeichenfolge)**: können Sie die Definition eines Begriffs  `<element>`  über ein anderes Schema kopieren. Dieses Attribut erhält eine Schema-Deklaration in Form eines &quot;Namensraum:name&quot;.
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

* **dbEnum (Zeichenfolge)**: erhält den internen Namen einer &quot;geschlossenen&quot;Auflistung. Die Werte für die Auflistung müssen in `<srcschema>` definiert werden.
* **defOnDuplicate (boolean)**: Wenn dieses Attribut aktiviert ist, wird bei der Duplizierung eines Datensatzes der (in &quot;@default&quot;definierte) Standardwert automatisch erneut auf den Datensatz angewendet.
* **default (Zeichenfolge)**: ermöglicht die Definition des Elementverhaltens (Aufruf einer Funktion, Standardwert). Dieses Attribut erhält einen XTK-Ausdruck.
* **desc (Zeichenfolge)**: können Sie eine Beschreibung des Elements einfügen. Diese Beschreibung wird in der Statusleiste der Benutzeroberfläche angezeigt.
* **displayAsField (boolean)**: Wenn dieses Attribut aktiviert ist,  `<element>`  wird ein &quot;Link&quot;-Typ als Feld in der Ansicht der Schema (&quot;Struktur&quot;, Registerkarte &quot;Struktur&quot;) angezeigt. Auf diese Weise können Sie einen Link als lokales Feld anzeigen und das Verhalten während einer Abfrage ändern. Wenn das Element in der SELECT-Anweisung einer Abfrage gefunden wird, wird der Wert der Link-Zielgruppe verwendet. Wenn das Element im WO einer Abfrage gefunden wird, wird der zugrunde liegende Schlüssel des Links verwendet.
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
* **revCardinality (Zeichenfolge)**: Dieses Attribut definiert die Kardinalität eines Links zwischen zwei Tabellen. Es wird in einem &quot;link&quot;-Typ `<element>` verwendet.

   Mögliche Werte:

   * &quot;single&quot; : Einfacher 1-1-Typ-Link
   * &quot;ungebunden&quot;: Sammlungslink für 1-N-Typ

   Wenn das Attribut bei der Linkerstellung nicht angegeben wird, ist die Kardinalität standardmäßig 1-N.

* **revDesc (Zeichenfolge)**: Dieses Attribut erhält eine Beschreibung, die mit dem anderen Link verknüpft ist.
* **revExternalJoin (boolean)**: Wenn dieses Attribut aktiviert ist, können Sie die externe Verbindung zum anderen Link erzwingen.
* **revIntegrity (Zeichenfolge)**: Dieses Attribut definiert die Integrität des Schemas Zielgruppe. Es werden dieselben Werte wie das Attribut &quot;@integer&quot;autorisiert. Standardmäßig gibt Adobe Campaign diesem Attribut den &quot;normalen&quot;Wert zu.
* **revLabel (Zeichenfolge)**: Beschriftung des Gegenlinks.
* **revLink (Zeichenfolge)**: Name des anderen Links. Lautet der Wert &quot;_KEINE_&quot;, wird im Ziel-Schema kein entgegengesetzten Link erstellt.
* **revTarget (Zeichenfolge)**: zielgruppe des gegenteiligen Links.
* **sql (boolean)**: Wenn dieses Attribut aktiviert ist (@sql=&quot;true&quot;), erzwingt es die Datenspeicherung des SQL-Elements, auch wenn das Element die Eigenschaft xml=&quot;true&quot; hat.
* **sqlname (Zeichenfolge)**: Name des Felds bei der Tabellenerstellung. Wenn &quot;@sqlname&quot;nicht angegeben ist, wird der Wert des Attributs &quot;@name&quot;standardmäßig verwendet. Beim Schreiben des Schemas in die Tabelle werden je nach Feldtyp automatisch Präfixe hinzugefügt.
* **sqltable (Zeichenfolge)**: für das Hauptelement des Schemas, überschreibt dieses Attribut den standardmäßig generierten Namen der SQL-Tabelle. Wenn &quot;@sqltable&quot;nicht angegeben ist, wird der Standardname wie folgt strukturiert: namensraum (Groß-/Kleinschreibung des ersten Buchstabens) gefolgt vom Wert des SrcSchema &quot;@name&quot;.
* **tableSpace (Zeichenfolge)**: Mit diesem Attribut können Sie eine neue Datenspeicherung für Tablespace für eine Tabelle angeben (gültig im Stammverzeichnis  `<element>`).
* **tableSpaceIndex (Zeichenfolge)**: Mit diesem Attribut können Sie einen neuen Tabellenraum für die Index-Datenspeicherung angeben (gültig im Stammverzeichnis  `<element>`).
* **zielgruppe (MNTOKEN)**: erhält beim Erstellen einer Verknüpfung zwischen Tabellen den Namen des Schemas Zielgruppe. Dieses Attribut ist nur für Elemente des Typs &quot;Link&quot;aktiv.
* **template (string)**: Dieses Attribut definiert einen Verweis auf ein  `<element>` Element, das von mehreren Schemas gemeinsam verwendet wird. Die Definition wird automatisch in das aktuelle Schema kopiert.
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
* **xmlChildren (boolean)**: erzwingt die Datenspeicherung für jedes Kind (  `<element>  or  <attribute>   ) of the   <element>    element in an XML document.   </element>  </attribute> </element>`
