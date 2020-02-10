---
title: Erfassen aller Besuche
seo-title: Erfassen aller Besuche
description: Erfassen aller Besuche
seo-description: null
page-status-flag: never-activated
uuid: c2869b3d-33bb-4a22-a8e6-ac037f0665d9
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
discoiquuid: 7f841368-3867-4d6e-9720-c038d9bea0ce
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Erfassen aller Besuche{#collecting-all-visits}

Mit dem von Adobe Campaign bereitgestellten Web-Tracking-Modul können Sie die Besuche bestimmter Seiten der Site erfassen, die ein Empfänger im Zusammenhang mit der Site-Verfolgung nach einem Klick in einer Nachricht durchführt.

Sie können Ihre Plattform jedoch so konfigurieren, dass alle Besuche von Seiten mit einem Web-Tracking-Tag durch einen Benutzer erfasst werden, der der Plattform bekannt ist.

Ein Benutzer, der der Plattform bekannt ist, ist ein Empfänger, für den bereits eine Zustellung geplant war und der mindestens einmal auf eine empfangene Nachricht geklickt hat. Zur Identifizierung dieses Empfängers wird ein permanentes Cookie verwendet.

>[!CAUTION]
>
>Die Adobe Campaign-Plattform ist nicht zur Verwendung als Website-Verfolgungstool über den Kontext des Besuchs der Site hinaus nach einem Klick in einer Nachricht hinaus vorgesehen. Wenn diese Option aktiviert ist, kann dies zu einem sehr hohen Ressourcenverbrauch auf den Computern führen, auf denen Ihre Server gehostet werden (Umleitung, Anwendung und Datenbank). Es wird empfohlen, sicherzustellen, dass Ihre Hardware-Architektur diese Belastung unterstützen kann, und zu vermeiden, dass Web-Tracking-Tags auf den am häufigsten besuchten Seiten wie der Homepage platziert werden.

## Serverkonfiguration {#server-configuration}

Die Server werden durch Überladen bestimmter Elemente der Datei &quot; **serverConf.xml** &quot;konfiguriert. Diese Dateien werden im **conf** -Unterverzeichnis des Adobe Campaign-Installationsordners gespeichert.

### Weiterleitungsserver {#redirection-server}

Legen Sie für den Umleitungsserver das Attribut **trackWebVisitors** des **Umleitungselements** auf **true** fest.

```
<redirection P3PCompactPolicy="CAO DSP COR CURa DEVa TAIa OUR BUS IND UNI COM NAV"
databaseId="" defLogCount="30" expirationURL="" maxJobsInCache="100"
startRedirection="true" startRedirectionInModule="true" trackWebVisitors="true"
trackingPassword=""
```

## Konfigurieren einer Standardkampagne {#configuring-a-default-matching-campaign}

Um Verfolgungsinformationen über Ihre Client-Konsole anzuzeigen, müssen Sie:

* Erstellen einer **Dummy-Auslieferung** (die Auslieferungszuordnung muss mit der Zuordnung des Zielschemas identisch sein),
* Geben Sie den **internen Namen** dieser Bereitstellung in der Option **NmsTracking_WebTrackingDelivery** ein.

Alle Site-Verfolgungsinformationen, die nicht direkt nach einem Klick in einer E-Mail erfolgen, können in der erstellten Platzhalterübergabe angezeigt werden.
