---
title: SOAP-Methoden in JavaScript
seo-title: SOAP-Methoden in JavaScript
description: SOAP-Methoden in JavaScript
seo-description: null
page-status-flag: never-activated
uuid: 8fd1aabc-e51a-433d-835f-6b5a717c7aeb
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: api
discoiquuid: 815d3eb9-ac45-441f-9a5f-0cd505fcf88a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# SOAP-Methoden in JavaScript{#soap-methods-in-javascript}

Dies ist das JavaScript, das auf dem Adobe Campaign-Server ausgeführt wird.

## Statische Methoden {#static-methods}

Auf statische SOAP-Methoden wird zugegriffen, indem eine Methode für das Objekt aufgerufen wird, das das Schema darstellt. Schemas sind Eigenschaften von &#39;namespace&#39;-Objekten. Diese Namespaces sind globale Variablen, daher stellen z. B. xtk- oder nms-Variablen die entsprechenden Namespaces dar

Im folgenden Beispiel wird die statische PostEvent-Methode des Schemas xtk:workflow aufgerufen:

```
xtk.workflow.PostEvent("WKF1", "signal", "", $recipient-id='123', false) 
```

## Nicht-statische Methoden {#non-static-methods}

Um nicht-statische SOAP-Methoden zu verwenden, muss zunächst eine Entität mit den Methoden &quot;get&quot;oder &quot;create&quot;für die entsprechenden Schemata abgerufen werden.

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

* Abfrage auf der Empfängertabelle mit einer &quot;get&quot;-Operation:

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

* Abfrage auf der Empfängertabelle mit einem &quot;Select&quot;-Vorgang:

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

* Daten in die Empfängertabelle schreiben:

   ```
   xtk.session.Write(<recipient _operation="insert" lastName="Martinez" firstName="Peter" xtkschema="nms:recipient"/>);
   ```

