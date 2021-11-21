---
product: campaign
title: Elemente und Attribute
description: Elemente und Attribute
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: 60f15ae5-b2bd-48f9-aa45-8f795a3071aa
source-git-commit: bd9f035db1cbad883e1f27fe901e34dfbc9c1229
workflow-type: tm+mt
source-wordcount: '2012'
ht-degree: 1%

---

# Element {#element--element}

![](../../../assets/v7-only.svg)

## Inhaltsmodell {#content-model-4}

element:==(attribute | Compute-string | dbindex | default | element | help | join | key | sysFilter | translateDefault)

## Attribute {#attributes-4}

_operation (string), advanced (boolean), aggregate (string), applyIf (string), autopk (boolean), gehörtTo (string), convDate (string), dataPolicy (string), dataSource (string), dbEnum (string), defOnDuplicate (boolean), default (string), desc (string), displayAs Feld (boolean), doesNotSupportDiff (boolean), edit (string), emptyKeyValue (string), enum (string), enumImage (string), expandSchemaTarget (string), expr (string), externalJoin (boolean), feature (string), featureDate (boolean), filterPath (string), folderLink (Zeichenfolge)), folderModel (string), folderProcess (string), fullLoad (boolean), hierarchisch (boolean), hierarchicalPath (string), img (string), inout (string), integrieren (string), label (string), labelSingular (string), length (string), localizable (boolean), name (MNTOKEN), noDbIndex (boolean), noKey (boolean), ordered (boolean), overflowtable (boolean), pkSequence (string), pkgStatus (string), ref (string), required (boolean), revAdvanced (boolean), revCardinality (string), revDesc (string), revExternalJoin (boolean)), revIntegrity (string), revLabel (string), revLink (string), revTarget (string), revVisibleIf (string), sql (boolean), sqlname (string), sqltable (string), tableSpace (string), tableSpaceIndex (string), target (MNTOKEN), template (string), Tabelle (boolesch), translateDefault (string), translationExpr (string), Typ (MNTOKEN), unbound (boolesch), Benutzer (boolesch), userEnum (string), visibleIf (string), xml (boolean), xmlChildren (boolesch)

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

Es gibt vier Arten von `<element>`  Elemente in Adobe Campaign:

* Stamm `<element>`  : definiert den Namen der SQL-Tabelle, die dem Schema entspricht.
* Struktur `<element>`  : definiert eine Gruppe von  `<element>`   oder   `<attribute>`    -Elemente.
* Link `<element>`  : definiert einen Link. Diese Elemente müssen das Attribut &quot;@type=link&quot; enthalten.
* XML `<element>`  : definiert ein Feld vom Typ &quot;mData&quot;. Dieses Element muss das Attribut &quot;@type=xml&quot; enthalten.

## Attributbeschreibung {#attribute-description-4}

* **_operation (string)**: definiert den Typ des Schreibens in der Datenbank.

   Dieses Attribut wird hauptsächlich bei der Erweiterung von nativen Schemata verwendet.

   Barrierefreie Werte sind:

   * &quot;none&quot;: Abstimmung. Das bedeutet, dass Adobe Campaign das Element wiederherstellt, ohne es zu aktualisieren, oder einen Fehler erzeugt, wenn es nicht vorhanden ist.
   * &quot;insertOrUpdate&quot;: durch Einfügen aktualisiert werden. Das bedeutet, dass Adobe Campaign das Element aktualisiert oder erstellt, falls es nicht vorhanden ist.
   * &quot;insert&quot;: einfügen. Das bedeutet, dass Adobe Campaign das Element einfügt, ohne zu überprüfen, ob es vorhanden ist.
   * &quot;update&quot;: aktualisieren. Das bedeutet, dass Adobe Campaign das Element aktualisiert oder einen Fehler erzeugt, wenn es nicht vorhanden ist.
   * &quot;delete&quot;: Löschen. Dies bedeutet, dass Adobe Campaign Elemente wiederherstellt und löscht.

