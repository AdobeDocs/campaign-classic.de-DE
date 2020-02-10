---
title: Allgemeine Architektur
seo-title: Allgemeine Architektur
description: Allgemeine Architektur
seo-description: null
page-status-flag: never-activated
uuid: 686bc660-2403-4bab-a4ea-9b872adf8fa0
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: architecture-and-hosting-models
discoiquuid: 7c28c179-eb18-437e-baf2-25829566c766
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 46f5bfb41bfe9c938ac0ffa767ead3e47a32047d

---


# Allgemeine Architektur{#general-architecture}

Die typische Bereitstellung der Adobe Campaign-Lösung besteht aus den folgenden Komponenten:

* **Personalisierte Client-Umgebung**

   Intuitive grafische Oberfläche, in der Benutzer Marketingangebote kommunizieren und verfolgen können, Kampagnen erstellen, alle Marketingaktivitäten, Programme und Pläne - einschließlich E-Mails, Workflows und Einstiegsseiten - überprüfen und verwalten, Kundenprofile erstellen und verwalten sowie Zielgruppentypen definieren können.

* **Entwicklungsumgebung**

   Serverseitige Software, die die Marketingkampagnen über ausgewählte Kommunikationskanäle ausführt, einschließlich E-Mails, SMS, Push-Benachrichtigungen, Direktwerbung, Web oder Social, basierend auf den in der Benutzeroberfläche definierten Regeln und Workflows.

* **Datenbankcontainer**

   Basierend auf relationaler Datenbanktechnologie speichert die Adobe Campaign-Datenbank alle Kundeninformationen, Kampagnenkomponenten, Angebote und Arbeitsabläufe sowie die Kampagnenergebnisse in Kundendatenbankbehältern.

Adobe Campaign basiert auf einer serviceorientierten Architektur (SOA) und umfasst mehrere Funktionsmodule. Diese Module können auf einem oder mehreren Computern in einer oder mehreren Instanzen bereitgestellt werden, je nach Einschränkungen hinsichtlich Skalierbarkeit, Verfügbarkeit und Dienstisolierung. Der Umfang der Implementierungskonfigurationen ist daher sehr breit gefasst und erstreckt sich über einen einzelnen zentralen Computer bis hin zu Konfigurationen, einschließlich mehrerer dedizierter Server über mehrere Sites.

>[!NOTE]
>
>Als Softwareanbieter spezifizieren wir kompatible Hardware- und Softwareinfrastruktur. Die hier abgegebenen Hardware-Empfehlungen dienen nur zu Informationszwecken und basieren auf unserer Erfahrung. Adobe haftet nicht für Entscheidungen, die aufgrund dieser Entscheidungen getroffen werden. Es hängt auch von Ihren Geschäftsregeln und -praktiken und der Kritikalität und den erforderlichen Leistungsniveaus des Projekts ab.

![](assets/s_ncs_install_architecture.png)

>[!CAUTION]
>
>Sofern nicht ausdrücklich anders angegeben, sind die Installation, Updates und Wartung aller Komponenten einer Adobe Campaign-Plattform Sache des bzw. der Computeradministratoren, der bzw. die diese hostet. Dies umfasst die Implementierung der Voraussetzungen für Adobe Campaign-Anwendungen sowie die Einhaltung der [Kompatibilitätsmatrix](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html) zwischen Komponenten.

## Präsentationsebene {#presentation-layer}

Der Zugriff auf die Anwendung erfolgt auf unterschiedliche Weise je nach Bedarf des Benutzers: Rich Client-, Thin Client- oder API-Integration.

