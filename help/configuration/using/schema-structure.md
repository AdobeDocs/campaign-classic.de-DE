---
product: campaign
title: Schemastruktur
description: Schemastruktur
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: 3405efb8-a37c-4622-a271-63d7a4148751
source-git-commit: 00b8a9b4a693920aa6b4be9e7c41f08c2e53a0c6
workflow-type: tm+mt
source-wordcount: '1570'
ht-degree: 86%

---

# Schemastruktur{#schema-structure}

![](../../assets/v7-only.svg)

Die Grundstruktur eines `<srcschema>` sieht wie folgt aus:

```
<srcSchema>
    <enumeration>
        ...          //definition of enumerations
    </enumeration>
   
    <element>         //definition of the root <element>    (mandatory)

        <compute-string/>  //definition of a compute-string
        <dbindex>
            ...        //definition of indexes
        </dbindex>
        <key>
            ...        //definition of keys
        </key>
        <sysFilter>
            ...           //definition of filters
        </sysFilter>
        <attribute>
            ...             //definition of fields
        </attribute>
    
            <element>           //definition of sub-<element> 
                  <attribute>           //(collection, links or XML)
                  ...                         //and additional fields
                  </attribute>
                ...
            </element>
      
    </element> 

        <methods>                 //definition of SOAP methods
            <method>
                ...
            </method>
            ...
    </methods>  
          
</srcSchema>
```

Das XML-Dokument eines Datenschemas muss die Wurzel **`<srcschema>`** mit den Attributen **name** und **namespace** zur Angabe des Schemanamens und des Namespace enthalten.

```
<srcSchema name="schema_name" namespace="namespace">
...
</srcSchema>
```

Verwenden wir den folgenden XML-Inhalt, um die Struktur eines Schemas zu illustrieren:

```
<recipient email="John.doe@aol.com" created="2009/03/12" gender="1"> 
  <location city="London"/>
</recipient>
```

Mit dem zugehörigen Datenschema:

```
<srcSchema name="recipient" namespace="cus">
  <element name="recipient">
    <attribute name="email"/>
    <attribute name="created"/>
    <attribute name="gender"/>
    <element name="location">
      <attribute name="city"/>
   </element>
  </element>
</srcSchema>
```

## Beschreibung  {#description}

Der Startpunkt des Schemas ist sein Hauptelement. Es ist leicht identifizierbar, da sein Name mit dem des Schemas identisch ist. Außerdem handelt es sich um das direkte untergeordnete Element der Wurzel. Ausgehend von diesem Element beginnt die Inhaltsbeschreibung.

In unserem Beispiel wird das Hauptelement durch die folgende Zeile dargestellt:

```
<element name="recipient">
```

Die Elemente **`<attribute>`** und **`<element>`**, die dem Hauptelement folgen, ermöglichen es Ihnen, die Speicherorte und Namen der Datenelemente in der XML-Struktur zu definieren.

In unserem Beispielschema sind dies:

```
<attribute name="email"/>
<attribute name="created"/>
<attribute name="gender"/>
<element name="location">
  <attribute name="city"/>
</element>
```

Folgende Regeln müssen eingehalten werden:

* Jedes **`<element>`** und **`<attribute>`** müssen mit dem Namen über das Attribut **name** identifiziert werden.

   >[!IMPORTANT]
   >
   >Der Name des Elements sollte kurz sein, vorzugsweise in Englisch, und nur gemäß den XML-Benennungsregeln zulässige Zeichen enthalten.

* In der XML-Struktur dürfen nur **`<element>`**-Elemente **`<attribute>`**-Elemente und **`<element>`**-Elemente enthalten.
* Ein **`<attribute>`**-Element muss einen eindeutigen Namen innerhalb eines **`<element>`** haben.
* Die Verwendung von **`<elements>`** in mehrzeiligen Datenzeichenfolgen wird empfohlen.

## Datentypen {#data-types}

Der Datentyp wird über das Attribut **type** in den Elementen **`<attribute>`** und **`<element>`** eingegeben.

Eine detaillierte Liste finden Sie in der Beschreibung der [`<attribute>` element](../../configuration/using/schema/attribute.md) und [`<element>` element](../../configuration/using/schema/element.md)).

Wenn dieses Attribut nicht gefüllt wird, ist **string** der Standarddatentyp, es sei denn, das Element enthält untergeordnete Elemente. Wenn es gefüllt ist, wird es nur zur hierarchischen Strukturierung der Elemente verwendet (Element **`<location>`** in unserem Beispiel).

Die folgenden Datentypen werden in Schemata unterstützt:

