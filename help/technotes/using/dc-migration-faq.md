---
product: campaign
title: Häufig gestellte Fragen zur Migration zu Adobe Managed Services (Public Cloud)
description: Häufig gestellte Fragen zur Migration von Campaign Classic zu Public Cloud
hidefromtoc: true
feature: Overview
role: User
level: Beginner
source-git-commit: a4e7fb474d83be821343babacc493fd43c02857d
workflow-type: tm+mt
source-wordcount: '2273'
ht-degree: 81%

---

# Häufig gestellte Fragen zur Migration zu Public Cloud{#dc-faq}

![](../../assets/v7-only.svg)

Im Rahmen der [Gold Standard Initiative](../../rn/using/gold-standard.md) wird das alte Rechenzentrum von Adobe von der  eingestellt. Campaign Classic-Instanzen müssen in Public Cloud Amazon Web Services (AWS) übertragen werden. [Erfahren Sie mehr über diese Initiative](dc-migration.md).

Nachstehend finden Sie eine Reihe allgemeiner Fragen zu diesem Projekt und zu den Auswirkungen auf Ihre Campaign-Umgebungen sowie weitere nützliche Informationsquellen.

Für alle anderen Fragen wenden Sie sich bitte an die [Adobe-Kundenunterstützung](https://experienceleague.adobe.com/?support-solution=Campaign#support).

## Auswirkungen auf die Infrastruktur

![](assets/do-not-translate/database.png)

Die globalen Auswirkungen auf die Datenbank und Infrastruktur sind nachstehend aufgeführt.

* **Wird sich die Datenbank verändern? Welche Version hat die neue Datenbank? Welches Betriebssystem wird verwendet?**

   Adobe behält sich das Recht vor, die am besten geeignete Datenbank-Management-Engine auszuwählen und zu verwenden, um den Adobe Campaign-Dienst unter optimalen Bedingungen bereitzustellen.

   Darüber hinaus wird Adobe keine detaillierten Informationen zur Infrastruktur bereitstellen, um das beste Sicherheitsniveau zu gewährleisten.

* **Besteht das Risiko von Datenverlust?**

   Die Datenbank wird aus dem alten Rechenzentrum entfernt und in der Public Cloud (AWS) wiederhergestellt. Beim Neustart im neuen Rechenzentrum wird die Anwendung genau in dem Zustand fortgesetzt, in dem sie sich vor dem Herunterfahren befand. Die Benutzer werden keinen Unterschied bemerken, außer dass sich einige geplante Aufgaben verzögert haben werden.

* **Gibt es Unterschiede in der Größe des Pakets zwischen dem alten Rechenzentrum und der Public Cloud?**

   Wir stellen in der Public Cloud (AWS) neue Paketdefinitionen bereit, die auf der aktuellen Datenbankgröße, der Festplattengröße usw. basieren. Wenn beispielsweise ein Kunde in alten Rechenzentren genau einen Anwendungsserver hat, kann er je nach Paketdefinitionen zwei Anwendungsserver in der Public Cloud (AWS) verwenden.

* **Wird sich die Build-Nummer oder die Campaign-Version ändern?**

   Als ersten Schritt werden wir den Campaign Classic-Build bei der Migration beibehalten.

   In einem weiteren Schritt werden wir mit dem Upgrade auf den neuesten Campaign Classic GA-Build fortfahren. Weiterführende Informationen dazu finden Sie in den [FAQ zum Build-Upgrade](../../platform/using/faq-build-upgrade.md) und den [Versionshinweisen zu Campaign Gold Standard](../../rn/using/gold-standard.md).

* **Was ist der Plan zur Behebung von Problemen nach der Migration?**

   Vor der Migration der Produktionssysteme sind umfangreiche Tests geplant. Bei Problemen bleibt [Adobe Kundenunterstützung](https://experienceleague.adobe.com/?support-solution=Campaign#support) der Hauptansprechpartner. Adobe hat ein Expertenteam zusammengestellt, das bei Bedarf zusätzliche Unterstützung bietet.

## Auswirkungen auf die Zustellbarkeit

![](assets/do-not-translate/features.png)

Die globalen Auswirkungen auf IPs, Blockierungsliste, Subdomains und URLs sind unten aufgeführt.

* **Wie werden IPs auf der Zulassungsliste gehandhabt? Müssen Kunden neue IP-Adressen für eingehenden Traffic von Campaign auf die Zulassungsliste setzen?**

   Die IP-Adresse der Adobe-Server wird sich ändern. Deshalb müssen Kunden diese neuen IP-Adressen möglicherweise in ihrem System auf die Zulassungsliste setzen.

   [Klicken Sie hier](#config), um weitere Informationen zu IPs auf der Zulassungsliste zu erhalten.

* **Wie werden Ports gehandhabt, die für den SFTP-/FTP-Zugriff auf die Zulassungsliste gesetzt werden?**

   Die SFTP-Konfiguration (öffentliche Schlüssel + IP auf der Zulassungsliste) wird auch vom alten Rechenzentrum in die Public Cloud (AWS) verschoben. Seitens des Kunden besteht kein Handlungsbedarf.

* **Werden IPs geändert?**

   Die IP-Adresse der Adobe-Server wird sich ändern. Deshalb müssen Kunden diese neuen IP-Adressen möglicherweise in ihrem System auf die Zulassungsliste setzen.

   [Klicken Sie hier](#config), um weitere Informationen zu IPs auf der Zulassungsliste zu erhalten.

* **Wie wird die Zuordnung von Subdomains gehandhabt?**

   Vorhandene Subdomains werden vom alten Rechenzentrum in die Public Cloud (AWS) verschoben. Dieser Prozess wird im Rahmen des Migrationsprozesses vom Zustellbarkeitsteam von Adobe gehandhabt.

   Adobe führt den Kunden durch die erforderlichen Tests, um sicherzustellen, dass die Konfiguration nach der Migration auf den neuen Public Cloud-Servern (AWS) erfolgreich durchgeführt wurde.

* **Entstehen durch die Migration neue URLs für Tracking, Ressourcen und Webanwendungen?**

   Nein, die bestehenden URLs bleiben erhalten.

* **Wird die Subdomain von Neolane.net in campaign.adobe.com geändert?**

   Sowohl `neolane.net` als auch `campaign.adobe.com` sind nach der Migration vorhanden. Einfach zu machen: wird neolane.net zu neuen Instanzen in Public Cloud (AWS) umgeleitet, sodass keine Änderungen vom Kunden erforderlich sind.

* **Was ist der Plan für die IP-Erwärmung?**

   Zustellbarkeit von Adoben bewertet zunächst den Zustellbarkeitsstatus der Plattform und empfiehlt einen Plan für den Wechsel zu den neuen IPs

   Nach der Migration ist keine Erwärmung erforderlich. Sollte jedoch in Ausnahmefällen eine Erwärmung nötig sein, wird die [Adobe-Kundenunterstützung](https://experienceleague.adobe.com/?support-solution=Campaign#support) Kontakt zu den jeweiligen Kunden aufnehmen.

   Es ist jedoch geplant, diesen Vorgang für Ihr Unternehmen transparent zu gestalten, anders als der während des Go-Live erfolgte ursprüngliche Ramp-up.

   Nach Abschluss der Migration wird die Campaign-Instanz völlig andere Sende-IPs aufweisen. Um eine reibungslose Migration zu gewährleisten, wird Adobe ein Ramp-up der neuen Sende-IPs durchführen, indem der Traffic schrittweise von den alten auf die neuen IPs umgestellt wird.

* **Werden auch URLs auf die Zulassungsliste verschoben?**

   Ja, dies wird in der Server-Konfigurationsdatei gespeichert, die von der Quelle in die neue Instanz kopiert wird.

* **Wie wird sich das auf unsere zugewiesene Subdomain auswirken, mit der wir unsere Kommunikation branden?**

   Die für die Marketing-Kommunikation verwendeten Subdomains bleiben unverändert. Abhängig von der Implementierung können jedoch auf der Client-Seite Aktionen erforderlich sein:
   * Bei einer Subdomain-Zuweisung an Adobe (Standard) übernimmt Adobe alle Änderungen und sorgt für einen nahtlosen Übergang.
   * Bei der CNAME-Einrichtung (Ausnahme) muss der Kunde die Änderungen selbst implementieren. Dabei ist die Koordination mit Adobe ist erforderlich.

## Auswirkungen auf Konfiguration und Konnektivität

![](assets/do-not-translate/maintenance.png)

### Hinweis zu IPs auf der Zulassungsliste{#config}

Die Migration zur Public Cloud beinhaltet neue IPs für Adobe Campaign-Anwendungsserver, sodass sich eine IP-Änderung auf die Konnektivität zwischen Adobe-Servern und Ihren Informationssystemen auswirken kann.

![](assets/migration.png)

Betrachten wir die beiden Fälle:

* Eingehender Traffic: Die gesamte Netzwerkaktivität, die von Ihren Systemen oder anderen Drittanbietern an Adobe Campaign-Servern initiiert wird. Die Konfiguration wird von Adobe vorgenommen und dann während der Migration von der bestehenden Cloud in die Public Cloud kopiert. Anschließend wird die Konnektivität für den eingehenden Traffic wie nach der Migration beibehalten und es wird keine Aktion vom Kunden erwartet

* Ausgehender Traffic: Die gesamte Netzwerkaktivität, die von Adobe Campaign-Servern an Ihr Informationssystem oder einen anderen Drittanbieter initiiert wird (z. B.: SMS-Provider). Je nach den in Ihrem Unternehmen geltenden Sicherheitsrichtlinien kann das Ändern von IP-Adressen einen Zulassungslistenvorgang Ihres Informationssystems oder eines anderen Dritten erforderlich machen.

### Globale Auswirkungen

Globale Auswirkungen auf die Konfiguration, die Konnektivität mit anderen Systemen und Produkten, APIs und die Zeitzone sind nachstehend aufgeführt.

* **Wirkt sich die Migration auf die Konnektivität zu externen Konten aus?**

   Ja. Drittanbieterintegrationen, beispielsweise SMS-Anbieter, sollten der Zulassungsliste neue IP-Adressen der Adobe Campaign-Anwendungsserver hinzufügen.

* **Beeinträchtigt die Migration die Konnektivität zu Adobe Analytics bei Verwendung des Genesis-Connectors? Wie sieht es mit dem Hinzufügen von Campaign-IP-Adressen zur Zulassungsliste durch Adobe Analytics aus?**

   Die IP-Adressen der Adobe Campaign-Anwendungsserver ändern sich. Dieser Schritt wird von der Adobe-Kundenunterstützung nach der Migration ausgeführt.

* **Beeinträchtigt die Migration die Konnektivität mit anderen Adobe-Lösungen (AEM, Target usw.)?**

   Integrationen sind eine Kombination aus IP-Adressen, die in der Zulassungsliste- und Webdienst-Kontokonfiguration deklariert werden. Dies wird von der Adobe-Kundenunterstützung berücksichtigt und gehört.

   Es gibt IP-Adressen auf der Zulassungsliste, die in der externen Lösung benötigt werden, da sich die IP der Anwendungsserver ändert. Diese Informationen werden bereitgestellt. Andere Teile der Integration sind IMS-basiert und sollten unverändert funktionieren.

* **Was ist mit Kunden, die keine Org-ID für die IMS-Integration haben?**

   Kunden, die keine IMS-Org-ID haben, erhalten eine: Eine IMS-Organisations-ID wird an ihre Instanz angefügt.

* **Sind Multi-Branding-Konfigurationen von der Migration betroffen?**

   Nachdem die Subdomain und alle zugehörigen Konfigurationen korrekt vom alten Rechenzentrum in die Public Cloud (AWS) verschoben bzw. umgeleitet wurden, sind keine Auswirkungen mehr zu erwarten.

* **Hat die Migration Auswirkungen auf die API-Konnektivität?**

   Die IP-Adresse der Adobe-Server wird sich ändern. Deshalb müssen Kunden diese neuen IP-Adressen möglicherweise in ihrem System auf die Zulassungsliste setzen.

   [Klicken Sie ](#config) hier , um weitere Informationen zu IP auf Zulassungsliste zu erhalten.

* **Stellt Adobe sicher, dass alle JavaScript-Speicherkonfigurationsparameter nach der Migration korrekt eingestellt sind?**

   Adobe kopiert die Instanzkonfiguration aus dem alten Rechenzentrum in die Public Cloud (AWS), damit diese Werte auch nach der Migration erhalten bleiben.

* **Besteht die Gefahr, dass auf bestimmte Dateierweiterungen nicht mehr zugegriffen werden kann?**

   Es wird empfohlen, das Laden von Schriftartdateien und Outlook-Besprechungsdateien in den Ordner für öffentliche Ressourcen zuzulassen. Diese Konfiguration erfolgt in der aktuellen `config-<instance>.xml`-Datei. Diese wird gemeinsam mit den Konfigurationsdateien in das neue Rechenzentrum kopiert.

* **Ändert sich die Zeitzone auf dem neuen Server? Können Kunden ihre aktuelle Zeitzone beibehalten?**

   Sie kann sich je nach dem Standort des neuen Servers ändern. Die Kunden können jedoch ihre aktuelle Zeitzone beibehalten.

   [Klicken Sie ](../../workflow/using/managing-time-zones.md) hier , um mehr über die Zeitzonenverwaltung in Adobe Campaign Classic v7 zu erfahren.


## Sicherheit und Berechtigungen

![](assets/do-not-translate/security.png)

Durch diese Migration zur Public Cloud (AWS) werden die Kundenumgebungen entsprechend allen nötigen Sicherheitsanforderungen laufend auf den neuesten Stand gebracht. Dies umfasst:

* Regelmäßige neue Betriebssystem- und Sicherheits-Patches
* Isolierung der Infrastruktur nach Kunden
* Verwaltete Sicherheits- und Auditprüfungen zur Unterstützung von Cloud-Infrastrukturen wie Lastenausgleich, Netzwerksicherheitsregeln und Speicherverschlüsselung

Die Auswirkungen auf Berechtigungen, Zertifikate und SFTP-Zugriff sind unten aufgeführt.

* **Verschiebt Adobe alle Zertifikate auf die neuen Server?**

   Ja, alle Zertifikate werden im Rahmen dieser Migration verschoben.

* **Benötigt Adobe neue STP-Zugangsschlüssel vom Kunden?**

   Nein, Adobe kopiert die SFTP-Zugriffsschlüssel auf den neuen Server.

* **Wie werden SFTP-Berechtigungen gehandhabt?**

   Wir stellen sicher, dass neue SFTP-Server, Benutzer, Verzeichnisse und Dateien genau dieselben Berechtigungen haben.

* **Wie sieht der Notfallplan aus, um die Betriebsbereitschaft der Kunden sicherzustellen, sollte die SFTP-Verbindung nicht hergestellt werden können?**

   Das einzige Konnektivitätsproblem, das auftreten kann, hängt mit der Zulassungsliste auf Kundenseite zusammen. Der Kunde sollte diesen Test in der Nicht-Produktionsumgebung durchführen, um sicherzustellen, dass alles funktioniert, bevor er zur Produktionsumgebung wechselt.

* **Gibt es spezielle Konfigurationen der Zulassungsliste für Rechenzentren, die ebenfalls migriert werden müssen?**

   Nein, es gibt keine rechenzentrumspezifische Konfigurationen der Zulassungsliste, die verwaltet werden müssen.

* **Stellt Adobe sicher, dass benutzerdefinierte Skripts in der neuen Umgebung ordnungsgemäß ausgeführt werden?**

   Bei der Kundenimplementierung können benutzerdefinierte Skripts (Perl/Shell/Python/JavaScript) in Workflows verwendet werden, um beispielsweise Dateien und Ordner zu bearbeiten.

   Auf der gehosteten Instanz werden Skripts nur über die JavaScript-Engine ausgeführt. Andere Implementierungen können zu Sicherheitslücken und Problemen nach dem Upgrade führen. Sie werden deshalb nicht unterstützt.

* **Wird die IMS-Integration in der neuen Instanz wie bisher funktionieren oder muss die Konfiguration aktualisiert werden?**

   Da wir die DNS-Namen beibehalten, sollte nach der Migration alles wie bisher funktionieren.


## Durchführung der Migration

![](assets/do-not-translate/upgrades.png)

Die globalen Auswirkungen während der Migration werden unten aufgeführt.

* **Sollten Vorkehrungen getroffen werden, um die Marketing-Aktivitäten während der Migration einzustellen?**

   Adobe empfiehlt, die Ausführung von Sendungen und Workflows zu verlangsamen und im Idealfall anzuhalten, bevor die Anwendung im alten Rechenzentrum heruntergefahren wird. Auf diese Weise wird der Neustart auf dem Cloud-Server (AWS) vereinfacht, da die Prozesse ausreichend Zeit hatten, ordnungsgemäß zu pausieren und den aktuellen Ausführungsstatus zu speichern.

* **Sind Ausfallzeiten des Adobe Campaign-Dienstes zu erwarten?**

   Eine gewisse Ausfallzeit der Plattform ist bei der Migration unvermeidlich. Das Ziel dieses Plans ist es, Ihnen zu helfen, die Ausfallzeit möglichst gering zu halten.

   Die Datenübertragung zwischen den Rechenzentren ist der Teil des Vorgangs, der die größte Auswirkung auf die Ausfallzeit hat. Die Daten werden auf zwei Arten gespeichert:

   * In der Datenbank (die mit Abstand wichtigste)
   * In Dateien auf dem Anwendungsserver (Datenimport und -export)

   Die Reduzierung der Datenbankgröße ist von größter Bedeutung, um die Datenübertragung zu beschleunigen. Empfehlungen:

   * Reduzieren Sie die Aufbewahrungszeiträume historischer Daten (Versandlogs, Trackinglogs usw.).
   * Löschen Sie nicht mehr genutzte Datensätze aus anderen Tabellen (Sendungen, Empfänger, benutzerdefinierte Tabellen).


* **Wie hoch ist die geschätzte Ausfallzeit für die Migration einer Instanz?**

   Die Ausfallzeit hängt zur Gänze von der Größe der Datenbank und des SFTP-Dateispeichers des Kunden ab. Bitte wenden Sie sich an Ihre Kundenunterstützung, um eine ungefähre Dauer zu erfahren.

* **Was ist mit Nachrichten, die vom alten Server gesendet werden? Kann zu jedem Zeitpunkt auf Links zugegriffen werden?**

   Während der Migration bleibt nur ein Dienst funktionsfähig: die Umleitung von E-Mail-Links. Alle Empfänger gelangen beim Anklicken des Links in einer E-Mail auf die Landingpage. Diese Klicks werden jedoch nicht getrackt, sodass die Klickraten für die Sendungen, die kurz vor der Migration gestartet wurden, niedriger als gewöhnlich sein werden.

* **Was ist mit Mid-Sourcing/RT-Umgebungen?**

   MID-Sourcing und RT werden wie jede andere gehostete Infrastruktur gehandhabt.

* **In welcher Reihenfolge werden die Migrationen durchgeführt?**

   Die Umgebungen werden in der folgenden Reihenfolge migriert:

   1. Entwicklungsumgebungen
   1. Staging-Umgebungen
   1. Produktionsumgebungen
   1. RT-Umgebungen
   1. Mid-Sourcing-Umgebungen

* **Wie sieht der Rollback-Plan aus?**

   Der Rollback-Plan besteht darin, das DNS zurückzusetzen und den Lese- und Schreibzugriff zur Quelldatenbank wieder zu aktivieren. Dies erfolgt automatisch.

* **Besteht nach der Migration Zugriff auf die alten Instanzen?**

   Nach Abschluss der Anwendungsmigration ist keine erneute Ausführung von Prozessen im alten Rechenzentrum geplant. Wir gehen davon aus, dass alle Daten im alten Rechenzentrum gelöscht werden können. Die einzige Ausnahme ist das temporäre Backup, bis die geplanten Backup-Vorgänge auf Public Cloud (AWS) ausgeführt wurden.

* **Wie viel Zeit steht für das Testen jeder Instanz nach der Migration zur Public Cloud zur Verfügung?**

   Abhängig von der Komplexität des Systems des Kunden ist zwischen der Migration der Staging-Umgebung und der Produktionsumgebung eine Wartezeit von mindestens 1 Woche erforderlich.

* **Wer kümmert sich um das Hinzufügen neuer IPs zur Zulassungsliste?**

   Das Team der Kundenunterstützung von Adobe sorgt dafür, dass Kunden und etwaige Drittparteien Zugriff auf das neue System haben, indem die neuen IP-Adressen auf die Zulassungsliste gesetzt werden.

## Support und andere nützliche Links{#support}

* [Migration zu Adobe Managed Services (Public Cloud)](dc-migration.md)
* [Upgrade zum Gold-Standard](../../rn/using/gs-overview.md)
* [Häufig gestellte Fragen zum Build-Upgrade](../../platform/using/faq-build-upgrade.md)

