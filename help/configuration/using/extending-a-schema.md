---
title: Erweitern eines Schemas
seo-title: Erweitern eines Schemas
description: Erweitern eines Schemas
seo-description: null
page-status-flag: never-activated
uuid: 1767b9de-1d72-4ece-aeec-87f83862d81c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: 1c9af980-4e6b-44dc-af61-dd284863ec7d
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: e7ff12260d875b85256c8678fa8d100fd355398e

---


# Erweitern eines Schemas{#extending-a-schema}

>[!CAUTION]
>
>Einige integrierte Schemata dürfen nicht erweitert werden: hauptsächlich für die folgenden Einstellungen:\
>**dataSource=&quot;file&quot;** und **mappingType=&quot;xmlFile&quot;**.\
>Die folgenden Schemata dürfen nicht erweitert werden: **xtk:entityBackupNew**, **xtk:entityBackupOriginal**, **xtk:entityOriginal**, **xtk:form**, **xtk:srcSchema********************************************,ncm:publishing,nl:monitoringinsg,nms:remoteTracking,xtk:userAgentRules,xtk:builderxtk:connections,xtkInit, xtk:funcList,xtk:fusion, xtk:fusion: jst**, **xtk:navtree**, **xtk:queryDef**, **xtk:resourceMenu**, **xtk:schema**, **xtk:scriptContextText, xtk:**************xtk:sqlSchemaSession:strings.
>Diese Liste ist nicht erschöpfend.

Es gibt zwei Methoden zum Erweitern eines vorhandenen Schemas:

1. Direktes Ändern des Quellschemas.
1. Erstellen eines anderen Schemas mit demselben Namen, jedoch einem anderen Namespace. Der Vorteil besteht darin, dass Sie eine Tabelle erweitern können, ohne das ursprüngliche Schema ändern zu müssen.

   Das Stammelement des Schemas muss das Attribut **extendedSchema** mit dem Namen des Schemas enthalten, das als Wert erweitert werden soll.

   Ein Erweiterungsschema hat kein eigenes Schema: Das aus dem Quellschema generierte Schema wird mit den Feldern des Erweiterungsschemas ausgefüllt.

   >[!CAUTION]
   >
   >Es ist nicht zulässig, die integrierten Schemata der Anwendung zu ändern, sondern den Schemaerweiterungsmechanismus. Andernfalls werden geänderte Schemata zum Zeitpunkt künftiger Aktualisierungen der Anwendung nicht aktualisiert. Dies kann zu Funktionsstörungen bei der Verwendung von Adobe Campaign führen.

   **Beispiel**: Erweiterung des Schemas **nms:empfänger** .

   ```
   <srcSchema extendedSchema="nms:recipient" name="recipient" namespace="cus">
     <element name="recipient">
       <attribute name="code" label="Branch code" type="long"/>
     </element>
   </srcSchema>
   ```

   Das erweiterte Schema **nms:empfänger** wird mit dem im Erweiterungsschema ausgefüllten Feld gefüllt:

   ```
   <schema dependingSchemas="cus:recipient" name="recipient" namespace="nms">
     ...
     <attribute belongsTo="cus:recipient" label="Branch code" name="code" sqlname="iCode" type="long"/>
     ...
   </schema>
   ```

   Das Attribut **dependencesSchemas** auf dem Stammelement des Schemas verweist auf die Abhängigkeiten von den Erweiterungsschemas.

   Das Attribut **gehörtTo** auf den Feldfüllungen im Schema, in dem es deklariert wird.

>[!CAUTION]
>
>Damit die Änderungen berücksichtigt werden, müssen Sie Schemata neu generieren. For more on this, refer to the [Regenerating schemas](../../configuration/using/regenerating-schemas.md) section.\
>Wenn sich die Änderungen auf die Struktur der Datenbank auswirken, müssen Sie eine Aktualisierung ausführen. Weiterführende Informationen finden Sie im Abschnitt [Datenbankstruktur aktualisieren](../../configuration/using/updating-the-database-structure.md).