* **advanced (boolean)**: Wenn diese Option aktiviert ist (@advanced=&quot;true&quot;), können Sie das Attribut in der Liste der verfügbaren Felder ausblenden, auf die für die Konfiguration einer Liste in einem Formular zugegriffen werden kann.
* **aggregate (string)**: ermöglicht das Kopieren der Definition eines `<element>`  über ein anderes Schema. Dieses Attribut erhält eine Schemadeklaration in Form eines &quot;namespace:name&quot;.
* **applyIf (string)**: -Bedingung für die Anwendung des Index. Dieses Attribut erhält einen XTK-Ausdruck.
* **autopk (boolesch)**: Wenn diese Option aktiviert ist (autopk=&quot;true&quot;), wird automatisch ein eindeutiger Schlüssel definiert. Diese Option kann nur für das Hauptelement des Schemas verwendet werden. Achtung: Adobe Campaign garantiert nur, dass der generierte Schlüssel eindeutig ist. Es ist nicht garantiert, dass die Schlüsselwerte zusammenhängend und inkrementell sind.
* **dataPolicy (Zeichenfolge)**: ermöglicht es Ihnen, Genehmigungseinschränkungen für die im SQL-Feld zulässigen Werte festzulegen. Die Werte für dieses Attribut sind:

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
* **default (string)**: ermöglicht die Definition des Elementverhaltens (Aufruf einer Funktion, Standardwert). Dieses Attribut erhält einen XTK-Ausdruck.
* **desc (Zeichenfolge)**: fügt eine Beschreibung des Elements ein. Diese Beschreibung wird in der Statusleiste der Benutzeroberfläche angezeigt.
* **displayAsField (boolean)**: Wenn dieses Attribut aktiviert ist, wird der Typ &quot;Link&quot; `<element>`  wird als Feld in der Baumansicht der Schemas angezeigt ( Registerkarte &quot;Struktur&quot;). Auf diese Weise kann ein Link als lokales Feld angezeigt und sein Verhalten während einer Abfrage geändert werden. Wenn das Element im SELECT einer Abfrage gefunden wird, wird der Wert des Link-Ziels verwendet. Wenn das Element im WHERE einer Abfrage gefunden wird, wird der zugrunde liegende Schlüssel des Links verwendet.
* **edit (string)**: Dieses Attribut gibt den Typ der Eingabe an, die in dem mit dem Schema verknüpften Formular verwendet wird.
* **enum (string)**: erhält den Namen der mit dem Feld verknüpften Auflistung. Die Auflistung kann im selben Schema oder in ein Remote-Schema eingefügt werden.
* **expr (Zeichenfolge)**: Dieses Attribut definiert ein berechnetes Feld, für das keine Definition in der Tabelle gespeichert ist. Sie erhält einen Xpath- oder einen XTK-Ausdruck (Zeichenfolge).
* **externalJoin (boolesch)**: externer Join in einem Element vom Typ &quot;Link&quot;.
* **Funktion (Zeichenfolge)**: definiert ein Merkmalfeld: Diese Felder dienen zur Erweiterung der Daten in einer vorhandenen Tabelle, jedoch mit Speicherung in einer Tabelle im Anhang. Zulässige Werte sind:

   * &quot;shared&quot;: Der Inhalt wird in einer freigegebenen Tabelle nach Datentyp gespeichert.
   * &quot;dediziert&quot;: Der Inhalt wird in einer eigenen Tabelle gespeichert.

   SQL-Eigenschaftstabellen werden automatisch basierend auf dem charakteristischen Typ erstellt:

   * dediziert: `Ft_[name_of_the_schema_containing_the_characteristic]_[name_of_the_characteristic]`
   * shared: `Ft_[type_of_key_of_the_schema_containing_the_characteristic]_[type_of_the_characteristic]`

   Es gibt zwei Arten von Eigenschaftenfeldern: einfache Felder, bei denen ein einzelner Wert für das Merkmal zulässig ist, und Multiple-Choice-Felder, bei denen das Merkmal mit einem Kollektionselement verknüpft ist, das mehrere Werte enthalten kann.

   Wenn ein Merkmal in einem Schema definiert ist, muss dieses Schema über einen Hauptschlüssel verfügen, der auf einem einzelnen Feld basiert (zusammengesetzte Schlüssel sind nicht autorisiert).

* **featureDate (boolean)**: Attribut im Zusammenhang mit dem Feld &quot;@feature&quot;. Wenn der Wert &quot;true&quot;ist, können Sie feststellen, wann der Wert zuletzt aktualisiert wurde.
* **filterPath (Zeichenfolge)**: Dieses Attribut erhält einen Xpath und ermöglicht Ihnen die Definition eines Filters für ein Feld.
* **folderLink (Zeichenfolge)**: Dieses Attribut erhält den Namen des Links, über den Sie die Dateien abrufen können, die Entitäten enthalten.
* **folderModel (string)**: definiert den Ordnertyp, der die Speicherung von Entitäten ermöglicht. Dieses Attribut wird nur definiert, wenn &quot;@folderLink&quot;vorhanden ist.
* **folderProcess (string)**: definiert den Link, unter dem Entitätsmodellinstanzen gespeichert werden. Dieses Attribut wird nur definiert, wenn &quot;@folderLink&quot;vorhanden ist.
* **fullLoad (boolesch)**: Dieses Attribut erzwingt die Anzeige aller Datensätze in einer Tabelle während der Feldauswahl in einem Formular.
* **img (Zeichenfolge)**: empfängt den Pfad eines mit einem Element verknüpften Bildes. Der Wert dieses Attributs hat den Typ &quot;namespace:image name&quot;. Beispiel: img=&quot;cus:myImage.jpg&quot;. Das Bild muss physisch auf den Anwendungsserver importiert werden.
* **integrität (Zeichenfolge)**: referenzielle Integrität des Vorkommens der Quelltabelle gegenüber der Zieltabelle.

   Barrierefreie Werte sind:

   * &quot;define&quot;: Adobe Campaign löscht die Entität nicht, wenn sie über den Link referenziert wird
   * &quot;normal&quot;: Wenn Sie das Quellereignis löschen, werden die Schlüssel des Links auf das Zielereignis initialisiert (Standardmodus). Dieser Integritätstyp initialisiert alle Fremdschlüssel
   * &quot;own&quot;: Beim Löschen des Vorkommens der Quelle wird das Löschen des Vorkommens der Zielgruppe Trigger
   * &quot;owncopy&quot;: ähnlich wie &quot;own&quot;(bei Löschung) oder Duplikate von Vorkommnissen (bei Duplizierung)
   * &quot;neutral&quot;: nichts tut

