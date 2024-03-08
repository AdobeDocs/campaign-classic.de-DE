---
product: campaign
title: Tomcat-Version in Adobe Campaign suchen
description: Erfahren Sie, wie Sie die aktuelle Version des eingebetteten Tomcat-Webservlets ermitteln, das in einer Instanz von Adobe Campaign verwendet wird.
feature: Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="Gilt nur für Campaign Classic v7"
badge-v7-prem: label="On-Premise und Hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Gilt nur für Hybrid- und On-Premise-Bereitstellungen"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 76411b29-d300-4aaa-8d3b-d8ff74c3ce93
source-git-commit: 209ccbcac20052826dad0c55b35173be20b10114
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 3%

---

# Tomcat-Version suchen{#locate-tomcat-version}



Adobe Campaign verwendet eine **eingebettetes Webservlet namens Apache Tomcat** zur Verarbeitung von HTTP/HTTPS-Anforderungen zwischen der Anwendung und einer beliebigen externen Schnittstelle (einschließlich Client-Konsole, getrackte URL-Links, SOAP-Aufrufe und andere). Oft liegt ein externer Webserver (normalerweise IIS oder Apache) vor diesem für alle externen Adobe Campaign-Instanzen.

Gehen Sie wie folgt vor, um die genaue Version von Tomcat zu ermitteln, die in einer **Campaign Classic On-Premise-Instanz** um die Fehlerbehebung zu unterstützen.

## Tomcat wird in Adobe Campaign verwendet

Tomcat läuft auf Java und erfordert die Installation von JDK. Weitere Informationen finden Sie unter Java Development Kit (JDK) im [Campaign-Kompatibilitätsmatrix](../../rn/using/compatibility-matrix.md) Abschnitt.

Der in Adobe Campaign verwendete Tomcat ist eine angepasste eingebettete Version, die nicht alle Funktionen der vollständigen allgemein verfügbaren Version von Tomcat nutzt und möglicherweise nicht alle Verwundbarkeiten der Vollversion leidet. Der Tomcat sollte auch nicht für das externe Internet verfügbar sein, und alle Adobe Campaign-Instanzen, die verfügbar gemacht werden, sollten über einen externen Webserver verfügen (IIS, Apache usw.) vor dem Tomcat, um ihn zu schützen.

Neue oder aktualisierte Versionen der eingebetteten Versionen von Tomcat werden nur mit neuen Builds von Adobe Campaign selbst veröffentlicht und nicht als separate Patches außerhalb der Adobe Campaign-Builds.

## Suchen der eingebetteten Tomcat-Version

Gehen Sie wie folgt vor, um die Version des eingebetteten Tomcat in einer Instanz von Adobe Campaign zu finden.

>[!NOTE]
>
>Sie müssen Zugriff auf die Dateien auf dem Adobe Campaign-Server haben, den Sie überprüfen müssen. Das unten beschriebene Verfahren gilt nur für **On-Premise-Hosting-Modelle**.

1. Navigieren Sie zum *\tomcat-7\lib* Unterordner im Adobe Campaign-Installationsordner (z. B. *C:\Program Dateien\ [Installation_folder]* unter Windows oder */usr/local/neolane/nl6* in Linux).

1. Datei kopieren *catalina.jar* in einen externen temporären Ordner (z. B. Ihren Desktop) und benennen Sie die Erweiterung von .jar in .zip um.

1. Entpacken Sie die kopierte Datei. Dies führt zu vielen Unterordnern und Dateien.

1. Öffnen oder lesen Sie in den entpackten Dateien/Ordnern die folgende enthaltene Datei mithilfe eines Texteditors: *org/apache/catalina/util/ServerInfo.properties*. Möglicherweise müssen Sie eine TXT-Erweiterung hinzufügen, um das Öffnen mit einem Texteditor zu erleichtern.

1. Löschen Sie nach Abschluss die von Ihnen erstellten temporären Dateien, wenn sie sich auf einem Servercomputer befinden.

Beispiel: *ServerInfo.properties* -Datei für Adobe Campaign enthält die folgenden Informationen, die Tomcat v8.5.X angeben:

*`server.info=Apache Tomcat/8.5.X`*

*`server.number=8.5.X.Y`*

*`server.built=MM DD YYY HH:MM:SS`*

Sobald Sie die exakte Version von Tomcat ermitteln können, die in einer bestimmten Instanz verwendet wird, kann es Ihnen bei der Fehlerbehebung von Tomcat-bezogenen Problemen helfen.

>[!NOTE]
>
>Die Hauptversion des eingebetteten Tomcat wird nur aktualisiert, wenn sich die Hauptversion von Adobe Campaign ändert (obwohl ältere Versionen möglicherweise nicht mehr offiziell unterstützt werden, können die Informationen nützlich sein, da einige Kunden diese Versionen möglicherweise noch ausführen).
>

