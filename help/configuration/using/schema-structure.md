---
product: campaign
title: Schemastruktur in Adobe Campaign
description: Schemastruktur
feature: Custom Resources
role: Data Engineer, Developer
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: 3405efb8-a37c-4622-a271-63d7a4148751
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '1514'
ht-degree: 65%

---

# Grundlegendes zur Schemastruktur {#schema-structure}

Die grundlegende Struktur eines Schemas wird nachfolgend beschrieben.

## Datenschemata  {#data-schema}

Für einen `<srcschema>` ist die Struktur wie folgt:

```sql
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

```sql
<srcSchema name="schema_name" namespace="namespace">
...
</srcSchema>
```

Verwenden wir den folgenden XML-Inhalt, um die Struktur eines Schemas zu illustrieren:

```sql
<recipient email="John.doe@aol.com" created="2009/03/12" gender="1"> 
  <location city="London"/>
</recipient>
```

Mit dem zugehörigen Datenschema:

```sql
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

Der Einstiegspunkt des Schemas ist sein Hauptelement. Es ist einfach zu identifizieren, da es denselben Namen wie das Schema hat und das Stammelement untergeordnet sein sollte. Die Beschreibung des Inhalts beginnt mit diesem Element.

In unserem Beispiel wird das Hauptelement durch die folgende Zeile dargestellt:

```
<element name="recipient">
```

Die Elemente **`<attribute>`** und **`<element>`**, die dem Hauptelement folgen, werden verwendet, um die Speicherorte und Namen der Datenelemente in der XML-Struktur zu definieren.

In unserem Beispielschema sind dies:

```sql
<attribute name="email"/>
<attribute name="created"/>
<attribute name="gender"/>
<element name="location">
  <attribute name="city"/>
</element>
```

Es gelten die folgenden Regeln:

* Jedes **`<element>`** und **`<attribute>`** müssen mit dem Namen über das Attribut **name** identifiziert werden.

  >[!IMPORTANT]
  >
  >Der Name des Elements sollte kurz sein, vorzugsweise auf Englisch, und nur Zeichen einschließen, die in XML-Benennungsregeln zulässig sind.

* In der XML-Struktur dürfen nur **`<element>`**-Elemente **`<attribute>`**-Elemente und **`<element>`**-Elemente enthalten.
* Ein **`<attribute>`**-Element muss einen eindeutigen Namen innerhalb eines **`<element>`** haben.
* Die Verwendung von **`<elements>`** in mehrzeiligen Datenzeichenfolgen wird empfohlen.

## Datentypen {#data-types}

Der Datentyp wird über das Attribut **type** in den Elementen **`<attribute>`** und **`<element>`** eingegeben.

Eine detaillierte Liste finden Sie in der Beschreibung des Elements [`<attribute>` ](../../configuration/using/schema/attribute.md) und des Elements [`<element>` ](../../configuration/using/schema/element.md).

Wenn dieses Attribut nicht gefüllt wird, ist **string** der Standarddatentyp, es sei denn, das Element enthält untergeordnete Elemente. Wenn es gefüllt ist, wird es nur zur hierarchischen Strukturierung der Elemente verwendet (Element **`<location>`** in unserem Beispiel).

Die folgenden Datentypen werden in Schemata unterstützt:

* **string**: Zeichenfolge. Beispiele: ein Vorname, eine Stadt usw.

  Die Größe kann über das Attribut **length** (optional, Standardwert &quot;255&quot;) angegeben werden.

* **boolean**: Boolesches Feld. Beispiel für mögliche Werte: wahr/falsch, 0/1, ja/nein usw.
* **byte**, **short**, **long**: ganze Zahlen (1 Byte, 2 Byte, 4 Byte). Beispiele: Alter, Kontonummer, Anzahl der Punkte usw.
* **double**: Gleitkommazahl doppelter Genauigkeit. Beispiele: Preis, Quote usw.
* **date**, **datetime**: Datum und Datum + Uhrzeit. Beispiele: Geburtsdatum, Kaufdatum usw.
* **datetimenotz**: Datum + Uhrzeit ohne Zeitzonendaten.
* **timespan**: Dauer. Beispiel: Betriebszugehörigkeit.
* **memo**: Langtextfelder (mehrere Zeilen). Beispiele: eine Beschreibung, ein Kommentar usw.
* **uuid**: Felder &quot;uniqueidentifier&quot;, um eine GUID zu unterstützen (nur bei Microsoft SQL Server unterstützt).

  >[!NOTE]
  >
  >Um ein Feld **uuid** in einem anderen RDBMS als Microsoft SQL Server zu enthalten, muss die Funktion `the newuuid()` hinzugefügt und mit dem Standardwert ausgefüllt werden.

