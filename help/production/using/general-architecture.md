---
title: Allgemeine Architektur
seo-title: Allgemeine Architektur
description: Allgemeine Architektur
seo-description: null
page-status-flag: never-activated
uuid: a565a10c-cbef-455a-aa1d-9be9cd207c7a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: introduction
discoiquuid: f4879774-afe5-4556-ab60-9297cabbca2c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Allgemeine Architektur{#general-architecture}

## Minimale Architektur {#minimum-architecture}

Adobe Campaign funktioniert in einer Mindestkonfiguration mit:

* Adobe Campaign-Anwendungsserver,
* die Datenbank.

   ![](assets/formation_exploitation.png)

Dieses Diagramm zeigt, dass der einzige Traffic, der im Zusammenhang mit einer Mindestarchitektur involviert ist, der folgende ist:

1. HTTP-Protokoll-Traffic zum Adobe Campaign-Server über das Internet,
1. Traffic des SMTP-Protokolls vom und zum Adobe Campaign-Server über das Internet.

## Verteilte Architektur {#distributed-architecture}

Adobe Campaign besteht aus mehreren Modulen, die auf mehreren Computern unterteilt werden können. Dieser Betriebsmodus hat mehrere Vorteile:

* Lastenausgleich,
* Einrichtung der Modulredundanz,
* Aufbau einer Architektur, die über mehrere Dienstleister aufgegliedert ist (Segmentierung der bereitgestellten Dienste).

![](assets/architecturerepartie.png)

Die Verteilung von Modulen auf mehrere Maschinen bietet große Flexibilität bei der Handhabung und verbesserte Anpassbarkeit.

>[!NOTE]
>
>For more on the various architectures, refer to [this section](../../installation/using/general-architecture.md).

## Liste offener Anschlüsse {#list-of-open-ports}

| Anschlussnummer | Betreffendes Adobe Campaign-Modul oder -Anwendung | Konfigurierbar |
|---|---|---|
| 443/tcp oder 80/tcp | Webserver (Apache/IIS) | JA |
| 6666/udp (lokal) | Adobe Campaign: Syslogd | JA |
| 8005/tcp (lokal) | Adobe Campaign: Webmodul | JA |
| 8080/tcp | Adobe Campaign: web module (tomcat) | JA |
| 7777 | Statistischer Server (STAT-Server) | JA |

