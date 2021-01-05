---
solution: Campaign Classic
product: campaign
title: Tomcat-Version in Adobe Campaign suchen
description: Erfahren Sie, wie Sie die aktuelle Version des eingebetteten Tomcat Web-Servlets ermitteln, das in einer Instanz von Adobe Campaign verwendet wird.
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 49e49d5e35d14a31236cc4f78188cdf77353fbbf
workflow-type: tm+mt
source-wordcount: '527'
ht-degree: 0%

---


# Suchen der Tomcat-Version{#locate-tomcat-version}

Adobe Campaign verwendet ein eingebettetes **Webservlet mit dem Namen Apache Tomcat**, um HTTP/HTTPS-Anforderungen zwischen der Anwendung und jeder externen Schnittstelle (einschließlich Client-Konsole, verfolgte URL-Links, SOAP-Aufrufe und andere) zu verarbeiten. Oft liegt ein externer Webserver (normalerweise IIS oder Apache) vor diesem für alle externen Adobe Campaign-Instanzen.

Gehen Sie wie folgt vor, um die genaue Version von Tomcat zu ermitteln, die in einer lokalen **Campaign Classic-Instanz** verwendet wird, um Probleme zu beheben.

## Tomcat in Adobe Campaign

Tomcat läuft auf Java und erfordert die Installation von JDK. Weitere Informationen finden Sie unter Java Development Kit (JDK) im Abschnitt [Kampagne Compatibility Matrix](../../rn/using/compatibility-matrix.md).

Der in Adobe Campaign verwendete Tomcat ist eine angepasste Embedded Version, die nicht alle Funktionen der gesamten allgemein verfügbaren Version von Tomcat nutzt und möglicherweise nicht alle Schwachstellen der Vollversion leidet. Der Tomcat sollte auch nicht mit dem externen Adobe Campaign verbunden sein, und alle offen gelegten Instanzen sollten über einen externen Webserver verfügen (IIS, Apache usw.). vor dem Tomcat zu schützen.

Neue oder aktualisierte Versionen der eingebetteten Versionen von Tomcat werden nur mit neuen Builds von Adobe Campaign selbst und nicht als separate Patches außerhalb der Adobe Campaign Builds veröffentlicht.

## So suchen Sie die Version des eingebetteten Tomcat

Gehen Sie wie folgt vor, um die Version des eingebetteten Tomcat in einer Instanz von Adobe Campaign zu suchen.

>[!NOTE]
>
>Sie müssen Zugriff auf die Dateien auf dem zu prüfenden Adobe Campaign-Server haben. Das unten beschriebene Verfahren gilt nur für **lokale Hostingmodelle**.

1. Navigieren Sie zum Unterordner *\tomcat-7\lib* im Installationsordner des Adobe Campaigns (z. B. *C:\Program Files\ [Installationsordner]* unter Windows oder */usr/local/neolane/nl6* unter Linux).

   Wenn Sie eine ältere Version von Adobe Campaign mit Tomcat v6 ausführen, verwenden Sie *\tomcat-6\lib*.

1. Kopieren Sie die Datei *catalina.jar* in einen externen temporären Ordner (z. B. Ihren Desktop) und benennen Sie die Erweiterung von .jar in .zip um.

1. Dekomprimieren Sie die kopierte Datei. Dies führt zu vielen Unterordnern und Dateien.

1. Öffnen oder lesen Sie in den entpackten Dateien/Ordnern die folgende enthaltene Datei mit einem Texteditor: *org/apache/catalina/util/ServerInfo.properties*. Möglicherweise müssen Sie eine TXT-Erweiterung hinzufügen, um das Öffnen mit einem Texteditor zu erleichtern.

1. Löschen Sie nach Abschluss des Vorgangs auf einem Servercomputer die von Ihnen erstellten temporären Dateien.

Beispielsweise enthält die Datei *ServerInfo.properties* zum Adobe Campaign die folgenden Informationen, die Tomcat v8.5.X angeben:

*server.info=Apache Tomcat/8.5.X*

*server.number=8.5.X.Y*

*server.build=MM DD YYY HH:MM:SS*

Sobald Sie in der Lage sind, die exakte Version von Tomcat zu ermitteln, die in einer bestimmten Instanz verwendet wird, kann es Ihnen bei der Fehlerbehebung von Tomcat-Problemen helfen.

>[!NOTE]
>
>Die Hauptversion des eingebetteten Tomcat wird nur dann aktualisiert, wenn sich die Hauptversion des Adobe Campaigns ändert (obwohl ältere Versionen nicht mehr offiziell unterstützt werden, können die Informationen nützlich sein, da einige Kunden diese Versionen noch ausführen).
>
>Adobe Campaign v6.02 verwendet beispielsweise immer Tomcat v6.x.