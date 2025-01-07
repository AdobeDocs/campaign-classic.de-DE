---
product: campaign
title: Schemaelemente und -attribute - element
description: Element
feature: Schema Extension
exl-id: 60f15ae5-b2bd-48f9-aa45-8f795a3071aa
source-git-commit: 254c89490fefa5d405bcecd2f1781df46450a873
workflow-type: tm+mt
source-wordcount: '2029'
ht-degree: 0%

---

# Element {#element--element}


## Inhaltsmodell {#content-model-4}

element:==(attribute | Compute-String | dbindex | Standard | Element | Hilfe | beitreten | Schlüssel | sysFilter | translatedDefault)

## Attribute {#attributes-4}

_operation (Zeichenfolge), Advanced (Boolescher Wert), Aggregat (Zeichenfolge), ApplicableIf (Zeichenfolge), AutoPK (Boolescher Wert), BelsTo (Zeichenfolge), ConvDate (Zeichenfolge), DataPolicy (Zeichenfolge), DataSource (Zeichenfolge), dbEnum (Zeichenfolge), DefOnDuplicate (Boolescher Wert), Default (Zeichenfolge), desc (Zeichenfolge), displayAsField (Boolescher Wert), DoesNotSupportDiff (Boolescher Wert), edit (Zeichenfolge), emptyKeyValue (Zeichenfolge), enum (Zeichenfolge), enumImage (Zeichenfolge), expandSchemaTarget (Zeichenfolge), expr (Zeichenfolge), externalJoin (Boolesch), feature (Zeichenfolge), featureDate (Boolesch), filterPath (Zeichenfolge), folderLink (Zeichenfolge), folderModel (Zeichenfolge), folderProcess (Zeichenfolge), fullLoad (Boolesch), hierarchisch (Boolesch), hierarchicalPath (Zeichenfolge), img (Zeichenfolge), input (Zeichenfolge), integrity (Zeichenfolge), label (Zeichenfolge), labelSingular (Zeichenfolge), length (Zeichenfolge), lokalisierbar (boolesch), name (MNTOKEN), noDB (Boolesch), noKey (Boolesch), ordered (Boolesch), overflowtable (Boolesch), pkSequence (Zeichenfolge), pkgStatus (Zeichenfolge), ref (Zeichenfolge), required (Boolesch), revAdvanced (Boolesch), revCardinality (Zeichenfolge), revDesc (Zeichenfolge), revExternalJoin (Boolesch), revIntegrity (Zeichenfolge), revLabel (Zeichenfolge), revLink (Zeichenfolge), revTarget (Zeichenfolge), revVisibleIf (Zeichenfolge), sql (Boolesch), sqlname (Zeichenfolge), sqltable (Zeichenfolge), tableSpace (Zeichenfolge), tableSpaceIndex (Zeichenfolge), target (MNTOKEN), template (Zeichenfolge), temporärTable (Boolesch), translatedDefault (Zeichenfolge), translatedExpr (Zeichenfolge), type (MNTOKEN), unbound (Boolesch), user (Boolesch), userEnum (Zeichenfolge), visibleIf (Zeichenfolge), xml (Boolesch), xmlChildren (Boolesch)

## Übergeordnete Elemente {#parents-4}

`<srcschema>`

`<element>`

## Untergeordnetes Element {#children-4}

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

In Adobe Campaign gibt es vier Arten von `<element>`:

* `<element>` : definiert den Namen der SQL-Tabelle, die dem Schema entspricht.
* `<element>` : definiert eine Gruppe von `<element>`   oder   `<attribute>`    -Elemente.
* Link-`<element>` : definiert einen Link. Diese Elemente müssen das Attribut &quot;@type=link“ enthalten.
* XML-`<element>` : definiert ein Feld vom Typ „mData“. Dieses Element muss das Attribut &quot;@type=xml“ enthalten.

## Attributbeschreibung {#attribute-description-4}

