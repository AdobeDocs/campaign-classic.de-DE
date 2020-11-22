---
solution: Campaign Classic
product: campaign
title: Erfassen aller Besuche
description: Erfassen aller Besuche
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 3%

---


# Erfassen aller Besuche{#collecting-all-visits}

Mit dem von Adobe Campaign bereitgestellten Web-Tracking-Modul können Sie die Besuche bestimmter Seiten der Site erfassen, die ein Empfänger im Zusammenhang mit der Site-Verfolgung nach einem Klick in einer Nachricht durchführt.

Sie können Ihre Plattform jedoch so konfigurieren, dass alle Seitenbesuche mit einem Web-Trackingtag von einem Plattformbenutzer erfasst werden.

Ein Plattformbenutzer ist ein Empfänger, der bereits ein Targeting durch einen Versand durchgeführt hat und mindestens einmal auf eine empfangene Nachricht geklickt hat. Zur Identifizierung dieses Empfängers wird ein permanentes Cookie verwendet.

>[!IMPORTANT]
>
>Die Adobe Campaign-Plattform ist nicht zur Verwendung als Website-Verfolgungswerkzeug über den Kontext des Besuchs der Site nach einem Klick in einer Nachricht hinaus vorgesehen. Wenn diese Option aktiviert ist, kann dies zu einem sehr hohen Ressourcenverbrauch auf den Computern führen, auf denen Ihre Server gehostet werden (Umleitung, Anwendung und Datenbank). Es wird empfohlen, sicherzustellen, dass Ihre Hardwarearchitektur diese Belastung unterstützen kann, und zu vermeiden, dass Web-Trackingtag auf den am häufigsten besuchten Seiten wie der Startseite platziert werden.

## Serverkonfiguration {#server-configuration}

Die Server werden durch Überladen bestimmter Elemente der Datei &quot; **serverConf.xml** &quot;konfiguriert. Diese Dateien werden im **conf** -Unterverzeichnis des Installationsordners des Adobe Campaigns gespeichert.

### Weiterleitungsserver {#redirection-server}

Legen Sie für den Umleitungsserver das Attribut **trackWebVisitors** des **Umleitungselements** auf **true** fest.

```
<redirection P3PCompactPolicy="CAO DSP COR CURa DEVa TAIa OUR BUS IND UNI COM NAV"
databaseId="" defLogCount="30" expirationURL="" maxJobsInCache="100"
startRedirection="true" startRedirectionInModule="true" trackWebVisitors="true"
trackingPassword=""
```

## Konfigurieren einer Kampagne mit Standardübereinstimmung {#configuring-a-default-matching-campaign}

Zur Ansicht von Verfolgungsinformationen über Ihre Client-Konsole müssen Sie:

* Erstellen eines **Dummy-Versands** (die Zuordnung des Versands muss mit der Zuordnung des Zielgruppe-Schemas identisch sein),
* Geben Sie den **internen Namen** dieses Versands in der Option **NmsTracking_WebTrackingDelivery** ein.

Alle Site-Verfolgungsinformationen, die nicht direkt nach einem Klick in einer E-Mail erfolgen, können in dem erstellten Platzhalter-Versand angezeigt werden.