Im Folgenden finden Sie unser Schema mit den eingegebenen Typen:

```sql
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

### Mapping der Typen von Adobe Campaign/DBMS-Daten {#mapping-the-types-of-adobe-campaign-dbms-data}

In der folgenden Tabelle sind die Zuordnungen für die Datentypen aufgeführt, die von Adobe Campaign für die verschiedenen Datenbankverwaltungssysteme generiert wurden.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Adobe Campaign</strong><br /> </td> 
   <td> <strong>PosgreSQL</strong><br /> </td> 
   <td> <strong>Oracle</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> String <br /> </td> 
   <td> VARCHAR(255)<br /> </td> 
   <td> VARCHAR2 (NVARCHAR2 bei Unicode)<br /> </td> 
  </tr> 
  <tr> 
   <td> Boolean<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> NUMBER(3)<br /> </td> 
  </tr> 
  <tr> 
   <td> Byte<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> NUMBER(3)<br /> </td> 
  </tr> 
  <tr> 
   <td> short<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> NUMBER(5)<br /> </td> 
  </tr> 
  <tr> 
   <td> Double<br /> </td> 
   <td> DOPPELPRÄZISION<br /> </td> 
   <td> FLOAT<br /> </td> 
  </tr> 
  <tr> 
   <td> Long<br /> </td> 
   <td> INTEGER<br /> </td> 
   <td> NUMBER(10)<br /> </td> 
  </tr> 
  <tr> 
   <td> Int64<br /> </td> 
   <td> BIGINT<br /> </td> 
   <td> NUMBER(20)<br /> </td> 
  </tr> 
  <tr> 
   <td> Datum<br /> </td> 
   <td> DATE<br /> </td> 
   <td> DATE<br /> </td> 
  </tr> 
  <tr> 
   <td> Zeit<br /> </td> 
   <td> ZEIT<br /> </td> 
   <td> FLOAT<br /> </td> 
  </tr> 
  <tr> 
   <td> dateTime<br /> </td> 
   <td> TIMESTAMPZ<br /> </td> 
   <td> DATE<br /> </td> 
  </tr> 
  <tr> 
   <td> Datetimenotz<br /> </td> 
   <td> TIMESTAMPZ<br /> </td> 
   <td> DATE<br /> </td> 
  </tr> 
  <tr> 
   <td> Timespan<br /> </td> 
   <td> DOPPELPRÄZISION<br /> </td> 
   <td> FLOAT<br /> </td> 
  </tr> 
  <tr> 
   <td> Memo<br /> </td> 
   <td> TEXT<br /> </td> 
   <td> CLOB (NCLOB bei Unicode)<br /> </td> 
  </tr> 
  <tr> 
   <td> Blob<br /> </td> 
   <td> BLOB<br /> </td> 
   <td> BLOB<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Eigenschaften {#properties}

Die Elemente **`<elements>`** und **`<attributes>`** des Datenschemas können mit verschiedenen Eigenschaften angereichert werden. Sie können ein Label ausfüllen, um das aktuelle Element zu beschreiben.

### Labels und Beschreibungen {#labels-and-descriptions}

* Mit der Eigenschaft **label** können Sie eine kurze Beschreibung eingeben.

  >[!NOTE]
  >
  >Das Label ist mit der aktuellen Sprache der Instanz verknüpft.

  **Beispiel**:

  ```sql
  <attribute name="email" type="string" length="80" label="Email"/>
  ```

  Der Titel wird im Eingabeformular der Adobe Campaign-Clientkonsole angezeigt:

  ![](assets/d_ncs_integration_schema_label.png)

* Mit der Eigenschaft **desc** können Sie eine lange Beschreibung eingeben.

  Die Beschreibung wird im Formular in der Statusleiste des Hauptfensters der Adobe Campaign-Clientkonsole angezeigt.

  >[!NOTE]
  >
  >Die Beschreibung ist mit der aktuellen Sprache der Instanz verknüpft.

  **Beispiel**:

  ```sql
  <attribute name="email" type="string" length="80" label="Email" desc="Email of recipient"/>
  ```

### Standardwerte {#default-values}

Verwenden Sie die Eigenschaft **default** , um einen Ausdruck zu definieren, der bei der Inhaltserstellung einen Standardwert zurückgibt.

Der Wert muss ein mit der XPath-Sprache kompatibler Ausdruck sein. Weitere Informationen hierzu finden Sie unter [Verweisen auf XPath](../../configuration/using/schema-structure.md#referencing-with-xpath).

**Beispiel**:

* Aktuelles Datum: **default=&quot;GetDate()&quot;**
* Zähler: **default=&quot;&#39;FRM&#39;+CounterValue(&#39;myCounter&#39;)&quot;**

  In diesem Beispiel wird der Standardwert mithilfe der Verkettung einer Zeichenfolge und des Aufrufs der Funktion **CounterValue** mit einem freien Zählernamen erstellt. Die zurückgegebene Zahl wird bei jedem Einfügen um 1 erhöht.

  >[!NOTE]
  >
  >Navigieren Sie in der Adobe Campaign-Clientkonsole zum Ordner **[!UICONTROL Administration > Zähler]** des Explorers, um Zähler zu verwalten.

Um einen Standardwert mit einem Feld zu verknüpfen, können Sie die `<default>` oder `<sqldefault>` verwenden   -Feld.

`<default>` : ermöglicht es Ihnen, das Feld beim Erstellen von Entitäten mit einem Standardwert vorauszufüllen. Der Wert wird kein SQL-Standardwert sein.

`<sqldefault>` : ermöglicht es Ihnen, beim Erstellen eines Felds einen zusätzlichen Wert zu erhalten. Dieser Wert wird als SQL-Ergebnis angezeigt. Während einer Aktualisierung des Schemas wirkt sich dieser Wert nur auf die neuen Einträge aus.

### Auflistungen {#enumerations}

#### Aufzählung öffnen {#free-enumeration}

Mit der Eigenschaft **userEnum** können Sie eine geöffnete Auflistung definieren, in der die über dieses Feld eingegebenen Werte gespeichert und angezeigt werden.

Die Syntax sieht folgendermaßen aus:

`userEnum="name of enumeration"`

Diese Werte werden in einer Dropdown-Liste im Formular angezeigt:

![](assets/d_ncs_integration_schema_user_enum.png)

>[!NOTE]
>
>Navigieren Sie in der Adobe Campaign-Clientkonsole zum Ordner **[!UICONTROL Administration > Auflistungen]** des Explorers, um Auflistungen zu verwalten.

#### Auflistung festlegen {#set-enumeration}

Mit der Eigenschaft **enum** können Sie eine feste Auflistung definieren, die verwendet wird, wenn die Liste der möglichen Werte im Voraus bekannt ist.

Das Attribut **enum** bezieht sich auf die Definition einer Auflistungsklasse, die im Schema außerhalb des Hauptelements gefüllt wird.

Auflistungen ermöglichen es dem Benutzer, einen Wert aus einer Dropdown-Liste auszuwählen, anstatt ihn in ein reguläres Eingabefeld einzugeben:

![](assets/d_ncs_integration_schema_enum.png)

Beispiel für eine Deklaration einer Auflistung im Datenschema:

```sql
<enumeration name="gender" basetype="byte" default="0">    
  <value name="unknown" label="Not specified" value="0"/>    
  <value name="male" label="male" value="1"/>   
  <value name="female" label="female" value="2"/>   
