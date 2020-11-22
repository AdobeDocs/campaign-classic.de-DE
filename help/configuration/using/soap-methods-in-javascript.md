---
solution: Campaign Classic
product: campaign
title: SOAP-Methoden in JavaScript
description: SOAP-Methoden in JavaScript
audience: configuration
content-type: reference
topic-tags: api
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 9%

---


# SOAP-Methoden in JavaScript{#soap-methods-in-javascript}

Dies ist das JavaScript, das auf dem Adobe Campaign-Server ausgeführt wird.

## Statische Methoden {#static-methods}

Statische SOAP-Methoden werden aufgerufen, indem eine Methode für das Objekt aufgerufen wird, das das Schema darstellt. Schema sind Eigenschaften von &quot;Namensraum&quot;-Objekten. Bei diesen Namensräumen handelt es sich um globale Variablen. Daher stellen z. B. xtk- oder nms-Variablen die entsprechenden Namensraum dar.

Im folgenden Beispiel wird die statische PostEvent-Methode des Schemas xtk:workflow aufgerufen:

```
xtk.workflow.PostEvent("WKF1", "signal", "", $recipient-id='123', false) 
```

## Nicht-statische Methoden {#non-static-methods}

Um nicht-statische SOAP-Methoden zu verwenden, muss zunächst eine Entität mit den Methoden &quot;get&quot;oder &quot;create&quot;für die entsprechenden Schema abgerufen werden.

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

* Abfrage auf der Empfänger-Tabelle mit einer &quot;get&quot;-Operation:

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

* Abfrage auf der Empfänger-Tabelle mit einem &quot;Select&quot;-Vorgang:

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

* Daten in die Empfänger-Tabelle schreiben:

   ```
   xtk.session.Write(<recipient _operation="insert" lastName="Martinez" firstName="Peter" xtkschema="nms:recipient"/>);
   ```

