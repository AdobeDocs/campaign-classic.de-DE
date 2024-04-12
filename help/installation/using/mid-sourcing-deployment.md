---
product: campaign
title: Mid-Sourcing-Bereitstellung
description: Mid-Sourcing-Bereitstellung
feature: Installation, Architecture, Deployment
audience: installation
content-type: reference
topic-tags: deployment-types-
exl-id: 8a4d7ef1-de5b-4aee-a527-1b74d987ba61
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 16%

---

# Mid-Sourcing-Bereitstellung{#mid-sourcing-deployment}



Diese Konfiguration ist eine optimale Zwischenlösung zwischen einer gehosteten (ASP)-Konfiguration und der Internalisierung. Die nach außen gerichteten Ausführungskomponenten werden auf einem &quot;Mid-Sourcing&quot;-Server ausgeführt, der in Adobe Campaign gehostet wird.

>[!NOTE]
>
>Um diese Art der Bereitstellung einzurichten, müssen Sie die entsprechende Option erwerben. Bitte überprüfen Sie Ihren Lizenzvertrag.

Die allgemeine Kommunikation zwischen Servern und Prozessen erfolgt gemäß dem folgenden Schema:

![](assets/s_ncs_install_midsourcing.png)

* Die Ausführungs- und Bounce-Management-Module sind in der Instanz deaktiviert.
* Das Programm ist so konfiguriert, dass Nachrichten auf einem entfernten &quot;Mid-Sourced&quot;-Server ausgeführt werden, der über SOAP-Aufrufe (über HTTP oder HTTPS) gesteuert wird.

## Funktionen {#features}

### Vorteile {#advantages}

* Vereinfachte Serverkonfiguration: Es ist nicht erforderlich, dass der Kunde nach außen gerichtete Module (mta und inMail) konfiguriert.
* Eingeschränkte Bandbreitennutzung: Da die Ausführung vom Mid-Sourcing-Server erfolgt, ist nur eine ausreichende Bandbreite erforderlich, um Personalisierungsdaten an den Mid-Sourcing-Server zu senden.
* Hohe Verfügbarkeit ist kein internes Problem mehr: Das Problem wird auf den Mid-Sourcing-Server (Umleitung, Mirrorseiten, Ausführungsserver usw.) verschoben.
* Die Datenbank verlässt das Unternehmen nicht: Es werden nur Daten an den Mid-Sourcing-Server gesendet, die zum Zusammenstellen der Nachrichten erforderlich sind (HTTPS kann dazu verwendet werden).
* Diese Art der Bereitstellung kann eine Lösung für Architekturen mit hohem Volumen (viele Empfänger in der Datenbank) mit einem erheblichen Versanddurchsatz sein.

### Nachteile {#disadvantages}

* Aufgrund der Zeit, die benötigt wird, um Informationen vom Mid-Sourcing-Server zurückzuerhalten, ist die Anzeige von Informationen zur Ausführung von Nachrichten und zur Berichterstellung nur geringfügig verzögert.
* Umfragen und Webformulare verbleiben auf der Client-Plattform.

### Empfohlene Ausrüstung {#recommended-equipment}

* Anwendungsserver: 2-GHz-Quad-Core-CPU, 4 GB RAM, Software RAID 1-80-GB-SATA-Festplatte.
* Datenbankserver: 3-GHz-bi-quad-Core-CPUs, mindestens 4 GB RAM, Hardware-RAID 10 15000RPM SAS-Festplatte, die Anzahl je nach Größe und erwarteter Leistung der Datenbank.

>[!NOTE]
>
>Umleitung und Mid-Sourcing sind separate Elemente, der Tracking-Server wird jedoch im Allgemeinen für die Mid-Sourcing-Server freigegeben.

## Installation und Konfiguration {#installation-and-configuration-steps-}

### Voraussetzungen {#prerequisites}

* JDK auf dem Anwendungsserver.
* Zugriff auf einen Datenbankserver auf dem Anwendungsserver.
* Firewall konfiguriert, um HTTP (80)- oder HTTPS (443)-Ports zum Mid-Sourcing-Server zu öffnen.

### Installation und Konfiguration (Mid-Sourcing-Bereitstellung) {#installing-and-configuring--mid-sourcing-deployment-}

Siehe Abschnitt [Mid-Sourcing-Server](../../installation/using/mid-sourcing-server.md).
