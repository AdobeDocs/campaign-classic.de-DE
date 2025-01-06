---
product: campaign
title: Schlüsselverwaltung in Datenschemata
description: Grundlegendes zur Schlüsselverwaltung in Datenschemata
feature: Configuration, Instance Settings
role: Data Engineer, Developer
exl-id: faf63c8f-9d10-43c1-a990-91361594af9f
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '619'
ht-degree: 30%

---

# Schlüsselverwaltung in Schemata {#management-of-keys}

Jede mit einem Datenschema verknüpfte Tabelle benötigt mindestens einen Schlüssel zur Identifizierung eines Eintrags in einer Tabelle.

Ein Schlüssel wird über das Hauptelement des Datenschemas deklariert.

```sql
<key name="name_of_key">
  <keyfield xpath="xpath_of_field1"/>
  <keyfield xpath="xpath_of_field2"/>
  ...
</key>
```

Ein Schlüssel wird als „Primärschlüssel“ bezeichnet, wenn er an erster Stelle im auszufüllenden Schema steht oder wenn er ein `internal`-Attribut enthält, das auf „true“ festgelegt ist.

Die folgenden Regeln gelten für Schlüssel:

* Ein Schlüssel kann auf ein oder mehrere Felder in der Tabelle verweisen
* Für jede Schlüsseldefinition wird implizit ein eindeutiger Index deklariert. Die Erstellung eines Index für den Schlüssel kann verhindert werden, indem das Attribut `noDbIndex` auf „true“ gesetzt wird.

>[!NOTE]
>
>* Standardmäßig sind Schlüssel die Elemente, die vom Hauptelement des Schemas deklariert werden, nachdem Indizes definiert wurden.
>
>* Schlüssel werden während der Tabellenzuordnung erstellt (Standard oder FDA). Adobe Campaign findet eindeutige Indizes.

**Beispiel**:

* Hinzufügen eines Schlüssels zur E-Mail-Adresse und zum Ort:

  ```sql
  <srcSchema name="recipient" namespace="cus">
    <element name="recipient">
      <key name="email">
        <keyfield xpath="@email"/> 
        <keyfield xpath="location/@city"/> 
      </key>
  
      <attribute name="email" type="string" length="80" label="Email" desc="Email address of recipient"/>
      <element name="location" label="Location">
        <attribute name="city" type="string" length="50" label="City" userEnum="city"/>
      </element>
    </element>
  </srcSchema>
  ```

  Das generierte Schema:

  ```sql
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
  
     <attribute desc="Email address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>    
     <element label="Location" name="location">      
       <attribute label="City" length="50" name="city" sqlname="sCity" type="string" userEnum="city"/>    
     </element>  
    </element>
  </schema>
  ```

* Hinzufügen eines primären oder internen Schlüssels zum Namensfeld &quot;id&quot;:

  ```sql
  <srcSchema name="recipient" namespace="cus">
    <element name="recipient">
      <key name="id" internal="true">
        <keyfield xpath="@id"/> 
      </key>
  
      <key name="email" noDbIndex="true">
        <keyfield xpath="@email"/> 
      </key>
  
      <attribute name="id" type="long" label="Identifier"/>
      <attribute name="email" type="string" length="80" label="Email" desc="Email address of recipient"/>
    </element>
  </srcSchema>
  ```

  Das generierte Schema:

  ```sql
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
      <attribute desc="Email address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>  
    </element>
  </schema>
  ```

## Automatisch inkrementeller Schlüssel {#auto-incremental-key}

Der Primärschlüssel der meisten Adobe Campaign-Tabellen ist eine 32-Bit-Ganzzahl, die automatisch von der Datenbank-Engine generiert wird. Die Berechnung des Schlüsselwerts hängt von einer Sequenz ab (standardmäßig die SQL-Funktion **XtkNewId**), die eine in der gesamten Datenbank eindeutige Zahl generiert. Der Inhalt des Schlüssels wird beim Einfügen des Datensatzes automatisch eingegeben.

Der Vorteil eines inkrementellen Schlüssels besteht darin, dass er einen nicht veränderbaren technischen Schlüssel für die Joins zwischen Tabellen bereitstellt. Darüber hinaus benötigt dieser Schlüssel nicht viel Speicher, da er eine Doppelbyte-Ganzzahl verwendet.

Sie können im Quellschema den Namen der mit dem Attribut **pkSequence** zu verwendenden Sequenz angeben. Wenn dieses Attribut nicht im Quellschema angegeben ist, wird die **XtkNewId** Standardsequenz verwendet. Die Anwendung verwendet dedizierte Sequenzen für die **nms:broadLog**- und **nms:trackingLog**-Schemas (**NmsBroadLogId** bzw. **NmsTrackingLogId**), da dies die Tabellen sind, die die meisten Einträge enthalten.

Ab ACC 18.10 **XtkNewId** nicht mehr der Standardwert für die Sequenz in den vordefinierten Schemata. Sie können jetzt ein Schema erstellen oder ein vorhandenes Schema mit einer dedizierten Sequenz erweitern.

>[!IMPORTANT]
>
>Beim Anlegen eines neuen Schemas oder bei einer Schema-Erweiterung müssen Sie für das gesamte Schema den gleichen Wert für die Primärschlüsselsequenz (@pkSequence) beibehalten.

Eine Sequenz, auf die in einem Adobe Campaign-Schema (**NmsTrackingLogId** verwiesen wird), muss mit einer SQL-Funktion verknüpft sein, die die Anzahl der IDs in den Parametern zurückgibt, getrennt durch Kommas. Diese Funktion muss als **GetNew** XXX **Ids** bezeichnet werden, wobei **XXX** der Name der Sequenz ist (z. B **GetNewNmsTrackingLogIds**). Sehen Sie sich die **postgres-nms.sql**, **mssql-nms.sql** oder **oracle-nms.sql** an, die mit der Anwendung im Verzeichnis **datakit/nms/eng/sql/** bereitgestellt werden, um das Beispiel einer Sequenzerstellung „NmsTrackingLogId“ für jede Datenbank-Engine abzurufen.

Um einen eindeutigen Schlüssel zu deklarieren, füllen **das Attribut &quot;**&quot; (mit dem Wert „true„) im Hauptelement des Datenschemas auf.

**Beispiel**:

Deklarieren eines inkrementellen Schlüssels im Quellschema:

```sql
<srcSchema name="recipient" namespace="cus">
  <element name="recipient" autopk="true">
  ...
  </element>
</srcSchema>
```

Generiertes Schema:

```sql
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

Zusätzlich zur Definition des Schlüssels und seines Index wurde dem erweiterten Schema ein numerisches Feld namens „id“ hinzugefügt, das den automatisch generierten Primärschlüssel enthält.

>[!IMPORTANT]
>
>Ein Datensatz mit einem auf 0 gesetzten Primärschlüssel wird bei der Erstellung der Tabelle automatisch eingefügt. Durch die Verwendung dieses Datensatzes werden äußere Joins vermieden, die sich bei Volumentabellen als nicht effektiv erweisen. Standardmäßig werden alle Fremdschlüssel mit dem Wert 0 initialisiert. Auf diese Weise kann beim Join immer ein Ergebnis zurückgegeben werden, wenn das Datenelement nicht ausgefüllt wird.


## Weitere Informationen

Weitere Informationen finden Sie unter den folgenden Links:

* [Erste Schritte mit Schemata](about-schema-reference.md)
* [Schemastruktur](schema-structure.md)
* [Datenbank-Mapping](database-mapping.md)
* [Verknüpfungs-Management](database-links.md)
* [Campaign-Datenmodell](about-data-model.md)
