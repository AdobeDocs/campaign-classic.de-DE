---
title: Datenbankzuordnung
seo-title: Datenbankzuordnung
description: Datenbankzuordnung
seo-description: null
page-status-flag: never-activated
uuid: a51df3eb-cae6-4e8d-8386-d62defc1b610
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: schema-reference
discoiquuid: bc06c00d-f421-452e-bde0-b4ecc12c72c8
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: e7ff12260d875b85256c8678fa8d100fd355398e

---


# Datenbankzuordnung{#database-mapping}

Die SQL-Zuordnung unseres Beispielschemas enthält das folgende XML-Dokument:

```
<schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">
  <enumeration basetype="byte" name="gender">    
    <value label="Not specified" name="unknown" value="0"/>    
    <value label="Male" name="male" value="1"/>    
    <value label="Female" name="female" value="2"/> 
  </enumeration>  

  <element name="recipient" sqltable="CusRecipient">    
    <attribute desc="Recipient e-mail address" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>    
    <attribute default="GetDate()" label="Date of creation" name="created" sqlname="tsCreated" type="datetime"/>    
    <attribute enum="gender" label="Gender" name="gender" sqlname="iGender" type="byte"/>    
    <element label="Location" name="location">      
      <attribute label="City" length="50" name="city" sqlname="sCity" type="string" userEnum="city"/>    
    </element>  
  </element>
</schema>
```

## Beschreibung {#description}

Das Stammelement des Schemas ist nicht mehr **`<srcschema>`** sondern **`<schema>`**.

Dies führt uns zu einem anderen Dokumenttyp, der automatisch aus dem Quellschema generiert wird, das einfach als Schema bezeichnet wird. Dieses Schema wird von der Adobe Campaign-Anwendung verwendet.

Die SQL-Namen werden automatisch anhand des Elementnamens und des Elementtyps bestimmt.

Die SQL-Benennungsregeln lauten wie folgt:

* Tabelle: Verkettung des Schema-Namespace und des Namens

   In unserem Beispiel wird der Name der Tabelle über das Hauptelement des Schemas im Attribut &quot; **sqltable** &quot;eingegeben:

   ```
   <element name="recipient" sqltable="CusRecipient">
   ```

