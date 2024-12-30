---
product: campaign
title: Datenorientierte APIs
description: Datenorientierte APIs
feature: API
role: Data Engineer, Developer
exl-id: a392c55e-541a-40b1-a910-4a6dc79abd2d
source-git-commit: 517b85f5d7691acc2522bf4541f07c34c60c7fbf
workflow-type: tm+mt
source-wordcount: '1813'
ht-degree: 1%

---

# Datenorientierte APIs{#data-oriented-apis}

Mit datenorientierten APIs können Sie das gesamte Datenmodell adressieren.

## Übersicht über das Datenmodell {#overview-of-the-datamodel}

Adobe Campaign bietet keine dedizierte Lese-API pro Entität (keine getRecipient- oder getDelivery-Funktion usw.). Verwenden Sie die Lese- und Änderungsmethoden für ABFRAGE- und SCHREIBDATEN , um auf die Daten des Modells zuzugreifen.

Mit Adobe Campaign können Sie Sammlungen verwalten: Mit Abfragen können Sie einen Satz von Informationen abrufen, die in der gesamten Datenbank erfasst werden. Im Gegensatz zum Zugriff im SQL-Modus geben Adobe Campaign-APIs eine XML-Struktur anstelle von Datenspalten zurück. Adobe Campaign erstellt daher zusammengesetzte Dokumente mit allen erfassten Daten.

Dieser Betriebsmodus bietet keine Eins-zu-eins-Zuordnung zwischen den Attributen und Elementen der XML-Dokumente und den Spalten der Tabellen in der Datenbank.

XML-Dokumente werden in Feldern vom Typ MEMO der Datenbank gespeichert.

## Beschreibung des Modells {#description-of-the-model}

Sie müssen mit dem Adobe Campaign-Datenmodell vertraut sein, um die Datenbankfelder in Ihren Skripten bearbeiten zu können.

Eine Darstellung des Datenmodells finden Sie in der [Beschreibung des Adobe Campaign-Datenmodells](../../configuration/using/data-model-description.md).

## Abfrage und Writer {#query-and-writer}

Das folgende Einführungsschema beschreibt den Austausch auf niedriger Ebene zwischen Datenbank und Kunde (Web-Seiten oder Adobe Campaign-Client-Konsole) zum Lesen (ExecuteQuery) und Schreiben (Writer).

![](assets/s_ncs_integration_webservices_schema_writer.png)

### ExecuteQuery {#executequery}

Für Spalten und Bedingungen können Sie Abfragen verwenden.

Auf diese Weise können Sie die zugrunde liegende SQL isolieren. Die Abfragesprache hängt nicht von der zugrunde liegenden Engine ab: Einige Funktionen werden neu zugeordnet, was mehrere SELECT SQL-Bestellungen erzeugen kann.

