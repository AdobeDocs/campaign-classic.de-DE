---
product: campaign
title: Beispiele für Schemabearbeitung
description: Beispiele für Schemabearbeitung
feature: Schema Extension
role: Data Engineer, Developer
exl-id: b7ee70e0-89c6-4cd3-8116-2f073d4a2f2f
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '669'
ht-degree: 2%

---


# Beispiele für Schemabearbeitung{#examples-of-schemas-edition}

## Tabelle erweitern {#extending-a-table}

Erweiterung der **nms:recipient** Schema-Empfängertabelle verwenden:

1. Erstellen Sie das Erweiterungsschema (**cus:extension**) unter Verwendung der folgenden Daten:

   ```
   <srcSchema mappingType="sql" name="extension" namespace="cus" xtkschema="xtk:srcSchema" extendedSchema="nms:recipient">  
     <enumeration basetype="string" default="area1" name="area">    
       <value label="Zone 1" name="area1"/>    
       <value label="Zone 2" name="area2"/>  
     </enumeration>  
   
     <element name="extension">    
       <dbindex name="area">      
         <keyfield xpath="location/@area"/>    
       </dbindex>      
   
       <attribute label="Loyalty code" name="fidelity" type="long"/>    
       <element name="location">      
         <attribute name="area" label="Purchasing zone" type="string" length="50" enum="area"/>    
       </element>  </element>  
   </srcSchema>
   ```

   In diesem Beispiel wird ein indiziertes Feld (**Treue**) hinzugefügt wird und die **location** -Element (das bereits im **nms:recipient** schema) durch ein Aufzählungsfeld (**area**).

   >[!IMPORTANT]
   >
   >Denken Sie daran, die **extendedSchema** -Attribut, um auf das Erweiterungsschema zu verweisen.

1. Überprüfen Sie, ob das erweiterte Schema der **nms:recipient** und dass die zusätzlichen Daten vorhanden sind:

   ```
   <schema dependingSchemas="cus:extension" mappingType="sql" name="recipient" namespace="nms" xtkschema="xtk:schema">
     ...
     <enumeration basetype="string" default="area1" name="area">    
       <value label="Zone 1" name="area1"/>    
       <value label="Zone 2" name="area2"/>  
     </enumeration>
     ...
     <element autopk="true" name="recipient" sqltable="NmsRecipient"> 
       <dbindex name="area">      
         <keyfield xpath="location/@area"/>    
       </dbindex>
   
       ...
       <attribute belongsTo="cus:extension" label="Loyalty code" name="fidelity" sqlname="iFidelity" type="long"/>
       <element name="location">
         ...
         <attribute enum="area" label="Purchasing zone" length="50" name="area" sqlname="sArea" type="string"/>
       </element>
       ...
     </element>
   </schema>
   ```

   Das im Datenbankaktualisierungs-Assistenten generierte SQL-Skript stellt sich wie folgt dar:

   ```
   ALTER TABLE NmsRecipient ADD iFidelity INTEGER;
   UPDATE NmsRecipient SET iFidelity = 0;
   ALTER TABLE NmsRecipient ALTER COLUMN iFidelity SET NOT NULL;ALTER TABLE NmsRecipient ALTER COLUMN iFidelity SET Default 0;
   ALTER TABLE NmsRecipient ADD sArea VARCHAR(50); 
   CREATE INDEX NmsRecipient_area ON NmsRecipient(sArea);
   ```

## Verknüpfte Sammlungstabelle {#linked-collection-table}

In diesem Abschnitt wird beschrieben, wie Sie eine mit der Empfängertabelle verknüpfte Bestelltabelle mit Kardinalität 1-N erstellen.

Quellschema der Bestelltabelle:

```
<srcSchema label="Order" name="order" namespace="cus" xtkschema="xtk:srcSchema">  
  <element autopk="true" name="order">    
    <compute-string expr="@number" + '(' + ToString(@date) + ')'/>    
    
    <attribute label="Number" length="128" name="number" type="string"/>    
    <attribute desc="Order date" label="Date" name="date" type="datetime" default="GetDate()"/>    
    <attribute desc="order total" label="Total" name="total" type="double"/>    
    <element label="Recipient" name="recipient" revDesc="Orders associated with this recipient" revIntegrity="own" revLabel="Orders" target="nms:recipient" type="link"/>  
  </element>
</srcSchema>
```

