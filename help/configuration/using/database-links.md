---
product: campaign
title: Datenbank-Mapping
description: Datenbank-Mapping
feature: Configuration, Instance Settings
role: Data Engineer, Developer
exl-id: e05dcd81-bbca-4767-8da3-ea064f7f6c8e
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '932'
ht-degree: 99%

---

# Verknüpfungs-Management {#links--relation-between-tables}

Eine Verknüpfung beschreibt die Zuordnung einer Tabelle zu einer anderen.

Die Verbindungstypen, auch Kardinalitäten genannt, sind im Folgenden aufgeführt.

* 1-1-Kardinalität: Eine Entität in der Quelltabelle kann maximal mit einer Entität in der Zieltabelle in Beziehung stehen.
* 1-N-Kardinalität: Eine Entität in der Quelltabelle kann mit mehreren Entitäten in der Zieltabelle in Beziehung stehen, aber eine Entität in der Zieltabelle kann nur maximal mit einer Entität in der Quelltabelle in Beziehung stehen.
* N-N-Kardinalität: Eine Entität in der Quelltabelle kann mit mehreren Entitäten in der Zieltabelle in Beziehung stehen und umgekehrt.

In der Benutzeroberfläche werden Kardinalitäten mit einem bestimmten Symbol dargestellt.

Für Join-Beziehungen mit einer Campaign-Tabelle/-Datenbank:

* ![](assets/join_with_campaign11.png): 1-1-Kardinalität. Dies kann etwa eine Beziehung zwischen einem Empfänger und einer aktuellen Bestellung sein. Ein Empfänger kann jeweils nur mit einer Entität der aktuellen Tabelle zu Bestellungen verknüpft sein.
* ![](assets/externaljoin11.png): 1-1-Kardinalität, externer Join. Dies kann etwa eine Beziehung zwischen einem Empfänger und dem ihm zugehörigen Land sein. Ein Empfänger kann nur mit einer Entität der Ländertabelle verknüpft sein. Der Inhalt der Ländertabelle wird nicht gespeichert.
* ![](assets/join_with_campaign1n.png): 1-N-Kardinalität. Dies kann etwa eine Beziehung zwischen einem Empfänger und der Tabelle zu Abonnements sein. Ein Empfänger oder eine Empfängerin kann mit mehreren Instanzen in der Abonnements-Tabelle verknüpft sein.

Für Join-Beziehungen, die Federated Data Access (FDA) nutzen:

* ![](assets/join_fda_11.png): 1-1-Kardinalität
* ![](assets/join_fda_1m.png): 1-N-Kardinalität

Weitere Informationen zu FDA-Tabellen finden Sie unter [Zugriff auf eine externe Datenbank](../../installation/using/about-fda.md).

In dem Schema, das den Fremdschlüssel der Tabelle enthält, muss über das Hauptelement eine Relation angegeben werden:

```sql
<element name="name_of_link" type="link" target="key_of_destination_schema">
  <join xpath-dst="xpath_of_field1_destination_table" xpath-src="xpath_of_field1_source_table"/>
  <join xpath-dst="xpath_of_field2_destination_table" xpath-src="xpath_of_field2_source_table"/>
  ...
</element>
```

Für Relationen gelten folgende Regeln:

* Die Definition einer Relation erfolgt über den Typ **link** für **`<element>`**, wobei folgende Attributen eingegeben werden:

   * **name**: Name der Verknüpfung aus der Quelltabelle
   * **target**: Name des Zielschemas
   * **label**: Titel der Verknüpfung
   * **revLink** (optional): Name der Umkehrverknüpfung aus dem Zielschema (wird standardmäßig automatisch abgeleitet)
   * **integrity** (optional): Referenzintegrität der Instanz aus der Quelltabelle zur Instanz der Zieltabelle.
Mögliche Werte:

      * **define**: Es ist möglich, die Quellinstanz zu löschen, wenn diese nicht mehr durch eine Zielinstanz referenziert wird.
      * **normal**: Durch Löschen der Quellinstanz werden die Schlüssel der Verknüpfung mit der Zielinstanz initialisiert (Standardmodus). Bei diesem Integritätstyp werden alle Fremdschlüssel initialisiert.
      * **own**: Durch Löschen der Quellinstanz wird auch die Zielinstanz gelöscht
      * **owncopy**: Führt dieselbe Operation aus wie **own** (im Falle des Löschens) oder dupliziert die Instanzen (im Falle der Duplizierung).
      * **neutral**: kein spezifisches Verhalten

   * **revIntegrity** (optional): Integrität im Zielschema (optional, Standardwert ist „normal“)
   * **revCardinality** (optional): Mit dem Wert „single“ wird die Kardinalität mit dem Typ 1:1 ausgefüllt (standardmäßig 1:n).
   * **externalJoin** (optional): Erzwingt den äußeren Join.
   * **revExternalJoin** (optional): Erzwingt den äußeren Join am Umkehr-Link.

* Eine Relation referenziert ein oder mehrere Felder aus der Quelltabelle mit der Zieltabelle. Die Felder, aus denen sich der Join zusammensetzt (`<join>`-Element), müssen nicht ausgefüllt werden, da sie standardmäßig aus dem internen Schlüssel des Zielschemas abgeleitet werden.
* Im erweiterten Schema wird dem Fremdschlüssel der Verknüpfung automatisch ein Index hinzugefügt.
* Eine Relation setzt sich aus zwei Halb-Relationen zusammen, wobei die erste über das Quellschema deklariert und die zweite automatisch im erweiterten Schema des Zielschemas erstellt wird.
* Ein Join kann ein äußerer Join sein, wenn das Attribut **externalJoin** mit dem Wert &quot;true&quot; hinzugefügt wird (unterstützt in PostgreSQL).

