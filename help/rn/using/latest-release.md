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
ht-degree: 96%

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

* Es wurde ein Problem behoben, bei dem die Aktivität **Laden (Datei)** keine Dateien auf den Server hochladen konnte<!--after an upgrade to version 8.3.8-->. Benutzende können nun Dateien erfolgreich hochladen, ohne dass der Fortschritt einfriert oder Konsolenfehler auftreten. (NEO-47269)

* Es wurden Segmentierungsfehler in Apache <!--following an upgrade to Adobe Campaign Classic 7.2.2 build 9349--> behoben. Diese Fehlerbehebung verhindert die Generierung von Kerndateien und stellt einen stabilen Server-Betrieb sicher. (NEO-59059)

* Es wurde ein Verbindungsproblem mit der Google BigQuery-Datenbank <!--after upgrading to version 7.3.3 build 9359--> behoben. Benutzende können nun mithilfe des externen GCP-Kontos Verbindungen erfolgreich testen. (NEO-62455)

* Die Kompatibilität bei Aktualisierungen der Spalten vom Typ „Boolesch“ und „Datum/Uhrzeit“ in Google BigQuery-Tabellen wurde mit Federated Data Access (FDA) verbessert. Diese Fehlerbehebung stellt eine ordnungsgemäße Verarbeitung von Datentypen während Einfüge-/Aktualisierungsvorgängen sicher. (NEO-65774)

* Eine Sicherheitslücke beim Einfügen von Ressourcen wurde geschlossen, durch die Angreifende HTML-Elemente in E-Mail-Endpunkte einschleusen konnten. Diese Sicherheitsverbesserung verhindert unbefugten Zugriff und Phishing-Angriffe. (NEO-66462)

* Zeitweise auftretende Fehler beim Einfügen von Daten in Google BigQuery-Tabellen, die aufgrund von Problemen mit HTTP-Inhalten oder der Übertragungskodierung aufgetreten sind, wurden behoben. Diese Fehlerbehebung stellt stabile Workflows zum Laden von Daten sicher. (NEO-66989)

* Es wurde eine Sicherheitslücke beim Pfaddurchlauf in der `File.list()`-Methode in Workflows geschlossen. Diese Sicherheitsverbesserung verhindert unbefugten Verzeichniszugriff und schützt sensible Dateien. (NEO-77898)

* Es wurde ein Problem behoben, bei dem SMS-Versandlogs nicht korrekt in den Status „Auf Mobiltelefon erhalten“ wechselten. Diese Verbesserung stellt genaue Versandberichte sicher. (NEO-78843)

* Es wurden Anmeldefehler in Adobe Campaign Classic bei Verwendung von Azure Federated Data Access (FDA) behoben. Benutzende können sich nun erfolgreich über die Client-Konsole anmelden. (NEO-79373)

* Das Problem, dass Workflows durch die Methode `CCurlAzureBlobStorage::UploadStream()` abstürzen, wurde behoben. Diese Verbesserung stellt eine stabile Workflow-Ausführung sicher. (NEO-79598)

* Unter Windows wurden zwei kritische Kompilierungs-Flags (`ControlFlowGuard` und `StackProtection`) aktiviert, um die Produktsicherheit zu erhöhen und Nutzungsrisiken zu minimieren. (NEO-80145)

* Es wurde ein Problem behoben, bei dem Ereignisstatus beim Broadlog-Status „Fehlgeschlagen“ inkorrekt gesendet wurden. Diese Verbesserung stellt genaue Ereignisberichte sicher. (NEO-80245)

* Die POP3 OAuth-Aktualisierungs- und -Zugriffstoken werden nun in der Datenbank gespeichert und der Fehler `Authentication failure: unknown user name or bad password` wird nach Ablauf des Aktualisierungs-Tokens nicht mehr angezeigt. (NEO-80683)

* Anstatt der Client-ID des externen Marketing Cloud(MAC)-Kontos wird nun eine Option `XApiKey` als Wert für die Client-ID verwendet, um eine Verbindung zu Adobe Analytics herzustellen. (NEO-80434)

