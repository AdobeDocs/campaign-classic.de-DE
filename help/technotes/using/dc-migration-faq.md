---
product: campaign
title: Häufig gestellte Fragen zur Migration zu Adobe Managed Services (Public Cloud)
description: Häufig gestellte Fragen zur Migration von Campaign Classic zu Public Cloud
feature: Overview
role: User
level: Beginner
exl-id: a9cd08b0-55c2-4405-9fb8-f0c623cd4ccb
source-git-commit: 1f050ada481a7307a59ea6c81290bb0b24a3bf6c
workflow-type: tm+mt
source-wordcount: '2243'
ht-degree: 62%

---

# Häufig gestellte Fragen zur Migration zu Public Cloud{#dc-faq}

![](../../assets/v7-only.svg)

Im Rahmen der [Gold Standard Initiative](../../rn/using/gold-standard.md) wird das alte Rechenzentrum von Adobe von der  eingestellt. Campaign Classic-Instanzen müssen in Public Cloud Amazon Web Services (AWS) übertragen werden. [Erfahren Sie mehr über diese Initiative](dc-migration.md).

Nachstehend finden Sie eine Reihe häufiger Fragen zu diesem Projekt, den Auswirkungen auf Ihre Campaign-Umgebungen und anderen hilfreichen Ressourcen.

