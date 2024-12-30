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



Diese Konfiguration ist eine optimale Zwischenlösung zwischen einer gehosteten (ASP)-Konfiguration und der Internalisierung. Die nach außen gerichteten Ausführungskomponenten werden auf einem bei Adobe Campaign gehosteten „Mid-Sourcing“-Server ausgeführt.

>[!NOTE]
>
>Um diesen Bereitstellungstyp einzurichten, benötigen Sie die entsprechende Option. Bitte überprüfen Sie Ihren Lizenzvertrag.

Die allgemeine Kommunikation zwischen Servern und Prozessen erfolgt gemäß dem folgenden Schema:

![](assets/s_ncs_install_midsourcing.png)

* Die Ausführungs- und Bounce-Management-Module sind in der Instanz deaktiviert.
* Das Programm ist so konfiguriert, dass Nachrichten auf einem entfernten &quot;Mid-Sourced&quot;-Server ausgeführt werden, der über SOAP-Aufrufe (über HTTP oder HTTPS) gesteuert wird.

## Funktionen {#features}

### Vorteile {#advantages}

* Vereinfachte Server-Konfiguration: Es ist nicht erforderlich, dass der Kunde nach außen gerichtete Module (MTA und InMail) konfiguriert.
* Eingeschränkte Bandbreitennutzung: Da die Ausführung durch den Mid-Sourcing-Server erfolgt, ist nur ausreichend Bandbreite erforderlich, um Personalisierungsdaten an den Mid-Sourcing-Server zu senden.
* Hohe Verfügbarkeit ist kein internes Problem mehr: Das Problem wird auf den Mid-Sourcing-Server verschoben (Umleitung, Mirror-Seiten, Ausführungs-Server usw.).
* Die Datenbank verlässt das Unternehmen nicht: Nur Daten, die zur Zusammenstellung der Nachrichten erforderlich sind, werden an den Mid-Sourcing-Server gesendet (hierfür kann HTTPS verwendet werden).
* Diese Art der Bereitstellung kann eine Lösung für Architekturen mit hohem Volumen (viele Empfänger in der Datenbank) mit einem erheblichen Versanddurchsatz sein.

### Nachteile {#disadvantages}

* Leichte Verzögerung bei der Anzeige von Informationen zur Nachrichtenausführung und der Reporting-Funktionalität, da der Mid-Sourcing-Server mehr Zeit für das Zurückholen von Informationen benötigt.
* Umfragen und Web-Formulare verbleiben auf der Client-Plattform.

### Empfohlene Ausrüstung {#recommended-equipment}

* Anwendungsserver: Quad-Core CPU mit 2 GHz, 4 GB RAM, Software-RAID 1 SATA-Festplatte mit 80 GB.
* Datenbank-Server: 3 GHz Bi-Quad-Core-CPUs, mindestens 4 GB RAM, Hardware-RAID 10 15000RPM SAS-Festplatte, die Anzahl hängt von der Größe und der erwarteten Leistung der Datenbank ab.

>[!NOTE]
>
>Weiterleitung und Mid-Sourcing sind separate Elemente, der Tracking-Server wird jedoch im Allgemeinen mit den Mid-Sourcing-Servern geteilt.

## Installations- und Konfigurationsschritte {#installation-and-configuration-steps-}

### Voraussetzungen {#prerequisites}

* JDK auf dem Anwendungsserver
* Zugriff auf einen Datenbankserver auf dem Anwendungsserver.
* Firewall konfiguriert, um HTTP (80)- oder HTTPS (443)-Ports zum Mid-Sourcing-Server zu öffnen.

### Installieren und Konfigurieren (Mid-Sourcing-Bereitstellung) {#installing-and-configuring--mid-sourcing-deployment-}

Siehe [Mid-Sourcing-](../../installation/using/mid-sourcing-server.md).