* **_operation (Zeichenfolge)**: definiert den Typ des Schreibens in der Datenbank.

  Dieses Attribut wird hauptsächlich bei der Erweiterung von vordefinierten Schemata verwendet.

  Folgende Werte sind verfügbar:

   * „none“: Aussöhnung allein. Dies bedeutet, dass Adobe Campaign das Element wiederherstellt, ohne es zu aktualisieren oder einen Fehler zu erzeugen, wenn es nicht existiert.
   * „insertOrUpdate“: Mit dem Einfügen aktualisieren. Das bedeutet, dass Adobe Campaign das Element aktualisiert oder erstellt, wenn es nicht vorhanden ist.
   * „INSERT“: Einfügen. Dies bedeutet, dass Adobe Campaign das Element einfügt, ohne zu überprüfen, ob es vorhanden ist.
   * „UPDATE“: Aktualisieren. Das bedeutet, dass Adobe Campaign das Element aktualisiert oder einen Fehler generiert, wenn es nicht vorhanden ist.
   * „delete“: Löschung. Dies bedeutet, dass Adobe Campaign Elemente wiederherstellt und löscht.

* **Erweitert (Boolesch)**: Wenn diese Option aktiviert ist (@advanced=„true„), können Sie das Attribut in der Liste der verfügbaren Felder ausblenden, die zum Konfigurieren einer Liste in einem Formular verfügbar sind.
* **Aggregat (Zeichenfolge)**: dient dem Kopieren der Definition einer `<element>` über ein anderes Schema. Dieses Attribut erhält eine Schemadeklaration in Form eines „namespace:name“.
* **applicableIf (Zeichenfolge)**: Bedingung für die Anwendung des Index. Dieses Attribut erhält einen XTK-Ausdruck.
* **autopk (Boolescher Wert)**: Wenn diese Option aktiviert ist (autopk=„true„), wird automatisch ein eindeutiger Schlüssel definiert. Diese Option kann nur für das Hauptelement des Schemas verwendet werden. Achtung: Adobe Campaign garantiert nur, dass der generierte Schlüssel eindeutig ist. Es ist nicht garantiert, dass die Schlüsselwerte aufeinander folgend und inkrementell sind.
* **dataPolicy (Zeichenfolge)**: Ermöglicht es Ihnen, Validierungseinschränkungen für die im SQL-Feld zulässigen Werte anzugeben. Die Werte für dieses Attribut sind:

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
* **default (Zeichenfolge)** ermöglicht die Definition des Verhaltens von Elementen (Aufruf einer Funktion, Standardwert). Dieses Attribut erhält einen XTK-Ausdruck.
* **desc (Zeichenfolge)**: Hiermit können Sie eine Beschreibung des Elements einfügen. Diese Beschreibung wird verwendet, um zu verstehen, was das -Element ist und wofür es verwendet wird. Sie können sie im Formular anzeigen.
* **displayAsField (Boolescher Wert)**: Wenn dieses Attribut aktiviert ist, wird ein `<element>` vom Typ „Link“ in der Strukturansicht der Schemata als Feld angezeigt (Registerkarte „Struktur„). Auf diese Weise ist es möglich, einen Link als lokales Feld anzuzeigen und sein Verhalten während einer Abfrage zu ändern. Wenn das Element in SELECT einer Abfrage gefunden wird, wird der Wert des Link-Ziels verwendet. Wenn das Element im VERZEICHNIS einer Abfrage gefunden wird, wird der zugrunde liegende Schlüssel des Links verwendet.
* **edit (Zeichenfolge)** Dieses Attribut gibt den Typ der Eingabe an, die in dem mit dem Schema verknüpften Formular verwendet wird.
* **enum (Zeichenfolge)**: Empfängt den Namen der mit dem Feld verknüpften Auflistung. Die Auflistung kann in dasselbe Schema oder in ein Remote-Schema eingefügt werden.
* **expr (Zeichenfolge)** Dieses Attribut definiert ein berechnetes Feld, für das keine Definition in der Tabelle gespeichert ist. Sie empfängt einen Xpath- oder einen XTK-Ausdruck (Zeichenfolge).
* **externalJoin (Boolescher Wert)**: externer Join in einem Element vom Typ „link“.
* **Feature (String)** definiert ein Merkmalsfeld: Diese Felder werden zur Erweiterung der Daten in einer vorhandenen Tabelle verwendet, jedoch mit Speicherung in einer Anhang-Tabelle. Akzeptierte Werte sind:

   * „Freigegeben“: Der Inhalt wird pro Datentyp in einer freigegebenen Tabelle gespeichert
   * „Dediziert“: Der Inhalt wird in einer dedizierten Tabelle gespeichert

  SQL-Merkmalstabellen werden automatisch auf Basis des Merkmalstyps erstellt:

   * Dediziert: `Ft_[name_of_the_schema_containing_the_characteristic]_[name_of_the_characteristic]`
   * Freigegeben: `Ft_[type_of_key_of_the_schema_containing_the_characteristic]_[type_of_the_characteristic]`

  Es gibt zwei Arten von Merkmalsfeldern: einfache Felder, in denen ein einzelner Wert für das Merkmal zulässig ist, und Multiple-Choice-Felder, in denen das Merkmal mit einem Sammlungselement verknüpft ist, das mehrere Werte enthalten kann.

  Wenn ein Merkmal in einem Schema definiert ist, muss dieses Schema einen Hauptschlüssel haben, der auf einem einzelnen Feld basiert (zusammengesetzte Schlüssel sind nicht zulässig).

