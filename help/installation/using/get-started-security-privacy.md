---
product: campaign
title: Checkliste für Sicherheit und Datenschutz
description: Erfahren Sie mehr über die wichtigsten zu überprüfenden Elemente bezüglich Sicherheit und Datenschutz
feature: Installation, Privacy, Access Management, Privacy Tools
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: ec40498e-e673-4792-8dcf-8bb7e852b532
source-git-commit: 19b40f0b827c4b5b7b6484fe4953aebe61d00d1d
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 52%

---

# Checkliste für Sicherheit und Datenschutz{#get-started-security-privacy}



In diesem Abschnitt erfahren Sie mehr über die wichtigsten Elemente, die im Hinblick auf Sicherheit und Datenschutz überprüft werden müssen. Einige Konfigurationen können nur von On-Premise-Kunden durchgeführt werden.

## Datenschutz

<img src="assets/do-not-localize/icon_privacy.svg" width="60px">

Die Datenschutzkonfiguration und entsprechende Härtungsmaßnahmen sind zentrale Bestandteile der Optimierung der Sicherheit. Im Folgenden finden Sie einige Best Practices zum Datenschutz:

* Schützen Sie die personenbezogenen Daten Ihrer Kunden, indem Sie HTTPS anstelle von HTTP verwenden.
* Verwenden Sie die eingeschränkte Anzeige personenbezogener Daten, um die Daten zu schützen und ihren Missbrauch zu verhindern.
* Stellen Sie sicher, dass der Zugriff auf verschlüsselte Passwörter beschränkt ist.
* Schützen Sie Seiten, die möglicherweise personenbezogene Daten enthalten (z. B. Mirrorseiten, Web-Anwendungen usw.).

[Mehr dazu](../../installation/using/privacy.md)

## Zugriffsverwaltung 

<img src="assets/do-not-localize/icon_access.svg" width="60px">

Die Zugriffsverwaltung ist ein wichtiger Bestandteil des Sicherheits-Managements. Im Folgenden finden Sie die wichtigsten Best Practices:

* Erstellen Sie eine ausreichende Anzahl von Sicherheitsgruppen.
* Stellen Sie sicher, dass jeder Benutzer über geeignete Zugriffsberechtigungen verfügt.
* Vermeiden Sie möglichst die Vergabe der Administrator-Funktion und achten Sie darauf, dass sich nicht zu viele Benutzer in der Administrator-Gruppe befinden.

[Mehr dazu](../../installation/using/access-management.md)

## Richtlinien für Script-Erstellung und Codierung

<img src="assets/do-not-localize/icon_scripting.svg" width="60px">

Bei Entwicklungsaufgaben in Adobe Campaign (Workflows, JavaScript, JSSP usw.) sollten Sie sich grundsätzlich an diesen Leitlinien orientieren:

* auf die Zulassungsliste setzen **Scripting**: SQL-Anweisungen vermeiden, parametrisierte Funktionen anstelle von Zeichenfolgenverkettung verwenden, SQL-Injection vermeiden, indem die zu verwendenden SQL-Funktionen zur hinzufügen.

* **Schutz des Datenmodells**: Verwenden Sie spezifische Berechtigungen, um Benutzeraktionen einzuschränken, und fügen Sie Systemfilter hinzu (sysFilter).

* **Hinzufügen von Captchas in Web-Anwendungen**: Erfahren Sie, wie Sie Captchas in Ihren öffentlichen Landingpages und Anmeldeseiten hinzufügen.

[Mehr dazu](../../installation/using/scripting-coding-guidelines.md)

## Netzwerk, Datenbank und SSL/TLS

<img src="assets/do-not-localize/icon_network.svg" width="60px">

Bei der Einrichtung einer On-Premise-Architektur muss unbedingt die Netzwerkkonfiguration geprüft werden.

Es ist auch zwingend erforderlich, dass Sie die Sicherheit Ihrer Datenbank-Engine befolgen.

[Mehr dazu](../../installation/using/network-database.md)


## Serverkonfiguration

<img src="assets/do-not-localize/icon_server.svg" width="60px">

Die Konfiguration muss auf allen Servern durchgeführt werden. Die Konfigurationsdateien sind vom Typ **serverConf.xml** und **`config-<instance>.xml`**. Im Folgenden sind die wichtigsten Elemente aufgeführt, die überprüft werden müssen:

* **Sicherheitszonen**: Konfigurieren Sie Sicherheitszonen, damit die IP-Adressen von Clients eines Proxys automatisch berücksichtigt werden.

* **Schutz vor Datei-Uploads**: Beschränken Sie die Dateitypen, die mit einem neuen Attribut „uploadAllowList“ auf den Adobe Campaign-Server hochgeladen werden können. Dies kann in der Server-Konfigurationsdatei verwendet werden.

* **Relais**: Optimieren Sie die Relais-Konfiguration, indem Sie die Relais-Regeln für nicht verwendete Module/Anwendungen deaktivieren.

* **Schutz ausgehender Verbindungen** und **Befehlsbeschränkung** (Server-seitig)

* Sie können auch zusätzliche HTTP-Kopfzeilen hinzufügen, checkIPConsistent aktivieren, TLS aktivieren, sessionTimeOutSec aktivieren usw. Weitere Informationen finden Sie in der [Dokumentation zur Campaign](../../installation/using/configuring-campaign-server.md)Serverkonfiguration und in der [](../../installation/using/the-server-configuration-file.md)Beschreibung der Serverkonfigurationsdatei“.

[Mehr dazu](../../installation/using/server-configuration.md)

## Konfiguration des Webservers

<img src="assets/do-not-localize/icon_web.svg" width="60px">

Bei der Konfiguration Ihres Webservers (Apache/IIS) sollten Sie verschiedene Best Practices befolgen:

* Deaktivieren Sie die alte SSL-Version und -Ziffern.
* TRACE-Methode entfernen
* Entfernen Sie das Banner
* Begrenzung der Abfragegröße, um das Hochladen wichtiger Dateien zu verhindern

[Mehr dazu](../../installation/using/web-server-configuration.md)
