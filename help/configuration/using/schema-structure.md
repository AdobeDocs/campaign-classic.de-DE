---
title: Schemastruktur
seo-title: Schemastruktur
description: Schemastruktur
seo-description: null
page-status-flag: never-activated
uuid: 9be70907-6154-4890-91e8-fd0fac30ab05
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: schema-reference
discoiquuid: b5c8faf7-d0ae-4d95-b7fe-6ef9674a33d2
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: f9b3508fee3b441752648258b1bc9d5d2b919791

---


# Schemastruktur{#schema-structure}

Die Grundstruktur eines `<srcschema>` ist wie folgt:

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

The XML document of a data schema must contain the **`<srcschema>`** root element with the **name** and **namespace** attributes to populate the schema name and its namespace.

```
<srcSchema name="schema_name" namespace="namespace">
...
</srcSchema>
```

Verwenden Sie den folgenden XML-Inhalt, um die Struktur eines Datenschemas zu illustrieren:

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

## Beschreibung {#description}

Der Startpunkt des Schemas ist sein Hauptelement. Es ist leicht identifizierbar, da sein Name mit dem des Schemas identisch ist. Außerdem handelt es sich um das direkte Kindelement der Wurzel. Ausgehend von diesem Element beginnt die Inhaltsbeschreibung.

In unserem Beispiel wird das Hauptelement durch die folgende Zeile dargestellt:

```
<element name="recipient">
```

Mithilfe der Elemente **`<attribute>`** und **`<element>`** , die dem Hauptelement folgen, können Sie die Speicherorte und Namen der Datenelemente in der XML-Struktur definieren.

In unserem Beispielschema lauten die folgenden:

```
<attribute name="email"/>
<attribute name="created"/>
<attribute name="gender"/>
<element name="location">
  <attribute name="city"/>
</element>
```

Folgende Regeln müssen eingehalten werden:

* Jede **`<element>`** und **`<attribute>`** muss durch den Namen über das **Attribut name** identifiziert werden.

   >[!CAUTION]
   >
   >Der Name des Elements sollte kurz sein, vorzugsweise in Englisch, und nur autorisierte Zeichen gemäß XML-Benennungsregeln einschließen.

* Nur **`<element>`** Elemente können **`<attribute>`** Elemente und **`<element>`** Elemente in der XML-Struktur enthalten.
* Ein **`<attribute>`** Element muss einen eindeutigen Namen innerhalb eines **`<element>`** Elements haben.
* Die Verwendung von**`<elements>`** in mehrzeiligen Datenzeichenfolgen wird empfohlen.

## Datentypen {#data-types}

Der Datentyp wird über das **type** -Attribut in den **`<attribute>`** Elementen und **`<element>`** -Elementen eingegeben.

