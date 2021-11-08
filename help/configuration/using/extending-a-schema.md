---
product: campaign
title: Erweitern eines Schemas
description: Erfahren Sie, wie Sie ein Schema erweitern
audience: configuration
content-type: reference
topic-tags: editing-schemas
exl-id: 6e3e666d-6ab3-4346-93ca-fb0155a4660d
source-git-commit: bd9f035db1cbad883e1f27fe901e34dfbc9c1229
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 10%

---

# Erweitern eines Schemas{#extending-a-schema}

![](../../assets/v7-only.svg)

>[!IMPORTANT]
>
>Einige integrierte Schemata dürfen nicht erweitert werden: hauptsächlich für diejenigen, für die die folgenden Einstellungen definiert sind:\
>**dataSource=&quot;file&quot;** und **mappingType=&quot;xmlFile&quot;**.\
>Die folgenden Schemata dürfen nicht erweitert werden: **xtk:entityBackupNew**, **xtk:entityBackupOriginal**, **xtk:entityOriginal**, **xtk:form**, **xtk:srcSchema**, **ncm:publishing**, **nl:monitoring**, **nms:calendar**, **nms:remoteTracking**, **nms:userAgentRules**, **xtk:builder**, **xtk:connections**, **xtk:dbInit**, **xtk:funcList**, **xtk:fusion**, **xtk: jst**, **xtk:navtree**, **xtk:queryDef**, **xtk:resourceMenu**, **xtk:schema**, **xtk:scriptContext**, **xtk:session**, **xtk:sqlSchema**, **xtk:strings**.
>Diese Liste ist nicht vollständig.

Es gibt zwei Methoden zum Erweitern eines vorhandenen Schemas:

1. Direktes Ändern des Quellschemas.
1. Erstellen Sie ein anderes Schema mit demselben Namen, aber einem anderen Namespace. Der Vorteil besteht darin, dass Sie eine Tabelle erweitern können, ohne das ursprüngliche Schema ändern zu müssen.

   Das Stammelement des Schemas muss die **extendedSchema** -Attribut mit dem Namen des Schemas, das als Wert erweitert werden soll.

   Ein Erweiterungsschema hat kein eigenes Schema: Das aus dem Quellschema generierte Schema wird mit den Feldern des Erweiterungsschemas ausgefüllt.

   >[!IMPORTANT]
   >
   >Sie dürfen die integrierten Schemata der Anwendung nicht ändern, sondern den Mechanismus zur Schemaerweiterung. Andernfalls werden geänderte Schemas bei zukünftigen Aktualisierungen der Anwendung nicht aktualisiert. Dies kann zu Funktionsstörungen bei der Verwendung von Adobe Campaign führen.

   **Beispiel**: Erweiterung der **nms:recipient** Schema.

   ```
   <srcSchema extendedSchema="nms:recipient" name="recipient" namespace="cus">
     <element name="recipient">
       <attribute name="code" label="Branch code" type="long"/>
     </element>
   </srcSchema>
   ```

   Die **nms:recipient** Das Feld im Erweiterungsschema wird mit dem erweiterten Schema ausgefüllt:

   ```
   <schema dependingSchemas="cus:recipient" name="recipient" namespace="nms">
     ...
     <attribute belongsTo="cus:recipient" label="Branch code" name="code" sqlname="iCode" type="long"/>
     ...
   </schema>
   ```

   Die **JeSchemas** -Attribut im Stammelement des Schemas referenziert die Abhängigkeiten zu den Erweiterungsschemas.

   Die **gehörtTo** -Attribut im Feld füllt das Schema aus, in dem es deklariert wird.

>[!IMPORTANT]
>
>Damit die Änderungen berücksichtigt werden, müssen Sie die Schemata neu generieren. Weitere Informationen hierzu finden Sie im Abschnitt [Regenerieren von Schemata](../../configuration/using/regenerating-schemas.md) Abschnitt.\
>Wenn sich die Änderungen auf die Struktur der Datenbank auswirken, müssen Sie eine Aktualisierung ausführen. Weiterführende Informationen finden Sie im Abschnitt [Datenbankstruktur aktualisieren](../../configuration/using/updating-the-database-structure.md).