Für alle anderen Fragen wenden Sie sich bitte an die [Adobe-Kundenunterstützung](https://experienceleague.adobe.com/?support-solution=Campaign#support).

## Auswirkungen auf die Infrastruktur

![](assets/do-not-translate/database.png)

Die globalen Auswirkungen auf die Datenbank und Infrastruktur sind nachstehend aufgeführt.

* **Wird sich die Datenbank verändern? Welche Version hat die neue Datenbank? Welches Betriebssystem wird verwendet?**

   Adobe behält sich das Recht vor, die am besten geeignete Datenbank-Management-Engine auszuwählen und zu verwenden, um den Adobe Campaign-Dienst unter optimalen Bedingungen bereitzustellen.

   Darüber hinaus wird Adobe keine detaillierten Informationen zur Infrastruktur bereitstellen, um das beste Sicherheitsniveau zu gewährleisten.

* **Besteht das Risiko von Datenverlust?**

   Die Datenbank wird aus dem alten Rechenzentrum entfernt und in der Public Cloud (AWS) wiederhergestellt. Wenn die Anwendung im neuen Rechenzentrum neu gestartet wird, wird sie von dem Status fortgesetzt, der vor der Migration bestand. Die Benutzer werden keinen Unterschied bemerken, außer dass sich einige geplante Aufgaben verzögert haben werden.

* **Gibt es Unterschiede in der Größe des Pakets zwischen dem alten Rechenzentrum und der Public Cloud?**

   Wir stellen in der Public Cloud (AWS) neue Paketdefinitionen bereit, die auf der aktuellen Datenbankgröße, der Festplattengröße usw. basieren. Wenn beispielsweise ein Kunde in älteren Rechenzentren über einen Anwendungsserver verfügt, kann er je nach Package-Definitionen über zwei Anwendungsserver in Public Cloud (AWS) verfügen.

* **Wird sich die Build-Nummer oder die Campaign-Version ändern?**

   Als ersten Schritt werden wir den Campaign Classic-Build bei der Migration beibehalten.

   In einem weiteren Schritt werden wir mit dem Upgrade auf den neuesten Campaign Classic GA-Build fortfahren. Weiterführende Informationen dazu finden Sie in den [FAQ zum Build-Upgrade](../../platform/using/faq-build-upgrade.md) und den [Versionshinweisen zu Campaign Gold Standard](../../rn/using/gold-standard.md).

* **Was ist der Plan zur Behebung von Problemen nach der Migration?**

   Vor der Migration der Produktionssysteme sind umfangreiche Tests geplant. Bei Problemen bleibt [Adobe Kundenunterstützung](https://experienceleague.adobe.com/?support-solution=Campaign#support) der Hauptansprechpartner. Adobe hat ein Expertenteam zusammengestellt, das bei Bedarf zusätzliche Unterstützung bietet.

## Auswirkungen auf die Zustellbarkeit

![](assets/do-not-translate/features.png)

Die globalen Auswirkungen auf IPs, Blockierungsliste, Subdomains und URLs sind unten aufgeführt.

* **Wie werden IP-Adressen auf der Zulassungsliste gehandhabt? Müssen die Kunden der Zulassungsliste neue IP-Adressen für eingehenden Traffic von Campaign hinzufügen?**

   Die IP-Adresse der Adobe-Server wird sich ändern. Daher müssen die Kunden diese neuen IP-Adressen möglicherweise in der Zulassungsliste in ihr System einfügen.

   [Klicken Sie ](#config) hier , um weitere Informationen zur IP auf der Zulassungsliste zu erhalten.

* **Wie werden wir den zur Zulassungsliste hinzugefügten Port für den SFTP-/FTP-Zugriff handhaben?**

   Die SFTP-Konfiguration (öffentliche Schlüssel + IP auf der Zulassungsliste) wird auch vom alten Rechenzentrum in die Public Cloud (AWS) verschoben. Seitens des Kunden besteht kein Handlungsbedarf.

* **Werden IPs geändert?**

   Die IP-Adresse der Adobe-Server wird sich ändern. Daher müssen die Kunden diese neuen IP-Adressen möglicherweise der Zulassungsliste in ihrem System hinzufügen.

   [Klicken Sie ](#config) hier , um weitere Informationen zur IP auf der Zulassungsliste zu erhalten.

* **Wie wird die Zuordnung von Subdomains gehandhabt?**

   Bestehende Subdomains werden vom alten Rechenzentrum in die Public Cloud (AWS) verschoben. Dieser Prozess wird im Rahmen des Migrationsprozesses vom Zustellbarkeitsteam von Adobe gehandhabt.

   Adobe führt den Kunden durch die erforderlichen Tests, um sicherzustellen, dass die Konfiguration nach der Migration auf den neuen Public Cloud-Servern (AWS) erfolgreich durchgeführt wurde.

* **Entstehen durch die Migration neue URLs für Tracking, Ressourcen und Webanwendungen?**

   Nein, die bestehenden URLs bleiben erhalten.

* **Wird die Subdomain von Neolane.net in campaign.adobe.com geändert?**

   Sowohl `neolane.net` als auch `campaign.adobe.com` sind nach der Migration vorhanden. Einfach zu machen: wird neolane.net zu neuen Instanzen in Public Cloud (AWS) umgeleitet, sodass keine vom Kunden vorgenommenen Änderungen erforderlich sind.

* **Was ist der Plan für die IP-Erwärmung?**

   Zustellbarkeit von Adoben bewertet zunächst den Zustellbarkeitsstatus der Plattform und empfiehlt einen Plan für den Wechsel zu den neuen IPs

   Nach der Migration ist keine Erwärmung erforderlich. Sollte jedoch in Ausnahmefällen eine Erwärmung nötig sein, wird die [Adobe-Kundenunterstützung](https://experienceleague.adobe.com/?support-solution=Campaign#support) Kontakt zu den jeweiligen Kunden aufnehmen.

   Es ist jedoch geplant, diesen Vorgang für Ihr Unternehmen transparent zu gestalten, anders als der während des Go-Live erfolgte ursprüngliche Ramp-up.

   Nach Abschluss der Migration wird die Campaign-Instanz völlig andere Sende-IPs aufweisen. Um eine reibungslose Migration zu gewährleisten, wird Adobe ein Ramp-up der neuen Sende-IPs durchführen, indem der Traffic schrittweise von den alten auf die neuen IPs umgestellt wird.

* **Wechseln wir über die URL auf der Zulassungsliste?**

   Ja, dies wird in der Server-Konfigurationsdatei gespeichert, die von der Quelle in die neue Instanz kopiert wird.

* **Wie wird sich das auf unsere zugewiesene Subdomain auswirken, mit der wir unsere Kommunikation branden?**

   Die für die Marketing-Kommunikation verwendeten Subdomains bleiben gleich. Abhängig von der Implementierung sind jedoch Aktionen auf Client-Seite erforderlich:
   * Bei der Zuweisung von Subdomains zu Adobe (Standardeinstellung) übernimmt Adobe alle Änderungen und sorgt für einen nahtlosen Übergang.
   * Bei CNAME-Setup (Ausnahme) wird der Client aufgefordert, in Abstimmung mit Adobe Änderungen zu implementieren.

## Auswirkungen auf Konfiguration und Konnektivität

![](assets/do-not-translate/maintenance.png)

### Hinweis zur IP-Adresse auf der Zulassungsliste{#config}

Die Migration zur Public Cloud beinhaltet neue IPs für Adobe Campaign-Anwendungsserver, sodass sich eine IP-Änderung auf die Konnektivität zwischen Adobe-Servern und Ihren Informationssystemen auswirken kann.

![](assets/migration.png)

Betrachten wir die beiden Fälle:

* Eingehender Traffic: Die gesamte Netzwerkaktivität, die von Ihren Systemen oder anderen Drittanbietern an Adobe Campaign-Servern initiiert wird. Die Konfiguration wird von Adobe vorgenommen und dann während der Migration von der bestehenden Cloud in die Public Cloud kopiert. Anschließend wird die Konnektivität für den eingehenden Traffic wie nach der Migration beibehalten und es wird keine Aktion vom Kunden erwartet

* Ausgehender Traffic: Die gesamte Netzwerkaktivität, die von Adobe Campaign-Servern an Ihr Informationssystem oder einen anderen Drittanbieter initiiert wird (z. B.: SMS-Provider). Je nach den in Ihrem Unternehmen geltenden Sicherheitsrichtlinien kann die Änderung von IP-Adressen den Betrieb des Zulassungsliste-Programms über Ihr Informationssystem oder einen anderen Drittanbieter erfordern

### Globale Auswirkungen

Globale Auswirkungen auf die Konfiguration, die Konnektivität mit anderen Systemen und Produkten, APIs und die Zeitzone sind nachstehend aufgeführt.

* **Wirkt sich die Migration auf die Konnektivität zu externen Konten aus?**

   Ja. Drittanbieterintegrationen, beispielsweise SMS-Anbieter, sollten der Zulassungsliste neue IP-Adressen von Adobe Campaign-Anwendungsservern hinzufügen.

* **Beeinträchtigt die Migration die Konnektivität zu Adobe Analytics bei Verwendung des Genesis-Connectors? Wie verhält es sich mit dem Hinzufügen von Campaign-IP-Adressen zur Zulassungsliste Adobe Analytics?**

   Die IP-Adressen der Adobe Campaign-Anwendungsserver ändern sich. Dieser Schritt wird von der Adobe-Kundenunterstützung nach der Migration ausgeführt.

* **Beeinträchtigt die Migration die Konnektivität mit anderen Adobe-Lösungen (AEM, Target usw.)?**

   Integrationen sind eine Kombination aus IP-Adressen, die auf der Zulassungsliste deklariert werden, und Webdienst-Kontokonfiguration. Dies wird von der Adobe-Kundenunterstützung berücksichtigt und gehört.

   Auf der Zulassungsliste werden IP-Adressen in der externen Lösung benötigt, da sich die IP der Anwendungsserver ändert. Diese Informationen werden bereitgestellt. Andere Teile der Integration sind IMS-basiert und sollten unverändert funktionieren.

* **Was ist mit Kunden, die keine Org-ID für die IMS-Integration haben?**

   Kunden, die keine IMS-Org-ID haben, erhalten eine: Eine IMS-Organisations-ID wird an ihre Instanz angefügt.

* **Sind Multi-Branding-Konfigurationen von der Migration betroffen?**

   Nachdem die Subdomain und alle zugehörigen Konfigurationen korrekt vom alten Rechenzentrum in die Public Cloud (AWS) verschoben bzw. umgeleitet wurden, sind keine Auswirkungen mehr zu erwarten.

* **Hat die Migration Auswirkungen auf die API-Konnektivität?**

   Die IP-Adresse der Adobe-Server wird sich ändern. Daher müssen die Kunden diese neuen IP-Adressen möglicherweise der Zulassungsliste in ihrem System hinzufügen.

   [Klicken Sie ](#config) hier , um weitere Informationen zu IP auf der Zulassungsliste zu erhalten.

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

* Neueste regelmäßige Betriebssystem- und Sicherheits-Patches
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

   Das einzige Verbindungsproblem, das auftreten kann, hängt mit der Zulassungsliste auf Kundenseite zusammen. Der Kunde sollte diesen Test in der Nicht-Produktionsumgebung durchführen, um sicherzustellen, dass alles funktioniert, bevor er zur Produktionsumgebung wechselt.

* **Gibt es für das Rechenzentrum spezifische Konfigurationen für Zulassungslisten, die verschoben werden müssen?**

   Nein, es gibt keine Data Center-spezifische Konfiguration für Zulassungslisten zu verwalten.

* **Stellt Adobe sicher, dass benutzerdefinierte Skripts in der neuen Umgebung ordnungsgemäß ausgeführt werden?**

   Bei der Kundenimplementierung können benutzerdefinierte Skripts (Perl/Shell/Python/JavaScript) in Workflows verwendet werden, um beispielsweise Dateien und Ordner zu bearbeiten.

   Auf der gehosteten Instanz werden Skripte nur über die JavaScript-Engine ausgeführt. Andere Implementierungen können zu Sicherheitslücken und Problemen nach dem Upgrade führen. Sie werden deshalb nicht unterstützt.

* **Wird die IMS-Integration in der neuen Instanz wie bisher funktionieren oder muss die Konfiguration aktualisiert werden?**

   Da wir die DNS-Namen beibehalten, sollte nach der Migration alles wie bisher funktionieren.


## Durchführung der Migration

![](assets/do-not-translate/upgrades.png)

Die globalen Auswirkungen während der Migration werden unten aufgeführt.

* **Sollten Vorkehrungen getroffen werden, um die Marketing-Aktivitäten während der Migration einzustellen?**

   Adobe empfiehlt, alle Ausführungen zu verlangsamen und idealerweise anzuhalten, bevor die App im alten Rechenzentrum heruntergefahren wird: Sendungen und Workflows. Auf diese Weise wird der Neustart auf dem Cloud-Server (AWS) vereinfacht, da die Prozesse ausreichend Zeit hatten, ordnungsgemäß zu pausieren und den aktuellen Ausführungsstatus zu speichern.

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

* **Können wir nach der Migration noch auf alte Instanzen zugreifen?**

   Nach Abschluss der Anwendungsmigration ist keine erneute Ausführung von Prozessen im alten Rechenzentrum geplant. Wir gehen davon aus, dass alle Daten im alten Rechenzentrum gelöscht werden können. Die einzige Ausnahme ist das temporäre Backup, bis die geplanten Backup-Vorgänge auf Public Cloud (AWS) ausgeführt wurden.

* **Wie viel Zeit wird nach der Migration zu Public Cloud für das Testen der einzelnen Instanzen benötigt?**

   Abhängig von der Komplexität des Systems des Kunden ist zwischen der Migration der Staging-Umgebung und der Produktionsumgebung eine Wartezeit von mindestens 1 Woche erforderlich.

* **Wer wird mit dem Hinzufügen neuer IPs zur Zulassungsliste umgehen?**

   Das Team der Kundenunterstützung von Adobe wird dafür sorgen, dass der Kunde und Dritte auf das neue System zugreifen können, indem die neuen IPs zur Zulassungsliste hinzugefügt werden.

## Support und andere nützliche Links{#support}

* [Migration zu Adobe Managed Services (Public Cloud)](dc-migration.md)
* [Upgrade zum Gold-Standard](../../rn/using/gs-overview.md)
* [Häufig gestellte Fragen zum Build-Upgrade](../../platform/using/faq-build-upgrade.md)
