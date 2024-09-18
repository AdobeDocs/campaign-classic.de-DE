---
product: campaign
title: Datenbank-Mapping
description: Datenbank-Mapping
feature: Configuration, Instance Settings
role: Data Engineer, Developer
exl-id: 728b509f-2755-48df-8b12-449b7044e317
source-git-commit: 517b85f5d7691acc2522bf4541f07c34c60c7fbf
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 46%

---

# Datenbank-Mapping{#database-mapping}

Die SQL-Zuordnung des Beispielschemas, das [auf dieser Seite](schema-structure.md) beschrieben ist, generiert das folgende XML-Dokument:

```sql
<schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">
  <enumeration basetype="byte" name="gender">    
    <value label="Not specified" name="unknown" value="0"/>    
    <value label="Male" name="male" value="1"/>    
    <value label="Female" name="female" value="2"/> 
  </enumeration>  

  <element name="recipient" sqltable="CusRecipient">    
    <attribute desc="Recipient email address" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>    
    <attribute default="GetDate()" label="Date of creation" name="created" sqlname="tsCreated" type="datetime"/>    
    <attribute enum="gender" label="Gender" name="gender" sqlname="iGender" type="byte"/>    
    <element label="Location" name="location">      
      <attribute label="City" length="50" name="city" sqlname="sCity" type="string" userEnum="city"/>    
    </element>  
  </element>
</schema>
```

Das Stammelement des Schemas wurde in **`<srcschema>`** in **`<schema>`** geändert.

Dieser andere Dokumenttyp wird automatisch aus dem Quellschema generiert und einfach als Schema bezeichnet.

Die SQL-Namen werden automatisch anhand des Elementnamens und des Elementtyps bestimmt.

Die SQL-Benennungsregeln lauten wie folgt:

* **table**: Verkettung von Schema-Namespace und Name

  In diesem Beispiel wird der Tabellenname über das Hauptelement des Schemas im Attribut **sqltable** eingegeben:

  ```sql
  <element name="recipient" sqltable="CusRecipient">
  ```

* **field**: Name des Elements, dem ein Präfix vorangestellt ist, das nach Typ definiert wurde: &quot;i&quot;für Integer, &quot;d&quot;für Dublette, &quot;s&quot;für Zeichenfolge, &quot;ts&quot;für Datumsangaben usw.

  Der Feldname wird über das Attribut **sqlname** für die verschiedenen Eingaben von **`<attribute>`** und **`<element>`** eingegeben:

  ```sql
  <attribute desc="Email address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/> 
  ```

>[!NOTE]
>
>SQL-Namen können aus dem Quellschema geladen werden. Füllen Sie dazu die Attribute &quot;sqltable&quot; oder &quot;sqlname&quot; für das betreffende Element aus.

Das SQL-Script zur Erstellung der aus dem erweiterten Schema generierten Tabelle lautet wie folgt:

```sql
CREATE TABLE CusRecipient(
  iGender NUMERIC(3) NOT NULL Default 0,   
  sCity VARCHAR(50),   
  sEmail VARCHAR(80),
  tsCreated TIMESTAMP Default NULL);
```

In Bezug auf SQL-Felder gelten folgende Einschränkungen:

* Keine Nullwerte in numerischen und Datumsfeldern
* Numerische Felder werden mit 0 initialisiert

## XML-Felder {#xml-fields}

Standardmäßig werden alle Elemente vom Typ **`<attribute>`** und **`<element>`** einem SQL-Feld der Datenschematabelle zugeordnet. Sie können dieses Feld jedoch anstatt in SQL auch in XML referenzieren. Das bedeutet, dass die Daten in einem Memo-Feld (&quot;mData&quot;) der Tabelle gespeichert werden, in der Werte aller XML-Felder enthalten sind. Als Speicher dieser Daten fungiert ein XML-Dokument, das die Struktur des Schemas beibehält.

Um ein Feld in XML auszufüllen, müssen Sie dem betreffenden Element das Attribut **xml** mit dem Wert &quot;true&quot; hinzufügen.

**Beispiel**: Im Folgenden finden Sie zwei Beispiele für die Verwendung von XML-Feldern.

* Mehrzeiliges Kommentarfeld:

  ```sql
  <element name="comment" xml="true" type="memo" label="Comment"/>
  ```

* Beschreibung der Daten im HTML-Format:

  ```sql
  <element name="description" xml="true" type="html" label="Description"/>
  ```

  Über den Typ &quot;html&quot; können Sie HTML-Inhalte in einem CDATA-Tag speichern und eine spezielle HTML-Bearbeitungsprüfung in der Benutzeroberfläche des Adobe Campaign-Clients anzeigen.

Verwenden Sie XML-Felder, um neue Felder hinzuzufügen, ohne die physische Struktur der Datenbank zu ändern. Ein weiterer Vorteil besteht darin, dass Sie weniger Ressourcen verwenden (Größe für SQL-Felder, Anzahl der Felder pro Tabelle usw.). Beachten Sie jedoch, dass Sie ein XML-Feld nicht indizieren oder filtern können.

## Indexierte Felder {#indexed-fields}

Indizes ermöglichen die Optimierung der Leistung der in der Anwendung verwendeten SQL-Abfragen.

Ein Index wird aus dem Hauptelement des Datenschemas deklariert.

```sql
<dbindex name="name_of_index" unique="true/false">
  <keyfield xpath="xpath_of_field1"/>
  <keyfield xpath="xpath_of_field2"/>
  ...
</key>
```

Indizes folgen den folgenden Regeln:

* Ein Index kann auf ein oder mehrere Felder in der Tabelle verweisen
* Ein Index kann in allen Feldern eindeutig sein (um Duplikate zu vermeiden), wenn das Attribut **unique** den Wert &quot;true&quot;enthält
* Der SQL-Name des Index wird anhand des SQL-Namens der Tabelle und des Indexnamens bestimmt

>[!NOTE]
>
>* Standardmäßig sind Indizes die ersten Elemente, die aus dem Hauptelement des Schemas deklariert werden.
>
>* Indizes werden während der Tabellenzuordnung (Standard oder FDA) automatisch erstellt.

**Beispiel**:

* Hinzufügen eines Index zur E-Mail-Adresse und Stadt:

  ```sql
  <srcSchema name="recipient" namespace="cus">
    <element name="recipient">
      <dbindex name="email">
        <keyfield xpath="@email"/> 
        <keyfield xpath="location/@city"/> 
      </dbindex>
  
      <attribute name="email" type="string" length="80" label="Email" desc="Email address of recipient"/>
      <element name="location" label="Location">
        <attribute name="city" type="string" length="50" label="City" userEnum="city"/>
      </element>
    </element>
  </srcSchema>
  ```

* Hinzufügen eines eindeutigen Index zum Feld &quot;id&quot;-Name:

  ```sql
  <srcSchema name="recipient" namespace="cus">
    <element name="recipient">
      <dbindex name="id" unique="true">
        <keyfield xpath="@id"/> 
      </dbindex>
  
      <dbindex name="email">
        <keyfield xpath="@email"/> 
      </dbindex>
  
      <attribute name="id" type="long" label="Identifier"/>
      <attribute name="email" type="string" length="80" label="Email" desc="Email address of recipient"/>
    </element>
  </srcSchema>
  ```

## Weitere Informationen

Weitere Informationen finden Sie unter den folgenden Links:

* [Erste Schritte mit Schemata](about-schema-reference.md)
* [Schemastruktur](schema-structure.md)
* [Schlüssel-Management](database-keys.md)
* [Link-Management](database-links.md)
* [Campaign-Datenmodell](about-data-model.md)