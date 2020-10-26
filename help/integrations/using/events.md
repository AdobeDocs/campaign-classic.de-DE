---
title: Integration konfigurieren
seo-title: Integration konfigurieren
description: Integration konfigurieren
seo-description: null
page-status-flag: never-activated
uuid: e2db7bdb-8630-497c-aacf-242734cc0a72
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 1c20795d-748c-4f5d-b526-579b36666e8f
translation-type: ht
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: ht
source-wordcount: '1152'
ht-degree: 100%

---


# Triggers-Ereignisse {#events}

## Verarbeiten von Ereignissen in JavaScript {#events-javascript}

### JavaScript-Datei {#file-js}

Die Pipeline verwendet eine JavaScript-Funktion, um jede Nachricht zu verarbeiten. Diese Funktion ist benutzerdefiniert.

Sie wird in der Option **[!UICONTROL NmsPipeline_Config]** unter dem Attribut &quot;JSConnector&quot; konfiguriert. Dieses JavaScript wird jedes Mal aufgerufen, wenn ein Ereignis empfangen wird. Es wird vom [!DNL pipelined]-Prozess ausgeführt.

Die JS-Beispieldatei lautet &quot;cus:Trigger.js&quot;.

### JavaScript-Funktion {#function-js}

Das [!DNL pipelined]-JavaScript muss mit einer bestimmten Funktion beginnen.

Diese Funktion wird für jedes Ereignis einmal aufgerufen:

```
function processPipelineMessage(xmlTrigger) {}
```

Sie sollte zurückgegeben werden als

```
<undefined/>
```

Starten Sie [!DNL pipelined] nach Bearbeitung des JS neu.

### Datenformat des Auslösers {#trigger-format}

Die [!DNL trigger]-Daten werden an die JS-Funktion übergeben. Sie liegen im XML-Format vor.

* Das **[!UICONTROL @triggerId]**-Attribut enthält den Namen des [!DNL trigger].
* Das Element **Anreicherungen** im JSON-Format enthält die von Analytics generierten Daten und wird an den Auslöser angehängt.
* **[!UICONTROL @offset]** ist der &quot;Zeiger&quot; auf die Nachricht. Er gibt die Reihenfolge der Nachrichten in der Warteschlange an.
* **[!UICONTROL @partitio]**n ist ein Container mit Nachrichten, die sich in der Warteschlange befinden. Der Versatz ist relativ zu einer Partition. <br>Es gibt etwa 15 Partitionen in der Warteschlange.

Beispiel:

```
<trigger offset="1500435" partition="4" triggerId="LogoUpload_1_Visits_from_specific_Channel_or_ppp">
 <enrichments>{"analyticsHitSummary":{"dimensions":{" eVar01":{"type":"string","data":["PI4INE1ETDF6UK35GO13X7HO2ITLJHVH"],"name":" eVar01","source":"session summary"}, "timeGMT":{"type":"int","data":[1469164186,1469164195],"name":"timeGMT","source":"session summary"}},"products":{}}}</enrichments>
 <aliases/>
 </trigger>
```

### Datenformat der Anreicherung {#enrichment-format}

>[!NOTE]
>
>Es handelt sich hierbei um ein spezifisches Beispiel aus verschiedenen möglichen Implementierungen.

Für jeden Auslöser wird in Analytics der Inhalt definiert. Er liegt im JSON-Format vor.
Zum Beispiel im Auslöser &quot;logoUpload_uploading_Visits&quot;:

* **[!UICONTROL eVar01]** kann die Käufer-ID enthalten, die zur Abstimmung mit Campaign-Empfängern verwendet wird. Sie liegt im Zeichenfolgenformat vor. <br>Sie muss abgestimmt werden, um die Käufer-ID (den Primärschlüssel) zu ermitteln.

* **[!UICONTROL timeGMT]** kann die Zeit des Auslösers auf der Analytics-Seite enthalten. Das Format lautet UTC Epoch (Sekunden seit dem 1.1.1970 UTC).

Beispiel:

```
{
 "analyticsHitSummary": {
 "dimensions": {
 "eVar01": {
 "type": "string",
 "data": ["PI4INE1ETDF6UK35GO13X7HO2ITLJHVH"],
 "name": " eVar01",
 "source": "session summary"
 },
 "timeGMT": {
 "type": "int",
 "data": [1469164186, 1469164195],
 "name": "timeGMT",
 "source": "session summary"
 }
 },
 "products": {}
 }
 }
```

### Reihenfolge der Verarbeitung von Ereignissen {#order-events}

Die Ereignisse werden nacheinander in der Reihenfolge des Versatzes verarbeitet. Jeder Thread des [!DNL pipelined]-Prozesses verarbeitet eine andere Partition.

