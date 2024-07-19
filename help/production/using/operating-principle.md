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
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '506'
ht-degree: 13%

---

# Grundprinzip{#operating-principle}



Technisch betrachtet basiert die Adobe Campaign-Plattform auf mehreren Modulen.

Es gibt viele Adobe Campaign-Module. Einige werden kontinuierlich ausgeführt, während andere gelegentlich gestartet werden, um administrative Aufgaben auszuführen (z. B. zur Konfiguration der Datenbankverbindung) oder um eine wiederkehrende Aufgabe auszuführen (z. B. Konsolidierung von Tracking-Informationen).

Es gibt drei Typen von Adobe Campaign-Modulen:

* Module mit Mehrfach-Instanzen: Für alle Instanzen wird ein einzelner Prozess ausgeführt. Dies gilt für die folgenden Module: **web**, **syslogd**, **trackinglogd** und **watchdog** (Aktivitäten aus der Datei **config-default.xml**).
* Module mit Einfach-Instanz: Für die einzelnen Instanzen wird jeweils ein Prozess ausgeführt. Dies gilt für die folgenden Module: **mta**, **wfserver**, **inMail**, **sms** und **stat** (Aktivitäten aus der Datei **config-`<instance>`.xml**).
* Dienstprogrammmodule: Hierbei handelt es sich um Module, die gelegentlich ausgeführt werden, um gelegentliche oder wiederkehrende Vorgänge auszuführen (**cleanup**, **config**, Herunterladen von Trackinglogs usw.).

Die Modulverwaltung erfolgt mithilfe des Befehlszeilenwerkzeugs **nlserver**, das im Ordner **bin** des Installationsordners installiert ist.

Die allgemeine Syntax des Tools **nlserver** lautet wie folgt:

**nlserver `<command>``<command arguments>`**

Verwenden Sie für die Liste der verfügbaren Module den Befehl **nlserver** .

Die verfügbaren Module werden in der folgenden Tabelle beschrieben:

| Befehl | Beschreibung |
|---|---|
| aliasCleansing | Standardisierung der Auflistungswerte |
| billing | Senden des Systemaktivitätsberichts an billing@neolane.net |
| cleanup | Datenbank bereinigen: Löscht veraltete Daten aus der Datenbank und führt eine Aktualisierung der vom Datenbankmodul-Optimierer verwendeten Statistiken durch. |
| config | Ändern der Serverkonfiguration |
| export | In Befehlszeile exportieren: sendet an die Befehlszeile ein Exportmodell, das in der Adobe Campaign-Clientkonsole erstellt wurde. |
| fileconvert | Datei mit festgelegter Größe konvertieren |
| importieren | Import in Befehlszeile: sendet an die Befehlszeile ein Importmodell, das in der Adobe Campaign-Clientkonsole erstellt wurde. |
| inMail | Analyse eingehender Nachrichten |
| installsetup | Verfügbarkeit der Installationsdatei des Kunden |
| JavaScript | Ausführen von JavaScript-Skripten mit Zugriff auf SOAP APIs. |
| job | Befehlszeilenverarbeitung |
| merge | Formular-Zusammenführung |
| midSourcing | Abruf der Versandinformationen im Mid-Sourcing-Modus |
| überwachen | XML-Darstellung des Status von Serverprozessen und geplanten Aufgaben nach Instanz. |
| mta | Hauptübermittlungsnachricht für Agenten |
| package | Entitätspaket-Dateien importieren oder exportieren |
| pdump | Anzeigen des Serverprozessstatus |
| Prepareda | Versandaktion vorbereiten |
| Neustart | Teilweise Neustart des Servers |
| runwf | Ausführung einer Workflow-Instanz |
| Herunterfahren | Vollständiger Systemausfall |
| sms | SMS-Benachrichtigungsverarbeitung |
| sql | Ausführung von SQL-Scripts |
| start | Weitere Starts |
| stat | Führt Statistiken über MTA-Verbindungen |
| stop | Teilweise Herunterfahren des Systems |
| submitda | Senden einer Versandaktion |
| syslogd | Protokollierungs- und Ablaufverfolgungsserver |
| tracking | Trackinglogs konsolidieren und abrufen |
| trackinglogd | Tracking von Protokollschreibungs- und Bereinigungs-Server |
| watchdog | Start- und Überwachungsinstanz |
| Web | Anwendungsserver (HTTP und SOAP) |
| wfserver | Workflow-Server |

>[!IMPORTANT]
>
>Es gibt ein letztes Modul: das Tracking- und Relais-Modul, das mit dem Anwendungsserver verknüpft ist und der Leistung halber über native Mechanismen über eine dynamische Bibliothek in einen Apache- oder IIS-Webserver integriert wird. Es gibt keinen Adobe Campaign-Befehl, mit dem Sie dieses Modul starten oder verwalten können. Daher müssen Sie die Befehle des Webservers selbst verwenden.

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