* Es wurde ein Problem behoben, durch das inMail-Benutzende aufgrund des Token-Ablaufs auf Authentifizierungsfehler stießen. Benutzende können nun die Verbindung testen und den Server neu starten, um ähnliche Probleme zu beheben. (NEO-80683)

* Die Funktionalität des Analyse-APIs wurde verbessert, indem sichergestellt wird, dass alle Analyseaufrufe einen konsistenten API-Schlüssel (Campaign1) zur Authentifizierung verwenden, und zwar auch beim Wechsel zu einer zufälligen Client-ID. Dies stellt ein nahtloses Analyse-Tracking sicher. (NEO-80434)

* Der BigQuery Federated Data Access(FDA)-Connector wurde verbessert, indem Benutzende nun den Timeout-Zeitraum für Abfragen anpassen können. Diese Verbesserung verhindert Timeout-Fehler bei lang laufenden Abfragen. (NEO-81222)

* Der Upgrade-Prozess für Campaign <!--7.4.1-->-Versionen wurde aktualisiert und enthält jetzt die erforderlichen Abhängigkeiten. Diese Verbesserung vereinfacht den Upgrade-Prozess für Benutzende. (NEO-81433)

* Das Problem, dass die Konsole bei Verwendung eines Unter-Workflows in Kombination mit einem `enum`-Feld abstürzt, wurde behoben. Diese Verbesserung stellt eine stabile Workflow-Ausführung sicher. (NEO-81864)

* Es wurde ein Problem behoben, durch das untergeordnete MTA-Prozesse hängen geblieben sind, was Versand-Slots blockierte. Diese Fehlerbehebung sorgt für reibungslose Versandvorgänge für Push- und WhatsApp-Nachrichten. (NEO-82351)

* Es wurde ein Problem behoben, bei dem Sendungen bei ausstehender Personalisierung aufgrund pausierter Versandaktivitäten hängen blieben. Diese Verbesserung stellt die erfolgreiche Ausführung des Versands sicher. (NEO-82781)

* Die IMS-Anmeldefunktionen wurde durch Verwendung des CampaignIO-Endpunkts zur Authentifizierung verbessert. Diese Verbesserung optimiert den Anmeldeprozess. (NEO-82838)

* Google BigQuery Federated Data Access(FDA)-Timeout-Fehler wurden erneut behoben, um eine stabile Ausführung der Abfrage nach der Hotfix-Bereitstellung sicherzustellen. (NEO-82923)

* Es wurde ein Speicherplatzproblem beim Laden großer Datenvolumen in Teradata-Tabellen behoben. Diese Verbesserung stellt stabile Datenladevorgänge sicher. (NEO-83252)

* Es wurde ein Problem behoben, bei dem GCP-Abfragen aufgrund von nicht übereinstimmenden Datums- und Zeitstempelvergleichen <!--after upgrading to version 9383--> fehlgeschlagen sind. Diese Verbesserung stellt die Kompatibilität der Abfragen sicher. (NEO-83826)

* Es wurden Versandfehler aufgrund der Wiederaufnahme ausgesetzter Versandaktivitäten behoben. Diese Fehlerbehebung stellt eine erfolgreiche Ausführung des Versands sicher. (NEO-83809)

* Es wurden Authentifizierungsfehler mit dem Snowflake Federated Data Access(FDA)-Connector bei Authentifizierung mit privatem Schlüssel behoben. Diese Verbesserung stellt erfolgreiche Datenbankverbindungen sicher. (NEO-84024)

* Es wurden Watchdog-Änderungen implementiert, um die durch hängen gebliebene Prozesse verursachte Blockierung untergeordneter MTA-Slots zu beheben. Diese Verbesserung stellt reibungslose Versandvorgänge sicher. (NEO-84553)

* JavaScript-Warteprüfungen wurden erweitert, um die durch Prozesse in einem Arbeitszustand verursachte Blockierung untergeordneter MTA-Slots zu beheben. Diese Fehlerbehebung stellt stabile Versandvorgänge sicher. (NEO-85150)