Der &quot;Versatz&quot; des letzten abgerufenen Ereignisses wird in der Datenbank gespeichert. Wenn der Prozess angehalten wird, startet er daher bei der letzten Nachricht neu. Diese Daten werden im nativen Schema &quot;xtk:pipelineOffset&quot; gespeichert.

Dieser Zeiger ist für jede Instanz und jeden Verbraucher spezifisch. Wenn verschiedene Instanzen auf dieselbe Pipeline mit unterschiedlichen Verbrauchern zugreifen, erhalten diese also alle Nachrichten in derselben Reihenfolge.

Der Parameter &quot;consumer&quot; der Pipeline-Option identifiziert die aufrufende Instanz.

Derzeit gibt es keine Möglichkeit, unterschiedliche Warteschlangen für separate Umgebungen wie &quot;staging&quot; oder &quot;dev&quot; zu nutzen.

### Protokollierung und Fehlerbehandlung {#logging-error-handling}

Logs wie &quot;logInfo()&quot; werden an das [!DNL pipelined]-Log weitergeleitet. Fehler wie &quot;logError()&quot; werden in das [!DNL pipelined]-Log geschrieben und führen dazu, dass das Ereignis in eine Warteschlange für erneute Versuche gestellt wird. Überprüfen Sie das Pipelined-Protokoll.
Bei fehlerhaften Nachrichten werden im Zeitraum, der in den [!DNL pipelined]-Optionen festgelegt ist, mehrmals erneute Versuche ausgeführt.

Für Debugging- und Überwachungszwecke werden die vollständigen Auslöserdaten in die Auslösertabelle geschrieben. Sie liegen im Feld &quot;data&quot; im XML-Format vor. Alternativ dazu sind die Auslöserdaten auch in &quot;logInfo()&quot; verfügbar.

### Analysieren der Daten {#data-parsing}

Dieser JS-Beispielcode analysiert die eVar01 in den Anreicherungen.

```
function processPipelineMessage(xmlTrigger)
 {
 (…)
 var shopper_id = ""
 if (xmlTrigger.enrichments.length() > 0)
 {
 if (xmlTrigger.enrichments.toString().match(/eVar01/) != undefined)
 {
 var enrichments = JSON.parse(xmlTrigger.enrichments.toString())
 shopper_id = enrichments.analyticsHitSummary.dimensions. eVar01.data[0]
 }
 }
 (…)
 }
```

Gehen Sie beim Analysieren sorgfältig vor, um Fehler zu vermeiden.
Da dieser Code für alle Auslöser verwendet wird, sind die meisten Daten nicht erforderlich. Sie können daher leer bleiben, wenn nicht vorhanden.

### Speichern des Auslösers {#storing-triggers-js}

>[!NOTE]
>
>Es handelt sich hierbei um ein spezifisches Beispiel aus verschiedenen möglichen Implementierungen.

Dieser JS-Beispielcode speichert den Auslöser in der Datenbank.

```
function processPipelineMessage(xmlTrigger)
 {
 (…)
 var event = 
 <pipelineEvent
 xtkschema = "cus:pipelineEvent"
 _operation = "insert"
 created = {timeNow}
 lastModified = {timeNow}
 triggerType = {triggerType}
 timeGMT = {timeGMT}
 shopper_id = {shopper_id}
 data = {xmlTrigger.toXMLString()}
 />
 xtk.session.Write(event)
 return <undef/>; 
 }
```

### Einschränkungen {#constraints}

Die Leistung für diesen Code muss optimal sein, da er häufig ausgeführt wird. Andere Marketing-Aktivitäten können beeinträchtigt werden. Dies gilt besonders, wenn auf dem Marketing-Server mehr als eine Million Auslöserereignisse pro Stunde verarbeitet werden oder wenn keine richtige Optimierung vorgenommen wurde.

Der Kontext dieses JavaScripts ist begrenzt. Es sind nicht alle Funktionen der API verfügbar. Beispielsweise funktionieren &quot;getOption()&quot; und &quot;getCurrentdate()&quot; nicht.

Um eine schnellere Verarbeitung zu ermöglichen, werden mehrere Threads des Skripts gleichzeitig ausgeführt. Der Code muss Thread-sicher sein.

## Speichern der Ereignisse {#store-events}

>[!NOTE]
>
>Es handelt sich hierbei um ein spezifisches Beispiel aus verschiedenen möglichen Implementierungen.

### Pipeline-Ereignisschema {#pipeline-event-schema}

Ereignisse werden in einer Datenbanktabelle gespeichert. Sie werden in Marketing-Kampagnen verwendet, um mithilfe von Auslösern Zielkunden zu bestimmen und E-Mails anzureichern.
Zwar kann jeder Auslöser eine eigene Datenstruktur aufweisen, doch lassen sich alle Auslöser in einer einzigen Tabelle speichern.
Das Feld &quot;triggerType&quot; gibt an, von welchem Auslöser die Daten stammen.

