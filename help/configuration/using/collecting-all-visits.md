---
product: campaign
title: Erfassen aller Besuche
description: Erfassen aller Besuche
feature: Configuration, Instance Settings
role: Developer
exl-id: cc554d0d-bbab-4f72-b870-5fef5a2fda9d
TQID: 'https://experienceleague.adobe.com/EdEX0IPygnmmYAqewEpX2jRqrCZ723itOEW6DhnMSl8'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: 7f0a1ee5-eeb8-5478-a9cd-b1896f033118
    internal-label: Instance Settings
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: a14877cc-63b1-41d9-bf0b-5f97cadd0417
    internal-label: Configuration guidelines
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 3%
---
# Erfassen aller Besuche{#collecting-all-visits}

Mit dem von Adobe Campaign bereitgestellten Webtracking-Modul können Sie die Besuche auf bestimmten Seiten der Website erfassen, die von einem Empfänger im Rahmen des Site-Trackings nach einem Klick in einer Nachricht ausgeführt werden.

Sie können Ihre Plattform jedoch so konfigurieren, dass alle Besuche auf Seiten mit einem Webtracking-Tag durch einen der Plattform bekannten Benutzer erfasst werden.

Ein der Plattform bekannter Benutzer ist ein Empfänger, der bereits in einen Versand einbezogen wurde und der mindestens einmal auf eine empfangene Nachricht geklickt hat. Zur Identifizierung dieses Empfängers wird ein permanentes Cookie verwendet.

>[!IMPORTANT]
>
>Die Adobe Campaign-Plattform ist nicht für die Verwendung als Website-Tracking-Tool über den Kontext des Besuchs der Website nach einem Klick in einer Nachricht hinaus vorgesehen. Wenn diese Option aktiviert ist, kann dies zu einem sehr hohen Ressourcenverbrauch auf den Computern führen, auf denen Ihre Server gehostet werden (Umleitung, Anwendung und Datenbank). Es wird empfohlen sicherzustellen, dass Ihre Hardwarearchitektur diese Last unterstützen kann, und Web-Tracking-Tags nicht auf den am häufigsten besuchten Seiten zu platzieren, z. B. auf der Startseite.

## Serverkonfiguration {#server-configuration}

Die Server werden durch Überladen bestimmter Elemente der Datei **serverConf.xml“**. Diese Dateien werden im Unterverzeichnis **conf** des Adobe Campaign-Installationsverzeichnisses gespeichert.

### Weiterleitungs-Server {#redirection-server}

Legen Sie für den Weiterleitungsserver das Attribut **trackWebVisitors** des Elements **redirect** auf **true** fest.

```
<redirection P3PCompactPolicy="CAO DSP COR CURa DEVa TAIa OUR BUS IND UNI COM NAV"
databaseId="" defLogCount="30" expirationURL="" maxJobsInCache="100"
startRedirection="true" startRedirectionInModule="true" trackWebVisitors="true"
trackingPassword=""
```

## Konfigurieren einer standardmäßigen Abgleichskampagne {#configuring-a-default-matching-campaign}

Um Tracking-Informationen über Ihre Client-Konsole anzuzeigen, müssen Sie:

* Erstellen Sie **einen Pseudo-Versand** (das Versand-Mapping muss mit dem Mapping des Zielschemas identisch sein),
* Geben Sie den **internen Namen** dieses Versands in der Option **NmsTracking_WebTrackingDelivery** ein.

Alle Site-Tracking-Informationen, die nicht direkt nach einem Klick in einer E-Mail angezeigt werden, können im erstellten Dummy-Versand angezeigt werden.