Der Tabellentyp lautet **autopk** um einen automatisch generierten Primärschlüssel zu erstellen, der vom Join des Links zur Empfängertabelle verwendet wird.

Schema generiert:

```
<schema label="Order" mappingType="sql" name="order" namespace="cus" xtkschema="xtk:schema">  
  <element autopk="true" label="Order" name="order" sqltable="CusOrder">    
    <compute-string expr="ToString(@date) + ' - ' + @number"/>    

    <dbindex name="id" unique="true">      
      <keyfield xpath="@id"/>    
    </dbindex>    

    <key internal="true" name="id">      
      <keyfield xpath="@id"/>    
    </key>    

    <dbindex name="recipientId">      
      <keyfield xpath="@recipient-id"/>    
    </dbindex>    

    <attribute desc="Internal primary key" label="Primary key" name="id" sqlname="iOrderId" type="long"/>    
    <attribute label="Number" length="128" name="number" sqlname="sNumber" type="string"/>    
    <attribute desc="Order date" label="Date" name="date" sqlname="tsDate" type="datetime"/>    
    <attribute desc="order total" label="Total" name="total" sqlname="Total" type="double"/>    
    <element label="Recipient" name="recipient" revLink="order" target="nms:recipient" type="link">      
      <join xpath-dst="@id" xpath-src="@recipient-id"/>    
    </element>    
    <attribute advanced="true" label="Foreign key of 'Recipient' link ('id' field)" name="recipient-id" sqlname="iRecipientId" type="long"/>  
   </element>
</schema>
```

Das SQL-Skript zur Tabellenerstellung sieht wie folgt aus:

```
CREATE TABLE CusOrder(dTotal DOUBLE PRECISION NOT NULL Default 0, iOrderId INTEGER NOT NULL Default 0, iRecipientId INTEGER NOT NULL Default 0, sNumber VARCHAR(128), tsDate TIMESTAMP Default NULL);
CREATE UNIQUE INDEX CusOrder_id ON CusOrder(iOrderId);
CREATE INDEX CusOrder_recipientId ON CusOrder(iRecipientId);  
INSERT INTO CusOrder (iOrderId) VALUES (0); 
```

>[!NOTE]
>
>Mit dem SQL-Befehl INSERT INTO am Ende des Skripts können Sie einen Kennungsdatensatz mit dem Wert 0 einfügen, um äußere Joins zu simulieren.

## Erweiterungstabelle {#extension-table}

Mit einer Erweiterungstabelle können Sie den Inhalt einer existierenden Tabelle in einer verknüpften Tabelle mit Kardinalität 1-1 erweitern.

Mit einer Erweiterungstabelle sollen Begrenzungen der Anzahl der in einer Tabelle unterstützten Felder vermieden oder der für die Daten belegte Speicherplatz optimiert werden, der bei Bedarf genutzt wird.

Erstellen des Tabellen-Schemas für die Erweiterung (**cus:feature**):

```
<srcSchema mappingType="sql" name="feature" namespace="cus" xtkschema="xtk:srcSchema">  
  <element autopk="true" name="feature">    
    <attribute label="Children" name="children" type="byte"/>    
    <attribute label="Single" name="single" type="boolean"/>    
    <attribute label="Spouse first name" length="100" name="spouseFirstName" type="string"/>  
  </element>
</srcSchema>
```

Erstellen eines Erweiterungsschemas für die Empfängertabelle, um die Relation der Kardinalität 1-1 hinzuzufügen:

```
<srcSchema extendedSchema="nms:recipient" label="Recipient" mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:srcSchema">  
  <element name="recipient">    
    <element desc="Features" integrity="own" label="Features" name="feature" revCardinality="single" revLink="recipient" target="cus:feature" type="link"/> 
  </element>
</srcSchema>
```

>[!NOTE]
>
>Die Definition der Relation zwischen der Empfängertabelle und der Erweiterungstabelle muss aus dem Schema, das den Fremdschlüssel enthält, stammen.

Das SQL-Skript zum Erstellen der Erweiterungstabelle lautet wie folgt:

