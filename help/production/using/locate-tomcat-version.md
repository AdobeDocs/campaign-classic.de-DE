---
product: campaign
title: Tomcat-Version in Adobe Campaign suchen
description: Erfahren Sie, wie Sie die aktuelle Version des eingebetteten Tomcat-Webservlets finden, das in einer Instanz von Adobe Campaign verwendet wird.
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

Adobe Campaign verwendet ein **eingebettetes Web-Servlet mit dem Namen Apache Tomcat** zur Verarbeitung von HTTP/HTTPS-Anfragen zwischen der Anwendung und einer beliebigen externen Schnittstelle (einschließlich Client-Konsole, getrackten URL-Links, SOAP-Aufrufen usw.). Häufig befindet sich für alle nach außen gerichteten Adobe Campaign-Instanzen ein externer Webserver (normalerweise IIS oder Apache) davor.

Gehen Sie wie folgt vor, um die genaue Version von Tomcat zu ermitteln, die in einer **Campaign Classic On-Premise** Instanz verwendet wird, um Probleme zu beheben.

## Tomcat in Adobe Campaign verwendet

Tomcat läuft auf Java und benötigt JDK installiert. Weitere Informationen finden Sie unter Java Development Kit (JDK) im Abschnitt [Campaign-Kompatibilitätsmatrix](../../rn/using/compatibility-matrix.md).

Der in Adobe Campaign verwendete Tomcat ist eine angepasste eingebettete Version, die nicht alle Funktionen der vollständigen allgemein verfügbaren Version von Tomcat nutzt und möglicherweise nicht alle Schwachstellen der Vollversion aufweist. Der Tomcat sollte auch nicht über das Internet von außen zugänglich sein. Alle Adobe Campaign-Instanzen, die offen gelegt werden, sollten einen externen Webserver (IIS, Apache usw.) vor dem Tomcat haben, um ihn zu schützen.

Neue oder aktualisierte Versionen der eingebetteten Tomcat-Versionen werden nur mit neuen Builds von Adobe Campaign selbst veröffentlicht und nicht als separate Patches außerhalb der Adobe Campaign-Builds.

>[!AVAILABILITY]
>
>
>* Ab Campaign v7.4.1 ist Tomcat 10.1 die Standardversion.
>
>* Adobe Campaign Classic verwendet keine WebSocket- und HTTP2-Protokolle.
>


## So finden Sie die Version von eingebettetem Tomcat

Gehen Sie wie folgt vor, um die Version von eingebettetem Tomcat in einer Instanz von Adobe Campaign zu finden.

>[!NOTE]
>
>Sie müssen Zugriff auf die Dateien auf dem Adobe Campaign-Server haben, die Sie überprüfen müssen. Das unten beschriebene Verfahren gilt nur für **On-Premise-Hosting-Modelle**.

1. Navigieren Sie zum Unterordner *\tomcat-11\lib* im Adobe Campaign-Installationsordner (z. B. *C:\Program Files\ [Installation_Folder]* unter Windows oder */usr/local/neolane/nl6* unter Linux).

1. Kopieren Sie die Datei *catalina.jar* in einen externen temporären Ordner (z. B. Ihren Desktop) und benennen Sie die Erweiterung von .jar in .zip um.

1. Entpacken Sie die kopierte Datei. Dies führt zu vielen Unterordnern und Dateien.

1. Öffnen oder lesen Sie in den dekomprimierten Dateien/Ordnern die folgende enthaltene Datei mithilfe eines Texteditors: *org/apache/catalina/util/ServerInfo.properties*. Möglicherweise müssen Sie eine TXT-Erweiterung hinzufügen, um das Öffnen mit einem Texteditor zu erleichtern.

1. Wenn Sie fertig sind und sich auf einem Server-Computer befinden, löschen Sie die von Ihnen erstellten temporären Dateien.

Beispielsweise enthält die Datei *ServerInfo.properties* für Adobe Campaign die folgenden Informationen, die auf Tomcat v11.X hinweisen:

*`server.info=Apache Tomcat/11.X`*

*`server.number=A.B.X.Y`*

*`server.built=MM DD YYY HH:MM:SS`*

Sobald Sie die genaue Version von Tomcat ermittelt haben, die in einer bestimmten Instanz verwendet wird, kann es Ihnen bei der Fehlerbehebung bei Problemen im Zusammenhang mit Tomcat helfen.

>[!NOTE]
>
>Die Hauptversion des eingebetteten Tomcat wird erst aktualisiert, wenn sich die Hauptversion von Adobe Campaign ändert (obwohl ältere Versionen möglicherweise nicht mehr offiziell unterstützt werden, können die Informationen nützlich sein, da einige Kunden diese Versionen noch ausführen).
>

