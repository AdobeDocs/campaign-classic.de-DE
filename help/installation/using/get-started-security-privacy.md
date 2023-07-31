---
product: campaign
title: Checkliste für Sicherheit und Datenschutz
description: Erfahren Sie mehr über die wichtigsten zu prüfenden Elemente in Bezug auf Sicherheit und Datenschutz
feature: Installation, Privacy, Access Management, Privacy Tools
badge-v7-only: label="v7" type="Informative" tooltip="Gilt nur für Campaign Classic v7"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: ec40498e-e673-4792-8dcf-8bb7e852b532
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 58%

---

# Checkliste für Sicherheit und Datenschutz{#get-started-security-privacy}



In diesem Abschnitt erfahren Sie, welche Schlüsselelemente geprüft werden müssen, um Sicherheit und Datenschutz zu gewährleisten. Einige Konfigurationen können nur von On-Premise-Kunden durchgeführt werden.

## Datenschutz

<img src="assets/do-not-localize/icon_privacy.svg" width="60px">

Die Datenschutzkonfiguration und entsprechende Härtungsmaßnahmen sind zentrale Bestandteile der Optimierung der Sicherheit. Im Folgenden finden Sie einige Best Practices zum Datenschutz:

* Schützen Sie die personenbezogenen Daten Ihrer Kunden, indem Sie HTTPS anstelle von HTTP verwenden.
* Verwenden Sie die eingeschränkte Anzeige personenbezogener Daten, um die Daten zu schützen und ihren Missbrauch zu verhindern.
* Stellen Sie sicher, dass der Zugriff auf verschlüsselte Passwörter beschränkt ist.
* Schützen Sie Seiten, die möglicherweise personenbezogene Daten enthalten (z. B. Mirror-Seiten, Web-Anwendungen usw.).

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

* **Skripterstellung**: Vermeiden Sie SQL-Anweisungen, verwenden Sie parametrierte Funktionen anstelle von String-Verkettung und vermeiden Sie SQL-Injection, indem Sie die zu verwendenden SQL-Funktionen zur Zulassungsliste &quot;&quot;hinzufügen.

* **Schutz des Datenmodells**: Verwenden Sie spezifische Berechtigungen, um Benutzeraktionen einzuschränken, und fügen Sie Systemfilter hinzu (sysFilter).

* **Hinzufügen von Captchas in Webanwendungen**: Hier erfahren Sie, wie Sie Captchas zu Ihren öffentlichen Landingpages und Anmeldeseiten hinzufügen.

[Mehr dazu](../../installation/using/scripting-coding-guidelines.md)

## Netzwerk, Datenbank und SSL/TLS

<img src="assets/do-not-localize/icon_network.svg" width="60px">

Bei der Einrichtung einer On-Premise-Architektur muss unbedingt die Netzwerkkonfiguration geprüft werden.

Außerdem müssen Sie die Sicherheit Ihrer Datenbank-Engine unbedingt befolgen.

[Mehr dazu](../../installation/using/network-database.md)

>[!CAUTION]
>
>Ab dem 14. Juli 2021 verlieren Client-Systeme, die das TLS 1.2-Protokoll nicht unterstützen, den Zugriff auf alle Adobe-Produkte und -Dienste. Stellen Sie sicher, dass alle Benutzer- und Client-Systeme vor diesem Datum TLS 1.2-konform sind. [Weitere Informationen](https://helpx.adobe.com/x-productkb/multi/eol-tls-support.html)

## Konfiguration des Servers

<img src="assets/do-not-localize/icon_server.svg" width="60px">

Alle Server müssen konfiguriert werden. Die Konfigurationsdateien sind vom Typ **serverConf.xml** und **`config-<instance>.xml`**. Die folgenden Schlüsselelemente müssen überprüft werden:

* **Sicherheitszonen**: Konfigurieren Sie Sicherheitszonen, damit die IP-Adressen von Clients eines Proxys automatisch berücksichtigt werden.

* **Schutz vor Datei-Uploads**: Beschränken Sie die Dateitypen, die mit einem neuen uploadAllowList -Attribut auf den Adobe Campaign-Server hochgeladen werden können. Dies kann in der Serverkonfigurationsdatei verwendet werden.

* **Relais**: Optimieren Sie die Relais-Konfiguration, indem Sie die Relais-Regeln für nicht verwendete Module/Anwendungen deaktivieren.

* **Schutz vor ausgehenden Verbindungen** und **Einschränkung der Befehle** (serverseitig)

* Sie können auch zusätzliche HTTP-Header hinzufügen und checkIPConsistent, enableTLS, sessionTimeOutSec aktivieren etc. Siehe Abschnitt [Dokumentation zur Konfiguration des Campaign-Servers](../../installation/using/configuring-campaign-server.md) und [Beschreibung der Serverkonfigurationsdatei](../../installation/using/the-server-configuration-file.md) für weitere Informationen.

[Mehr dazu](../../installation/using/server-configuration.md)

## Konfiguration des Webservers

<img src="assets/do-not-localize/icon_web.svg" width="60px">

Beim Konfigurieren des Webservers (Apache/IIS) sollten verschiedene Best Practices befolgt werden:

* Deaktivieren Sie die alte SSL-Version und -Ziffern.
* Entfernen Sie die TRACE-Methode
* Entfernen Sie das Banner
* Begrenzen der Abfragegröße, um das Hochladen wichtiger Dateien zu verhindern

[Mehr dazu](../../installation/using/web-server-configuration.md)
