---
product: campaign
title: Schlüsselverwaltung in Datenschemata
description: Schlüsselverwaltung in Datenschemata
feature: Configuration, Instance Settings
role: Data Engineer, Developer
badge-v7-only: label="v7" type="Informative" tooltip="Gilt nur für Campaign Classic v7"
exl-id: faf63c8f-9d10-43c1-a990-91361594af9f
source-git-commit: 46dcd80d5adc31a66b47c6d75e7914b0a686326b
workflow-type: tm+mt
source-wordcount: '625'
ht-degree: 23%

---

# Schlüsselverwaltung in Schemata {#management-of-keys}

Jede mit einem Datenschema verknüpfte Tabelle muss über mindestens einen Schlüssel zur Identifizierung eines Datensatzes in einer Tabelle verfügen.

Ein Schlüssel wird über das Hauptelement des Datenschemas deklariert.

```sql
<key name="name_of_key">
  <keyfield xpath="xpath_of_field1"/>
  <keyfield xpath="xpath_of_field2"/>
  ...
</key>
```

Ein Schlüssel wird als &quot;Primärschlüssel&quot;bezeichnet, wenn er der erste im Schema ist, der ausgefüllt werden soll, oder wenn er die Variable `internal` auf &quot;true&quot;gesetzt ist.

Die folgenden Regeln gelten für Schlüssel:

* Ein Schlüssel kann auf ein oder mehrere Felder in der Tabelle verweisen
* Für jede Schlüsseldefinition wird implizit ein eindeutiger Index deklariert. Die Erstellung eines Index für den Schlüssel kann durch Festlegen der `noDbIndex` auf &quot;true&quot;gesetzt.

>[!NOTE]
>
>* Standardmäßig sind Schlüssel die Elemente, die aus dem Hauptelement des Schemas deklariert werden, nachdem Indizes definiert wurden.
>
>* Schlüssel werden während der Tabellenzuordnung (Standard oder FDA) erstellt, Adobe Campaign findet eindeutige Indizes.

**Beispiel**:

* Hinzufügen eines Schlüssels zur E-Mail-Adresse und Stadt:

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

  Generiertes Schema:

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

  Generiertes Schema:

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

## Automatischer inkrementeller Schlüssel {#auto-incremental-key}

Der Primärschlüssel der meisten Adobe Campaign-Tabellen ist eine von der Datenbank-Engine automatisch generierte 32-Bit-Ganzzahl. Die Berechnung des Schlüsselwerts hängt von einer Sequenz ab (standardmäßig ist die **XtkNewId** SQL-Funktion) Generieren einer eindeutigen Zahl in der gesamten Datenbank. Der Inhalt des Schlüssels wird beim Einfügen des Datensatzes automatisch eingegeben.

Der Vorteil eines inkrementellen Schlüssels besteht darin, dass er einen nicht änderbaren technischen Schlüssel für die Joins zwischen Tabellen bereitstellt. Darüber hinaus belegt dieser Schlüssel nicht viel Speicher, da er eine Double-Byte-Ganzzahl verwendet.

Sie können im Quellschema den Namen der Sequenz angeben, die mit der **pkSequence** -Attribut. Wenn dieses Attribut nicht im Quellschema angegeben ist, wird die **XtkNewId** wird die Standardsequenz verwendet. Die Anwendung verwendet spezielle Sequenzen für die **nms:broadLog** und **nms:trackingLog** Schemas (**NmsBroadLogId** und **NmsTrackingLogId** ), da dies die Tabellen sind, die die meisten Datensätze enthalten.

Ab ACC 18.10 **XtkNewId** ist nicht mehr der Standardwert für die Sequenz in den nativen Schemas. Sie können jetzt ein Schema erstellen oder ein vorhandenes Schema mit einer dedizierten Sequenz erweitern.

>[!IMPORTANT]
>
>Beim Anlegen eines neuen Schemas oder bei einer Schema-Erweiterung müssen Sie für das gesamte Schema den gleichen Wert für die Primärschlüsselfolge (@pkSequence) beibehalten.

Eine Sequenz, auf die in einem Adobe Campaign-Schema (**NmsTrackingLogId** Beispielsweise) muss mit einer SQL-Funktion verknüpft sein, die die Anzahl der IDs in den Parametern durch Kommas getrennt zurückgibt. Diese Funktion muss aufgerufen werden **GetNew** XXX **IDs**, wobei **XXX** ist der Name der Sequenz (**GetNewNmsTrackingLogIds** zum Beispiel). Anzeigen der **postgres-nms.sql**, **mssql-nms.sql** oder **oracle-nms.sql** -Dateien, die mit der Anwendung im **datakit/nms/eng/sql/** -Verzeichnis, um das Beispiel einer &quot;NmsTrackingLogId&quot;-Sequenzerstellung für jede Datenbank-Engine abzurufen.

Um einen eindeutigen Schlüssel zu deklarieren, füllen Sie die **autopk** -Attribut (mit dem Wert &quot;true&quot;) auf das Hauptelement des Datenschemas.

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

Zusätzlich zur Definition des Schlüssels und seines Index wurde dem erweiterten Schema ein numerisches Feld namens &quot;id&quot;hinzugefügt, das den automatisch generierten Primärschlüssel enthält.

>[!IMPORTANT]
>
>Ein Datensatz mit einem auf 0 gesetzten Primärschlüssel wird bei der Erstellung der Tabelle automatisch eingefügt. Durch die Verwendung dieses Datensatzes werden äußere Joins vermieden, die sich bei Volumentabellen als nicht effektiv erweisen. Standardmäßig werden alle Fremdschlüssel mit dem Wert 0 initialisiert. Auf diese Weise kann beim Join immer ein Ergebnis zurückgegeben werden, wenn das Datenelement nicht ausgefüllt wird.


## Weitere Informationen

Weitere Informationen finden Sie unter den folgenden Links:

* [Erste Schritte mit Schemata](about-schema-reference.md)
* [Schemastruktur](schema-structure.md)
* [Datenbank-Mapping](database-mapping.md)
* [Link-Management](database-links.md)
* [Campaign-Datenmodell](about-data-model.md)
