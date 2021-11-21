---
product: campaign
title: Empfehlungen zur Hardware-Größe für Campaign Classic v7
description: Empfehlungen zur Hardware-Größe für Campaign Classic v7
exl-id: c47e73a0-dbd8-43f5-a363-7e6783dc7685
source-git-commit: ee296e0ce25570d1fe62238e505f978df17c1f24
workflow-type: tm+mt
source-wordcount: '2512'
ht-degree: 1%

---

# Empfehlungen zur Hardware-Dimensionierung{#hardware-sizing-reco}

![](../../assets/v7-only.svg)

## Überblick

>[!CAUTION]
>
>Dieser Artikel wird nur als allgemeine Beispielanleitung bereitgestellt. Sie müssen sich an Ihren Adobe Campaign Customer Success Manager wenden, um die genaue Größe Ihrer Bereitstellung zu messen, bevor Sie mit Ihrem Campaign-Projekt beginnen. **Nicht** -Infrastruktur oder -Hardware zu erwerben oder bereitzustellen, bis dies geschehen ist.

Dieses Dokument enthält allgemeine Empfehlungen für die Bereitstellung von Adobe Campaign Classic v7 in Ihrem On-Premise-Rechenzentrum oder Ihrer virtualisierten Cloud-Umgebung. Diese Art von Einsatz, bezeichnet als **hybrid** oder **Mid-Sourcing** platziert die Marketing-Instanz von Campaign und die Marketing-Datenbank unter Ihrer betrieblichen Kontrolle, während Adobe Cloud Messaging-Dienste zum Senden von E-Mails, SMS oder SMPP-Nachrichten sowie zum Erfassen von E-Mail-Öffnungs-, Bounce- und Klick-Tracking-Daten verwendet werden.

Die Marketing-Instanz ist der Teil der Adobe Campaign-Architektur, der alle Marketing-Aktivitäten steuert und alle von Kampagnen zurückgegebenen Empfängerdaten und Analysedaten speichert. Die Marketing-Instanz besteht aus einer Reihe von On-Premise-Servern, auf denen Adobe Campaign-Dienste ausgeführt werden, und einer relationalen Datenbank.

>[!CAUTION]
>
>Die Informationen in diesem Dokument gelten nicht, wenn Sie eine vollständig gehostete Adobe Campaign-Instanz verwenden (die in Adobe Cloud Services bereitgestellt wird).

Die Softwarekompatibilität wird im Abschnitt [Kompatibilitätsmatrix](../../rn/using/compatibility-matrix.md).


### Szenarien

Bereitstellungsdiagramme und Empfehlungen zur Hardwaredimensionierung werden für drei repräsentative Szenarien bereitgestellt:

1. [Moderate Größe](#scenario-1) - 5 Millionen aktive Empfänger im System
1. [Groß-Größe](#scenario-2) - 20 Millionen aktive Empfänger im System
1. [Unternehmen](#scenario-3) - 50 Millionen aktive Empfänger mit Transaktionsnachrichten

### Annahmen

In diesem Dokument werden außerdem die folgenden Nutzungsarten für alle drei Szenarien angenommen:

* Große E-Mail-Kampagnen werden zweimal wöchentlich an ca. 50 % der aktiven Empfänger gesendet
* Briefpost wird einmal pro Monat für jeden Empfänger im System generiert
* SMS-Nachrichten werden monatlich an etwa 10 % der aktiven Empfänger gesendet
* Das Datenbankschema, das jeden Empfänger definiert, wurde um eine zusätzliche Tabelle erweitert, die für jeden Empfänger etwa 200 Byte an Daten enthält
* Das Adobe Campaign Interaction-Modul wird verwendet, um ausgehenden E-Mails Angebote hinzuzufügen.
* E-Mail-Tracking-Daten werden im Campaign-System 90 Tage lang aufbewahrt

## Allgemeine Richtlinien

Campaign ist eine datenbankorientierte Anwendung, und die Leistung des Datenbankservers ist entscheidend. Die Ausführung von Workflows, die Segmentierung, das Hochladen von Tracking-Daten, eingehende Interaktionen, Analysen und andere Aktivitäten generieren Datenbankaktivitäten. Im Allgemeinen bestimmen Größe und Häufigkeit dieser Vorgänge die Größe Ihrer Datenbankserver.

Die Anwendungsserver in Ihrer Marketing-Instanz benötigen genügend CPU und Arbeitsspeicher, um Workflows auszuführen und auf SOAP-API-Aufrufe zu reagieren, einschließlich Anforderungen von Campaign Console-Benutzern. Die CPU-Anforderungen können für Workflows von Bedeutung sein, die ausgehende Interaktionen mit komplexen Angebotsregeln, Workflows, die benutzerdefinierten JavaScript ausführen, und Webanwendungen mit hohem Traffic-Niveau verwenden.

Campaign-Webanwendungen können auch auf den App-Servern der Marketinginstanz oder auf separaten Webserversystemen bereitgestellt werden. Da Webanwendungsarbeitslasten mit kritischen Workflows und Benutzern der Campaign Console in Konflikt stehen, können Webanwendungen und eingehende Interaktionen auf separaten Servern bereitgestellt werden, um sicherzustellen, dass die Kernfunktionen von Campaign zuverlässig und leistungsstark ausgeführt werden.

Aus Gründen der Sicherheit und Verfügbarkeit empfiehlt Adobe, den Internetverkehr von dem von den Geschäftsbenutzern generierten Datenverkehr zu trennen. Aus diesem Grund enthalten die Diagramme zwei Gruppen von Servern: den Webserver (Internet-Zugriff auf Web1 und Web2) und die App-Server (Geschäftsprozesse App1 und App2).

Es ist eine gesetzliche Voraussetzung für kommerzielle E-Mail-Absender, über eine funktionale Opt-out-Webseite zu verfügen. Adobe empfiehlt, für Ausfallszenarien redundante Computer in jedem Gruppenserver zu verwenden. Dies gilt insbesondere, wenn Adobe Campaign die Opt-out-Seiten hostet.

### Reverse-Proxys

Die Campaign-Architektur erzwingt hohe Sicherheit durch die Verwendung von SSL über HTTP (HTTPS) für die Kommunikation zwischen Ihrer Marketing-Instanz und Adobe Cloud Messaging. Sicherheit, Zuverlässigkeit und Verfügbarkeit werden erzwungen, indem Reverse-Proxys in einem DMZ-Subnetz (demilitarisierte Zone) verwendet werden, um die Server und die Datenbank der Marketinginstanz zu isolieren und zu schützen.

### Lastenausgleich

Der Lastenausgleich für die App-Server wird in einer aktiven/passiven Konfiguration eingerichtet, wobei HTTPS am Proxy beendet wird. Der Lastenausgleich für die Webserver wird in einer aktiven/aktiven Konfiguration eingerichtet, wobei HTTPS am Proxy beendet wird.

Adobe bietet eine exklusive Liste von URL-Pfaden, die in Ihrer Bereitstellungsumgebung an den Adobe Campaign-Server weitergeleitet werden können.

### Architektur

Die allgemeine Architektur ist unabhängig von den Volumina fast identisch. Die Sicherheits- und Hochverfügbarkeitsanforderungen erfordern mindestens vier Server. zwei Server, wenn keine WebApps verwendet werden. Der Unterschied in der Konfiguration variiert hauptsächlich in der Hardwarekonfiguration wie CPU-Kern und Speicher.

## Szenario 1: Moderate Bereitstellung{#scenario-1}

![](assets/scenario-1.png)

Geschätztes Volumen:

| Kanal | Anzahl |
| ----------------------- | ----------------- |
| Aktive Empfänger | 5 Millionen |
| E-Mail | 4,2 Millionen/Monat |
| Briefpost | 1 Million/Monat |
| Mobile SMS | 100.000/Monat |
| Tägliche maximale E-Mail-Menge | 500 |

Für diese Volumes bietet eine Kombination aus Adobe Campaign-Anwendungsserversystemen alle Funktionen für Adobe Campaign-Client-Benutzer und die Ausführung von Workflows. Bei 5 Millionen aktiven Empfängern und diesem E-Mail-Volumen sind die Workloads des Anwendungsservers nicht CPU- oder I/O-intensiv. Der größte Stress liegt in der Datenbank.

Die Adobe Campaign-Webserver werden in der Sicherheitszone angezeigt.

### Web- und Anwendungsserver

In diesem Szenario wird empfohlen, Adobe Campaign auf vier Computern mit der folgenden Spezifikation zu installieren:

**3-GHz+-Quad-Core-CPU, 8-GB RAM, RAID 1 oder 10, 2 x 80-GB SSD**

Diese Systeme erstellen die Marketinginstanz Application Server, der Ihre Campaign Console-Benutzer direkt unterstützt und die Kampagnen-Workflows ausführt.

Reverse-Proxys in einer DMZ-Lastenausgleichsfunktion des Traffics auf die Adobe Campaign-Webserver. Es ist nicht erforderlich, den Adobe Campaign-Software-Stack auf Proxy-Computern zu installieren. jede Reverse-Proxy-Software oder Netzwerkausrüstung verwendet werden kann.

Opt-in/Opt-out-Funktion für Abonnements und Funktionen von Präferenzzentren können von Campaign oder Ihrer eigenen Website bereitgestellt werden. Wenn Sie diese Funktion auf Ihrer Website implementieren möchten, müssen Sie sicherstellen, dass die Voreinstellungs- und Abonnementinformationen an die Marketing-Datenbank von Campaign weitergeleitet werden. Dies geschieht normalerweise durch die automatische Erstellung von Extraktionsdateien, die von Campaign-Workflows hochgeladen werden.

Der Speicherplatzverbrauch auf Anwendungsservern hängt von der Aufbewahrungsfrist von Dateien ab, die mit Drittanbietern ausgetauscht werden (z. B. Druckanbieter für Briefpost), sowie von der Größe und Aufbewahrung importierter Flat Files, wie z. B. Anmelde- oder Vorlieben-Updates von Ihrer Website, oder von Auszügen aus Ihren eigenen CRM- oder Marketingsystemen.

### Datenbank

Die Hardware-Empfehlungen für den Datenbankserver lauten wie folgt:

**3-GHz+-4-Core-CPU, 16-GB-RAM, RAID 1 oder 10, 128-GB-SSD-Minimum**

Die Speicherschätzung geht von einer vollständigen Zwischenspeicherung von etwa 500.000 Empfängern für einen großen Kampagnenstart sowie von RDBMS-Pufferspeicher für die Ausführung von Workflows, den Import von Tracking-Daten und anderen gleichzeitigen Aktivitäten aus.

Es wird geschätzt, dass der Speicherplatz, der für die Datenbank benötigt wird, um alle technischen Daten von Adobe Campaign (Kampagnen, Tracking, Arbeitstabellen usw.) zu speichern, basierend auf einer Aufbewahrungsfrist von drei Monaten etwa 35 GB beträgt. Wenn Sie Tracking-Daten für 6 Monate aufbewahren, erhöht sich die Datenbankgröße auf etwa 40 GB und die 12-monatige Aufbewahrung erhöht die Datenbankgröße auf etwa 45 GB. Die Empfängerdaten verbrauchen für diese Umgebung etwa 5 GB.

>[!CAUTION]
>
>Diese Schätzung enthält keine zusätzlichen Kundendaten. Wenn Sie zusätzliche Spalten oder Tabellen mit Kundendaten in die Adobe Campaign-Datenbank replizieren möchten, müssen Sie den zusätzlichen Speicherplatzbedarf abschätzen. Hochgeladene Segmente/Listen erfordern außerdem je nach Größe, Häufigkeit und Aufbewahrungszeitraum mehr Speicher.

Beachten Sie außerdem, dass aufgrund des täglichen Informationsvolumens die IOPS des Datenbankservers wichtig sind. An einem Spitzentag können Sie beispielsweise Kampagnen bereitstellen, die auf insgesamt 500.000 Empfänger ausgerichtet sind. Zur Ausführung jeder Kampagne fügt Adobe Campaign 500.000 Datensätze in eine Tabelle mit rund 12 Millionen Datensätzen ein (die Versandlog-Tabelle). Um während der Kampagnenbereitstellung eine annehmbare Leistung zu erzielen, empfiehlt Adobe für dieses Szenario mindestens 60.000 zufällige Lese-/Schreib-IOPS mit 4 KB.


## Szenario 2: Große Implementierung{#scenario-2}

![](assets/scenario-2.png)

Geschätztes Volumen:

| Kanal | Anzahl |
| ----------------------- | ----------------- |
| Aktive Empfänger | 20 Millionen |
| E-Mail | 42 Millionen/Monat |
| Briefpost | 10 Millionen/Monat |
| Mobile SMS | 1.000.000/Monat |
| Tägliche maximale E-Mail-Menge | 5.000.000 |

### Web- und Anwendungsserver

In diesem Szenario empfiehlt Adobe die Installation von Adobe Campaign auf vier Computern, zwei Anwendungsservern und zwei Webservern mit der folgenden Spezifikation:

**3-GHz+-Quad-Core-CPU, 8-GB-RAM, RAID 1 oder 10, 80-GB-SSD**

Die Anwendungsserver unterstützen die Benutzer der Campaign Console sowie die Ausführung von Kampagnen-Workflows direkt. Diese Funktion wird auf zwei identischen Servern für hohe Verfügbarkeit bereitgestellt, wobei ein NAS-Dateisystem (Network-Attached Storage) gemeinsam genutzt wird, um Failover zu ermöglichen.

Die Webserver hosten Webanwendungen von Campaign, die die 10 Millionen aktiven Empfänger im System unterstützen.

Siehe [Szenario 1: Moderate Bereitstellung](#scenario-1) für weitere Kommentare zu Proxys, Präferenzzentren/Abonnement-Handhabung und Festplattenspeicherplatznutzung.

### Datenbank

Die Hardware-Empfehlungen für den Datenbankserver lauten wie folgt:

**3-GHz+-8-Core-CPU, 64-GB RAM, RAID 1 oder 10, 2 x 320-GB SSD oder RAID 10, 640-GB SSD-Minimum**

Die Speicherschätzung geht von einer vollständigen Zwischenspeicherung von etwa 5.000.000 Empfängern für einen großen Kampagnenstart sowie von RDBMS-Pufferspeicher für die Ausführung von Workflows, den Import von Tracking-Daten und anderen gleichzeitigen Aktivitäten aus.

Es wird geschätzt, dass der Speicherplatz, der für die Datenbank benötigt wird, um alle technischen Daten von Adobe Campaign (Kampagnen, Tracking, Arbeitstabellen usw.) zu speichern, basierend auf einer Aufbewahrungsfrist von 3 Monaten etwa 280 GB beträgt. Wenn Sie Tracking-Daten für 6 Monate aufbewahren, erhöht sich die Datenbankgröße auf etwa 450 GB und die 12-monatige Aufbewahrung erhöht die Datenbankgröße auf etwa 900 GB. Die Empfängerdaten verbrauchen für diese Umgebung etwa 15 GB.

## Szenario 3: Unternehmensbereitstellung mit Message Center{#scenario-3}

![](assets/scenario-3.png)

Geschätztes Volumen:

| Kanal | Anzahl |
| ----------------------- | ----------------- |
| Aktive Empfänger | 50 Millionen |
| E-Mail | 108 Millionen/Monat |
| Briefpost | 25 Millionen/Monat |
| Mobile SMS | 2,5 Millionen/Monat |
| Transaktionsnachrichten | 2,5 Millionen/Monat |
| Tägliche maximale E-Mail-Menge | 2,5 Millionen |


Die Bereitstellung, die 50 Millionen Empfänger unterstützt, entspricht im Wesentlichen der in [Szenario 2](#scenario-2): Der Traffic der Campaign-Webanwendung wird an die Campaign-Webserver weitergeleitet, sodass der Web-Traffic nach großen Kampagnenstarts keine Auswirkungen auf Campaign-Workflows und Client Console-Benutzer hat.

Diese Implementierung umfasst auch Message Center-Aufrufe, die von Ihren eigenen Websites und Anwendungen aus gesteuert werden.


### Web- und Anwendungsserver

In diesem Szenario empfiehlt Adobe, Adobe Campaign wie folgt auf vier Computern zu installieren:

* Anwendungsserver
   **Zwei Systeme, 3-GHz+-Quad-Core-CPU, 8-GB RAM, RAID 1 oder 10, 80-GB SSD**

* Webserver
   **Zwei Systeme, 3-GHz+-Quad-Core-CPU, 16-GB-RAM, RAID 1 oder 10, 80-GB-SSD**


Die Anwendungsserver unterstützen die Benutzer der Campaign Console sowie die Ausführung von Kampagnen-Workflows direkt. Diese Funktion wird auf zwei identischen Servern für hohe Verfügbarkeit bereitgestellt, wobei ein NAS-Dateisystem (Network-Attached Storage) gemeinsam genutzt wird, um Failover zu ermöglichen.

Die Webserver hosten Webanwendungen von Campaign, die die 10 Millionen aktiven Empfänger im System unterstützen.

Siehe [Szenario 1: Moderate Bereitstellung](#scenario-1) für weitere Kommentare zu Proxys, Präferenzzentren/Abonnement-Handhabung und Festplattenspeicherplatznutzung.

### Datenbank

Die Hardware-Empfehlungen für den Datenbankserver lauten wie folgt:

**3-GHz+-8-Core-CPU, 96-GB RAM, RAID 1 oder 10, 1,5-TB SSD-Minimum**

Die Speicherschätzung geht von einer vollständigen Zwischenspeicherung von etwa 12.500.000 Empfängern für einen großen Kampagnenstart sowie von RDBMS-Pufferspeicher für die Ausführung von Workflows, den Import von Tracking-Daten und anderen gleichzeitigen Aktivitäten aus.

Es wird geschätzt, dass der Speicherplatz, der für die Datenbank benötigt wird, um alle technischen Daten von Adobe Campaign (Kampagnen, Tracking, Arbeitstabellen usw.) zu speichern, basierend auf einer Aufbewahrungsfrist von 3 Monaten etwa 700 GB beträgt. Wenn Sie Tracking-Daten für 6 Monate aufbewahren, erhöht sich die Datenbankgröße auf etwa 1,2 TB und die 12-monatige Aufbewahrung erhöht die Datenbankgröße auf etwa 2 TB. Die Empfängerdaten verbrauchen für diese Umgebung etwa 50 GB.

## Richtlinien für das Ändern von Annahmen

Die Annahmen für diese Szenarien wirken sich alle erheblich auf die Hardware-Empfehlungen und die Bereitstellungsarchitektur aus. In diesem Abschnitt werden Richtlinien zu verschiedenen Annahmen erläutert. Wenden Sie sich an das Adobe Campaign Consulting-Team, um spezielle Empfehlungen zu erhalten, die Ihren Anforderungen entsprechen.

* **Anzahl der Empfänger**
Aktive Empfänger benötigen sowohl Speicherplatz als auch Datenbankpufferspeicherplatz, sodass mehr Empfänger im Allgemeinen mehr Speicher und mehr CPU-Kapazität auf dem Datenbankserver benötigen. Die Speichersteigerungen sind für die Empfänger selbst relativ gering, können aber für die Ereignisverfolgungsdaten von E-Mail-Kampagnen erheblich sein.

* **Größe der E-Mail-Kampagne**
Die Häufigkeit von Kampagnenstarts hat Auswirkungen auf die CPU-Anforderungen des Datenbankservers. In Kombination mit Briefpost, eingehenden Interaktionen und anderen Workflows belasten Segmentierungsvorgänge für E-Mail-Kampagnen den Datenbankserver erheblich.

* **Briefpost-Häufigkeit**
Die Häufigkeit von Direktversand kann sich auf die CPU-Anforderungen des Datenbankservers auswirken. In Kombination mit Kampagnenstarts und anderen Workflows belasten Segmentierungsvorgänge für Direkt-Mailings den Datenbankserver erheblich.

* **SMS-Nachrichtenvolumen**
Wie die Größe von E-Mail-Kampagnen wird auch das Volumen von SMS-Nachrichten auf Campaign-Servern, die sich On-Premise befinden, nicht stark ausgelastet. Die Auslastung erfolgt hauptsächlich über Adobe Cloud Messaging-Server in der Cloud. Die Segmentierung für SMS-Kampagnen wie E-Mail und Briefpost kann die Marketing-Datenbank erheblich belasten. Deshalb sind die Häufigkeit der SMS-Kampagnenstarts und die Komplexität der Segmentierung relevanter als die Anzahl der SMS-Nachrichten.

* **Komplexität des Datenbankschemas**
Die Datenmenge für jeden aktiven Empfänger erfordert sowohl Speicherplatz als auch Datenbankpufferspeicherplatz, sodass mehr Empfänger im Allgemeinen mehr Speicher und CPU auf dem Datenbankserver benötigen. Bei komplexen Schemata müssen auch mehr Tabellen für die Segmentierung zusammengefügt werden, sodass Segmentierungsvorgänge viel langsamer ablaufen können und mehr Datenbank-CPU und -Speicher erforderlich sind, wenn Daten über mehrere Tabellen verteilt sind.

   Der Datenbankserverspeicher wird geschätzt, indem sichergestellt wird, dass der Datenbankpufferpool groß genug sein kann, um alle Empfängerdaten, temporäre Tabellen für laufende Workflows sowie einen Spielraum für andere Datenbankvorgänge zu enthalten.

* **Ausgehende Interaktion - Nutzung**
Regeln für Interaktionen im Batch-Modus werden in Workflows ausgewertet, die die gesamte Berechnungskomplexität der Datenbank übergeben. Der Hauptfaktor für den Aufwand in der Datenbank ist die Gesamtzahl der in Frage kommenden Angebote, die während eines Engine-Aufrufs berechnet wurden (Zielgröße X durchschnittliche Anzahl der Angebote pro Empfänger, bevor die n besten Angebote beibehalten werden). Die CPU-Geschwindigkeit des Datenbankservers ist der erste Leistungsfaktor.

* **Eingehende Interaktionen oder Nutzung der SOAP-API**
Regeln und Angebote für eingehende Interaktionen werden in der Marketing-Datenbank ausgewertet, was erhebliche Datenbankserver-Ressourcen erfordert, insbesondere CPU. Eine starke Nutzung von eingehenden Interaktionen oder SOAP-APIs erfordert separate Webserver, um die Arbeitslast von der Ausführung von Campaign-Workflows zu trennen.

* **Tracking der Datenaufbewahrungsdauer**
Die Erhöhung der Aufbewahrung von Tracking-Daten über 90 Tage hinaus erfordert mehr Datenbankspeicher und kann das System verlangsamen, da das Einfügen neuer Tracking-Daten in große Tabellen erfolgt. Tracking-Daten sind für die Kampagnensegmentierung nach 90 Tagen nicht nützlich. Daher wird eine kürzere Aufbewahrungsfrist empfohlen.

   Tracking-Daten sollten in Adobe Analytics oder ein anderes Analysesystem verschoben werden, wenn Sie eine langfristige Analyse des Marketing-Erlebnisses der Empfänger benötigen.

## Virtualisierung

Alle Campaign-Server eignen sich gut für die Virtualisierung. Es müssen mehrere Probleme angesprochen werden, um eine angemessene Verfügbarkeit und Leistung sicherzustellen.

* **Fail-Over-Konfiguration**
Cluster-Server, z. B. redundante Anwendungsserver unter einem Lastverteilungs-Proxy, müssen auf separater Hardware bereitgestellt werden, um sicherzustellen, dass beide VMs nicht herunterfahren, wenn Hardware-Fehler vorliegen.

* **I/O-Konfiguration**
Die empfohlene RAID-Konfiguration muss aus Gründen der Datenbanksicherheit beibehalten werden, um sicherzustellen, dass Datenverluste durch den Verlust eines Speichergeräts nicht zu Datenverlusten führen.

* **I/O-Leistung**
Die empfohlene IOPS-Bewertung für die Datenbankspeicherung muss eingehalten werden. Cloud-Dienste wie Amazon EC2 bieten möglicherweise nicht die erforderliche Leistung und müssen sorgfältig ausgewertet werden. Beispielsweise werden von Amazon EC2 bereitgestellte SSD-Volumes derzeit mit jeweils 20.000 IOPS bewertet. Weitere Informationen finden Sie unter [Amazon-Dokumentation](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/EBSVolumeTypes.html), sodass eine 4-Volume-RAID-Konfiguration mit 80.000 IOPS bewertet würde, was möglicherweise nicht ausreicht.

Adobe empfiehlt Leistungstests für jede virtualisierte Implementierung von Adobe Campaign, bevor das System in die Produktion aufgenommen wird.

## Verwandte Themen

* [Kampagnenüberwachungsprozesse](../../production/using/monitoring-processes.md)
* [Allgemeine Architektur von Campaign](../../installation/using/general-architecture.md)
* [Leistungs- und Durchsatzprobleme](../../production/using/performance-and-throughput-issues.md)
* [Checkliste für Sicherheit und Datenschutz](../../installation/using/get-started-security-privacy.md)
