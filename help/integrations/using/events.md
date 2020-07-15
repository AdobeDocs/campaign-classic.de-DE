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
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0112d5bd052ad66169225073276d1da4f3c245d8
workflow-type: tm+mt
source-wordcount: '1152'
ht-degree: 2%

---


# Triggers-Ereignisse {#events}

## Verarbeiten von Ereignissen in JavaScript {#events-javascript}

### JavaScript-Datei {#file-js}

Pipeline verwendet eine JavaScript-Funktion, um jede Meldung zu verarbeiten. Diese Funktion ist benutzerdefiniert.

Es wird in der Option **[!UICONTROL NmsPipeline_Config]** unter dem Attribut &quot;JSConnector&quot;konfiguriert. Dieses Javascript wird jedes Mal aufgerufen, wenn ein Ereignis empfangen wird. Es wird vom [!DNL pipelined] Prozess ausgeführt.

Die JS-Beispieldatei lautet &quot;cus:Trigger.js&quot;.

### JavaScript-Funktion {#function-js}

Das [!DNL pipelined] Javascript muss mit einer bestimmten Funktion Beginn werden.

Diese Funktion wird für jedes Ereignis einmal aufgerufen:

```
function processPipelineMessage(xmlTrigger) {}
```

Es sollte als

```
<undefined/>
```

Starten Sie [!DNL pipelined] nach der Bearbeitung des JS neu.

### Auslöserdatenformat {#trigger-format}

Die [!DNL trigger] Daten werden an die JS-Funktion übergeben. Es ist im XML-Format.

* Das **[!UICONTROL @triggerId]** -Attribut enthält den Namen des [!DNL trigger].
* Das **Anreicherungen** -Element im JSON-Format enthält die von Analytics generierten Daten und wird an den Auslöser angehängt.
* **[!UICONTROL @offset]** ist der &quot;Zeiger&quot;auf die Nachricht. Es gibt die Reihenfolge der Nachricht in der Warteschlange an.
* **[!UICONTROL @partitio]**n ist ein Container von Nachrichten in der Warteschlange. Der Offset ist relativ zu einer Partition. <br>Es sind etwa 15 Partitionen in der Warteschlange.

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
>Es handelt sich dabei um ein spezifisches Beispiel aus verschiedenen möglichen Implementierungen.

Der Inhalt wird in Analytics für jeden Auslöser definiert. Es ist im JSON-Format.
Beispiel: In einem Auslöser logoUpload_uploading_Visits:

* **[!UICONTROL eVar01]** kann die Shopper-ID enthalten, die zum Abgleich mit Kampagne-Empfängern verwendet wird. Es ist im Zeichenfolgenformat. <br>Es muss abgeglichen werden, um die Shopper-ID zu finden, die der Hauptschlüssel ist.

* **[!UICONTROL timeGMT]** kann die Zeit des Auslösers auf der Analytics-Seite enthalten. Es hat das Format UTC Epoch (Sekunden seit dem 01/01/1970 UTC).

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

Die Ereignis werden einzeln in der Reihenfolge des Versatzes verarbeitet. Jeder Thread der [!DNL pipelined] Prozesse verarbeitet eine andere Partition.

Der &quot;Offset&quot;des letzten abgerufenen Ereignisses wird in der Datenbank gespeichert. Wenn der Prozess gestoppt wird, wird er daher mit der letzten Meldung neu gestartet. Diese Daten werden im integrierten Schema xtk:pipelineoffset gespeichert.

Dieser Zeiger ist für jede Instanz und jeden Verbraucher spezifisch. Wenn also viele Instanzen mit unterschiedlichen Verbrauchern auf dieselbe Pipeline zugreifen, erhalten sie alle Nachrichten in derselben Reihenfolge.

Der Parameter &quot;Consumer&quot;der Pipeline-Option gibt die aufrufende Instanz an.

