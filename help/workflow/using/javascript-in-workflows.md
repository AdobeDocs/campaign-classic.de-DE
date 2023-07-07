---
product: campaign
title: Beispiele für JavaScript-Code in Workflows
description: Diese Beispiele zeigen, wie Sie JavaScript-Code in einem Workflow verwenden können
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows
exl-id: 7213ea64-3dec-4b16-9d93-4ae941ddfaa7
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '1771'
ht-degree: 100%

---

# Beispiele für JavaScript-Code in Workflows{#javascript-in-workflows}



Diese Beispiele zeigen, wie Sie JavaScript-Code in einem Workflow verwenden können:

* [Schreiben in die Datenbank](#write-example)
* [Abfragen der Datenbank](#read-example)
* [Auslösen eines Workflows mit einer statischen SOAP-Methode](#trigger-example)
* [Interagieren mit der Datenbank mithilfe einer nicht statischen SOAP-Methode](#interact-example)

[Weitere Informationen](https://experienceleague.adobe.com/developer/campaign-api/api/p-14.html?lang=de) über statische und nicht statische SOAP-Methoden.

In diesen Beispielen wird die Erweiterung ECMAScript for XML (E4X) verwendet. Mit dieser Erweiterung können Sie JavaScript-Aufrufe und XML-Primitive im selben Script kombinieren.

Gehen Sie wie folgt vor, um diese Beispiele auszuprobieren:

1. Erstellen Sie einen Workflow und fügen Sie die folgenden Aktivitäten zum Workflow hinzu:
   1. Startaktivität
   1. JavaScript-Code-Aktivität
   1. Endaktivität

   [Weitere Informationen](building-a-workflow.md) über das Erstellen von Workflows.

1. Fügen Sie den JavaScript-Code zu einer Aktivität hinzu. [Weitere Informationen](advanced-parameters.md).
1. Speichern Sie den Workflow.
1. Testen Sie die Beispiele:
   1. Starten Sie den Workflow. [Weitere Informationen](starting-a-workflow.md).
   1. Öffnen Sie das Protokoll. [Weitere Informationen](monitoring-workflow-execution.md#displaying-logs).

## Beispiel 1: In Datenbank schreiben{#write-example}

Zum Schreiben in die Datenbank können Sie die statische `Write`-Methode mit dem `xtk:session`-Schema verwenden:

1. Erstellen Sie eine Schreibabfrage in XML.

1. Schreiben Sie den Datensatz:

   1. Rufen Sie die `Write`-Methode mit dem `xtk:session`-Schema auf.

      >[!IMPORTANT]
      > Wenn Sie Adobe Campaign v8 verwenden, empfehlen wir, den Staging-Mechanismus mit den **Aufnahme**- und **Datenaktualisierungs/-löschungs**-APIs für die `Write`-Methode in einer Snowflake-Tabelle zu verwenden. [Weitere Informationen](https://experienceleague.adobe.com/docs/campaign/campaign-v8/architecture/api/new-apis.html?lang=de){target="_blank"}.

   1. Übergeben Sie den XML-Code als Argument für die Schreibabfrage.

### Schritt 1: Erstellen einer Schreibabfrage

Sie können Datensätze hinzufügen, aktualisieren und löschen.

#### Einfügen eines Datensatzes

Da der `insert`-Vorgang der Standardvorgang ist, müssen Sie ihn nicht angeben.

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

#### Aktualisieren eines Datensatzes

Verwenden Sie den `_update`-Vorgang. [Weitere Informationen](../../configuration/using/data-oriented-apis.md).

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

#### Löschen eines Datensatzes

Verwenden Sie die `DeleteCollection`-Methode. [Weitere Informationen](https://experienceleague.adobe.com/developer/campaign-api/api/sm-session-DeleteCollection.html?lang=de).

Geben Sie diese Informationen an:

* Das Schema der zu ändernden Tabelle
* Die `where`-Klausel, die erforderlich ist, um den zu aktualisierenden Datensatz in Form eines XML-Elements zu identifizieren

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

### Schritt 2: Datensatz schreiben

Rufen Sie die nicht statische `Write`-Methode mit dem `xtk:session`-Schema auf:

```javascript
xtk.session.Write(myXML)
```

Für diese Methode wird kein Wert zurückgegeben.

Fügen Sie zu einer JavaScript-Code-Aktivität im Workflow den vollständigen Code hinzu:

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

Um die Datenbank abzufragen, können Sie die nicht statische `xtk:queryDef`-Instanzmethode verwenden:

1. Erstellen Sie eine Abfrage in XML.
1. Erstellen Sie ein Abfrageobjekt.
1. Führen Sie die Abfrage aus.

### Schritt 1: Abfrage erstellen

Geben Sie den XML-Code für eine `queryDef`-Entität an.

Syntax:

```xml
<queryDef schema="nms:recipient" operation="">
    <!-- select, where, and orderBy clauses as XML elements -->
</queryDef>
```

Geben Sie diese Informationen an:

* Das Schema der zu lesenden Tabelle
* Der Vorgang
* Die zurückzugebenden Spalten in einer `select`-Klausel
* Die Bedingungen in einer `where`-Klausel
* Die Filterkriterien in einer `orderBy`-Klausel

Sie können die folgenden Vorgänge verwenden:

| Vorgang | Ergebnis |
| --- | --- |
| `select` | Null oder mehr Elemente werden als Sammlung zurückgegeben. |
| `getIfExists` | Ein Element wird zurückgegeben. Wenn kein Übereinstimmungselement vorhanden ist, wird ein leeres Element zurückgegeben. |
| `get` | Ein Element wird zurückgegeben. Wenn kein Übereinstimmungselement vorhanden ist, wird ein Fehler zurückgegeben. |
| `count` | Die Anzahl der übereinstimmenden Datensätze wird in Form eines Elements mit einem `count`-Attribut zurückgegeben. |

Schreiben Sie die `select`-, `where`- und `orderBy`-Klauseln als XML-Elemente:

* `select`-Klausel

  Geben Sie die zurückzugebenden Spalten an. Um beispielsweise den Vor- und Nachnamen der Person auszuwählen, schreiben Sie folgenden Code:

  ```xml
  <select>
      <node expr="@firstName"/>
      <node expr="@lastName"/>
  </select>
  ```

  Mit dem `nms:recipient`-Schema werden Elemente in der folgenden Form zurückgegeben:

  ```xml
  <recipient firstName="Bo" lastName="Didley"/>
  ```

* `where`-Klausel

  Um Bedingungen festzulegen, verwenden Sie eine `where`-Klausel. Um beispielsweise die Datensätze auszuwählen, die sich im Ordner **Training** befinden, können Sie den folgenden Code schreiben:

  ```xml
  <where>
      <condition expr="[folder/@label]='Training'"/>
  </where>
  ```

  Verwenden Sie beim Kombinieren mehrerer Ausdrücke den booleschen Operator im ersten Ausdruck. Um beispielsweise alle Personen mit Namen Isabel Garcia auszuwählen, können Sie den folgenden Code schreiben:

  ```xml
  <condition boolOperator="AND" expr="@firstName='Isabel'"/>
  <condition expr="@lastName='Garcia'"/>
  ```

* `orderBy`-Klausel

  Um die Ergebnismenge zu sortieren, geben Sie die `orderBy`-Klausel als XML-Element mit dem `sortDesc`-Attribut an. Um beispielsweise die Nachnamen in aufsteigender Reihenfolge zu sortieren, können Sie den folgenden Code schreiben:

  ```xml
  <orderBy>
      <node expr="@lastName> sortDesc="false"/>
  </orderBy>
  ```

### Schritt 2: Abfrageobjekt erstellen

Um eine Entität aus dem XML-Code zu erstellen, verwenden Sie die `create(`*`content`*`)`-Methode:

```javascript
var query = xtk.queryDef.create(
    <queryDef schema="nms:recipient" operation="select">
    …
    </queryDef>)
```

Stellen Sie der `create(`*`content`*`)`-Methode das Schema der zu erstellenden Entität als Präfix voran.

Das *`content`*-Argument ist ein Zeichenfolgenargument und optional. Dieses Argument enthält den XML-Code, der die Entität beschreibt.

### Schritt 3: Abfrage ausführen

Führen Sie folgende Schritte aus:

1. Rufen Sie die `ExecuteQuery`-Methode mit der `queryDef`-Entität auf:

   ```javascript
   var res = query.ExecuteQuery()
   ```

1. Verarbeiten Sie die Ergebnisse:
   1. Iterieren Sie über die Ergebnisse des `select`-Vorgangs mithilfe eines Schleifenkonstrukts.
   1. Testen Sie die Ergebnisse mithilfe des `getIfExists`-Vorgangs.
   1. Zählen Sie die Ergebnisse mithilfe des `count`-Vorgangs.

#### Ergebnisse eines `select`-Vorgangs

Alle Übereinstimmungen werden als Sammlung zurückgegeben:

```xml
<recipient-collection>
    <recipient email="jane.smith@mycompany.com">
    <recipient email="john.harris@mycompany.com">
</recipient-collection>
```

Um die Ergebnisse zu durchlaufen, verwenden Sie die `for each`-Schleife:

```javascript
for each (var rcp in res:recipient)
    logInfo(rcp.@email)
```

Die Schleife enthält eine lokale Empfängervariable. Für jeden Empfänger, der in der Empfängersammlung zurückgegeben wird, wird die E-Mail des Empfängers ausgedruckt. [Weitere Informationen](https://experienceleague.adobe.com/developer/campaign-api/api/f-logInfo.html?lang=de) über die `logInfo`-Funktion.

#### Ergebnisse eines `getIfExists`-Vorgangs

Jede Übereinstimmung wird als Element zurückgegeben:

```xml
<recipient id="52,378,079">
```

Wenn keine Übereinstimmung vorliegt, wird ein leeres Element zurückgegeben:

```xml
<recipient/>
```

Sie können auf den Primärschlüsselknoten verweisen, z. B. das `@id`-Attribut:

```javascript
if (res.@id !=undefined)
    { // match was found
    …
    }
```

#### Ergebnis eines `get`-Vorgangs

Eine Übereinstimmung wird als Element zurückgegeben:

```xml
<recipient id="52,378,079">
```

Wenn keine Übereinstimmung vorliegt, wird ein Fehler zurückgegeben.

>[!TIP]
>
>Wenn Sie wissen, dass eine Übereinstimmung vorliegt, verwenden Sie den `get`-Vorgang. Verwenden Sie andernfalls den `getIfExists`-Vorgang. Wenn Sie diese Best Practice verwenden, zeigt das Auftreten von Fehlern, dass unerwartete Probleme vorliegen. Wenn Sie den `get`-Vorgang verwenden, verwenden Sie nicht die Anweisung `try…catch`. Das Problem wird durch den Fehlerverarbeitungsprozess des Workflows behoben.

#### Ergebnis eines `count`-Vorgangs

Ein Element mit dem `count`-Attribut wird zurückgegeben:

```xml
<recipient count="200">
```

Um das Ergebnis zu verwenden, verweisen Sie auf das `@count`-Attribut:

```javascript
if (res.@count > 0)
    { // matches were found
    …
    }
```

Fügen Sie für den `select`-Vorgang den folgenden Code zu einer JavaScript-Code-Aktivität im Workflow hinzu:

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

Da der `select`-Vorgang der Standardvorgang ist, müssen Sie ihn nicht angeben.

In diesem Video wird gezeigt, wie aus der Datenbank gelesen wird:
>[!VIDEO](https://video.tv.adobe.com/v/18475/?learn=on)

## Auslösen eines Workflows {#trigger-example}

Sie können Workflows programmgesteuert auslösen, beispielsweise in technischen Workflows oder zur Verarbeitung von Informationen, die ein Benutzer auf einer Web-Anwendungsseite eingegeben hat.

Das Auslösen von Workflows erfolgt durch die Verwendung von Ereignissen. Sie können die folgenden Funktionen für Ereignisse verwenden:

* Um ein Ereignis zu posten, können Sie die statische `PostEvent`-Methode verwenden. [Weitere Informationen](https://experienceleague.adobe.com/developer/campaign-api/api/sm-workflow-PostEvent.html?lang=de).
* Um ein Ereignis zu erhalten, können Sie die Aktivität **[!UICONTROL Externes Signal]** verwenden. [Weitere Informationen](external-signal.md).

Sie haben verschiedene Möglichkeiten, Workflows auszulösen:

* Sie können einen Workflow inline auslösen, d. h. vom Hauptskript einer **[!UICONTROL JavaScript-Code]**-Aktivität aus.
* Sie können einen Workflow nach Abschluss eines anderen auslösen:
   * Fügen Sie zur **[!UICONTROL Endaktivität]** des ersten Workflows ein Initialisierungsscript hinzu.
   * Fügen Sie die Aktivität **[!UICONTROL Externes Signal]** am Beginn des Ziel-Workflows hinzu.

     Nach Abschluss des ersten Workflows wird ein Ereignis gepostet. Die ausgehende Transition wird aktiviert und die Ereignisvariablen werden ausgefüllt. Anschließend wird das Ereignis vom Ziel-Workflow empfangen.

     >[!TIP]
     >
     >Wenn Sie ein Script zu einer Aktivität hinzufügen, empfiehlt es sich, den Aktivitätsnamen in doppelte Bindestriche einzuschließen, beispielsweise `-- end --`. [Weitere Informationen](workflow-best-practices.md) zu Best Practices für Workflows.

Syntax der `PostEvent`-Methode:

```javascript
PostEvent(
    String     //ID of the target workflow
    String     //Name of the target activity
    String     //Name of the transition to be activated in case of multiple transitions
    XML        //Event parameters, in the <variables/> element
    Boolean    //To trigger the target workflow only once, set this parameter to true.
)
```

In diesem Beispiel wird nach Abschluss des Workflows ein kurzer Text an die **Signalaktivität** des Workflows **wkfExampleReceiver** übergeben:

```javascript
var strLabel = "Adobe Campaign, Marketing that delivers"
xtk.workflow.PostEvent(
    "wkfExampleReceiver",
    "signal",
    "",
    <variables strLine={strLabel}/>,
    false)
```

Da der letzte Parameter auf `false` festgelegt ist, wird der Workflow **wkfExampleReceiver** jedes Mal ausgelöst, wenn der erste Workflow abgeschlossen ist.

Beachten Sie beim Auslösen eines Workflows die folgenden Grundsätze:

* Der Befehl `PostEvent` wird asynchron ausgeführt. Der Befehl wird in die Server-Warteschlange eingefügt. Die Methode gibt nach der Veröffentlichung des Ereignisses etwas zurück.
* Der Ziel-Workflow muss gestartet werden. Andernfalls wird ein Fehler in die Protokolldatei geschrieben.
* Wenn der Ziel-Workflow ausgesetzt wird, wird der Befehl `PostEvent` in die Warteschlange aufgenommen, bis der Workflow fortgesetzt wird.
* Die ausgelöste Aktivität erfordert nicht, dass eine Aufgabe in Bearbeitung ist.

In diesem Video wird gezeigt, wie statische API-Methoden verwendet werden können:
>[!VIDEO](https://video.tv.adobe.com/v/18481/?learn=on)

In diesem Video wird gezeigt, wie Workflows ausgelöst werden:
>[!VIDEO](https://video.tv.adobe.com/v/18485/?learn=on)

## Interagieren mit der Datenbank {#interact-example}

Diese Beispiele zeigen, wie Sie diese Aktionen durchführen:

* Verwenden Sie die Methoden `get` und `create` für Schemas zur Verwendung nicht statischer SOAP-Methoden
* Erstellen von Methoden zum Ausführen von SQL-Abfragen
* Verwenden Sie die `write`-Methode zum Einfügen, Aktualisieren und Löschen von Datensätzen

Führen Sie folgende Schritte aus:

1. Definieren Sie die Abfrage:

   * Rufen Sie eine Entität mithilfe der `create`-Methode für das entsprechende Schema ab, z. B. das `xtk:workflow`-Schema. [Weitere Informationen](https://experienceleague.adobe.com/developer/campaign-api/api/f-create.html?lang=de).
   * Verwenden Sie die `queryDef`-Methode, um eine SQL-Abfrage auszugeben.

1. Führen Sie die Abfrage mithilfe der `ExecuteQuery`-Methode aus. [Weitere Informationen](https://experienceleague.adobe.com/developer/campaign-api/api/sm-queryDef-ExecuteQuery.html?lang=de).

   Verwenden Sie die `for each`-Schleife zum Abrufen der Ergebnisse.

### Syntax der `queryDef`-Methode mit der `select`-Klausel

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

### `Create`-Methode

#### Beispiel 1: Datensätze auswählen und in das Protokoll schreiben

Die internen Namen der Workflows, die sich im Ordner **wfExamples** befinden, werden ausgewählt. Die Ergebnisse werden nach internem Namen in aufsteigender Reihenfolge sortiert und in das Protokoll geschrieben.

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

#### Beispiel 2: Datensätze löschen

Vorname, Nachname, E-Mail-Adresse und Kennung aller Empfänger mit dem Namen Chris Smith werden ausgewählt. Die Ergebnisse werden nach E-Mail-Adresse in aufsteigender Reihenfolge sortiert und in das Protokoll geschrieben. Ein `delete`-Vorgang wird zum Löschen der ausgewählten Datensätze verwendet.

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

In diesem Beispiel wird eine nicht statische Methode verwendet. Die E-Mail-Adresse und das Geburtsjahr aller Empfänger, deren Informationen im Ordner **1234** gespeichert sind und deren E-Mail-Domain-Name mit &quot;adobe&quot; beginnt, werden ausgewählt. Die Ergebnisse werden nach Geburtsdatum in absteigender Reihenfolge sortiert. Die E-Mail-Adressen der Empfänger werden in das Protokoll geschrieben.

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

### `Write`-Methode

Sie können Datensätze einfügen, aktualisieren und löschen. Sie können die `Write`-Methode für ein beliebiges Schema in Adobe Campaign verwenden. Da diese Methode statisch ist, müssen Sie kein Objekt erstellen. Sie können die folgenden Vorgänge verwenden:

* Der `update`-Vorgang
* Der `insertOrUpdate`-Vorgang mit dem `_key`-Argument zur Identifizierung des zu aktualisierenden Datensatzes

  Wenn Sie den Ordner **Empfänger** nicht angeben und eine Übereinstimmung vorhanden ist, wird der Datensatz in allen Unterordnern aktualisiert. Andernfalls wird der Datensatz im Stammverzeichnis des Ordners **Empfänger** erstellt.

* Der `delete`-Vorgang

>[!IMPORTANT]
> Wenn Sie Adobe Campaign v8 verwenden, empfehlen wir, den Staging-Mechanismus mit den **Aufnahme**- und **Datenaktualisierungs/-löschungs**-APIs für die `Write`-Methode in einer Snowflake-Tabelle zu verwenden. [Weitere Informationen](https://experienceleague.adobe.com/docs/campaign/campaign-v8/architecture/api/new-apis.html?lang=de){target="_blank"}.

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

#### Beispiel 2: Datensätze löschen

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

In diesem Video wird gezeigt, wie nicht statische API-Methoden verwendet werden:
>[!VIDEO](https://video.tv.adobe.com/v/18477/?learn=on)

In diesem Video wird ein Beispiel für die Verwendung einer nicht statischen API-Methode in einem Workflow gezeigt:
>[!VIDEO](https://video.tv.adobe.com/v/18476/?learn=on)

## Verwandte Themen

* [Datenorientierte APIs](../../configuration/using/data-oriented-apis.md)
* [JavaScript-Scripte und -Vorlagen](javascript-scripts-and-templates.md)
* [SOAP-Methoden in JavaScript](../../configuration/using/soap-methods-in-javascript.md)

### API-Dokumentation

* [Beispiele für SOAP-Aufrufe](https://experienceleague.adobe.com/developer/campaign-api/api/p-14.html?lang=de)
* Methoden:
   * [Create](https://experienceleague.adobe.com/developer/campaign-api/api/f-create.html?lang=de)
   * [DeleteCollection](https://experienceleague.adobe.com/developer/campaign-api/api/sm-session-DeleteCollection.html?lang=de)
   * [ExecuteQuery](https://experienceleague.adobe.com/developer/campaign-api/api/sm-queryDef-ExecuteQuery.html?lang=de)
   * [PostEvent](https://experienceleague.adobe.com/developer/campaign-api/api/sm-workflow-PostEvent.html?lang=de)
   * [Write](https://experienceleague.adobe.com/developer/campaign-api/api/sm-session-Write.html?lang=de)
* [logInfo-Funktion](https://experienceleague.adobe.com/developer/campaign-api/api/f-logInfo.html?lang=de)