* **label (string)**: Elementtitel.
* **labelSingular (Zeichenfolge)**: label (Singular form) des Elements, das in einigen Teilen der Benutzeroberfläche verwendet wird.
* **length (Zeichenfolge)**: max. Anzahl der Zeichen, die für einen Wert des SQL-Felds vom Typ &quot;String&quot; autorisiert sind.
* **localizable (boolean)**: Wenn es aktiviert ist, weist dieses Attribut das Tool zur Sammlung an, den Wert des Attributs &quot;@label&quot;für die Übersetzung abzurufen (interne Verwendung).
* **name (MNTOKEN)**: interner Name des Elements, das mit dem Namen der Tabelle übereinstimmt. Der Wert des Attributs &quot;@name&quot;muss kurz sein, vorzugsweise in Englisch, und muss den mit XML verknüpften Benennungsbeschränkungen entsprechen.

   Beim Schreiben des Schemas in die Datenbank werden dem Feldnamen von Adobe Campaign automatisch Präfixe hinzugefügt.

   * &quot;i&quot;: -Präfix für den Typ &quot;Ganzzahl&quot;.
   * &quot;d&quot;: -Präfix für den Typ &quot;double&quot;.
   * &quot;s&quot;: -Präfix für den Zeichenfolgentyp.
   * &quot;ts&quot;: -Präfix für den Typ &quot;Datum&quot;.

   Um den Namen der Tabelle eigenständig zu definieren, müssen Sie das Attribut &quot;@sqltable&quot; in der Definition des Hauptrelements des Schemas verwenden.

* **noDbIndex (boolean)**: ermöglicht die Angabe, dass das Element nicht indiziert wird.
* **ordered (boolean)**: Wenn das Attribut aktiviert ist (ordered=&quot;true&quot;), behält Adobe Campaign die Elementdeklarationssequenz in einem XML-Kollektionselement bei.
* **pkSequence (Zeichenfolge)**: erhält den Namen der Sequenz, die zur Berechnung eines automatisch inkrementellen Schlüssels verwendet werden soll. Dieses Attribut darf nur verwendet werden, wenn im Stammelement des Schemas ein automatisch inkrementeller Schlüssel definiert ist.
* **pkgStatus (Zeichenfolge)**: Bei Package-Exporten werden Werte als Funktion des Werts dieses Attributs berücksichtigt:

   * &quot;always&quot;: das Element immer vorhanden ist
   * &quot;never&quot;: das Element wird nie vorhanden sein
   * &quot;default (oder nichts)&quot;: das Element wird exportiert, es sei denn, es ist das Standardelement oder, es ist kein internes Feld und ist nicht mit anderen Instanzen kompatibel

* **ref (string)**: Dieses Attribut definiert einen Verweis auf ein Element > element>, das von mehreren Schemas gemeinsam verwendet wird (Definition-Factoring). Die Definition wird nicht in das aktuelle Schema kopiert.
* **erforderlich (boolesch)**: Wenn dieses Attribut aktiviert ist (@required=&quot;true&quot;), wird das Feld in der Benutzeroberfläche hervorgehoben. Die Beschriftung des Felds wird in Formularen rot dargestellt.
* **revAdvanced (boolesch)**: Wenn dieses Attribut aktiviert ist, gibt es an, dass der umgekehrte Link ein &quot;erweiterter&quot;Link ist.
* **revCardinality (string)**: Dieses Attribut definiert die Kardinalität einer Verknüpfung zwischen zwei Tabellen. Sie wird in einem &quot;Link&quot;-Typ verwendet `<element>`.

   Mögliche Werte:

   * &quot;single&quot;: Einfache Relation vom Typ 1:1
   * &quot;unbound&quot;: Kollektionslink vom Typ 1:N

   Wenn das Attribut bei der Erstellung von Links nicht angegeben wird, beträgt die Kardinalität standardmäßig 1:N.

