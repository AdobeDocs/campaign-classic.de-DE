---
product: campaign
title: Campaign Tomcat-Konfiguration
description: Campaign Tomcat-Konfiguration
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: a2126458-2ae5-47c6-ad13-925f0e067ecf
source-git-commit: 26ae7ff1f0837a9a50057d97b00422a288b9dc7a
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 1%

---

# Konfigurieren von Apache Tomcat {#configuring-tomcat}

![](../../assets/v7-only.svg)

Adobe Campaign verwendet eine **eingebettetes Webservlet namens Apache Tomcat** zur Verarbeitung von HTTP/HTTPS-Anforderungen zwischen der Anwendung und einer beliebigen externen Schnittstelle (einschließlich Client-Konsole, getrackte URL-Links, SOAP-Aufrufe und andere). Oft liegt ein externer Webserver (normalerweise IIS oder Apache) vor diesem für alle externen Adobe Campaign-Instanzen.

Erfahren Sie mehr über Tomcat in Campaign und wie Sie Ihre Tomcat-Version finden in [diese Seite](../../production/using/locate-tomcat-version.md).

>[!NOTE]
>
>Dieses Verfahren beschränkt sich auf **On-Premise** -Implementierungen.

## Standardanschluss für Apache Tomcat {#default-port-for-tomcat}

Wenn der 8080-Listening-Port des Tomcat-Servers bereits mit einer anderen für Ihre Konfiguration erforderlichen Anwendung besetzt ist, müssen Sie den 8080-Port durch einen freien ersetzen (z. B. 8090). Um sie zu ändern, bearbeiten Sie die **server.xml** in der Datei **/tomcat-8/conf** Ordner des Adobe Campaign-Installationsordners.

Ändern Sie dann den Port der JSP-Relais-Seiten. Ändern Sie dazu die **serverConf.xml** in der Datei **/conf** Ordner des Adobe Campaign-Installationsordners.

```
<serverConf>
   ...
   <web controlPort="8005" httpPort="8090"...
   <url ... targetUrl="http://localhost:8090"...
```

## Ordner in Apache Tomcat zuordnen {#mapping-a-folder-in-tomcat}

Um kundenspezifische Einstellungen zu definieren, können Sie eine **user_contexts.xml** in der Datei **/tomcat-8/conf** -Ordner, der auch den **contexts.xml** -Datei.

Diese Datei enthält die folgenden Informationen:

```
 <Context path='/foo' docBase='../customers/foo'   crossContext='true' debug='0' reloadable='true' trusted='false'/>
```

Bei Bedarf kann dieser Vorgang serverseitig reproduziert werden.

## Tomcat-Fehlerbericht ausblenden {#hide-tomcat-error-report}

Aus Sicherheitsgründen empfehlen wir dringend, den Tomcat-Fehlerbericht auszublenden. Im Folgenden werden die Schritte beschrieben.

1. Öffnen Sie die **server.xml** Datei im **/tomcat-8/conf** Ordner des Adobe Campaign-Installationsordners:  `/usr/local/neolane/nl6/tomcat-8/conf`
1. Fügen Sie das folgende Element am unteren Rand nach allen vorhandenen Kontextelementen hinzu:

   ```
   <Valve className="org.apache.catalina.valves.ErrorReportValve" showReport="false" showServerInfo="false"/>
   ```
1. Starten Sie die nlserver- und Apache-Webserver neu.
