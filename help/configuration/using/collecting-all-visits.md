---
product: campaign
title: Erfassen aller Besuche
description: Erfassen aller Besuche
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
exl-id: cc554d0d-bbab-4f72-b870-5fef5a2fda9d
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 3%

---

# Erfassen aller Besuche{#collecting-all-visits}

Mit dem von Adobe Campaign bereitgestellten Webtracking-Modul können Sie die Besuche auf bestimmten Seiten der Site erfassen, die von einem Empfänger im Rahmen des Site-Trackings nach einem Klick in einer Nachricht ausgeführt werden.

Sie können Ihre Plattform jedoch so konfigurieren, dass alle Besuche auf Seiten mit einem Web-Tracking-Tag durch einen Benutzer erfasst werden, der der Plattform bekannt ist.

Ein Benutzer, der der Plattform bekannt ist, ist ein Empfänger, der bereits in der Zielgruppe eines Versands war und mindestens einmal in einer empfangenen Nachricht geklickt hat. Dieser Empfänger wird anhand eines permanenten Cookies identifiziert.

>[!IMPORTANT]
>
>Die Adobe Campaign-Plattform ist nicht zur Verwendung als Website-Tracking-Tool vorgesehen, das über den Kontext des Besuchs der Site nach einem Klick in einer Nachricht hinausgeht. Wenn diese Option aktiviert ist, kann dies zu einer sehr hohen Nutzung von Ressourcen auf den Computern führen, auf denen Ihre Server gehostet werden (Umleitung, Anwendung und Datenbank). Es wird empfohlen, sicherzustellen, dass Ihre Hardware-Architektur diese Auslastung unterstützen kann, und zu vermeiden, dass Webtrackingtags auf den am häufigsten besuchten Seiten wie der Startseite platziert werden.

## Konfiguration des Servers {#server-configuration}

Die Server werden konfiguriert, indem bestimmte Elemente der **serverConf.xml** -Datei. Diese Dateien werden im **conf** -Unterverzeichnis des Adobe Campaign-Installationsordners.

### Weiterleitungsserver {#redirection-server}

Legen Sie für den Weiterleitungsserver die **trackWebVisitors** -Attribut **Umleitung** Element zu **true**.

```
<redirection P3PCompactPolicy="CAO DSP COR CURa DEVa TAIa OUR BUS IND UNI COM NAV"
databaseId="" defLogCount="30" expirationURL="" maxJobsInCache="100"
startRedirection="true" startRedirectionInModule="true" trackWebVisitors="true"
trackingPassword=""
```

## Standardkampagne konfigurieren {#configuring-a-default-matching-campaign}

Um Tracking-Informationen über Ihre Clientkonsole anzuzeigen, müssen Sie:

* Erstellen Sie eine **Platzhalterversand** (Das Versand-Mapping muss mit dem Mapping des Zielschemas identisch sein),
* Geben Sie die **interner Name** des Versands im **NmsTracking_WebTrackingDelivery** -Option.

Alle Site-Tracking-Informationen, die nicht direkt nach einem Klick in eine E-Mail folgen, können im erstellten Platzhalterversand angezeigt werden.