* **revDesc (Zeichenfolge)**: Dieses Attribut erhält eine Beschreibung, die mit dem anderen Link verknüpft ist.
* **revExternalJoin (boolesch)**: Wenn dieses Attribut aktiviert ist, können Sie den externen Join für den anderen Link erzwingen.
* **revIntegrity (Zeichenfolge)**: Dieses Attribut definiert die Integrität des Zielschemas. Die gleichen Werte wie das Attribut &quot;@integrität&quot; sind zulässig. Standardmäßig gibt Adobe Campaign diesem Attribut den &quot;normalen&quot;Wert.
* **revLabel (Zeichenfolge)**: Bezeichnung des Gegenlinks.
* **revLink (Zeichenfolge)**: Name des anderen Links. Wenn der Wert &quot;_KEINE_&quot;, wird im Zielschema keine entgegengesetzte Verknüpfung erstellt.
* **revTarget (Zeichenfolge)**: Zielgruppe des Gegenlinks.
* **sql (boolesch)**: Wenn dieses Attribut aktiviert ist (@sql=&quot;true&quot;), wird die Speicherung des SQL-Elements erzwungen, selbst wenn das Element die Eigenschaft xml=&quot;true&quot; aufweist.
* **sqlname (string)**: Name des Felds bei der Tabellenerstellung. Wenn &quot;@sqlname&quot; nicht angegeben ist, wird standardmäßig der Wert des Attributs &quot;@name&quot; verwendet. Beim Schreiben des Schemas in die Tabelle werden je nach Feldtyp automatisch Präfixe hinzugefügt.
* **sqltable (string)**: für das Hauptelement des Schemas überschreibt dieses Attribut den Namen der standardmäßig generierten SQL-Tabelle. Wenn &quot;@sqltable&quot;nicht angegeben ist, lautet der Standardname wie folgt: namespace (Groß-/Kleinschreibung des ersten Buchstabens) gefolgt vom Wert des SrcSchema &quot;@name&quot;.
* **tableSpace (Zeichenfolge)**: Mit diesem Attribut können Sie neue Daten zum Speichern von Tablespaces für eine Tabelle angeben (gültig für Stammverzeichnis) `<element>`).
* **tableSpaceIndex (Zeichenfolge)**: Mit diesem Attribut können Sie einen neuen Indexspeicher-Tablespace für eine Tabelle angeben (gültig für Stammverzeichnis) `<element>`).
* **target (MNTOKEN)**: erhält beim Erstellen einer Relation zwischen Tabellen den Namen des Zielschemas. Dieses Attribut ist nur für Elemente vom Typ &quot;Link&quot;aktiv.
* **template (string)**: Dieses Attribut definiert einen Verweis auf eine `<element>` -Element, das von mehreren Schemas gemeinsam genutzt wird. Die Definition wird automatisch in das aktuelle Schema kopiert.
* **translateDefault (string)**: Wenn ein &quot;@default&quot;-Attribut gefunden wird, können Sie mit &quot;@translationDefault&quot;einen Ausdruck neu definieren, der mit dem in &quot;@default&quot;definierten Ausdruck übereinstimmt, der vom Übersetzungs-Tool erfasst werden soll (interne Verwendung).
* **translateExpr (Zeichenfolge)**: Wenn ein &quot;@expr&quot;-Attribut gefunden wird, können Sie mit dem Attribut &quot;@translationExpr&quot; einen Ausdruck neu definieren, der mit dem in &quot;@expr&quot; definierten Ausdruck übereinstimmt und der vom Übersetzungstool (interne Verwendung) erfasst wird.
* **type (MNTOKEN)**: definiert den Typ der im Element gespeicherten Daten.

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

* **unbound (boolesch)**: Wenn das Attribut aktiviert ist (unbound=&quot;true&quot;), wird die Verknüpfung als Kollektionselement für eine 1:n-Kardinalität deklariert.
* **userEnum (Zeichenfolge)**: empfängt den internen Namen einer &quot;open&quot;-Auflistung. Auflistungswerte können vom Benutzer in der Benutzeroberfläche definiert werden.
* **xml (boolesch)**: Wenn diese Option aktiviert ist, werden alle im Element definierten Werte in XML in einem Feld vom Typ &quot;mData&quot; vom Typ TEXT gespeichert. Dies bedeutet, dass diese Felder nicht gefiltert oder sortiert werden.
* **xmlChildren (boolesch)**: erzwingt die Speicherung jedes untergeordneten Elements ( `<element>  or  <attribute>   ) of the   <element>    element in an XML document.   </element>  </attribute> </element>`
