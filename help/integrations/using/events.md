---
title: Konfigurieren von Ereignissen
description: Erfahren Sie, wie Sie Ereignis für die benutzerdefinierte Implementierung konfigurieren
page-status-flag: never-activated
uuid: e2db7bdb-8630-497c-aacf-242734cc0a72
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 1c20795d-748c-4f5d-b526-579b36666e8f
translation-type: tm+mt
source-git-commit: 48acf8cbc52a54a2dd08f0b8f29be57d4e5e006f
workflow-type: tm+mt
source-wordcount: '1205'
ht-degree: 95%

---


# Konfigurieren von Ereignissen für eine benutzerdefinierte Implementierung {#events}

Diese Konfiguration enthält benutzerspezifische Anpassungen. Sie erfordert:

* Grundkenntnisse der JSON-, XML- und JavaScript-Analyse in Adobe Campaign.
* Grundkenntnisse der QueryDef- und Writer-APIs.
* Grundverständnis der Verschlüsselung und Authentifizierung mit privaten Schlüsseln.

Da die Bearbeitung des Javascript-Codes technische Fähigkeiten erfordert, versuchen Sie es bitte nicht ohne das richtige Verständnis.

## Verarbeiten von Ereignissen in JavaScript {#events-javascript}

### JavaScript-Datei {#file-js}

Die Pipeline verwendet eine JavaScript-Funktion, um jede Nachricht zu verarbeiten. Diese Funktion ist benutzerdefiniert.

Sie wird in der Option **[!UICONTROL NmsPipeline_Config]** unter dem Attribut &quot;JSConnector&quot; konfiguriert. Dieses JavaScript wird jedes Mal aufgerufen, wenn ein Ereignis empfangen wird. Es wird vom [!DNL pipelined]-Prozess ausgeführt.

Die JavaScript-Beispieldatei lautet &quot;cus:Trigger.js&quot;.

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

You should restart [!DNL pipelined] after editing the Javascript.

### Datenformat des Auslösers {#trigger-format}

Die [!DNL trigger]-Daten werden im XML-Format an die JS-Funktion übergeben.

* Das **[!UICONTROL @triggerId]**-Attribut enthält den Namen des [!DNL trigger].
* Das Element **Anreicherungen** im JSON-Format enthält die von Adobe Analytics generierten Daten und wird an den Auslöser angehängt.
* **[!UICONTROL @offset]** ist der &quot;Zeiger&quot; auf die Nachricht. Er gibt die Reihenfolge der Nachrichten in der Warteschlange an.
* **[!UICONTROL @partition]** ist ein Container mit Nachrichten, die sich in der Warteschlange befinden. Der Versatz ist relativ zu einer Partition. <br>Es gibt etwa 15 Partitionen in der Warteschlange.

Beispiel:

```
<trigger offset="1500435" partition="4" triggerId="LogoUpload_1_Visits_from_specific_Channel_or_ppp">
 <enrichments>{"analyticsHitSummary":{"dimensions":{" eVar01":{"type":"string","data":["PI4INE1ETDF6UK35GO13X7HO2ITLJHVH"],"name":" eVar01","source":"session summary"}, "timeGMT":{"type":"int","data":[1469164186,1469164195],"name":"timeGMT","source":"session summary"}},"products":{}}}</enrichments>
 <aliases/>
 </trigger>
```

### Anreicherung von Datenformaten {#enrichment-format}

>[!NOTE]
>
>Es handelt sich hierbei um ein spezifisches Beispiel aus verschiedenen möglichen Implementierungen.

Der Inhalt wird für jeden Auslöser in Adobe Analytics im JSON-Format definiert.
Zum Beispiel im Auslöser &quot;logoUpload_uploading_Visits&quot;:

* **[!UICONTROL eVar01]** kann die Käufer-ID im Zeichenfolgenformat (&quot;String&quot;) enthalten, die zur Abstimmung mit Adobe Campaign-Empfängern verwendet wird. <br>Sie muss abgestimmt werden, um die Käufer-ID zu ermitteln, die den Primärschlüssel darstellt.

* **[!UICONTROL timeGMT]** kann die Uhrzeit des Auslösers auf Seite von Adobe Analytics im UTC Epoch-Format enthalten (Sekunden seit 1.1.1970 UTC).

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

### Reihenfolge der Verarbeitung von Ereignissen{#order-events}

Die Ereignisse werden nacheinander in der Reihenfolge des Versatzes verarbeitet. Jeder Thread des [!DNL pipelined]-Prozesses verarbeitet eine andere Partition.

