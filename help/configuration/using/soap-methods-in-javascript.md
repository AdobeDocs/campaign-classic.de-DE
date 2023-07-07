---
product: campaign
title: SOAP-Methoden in JavaScript
description: SOAP-Methoden in JavaScript
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
exl-id: 62020447-fe59-4363-994d-de4d8032bbd7
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 9%

---

# SOAP-Methoden in JavaScript{#soap-methods-in-javascript}

Dies ist das JavaScript, das auf dem Adobe Campaign-Server ausgeführt wird.

## Statische Methoden {#static-methods}

Auf statische SOAP-Methoden kann zugegriffen werden, indem eine Methode für das Objekt aufgerufen wird, das das Schema darstellt. Schemas sind Eigenschaften von &quot;namespace&quot;-Objekten. Bei diesen Namespaces handelt es sich um globale Variablen. Daher stellen beispielsweise xtk- oder nms-Variablen die entsprechenden Namespaces dar

Im folgenden Beispiel wird die statische PostEvent-Methode des xtk:workflow-Schemas aufgerufen:

```
xtk.workflow.PostEvent("WKF1", "signal", "", $recipient-id='123', false) 
```

## Nicht statische Methoden {#non-static-methods}

Um nicht statische SOAP-Methoden zu verwenden, muss zunächst eine Entität mit den Methoden &quot;get&quot;oder &quot;create&quot;für die entsprechenden Schemas abgerufen werden.

Im folgenden Beispiel wird die ExecuteQuery-Methode des Schemas &quot;xtk:queryDef&quot;aufgerufen:

```
var query = xtk.queryDef.create(
  <queryDef schema="xtk:workflow" operation="select">
    <select>
      <node expr="@internalName"/>
    </select>
  </queryDef>
)

var res = query.ExecuteQuery()

for each (var w in res.workflow) 
  logInfo(w.@internalName)
```

## Beispiele {#examples}

* Abfrage zur Empfängertabelle mit &quot;get&quot;-Vorgang:

  ```
  var query = xtk.queryDef.create(  
    <queryDef schema="nms:recipient" operation="get">    
      <select>      
        <node expr="@firstName"/>      
        <node expr="@lastName"/>      
        <node expr="@email"/>    
      </select>    
      <where>      
        <condition expr="@email = 'peter.martinez@adobe.com'"/>    
      </where>  
    </queryDef>)
  
  var recipient = query.ExecuteQuery()
  
  logInfo(recipient.@firstName)
  logInfo(recipient.@lastName)
  ```

* Abfrage zur Empfängertabelle mit dem Vorgang &quot;select&quot;:

  ```
  var query = xtk.queryDef.create(  
    <queryDef schema="nms:recipient" operation="select">    
      <select>      
        <node expr="@email"/>      
        <node expr="@lastName"/>      
        <node expr="@firstName"/>    
      </select>    
      <where>      
        <condition expr="@age > 25"/>    
      </where>    
    </queryDef>)
  
  var res = query.ExecuteQuery()
  
  for each (var recipient in res.recipient) 
  {  
    logInfo(recipient.@email)  
    logInfo(recipient.@firstName)  
    logInfo(recipient.@lastName)
  }
  ```

* Schreiben von Daten in die Empfängertabelle:

  ```
  xtk.session.Write(<recipient _operation="insert" lastName="Martinez" firstName="Peter" xtkschema="nms:recipient"/>);
  ```