* **featureDate (boolesch)**: Mit dem Merkmalsfeld &quot;@feature“ verknüpftes Attribut. Wenn der Wert „true“ lautet, können Sie damit herausfinden, wann der Wert zuletzt aktualisiert wurde.
* **filterPath (Zeichenfolge)**: Dieses Attribut empfängt einen Xpath und ermöglicht die Definition eines Filters für ein Feld.
* **folderLink (Zeichenfolge)**: Dieses Attribut erhält den Namen der Relation, mit der Sie die Dateien mit den Entitäten wiederherstellen können.
* **folderModel (Zeichenfolge)**: definiert den Ordnertyp, der die Entitätsspeicherung ermöglicht. Dieses Attribut wird nur definiert, wenn &quot;@folderLink“ vorhanden ist.
* **folderProcess (Zeichenfolge)**: definiert die Relation, unter der Entitätsmodellinstanzen gespeichert werden. Dieses Attribut wird nur definiert, wenn &quot;@folderLink“ vorhanden ist.
* **fullLoad (Boolesch)** Dieses Attribut erzwingt die Anzeige aller Datensätze in einer Tabelle während der Feldauswahl in einem Formular.
* **img (Zeichenfolge)**: Empfängt den Pfad eines mit einem Element verknüpften Bildes. Der Wert dieses Attributs ist vom Typ „namespace:image name“. Beispiel: img=„cus:myImage.jpg“. Physisch muss das Bild auf den Anwendungsserver importiert werden.
* **integrity (Zeichenfolge)**: Referenzintegrität der Entität der Quelltabelle zur Zieltabelle.

  Folgende Werte sind verfügbar:

   * „define“: Adobe Campaign löscht die Entität nicht, wenn sie über den Link referenziert wird
   * „Normal“: Durch Löschen der Quellentität werden die Schlüssel der Relation auf der Zielentität initialisiert (Standardmodus). Bei diesem Integritätstyp werden alle Fremdschlüssel initialisiert
   * „own“: Durch Löschen der Quellentität wird das Löschen der Zielentität zum Trigger
   * „owncopy“: Ähnlich wie „own“ (beim Löschen) oder dupliziert Vorkommen (bei Duplizierung)
   * „neutral“: Führt keine Operation aus

