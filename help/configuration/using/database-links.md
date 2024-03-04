---
product: campaign
title: Datenbank-Mapping
description: Datenbank-Mapping
feature: Configuration, Instance Settings
role: Data Engineer, Developer
badge-v7-only: label="v7" type="Informative" tooltip="Gilt nur für Campaign Classic v7"
source-git-commit: f03e72d4ecd17446264adf74603aefca95f99d41
workflow-type: tm+mt
source-wordcount: '918'
ht-degree: 57%

---


# Linkverwaltung {#links--relation-between-tables}

Eine Relation beschreibt die Zuordnung einer Tabelle zu einer anderen.

Die Vereinigungen, auch Kardinalität genannt, sind im Folgenden aufgeführt.

* 1-1-Kardinalität: Eine Entität in der Quelltabelle kann maximal mit einer Entität in der Zieltabelle in Beziehung stehen.
* 1-N-Kardinalität: Eine Entität in der Quelltabelle kann mit mehreren Entitäten in der Zieltabelle in Beziehung stehen, aber eine Entität in der Zieltabelle kann nur maximal mit einer Entität in der Quelltabelle in Beziehung stehen.
* N-N-Kardinalität: Eine Entität in der Quelltabelle kann mit mehreren Entitäten in der Zieltabelle in Beziehung stehen und umgekehrt.

In der Benutzeroberfläche werden Kardinalitäten mit einem bestimmten Symbol dargestellt.

Für Join-Beziehungen mit einer Campaign-Tabelle/-Datenbank:

* ![](assets/join_with_campaign11.png): 1-1-Kardinalität. Dies kann etwa eine Beziehung zwischen einem Empfänger und einer aktuellen Bestellung sein. Ein Empfänger kann jeweils nur mit einer Entität der aktuellen Tabelle zu Bestellungen verknüpft sein.
* ![](assets/externaljoin11.png): 1-1-Kardinalität, externer Join. Dies kann etwa eine Beziehung zwischen einem Empfänger und dem ihm zugehörigen Land sein. Ein Empfänger kann nur mit einer Entität der Ländertabelle verknüpft sein. Der Inhalt der Ländertabelle wird nicht gespeichert.
* ![](assets/join_with_campaign1n.png): 1-N-Kardinalität. Dies kann etwa eine Beziehung zwischen einem Empfänger und der Tabelle zu Abonnements sein. Ein Empfänger kann mit mehreren Vorkommen in der Abonnementtabelle in Verbindung gebracht werden.

Für Verknüpfungsrelationen mit Federated Database Access (FDA):

* ![](assets/join_fda_11.png): 1-1-Kardinalität
* ![](assets/join_fda_1m.png): 1-N-Kardinalität

Weitere Informationen zu FDA-Tabellen finden Sie unter [Zugriff auf externe Datenbanken](../../installation/using/about-fda.md).

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

   * **name**: Name des Links aus der Quelltabelle
   * **target**: Name des Zielschemas
   * **label**: Link-Titel
   * **revLink** (optional): Name des Reverse-Links aus dem Zielschema (standardmäßig automatisch abgezogen)
   * **Integrität** (optional): referenzielle Integrität des Vorkommens der Quelltabelle mit dem Vorkommen der Zieltabelle.
Mögliche Werte:

      * **definieren**: Das Quellvorkommen kann gelöscht werden, wenn es nicht mehr durch ein Zielvorkommen referenziert wird.
      * **normal**: Beim Löschen des Vorkommens der Quelle werden die Schlüssel der Relation zum Vorkommen der Zielgruppe initialisiert (Standardmodus). Dieser Integritätstyp initialisiert alle Fremdschlüssel
      * **own**: Das Löschen des Vorkommens der Quelle führt zum Löschen des Vorkommens der Zielgruppe
      * **owncopy**: entspricht **own** (im Falle einer Löschung) oder dupliziert die Vorkommnisse (im Fall einer Duplizierung).
      * **neutral**: kein spezifisches Verhalten

   * **revIntegrity** (optional): Integrität des Zielschemas (optional, standardmäßig &quot;normal&quot;)
   * **revCardinality** (optional): mit dem Wert &quot;single&quot;wird die Kardinalität mit dem Typ 1-1 ausgefüllt (standardmäßig 1-N)
   * **externalJoin** (optional): Erzwingt den äußeren Join.
   * **revExternalJoin** (optional): Erzwingt den äußeren Join am Umkehr-Link.

* Eine Relation referenziert ein oder mehrere Felder aus der Quelltabelle mit der Zieltabelle. Die Felder, aus denen sich der Join zusammensetzt (`<join>`-Element), müssen nicht ausgefüllt werden, da sie standardmäßig aus dem internen Schlüssel des Zielschemas abgeleitet werden.
* Im erweiterten Schema wird dem Fremdschlüssel der Relation automatisch ein Index hinzugefügt.
* Eine Relation setzt sich aus zwei Halb-Relationen zusammen, wobei die erste über das Quellschema deklariert und die zweite automatisch im erweiterten Schema des Zielschemas erstellt wird.
* Ein Join kann ein äußerer Join sein, wenn das Attribut **externalJoin** mit dem Wert &quot;true&quot; hinzugefügt wird (unterstützt in PostgreSQL).

>[!NOTE]
>
>Standardmäßig sind Links die Elemente, die am Ende des Schemas deklariert werden.

## Beispiel: Reverse-Link {#example-1}

Im folgenden Beispiel deklarieren wir eine 1:N-Relation zur Schematabelle &quot;cus:company&quot;:

```sql
<srcSchema name="recipient" namespace="cus">
  <element name="recipient">
    ...
    <element label="Company" name="company" revIntegrity="define" revLabel="Contact" target="cus:company" type="link"/>
  </element>
</srcSchema>
```

Generiertes Schema:

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

## Beispiel: einfacher Link {#example-2}

In diesem Beispiel deklarieren wir einen Link zur Schematabelle &quot;nms:address&quot;. Der Join ist ein äußere Join und wird explizit mit der E-Mail-Adresse des Empfängers und dem Feld &quot;@address&quot;der verknüpften Tabelle (&quot;nms:address&quot;) ausgefüllt.

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

In diesem Beispiel erstellen wir eine 1:1-Relation zur Schematabelle &quot;cus:extension&quot;:

```sql
<element integrity="own" label="Extension" name="extension" revCardinality="single" revLink="recipient" target="cus:extension" type="link"/>
```

## Beispiel: Link zu einem Ordner {#example-4}

In diesem Beispiel deklarieren wir einen Link zu einem Ordner ( Schema &quot;xtk:folder&quot;):

```sql
<element default="DefaultFolder('nmsFolder')" label="Folder" name="folder" revDesc="Recipients in the folder" revIntegrity="own" revLabel="Recipients" target="xtk:folder" type="link"/>
```

Der Standardwert gibt die Kennung der ersten qualifizierten Parametertypdatei zurück, die in der Funktion &quot;DefaultFolder(&#39;nmsFolder&#39;)&quot; eingegeben wurde.

## Beispiel: Erstellen eines Schlüssels für einen Link {#example-5}

In diesem Beispiel erstellen wir einen Schlüssel für einen Link (&quot;company&quot; zu &quot;cus:company&quot;-Schema) mit dem **xlink** und ein Feld der Tabelle (&quot;email&quot;):

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

Generiertes Schema:

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

Die Definition des Namensschlüssels &quot;companyEmail&quot;wurde um den Fremdschlüssel der &quot;company&quot;-Relation erweitert. Dieser Schlüssel generiert einen eindeutigen Index für beide Felder.
