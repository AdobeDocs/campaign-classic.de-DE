---
product: campaign
title: Datenorientierte APIs
description: Datenorientierte APIs
audience: configuration
content-type: reference
topic-tags: api
exl-id: a392c55e-541a-40b1-a910-4a6dc79abd2d
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1885'
ht-degree: 1%

---

# Datenorientierte APIs{#data-oriented-apis}

![](../../assets/v7-only.svg)

Datenorientierte APIs ermöglichen es Ihnen, das gesamte Datenmodell anzusprechen.

## Übersicht über das Datenmodell {#overview-of-the-datamodel}

Adobe Campaign bietet keine dedizierte Lese-API pro Entität (keine getRecipient- oder getDelivery-Funktion usw.). Verwenden Sie die Lese- und Änderungsmethoden für die Daten von QUERY &amp; WRITER , um auf die Daten des Modells zuzugreifen.

Mit Adobe Campaign können Sie Sammlungen verwalten: -Abfragen ermöglichen die Wiederherstellung einer Reihe von Informationen, die auf der Basis gesammelt wurden. Im Gegensatz zum Zugriff im SQL-Modus geben Adobe Campaign-APIs eine XML-Baumstruktur anstelle von Datenspalten zurück. Adobe Campaign erstellt so zusammengesetzte Dokumente mit allen erfassten Daten.

Dieser Betriebsmodus bietet keine Eins-zu-Eins-Zuordnung zwischen den Attributen und Elementen der XML-Dokumente und den Spalten der Tabellen in der Datenbank.

XML-Dokumente werden in Feldern vom Typ MEMO der Datenbank gespeichert.

## Beschreibung des Modells {#description-of-the-model}

Sie müssen mit dem Adobe Campaign-Datenmodell vertraut sein, um die Datenbankfelder in Ihren Skripten ansprechen zu können.

Eine Darstellung des Datenmodells finden Sie im Abschnitt [Beschreibung des Adobe Campaign-Datenmodells](../../configuration/using/data-model-description.md).

