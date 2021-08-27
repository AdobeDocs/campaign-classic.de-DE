---
product: campaign
title: Erfassen aller Besuche
description: Erfassen aller Besuche
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
exl-id: cc554d0d-bbab-4f72-b870-5fef5a2fda9d
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 3%

---

# Erfassen aller Besuche{#collecting-all-visits}

![](../../assets/v7-only.svg)

Mit dem von Adobe Campaign bereitgestellten Webtracking-Modul können Sie die Besuche auf bestimmten Seiten der Site erfassen, die von einem Empfänger im Rahmen des Site-Trackings nach einem Klick in einer Nachricht ausgeführt werden.

Sie können Ihre Plattform jedoch so konfigurieren, dass alle Besuche auf Seiten mit einem Web-Tracking-Tag durch einen Benutzer erfasst werden, der der Plattform bekannt ist.

Ein Benutzer, der der Plattform bekannt ist, ist ein Empfänger, der bereits in der Zielgruppe eines Versands war und mindestens einmal in einer empfangenen Nachricht geklickt hat. Dieser Empfänger wird anhand eines permanenten Cookies identifiziert.

>[!IMPORTANT]
>
>Die Adobe Campaign-Plattform ist nicht zur Verwendung als Website-Tracking-Tool vorgesehen, das über den Kontext des Besuchs der Site nach einem Klick in einer Nachricht hinausgeht. Wenn diese Option aktiviert ist, kann dies zu einer sehr hohen Nutzung von Ressourcen auf den Computern führen, auf denen Ihre Server gehostet werden (Umleitung, Anwendung und Datenbank). Es wird empfohlen, sicherzustellen, dass Ihre Hardware-Architektur diese Auslastung unterstützen kann, und zu vermeiden, dass Webtrackingtags auf den am häufigsten besuchten Seiten wie der Startseite platziert werden.

## Konfiguration des Servers {#server-configuration}

Die Server werden durch Überladen bestimmter Elemente der Datei **serverConf.xml** konfiguriert. Diese Dateien werden im Unterverzeichnis **conf** des Adobe Campaign-Installationsordners gespeichert.

### Weiterleitungsserver {#redirection-server}

Setzen Sie für den Weiterleitungsserver das Attribut **trackWebVisitors** des Elements **redirection** auf **true**.

```
<redirection P3PCompactPolicy="CAO DSP COR CURa DEVa TAIa OUR BUS IND UNI COM NAV"
databaseId="" defLogCount="30" expirationURL="" maxJobsInCache="100"
startRedirection="true" startRedirectionInModule="true" trackWebVisitors="true"
trackingPassword=""
```

## Standardkampagne konfigurieren {#configuring-a-default-matching-campaign}

Um Tracking-Informationen über Ihre Clientkonsole anzuzeigen, müssen Sie:

* Erstellen Sie einen **Platzhalterversand** (das Versand-Mapping muss mit dem Mapping des Zielschemas identisch sein),
* Geben Sie den internen Namen **a1/> dieses Versands in die Option** NmsTracking_WebTrackingDelivery **ein.**

Alle Site-Tracking-Informationen, die nicht direkt auf einen Klick in einer E-Mail folgen, können im erstellten Platzhalterversand angezeigt werden.
