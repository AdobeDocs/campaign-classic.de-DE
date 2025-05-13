---
product: campaign
title: Aktuelle Version
description: Aktuelle Versionshinweise von Campaign Classic v7
feature: Release Notes
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: cdbcfc5aa0614e41ce76cb777fec58fbd01797d2
workflow-type: tm+mt
source-wordcount: '908'
ht-degree: 26%

---

# Aktuelle Version {#latest-release}

Auf dieser Seite werden neue Funktionen, Verbesserungen und Fehlerbehebungen der **aktuellen Version Campaign Classic v7** aufgelistet. Jeder neue Build weist einen Status auf, der durch eine bestimmte Farbe dargestellt wird. Sie erfahren mehr über den Build-Status von Campaign Classic v7 auf [dieser Seite](rn-overview.md).

## Version 7.4.2  {#release-7-4-2}

### Build 9391 {#build-9391}

[!BADGE Eingeschränkte Verfügbarkeit]{type=Informative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=de#rn-statuses" tooltip="Eingeschränkte Verfügbarkeit"}

_Dienstag, 12. Mai 2025_

Dieser Build umfasst die folgenden Fehlerbehebungen:

* Fehlerkorrektur - In Setups, die nicht mit Oracle erstellt wurden, tritt jetzt kein Postupgrade-Problem mehr auf. (NEO-87012)
* Fehlerkorrektur - Die Client-Konsole und der Server sind jetzt nicht mehr von einem TLS/HTTPS-Backend-Problem betroffen. (NEO-87432)

### Build 9390 {#build-9390}

[!BADGE Allgemeine Verfügbarkeit]{type=Positive url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=de#rn-statuses" tooltip="Allgemeine Verfügbarkeit"}

_2. April 2025_

<!--
### Compatibility updates {#comp-7-4-2}

This release comes with the following compatibility updates:

* JQuery library update: fixes multiple UI issues (reports, web apps)
* PostgreSQL 15 and 16

-->

**Verbesserungen bezüglich der Sicherheit**

Diese Version enthält mehrere Korrekturen von Sicherheitsproblemen.

Die Verbindung mit Adobe-Lösungen und -Anwendungen über das externe **[!UICONTROL Adobe Experience Cloud]**-Konto wurde aktualisiert, um die Sicherheit zu erhöhen.

**Wichtige Fehlerbehebungen**

Diese Version enthält die folgenden Hauptfehlerbehebungen:

* TLS-/SMPP-Verbindung: Behebung von SMPP-Stabilitätsproblemen

* Google BigQuery-Fehlerbehebungen:

   * Behebung von Regressionen bei Datentypen vom Typ „BOOLEAN“
   * Behebung von Problemen mit Proxy-Einstellungen
   * Behebung von Regressionen bei Datentypen vom Typ „DATETIME“
   * Behebung der Stabilität beim Massenladevorgang
   * Verbesserte interne Tests bei ODBC-Versionen
   * Behebung eines Problems mit Sonderzeichen im Verbindungs-String
   * Entfernung des Standard-Timeouts (5 Minuten) für Google BigQuery-Abfragen

* Mail Transfer Agent (MTA): Behebung eines Problems, bei dem ein verwaistes untergeordnetes MTA-Element im Status **[!UICONTROL Start ausstehend]** hängen bleibt.


**Weitere Fehlerbehebungen**

Die folgenden Probleme wurden ebenfalls in dieser Version behoben:

* Fehlerkorrektur - Die Aktivität **Laden (Datei)** lädt keine Dateien auf den Server<!--after an upgrade to version 8.3.8-->. Benutzer können jetzt Dateien erfolgreich hochladen, ohne dass ein steckengebliebener Fortschritt oder Konsolenfehler auftritt. (NEO-47269)

* Behobene Segmentierungsfehler in Apache <!--following an upgrade to Adobe Campaign Classic 7.2.2 build 9349-->. Diese Fehlerbehebung verhindert die Generierung von Kerndateien und stellt einen stabilen Serverbetrieb sicher. (NEO-59059)

* Es wurde ein Verbindungsproblem mit der Google BigQuery-<!--after upgrading to version 7.3.3 build 9359--> behoben. Benutzer können jetzt mithilfe des externen GCP-Kontos Verbindungen erfolgreich testen. (NEO-62455)

* Verbesserte Kompatibilität für Spaltenaktualisierungen vom Typ „Boolean“ und „Datum/Uhrzeit“ in Google BigQuery-Tabellen mit Federated Data Access (FDA). Diese Fehlerbehebung stellt eine ordnungsgemäße Verarbeitung von Datentypen während Einfüge-/Aktualisierungsvorgängen sicher. (NEO-65774)

* Fehlerkorrektur - Beim Einschleusen von Ressourcen tritt jetzt keine Sicherheitslücke mehr auf, durch die Angreifer HTML-Elemente in E-Mail-Endpunkte einfügen können. Diese Sicherheitsverbesserung verhindert unbefugten Zugriff und Phishing-Angriffe. (NEO-66462)

* Zeitweise auftretende Fehler beim Einfügen von Daten in Google BigQuery-Tabellen aufgrund von Problemen mit HTTP-Inhalten oder der Übertragungskodierung wurden behoben. Diese Fehlerbehebung stellt stabile Workflows zum Laden von Daten sicher. (NEO-66989)

* Behebung einer Verwundbarkeit durch Pfaddurchlauf in der `File.list()`-Methode in Workflows. Diese Sicherheitsverbesserung verhindert nicht autorisierten Verzeichniszugriff und schützt sensible Dateien. (NEO-77898)

* Fehlerkorrektur - SMS-Versandlogs werden jetzt nicht korrekt in den Status „Auf Mobilgerät empfangen“ aktualisiert. Diese Verbesserung gewährleistet ein genaues Reporting der Sendungen. (NEO-78843)

* Behobene Anmeldefehler in Adobe Campaign Classic bei Verwendung von Azure Federated Data Access (FDA). Benutzer können sich jetzt erfolgreich über die Client-Konsole anmelden. (NEO-79373)

* Fehlerkorrektur - Die `CCurlAzureBlobStorage::UploadStream()` Methode führt nicht mehr zu einem Absturz in Workflows. Diese Verbesserung gewährleistet eine stabile Ausführung des Workflows. (NEO-79598)

* Unter Windows wurden zwei kritische Kompilierungs-Flags (`ControlFlowGuard` und `StackProtection`) aktiviert, um die Produktsicherheit zu erhöhen und Nutzungsrisiken zu minimieren. (NEO-80145)

* Fehlerkorrektur - Ereignisstatus werden jetzt korrekt gesendet, wenn der Broadlog-Status „Fehlgeschlagen“ ist. Diese Verbesserung gewährleistet ein genaues Reporting über Ereignisse. (NEO-80245)

* Die POP3 OAuth-Aktualisierung und das Zugriffstoken werden jetzt in der Datenbank gespeichert und `Authentication failure: unknown user name or bad password` Fehler wird nach Ablauf des Aktualisierungstokens nicht mehr angezeigt. (NEO-80683)

* Eine Option `XApiKey` wird jetzt als Wert für die Client-ID verwendet, um eine Verbindung zu Adobe Analytics herzustellen, anstatt die Client-ID des externen Marketing Cloud (MAC)-Kontos zu verwenden. (NEO-80434)

* Es wurde ein Problem behoben, bei dem inMail-Benutzer aufgrund des Token-Ablaufs auf Authentifizierungsfehler stießen. Benutzer können jetzt die Verbindung testen und den Server neu starten, um ähnliche Probleme zu beheben. (NEO-80683)

* Verbesserte Funktionalität der Analytics-API, da sichergestellt wird, dass alle Analytics-Aufrufe einen konsistenten API-Schlüssel (Campaign1) für die Authentifizierung verwenden, auch beim Wechsel zu einer zufälligen Client-ID. Dies stellt ein nahtloses Analytics-Tracking sicher. (NEO-80434)

* Der BigQuery Federated Data Access (FDA)-Connector wurde verbessert, indem Benutzenden ermöglicht wurde, den Timeout-Zeitraum für Abfragen anzupassen. Diese Verbesserung verhindert Zeitüberschreitungsfehler bei lang laufenden Abfragen. (NEO-81222)

* Der Upgrade-Prozess für Campaign <!--7.4.1-->-Versionen wurde aktualisiert und enthält jetzt die erforderlichen Abhängigkeiten. Diese Verbesserung vereinfacht den Upgrade-Prozess für Benutzer. (NEO-81433)

* Es wurde ein Konsolen-Absturzproblem bei der Verwendung eines Unter-Workflows in Kombination mit einem `enum` behoben. Diese Verbesserung gewährleistet eine stabile Ausführung des Workflows. (NEO-81864)

* Es wurde ein Problem behoben, bei dem untergeordnete MTA-Prozesse stecken blieben, was die Bereitstellungssteckplätze blockierte. Diese Fehlerbehebung sorgt für reibungslose Versandvorgänge für Push- und WhatsApp-Nachrichten. (NEO-82351)

* Fehlerkorrektur - Sendungen bleiben jetzt nicht mehr bei ausstehender Personalisierung aufgrund pausierter Versandaktivitäten. Diese Verbesserung stellt die erfolgreiche Ausführung des Versands sicher. (NEO-82781)

* Verbesserte IMS-Anmeldefunktionen durch die Verwendung des CampaignIO-Endpunkts zur Authentifizierung. Diese Verbesserung optimiert den Anmeldeprozess. (NEO-82838)

* Google BigQuery Federated Data Access (FDA)-Zeitüberschreitungsfehler wurden erneut behoben, um eine stabile Ausführung der Abfrage nach der Hotfix-Bereitstellung sicherzustellen. (NEO-82923)

* Es wurde ein Speicherplatzproblem beim Laden großer Datenvolumen in Teradata-Tabellen behoben. Diese Verbesserung gewährleistet stabile Datenladevorgänge. (NEO-83252)

* Es wurde ein Problem behoben, bei dem GCP-Abfragen aufgrund von nicht übereinstimmenden Datums- und Zeitstempelvergleichen <!--after upgrading to version 9383-->. Diese Verbesserung stellt die Kompatibilität der Abfragen sicher. (NEO-83826)

* Behebung von fehlgeschlagenen Sendungen aufgrund der Wiederaufnahme pausierter Versandaktivitäten Diese Fehlerbehebung stellt eine erfolgreiche Ausführung des Versands sicher. (NEO-83809)

* Es wurden Authentifizierungsfehler mit dem Snowflake Federated Data Access (FDA)-Connector bei Verwendung der Authentifizierung mit privatem Schlüssel behoben. Diese Verbesserung stellt eine erfolgreiche Datenbankverbindung sicher. (NEO-84024)

* Watchdog-Änderungen wurden implementiert, um die durch blockierte Prozesse verursachte Blockierung des untergeordneten MTA-Steckplatzes zu beheben. Diese Verbesserung gewährleistet einen reibungslosen Versand. (NEO-84553)

* Erweiterte JavaScript-Warteprüfungen zur Behebung der Blockierung untergeordneter MTA-Steckplätze, die durch Prozesse in einem Arbeitszustand verursacht wurde. Diese Fehlerbehebung gewährleistet stabile Versandvorgänge. (NEO-85150)