Hier ist ein Beispiel für einen Schema-Code für diese Tabelle:

| Attribut | Typ | Titel | Beschreibung  |
|:-:|:-:|:-:|:-:|
| pipelineEventId | Lang | Primärschlüssel | Der interne Primärschlüssel des Auslösers. |
| data | Memo | Auslöserdaten | Der vollständige Inhalt der Auslöserdaten im XML-Format. Für Debugging- und Audit-Zwecke. |
| triggerType | String 50 | TriggerType | Der Name des Auslösers. Identifiziert das Verhalten des Kunden auf der Website. |
| shopper_id | String 32 | shopper_id | Die interne Kennung des Käufers. Wird durch den Abstimmungs-Workflow festgelegt. &quot;zero&quot; bedeutet, dass der Kunde in Campaign unbekannt ist. |
| shopper_key | Lang | shopper_key | Die externe Kennung des Käufers, wie von Analytics erfasst. |
| Erstellt | Datum/Uhrzeit | Erstellt | Der Zeitpunkt, zu dem das Ereignis in Campaign erstellt wurde. |
| lastModified | Datum/Uhrzeit | Zuletzt geändert | Der letzte Zeitpunkt, zu dem das Ereignis in Adobe geändert wurde. |
| timeGMT | Datum/Uhrzeit | Zeitstempel | Der Zeitpunkt, zu dem das Ereignis in Analytics erstellt wurde. |

### Anzeigen der Ereignisse {#display-events}

Die Ereignisse können mit einem einfachen Formular, das auf dem Ereignisschema basiert, angezeigt werden.

>[!NOTE]
>
>Der Knoten &quot;Pipeline Event&quot; ist nicht nativ und muss hinzugefügt werden. Außerdem muss in Campaign das zugehörige Formular erstellt werden. Diese Aufgaben sind erfahrenen Benutzern vorbehalten. Weitere Informationen finden Sie in den folgenden Abschnitten: [Navigationshierarchie](../../configuration/using/about-navigation-hierarchy.md) und [Bearbeiten von Formularen](../../configuration/using/editing-forms.md).

![](assets/triggers_7.png)

## Verarbeiten der Ereignisse {#processing-the-events}

### Abstimmungs-Workflow {#reconciliation-workflow}

Bei der Abstimmung wird der Kunde von Analytics mit der Campaign-Datenbank abgeglichen. Das Kriterium für die Abstimmung kann beispielsweise &quot;shopper_id&quot; sein.

Aus Leistungsgründen muss die Abstimmung von einem Workflow im Batch-Modus vorgenommen werden.
Die Häufigkeit muss für eine optimale Arbeitslast auf 15 Minuten gesetzt werden. Die Verzögerung zwischen dem Empfang eines Ereignisses in Adobe Campaign und dessen Verarbeitung durch einen Marketing-Workflow beträgt daher bis zu 15 Minuten.

### Optionen zur Abstimmung von Einheiten in JavaScript {#options-unit-reconciliation}

Theoretisch ist es möglich, die Abstimmungsabfrage für jeden Auslöser im JavaScript auszuführen. Das sorgt für eine höhere Leistung und schnellere Ergebnisse. Dies kann für spezifische Anwendungsfälle erforderlich sein, wenn eine Reaktionsrate erforderlich ist.

Doch das kann schwierig sein, wenn kein Index für &quot;shopper_id&quot; festgelegt ist. Wenn sich die Kriterien auf einem anderen Datenbank-Server als dem Marketing-Server befinden, wird ein Datenbank-Link mit geringer Leistung verwendet.

### Workflow bereinigen {#purge-workflow}

Auslöser werden innerhalb einer Stunde verarbeitet, sodass es keinen Grund gibt, sie lange aufzubewahren. Das Volumen kann etwa 1 Million Auslöser pro Stunde betragen. Aus diesem Grund muss ein Bereinigungs-Workflow eingerichtet werden. Bei der Bereinigung werden alle Auslöser gelöscht, die älter als drei Tage sind. Dieser Vorgang wird einmal pro Tag ausgeführt.

### Kampagnen-Workflow {#campaign-workflow}

Der Kampagnen-Workflow für Auslöser ähnelt oft anderen wiederkehrenden Kampagnen, die bereits verwendet wurden.
Beispielsweise kann er mit einer Abfrage nach den Auslösern starten, um nach bestimmten Ereignissen zu suchen, die während des letzten Tages stattgefunden haben. Diese Zielgruppe wird zum Senden der E-Mail genutzt. Anreicherungen oder Daten können vom Auslöser übernommen werden. Sie können vom Marketing-Team sicher verwendet werden, da keine Konfiguration erforderlich ist.
