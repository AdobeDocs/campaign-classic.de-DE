---
title: Grundprinzip
seo-title: Grundprinzip
description: Grundprinzip
seo-description: null
page-status-flag: never-activated
uuid: a15929ca-5b1f-499a-a883-43fd0a318c98
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: production-procedures
discoiquuid: 5e9c17ad-14d2-4173-9fc9-0e48a21426c8
translation-type: tm+mt
source-git-commit: 849e1ebf14f707d9e86c5a152de978acb6f1cb35
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 4%

---


# Grundprinzip{#operating-principle}

Technisch gesehen basiert die Adobe Campaign-Plattform auf mehreren Modulen.

Es gibt viele Adobe Campaign-Module. Einige werden kontinuierlich ausgeführt, während andere gelegentlich gestartet werden, um administrative Aufgaben auszuführen (z. B. zum Konfigurieren der Datenbankverbindung) oder um eine wiederkehrende Aufgabe auszuführen (z. B. zum Konsolidieren von Verfolgungsinformationen).

Es gibt drei Typen von Adobe Campaign-Modulen:

* Module mit mehreren Instanzen: für alle Instanzen wird ein einzelner Prozess ausgeführt. Dies gilt für die folgenden Module: **web**, **syslogd**, **trackinglogd** und **watchdog** (Aktivitäten aus der Datei **config-default.xml** ).
* Instanzmodule: pro Instanz ein Prozess ausgeführt wird. Dies gilt für die folgenden Module: **mta**, **wfserver**, **inMail**, **sms** und **stat** (Aktivitäten aus der **`<instance>`** Datei &quot;config-.xml&quot;).
* Dienstprogrammmodule: Hierbei handelt es sich um Module, die gelegentlich ausgeführt werden, um gelegentliche oder wiederkehrende Vorgänge durchzuführen (**Bereinigung**, **Konfiguration**, Herunterladen von Trackinglogs usw.).

Die Modulverwaltung wird mithilfe des Befehlszeilenwerkzeugs nlserver **durchgeführt, der im Ordner &quot;** bin **** &quot;des Installationsordners installiert ist.

Die allgemeine Syntax des **nlserver** -Tools lautet wie folgt:

**nlserver `<command>``<command arguments>`**

Für die Liste der verfügbaren Module verwenden Sie den **Befehl nlserver** .

Die verfügbaren Module sind in der folgenden Tabelle aufgeführt:

| Befehl | Beschreibung  |
|---|---|
| aliasCleansing | Standardisierung der Werte für die Auflistung |
| billing | Systembericht zur Aktivität senden an billing@neolane.net |
| cleanup | Datenbereingung der Datenbank: löscht veraltete Daten aus der Datenbank und führt eine Aktualisierung der vom Datenbank-Engine-Optimierer verwendeten Statistiken durch. |
| config | Serverkonfiguration ändern |
| Copybase | Kopie einer Datenbank |
| export | Exportieren in die Befehlszeile: ermöglicht Ihnen, ein in der Adobe Campaign-Client-Konsole erstelltes Exportmodell an die Befehlszeile zu senden |
| fileconvert | Konvertieren einer Datei mit festgelegter Größe |
| importieren | In Befehlszeile importieren: ermöglicht Ihnen, ein in der Adobe Campaign-Client-Konsole erstelltes Importmodell an die Befehlszeile zu senden. |
| inMail | Inbound Mail Analyzer |
| installsetup | Verfügbarkeit der Installationsdatei des Kunden |
| javascript | Ausführen von JavaScript-Skripten mit Zugriff auf SOAP-APIs. |
| job | Befehlszeilenverarbeitung |
| zusammenführen | Formularzusammenführung |
| midSourcing | Wiederherstellung der Informationen zum Versand im Mid-Sourcing-Modus |
| monitor | XML-Anzeige des Status von Serverprozessen und geplanten Aufgaben nach Instanz. |
| mta | Hauptübermittlungsnachricht des Agenten |
| Paket | Importieren oder Exportieren von Entitätspaket-Dateien |
| pdump | Anzeigen von Serverprozessstatus |
| Prepareda | Vorbereiten einer Versand-Aktion |
| starten | Teilweise Neustart des Servers |
| runwf | Ausführung einer Workflow-Instanz |
| shutdown | Vollständiger Systemausfall |
| sms | Verarbeitung von SMS-Benachrichtigungen |
| sql | SQL-Skriptausführung |
| start | Zusätzliche Beginn |
| stat | Pflege der MTA-Verbindungsstatistiken |
| stop | Teilweise Systemabschaltung |
| submitda | Übermitteln einer Versand-Aktion |
| syslogd | Schreibserver protokollieren und verfolgen |
| tracking | Konsolidieren und Abrufen von Trackinglogs |
| trackinglogd | Verfolgen des Schreibens und Bereinigen von Protokollen |
| watchdog | Start- und Überwachungsinstanz |
| web | Anwendungsserver (HTTP und SOAP) |
| wfserver | Workflow-Server |

>[!IMPORTANT]
>
>Es gibt ein letztes Modul: das mit dem Anwendungsserver verknüpfte Tracking- und Relaismodul, das aus Leistungsgründen über native Mechanismen in einen Apache- oder IIS-Webserver über eine dynamische Bibliothek integriert wird. Es gibt keinen Adobe Campaign-Befehl, mit dem Sie dieses Modul verwalten oder Beginn ausführen können. Daher müssen Sie die Befehle des Webservers selbst verwenden.

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
-monoinstance : initialises for a single instance ().
-addtrackinginstance : adds a new tracking instance.
-trackingpassword : changes the tracking password of an instance
-setproxy : sets the parameters for connection to a proxy server. The protocol can be 'http', 'https' or 'all'.
-reload : asks the server to reload the configuration of the instances. 
-applyxsl : applies an XSL stylesheet to all entities of a schema. 
-filter : applies the XTK filter contained in the file during loading of the schema entities.
-setactivationkey : sets the activation key
```

