---
product: campaign
title: Campaign Tomcat-Konfiguration
description: Campaign Tomcat-Konfiguration
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: a2126458-2ae5-47c6-ad13-925f0e067ecf
source-git-commit: ed9e76495efb0cb49e248a7d38417642c5094a11
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 0%

---

# Konfigurieren von Apache Tomcat {#configuring-tomcat}

![](../../assets/v7-only.svg)

Adobe Campaign verwendet ein **eingebettetes Webservlet namens Apache Tomcat**, um HTTP/HTTPS-Anforderungen zwischen der Anwendung und einer beliebigen externen Schnittstelle zu verarbeiten (einschließlich Client-Konsole, getrackte URL-Links, SOAP-Aufrufe und andere). Oft liegt ein externer Webserver (normalerweise IIS oder Apache) vor diesem für alle externen Adobe Campaign-Instanzen.

Erfahren Sie mehr über Tomcat in Campaign und wie Sie Ihre Tomcat-Version in [dieser Seite](../../production/using/locate-tomcat-version.md) finden.

>[!NOTE]
>
>Dieses Verfahren ist auf **On-Premise** -Implementierungen beschränkt.

## Standardanschluss für Apache Tomcat {#default-port-for-tomcat}

Wenn der 8080-Listening-Port des Tomcat-Servers bereits mit einer anderen für Ihre Konfiguration erforderlichen Anwendung besetzt ist, müssen Sie den 8080-Port durch einen freien ersetzen (z. B. 8090). Um sie zu ändern, bearbeiten Sie die Datei **server.xml**, die im Ordner **/tomcat-8/conf** des Adobe Campaign-Installationsordners gespeichert ist.

Ändern Sie dann den Port der JSP-Relais-Seiten. Ändern Sie dazu die Datei **serverConf.xml**, die im Ordner **/conf** des Adobe Campaign-Installationsordners gespeichert ist.

```
<serverConf>
   ...
   <web controlPort="8005" httpPort="8090"...
   <url ... targetUrl="http://localhost:8090"...
```

## Ordner in Apache Tomcat zuordnen {#mapping-a-folder-in-tomcat}

Um kundenspezifische Einstellungen zu definieren, können Sie eine Datei **user_contexts.xml** im Ordner **/tomcat-8/conf** erstellen, die auch die Datei **contexts.xml** enthält.

Diese Datei enthält die folgenden Informationen:

```
 <Context path='/foo' docBase='../customers/foo'   crossContext='true' debug='0' reloadable='true' trusted='false'/>
```

Bei Bedarf kann dieser Vorgang serverseitig reproduziert werden.
