---
title: Allgemeine Architektur
description: Erfahren Sie, wie Sie Campaign Classic installieren und konfigurieren.
page-status-flag: never-activated
uuid: 686bc660-2403-4bab-a4ea-9b872adf8fa0
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: architecture-and-hosting-models
discoiquuid: 7c28c179-eb18-437e-baf2-25829566c766
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '1341'
ht-degree: 0%

---


# Allgemeine Architektur{#general-architecture}

Die typische Adobe Campaign-Lösungsbereitstellung besteht aus den folgenden Komponenten:

* **Personalisierte Client-Umgebung**

   Intuitive grafische Benutzeroberfläche, in der Benutzer Marketing-Angebot kommunizieren und verfolgen können, Kampagnen erstellen, alle Marketing-Aktivitäten, Programme und Pläne - einschließlich E-Mails, Workflows und Landingpages - überprüfen und verwalten, kundenspezifische Profil erstellen und verwalten und Audiencen definieren können.

* **Entwicklungs-Umgebung**

   Serverseitige Software, die die Marketing-Kampagnen über ausgewählte Kommunikationsserver ausführt, einschließlich E-Mails, SMS, Push-Benachrichtigungen, Direktwerbung, Web- oder Social-Kanal, basierend auf den in der Benutzeroberfläche festgelegten Regeln und Workflows.

* **Datenbank-Container**

   Basierend auf relativer Datenbanktechnologie speichert die Adobe Campaign-Datenbank alle Kundeninformationen, Kampagnen, Angebot und Workflows sowie die Kampagne in Containern der Kundendatenbank.

Adobe Campaign basiert auf einer serviceorientierten Architektur (SOA) und umfasst mehrere Funktionsmodule. Diese Module können auf einem oder mehreren Computern in einer oder mehreren Instanzen bereitgestellt werden, je nach Einschränkungen hinsichtlich Skalierbarkeit, Verfügbarkeit und Dienstisolierung. Der Umfang der Implementierungskonfigurationen ist daher sehr breit gefasst und erstreckt sich über einen einzelnen zentralen Computer bis hin zu Konfigurationen, einschließlich mehrerer dedizierter Server über mehrere Sites.

>[!NOTE]
>
>Als Softwareanbieter spezifizieren wir kompatible Hardware- und Softwareinfrastruktur. Die hier abgegebenen Hardware-Empfehlungen dienen nur zu Informationszwecken und basieren auf unserer Erfahrung. Die Adobe haftet nicht für Entscheidungen, die auf der Grundlage dieser Entscheidungen getroffen werden. Es hängt auch von Ihren Geschäftsregeln und -praktiken und der Kritikalität und den erforderlichen Leistungsniveaus des Projekts ab.

![](assets/s_ncs_install_architecture.png)