Informationen zum Generieren der Struktur finden Sie in diesem Artikel: [Generieren eines Datenmodells oder eines Datenwörterbuchs](https://helpx.adobe.com/campaign/kb/generate-data-model.html).

## Abfrage und Writer {#query-and-writer}

Das folgende Einführungsschema beschreibt den Austausch auf niedriger Ebene zum Lesen (ExecuteQuery) und Schreiben (Writer) zwischen Datenbank und Kunde (Webseiten oder Adobe Campaign-Clientkonsole).

![](assets/s_ncs_integration_webservices_schema_writer.png)

### ExecuteQuery {#executequery}

Für Spalten und Bedingungen können Sie Abfragen verwenden.

Auf diese Weise können Sie die zugrunde liegende SQL isolieren. Die Abfragesprache hängt nicht von der zugrunde liegenden Engine ab: Einige Funktionen werden neu zugeordnet, was mehrere SELECT SQL-Bestellungen generieren kann.

Weitere Informationen hierzu finden Sie unter [Beispiel für die Methode &#39;ExecuteQuery&#39; des Schemas &#39;xtk:queryDef&#39;](../../configuration/using/web-service-calls.md#example-on-the--executequery--method-of-schema--xtk-querydef-).

Die **ExecuteQuery** -Methode wird in [ExecuteQuery (xtk:queryDef)](#executequery--xtk-querydef-).

### Schreiben {#write}

Mit Schreibbefehlen können Sie einfache oder komplexe Dokumente mit Einträgen in einer oder mehreren Tabellen der Basis schreiben.

Mit Transaktions-APIs können Sie Abstimmungen über das **updateOrInsert** command: Mit einem Befehl können Sie Daten erstellen oder aktualisieren. Sie können auch die Änderungszusammenführung konfigurieren (**merge**): In diesem Betriebsmodus können Sie Teilaktualisierungen zulassen.

Die XML-Struktur bietet eine logische Ansicht der Daten und ermöglicht es Ihnen, die physische Struktur der SQL-Tabelle zu umgehen.

Die Write-Methode wird im Abschnitt [Write/WriteCollection (xtk:session)](#write---writecollection--xtk-session-).

## ExecuteQuery (xtk:queryDef) {#executequery--xtk-querydef-}

Auf diese Weise können Sie Abfragen aus Daten durchführen, die mit einem Schema verknüpft sind. Es benötigt eine Authentifizierungszeichenfolge (muss angemeldet sein) und ein XML-Dokument, das die als Parameter zu übermittelnde Abfrage beschreibt. Der Parameter return ist ein XML-Dokument, das das Ergebnis der Abfrage im Format des Schemas enthält, auf das sich die Abfrage bezieht.

Definition der Methode &quot;ExecuteQuery&quot;im Schema &quot;xtk:queryDef&quot;:

```
<method name="ExecuteQuery" const="true">
  <parameters>
    <param desc="Output XML document" name="output" type="DOMDocument" inout="out"/>
  </parameters>
</method>
```

>[!NOTE]
>
>Dies ist eine &quot;const&quot;-Methode. Die Eingabeparameter sind in einem XML-Dokument im Format des Schemas &quot;xtk:queryDef&quot; enthalten.

### Format des XML-Dokuments der Eingabeabfrage {#format-of-the-xml-document-of-the-input-query}

Die Struktur des XML-Dokuments der Abfrage wird im Schema &quot;xtk:queryDef &quot; beschrieben. In diesem Dokument werden die Klauseln einer SQL-Abfrage beschrieben: &quot;select&quot;, &quot;where&quot;, &quot;order by&quot;, &quot;group by&quot;, &quot;having&quot;.

```
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

Eine Unterabfrage ( `<subquery>`  ) in einer  `<condition> `  -Element. Die Syntax für eine   `<subquery> `   -Element basiert auf der Syntax eines    `<querydef>`.

Beispiel einer `<subquery>  : </subquery>`

```
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

Eine Abfrage muss auf ein Startschema aus dem **schema** -Attribut.

Der gewünschte Vorgangstyp wird im Feld **operation** -Attribut und enthält einen der folgenden Werte:

* **get**: ruft einen Datensatz aus der Tabelle ab und gibt einen Fehler zurück, wenn die Daten nicht vorhanden sind.
* **getIfExists**: Ruft einen Datensatz aus der Tabelle ab und gibt ein leeres Dokument zurück, wenn die Daten nicht vorhanden sind;
* **select**: erstellt einen Cursor, um mehrere Datensätze zurückzugeben, und gibt ein leeres Dokument zurück, wenn keine Daten vorhanden sind;
* **count**: gibt eine Datenanzahl zurück.

Die **XPath** -Syntax verwendet wird, um Daten basierend auf dem Eingabeschema zu suchen. Weitere Informationen zu XPaths finden Sie unter [Datenschemata](../../configuration/using/data-schemas.md).

#### Beispiel mit dem &quot;get&quot;-Vorgang {#example-with-the--get--operation}

Ruft den Vor- und Nachnamen eines Empfängers ( Schema &quot;nms:recipient&quot;) mit einem Filter für die E-Mail ab.

```
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

#### Beispiel mit dem Vorgang &quot;select&quot; {#example-with-the--select--operation}

Gibt die Liste der Empfänger zurück, die nach einem Ordner gefiltert wurden, sowie die E-Mail-Domain, deren Sortierung am Geburtsdatum in absteigender Reihenfolge erfolgt.

```
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

Ausdrücke können einfache Felder oder komplexe Ausdrücke sein, wie arithmetische Vorgänge oder die Verkettung von Zeichenfolgen.

Um die Anzahl der zurückzugebenden Datensätze zu begrenzen, fügen Sie die **lineCount** -Attribut `<querydef>` -Element.

So begrenzen Sie die Anzahl der von der Abfrage zurückgegebenen Datensätze auf 100:

```
<queryDef schema="nms:recipient" operation="select" lineCount="100">
...
```

Um die nächsten 100 Datensätze abzurufen, führen Sie dieselbe Abfrage erneut aus und fügen Sie die **startLine** -Attribut.

```
<queryDef schema="nms:recipient" operation="select" lineCount="100" startLine="100">
...
```

#### Beispiel mit dem Vorgang &quot;count&quot; {#example-with-the--count--operation}

So zählen Sie die Anzahl an Datensätzen in einer Abfrage:

```
<queryDef schema="nms:recipient" operation="count"">
  <!-- condition on the folder and domain of the e-mail -->
  <where>  
    <condition expr="[@folder-id] = 1234" and @domain like 'Adobe%'"/>
  </where>
</queryDef>
```

>[!NOTE]
>
>Auch hier verwenden wir die Bedingung aus dem vorherigen Beispiel. Die `<select>` und -Klauseln nicht verwendet werden. `</select>`

#### Nach welchen Kriterien werden die Daten gruppiert {#data-grouping}

So rufen Sie E-Mail-Adressen ab, auf die mehrmals verwiesen wird:

```
<queryDef schema="nms:recipient" operation="select">
  <select>
    <node expr="@email"/>
    <node expr="count(@email)"/>
  </select>

  <!-- e-mail grouping clause -->
  <groupby>
    <node expr="@email"/>
  </groupby>

  <!-- grouping condition -->
  <having>
    <condition expr="count(@email) > 1"/>
  </having>

</queryDef>
```

Die Abfrage kann durch Hinzufügen der **groupBy** direkt dem zu gruppierenden Feld zuordnen:

```
<select>
  <node expr="@email" groupBy="true"/>
</select>
```

>[!NOTE]
>
>Es ist nicht mehr erforderlich, die `<groupby>` -Element.

#### Bremsung unter Bedingungen {#bracketing-in-conditions}

Im Folgenden finden Sie zwei Beispiele für die Verwendung von Klammern für dieselbe Bedingung.

* Die einfache Version in einem einzelnen Ausdruck:

   ```
   <where>
     <condition expr="(@age > 15 or @age <= 45) and  (@city = 'Newton' or @city = 'Culver City') "/>
   </where>
   ```

* Die strukturierte Version mit `<condition>` -Elemente:

   ```
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

Der Operator &quot;OR&quot;kann durch den Vorgang &quot;IN&quot;ersetzt werden, wenn mehrere Bedingungen für dasselbe Feld gelten:

```
<where>
  <condition>
    <condition expr="@age IN (15, 45)"/>
    <condition expr="@city IN ('Newton', 'Culver City')"/>
  </condition>
</where>
```

Diese Syntax vereinfacht die Abfrage, wenn mehr als zwei Daten in der Bedingung verwendet werden.

#### Beispiele für Links {#examples-on-links}

* Links 1-1 oder N1: Wenn die Tabelle über den Fremdschlüssel verfügt (der Link beginnt in der Tabelle), können die Felder der verknüpften Tabelle gefiltert oder direkt abgerufen werden.

   Beispiel eines Filters für die Ordnername:

   ```
   <where>
     <condition expr="[folder/@label] like 'Segment%'"/>
   </where>
   ```

   So rufen Sie die Felder des Ordners aus dem Schema &quot;nms:recipient&quot;ab:

   ```
   <select>
     <!-- label of recipient folder -->
     <node expr="[folder/@label]"/>
     <!-- displays the string count of the folder -->
     <node expr="partition"/>
   </select>
   ```

* Sammlungslinks (1N): Die Filterung der Felder einer Kollektionstabelle muss über die **VORHANDEN** oder **NICHT VORHANDEN** Operator.

   So filtern Sie die Empfänger, die den Informationsdienst &#39;Newsletter&#39; abonniert haben:

   ```
   <where>
     <condition expr="subscription" setOperator="EXISTS">
       <condition expr="@name = 'Newsletter'"/>
     </condition>
   </where>
   ```

   Direkter Abruf der Felder eines Sammlungslinks aus dem `<select>` wird nicht empfohlen, da die Abfrage ein Kardinalprodukt zurückgibt. Sie wird nur verwendet, wenn die verknüpfte Tabelle nur einen Datensatz enthält (Beispiel `<node expr="">`).

   Beispiel für den Kollektionslink &quot;Abonnement&quot;:

   ```
   <select>
     <node expr="subscription/@label"/>
   </select>
   ```

   Es ist möglich, eine Unterliste abzurufen, die die Elemente eines Kollektions-Links im `<select>` -Klausel. Die XPaths der referenzierten Felder sind kontextuell aus dem Kollektionselement.

   Die Filterung ( `<orderby>`  ) und Einschränkungen (  `<where>`  ) können dem Kollektionselement hinzugefügt werden.

   In diesem Beispiel gibt die Abfrage für jeden Empfänger die E-Mail-Adresse und die Liste der Informationsdienste zurück, die der Empfänger abonniert:

   ```
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

#### Parameter der &#39;where&#39;- und &#39;select&#39;-Klausel binden {#binding-the-parameters-of-the--where--and--select--clause}

Durch die Bindung von Parametern kann die Engine die Werte der in der Abfrage verwendeten Parameter festlegen. Dies ist sehr nützlich, da die Engine für die Maskierung von Werten verantwortlich ist und es den zusätzlichen Vorteil eines Caches gibt, damit die Parameter abgerufen werden können.

Wenn eine Abfrage erstellt wird, werden die &quot;gebundenen&quot; Werte durch ein Zeichen (? in ODBC, `#[index]#` in postgres...) im Text der SQL-Abfrage.

```
<select>
  <!--the value will be bound by the engine -->
  <node expr="@startDate = #2002/02/01#"/>                   
  <!-- the value will not be bound by the engine but visible directly in the query -->
  <node expr="@startDate = #2002/02/01#" noSqlBind="true"/> 
</select>
```

Um das Binden eines Parameters zu vermeiden, muss das Attribut &quot;noSqlBind&quot;mit dem Wert &quot;true&quot;ausgefüllt werden.

>[!IMPORTANT]
>
>Wenn die Abfrage &quot;order-by&quot;- oder &quot;group-by&quot;-Anweisungen enthält, können die Datenbank-Engines keine Werte &quot;binden&quot;. Sie müssen das Attribut @noSqlBind=&quot;true&quot; in den Anweisungen &quot;select&quot; und/oder &quot;where&quot; der Abfrage platzieren.

#### Tipp zur Erstellung von Abfragen: {#query-building-tip-}

Um die Syntax einer Abfrage zu unterstützen, können Sie die Abfrage mit dem generischen Abfrageeditor in der Adobe Campaign-Clientkonsole ( **[!UICONTROL Tools/ Generischer Abfrageeditor...]** Menü). Gehen Sie dazu wie folgt vor:

1. Wählen Sie die abzurufenden Daten aus:

   ![](assets/s_ncs_integration_webservices_queyr1.png)

1. Definieren Sie die Filterbedingung:

   ![](assets/s_ncs_integration_webservices_queyr2.png)

1. Führen Sie die Abfrage aus und drücken Sie Strg+F4, um den Quellcode der Abfrage anzuzeigen.

   ![](assets/s_ncs_integration_webservices_queyr3.png)

### Output Document Format {#output-document-format}

Der Parameter return ist ein XML-Dokument im Format des Schemas, das der Abfrage zugeordnet ist.

Beispiel einer Rückgabe aus dem Schema &quot;nms:recipient&quot;bei einem &quot;get&quot;-Vorgang:

```
<recipient email="john.doe@adobe.com" lastName"Doe" firstName="John"/>
```

Bei einem &quot;select&quot;-Vorgang ist das zurückgegebene Dokument eine Auflistung von Elementen:

```
<!-- the name of the first element does not matter -->
<recipient-collection>   
  <recipient email="john.doe@adobe.com" lastName"Doe" firstName="John"/>
  <recipient email="peter.martinez@adobe.com" lastName"Martinez" firstName="Peter"/>
  <recipient...
</recipient-collection>  
```

Beispiel eines für den Vorgang vom Typ &quot;count&quot; zurückgegebenen Dokuments:

```
<recipient count="3"/>
```

#### Alias {#alias}

Mit einem Alias können Sie den Speicherort der Daten im Ausgabedokument ändern. Die **alias** -Attribut muss einen XPath für das entsprechende Feld angeben.

```
<queryDef schema="nms:recipient" operation="get">
  <select>
    <node expr="@firstName" alias="@firstName"/>
    <node expr="@lastName"/>
    <node expr="[folder/@label]" alias="@My_folder"/>
  </select> 
</queryDef>
```

Rückgabe:

```
<recipient My_folder="Recipients" First name ="John" lastName="Doe"/>
```

Statt:

```
<recipient firstName="John" lastName="Doe">
  <folder label="Recipients"/>
</recipient>
```

### Beispiel für SOAP-Nachrichten {#example-of-soap-messages}

* Abfrage:

   ```
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

   ```
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

Diese Dienste werden zum Einfügen, Aktualisieren oder Löschen einer Entität (&quot;Write&quot;-Methode) oder einer Sammlung von Entitäten (&quot;WriteCollection&quot;-Methode) verwendet.

Die zu aktualisierenden Entitäten sind mit einem Datenschema verknüpft. Die Eingabeparameter sind eine Authentifizierungszeichenfolge (muss angemeldet sein) und ein XML-Dokument, das die zu aktualisierenden Daten enthält.

Dieses Dokument wird durch Anweisungen zur Konfiguration der Schreibverfahren ergänzt.

Der Aufruf gibt außer Fehlern keine Daten zurück.

Definition der Methoden &quot;Write&quot;und &quot;WriteCollection&quot;im Schema &quot;xtk:session&quot;:

```
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
>Dies ist eine &quot;statische&quot;Methode. Die Eingabeparameter sind in einem XML-Dokument im Format des zu aktualisierenden Schemas enthalten.

### Überblick {#overview}

Die Abstimmung der Daten basiert auf der Definition der im zugehörigen Schema eingegebenen Schlüssel. Beim Schreiben wird basierend auf den im Eingabedokument eingegebenen Daten nach dem ersten geeigneten Schlüssel gesucht. Die Entität wird je nach ihrer Existenz in der Datenbank hinzugefügt oder aktualisiert.

Der Schlüssel des Schemas der zu aktualisierenden Entität wird basierend auf dem **xtkschema** -Attribut.

Der Abstimmschlüssel kann daher mit der **_key** -Attribut, das die Liste der XPaths enthält, aus denen der Schlüssel besteht (durch Kommas getrennt).

Es ist möglich, die Art des Vorgangs zu erzwingen, indem Sie die Variable **_operation** -Attribut mit den folgenden Werten verwenden:

* **insert**: erzwingt das Einfügen des Datensatzes (der Abstimmschlüssel wird nicht verwendet);
* **insertOrUpdate**: aktualisiert oder fügt den Datensatz je nach Abstimmschlüssel ein (Standardmodus),
* **update**: aktualisiert den Datensatz; nichts ausführt, wenn die Daten nicht vorhanden sind,
* **delete**: löscht die Datensätze,
* **Keine**: wird nur zur Abstimmung der Relationen verwendet, ohne Aktualisierung oder Einfügung.

### Beispiel mit der Methode &quot;Write&quot; {#example-with-the--write--method}

Aktualisieren oder Einfügen eines Empfängers (impliziter Vorgang &quot;insertOrUpdate&quot;) mit E-Mail-Adresse, Geburtsdatum und Ort:

```
<recipient xtkschema="nms:recipient" email="john.doe@adobe.com" birthDate="1956/05/04" folder-id=1203 _key="@email, [@folder-id]">
  <location city="Newton"/>
</recipient>
```

Empfänger löschen:

```
<recipient xtkschema="nms:recipient" _operation="delete" email="rene.dupont@adobe.com" folder-id=1203 _key="@email, [@folder-id]"/>
```

>[!NOTE]
>
>Bei einem Löschvorgang darf das Eingabedokument nur die Felder enthalten, aus denen der Abstimmschlüssel besteht.

### Beispiel mit der Methode &quot;WriteCollection&quot; {#example-with-the--writecollection--method}

Aktualisieren oder einfügen für mehrere Empfänger:

```
<recipient-collection xtkschema="nms:recipient">    
  <recipient email="john.doe@adobe.com" firstName="John" lastName="Doe" _key="@email"/>
  <recipient email="peter.martinez@adobe.com" firstName="Peter" lastName="Martinez" _key="@email"/>
  <recipient ...
</recipient-collection>
```

### Beispiel für Links {#example-on-links}

#### Beispiel 1 {#example-1}

Zuordnung des Ordners zu einem Empfänger basierend auf seinem internen Namen (@name).

```
<recipient _key="[folder/@name], @email" email="john.doe@adobe.net" lastName="Doe" firstName="John" xtkschema="nms:recipient">
  <folder name="Folder2" _operation="none"/>
</recipient>
```

Die Attribute &quot;_key&quot;und &quot;_operation&quot;können in einem verknüpften Element eingegeben werden. Das Verhalten dieses Elements ist mit dem des Hauptelements des Eingabeschemas identisch.

Die Definition des Schlüssels der Hauptentität (&quot;nms:recipient&quot;) besteht aus einem Feld einer verknüpften Tabelle (Element) `<folder>`  Schema &quot;xtk:folder&quot;) und der E-Mail.

>[!NOTE]
>
>Der im Ordnerelement eingegebene Vorgang &quot;none&quot; definiert eine Abstimmung im Ordner ohne Aktualisierung oder Einfügen.

#### Beispiel 2 {#example-2}

Aktualisieren des Unternehmens (verknüpfte Tabelle im Schema &quot;cus:Firma&quot;) von einem Empfänger:

```
<recipient _key="[folder/@name], @email" email="john.doe@adobe.net" lastName="Doe" firstName="John" xtkschema="nms:recipient">
  <company name="adobe" code="ERT12T" _key="@name" _operation="update"/>
</recipient>
```

#### Beispiel 3 {#example-3}

Hinzufügen eines Empfängers zu einer Gruppe mit der Gruppierungstabelle (&quot;nms:rcpGrpRel&quot;):

```
<recipient _key="@email" email="martin.ledger@adobe.net" xtkschema="nms:recipient">
  <rcpGrpRel _key="[rcpGroup/@name]">
    <rcpGroup name="GRP1"/>
  </rcpGrpRel>
</recipient>
```

>[!NOTE]
>
>Die Definition des Schlüssels wird nicht in der Variablen `<rcpgroup>` -Element, da ein auf dem Gruppennamen basierender impliziter Schlüssel im Schema &quot;nms:group&quot;definiert ist.

### XML-Kollektionselemente {#xml-collection-elements}

Standardmäßig müssen alle Kollektionselemente ausgefüllt werden, um die XML-Kollektionselemente zu aktualisieren. Daten aus der Datenbank werden durch Daten aus dem Eingabedokument ersetzt. Wenn das Dokument nur die zu aktualisierenden Elemente enthält, müssen Sie das Attribut &quot;_operation&quot;für alle zu aktualisierenden Kollektionselemente angeben, um eine Zusammenführung mit den XML-Daten der Datenbank zu erzwingen.

### Beispiel für SOAP-Nachrichten {#example-of-soap-messages-1}

* Abfrage:

   ```
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

   ```
   <?xml version='1.0' encoding='ISO-8859-1'?>
   <SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:ns='http://xml.apache.org/xml-soap' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
     <SOAP-ENV:Body>
       <WriteResponse xmlns='urn:' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
       </WriteResponse>
     </SOAP-ENV:Body>
   </SOAP-ENV:Envelope>
   ```

   Rückgabe mit Fehler:

   ```
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
