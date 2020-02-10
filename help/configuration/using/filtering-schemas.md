---
title: Filtern von Schemata
seo-title: Filtern von Schemata
description: Filtern von Schemata
seo-description: null
page-status-flag: never-activated
uuid: 04a90785-3084-42fd-85af-77bc28687579
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: 64d4c5b8-db0b-4287-8d30-4bf09878a401
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Filtern von Schemata{#filtering-schemas}

## Systemfilter {#system-filters}

Sie können den Schemazugriff auf bestimmte Benutzer je nach ihren Berechtigungen filtern. Mit Systemfiltern können Sie die Lese- und Schreibberechtigungen von Entitäten, die in Schemas beschrieben sind, mithilfe von **readAccess** - und **writeAccess** -Parametern verwalten.

>[!NOTE]
>
>Diese Einschränkung gilt nur für nicht technische Nutzer: ein technischer Benutzer mit entsprechenden Berechtigungen oder mithilfe eines Workflows Daten abrufen und aktualisieren kann.

* **readAccess**: bietet schreibgeschützten Zugriff auf Schemadaten.

   **Warnung** : Alle verknüpften Tabellen müssen mit derselben Einschränkung versehen sein. Diese Konfiguration kann sich auf die Leistung auswirken.

* **writeAccess**: bietet Schreibzugriff auf Schemadaten.

Diese Filter werden auf der Haupt- **Element** -Ebene der Schemata eingegeben und können, wie in den folgenden Beispielen gezeigt, gebildet werden, um den Zugriff einzuschränken.

* Schreibberechtigungen einschränken

   Hier wird der Filter verwendet, um WRITE-Berechtigungen für das Schema für Operatoren ohne die Berechtigung ADMINISTRATION zu deaktivieren. Das bedeutet, dass nur Administratoren Schreibberechtigungen für Entitäten haben, die in diesem Schema beschrieben werden.

   ```
   <sysFilter name="writeAccess">      
    <condition enabledIf="hasNamedRight('admin')=false" expr="FALSE"/>    
   </sysFilter>
   ```

* Berechtigungen zum Lesen und Schreiben einschränken:

   Hier wird der Filter verwendet, um sowohl READ- als auch WRITE-Berechtigungen für das Schema für alle Operatoren zu deaktivieren. Nur das **interne** Konto, dargestellt durch den Ausdruck &quot;$(loginId)!=0&quot;, hat diese Berechtigungen.

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

## Schutz integrierter Schemata {#protecting-built-in-schemas}

Standardmäßig sind integrierte Schemas nur mit WRITE-Berechtigungen für Benutzer mit ADMINISTRATION-Rechten verfügbar:

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
* xtk:schema
* xtk:scriptContext
* xtk:specFile
* xtk:sql
* xtk:sqlSchema
* xtk:srcSchema
* xtk:strings
* xtk:xslt

>[!CAUTION]
>
>READ- und WRITE-Berechtigungen für das **Schema &quot;xtk:sessionInfo** &quot;sind nur für das interne Konto einer Adobe Campaign-Instanz verfügbar.

## Ändern von Systemfiltern integrierter Schemata {#modifying-system-filters-of-built-in-schemas}

Sie können die Systemfilter der standardmäßig geschützten vordefinierten Schemata weiterhin ändern, da Kompatibilitätsprobleme mit älteren Versionen auftreten.

>[!NOTE]
>
>Adobe empfiehlt jedoch, die Standardparameter nicht zu ändern, um eine optimale Sicherheit zu gewährleisten.

1. Erstellen Sie eine Erweiterung für das betreffende Schema oder öffnen Sie eine vorhandene Erweiterung.
1. Fügen Sie ein untergeordnetes Element **`<sysfilter name="<filter name>" _operation="delete"/>`** im Hauptelement hinzu, um die Anwendung des Filters unter dem gleichen im Ursprungsschema zu löschen.
1. Wenn Sie möchten, können Sie einen neuen Filter hinzufügen, wie unter [Systemfilter](#system-filters)beschrieben.

