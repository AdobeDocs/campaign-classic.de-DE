---
product: campaign
title: Empfehlungen zur Hardware-Dimensionierung für Campaign Classic v7
description: Empfehlungen zur Hardware-Dimensionierung für Campaign Classic v7
feature: Technote
exl-id: c47e73a0-dbd8-43f5-a363-7e6783dc7685
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: ht
source-wordcount: '2569'
ht-degree: 100%

---

# Empfehlungen zur Hardware-Dimensionierung{#hardware-sizing-reco}



## Übersicht

>[!CAUTION]
>
>Dieser Artikel dient lediglich als allgemeiner beispielhafter Leitfaden. Sie müssen sich an Ihren Adobe Campaign Customer Success Manager wenden, um die genaue Dimensionierung Ihrer Bereitstellung abzuschätzen, bevor Sie mit Ihrem Campaign-Projekt beginnen. Erwerben oder implementieren Sie erst **danach** Infrastruktur oder Hardware.

Dieses Dokument enthält allgemeine Empfehlungen für die Bereitstellung von Adobe Campaign Classic v7 in Ihrem On-Premise-Rechenzentrum oder Ihrer virtualisierten Cloud-Umgebung. Diese Art der Bereitstellung wird als **Hybrid**- oder **Mid-Sourcing**-Bereitstellung bezeichnet. Dadurch erhalten Sie die betriebliche Kontrolle über die Marketing-Instanz und Marketing-Datenbank von Campaign, während Adobe Cloud Messaging-Dienste zum Senden von E-Mails, SMS oder SMPP-Nachrichten sowie zum Erfassen von E-Mail-Öffnungen, Bounce Messages und Klick-Tracking-Daten verwendet werden.

Die Marketing-Instanz ist der Teil der Adobe Campaign-Architektur, der alle Marketing-Aktivitäten steuert und sämtliche von Kampagnen zurückgegebenen Empfänger- und Analysedaten speichert. Die Marketing-Instanz besteht aus einer Reihe von On-Premise-Servern, auf denen Adobe Campaign-Dienste ausgeführt werden, und einer relationalen Datenbank.

>[!CAUTION]
>
>Die Informationen in diesem Dokument gelten nicht, wenn Sie eine vollständig gehostete (in Adobe-Cloud-Diensten bereitgestellte) Adobe Campaign-Instanz verwenden.

Ausführliche Informationen zur Software-Kompatibilität finden Sie in der [Kompatibilitätsmatrix](../../rn/using/compatibility-matrix.md).


### Szenarien

Bereitstellungsdiagramme und Empfehlungen zur Hardware-Dimensionierung werden für drei repräsentative Szenarien bereitgestellt:

