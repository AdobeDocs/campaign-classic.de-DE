---
product: campaign
title: Erweitern eines Schemas
description: Erfahren Sie, wie Sie ein Schema erweitern
audience: configuration
content-type: reference
topic-tags: editing-schemas
exl-id: 6e3e666d-6ab3-4346-93ca-fb0155a4660d
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 5%

---

# Erweitern eines Schemas{#extending-a-schema}

![](../../assets/v7-only.svg)

>[!IMPORTANT]
>
>Einige integrierte Schemata dürfen nicht erweitert werden: hauptsächlich für diejenigen, für die die folgenden Einstellungen definiert sind:\
>**dataSource=&quot;file&quot;** and  **mappingType=&quot;xmlFile&quot;**.\
>Die folgenden Schemata dürfen nicht erweitert werden: **xtk:entityBackupNew**, **xtk:entityBackupOriginal**, **xtk:entityOriginal**, **xtk:form**, **xtk:srcSchema**, **ncm:publishing**, **nl:monitoring**, **nms:calendar**, **nms:remoteTracking**, **nms:userAgentRules&lt;a11 9/>,** xtk:builder **,** xtk:connections **,** xtk:dbInit **,** xtk:funcList **** xtk:fusion **,** xtk: jst **,** xtk:navtree **,** xtk:queryDef **,** xtk:resourceMenu **,** xtk:schema&lt;a 39/>, **xtk:scriptContext**, **xtk:session**, **xtk:sqlSchema**, **xtk:strings******
>Diese Liste ist nicht vollständig.

Es gibt zwei Methoden zum Erweitern eines vorhandenen Schemas:

1. Direktes Ändern des Quellschemas.
1. Erstellen Sie ein anderes Schema mit demselben Namen, aber einem anderen Namespace. Der Vorteil besteht darin, dass Sie eine Tabelle erweitern können, ohne das ursprüngliche Schema ändern zu müssen.

   Das Stammelement des Schemas muss das Attribut **extendedSchema** mit dem Namen des Schemas enthalten, das als Wert erweitert werden soll.

   Ein Erweiterungsschema hat kein eigenes Schema: Das aus dem Quellschema generierte Schema wird mit den Feldern des Erweiterungsschemas ausgefüllt.

   >[!IMPORTANT]
   >
   >Sie dürfen die integrierten Schemata der Anwendung nicht ändern, sondern den Mechanismus zur Schemaerweiterung. Andernfalls werden geänderte Schemata bei zukünftigen Aktualisierungen der Anwendung nicht aktualisiert. Dies kann zu Funktionsstörungen bei der Verwendung von Adobe Campaign führen.

   **Beispiel**: Erweiterung des  **nms:** recipientSchemas.

   ```
   <srcSchema extendedSchema="nms:recipient" name="recipient" namespace="cus">
     <element name="recipient">
       <attribute name="code" label="Branch code" type="long"/>
     </element>
   </srcSchema>
   ```

   Das erweiterte Schema **nms:recipient** wird mit dem im Erweiterungsschema ausgefüllten Feld ausgefüllt:

   ```
   <schema dependingSchemas="cus:recipient" name="recipient" namespace="nms">
     ...
     <attribute belongsTo="cus:recipient" label="Branch code" name="code" sqlname="iCode" type="long"/>
     ...
   </schema>
   ```

   Das Attribut **AbhängigSchemas** im Stammelement des Schemas verweist auf die Abhängigkeiten von den Erweiterungsschemas.

   Das Attribut **gehörtTo** auf dem Feld füllt das Schema aus, in dem es deklariert wird.

>[!IMPORTANT]
>
>Damit die Änderungen berücksichtigt werden, müssen Sie die Schemata neu generieren. Weitere Informationen hierzu finden Sie im Abschnitt [Regenerieren von Schemata](../../configuration/using/regenerating-schemas.md) .\
>Wenn sich die Änderungen auf die Struktur der Datenbank auswirken, müssen Sie eine Aktualisierung ausführen. Weiterführende Informationen finden Sie im Abschnitt [Datenbankstruktur aktualisieren](../../configuration/using/updating-the-database-structure.md).
