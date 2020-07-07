---
title: Datenbank-Mapping
seo-title: Datenbank-Mapping
description: Datenbank-Mapping
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
source-git-commit: 656b867686dd90f3e921c2adb5e5676fec184803
workflow-type: tm+mt
source-wordcount: '1976'
ht-degree: 1%

---


# Datenbank-Mapping{#database-mapping}

Die SQL-Zuordnung unseres Beispiels Schema enthält das folgende XML-Dokument:

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

Dies führt uns zu einem anderen Dokument, das automatisch aus dem Quellcode-Schema generiert wird, das einfach als Schema bezeichnet wird. Dieses Schema wird von der Adobe Campaign-Anwendung verwendet.

Die SQL-Namen werden automatisch anhand des Elementnamens und des Elementtyps bestimmt.

Die SQL-Benennungsregeln lauten wie folgt:

* Tabelle: Verkettung des Schema-Namensraums und -Namens

   In unserem Beispiel wird der Tabellenname über das Hauptelement des Schemas im Attribut &quot; **sqltable** &quot;eingegeben:

   ```
   <element name="recipient" sqltable="CusRecipient">
   ```

* Feld: Name des Elements, dem ein Präfix vorangestellt wird, der nach Typ (&#39;i&#39; für Ganzzahl, &#39;d&#39; für Dublette, &#39;s&#39; für Zeichenfolge, &#39;ts&#39; für Datumsangaben usw.) definiert ist

   Der Feldname wird über das Attribut **sqlname** für jede Eingabe **`<attribute>`** und **`<element>`**:

   ```
   <attribute desc="E-mail address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/> 
   ```

>[!NOTE]
>
>SQL-Namen können aus dem Quellcode-Schema überladen werden. Füllen Sie dazu die Attribute &quot;sqltable&quot;oder &quot;sqlname&quot;für das betreffende Element aus.

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

Standardmäßig werden alle typisierten **`<attribute>`** und **`<element>`** eingegebenen Elemente einem SQL-Feld der Datentabelle zugeordnet. Sie können dieses Feld jedoch in XML anstatt in SQL referenzieren. Das bedeutet, dass die Daten in einem Memofeld (&quot;mData&quot;) der Tabelle gespeichert werden, das die Werte aller XML-Felder enthält. Die Datenspeicherung dieser Daten ist ein XML-Dokument, das die Schema-Struktur einhält.

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

   Mit dem &quot;html&quot;-Typ können Sie HTML-Inhalte in einem CDATA-Tag speichern und eine spezielle HTML-Bearbeitungsprüfung in der Adobe Campaign-Client-Oberfläche anzeigen.

Mithilfe von XML-Feldern können Sie Felder hinzufügen, ohne die physische Struktur der Datenbank ändern zu müssen. Ein weiterer Vorteil besteht darin, dass Sie weniger Ressourcen verwenden (Größe den SQL-Feldern zugeordnet, Anzahl der Felder pro Tabelle usw.).

Der Hauptnachteil ist, dass es unmöglich ist, ein XML-Feld zu indizieren oder zu filtern.

## Indexierte Felder {#indexed-fields}

Mithilfe von Indizes können Sie die Leistung der in der Anwendung verwendeten SQL-Abfragen optimieren.

Ein Index wird aus dem Hauptelement des data-Schemas deklariert.

```
<dbindex name="name_of_index" unique="true/false">
  <keyfield xpath="xpath_of_field1"/>
  <keyfield xpath="xpath_of_field2"/>
  ...
</key>
```

Indizes folgen den folgenden Regeln:

* Ein Index kann auf ein oder mehrere Felder in der Tabelle verweisen.
* Ein Index kann in allen Feldern eindeutig sein (um Duplikat zu vermeiden), wenn das **Attribut unique** den Wert &quot;true&quot;enthält.
* Der SQL-Name des Indexes wird anhand des SQL-Namens der Tabelle und des Indexnamens bestimmt.

>[!NOTE]
>
>Standardmäßig sind Indizes die ersten Elemente, die aus dem Hauptelement des Schemas deklariert wurden.

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

Ein Schlüssel wird aus dem Hauptelement des data-Schemas deklariert.

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
>Standardmäßig sind Schlüssel die Elemente, die aus dem Hauptelement des Schemas deklariert wurden, nachdem Indizes definiert wurden.

>[!NOTE]
>
>Tasten werden während der Tabellenzuordnung (Standard oder FDA) erstellt, Adobe Campaign findet eindeutige Indizes.

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

   Das generierte Schema:

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

   Das generierte Schema:

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

Der Vorteil eines inkrementellen Schlüssels besteht darin, dass er einen nicht-modifizierbaren technischen Schlüssel für die Verbindungen zwischen Tabellen bereitstellt. Darüber hinaus belegt dieser Schlüssel nicht viel Arbeitsspeicher, da er eine Dublette-Byte-Ganzzahl verwendet.

Sie können im Quellattribut den Namen der Sequenz angeben, die mit dem **pkSequence** -Attribut verwendet werden soll. Wenn dieses Attribut nicht im source-Schema angegeben ist, wird die **XtkNewId** -Standardsequenz verwendet. Die Anwendung verwendet dedizierte Sequenzen für die **nms:wideLog** - und **nms:trackingLog** -Schema (**NmsBroadLogId** bzw. **NmsTrackingLogId** ), da diese Tabellen die meisten Datensätze enthalten.

Ab ACC 18.10 ist **XtkNewId** nicht mehr der Standardwert für die Sequenz in den vordefinierten Schemas. Sie können jetzt Schema erstellen oder bestehende Schemas mit einer eigenen Sequenz erweitern.

>[!IMPORTANT]
>
>Beim Anlegen eines neuen Schemas oder bei einer Schema-Erweiterung müssen Sie für das gesamte Schema den gleichen Wert für die Primärschlüsselfolge (@pkSequence) beibehalten.

>[!NOTE]
>
>Eine Sequenz, auf die in einem Adobe Campaign-Schema verwiesen wird (z. B.**NmsTrackingLogId** ), muss mit einer SQL-Funktion verknüpft sein, die die Anzahl der IDs in den Parametern zurückgibt (durch Kommas getrennt). Diese Funktion muss ******GetNewXXXIds** heißen, wobei **XXX** der Name der Sequenz ist (z. B.**GetNewNmsTrackingLogIds** ). Ansicht der **Dateien &quot;postgres-nms.sql**&quot;, &quot; **mssql-nms.sql** &quot;oder &quot; **oracle-nms.sql** &quot;, die mit der Anwendung im Ordner &quot; **datakit/nms/eng/sql/** &quot;bereitgestellt werden, um das Beispiel einer &quot;NmsTrackingLogId&quot;-Sequenzerstellung für jede Datenbank-Engine wiederherzustellen.

Um einen eindeutigen Schlüssel zu deklarieren, füllen Sie das **autopk** -Attribut (mit dem Wert &quot;true&quot;) im Hauptelement des data-Schemas aus.

**Beispiel**:

Deklarieren eines inkrementellen Schlüssels im Quell-Schema:

```
<srcSchema name="recipient" namespace="cus">
  <element name="recipient" autopk="true">
  ...
  </element>
</srcSchema>
```

Das generierte Schema:

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

Zusätzlich zur Definition des Schlüssels und seines Indexes wurde dem erweiterten Schema ein numerisches Feld namens &quot;id&quot;hinzugefügt, um den automatisch generierten Primärschlüssel zu enthalten.

>[!IMPORTANT]
>
>Ein Datensatz mit einem Primärschlüssel auf 0 wird bei der Tabellenerstellung automatisch eingefügt. Dieser Datensatz wird verwendet, um äußere Verbindungen zu vermeiden, die bei Volumentabellen nicht wirksam sind. Standardmäßig werden alle Fremdschlüssel mit dem Wert 0 initialisiert, sodass ein Ergebnis immer bei der Verknüpfung zurückgegeben werden kann, wenn das Datenelement nicht gefüllt wird.

## Links: Verhältnis zwischen Tabellen {#links--relation-between-tables}

Eine Verknüpfung beschreibt die Verbindung zwischen einer Tabelle und einer anderen.

Die verschiedenen Vereinigungen (auch &quot;Kardinalitäten&quot; genannt) sind:

* Kardinalität 1-1: Ein Vorkommen der Quelltabelle kann maximal ein entsprechendes Vorkommen der Zielgruppe aufweisen.
* Kardinalität 1-N: Ein Vorkommen der Quelltabelle kann mehrere entsprechende Vorkommen der Tabelle &quot;Zielgruppe&quot;aufweisen, aber ein Vorkommen der Tabelle &quot;Zielgruppe&quot;kann höchstens ein entsprechendes Vorkommen der Quelltabelle aufweisen.
* Kardinalität N-N: Ein Vorkommen der Quelltabelle kann mehrere entsprechende Vorkommen der Tabelle &quot;Zielgruppe&quot;aufweisen und umgekehrt.

In der Oberfläche können Sie die verschiedenen Arten von Beziehungen leicht durch ihre Symbole unterscheiden.

Verknüpfen von Beziehungen mit einer Kampagne:

* ![](assets/join_with_campaign11.png) : Kardinalität 1-1. Beispielsweise zwischen einem Empfänger und einer aktuellen Reihenfolge. Ein Empfänger kann jeweils nur mit einem Vorkommen der aktuellen Bestelltabelle verknüpft werden.
* ![](assets/externaljoin11.png) : Kardinalität 1-1, externe Verbindung. Zum Beispiel zwischen einem Empfänger und seinem Land. Ein Empfänger kann nur mit einem Vorkommen des Tabellenlandes verbunden sein. Der Inhalt der Ländertabelle wird nicht gespeichert.
* ![](assets/join_with_campaign1n.png) : Kardinalität 1-N. Beispielsweise zwischen einem Empfänger und der Tabelle &quot;Abonnement&quot;. Ein Empfänger kann mit mehreren Vorfällen in der Abonnement-Tabelle in Zusammenhang stehen.

Für Verbindungsbeziehungen mit Federated Database Access:

* ![](assets/join_fda_11.png) : Kardinalität 1-1
* ![](assets/join_fda_1m.png) : Kardinalität 1-N

For more information on FDA tables, refer to [Accessing an external database](../../platform/using/about-fda.md).

In dem Schema, das den Fremdschlüssel der Tabelle enthält, muss über das Hauptelement ein Link angegeben werden:

```
<element name="name_of_link" type="link" target="key_of_destination_schema">
  <join xpath-dst="xpath_of_field1_destination_table" xpath-src="xpath_of_field1_source_table"/>
  <join xpath-dst="xpath_of_field2_destination_table" xpath-src="xpath_of_field2_source_table"/>
  ...
</element>
```

Links folgen den folgenden Regeln:

* Die Definition eines Links wird in einen **Link**-Typ **`<element>`** mit den folgenden Attributen eingegeben:

   * **name**: Name des Links aus der Quelltabelle,
   * **Zielgruppe**: Name des Schemas der Zielgruppe,
   * **label**: Bezeichnung des Links,
   * **revLink** (optional): Name des Rückwärtslinks aus dem Schema Zielgruppe (standardmäßig automatisch abgezogen),
   * **Integrität** (optional): Referenzintegrität des Vorkommens der Quelltabelle zum Vorkommen der Zielgruppe-Tabelle. Mögliche Werte sind:

      * **definieren**: das Quellvorkommen gelöscht werden kann, wenn es nicht mehr durch ein Vorkommen einer Zielgruppe referenziert wird,
      * **normal**: Wenn Sie das Quellvorkommen löschen, werden die Schlüssel des Links zum Vorkommen der Zielgruppe (Standardmodus) initialisiert. Bei diesem Integritätstyp werden alle Fremdschlüssel initialisiert,
      * **eigene**: Das Löschen des Quellvorkommens führt zum Löschen des Vorkommens der Zielgruppe,
      * **Copyright**: dieselben wie **eigene** (im Falle der Löschung) oder Duplikat die Vorkommnisse (im Falle der Vervielfältigung),
      * **neutral**: tut nichts.
   * **revIntegrity** (optional): Integrität im Schema Zielgruppe (optional, standardmäßig &quot;normal&quot;),
   * **revKardinalität** (optional): mit dem Wert &quot;single&quot;wird die Kardinalität mit dem Typ 1-1 ausgefüllt (standardmäßig 1-N).
   * **externalJoin** (optional): erzwingt die äußere Verbindung
   * **revExternalJoin** (optional): erzwingt die äußere Verbindung am Rückwärtslink


* Ein Link verweist auf ein oder mehrere Felder aus der Quelltabelle zur Zieltabelle. Die Felder, aus denen die Verknüpfung ( `<join>` Element) besteht, müssen nicht ausgefüllt werden, da sie standardmäßig mit dem internen Schlüssel des Zielgruppe-Schemas abgezogen werden.
* Dem Fremdschlüssel des Links im erweiterten Schema wird automatisch ein Index hinzugefügt.
* Ein Link besteht aus zwei Halblinks, wobei der erste aus dem Quellcode-Schema deklariert und der zweite automatisch im erweiterten Schema des Zielgruppe-Schemas erstellt wird.
* Ein Join kann ein Außenverbindung sein, wenn das Attribut **externalJoin** mit dem Wert &quot;true&quot;hinzugefügt wird (unterstützt in PostgreSQL).

>[!NOTE]
>
>Standardmäßig sind Links die am Ende des Schemas deklarierten Elemente.

### Example 1 {#example-1}

1-N Bezug zur Tabelle &quot;cus:Firma&quot;-Schema:

```
<srcSchema name="recipient" namespace="cus">
  <element name="recipient">
    ...
    <element label="Company" name="company" revIntegrity="define" revLabel="Contact" target="cus:company" type="link"/>
  </element>
</srcSchema>
```

Das generierte Schema:

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

Die Linkdefinition wird ergänzt durch die Felder, aus denen die Verknüpfung besteht, d. h. der Primärschlüssel mit XPath (&quot;@id&quot;) im Ziel-Schema und der Fremdschlüssel mit XPath (&quot;@Firma-id&quot;) im Schema.

Der Fremdschlüssel wird automatisch in einem Element hinzugefügt, das dieselben Eigenschaften wie das zugehörige Feld in der Zieltabelle verwendet, mit der folgenden Benennungskonvention: Name des Schemas Zielgruppe gefolgt vom Namen des zugehörigen Felds (&quot;Firma-ID&quot;in unserem Beispiel).

Erweitertes Schema der Zielgruppe (&quot;cus:Firma&quot;):

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

Ein umgekehrter Link zur Tabelle &quot;cus:Empfänger&quot;wurde mit folgenden Parametern hinzugefügt:

* **name**: automatisch vom Namen des Quell-Schemas abgezogen (kann mit dem Attribut &quot;revLink&quot;in der Linkdefinition im Quell-Schema erzwungen werden)
* **revLink**: Name des umgekehrten Links
* **Zielgruppe**: Schlüssel des verknüpften Schemas (&quot;cus:Empfänger&quot;-Schema)
* **ungebunden**: Der Link wird als Collection-Element für eine 1-N Kardinalität deklariert (standardmäßig)
* **Integrität**: &quot;Definieren&quot;standardmäßig (kann mit dem Attribut &quot;revIntegrity&quot;in der Linkdefinition im Quellcode-Schema erzwungen werden).

### Example 2 {#example-2}

In diesem Beispiel werden wir einen Link zum Schema &quot;nms:address&quot;angeben. Der Join ist ein externer Join und wird explizit mit der E-Mail-Adresse des Empfängers und dem Feld &quot;@address&quot;der verknüpften Tabelle (&quot;nms:address&quot;) ausgefüllt.

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

1-1 Bezug zur Tabelle mit dem Schema &quot;cus:extension&quot;:

```
<element integrity="own" label="Extension" name="extension" revCardinality="single" revLink="recipient" target="cus:extension" type="link"/>
```

### Example 4 {#example-4}

Verknüpfen mit einem Ordner (&quot;xtk:folder&quot;-Schema):

```
<element default="DefaultFolder('nmsFolder')" label="Folder" name="folder" revDesc="Recipients in the folder" revIntegrity="own" revLabel="Recipients" target="xtk:folder" type="link"/>
```

Der Standardwert gibt den Bezeichner der ersten zulässigen Parametertypdatei zurück, die in der Funktion &quot;DefaultFolder(&#39;nmsFolder&#39;)&quot;eingegeben wurde.

### Example 5 {#example-5}

In diesem Beispiel möchten wir einen Schlüssel für einen Link (&quot;Firma&quot; zu &quot;cus:Firma&quot;-Schema) mit dem **xlink** -Attribut und einem Feld der Tabelle (&quot;E-Mail&quot;) erstellen:

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

Das generierte Schema:

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

Die Definition des Namensschlüssels &quot;companyEmail&quot;wurde um den Fremdschlüssel des Links &quot;Firma&quot;erweitert. Dieser Schlüssel generiert einen eindeutigen Index für beide Felder.