1. [Mittelgroß](#scenario-1) – 5 Millionen aktive Empfängerinnen und Empfänger im System
1. [Groß](#scenario-2) – 20 Millionen aktive Empfängerinnen und Empfänger im System
1. [Unternehmen](#scenario-3) – 50 Millionen aktive Empfängerinnen und Empfänger mit Transaktionsnachrichten

### Annahmen

In diesem Dokument werden außerdem die folgenden Nutzungsarten für alle drei Szenarien angenommen:

* Große E-Mail-Kampagnen werden zweimal wöchentlich an ca. 50 % der aktiven Empfängerinnen und Empfänger gesendet.
* Briefpost wird einmal pro Monat für jede Empfängerin und jeden Empfänger im System generiert.
* SMS-Nachrichten werden monatlich an ca. 10 % der aktiven Empfängerinnen und Empfänger gesendet.
* Das Datenbankschema, das jede Empfängerin und jeden Empfänger definiert, wurde um eine zusätzliche Tabelle erweitert, die für jede Empfängerin und jeden Empfänger etwa 200 Byte an Daten enthält.
* Das Adobe Campaign Interaction-Modul wird verwendet, um ausgehenden E-Mails Angebote hinzuzufügen.
* E-Mail-Tracking-Daten werden im Campaign-System 90 Tage lang aufbewahrt.

## Allgemeine Richtlinien

Campaign ist eine datenbankorientierte Anwendung, und die Performance des Datenbank-Servers ist entscheidend. Die Ausführung von Workflows, Segmentierungen, Uploads von Tracking-Daten, eingehende Interaktionen, Analysen und andere Aktivitäten führen alle zu Datenbankaktivität. Im Allgemeinen bestimmen die Größe und Häufigkeit dieser Vorgänge die Größe Ihrer Datenbank-Server.

Die Anwendungs-Server in Ihrer Marketing-Instanz benötigen ausreichend CPU und Arbeitsspeicher, um Workflows auszuführen und auf SOAP-API-Aufrufe zu reagieren, einschließlich Anfragen von Benutzenden der Campaign-Konsole. Die CPU-Anforderungen können für Workflows, die ausgehende Interaktionen mit komplexen Angebotsregeln verwenden, für Workflows, die benutzerdefiniertes JavaScript ausführen, und für Webanwendungen mit hohem Traffic erheblich sein.

Campaign-Webanwendungen können auch auf den App-Servern der Marketing-Instanz oder auf separaten Webserver-Systemen bereitgestellt werden. Da Webanwendungs-Workloads mit wichtigen Workflows und Benutzenden der Campaign-Konsole in Konflikt stehen, können Webanwendungen und eingehende Interaktionen auf separaten Servern bereitgestellt werden, um sicherzustellen, dass die Kernfunktionen von Campaign zuverlässig und mit guter Performance ausgeführt werden.

Aus Gründen der Sicherheit und Verfügbarkeit empfiehlt Adobe, den Internet-Traffic und den von geschäftlichen Anwenderinnen und Anwendern generierten Traffic zu trennen. Daher enthalten die Diagramme zwei Gruppen von Servern: den Webserver (Internet-Zugriff auf Web1 und Web2) und die Appserver (Geschäftsprozesse App1 und App2).

Es ist eine gesetzliche Voraussetzung für kommerzielle E-Mail-Absender, über eine funktionale Opt-out-Webseite zu verfügen. Adobe empfiehlt, für Ausfallszenarien redundante Computer in jedem Gruppen-Server zu verwenden. Dies gilt insbesondere, wenn Adobe Campaign die Opt-out-Seiten hostet.

### Reverse-Proxys

Die Campaign-Architektur setzt eine hohe Sicherheit durch, indem SSL über HTTP (HTTPS) für die Kommunikation zwischen Ihrer Marketing-Instanz und Adobe Cloud Messaging verwendet wird. Sicherheit, Zuverlässigkeit und Verfügbarkeit werden über Reverse-Proxys in einem DMZ-Subnetz („demilitarisierte Zone“) durchgesetzt, um die Server und die Datenbank der Marketing-Instanz zu isolieren und zu schützen.

### Lastenausgleich

Der Lastenausgleich für die Webserver wird in einer Aktiv/Aktiv-Konfiguration eingerichtet, wobei HTTPS am Proxy endet. Der Lastenausgleich für die Webserver wird in einer Aktiv/Aktiv-Konfiguration eingerichtet, wobei HTTPS am Proxy endet.

Adobe stellt Ihnen eine exklusive Liste von URL-Pfaden zur Verfügung, die in Ihrer Bereitstellungsumgebung an den Adobe Campaign-Server weitergeleitet werden können.

### Architektur

Die allgemeine Architektur ist ungeachtet der Volumen nahezu identisch. Die Anforderungen an Sicherheit und Hochverfügbarkeit setzen mindestens vier Server voraus (zwei Server, wenn keine WebApps verwendet werden). Der Unterschied in der Konfiguration variiert hauptsächlich bei der Hardware-Konfiguration wie CPU-Kern und Arbeitsspeicher.

## Szenario 1: Mittelgroße Bereitstellung{#scenario-1}

![](assets/scenario-1.png)

Geschätztes Volumen:

| Kanal | Anzahl |
| ----------------------- | ----------------- |
| Aktive Empfängerinnen und Empfänger | 5 Millionen |
| E-Mail | 4,2 Millionen/Monat |
| Briefpost | 1 Million/Monat |
| Mobile SMS | 100.000/Monat |
| Maximale E-Mail-Anzahl täglich | 500 |

Für diese Volumen bieten zwei Adobe Campaign-Anwendungs-Server-Systeme alle Funktionen für Adobe Campaign-Client-Benutzende und die Ausführung von Workflows. Bei 5 Millionen aktiven Empfängerinnen und Empfängern und dieser E-Mail-Anzahl sind die Workloads der Anwendungs-Server weder CPU- noch E/A-intensiv. Die meiste Belastung entfällt auf die Datenbank.

Die Adobe Campaign-Webserver werden in der sicheren Zone angezeigt.

### Web- und Anwendungs-Server

In diesem Szenario wird empfohlen, Adobe Campaign auf vier Computern mit folgender Spezifikation zu installieren:

**Quad-Core-CPU mit mindestens 3 GHz, 8 GB RAM, RAID 1 oder 10, 2 SSD mit je 80 GB**

Diese Systeme bilden den Anwendungs-Server für die Marketing-Instanz, der die Benutzenden der Campaign-Konsole direkt unterstützt und die Kampagnen-Workflows ausführt.

Reverse-Proxys in DMZ-Lastenausgleichs-Traffic an die Adobe Campaign-Webserver. Es ist nicht erforderlich, den Adobe Campaign-Softwarestack auf Proxy-Computern zu installieren. Es kann beliebige Reverse-Proxy-Software oder -Netzwerkausrüstung verwendet werden.

Funktionen zum Opt-in/Opt-out für Abonnements und Funktionen für Präferenzzentren können von Campaign oder Ihrer eigenen Website bereitgestellt werden. Wenn Sie diese Funktionalität auf Ihrer Website implementieren möchten, müssen Sie sicherstellen, dass die Präferenz- und Abonnementinformationen an die Marketing-Datenbank von Campaign weitergeleitet werden. Dies geschieht normalerweise durch die Erstellung von Extraktionsdateien, die von Campaign-Workflows automatisch hochgeladen werden.

Der Speicherplatzverbrauch auf Anwendungs-Servern hängt von der Aufbewahrungsdauer von Dateien ab, die mit Drittanbietern ausgetauscht werden (z. B. Druckanbietern für Briefpost), sowie von der Größe und Aufbewahrungsdauer der importierten flachen Dateien (wie z. B. Abonnements- oder Präferenzaktualisierungen von Ihrer Website) oder der Auszüge aus Ihren eigenen CRM- oder Marketing-Systemen.

### Datenbank

Die Hardware-Empfehlungen für den Datenbank-Server lauten wie folgt:

**Quad-Core-CPU mit mindestens 3 GHz, 16 GB RAM, RAID 1 oder 10, SSD mit mindestens 128 GB**

Die Speicherschätzung geht von einer vollständigen Zwischenspeicherung von etwa 500.000 Empfängerinnen und Empfängern bei einem großen Kampagnen-Launch sowie von zusätzlichem RDBMS-Pufferspeicher für die Ausführung von Workflows, den Import von Tracking-Daten und andere gleichzeitige Aktivitäten aus.

Schätzungsweise benötigt die Datenbank zum Speichern aller technischen Adobe Campaign-Daten (Kampagnen, Tracking, Arbeitstabellen usw.) bei einem Aufbewahrungszeitraum von drei Monaten etwa 35 GB an Speicherplatz. Wenn Sie Tracking-Daten 6 Monate lang aufbewahren, erhöht sich die Datenbankgröße auf etwa 40 GB, und bei 12 Monaten auf etwa 45 GB. Die Empfängerdaten verbrauchen bei dieser Umgebung etwa 5 GB.

>[!CAUTION]
>
>Diese Schätzung umfasst keine zusätzlichen Kundendaten. Wenn Sie zusätzliche Spalten oder Tabellen mit Kundendaten in die Adobe Campaign-Datenbank replizieren möchten, müssen Sie dafür den zusätzlichen Speicherplatzbedarf abschätzen. Für hochgeladene Segmente/Listen ist ebenfalls je nach Größe, Häufigkeit und Aufbewahrungszeitraum mehr Speicher erforderlich.

Beachten Sie außerdem, dass aufgrund der täglich verarbeiteten Menge an Informationen die IOPS des Datenbank-Servers wichtig sind. An einem Spitzentag können Sie beispielsweise Kampagnen für insgesamt 500.000 Empfängerinnen und Empfänger bereitstellen. Zur Ausführung jeder Kampagne fügt Adobe Campaign 500.000 Datensätze in eine Tabelle mit rund 12 Millionen Datensätzen ein (die Versandlog-Tabelle). Für eine akzeptable Performance während der Kampagnenimplementierung empfiehlt Adobe bei diesem Szenario mindestens 60.000 zufällige Lese-/Schreib-IOPS mit je 4 KB.


## Szenario 2: Große Bereitstellung{#scenario-2}

![](assets/scenario-2.png)

Geschätztes Volumen:

| Kanal | Anzahl |
| ----------------------- | ----------------- |
| Aktive Empfängerinnen und Empfänger | 20 Millionen |
| E-Mail | 42 Millionen/Monat |
| Briefpost | 10 Millionen/Monat |
| Mobile SMS | 1.000.000/Monat |
| Maximale E-Mail-Anzahl täglich | 5.000.000 |

### Web- und Anwendungs-Server

Bei diesem Szenario empfiehlt Adobe die Installation von Adobe Campaign auf vier Computern, nämlich zwei Anwendungs-Servern und zwei Webservern, mit der folgenden Spezifikation:

**Quad-Core-CPU mit mindestens 3 GHz, 8 GB RAM, RAID 1 oder 10, SSD mit 80 GB**

Die Anwendungs-Server unterstützen die Benutzenden der Campaign-Konsole sowie die Ausführung von Kampagnen-Workflows direkt. Diese Funktionalität wird auf zwei identischen Servern für hohe Verfügbarkeit bereitgestellt, wobei ein NAS-Dateisystem (Network-Attached Storage) gemeinsam genutzt wird, um Failover zu ermöglichen.

Die Webserver hosten Campaign-Webanwendungen, die die 10 Millionen aktiven Empfängerinnen und Empfänger im System ermöglichen.

Unter [Szenario 1: Mittegroße Bereitstellung](#scenario-1) finden Sie weitere Kommentare zu Proxys, Präferenzzentren/Abonnements und Speicherplatznutzung.

### Datenbank

Die Hardware-Empfehlungen für den Datenbank-Server lauten wie folgt:

**Octa-Core-CPU mit mindestens 3 GHz, 64 GB RAM, RAID 1 oder 10 und 2 SSD mit je 320 GB oder RAID 10 und SSD mit mindestens 640 GB**

Die Speicherschätzung geht von einer vollständigen Zwischenspeicherung von etwa 5.000.000 Empfängerinnen und Empfängern bei einem großen Kampagnen-Launch sowie von zusätzlichem RDBMS-Pufferspeicher für die Ausführung von Workflows, den Import von Tracking-Daten und andere gleichzeitige Aktivitäten aus.

Schätzungsweise benötigt die Datenbank zum Speichern aller technischen Adobe Campaign-Daten (Kampagnen, Tracking, Arbeitstabellen usw.) bei einem Aufbewahrungszeitraum von drei Monaten etwa 280 GB an Speicherplatz. Wenn Sie Tracking-Daten 6 Monate lang aufbewahren, erhöht sich die Datenbankgröße auf etwa 450 GB, und bei 12 Monaten auf etwa 900 GB. Die Empfängerdaten verbrauchen bei dieser Umgebung etwa 15 GB.

## Szenario 3: Implementierung für Unternehmen mit Message Center{#scenario-3}

![](assets/scenario-3.png)

Geschätztes Volumen:

| Kanal | Anzahl |
| ----------------------- | ----------------- |
| Aktive Empfängerinnen und Empfänger | 50 Millionen |
| E-Mail | 108 Millionen/Monat |
| Briefpost | 25 Millionen/Monat |
| Mobile SMS | 2,5 Millionen/Monat |
| Transaktionsnachrichten | 2,5 Millionen/Monat |
| Maximale E-Mail-Anzahl täglich | 2,5 Millionen |


Diese Implementierung, die 50 Millionen Empfängerinnen und Empfänger ermöglicht, entspricht im Wesentlichen der aus [Szenario 2](#scenario-2): Der Traffic der Campaign-Webanwendung wird an die Campaign-Webserver weitergeleitet, sodass der Webtraffic nach dem Launch großer Kampagnen keine Auswirkungen auf Campaign-Workflows und Benutzende der Client-Konsole hat.

Diese Implementierung umfasst auch Message Center-Aufrufe, die von Ihren eigenen Websites und Anwendungen aus gesteuert werden.


### Web- und Anwendungs-Server

Bei diesem Szenario empfiehlt Adobe, Adobe Campaign wie folgt auf vier Computern zu installieren:

* Anwendungs-Server
  **Zwei Systeme, Quad-Core-CPU mit mindestens 3 GHz, 8 GB RAM, RAID 1 oder 10, SSD mit 80 GB**

* Webserver
  **Zwei Systeme, Quad-Core-CPU mit mindestens 3 GHz, 16 GB RAM, RAID 1 oder 10, SSD mit 80 GB**


Die Anwendungs-Server unterstützen die Benutzenden der Campaign-Konsole sowie die Ausführung von Kampagnen-Workflows direkt. Diese Funktionalität wird auf zwei identischen Servern für hohe Verfügbarkeit bereitgestellt, wobei ein NAS-Dateisystem (Network-Attached Storage) gemeinsam genutzt wird, um Failover zu ermöglichen.

Die Webserver hosten Campaign-Webanwendungen, die die 10 Millionen aktiven Empfängerinnen und Empfänger im System ermöglichen.

Unter [Szenario 1: Mittegroße Bereitstellung](#scenario-1) finden Sie weitere Kommentare zu Proxys, Präferenzzentren/Abonnements und Speicherplatznutzung.

### Datenbank

Die Hardware-Empfehlungen für den Datenbank-Server lauten wie folgt:

**Octa-Core-CPU mit mindestens 3 GHz, 96 GB RAM, RAID 1 oder 10, SSD mit mindestens 1,5 TB**

Die Speicherschätzung geht von einer vollständigen Zwischenspeicherung von etwa 12.500.000 Empfängerinnen und Empfängern bei einem großen Kampagnen-Launch sowie von zusätzlichem RDBMS-Pufferspeicher für die Ausführung von Workflows, den Import von Tracking-Daten und andere gleichzeitige Aktivitäten aus.

Schätzungsweise benötigt die Datenbank zum Speichern aller technischen Adobe Campaign-Daten (Kampagnen, Tracking, Arbeitstabellen usw.) bei einem Aufbewahrungszeitraum von drei Monaten etwa 700 GB an Speicherplatz. Wenn Sie Tracking-Daten 6 Monate lang aufbewahren, erhöht sich die Datenbankgröße auf etwa 1,2 TB, und bei 12 Monaten auf etwa 2 TB. Die Empfängerdaten verbrauchen bei dieser Umgebung etwa 50 GB.

## Richtlinien für das Ändern der Annahmen

Die Annahmen für diese Szenarien wirken sich alle erheblich auf die Hardware-Empfehlungen und die Bereitstellungsarchitektur aus. In diesem Abschnitt werden Richtlinien zu verschiedenen Annahmen erläutert. Wenden Sie sich an das Adobe Campaign-Consulting-Team, um spezielle Empfehlungen für Ihre Anforderungen zu erhalten.

* **Anzahl der Empfängerinnen und Empfänger**
Aktive Empfängerinnen und Empfänger benötigen sowohl Speicherplatz als auch Datenbankpufferspeicher, sodass bei mehr Empfängerinnen und Empfängern im Allgemeinen auch mehr Speicher und mehr CPU-Kapazität auf dem Datenbank-Server erforderlich sind. Die Speichererhöhungen sind für die Empfängerinnen und Empfänger selbst relativ gering, können aber für die Ereignis-Tracking-Daten von E-Mail-Kampagnen erheblich sein.

* **Größe der E-Mail-Kampagne**
Die Häufigkeit von Kampagnen-Launches hat Auswirkungen auf die CPU-Anforderungen des Datenbank-Servers. In Kombination mit Briefpost, eingehenden Interaktionen und anderen Workflows belasten Segmentierungsvorgänge für E-Mail-Kampagnen den Datenbank-Server erheblich.

* **Häufigkeit von Briefpost**
Die Häufigkeit von Briefpost kann sich auf die CPU-Anforderungen des Datenbank-Servers auswirken. In Kombination mit Kampagnen-Launches und anderen Workflows belasten Segmentierungsvorgänge für Briefpost den Datenbank-Server erheblich.

* **Anzahl von SMS-Nachrichten**
Wie die Größe von E-Mail-Kampagnen bedeutet auch die Anzahl von SMS-Nachrichten keine große Belastung für Campaign-On-Premise-Server. Belastet werden hier vor allem die Adobe Cloud Messaging-Server in der Cloud. Die Segmentierung für SMS-Kampagnen wie E-Mail und Briefpost kann die Marketing-Datenbank erheblich belasten. Deshalb sind die Häufigkeit von SMS-Kampagnen-Launches und die Komplexität der Segmentierung relevanter als die Anzahl der SMS-Nachrichten.

* **Komplexität des Datenbankschemas**
Die Datenmenge für jede aktive Empfängerin und jeden aktiven Empfänger erfordert sowohl Speicherplatz als auch Datenbankpuffer, sodass mehr Empfängerinnen und Empfänger im Allgemeinen mehr Speicher und CPU auf dem Datenbank-Server benötigen. Bei komplexen Schemata müssen auch mehr Tabellen für die Segmentierung zusammengefügt werden, sodass Segmentierungsvorgänge unter Umständen deutlich langsamer durchgeführt werden und mehr Datenbank-CPU und Arbeitsspeicher erforderlich sind, wenn Daten über mehrere Tabellen verteilt sind.

  Der Arbeitsspeicher für den Datenbank-Server wird geschätzt, indem sichergestellt wird, dass der Datenbankpuffer-Pool groß genug für alle Empfängerdaten sowie die temporären Tabellen für aktive Workflows ist und dazu noch eine gewisse Reserve für andere Datenbankvorgänge hat.

* **Nutzung ausgehender Interaktionen**
Regeln für Interaktionen im Batch-Modus werden in Workflows ausgewertet, die die gesamte Berechnungskomplexität an die Datenbank übergeben. Der wichtigste Faktor für den Aufwand in der Datenbank ist die Gesamtzahl der geeigneten Angebote, die während eines Engine-Aufrufs berechnet wurden (Zielgruppengröße x durchschnittliche Anzahl der Angebote pro Empfänger, bevor die n besten Angebote beibehalten werden). Die CPU-Geschwindigkeit des Datenbank-Servers ist der wichtigste Performance-Faktor.

* **Nutzung von eingehenden Interaktionen oder SOAP-APIs**
Regeln und Angebote für eingehende Interaktionen werden in der Marketing-Datenbank ausgewertet, wodurch die Ressourcen des Datenbank-Servers, insbesondere die CPU, in erheblichem Maße in Anspruch genommen werden. Eine starke Nutzung von eingehenden Interaktionen oder SOAP-APIs setzt separate Webserver voraus, um die Arbeitslast von der Ausführung von Campaign-Workflows zu trennen.

* **Aufbewahrungszeitraum von Tracking-Daten**
Werden Tracking-Daten länger als 90 Tage aufbewahrt, ist mehr Datenbankspeicher erforderlich. Außerdem kann das System dadurch langsamer werden, da neue Tracking-Daten in große Tabellen eingefügt werden. Das Tracking von Daten ist nach 90 Tagen nicht mehr für die Kampagnensegmentierung nützlich. Daher wird eine kürzere Aufbewahrungsfrist empfohlen.

  Tracking-Daten sollten in Adobe Analytics oder ein anderes Analysesystem verschoben werden, wenn Sie auf eine langfristige Analyse des Marketing-Erlebnisses der Empfängerinnen und Empfänger angewiesen sind.

## Virtualisierung

Alle Campaign-Server eignen sich gut zur Virtualisierung. Es müssen verschiedene Punkte berücksichtigt werden, um eine angemessene Verfügbarkeit und Performance sicherzustellen.

* **Failover-Konfiguration**
Cluster-Server, z. B. redundante Anwendungs-Server unter einem Proxy mit Lastenausgleich, müssen auf separater Hardware bereitgestellt werden, um sicherzustellen, dass bei einem Hardware-Fehler nicht beide VMs ausfallen.

* **E/A-Konfiguration**
Die empfohlene RAID-Konfiguration muss zwecks Datenbanksicherheit beibehalten werden, damit bei Verlust eines Speichergeräts keine Daten verloren gehen.

* **E/A-Performance**
Die empfohlene IOPS-Bewertung für den Datenbankspeicher muss eingehalten werden. Cloud-Dienste wie Amazon EC2 bieten möglicherweise nicht die erforderliche Performance und müssen sorgfältig ausgewertet werden. Beispielsweise liefern von Amazon EC2 bereitgestellte SSD-Volumes derzeit jeweils 20.000 IOPS. Weitere Informationen finden Sie in der [Amazon-Dokumentation](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-volume-types.html). Eine RAID-Konfiguration mit vier Volumes entspräche also 80.000 IOPS, was unter Umständen nicht ausreicht.

Adobe empfiehlt Performance-Tests für jede virtualisierte Adobe Campaign-Implementierung, bevor das System in die Produktion aufgenommen wird.

## Verwandte Themen

* [Überwachungsverfahren in Campaign](../../production/using/monitoring-processes.md)
* [Allgemeine Campaign-Architektur](../../installation/using/general-architecture.md)
* [Performance- und Durchsatzprobleme](../../production/using/performance-and-throughput-issues.md)
* [Checkliste für Sicherheit und Datenschutz](../../installation/using/get-started-security-privacy.md)