* **string**: Zeichenfolge. Beispiele: ein Vorname, eine Stadt usw.

   Die Größe kann über das Attribut **length** (optional, Standardwert &quot;255&quot;) angegeben werden.

* **boolean**: Boolesches Feld. Beispiel für mögliche Werte: true/false, 0/1, yes/no usw.
* **byte**, **short**, **long**: ganze Zahlen (1 Byte, 2 Byte, 4 Byte). Beispiele: Alter, Kontonummer, Anzahl der Punkte usw.
* **double**: Gleitkommazahl doppelter Genauigkeit. Beispiele: Preis, Quote usw.
* **date**, **datetime**: Datum und Datum + Uhrzeit. Beispiele: Geburtsdatum, Kaufdatum usw.
* **datetimenotz**: Datum + Uhrzeit ohne Zeitzonendaten.
* **timespan**: Dauer. Beispiel: Betriebszugehörigkeit.
* **memo**: Langtextfelder (mehrere Zeilen). Beispiele: eine Beschreibung, ein Kommentar usw.
* **uuid**: eindeutig identifizierende Felder zur Unterstützung einer GUID (nur in Microsoft SQL Server unterstützt).

   >[!NOTE]
   >
   >So enthalten Sie eine **uuid** in anderen Engines als Microsoft SQL Server muss die Funktion &quot;newuid()&quot; hinzugefügt und mit dem Standardwert ausgefüllt werden.

Im Folgenden finden Sie unser Schema mit den eingegebenen Typen:

```
<srcSchema name="recipient" namespace="cus">
  <element name="recipient">
    <attribute name="email" type="string" length="80"/>
    <attribute name="created" type="datetime"/>
    <attribute name="gender" type="byte"/>
    <element name="location">
      <attribute name="city" type="string" length="50"/>
   </element>
  </element>
</srcSchema>
```

### Mapping der Adobe Campaign/DBMS-Datentypen {#mapping-the-types-of-adobe-campaign-dbms-data}

