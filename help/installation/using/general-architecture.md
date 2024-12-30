---
product: campaign
title: Allgemeine Campaign Classic-Architektur
description: Erfahren Sie, wie Sie Campaign Classic installieren und konfigurieren
feature: Installation, Architecture
audience: installation
content-type: reference
topic-tags: architecture-and-hosting-models
exl-id: 04e6dc17-427b-4745-84cc-bf45c03dbf81
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '1342'
ht-degree: 46%

---

# Allgemeine Architektur{#general-architecture}



Die typische Bereitstellung einer Adobe Campaign-Lösung setzt sich aus folgenden Komponenten zusammen:

* **Personalisierte Client-Umgebung**

  Intuitive grafische Benutzeroberfläche, über die Benutzer Marketing-Angebote kommunizieren und verfolgen, Kampagnen erstellen, alle Marketing-Aktivitäten, -Programme und -Pläne (einschließlich E-Mails, Workflows und Landingpages) überprüfen und verwalten, Kundenprofile erstellen und verwalten und Zielgruppentypen definieren können.

* **Entwicklungsumgebung**

  Eine Server-seitige Software, die Marketing-Kampagnen über benutzerseitig ausgewählte Kommunikationskanäle ausführt, die von E-Mail, SMS und Push-Benachrichtigungen über Briefpost bis zu Web- und Social-Media-Kanälen reichen. In der Benutzeroberfläche werden dabei zugehörige Regeln und Workflows festgelegt.

* **Datenbank-Container**

  Basierend auf relationaler Datenbanktechnologie speichert die Adobe Campaign-Datenbank alle Kundeninformationen, Kampagnenkomponenten, Angebote und Workflows sowie die Kampagnenergebnisse in Containern der Kundendatenbank.

Adobe Campaign basiert auf einer Service-orientierten Architektur (SOA) und umfasst mehrere Funktionsmodule. Diese Module können auf einem oder mehreren Computern in einzelnen oder mehreren Instanzen bereitgestellt werden, je nach Einschränkungen in Bezug auf Skalierbarkeit, Verfügbarkeit und Service-Isolierung. Der Umfang der Bereitstellungskonfigurationen ist daher sehr breit gefächert und erstreckt sich von einem einzelnen, zentralen Computer bis hin zu Konfigurationen mit mehreren dedizierten Servern über mehrere Standorte.

>[!NOTE]
>
>Als Software-Anbieter spezifizieren wir kompatible Hardware- und Software-Infrastruktur. Die hier angegebenen Hardware-Empfehlungen dienen nur zu Informationszwecken und basieren auf unseren Erfahrungen. Adobe haftet nicht für Entscheidungen, die auf dieser Grundlage getroffen werden. Dies hängt auch von Ihren Geschäftsregeln und -praktiken sowie der Wichtigkeit und den erforderlichen Leistungsstufen des Projekts ab.

![](assets/s_ncs_install_architecture.png)

>[!CAUTION]
>
>Sofern nicht ausdrücklich anders angegeben, sind die Installation, Updates und Wartung für alle Komponenten einer Adobe Campaign-Plattform in der Verantwortung der Computeradministratoren, die die Komponenten hosten. Dazu gehört die Implementierung der Voraussetzungen für Adobe Campaign-Anwendungen sowie die Einhaltung der Campaign-[Kompatibilitätsmatrix](../../rn/using/compatibility-matrix.md) zwischen Komponenten.

## Präsentationsebene {#presentation-layer}

Der Zugriff auf das Programm erfolgt je nach Bedarf der Benutzer auf unterschiedliche Weise: Rich-Client-, Thin-Client- oder API-Integration.

* **Rich-Client**: Die Hauptbenutzeroberfläche des Programms ist ein Rich-Client, d. h. ein natives Programm (Windows), das ausschließlich über Standard-Internet-Protokolle (SOAP, HTTP usw.) mit dem Adobe Campaign-Anwendungs-Server kommuniziert. Diese Konsole bietet hohe Benutzerfreundlichkeit für Produktivität, verbraucht sehr wenig Bandbreite (durch die Verwendung eines lokalen Cache) und wurde für eine einfache Bereitstellung entwickelt. Diese Konsole kann über einen Internet-Browser bereitgestellt werden, kann automatisch aktualisiert werden und erfordert keine spezielle Netzwerkkonfiguration, da sie nur HTTP(S)-Traffic erzeugt.
* **Thin Client**: Einige Bereiche des Programms können über einen einfachen Webbrowser mittels HTML-Benutzeroberfläche aufgerufen werden, darunter etwa das Reporting-Modul, die einzelnen Phasen der Versandvalidierung oder auch Funktionen des Moduls für dezentrales Marketing (zentral/lokal) bzw. das Instanz-Monitoring. Dieser Modus ermöglicht es, Adobe Campaign-Funktionen in ein Intranet oder ein Extranet einzubinden.
* **Integration über die APIs**: In bestimmten Fällen kann das System über die via SOAP-Protokoll bereitgestellten Web Services-APIs von einem externen Programm aus aufgerufen werden.

## Logische Anwendungsebene {#logical-application-layer}

Adobe Campaign führt verschiedene Programme in einer zentralen Plattform zusammen und schafft so eine offenen und zugleich skalierbare Architektur. Die Adobe Campaign-Plattform basiert auf einer flexiblen Anwendungsebene und kann einfach konfiguriert werden, um die Geschäftsanforderungen eines Unternehmens zu erfüllen. Damit wird den wachsenden Anforderungen des Unternehmens sowohl aus funktionaler als auch aus technischer Sicht Rechnung getragen. Dank der verteilten Architektur ist das System linear von mehreren Tausend auf mehrere Millionen Nachrichten skalierbar.

