---
product: campaign
title: Allgemeine Architektur
description: Erfahren Sie, wie Sie Campaign Classic installieren und konfigurieren können.
audience: installation
content-type: reference
topic-tags: architecture-and-hosting-models
exl-id: 04e6dc17-427b-4745-84cc-bf45c03dbf81
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1340'
ht-degree: 51%

---

# Allgemeine Architektur{#general-architecture}

![](../../assets/v7-only.svg)

Die typische Implementierung einer Adobe Campaign-Lösung setzt sich aus folgenden Komponenten zusammen:

* **Personalisierte Client-Umgebung**

   Intuitive grafische Benutzeroberfläche, über die Benutzer Marketingangebote kommunizieren und verfolgen, Kampagnen erstellen, alle Marketing-Aktivitäten, Programme und Pläne - einschließlich E-Mails, Workflows und Landingpages - überprüfen und verwalten, Kundenprofile erstellen und verwalten sowie Kundentypen definieren können.

* **Entwicklungsumgebung**

   Eine Server-seitige Software, die Marketing-Kampagnen über benutzerseitig ausgewählte Kommunikationskanäle ausführt, die von E-Mail, SMS und Push-Benachrichtigungen über Briefpost bis zu Web- und Social-Media-Kanälen reichen. In der Benutzeroberfläche werden dabei zugehörige Regeln und Workflows festgelegt.

* **Datenbank-Container**

   Basierend auf relativer Datenbanktechnologie speichert die Adobe Campaign-Datenbank alle Kundeninformationen, Kampagnenkomponenten, Angebote und Workflows sowie Kampagnenergebnisse in Container mit Kundendatenbanken.

Adobe Campaign basiert auf einer Service-orientierten Architektur (SOA) und umfasst mehrere Funktionsmodule. Diese Module können auf einem oder mehreren Computern in einzelnen oder mehreren Instanzen bereitgestellt werden, je nach Einschränkungen hinsichtlich Skalierbarkeit, Verfügbarkeit und Dienstisolierung. Der Umfang der Implementierungskonfigurationen ist daher sehr breit angelegt und erstreckt sich über einen zentralen Computer bis hin zu Konfigurationen, die mehrere dedizierte Server über mehrere Sites hinweg umfassen.

>[!NOTE]
>
>Als Softwareanbieter spezifizieren wir kompatible Hardware- und Software-Infrastrukturen. Die hier gegebenen Hardware-Empfehlungen dienen nur zu Informationszwecken und basieren auf unserer Erfahrung. Die Adobe haftet nicht für Entscheidungen, die auf dieser Grundlage getroffen werden. Dies hängt auch von Ihren Geschäftsregeln und -praktiken sowie von der Kritikalität und den erforderlichen Leistungsstufen des Projekts ab.

![](assets/s_ncs_install_architecture.png)

>[!CAUTION]
>
>Sofern nicht ausdrücklich anders angegeben, obliegt die Installation, Aktualisierung und Wartung auf allen Komponenten einer Adobe Campaign-Plattform dem/den Maschinadministrator(en), der/die diese Komponenten hostet. Dazu gehört die Implementierung der Voraussetzungen für Adobe Campaign-Anwendungen sowie die Einhaltung von Campaign [Kompatibilitätsmatrix](../../rn/using/compatibility-matrix.md) zwischen Komponenten.

## Präsentationsschicht {#presentation-layer}

Der Zugriff auf die Anwendung ist je nach den Anforderungen der Benutzer auf unterschiedliche Weise möglich: Rich-Client-, Thin-Client- oder API-Integration.

* **Rich-Client**: Die Hauptbenutzeroberfläche des Programms ist ein Rich-Client, d. h. eine native Anwendung (Windows), die ausschließlich mit Standardinternetprotokollen (SOAP, HTTP usw.) mit dem Adobe Campaign-Anwendungsserver kommuniziert. Diese Konsole bietet eine hervorragende Benutzerfreundlichkeit für die Produktivität, verwendet sehr wenig Bandbreite (durch die Verwendung eines lokalen Caches) und ist für eine einfache Implementierung konzipiert. Diese Konsole kann über einen Internetbrowser bereitgestellt werden, kann automatisch aktualisiert werden und erfordert keine spezifische Netzwerkkonfiguration, da sie nur HTTP(S)-Traffic generiert.
* **Thin Client**: Bestimmte Anwendungsbereiche können über einen einfachen Webbrowser über eine HTML-Benutzeroberfläche aufgerufen werden. Dazu gehören das Berichtsmodul, Etappen der Versandvalidierung, Funktionen des Moduls Dezentrales Marketing (zentrales/lokales), Instanzüberwachung usw. Auf diese Weise können Adobe Campaign-Funktionen in ein Intranet oder ein Extranet integriert werden.
* **Integration über APIs**: In bestimmten Fällen kann das System mithilfe der Web-Services-APIs, die über das SOAP-Protokoll verfügbar gemacht werden, über eine externe Anwendung aufgerufen werden.

