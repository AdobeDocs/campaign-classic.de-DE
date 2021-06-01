---
product: campaign
title: Tomcat-Version in Adobe Campaign suchen
description: Erfahren Sie, wie Sie die aktuelle Version des eingebetteten Tomcat-Webservlets ermitteln, das in einer Instanz von Adobe Campaign verwendet wird.
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 76411b29-d300-4aaa-8d3b-d8ff74c3ce93
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '527'
ht-degree: 0%

---

# Suchen Sie die Tomcat-Version{#locate-tomcat-version}

Adobe Campaign verwendet ein **eingebettetes Webservlet namens Apache Tomcat**, um HTTP/HTTPS-Anforderungen zwischen der Anwendung und einer beliebigen externen Schnittstelle zu verarbeiten (einschließlich Client-Konsole, getrackte URL-Links, SOAP-Aufrufe und andere). Oft liegt ein externer Webserver (normalerweise IIS oder Apache) vor diesem für alle externen Adobe Campaign-Instanzen.

Gehen Sie wie folgt vor, um die genaue Version von Tomcat zu ermitteln, die in einer **On-Premise-Campaign Classic-Instanz** verwendet wird, um Probleme zu beheben.

## Tomcat wird in Adobe Campaign verwendet

Tomcat läuft auf Java und erfordert die Installation von JDK. Weitere Informationen finden Sie unter Java Development Kit (JDK) im Abschnitt [Campaign Compatibility Matrix](../../rn/using/compatibility-matrix.md) .

Der in Adobe Campaign verwendete Tomcat ist eine angepasste eingebettete Version, die nicht alle Funktionen der vollständigen allgemein verfügbaren Version von Tomcat nutzt und möglicherweise nicht alle Verwundbarkeiten der Vollversion leidet. Der Tomcat sollte auch nicht für das externe Internet verfügbar sein, und alle Adobe Campaign-Instanzen, die verfügbar gemacht werden, sollten über einen externen Webserver verfügen (IIS, Apache usw.). vor dem Tomcat, um ihn zu schützen.

Neue oder aktualisierte Versionen der eingebetteten Versionen von Tomcat werden nur mit neuen Builds von Adobe Campaign selbst veröffentlicht und nicht als separate Patches außerhalb der Adobe Campaign-Builds.

## Suchen der eingebetteten Tomcat-Version

Gehen Sie wie folgt vor, um die Version des eingebetteten Tomcat in einer Instanz von Adobe Campaign zu finden.

>[!NOTE]
>
>Sie müssen Zugriff auf die Dateien auf dem Adobe Campaign-Server haben, den Sie überprüfen müssen. Das unten beschriebene Verfahren gilt nur für **On-Premise-Hosting-Modelle**.

1. Navigieren Sie zum Unterordner *\tomcat-7\lib* im Adobe Campaign-Installationsordner (z. B. *C:\Program Files\ [Installation_folder]* unter Windows oder */usr/local/neolane/nl6* unter Linux).

   Wenn Sie eine ältere Version von Adobe Campaign mit Tomcat v6 ausführen, verwenden Sie *\tomcat-6\lib*.

1. Kopieren Sie die Datei *catalina.jar* in einen externen temporären Ordner (z. B. Ihren Desktop) und benennen Sie die Erweiterung von .jar in .zip um.

1. Entpacken Sie die kopierte Datei. Dies führt zu vielen Unterordnern und Dateien.

1. Öffnen oder lesen Sie in den entpackten Dateien/Ordnern die folgende enthaltene Datei mithilfe eines Texteditors: *org/apache/catalina/util/ServerInfo.properties*. Möglicherweise müssen Sie eine TXT-Erweiterung hinzufügen, um das Öffnen mit einem Texteditor zu erleichtern.

1. Löschen Sie nach Abschluss die von Ihnen erstellten temporären Dateien, wenn sie sich auf einem Servercomputer befinden.

Beispielsweise enthält die Datei *ServerInfo.properties* für Adobe Campaign die folgenden Informationen, die Tomcat v8.5.X angeben:

*server.info=Apache Tomcat/8.5.X*

*server.number=8.5.X.Y*

*server.built=MM DD YYY HH:MM:SS*

Sobald Sie die exakte Version von Tomcat ermitteln können, die in einer bestimmten Instanz verwendet wird, kann es Ihnen bei der Fehlerbehebung von Tomcat-bezogenen Problemen helfen.

>[!NOTE]
>
>Die Hauptversion des eingebetteten Tomcat wird nur aktualisiert, wenn sich die Hauptversion von Adobe Campaign ändert (obwohl ältere Versionen möglicherweise nicht mehr offiziell unterstützt werden, können die Informationen nützlich sein, da einige Kunden diese Versionen möglicherweise noch ausführen).
>
>Beispielsweise verwendet Adobe Campaign v6.02 immer Tomcat v6.x.
