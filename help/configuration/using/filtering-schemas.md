---
product: campaign
title: Filtern von Schemata
description: Filtern von Schemata
feature: Custom Resources
role: Data Engineer, Developer
exl-id: 009bed25-cd35-437c-b789-5b58a6d2d7c6
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 79%

---

# Filtern von Schemata{#filtering-schemas}

## Systemfilter {#system-filters}

Sie können den Schema-Zugriff abhängig von Berechtigungen nach bestimmten Benutzern filtern. Mit Systemfiltern können Sie die Lese- und Schreibberechtigungen von Entitäten verwalten, die in Schemata beschrieben sind. Dabei verwenden Sie die Parameter **readAccess** und **writeAccess**.

>[!NOTE]
>
>Diese Einschränkung gilt nur für nicht-technische Benutzer: Ein technischer Benutzer mit entsprechenden Berechtigungen oder unter Verwendung eines Workflows kann die Daten abrufen und aktualisieren.

* **readAccess**: bietet schreibgeschützten Zugriff auf Schemadaten.

  **Warnung**  - Alle verknüpften Tabellen müssen mit derselben Einschränkung versehen werden. Diese Konfiguration kann die Performance beeinträchtigen.

* **writeAccess**: bietet Schreibzugriff auf Schemadaten.

Diese Filter werden auf der **Hauptelementebene** der Schemata eingegeben und können, wie in den folgenden Beispielen gezeigt, zur Einschränkung des Zugriffs gebildet werden.

* SCHREIB-Berechtigungen beschränken

  Hier wird der Filter verwendet, um Betreibern ohne ADMINISTRATOR-Berechtigung die SCHREIB-Berechtigung für das Schema zu verweigern. Das bedeutet, dass nur Administratoren Schreibrechte für Entitäten haben, die durch dieses Schema beschrieben werden.

  ```
  <sysFilter name="writeAccess">      
   <condition enabledIf="hasNamedRight('admin')=false" expr="FALSE"/>    
  </sysFilter>
  ```

* Schränken Sie die LESE- und SCHREIB-Berechtigungen ein:

  Hier wird der Filter verwendet, um sowohl LESE- als auch SCHREIB-Berechtigungen für das Schema für alle Operatoren zu verbieten. Nur das **interne** Konto, dargestellt durch den Ausdruck &quot;$(loginId)!=0&quot;, hat diese Berechtigungen.

  ```
  <sysFilter name="readAccess"> 
   <condition enabledIf="$(loginId)!=0" expr="FALSE"/>
  </sysFilter>
  
  <sysFilter name="writeAccess">  
   <condition enabledIf="$(loginId)!=0" expr="FALSE"/>
  </sysFilter>
  ```

  Mögliche **expr**-Attributwerte, die zur Definition der Bedingung verwendet werden, sind TRUE oder FALSE.

>[!NOTE]
>
>Wenn kein Filter angegeben ist, verfügen alle Benutzer über Lese- und Schreibberechtigungen für das Schema.

## Integrierte Schemata schützen {#protecting-built-in-schemas}

Standardmäßig sind integrierte Schemata nur mit SCHREIB-Berechtigungen für Benutzer mit ADMINISTRATOR-Rechten zugänglich:

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
>LESE- und SCHREIB-Berechtigungen für das Schema **xtk:sessionInfo** sind nur über das interne Konto einer Adobe Campaign-Instanz zugänglich.

## Systemfilter der integrierten Schemata ändern {#modifying-system-filters-of-built-in-schemas}

Sie können die Systemfilter der vordefinierten Schemata, die aufgrund von Kompatibilitätsproblemen mit älteren Versionen standardmäßig geschützt sind, weiterhin ändern.

>[!NOTE]
>
>Adobe empfiehlt jedoch, die Standardparameter nicht zu ändern, um optimale Sicherheit zu gewährleisten.

1. Erstellen Sie eine Erweiterung für das betreffende Schema oder öffnen Sie eine vorhandene Erweiterung.
1. Fügen Sie ein untergeordnetes Element **`<sysfilter name="<filter name>" _operation="delete"/>`** im Hauptelement hinzu, um die Anwendung des Filters unter demselben Element im Ursprungsschema zu löschen.
1. Wenn Sie möchten, können Sie einen neuen Filter hinzufügen, wie unter [&#x200B; beschrieben](#system-filters).
