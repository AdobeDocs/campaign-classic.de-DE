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
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 4%

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