* **Rich-Client**: Die Hauptbenutzeroberfläche der Anwendung ist ein Rich-Client, d. h. eine native Anwendung (Windows), die ausschließlich mit Standard-Internetprotokollen (SOAP, HTTP usw.) mit dem Adobe Campaign-Anwendungsserver kommuniziert. Diese Konsole bietet eine großartige Benutzerfreundlichkeit für Produktivität, verwendet sehr wenig Bandbreite (über einen lokalen Cache) und ist für eine einfache Bereitstellung konzipiert. Diese Konsole kann über einen Internetbrowser bereitgestellt werden, kann automatisch aktualisiert werden und erfordert keine spezielle Netzwerkkonfiguration, da nur HTTP(S)-Traffic generiert wird.
* **Dünner Client**: Bestimmte Teile der Anwendung können über einen einfachen Webbrowser über eine HTML-Benutzeroberfläche aufgerufen werden, einschließlich des Berichtsmoduls, der Genehmigungsphasen für die Bereitstellung, der Funktionen des Moduls für verteiltes Marketing (zentral/lokal), der Instanzüberwachung usw. Dieser Modus ermöglicht die Integration von Adobe Campaign-Funktionen in ein Intranet oder Extranet.
* **Integration über die APIs**: In bestimmten Fällen kann das System über die Web-Services-APIs, die über das SOAP-Protokoll bereitgestellt werden, von einer externen Anwendung aus aufgerufen werden.

## Logische Anwendungsebene {#logical-application-layer}

Adobe Campaign ist eine einzelne Plattform mit verschiedenen Anwendungen, die kombiniert werden, um eine offene und skalierbare Architektur zu erstellen. Die Adobe Campaign-Plattform ist auf einer flexiblen Anwendungsebene konzipiert und lässt sich einfach an die geschäftlichen Anforderungen eines Unternehmens anpassen. Dies entspricht den wachsenden Bedürfnissen des Unternehmens sowohl aus funktionaler als auch aus technischer Sicht. Die verteilte Architektur gewährleistet eine lineare Skalierbarkeit des Systems von Tausenden von Nachrichten auf Millionen von Nachrichten.

Adobe Campaign basiert auf einer Reihe serverseitiger Prozesse, die zusammenarbeiten.

Die wichtigsten Prozesse sind:

**Anwendungsserver** (nlserver web)

Dieser Prozess stellt die gesamte Bandbreite der Adobe Campaign-Funktionen über Web-Services-APIs (SOAP - HTTP + XML) zur Verfügung. Darüber hinaus kann es dynamisch die Webseiten generieren, die für den HTML-basierten Zugriff verwendet werden (Berichte, Webformulare usw.). Dazu gehört ein Apache Tomcat JSP-Server. Dies ist der Prozess, mit dem die Konsole verbunden wird.

**Workflow-Engine** (nlserver wfserver)

Es führt die in der Anwendung definierten Workflow-Prozesse aus.

Außerdem werden regelmäßig ausgeführte technische Arbeitsabläufe verarbeitet, darunter:

* Verfolgung: Wiederherstellen und Konsolidieren von Verfolgungsprotokollen. Dadurch können Sie die Protokolle vom Umleitungsserver abrufen und die vom Berichtsmodul verwendeten aggregierten Indikatoren erstellen.
* Bereinigung: Datenbankreinigung. Dient zum Bereinigen alter Datensätze und zur Vermeidung eines exponentiellen Wachstums der Datenbank.
* Rechnungsstellung: Automatisches Senden eines Aktivitätsberichts für die Plattform (Datenbankgröße, Anzahl der Marketingaktionen usw.)

**Bereitstellungsserver** (nlserver-Metadaten)

Adobe Campaign verfügt über eine native Funktion zum Senden von E-Mails. Dieser Prozess fungiert als SMTP Mail Transfer Agent (MTA). Es führt eine persönliche Personalisierung von Nachrichten durch und verarbeitet deren physische Auslieferung. Es funktioniert mit Bereitstellungsaufträgen und verarbeitet automatische Wiederholungen. Wenn die Verfolgung aktiviert ist, werden die URLs automatisch ersetzt, sodass sie auf den Umleitungsserver zeigen.

Dieser Prozess kann die Anpassung und automatische Versendung an einen Drittanbieter für SMS, Fax und Direktwerbung durchführen.

**Umleitungsserver** (nlserver webmdl)

Für E-Mail verarbeitet Adobe Campaign automatisch die Verfolgung von Öffnen und Klick (eine weitere Möglichkeit ist die Transaktionsverfolgung auf Website-Ebene). Zu diesem Zweck werden die in den E-Mail-Nachrichten enthaltenen URLs umgeschrieben, um auf dieses Modul zu verweisen, das die Weitergabe des Internetbenutzers registriert, bevor sie an die erforderliche URL weitergeleitet werden.