## Logische Anwendungsschicht {#logical-application-layer}

Adobe Campaign führt verschiedene Programme in einer zentralen Plattform zusammen und schafft so eine offenen und zugleich skalierbare Architektur. Die Adobe Campaign-Plattform ist auf einer flexiblen Anwendungsebene konzipiert und lässt sich einfach an die geschäftlichen Anforderungen eines Unternehmens anpassen. Dies entspricht sowohl aus funktionaler als auch aus technischer Perspektive den wachsenden Anforderungen des Unternehmens. Dank der verteilten Architektur ist das System linear von mehreren Tausend auf mehrere Millionen Nachrichten skalierbar.

Adobe Campaign stützt sich auf eine Reihe von serverseitigen Prozessen, die zusammenarbeiten.

Dies sind die wichtigsten Prozesse:

**Anwendungs-Server** (nlserver web)

Dieser Prozess stellt das gesamte Spektrum an Adobe Campaign-Funktionen mittels Web-Services-APIs (SOAP - HTTP + XML) zur Verfügung. Darüber hinaus kann er dynamisch die Web-Seiten generieren, die für den HTML-basierten Zugriff verwendet werden (Berichte, Web-Formulare usw.). Um dies zu ermöglichen, umfasst der Prozess einen Apache Tomcat JSP-Server. Dies ist der Prozess, mit dem die Konsole eine Verbindung herstellt.

**Workflow-Engine** (nlserver wfserver)

Diese führt die im Programm definierten Workflow-Prozesse aus.

Außerdem verarbeitet sie zeitweise ausgeführte technische Workflows, darunter:

* Tracking: Wiederherstellen und Konsolidieren von Trackinglogs. Dadurch können Protokolle vom Weiterleitungs-Server abgerufen und die vom Reporting-Modul verwendeten aggregierten Indikatoren erstellt werden.
* Bereinigung: zur Bereinigung von Datenbanken. Dabei wird die Datenbank von alten Datensätzen bereinigt, um zu vermeiden, dass sie übermäßig wächst.
* Rechnungsstellung: Automatischer Versand eines Aktivitätsberichts für die Plattform (Datenbankgröße, Anzahl der Marketing-Aktionen, Anzahl der aktiven Profile usw.).

**Versand-Server** (nlserver mta)

Adobe Campaign umfasst eine native Funktion zum Senden von E-Mails. Dieser Prozess fungiert als SMTP Mail Transfer Agent (MTA). Er personalisiert Nachrichten individuell für den jeweiligen Empfänger und verarbeitet deren physischen Versand. Dies erfolgt mittels Versandvorgängen, wobei zudem auch nachgelagerte, weitere Zustellversuche automatisiert werden. Ist zusätzlich noch Tracking aktiviert, werden die URLs automatisch ersetzt, sodass sie auf den Weiterleitungs-Server verweisen.

Über diesen Prozess ist die Anpassung sowie der automatische Versand an einen Dritt-Router für SMS, Fax und Briefpost möglich.

**Weiterleitungs-Server** (nlserver webmdl)

Bei E-Mails übernimmt Adobe Campaign automatisch das Öffnungs- und Klick-Tracking (wobei das Tracking von Transaktionen auf Website-Ebene ebenfalls möglich ist). Hierfür werden die in den E-Mail-Nachrichten enthaltenen URLs so umgeschrieben, dass sie auf dieses Modul verweisen. Dieses wiederum registriert Internet-Benutzer, während diese an die Ziel-URL weitergeleitet werden.

