---
product: campaign
title: Filtern von Schemata
description: Filtern von Schemata
audience: configuration
content-type: reference
topic-tags: editing-schemas
exl-id: 009bed25-cd35-437c-b789-5b58a6d2d7c6
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# Filterschemata{#filtering-schemas}

## Systemfilter {#system-filters}

Sie können den Schemazugriff nach bestimmten Benutzern filtern, abhängig von deren Berechtigungen. Mit Systemfiltern können Sie die Lese- und Schreibberechtigungen von Entitäten verwalten, die in Schemas beschrieben sind, und dabei die Parameter **readAccess** und **writeAccess** verwenden.

>[!NOTE]
>
>Diese Einschränkung gilt nur für nicht technische Benutzer: Ein technischer Benutzer mit entsprechenden Berechtigungen oder mithilfe eines Workflows kann Daten abrufen und aktualisieren.

* **readAccess**: bietet schreibgeschützten Zugriff auf Schemadaten.

   **Warnung**  - Alle verknüpften Tabellen müssen mit derselben Einschränkung versehen werden. Diese Konfiguration kann sich auf die Leistung auswirken.

* **writeAccess**: bietet Schreibzugriff auf Schemadaten.

Diese Filter werden auf der Hauptseite **element** der Schemas eingegeben und können, wie in den folgenden Beispielen gezeigt, gebildet werden, um den Zugriff zu beschränken.

* SCHREIBberechtigungen beschränken

   Hier wird der Filter verwendet, um WRITE-Berechtigungen für das Schema für Benutzer ohne ADMINISTRATION zu verweigern. Dies bedeutet, dass nur Administratoren Schreibberechtigungen für Entitäten haben, die von diesem Schema beschrieben werden.

   ```
   <sysFilter name="writeAccess">      
    <condition enabledIf="hasNamedRight('admin')=false" expr="FALSE"/>    
   </sysFilter>
   ```

* READ- und WRITE-Berechtigungen beschränken:

   Hier wird der Filter verwendet, um die LESE- und WRITE-Berechtigungen für das Schema für alle Operatoren zu deaktivieren. Nur das Konto **internal**, dargestellt durch den Ausdruck &quot;$(loginId)!= 0&quot;, hat diese Berechtigungen.

   ```
   <sysFilter name="readAccess"> 
    <condition enabledIf="$(loginId)!=0" expr="FALSE"/>
   </sysFilter>
   
   <sysFilter name="writeAccess">  
    <condition enabledIf="$(loginId)!=0" expr="FALSE"/>
   </sysFilter>
   ```

   Mögliche **expr** Attributwerte, die zur Definition der Bedingung verwendet werden, sind TRUE oder FALSE.

>[!NOTE]
>
>Wenn kein Filter angegeben ist, verfügen alle Benutzer über Lese- und Schreibberechtigungen für das Schema.

## Integrierte Protect-Schemata {#protecting-built-in-schemas}

Standardmäßig sind integrierte Schemata nur mit WRITE-Berechtigungen für Benutzer mit ADMINISTRATION-Rechten zugänglich:

* ncm:publishing
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

>[!IMPORTANT]
>
>Lese- und WRITE-Berechtigungen für das Schema **xtk:sessionInfo** sind nur für das interne Konto einer Adobe Campaign-Instanz zugänglich.

## Systemfilter integrierter Schemata ändern {#modifying-system-filters-of-built-in-schemas}

Sie können weiterhin die Systemfilter der nativen Schemas ändern, die aufgrund von Kompatibilitätsproblemen mit älteren Versionen standardmäßig geschützt sind.

>[!NOTE]
>
>Adobe empfiehlt jedoch, die Standardparameter nicht zu ändern, um eine optimale Sicherheit zu gewährleisten.

1. Erstellen Sie eine Erweiterung für das betreffende Schema oder öffnen Sie eine vorhandene Erweiterung.
1. Fügen Sie ein untergeordnetes Element **`<sysfilter name="<filter name>" _operation="delete"/>`** im Hauptelement hinzu, um die Anwendung des Filters unter demselben im Ursprungsschema zu löschen.
1. Bei Bedarf können Sie einen neuen Filter hinzufügen, wie unter [Systemfilter](#system-filters) beschrieben.