* **label (Zeichenfolge)**: Elementbezeichnung.
* **labelSingular (Zeichenfolge)**: label (Singulärform) des Elements, das in einigen Teilen der Schnittstelle verwendet wird.
* **length (Zeichenfolge)**: max. Anzahl der Zeichen, die für einen Wert des SQL-Feldes vom Typ „Zeichenfolge“ zulässig sind.
* **Localizable (Boolescher Wert)**: Wenn es aktiviert ist, weist dieses Attribut das Sammlungs-Tool an, den Wert des Attributs &quot;@label“ für die Übersetzung abzurufen (interne Verwendung).
* **name (MNTOKEN)**: Interner Name des Elements, das dem Namen der Tabelle entspricht. Der Wert des Attributs &quot;@name“ muss kurz sein, vorzugsweise in englischer Sprache, und Namensbeschränkungen im Zusammenhang mit XML entsprechen.

  Wenn das Schema in die Datenbank geschrieben wird, werden dem Feldnamen von Adobe Campaign automatisch Präfixe hinzugefügt.

   * „i“: Präfix für den Typ „integer“.
   * „D“: Präfix für den Typ „double“.
   * „s“: Präfix für den String-Typ.
   * „ts“: Präfix für den Typ „date“.

  Um den Namen der Tabelle autonom zu definieren, müssen Sie das Attribut &quot;@sqltable“ in der Definition des Hauptschemaelements verwenden.

* **noDbIndex (boolesch)**: Hiermit können Sie angeben, dass das Element nicht indiziert wird.
* **ordered (Boolescher Wert)**: Wenn das Attribut aktiviert ist (ordered=„true„), behält Adobe Campaign die Elementdeklarationssequenz in einem XML-Sammlungselement bei.
* **pkSequence (Zeichenfolge)**: Empfängt den Namen der Sequenz, die für die Berechnung eines automatisch inkrementellen Schlüssels verwendet werden soll. Dieses Attribut kann nur verwendet werden, wenn für das Stammelement des Schemas ein automatisch inkrementeller Schlüssel definiert ist.
* **pkgStatus (Zeichenfolge)**: Bei Paketexporten werden Werte als Funktion des Werts dieses Attributs berücksichtigt:

   * „Always“: Das Element ist immer vorhanden
   * „Nie“: Das Element wird nie vorhanden sein
   * „Standard (oder nichts)“: Das Element wird exportiert, es sei denn, es handelt sich um das Standardelement oder es ist kein internes Feld und wäre nicht mit anderen Instanzen kompatibel

* **ref (Zeichenfolge)** Dieses Attribut definiert einen Verweis auf ein >Element>-Element, das von mehreren Schemata gemeinsam genutzt wird (Definition-Factoring). Die Definition wird nicht in das aktuelle Schema kopiert.
* **required (boolean)**: Wenn dieses Attribut aktiviert ist (@required=„true„), wird das Feld in der Benutzeroberfläche hervorgehoben. Die Beschriftung des Felds wird in den Formularen rot angezeigt.
* **revAdvanced (Boolescher Wert)**: Bei Aktivierung gibt dieses Attribut an, dass der gegenüberliegende Link ein „erweiterter“ Link ist.
* **revCardinality (Zeichenfolge)** Dieses Attribut definiert die Kardinalität einer Relation zwischen zwei Tabellen. Sie wird in einem `<element>` vom Typ „Link“ verwendet.

  Mögliche Werte:

   * „single“ : Einfacher Link vom Typ 1-1
   * „unbound“: Sammlungsrelation vom Typ 1-N

  Wenn das Attribut bei der Link-Erstellung nicht angegeben wird, ist die Kardinalität standardmäßig 1-N.