Der &quot;Versatz&quot; des letzten abgerufenen Ereignisses wird in der Datenbank gespeichert. Wenn der Prozess angehalten wird, startet er daher bei der letzten Nachricht neu. Diese Daten werden im nativen Schema &quot;xtk:pipelineOffset&quot; gespeichert.

Dieser Zeiger ist für jede Instanz und jeden Verbraucher spezifisch. Wenn verschiedene Instanzen auf dieselbe Pipeline mit unterschiedlichen Verbrauchern zugreifen, erhalten diese also alle Nachrichten in derselben Reihenfolge.

Der Parameter **consumer** der Pipeline-Option identifiziert die aufrufende Instanz.

Derzeit gibt es keine Möglichkeit, unterschiedliche Warteschlangen für separate Umgebungen wie &quot;staging&quot; oder &quot;dev&quot; zu nutzen.

### Protokollierung und Fehlerbehandlung {#logging-error-handling}

Logs wie &quot;logInfo()&quot; werden an das [!DNL pipelined]-Log weitergeleitet. Fehler wie &quot;logError()&quot; werden in das [!DNL pipelined]-Log geschrieben und führen dazu, dass das Ereignis in eine Warteschlange für erneute Versuche gestellt wird. In diesem Fall sollten Sie das pipelined-Log überprüfen.
Bei fehlerhaften Nachrichten werden im Zeitraum, der in den [!DNL pipelined]-Optionen festgelegt ist, mehrmals erneute Versuche ausgeführt.

Zu Debugging- und Überwachungszwecken werden die vollständigen Auslöserdaten im Feld &quot;data&quot; der Auslösertabelle im XML-Format geschrieben. Alternativ dazu sind die Auslöserdaten auch in &quot;logInfo()&quot; verfügbar.

### Analysieren der Daten {#data-parsing}

Dieser JavaScript-Beispielcode analysiert die eVar01 in den Anreicherungen.

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

Dieser Code erfordert optimale Leistung, da er mit hoher Frequenz ausgeführt wird, was sich u. U. negativ auf andere Marketing-Aktivitäten auswirken kann. Das gilt insbesondere, wenn mehr als 1 Million Auslöserereignisse pro Stunde auf dem Marketing-Server verarbeitet werden oder wenn der Server nicht entsprechend angepasst ist.

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

Bei der Abstimmung gleicht Adobe Analytics den Kunden mit der Adobe Campaign-Datenbank ab. Das Kriterium für die Abstimmung kann beispielsweise &quot;shopper_id&quot; sein.

Aus Leistungsgründen muss die Abstimmung von einem Workflow im Batch-Modus vorgenommen werden.
Die Häufigkeit muss für eine optimale Arbeitslast auf 15 Minuten gesetzt werden. Die Verzögerung zwischen dem Empfang eines Ereignisses in Adobe Campaign und dessen Verarbeitung durch einen Marketing-Workflow beträgt daher bis zu 15 Minuten.

### Optionen zur Abstimmung von Einheiten in JavaScript {#options-unit-reconciliation}

Es ist möglich, die Abstimmungsabfrage für jeden Auslöser im JavaScript auszuführen. Das sorgt für eine höhere Leistung und schnellere Ergebnisse. Dies kann für spezifische Anwendungsfälle erforderlich sein, wenn eine Reaktionsrate erforderlich ist.

Ist jedoch kein Index für &quot;shopper_id&quot; festgelegt, lässt sich dies nur schwer umsetzen. Wenn sich die Kriterien auf einem anderen Datenbank-Server als dem Marketing-Server befinden, wird ein Datenbank-Link mit geringer Leistung verwendet.

### Workflow bereinigen {#purge-workflow}

Auslöser werden innerhalb der jeweiligen Stunde verarbeitet. Das Volumen kann etwa 1 Million Auslöser pro Stunde betragen. Aus diesem Grund muss ein Bereinigungs-Workflow eingerichtet werden. Die Bereinigung wird einmal pro Tag ausgeführt und löscht alle Auslöser, die älter als drei Tage sind.

### Kampagnen-Workflow {#campaign-workflow}

Der Kampagnen-Workflow für Auslöser ähnelt oft anderen wiederkehrenden Kampagnen, die bereits verwendet wurden.
Beispielsweise kann er mit einer Abfrage nach den Auslösern starten, um nach bestimmten Ereignissen zu suchen, die während des letzten Tages stattgefunden haben. Diese Zielgruppe wird zum Senden der E-Mail genutzt. Anreicherungen oder Daten können vom Auslöser übernommen werden. Sie können vom Marketing-Team sicher verwendet werden, da keine Konfiguration erforderlich ist.