>[!NOTE]
>
>Standardmäßig sind Verknüpfungen die am Ende des Schemas deklarierten Elemente.

## Beispiel: Umkehrverknüpfung {#example-1}

Im folgenden Beispiel deklarieren wir eine 1:n-Verknüpfung mit der Schematabelle „cus:company“:

```sql
<srcSchema name="recipient" namespace="cus">
  <element name="recipient">
    ...
    <element label="Company" name="company" revIntegrity="define" revLabel="Contact" target="cus:company" type="link"/>
  </element>
</srcSchema>
```

Das generierte Schema:

```sql
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

Die Definition der Relation wird ergänzt durch die Felder, aus denen sich die Relation zusammensetzt: der Primärschlüssel mit XPath (&quot;@id&quot;) im Zielschema und der Fremdschlüssel mit XPath (&quot;@company-id&quot;) im Schema.

Der Fremdschlüssel wird automatisch in einem Element hinzugefügt, das dieselben Eigenschaften wie das zugehörige Feld in der Zieltabelle verwendet. Die Benennungskonvention hierfür lautet wie folgt: Name des Zielschemas gefolgt vom Namen des zugehörigen Felds (in diesem Beispiel &quot;company-id&quot;).

Erweitertes Zielgruppenschema (&quot;cus:company&quot;):

```sql
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

Ein Umkehrlink zur Tabelle &quot;cus:recipient&quot; wurde mit folgenden Parametern hinzugefügt:

* **name**: wird automatisch vom Namen des Quellschemas abgeleitet (kann mit dem Attribut &quot;revLink&quot; in der Definition der Relation im Quellschema erzwungen werden)
* **revLink**: Name des Umkehr-Links
* **target**: Schlüssel des verknüpften Schemas (Schema &quot;cus:recipient&quot;)
* **unbound**: Relation wird als Sammlungselement für eine 1-N-Kardinalität deklariert (standardmäßig)
* **integrity**: Standardwert ist &quot;define&quot; (kann mit dem Attribut &quot;revIntegrity&quot; in der Definition der Relation im Quellschema erzwungen werden)

## Beispiel: einfache Verknüpfung {#example-2}

In diesem Beispiel wird eine Verknüpfung mit der Schematabelle „nms:address“ deklariert. Der Join ist ein externer Join und wird explizit mit der E-Mail-Adresse des Empfängers oder der Empfängerin und dem Feld „@address“ der verknüpften Tabelle („nms:address“) ausgefüllt.

```sql
<srcSchema name="recipient" namespace="cus">
  <element name="recipient"> 
    ...
    <element integrity="neutral" label="Info about email" name="emailInfo" revIntegrity="neutral" revLink="recipient" target="nms:address" type="link" externalJoin="true">      
      <join xpath-dst="@address" xpath-src="@email"/>
    </element>
  </element>
</srcSchema>
```

## Beispiel: eindeutige Kardinalität {#example-3}

In diesem Beispiel erstellen wir eine 1:1-Verknüpfung mit der Schematabelle „cus:extension“:

```sql
<element integrity="own" label="Extension" name="extension" revCardinality="single" revLink="recipient" target="cus:extension" type="link"/>
```

## Beispiel: Verknüpfung mit einem Ordner {#example-4}

In diesem Beispiel deklarieren wir eine Verknüpfung mit einem Ordner (Schema „xtk:folder“):

```sql
<element default="DefaultFolder('nmsFolder')" label="Folder" name="folder" revDesc="Recipients in the folder" revIntegrity="own" revLabel="Recipients" target="xtk:folder" type="link"/>
```

Der Standardwert gibt die Kennung der ersten qualifizierten Parametertypdatei zurück, die in der Funktion &quot;DefaultFolder(&#39;nmsFolder&#39;)&quot; eingegeben wurde.

## Beispiel: Erstellen eines Schlüssels für eine Verknüpfung {#example-5}

In diesem Beispiel erstellen wir einen Schlüssel für eine Verknüpfung (zwischen Schema „company“ und Schema „cus:company“) mit dem Attribut **xlink** und einem Feld der Tabelle „email“:

```sql
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

```sql
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

    <attribute desc="Email address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>
    <element label="Company" name="company" revLink="recipient" target="sfa:company" type="link">      
      <join xpath-dst="@id" xpath-src="@company-id"/>    
    </element>    
    <attribute advanced="true" label="Foreign key of link 'Company' (field 'id')" name="company-id" sqlname="iCompanyId" type="long"/>
  </element>
</schema>
```

Die Definition des Namensschlüssels „companyEmail“ wurde um den Fremdschlüssel der Verknüpfung „company“ erweitert. Dieser Schlüssel generiert einen eindeutigen Index für beide Felder.

## Weitere Informationen

Weitere Informationen finden Sie unter den folgenden Links:

* [Erste Schritte mit Schemata](about-schema-reference.md)
* [Schemastruktur](schema-structure.md)
* [Datenbank-Mapping](database-mapping.md)
* [Schlüssel-Management](database-keys.md)
* [Campaign-Datenmodell](about-data-model.md)