Weitere Informationen hierzu finden Sie unter [Beispiel zur Methode „ExecuteQuery“ des Schemas „xtk:queryDef“](../../configuration/using/web-service-calls.md#example-on-the--executequery--method-of-schema--xtk-querydef-).

Die **ExecuteQuery**-Methode wird in &quot;[ExecuteQuery (xtk:queryDef)“ ](#executequery--xtk-querydef-).

### Schreiben {#write}

Mit Write-Befehlen können Sie einfache oder komplexe Dokumente mit Einträgen in einer oder mehreren Tabellen der Basis schreiben.

Mit Transaktions-APIs können Sie Abstimmungen über den Befehl **updateOrInsert** verwalten: Mit einem Befehl können Sie Daten erstellen oder aktualisieren. Sie können auch die Änderungszusammenführung konfigurieren **merge**: In diesem Betriebsmodus können Sie partielle Aktualisierungen genehmigen.

Die XML-Struktur bietet eine logische Ansicht der Daten und ermöglicht es Ihnen, die physische Struktur der SQL-Tabelle zu umgehen.

Die Write-Methode wird in [Write/WriteCollection (xtk:session) ](#write---writecollection--xtk-session-).

## ExecuteQuery (xtk:queryDef) {#executequery--xtk-querydef-}

Mit dieser Methode können Sie Abfragen aus Daten durchführen, die mit einem Schema verknüpft sind. Dazu sind eine Authentifizierungszeichenfolge (muss angemeldet sein) und ein XML-Dokument erforderlich, das die als Parameter zu sendende Abfrage beschreibt. Der Rückgabeparameter ist ein XML-Dokument, das das Ergebnis der Abfrage im Format des Schemas enthält, auf das sich die Abfrage bezieht.

Definition der Methode „ExecuteQuery“ im Schema „xtk:queryDef“:

```xml
<method name="ExecuteQuery" const="true">
  <parameters>
    <param desc="Output XML document" name="output" type="DOMDocument" inout="out"/>
  </parameters>
</method>
```

>[!NOTE]
>
>Dies ist eine „const“-Methode. Die Eingabeparameter sind in einem XML-Dokument im Format des Schemas „xtk:queryDef“ enthalten.

### Format des XML-Dokuments der Eingabeabfrage {#format-of-the-xml-document-of-the-input-query}

Die Struktur des XML-Dokuments der Abfrage wird im Schema „xtk:queryDef &quot; beschrieben. Dieses Dokument beschreibt die Klauseln einer SQL-Abfrage: „select“, „where“, „order by“, „group by“, „have“.

```xml
<queryDef schema="schema_key" operation="operation_type">
  <select>
    <node expr="expression1">
    <node expr="expression2">
    ...
  </select>
  <where> 
    <condition expr="expression1"/> 
    <condition expr="expression2"/>
    ... 
  </where>
  <orderBy>
    <node expr="expression1">
    <node expr="expression2">
    ...
  </orderBy>
  <groupBy>
    <node expr="expression1">
    <node expr="expression2">
    ...
  </groupBy>
  <having>
    <condition expr="expression1"/> 
    <condition expr="expression2"/>
    ...
  </having>
</queryDef>
```

Eine Unterabfrage ( `<subquery>` ) kann in einem `<condition> ` definiert werden. Die Syntax für ein   `<subquery> `   -Element basiert auf der Syntax eines    `<querydef>`.

Beispiel einer `<subquery>  : </subquery>`

```xml
<condition setOperator="NOT IN" expr="@id" enabledIf="$(/ignored/@ownerType)=1">
  <subQuery schema="xtk:operatorGroup">
     <select>
       <node expr="[@operator-id]" />
     </select>
     <where>
       <condition expr="[@group-id]=$long(../@owner-id)"/>
     </where>
   </subQuery>
</condition>  
  
```

Eine Abfrage muss ausgehend vom Attribut **schema“ auf** Startschema verweisen.

Der gewünschte Vorgangstyp wird im Attribut **operation** eingegeben und enthält einen der folgenden Werte:

* **GET**: ruft einen Datensatz aus der Tabelle ab und gibt einen Fehler zurück, wenn die Daten nicht vorhanden sind.
* **getIfExists**: Ruft einen Datensatz aus der Tabelle ab und gibt ein leeres Dokument zurück, wenn die Daten nicht vorhanden sind.
* **Auswählen**: erstellt einen Cursor, der mehrere Datensätze zurückgibt, und gibt ein leeres Dokument zurück, wenn keine Daten vorhanden sind,
* **count**: Gibt eine Anzahl von Daten zurück.

Die **XPath**-Syntax wird verwendet, um Daten basierend auf dem Eingabeschema zu finden. Weitere Informationen zu XPaths finden Sie unter [Datenschemata](../../configuration/using/data-schemas.md).

#### Beispiel mit dem Vorgang „get“ {#example-with-the--get--operation}

Ruft den Vor- und Nachnamen eines Empfängers (Schema „nms:recipient„) mit einem E-Mail-Filter ab.

```xml
<queryDef schema="nms:recipient" operation="get">
  <!-- fields to retrieve -->
  <select>
    <node expr="@firstName"/>
    <node expr="@lastName"/>
  </select> 

  <!-- condition on email -->
  <where>  
    <condition expr="@email= 'john.doe@aol.com'"/>
  </where>
</queryDef>
```

#### Beispiel mit dem Vorgang „select“ {#example-with-the--select--operation}

Gibt die Liste der Empfänger zurück, die nach Ordner und E-Mail-Domain gefiltert wurden, wobei am Geburtsdatum eine Sortierung in absteigender Reihenfolge erfolgt.

```xml
<queryDef schema="nms:recipient" operation="select">
  <select>
    <node expr="@email"/>
    <!-- builds a string with the concatenation of the last name and first name separated by a dash -->      
    <node expr="@lastName+'-'+@firstName"/>
    <!-- get year of birth date -->
    <node expr="Year(@birthDate)"/>
  </select> 

  <where>  
     <condition expr="[@folder-id] = 1234 and @domain like 'Adobe%'"/>
  </where>

  <!-- order by birth date -->
  <orderBy>
    <node expr="@birthDate" sortDesc="true"/> <!-- by default sortDesc="false" -->
  </orderBy>
</queryDef>
```

Ausdrücke können einfache Felder oder komplexe Ausdrücke wie arithmetische Operationen oder die Verkettung von Zeichenfolgen sein.

Um die Anzahl der zurückzugebenden Datensätze zu begrenzen, fügen Sie dem `<querydef>`-Element **Attribut** lineCount) hinzu.

So begrenzen Sie die Anzahl der von der Abfrage zurückgegebenen Datensätze auf 100:

```xml
<queryDef schema="nms:recipient" operation="select" lineCount="100">
...
```

Um die nächsten 100 Datensätze abzurufen, führen Sie dieselbe Abfrage erneut aus und fügen Sie das Attribut **startLine** hinzu.

```xml
<queryDef schema="nms:recipient" operation="select" lineCount="100" startLine="100">
...
```

#### Beispiel mit dem Vorgang „count“ {#example-with-the--count--operation}

So zählen Sie die Anzahl der Datensätze in einer Abfrage:

```xml
<queryDef schema="nms:recipient" operation="count"">
  <!-- condition on the folder and domain of the email -->
  <where>  
    <condition expr="[@folder-id] = 1234" and @domain like 'Adobe%'"/>
  </where>
</queryDef>
```

>[!NOTE]
>
>Auch hier verwenden wir die Bedingung aus dem vorherigen Beispiel. Die `<select>` und -Klauseln werden nicht verwendet. `</select>`

#### Datengruppierung {#data-grouping}

So rufen Sie E-Mail-Adressen ab, auf die mehrmals verwiesen wird:

```xml
<queryDef schema="nms:recipient" operation="select">
  <select>
    <node expr="@email"/>
    <node expr="count(@email)"/>
  </select>

  <!-- email grouping clause -->
  <groupby>
    <node expr="@email"/>
  </groupby>

  <!-- grouping condition -->
  <having>
    <condition expr="count(@email) > 1"/>
  </having>

</queryDef>
```

Die Abfrage kann vereinfacht werden, indem das Attribut **groupBy** direkt zu dem zu gruppierenden Feld hinzugefügt wird:

```xml
<select>
  <node expr="@email" groupBy="true"/>
</select>
```

>[!NOTE]
>
>Es ist nicht mehr erforderlich, das `<groupby>`-Element auszufüllen.

#### Einklammern in Bedingungen {#bracketing-in-conditions}

Im Folgenden finden Sie zwei Beispiele für Klammern in derselben Bedingung.

* Die einfache Version in einem einzigen Ausdruck:

  ```xml
  <where>
    <condition expr="(@age > 15 or @age <= 45) and  (@city = 'Newton' or @city = 'Culver City') "/>
  </where>
  ```

* Die strukturierte Version mit `<condition>` Elementen:

  ```xml
  <where>
    <condition bool-operator="AND">
      <condition expr="@age > 15" bool-operator="OR"/>
      <condition expr="@age <= 45"/>
    </condition>
    <condition>
      <condition expr="@city = 'Newton'" bool-operator="OR"/>
      <condition expr="@city = 'Culver City'"/>
    </condition>
  </where>
  ```

Es ist möglich, den Operator „OR“ durch den Vorgang „IN“ zu ersetzen, wenn mehrere Bedingungen für dasselbe Feld gelten:

```xml
<where>
  <condition>
    <condition expr="@age IN (15, 45)"/>
    <condition expr="@city IN ('Newton', 'Culver City')"/>
  </condition>
</where>
```

Diese Syntax vereinfacht die Abfrage, wenn mehr als zwei Daten in der Bedingung verwendet werden.

#### Beispiele für Links {#examples-on-links}

* Relationen 1-1 oder N1: Wenn die Tabelle den Fremdschlüssel hat (der Link beginnt in der Tabelle), können die Felder der verknüpften Tabelle gefiltert oder direkt abgerufen werden.

  Beispiel für einen Filter auf der Ordnerbeschriftung:

  ```xml
  <where>
    <condition expr="[folder/@label] like 'Segment%'"/>
  </where>
  ```

  Abrufen der Felder des Ordners aus dem Schema „nms:recipient“:

  ```xml
  <select>
    <!-- label of recipient folder -->
    <node expr="[folder/@label]"/>
    <!-- displays the string count of the folder -->
    <node expr="partition"/>
  </select>
  ```

* Sammlungsrelationen (1N): Die Filterung der Felder einer Sammlungstabelle muss über den Operator **EXISTS** oder **NOT EXISTS** erfolgen.

  So filtern Sie die Empfänger, die sich für den Informationsdienst „Newsletter“ angemeldet haben:

  ```xml
  <where>
    <condition expr="subscription" setOperator="EXISTS">
      <condition expr="@name = 'Newsletter'"/>
    </condition>
  </where>
  ```

  Der direkte Abruf der Felder einer Sammlungsrelation aus der `<select>`-Klausel wird nicht empfohlen, da die Abfrage ein Kardinalprodukt zurückgibt. Sie wird nur verwendet, wenn die verknüpfte Tabelle nur einen Datensatz enthält (Beispiel `<node expr="">`).

  Beispiel für den Sammlungslink „Abonnement“:

  ```xml
  <select>
    <node expr="subscription/@label"/>
  </select>
  ```

  Es ist möglich, eine Unterliste abzurufen, die die Elemente einer Sammlungsrelation in der `<select>`-Klausel enthält. Die XPaths der referenzierten Felder sind kontextuell aus dem Sammlungselement.

  Die Filterelemente ( `<orderby>` ) und Einschränkungselemente ( `<where>` ) können dem Sammlungselement hinzugefügt werden.

  In diesem Beispiel gibt die Abfrage für jeden Empfänger die E-Mail-Adresse und eine Liste der Informationsdienste zurück, die der Empfänger abonniert:

  ```xml
  <queryDef schema="nms:recipient" operation="select">
    <select>
      <node expr="@email"/>
  
      <!-- collection table (unbound type) -->
      <node expr="subscription">  
        <node expr="[service/@label]"/>    
        <!-- sub-condition on the collection table -->
        <where>  
          <condition expr="@expirationDate >= GetDate()"/>
        </where>
        <orderBy>
          <node expr="@expirationDate"/> 
        </orderBy>
      </node>
    </select> 
  </queryDef>
  ```

#### Binden der Parameter der WHERE- und SELECT-Klausel {#binding-the-parameters-of-the--where--and--select--clause}

Durch die Parameterbindung kann die Engine die Werte der in der Abfrage verwendeten Parameter festlegen. Dies ist sehr nützlich, da die Engine für das Maskieren von Werten zuständig ist und es den zusätzlichen Vorteil eines Cache für die abzurufenden Parameter gibt.

Wenn eine Abfrage erstellt wird, werden die „gebundenen“ Werte durch das Zeichen (? `#[index]#` Sie in ODBC in postgres…) im Hauptteil der SQL-Abfrage.

```xml
<select>
  <!--the value will be bound by the engine -->
  <node expr="@startDate = #2002/02/01#"/>                   
  <!-- the value will not be bound by the engine but visible directly in the query -->
  <node expr="@startDate = #2002/02/01#" noSqlBind="true"/> 
</select>
```

Um die Bindung eines Parameters zu vermeiden, muss das Attribut „noSqlBind“ mit dem Wert „true“ ausgefüllt werden.

>[!IMPORTANT]
>
>Wenn die Abfrage „order-by“- oder „group-by“-Anweisungen enthält, können die Datenbank-Engines keine Werte „binden“. Sie müssen das Attribut @noSqlBind=„true“ auf den „select“- und/oder „where“-Anweisungen der Abfrage platzieren.


### Format des Ausgabedokuments {#output-document-format}

Der Rückgabeparameter ist ein XML-Dokument im Format des Schemas, das mit der Abfrage verknüpft ist.

Beispiel für eine Rückgabe aus dem Schema „nms:recipient“ über einen „get“-Vorgang:

```
<recipient email="john.doe@adobe.com" lastName"Doe" firstName="John"/>
```

Bei einem „select“-Vorgang ist das zurückgegebene Dokument eine Auflistung von Elementen:

```xml
<!-- the name of the first element does not matter -->
<recipient-collection>   
  <recipient email="john.doe@adobe.com" lastName"Doe" firstName="John"/>
  <recipient email="peter.martinez@adobe.com" lastName"Martinez" firstName="Peter"/>
  <recipient...
</recipient-collection>  
```

Beispiel eines Dokuments, das für einen Vorgang vom Typ „count“ zurückgegeben wird:

```xml
<recipient count="3"/>
```

#### Alias {#alias}

Mit einem Alias können Sie den Speicherort von Daten im Ausgabedokument ändern. Das **alias**-Attribut muss einen XPath für das entsprechende Feld angeben.

```xml
<queryDef schema="nms:recipient" operation="get">
  <select>
    <node expr="@firstName" alias="@firstName"/>
    <node expr="@lastName"/>
    <node expr="[folder/@label]" alias="@My_folder"/>
  </select> 
</queryDef>
```

Gibt zurück:

```xml
<recipient My_folder="Recipients" First name ="John" lastName="Doe"/>
```

anstelle von:

```xml
<recipient firstName="John" lastName="Doe">
  <folder label="Recipients"/>
</recipient>
```

### Beispiel für SOAP-Nachrichten {#example-of-soap-messages}

* Abfrage:

  ```xml
  <?xml version='1.0' encoding='ISO-8859-1'?>
  <SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:ns='http://xml.apache.org/xml-soap' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
    <SOAP-ENV:Body>
      <ExecuteQuery xmlns='urn:xtk:queryDef' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
        <__sessiontoken xsi:type='xsd:string'/>
        <entity xsi:type='ns:Element' SOAP-ENV:encodingStyle='http://xml.apache.org/xml-soap/literalxml'>
          <queryDef operation="get" schema="nms:recipient" xtkschema="xtk:queryDef">
            <select>
              <node expr="@email"/>
              <node expr="@lastName"/>
              <node expr="@firstName"/>
            </select>
            <where>
              <condition expr="@id = 3599"/>
            </where>
          </queryDef>
        </entity>
      </ExecuteQuery>
    </SOAP-ENV:Body>
  </SOAP-ENV:Envelope>
  ```

* Antwort:

  ```xml
  <?xml version='1.0' encoding='ISO-8859-1'?>
  <SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:ns='http://xml.apache.org/xml-soap' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
    <SOAP-ENV:Body>
      <ExecuteQueryResponse xmlns='urn:xtk:queryDef' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
        <pdomOutput xsi:type='ns:Element' SOAP-ENV:encodingStyle='http://xml.apache.org/xml-soap/literalxml'>
          <recipient email="john.doe@adobe.com" lastName"Doe" firstName="John"/>
        </pdomOutput>
      </ExecuteQueryResponse>
    </SOAP-ENV:Body>
  </SOAP-ENV:Envelope>
  ```

## Write/WriteCollection (xtk:session) {#write---writecollection--xtk-session-}

Diese Dienste werden verwendet, um eine Entität („Write“-Methode) oder eine Auflistung von Entitäten („WriteCollection“-Methode) einzufügen, zu aktualisieren oder zu löschen.

Die zu aktualisierenden Entitäten sind mit einem Datenschema verknüpft. Die Eingabeparameter sind eine Authentifizierungszeichenfolge (muss angemeldet sein) und ein XML-Dokument mit den zu aktualisierenden Daten.

Dieses Dokument wird durch Anweisungen zum Konfigurieren der Schreibvorgänge ergänzt.

Der Aufruf gibt keine Daten zurück, mit Ausnahme von Fehlern.

Definition der Methoden „Write“ und „WriteCollection“ im Schema „xtk:session“:

```xml
<method name="Write" static="true">
  <parameters>
    <param name="doc" type="DOMDocument" desc="Difference document"/>
  </parameters>
</method>
<method name="WriteCollection" static="true">
  <parameters>
    <param name="doc" type="DOMDocument" desc="Difference collection document"/>
  </parameters>
</method>
```

>[!NOTE]
>
>Dies ist eine „statische“ Methode. Die Eingabeparameter sind in einem XML-Dokument im Format des zu aktualisierenden Schemas enthalten.

### Übersicht {#overview}

Die Datenabstimmung basiert auf der Definition der Schlüssel, die in das verknüpfte Schema eingegeben wurden. Beim Schreibvorgang wird basierend auf den im Eingabedokument eingegebenen Daten nach dem ersten qualifizierten Schlüssel gesucht. Die Entität wird eingefügt oder aktualisiert, je nachdem, ob sie in der Datenbank vorhanden ist.

Der Schlüssel des Schemas der zu aktualisierenden Entität wird anhand des Attributs **xtkschema** abgeschlossen.

Der Abstimmschlüssel kann daher mit dem Attribut **_key** erzwungen werden, das die Liste der XPaths enthält, aus denen der Schlüssel besteht (durch Kommas getrennt).

Es ist möglich, den Vorgangstyp zu erzwingen, indem das Attribut **_operation** mit den folgenden Werten ausgefüllt wird:

* **insert**: erzwingt das Einfügen des Datensatzes (der Abstimmschlüssel wird nicht verwendet),
* **insertOrUpdate**: aktualisiert oder fügt den Datensatz in Abhängigkeit vom Abstimmschlüssel ein (Standardmodus).
* **Aktualisieren**: aktualisiert den Datensatz; hat keine Auswirkung, wenn die Daten nicht vorhanden sind,
* **delete**: löscht die Datensätze,
* **none**: Wird nur für die Link-Abstimmung ohne Aktualisierung oder Einfügen verwendet.

### Beispiel mit der „Write“-Methode {#example-with-the--write--method}

Aktualisieren oder Einfügen eines Empfängers (impliziter Vorgang „insertOrUpdate„) mit E-Mail-Adresse, Geburtsdatum und Stadt:

```xml
<recipient xtkschema="nms:recipient" email="john.doe@adobe.com" birthDate="1956/05/04" folder-id=1203 _key="@email, [@folder-id]">
  <location city="Newton"/>
</recipient>
```

Empfänger wird gelöscht:

```xml
<recipient xtkschema="nms:recipient" _operation="delete" email="rene.dupont@adobe.com" folder-id=1203 _key="@email, [@folder-id]"/>
```

>[!NOTE]
>
>Bei einem Löschvorgang darf das Eingabedokument nur die Felder enthalten, aus denen der Abstimmschlüssel besteht.

### Beispiel mit der „WriteCollection“-Methode {#example-with-the--writecollection--method}

Für mehrere Empfänger aktualisieren oder einfügen:

```xml
<recipient-collection xtkschema="nms:recipient">    
  <recipient email="john.doe@adobe.com" firstName="John" lastName="Doe" _key="@email"/>
  <recipient email="peter.martinez@adobe.com" firstName="Peter" lastName="Martinez" _key="@email"/>
  <recipient ...
</recipient-collection>
```

### Beispiel für Links {#example-on-links}

#### Beispiel 1 {#example-1}

Verknüpfen des Ordners mit einem Empfänger auf Grundlage seines internen Namens (@name).

```xml
<recipient _key="[folder/@name], @email" email="john.doe@adobe.net" lastName="Doe" firstName="John" xtkschema="nms:recipient">
  <folder name="Folder2" _operation="none"/>
</recipient>
```

Die Attribute „_key“ und „_operation“ können für ein verknüpftes Element eingegeben werden. Das Verhalten in diesem Element ist dasselbe wie im Hauptelement des Eingabeschemas.

Die Definition des Schlüssels der Hauptentität („nms:recipient„) besteht aus einem Feld einer verknüpften Tabelle (Element `<folder>` Schema „xtk:folder„) und der E-Mail.

>[!NOTE]
>
>Der Vorgang „none“, der für das Ordnerelement eingegeben wurde, definiert eine Abstimmung für den Ordner ohne Aktualisierung oder Einfügen.

#### Beispiel 2 {#example-2}

Aktualisieren des Unternehmens (verknüpfte Tabelle im Schema „cus:company„) von einem Empfänger:

```xml
<recipient _key="[folder/@name], @email" email="john.doe@adobe.net" lastName="Doe" firstName="John" xtkschema="nms:recipient">
  <company name="adobe" code="ERT12T" _key="@name" _operation="update"/>
</recipient>
```

#### Beispiel 3 {#example-3}

Hinzufügen eines Empfängers zu einer Gruppe mit der Gruppenbeziehungstabelle („nms:rcpGrpRel„):

```xml
<recipient _key="@email" email="martin.ledger@adobe.net" xtkschema="nms:recipient">
  <rcpGrpRel _key="[rcpGroup/@name]">
    <rcpGroup name="GRP1"/>
  </rcpGrpRel>
</recipient>
```

>[!NOTE]
>
>Die Definition des Schlüssels wird nicht im `<rcpgroup>`-Element eingegeben, da im Schema „nms:group“ ein impliziter Schlüssel definiert ist, der auf dem Gruppennamen basiert.

### XML-Sammlungselemente {#xml-collection-elements}

Standardmäßig müssen alle Sammlungselemente gefüllt werden, damit die XML-Sammlungselemente aktualisiert werden können. Daten aus der Datenbank werden durch Daten aus dem Eingabedokument ersetzt. Wenn das Dokument nur die zu aktualisierenden Elemente enthält, müssen Sie das Attribut „_operation“ für alle zu aktualisierenden Sammlungselemente ausfüllen, um eine Zusammenführung mit den XML-Daten der Datenbank zu erzwingen.

### Beispiel für SOAP-Nachrichten {#example-of-soap-messages-1}

* Abfrage:

  ```xml
  <?xml version='1.0' encoding='ISO-8859-1'?>
  <SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:ns='http://xml.apache.org/xml-soap' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
    <SOAP-ENV:Body>
      <Write xmlns='urn:xtk:persist' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
        <__sessiontoken xsi:type='xsd:string'/>
        <domDoc xsi:type='ns:Element' SOAP-ENV:encodingStyle='http://xml.apache.org/xml-soap/literalxml'>
          <recipient xtkschema="nms:recipient" email="rene.dupont@adobe.com" firstName="René" lastName="Dupont" _key="@email">
        </domDoc>
      </Write>
    </SOAP-ENV:Body>
  </SOAP-ENV:Envelope>
  ```

* Antwort:

  ```xml
  <?xml version='1.0' encoding='ISO-8859-1'?>
  <SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:ns='http://xml.apache.org/xml-soap' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
    <SOAP-ENV:Body>
      <WriteResponse xmlns='urn:' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
      </WriteResponse>
    </SOAP-ENV:Body>
  </SOAP-ENV:Envelope>
  ```

  Rückgabe mit Fehler:

  ```xml
  <?xml version='1.0'?>
  <SOAP-ENV:Envelope xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
    <SOAP-ENV:Body>
      <SOAP-ENV:Fault>
        <faultcode>SOAP-ENV:Server</faultcode>
        <faultstring xsi:type="xsd:string">Error while executing the method 'Write' of service 'xtk:persist'.</faultstring>
        <detail xsi:type="xsd:string">PostgreSQL error: ERROR:  duplicate key violates unique constraint &quot;nmsrecipient_id&quot;Impossible to save document of type 'Recipients (nms:recipient)'</detail>
      </SOAP-ENV:Fault>
    </SOAP-ENV:Body>
  </SOAP-ENV:Envelope>
  ```