</enumeration>
```

Eine Auflistung wird über das Element **`<enumeration>`** außerhalb des Hauptelements deklariert.

Die Eigenschaften der Auflistung lauten wie folgt:

* **baseType**: Datentyp, der den Werten zugeordnet ist
* **label**: Beschreibung der Auflistung
* **name**: Name der Auflistung
* **default**: Standardwert der Auflistung

Die Werte für die Auflistung werden im Element **`<value>`** mit den folgenden Attributen deklariert:

* **name**: Name des intern gespeicherten Werts
* **label**: in der grafischen Benutzeroberfläche angezeigte Bezeichnung

#### dbenum-Auflistung {#dbenum-enumeration}

*Mit der Eigenschaft **dbenum** können Sie eine Auflistung definieren, deren Eigenschaften denen der Eigenschaft **enum** ähneln.

Das Attribut **name** speichert den Wert jedoch nicht intern, sondern speichert einen Code, mit dem Sie die betreffenden Tabellen erweitern können, ohne ihr Schema zu ändern.

Diese Auflistung dient beispielsweise zur Angabe der Art von Kampagnen.

![](assets/d_ncs_configuration_schema_dbenum.png)

### Beispiel {#example}

Beispiel des um diese Eigenschaften ergänzten Schemas:

```sql
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