* **revDesc (Zeichenfolge)**: Dieses Attribut erhält eine Beschreibung, die mit dem gegenüberliegenden Link verknüpft ist.
* **revExternalJoin (Boolescher Wert**: Bei Aktivierung ermöglicht dieses Attribut das Erzwingen des externen Joins auf dem gegenüberliegenden Link.
* **revIntegrity (Zeichenfolge)** Dieses Attribut definiert die Integrität im Zielschema. Die gleichen Werte wie das Attribut &quot;@integrity“ werden autorisiert. Standardmäßig weist Adobe Campaign diesem Attribut den Wert „normal“ zu.
* **revLabel (Zeichenfolge)**: Bezeichnung des gegenüberliegenden Links.
* **revLink (Zeichenfolge)**: Name des gegenüberliegenden Links. Wenn der Wert &quot;_NONE_ lautet, wird im Zielschema kein gegenteiliger Link erstellt.
* **revTarget (Zeichenfolge)**: Ziel des gegenüberliegenden Links.
* **sql (Boolescher Wert)**: Wenn dieses Attribut aktiviert ist (@sql=„true„), wird die Speicherung des SQL-Elements erzwungen, auch wenn das Element die Eigenschaft xml=„true“ aufweist.
* **sqlname (Zeichenfolge)**: Name des Felds bei der Tabellenerstellung. Wenn &quot;@sqlname“ nicht angegeben ist, wird standardmäßig der Wert des Attributs &quot;@name“ verwendet. Beim Schreiben des Schemas in die Tabelle werden Präfixe je nach Feldtyp automatisch hinzugefügt.
* **sqltable (Zeichenfolge)**: Für das Hauptelement des Schemas überschreibt dieses Attribut den Namen der standardmäßig generierten SQL-Tabelle. Wenn &quot;@sqltable“ nicht angegeben wird, ist der Standardname wie folgt strukturiert: Namespace (Großbuchstaben erster Buchstabe) gefolgt vom Wert des SrcSchema &quot;@name“.
* **tableSpace (Zeichenfolge)**: Mit diesem Attribut können Sie einen neuen Datenspeicherungs-Tablespace für eine Tabelle angeben (gültig für den `<element>`).
* **tableSpaceIndex (Zeichenfolge)**: Mit diesem Attribut können Sie einen neuen Tablespace für die Indexspeicherung einer Tabelle angeben (gültig für den `<element>`).
* **target (MNTOKEN)**: Empfängt den Namen des Zielschemas beim Erstellen einer Relation zwischen Tabellen. Dieses Attribut ist nur für Elemente vom Typ „link“ aktiv.
* **template (Zeichenfolge)** Dieses Attribut definiert einen Verweis auf ein `<element>`, das von mehreren Schemata gemeinsam genutzt wird. Die Definition wird automatisch in das aktuelle Schema kopiert.
* **translatedDefault (Zeichenfolge)**: Wenn das Attribut &quot;@default“ gefunden wird, können Sie mit dem Attribut &quot;@translatedDefault“ einen Ausdruck neu definieren, sodass er mit dem in @default definierten Ausdruck übereinstimmt, der vom Übersetzungs-Tool erfasst werden soll (interne Verwendung).
* **translatedExpr (Zeichenfolge)**: Wenn das Attribut &quot;@expr“ gefunden wird, können Sie mit dem Attribut &quot;@translatedExpr“ einen Ausdruck neu definieren, der mit dem in &quot;@expr“ definierten Ausdruck übereinstimmt. Dieser wird vom Übersetzungs-Tool erfasst (interne Verwendung).
* **type (MNTOKEN)** definiert den Typ der im Element gespeicherten Daten.

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

* **unbound (Boolescher Wert)**: Wenn das Attribut aktiviert ist (unbound=„true„), wird die Relation als Sammlungselement für eine 1-N-Kardinalität deklariert.
* **userEnum (Zeichenfolge)**: Empfängt den internen Namen einer „offenen“ Auflistung. Auflistungswerte können vom Benutzer in der -Schnittstelle definiert werden.
* **xml (Boolescher Wert)**: Wenn diese Option aktiviert ist, werden alle im Element definierten Werte in XML in einem Feld vom Typ „mData“ vom Typ TEXT gespeichert. Das bedeutet, dass es bei diesen Feldern keine Filterung oder Sortierung gibt.
* **xmlChildren (boolean)**: Erzwingt die Speicherung für jedes untergeordnete Element ( `<element>  or  <attribute>   ) of the   <element>    element in an XML document.   </element>  </attribute> </element>`