Derzeit gibt es keine Möglichkeit, unterschiedliche Warteschlangen für separate Umgebung wie &quot;Staging&quot;oder &quot;dev&quot;zu haben.

### Protokollierung und Fehlerverarbeitung {#logging-error-handling}

Protokolle wie logInfo() werden an das [!DNL pipelined] Protokoll weitergeleitet. Fehler wie logError() werden in das [!DNL pipelined] Protokoll geschrieben und führen dazu, dass das Ereignis in eine Wiederholungswarteschlange gestellt wird. Überprüfen Sie das Pipeline-Protokoll.
Fehlermeldungen werden in der in den [!DNL pipelined] Optionen festgelegten Dauer mehrmals wiederholt.

Für Debugging- und Überwachungszwecke werden die vollständigen Auslösedaten in die Auslösetabelle geschrieben. Sie befindet sich im Feld &quot;data&quot;im XML-Format. Alternativ dazu dient eine logInfo()-Funktion, die die Auslöserdaten enthält, demselben Zweck.

### Daten analysieren {#data-parsing}

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

Gehen Sie beim Analysieren vorsichtig vor, um Fehler zu vermeiden.
Da dieser Code für alle Auslöser verwendet wird, sind die meisten Daten nicht erforderlich. Daher kann es leer bleiben, wenn nicht vorhanden.

### Speichern des Auslösers {#storing-triggers-js}

>[!NOTE]
>
>Es handelt sich dabei um ein spezifisches Beispiel aus verschiedenen möglichen Implementierungen.

Dieser JS-Beispielcode speichert den Auslöser in der Datenbank.

```
function processPipelineMessage(xmlTrigger)
 {```
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

Die Leistung für diesen Code muss optimal sein, da er mit hohen Frequenzen ausgeführt wird. Für andere Marketing-Aktivitäten können negative Auswirkungen auftreten. Vor allem, wenn die Verarbeitung von mehr als einer Million Auslöser-Ereignis pro Stunde auf dem Marketing-Server. Oder wenn es nicht richtig eingestellt ist.

Der Kontext dieses Javascripts ist begrenzt. Es sind nicht alle Funktionen der API verfügbar. Beispielsweise funktionieren getOption() oder getCurrentdate() nicht.

Um eine schnellere Verarbeitung zu ermöglichen, werden mehrere Threads dieses Skripts gleichzeitig ausgeführt. Der Code muss threadsicher sein.

## Speichern der Ereignisse {#store-events}

>[!NOTE]
>
>Es handelt sich dabei um ein spezifisches Beispiel aus verschiedenen möglichen Implementierungen.

### Pipeline-Ereignis-Schema {#pipeline-event-schema}

Ereignis werden in einer Datenbanktabelle gespeichert. Es wird von Marketing-Kampagnen zur Zielgruppe von Kunden und zur Aufbereitung von E-Mails mithilfe von Triggern verwendet.
Obwohl jeder Auslöser eine eigene Datenstruktur haben kann, können alle Auslöser in einer einzigen Tabelle gehalten werden.
Das Feld &quot;triggerType&quot;gibt an, von welchem Auslöser die Daten stammen.

Hier ein Beispiel für einen Schema-Code für diese Tabelle:

| Attribut | Typ | Titel | Beschreibung |
|:-:|:-:|:-:|:-:|
| pipelineEventId | lang | Primärschlüssel | Der interne Primärschlüssel des Auslösers. |
| data | Memo | Auslöserdaten | Der vollständige Inhalt der Auslöserdaten im XML-Format. Für Debugging- und Prüfzwecke. |
| triggerType | Zeichenfolge 50 | TriggerType | Der Name des Auslösers. Identifiziert das Verhalten des Kunden auf der Website. |
| shopper_id | Zeichenfolge 32 | shopper_id | Die interne Kennung des Käufers. Wird durch den Abgleicharbeitsablauf festgelegt. Bei null bedeutet dies, dass der Kunde in der Kampagne unbekannt ist. |
| shopper_key | lang | shopper_key | Die Externe Kennung des Käufers, wie sie von Analytics erfasst wird. |
| created | Datum/Uhrzeit | Created | Der Zeitpunkt, zu dem das Ereignis in Kampagne erstellt wurde. |
| lastModified | Datum/Uhrzeit | Zuletzt geändert | Das letzte Mal, dass das Ereignis in Adobe geändert wurde. |
| timeGMT | Datum/Uhrzeit | Zeitstempel | Der Zeitpunkt, zu dem das Ereignis in Analytics generiert wurde. |

