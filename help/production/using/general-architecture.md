---
product: campaign
title: Allgemeine Architektur
description: Allgemeine Architektur
feature: Monitoring, Architecture
audience: production
content-type: reference
topic-tags: introduction
exl-id: 3bfb5448-6996-4080-bf9a-434f1207637e
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 4%

---

# Allgemeine Architektur{#general-architecture}



## Mindestarchitektur {#minimum-architecture}

In einer Mindestkonfiguration funktioniert Adobe Campaign mit:

* den Adobe Campaign-Anwendungsserver,
* Datenbank.

  ![](assets/formation_exploitation.png)

Dieses Diagramm zeigt, dass der einzige Traffic, der im Kontext einer minimalen Architektur involviert ist, Folgendes ist:

1. HTTP-Protokolldatenverkehr zum Adobe Campaign-Server über das Internet,
1. SMTP-Protokolltraffic vom und zum Adobe Campaign-Server über das Internet.

## Verteilte Architektur {#distributed-architecture}

Adobe Campaign besteht aus mehreren Modulen, die auf mehrere Maschinen verteilt werden können. Dieser Betriebsmodus hat mehrere Vorteile:

* Lastenausgleich,
* Einrichtung der Modulredundanz,
* Aufbau einer über mehrere Dienstleister verteilten Architektur (Segmentierung der angebotenen Dienste).

![](assets/architecturerepartie.png)

Die Verteilung der Module über mehrere Maschinen bietet große Flexibilität bei der Bedienung und verbesserte Anpassungsfähigkeit.

>[!NOTE]
>
>Weitere Informationen zu den verschiedenen Architekturen finden Sie in [diesem Abschnitt](../../installation/using/general-architecture.md).

## Liste offener Ports {#list-of-open-ports}

| Port-Nummer | Betroffenes Adobe Campaign-Modul oder -Anwendung | Konfigurierbar |
|---|---|---|
| 443/tcp oder 80/tcp | Webserver (Apache/IIS) | JA |
| 6666/udp (lokal) | Adobe Campaign: Syslogd | JA |
| 8005/tcp (lokal) | Adobe Campaign: Webmodul | JA |
| 8080/tcp | Adobe Campaign: Webmodul (tomcat) | JA |
| 7777 | Statistikserver (stat-Server) | JA |
