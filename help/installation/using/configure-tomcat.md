---
solution: Campaign Classic
product: campaign
title: Konfiguration von Kampagne Tomcat
description: Konfiguration von Kampagne Tomcat
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: a2126458-2ae5-47c6-ad13-925f0e067ecf
translation-type: tm+mt
source-git-commit: b0a1e0596e985998f1a1d02236f9359d0482624f
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 0%

---


# Apache Tomcat {#configuring-tomcat} konfigurieren

Adobe Campaign verwendet ein eingebettetes **Webservlet mit dem Namen Apache Tomcat**, um HTTP/HTTPS-Anforderungen zwischen der Anwendung und jeder externen Schnittstelle (einschließlich Client-Konsole, verfolgte URL-Links, SOAP-Aufrufe und andere) zu verarbeiten. Oft liegt ein externer Webserver (normalerweise IIS oder Apache) vor diesem für alle externen Adobe Campaign-Instanzen.

Erfahren Sie mehr über Tomcat in Kampagne und wie Sie Ihre Tomcat-Version in [dieser Seite ](../../production/using/locate-tomcat-version.md) finden.

## Standardanschluss für Apache Tomcat {#default-port-for-tomcat}

Wenn der 8080-Listening-Anschluss des Tomcat-Servers bereits mit einer anderen Anwendung besetzt ist, die für Ihre Konfiguration erforderlich ist, müssen Sie den 8080-Port durch einen kostenlosen ersetzen (z. B. 8090). Um sie zu ändern, bearbeiten Sie die Datei **server.xml**, die im Ordner **/tomcat-8/conf** des Installationsordners des Adobe Campaigns gespeichert ist.

Ändern Sie dann den Anschluss der JSP-Relaisseiten. Ändern Sie dazu die Datei **serverConf.xml**, die im Ordner **/conf** des Installationsordners des Adobe Campaigns gespeichert ist.

```
<serverConf>
   ...
   <web controlPort="8005" httpPort="8090"...
   <url ... targetUrl="http://localhost:8090"...
```

## Ordnen Sie einen Ordner in Apache Tomcat zu.{#mapping-a-folder-in-tomcat}

Um kundenspezifische Einstellungen zu definieren, können Sie eine Datei **user_Kontexte.xml** im Ordner **/tomcat-8/conf** erstellen, die auch die Datei **Kontexte.xml** enthält.

Diese Datei enthält die folgenden Informationen:

```
 <Context path='/foo' docBase='../customers/foo'   crossContext='true' debug='0' reloadable='true' trusted='false'/>
```

Bei Bedarf kann dieser Vorgang serverseitig reproduziert werden.
