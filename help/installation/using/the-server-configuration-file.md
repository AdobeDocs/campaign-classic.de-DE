---
product: campaign
title: Die Server-Konfigurationsdatei
description: Die Server-Konfigurationsdatei
feature: Installation, Instance Settings
audience: installation
content-type: reference
topic-tags: appendices
exl-id: 70cd6a4b-c839-4bd9-b9a7-5a12e59c0cbf
source-git-commit: f032ed3bdc0b402c8281bc34e6cb29f3c575aaf9
workflow-type: tm+mt
source-wordcount: '8066'
ht-degree: 6%

---

# Die Server-Konfigurationsdatei{#the-server-configuration-file}

Die Gesamtkonfiguration von Adobe Campaign wird in der Datei **serverConf.xml** definiert, die sich im Verzeichnis **conf** des Installationsverzeichnisses befindet. In diesem Abschnitt werden alle Knoten und Parameter der Datei **serverConf.xml** aufgelistet.

>[!NOTE]
>
>Server-seitige Konfigurationen können von Adobe nur für Bereitstellungen durchgeführt werden, die von Adobe gehostet werden. Weitere Informationen zu den verschiedenen Bereitstellungen finden Sie im Abschnitt [Hosting](../../installation/using/hosting-models.md) oder auf [dieser Seite](../../installation/using/capability-matrix.md). Die Installations- und Konfigurationsschritte für gehostete und Hybridmodelle werden in diesem [Abschnitt](../../installation/using/hosting-models.md) beschrieben.

Die ersten Parameter befinden sich im Knoten **shared**. Diese beziehen sich auf die Instanz. Sie werden möglicherweise von allen nlserver-Befehlen (nlserver web, nlserver wfserver usw.) verwendet. Die anderen Abschnitte beziehen sich auf einen bestimmten nlserver-Unterbefehl.

**Freigegebene Parameter**