Zur Sicherstellung maximaler Verfügbarkeit ist dieser Prozess vollkommen unabhängig von der Datenbank: Die anderen Server-Prozesse kommunizieren mit ihm nur über SOAP-Aufrufe (HTTP, HTTPS und XML). Aus technischer Sicht ist diese Funktion in einem Erweiterungsmodul (ISAPI-Erweiterung in IIS, DSO Apache-Modul usw.) eines HTTP-Servers implementiert und nur unter Windows verfügbar.

Daneben sind auch noch weitere technische Prozesse verfügbar:

**Handhabung von Bounce-E-Mails** (nlserver inMail)

Dieser Prozess ermöglicht den automatischen Abruf von E-Mails aus Postfächern, die für den Empfang von Nachrichten konfiguriert sind, die bei fehlgeschlagenem Versand als unzustellbar zurückgesendet werden. Diese Nachrichten werden dann regelbasiert verarbeitet, um die Gründe für die Unzustellbarkeit (z. B. Empfänger unbekannt, Nachrichtenkontingente ausgeschöpft) zu ermitteln und den Versandstatus in der Datenbank zu aktualisieren.

Alle diese Operationen laufen vollkommen automatisch und sind vorkonfiguriert.

**Status des SMS-Versands** (nlserver sms)

Dieser Prozess fragt beim SMS-Router den Status des Versandfortschritts ab und aktualisiert diesen in der Datenbank.

**Schreiben von Log-Nachrichten** (nlserver-syslogd)

Dieser technische Prozess erfasst von anderen Prozessen generierte Log-Nachrichten und -Traces und speichert sie auf der Festplatte. Dadurch stehen im Falle von Problemen umfangreiche Informationen zur Diagnose zur Verfügung.

**Schreiben von Trackinglogs** (nlserver trackinglogd)

Dieser Prozess speichert die Trackinglogs, die durch vom Weiterleitungsprozess generiert werden.

**Schreiben eingehender Ereignisse** (nlserver interactiond)

Dieser Vorgang gewährleistet die Aufzeichnung von im Rahmen der Interaktion eingehenden Ereignisse auf der Festplatte

**Überwachungsmodule** (nlserver watchdog)

Hierbei handelt es sich um einen technischen Primärprozess, der zur Erzeugung der anderen Prozesse dient. Zugleich überwacht er diese aber auch startet sie beim Auftreten von Vorfällen automatisch neu, sodass maximale Systemverfügbarkeit gewährleistet bleibt.

**Statistik-Server** (nlserver stat)

Dieser Prozess erstellt Statistiken zur Anzahl von Verbindungen, zu an die einzelnen Mailserver gesendeten Nachrichten und zu deren Einschränkungen (z. B. Maximalzahl gleichzeitiger Verbindungen, Nachrichten pro Stunde und/oder Verbindung usw.). Ebenfalls lassen sich über diesen Prozess Instanzen oder Computer zusammenführen, sofern diese dieselben öffentlichen IP-Adressen verwenden.

>[!NOTE]
>
>Die vollständige Liste der Adobe Campaign-Module finden Sie unter [dieses Dokuments](../../production/using/operating-principle.md).

## Persistenzschicht {#persistence-layer}

Die Datenbank wird als Persistenzschicht verwendet und enthält fast alle von Adobe Campaign verwalteten Informationen. Dazu gehören funktionale Daten (Profile, Abonnements, Inhalte usw.), technische Daten (Versandaufträge und Protokolle, Trackinglogs usw.) und Arbeitsdaten (Einkäufe, Leads).

Die Zuverlässigkeit der Datenbank ist von größter Bedeutung, da die meisten Adobe Campaign-Komponenten für die Ausführung ihrer Aufgaben Zugriff auf die Datenbank benötigen (mit Ausnahme des Umleitungsmoduls).

Die Plattform wird mit einem vordefinierten Marketing-zentrierten Datenstrom geliefert oder kann mithilfe eines der wichtigsten RDBMS (Relational Database Management Systems) einfach auf einem vorhandenen Datenstrom und Schema sitzen. Alle Daten im Datamart werden von der Adobe Campaign-Plattform über SQL-Aufrufe von Adobe Campaign zur Datenbank aufgerufen. Adobe Campaign bietet außerdem eine vollständige Ergänzung der ETL-Tools (Extract, Transform, Load – Extrahieren, Umwandeln, Laden), mittels derer Daten in das und aus dem System importiert und exportiert werden können.