Adobe Campaign beruht auf einer Reihe von Server-seitigen Prozessen, die zusammenarbeiten.

Dies sind die wichtigsten Prozesse:

**Anwendungs-Server** (nlserver web)

Dieser Prozess stellt das gesamte Spektrum an Adobe Campaign-Funktionen mittels Web-Services-APIs (SOAP - HTTP + XML) zur Verfügung. Darüber hinaus kann er dynamisch die Web-Seiten generieren, die für den HTML-basierten Zugriff verwendet werden (Berichte, Web-Formulare usw.). Um dies zu ermöglichen, umfasst der Prozess einen Apache Tomcat JSP-Server. Dies ist der Prozess, mit dem sich die Konsole verbindet.

**Workflow-Engine** (nlserver wfserver)

Diese führt die im Programm definierten Workflow-Prozesse aus.

Außerdem verarbeitet sie zeitweise ausgeführte technische Workflows, darunter:

* Tracking: Wiederherstellen und Konsolidieren von Trackinglogs. Dadurch können Protokolle vom Weiterleitungs-Server abgerufen und die vom Reporting-Modul verwendeten aggregierten Indikatoren erstellt werden.
* Bereinigung: zur Bereinigung von Datenbanken. Dabei wird die Datenbank von alten Datensätzen bereinigt, um zu vermeiden, dass sie übermäßig wächst.
* Abrechnung : Automatisches Senden eines Berichts zu Aktivitäten auf der Plattform (Datenbankgröße, Anzahl der Marketing-Aktionen, Anzahl der aktiven Profile usw.)

**Versand-Server** (nlserver mta)

Adobe Campaign umfasst eine native Funktion zum Senden von E-Mails. Dieser Prozess fungiert als SMTP Mail Transfer Agent (MTA). Er personalisiert Nachrichten individuell für den jeweiligen Empfänger und verarbeitet deren physischen Versand. Dies erfolgt mittels Versandvorgängen, wobei zudem auch nachgelagerte, weitere Zustellversuche automatisiert werden. Ist zusätzlich noch Tracking aktiviert, werden die URLs automatisch ersetzt, sodass sie auf den Weiterleitungs-Server verweisen.

Über diesen Prozess ist die Anpassung sowie der automatische Versand an einen Dritt-Router für SMS, Fax und Briefpost möglich.

**Weiterleitungs-Server** (nlserver webmdl)

Bei E-Mails übernimmt Adobe Campaign automatisch das Öffnungs- und Klick-Tracking (wobei das Tracking von Transaktionen auf Website-Ebene ebenfalls möglich ist). Hierfür werden die in den E-Mail-Nachrichten enthaltenen URLs so umgeschrieben, dass sie auf dieses Modul verweisen. Dieses wiederum registriert Internet-Benutzer, während diese an die Ziel-URL weitergeleitet werden.

Zur Sicherstellung maximaler Verfügbarkeit ist dieser Prozess vollkommen unabhängig von der Datenbank: Die anderen Server-Prozesse kommunizieren mit ihm nur über SOAP-Aufrufe (HTTP, HTTPS und XML). Aus technischer Sicht ist diese Funktion in einem Erweiterungsmodul (ISAPI-Erweiterung in IIS, DSO Apache-Modul usw.) eines HTTP-Servers implementiert und nur unter Windows verfügbar.

Daneben sind auch noch weitere technische Prozesse verfügbar:

**Handhabung von Bounce-E-Mails** (nlserver inMail)

Dieser Prozess ermöglicht den automatischen Abruf von E-Mails aus Postfächern, die für den Empfang von Nachrichten konfiguriert sind, die bei fehlgeschlagenem Versand als unzustellbar zurückgesendet werden. Diese Nachrichten werden dann regelbasiert verarbeitet, um die Gründe für die Unzustellbarkeit (z. B. Empfänger unbekannt, Nachrichtenkontingente ausgeschöpft) zu ermitteln und den Versandstatus in der Datenbank zu aktualisieren.

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
>Die vollständige Liste der Adobe Campaign-Module finden Sie in [diesem Dokument](../../production/using/operating-principle.md).

## Persistenzebene {#persistence-layer}

Die Datenbank wird als Persistenzschicht verwendet und enthält fast alle von Adobe Campaign verwalteten Informationen. Dazu gehören sowohl funktionale Daten (Profile, Abonnements, Inhalte usw.), technische Daten (Versandvorgänge und -protokolle, Trackinglogs usw.) als auch Arbeitsdaten (Käufe, Leads).

Die Zuverlässigkeit der Datenbank ist von größter Bedeutung, da die meisten Adobe Campaign-Komponenten Zugriff auf die Datenbank benötigen, um ihre Aufgaben ausführen zu können (mit Ausnahme des Weiterleitungsmoduls).

Die Plattform verfügt über einen vordefinierten Marketing-zentrierten Datamart oder kann mithilfe eines der wichtigsten relationalen Datenbankmanagementsysteme (RDBMS) einfach auf einem vorhandenen Datamart und Schema platziert werden. Auf alle Daten im Datamart wird von der Adobe Campaign-Plattform über SQL-Aufrufe von Adobe Campaign an die Datenbank zugegriffen. Adobe Campaign bietet außerdem ein vollständiges Komplement der ETL-Tools (Extract, Transform, Load – Extrahieren, Umwandeln, Laden), mittels dessen Daten in das und aus dem System importiert und exportiert werden können.
