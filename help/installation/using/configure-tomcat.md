---
product: campaign
title: Campaign Tomcat-Konfiguration
description: Campaign Tomcat-Konfiguration
feature: Installation, Instance Settings
badge-v7-prem: label="Nur On-Premise/Hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Gilt nur für Hybrid- und On-Premise-Bereitstellungen"
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: a2126458-2ae5-47c6-ad13-925f0e067ecf
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 4%

---

# Konfigurieren von Apache Tomcat {#configuring-tomcat}

Adobe Campaign verwendet ein **eingebettetes Web-Servlet mit dem Namen Apache Tomcat** zur Verarbeitung von HTTP/HTTPS-Anfragen zwischen der Anwendung und einer beliebigen externen Schnittstelle (einschließlich Client-Konsole, getrackten URL-Links, SOAP-Aufrufen usw.). Häufig befindet sich für alle nach außen gerichteten Adobe Campaign-Instanzen ein externer Webserver (normalerweise IIS oder Apache) davor.

Erfahren Sie mehr über Tomcat in Campaign und wie Sie Ihre Tomcat-Version finden können auf [dieser Seite](../../production/using/locate-tomcat-version.md).

>[!AVAILABILITY]
>
>
>* Ab Campaign v7.4.1 ist Tomcat 10.1 die Standardversion.
>
>* Adobe Campaign Classic verwendet keine WebSocket- und HTTP2-Protokolle.
>



## Standard-Port für Apache Tomcat {#default-port-for-tomcat}


>[!NOTE]
>
>Dieses Verfahren ist auf On **Premise-Bereitstellungen**.
>

Wenn der 8080-Listening-Port des Tomcat-Servers bereits mit einer anderen für Ihre Konfiguration erforderlichen Anwendung belegt ist, müssen Sie den 8080-Port durch einen freien Port ersetzen (z. B. 8090). Um dies zu ändern, bearbeiten Sie die Datei **server.xml**, die im Verzeichnis **/tomcat-X/** des Adobe Campaign-Installationsordners gespeichert ist.

Ändern Sie dann den Port der JSP-Relay-Seiten. Ändern Sie dazu die Datei **serverConf.xml**, die im Verzeichnis **/conf** des Adobe Campaign-Installationsverzeichnisses gespeichert ist.

```xml
<serverConf>
   ...
   <web controlPort="8005" httpPort="8090"...
   <url ... targetUrl="http://localhost:8090"...
```

## Zuordnen eines Ordners in Apache Tomcat {#mapping-a-folder-in-tomcat}


>[!NOTE]
>
>Dieses Verfahren ist auf On **Premise-Bereitstellungen**.
>

Um kundenspezifische Einstellungen zu definieren, können Sie eine Datei **user_contexts.xml** im Ordner **/tomcat-X/** erstellen, die auch die Datei **contexts.xml** enthält.

Diese Datei enthält die folgenden Informationen:

```xml
 <Context path='/foo' docBase='../customers/foo'   crossContext='true' debug='0' reloadable='true' trusted='false'/>
```

Bei Bedarf kann dieser Vorgang Server-seitig reproduziert werden.

## Tomcat-Fehlerbericht ausblenden {#hide-tomcat-error-report}


>[!NOTE]
>
>Dieses Verfahren ist auf On **Premise-Bereitstellungen**.
>
>Diese Änderung ist ab Campaign v7.4.1 nicht mehr erforderlich.
>

Aus Sicherheitsgründen empfehlen wir dringend, den Tomcat-Fehlerbericht auszublenden. Führen Sie folgende Schritte aus:

1. Öffnen Sie die Datei **server** xml) im Verzeichnis **/tomcat-X/** des Adobe Campaign-Installationsordners: `/usr/local/neolane/nl6/tomcat-X/conf`
1. Fügen Sie unten nach allen vorhandenen Kontextelementen das folgende Element hinzu:

   ```xml
   <Valve className="org.apache.catalina.valves.ErrorReportValve" showReport="false" showServerInfo="false"/>
   ```

1. Starten Sie die Webserver nlserver und Apache neu.
