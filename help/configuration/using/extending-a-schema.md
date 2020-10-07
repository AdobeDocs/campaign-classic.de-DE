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
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 7%

---


# Erweitern eines Schemas{#extending-a-schema}

>[!IMPORTANT]
>
>Einige integrierte Schema dürfen nicht erweitert werden: hauptsächlich für die folgenden Einstellungen:\
>**dataSource=&quot;file&quot;** und **mappingType=&quot;xmlFile&quot;**.\
>Die folgenden Schema dürfen nicht verlängert werden: **xtk:entityBackupNew**, **xtk:entityBackupOriginal**, **xtk:entityOriginal**, **xtk:form**, **xtk:srcSchema**, ******************************************ncm:publishing,nl:monitoring, etc:calendarnms:remoteTracking, nmsAgentRules,xtk:builder, xtk:connectionsxtk, xtk:dbInit,xtk:funcList,xtk:fusionxtk: jst**, **xtk:navtree**, **xtk:queryDef**, **xtk:resourceMenu**, **xtk:Schema**, **xtk:scriptContextText, xtk:sessionPassword,**************xtk:sqlSchemaString.
>Diese Liste ist nicht erschöpfend.

Es gibt zwei Methoden zum Erweitern eines vorhandenen Schemas:

1. Direktes Ändern des Quell-Schemas.
1. Erstellen eines anderen Schemas mit demselben Namen, jedoch einem anderen Namensraum. Der Vorteil besteht darin, dass Sie eine Tabelle erweitern können, ohne das ursprüngliche Schema ändern zu müssen.

   Das Stammelement des Schemas muss das Attribut **extendedSchema** mit dem Namen des Schemas enthalten, das als Wert erweitert werden soll.

   Ein Erweiterungsschema hat kein eigenes Schema: das aus dem Quellcode-Schema generierte Schema wird mit den Feldern des Erweiterungsschemas ausgefüllt.

   >[!IMPORTANT]
   >
   >Es ist nicht zulässig, die integrierten Schema der Anwendung zu ändern, sondern den Schema-Erweiterungsmechanismus. Andernfalls werden modifizierte Schema bei zukünftigen Aktualisierungen der Anwendung nicht aktualisiert. Dies kann zu Funktionsstörungen bei der Verwendung von Adobe Campaign führen.

   **Beispiel**: Erweiterung des **nms:Empfänger** -Schemas.

   ```
   <srcSchema extendedSchema="nms:recipient" name="recipient" namespace="cus">
     <element name="recipient">
       <attribute name="code" label="Branch code" type="long"/>
     </element>
   </srcSchema>
   ```

   Das erweiterte Schema **nms:Empfänger** wird mit dem im Erweiterungsschema ausgefüllten Feld gefüllt:

   ```
   <schema dependingSchemas="cus:recipient" name="recipient" namespace="nms">
     ...
     <attribute belongsTo="cus:recipient" label="Branch code" name="code" sqlname="iCode" type="long"/>
     ...
   </schema>
   ```

   Das Attribut **dependencesSchemas** für das Stammelement des Schemas verweist auf die Abhängigkeiten zu den Erweiterungsschemas.

   Das Attribut **gehörtTo** in den Feldfüllungen in dem Schema, in dem es deklariert wird.

>[!IMPORTANT]
>
>Damit die Änderungen berücksichtigt werden, müssen Sie Schema neu generieren. For more on this, refer to the [Regenerating schemas](../../configuration/using/regenerating-schemas.md) section.\
>Wenn sich die Änderungen auf die Struktur der Datenbank auswirken, müssen Sie eine Aktualisierung ausführen. Weiterführende Informationen finden Sie im Abschnitt [Datenbankstruktur aktualisieren](../../configuration/using/updating-the-database-structure.md).

