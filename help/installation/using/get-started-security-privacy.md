---
product: campaign
title: Erste Schritte mit Sicherheit und Datenschutz
description: Erfahren Sie mehr über die Schlüsselelemente, die hinsichtlich Sicherheit und Datenschutz überprüft werden müssen.
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: ec40498e-e673-4792-8dcf-8bb7e852b532
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 70%

---

# Erste Schritte mit Sicherheit und Datenschutz {#get-started-security-privacy}

![](../../assets/v7-only.svg)

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

* **Skripterstellung**: Vermeiden Sie SQL-Anweisungen, verwenden Sie parametrierte Funktionen anstelle von String-Konkatenation, und vermeiden Sie SQL-Injection, indem Sie die zu verwendenden SQL-Funktionen auf die Zulassungsliste setzen.

* **Schutz des Datenmodells**: Verwenden Sie spezifische Berechtigungen, um Benutzeraktionen einzuschränken, und fügen Sie Systemfilter hinzu (sysFilter).

* **Hinzufügen von Captchas in Webanwendungen**: Hier erfahren Sie, wie Sie Captchas zu Ihren öffentlichen Landingpages und Anmeldeseiten hinzufügen.

[Mehr dazu](../../installation/using/scripting-coding-guidelines.md)

## Netzwerk, Datenbank und SSL/TLS

<img src="assets/do-not-localize/icon_network.svg" width="60px">

Bei der Einrichtung einer On-Premise-Architektur muss unbedingt die Netzwerkkonfiguration geprüft werden.

Außerdem müssen Sie die Sicherheit Ihrer Datenbank-Engine unbedingt befolgen.

[Mehr dazu](../../installation/using/network-database.md)

## Konfiguration des Servers

<img src="assets/do-not-localize/icon_server.svg" width="60px">

Alle Server müssen konfiguriert werden. Die Konfigurationsdateien sind vom Typ **serverConf.xml** und **`config-<instance>.xml`**. Die folgenden Schlüsselelemente müssen überprüft werden:

* **Sicherheitszonen**: Konfigurieren Sie Sicherheitszonen, damit die IP-Adressen von Clients eines Proxys automatisch berücksichtigt werden.

* **Schutz beim Datei-Upload**: beschränken Sie die Dateitypen, die mit einem neuen uploadAllowList -Attribut auf den Adobe Campaign-Server hochgeladen werden können. Dies kann in der Serverkonfigurationsdatei verwendet werden.

* **Relais**: Optimieren Sie die Relais-Konfiguration, indem Sie die Relais-Regeln für nicht verwendete Module/Anwendungen deaktivieren.

* **Schutz vor ausgehenden Verbindungen** und **Einschränkung der Befehle** (serverseitig)

* Sie können auch zusätzliche HTTP-Header hinzufügen und checkIPConsistent, enableTLS, sessionTimeOutSec aktivieren etc. Weitere Informationen finden Sie in der [Dokumentation zur Konfiguration des Campaign-Servers](../../installation/using/configuring-campaign-server.md) und der [Beschreibung der Serverkonfigurationsdatei](../../installation/using/the-server-configuration-file.md) .

[Mehr dazu](../../installation/using/server-configuration.md)

## Konfiguration des Webservers

<img src="assets/do-not-localize/icon_web.svg" width="60px">

Beim Konfigurieren des Webservers (Apache/IIS) sollten verschiedene Best Practices befolgt werden:

* Deaktivieren Sie die alte SSL-Version und -Ziffern.
* Entfernen Sie die TRACE-Methode
* Entfernen Sie das Banner
* Begrenzen Sie die Abfragegröße, um das Hochladen wichtiger Dateien zu verhindern.

[Mehr dazu](../../installation/using/web-server-configuration.md)