Um eine maximale Verfügbarkeit zu gewährleisten, ist dieser Prozess völlig unabhängig von der Datenbank: die anderen Serverprozesse kommunizieren mit ihnen nur über SOAP-Aufrufe (HTTP, HTTP(S) und XML). Technisch gesehen ist diese Funktion in einem Erweiterungsmodul eines HTTP-Servers implementiert (ISAPI-Erweiterung in IIS, oder ein DSO Apache-Modul usw.) und ist nur unter Windows verfügbar.

Weitere technische Verfahren sind ebenfalls verfügbar:

**Verwalten von Absprung-E-Mails** (nlserver inMail)

Durch diesen Prozess können Sie automatisch E-Mails von Postfächern abrufen, die für den Empfang von Nachrichten mit Absprungfunktion konfiguriert sind, die bei einem Lieferfehler zurückgegeben werden. Diese Meldungen werden dann regelbasiert verarbeitet, um die Gründe für die Nichtauslieferung (unbekannter Empfänger, Überschreitung der Quote usw.) zu ermitteln. und den Bereitstellungsstatus in der Datenbank zu aktualisieren.

Alle diese Vorgänge sind vollautomatisch und vorkonfiguriert.

**Status** der SMS-Zustellung (nlserver sms)

Dieser Prozess fragt den SMS-Router ab, um den Statusstatus zu erfassen und die Datenbank zu aktualisieren.

**Schreiben von Protokollmeldungen** (nlserver-syslogd)

Dieser technische Prozess erfasst Protokollmeldungen und -spuren, die von den anderen Prozessen erzeugt wurden, und schreibt sie auf die Festplatte. Dadurch werden bei Problemen reichlich Informationen zur Diagnose bereitgestellt.

**Schreiben von Verfolgungsprotokollen** (nlserver trackinglogd)

Dieser Prozess speichert die Verfolgungsprotokolle, die durch die Weiterleitung generiert wurden.

**Schreiben von Inbound-Ereignissen** (nlserver-Interaktion)

Dieser Prozess gewährleistet die Aufzeichnung von eingehenden Ereignissen im Rahmen der Interaktion auf der Festplatte.

**Überwachungsmodule** (nlserver watchdog)

Dieser technische Prozess fungiert als Master-Prozess, der die anderen hervorbringt. Außerdem überwacht es sie und startet sie bei Vorfällen automatisch neu, sodass maximale Systemlaufzeit erhalten bleibt.

**Statistischer Server** (nlserver stat)

Dieser Prozess unterhält Statistiken über die Anzahl der Verbindungen, die Nachrichten, die für jeden Mail-Server gesendet werden, an den Nachrichten gesendet werden, sowie deren Einschränkungen (höchste Anzahl gleichzeitiger Verbindungen, Nachrichten pro Stunde/ und Verbindung). Sie können auch mehrere Instanzen oder Computer zusammenführen, wenn diese dieselben öffentlichen IP-Adressen haben.

>[!NOTE]
>
>Die vollständige Liste der Adobe Campaign-Module ist in [diesem Dokument](../../production/using/operating-principle.md)verfügbar.

## Persistenzebene {#persistence-layer}

Die Datenbank wird als Persistenzebene verwendet und enthält fast alle von Adobe Campaign verwalteten Informationen. Dazu gehören funktionale Daten (Profile, Abonnements, Inhalte usw.), technische Daten (Lieferaufträge und Protokolle, Verfolgungsprotokolle usw.) und Arbeitsdaten (Einkäufe, Interessenten).

Die Zuverlässigkeit der Datenbank ist von größter Bedeutung, da die meisten Adobe Campaign-Komponenten zum Ausführen ihrer Aufgaben Zugriff auf die Datenbank benötigen (mit Ausnahme des Umleitungsmoduls).

Die Plattform ist vordefiniert mit einem Marketing-zentrierten Datenstrom oder kann einfach auf einem vorhandenen Datendiagramm und Schema mit einem der wichtigsten Relational Database Management Systems (RDBMS) sitzen. Auf alle Daten im Datendiagramm kann die Adobe Campaign-Plattform über SQL-Aufrufe von Adobe Campaign zur Datenbank zugreifen. Adobe Campaign bietet außerdem eine vollständige Ergänzung der Tools für die Transformation und das Laden von Daten, um Daten in das System zu importieren und zu exportieren.
