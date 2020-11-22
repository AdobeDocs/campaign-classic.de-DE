---
solution: Campaign Classic
product: campaign
title: Allgemeine Architektur
description: Allgemeine Architektur
audience: production
content-type: reference
topic-tags: introduction
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 4%

---


# Allgemeine Architektur{#general-architecture}

## Minimale Architektur {#minimum-architecture}

In einer Mindestkonfiguration funktioniert Adobe Campaign mit:

* adobe campaign-Anwendungsserver,
* die Datenbank.

   ![](assets/formation_exploitation.png)

Dieses Diagramm zeigt, dass der einzige Traffic, der im Zusammenhang mit einer Mindestarchitektur involviert ist, der folgende ist:

1. HTTP-Protokoll-Datenverkehr zum Adobe Campaign-Server über das Internet,
1. SMTP-Protokollverkehr vom und zum Adobe Campaign-Server über das Internet.

## Verteilte Architektur {#distributed-architecture}

Adobe Campaign besteht aus mehreren Modulen, die über mehrere Rechner heruntergebrochen werden können. Dieser Betriebsmodus hat mehrere Vorteile:

* Lastenausgleich,
* Einrichtung der Modulredundanz,
* Aufbau einer auf mehrere Dienstleister aufgegliederten Architektur (Segmentierung der bereitgestellten Dienste).

![](assets/architecturerepartie.png)

Die Verteilung von Modulen auf mehrere Maschinen bietet große Flexibilität bei der Handhabung und verbesserte Anpassbarkeit.

>[!NOTE]
>
>For more on the various architectures, refer to [this section](../../installation/using/general-architecture.md).

## Liste offener Häfen {#list-of-open-ports}

| Anschlussnummer | Betroffenes Adobe Campaign-Modul oder -Anwendung | Konfigurierbar |
|---|---|---|
| 443/tcp oder 80/tcp | Webserver (Apache/IIS) | JA |
| 6666/udp (lokal) | Adobe Campaign: Syslogd | JA |
| 8005/tcp (lokal) | Adobe Campaign: Webmodul | JA |
| 8080/tcp | Adobe Campaign: web module (tomcat) | JA |
| 7777 | Statistischer Server (STAT-Server) | JA |

