---
product: campaign
title: Schema erweitern
description: Erfahren Sie, wie Sie ein Schema erweitern
role: Developer
feature: Schema Extension
exl-id: 6e3e666d-6ab3-4346-93ca-fb0155a4660d
source-git-commit: 9f5205ced6b8d81639d4d0cb6a76905a753cddac
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 12%

---

# Schema erweitern{#extending-a-schema}

>[!IMPORTANT]
>
>Einige integrierte Schemata dürfen nicht erweitert werden, insbesondere diejenigen, für die die folgenden Einstellungen definiert sind:\
>**dataSource=„file“** und **mappingType=„xmlFile“**.\
>Folgende Schemata dürfen nicht erweitert werden: **xtk:entityBackupNew**, **xtk:entityBackupOriginal**, **xtk:entityOriginal**, **xtk:form**, **xtk:srcSchema**, **ncm:publishing**, **nms:monitoring**, **nms:calendar**, **nms:remoteTracking**,xtk **,:userAgentRules** xtk **: jst:builder**, xtk **:connections** xtk **,:dbInit** xtk **,:funcList** xtk **,:fusion** xtk **,** xtk **,:navtree** xtkTk **, xtkTk:queryDef** **:resourceMenu** **:schema** **:scriptContext** **:session** **:sqlSchema** **:strings**.
>Diese Liste ist nicht vollständig.

Es gibt zwei Methoden zum Erweitern eines vorhandenen Schemas:

1. Direktes Ändern des Quellschemas.
1. Erstellen eines anderen Schemas mit demselben Namen, aber einem anderen Namespace. Der Vorteil besteht darin, dass Sie eine Tabelle erweitern können, ohne das ursprüngliche Schema ändern zu müssen.

   Das Stammelement des Schemas muss das Attribut **extendedSchema** mit dem Namen des zu erweiternden Schemas als seinen Wert enthalten.

   Ein Erweiterungsschema hat kein eigenes Schema: Das aus dem Quellschema generierte Schema wird mit den Feldern des Erweiterungsschemas ausgefüllt.

   >[!IMPORTANT]
   >
   >Sie dürfen nicht die integrierten Schemata des Programms ändern, sondern nur den Mechanismus der Schemaerweiterung. Andernfalls werden geänderte Schemata bei zukünftigen Aktualisierungen der Anwendung nicht aktualisiert. Dies kann zu Funktionsstörungen bei der Verwendung von Adobe Campaign führen.

   **Beispiel**: Erweiterung des Schemas **nms:recipient**.

   ```
   <srcSchema extendedSchema="nms:recipient" name="recipient" namespace="cus">
     <element name="recipient">
       <attribute name="code" label="Branch code" type="long"/>
     </element>
   </srcSchema>
   ```

   Das **nms:recipient**-Erweiterungsschema wird mit dem Feld ausgefüllt, das im Erweiterungsschema ausgefüllt wird:

   ```
   <schema dependingSchemas="cus:recipient" name="recipient" namespace="nms">
     ...
     <attribute belongsTo="cus:recipient" label="Branch code" name="code" sqlname="iCode" type="long"/>
     ...
   </schema>
   ```

   Das **dependingSchemas**-Attribut im Stammelement des Schemas verweist auf die Abhängigkeiten von den Erweiterungsschemata.

   Das **BelongsTo**-Attribut im Feld füllt das Schema aus, in dem es deklariert wird.

>[!IMPORTANT]
>
>Damit die Änderungen berücksichtigt werden, müssen Sie die Schemata neu generieren. Weitere Informationen hierzu finden Sie auf [dieser Seite](../../configuration/using/regenerating-schemas.md).\
>Wenn sich die Änderungen auf die Struktur der Datenbank auswirken, müssen Sie eine Aktualisierung ausführen. Weitere Informationen hierzu finden Sie auf [dieser Seite](../../configuration/using/updating-the-database-structure.md).
