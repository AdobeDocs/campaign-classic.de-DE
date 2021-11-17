---
product: campaign
title: Beispiele für JavaScript-Code in Workflows
description: Diese Beispiele zeigen, wie Sie JavaScript-Code in einem Workflow verwenden können
audience: workflow
content-type: reference
topic-tags: advanced-management
source-git-commit: fa3a3e1801738928876734aa42342f0a5b49e320
workflow-type: tm+mt
source-wordcount: '1775'
ht-degree: 3%

---

# Beispiele für JavaScript-Code in Workflows{#javascript-in-workflows}

![](../../assets/common.svg)

Diese Beispiele zeigen, wie Sie JavaScript-Code in einem Workflow verwenden können:

* [In die Datenbank schreiben](#write-example)
* [Abfrage der Datenbank](#read-example)
* [Trigger eines Workflows mit einer statischen SOAP-Methode](#trigger-example)
* [Interagieren Sie mit der Datenbank mithilfe einer nicht statischen SOAP-Methode.](#interact-example)

[Weitere Infos](https://experienceleague.adobe.com/developer/campaign-api/api/p-14.html?lang=de) über statische und nicht statische SOAP-Methoden.

In diesen Beispielen wird die Erweiterung ECMAScript for XML (E4X) verwendet. Mit dieser Erweiterung können Sie JavaScript-Aufrufe und XML-Primitive im selben Skript kombinieren.

Gehen Sie wie folgt vor, um diese Beispiele auszuprobieren:

1. Erstellen Sie einen Workflow und fügen Sie dem Workflow diese Aktivitäten hinzu:
   1. Aktivität starten
   1. JavaScript-Code-Aktivität
   1. Endaktivität

   [Weitere Infos](building-a-workflow.md) über das Erstellen von Workflows.

1. Fügen Sie einer Aktivität den JavaScript-Code hinzu. [Weitere Informationen](advanced-parameters.md).
1. Speichern Sie den Workflow.
1. Testen Sie die Beispiele:
   1. Workflow starten. [Weitere Informationen](starting-a-workflow.md).
   1. Öffnen Sie das Journal. [Weitere Informationen](monitoring-workflow-execution.md#displaying-logs).

## Beispiel 1: in die Datenbank schreiben{#write-example}

Zum Schreiben in die Datenbank können Sie die statische `Write` -Methode `xtk:session` schema:

1. Erstellen Sie eine Schreibanforderung in XML.

1. Schreiben Sie den Datensatz:

   1. Rufen Sie die `Write` -Methode `xtk:session` Schema.

      >[!IMPORTANT]
      > Wenn Sie Adobe Campaign v8 verwenden, empfehlen wir, den Staging-Mechanismus mit dem **Aufnahme** und **Datenaktualisierung/-löschung** APIs für die `Write` -Methode in einer Snowflake-Tabelle. [Mehr dazu](https://experienceleague.adobe.com/docs/campaign/campaign-v8/architecture/api/new-apis.html){target=&quot;_blank&quot;}.

   1. Übergeben Sie den XML-Code als Argument für die Schreibanforderung.

### Schritt 1: Erstellen einer Schreibanforderung

Sie können Datensätze hinzufügen, aktualisieren und löschen.

#### Datensatz einfügen

Da die `insert` -Vorgang der Standardvorgang ist, müssen Sie ihn nicht angeben.

Geben Sie diese Informationen als XML-Attribute an:

* Das Schema der zu ändernden Tabelle
* Die auszufüllenden Tabellenfelder

Beispiel:

```javascript
var myXML = <recipient xtkschema="nms:recipient"
    firstName="Isabel"
    lastName="Garcia"
    email="isabel.garcia@mycompany.com"/>
```

#### Datensatz aktualisieren

Verwenden Sie die `_update` Vorgang. [Weitere Informationen](../../configuration/using/data-oriented-apis.md).

Geben Sie diese Informationen als XML-Attribute an:

* Das Schema der zu ändernden Tabelle
* Die zu aktualisierenden Tabellenfelder
* Das Schlüsselargument, das erforderlich ist, um den zu aktualisierenden Datensatz zu identifizieren

Beispiel:

```javascript
var myXML = <recipient xtkschema="nms:recipient"
    status="Client"
    email="isabel.garcia@mycompany.com"
    operation="_update"
    _key="@email"/>
```

#### Datensatz löschen

Verwenden Sie die `DeleteCollection` -Methode. [Weitere Informationen](https://experienceleague.adobe.com/developer/campaign-api/api/sm-session-DeleteCollection.html).

Geben Sie diese Informationen an:

* Das Schema der zu ändernden Tabelle
* Die `where` -Klausel, die erforderlich ist, um den zu aktualisierenden Datensatz in Form eines XML-Elements zu identifizieren

Beispiel:

```javascript
xtk.session.DeleteCollection(
    "nms:recipient",
    <where>
        <condition expr="[@email] = 'isabel.garcia@mycompany.com'"/>
    </where>,
    false
    )
```

### Schritt 2: den Datensatz schreiben

Rufen Sie die nicht-statischen `Write` -Methode `xtk:session` schema:

```javascript
xtk.session.Write(myXML)
```

Für diese Methode wird kein Wert zurückgegeben.

Fügen Sie einer JavaScript-Code-Aktivität im Workflow den vollständigen Code hinzu:

```javascript
var myXML = <recipient xtkschema="nms:recipient"
    firstName="Isabel"
    lastName="Garcia"
    email="isabel.garcia@mycompany.com"/>

xtk.session.Write(myXML)
```

In diesem Video wird gezeigt, wie in die Datenbank geschrieben wird:
>[!VIDEO](https://video.tv.adobe.com/v/18472/?learn=on)

## Beispiel 2: Datenbank abfragen{#read-example}

Um die Datenbank abzufragen, können Sie die nicht-statische `xtk:queryDef` Instanzmethode:

1. Erstellen Sie eine Abfrage in XML.
1. Erstellen Sie ein Abfrageobjekt.
1. Führen Sie die Abfrage aus.

### Schritt 1: Abfrage erstellen

Geben Sie den XML-Code für eine `queryDef` Entität.

Syntax:

```xml
<queryDef schema="nms:recipient" operation="">
    <!-- select, where, and orderBy clauses as XML elements -->
</queryDef>
```

Geben Sie diese Informationen an:

* Das Schema der zu lesenden Tabelle
* Der Vorgang
* Die zurückzugebenden Spalten in einer `select` clause
* Die Bedingungen in einer `where` clause
* Die Filterkriterien in einer `orderBy` clause

Sie können die folgenden Vorgänge verwenden:

| Prinzip | Ergebnis |
| --- | --- |
| `select` | Null oder mehr Elemente werden als Sammlung zurückgegeben. |
| `getIfExists` | Ein Element wird zurückgegeben. Wenn kein Übereinstimmungselement vorhanden ist, wird ein leeres Element zurückgegeben. |
| `get` | Ein Element wird zurückgegeben. Wenn kein Übereinstimmungselement vorhanden ist, wird ein Fehler zurückgegeben. |
| `count` | Die Anzahl der übereinstimmenden Datensätze wird in Form eines Elements mit einer `count` -Attribut. |

Schreiben Sie die `select`, `where`und `orderBy` als XML-Elemente:

* `select` clause

   Geben Sie die zurückzugebenden Spalten an. Um beispielsweise den Vor- und Nachnamen der Person auszuwählen, schreiben Sie folgenden Code:

   ```xml
   <select>
       <node expr="@firstName"/>
       <node expr="@lastName"/>
   </select>
   ```

   Mit dem `nms:recipient` -Schema, werden Elemente in diesem Formular zurückgegeben:

   ```xml
   <recipient firstName="Bo" lastName="Didley"/>
   ```

* `where` clause

   Um Bedingungen festzulegen, verwenden Sie eine `where` -Klausel. Um beispielsweise die Datensätze auszuwählen, die sich im **Schulung** -Ordner können Sie diesen Code schreiben:

   ```xml
   <where>
       <condition expr="[folder/@label]='Training'"/>
   </where>
   ```

   Verwenden Sie beim Kombinieren mehrerer Ausdrücke den booleschen Operator im ersten Ausdruck. Um beispielsweise alle Personen mit Namen Isabel Garcia auszuwählen, können Sie diesen Code schreiben:

   ```xml
   <condition boolOperator="AND" expr="@firstName='Isabel'"/>
   <condition expr="@lastName='Garcia'"/>
   ```

* `orderBy` clause

   Um die Ergebnismenge zu sortieren, geben Sie die `orderBy` -Klausel als XML-Element mit dem `sortDesc` -Attribut. Um beispielsweise die Nachnamen in aufsteigender Reihenfolge zu sortieren, können Sie diesen Code schreiben:

   ```xml
   <orderBy>
       <node expr="@lastName> sortDesc="false"/>
   </orderBy>
   ```

### Schritt 2: Abfrageobjekt erstellen

Um eine Entität aus dem XML-Code zu erstellen, verwenden Sie die `create(`*`content`*`)` -Methode:

```javascript
var query = xtk.queryDef.create(
    <queryDef schema="nms:recipient" operation="select">
    …
    </queryDef>)
```

Präfix `create(`*`content`*`)` -Methode mit dem Schema der zu erstellenden Entität.

Die *`content`* -Argument ist ein Zeichenfolgenargument und optional. Dieses Argument enthält den XML-Code, der die Entität beschreibt.

### Schritt 3: Abfrage ausführen

Führen Sie folgende Schritte aus:

1. Rufen Sie die `ExecuteQuery` -Methode `queryDef` entity:

   ```javascript
   var res = query.ExecuteQuery()
   ```

1. Verarbeiten Sie die Ergebnisse:
   1. Über die Ergebnisse der `select` -Vorgang mithilfe eines Schleifenkonstrukts.
   1. Testen Sie die Ergebnisse mithilfe des `getIfExists` Vorgang.
   1. Zählen Sie die Ergebnisse mithilfe der `count` Vorgang.

#### Ergebnisse einer `select` operation

Alle Übereinstimmungen werden als Sammlung zurückgegeben:

```xml
<recipient-collection>
    <recipient email="jane.smith@mycompany.com">
    <recipient email="john.harris@mycompany.com">
</recipient-collection>
```

Um die Ergebnisse zu durchlaufen, verwenden Sie die `for each` loop:

```javascript
for each (var rcp in res:recipient)
    logInfo(rcp.@email)
```

Die Schleife enthält eine lokale Empfängervariable. Für jeden Empfänger, der in der Empfängersammlung zurückgegeben wird, wird die E-Mail des Empfängers ausgegeben. [Weitere Infos](https://experienceleague.adobe.com/developer/campaign-api/api/f-logInfo.html) über die `logInfo` -Funktion.

#### Ergebnisse einer `getIfExists` operation

Jede Übereinstimmung wird als Element zurückgegeben:

```xml
<recipient id="52,378,079">
```

Wenn keine Übereinstimmung vorliegt, wird ein leeres Element zurückgegeben:

```xml
<recipient/>
```

Sie können auf den Primärschlüsselknoten verweisen, z. B. auf die `@id` Attribut:

```javascript
if (res.@id !=undefined)
    { // match was found
    …
    }
```

#### Ergebnis eines `get` operation

Eine Übereinstimmung wird als Element zurückgegeben:

```xml
<recipient id="52,378,079">
```

Wenn keine Übereinstimmung vorliegt, wird ein Fehler zurückgegeben.

>[!TIP]
>
>Wenn Sie wissen, dass eine Übereinstimmung vorliegt, verwenden Sie die `get` Vorgang. Verwenden Sie andernfalls die `getIfExists` Vorgang. Wenn Sie diese Best Practice verwenden, zeigen Fehler unerwartete Probleme. Wenn Sie `get` -Vorgang verwenden, verwenden Sie nicht die `try…catch` -Anweisung. Das Problem wird durch den Fehlerverarbeitungsprozess des Workflows behoben.

#### Ergebnis eines `count` operation

Ein Element mit dem `count` -Attribut zurückgegeben wird:

```xml
<recipient count="200">
```

Informationen zur Verwendung des Ergebnisses finden Sie im Abschnitt `@count` Attribut:

```javascript
if (res.@count > 0)
    { // matches were found
    …
    }
```

Für `select` -Operation, fügen Sie diesen Code einer JavaScript-Code -Aktivität im Workflow hinzu:

```javascript
var myXML =
<queryDef schema="nms:recipient" operation="select">
    <select>
        <node expr="@firstName"/>
        <node expr="@lastName"/>
    </select>
</queryDef>

var query = xtk.queryDef.create(myXML)

var res = query.ExecuteQuery()

for each (var rcp in res.recipient)
    logInfo(rcp.@firstName + " " + rcp.@lastName)
```

Da die `select` -Vorgang der Standardvorgang ist, müssen Sie ihn nicht angeben.

In diesem Video wird gezeigt, wie aus der Datenbank gelesen wird:
>[!VIDEO](https://video.tv.adobe.com/v/18475/?learn=on)

## Trigger eines Workflows {#trigger-example}

Sie können Workflows programmgesteuert beispielsweise in technischen Workflows oder zur Verarbeitung von Informationen verwenden, die ein Benutzer auf einer Webanwendungsseite eingegeben hat.

Die Auslösung von Workflows funktioniert durch die Verwendung von Ereignissen. Sie können diese Funktionen für Ereignisse verwenden:

* Um ein Ereignis zu posten, können Sie das statische `PostEvent` -Methode. [Weitere Informationen](https://experienceleague.adobe.com/developer/campaign-api/api/sm-workflow-PostEvent.html).
* Um ein Ereignis zu erhalten, können Sie die **[!UICONTROL Externes Signal]** Aktivität. [Weitere Informationen](external-signal.md).

Sie haben verschiedene Möglichkeiten, Workflows Trigger:

* Sie können einen Workflow inline, d. h. aus dem Hauptskript eines **[!UICONTROL JavaScript-Code]** Aktivität.
* Sie können einen Workflow nach Abschluss eines anderen Triggers ausführen:
   * Fügen Sie dem **[!UICONTROL Ende]** Aktivität des ersten Workflows.
   * Fügen Sie die **[!UICONTROL Externes Signal]** -Aktivität am Anfang des Zielgruppen-Workflows.

      Nach Abschluss des ersten Workflows wird ein Ereignis gepostet. Die ausgehende Transition wird aktiviert und die Ereignisvariablen werden ausgefüllt. Anschließend wird das Ereignis vom Ziel-Workflow empfangen.

      >[!TIP]
      >
      >Wenn Sie ein Skript zu einer Aktivität hinzufügen, empfiehlt es sich, den Aktivitätsnamen in doppelte Bindestriche einzuschließen, beispielsweise `-- end --`. [Weitere Infos](workflow-best-practices.md) Best Practices für Workflows.

Syntax der `PostEvent` -Methode:

```javascript
PostEvent(
    String     //ID of the target workflow
    String     //Name of the target activity
    String     //Name of the transition to be activated in case of multiple transitions
    XML        //Event parameters, in the <variables/> element
    Boolean    //To trigger the target workflow only once, set this parameter to true.
)
```

In diesem Beispiel wird nach Abschluss des Workflows ein kurzer Text an die **Signal** der **wkfExampleReceiver** workflow:

```javascript
var strLabel = "Adobe Campaign, Marketing that delivers"
xtk.workflow.PostEvent(
    "wkfExampleReceiver",
    "signal",
    "",
    <variables strLine={strLabel}/>,
    false)
```

Da der letzte Parameter auf `false`, die **wkfExampleReceiver** Der Workflow wird jedes Mal ausgelöst, wenn der erste Workflow abgeschlossen ist.

Beachten Sie beim Trigger von Workflows die folgenden Grundsätze:

* Die `PostEvent` -Befehl wird asynchron ausgeführt. Der Befehl wird in die Serverwarteschlange gestellt. Die Methode gibt nach der Veröffentlichung des Ereignisses zurück.
* Der Zielgruppen-Workflow muss gestartet werden. Andernfalls wird ein Fehler in die Protokolldatei geschrieben.
* Wenn der Zielgruppen-Workflow ausgesetzt wird, wird die `PostEvent` in die Warteschlange gestellt, bis der Workflow fortgesetzt wird.
* Die ausgelöste Aktivität erfordert nicht, dass eine Aufgabe ausgeführt wird.

In diesem Video wird gezeigt, wie statische API-Methoden verwendet werden:
>[!VIDEO](https://video.tv.adobe.com/v/18481/?learn=on)

In diesem Video wird gezeigt, wie Trigger-Workflows ausgeführt werden:
>[!VIDEO](https://video.tv.adobe.com/v/18485/?learn=on)

## Interagieren mit der Datenbank {#interact-example}

Diese Beispiele zeigen, wie Sie diese Aktionen durchführen:

* Verwenden Sie die `get` und `create` Methoden für Schemata zur Verwendung nicht statischer SOAP-Methoden
* Erstellen von Methoden zum Ausführen von SQL-Abfragen
* Verwenden Sie die `write` Methode zum Einfügen, Aktualisieren und Löschen von Datensätzen

Führen Sie folgende Schritte aus:

1. Definieren Sie die Abfrage:

   * Abrufen einer Entität mithilfe der `create` -Methode für das entsprechende Schema - z. B. die `xtk:workflow` Schema. [Weitere Informationen](https://experienceleague.adobe.com/developer/campaign-api/api/f-create.html).
   * Verwenden Sie die `queryDef` -Methode, um eine SQL-Abfrage auszugeben.

1. Führen Sie die Abfrage mit der `ExecuteQuery` -Methode. [Weitere Informationen](https://experienceleague.adobe.com/developer/campaign-api/api/sm-queryDef-ExecuteQuery.html).

   Verwenden Sie die `for each` Schleife zum Abrufen der Ergebnisse.

### Syntax der `queryDef` -Methode mit `select` clause

```xml
<queryDef schema="schema_key" operation="operation_type">
    <select>
        <node expr="expression1">
        <node sql="expression2">
    </select>
    <where> 
        <condition expr="expression1"/> 
        <condition sql="expression2"/>
    </where>
    <orderBy>
        <node expr="expression1">
        <node sql="expression2">
    </orderBy>
    <groupBy>
        <node expr="expression1">
        <node sql="expression2">
    </groupBy>
    <having>
        <condition expr="expression1"/> 
        <condition sql="expression2"/>
    </having>
</queryDef>
```

### `Create` method

#### Beispiel 1: Datensätze auswählen und in das Protokoll schreiben

Die internen Namen der Workflows, die sich im **wfExample** -Ordner ausgewählt sind. Die Ergebnisse werden nach internem Namen in aufsteigender Reihenfolge sortiert und in das Journal geschrieben.

```javascript
var query = xtk.queryDef.create(
    <queryDef schema="xtk:workflow" operation="select">
        <select>
            <node expr="@internalName"/>
        </select>
        <where>
            <condition expr="[folder/@name]='wfExamples'"/>
        </where>
        <orderBy>
            <node expr="@internalName" sortDesc="false"/>
        </orderBy>
    </queryDef>
    )

var res = query.ExecuteQuery()
for each (var w in res.workflow)
    logInfo(w.@internalName)
```

#### Beispiel 2: Löschen von Datensätzen

Vorname, Nachname, E-Mail-Adresse und Kennung aller Empfänger mit dem Namen Chris Smith werden ausgewählt. Die Ergebnisse werden nach E-Mail, aufsteigender Reihenfolge sortiert und in das Journal geschrieben. A `delete` wird zum Löschen der ausgewählten Datensätze verwendet.

```javascript
// Build the query, create a query object and hold the object in a variable
var query = xtk.queryDef.create(
        <queryDef schema="nms:recipient" operation="select">
            <select>
                <node expr="@firstName"/>
                <node expr="@lastName"/>
                <node expr="@email"/>
                <node expr="@id"/>
            </select>
            <where>
                <condition expr="[folder/@label]='Recipients'"/>
                <condition expr="[@lastName]='Smith'"/>
                <condition expr="[@firstName]='Chris'"/>
            </where>
            <orderBy>
                <node expr="@email" sortDesc="false"/>
            </orderBy>
        </queryDef>
)

//Run the query using the ExecuteQuery method against the created object
var res = query.ExecuteQuery()

//Loop through the results, print out the person's name and email, then delete the records
for each (var rec in res.recipient)
    {
     logInfo("Delete record = Email: " + rec.@email + ', ' + rec.@firstName + ' ' + rec.@lastName)
     xtk.session.Write(<recipient xtkschema="nms:recipient" _operation="delete" id={rec.@id}/>)
    }
```

#### Beispiel 3: Datensätze auswählen und in das Protokoll schreiben

In diesem Beispiel wird eine nicht statische Methode verwendet. Die E-Mail-Adresse und das Geburtsjahr aller Empfänger, deren Informationen in der Variablen **1234** und deren E-Mail-Domainname mit &quot;adobe&quot;beginnt, ausgewählt werden. Die Ergebnisse werden nach Geburtsdatum in absteigender Reihenfolge sortiert. Die E-Mail der Empfänger wird in das Protokoll geschrieben.

```javascript
var query = xtk.queryDef.create(
<queryDef schema="nms:recipient" operation="select">
    <select>
        <node expr="@email"/>
        <node sql="sEmail"/>
        <node expr="Year(@birthDate)"/>
    </select>
    <where>
        <condition expr="[@folder-id] = 1234 and @domain like 'adobe%'"/>
        <condition sql="iFolderId = 1234 and sDomain like 'adobe%'"/>
    </where>
    <orderBy>
        <node expr="@birthDate" sortDesc="true"/>
    </orderBy>
</queryDef>
)

var res = query.ExecuteQuery()
for each (var w in res.recipient)
    logInfo(w.@email)
```

### `Write` method

Sie können Datensätze einfügen, aktualisieren und löschen. Sie können die `Write` -Methode für ein beliebiges Schema in Adobe Campaign verwenden. Da diese Methode statisch ist, müssen Sie kein Objekt erstellen. Sie können die folgenden Vorgänge verwenden:

* Die `update` operation
* Die `insertOrUpdate` -Vorgang mit dem `_key` -Argument zur Identifizierung des zu aktualisierenden Datensatzes

   Wenn Sie die **Empfänger** -Ordner, und wenn eine Übereinstimmung vorhanden ist, wird der Datensatz in einem beliebigen Unterordner aktualisiert. Andernfalls wird der Datensatz im Stammverzeichnis erstellt **Empfänger** Ordner.

* Die `delete` operation

>[!IMPORTANT]
> Wenn Sie Adobe Campaign v8 verwenden, empfehlen wir, den Staging-Mechanismus mit dem **Aufnahme** und **Datenaktualisierung/-löschung** APIs für die `Write` -Methode in einer Snowflake-Tabelle. [Mehr dazu](https://experienceleague.adobe.com/docs/campaign/campaign-v8/architecture/api/new-apis.html){target=&quot;_blank&quot;}.

#### Beispiel 1: Datensatz einfügen oder aktualisieren

```javascript
xtk.session.Write(
<recipient
    xtkschema="nms:recipient"
    _operation="insertOrUpdate" _key="@email"
    lastName="Lennon"
    firstName="John"
    email="johnlennon@thebeatles.com"
/>
)
```

#### Beispiel 2: Löschen von Datensätzen

In diesem Beispiel werden eine statische Methode und eine nicht statische Methode kombiniert.

```javascript
var query=xtk.queryDef.create(
<queryDef schema="nms:recipient" operation="select">
    <select>
        <node expr="@Id"/>
    </select>
    <where>
        <condition expr="[@email]='johnlennon@thebeatles.com'"/>
    </where>
</queryDef>
);

var res = query.ExecuteQuery()
for each (var w in res.recipient) {
xtk.session.Write(
    <recipient xtkschema="nms:recipient" _operation="delete" id={w.@id}/>
);
}
```

In diesem Video wird gezeigt, wie nichtstatische API-Methoden verwendet werden:
>[!VIDEO](https://video.tv.adobe.com/v/18477/?learn=on)

In diesem Video wird ein Beispiel für die Verwendung einer nicht statischen API-Methode in einem Workflow gezeigt:
>[!VIDEO](https://video.tv.adobe.com/v/18476/?learn=on)

## Verwandte Themen

* [Datenorientierte APIs](../../configuration/using/data-oriented-apis.md)
* [JavaScript-Scripts und -Vorlagen](javascript-scripts-and-templates.md)
* [SOAP-Methoden in JavaScript](../../configuration/using/soap-methods-in-javascript.md)

### API-Handbuch

* [Beispiele für SOAP-Aufrufe](https://experienceleague.adobe.com/developer/campaign-api/api/p-14.html)
* Methoden:
   * [Erstellen](https://experienceleague.adobe.com/developer/campaign-api/api/f-create.html)
   * [DeleteCollection](https://experienceleague.adobe.com/developer/campaign-api/api/sm-session-DeleteCollection.html)
   * [ExecuteQuery](https://experienceleague.adobe.com/developer/campaign-api/api/sm-queryDef-ExecuteQuery.html)
   * [PostEvent](https://experienceleague.adobe.com/developer/campaign-api/api/sm-workflow-PostEvent.html)
   * [Schreiben](https://experienceleague.adobe.com/developer/campaign-api/api/sm-session-Write.html)
* [logInfo-Funktion](https://experienceleague.adobe.com/developer/campaign-api/api/f-logInfo.html)