* Feld: Name des Elements, dem ein Präfix vorangestellt wird, der nach Typ (&#39;i&#39; für Ganzzahl, &#39;d&#39; für Doppelpunkt, &#39;s&#39; für Zeichenfolge, &#39;ts&#39; für Datumsangaben usw.) definiert ist

   Der Feldname wird über das Attribut **sqlname** für jede Eingabe **`<attribute>`** und **`<element>`**:

   ```
   <attribute desc="E-mail address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/> 
   ```

>[!NOTE]
>
>SQL-Namen können aus dem Quellschema überladen werden. Füllen Sie dazu die Attribute &quot;sqltable&quot;oder &quot;sqlname&quot;für das betreffende Element aus.

Das SQL-Skript zum Erstellen der aus dem erweiterten Schema generierten Tabelle lautet wie folgt:

```
CREATE TABLE CusRecipient(
  iGender NUMERIC(3) NOT NULL Default 0,   
  sCity VARCHAR(50),   
  sEmail VARCHAR(80),
  tsCreated TIMESTAMP Default NULL);
```

Die SQL-Feldbeschränkungen lauten wie folgt:

* keine Nullwerte in numerischen und Datumsfeldern,
* Numerische Felder werden auf 0 initialisiert.

## XML-Felder {#xml-fields}

Standardmäßig werden alle typisierten **`<attribute>`** und **`<element>`** eingestellten Elemente einem SQL-Feld der Datenschemakabelle zugeordnet. Sie können dieses Feld jedoch in XML anstatt in SQL referenzieren. Das bedeutet, dass die Daten in einem Memofeld (&quot;mData&quot;) der Tabelle gespeichert werden, das die Werte aller XML-Felder enthält. Die Speicherung dieser Daten ist ein XML-Dokument, das die Schemastruktur einhält.

Um ein Feld in XML auszufüllen, müssen Sie dem betreffenden Element das **XML** -Attribut mit dem Wert &quot;true&quot;hinzufügen.

**Beispiel**: Es gibt zwei Beispiele für die Verwendung von XML-Feldern.

* Mehrzeiliges Kommentarfeld:

   ```
   <element name="comment" xml="true" type="memo" label="Comment"/>
   ```

* Beschreibung der Daten im HTML-Format:

   ```
   <element name="description" xml="true" type="html" label="Description"/>
   ```

   Mit dem Typ &quot;html&quot;können Sie den HTML-Inhalt in einem CDATA-Tag speichern und eine spezielle HTML-Bearbeitungsüberprüfung in der Adobe Campaign-Client-Oberfläche anzeigen.

Mithilfe von XML-Feldern können Sie Felder hinzufügen, ohne die physische Struktur der Datenbank ändern zu müssen. Ein weiterer Vorteil besteht darin, dass Sie weniger Ressourcen verwenden (Größe, Größe, Anzahl der Felder pro Tabelle usw.).

Der Hauptnachteil ist, dass es unmöglich ist, ein XML-Feld zu indizieren oder zu filtern.

## Indexierte Felder {#indexed-fields}

Mithilfe von Indizes können Sie die Leistung der in der Anwendung verwendeten SQL-Abfragen optimieren.

Ein Index wird aus dem Hauptelement des Datenschemas deklariert.

```
<dbindex name="name_of_index" unique="true/false">
  <keyfield xpath="xpath_of_field1"/>
  <keyfield xpath="xpath_of_field2"/>
  ...
</key>
```

Indizes folgen den folgenden Regeln:

* Ein Index kann auf ein oder mehrere Felder in der Tabelle verweisen.
* Ein Index kann in allen Feldern eindeutig sein (um Duplikate zu vermeiden), wenn das Attribut **unique** den Wert &quot;true&quot;enthält.
* Der SQL-Name des Indexes wird anhand des SQL-Namens der Tabelle und des Indexnamens bestimmt.

>[!NOTE]
>
>Als Standard sind Indizes die ersten Elemente, die aus dem Hauptelement des Schemas deklariert wurden.

>[!NOTE]
>
>Indizes werden während der Tabellenzuordnung (Standard oder FDA) automatisch erstellt.

**Beispiel**:

* Hinzufügen eines Index zur E-Mail-Adresse und zum Ort:

   ```
   <srcSchema name="recipient" namespace="cus">
     <element name="recipient">
       <dbindex name="email">
         <keyfield xpath="@email"/> 
         <keyfield xpath="location/@city"/> 
       </dbindex>
   
       <attribute name="email" type="string" length="80" label="Email" desc="E-mail address of recipient"/>
       <element name="location" label="Location">
         <attribute name="city" type="string" length="50" label="City" userEnum="city"/>
       </element>
     </element>
   </srcSchema>
   ```

* Hinzufügen eines eindeutigen Indexes zum Feld &quot;id&quot;-Name:

   ```
   <srcSchema name="recipient" namespace="cus">
     <element name="recipient">
       <dbindex name="id" unique="true">
         <keyfield xpath="@id"/> 
       </dbindex>
   
       <dbindex name="email">
         <keyfield xpath="@email"/> 
       </dbindex>
   
       <attribute name="id" type="long" label="Identifier"/>
       <attribute name="email" type="string" length="80" label="Email" desc="E-mail address of recipient"/>
     </element>
   </srcSchema>
   ```

## Verwaltung von Schlüsseln {#management-of-keys}

Eine Tabelle muss über mindestens einen Schlüssel zur Identifizierung eines Datensatzes in der Tabelle verfügen.

Ein Schlüssel wird aus dem Hauptelement des Datenschemas deklariert.

```
<key name="name_of_key">
  <keyfield xpath="xpath_of_field1"/>
  <keyfield xpath="xpath_of_field2"/>
  ...
</key>
```

Schlüssel beachten die folgenden Regeln:

* Ein Schlüssel kann auf ein oder mehrere Felder in der Tabelle verweisen.
* Ein Schlüssel wird als &quot;primär&quot;(oder &quot;Priorität&quot;) bezeichnet, wenn er der erste im auszufüllenden Schema ist oder wenn er das **interne** Attribut mit dem Wert &quot;true&quot;enthält.
* Für jede Schlüsseldefinition wird implizit ein eindeutiger Index deklariert. Die Erstellung eines Indexes auf dem Schlüssel kann verhindert werden, indem das Attribut **noDbIndex** mit dem Wert &quot;true&quot;hinzugefügt wird.

>[!NOTE]
>
>Standardmäßig sind Schlüssel die Elemente, die nach der Definition von Indizes aus dem Hauptelement des Schemas deklariert wurden.

>[!NOTE]
>
>Schlüssel werden bei der Tabellenzuordnung (Standard oder FDA) erstellt, Adobe Campaign findet eindeutige Indizes.

**Beispiel**:

* Hinzufügen eines Schlüssels zur E-Mail-Adresse und zum Ort:

   ```
   <srcSchema name="recipient" namespace="cus">
     <element name="recipient">
       <key name="email">
         <keyfield xpath="@email"/> 
         <keyfield xpath="location/@city"/> 
       </key>
   
       <attribute name="email" type="string" length="80" label="Email" desc="E-mail address of recipient"/>
       <element name="location" label="Location">
         <attribute name="city" type="string" length="50" label="City" userEnum="city"/>
       </element>
     </element>
   </srcSchema>
   ```

   Das erstellte Schema:

   ```
   <schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">  
     <element name="recipient" sqltable="CusRecipient">    
      <dbindex name="email" unique="true">      
        <keyfield xpath="@email"/>      
        <keyfield xpath="location/@city"/>    
      </dbindex>    
   
      <key name="email">      
       <keyfield xpath="@email"/>      
       <keyfield xpath="location/@city"/>    
      </key>    
   
      <attribute desc="E-mail address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>    
      <element label="Location" name="location">      
        <attribute label="City" length="50" name="city" sqlname="sCity" type="string" userEnum="city"/>    
      </element>  
     </element>
   </schema>
   ```

* Hinzufügen eines primären oder internen Schlüssels zum Namensfeld &quot;id&quot;:

   ```
   <srcSchema name="recipient" namespace="cus">
     <element name="recipient">
       <key name="id" internal="true">
         <keyfield xpath="@id"/> 
       </key>
   
       <key name="email" noDbIndex="true">
         <keyfield xpath="@email"/> 
       </key>
   
       <attribute name="id" type="long" label="Identifier"/>
       <attribute name="email" type="string" length="80" label="Email" desc="E-mail address of recipient"/>
     </element>
   </srcSchema>
   ```

   Das erstellte Schema:

   ```
   <schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">  
     <element name="recipient" sqltable="CusRecipient">    
       <key name="email">      
         <keyfield xpath="@email"/>    
       </key>    
   
       <dbindex name="id" unique="true">      
         <keyfield xpath="@id"/>    
       </dbindex>    
   
       <key internal="true" name="id">      
        <keyfield xpath="@id"/>    
       </key>    
   
       <attribute label="Identifier" name="id" sqlname="iRecipientId" type="long"/>    
       <attribute desc="E-mail address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>  
     </element>
   </schema>
   ```

### Auto-Inkrementalschlüssel {#auto-incremental-key}

Der Hauptschlüssel der meisten Adobe Campaign-Tabellen ist eine 32-Bit-Ganzzahl, die automatisch von der Datenbank-Engine generiert wird. Die Berechnung des Schlüsselwerts hängt von einer Sequenz ab (standardmäßig die SQL-Funktion **XtkNewId** ), die eine eindeutige Zahl in der gesamten Datenbank generiert. Der Inhalt des Schlüssels wird beim Einfügen des Datensatzes automatisch eingegeben.

Der Vorteil eines inkrementellen Schlüssels besteht darin, dass er einen nicht-modifizierbaren technischen Schlüssel für die Verbindungen zwischen Tabellen bereitstellt. Darüber hinaus belegt dieser Schlüssel nicht viel Arbeitsspeicher, da er eine Double-Byte-Ganzzahl verwendet.

Sie können im Quellschema den Namen der Sequenz angeben, die mit dem **pkSequence** -Attribut verwendet werden soll. Wenn dieses Attribut nicht im Quellschema angegeben ist, wird die **XtkNewId** -Standardsequenz verwendet. Die Anwendung verwendet dedizierte Sequenzen für die **nms:wideLog** - und **nms:trackingLog** -Schemata (**NmsBroadLogId** bzw. **NmsTrackingLogId** ), da diese Tabellen die meisten Datensätze enthalten.

Ab ACC 18.10 ist **XtkNewId** nicht mehr der Standardwert für die Sequenz in den vordefinierten Schemata. Sie können nun ein Schema erstellen oder ein vorhandenes Schema mit einer dedizierten Sequenz erweitern.

>[!CAUTION]
>
>Beim Anlegen eines neuen Schemas oder bei einer Schema-Erweiterung müssen Sie für das gesamte Schema den gleichen Wert für die Primärschlüsselfolge (@pkSequence) beibehalten.

>[!NOTE]
>
>Eine Sequenz, die in einem Adobe Campaign-Schema referenziert wird (z. B.**NmsTrackingLogId** ), muss mit einer SQL-Funktion verknüpft sein, die die Anzahl der IDs in den Parametern zurückgibt, durch Kommas getrennt. Diese Funktion muss ******GetNewXXXIds** heißen, wobei **XXX** der Name der Sequenz ist (z. B.**GetNewNmsTrackingLogIds** ). Zeigen Sie die **Dateien &quot;postgres-nms.sql**&quot;, &quot; **mssql-nms.sql** &quot;oder &quot; **oracle-nms.sql** &quot;an, die mit der Anwendung im Ordner &quot; **datakit/nms/eng/sql/** &quot;bereitgestellt wurden, um das Beispiel einer &quot;NmsTrackingLogId&quot;-Sequenzerstellung für jede Datenbank-Engine wiederherzustellen.

Um einen eindeutigen Schlüssel zu deklarieren, füllen Sie das **Attribut autopk** (mit dem Wert &quot;true&quot;) im Hauptelement des Datenschemas aus.

**Beispiel**:

Deklarieren eines inkrementellen Schlüssels im Quellschema:

```
<srcSchema name="recipient" namespace="cus">
  <element name="recipient" autopk="true">
  ...
  </element>
</srcSchema>
```

Das erstellte Schema:

```
<schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">  
  <element name="recipient" autopk="true" pkSequence="XtkNewId" sqltable="CusRecipient"> 
    <dbindex name="id" unique="true">
      <keyfield xpath="@id"/>
    </dbindex>

    <key internal="true" name="id">
      <keyfield xpath="@id"/>
    </key>

    <attribute desc="Internal primary key" label="Primary key" name="id" sqlname="iRecipientId" type="long"/>
  </element>
</schema>
```

Zusätzlich zur Definition des Schlüssels und seines Indexes wurde dem erweiterten Schema ein numerisches Feld namens &quot;id&quot;hinzugefügt, um den automatisch generierten primären Schlüssel zu enthalten.

>[!CAUTION]
>
>Ein Datensatz mit einem Primärschlüssel auf 0 wird bei der Tabellenerstellung automatisch eingefügt. Dieser Datensatz wird verwendet, um äußere Verbindungen zu vermeiden, die bei Volumentabellen nicht wirksam sind. Standardmäßig werden alle Fremdschlüssel mit dem Wert 0 initialisiert, sodass ein Ergebnis immer bei der Verknüpfung zurückgegeben werden kann, wenn das Datenelement nicht gefüllt wird.

## Links: Verhältnis zwischen Tabellen {#links--relation-between-tables}

Eine Verknüpfung beschreibt die Verbindung zwischen einer Tabelle und einer anderen.

Die verschiedenen Vereinigungen (auch &quot;Kardinalitäten&quot; genannt) sind:

* Kardinalität 1-1: ein Vorkommen der Ausgangstabelle kann maximal ein entsprechendes Vorkommen der Zieltabelle aufweisen.
* Kardinalität 1-N: Ein Vorkommen der Ausgangstabelle kann mehrere entsprechende Vorkommen der Zieltabelle aufweisen, aber ein Vorkommen der Zieltabelle kann maximal ein entsprechendes Vorkommen der Ausgangstabelle aufweisen.
* Kardinalität N-N: Ein Vorkommen der Quelltabelle kann mehrere entsprechende Vorkommen der Zieltabelle aufweisen und umgekehrt.

In der Oberfläche können Sie die verschiedenen Arten von Beziehungen leicht durch ihre Symbole unterscheiden.

Für die Verknüpfung mit einer Kampagnentabelle/Datenbank:

* ![](assets/join_with_campaign11.png) : Kardinalität 1-1. Beispiel: zwischen einem Empfänger und einer aktuellen Bestellung. Ein Empfänger kann jeweils nur mit einem Vorkommen der aktuellen Bestelltabelle in Beziehung gesetzt werden.
* ![](assets/externaljoin11.png) : Kardinalität 1-1, externe Verbindung. Zum Beispiel zwischen einem Empfänger und seinem Land. Ein Empfänger kann nur mit einem Vorkommen des Tabellenlandes verbunden sein. Der Inhalt der Ländertabelle wird nicht gespeichert.
* ![](assets/join_with_campaign1n.png) : Kardinalität 1-N. Beispielsweise zwischen einem Empfänger und der Abonnementtabelle. Ein Empfänger kann mit mehreren Vorfällen in der Abonnementtabelle in Zusammenhang stehen.

Für Verbindungsbeziehungen mit Federated Database Access:

* ![](assets/join_fda_11.png) : Kardinalität 1-1
* ![](assets/join_fda_1m.png) : Kardinalität 1-N

For more information on FDA tables, refer to [Accessing an external database](../../platform/using/accessing-an-external-database.md).

Ein Link muss im Schema deklariert werden, das den Fremdschlüssel der Tabelle enthält, die über das Hauptelement verknüpft ist:

```
<element name="name_of_link" type="link" target="key_of_destination_schema">
  <join xpath-dst="xpath_of_field1_destination_table" xpath-src="xpath_of_field1_source_table"/>
  <join xpath-dst="xpath_of_field2_destination_table" xpath-src="xpath_of_field2_source_table"/>
  ...
</element>
```

Links folgen den folgenden Regeln:

* Die Definition eines Links wird in einen **Link**-Typ **`<element>`** mit folgenden Attributen eingegeben:

   * **name**: Name des Links aus der Quelltabelle,
   * **target**: Name des Zielschemas,
   * **label**: Bezeichnung des Links,
   * **revLink** (optional): Name des Rückwärtslinks vom Zielschema (standardmäßig automatisch abgezogen),
   * **Integrität** (optional): Referenzintegrität des Vorkommens der Quelltabelle zum Vorkommen der Zieltabelle. Mögliche Werte sind:

      * **definieren**: das Quellvorkommen gelöscht werden kann, wenn es nicht mehr durch ein Zielvorkommen referenziert wird,
      * **normal**: Wenn Sie das Quellvorkommen löschen, werden die Schlüssel des Links zum Zielvorkommen (Standardmodus) initialisiert. Bei diesem Integritätstyp werden alle Fremdschlüssel initialisiert,
      * **eigene**: Das Löschen des Quellvorkommens führt zum Löschen des Zielvorkommens,
      * **Copyright**: die gleichen wie **eigene** (im Falle der Löschung) oder die Duplizierung der Vorkommnisse (im Falle der Duplizierung),
      * **neutral**: tut nichts.
   * **revIntegrity** (optional): Integrität des Zielschemas (optional, standardmäßig &quot;normal&quot;),
   * **revKardinalität** (optional): mit dem Wert &quot;single&quot;wird die Kardinalität mit dem Typ 1-1 ausgefüllt (standardmäßig 1-N).
   * **externalJoin** (optional): erzwingt die äußere Verbindung
   * **revExternalJoin** (optional): erzwingt die äußere Verbindung am Rückwärtslink


* Ein Link verweist auf ein oder mehrere Felder aus der Quelltabelle zur Zieltabelle. Die Felder, aus denen die Verknüpfung ( `<join>` Element) besteht, müssen nicht ausgefüllt werden, da sie standardmäßig mit dem internen Schlüssel des Zielschemas abgezogen werden.
* Dem Fremdschlüssel des Links im erweiterten Schema wird automatisch ein Index hinzugefügt.
* Eine Verknüpfung besteht aus zwei Halblinks, wobei die erste aus dem Quellschema deklariert und die zweite automatisch im erweiterten Schema des Zielschemas erstellt wird.
* Ein Join kann ein Außenverbindung sein, wenn das Attribut **externalJoin** mit dem Wert &quot;true&quot;hinzugefügt wird (unterstützt in PostgreSQL).

>[!NOTE]
>
>Standardmäßig sind Links die Elemente, die am Ende des Schemas deklariert werden.

### Example 1 {#example-1}

1-N Bezug zur Schematabelle &quot;cus:company&quot;:

```
<srcSchema name="recipient" namespace="cus">
  <element name="recipient">
    ...
    <element label="Company" name="company" revIntegrity="define" revLabel="Contact" target="cus:company" type="link"/>
  </element>
</srcSchema>
```

Das erstellte Schema:

```
<schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">  
  <element name="recipient" sqltable="CusRecipient"> 
    <dbindex name="companyId">      
      <keyfield xpath="@company-id"/>    
    </dbindex>
    ...
    <element label="Company" name="company" revLink="recipient" target="cus:company" type="link">      
      <join xpath-dst="@id" xpath-src="@company-id"/>    
    </element>    
    <attribute advanced="true" label="Foreign key of 'Company' link (field 'id')" name="company-id" sqlname="iCompanyId" type="long"/>
  </element>
</schema>
```

Die Linkdefinition wird durch die Felder, aus denen die Verbindung besteht, ergänzt, d. h. durch den primären Schlüssel mit XPath (&quot;@id&quot;) im Zielschema und den Fremdschlüssel mit dem XPath (&quot;@company-id&quot;) im Schema.

Der Fremdschlüssel wird automatisch in einem Element hinzugefügt, das dieselben Eigenschaften wie das zugehörige Feld in der Zieltabelle verwendet, mit der folgenden Benennungskonvention: Name des Zielschemas gefolgt vom Namen des zugehörigen Felds (&quot;company-id&quot;in unserem Beispiel).

Erweitertes Schema des Ziels (&quot;cus:company&quot;):

```
<schema mappingType="sql" name="company" namespace="cus" xtkschema="xtk:schema">  
  <element name="company" sqltable="CusCompany" autopk="true"> 
    <dbindex name="id" unique="true">     
      <keyfield xpath="@id"/>    
    </dbindex>   
    <key internal="true" name="id">      
      <keyfield xpath="@id"/>    
    </key>
    ...
    <attribute desc="Internal primary key" label="Primary key" name="id" sqlname="iCompanyId" type="long"/>
    ...
    <element belongsTo="cus:recipient" integrity="define" label="Contact" name="recipient" revLink="company" target="nms:recipient" type="link" unbound="true">      
      <join xpath-dst="@company-id" xpath-src="@id"/>    
    </element>
  </element>
</schema>
```

Eine umgekehrte Verknüpfung zur Tabelle &quot;cus:empfänger&quot;wurde mit folgenden Parametern hinzugefügt:

* **name**: automatisch vom Namen des Quellschemas abgezogen (kann mit dem Attribut &quot;revLink&quot;in der Linkdefinition im Quellschema erzwungen werden)
* **revLink**: Name des umgekehrten Links
* **target**: Schlüssel des verknüpften Schemas (&quot;cus:empfänger&quot;-Schema)
* **ungebunden**: Der Link wird als Collection-Element für eine 1-N Kardinalität deklariert (standardmäßig)
* **Integrität**: &quot;Definieren&quot;standardmäßig (kann mit dem Attribut &quot;revIntegrity&quot;in der Linkdefinition im Quellschema erzwungen werden).

### Example 2 {#example-2}

In diesem Beispiel werden wir einen Link zur Schematabelle &quot;nms:address&quot;deklarieren. Der Join ist ein externer Join und wird explizit mit der E-Mail-Adresse des Empfängers und dem Feld &quot;@address&quot;der verknüpften Tabelle (&quot;nms:address&quot;) ausgefüllt.

```
<srcSchema name="recipient" namespace="cus">
  <element name="recipient"> 
    ...
    <element integrity="neutral" label="Info about email" name="emailInfo" revIntegrity="neutral" revLink="recipient" target="nms:address" type="link" externalJoin="true">      
      <join xpath-dst="@address" xpath-src="@email"/>
    </element>
  </element>
</srcSchema>
```

### Example 3 {#example-3}

1-1 Bezug zur Schematabelle &quot;cus:extension&quot;:

```
<element integrity="own" label="Extension" name="extension" revCardinality="single" revLink="recipient" target="cus:extension" type="link"/>
```

### Example 4 {#example-4}

Link zu einem Ordner (&quot;xtk:folder&quot;-Schema):

```
<element default="DefaultFolder('nmsFolder')" label="Folder" name="folder" revDesc="Recipients in the folder" revIntegrity="own" revLabel="Recipients" target="xtk:folder" type="link"/>
```

Der Standardwert gibt den Bezeichner der ersten zulässigen Parametertypdatei zurück, die in der Funktion &quot;DefaultFolder(&#39;nmsFolder&#39;)&quot;eingegeben wurde.

### Example 5 {#example-5}

In diesem Beispiel möchten wir einen Schlüssel für einen Link (&quot;Unternehmen&quot; zu &quot;cus:Firma&quot;-Schema) mit dem **xlink** -Attribut und einem Feld der Tabelle (&quot;E-Mail&quot;) erstellen:

```
<srcSchema name="recipient" namespace="cus">
  <element name="recipient">
    <key name="companyEmail"> 
      <keyfield xpath="@email"/>
      <keyfield xlink="company"/>
    </key>
    
    <attribute name="email" type="string" length="80" label="Email" desc="Recipient email"/>
    <element label="Company" name="company" revIntegrity="define" revLabel="Contact" target="cus:company" type="link"/>
  </element>
</srcSchema>
```

Das erstellte Schema:

```
<schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">  
  <element name="recipient" sqltable="CusRecipient"> 
    <dbindex name="companyId">      
      <keyfield xpath="@company-id"/>    
    </dbindex>

    <dbindex name="companyEmail" unique="true">
      <keyfield xpath="@email"/>      
      <keyfield xpath="@company-id"/>    
    </dbindex>    

    <key name="companyEmail">      
      <keyfield xpath="@email"/>      
      <keyfield xpath="@company-id"/>    
    </key>

    <attribute desc="E-mail address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>
    <element label="Company" name="company" revLink="recipient" target="sfa:company" type="link">      
      <join xpath-dst="@id" xpath-src="@company-id"/>    
    </element>    
    <attribute advanced="true" label="Foreign key of link 'Company' (field 'id')" name="company-id" sqlname="iCompanyId" type="long"/>
  </element>
</schema>
```

Die Definition des Namensschlüssels &quot;companyEmail&quot;wurde um den Fremdschlüssel des Links &quot;company&quot;erweitert. Dieser Schlüssel generiert einen eindeutigen Index für beide Felder.