```
CREATE TABLE CusFeature(  iChildren NUMERIC(3) NOT NULL Default 0, iFeatureId INTEGER NOT NULL Default 0, iSingle NUMERIC(3) NOT NULL Default 0, sSpouseFirstName VARCHAR(100));
CREATE UNIQUE INDEX CusFeature_id ON CusFeature(iFeatureId);  
INSERT INTO CusFeature (iFeatureId) VALUES (0); 
```

Das SQL-Aktualisierungsskript für die Empfängertabelle stellt sich wie folgt dar:

```
ALTER TABLE NmsRecipient ADD iFeatureId INTEGER;
UPDATE NmsRecipient SET iFeatureId = 0;
ALTER TABLE NmsRecipient ALTER COLUMN iFeatureId SET NOT NULL;
ALTER TABLE NmsRecipient ALTER COLUMN iFeatureId SET Default 0;
CREATE INDEX NmsRecipient_featureId ON NmsRecipient(iFeatureId);
```

## Überlauftabelle {#overflow-table}

Eine Überlauftabelle ist eine Erweiterungstabelle (Kardinalität 1-1). Die Deklaration der Relation zur zu erweiternden Tabelle wird jedoch im Schema der Überlauftabelle ausgefüllt.

Die Überlauftabelle enthält den Fremdschlüssel der Tabelle, die erweitert werden soll. Die zu erweiternde Tabelle wird daher nicht geändert. Die Relation zwischen den beiden Tabellen ist der Wert des Primärschlüssels der zu erweiternden Tabelle.

Erstellen des Überlauftabellenschemas (**cus:overflow**):

```
<srcSchema label="Overflow" name="overflow" namespace="cus" xtkschema="xtk:srcSchema">  
  <element name="overflow">    
    <key internal="true" name="id">      
      <keyfield xlink="recipient"/>    
    </key>    

    <attribute label="Children" name="children" type="byte"/>    
    <attribute label="Single" name="single" type="boolean"/>    
    <attribute label="Spouse first name" length="100" name="spouseFirstName" type="string"/>  
    <element label="Customer" name="recipient" revCardinality="single" revIntegrity="own" revExternalJoin="true" target="nms:recipient" type="link"/>  
  </element>  
</srcSchema>
```

>[!NOTE]
>
>Der Primärschlüssel der Überlauftabelle ist die Relation zur Tabelle, die erweitert werden soll ( Schema &quot;nms:recipient&quot; in unserem Beispiel).

Das SQL-Skript zur Tabellenerstellung sieht wie folgt aus:

```
CREATE TABLE CusOverflow(iChildren NUMERIC(3) NOT NULL Default 0, iRecipientId INTEGER NOT NULL Default 0, iSingle NUMERIC(3) NOT NULL Default 0, sSpouseFirstName VARCHAR(100));
CREATE UNIQUE INDEX CusOverflow2_id ON CusOverflow2(iRecipientId);  
```

## Relationstabelle {#relationship-table}

Mithilfe einer Beziehungstabelle können Sie zwei Tabellen mit Kardinalität N-N verknüpfen. Diese Tabelle enthält nur die Fremdschlüssel der zu verknüpfenden Tabellen.

Beispiel einer Beziehungstabelle zwischen Gruppen (**nms:group**) und Empfängern (**nms:recipient**).

Quellschema der Beziehungstabelle:

```
<srcSchema name="rcpGrpRel" namespace="cus">
  <element name="rcpGrpRel">
    <key internal="true" name="id">      
      <keyfield xlink="rcpGroup"/>      
      <keyfield xlink="recipient"/>    
    </key>

    <element integrity="neutral" label="Recipient" name="recipient" revDesc="Groups to which this recipient belongs" revIntegrity="own" revLabel="Groups" target="nms:recipient" type="link"/>    
    <element integrity="neutral" label="Group" name="rcpGroup" revDesc="Recipients in the group" revIntegrity="own" revLabel="Recipients" revLink="rcpGrpRel" target="nms:group" type="link"/>
  </element>
</srcSchema>
```

Das generierte Schema stellt sich wie folgt dar:

```
<schema mappingType="sql" name="rcpGrpRel" namespace="cus" xtkschema="xtk:schema">  
  <element name="rcpGrpRel" sqltable="CusRcpGrpRel">    
    <compute-string expr="ToString([@rcpGroup-id]) + ',' + ToString([@recipient-id])"/>    
    <dbindex name="id" unique="true">      
      <keyfield xpath="@rcpGroup-id"/>      
      <keyfield xpath="@recipient-id"/>    
    </dbindex>    

    <key internal="true" name="id">      
      <keyfield xpath="@rcpGroup-id"/>      
      <keyfield xpath="@recipient-id"/>    
    </key>    

    <dbindex name="rcpGroupId">      
      <keyfield xpath="@rcpGroup-id"/>    
    </dbindex>    
    <dbindex name="recipientId">      
      <keyfield xpath="@recipient-id"/>    
    </dbindex>    

    <element integrity="neutral" label="Recipient" name="recipient" revLink="rcpGrpRel" target="nms:recipient" type="link">      
      <join xpath-dst="@id" xpath-src="@recipient-id"/>    
    </element>    
    <attribute advanced="true" label="Foreign key of 'Recipient' link ('id' field)" name="recipient-id" sqlname="iRecipientId" type="long"/>    

    <element integrity="neutral" label="Group" name="rcpGroup" revLink="rcpGrpRel" target="nms:group" type="link">      
      <join xpath-dst="@id" xpath-src="@rcpGroup-id"/>    
    </element>    
    <attribute advanced="true" label="Foreign key of 'Group' link ('id' field)" name="rcpGroup-id" sqlname="iRcpGroupId" type="long"/>  
  </element>
</schema>
```

Das SQL-Skript zur Tabellenerstellung sieht wie folgt aus:

```
CREATE TABLE CusRcpGrpRel( iRcpGroupId INTEGER NOT NULL Default 0, iRecipientId INTEGER NOT NULL Default 0);
CREATE UNIQUE INDEX CusRcpGrpRel_id ON CusRcpGrpRel(iRcpGroupId, iRecipientId);
CREATE INDEX CusRcpGrpRel_recipientId ON CusRcpGrpRel(iRecipientId);
```

## Anwendungsbeispiel: Feld mit einer vorhandenen Referenztabelle verknüpfen {#uc-link}

Dieser Anwendungsfall zeigt, wie Sie eine vorhandene Referenztabelle als Alternative zu den integrierten Adobe Campaign-Auflistungsmechanismen (enum, userEnum oder dbEnum) verwenden können.

Sie können auch eine vorhandene Referenztabelle als Auflistung in Ihren Schemas verwenden. Dies kann durch Erstellen einer Relation zwischen einer Tabelle und der Referenztabelle und Hinzufügen des Attributs erreicht werden. **displayAsField=&quot;true&quot;**.

In diesem Beispiel enthält die Referenztabelle eine Liste von Banknamen und Kennungen:

```
<srcSchema entitySchema="xtk:srcSchema" img="cus:bank16x16.png" label="Bank" mappingType="sql" name="bank" namespace="cus"
xtkschema="xtk:srcSchema">
    <element img="cus:bank16x16.png" label="Banks" name="bank">
        <compute-string expr="@name"/>
        <key name="id">
            <keyfield xpath="@id"/>
        </key>
        <attribute label="Bank Id" name="id" type="short"/>
        <attribute label="Name" length="64" name="name" type="string"/>
     </element> 
</srcSchema>
```

Definieren Sie in jeder Tabelle, die diese Referenztabelle verwendet, einen Link und fügen Sie die **displayAsField=&quot;true&quot;** -Attribut.

```
<element displayAsField="true" label="Bank" name="bank" target="cus:bank" type="link" noDbIndex="true"/>
```

In der Benutzeroberfläche wird kein Link, sondern ein Feld angezeigt. Wenn Benutzer dieses Feld auswählen, können sie einen Wert aus der Referenztabelle auswählen oder die Funktion für die automatische Vervollständigung verwenden.

![](assets/schema-edition-ex.png)

* Damit sie automatisch ausgefüllt werden kann, müssen Sie eine Compute-String in der Referenztabelle definieren.

* Fügen Sie die **noDbIndex=&quot;true&quot;** -Attribut in der Link-Definition verwenden, um zu verhindern, dass Adobe Campaign einen Index für die in der Quelltabelle des Links gespeicherten Werte erstellt.

## Verwandte Themen

* [Arbeiten mit Auflistungen](../../platform/using/managing-enumerations.md)

* [Erste Schritte mit Campaign-Schemata](../../configuration/using/about-schema-edition.md)

* [Datenbankstruktur aktualisieren](../../configuration/using/updating-the-database-structure.md)
