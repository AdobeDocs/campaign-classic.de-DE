---
solution: Campaign Classic
product: campaign
title: Filtern von Schemata
description: Filtern von Schemata
audience: configuration
content-type: reference
topic-tags: editing-schemas
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 1%

---


# Filtern von Schemata{#filtering-schemas}

## System-Filter {#system-filters}

Sie können den Zugriff auf Schemas je nach Zugriffsberechtigungen filtern. Mit System-Filtern können Sie die Lese- und Schreibberechtigungen von Entitäten, die in Schemas detailliert sind, mithilfe von **readAccess** - und **writeAccess** -Parametern verwalten.

>[!NOTE]
>
>Diese Einschränkung gilt nur für nicht technische Nutzer: ein technischer Benutzer mit entsprechenden Berechtigungen oder mithilfe eines Workflows Daten abrufen und aktualisieren kann.

* **readAccess**: bietet schreibgeschützten Zugriff auf Schema-Daten.

   **Warnung** : Alle verknüpften Tabellen müssen mit derselben Einschränkung versehen sein. Diese Konfiguration kann sich auf die Leistung auswirken.

* **writeAccess**: bietet Schreibzugriff auf Schema-Daten.

Diese Filter werden auf der Haupt- **Element** -Ebene der Schema eingegeben und können, wie in den folgenden Beispielen dargestellt, gebildet werden, um den Zugriff einzuschränken.

* Schreibberechtigungen einschränken

   Hier wird der Filter verwendet, um WRITE-Berechtigungen für das Schema für Operatoren ohne die Berechtigung ADMINISTRATION zu deaktivieren. Das bedeutet, dass nur Administratoren Schreibberechtigungen für Entitäten haben, die in diesem Schema beschrieben werden.

   ```
   <sysFilter name="writeAccess">      
    <condition enabledIf="hasNamedRight('admin')=false" expr="FALSE"/>    
   </sysFilter>
   ```

* Berechtigungen zum Lesen und Schreiben einschränken:

   Hier wird der Filter verwendet, um sowohl READ- als auch WRITE-Berechtigungen für das Schema für alle Operatoren zu deaktivieren. Nur das **interne** Konto, vertreten durch den Ausdruck &quot;$(loginId)!=0&quot;, hat diese Berechtigungen.

   ```
   <sysFilter name="readAccess"> 
    <condition enabledIf="$(loginId)!=0" expr="FALSE"/>
   </sysFilter>
   
   <sysFilter name="writeAccess">  
    <condition enabledIf="$(loginId)!=0" expr="FALSE"/>
   </sysFilter>
   ```

   Mögliche **expr** -Attributwerte, die zur Definition der Bedingung verwendet werden, sind TRUE oder FALSE.

>[!NOTE]
>
>Wenn kein Filter angegeben ist, verfügen alle Operatoren über Lese- und Schreibberechtigungen für das Schema.

## Schutz integrierter Schema {#protecting-built-in-schemas}

Standardmäßig sind integrierte Schema nur mit WRITE-Berechtigungen für Benutzer mit ADMINISTRATION-Rechten verfügbar:

* ncm:veröffentlichen
* nl:monitoring
* nms:calendar
* xtk:builder
* xtk:connections
* xtk:dbInit
* xtk:entityBackupNew
* xtk:entityBackupOriginal
* xtk:entityOriginal
* xtk:form
* xtk:funcList
* xtk:fusion
* xtk:image
* xtk:javascript
* xtk:jssp
* xtk:jst
* xtk:navtree
* xtk:operatorGroup
* xtk:package
* xtk:queryDef
* xtk:resourceMenu
* xtk:rights
* xtk:Schema
* xtk:scriptContext
* xtk:specFile
* xtk:sql
* xtk:sqlSchema
* xtk:srcSchema
* xtk:strings
* xtk:xslt

>[!IMPORTANT]
>
>READ- und WRITE-Berechtigungen für das **xtk:sessionInfo** -Schema sind nur für das interne Konto einer Adobe Campaign-Instanz verfügbar.

## Ändern der Filter von integrierten Schemas {#modifying-system-filters-of-built-in-schemas}

Sie können weiterhin die Filter der vordefinierten Schema ändern, die aufgrund von Kompatibilitätsproblemen mit älteren Versionen standardmäßig geschützt sind.

>[!NOTE]
>
>Adobe empfiehlt jedoch, die Standardparameter nicht zu ändern, um eine optimale Sicherheit zu gewährleisten.

1. Erstellen Sie eine Erweiterung für das betreffende Schema oder öffnen Sie eine bestehende Erweiterung.
1. hinzufügen Sie ein untergeordnetes Element **`<sysfilter name="<filter name>" _operation="delete"/>`** im Hauptelement, um die Anwendung des Filters im gleichen Schema der Herkunft zu löschen.
1. Wenn Sie möchten, können Sie einen neuen Filter hinzufügen, wie unter [Systemfilter](#system-filters)beschrieben.