## Sammlungen {#collections}

Eine Sammlung ist eine Liste von Elementen mit gleichem Namen und auf gleicher Hierarchieebene.

Mithilfe des Attributs **unbound** mit dem Wert &quot;true&quot; können Sie ein Sammlungselement füllen.

**Beispiel**: Definition des Sammlungselements **`<group>`** im Schema.

```sql
<element name="group" unbound="true" label="List of groups">
  <attribute name="label" type="string" label="Label"/>
</element>
```

Mit Projektion des XML-Inhalts:

```sql
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
* **../@email**: markiert die E-Mail-Adresse des übergeordneten Elements des aktuellen Elements
* **group`[1]/@label`**: wählt das Attribut &quot;label&quot; aus, das dem ersten **`<group>`**-Sammlungselement untergeordnet ist,
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
* **@email + &#39;(&#39;+@created+&#39;)&#39;**: erstellt einen String, indem der Wert der E-Mail-Adresse, die zum Erstellungsdatum hinzugefügt wurde, in Klammern gesetzt wird (für den String-Typ muss die Konstante in Anführungszeichen gesetzt werden).

Die Ausdrücke wurden um Funktionen auf hoher Ebene erweitert, um das Potenzial dieser Sprache zu erweitern.

In der Adobe Campaign-Client-Konsole können Sie über einen beliebigen Ausdruckseditor auf die Liste der verfügbaren Funktionen zugreifen:

![](assets/d_ncs_integration_schema_function.png)

**Beispiel**:

* **GetDate()**: gibt das aktuelle Datum zurück,
* **Year(@created)**: gibt das Jahr des im Attribut &quot;created&quot;enthaltenen Datums aus
* **GetEmailDomain(@email)**: gibt die Domäne der E-Mail-Adresse zurück

## Erstellen einer Zeichenfolge über den Compute string {#building-a-string-via-the-compute-string}

Ein **Compute string** ist ein XPath-Ausdruck, mit dem eine Zeichenfolge erstellt wird, die einen Eintrag in einer mit dem Schema verknüpften Tabelle darstellt. **Compute string** wird hauptsächlich in der grafischen Oberfläche verwendet, um die Beschriftung eines ausgewählten Eintrags anzuzeigen.

Der **Compute string** wird über das Element **`<compute-string>`** unter dem Hauptelement des Datenschemas definiert. Ein **expr**-Attribut enthält einen XPath-Ausdruck zur Berechnung der Anzeige.

**Beispiel**: Compute string der Empfänger-Tabelle.

```sql
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


## Weitere Informationen

Weitere Informationen finden Sie unter den folgenden Links:

* [Erste Schritte mit Schemata](about-schema-reference.md)
* [Datenbank-Mapping](database-mapping.md)
* [Verknüpfungs-Management](database-links.md)
* [Schlüsselverwaltung](database-keys.md)
* [Campaign-Datenmodell](about-data-model.md)