Eine detaillierte Liste ist in der Beschreibung des [`<attribute>` Elements](../../configuration/using/elements-and-attributes.md#attribute--element) und des [`<element>` Elements](../../configuration/using/elements-and-attributes.md#element--element)verfügbar.

Wenn dieses Attribut nicht gefüllt wird, ist **string** der Standarddatentyp, es sei denn, das Element enthält untergeordnete Elemente. Ist dies der Fall, wird es nur dazu verwendet, die Elemente hierarchisch zu strukturieren (**`<location>`** Element in unserem Beispiel).

Die folgenden Datentypen werden in Schemata unterstützt:

* **Zeichenfolge**: Zeichenfolge. Beispiele: einen Vornamen, eine Stadt usw.

   Die Größe kann über das Attribut **length** angegeben werden (optional, Standardwert &quot;255&quot;).

* **boolean**: Boolesches Feld. Beispiel für mögliche Werte: true/false, 0/1, ja/nein usw.
* **byte**, **short**, **long**: ganze Zahlen (1 Byte, 2 Byte, 4 Byte). Beispiele: Alter, Kontonummer, Anzahl der Punkte usw.
* **Double**: Gleitkommazahl mit doppelter Genauigkeit. Beispiele: Preis, Preis usw.
* **Datum**, **Uhrzeit**: Daten und Daten + Uhrzeiten. Beispiele: Geburtsdatum, Kaufdatum usw.
* **datetimenotz**: Datum + Uhrzeit ohne Zeitzonendaten.
* **timespan**: Dauer. Beispiel: Ranghöhe.
* **memo**: Lange Textfelder (mehrere Zeilen). Beispiele: eine Beschreibung, einen Kommentar usw.
* **uuid**: &quot;uniqueidentifier&quot;-Felder zur Unterstützung einer GUID (nur in Microsoft SQL Server unterstützt).

   >[!NOTE]
   >
   >Um ein **uuid** -Feld in anderen Engines als Microsoft SQL Server zu enthalten, muss die Funktion &quot;newuid()&quot;hinzugefügt und mit ihrem Standardwert ausgefüllt werden.

Hier ist unser Beispielschema mit den eingegebenen Typen:

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

### Typen von Adobe Campaign-/DBMS-Daten zuordnen {#mapping-the-types-of-adobe-campaign-dbms-data}

In der folgenden Tabelle sind die Zuordnungen der Datentypen aufgeführt, die von Adobe Campaign für die verschiedenen Datenbankverwaltungssysteme generiert wurden.

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
   <td> VARCHAR2 (NVARCHAR2, wenn Unicode)<br /> </td> 
   <td> VARCHAR (VARCHAR-ZEICHEN EINSTELLEN VON UNICODE, falls Unicode<br /> </td> 
   <td> VARCHAR<br /> </td> 
   <td> VARCHAR (NVARCHAR, wenn Unicode)<br /> </td> 
  </tr> 
  <tr> 
   <td> Boolesch<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> NUMBER(3)<br /> </td> 
   <td> NUMERIC(3)<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> TINYINT<br /> </td> 
  </tr> 
  <tr> 
   <td> Byte<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> NUMBER(3)<br /> </td> 
   <td> NUMERIC(3)<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> TINYINT<br /> </td> 
  </tr> 
  <tr> 
   <td> Short<br /> </td> 
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
   <td> lang<br /> </td> 
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
   <td> NUMERIC(20)<br /> </td> 
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
   <td> Uhrzeit<br /> </td> 
   <td> ZEIT<br /> </td> 
   <td> FLUSS<br /> </td> 
   <td> ZEIT<br /> </td> 
   <td> ZEIT<br /> </td> 
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
   <td> Zeitspanne<br /> </td> 
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
   <td> CLOB (CLOB CHARACTER SET UNICODE, falls Unicode)<br /> </td> 
   <td> CLOB(6M)<br /> </td> 
   <td> TEXT (NTEXT, wenn Unicode)<br /> </td> 
  </tr> 
  <tr> 
   <td> Blob<br /> </td> 
   <td> BLOB<br /> </td> 
   <td> BLOB<br /> </td> 
   <td> BLOB<br /> </td> 
   <td> BLOB(4M)<br /> </td> 
   <td> IMAGE<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Eigenschaften {#properties}

Die Elemente **`<elements>`** und **`<attributes>`** Elemente des Datenschemas können mit verschiedenen Eigenschaften bereichert werden. Sie können eine Beschriftung ausfüllen, um das aktuelle Element zu beschreiben.

### Beschriftungen und Beschreibungen {#labels-and-descriptions}

* Mit der **label** -Eigenschaft können Sie eine kurze Beschreibung eingeben.

   >[!NOTE]
   >
   >Die Beschriftung ist mit der aktuellen Sprache der Instanz verknüpft.

   **Beispiel**:

   ```
   <attribute name="email" type="string" length="80" label="Email"/>
   ```

   Die Beschriftung wird über das Eingabeformular für die Adobe Campaign-Client-Konsole angezeigt:

   ![](assets/d_ncs_integration_schema_label.png)

* Mit der **desc** -Eigenschaft können Sie eine lange Beschreibung eingeben.

   Die Beschreibung wird im Eingabedatum in der Statusleiste des Hauptfensters der Adobe Campaign-Client-Konsole angezeigt.

   >[!NOTE]
   >
   >Die Beschreibung ist mit der aktuellen Sprache der Instanz verknüpft.

   **Beispiel**:

   ```
   <attribute name="email" type="string" length="80" label="Email" desc="Email of recipient"/>
   ```

### Standardwerte {#default-values}

Mit der **default** -Eigenschaft können Sie einen Ausdruck definieren, der bei der Inhaltserstellung einen Standardwert zurückgibt.

Der Wert muss ein Ausdruck sein, der der XPath-Sprache entspricht. Weitere Informationen finden Sie unter [Verweisen auf XPath](../../configuration/using/schema-structure.md#referencing-with-xpath).

**Beispiel**:

* Aktuelles Datum: **default=&quot;GetDate()&quot;**
* Zähler: **default=&quot;&#39;FRM&#39;+CounterValue(&#39;myCounter&#39;)&quot;**

   In diesem Beispiel wird der Standardwert mithilfe der Verkettung einer Zeichenfolge und des Aufrufs der Funktion **CounterValue** mit einem freien Zählernamen erstellt. Die zurückgegebene Zahl wird bei jeder Einfügung um 1 inkrementiert.

   >[!NOTE]
   >
   >In der Adobe Campaign-Client-Konsole wird der **[!UICONTROL Administration>Counters]** Knoten zum Verwalten von Zählern verwendet.

Um einen Standardwert mit einem Feld zu verknüpfen, können Sie die Variable `<default>  or  <sqldefault>   field.  </sqldefault> </default>`

`<default>` : ermöglicht Ihnen, das Feld beim Erstellen von Entitäten mit einem Standardwert vorauszufüllen. Der Wert ist kein SQL-Standardwert.

`<sqldefault>` : ermöglicht Ihnen, beim Erstellen eines Felds einen Mehrwert zu erzielen. Dieser Wert wird als SQL-Ergebnis angezeigt. Während einer Schemaaktualisierung wirkt sich dieser Wert nur auf die neuen Datensätze aus.

### Auflistungen {#enumerations}

#### Kostenlose Aufzählung {#free-enumeration}

Mit der **userEnum** -Eigenschaft können Sie eine kostenlose Aufzählung definieren, um die über dieses Feld eingegebenen Werte zu speichern und anzuzeigen. Die Syntax lautet wie folgt:

**userEnum=&quot;Name der Aufzählung&quot;**

Der Name der Aufzählung kann frei gewählt und für andere Felder freigegeben werden.

Diese Werte werden in einer Dropdown-Liste im Eingabefeld angezeigt:

![](assets/d_ncs_integration_schema_user_enum.png)

>[!NOTE]
>
>In der Adobe Campaign-Client-Konsole wird der **[!UICONTROL Administration > Enumerations]** Knoten zum Verwalten von Aufzählungen verwendet.

#### Enumeration festlegen {#set-enumeration}

Mit der **enum** -Eigenschaft können Sie eine feste Aufzählung definieren, die verwendet wird, wenn die Liste der möglichen Werte im Voraus bekannt ist.

Das **enum** -Attribut bezieht sich auf die Definition einer Aufzählungsklasse, die im Schema außerhalb des Hauptelements gefüllt wird.

Mit Aufzählungen kann der Benutzer einen Wert aus einer Dropdown-Liste auswählen, anstatt den Wert in ein reguläres Eingabefeld einzugeben:

![](assets/d_ncs_integration_schema_enum.png)

Beispiel einer Enumeration-Deklaration im Datenschema:

```
<enumeration name="gender" basetype="byte" default="0">    
  <value name="unknown" label="Not specified" value="0"/>    
  <value name="male" label="male" value="1"/>   
  <value name="female" label="female" value="2"/>   
</enumeration>
```

Eine Aufzählung wird über das **`<enumeration>`** Element außerhalb des Hauptelements deklariert.

Die Enumeration-Eigenschaften lauten wie folgt:

* **baseType**: Datentyp, der den Werten zugeordnet ist,
* **label**: Beschreibung der Aufzählung,
* **name**: Name der Aufzählung,
* **Standard**: Standardwert der Enumeration.

Die Aufzählungswerte werden im Element mit den folgenden Attributen deklariert **`<value>`** :

* **name**: Name des intern gespeicherten Werts,
* **label**: über die grafische Oberfläche angezeigt.

#### dbenum enumeration {#dbenum-enumeration}

* Mit der **dbenum** -Eigenschaft können Sie eine Aufzählung definieren, deren Eigenschaften denen der **enum** -Eigenschaft ähnlich sind.

   Das **name** -Attribut speichert den Wert jedoch nicht intern, sondern speichert einen Code, mit dem Sie die betreffenden Tabellen erweitern können, ohne ihr Schema zu ändern.

   Die Werte werden über die **[!UICONTROL Administration>Enumerations]** Node definiert.

   Diese Aufzählung dient beispielsweise zur Angabe der Art von Kampagnen.

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

Mit dem **ungebundenen** Attribut mit dem Wert &quot;true&quot;können Sie ein Collection-Element füllen.

**Beispiel**: Definition des **`<group>`** Collection-Elements im Schema.

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

## Mit XPath referenzieren {#referencing-with-xpath}

Die XPath-Sprache wird in Adobe Campaign verwendet, um ein zu einem Datenschema gehörendes Element oder Attribut zu adressieren.

XPath ist eine Syntax, die es ermöglicht, einen Knoten in der Baumstruktur eines XML-Dokuments zu lokalisieren.

Elemente werden mit ihren Namen bezeichnet, während den Namen von Attributen ein &quot;@&quot;-Zeichen vorangestellt wird.

**Beispiel**:

* **@email**: wählt die E-Mail aus,
* **location/@city**: wählt das Attribut &quot;city&quot;unter dem **`<location>`** Element aus
* **../@email**: wählt die E-Mail-Adresse aus dem übergeordneten Element des aktuellen Elements aus
* **Gruppe`[1]/@label`**: wählt das Attribut &quot;label&quot;aus, das dem ersten **`<group>`**Collection-Element untergeordnet ist
* **Gruppe`[@label='test1']`**: wählt das Attribut &quot;label&quot;aus, das dem **`<group>`**Element untergeordnet ist und den Wert &quot;test1&quot;enthält

>[!NOTE]
>
>Eine zusätzliche Einschränkung wird hinzugefügt, wenn der Pfad ein Unterelement passiert. In diesem Fall muss der folgende Ausdruck in Klammern gesetzt werden:
>
>* **location/@city** ist ungültig; verwenden **`[location/@city]`**
>* **`[@email]`** und **@email** entsprechen
>



Es ist auch möglich, komplexe Ausdrücke wie die folgenden arithmetischen Vorgänge zu definieren:

* **@gender+1**: 1 zum Inhalt des Attributs **gender** hinzufügt,
* **@email + &#39;(&#39;+@created+&#39;)&#39;**: erstellt eine Zeichenfolge unter Verwendung des Werts der E-Mail-Adresse, die zum Erstellungsdatum zwischen Klammern hinzugefügt wird (für den Zeichenfolgentyp muss die Konstante in Anführungszeichen gesetzt werden).

Zu den Ausdrücken wurden Funktionen auf hoher Ebene hinzugefügt, um das Potenzial dieser Sprache zu bereichern.

Sie können über einen beliebigen Ausdruckseditor in der Adobe Campaign-Client-Konsole auf die Liste der verfügbaren Funktionen zugreifen:

![](assets/d_ncs_integration_schema_function.png)

**Beispiel**:

* **GetDate()**: gibt das aktuelle Datum zurück
* **Jahr(@erstellt)**: gibt das Jahr des im Attribut &quot;erstellt&quot;enthaltenen Datums zurück.
* **GetEmailDomain(@email)**: gibt die Domäne der E-Mail-Adresse zurück.

## Erstellen einer Zeichenfolge über die Zeichenfolge &quot;calculate&quot; {#building-a-string-via-the-compute-string}

Eine **Compute-Zeichenfolge** ist ein XPath-Ausdruck, mit dem eine Zeichenfolge erstellt wird, die einen Datensatz in einer mit dem Schema verknüpften Tabelle darstellt. **Die Rechenzeichenfolge** wird hauptsächlich in der grafischen Oberfläche verwendet, um die Beschriftung eines ausgewählten Datensatzes anzuzeigen.

Die **Compute-Zeichenfolge** wird über das **`<compute-string>`** Element unter dem Hauptelement des Datenschemas definiert. Ein **Attribut &quot;expr** &quot;enthält einen XPath-Ausdruck zur Berechnung der Anzeige.

**Beispiel**: die Zeichenfolge der Empfängertabelle berechnen.

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
>Wenn das Schema keine Rechenzeichenfolge enthält, wird standardmäßig eine Rechenzeichenfolge mit den Werten des primären Schlüssels des Schemas gefüllt.

