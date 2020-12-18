---
solution: Campaign Classic
product: campaign
title: Erweitern eines Schemas
description: Erfahren Sie, wie Sie ein Schema erweitern
audience: configuration
content-type: reference
topic-tags: editing-schemas
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 5%

---


# Erweitern eines Schemas{#extending-a-schema}

>[!IMPORTANT]
>
>Einige integrierte Schema dürfen nicht erweitert werden: hauptsächlich für die folgenden Einstellungen:\
>**dataSource=&quot;file&quot;** und  **mappingType=&quot;xmlFile&quot;**.\
>Die folgenden Schema dürfen nicht verlängert werden: **xtk:entityBackupNew**, **xtk:entityBackupOriginal**, **xtk:entityOriginal**, **xtk:form**, **xtk:srcSchema**, **ncm:publishing**, **nl:monitoring**, **nms:calendar**, **nms:remoteTracking**, **nms:userAgentRules&lt;a11 9/>,** xtk:builder **,** xtk:connections **,** xtk:dbInit **,** xtk:funcList **,** xtk:fusion **,** xtk: jst **,** xtk:navtree **,** xtk:queryDef **,** xtk:resourceMenu **,** xtk:Schema 39/>, **xtk:scriptContext**, **xtk:session**, **xtk:sqlSchema**, **xtk:strings**.****
>Diese Liste ist nicht erschöpfend.

Es gibt zwei Methoden zum Erweitern eines vorhandenen Schemas:

1. Direktes Ändern des Quell-Schemas.
1. Erstellen eines anderen Schemas mit demselben Namen, jedoch einem anderen Namensraum. Der Vorteil besteht darin, dass Sie eine Tabelle erweitern können, ohne das ursprüngliche Schema ändern zu müssen.

   Das Stammelement des Schemas muss das Attribut **extendedSchema** mit dem Namen des Schemas enthalten, das als Wert erweitert werden soll.

   Ein Erweiterungsschema hat kein eigenes Schema: das aus dem Quellcode-Schema generierte Schema wird mit den Feldern des Erweiterungsschemas ausgefüllt.

   >[!IMPORTANT]
   >
   >Es ist nicht zulässig, die integrierten Schema der Anwendung zu ändern, sondern den Schema-Erweiterungsmechanismus. Andernfalls werden modifizierte Schema bei zukünftigen Aktualisierungen der Anwendung nicht aktualisiert. Dies kann zu Funktionsstörungen bei der Verwendung von Adobe Campaign führen.

   **Beispiel**: Erweiterung des  **nms:** empfängerSchema.

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

   Das **dependenzSchemas**-Attribut im Stammelement des Schemas verweist auf die Abhängigkeiten zu den Erweiterungsschemas.

   Das Attribut **gehörtTo** in den Feldfüllungen des Schemas, in dem es deklariert wird.

>[!IMPORTANT]
>
>Damit die Änderungen berücksichtigt werden, müssen Sie Schema neu generieren. Weitere Informationen finden Sie im Abschnitt [Regenerierende Schema](../../configuration/using/regenerating-schemas.md).\
>Wenn sich die Änderungen auf die Struktur der Datenbank auswirken, müssen Sie eine Aktualisierung ausführen. Weiterführende Informationen finden Sie im Abschnitt [Datenbankstruktur aktualisieren](../../configuration/using/updating-the-database-structure.md).

