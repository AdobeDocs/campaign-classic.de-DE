---
product: campaign
title: Grundprinzip
description: Grundprinzip
feature: Monitoring
badge-v7-prem: label="Nur On-Premise/Hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Gilt nur für Hybrid- und On-Premise-Bereitstellungen"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 1c032ef9-af11-4947-90c6-76cb9434ae85
TQID: https://experienceleague.adobe.com/HCoIXlpEtxAHVh-rj51UD1GTNRnXh8Ir8x4t3QZT9YU
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: b12f6872-9271-4369-85e5-86969a0b99a2
  - id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
subfeature_v2:
  - id: cfc95e9b-b035-4403-a6a9-b27a8a053a37
  - id: e656c701-3899-4db3-989c-de0980ddfffa
  - id: eff19c99-440a-4318-b319-444edc4d8d8f
topic_v2:
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 530
ht-degree: 16%

---

# Grundprinzip{#operating-principle}



Technisch gesehen basiert die Adobe Campaign-Plattform auf mehreren Modulen.

Es gibt viele Adobe Campaign-Module. Einige werden ununterbrochen ausgeführt, andere wiederum nur gelegentlich zur Durchführung administrativer Aufgaben (z.B. zur Konfiguration der Datenbankverbindung) oder zur Ausführung wiederkehrender Aufgaben (z.B. zur Konsolidierung von Tracking-Informationen) gestartet.

Es gibt drei Typen von Adobe Campaign-Modulen:

* Module mit Mehrfach-Instanzen: Für alle Instanzen wird ein einzelner Prozess ausgeführt. Dies gilt für die folgenden Module: **web**, **syslogd**, **trackinglogd** und **watchdog** (Aktivitäten aus der Datei **config-default.xml**).
* Module mit Einfach-Instanz: Für die einzelnen Instanzen wird jeweils ein Prozess ausgeführt. Dies gilt für die folgenden Module: **mta**, **wfserver**, **inMail**, **sms** und **stat** (Aktivitäten aus der Datei **config-`<instance>`.xml**).
* Dienstprogramm-Module: Hierbei handelt es sich um Module, die von Zeit zu Zeit für gelegentlich notwendige oder wiederkehrende Operationen ausgeführt werden **z. B** Bereinigung, **config** Herunterladen von Trackinglogs.

Die Modulverwaltung erfolgt über das Befehlszeilen-Tool **nlserver**, das im **bin** des Installationsordners installiert ist.

Die allgemeine Syntax des **nlserver**-Tools lautet wie folgt:

**nlserver `<command>` `<command arguments>`**

Um eine Liste der verfügbaren Module zu erhalten, verwenden Sie den Befehl **nlserver**.

Die verfügbaren Module werden in der folgenden Tabelle aufgeführt:

| Befehl | Beschreibung |
|---|---|
| aliasCleansing | Standardisieren von Auflistungswerten |
| billing | Senden des Systemaktivitätsberichts an billing@neolane.net |
| cleanup | Bereinigen der Datenbank: Löscht veraltete Daten aus der Datenbank und führt eine Aktualisierung der vom Datenbank-Engine-Optimizer verwendeten Statistiken durch. |
| Konfiguration | Ändern der Server-Konfiguration |
| Export | In Befehlszeile exportieren: sendet ein in der Adobe Campaign-Client-Konsole erstelltes Exportmodell an die Befehlszeile |
| DateiKonvertieren | Konvertieren einer Datei mit festgelegter Größe |
| importieren | In Befehlszeile importieren: sendet ein in der Adobe Campaign-Client-Konsole erstelltes Importmodell an die Befehlszeile. |
| inMail | Analysator eingehender Nachrichten |
| InstallSetup | Verfügbarkeit der Kundeninstallationsdatei |
| JavaScript | Ausführen von JavaScript-Skripten mit Zugriff auf SOAP-APIs. |
| job | Befehlszeilenverarbeitung |
| Fusionieren | Formularzusammenführung |
| Mid-Sourcing | Abruf von Versandinformationen im Mid-Sourcing-Modus |
| überwachen | XML-Anzeige des Status von Serverprozessen und geplanten Aufgaben nach Instanz. |
| mta | Hauptagenten-Übertragungsnachricht |
| Packstück | Importieren oder Exportieren von Entitätspaketdateien |
| pumpen | Anzeigen des Status von Serverprozessen |
| Prepareda | Versandaktion vorbereiten |
| Neustart | Teilweiser Neustart des Servers |
| runwf | Ausführung einer Workflow-Instanz |
| Abschalten | Vollständiges Herunterfahren des Systems |
| sms | SMS-Benachrichtigungsverarbeitung |
| SQL | Ausführung von SQL-Scripts |
| start | Zusätzliche Starts |
| Bundesland | Führt Statistiken über MTA-Verbindungen |
| Stoppen | Teilweise Abschalten des Systems |
| submitda | Übermitteln eines Versands |
| syslogd | Log- und Spurenschreibserver |
| tracking | Analyse und Abruf von Trackinglogs |
| trackingLog | Trackinglog-Schreib- und Löschserver |
| Wachhund | Instanz starten und überwachen |
| Web | Anwendungsserver (HTTP und SOAP) |
| wfserver | Workflow-Server |

