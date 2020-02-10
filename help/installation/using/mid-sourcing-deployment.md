---
title: Bereitstellung von Mid-Sourcing
seo-title: Bereitstellung von Mid-Sourcing
description: Bereitstellung von Mid-Sourcing
seo-description: null
page-status-flag: never-activated
uuid: e359c486-7ee6-4295-80fc-4c371a0ef068
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: deployment-types-
discoiquuid: 19220d8e-9494-46b4-9aa0-4c4a729aea96
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: be590c6d993eecacf51736e3c3e415addae5c6bd

---


# Bereitstellung von Mid-Sourcing{#mid-sourcing-deployment}

Diese Konfiguration ist eine optimale Zwischenlösung zwischen einer gehosteten (ASP) Konfiguration und Internalisierung. Die nach außen gerichteten Ausführungskomponenten werden auf einem &quot;Mid-Sourcing&quot;-Server ausgeführt, der bei Adobe Campaign gehostet wird.

>[!NOTE]
>
>Um diese Art der Bereitstellung einzurichten, müssen Sie die entsprechende Option erwerben. Bitte überprüfen Sie Ihren Lizenzvertrag.

Die allgemeine Kommunikation zwischen Servern und Prozessen erfolgt gemäß dem folgenden Schema:

![](assets/s_ncs_install_midsourcing.png)

* Die Management-Module für Ausführung und Absprung sind in der Instanz deaktiviert.
* Die Anwendung ist so konfiguriert, dass eine Nachrichtenausführung auf einem Remote-Server mit mittlerer Quelle durchgeführt wird, der mit SOAP-Aufrufen (über HTTP oder HTTPS) angetrieben wird.

## Funktionen {#features}

### Vorteile {#advantages}

* Vereinfachte Serverkonfiguration: Es ist nicht erforderlich, dass der Kunde nach außen gerichtete Module (mta und inMail) konfiguriert.
* Eingeschränkte Nutzung der Bandbreite: Da die Ausführung vom Server mit mittlerer Quelle erfolgt, ist nur eine ausreichende Bandbreite erforderlich, um Personalisierungsdaten an den Server mit mittlerer Quelle zu senden.
* Hohe Verfügbarkeit ist kein internes Problem mehr: Das Problem wird auf den Server mit mittlerer Quelle (Umleitung, Spiegelseiten, Ausführungsserver usw.) verlagert.
* Die Datenbank verlässt das Unternehmen nicht: Nur Daten, die zum Zusammenstellen der Nachrichten erforderlich sind, werden an den mid-sourcing-Server gesendet (dazu kann HTTPS verwendet werden).
* Diese Art der Bereitstellung kann eine Lösung für große Volumen-Architekturen (viele Empfänger in der Datenbank) mit einem erheblichen Bereitstellungsdurchsatz sein.

### Nachteile {#disadvantages}

* Geringfügige Verzögerung bei der Anzeige von Informationen zur Nachrichtenausführung und für die Berichterstellungsfunktion aufgrund der Zeit, die benötigt wird, um Informationen vom mid-sourcing-Server zurückzuerhalten.
* Umfragen und Webformulare bleiben auf der Client-Plattform erhalten.

### Empfohlene Ausrüstung {#recommended-equipment}

* Anwendungsserver: 2 GHz Quadcore-CPU, 4 GB RAM, Software RAID 1 80 GB SATA-Festplatte.
* Datenbankserver: 3 GHz-Kern-CPUs mit zwei Quadraten, mindestens 4 GB RAM, Hardware-RAID 10 15000RPM SAS-Festplatte, die Anzahl je nach Größe und erwarteter Leistung der Datenbank.

>[!NOTE]
>
>Umleitung und Mid-Sourcing sind separate Elemente, aber der Tracking-Server wird im Allgemeinen für die Mid-Sourcing-Server freigegeben.

## Installation und Konfigurationsschritte {#installation-and-configuration-steps-}

### Voraussetzungen {#prerequisites}

* JDK auf dem Anwendungsserver.
* Zugriff auf einen Datenbankserver auf dem Anwendungsserver.
* Firewall konfiguriert, um HTTP (80)- oder HTTPS (443)-Anschlüsse an den mid-sourcing-Server zu öffnen.

### Installieren und Konfigurieren (Bereitstellung mit mittlerer Quelle) {#installing-and-configuring--mid-sourcing-deployment-}

Siehe [Mid-Sourcing-Server](../../installation/using/mid-sourcing-server.md).
