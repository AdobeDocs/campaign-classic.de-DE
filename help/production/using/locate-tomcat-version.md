---
product: campaign
title: Tomcat-Version in Adobe Campaign suchen
description: Erfahren Sie, wie Sie die aktuelle Version des eingebetteten Tomcat-Webservlets ermitteln, das in einer Instanz von Adobe Campaign verwendet wird.
feature: Monitoring
badge-v7-prem: label="Nur On-Premise/Hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Gilt nur für Hybrid- und On-Premise-Bereitstellungen"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 76411b29-d300-4aaa-8d3b-d8ff74c3ce93
source-git-commit: fd4a815bca23b94590012c4883cfaa9c29b6f118
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 2%

---

# Tomcat-Version suchen{#locate-tomcat-version}

Adobe Campaign verwendet ein **eingebettetes Web-Servlet namens Apache Tomcat**, um HTTP-/HTTPS-Anforderungen zwischen der Anwendung und beliebigen externen Schnittstellen zu verarbeiten (einschließlich Client Console, getrackten URL-Links, SOAP-Aufrufe und anderen). Oft liegt ein externer Webserver (normalerweise IIS oder Apache) vor diesem für alle externen Adobe Campaign-Instanzen.

Gehen Sie wie folgt vor, um die genaue Version von Tomcat zu ermitteln, die in einer **On-Premise-Instanz von Campaign Classic** verwendet wird, um Probleme zu beheben.

## Tomcat wird in Adobe Campaign verwendet

Tomcat läuft auf Java und erfordert die Installation von JDK. Weitere Informationen finden Sie unter Java Development Kit (JDK) im Abschnitt [Campaign Compatibility Matrix](../../rn/using/compatibility-matrix.md) .

Der in Adobe Campaign verwendete Tomcat ist eine angepasste eingebettete Version, die nicht alle Funktionen der vollständigen allgemein verfügbaren Version von Tomcat nutzt und möglicherweise nicht alle Verwundbarkeiten der Vollversion leidet. Der Tomcat sollte auch nicht für das externe Internet verfügbar sein, und alle Adobe Campaign-Instanzen, die verfügbar gemacht werden, sollten über einen externen Webserver verfügen (IIS, Apache usw.) vor dem Tomcat, um ihn zu schützen.

Neue oder aktualisierte Versionen der eingebetteten Versionen von Tomcat werden nur mit neuen Builds von Adobe Campaign selbst veröffentlicht und nicht als separate Patches außerhalb der Adobe Campaign-Builds.

>[!AVAILABILITY]
>
>
>* Ab Campaign v7.4.1 ist Tomcat 10.1 die Standardversion.
>
>* Adobe Campaign Classic verwendet keine WebSocket- und HTTP2-Protokolle.
>


## Suchen der eingebetteten Tomcat-Version

Gehen Sie wie folgt vor, um die Version des eingebetteten Tomcat in einer Instanz von Adobe Campaign zu finden.

>[!NOTE]
>
>Sie müssen Zugriff auf die Dateien auf dem Adobe Campaign-Server haben, den Sie überprüfen müssen. Das unten beschriebene Verfahren gilt nur für **On-Premise-Hosting-Modelle**.

1. Navigieren Sie zum Unterordner &quot;*\tomcat-11\lib*&quot;im Adobe Campaign-Installationsordner (z. B. &quot;*C:\Program Files\ [Installation_folder]*&quot;unter Windows oder &quot;*/usr/local/neolane/nl6*&quot; unter Linux).

1. Kopieren Sie die Datei *catalina.jar* in einen externen temporären Ordner (z. B. Ihren Desktop) und benennen Sie die Erweiterung von .jar in .zip um.

1. Entpacken Sie die kopierte Datei. Dies führt zu vielen Unterordnern und Dateien.

1. Öffnen oder lesen Sie in den entpackten Dateien/Ordnern die folgende enthaltene Datei mithilfe eines Texteditors: *org/apache/catalina/util/ServerInfo.properties*. Möglicherweise müssen Sie eine TXT-Erweiterung hinzufügen, um das Öffnen mit einem Texteditor zu erleichtern.

1. Löschen Sie nach Abschluss die von Ihnen erstellten temporären Dateien, wenn sie sich auf einem Servercomputer befinden.

Beispielsweise enthält die Datei *ServerInfo.properties* für Adobe Campaign die folgenden Informationen, die Tomcat v11.X angeben:

*`server.info=Apache Tomcat/11.X`*

*`server.number=A.B.X.Y`*

*`server.built=MM DD YYY HH:MM:SS`*

Sobald Sie die exakte Version von Tomcat ermitteln können, die in einer bestimmten Instanz verwendet wird, kann es Ihnen bei der Fehlerbehebung von Tomcat-bezogenen Problemen helfen.

>[!NOTE]
>
>Die Hauptversion des eingebetteten Tomcat wird nur aktualisiert, wenn sich die Hauptversion von Adobe Campaign ändert (obwohl ältere Versionen möglicherweise nicht mehr offiziell unterstützt werden, können die Informationen nützlich sein, da einige Kunden diese Versionen möglicherweise noch ausführen).
>

