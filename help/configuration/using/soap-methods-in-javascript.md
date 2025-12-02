---
product: campaign
title: SOAP-Methoden in JavaScript
feature: Configuration, Instance Settings
description: SOAP-Methoden in JavaScript
role: Developer
exl-id: 62020447-fe59-4363-994d-de4d8032bbd7
source-git-commit: 9f5205ced6b8d81639d4d0cb6a76905a753cddac
workflow-type: tm+mt
source-wordcount: '134'
ht-degree: 9%

---

# SOAP-Methoden in JavaScript{#soap-methods-in-javascript}

Dies ist die JavaScript, die auf dem Adobe Campaign-Server ausgeführt wird.

## Statische Methoden {#static-methods}

Auf statische SOAP-Methoden kann durch Aufrufen einer -Methode für das -Objekt zugegriffen werden, das das Schema darstellt. Schemata sind Eigenschaften von „namespace“-Objekten. Diese Namespaces sind globale Variablen, daher stellen beispielsweise xtk- oder nms-Variablen die entsprechenden Namespaces dar

Im folgenden Beispiel wird die statische PostEvent-Methode des xtk:workflow-Schemas aufgerufen:

```
xtk.workflow.PostEvent("WKF1", "signal", "", $recipient-id='123', false) 
```

## Nicht statische Methoden {#non-static-methods}

Um nicht statische SOAP-Methoden zu verwenden, müssen Sie zunächst eine Entität mit den Methoden „get“ oder „create“ für die entsprechenden Schemata abrufen.

Im folgenden Beispiel wird die ExecuteQuery-Methode des Schemas „xtk:queryDef aufgerufen:

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

* Abfrage der Empfängertabelle mit einer „get“-Operation:

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

* Abfrage der Empfängertabelle mit dem Vorgang „Auswählen“:

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