>[!IMPORTANT]
>
>Es gibt noch ein letztes Modul: das mit dem Anwendungs-Server verknüpfte Tracking- und Relais-Modul, das aus Leistungsgründen über native Mechanismen über eine dynamische Bibliothek in einen Apache- oder IIS-Webserver integriert wird. Es gibt keinen Adobe Campaign-Befehl, mit dem Sie dieses Modul starten oder verwalten können. Sie müssen daher die Befehle des Webservers selbst verwenden.

Die Modulverwendung und die Syntax ihrer Parameter werden mit dem folgenden Befehl angezeigt: **nlserver `[module]` -?**

Beispiel:

**nlserver config -?**

```
Usage: nlserver [-verbose:<verbose mode>] [-?|h|H] [-version] [-noconsole]
 [-tracefile:<file>] [-tracefilter:<[type|!type],...>]
 [-instance:<instance>] [-low] [-high] [-queryplans] [-detach]
 [-internalpassword:<[password/newpassword]>] [-postupgrade]
 [-nogenschema] [-force] [-allinstances]
 [-addinstance:<instance/DNS masks[/language]>]
 [-setdblogin:<[dbms:]account[:database][/password]@server>]
 [-monoinstance]
 [-addtrackinginstance:<instance/masks DNS[/databaseId/[/language[/password]]]>]
 [-trackingpassword:<[password][/newpassword]>]
 [-setproxy:<protocol/server:port[/login]>] [-reload]
 [-applyxsl:<schema/file.xsl>] [-filter:<file>]
 [-setactivationkey:<activation key>]
 [-getactivationkey:<client identifier>]
-verbose : verbose mode
-? : display this help message
-version : display version number
-noconsole : no longer display logs and traces on the console
-tracefile : name of trace file to be generated (without extension)
-tracefilter : filter for the traces to be generated e.g.: wdbc,soap,!xtkquery.
-instance : instance to be used (default instance if this option is not present).
-low : start up with low priority
-high : start up with high priority (not recommended)
-queryplans : generate traces with the execution plans of SQL queries.
-detach : detaches the process from its parent (internal option)
-internalpassword : changes the password of the server internal account.
-postupgrade : updates the database following upgrade to a higher version. 
-nogenschema : does not recompute the schemas during database update
-force : updates the database even if this has already been done with the current build 
-allinstances : updates the database over all configured instances
-addinstance : adds a new instance.
-setdblogin : sets the parameters for connection to the database of an instance. The DBMS can be 'oracle', 'postgresql', 'mssql' or 'odbc' (default=postgresql)
-monoinstance : initializes for a single instance ().
-addtrackinginstance : adds a new tracking instance.
-trackingpassword : changes the tracking password of an instance
-setproxy : sets the parameters for connection to a proxy server. The protocol can be 'http', 'https' or 'all'.
-reload : asks the server to reload the configuration of the instances. 
-applyxsl : applies an XSL stylesheet to all entities of a schema. 
-filter : applies the XTK filter contained in the file during loading of the schema entities.
-setactivationkey : sets the activation key
```