In der folgenden Tabelle sind die Zuordnungen für die Datentypen aufgeführt, die von Adobe Campaign für die verschiedenen Datenbankverwaltungssysteme generiert wurden.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Adobe Campaign</strong><br /> </td> 
   <td> <strong>PosgreSQL</strong><br /> </td> 
   <td> <strong>Oracle</strong><br /> </td> 
   <td> <strong>Teradata</strong><br /> </td> 
   <td> <strong>DB2</strong><br /> </td> 
   <td> <strong>MS SQL</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> String <br /> </td> 
   <td> VARCHAR(255)<br /> </td> 
   <td> VARCHAR2 (NVARCHAR2, falls Unicode vorhanden)<br /> </td> 
   <td> VARCHAR (VARCHARZEICHENSATZ UNICODE, falls Unicode vorhanden)<br /> </td> 
   <td> VARCHAR<br /> </td> 
   <td> VARCHAR (NVARCHAR, falls unicode)<br /> </td> 
  </tr> 
  <tr> 
   <td> Boolesch<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> NUMBER(3)<br /> </td> 
   <td> NUMERISCH(3)<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> TINYINT<br /> </td> 
  </tr> 
  <tr> 
   <td> Byte<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> NUMBER(3)<br /> </td> 
   <td> NUMERISCH(3)<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> TINYINT<br /> </td> 
  </tr> 
  <tr> 
   <td> Kurz<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> NUMBER(5)<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> SMALLINT<br /> </td> 
  </tr> 
  <tr> 
   <td> Doppelt<br /> </td> 
   <td> DOPPELPRÄZISE<br /> </td> 
   <td> FLUSS<br /> </td> 
   <td> FLUSS<br /> </td> 
   <td> DOUBLE<br /> </td> 
   <td> FLUSS<br /> </td> 
  </tr> 
  <tr> 
   <td> Lang<br /> </td> 
   <td> INTEGER<br /> </td> 
   <td> NUMBER(10)<br /> </td> 
   <td> INTEGER<br /> </td> 
   <td> INTEGER<br /> </td> 
   <td> INT<br /> </td> 
  </tr> 
  <tr> 
   <td> Int64<br /> </td> 
   <td> BIGINT<br /> </td> 
   <td> NUMBER(20)<br /> </td> 
   <td> NUMERISCH(20)<br /> </td> 
   <td> BIGINT<br /> </td> 
   <td> BIGINT<br /> </td> 
  </tr> 
  <tr> 
   <td> Datum<br /> </td> 
   <td> DATUM<br /> </td> 
   <td> DATUM<br /> </td> 
   <td> ZEITSTEMPEL<br /> </td> 
   <td> DATUM<br /> </td> 
   <td> DATETIME<br /> </td> 
  </tr> 
  <tr> 
   <td> Zeit<br /> </td> 
   <td> UHRZEIT<br /> </td> 
   <td> FLUSS<br /> </td> 
   <td> UHRZEIT<br /> </td> 
   <td> UHRZEIT<br /> </td> 
   <td> FLUSS<br /> </td> 
  </tr> 
  <tr> 
   <td> Datum/Uhrzeit<br /> </td> 
   <td> TIMESTAMPZ<br /> </td> 
   <td> DATUM<br /> </td> 
   <td> ZEITSTEMPEL<br /> </td> 
   <td> ZEITSTEMPEL<br /> </td> 
   <td> MS SQL &lt; 2008: DATETIME<br /> MS SQL &gt;= 2012: DATETIMEOFFSET<br /> </td> 
  </tr> 
  <tr> 
   <td> Datetimenotz<br /> </td> 
   <td> TIMESTAMPZ<br /> </td> 
   <td> DATUM<br /> </td> 
   <td> ZEITSTEMPEL<br /> </td> 
   <td> ZEITSTEMPEL<br /> </td> 
   <td> MS SQL &lt; 2008: DATETIME<br /> MS SQL &gt;= 2012: DATETIME2<br /> </td> 
  </tr> 
  <tr> 
   <td> Zeitbereich<br /> </td> 
   <td> DOPPELPRÄZISE<br /> </td> 
   <td> FLUSS<br /> </td> 
   <td> FLUSS<br /> </td> 
   <td> DOUBLE<br /> </td> 
   <td> FLUSS<br /> </td> 
  </tr> 
  <tr> 
   <td> Memo<br /> </td> 
   <td> TEXT<br /> </td> 
   <td> CLOB (NCLOB, wenn Unicode)<br /> </td> 
   <td> CLOB (CLOB-ZEICHENSATZ UNICODE, falls Unicode)<br /> </td> 
   <td> CLOB(6M)<br /> </td> 
   <td> TEXT (NTEXT bei Unicode)<br /> </td> 
  </tr> 
  <tr> 
   <td> Blob<br /> </td> 
   <td> BLOB<br /> </td> 
   <td> BLOB<br /> </td> 
   <td> BLOB<br /> </td> 
   <td> BLOB(4M)<br /> </td> 
   <td> BILD<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Eigenschaften {#properties}

Die **`<elements>`** und **`<attributes>`** -Elemente des Datenschemas können mit verschiedenen Eigenschaften angereichert werden. Sie können ein Label ausfüllen, um das aktuelle Element zu beschreiben.

### Labels und Beschreibungen {#labels-and-descriptions}

* Mit der Eigenschaft **label** können Sie eine kurze Beschreibung eingeben.

   >[!NOTE]
   >
   >Das Label ist mit der aktuellen Sprache der Instanz verknüpft.

   **Beispiel**:

   ```
   <attribute name="email" type="string" length="80" label="Email"/>
   ```

   Das Label wird vom Formular der Adobe Campaign-Client-Konsole aus angezeigt:

   ![](assets/d_ncs_integration_schema_label.png)

* Mit der Eigenschaft **desc** können Sie eine lange Beschreibung eingeben.

   Die Beschreibung ist vom Formular aus in der Statusleiste des Hauptfensters der Adobe Campaign-Client-Konsole zu finden.

   >[!NOTE]
   >
   >Die Beschreibung ist mit der aktuellen Sprache der Instanz verknüpft.

   **Beispiel**:

   ```
   <attribute name="email" type="string" length="80" label="Email" desc="Email of recipient"/>
   ```

### Standardwerte {#default-values}

Mit der Eigenschaft **default** können Sie einen Ausdruck definieren, der bei der Inhaltserstellung einen Standardwert zurückgibt.

Der Wert muss ein mit der XPath-Sprache kompatibler Ausdruck sein. Weitere Informationen hierzu finden Sie unter [Verweisen mit XPath](../../configuration/using/schema-structure.md#referencing-with-xpath).

**Beispiel**:

* Aktuelles Datum: **default=&quot;GetDate()&quot;**
* Zähler: **default=&quot;&#39;FRM&#39;+CounterValue(&#39;myCounter&#39;)&quot;**

   In diesem Beispiel wird der Standardwert mithilfe der Verkettung einer Zeichenfolge und des Aufrufs der Funktion **CounterValue** mit einem freien Zählernamen erstellt. Die zurückgegebene Zahl wird bei jedem Einfügen um 1 erhöht.

   >[!NOTE]
   >
   >In der Adobe Campaign-Client-Konsole wird der Knoten **[!UICONTROL Administration > Zähler]** verwendet, um Zähler zu verwalten.

Um einen Standardwert mit einem Feld zu verknüpfen, können Sie die Variable `<default>  or  <sqldefault>   field.  </sqldefault> </default>` verwenden.

`<default>` : ermöglicht es Ihnen, das Feld beim Erstellen von Entitäten mit einem Standardwert vorauszufüllen. Der Wert wird kein SQL-Standardwert sein.

`<sqldefault>` : ermöglicht es Ihnen, beim Erstellen eines Felds einen zusätzlichen Wert zu erhalten. Dieser Wert wird als SQL-Ergebnis angezeigt. Während einer Aktualisierung des Schemas wirkt sich dieser Wert nur auf die neuen Einträge aus.

### Auflistungen {#enumerations}

#### Freie Auflistung {#free-enumeration}

Mit der Eigenschaft **userEnum** können Sie eine freie Auflistung definieren, um die in diesem Feld eingegebenen Werte zu speichern und anzuzeigen. Die Syntax sieht folgendermaßen aus:

**userEnum=&quot;Name der Auflistung&quot;**

Der Name der Auflistung kann frei gewählt und für andere Felder freigegeben werden.

Diese Werte werden in einer Dropdown-Liste im Formular angezeigt:

![](assets/d_ncs_integration_schema_user_enum.png)

>[!NOTE]
>
>In der Adobe Campaign-Client-Konsole wird der Knoten **[!UICONTROL Administration > Auflistungen]** zum Verwalten von Auflistungen verwendet.

#### Auflistung festlegen {#set-enumeration}

Mit der Eigenschaft **enum** können Sie eine feste Auflistung definieren, die verwendet wird, wenn die Liste der möglichen Werte im Voraus bekannt ist.

Das Attribut **enum** bezieht sich auf die Definition einer Auflistungsklasse, die im Schema außerhalb des Hauptelements gefüllt wird.

Auflistungen ermöglichen es dem Benutzer, einen Wert aus einer Dropdown-Liste auszuwählen, anstatt ihn in ein reguläres Eingabefeld einzugeben:

![](assets/d_ncs_integration_schema_enum.png)

Beispiel für eine Deklaration einer Auflistung im Datenschema:

```
<enumeration name="gender" basetype="byte" default="0">    
  <value name="unknown" label="Not specified" value="0"/>    
  <value name="male" label="male" value="1"/>   
  <value name="female" label="female" value="2"/>   
</enumeration>
```

Eine Auflistung wird über das Element **`<enumeration>`** außerhalb des Hauptelements deklariert.

Die Eigenschaften der Auflistung lauten wie folgt:

* **baseType**: Datentyp, der mit den Werten verknüpft ist,
* **label**: Beschreibung der Auflistung,
* **name**: Name der Auflistung,
* **default**: Standardwert der Auflistung.

Die Werte für die Auflistung werden im Element **`<value>`** mit den folgenden Attributen deklariert:

* **name**: Name des intern gespeicherten Werts,
* **label**: über die grafische Oberfläche angezeigtes Label.

#### dbenum-Auflistung {#dbenum-enumeration}

* Mit der Eigenschaft **dbenum** können Sie eine Auflistung definieren, deren Eigenschaften denen der Eigenschaft **enum** ähnlich sind.

   Das Attribut **name** speichert den Wert jedoch nicht intern, sondern speichert einen Code, mit dem Sie die betreffenden Tabellen erweitern können, ohne ihr Schema zu ändern.

   Die Werte werden über den Knoten **[!UICONTROL Administration > Auflistungen]** definiert.

   Diese Auflistung dient beispielsweise zur Angabe der Art von Kampagnen.

   ![](assets/d_ncs_configuration_schema_dbenum.png)

### Beispiel {#example}

Beispiel des um diese Eigenschaften ergänzten Schemas:

```
<srcSchema name="recipient" namespace="cus">
  <enumeration name="gender" basetype="byte">    
    <value name="unknown" label="Not specified" value="0"/>    
    <value name="male" label="male" value="1"/>   
    <value name="female" label="female" value="2"/>   
  </enumeration>

  <element name="recipient">
    <attribute name="email" type="string" length="80" label="Email" desc="Email of recipient"/>
    <attribute name="created" type="datetime" label="Date of creation" default="GetDate()"/>
    <attribute name="gender" type="byte" label="gender" enum="gender"/>
    <element name="location" label="Location">
      <attribute name="city" type="string" length="50" label="City" userEnum="city"/>
   </element>
  </element>
</srcSchema>
```

## Kollektionen {#collections}

Eine Kollektion ist eine Liste von Elementen mit gleichem Namen und auf gleicher Hierarchieebene.

Mithilfe des Attributs **unbound** mit dem Wert &quot;true&quot; können Sie ein Kollektionselement füllen.

**Beispiel**: Definition des Kollektionselements **`<group>`** im Schema.

```
<element name="group" unbound="true" label="List of groups">
  <attribute name="label" type="string" label="Label"/>
</element>
```

Mit Projektion des XML-Inhalts:

```
<group label="Group1"/>
<group label="Group2"/>
```

## Verweisen mit XPath {#referencing-with-xpath}

Die XPath-Sprache wird in Adobe Campaign verwendet, um ein zu einem Datenschema gehörendes Element oder Attribut zu adressieren.

XPath ist eine Syntax, die es ermöglicht, einen Knoten in der Baumstruktur eines XML-Dokuments zu lokalisieren.

Elemente werden mit ihren Namen bezeichnet, während den Namen von Attributen ein &quot;@&quot;-Zeichen vorangestellt wird.

**Beispiel**:

* **@email**: wählt die E-Mail-Adresse aus,
* **location/@city**: wählt das Attribut &quot;city&quot; unter dem Element **`<location>`** aus,
* **../@email**: wählt die E-Mail-Adresse aus dem übergeordneten Element des aktuellen Elements aus,
* **group`[1]/@label`**: wählt das Attribut &quot;label&quot; aus, das dem ersten **`<group>`**- Kollektionselement untergeordnet ist,
* **group`[@label='test1']`**: wählt das Attribut &quot;label&quot; aus, das dem Element **`<group>`** untergeordnet ist und den Wert &quot;test1&quot; enthält.

>[!NOTE]
>
>Eine zusätzliche Einschränkung wird hinzugefügt, wenn der Pfad ein Unterelement kreuzt. In diesem Fall muss der folgende Ausdruck zwischen Klammern stehen:
>
>* **location/@city** ist nicht gültig; verwenden Sie **`[location/@city]`**
>* **`[@email]`** und **@email** entsprechen einander

>


Es ist auch möglich, komplexe Ausdrücke wie die folgenden arithmetischen Operationen zu definieren:

* **@gender+1**: fügt 1 zum Inhalt des Attributs **gender** hinzu,
* **@email + &#39;(&#39;+@created+&#39;)&#39;**: erstellt eine Zeichenfolge unter Verwendung des Werts der E-Mail-Adresse, zu der das Erstellungsdatum zwischen Klammern hinzugefügt wird (für den Typ &quot;string&quot; muss die Konstante in Anführungszeichen gesetzt werden).

Die Ausdrücke wurden um Funktionen auf hoher Ebene erweitert, um das Potenzial dieser Sprache zu erweitern.

In der Adobe Campaign-Client-Konsole können Sie über einen beliebigen Ausdruckseditor auf die Liste der verfügbaren Funktionen zugreifen:

![](assets/d_ncs_integration_schema_function.png)

**Beispiel**:

* **GetDate()**: gibt das aktuelle Datum zurück,
* **Year(@created)**: gibt das Jahr des Datums zurück, das im Attribut &quot;created&quot; enthalten ist,
* **GetEmailDomain(@email)**: gibt die Domain der E-Mail-Adresse zurück.

## Erstellen einer Zeichenfolge über den Compute string {#building-a-string-via-the-compute-string}

Ein **Compute string** ist ein XPath-Ausdruck, mit dem eine Zeichenfolge erstellt wird, die einen Eintrag in einer mit dem Schema verknüpften Tabelle darstellt. **Compute string** wird hauptsächlich in der grafischen Oberfläche verwendet, um die Beschriftung eines ausgewählten Eintrags anzuzeigen.

Der **Compute string** wird über das Element **`<compute-string>`** unter dem Hauptelement des Datenschemas definiert. Ein **expr**-Attribut enthält einen XPath-Ausdruck zur Berechnung der Anzeige.

**Beispiel**: Compute string der Empfänger-Tabelle.

```
<srcSchema name="recipient" namespace="nms">  
  <element name="recipient">
    <compute-string expr="@lastName + ' ' + @firstName +' (' + @email + ')' "/>
    ...
  </element>
</srcSchema>
```

Ergebnis der berechneten Zeichenfolge für einen Empfänger: **Doe John (john.doe@aol.com)**

>[!NOTE]
>
>Wenn das Schema keinen Compute string enthält, wird standardmäßig ein Compute string mit den Werten des Primärschlüssels des Schemas gefüllt.