* [Authentifizierung](#authentication)
* [dataStore](#datastore)
* [dnsConfig](#dnsconfig)
* [ausführen](#exec)
* [htmlToPDF](#htmltopdf)
* [IMS](#ims)
* [JavaScript](#javascript)
* [MailExchange](#mailexchanger)
* [Modul](#module)
* [Überwachung](#monitoring)
* [ooconv](#ooconv)
* [proxyConfig](#proxyconfig)
* [ThreadPool](#threadpool)
* [urlPermission](#urlpermission)
* [cusHeaders](#cusheaders)
* [xtkJobs](#xtkjobs)

**Andere Parameter**

* [Archivierung](#archiving)
* [inMail](#inmail)
* [Interaktionen](#interactiond)
* [mta](#mta)
* [NMAC](#nmac)
* [Pipeline](#pipelined)
* [Reparatur](#repair)
* [Sicherheitszone](#securityzone)
* [sms](#sms)
* [Bundesland](#stat)
* [syslogd](#syslogd)
* [tracking](#tracking)
* [trackingLog](#trackinglogd)
* [Web](#web)
* [wfserver](#wfserver)

## Authentifizierung {#authentication}

Im Folgenden finden Sie die verschiedenen Parameter des **Authentifizierungsknotens**:

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschreibung </th> 
   <th> Typ </th> 
   <th> Standardwert </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> checkIPConsistent<br /> </td> 
   <td> Prüfung der IP-Adresse aktivieren.<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> defaultMode<br /> </td> 
   <td> Standard-Identifizierungsmodus.<br /> </td> 
   <td> String <br /> </td> 
   <td> 'nl'<br /> </td> 
  </tr> 
  <tr> 
   <td> longSessionTimeOutSec<br /> </td> 
   <td> Timeout langer Sitzungen in Sekunden.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1296000<br /> </td> 
  </tr> 
  <tr> 
   <td> securityTimeOutSec<br /> </td> 
   <td> Zeitüberschreitung des Sicherheits-Tokens in Sekunden.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
  <tr> 
   <td> sessionCacheSec<br /> </td> 
   <td> Aufbewahrungsfrist im Cache: Sitzungsinformationen im Cache in Sekunden.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 600 <br /> </td> 
  </tr> 
  <tr> 
   <td> sessionTimeOutSec<br /> </td> 
   <td> Sitzungs-Timeout in Sekunden.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
 </tbody> 
</table>

### XTK {#xtk}

Im Folgenden finden Sie die verschiedenen Parameter **Knotens „Authentifizierung > XTK**:

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschreibung </th> 
   <th> Typ </th> 
   <th> Standardwert </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> internalPassword<br /> </td> 
   <td> Passwort des internen Kontos.<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> internalSecurityZone<br /> </td> 
   <td> Sicherheitszone des internen Kontos: Zulässige Zone für das interne Konto.<br /> </td> 
   <td> String <br /> </td> 
   <td> 'LAN'<br /> </td> 
  </tr> 
 </tbody> 
</table>

## dataStore {#datastore}

Im Folgenden finden Sie die verschiedenen Parameter **Knotens „dataStore**. Hier werden die Datenquellen des Servers definiert.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschreibung </th> 
   <th> Typ </th> 
   <th> Standardwert </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> exportDirectory<br /> </td> 
   <td> Exportverzeichnis: Pfad des Zielverzeichnisses für die exportierten Daten.<br /> </td> 
   <td> String <br /> </td> 
   <td> '$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/export/' <br /> </td> 
  </tr> 
  <tr> 
   <td> extraSandboxDirectories<br /> </td> 
   <td> Zusätzliche Sandbox-Ordner: Andere in die Sandbox einzufügende Pfade (durch Kommata getrennt).<br /> </td> 
   <td> String <br /> </td> 
   <td> '/home/customers/,/sftp/' <br /> </td> 
  </tr> 
  <tr> 
   <td> formCacheTimeToLive<br /> </td> 
   <td> Gültigkeitsdauer des Formular-Caches: Zeitüberschreitung in Sekunden, nach der ein Eintrag im Cache ungültig wird. O bedeutet, dass Cache-Einträge nur zum Zeitpunkt der Veröffentlichung aktualisiert werden.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 600 <br /> </td> 
  </tr> 
  <tr> 
   <td> Hosts<br /> </td> 
   <td> DNS-Masken: Liste der von dieser Instanz bereitgestellten DNS-Masken (durch Kommata getrennt, Platzhalter * und ? Patterns).<br /> </td> 
   <td> String <br /> </td> 
   <td> "<br /> </td> 
  </tr> 
  <tr> 
   <td> interactionCacheTimeToLive<br /> </td> 
   <td> Gültigkeitsdauer des Interaktions-JSSP-Cache: Zeitüberschreitung in Sekunden, nach der ein Cache-Eintrag ungültig wird. Ein negativer Wert bedeutet, dass der Cache immer invalidiert wird. '0', leere oder ungültige Werte werden als 60.<br /> betrachtet </td> 
   <td> Lang<br /> </td> 
   <td> 300 <br /> </td> 
  </tr> 
  <tr> 
   <td> lang<br /> </td> 
   <td> Sprache der Instanz (Auflistung). Mögliche Werte sind 'fr_FR' (Français), 'en_GB' (Englisch (UK)), 'en_US' (Englisch (US)), 'de_DE' (Deutsch) und 'ja_JP' (Japanisch).<br /> </td> 
   <td> String <br /> </td> 
   <td> 'en_US'<br /> </td> 
  </tr> 
  <tr> 
   <td> uploadDirectory<br /> </td> 
   <td> Upload-Ordner: Pfad des Zielverzeichnisses für die hochgeladenen Daten.<br /> </td> 
   <td> String <br /> </td> 
   <td> '$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/upload/' <br /> </td> 
  </tr> 
  <tr> 
   <td> uploadAllowlist<br /> </td> 
   <td> Dateien, die hochgeladen werden dürfen, durch ",“ getrennt Die Zeichenfolge muss ein gültiger regulärer Java-Ausdruck sein. Siehe <a href="file-res-management.md" target="_blank">Einschränken von hochladbaren Dateien</a>.<br /> </td> 
   <td> String <br /> </td> 
   <td> '.+'-<br /> </td> 
  </tr> 
  <tr> 
   <td> useVault<br /> </td> 
   <td> Geheime Daten in Vault speichern: Hashicorp Vault verwenden.<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> vaultSecretPath<br /> </td> 
   <td> Geheimpfad in Vault<br /> </td> 
   <td> String <br /> </td> 
   <td> '/v1/secret/campaign/'<br /> </td> 
  </tr> 
  <tr> 
   <td> vaultTokenPath<br /> </td> 
   <td> Lokaler Pfad der Datei, die das Vault-Token enthält. $(HOME) kann auf diesem Pfad verwendet werden (aber keine anderen Umgebungsvariablen).<br /> </td> 
   <td> String <br /> </td> 
   <td> '$(HOME)/.vaultToken'<br /> </td> 
  </tr> 
  <tr> 
   <td> vaultUrl<br /> </td> 
   <td> Hashicorp Vault URL-<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> viewCacheTimeToLive<br /> </td> 
   <td> Gültigkeitszeitraum des Ansichtscache: Zeitüberschreitung in Sekunden, nach der ein Cache-Eintrag ungültig wird. Ein negativer Wert bedeutet, dass der Cache immer invalidiert wird. '0', leere oder ungültige Werte werden als 60.<br /> betrachtet </td> 
   <td> Lang<br /> </td> 
   <td> 600 <br /> </td> 
  </tr> 
  <tr> 
   <td> workingDirectory<br /> </td> 
   <td> XPath des Arbeitsverzeichnisses.<br /> </td> 
   <td> String <br /> </td> 
   <td> workingDirectory : Pfad des Arbeitsverzeichnisses. Standard: '$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/workspace/'<br /> </td> 
  </tr> 
 </tbody> 
</table>

### proxyAdjust {#proxyadjust}

Im Folgenden finden Sie die verschiedenen Parameter **Knotens „dataStore > proxyAdjust**. URLs, die mit dem regulären Ausdruck übereinstimmen, werden basierend auf der in urlBase definierten URL neu generiert.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschreibung </th> 
   <th> Typ </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> urlBase<br /> </td> 
   <td> Basis zur Erzeugung externer URLs. z. B.: https://server.domain.com<br /> </td> 
   <td> String <br /> </td> 
  </tr> 
  <tr> 
   <td> urlRegEx<br /> </td> 
   <td> Regulärer Ausdruck, der URLs zuordnet Beispiel: http://server\.lan\.net.*<br /> </td> 
   <td> String <br /> </td> 
  </tr> 
 </tbody> 
</table>

### dataSource {#datasource}

Im Folgenden finden Sie die verschiedenen Parameter des **dataStore > dataSource**-Knotens.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschreibung </th> 
   <th> Typ </th> 
   <th> Standardwert </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Name<br /> </td> 
   <td> Name von Data Source<br /> </td> 
   <td> String <br /> </td> 
   <td> Standard<br /> </td> 
  </tr> 
 </tbody> 
</table>

Konfigurieren **im Knoten dataStore > dataSource > dbcnx** die Verbindungseinstellungen:

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschreibung </th> 
   <th> Typ </th> 
   <th> Standardwert<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> NChar<br /> </td> 
   <td> Unicode-Speicherung<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> dbSchema<br /> </td> 
   <td> Workspace<br /> </td> 
   <td> String <br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Verschlüsselte <br /> </td> 
   <td> Verschlüsseltes Passwort<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> anmelden<br /> </td> 
   <td> Konto<br /> </td> 
   <td> String <br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Passwort<br /> </td> 
   <td> Passwort<br /> </td> 
   <td> String <br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Anbieter<br /> </td> 
   <td> Typ (Auflistung). Mögliche Werte sind 'Oracle', 'MSSQL' (Microsoft SQL Server), 'PostgreSQL' (PostgreSQL), 'Teradata', 'MySQL', 'Netezza', 'AsterData', 'SAPHANA' (SAP HANA), 'RedShift' (Amazon Redshift), 'ODBC' (ODBC (Sybase ASE, Sybase IQ)), 'Relay' (HTTP-Weiterleitung auf Remote-Datenbank).<br /> </td> 
   <td> String <br /> </td> 
   <td> 'Oracle'<br /> </td> 
  </tr> 
  <tr> 
   <td> Server<br /> </td> 
   <td> Server<br /> </td> 
   <td> String <br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Zeitzone<br /> </td> 
   <td> Zeitzone: siehe <a href="../../installation/using/time-zone-management.md" target="_blank">Zeitzonenverwaltung</a>.<br /> </td> 
   <td> String <br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> unicodeData<br /> </td> 
   <td> Unicode-Daten in der Datenbank<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> useTimestampTZ<br /> </td> 
   <td> Datumsfelder mit Zeitzone: siehe <a href="../../installation/using/time-zone-management.md" target="_blank">Verwaltung von Zeitzonen</a>.<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

Konfigurieren **im Knoten dataStore > dataSource > sqlParams** die SQL-Parameter:

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschreibung </th> 
   <th> Typ </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> funcPrefix<br /> </td> 
   <td> Präfix für Funktionen<br /> </td> 
   <td> String <br /> </td> 
  </tr> 
 </tbody> 
</table>

Konfigurieren **im Knoten dataStore > dataSource > Pool** die Parameter des zugeordneten Verbindungspools:

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschreibung </th> 
   <th> Typ </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> aliveTestDelaySec<br /> </td> 
   <td> Zeitspanne zwischen den Gültigkeitsprüfungen der Verbindung.<br /> </td> 
   <td> Kurz<br /> </td> 
  </tr> 
  <tr> 
   <td> freeCnx<br /> </td> 
   <td> Anzahl der im Pool beibehaltenen freien Verbindungen.<br /> </td> 
   <td> Kurz<br /> </td> 
  </tr> 
  <tr> 
   <td> maxCnx<br /> </td> 
   <td> Maximale Anzahl zulässiger Verbindungen, bevor eine neue Verbindung verweigert wird. Siehe diese <a href="https://helpx.adobe.com/campaign/kb/how-to-increase-the-maximum-number-of-database-connections-from-.html">Technote</a>.<br /> </td> 
   <td> Kurz<br /> </td> 
  </tr> 
  <tr> 
   <td> maxIdleDelaySec<br /> </td> 
   <td> Maximale Inaktivitätsdauer der Verbindung 0 bedeutet Standardwert.<br /> </td> 
   <td> Kurz<br /> </td> 
  </tr> 
 </tbody> 
</table>

### virtualDir {#virtualdir}

Im Folgenden finden Sie die verschiedenen Parameter **Knotens „dataStore > virtualDir**. Dies ist die Konfiguration des virtuellen Verzeichnisses für die Zuordnung von echten Verzeichnissen.

Weitere Informationen finden Sie unter &quot;[ öffentlicher Ressourcen](file-res-management.md).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschreibung </th> 
   <th> Typ </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Name<br /> </td> 
   <td> Name des virtuellen Verzeichnisses <br /> </td> 
   <td> String <br /> </td> 
  </tr> 
  <tr> 
   <td> Pfad<br /> </td> 
   <td> Vollständiger Pfad des tatsächlichen Verzeichnisses<br /> </td> 
   <td> String <br /> </td> 
  </tr> 
 </tbody> 
</table>

Hier finden Sie die Standardkonfiguration:

```
<virtualDir name="images" path="$(XTK_INSTALL_DIR)/var/res/img/"/>
<virtualDir name="formCache" path="$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/formCache/"/>
<virtualDir name="publicFileRes" path="$(XTK_INSTALL_DIR)/var/res/$(INSTANCE_NAME)"/>
```

### preprocessCommand {#preprocesscommand}

Im Folgenden finden Sie die verschiedenen Parameter des **dataStore > preprocessCommand**-Knotens. Dies sind die zulässigen Befehle für die Vorab-Bearbeitung der Workflow-Aktivität „Datei laden“.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschreibung </th> 
   <th> Typ </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Befehl<br /> </td> 
   <td> Befehlszeilen-<br /> </td> 
   <td> String <br /> </td> 
  </tr> 
  <tr> 
   <td> Bezeichnung<br /> </td> 
   <td> Befehlszeilenbezeichnung<br /> </td> 
   <td> String <br /> </td> 
  </tr> 
  <tr> 
   <td> Name<br /> </td> 
   <td> Name der Befehlszeile<br /> </td> 
   <td> String <br /> </td> 
  </tr> 
 </tbody> 
</table>

Hier finden Sie die Standardkonfiguration:

```
<preprocessCommand command="" label="None" name="none"/>
<preprocessCommand command="zcat &quot;$fileName&quot;" label="Decompression" name="zcat"/><preprocessCommand command="gpg --decrypt &quot;$fileName&quot;" label="Decrypt" name="gpg"/>
```

## dnsConfig {#dnsconfig}

Im Folgenden finden Sie die verschiedenen Parameter des **dnsConfig**-Knotens (DNS-Konfiguration).

Weitere Informationen finden Sie in diesem [Abschnitt](../../installation/using/configuring-campaign-server.md).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschreibung </th> 
   <th> Typ </th> 
   <th> Standardwert </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> localDomain<br /> </td> 
   <td> Domain-Name: Standard-Domain-Name. Wird vom SMTP-HELO-Befehl verwendet. Verwendet standardmäßig die Netzwerkparameter der ersten unter Windows deklarierten Netzwerkschnittstelle oder parst die Datei file/etc/resolv.conf unter Linux (Domain oder Sucheintrag). <br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> nameServers<br /> </td> 
   <td> DNS-Server: Kommagetrennte Liste von Domain Name Servers (DNS). Siehe den Hinweis unten.<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> Wiederholen<br /> </td> 
   <td> Anzahl weiterer Versuche für eine DNS-Abfrage.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> Zeitüberschreitung<br /> </td> 
   <td> Timeout in Millisekunden für eine DNS-Abfrage.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 5 000 <br /> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Hinweis zu **nameSevers**: nutzt standardmäßig das Netzwerk
>Parameter der ersten unter Windows deklarierten Netzwerkschnittstelle
>nicht in UNIX definiert. Definiert die Domain Name Servers (DNS)
>wird vom MTA verwendet, um den Mail Exchanger für zu deklarieren.
>Eine Domain.
>
>Wenn dieser Wert nicht definiert ist, sucht der MTA diese Informationen in der Host-Netzwerkkonfiguration. Wenn mehrere DNS möglich sind, müssen die verschiedenen DNS-Adressen durch ein Komma getrennt werden (Beispiel: 212.155.207.1,212.155.207.2). Wenn Ihr Versand-Server über mehrere Netzwerkschnittstellen verfügt, ist die vom MTA verwendete DNS-Liste die erste. In diesem Fall wird empfohlen, den Parameter **nameServer** anzugeben, um Unklarheiten zu vermeiden.

>[!CAUTION]
>
>Wenn Ihre Netzwerk-Host-Konfiguration DHCP verwendet, findet der MTA die von DHCP bereitgestellte DNS-Liste nicht. In diesem Fall wird empfohlen, die DNS-Liste in den Netzwerkparametern der Windows-Systemsteuerung anzugeben.

## ausführen {#exec}

Im Folgenden finden Sie die verschiedenen Parameter des **exec**-Knotens (Befehlsausführung).

Weitere Informationen finden Sie unter [Einschränken autorisierter externer Befehle](../../installation/using/configuring-campaign-server.md#restricting-authorized-external-commands).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschreibung </th> 
   <th> Typ </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> blacklistFile<br /> </td> 
   <td> Pfad zur Datei mit den Befehlen, die der Zulassungsliste hinzugefügt werden sollen. <br /> </td> 
   <td> String <br /> </td> 
  </tr> 
  <tr> 
   <td> Benutzer<br /> </td> 
   <td> Führt Befehle als anderer Benutzer aus.<br /> </td> 
   <td> String <br /> </td> 
  </tr> 
 </tbody> 
</table>

## htmlToPDF {#htmltopdf}

Im Folgenden finden Sie die verschiedenen Parameter des **htmlToPdf**-Knotens. Dies ist die Konfiguration des Service zum Konvertieren von Web-Seiten in PDF-Dokumente.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschreibung </th> 
   <th> Typ </th> 
   <th> Standardwert </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Befehl<br /> </td> 
   <td> In die Befehlszeile einzugebender Befehl, um die Konvertierung zu starten (im „other“-Modus).<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessCount<br /> </td> 
   <td> Max. Anzahl der Konvertierungsprozesse, die gleichzeitig auf einem Computer zulässig sind.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> <br /> </td> 
   <td> Für die Konvertierung zu verwendendes Tool Mögliche Werte sind: phantomjs, wkhtmltopdf, other, disabled<br /> </td> 
   <td> String <br /> </td> 
   <td> 'PhantomJS'-<br /> </td> 
  </tr> 
  <tr> 
   <td> Zeitüberschreitung<br /> </td> 
   <td> Zeitüberschreitung für eine Konvertierung: Maximale Konvertierungszeit in Sekunden. Bei Überschreitung dieses Grenzwerts wird der Konvertierungsprozess angehalten und ein Fehler ausgegeben.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 120 <br /> </td> 
  </tr> 
  <tr> 
   <td> Verbose<br /> </td> 
   <td> Verbose-Modus: Im Verbose-Modus starten, um mögliche Fehler zu diagnostizieren.<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> waitTime<br /> </td> 
   <td> Verzögerung beim Warten auf einen Prozess: Verzögerung in Sekunden, wenn alle Prozesse gleichzeitig verwendet werden, und beim Warten darauf, dass ein Prozess freigegeben wird. Wenn diese Verzögerung überschritten wird, wird die Konvertierung angehalten und ein Fehler ausgegeben. <br /> </td> 
   <td> Lang<br /> </td> 
   <td> 15 <br /> </td> 
  </tr> 
 </tbody> 
</table>

Beispiel für PhantomJS:

```
phantomjs - -ignore-ssl-errors=true '$(XTK_INSTALL_DIR)/bin/htmlToPdf.js' '-out:{outPdf}' '-post:{postFile}' '-url:{originUrl}' -sessiontoken:{sessiontoken} -format:{format} -orientation:{orientation} -marginTop:{marginTop} -marginLeft:{marginLeft} -marginRight:{marginRight} -marginBottom:{marginBottom}
```

## IMS {#ims}

Im Folgenden finden Sie die verschiedenen Parameter des **ims**-Knotens. Dies ist die Konfiguration für die Verbindung von Campaign mit einem anderen Service unter Verwendung von [IMS](../../integrations/using/about-adobe-id.md).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschreibung </th> 
   <th> Typ </th> 
   <th> Standardwert </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> authIMSClientId<br /> </td> 
   <td> Client-ID<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSClientSecret<br /> </td> 
   <td> Geheimer Schlüssel (mit AES verschlüsselt)<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSCode<br /> </td> 
   <td> Autorisierungs-Code (mit AES verschlüsselt)<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSEndpoint<br /> </td> 
   <td> IMS-Server-URL<br /> </td> 
   <td> String <br /> </td> 
   <td> 'https://ims-na1.adobelogin.com'<br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSTAClientId<br /> </td> 
   <td> Client-ID des technischen Kontos<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSTAClientSecret<br /> </td> 
   <td> Geheimschlüssel des technischen Kontos (mit AES verschlüsselt)<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSTAId<br /> </td> 
   <td> ID des technischen Kontos<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSTAPrivateKey<br /> </td> 
   <td> Privater Schlüssel des technischen Kontos (mit AES verschlüsselt)<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

## JavaScript {#javascript}

Im Folgenden finden Sie die verschiedenen Parameter des **javascript**-Knotens. Dies ist die Konfiguration des JavaScript-Interpreters.

Weitere Informationen finden Sie in der [Reporting-Dokumentation](../../reporting/using/actions-on-reports.md#memory-allocation).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschreibung </th> 
   <th> Typ </th> 
   <th> Standardwert </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> maxMB<br /> </td> 
   <td> Maximale Größe in Megabyte vor Ausführung der Garbage Collection.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 512 <br /> </td> 
  </tr> 
  <tr> 
   <td> stackSizeKB<br /> </td> 
   <td> Größe jedes Stapelblocks in Kilobyte. Dies ist ein Optimierungsparameter für die Speicherverwaltung, den die meisten Benutzer nicht anpassen sollten. <br /> </td> 
   <td> Lang<br /> </td> 
   <td> 8<br /> </td> 
  </tr> 
 </tbody> 
</table>

## MailExchange {#mailexchanger}

Im Folgenden finden Sie die verschiedenen Parameter des **mailExchanger**-Knotens. Dies ist die Konfiguration des SMTP-Servers.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschreibung </th> 
   <th> Typ </th> 
   <th> Standardwert </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> mxAddress<br /> </td> 
   <td> SMTP-Server: IP-Adresse des SMTP-Servers für die Übertragung von E-Mails.<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> mxPort<br /> </td> 
   <td> TCP-Port des SMTP-Servers, der für die E-Mail-Übertragung verwendet wird.<br /> </td> 
   <td> String <br /> </td> 
   <td> 25 <br /> </td> 
  </tr> 
 </tbody> 
</table>

## Modul {#module}

Im Folgenden finden Sie die verschiedenen Parameter des **module**-Knotens. Dies ist die Konfiguration für das Modul Namespaces-Einschränkungen xtk.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschreibung </th> 
   <th> Typ </th> 
   <th> Standardwert </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> defaultNameSpace<br /> </td> 
   <td> Beim Erstellen einer neuen Entität verwendeter Standard-Namespace.<br /> </td> 
   <td> String <br /> </td> 
   <td> 'cus'<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Überwachung {#monitoring}

Im Folgenden finden Sie die verschiedenen Parameter **Knotens &quot;**&quot;. Dies ist die Konfiguration des Monitoring-Services.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschreibung </th> 
   <th> Typ </th> 
   <th> Standardwert </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> maxPreparingJobsSec<br /> </td> 
   <td> Maximale Vorbereitungszeit: Dauer in Sekunden, nach der eine Versandaktion nicht mehr in Vorbereitung sein darf.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 3 600 <br /> </td> 
  </tr> 
  <tr> 
   <td> unixScript<br /> </td> 
   <td> Unix-Skript, das vom Überwachungsdienst ausgeführt wird.<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> winScript<br /> </td> 
   <td> Windows-Skript, das vom Überwachungsdienst ausgeführt werden soll.<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

## ooconv {#ooconv}

Im Folgenden finden Sie die verschiedenen Parameter des **ooconv**-Knotens. Dies ist die Konfiguration des Dokumentenkonvertierungs-Servers.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschreibung </th> 
   <th> Typ </th> 
   <th> Standardwert </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> maxConversions<br /> </td> 
   <td> Maximale Anzahl an Konvertierungen, die ein OpenOffice-Server ausführen darf. Ist diese Anzahl überschritten, wird der Server neu gestartet.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1.000 <br /> </td> 
  </tr> 
  <tr> 
   <td> maxServerIdleSec<br /> </td> 
   <td> Maximale Inaktivitätsdauer des OpenOffice-Servers vor dem erzwungenen Schließen.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 7 200 <br /> </td> 
  </tr> 
  <tr> 
   <td> portRange<br /> </td> 
   <td> Port-Intervall, auf dem die OpenOffice-Server lauschen.<br /> </td> 
   <td> String <br /> </td> 
   <td> 8101-8110 <br /> </td> 
  </tr> 
  <tr> 
   <td> URL<br /> </td> 
   <td> URL des Dokumentenkonvertierungs-Servers.<br /> </td> 
   <td> String <br /> </td> 
   <td> 'http://localhost:8080/nl/jsp/ooconv.jsp'<br /> </td> 
  </tr> 
 </tbody> 
</table>

## proxyConfig {#proxyconfig}

Im Folgenden finden Sie die verschiedenen Parameter **Knotens „proxyConfig**. Dies ist die Konfiguration der Proxy-Parameter.

Weitere Informationen finden Sie unter [Proxy-Verbindungskonfiguration](file-res-management.md).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschreibung </th> 
   <th> Typ </th> 
   <th> Standardwert </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> aktiviert<br /> </td> 
   <td> Proxy-Server verwenden.<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> überschreiben<br /> </td> 
   <td> Ausnahmen: Liste der Adressen, für die Proxy-Parameter ignoriert werden sollen.<br /> </td> 
   <td> String <br /> </td> 
   <td> 'localhost*'-<br /> </td> 
  </tr> 
  <tr> 
   <td> useSingleProxy<br /> </td> 
   <td> Eindeutiger Proxy-Server: Verwenden Sie dieselbe Konfiguration für alle Proxy-Typen.<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

### HTTP-Proxy/Sicherer Proxy {#http-proxy---secure-proxy-}

Konfigurieren **im Knoten proxyConfig > HTTP-Proxy / Sicherer Proxy** die folgenden Parameter.

Weitere Informationen finden Sie unter [Proxy-Verbindungskonfiguration](file-res-management.md).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschreibung </th> 
   <th> Typ </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Adresse<br /> </td> 
   <td> Adresse des Proxy-Servers<br /> </td> 
   <td> String <br /> </td> 
  </tr> 
  <tr> 
   <td> anmelden<br /> </td> 
   <td> Melden Sie sich für die Verbindung zum Proxy-Server an<br /> </td> 
   <td> String <br /> </td> 
  </tr> 
  <tr> 
   <td> Passwort<br /> </td> 
   <td> Kennwort für die Verbindung mit dem Proxy-Server<br /> </td> 
   <td> String <br /> </td> 
  </tr> 
  <tr> 
   <td> Port<br /> </td> 
   <td> Proxy-Server-Port<br /> </td> 
   <td> Kurz<br /> </td> 
  </tr> 
 </tbody> 
</table>

## ThreadPool {#threadpool}

Im Folgenden finden Sie die verschiedenen Parameter **Knotens &quot;**&quot;.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschreibung </th> 
   <th> Typ </th> 
   <th> Standardwert </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> maxThreadCount<br /> </td> 
   <td> Maximale Anzahl an Threads im Pool. <br /> </td> 
   <td> Lang<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## urlPermission {#urlpermission}

Im Folgenden finden Sie die verschiedenen Parameter des **urlPermission**-Knotens. Dies ist die Liste der URLs, auf die der JavaScript-Code zugreifen kann.

Liste der Domains und regulären Ausdrücke, die angeben, ob eine im JavaScript-Code gefundene URL vom Adobe Campaign-Server verwendet werden kann oder nicht.

Wenn die URL nicht gefunden werden kann, wird die Standardaktion gemäß dem angegebenen Standardmodus ausgeführt.

Weitere Informationen finden Sie unter [Schutz ausgehender Verbindungen](../../installation/using/configuring-campaign-server.md#url-permissions).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschreibung </th> 
   <th> Typ </th> 
   <th> Standardwert </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Aktion<br /> </td> 
   <td> Standardaktion, wenn sich die URL nicht in der autorisierten Liste befindet (Auflistung). Mögliche Werte sind „ignore“ (autorisieren ohne Warnmeldung, hierfür muss der Schutz deaktiviert werden), „warn“ (autorisieren und eine Warnmeldung ausgeben) und „deny“ (Zugriff auf die URL verweigern).<br /> </td> 
   <td> String <br /> </td> 
   <td> Ablehnen<br /> </td> 
  </tr> 
  <tr> 
   <td> debugTrace<br /> </td> 
   <td> Debug-Spur des URL-Auswahlmechanismus: Gibt zusätzliche Meldungen während des URL-Verifizierungsprozesses aus.<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

## cusHeaders {#cusheaders}

Mit diesem Knoten können Sie bestimmte Kopfzeilen zu Anfragen hinzufügen, die beim Hochladen einer Datei von einem externen Server ausgeführt werden. Content Delivery Networks (CND) kann eine bestimmte Kopfzeile anfordern, um dem Anfragenden zu vertrauen. Diese Kopfzeilen können verwendet werden, um die Vertrauensstellung bei Campaign-Anfragen zu verbessern, insbesondere beim Herunterladen personalisierter Dokumente für jeden Empfänger während des Versandausführungsschritts. Eine hohe Anzahl von Anfragen zum Herunterladen von Ressourcen kann als DOS-Angriff interpretiert werden. dnsPattern ermöglicht es Ihnen, bestimmte Kopfzeilennamen und Werte für verschiedene CDNs basierend auf ihrem Domain-Namen festzulegen.

```
  <!-- List of custom headers added to request. 
         -->
    <cusHeaders>

    <!-- Pattern of DNS name or domain 
         value :  dnsPattern: All or part of the URL's domain to verify, * is a wild card Default:  -->
      <dnsPattern value="">

    <!-- Header Name and Value 
           headerName :  Header Name 
           headerValue :  Header Value -->
        <headerDef headerName="" headerValue=""/>

      </dnsPattern>

    </cusHeaders> 
```

### url {#url}

Fügen Sie für jede URL einen **url**-Knoten mit den folgenden Parametern hinzu:

Weitere Informationen finden Sie unter [Schutz ausgehender Verbindungen](../../installation/using/configuring-campaign-server.md#url-permissions).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschreibung </th> 
   <th> Typ </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> dnsSuffix<br /> </td> 
   <td> Von der URL betroffener Domain-Name oder übergeordnete Domain: Die zu verifizierende Domain der URL ganz oder teilweise, um die Verifizierung zu beschleunigen. Die URL wird nur dann in Bezug auf den regulären Ausdruck überprüft, wenn die Domain dsnSuffix enthält.<br /> </td> 
   <td> String <br /> </td> 
  </tr> 
  <tr> 
   <td> urlRegEx<br /> </td> 
   <td> Regulärer Ausdruck zur Verfeinerung der Validierung von URLs, die zu dieser Domain gehören: Regulärer Ausdruck, den die URL überprüfen muss, falls er dnsSuffix entspricht.<br /> </td> 
   <td> String <br /> </td> 
  </tr> 
 </tbody> 
</table>

Wenn ein Datensatz das **dnsSuffix**, aber nicht **urlRegEx** erfüllt, wird der folgende Datensatz untersucht.

Um beispielsweise den Zugriff auf alle URLs der Domain business.com zu autorisieren, können zwei Datensätze definiert werden:

dnsSuffix=„business.com“ urlRegEx=&quot;http://.&#42;&quot;

and

dnsSuffix=„business.com“ urlRegEx=&quot;https://.&#42;&quot;

Hier finden Sie die Standardkonfiguration:

```
<url dnsSuffix="api.omniture.com" urlRegEx="https://api.omniture.com/genesis/i/3.1.*"   />
<url dnsSuffix="omniture.com" urlRegEx="https://api[1-5].omniture.com/genesis/i/3.1.*"  />
<url dnsSuffix="marketing.adobe.com"                     urlRegEx="https://.*"                                    />
<url dnsSuffix="fcm.googleapis.com"                      urlRegEx="https://fcm.googleapis.com/fcm/send.*"       />
<url dnsSuffix="graph.facebook.com"                      urlRegEx="https://.*"                                    />
<url dnsSuffix="api.line.me"                             urlRegEx="https://api.line.me/.*"                      />
<url dnsSuffix="api.twitter.com"                         urlRegEx="https://api.twitter.com/1.1.*"              />
<url dnsSuffix="adobeid-na1.services.adobe.com"          urlRegEx="https://.*"                                    />
<url dnsSuffix="adobeid-na1-stg1.services.adobe.com"     urlRegEx="https://.*"                                    />
<url dnsSuffix="localhost"                               urlRegEx="http://localhost:8080/nms/jsp/.*"              />
<url dnsSuffix="localhost"                               urlRegEx="http://localhost:8080/nl/jsp/.*"               />
<url dnsSuffix="localhost"                               urlRegEx="http://localhost:8080/xtk/jsp/.*"              />
```

## xtkJobs {#xtkjobs}

Im Folgenden finden Sie die verschiedenen Parameter des **xtkJobs**-Knotens. Dies ist die Konfiguration der Server-Aufträge.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschreibung </th> 
   <th> Typ </th> 
   <th> Standardwert </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> purgeLogsPeriod<br /> </td> 
   <td> Speicherstatus-Aktualisierungszeitraum der Serververarbeitung (in ms).<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 500 <br /> </td> 
  </tr> 
 </tbody> 
</table>

## Archivierung {#archiving}

Im Folgenden finden Sie die verschiedenen Parameter **Knotens &quot;**&quot;. Dies ist die Konfiguration der im Hintergrund ausgeführten Archivierungsvorgänge.

Weitere Informationen finden Sie unter [Aktivieren der E-Mail-Archivierung (On-Premise)](../../installation/using/email-archiving.md#activating-email-archiving--on-premise-).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschreibung </th> 
   <th> Typ </th> 
   <th> Standardwert </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> acquetlimit<br /> </td> 
   <td> Anzahl der gleichzeitig zu bearbeitenden EMLs<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 100 <br /> </td> 
  </tr> 
  <tr> 
   <td> archivingType<br /> </td> 
   <td> Archivierungsstrategie der gesendeten Nachrichten (Auflistung). Mögliche Werte sind '0' (keine Archivierung) und '1' (Übertragung der Archivierung gesendeter Nachrichten an einen SMTP-Server).<br /> </td> 
   <td> byte<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> args<br /> </td> 
   <td> Startparameter<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Automatischer Start<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> compressBatchSize<br /> </td> 
   <td> Größe eines komprimierten Archivs: Maximale Anzahl von Dateien in einem komprimierten Archiv.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 10000<br /> </td> 
  </tr> 
  <tr> 
   <td> compressionFormat<br /> </td> 
   <td> Bei der Archivierung verwendetes Komprimierungsformat (Auflistung). Mögliche Werte sind '0' (keine Komprimierung) und '1' (gesendete Nachrichten im ZIP-Format komprimieren).<br /> </td> 
   <td> byte<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> expirationDelay<br /> </td> 
   <td> Verzögerung vor der automatischen Archivierung nicht verarbeiteter E-Mails: Anzahl der Tage vor der Archivierung nicht verarbeiteter E-Mails.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID der JavaScript, die beim Starten des Prozesses ausgeführt werden soll.<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Warnhinweis bezüglich des Speicherverbrauchs: Warnhinweis bezüglich der RAM-Menge, die von einem bestimmten Prozess verbraucht wird (in MB)<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1 800 <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Warnung bezüglich des Speicherverbrauchs: Warnung bezüglich des RAM-Verbrauchs (in MB) durch einen bestimmten Prozess.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1 600 <br /> </td> 
  </tr> 
  <tr> 
   <td> pollDelay<br /> </td> 
   <td> Intervall in Sekunden zwischen den einzelnen Aktualisierungsereignissen.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 60 <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Tageszeit, zu der der Prozess automatisch neu gestartet wird. Siehe <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatischer Prozessneustart</a>.<br /> </td> 
   <td> String <br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> purgeArchivesDelay<br /> </td> 
   <td> Anzahl Tage vor der Löschung der nicht verarbeiteten E-Mails.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 7<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priorität beim Start. Module mit niedriger Priorität werden zuerst gestartet und zuletzt angehalten. Das Syslogd-Modul muss daher die Priorität 0.<br /> haben </td> 
   <td> Kurz<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> smtpBccAddress<br /> </td> 
   <td> Ziel der Zielarchivierung<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> smtpEnableTLS<br /> </td> 
   <td> SMTPS-Unterstützung aktivieren : Aktiviert den Versand von E-Mails im abgesicherten Modus (STARTTLS/SMTPS), wenn er vom Remote-Server unterstützt wird.<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> smtpNbConnection<br /> </td> 
   <td> Anzahl der Verbindungen mit dem SMTP-Archivierungsserver.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> smtpRelayAddress<br /> </td> 
   <td> Kommagetrennte Liste der DNS-Namen oder IP-Adressen der zu verwendenden SMTP-Relais. <br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> smtpRelayPort<br /> </td> 
   <td> IP-Port des SMTP-Servers.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 25 <br /> </td> 
  </tr> 
 </tbody> 
</table>

## inMail {#inmail}

Im Folgenden finden Sie die verschiedenen Parameter des **inMail**-Knotens. Dies ist die Konfiguration des Moduls zur Verwaltung eingehender E-Mails.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschreibung </th> 
   <th> Typ </th> 
   <th> Standardwert </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> Startparameter<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Automatischer Start<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> checkInstanceName<br /> </td> 
   <td> Instanzname überprüfen: Wenn „true“, muss der in den Message-ID-Headern enthaltene Name der Adobe Campaign-Instanz mit dem der aktuellen Instanz übereinstimmen. <br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> Ja<br /> </td> 
  </tr> 
  <tr> 
   <td> defaultForwardAddress<br /> </td> 
   <td> Weiterleitungsadresse: Standardmäßige E-Mail-Weiterleitungsadresse, die nicht von einer Regel verarbeitet wird. <br /> </td> 
   <td> String <br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> errorForwardAddress<br /> </td> 
   <td> Fehleradresse: Standardadresse für die Übertragung ungültiger E-Mails (fehlerhafte MIME-Kodierung). <br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> ignoreSize<br /> </td> 
   <td> Nachrichtengröße ignorieren: wird verwendet, um die Größe einer von POP3-Servern zurückgegebenen Nachricht zu ignorieren. In diesem Fall erwartet das Modul ein ".“ am Ende der Nachrichten. <br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> inMailPeriodSec<br /> </td> 
   <td> Nachrichtenlesezeitraum: Abrufintervall der Nachrichtenwarteschlange.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID der JavaScript, die beim Starten des Prozesses ausgeführt werden soll.<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxBroadLog<br /> </td> 
   <td> Maximale Anzahl an zu aktualisierenden Protokollen: Legt die maximale Anzahl an Protokollmeldungen fest, die im Arbeitsspeicher behalten werden sollen, bevor die Datenbank aktualisiert wird.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 20<br /> </td> 
  </tr> 
  <tr> 
   <td> maxMsgPerSession<br /> </td> 
   <td> Maximale Anzahl an Nachrichten, die während einer POP3-Sitzung gelesen werden können.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 200 <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Warnhinweis bezüglich des Speicherverbrauchs: Warnhinweis bezüglich der RAM-Menge, die von einem bestimmten Prozess verbraucht wird (in MB)<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1 800 <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Warnung bezüglich des Speicherverbrauchs: Warnung bezüglich des RAM-Verbrauchs (in MB) durch einen bestimmten Prozess.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1 600 <br /> </td> 
  </tr> 
  <tr> 
   <td> maxSessionTTLSec<br /> </td> 
   <td> Sitzungsdauer: Maximale Dauer einer Nachrichtenverarbeitungssitzung.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 100 <br /> </td> 
  </tr> 
  <tr> 
   <td> popMailPeriodSec<br /> </td> 
   <td> POP3-Abrufintervall<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 300 <br /> </td> 
  </tr> 
  <tr> 
   <td> popQueueSize<br /> </td> 
   <td> Warteschlangengröße der gelesenen Nachrichten<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 100 <br /> </td> 
  </tr> 
  <tr> 
   <td> popTimeoutSec<br /> </td> 
   <td> Timeout der POP3-Serververbindung <br /> </td> 
   <td> Lang<br /> </td> 
   <td> 300 <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Tageszeit, zu der der Prozess automatisch neu gestartet wird. Siehe <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatischer Prozessneustart</a>.<br /> </td> 
   <td> String <br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> reloadPeriodSec<br /> </td> 
   <td> Intervall, in der die Konten neu geladen werden, die abgefragt werden sollen.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 600 <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priorität beim Start. Module mit niedriger Priorität werden zuerst gestartet und zuletzt angehalten. Das Syslogd-Modul muss daher die Priorität 0.<br /> haben </td> 
   <td> Kurz<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

### msgDump {#msgdump}

Konfigurieren **im Knoten inMail > msgDump** die folgenden Parameter. Dies ist die Konfiguration des Speicherauszugs verarbeiteter Nachrichten.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschreibung </th> 
   <th> Typ </th> 
   <th> Standardwert </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Speicherauszug<br /> </td> 
   <td> Speichert alle eingehenden Nachrichten im Textformat. <br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> msgPath<br /> </td> 
   <td> Speicherpfad der Nachrichten.<br /> </td> 
   <td> String <br /> </td> 
   <td> '/tmp/inMail'<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Interaktionen {#interactiond}

Im Folgenden finden Sie die verschiedenen Parameter des **interactiond**-Knotens. Dies ist die Konfiguration des Schreib-Daemon für eingehende Interaction-Ereignisse.

Weitere Informationen finden Sie unter [Interaction - Datenpuffer](../../installation/using/interaction-data-buffer.md).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschreibung </th> 
   <th> Typ </th> 
   <th> Standardwert </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> Startparameter<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Automatischer Start<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> callDataSize<br /> </td> 
   <td> Max. Anzahl der Zeichen, die im gemeinsamen Speicher für Aufrufdaten gespeichert sind.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID der JavaScript, die beim Starten des Prozesses ausgeführt werden soll<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Warnhinweis bezüglich des Speicherverbrauchs: Warnhinweis bezüglich der RAM-Menge, die von einem bestimmten Prozess verbraucht wird (in MB)<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1 800 <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Warnung bezüglich des Speicherverbrauchs: Warnung bezüglich des RAM-Verbrauchs (in MB) durch einen bestimmten Prozess.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1 600 <br /> </td> 
  </tr> 
  <tr> 
   <td> maxSharedEntries<br /> </td> 
   <td> Max. Anzahl der Ereignisse, die im gemeinsamen Speicher gespeichert sind.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 25000<br /> </td> 
  </tr> 
  <tr> 
   <td> nextOffersSize<br /> </td> 
   <td> Maximale Anzahl an geeigneten Angeboten, die direkt nach den Vorschlägen sortiert und für Statistiken gespeichert werden.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Tageszeit, zu der der Prozess automatisch neu gestartet wird. Siehe <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatischer Prozessneustart</a>.<br /> </td> 
   <td> String <br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priorität beim Start. Module mit niedriger Priorität werden zuerst gestartet und zuletzt angehalten. Das Syslogd-Modul muss daher die Priorität 0.<br /> haben </td> 
   <td> Kurz<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> statsPeriod<br /> </td> 
   <td> Aggregationsdauer in Sekunden für die Antwortzeit-Statistiken. 0 bedeutet, dass die Speicherung der Statistiken deaktiviert wurde.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 600 <br /> </td> 
  </tr> 
  <tr> 
   <td> targetKeySize<br /> </td> 
   <td> Max. Anzahl der Zeichen, die im gemeinsamen Speicher zur Identifizierung von Personen gespeichert sind.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 16 <br /> </td> 
  </tr> 
 </tbody> 
</table>

## mta {#mta}

Im Folgenden finden Sie die verschiedenen Parameter des **mta**-Knotens. Dies ist die Konfiguration der Versandagenten.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschreibung </th> 
   <th> Typ </th> 
   <th> Standardwert </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> Startparameter<br /> </td> 
   <td> String <br /> </td> 
   <td> '-tracefilter:nlmta' <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Automatischer Start<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> dataLogPath<br /> </td> 
   <td> Speicherpfad der gesendeten E-Mails: Wenn nicht leer, der Pfad, in dem alle Quelldateien der gesendeten E-Mails gespeichert werden. <br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> debugPath<br /> </td> 
   <td> Dump-Verzeichnis: Wenn nicht leer, kopieren Sie MIME-Umschläge gesendeter E-Mail-Nachrichten in dieses Verzeichnis. Wird zur Fehlerbehebung verwendet. <br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> dnsRequestLogDelayMs<br /> </td> 
   <td> Verzögerung bei DNS-Abfrageprotokollen: Zeit in Millisekunden, um die Protokolle anzuzeigen.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> errorPeriodSec<br /> </td> 
   <td> Häufigkeit der Fehlerstatistiken: Zeit zwischen der Erstellung von Statistiken und der Speicherung in der Datenbank. <br /> </td> 
   <td> Lang<br /> </td> 
   <td> 300 <br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID der JavaScript, die beim Starten des Prozesses ausgeführt werden soll.<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> logEmailErrors<br /> </td> 
   <td> Erzeugt Fehlerstatistiken und speichert sie in der Datenbank.<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> Ja<br /> </td> 
  </tr> 
  <tr> 
   <td> logLevel<br /> </td> 
   <td> Zeigt die Ebene der Protokollmeldungen an. Dringlichkeitsstufe der in die Datenbank geschriebenen Protokolle Vom MTA erzeugte Lognachrichten werden nicht immer in die Datenbank geschrieben. Mit diesem Parameter können Sie festlegen, ab welcher Ebene eine Nachricht in die Datenbank geschrieben werden soll. Wenn Sie Ebene 2 definieren, werden auch Nachrichten der Ebenen 1 und 0 geschrieben, während bei der Definition der Ebene 1 nur Nachrichten der Ebenen 1 und 0 geschrieben werden. Mögliche Werte sind: 0 (Fehler), 1 (Warnung), 2 (Info)<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> maxMemoryMb<br /> </td> 
   <td> Maximale Speichergröße (in MB), die ein MTA-Prozess verwenden kann. Bei Überschreitung dieser Grenze wird der Prozess neu gestartet, sodass der von ihm verwendete Speicher für das System freigegeben wird.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1 024 <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Warnhinweis bezüglich des Speicherverbrauchs: Warnhinweis bezüglich der RAM-Menge, die von einem bestimmten Prozess verbraucht wird (in MB)<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1 800 <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Warnung bezüglich des Speicherverbrauchs: Warnung bezüglich des RAM-Verbrauchs (in MB) durch einen bestimmten Prozess.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1 600 <br /> </td> 
  </tr> 
  <tr> 
   <td> minConnectionsToLog<br /> </td> 
   <td> Zu berücksichtigender Verbindungsschwellenwert Fehlerstatistiken werden für einen bestimmten Pfad nicht erzeugt, wenn die Gesamtzahl an Verbindungen seit der von errorPeriodSec bestimmten Dauer streng kleiner als diese Schwelle ist.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 100 <br /> </td> 
  </tr> 
  <tr> 
   <td> minErrorsToLog<br /> </td> 
   <td> Zu berücksichtigender Fehlerschwellenwert: Fehlerstatistiken werden für einen bestimmten Pfad nicht erzeugt, wenn die Gesamtzahl an Fehlern seit der von errorPeriodSec bestimmten Dauer streng kleiner als diese Schwelle ist.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> minMessagesToLog<br /> </td> 
   <td> Zu berücksichtigender Nachrichtenschwellenwert Fehlerstatistiken werden für einen bestimmten Pfad nicht generiert, wenn die Gesamtzahl an gesendeten Nachrichten seit der von errorPeriodSec bestimmten Dauer streng kleiner als diese Schwelle ist.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1.000 <br /> </td> 
  </tr> 
  <tr> 
   <td> notifRelay<br /> </td> 
   <td> Benachrichtigungsrelais: HostName:Port, der zum Weiterleiten von Benachrichtigungen verwendet wird.<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Tageszeit, zu der der Prozess automatisch neu gestartet wird. Siehe <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatischer Prozessneustart</a>.<br /> </td> 
   <td> String <br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> purgeDataLogDelay<br /> </td> 
   <td> Verzögerung vor dem Löschen archivierter E-Mails: Anzahl der Tage, nach denen archivierte E-Mails in dem in dataLogPath angegebenen Verzeichnis gelöscht werden.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 15 <br /> </td> 
  </tr> 
  <tr> 
   <td> retryLostMessages<br /> </td> 
   <td> Verlorene Nachrichten erneut versuchen: Versandkontingente werden erneut versucht, wenn der untergeordnete Prozess tot ist.<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> Ja<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priorität beim Start. Module mit niedriger Priorität werden zuerst gestartet und zuletzt angehalten. Das Syslogd-Modul muss daher die Priorität 0.<br /> haben </td> 
   <td> Kurz<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> signEmailLinks<br /> </td> 
   <td> Aktivieren Sie den Signaturmechanismus. Dies verbessert die Sicherheit beim Tracking von Links in E-Mails.<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> Ja<br /> </td> 
  </tr>
  <tr> 
   <td> statServerAddress<br /> </td> 
   <td> Adresse des Servers der Versandstatistik, angegeben als 
    &lt;DNS oder IP&gt; 
      <code>&lbrack;</code>: 
     &lt;port&gt; 
       <code>&rbrack;</code>. Siehe 
      <a href="../../installation/using/email-deliverability.md#coordinates-of-the-statistics-server" target="_blank">Koordinaten des Statistikservers</a>. 
      <br /> 
     </td> 
   <td> String <br /> </td> 
   <td> Wenn nicht anders angegeben, lautet der Standardport 7777.<br /> </td> 
  </tr> 
  <tr> 
   <td> statServerTLSSupport<br /> </td> 
   <td> TLS nach Domain aktivieren: Aktiviert die per MX konfigurierbare TLS (erfordert einen aktualisierten Statistikserver).<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> wahre <br /> </td> 
  </tr> 
  <!--tr> 
   <td> statServerVersion<br /> </td> 
   <td> Protocol version used: communication protocol version (1 for a v5.11 and 6.0.2 server, 2 for a v6.1 server).<br /> </td> 
   <td> String<br /> </td> 
   <td> If undefined, the latest version is used. <br /> </td> 
  </tr--> 
  <tr> 
   <td> useMomentum<br /> </td> 
   <td> Wenn dies auf „true“ festgelegt ist, verwendet Ihre Instanz den <a href="../../delivery/using/sending-with-enhanced-mta.md" target="_blank">Enhanced MTA</a>.<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> <br /> </td>b 
  </tr>
  <tr> 
   <td> verifyMode<br /> </td> 
   <td> Überprüfungsmodus: Aktiviert den Überprüfungsmodus (keine physische Übertragung von Nachrichten; wird für Simulationen und Tests verwendet).<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> workingPath<br /> </td> 
   <td> Arbeitsverzeichnis : Speicherort der temporären Dateien, die vom MTA zur Kommunikation mit den untergeordneten Prozessen verwendet werden.<br /> </td> 
   <td> String <br /> </td> 
   <td> '$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/mta/' <br /> </td> 
  </tr> 
  <tr> 
   <td> xMailer<br /> </td> 
   <td> X-Mailer-Feld: Wert des Feldes 'X-Mailer' im SMTP-Mail-Header.<br /> </td> 
   <td> String <br /> </td> 
   <td> 'nlserver, Build $(PRODUCT_VERSION)'<br /> </td> 
  </tr>  
 </tbody> 
</table>

### cache {#cache}

Konfigurieren Sie im **cache**-Knoten die folgenden Parameter. Dies ist die Konfiguration des lokalen Datei-Caches.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschreibung </th> 
   <th> Typ </th> 
   <th> Standardwert </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> maxPeriodSec<br /> </td> 
   <td> Wiederverwendet nach: Zeitraum in Sekunden, nach dem die Datei automatisch aus dem Cache gelöscht wird, um Speicher freizugeben.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 244800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSizeOnDiskMb<br /> </td> 
   <td> Maximale Cache-Größe (MB).<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1 024 <br /> </td> 
  </tr> 
  <tr> 
   <td> purgePeriodSec<br /> </td> 
   <td> Bereinigungsfrequenz: Zeitraum in Sekunden zwischen den Ausführungen des Cache-Bereinigungsmechanismus.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 3 600 <br /> </td> 
  </tr> 
 </tbody> 
</table>

### weiterleiten {#relay}

Konfigurieren **im Knoten** mta > relais“ die folgenden Parameter. Dies ist die Konfiguration des Mailservers für den Nachrichtenversand.

Die Liste wird wie eine MX-Liste gehandhabt, die von einer MX-DNS-Abfrage zurückgegeben wird. Normalerweise wird die erste MX verwendet, solange sie verfügbar ist, dann wird die nächste verwendet usw.

Weitere Informationen finden Sie unter [SMTP-](../../installation/using/configuring-campaign-server.md#smtp-relay).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschreibung </th> 
   <th> Typ </th> 
   <th> Standardwert </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Adresse<br /> </td> 
   <td> Kommagetrennte Liste der DNS-Namen oder IP-Adressen der zu verwendenden SMTP-Relais. <br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> Port<br /> </td> 
   <td> IP-Port des SMTP-Servers.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 25 <br /> </td> 
  </tr> 
 </tbody> 
</table>

### Vorlage {#master}

Konfigurieren **im Knoten** mta > master“ die folgenden Parameter. Dies ist die Konfiguration des Haupt-Servers.

Weitere Informationen finden Sie in diesem [Abschnitt](../../installation/using/configuring-campaign-server.md#mta-child-processes).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschreibung </th> 
   <th> Typ </th> 
   <th> Standardwert </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> dataBasePoolPeriodSec<br /> </td> 
   <td> Intervall, in der die zu sendenden Vorgänge aus der Datenbank abgerufen werden Dieser Wert gibt die Abrufintervall der Datenbank an (in Sekunden). Um die Liste der auf einen Versand wartenden Aufträge zu erhalten, fragt der MTA die Datenbank regelmäßig ab. Wenn kein Auftrag wartet, wird der Abfrageintervall durch diesen Wert definiert. Ist andernfalls ein Auftrag auf einen untergeordneten Server übertragen worden, so verkürzt sich diese Abrufdauer automatisch auf eine Sekunde, sodass ein neuer Auftrag schnellstmöglich, d.h. sobald ein untergeordneter Server wieder verfügbar ist, wieder verarbeitet werden kann. Dies bedeutet nicht, dass die Datenbankabfrage jede Sekunde durchgeführt wird, bis ein untergeordneter Server wieder verfügbar ist. Tatsächlich erfolgt ein Datenbankzugriff nur, wenn mindestens ein untergeordneter Server verfügbar wird.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
  <tr> 
   <td> dataBaseRetryDelaySec<br /> </td> 
   <td> Wartezeit nach fehlgeschlagener Datenbankverbindung. Ein Fehler bei der Datenbankverbindung wird normalerweise vom Datenbankserver selbst verursacht. Der Server kann auch z.B. zu Wartungszwecken angehalten werden. Der Parameter DataBaseRetryDelay definiert die Dauer zwischen zwei Verbindungsversuchen im Falle eines Datenbankverbindungsfehlers.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 60 <br /> </td> 
  </tr> 
  <tr> 
   <td> domainKeysReloadPeriodSec<br /> </td> 
   <td> Gültigkeitszeitraum für den Cache privater Schlüssel (DomainKeys). Private Schlüssel, die zum Signieren von E-Mails gemäß der DomainKeys-Empfehlung (http://antispam.yahoo.com/domainkeys) verwendet werden, werden als Optionen in der Datenbank gespeichert. Der Parameter domainKeysReloadPeriodSec definiert, wie viele Sekunden der MTA diese Schlüssel in einem Cache speichern kann. Nach dieser Verzögerung müssen alle Schlüssel aus der Datenbank neu geladen werden.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 600 <br /> </td> 
  </tr> 
  <tr> 
   <td> maxSpareServers<br /> </td> 
   <td> Maximale Anzahl an untergeordneten Servern Stellt die maximale Anzahl an laufenden Servern dar. Es wird empfohlen, diese Zahl auf ein Optimum zu beschränken, das mit den Speicherressourcen des Servers kompatibel ist. Dies kann während eines Versands überprüft werden. Der belegte Speicher sollte ein Drittel des verfügbaren physischen Speichers nicht überschreiten, da andernfalls der Swap verwendet wird. Siehe <a href="../../installation/using/configuring-campaign-server.md#mta-child-processes" target="_blank">Untergeordnete MTA-Prozesse</a>.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> minSpareServers<br /> </td> 
   <td> Minimale Anzahl an untergeordneten Servern Der MTA versucht, mindestens diese Anzahl an Servern am Laufen zu halten. Wenn es weniger sind, werden neue Server jede Sekunde neu gestartet, bis dieser Wert erreicht ist.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> startSpareServers<br /> </td> 
   <td> Anzahl der untergeordneten Server beim Start Die Anzahl der untergeordneten Server wird dynamisch überwacht. Beim Starten des MTAs werden so viele untergeordnete Server erstellt, wie in diesem Wert angegeben. Normalerweise können untergeordnete Server nicht schneller als ein Server pro Sekunde gestartet werden, um Host-Ressourcen zu sparen. Beim Start des MTAs wird diese Einschränkung jedoch aufgehoben, sodass untergeordnete Server so bald wie möglich verfügbar sind.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Kind {#child}

Konfigurieren Sie im Knoten **mta >** untergeordnet“ die folgenden Parameter. Dies ist die Konfiguration untergeordneter Server.

Weitere Informationen finden Sie unter [Optimierung des E-Mail-Versands](../../installation/using/email-deliverability.md#email-sending-optimization).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschreibung </th> 
   <th> Typ </th> 
   <th> Standardwert </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> extraArgs<br /> </td> 
   <td> Optionale <br /> für Befehlszeilenargumente </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> idleChildTimeoutSec<br /> </td> 
   <td> Zeitüberschreitung bis zum Anhalten inaktiver untergeordneter Server. Wenn ein untergeordneter Server länger inaktiv ist als dieser Parameter, wird er automatisch beendet, um Ressourcen freizugeben.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 60 <br /> </td> 
  </tr> 
  <tr> 
   <td> maxAgeSec<br /> </td> 
   <td> Maximale Aufbewahrungsdauer einer Nachricht Wenn eine vorbereitete Nachricht aufgrund einer Drosselung nicht gesendet werden konnte oder keine Verbindung zum Ziel-MTA herstellen konnte, wird die Nachricht abgebrochen und beim nächsten Versuch verarbeitet.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 600 <br /> </td> 
  </tr> 
  <tr> 
   <td> maxGCMConnectPerChild<br /> </td> 
   <td> Maximale Anzahl paralleler HTTP-Anfragen an FCM von jedem untergeordneten Server initiiert.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 8<br /> </td> 
  </tr> 
  <tr> 
   <td> maxMsgPerChild<br /> </td> 
   <td> Maximale Nachrichtenanzahl pro untergeordnetem Server Jedes untergeordnete MTA-Element verarbeitet diese Anzahl von Nachrichten und stirbt. Es ist wichtig, eine Zahl anzugeben, bei der Speicher- oder Ressourcenlecks im MTA harmlos sind (in der Regel einige Tausend). Selbst wenn im MTA-Code keine Speicherlecks bekannt sind, sind die eingebetteten JavaScript- und XSL-Engines nicht vollständig zuverlässig.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 5000000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxWaitingMessages<br /> </td> 
   <td> Ausstehende Nachrichten: Maximale Anzahl von Nachrichten, die im Speicher auf den Versand warten. <br /> </td> 
   <td> Lang<br /> </td> 
   <td> 2.000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxWorkingSetMb<br /> </td> 
   <td> Maximale Speichergröße (in MB), die ein untergeordneter Prozess verwenden kann. Bei Überschreiten dieser Grenze wird der Prozess angehalten, sodass der von ihm verwendete Speicher für das System freigegeben wird. <br /> </td> 
   <td> Lang<br /> </td> 
   <td> 128 <br /> </td> 
  </tr> 
  <tr> 
   <td> soapConnectorTimeoutSec<br /> </td> 
   <td> Timeout (in Sekunden), nach dem eine SOAP-Verbindung für einen Versand-Connector unterbrochen wird.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 600 <br /> </td> 
  </tr> 
  <tr> 
   <td> startWithFirstMX<br /> </td> 
   <td> Beginnen Sie immer mit der höchsten Priorität MX.<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> timeToLive<br /> </td> 
   <td> Maximale Anzahl aufeinander folgender Versuche bei Wiederaufnahme.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 48 <br /> </td> 
  </tr> 
 </tbody> 
</table>

Konfigurieren **im Knoten mta > child > smtp** die folgenden Parameter. Dies ist die Konfiguration von SMTP-Sitzungen.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschreibung </th> 
   <th> Typ </th> 
   <th> Standardwert </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> enableTLS<br /> </td> 
   <td> Aktiviert den E-Mail-Versand im abgesicherten Modus (STARTTLS/SMTPS), wenn er vom Remote-Server unterstützt wird.<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> idleSessionTimeoutSec<br /> </td> 
   <td> Timeout inaktiver Sitzungen Dieser Parameter wird nur verwendet, wenn die Sitzung zur Übertragung mehrerer Nachrichten an eine bestimmte Domain wiederverwendet wird. Wenn der MTA die Nachrichtenübertragung abgeschlossen hat, wird die verwendete SMTP-Sitzung nicht systematisch geschlossen. Wenn eine Nachricht für dieselbe Domain versandbereit ist, wird dieselbe SMTP-Sitzung wiederverwendet und die Sitzung wird daher nicht automatisch geschlossen. Mit dem Parameter IdleSessionTimeout können Sie festlegen, wie lange eine SMTP-Sitzung aktiv bleiben kann, bis eine andere Nachricht angezeigt wird. Nach Ablauf der Dauer wird die Sitzung automatisch geschlossen.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> initialDelaySec<br /> </td> 
   <td> Anfangswartezeit vor einem erneuten Verbindungsversuch. Diese Verzögerung wird bei Verbindungsfehlern verdoppelt.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSessionsPerChild<br /> </td> 
   <td> Maximale Anzahl an SMTP-Sitzungen pro untergeordnetem Server Um eine Nachricht zuzustellen, initiiert der MTA eine SMTP-Verbindung mit dem Empfänger-MTA. Die maximale Anzahl gleichzeitiger und aktiver SMTP-Sitzungen für einen bestimmten untergeordneten Server ist durch diesen Wert begrenzt. Wenn Sie diesen Wert mit maxSpareServers multiplizieren, erhalten Sie die maximale Anzahl an Nachrichten, die gleichzeitig von einem bestimmten untergeordneten Server verarbeitet werden können.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1.000 <br /> </td> 
  </tr> 
 </tbody> 
</table>

Konfigurieren Sie im Knoten **mta > child > smtp > IPAffinity** die folgenden Parameter. Dies ist die Konfiguration der Verwaltung von IP-Adressaffinitäten für optimierten ausgehenden SMTP-Traffic.

Weitere Informationen finden Sie unter [Liste der zu verwendenden IP](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use) und [Verwalten des ausgehenden SMTP-Traffics mit Affinitäten](../../installation/using/configuring-campaign-server.md#managing-outbound-smtp-traffic-with-affinities).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschreibung </th> 
   <th> Typ </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> localDomain<br /> </td> 
   <td> Domain-Name: Der IP-Adresse entsprechender lokaler Domain-Name. Wird beim Ausgeben eines SMTP-HELO-Befehls verwendet.<br /> </td> 
   <td> String <br /> </td> 
  </tr> 
  <tr> 
   <td> Name<br /> </td> 
   <td> Logischer Name: Namen, die von Benutzern mit der Affinität verknüpft werden. Namen werden durch Semikolons getrennt<br /> </td> 
   <td> String <br /> </td> 
  </tr> 
 </tbody> 
</table>

Konfigurieren **im Knoten mta > child > smtp > IP** die folgenden Parameter.

Weitere Informationen finden Sie unter [Liste der zu verwendenden IP](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschreibung </th> 
   <th> Typ </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Adresse<br /> </td> 
   <td> Zugeordnete physische Adresse. Beispiel: „192.168.0.1“<br /> </td> 
   <td> String <br /> </td> 
  </tr> 
  <tr> 
   <td> publicId<br /> </td> 
   <td> Kennung der zugeordneten öffentlichen Adresse. Wird als Schlüssel für den Statistikserver verwendet. Muss numerisch sein. Siehe diesen <a href="../../installation/using/email-deliverability.md#managing-ip-addresses">Abschnitt</a>.<br /> </td> 
   <td> Lang<br /> </td> 
  </tr> 
  <tr> 
   <td> Gewicht<br /> </td> 
   <td> Gibt die Verwendungsfrequenz dieser IP-Adresse im Vergleich zu anderen IP-Adressen an (höhere Gewichtung führt zu höheren Frequenzen).<br /> </td> 
   <td> Lang<br /> </td> 
  </tr> 
  <tr> 
   <td> includeDomains<br /> </td> 
   <td> Liste der einzuschließenden Domain-Masken, durch Kommata getrennt.<br /> </td> 
   <td> String <br /> </td> 
  </tr> 
  <tr> 
   <td> excludeDomains<br /> </td> 
   <td> Maske für auszuschließende Domains, durch Kommata getrennt<br /> </td> 
   <td> String <br /> </td> 
  </tr> 
  <tr> 
   <td> heloHost<br /> </td> 
   <td> Der IP-Adresse zugeordnete Computername. Wird beim Ausgeben eines SMTP-HELO-Befehls verwendet.<br /> </td> 
   <td> String <br /> </td> 
  </tr> 
 </tbody> 
</table>

## NMAC {#nmac}

Im Folgenden finden Sie die verschiedenen Parameter des **nmac**-Knotens. Dies ist die Konfiguration von für Push-Benachrichtigungs-Sendungen.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschreibung </th> 
   <th> Typ </th> 
   <th> Standardwert </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> useHTTPProxy<br /> </td> 
   <td> Verwenden Sie den in shared/proxyHTTP definierten HTTP-Proxy. <br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

### weiterleiten {#relay-1}

Im Folgenden finden Sie die verschiedenen Parameter des **nmac >**. Dadurch wird die Verwendung eines Relais für den Nachrichtenversand konfiguriert (iOS-HTTP2-Connector).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschreibung </th> 
   <th> Typ </th> 
   <th> Standardwert </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Adresse<br /> </td> 
   <td> DNS-Adresse oder Name des zu verwendenden Relais. <br /> </td> 
   <td> String <br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Port<br /> </td> 
   <td> Relais-Port<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 443 <br /> </td> 
  </tr> 
  <tr> 
   <td> trustedCertsChain<br /> </td> 
   <td> Zertifikatskette (PEM-Datei). Nützlich bei Verwendung eines Pseudo-Servers.<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

## Pipeline {#pipelined}

Im Folgenden finden Sie die verschiedenen Parameter **Knotens &quot;**&quot;. Dies ist die Konfiguration des Ereignisverarbeitungsmoduls für Pipeline-Services.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschreibung </th> 
   <th> Typ </th> 
   <th> Standardwert </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> appName<br /> </td> 
   <td> Name der Anwendung, der bei Speicherung des öffentlichen Schlüssels in der Developer Connection generiert wird. <br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> args<br /> </td> 
   <td> Startparameter<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authGatewayEndpoint<br /> </td> 
   <td> URL zum Abrufen eines Gateway-Tokens.<br /> </td> 
   <td> String <br /> </td> 
   <td> 'https://api.omniture.com' <br /> </td> 
  </tr> 
  <tr> 
   <td> authPrivateKey<br /> </td> 
   <td> Privater Schlüssel für den Erhalt der Token (in AES mit der Option XtkKey verschlüsselt).<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Automatischer <br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> disableAuth<br /> </td> 
   <td> Authentifizierung deaktivieren: Verbindung zu Pipeline Services ohne Authentifizierung herstellen. <br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> DiscoverPipelineEndpoint<br /> </td> 
   <td> URL zum Auffinden der Pipeline-Services-URL.<br /> </td> 
   <td> String <br /> </td> 
   <td> 'https://producer-pipeline-pnw.adobe.net'<br /> </td> 
  </tr> 
  <tr> 
   <td> dumpStatePeriodSec<br /> </td> 
   <td> Speicherzeitraum für Status: Häufigkeit, mit der die internen Prozessinformationen in einer Datei gespeichert werden. Inaktiv, wenn 0. <br /> </td> 
   <td> Lang<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> forcedPipelineEndpoint<br /> </td> 
   <td> Listen-URL: Erzwingt die Listen-URL der Pipeline Services. <br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID der JavaScript, die beim Starten des Prozesses ausgeführt werden soll.<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Warnhinweis bezüglich des Speicherverbrauchs: Warnhinweis bezüglich der RAM-Menge, die von einem bestimmten Prozess verbraucht wird (in MB)<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1 800 <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Warnung bezüglich des Speicherverbrauchs: Warnung bezüglich des RAM-Verbrauchs (in MB) durch einen bestimmten Prozess.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1 600 <br /> </td> 
  </tr> 
  <tr> 
   <td> monitorServerPort<br /> </td> 
   <td> Status-Server-Port: HTTP-Server-Port, über den Sie den Status des Prozesses abfragen können. Inaktiv bei 0,<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 7 781 <br /> </td> 
  </tr> 
  <tr> 
   <td> pointerFlushMessageCount<br /> </td> 
   <td> Der Zeiger wird jedes Mal in der Datenbank gespeichert, wenn diese Anzahl von Nachrichten verarbeitet wird.<br /> </td> 
   <td> <br /> </td> 
   <td> 1.000 <br /> </td> 
  </tr> 
  <tr> 
   <td> pointerFlushPeriodSec<br /> </td> 
   <td> Zeitspanne vor Speicherung des Zeigers: Der Zeiger wird mindestens einmal während dieses Zeitraums in der Datenbank gespeichert (nützlich bei geringer Aktivität).<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Tageszeit, zu der der Prozess automatisch neu gestartet wird. Siehe <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatischer Prozessneustart</a>.<br /> </td> 
   <td> String <br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> processingJSThreads<br /> </td> 
   <td> Anzahl der Threads für die Ereignisverarbeitung mit einem personalisierten JavaScript-Connector.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> processingThreads<br /> </td> 
   <td> Anzahl an Threads für die Ereignisverarbeitung.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> retryPeriodSec<br /> </td> 
   <td> Intervall zwischen Verarbeitungsversuchen im Fall eines Fehlers.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
  <tr> 
   <td> retryValiditySec<br /> </td> 
   <td> Nach diesem Zeitraum abbrechen : Ereignis wird abgebrochen, wenn die Verarbeitung nach diesem Zeitraum noch immer fehlschlägt.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 300 <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priorität beim Start. Module mit niedriger Priorität werden zuerst gestartet und zuletzt angehalten. Das Syslogd-Modul muss daher die Priorität 0.<br /> haben </td> 
   <td> Kurz<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Reparatur {#repair}

Im Folgenden finden Sie die verschiedenen Parameter **Knotens &quot;**&quot;. Dies ist die Konfiguration des Datenbankreparaturmoduls.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschreibung </th> 
   <th> Typ </th> 
   <th> Standardwert </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> replicationActionDelayMin<br /> </td> 
   <td> Reparatur-Modul der Versandaktionen: Verzögerung (in Minuten), nach der die Versandaktionen vom Reparatur-Modul verarbeitet werden können. <br /> </td> 
   <td> Lang<br /> </td> 
   <td> 60 <br /> </td> 
  </tr> 
 </tbody> 
</table>

## Sicherheitszone {#securityzone}

Im Folgenden finden Sie die verschiedenen Parameter des **securityZone**-Knotens.

Weitere Informationen finden Sie unter [ von Sicherheitszonen](../../installation/using/security-zones.md).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschreibung </th> 
   <th> Typ </th> 
   <th> Standardwert </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> allowDebug<br /> </td> 
   <td> Debug-Modus für Webanwendungen zulassen.<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> allowEmptyPassword<br /> </td> 
   <td> Autorisieren Sie den Benutzer, die Anwendung ohne Kennwort zu verwenden.<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> allowHTTP<br /> </td> 
   <td> Verwendung von HTTP bei der Benutzeranmeldung zulassen.<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> allowSQLInjection<br /> </td> 
   <td> Verwendung von SQLDATA in Ausdrücken zulassen.<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> allowUserPassword<br /> </td> 
   <td> Sitzungstoken mit Benutzer/Passwort zulassen.<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> Bezeichnung<br /> </td> 
   <td> Bezeichnung<br /> </td> 
   <td> String <br /> </td> 
   <td> NewLabel()<br /> </td> 
  </tr> 
  <tr> 
   <td> Name<br /> </td> 
   <td> Interner <br /> </td> 
   <td> String <br /> </td> 
   <td> NewName() <br /> </td> 
  </tr> 
  <tr> 
   <td> sessionTokenOnly<br /> </td> 
   <td> Security-Token nicht verwenden.<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> showErrors<br /> </td> 
   <td> Fehlerdetails anzeigen<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

Hier finden Sie die Standardkonfiguration:

```
<securityZone allowDebug="false" allowHTTP="false" allowSQLInjection="false" label="Public Network" name="public">
  <subNetwork name="all" label="All addresses" mask="*" proxy="127.0.0.1, ::1"/>

  <securityZone allowDebug="true" allowHTTP="false" allowSQLInjection="false" label="Private Network (VPN)"
                name="vpn" showErrors="true">

    <securityZone allowDebug="true" allowEmptyPassword="false" allowHTTP="true" allowUserPassword="false"
                  allowSQLInjection="false" label="Private Network (LAN)" name="lan" sessionTokenOnly="true"
                  showErrors="true">
      <subNetwork name="lan1" label="Lan 1" mask="192.168.0.0/16" proxy="127.0.0.1, ::1"/>
      <subNetwork name="lan2" label="Lan 2" mask="172.16.0.0/12" proxy="127.0.0.1, ::1"/>
      <subNetwork name="lan3" label="Lan 3" mask="10.0.0.0/8" proxy="127.0.0.1, ::1"/>
      <subNetwork name="localhost" label="Localhost" mask="127.0.0.0/8" proxy="127.0.0.1, ::1"/>
      <subNetwork name="lan6"  label="Lan (IPv6)" mask="fc00::/7" proxy="127.0.0.1, ::1"/>
      <subNetwork name="lan6b" label="Lan (IPv6)" mask="fe80::/10" proxy="127.0.0.1, ::1"/>
      <subNetwork name="localhost6" label="Localhost (IPv6)" mask="::1/128" proxy="127.0.0.1, ::1"/>
    </securityZone>

  </securityZone>
</securityZone>
```

### SubNetwork {#subnetwork}

Im Folgenden finden Sie die verschiedenen Parameter **Knotens „securityZone > subNetwork**.

Weitere Informationen finden Sie unter [ von Sicherheitszonen](../../installation/using/security-zones.md).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschreibung </th> 
   <th> Typ </th> 
   <th> Standardwert </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Bezeichnung<br /> </td> 
   <td> Bezeichnung<br /> </td> 
   <td> String <br /> </td> 
   <td> NewLabel()<br /> </td> 
  </tr> 
  <tr> 
   <td> Maske<br /> </td> 
   <td> Maske oder Adresse<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> Name<br /> </td> 
   <td> Interner <br /> </td> 
   <td> String <br /> </td> 
   <td> NewName() <br /> </td> 
  </tr> 
  <tr> 
   <td> Proxy<br /> </td> 
   <td> Maske oder Adresse des vom Sub-Netzwerk verwendeten (Reverse) Proxys für den Zugriff auf die Instanz. In diesem Fall wird der Header „X-Forwarded-For“ anstelle dieses Proxys getestet.<br /> </td> 
   <td> String <br /> </td> 
   <td> 127.0.0.1 <br /> </td> 
  </tr> 
 </tbody> 
</table>

## sms {#sms}

Im Folgenden finden Sie die verschiedenen Parameter des **sms**-Knotens. Dies ist die Konfiguration des Verwaltungsmoduls für eingehende SMS.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschreibung </th> 
   <th> Typ </th> 
   <th> Standardwert </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> Startparameter<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Automatischer Start<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> dataRetentionDays<br /> </td> 
   <td> Maximale Anzahl an Tagen, die Arbeitsdateien des SMPP-Connectors aufbewahrt werden.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 60 <br /> </td> 
  </tr> 
  <tr> 
   <td> dataSizeMo<br /> </td> 
   <td> Maximale Größe der SMPP-Arbeitsdateien in MB.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 512 <br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID der JavaScript, die beim Starten des Prozesses ausgeführt werden soll.<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> keepAlivePeriod<br /> </td> 
   <td> Intervall des Kontinuitätsrahmens der Sitzung: max. Intervall in Sekunden zwischen zwei Frames, um anzuzeigen, dass die Empfangssitzung noch aktiviert ist.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 25 <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Warnhinweis bezüglich des Speicherverbrauchs: Warnhinweis bezüglich der RAM-Menge, die von einem bestimmten Prozess verbraucht wird (in MB)<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1 800 <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Warnung bezüglich des Speicherverbrauchs: Warnung bezüglich des RAM-Verbrauchs (in MB) durch einen bestimmten Prozess.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1 600 <br /> </td> 
  </tr> 
  <tr> 
   <td> pollPeriod<br /> </td> 
   <td> Suchfrequenz: Zeitraum der SMS-Kontoabfrage.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 300 <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Tageszeit, zu der der Prozess automatisch neu gestartet wird. Siehe <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatischer Prozessneustart</a>.<br /> </td> 
   <td> String <br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> reloadPeriod<br /> </td> 
   <td> Häufigkeit der Kontoneuladung: Häufigkeit der Datenbankneuladung der abzufragenden Konten.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 600 <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priorität beim Start. Module mit niedriger Priorität werden zuerst gestartet und zuletzt angehalten. Das Syslogd-Modul muss daher die Priorität 0.<br /> haben </td> 
   <td> Kurz<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> srReadDelay<br /> </td> 
   <td> Anzahl der Sekunden, die mit der Verarbeitung der SR in Verzug sind: Nur SRs mit einem Wiederherstellungsdatum, das vor der aktuellen Zeit liegt, minus der von srReadDelay angegebenen Dauer in Sekunden. <br /> </td> 
   <td> Lang<br /> </td> 
   <td> 600 <br /> </td> 
  </tr> 
  <tr> 
   <td> Zeitüberschreitung<br /> </td> 
   <td> Kommunikations-Timeout mit SMS-Gateway.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 300 <br /> </td> 
  </tr> 
 </tbody> 
</table>

### Netzgröße {#netsize}

Im Folgenden finden Sie die verschiedenen Parameter des Knotens **sms > netsize**.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschreibung </th> 
   <th> Typ </th> 
   <th> Standardwert </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> netsizeConnectionTimeout<br /> </td> 
   <td> Timeout in Sekunden beim Herstellen einer Verbindung mit Netsize.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Bundesland {#stat}

Im Folgenden finden Sie die verschiedenen Parameter des **stat**-Knotens. Dies ist die Konfiguration des Statistikmoduls des MTA.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschreibung </th> 
   <th> Typ </th> 
   <th> Standardwert </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> Startparameter<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Automatischer Start<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID der JavaScript, die beim Starten des Prozesses ausgeführt werden soll.<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Warnhinweis bezüglich des Speicherverbrauchs: Warnhinweis bezüglich der RAM-Menge, die von einem bestimmten Prozess verbraucht wird (in MB)<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1 800 <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Warnung bezüglich des Speicherverbrauchs: Warnung bezüglich des RAM-Verbrauchs (in MB) durch einen bestimmten Prozess.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1 600 <br /> </td> 
  </tr> 
  <tr> 
   <td> Port<br /> </td> 
   <td> Listening-Port des Servers Siehe diesen <a href="../../installation/using/email-deliverability.md#definition-of-the-server-port">Abschnitt</a>.<br /> </td> 
   <td> Kurz<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Tageszeit, zu der der Prozess automatisch neu gestartet wird. Siehe <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatischer Prozessneustart</a>.<br /> </td> 
   <td> String <br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priorität beim Start. Module mit niedriger Priorität werden zuerst gestartet und zuletzt angehalten. Das Syslogd-Modul muss daher die Priorität 0.<br /> haben </td> 
   <td> Kurz<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## syslogd {#syslogd}

Im Folgenden finden Sie die verschiedenen Parameter des **syslogd**-Knotens. Dies ist die Konfiguration des Log-Management-Moduls.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschreibung </th> 
   <th> Typ </th> 
   <th> Standardwert </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> Startparameter<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Automatischer Start<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID der JavaScript, die beim Starten des Prozesses ausgeführt werden soll.<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxFileSizeMb<br /> </td> 
   <td> Maximale Größe einer Protokolldatei in MB. <br /> </td> 
   <td> Lang<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> maxNumberOfLoginsFiles<br /> </td> 
   <td> Maximale Anzahl an beizubehaltenden logins.log-Dateien <br /> </td> 
   <td> Lang<br /> </td> 
   <td> 365 <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Warnhinweis bezüglich des Speicherverbrauchs: Warnhinweis bezüglich der RAM-Menge, die von einem bestimmten Prozess verbraucht wird (in MB)<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1 800 <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Warnung bezüglich des Speicherverbrauchs: Warnung bezüglich des RAM-Verbrauchs (in MB) durch einen bestimmten Prozess.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1 600 <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Tageszeit, zu der der Prozess automatisch neu gestartet wird. Siehe <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatischer Prozessneustart</a>.<br /> </td> 
   <td> String <br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priorität beim Start. Module mit niedriger Priorität werden zuerst gestartet und zuletzt angehalten. Das Syslogd-Modul muss daher die Priorität 0.<br /> haben </td> 
   <td> Kurz<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## tracking {#tracking}

Im Folgenden finden Sie die verschiedenen Parameter des **tracking**-Knotens. Dies ist die Konfiguration des Tracking-Servers.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschreibung </th> 
   <th> Typ </th> 
   <th> Standardwert </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> Startparameter<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Automatischer Start<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> blockRedirectForUnsignedTrackingLink<br /> </td> 
   <td> Deaktiviert falsch formatierte URLs, die von früheren Builds generiert wurden.<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> consolidationPeriodSec<br /> </td> 
   <td> Konsolidierungszeitraum<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 300 <br /> </td> 
  </tr> 
  <tr> 
   <td> dedupOpenPeriodMin<br /> </td> 
   <td> Öffnungen deduplizieren: Entfernen Sie doppelte Öffnungs-Trackinglogs, um die Auswirkungen von E-Mail-Vorschauen in E-Mail-Lesegeräten wie Outlook zu begrenzen.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> errorIgnorePercent<br /> </td> 
   <td> Bis zu X % der Fehler ignorieren: Die Tracking-Indikatoren werden nicht aktualisiert, solange der nicht berücksichtigte Anteil der Journale diesen Wert nicht erreicht. <br /> </td> 
   <td> byte<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> errorIgnorePeriod<br /> </td> 
   <td> Aktualisierung der Fehlerindikatoren: Maximale Dauer bis zur Neuberechnung der Fehlerindikatoren.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
  <tr> 
   <td> indicatorsDuration<br /> </td> 
   <td> Indikatoren berechnen während: Dauer nach dem Gültigkeitsdatum eines Versands, nach der konsolidierte Indikatoren nicht mehr berechnet werden.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 2592000<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID des JavaScript, der beim Starten des Prozesses ausgeführt werden soll<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> logCountPerRequest<br /> </td> 
   <td> Anzahl der pro Aufruf des Remote-Trackingservers abgerufenen Logs.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1.000 <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Warnhinweis bezüglich des Speicherverbrauchs: Warnhinweis bezüglich der RAM-Menge, die von einem bestimmten Prozess verbraucht wird (in MB)<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1 800 <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Warnung bezüglich des Speicherverbrauchs: Warnung bezüglich des RAM-Verbrauchs (in MB) durch einen bestimmten Prozess.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1 600 <br /> </td> 
  </tr> 
  <tr> 
   <td> phishbowlServiceAPIKey<br /> </td> 
   <td> API-Schlüssel für die Integration des Phishbowl-Service-Endpunkts. Dadurch wird die Weiterleitung von fehlerhaften URLs, die von älteren Builds generiert wurden, geschützt. <br /> </td> 
   <td> Lang<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> phishbowlServiceEndpoint<br /> </td> 
   <td> Endpunkt für die Integration des Phishbowl-Service-Endpunkts. Dadurch wird die Weiterleitung von fehlerhaften URLs geschützt, die von älteren Builds generiert wurden.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Tageszeit, zu der der Prozess automatisch neu gestartet wird. Siehe <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatischer Prozessneustart</a>.<br /> </td> 
   <td> String <br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priorität beim Start. Module mit niedriger Priorität werden zuerst gestartet und zuletzt angehalten. Das Syslogd-Modul muss daher die Priorität 0.<br /> haben </td> 
   <td> Kurz<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> trackingIgnorePercent<br /> </td> 
   <td> Bis zu X % des Trackings ignorieren: Die Trackingindikatoren werden nicht aktualisiert, solange der nicht berücksichtigte Anteil an den Journalen diesen Wert nicht erreicht.<br /> </td> 
   <td> byte<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> trackingIgnorePeriod<br /> </td> 
   <td> Aktualisierung der Tracking-Indikatoren: Maximale Dauer bis zur Neuberechnung der Tracking-Indikatoren.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
  <tr> 
   <td> userAgentCacheSize<br /> </td> 
   <td> Größe des Browserkennungs-Caches.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 500 <br /> </td> 
  </tr> 
 </tbody> 
</table>

## trackingLog {#trackinglogd}

Im Folgenden finden Sie die verschiedenen Parameter **Knotens** trackinglogd“. Dies ist die Konfiguration des Schreibdämons für Trackinglogs.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschreibung </th> 
   <th> Typ </th> 
   <th> Standardwert </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> Startparameter<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Automatischer Start<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID des JavaScript, der beim Starten des Prozesses ausgeführt werden soll<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxCreateFileRetry<br /> </td> 
   <td> Maximale Anzahl erneuter Schreibversuche: Maximale Anzahl von Dateien, die im Falle eines Schreibfehlers in den Protokolldateien erstellt werden können.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> maxLogsSizeOnDiskMb<br /> </td> 
   <td> Maximale Protokollgröße: Maximaler Speicherplatz für Protokolle auf der Festplatte (in MB). Darf nicht weniger als 100 MB sein. <br /> </td> 
   <td> Lang<br /> </td> 
   <td> 500 <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Warnhinweis bezüglich des Speicherverbrauchs: Warnhinweis bezüglich der RAM-Menge, die von einem bestimmten Prozess verbraucht wird (in MB)<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1 800 <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Warnung bezüglich des Speicherverbrauchs: Warnung bezüglich des RAM-Verbrauchs (in MB) durch einen bestimmten Prozess.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1 600 <br /> </td> 
  </tr> 
  <tr> 
   <td> maxSharedLogs<br /> </td> 
   <td> Maximale Log-Anzahl: Maximale Anzahl von Logs, die im gemeinsamen Speicher gespeichert werden. Darf nicht weniger sein als 10000. <br /> </td> 
   <td> Lang<br /> </td> 
   <td> 25000<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Tageszeit, zu der der Prozess automatisch neu gestartet wird. Siehe <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatischer Prozessneustart</a>.<br /> </td> 
   <td> String <br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> purgeLogsPeriod<br /> </td> 
   <td> Anzahl der Protokolle vor der Bereinigung: Anzahl der eingefügten Protokolle, bevor die Bereinigung der Protokolldateien gestartet wird. Darf nicht weniger sein als 50000.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 50000<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priorität beim Start. Module mit niedriger Priorität werden zuerst gestartet und zuletzt angehalten. Das Syslogd-Modul muss daher die Priorität 0.<br /> haben </td> 
   <td> Kurz<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> webTrackingParamSize<br /> </td> 
   <td> Maximale Anzahl an Zeichen, die im gemeinsamen Speicher für zusätzliche Webtracking-Parameter gespeichert werden.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 64 <br /> </td> 
  </tr> 
 </tbody> 
</table>

## Web {#web}

Im Folgenden finden Sie die verschiedenen Parameter des **web**-Knotens. Dies ist die Konfiguration des Web-Moduls.

Weitere Informationen finden Sie in diesem [Abschnitt](configuring-campaign-server.md#default-port-for-tomcat).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschreibung </th> 
   <th> Typ </th> 
   <th> Standardwert </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> JVMOptions<br /> </td> 
   <td> Optionen der als Zeichenfolge übergebenen JVM.<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> MaxThreads<br /> </td> 
   <td> Maximale Thread-Anzahl.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 75 <br /> </td> 
  </tr> 
  <tr> 
   <td> MinSpareThreads<br /> </td> 
   <td> Minimale Thread-Anzahl.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> args<br /> </td> 
   <td> Startparameter<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Automatischer Start<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> controlPort<br /> </td> 
   <td> Tomcat Listening Control Port: siehe <a href="configure-tomcat.md" target="_blank">Konfigurieren von Tomcat</a>.<br /> </td> 
   <td> Kurz<br /> </td> 
   <td> 8 005 <br /> </td> 
  </tr> 
  <tr> 
   <td> httpPort<br /> </td> 
   <td> Tomcat HTTP Listening-Port: siehe <a href="configure-tomcat.md" target="_blank">Konfigurieren von Tomcat</a>.<br /> </td> 
   <td> Kurz<br /> </td> 
   <td> 8 080 <br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID der JavaScript, die beim Starten des Prozesses ausgeführt werden soll.<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxDeliveryQueueSize<br /> </td> 
   <td> Größe der Warteschlange für SubmitDelivery-Aufrufe: Maximale Anzahl von SubmitDelivery SOAP-Aufrufen, die in die Warteschlange gestellt werden können.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 50 <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Warnhinweis bezüglich des Speicherverbrauchs: Warnhinweis bezüglich der RAM-Menge, die von einem bestimmten Prozess verbraucht wird (in MB)<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1 800 <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Warnung bezüglich des Speicherverbrauchs: Warnung bezüglich des RAM-Verbrauchs (in MB) durch einen bestimmten Prozess<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1 600 <br /> </td> 
  </tr> 
  <tr> 
   <td> notifRelay<br /> </td> 
   <td> Benachrichtigungsrelais: HostName:Port, das das Weiterleiten von Benachrichtigungen aktiviert.<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Tageszeit, zu der der Prozess automatisch neu gestartet wird. Siehe <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatischer Prozessneustart</a>.<br /> </td> 
   <td> String <br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priorität beim Start. Module mit niedriger Priorität werden zuerst gestartet und zuletzt angehalten. Das Syslogd-Modul muss daher die Priorität 0.<br /> haben </td> 
   <td> Kurz<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> startSoapRouterInModule<br /> </td> 
   <td> Starten Sie den SOAP-Router im Modulmodus.<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

### JSP {#jsp}

Im Folgenden finden Sie die verschiedenen Parameter **Knotens „web > jsp**. Dies ist die Konfiguration der von den JSPs verwendeten Parameter.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschreibung </th> 
   <th> Typ </th> 
   <th> Standardwert </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> DEBUG<br /> </td> 
   <td> JSP-Ausführung im Debug-Modus oder nicht.<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> downloadPath<br /> </td> 
   <td> Download-Ordner: Pfad zum Herunterladen der Installationsprogramme für die Client-Konsolen.<br /> </td> 
   <td> String <br /> </td> 
   <td> '$(XTK_INSTALL_DIR)/datakit/nl/eng/jsp'<br /> </td> 
  </tr> 
  <tr> 
   <td> foFileName<br /> </td> 
   <td> Pfad der .fo-Datei.<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> soapRouter<br /> </td> 
   <td> URL des SOAP-Routers (http://myserver/xxx, http://jni oder mailto:xxx).<br /> </td> 
   <td> String <br /> </td> 
   <td> 'http://jni'<br /> </td> 
  </tr> 
 </tbody> 
</table>

Der Knoten **web > jsp >** enthält die Liste aller beim Starten von JVM zu verwendenden Klassenpfade. Hier finden Sie die Standardkonfiguration:

```
'$(XTK_INSTALL_DIR)/tomcat-X/bin/bootstrap.jar
          $(XTK_INSTALL_DIR)/tomcat-X/bin/tomcat-juli.jar
          $(XTK_INSTALL_DIR)/tomcat-X/lib/tomcat-coyote.jar
          $(XTK_INSTALL_DIR)/tomcat-X/lib/tomcat-util.jar
          $(XTK_INSTALL_DIR)/tomcat-X/lib/tomcat-api.jar
          $(XTK_INSTALL_DIR)/tomcat-X/lib/servlet-api.jar
          $(XTK_INSTALL_DIR)/tomcat-X/lib/jsp-api.jar
          $(XTK_INSTALL_DIR)/tomcat-X/lib/el-api.jar
          $(XTK_INSTALL_DIR)/tomcat-X/lib/annotations-api.jar
          $(XTK_INSTALL_DIR)/tomcat-X/lib/catalina.jar
          $(XTK_INSTALL_DIR)/tomcat-X/lib/websocket-api.jar
          $(XTK_INSTALL_DIR)/tomcat-X/lib/tomcat7-websocket.jar
          $(XTK_INSTALL_DIR)/java/lib/pdfbox-2.0.4.jar
          $(XTK_INSTALL_DIR)/java/lib/FontBox-0.1.0.jar
          $(XTK_INSTALL_DIR)/java/lib/AGJavaEndpoint.22.jar
          $(XTK_INSTALL_DIR)/java/lib/NSGConstants.jar
          $(XTK_INSTALL_DIR)/java/lib/smpp.jar
          $(XTK_INSTALL_DIR)/java/lib/nlweb.jar
          $(XTK_INSTALL_DIR)/java/lib/jcaptcha-all.jar
          $(XTK_INSTALL_DIR)/java/lib/apns-1.0.0.Beta6-jar-with-dependencies.jar
          $(XTK_INSTALL_DIR)/java/lib/commons-collections-3.2.2.jar
          $(XTK_INSTALL_DIR)/java/lib/jcommon-1.0.16.jar
          $(XTK_INSTALL_DIR)/java/lib/jfreechart-1.0.13.jar
          $(XTK_INSTALL_DIR)/java/lib/barcode4j-light.jar
          $(XTK_INSTALL_DIR)/java/lib/zxing.jar
          $(XTK_INSTALL_DIR)/java/lib/raztec.jar
          $(XTK_INSTALL_DIR)/java/lib/gson-2.7.jar
          $(XTK_INSTALL_DIR)/java/lib/alpn-api-1.1.3.v20160715.jar
          $(XTK_INSTALL_DIR)/java/lib/netty-all-4.1.6.Final.jar
          $(XTK_INSTALL_DIR)/java/lib/netty-tcnative-boringssl-static-1.1.33.Fork22.jar
          $(XTK_INSTALL_DIR)/java/lib/pushy-0.8.1.jar
          $(XTK_INSTALL_DIR)/java/lib/slf4j-api-1.7.21.jar
          $(XTK_INSTALL_DIR)/java/lib/slf4j-simple-1.7.21.jar'
```

### JSSP {#jssp}

Im Folgenden finden Sie die verschiedenen Parameter **Knotens „web > jssp**. Dies ist die Konfiguration der von den JSSPs verwendeten Parameter.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschreibung </th> 
   <th> Typ </th> 
   <th> Standardwert </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> collectGarbageAfterRequest<br /> </td> 
   <td> Aktiviert die Garbage Collection des JavaScript-Kontexts nach jeder Abfrage.<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> Ja<br /> </td> 
  </tr> 
  <tr> 
   <td> timeToLive<br /> </td> 
   <td> Maximale Anzahl der Seiten, die von einem JavaScript-Kontext bereitgestellt werden <br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1.000 <br /> </td> 
  </tr> 
 </tbody> 
</table>

Der Knoten **web > jsp >** enthält die Liste aller beim Starten von JVM zu verwendenden Klassenpfade.

### weiterleiten {#relay-2}

Im Folgenden finden Sie die verschiedenen Parameter **Knotens „web >**&quot;. Dies ist die Konfiguration des Relais für HTTP-Anfragen zwischen zwei Zonen.

Weitere Informationen finden Sie in diesem [Abschnitt](../../installation/using/deploying-an-instance.md#synchronizing-public-resources).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschreibung </th> 
   <th> Typ </th> 
   <th> Standardwert </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> debugRelay<br /> </td> 
   <td> Starten Sie das HTTP-Weiterleitungsmodul im Webserver im Debug-Modus.<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> forbiddenCharsInAuthority<br /> </td> 
   <td> Unzulässige(s) Zeichen (Domain): Liste der unzulässigen Zeichen im 'Authority'-Abschnitt eines URI.<br /> </td> 
   <td> String <br /> </td> 
   <td> '.?#@/:' <br /> </td> 
  </tr> 
  <tr> 
   <td> forbiddenCharsInPath<br /> </td> 
   <td> Unzulässige(s) Zeichen (Pfad): Liste der unzulässigen Zeichen im 'Pfad'-Abschnitt eines URI.<br /> </td> 
   <td> String <br /> </td> 
   <td> '?#/'<br /> </td> 
  </tr> 
  <tr> 
   <td> modDir<br /> </td> 
   <td> Wert der Option des 'mod_dir'-Moduls: Liste der Dateien, die während einer Abfrage eines Ordners verwendet werden sollen.<br /> </td> 
   <td> String <br /> </td> 
   <td> 'index.md'-<br /> </td> 
  </tr> 
  <tr> 
   <td> startRelay<br /> </td> 
   <td> Startet das HTTP-Weiterleitungsmodul.<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> startRelayInModule<br /> </td> 
   <td> Startet das HTTP-Weiterleitungsmodul im Webserver. <br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> Ja<br /> </td> 
  </tr> 
  <tr> 
   <td> Zeitüberschreitung<br /> </td> 
   <td> Wartezeit vor Löschung der gesperrten URL.<br /> </td> 
   <td> String <br /> </td> 
   <td> '60'<br /> </td> 
  </tr> 
 </tbody> 
</table>

Fügen Sie für jede weiterzuleitende URL **Knoten** web > relais > url“ (die Einfügereihenfolge definiert die Priorität) mit den folgenden Parametern hinzu.

Weitere Informationen finden Sie unter [Dynamische Seitensicherheit und -](../../installation/using/configuring-campaign-server.md#dynamic-page-security-and-relays)) [Abschnitt](../../installation/using/deploying-an-instance.md#synchronizing-public-resources).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschreibung </th> 
   <th> Typ </th> 
   <th> Standardwert </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> IPMask<br /> </td> 
   <td> Autorisierte IPs: Durch Kommas getrennte Liste von Quell-IP-Adressen, die das -Relais für diese Maske verwenden dürfen.<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> Ablehnen<br /> </td> 
   <td> Verweigern des Zugriffs auf diese URLs (gibt einen HTTP 403-Fehler zurück)<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> hostMask<br /> </td> 
   <td> Weiterzuleitender DNS-Alias: Kommagetrennte Liste der weiterzuleitenden DNS-Alias-Masken (z. B.: '*.adobe.com').<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> httpAllowed<br /> </td> 
   <td> HTTP-Zugriff unabhängig von der Sicherheitszone zulässig (wie bei WebApps). <br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> relaisHost<br /> </td> 
   <td> Ursprünglichen Host hinzufügen: Verwendet den HTTP-'Host'-Header der weiterzuleitenden ursprünglichen Anfrage.<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> relaisPath<br /> </td> 
   <td> Anfänglichen URL-Pfad hinzufügen: Hängt den vollständigen Pfad der URLs an, die an die URL der Zielseite weitergeleitet werden sollen. <br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> Status<br /> </td> 
   <td> Synchronisierungsstatus einer öffentlichen Ressource (Auflistung). Mögliche Werte sind „normal“ (normale Ausführung), „blacklist“ (URL bei Fehler 404 zur Blockierungsliste hinzugefügt) und „spare“ (Datei-Upload auf Spare-Server, falls vorhanden).<br /> </td> 
   <td> String <br /> </td> 
   <td> normal<br /> </td> 
  </tr> 
  <tr> 
   <td> targetUrl<br /> </td> 
   <td> URL der Zielseite: siehe <a href="configure-tomcat.md" target="_blank">Tomcat konfigurieren</a>.<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> Zeitüberschreitung<br /> </td> 
   <td> Maximale Ausführungsdauer der weiterzuleitenden Anforderung (in Sekunden)<br /> </td> 
   <td> Lang<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> urlPath<br /> </td> 
   <td> Maske der weiterzuleitenden URLs (z. B.: '/nl*', '*.jsp').<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

Hier finden Sie die Standardkonfiguration:

```
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true"
     status="normal" targetUrl="http://localhost:7781" timeout="" urlPath="/pipelined/*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="false" urlPath="/view/*"/>
<url IPMask="" deny="true" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="false" urlPath="*ooconv.jsp*"/>
<url IPMask="" deny="true" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="false" urlPath="/res/*.jsp*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="*/sc.jssp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="*/interactionProposal.jssp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="*/zoneJson.jssp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/nms/jsp/barcode.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/nms/jsp/captcha.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/nms/jsp/webForm.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/xtk/jsp/zoneinfo.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="*/facebookCallback.jssp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/nl/jsp/m.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/nl/jsp/s.jsp"/>

<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="blacklist" httpAllowed="false" urlPath="/nms/jsp/*.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="blacklist" httpAllowed="false" urlPath="/xtk/jsp/*.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="blacklist" httpAllowed="false" urlPath="/nl/jsp/*.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="blacklist" httpAllowed="false" urlPath="*.jssp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="blacklist" httpAllowed="true" urlPath="/webApp/*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="blacklist" httpAllowed="false" urlPath="/report/*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="blacklist" httpAllowed="false" urlPath="/jssp/*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="false" urlPath="/strings/*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/interaction/*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/barcode/*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/lineImage/*"/>

<url IPMask="" deny="" hostMask="" relayHost="false" relayPath="false" targetUrl=""
     timeout="" status="spare" httpAllowed="true" urlPath="/favicon.*"/>
<url IPMask="" deny="" hostMask="" relayHost="false" relayPath="false" targetUrl=""
     timeout="" status="spare" httpAllowed="true" urlPath="/*.md"/>
<url IPMask="" deny="" hostMask="" relayHost="false" relayPath="false" targetUrl=""
     timeout="" status="spare" httpAllowed="true" urlPath="/*.png"/>
<url IPMask="" deny="" hostMask="" relayHost="false" relayPath="false" targetUrl=""
     timeout="" status="spare" httpAllowed="true" urlPath="/*.jpg"/>
```

Fügen Sie für jeden HTTP **Header einen Knoten („web“ > „relais** > „responseHeader„) hinzu, um ihn den an das Relais weitergeleiteten Antworten hinzuzufügen.

Weitere Informationen finden Sie unter [ von HTTP-Kopfzeilen](../../installation/using/configuring-campaign-server.md#managing-http-headers).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschreibung </th> 
   <th> Typ </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Name<br /> </td> 
   <td> Header-Name<br /> </td> 
   <td> String <br /> </td> 
  </tr> 
  <tr> 
   <td> Wert<br /> </td> 
   <td> Header-Wert <br /> </td> 
   <td> String <br /> </td> 
  </tr> 
 </tbody> 
</table>

Hier finden Sie die Standardkonfiguration:

```
<responseHeader name="X-XSS-Protection" value="1; mode=block"/>
```

### Umleitung {#redirection}

Im Folgenden finden Sie die verschiedenen Parameter **Knotens „web >**&quot;. Dies ist die Konfiguration des Weiterleitungsmoduls.

Weitere Informationen finden Sie in diesem [Abschnitt](../../installation/using/deploying-an-instance.md#synchronizing-public-resources).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschreibung </th> 
   <th> Typ </th> 
   <th> Standardwert </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> IMSOrgId<br /> </td> 
   <td> Organisations-ID: Eindeutige Organisationskennung innerhalb der Adobe Experience Cloud, die insbesondere für den VisitorID-Service und das IMS SSO verwendet wird. <br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> P3PCompactPolicy<br /> </td> 
   <td> Wert, der die für permanente Cookies verwendete Richtlinie beschreibt (im P3P Compact Policy Format). <br /> </td> 
   <td> String <br /> </td> 
   <td> 'CAO DSP COR CURa DEVa TAIa OUR BUS IND UNI COM NAV'<br /> </td> 
  </tr> 
  <tr> 
   <td> cookieDomain<br /> </td> 
   <td> Liste von Domains, durch Kommata getrennt, die so konfiguriert werden müssen, dass sie ausdrücklich angeben, dass Ihre Domain Cookies setzt. <br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> databaseId<br /> </td> 
   <td> Datenbankkennung der Trackinginstanz.<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> defLogCount<br /> </td> 
   <td> Protokollanzahl nach Aufruf: Anzahl der Protokolle, die bei einem Aufruf der GetTrackingLogs-Methode standardmäßig zurückgegeben werden<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
  <tr> 
   <td> expirationURL<br /> </td> 
   <td> Seite für abgelaufene Weiterleitungen: URL der vom Weiterleitungs-Server standardmäßig verwendeten Web-Seite, wenn die Weiterleitung für eine Versandaktion abgelaufen ist.<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxJobsInCache<br /> </td> 
   <td> Maximale Vorgangsanzahl: Maximale Anzahl von Versandaktionen im Cache. Darf nicht weniger als 50 sein. <br /> </td> 
   <td> Lang<br /> </td> 
   <td> 100 <br /> </td> 
  </tr> 
  <tr> 
   <td> showSourceIP<br /> </td> 
   <td> Bei Festlegung auf „false“ ist der Wert der Quell-IP in der von r/test zurückgegebenen Antwort eine leere Zeichenfolge. <br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> Ja<br /> </td> 
  </tr> 
  <tr> 
   <td> startRedirection<br /> </td> 
   <td> Starten Sie den Weiterleitungsdienst.<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> Ja<br /> </td> 
  </tr> 
  <tr> 
   <td> startRedirectionInModule<br /> </td> 
   <td> Starten Sie den Weiterleitungsdienst im Modulmodus.<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> Ja<br /> </td> 
  </tr> 
  <tr> 
   <td> trackWebVisitors<br /> </td> 
   <td> Webtracking: Erstellung von Protokollen für die von unbekannten Benutzern besuchten Seiten. <br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> trackingPassword<br /> </td> 
   <td> Vom Weiterleitungsserver verwendetes Kennwort.<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

Im Folgenden finden Sie die verschiedenen Parameter des Knotens **web > redirect > saveServer**.

Weitere Informationen finden Sie unter [Redundantes Tracking](../../installation/using/configuring-campaign-server.md#redundant-tracking).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschreibung </th> 
   <th> Typ </th> 
   <th> Standardwert </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> enabledIf<br /> </td> 
   <td> Berücksichtigt wenn: Der Tracking-Server wird berücksichtigt, wenn der Ausdruck „true“ zurückgibt. <br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> ID<br /> </td> 
   <td> Name<br /> </td> 
   <td> String <br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> URL<br /> </td> 
   <td> URL des zusätzlichen Weiterleitungsservers<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

### spamCheck {#spamcheck}

Im Folgenden finden Sie die verschiedenen Parameter **Knotens „web > spamCheck**. Dies ist die Konfiguration der Bewertungsparameter für die Anti-Spam-Punktzahl in E-Mails.

Weitere Informationen finden Sie unter [ von SpamAssassin](../../installation/using/configuring-spamassassin.md).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschreibung </th> 
   <th> Typ </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Befehl<br /> </td> 
   <td> Zur Auswertung der Anti-Spam-Punktzahl einer E-Mail auszuführender Befehl (z. B. 'perl spamcheck.pl').<br /> </td> 
   <td> String <br /> </td> 
  </tr> 
 </tbody> 
</table>

## wfserver {#wfserver}

Im Folgenden finden Sie die verschiedenen Parameter des **wfserver**-Knotens. Dies ist die Konfiguration des Workflow-Prozesses.

Weitere Informationen finden Sie unter [Workflows und Affinitäten mit hoher Verfügbarkeit](../../installation/using/configuring-campaign-server.md#high-availability-workflows-and-affinities).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschreibung </th> 
   <th> Typ </th> 
   <th> Standardwert </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Affinität<br /> </td> 
   <td> Affinität<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> args<br /> </td> 
   <td> Startparameter<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Automatischer Start<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> dataBasePoolPeriodSec<br /> </td> 
   <td> Zeitraum<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 20<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID der JavaScript, die beim Starten des Prozesses ausgeführt werden soll.<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Warnhinweis bezüglich des Speicherverbrauchs: Warnhinweis bezüglich der RAM-Menge, die von einem bestimmten Prozess verbraucht wird (in MB)<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1 800 <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Warnung bezüglich des Speicherverbrauchs: Warnung bezüglich des RAM-Verbrauchs (in MB) durch einen bestimmten Prozess.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1 600 <br /> </td> 
  </tr> 
  <tr> 
   <td> notifRelay<br /> </td> 
   <td> Benachrichtigungsrelais: HostName:Port, das das Weiterleiten von Benachrichtigungen aktiviert.<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Tageszeit, zu der der Prozess automatisch neu gestartet wird. Siehe <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatischer Prozessneustart</a>.<br /> </td> 
   <td> String <br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priorität beim Start. Module mit niedriger Priorität werden zuerst gestartet und zuletzt angehalten. Das Syslogd-Modul muss daher die Priorität 0.<br /> haben </td> 
   <td> Kurz<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>