>[!CAUTION]
>
>Sofern nicht ausdrücklich anders angegeben, sind die Installation, Updates und Wartung auf allen Komponenten einer Adobe Campaign-Plattform Sache des bzw. der Computeradministratoren, der bzw. die diese hostet. Dies umfasst die Implementierung der Voraussetzungen für Adobe Campaign-Anwendungen sowie die Einhaltung der [Kompatibilitätsmatrix](https://helpx.adobe.com/de/campaign/kb/compatibility-matrix.html) zwischen Komponenten.

## Präsentationsebene {#presentation-layer}

Der Zugriff auf die Anwendung erfolgt auf unterschiedliche Weise je nach Bedarf des Benutzers: Rich Client-, Thin Client- oder API-Integration.

* **Rich-Client**: Die Hauptbenutzeroberfläche der Applikation ist ein Rich-Client, d. h. eine native Applikation (Windows), die ausschließlich mit Standard-Internetprotokollen (SOAP, HTTP usw.) mit dem Adobe Campaign-Anwendungsserver kommuniziert. Diese Konsole bietet eine großartige Benutzerfreundlichkeit für Produktivität, verwendet sehr wenig Bandbreite (über einen lokalen Cache) und ist für eine einfache Bereitstellung konzipiert. Diese Konsole kann über einen Internetbrowser bereitgestellt werden, kann automatisch aktualisiert werden und erfordert keine spezielle Netzwerkkonfiguration, da nur HTTP(S)-Traffic generiert wird.
* **Dünner Client**: Bestimmte Anwendungsbereiche können über einen einfachen Webbrowser über eine HTML-Benutzeroberfläche aufgerufen werden, einschließlich Berichte-Modul, Versand-Genehmigungsphasen, Funktionen des Dezentrale Marketing-Moduls (zentral/lokal), Instanzüberwachung usw. Dieser Modus ermöglicht es, Adobe Campaign-Funktionen in ein Intranet oder ein Extranet einzubinden.
* **Integration über die APIs**: In bestimmten Fällen kann das System über die Web-Services-APIs, die über das SOAP-Protokoll bereitgestellt werden, von einer externen Anwendung aus aufgerufen werden.

## Logische Anwendungsebene {#logical-application-layer}

Adobe Campaign ist eine Plattform mit verschiedenen Anwendungen, die zu einer offenen und skalierbaren Architektur kombiniert werden. Die Adobe Campaign-Plattform ist auf einer flexiblen Anwendungsschicht geschrieben und lässt sich einfach an die geschäftlichen Anforderungen einer Firma anpassen. Dies entspricht den wachsenden Bedürfnissen des Unternehmens sowohl aus funktionaler als auch aus technischer Sicht. Die verteilte Architektur gewährleistet eine lineare Skalierbarkeit des Systems von Tausenden von Nachrichten auf Millionen von Nachrichten.

Adobe Campaign setzt auf eine Reihe serverseitiger Prozesse, die zusammenarbeiten.

Die wichtigsten Prozesse sind:

**Anwendungsserver** (nlserver web)

Dieser Vorgang stellt die gesamte Bandbreite der Adobe Campaign-Funktionalität über Web-Services-APIs (SOAP - HTTP + XML) zur Verfügung. Darüber hinaus kann es dynamisch die Webseiten generieren, die für den HTML-basierten Zugriff verwendet werden (Berichte, Webformulare usw.). Dazu gehört ein Apache Tomcat JSP-Server. Dies ist der Prozess, mit dem die Konsole verbunden wird.

**Workflow-Engine** (nlserver wfserver)

Es führt die in der Anwendung definierten Workflow-Prozesse aus.

Außerdem werden periodisch ausgeführte Technischen Workflows verarbeitet, darunter:

* Verfolgung: Wiederherstellen und Konsolidieren von Trackinglogs. Dadurch können Sie die Protokolle vom Umleitungsserver abrufen und die vom Berichte-Modul verwendeten Aggregat-Indikatoren erstellen.
* Bereinigung: Datenbankreinigung. Dient zum Bereinigen alter Datensätze und zur Vermeidung eines exponentiellen Wachstums der Datenbank.
* Rechnungsstellung: Automatisches Senden eines Plattformberichts (Datenbankgröße, Anzahl der Marketingaktionen usw.) für die Aktivität.

**Versand-Server** (nlserver-Metadaten)

Adobe Campaign verfügt über eine native Funktion zum Senden von E-Mails. Dieser Prozess fungiert als SMTP Mail Transfer Agent (MTA). Es führt eine persönliche Personalisierung von Nachrichten durch und verarbeitet deren physischen Versand. Es funktioniert mit Versand-Aufträgen und verarbeitet automatische weitere Zustellversuche. Wenn die Verfolgung aktiviert ist, werden die URLs automatisch ersetzt, sodass sie auf den Umleitungsserver zeigen.

Dieser Prozess kann die Anpassung und automatische Versendung an einen Drittanbieter für SMS, Fax und Direktwerbung durchführen.

**Umleitungsserver** (nlserver webmdl)

Für E-Mails verarbeitet Adobe Campaign automatisch die Verfolgung von &quot;open&quot;und &quot;click&quot;(Transaktionserfassung auf Website-Ebene ist eine weitere Möglichkeit). Zu diesem Zweck werden die in den E-Mail-Nachrichten enthaltenen URLs umgeschrieben, um auf dieses Modul zu verweisen, das die Weitergabe des Internetbenutzers registriert, bevor sie an die erforderliche URL weitergeleitet werden.

Um eine maximale Verfügbarkeit zu gewährleisten, ist dieser Prozess völlig unabhängig von der Datenbank: die anderen Serverprozesse kommunizieren mit ihnen nur über SOAP-Aufrufe (HTTP, HTTP(S) und XML). Technisch gesehen ist diese Funktion in einem Erweiterungsmodul eines HTTP-Servers implementiert (ISAPI-Erweiterung in IIS, oder ein DSO Apache-Modul usw.) und ist nur unter Windows verfügbar.

Weitere technische Verfahren sind ebenfalls verfügbar:

**Verwalten von Absprung-E-Mails** (nlserver inMail)

Auf diese Weise können Sie automatisch E-Mails von Postfächern abrufen, die für den Empfang von Nachrichten mit Absprungfunktion konfiguriert sind, die bei einem Versand-Fehler zurückgegeben werden. Diese Meldungen werden dann regelbasiert verarbeitet, um die Gründe für den Nichtbesuch (unbekannter Empfänger, Überschreitung der Quote usw.) zu ermitteln. und den Datenbankstatus des Versands zu aktualisieren.

Alle diese Vorgänge sind vollautomatisch und vorkonfiguriert.

**Status** des SMS-Versands (nlserver sms)

Dieser Prozess fragt den SMS-Router ab, um den Statusstatus zu erfassen und die Datenbank zu aktualisieren.

**Schreiben von Protokollmeldungen** (nlserver-syslogd)

Dieser technische Prozess erfasst Protokollmeldungen und -spuren, die von den anderen Prozessen erzeugt wurden, und schreibt sie auf die Festplatte. Dadurch stehen im Falle von Problemen reichlich Informationen zur Diagnose zur Verfügung.

**Schreiben von Trackinglogs** (nlserver trackinglogd)

Dieser Vorgang speichert die Trackinglogs, die durch die Weiterleitung generiert wurden.

**Schreiben von Inbound-Ereignissen** (nlserver-Interaktion)

Dieser Vorgang gewährleistet die Aufzeichnung von eingehenden Ereignissen auf der Festplatte im Rahmen der Interaktion.

**Überwachungsmodule** (nlserver watchdog)

Dieser technische Prozess dient als ein primäres Verfahren, das die anderen hervorbringt. Außerdem überwacht es sie und startet sie bei Vorfällen automatisch neu, sodass maximale Systemlaufzeit erhalten bleibt.

**Statistischer Server** (nlserver stat)

Dieser Prozess unterhält Statistiken über die Anzahl der Verbindungen, die Nachrichten, die für jeden Mail-Server gesendet werden, an den Nachrichten gesendet werden, sowie deren Einschränkungen (die höchste Anzahl gleichzeitiger Verbindungen, Nachrichten pro Stunde/ und Verbindung). Sie können auch mehrere Instanzen oder Computer zusammenführen, wenn diese dieselben öffentlichen IP-Adressen haben.

>[!NOTE]
>
>Die vollständige Liste der Adobe Campaign Module ist in [diesem Dokument](../../production/using/operating-principle.md)verfügbar.

## Persistenzebene {#persistence-layer}

Die Datenbank wird als Persistenzebene verwendet und enthält fast alle von Adobe Campaign verwalteten Informationen. Dazu gehören funktionale Daten (Profile, Abonnements, Inhalte usw.), technische Daten (Versand, Aufträge und Protokolle, Trackinglogs usw.) und Arbeitsdaten (Einkäufe, Interessenten).

Die Zuverlässigkeit der Datenbank ist von größter Bedeutung, da die meisten Adobe Campaign-Komponenten Zugriff auf die Datenbank benötigen, um ihre Aufgaben ausführen zu können (mit Ausnahme des Umleitungsmoduls).

Die Plattform ist vordefiniert mit einem Marketing-zentrierten Datenstrom oder kann einfach auf einem vorhandenen Datenstrom und Schema mit einem der wichtigsten Relational Database Management Systems (RDBMS) sitzen. Alle Daten im Datenverkehr werden von der Adobe Campaign-Plattform über SQL-Aufrufe von Adobe Campaign zur Datenbank aufgerufen. Adobe Campaign bietet außerdem eine vollständige Ergänzung der Tools für das Extrahieren von Transformationen und Laden (ETL), um Daten in das und aus dem System zu importieren und zu exportieren.
