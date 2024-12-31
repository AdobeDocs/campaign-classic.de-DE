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



## Minimale Architektur {#minimum-architecture}

Bei einer Mindestkonfiguration wird Adobe Campaign wie folgt ausgeführt:

* den Adobe Campaign-Anwendungsserver,
* Die Datenbank.

  ![](assets/formation_exploitation.png)

Dieses Diagramm zeigt, dass der einzige Traffic, der im Kontext einer Mindestarchitektur involviert ist, ist:

1. HTTP-Protokollverkehr zum Adobe Campaign-Server über das Internet,
1. SMTP-Protokoll-Traffic vom und zum Adobe Campaign-Server über das Internet.

## Verteilte Architektur {#distributed-architecture}

Adobe Campaign besteht aus mehreren Modulen, die auf mehrere Computer verteilt werden können. Diese Betriebsart hat mehrere Vorteile:

* Lastausgleich,
* Einrichtung der Modulredundanz,
* Aufbau einer auf mehrere Dienstleister aufgegliederten Architektur (Segmentierung der erbrachten Dienstleistungen).

![](assets/architecturerepartie.png)

Die Modulverteilung auf mehrere Maschinen bietet eine hohe Flexibilität und verbesserte Anpassungsfähigkeit.

>[!NOTE]
>
>Weiterführende Informationen zu den verschiedenen Architekturen finden Sie [diesem Abschnitt](../../installation/using/general-architecture.md).

## Liste der offenen Ports {#list-of-open-ports}

| Portnummer | Betroffenes Adobe Campaign-Modul oder Programm | Konfigurierbar |
|---|---|---|
| 443/TCP oder 80/TCP | Webserver (Apache/IIS) | JA |
| 6666/UDP (lokal) | Adobe Campaign: syslogd | JA |
| 8005/TCP (lokal) | Adobe Campaign: Web-Modul | JA |
| 8080/TCP | Adobe Campaign: Web-Modul (Tomcat) | JA |
| 7777 | Statistikserver (stat-server) | JA |