### Anzeigen der Ereignisse {#display-events}

Die Ereignisse können mit einem einfachen Formular auf der Grundlage des Ereignisses-Schemas angezeigt werden.

>[!NOTE]
>
>Der Knoten Pipeline-Ereignis ist nicht integriert und muss hinzugefügt werden. Das zugehörige Formular muss in Kampagne erstellt werden. Diese Vorgänge sind nur für Benutzer von Experten verfügbar. Weitere Informationen finden Sie in den folgenden Abschnitten: [Navigationshierarchie](../../configuration/using/about-navigation-hierarchy.md) und [Bearbeitung von Formularen](../../configuration/using/editing-forms.md).

![](assets/triggers_7.png)

## Verarbeitung der Ereignis {#processing-the-events}

### Abgleichungsarbeitsablauf {#reconciliation-workflow}

Bei der Abstimmung wird der Kunde von Analytics in die Kampagne-Datenbank aufgenommen. Die Kriterien für die Übereinstimmung können beispielsweise die &quot;shopper_id&quot;sein.

Aus Leistungsgründen muss die Übereinstimmung im Stapelmodus durch einen Workflow erfolgen.
Die Häufigkeit muss auf 15 Minuten eingestellt werden, um die Arbeitslast zu optimieren. Die Verzögerung zwischen dem Empfang eines Ereignisses in Adobe Campaign und seiner Verarbeitung durch einen Marketingarbeitsablauf beträgt daher bis zu 15 Minuten.

### Optionen für die Einheitenaussöhnung in JavaScript {#options-unit-reconciliation}

Theoretisch ist es möglich, die Abfrage zur Aussöhnung für jeden Auslöser in JavaScript auszuführen. Sie hat eine höhere Leistung und führt zu schnelleren Ergebnissen. Sie kann für spezifische Anwendungsfälle erforderlich sein, wenn eine Reaktivität erforderlich ist.

Es kann schwierig sein, dies zu tun, wenn kein Index für shopper_id festgelegt ist. Wenn sich die Kriterien auf einem separaten Datenbankserver als dem Marketingserver befinden, wird ein Datenbanklink verwendet, der eine schlechte Leistung aufweist.

### Arbeitsablauf löschen {#purge-workflow}

Auslöser werden innerhalb der Stunde verarbeitet, sodass es keinen Grund gibt, sie für eine lange Zeit zu behalten. Das Volumen kann etwa 1 Million Auslöser pro Stunde betragen. Es erklärt, warum ein Bereinigungsarbeitsablauf eingerichtet werden muss. Die Bereinigung löscht alle Auslöser, die älter als drei Tage sind und einmal pro Tag ausgeführt werden.

### Arbeitsablauf für Kampagnen {#campaign-workflow}

Der Arbeitsablauf für die Kampagne von Auslösern ist oft ähnlich wie andere wiederkehrende Kampagnen, die verwendet wurden.
Beispielsweise kann es mit einer Abfrage auf den Auslösern, die während des letzten Tages nach bestimmten Ereignissen suchen, Beginn geben. Diese Zielgruppe wird verwendet, um die E-Mail zu senden. Anreicherungen oder Daten können vom Auslöser stammen. Es kann von Marketing sicher verwendet werden, da es keine Konfiguration erfordert.
