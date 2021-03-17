---
solution: Campaign Classic
product: campaign
title: Erste Schritte mit Sicherheit und Datenschutz
description: Erfahren Sie mehr über die wichtigsten Elemente, die hinsichtlich Sicherheit und Datenschutz überprüft werden müssen.
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
translation-type: tm+mt
source-git-commit: 922603492d2c98d751683d3aa481e9ab19bca70c
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 58%

---


# Erste Schritte mit Sicherheit und Datenschutz {#get-started-security-privacy}

In diesem Abschnitt erfahren Sie mehr über die wichtigsten Aspekte der Sicherheit und des Datenschutzes. Einige Konfigurationen können nur von Kunden vor Ort durchgeführt werden.

## Datenschutz

<img src="assets/do-not-localize/icon_privacy.svg" width="60px">

Die Datenschutzkonfiguration und entsprechende Härtungsmaßnahmen sind zentrale Bestandteile der Optimierung der Sicherheit. Im Folgenden finden Sie einige Best Practices zum Schutz der Privatsphäre:

* Schützen Sie die personenbezogenen Daten Ihrer Kunden, indem Sie HTTPS anstelle von HTTP verwenden.
* Verwenden Sie die eingeschränkte Anzeige personenbezogener Daten, um die Daten zu schützen und ihren Missbrauch zu verhindern.
* Stellen Sie sicher, dass der Zugriff auf verschlüsselte Passwörter beschränkt ist.
* Schützen Sie Seiten, die möglicherweise personenbezogene Daten enthalten (z. B. Mirrorseiten, Webanwendungen usw.).

[Mehr dazu](../../installation/using/privacy.md)

## Zugriffsverwaltung

<img src="assets/do-not-localize/icon_access.svg" width="60px">

Zugriffsverwaltung ist ein wichtiger Teil der Sicherheitshärtung. Im Folgenden finden Sie einige der wichtigsten Best Practices:

* Erstellen Sie eine ausreichende Anzahl von Sicherheitsgruppen.
* Stellen Sie sicher, dass jeder Benutzer über geeignete Zugriffsberechtigungen verfügt.
* Vermeiden Sie möglichst die Vergabe der Administrator-Funktion, und achten Sie darauf, dass sich nicht zu viele Benutzer in der Administrator-Gruppe befinden.

[Mehr dazu](../../installation/using/access-management.md)

## Richtlinien für Skripterstellung und Codierung

<img src="assets/do-not-localize/icon_scripting.svg" width="60px">

Beachten Sie bei der Entwicklung in Adobe Campaign (Workflows, Javascript, JSSP usw.) immer folgende Richtlinien:

* **Skripterstellung**: Vermeiden Sie SQL-Anweisungen, verwenden Sie parametrierte Funktionen anstelle von String-Konkatenation, und vermeiden Sie SQL-Injection, indem Sie die zu verwendenden SQL-Funktionen auf die Zulassungsliste setzen.

* **Sichern Sie das Datenmodell**: Verwenden Sie Spezifische Berechtigungen, um Operatoraktionen zu begrenzen, Systemkomponenten hinzuzufügen (sysFilter).

* **hinzufügen captchas in Webanwendungen**: Erfahren Sie, wie Sie auf Ihren öffentlichen Landingpages und Abonnement-Seiten captchas hinzufügen.

[Mehr dazu](../../installation/using/scripting-coding-guidelines.md)

## Netzwerk, Datenbank und SSL/TLS

<img src="assets/do-not-localize/icon_network.svg" width="60px">

Bei der Einrichtung einer On-Premise-Architektur muss unbedingt die Netzwerkkonfiguration geprüft werden.

Sie müssen außerdem die Sicherheit Ihrer Datenbank-Engine beachten.

[Mehr dazu](../../installation/using/network-database.md)

## Konfiguration des Servers

<img src="assets/do-not-localize/icon_server.svg" width="60px">

Alle Server müssen konfiguriert werden. Die Konfigurationsdateien sind vom Typ **serverConf.xml** und **`config-<instance>.xml`**. Die folgenden Schlüsselelemente müssen überprüft werden:

* **Sicherheitszonen**: Konfigurieren Sie Sicherheitszonen, damit die IP-Adressen von Clients eines Proxys automatisch berücksichtigt werden.

* **Schutz** beim Hochladen von Dateien: beschränken Sie die Dateitypen, die mit einem neuen Attribut uploadAllowList auf den Adobe Campaign-Server hochgeladen werden können. Dies kann in der Serverkonfigurationsdatei verwendet werden.

* **Relais**: Optimieren Sie die Relais-Konfiguration, indem Sie die Relais-Regeln für nicht verwendete Module/Anwendungen deaktivieren.

* **Schutz vor ausgehenden Verbindungen** und **Einschränkung der Befehle** (serverseitig)

* Sie können auch zusätzliche HTTP-Header hinzufügen und checkIPConsistent, enableTLS, sessionTimeOutSec aktivieren etc. Weitere Informationen finden Sie in der [Kampagne-Serverkonfigurationsdokumentation](../../installation/using/configuring-campaign-server.md) und in der [Serverkonfigurationsdatei.](../../installation/using/the-server-configuration-file.md)

[Mehr dazu](../../installation/using/server-configuration.md)

## Konfiguration des Webservers

<img src="assets/do-not-localize/icon_web.svg" width="60px">

Beim Konfigurieren des Webservers (Apache/IIS) sollten verschiedene Best Practices befolgt werden:

* Deaktivieren Sie die alte SSL-Version und -Ziffern.
* Entfernen Sie die TRACE-Methode
* Entfernen Sie das Banner
* Abfrage begrenzen, um das Hochladen wichtiger Dateien zu verhindern

[Mehr dazu](../../installation/using/web-server-configuration.md)
