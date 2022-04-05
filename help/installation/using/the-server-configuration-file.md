---
product: campaign
title: Die Server-Konfigurationsdatei
description: Die Server-Konfigurationsdatei
audience: installation
content-type: reference
topic-tags: appendices
exl-id: 70cd6a4b-c839-4bd9-b9a7-5a12e59c0cbf
source-git-commit: f4513834cf721f6d962c7c02c6c64b2171059352
workflow-type: tm+mt
source-wordcount: '7961'
ht-degree: 39%

---

# Die Server-Konfigurationsdatei{#the-server-configuration-file}

![](../../assets/v7-only.svg)

Die Gesamtkonfiguration von Adobe Campaign wird im Abschnitt **serverConf.xml** -Datei, die sich im **conf** -Ordner des Installationsordners. In diesem Abschnitt werden alle verschiedenen Knoten und Parameter der **serverConf.xml** -Datei.

>[!NOTE]
>
>Serverseitige Konfigurationen können nur von Adobe für Bereitstellungen durchgeführt werden, die von Adobe gehostet werden. Weitere Informationen zu den verschiedenen Implementierungen finden Sie im Abschnitt [Hosting-Modelle](../../installation/using/hosting-models.md) oder [diese Seite](../../installation/using/capability-matrix.md). Die Installations- und Konfigurationsschritte für gehostete und hybride Modelle werden in diesem Abschnitt beschrieben. [Abschnitt](../../installation/using/hosting-models.md).

Die ersten Parameter befinden sich innerhalb der **shared** Knoten. Diese beziehen sich auf die Instanz. Sie werden potenziell von allen nlserver-Befehlen verwendet (nlserver web, nlserver wfserver usw.). Die anderen Abschnitte beziehen sich auf einen bestimmten nlserver-Unterbefehl.

**Freigegebene Parameter**

* [Authentifizierung](#authentication)
* [dataStore](#datastore)
* [dnsConfig](#dnsconfig)
* [exec](#exec)
* [htmlToPdf](#htmltopdf)
* [ims](#ims)
* [javaScript](#javascript)
* [mailExchanger](#mailexchanger)
* [module](#module)
* [Monitoring](#monitoring)
* [ooconv](#ooconv)
* [proxyConfig](#proxyconfig)
* [threadPool](#threadpool)
* [urlPermission](#urlpermission)
* [xtkJobs](#xtkjobs)

**Andere Parameter**

* [Archivierung](#archiving)
* [inMail](#inmail)
* [interactiond](#interactiond)
* [mta](#mta)
* [nmac](#nmac)
* [pipelined](#pipelined)
* [Reparatur](#repair)
* [securityZone](#securityzone)
* [sms](#sms)
* [stat](#stat)
* [syslogd](#syslogd)
* [tracking](#tracking)
* [trackinglogd](#trackinglogd)
* [Web](#web)
* [wfserver](#wfserver)

## Authentifizierung {#authentication}

Im Folgenden finden Sie die verschiedenen Parameter der **Authentifizierung** node:

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
   <td> Prüfung der IP-Adressen aktivieren.<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> defaultMode<br /> </td> 
   <td> Standard-Authentifizierungsmodus.<br /> </td> 
   <td> String <br /> </td> 
   <td> 'nl'<br /> </td> 
  </tr> 
  <tr> 
   <td> longSessionTimeOutSec<br /> </td> 
   <td> Zeitbeschränkung langer Sitzungen in Sekunden.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1296000<br /> </td> 
  </tr> 
  <tr> 
   <td> securityTimeOutSec<br /> </td> 
   <td> Zeitbeschränkung des Security-Tokens.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
  <tr> 
   <td> sessionCacheSec<br /> </td> 
   <td> Aufbewahrungsfrist im Cache: Cache der Sitzungsinformationen in Sekunden.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> sessionTimeOutSec<br /> </td> 
   <td> Zeitbeschränkung in Sekunden.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
 </tbody> 
</table>

### XTK {#xtk}

Im Folgenden finden Sie die verschiedenen Parameter der **Authentifizierung > XTK** node:

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
   <td> Sicherheitszone des internen Kontos: die zulässige Zone für das interne Konto.<br /> </td> 
   <td> String <br /> </td> 
   <td> "lan"<br /> </td> 
  </tr> 
 </tbody> 
</table>

## dataStore {#datastore}

Im Folgenden finden Sie die verschiedenen Parameter der **dataStore** Knoten. Hier werden die Server-Datenquellen definiert.

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
   <td> extraSandboxedDirectories<br /> </td> 
   <td> Zusätzliche Ordner mit Sandboxes: andere Pfade, die in die Sandbox hinzugefügt werden sollen (durch Kommas getrennt).<br /> </td> 
   <td> String <br /> </td> 
   <td> '/home/Customers/,/sftp/' <br /> </td> 
  </tr> 
  <tr> 
   <td> formCacheTimeToLive<br /> </td> 
   <td> Ablaufverzögerung für Formular-Cache: Zeitüberschreitung in Sekunden, nach der ein Cache-Eintrag ungültig gemacht wird. O bedeutet, dass Cache-Einträge nur zum Zeitpunkt der Veröffentlichung aktualisiert werden.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> hosts<br /> </td> 
   <td> DNS-Masken: Liste der DNS-Masken, die diese Instanz bereitstellt (durch Kommas getrennt, kann * und ? verwenden Muster).<br /> </td> 
   <td> String <br /> </td> 
   <td> '*'<br /> </td> 
  </tr> 
  <tr> 
   <td> interactionCacheTimeToLive<br /> </td> 
   <td> Interaction JSSP-Cache-Ablaufverzögerung: Zeitüberschreitung in Sekunden, nach der ein Cache-Eintrag ungültig gemacht wird. Ein negativer Wert bedeutet, dass der Cache immer invalidiert wird. "0", leere oder ungültige Werte werden als 60 betrachtet.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> lang<br /> </td> 
   <td> Instanzsprache (Auflistung). Mögliche Werte sind "fr_FR"(Français), "en_GB"(Englisch (UK)), "en_US"(Englisch (US)), "de_DE"(Deutsch) und "ja_JP"(Japanisch).<br /> </td> 
   <td> String <br /> </td> 
   <td> "en_US"<br /> </td> 
  </tr> 
  <tr> 
   <td> uploadDirectory<br /> </td> 
   <td> Ordner hochladen: Pfad des Zielverzeichnisses für die hochgeladenen Daten.<br /> </td> 
   <td> String <br /> </td> 
   <td> '$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/upload/' <br /> </td> 
  </tr> 
  <tr> 
   <td> uploadAllowlist<br /> </td> 
   <td> Dateien, die hochgeladen werden dürfen, durch ',' getrennt. String muss ein gültiger regulärer Java-Ausdruck sein. Siehe <a href="file-res-management.md" target="_blank">Eingrenzen hochladbarer Dateien</a>.<br /> </td> 
   <td> String <br /> </td> 
   <td> '.+' <br /> </td> 
  </tr> 
  <tr> 
   <td> useVault<br /> </td> 
   <td> Geheimnisse im Vault speichern: Verwenden Sie Hashicorp Vault.<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> vaultSecretPath<br /> </td> 
   <td> Geheimer Pfad in Vault<br /> </td> 
   <td> String <br /> </td> 
   <td> '/v1/secret/campaign/'<br /> </td> 
  </tr> 
  <tr> 
   <td> vaultTokenPath<br /> </td> 
   <td> Lokaler Pfad der Datei, die den Volt-Token enthält. $(HOME) kann in diesem Pfad verwendet werden (aber nicht in anderen env-Variablen).<br /> </td> 
   <td> String <br /> </td> 
   <td> '$(HOME)/.vaultoken'<br /> </td> 
  </tr> 
  <tr> 
   <td> vaultUrl<br /> </td> 
   <td> Vault-URL von HashiCorp <br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> viewCacheTimeToLive<br /> </td> 
   <td> Gültigkeitszeitraum des Ansichtscache: Zeitüberschreitung in Sekunden, nach der ein Cache-Eintrag ungültig gemacht wird. Ein negativer Wert bedeutet, dass der Cache immer invalidiert wird. "0", leere oder ungültige Werte werden als 60 betrachtet.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> workingDirectory<br /> </td> 
   <td> Pfad des Arbeitsverzeichnisses<br /> </td> 
   <td> String <br /> </td> 
   <td> workingDirectory : XPath des Arbeitsverzeichnisses. Standard: '$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/workspace/'<br /> </td> 
  </tr> 
 </tbody> 
</table>

### proxyAdjust {#proxyadjust}

Im Folgenden finden Sie die verschiedenen Parameter der **dataStore > proxyAdjust** Knoten. URLs, die mit dem regulären Ausdruck übereinstimmen, werden basierend auf der in urlBase definierten URL neu generiert.

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
   <td> Basis zur Erzeugung von externen URLs. Z. B.: https://server.domain.com<br /> </td> 
   <td> String <br /> </td> 
  </tr> 
  <tr> 
   <td> urlRegEx<br /> </td> 
   <td> Regulärer Ausdruck für das Pattern Matching; z. B. http://server\.lan\.net.*<br /> </td> 
   <td> String <br /> </td> 
  </tr> 
 </tbody> 
</table>

### dataSource {#datasource}

Im Folgenden finden Sie die verschiedenen Parameter der **dataStore > dataSource** Knoten.

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
   <td> name<br /> </td> 
   <td> Datenquellenname<br /> </td> 
   <td> String <br /> </td> 
   <td> Standard<br /> </td> 
  </tr> 
 </tbody> 
</table>

Im **dataStore > dataSource > dbcnx** -Knoten konfigurieren Sie die Verbindungseinstellungen:

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
   <td> Unicode-Speicher<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> dbSchema<br /> </td> 
   <td> Arbeitsbereich     <br /> </td> 
   <td> String <br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> verschlüsselt<br /> </td> 
   <td> Verschlüsseltes Kennwort<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Login<br /> </td> 
   <td> Konto<br /> </td> 
   <td> String <br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Kennwort<br /> </td> 
   <td> Passwort<br /> </td> 
   <td> String <br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Provider<br /> </td> 
   <td> Typ (Auflistung). Mögliche Werte sind 'Oracle', 'MSSQL' (Microsoft SQL Server), 'PostgreSQL' (PostgreSQL), 'Teradata', 'DB2', 'MySQL', 'Netezza', 'AsterData', 'SAPHANA' (SAP HANA), 'RedShift' (Amazon Redshift), 'ODBC' (Sybase ASE, Sybase IQ). , 'Relay' (HTTP-Weiterleitung auf Remote-Datenbank).<br /> </td> 
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
   <td> timezone<br /> </td> 
   <td> Zeitzone: see <a href="../../installation/using/time-zone-management.md" target="_blank">Zeitzonen-Management</a>.<br /> </td> 
   <td> String <br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> unicodeData<br /> </td> 
   <td> Unicode-Daten der Datenbank<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> useTimestampTZ<br /> </td> 
   <td> Datumsfelder mit Zeitzone: see <a href="../../installation/using/time-zone-management.md" target="_blank">Zeitzonen-Management</a>.<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

Im **dataStore > dataSource > sqlParams** -Knoten konfigurieren Sie die SQL-Parameter:

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

Im **dataStore > dataSource > pool** -Knoten konfigurieren Sie die Parameter des zugehörigen Verbindungspools:

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
   <td> Zeitspanne zwischen den Gültigkeitstests der Verbindung<br /> </td> 
   <td> Kurz<br /> </td> 
  </tr> 
  <tr> 
   <td> freeCnx<br /> </td> 
   <td> Anzahl der freien, im Pool beibehaltenen Verbindungen.<br /> </td> 
   <td> Kurz<br /> </td> 
  </tr> 
  <tr> 
   <td> maxCnx<br /> </td> 
   <td> Maximale Anzahl von zulässigen Verbindungen, bevor der Zugriff verweigert wird Siehe dies <a href="https://helpx.adobe.com/campaign/kb/how-to-increase-the-maximum-number-of-database-connections-from-.html">Technote</a>.<br /> </td> 
   <td> Kurz<br /> </td> 
  </tr> 
  <tr> 
   <td> maxIdleDelaySec<br /> </td> 
   <td> Zeitspanne vor der automatischen Abmeldung einer nicht genutzten Verbindung. 0 bedeutet den Gebrauch der Standardeinstellungen.<br /> </td> 
   <td> Kurz<br /> </td> 
  </tr> 
 </tbody> 
</table>

### virtualDir {#virtualdir}

Im Folgenden finden Sie die verschiedenen Parameter der **dataStore > virtualDir** Knoten. Dies ist die Konfiguration des virtuellen Verzeichnisses in das tatsächliche Verzeichnis-Mapping.

Weitere Informationen finden Sie unter [Verwaltung öffentlicher Ressourcen](file-res-management.md).

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
   <td> name<br /> </td> 
   <td> Name des virtuellen Verzeichnisses <br /> </td> 
   <td> String <br /> </td> 
  </tr> 
  <tr> 
   <td> path<br /> </td> 
   <td> Vollständiger Pfad des tatsächlichen Verzeichnisses<br /> </td> 
   <td> String <br /> </td> 
  </tr> 
 </tbody> 
</table>

Dies ist die Standardkonfiguration:

```
<virtualDir name="images" path="$(XTK_INSTALL_DIR)/var/res/img/"/>
<virtualDir name="formCache" path="$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/formCache/"/>
<virtualDir name="publicFileRes" path="$(XTK_INSTALL_DIR)/var/res/$(INSTANCE_NAME)"/>
```

### preprocessCommand {#preprocesscommand}

Im Folgenden finden Sie die verschiedenen Parameter der **dataStore > preprocessCommand** Knoten. Dies sind die autorisierten Befehle zur Vorverarbeitung der Workflow-Aktivität &quot;Datei laden&quot;.

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
   <td> command<br /> </td> 
   <td> Befehlszeile <br /> </td> 
   <td> String <br /> </td> 
  </tr> 
  <tr> 
   <td> label<br /> </td> 
   <td> Titel der Befehlszeile<br /> </td> 
   <td> String <br /> </td> 
  </tr> 
  <tr> 
   <td> name<br /> </td> 
   <td> Name der Befehlszeile<br /> </td> 
   <td> String <br /> </td> 
  </tr> 
 </tbody> 
</table>

Dies ist die Standardkonfiguration:

```
<preprocessCommand command="" label="None" name="none"/>
<preprocessCommand command="zcat &quot;$fileName&quot;" label="Decompression" name="zcat"/><preprocessCommand command="gpg --decrypt &quot;$fileName&quot;" label="Decrypt" name="gpg"/>
```

## dnsConfig {#dnsconfig}

Im Folgenden finden Sie die verschiedenen Parameter der **dnsConfig** (DNS-Konfiguration).

Weitere Informationen finden Sie in diesem Abschnitt [Abschnitt](../../installation/using/configuring-campaign-server.md).

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
   <td> Domänenname: Standarddomänenname. Wird vom SMTP HELO-Befehl verwendet. Nutzt standardmäßig die Netzwerkparameter der ersten unter Windows erklärten Netzwerkschnittstelle oder parst die Datei /etc/resolv.conf unter Linux (Angabe des Domain-Namens oder Search-Eintrag). <br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> nameServers<br /> </td> 
   <td> DNS-Server: Kommagetrennte Liste von Domain-Namen-Servern (DNS). Siehe Hinweis unten.<br /> </td> 
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
   <td> timeout<br /> </td> 
   <td> Zeitüberschreitung in Millisekunden für eine DNS-Abfrage.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 5000<br /> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Hinweis: **nameServer**: verwendet standardmäßig das Netzwerk
>Parameter der ersten unter Windows deklarierten Netzwerkschnittstelle
>nicht in UNIX definiert. Definiert die Domänennamenserver (DNS)
>wird vom MTA verwendet, um den E-Mail-Ausdrucksserver zu erhalten, der für
>eine Domäne.
>
>Wenn dieser Wert nicht definiert ist, sucht der MTA diese Informationen in der Host-Netzwerkkonfiguration. Wenn mehrere DNS-Adressen möglich sind, müssen die verschiedenen DNS-Adressen durch ein Komma getrennt werden (Beispiel: 212.155.207.1&#39;212.155.207.2). Wenn Ihr Versandserver über mehrere Netzwerkschnittstellen verfügt, ist die vom MTA verwendete DNS-Liste die erste. In diesem Fall wird empfohlen, die Variable **nameServer** -Parameter, um Unklarheiten zu vermeiden.

>[!CAUTION]
>
>Wenn Ihre Netzwerk-Host-Konfiguration DHCP verwendet, findet der MTA nicht die DNS-Liste, die von DHCP bereitgestellt wird. In diesem Fall wird empfohlen, die DNS-Liste in den Netzwerkparametern der Windows-Systemsteuerung anzugeben.

## exec {#exec}

Im Folgenden finden Sie die verschiedenen Parameter der **exec** (Befehlsausführung).

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
   <td> Pfad zur Datei mit den Befehlen, die zur Zulassungsliste hinzugefügt werden sollen. <br /> </td> 
   <td> String <br /> </td> 
  </tr> 
  <tr> 
   <td> Benutzer<br /> </td> 
   <td> Führen Sie Befehle als anderen Benutzer aus.<br /> </td> 
   <td> String <br /> </td> 
  </tr> 
 </tbody> 
</table>

## htmlToPdf {#htmltopdf}

Im Folgenden finden Sie die verschiedenen Parameter der **htmlToPdf** Knoten. Dies ist die Konfiguration des Diensts zum Konvertieren von Webseiten in PDF-Dokumente.

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
   <td> command<br /> </td> 
   <td> Befehlszeile zum Ausführen der Konvertierung (im Modus "Sonstige").<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessusCount<br /> </td> 
   <td> Max. Anzahl der Konvertierungsprozesse, die gleichzeitig auf einem Computer zulässig sind.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> mode<br /> </td> 
   <td> Tool für die Konvertierung. Mögliche Werte sind: phantomjs, wkhtmltopdf, other, disabled<br /> </td> 
   <td> String <br /> </td> 
   <td> "phantomjs" <br /> </td> 
  </tr> 
  <tr> 
   <td> timeout<br /> </td> 
   <td> Zeitüberschreitung für eine Konversion: maximale Konvertierungsdauer in Sekunden. Über diesen Schwellenwert hinaus wird der Konvertierungsprozess angehalten und ein Fehler erzeugt.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 120<br /> </td> 
  </tr> 
  <tr> 
   <td> verbose<br /> </td> 
   <td> Verbose mode: Starten Sie im ausführlichen Modus, um mögliche Fehler zu diagnostizieren.<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> waitTime<br /> </td> 
   <td> Wartezeit auf einen Prozess: Verzögerung in Sekunden, wenn alle Prozesse gleichzeitig verwendet werden und darauf gewartet wird, dass ein Prozess freigegeben wird. Wenn diese Verzögerung überschritten wird, wird die Konvertierung angehalten und ein Fehler erzeugt. <br /> </td> 
   <td> Lang<br /> </td> 
   <td> 15<br /> </td> 
  </tr> 
 </tbody> 
</table>

Beispiel für Phantomjs:

```
phantomjs - -ignore-ssl-errors=true '$(XTK_INSTALL_DIR)/bin/htmlToPdf.js' '-out:{outPdf}' '-post:{postFile}' '-url:{originUrl}' -sessiontoken:{sessiontoken} -format:{format} -orientation:{orientation} -marginTop:{marginTop} -marginLeft:{marginLeft} -marginRight:{marginRight} -marginBottom:{marginBottom}
```

## ims {#ims}

Im Folgenden finden Sie die verschiedenen Parameter der **ims** Knoten. Dies ist die Konfiguration für die Verbindung von Campaign mit einem anderen Dienst mithilfe von [IMS](../../integrations/using/about-adobe-id.md).

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
   <td> Client ID<br /> (Client-ID) </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSClientSecret<br /> </td> 
   <td> Geheimschlüssel (mit AES verschlüsselt)<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSCode<br /> </td> 
   <td> Zulassungs-Code (mit AES verschlüsselt)<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSEndpoint<br /> </td> 
   <td> IMS-Server-URL<br /> </td> 
   <td> String <br /> </td> 
   <td> "https://ims-na1.adobelogin.com'<br /> </td> 
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
   <td> Kennung des technischen Kontos<br /> </td> 
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

Im Folgenden finden Sie die verschiedenen Parameter der **javaScript** Knoten. Dies ist die Konfiguration des JavaScript-Interpreters.

Weitere Informationen finden Sie im Abschnitt [Berichtdokumentation](../../reporting/using/actions-on-reports.md#memory-allocation).

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
   <td> Maximale Größe in Megabyte, bevor die Garbage Collection ausgelöst wird.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 512 <br /> </td> 
  </tr> 
  <tr> 
   <td> stackSizeKB<br /> </td> 
   <td> Größe in Kilobyte für jeden Stapelblock. Dies ist ein Parameter zur Optimierung der Speicherverwaltung, den die meisten Benutzer nicht anpassen sollten. <br /> </td> 
   <td> Lang<br /> </td> 
   <td> 8<br /> </td> 
  </tr> 
 </tbody> 
</table>

## mailExchanger {#mailexchanger}

Im Folgenden finden Sie die verschiedenen Parameter der **mailExchanger** Knoten. Dies ist die Konfiguration des SMTP-Servers.

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
   <td> 25<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Modul {#module}

Im Folgenden finden Sie die verschiedenen Parameter der **Modul** Knoten. Dies ist die Konfiguration für das Namensraum-Einschränkungsmodul xtk.

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
   <td> Standard-Namespace bei der Erstellung einer neuen Entität.<br /> </td> 
   <td> String <br /> </td> 
   <td> 'cus'<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Monitoring {#monitoring}

Im Folgenden finden Sie die verschiedenen Parameter der **Monitoring** Knoten. Dies ist die Konfiguration des Überwachungsdienstes.

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
   <td> maxPreparationJobsSec<br /> </td> 
   <td> Maximale Vorbereitungszeit: Dauer in Sekunden, nach der eine Versandaktion nicht mehr vorbereitet werden soll.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 3600<br /> </td> 
  </tr> 
  <tr> 
   <td> unixScript<br /> </td> 
   <td> Unix-Script, das durch den Monitoring-Dienst ausgeführt wird.<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> winScript<br /> </td> 
   <td> Windows-Script, das durch den Monitoring-Dienst ausgeführt wird.<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

## ooconv {#ooconv}

Im Folgenden finden Sie die verschiedenen Parameter der **ooconv** Knoten. Dies ist die Konfiguration des Dokumentkonvertierungsservers.

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
   <td> Maximale Anzahl der Konvertierungen, die ein OpenOffice-Server ausführen darf. Über diese Zahl hinaus wird der Server neu gestartet.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxServerIdleSec<br /> </td> 
   <td> Maximale Leerlaufzeit des OpenOffice-Servers vor erzwungenem Schließen.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 7200<br /> </td> 
  </tr> 
  <tr> 
   <td> portRange<br /> </td> 
   <td> Intervall der Ports, auf denen die OpenOffice-Server lauschen.<br /> </td> 
   <td> String <br /> </td> 
   <td> 8101-8110<br /> </td> 
  </tr> 
  <tr> 
   <td> url<br /> </td> 
   <td> URL des Dokumentkonvertierungsservers.<br /> </td> 
   <td> String <br /> </td> 
   <td> "http://localhost:8080/nl/jsp/ooconv.jsp'<br /> </td> 
  </tr> 
 </tbody> 
</table>

## proxyConfig {#proxyconfig}

Im Folgenden finden Sie die verschiedenen Parameter der **proxyConfig** Knoten. Dies ist die Konfiguration von Proxy-Parametern.

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
   <td> Proxy-Server benutzen.<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> override<br /> </td> 
   <td> Ausnahmen: Liste der Adressen, für die Proxy-Parameter ignoriert werden sollen.<br /> </td> 
   <td> String <br /> </td> 
   <td> 'localhost*' <br /> </td> 
  </tr> 
  <tr> 
   <td> useSingleProxy<br /> </td> 
   <td> Unique Proxy-Server: dieselbe Konfiguration für alle Proxytypen verwenden.<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

### HTTP-Proxy/sicherer Proxy {#http-proxy---secure-proxy-}

Im **proxyConfig > HTTP-Proxy/Secure Proxy** Knoten konfigurieren Sie die folgenden Parameter.

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
   <td> Login<br /> </td> 
   <td> Login zur Verbindung mit dem Proxy-Server<br /> </td> 
   <td> String <br /> </td> 
  </tr> 
  <tr> 
   <td> Kennwort<br /> </td> 
   <td> Kennwort für die Anmeldung zum Proxy-Server<br /> </td> 
   <td> String <br /> </td> 
  </tr> 
  <tr> 
   <td> Port<br /> </td> 
   <td> Proxy-Server-Port<br /> </td> 
   <td> Kurz<br /> </td> 
  </tr> 
 </tbody> 
</table>

## threadPool {#threadpool}

Im Folgenden finden Sie die verschiedenen Parameter der **threadPool** Knoten.

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
   <td> Maximale Anzahl der Threads im Pool. <br /> </td> 
   <td> Lang<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## urlPermission {#urlpermission}

Im Folgenden finden Sie die verschiedenen Parameter der **urlPermission** Knoten. Dies ist die Liste der URLs, auf die der JavaScript-Code zugreifen kann.

Liste der Domänen und regulären Ausdrücke, die angeben, ob eine URL im JavaScript-Code vom Adobe Campaign-Server verwendet werden kann oder nicht.

Wenn die URL nicht gefunden werden kann, wird die Standardaktion entsprechend dem angegebenen Standardmodus ausgeführt.

Weitere Informationen finden Sie unter [Schutz der ausgehenden Verbindung](../../installation/using/configuring-campaign-server.md#url-permissions).

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
   <td> action<br /> </td> 
   <td> Standardaktion, wenn die URL nicht in der Liste der zulässigen Werte (Auflistung) enthalten ist. Mögliche Werte sind "ignore"(autorisieren ohne Warnmeldung, dies erfordert die Deaktivierung des Schutzes), "warn"(erlauben und geben Sie eine Warnmeldung) und "deny"(verbieten Sie den Zugriff auf die URL).<br /> </td> 
   <td> String <br /> </td> 
   <td> Ablehnen<br /> </td> 
  </tr> 
  <tr> 
   <td> debugTrace<br /> </td> 
   <td> Debugging-Trace des URL-Auswahlmechanismus: gibt während der URL-Überprüfung zusätzliche Nachrichten aus.<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

### url {#url}

Fügen Sie für jede URL eine **url** Knoten mit den folgenden Parametern:

Weitere Informationen finden Sie unter [Schutz der ausgehenden Verbindung](../../installation/using/configuring-campaign-server.md#url-permissions).

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
   <td> Domänenname oder übergeordnete Domäne, die von der URL betroffen sind: die Domäne der URL vollständig oder teilweise zu überprüfen, um die Verifizierung zu beschleunigen. Die URL wird nur in Bezug auf den regulären Ausdruck überprüft, wenn die Domäne dsnSuffix enthält.<br /> </td> 
   <td> String <br /> </td> 
  </tr> 
  <tr> 
   <td> urlRegEx<br /> </td> 
   <td> Regulärer Ausdruck zur Verfeinerung der Validierung von URLs, die zu dieser Domäne gehören: regulären Ausdruck, den die URL überprüfen muss, sollte sie mit dnsSuffix übereinstimmen.<br /> </td> 
   <td> String <br /> </td> 
  </tr> 
 </tbody> 
</table>

Wenn ein Datensatz **dnsSuffix** aber nicht **urlRegEx**, wird der folgende Datensatz geprüft.

Um beispielsweise den Zugriff auf alle URLs der Domain &quot;business.com&quot;zu erlauben, können wir zwei Datensätze definieren:

dnsSuffix=&quot;business.com&quot; urlRegEx=&quot;http://.&#42;&quot;

and

dnsSuffix=&quot;business.com&quot; urlRegEx=&quot;https://.&#42;&quot;

Dies ist die Standardkonfiguration:

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
<url dnsSuffix="deliverability.neolane.net"              urlRegEx="https://deliverability.neolane.net/jssp/dm/renderingSeed.jssp" />
<url dnsSuffix="deliverability.neolane.net"              urlRegEx="https://deliverability.neolane.net/nl/jsp/soaprouter.jsp" />
<url dnsSuffix="localhost"                               urlRegEx="http://localhost:8080/nms/jsp/.*"              />
<url dnsSuffix="localhost"                               urlRegEx="http://localhost:8080/nl/jsp/.*"               />
<url dnsSuffix="localhost"                               urlRegEx="http://localhost:8080/xtk/jsp/.*"              />
```

## xtkJobs {#xtkjobs}

Im Folgenden finden Sie die verschiedenen Parameter der **xtkJobs** Knoten. Dies ist die Konfiguration der Serveraufträge.

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
   <td> Aktualisierungszeitraum für den Speicherstatus der Serververarbeitung (in ms).<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 500<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Archivierung {#archiving}

Im Folgenden finden Sie die verschiedenen Parameter der **Archivierung** Knoten. Dies ist die Konfiguration der ausgeführten Archivierungsvorgänge im Hintergrund.

Weitere Informationen finden Sie unter [Aktivieren der E-Mail-Archivierung (vor Ort)](../../installation/using/email-archiving.md#activating-email-archiving--on-premise-).

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
   <td> acquisitionLimit<br /> </td> 
   <td> Anzahl gleichzeitig zu verarbeitender EML<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> archivingType<br /> </td> 
   <td> Archivierungsstrategie für gesendete Nachrichten (Auflistung). Mögliche Werte sind "0"(keine Archivierung) und "1" (Übertragung der Archivierung gesendeter Nachrichten an einen SMTP-Server).<br /> </td> 
   <td> Byte<br /> </td> 
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
   <td> Autostart<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> compressBatchSize<br /> </td> 
   <td> Größe eines komprimierten Archivs: maximale Anzahl von Dateien in einem komprimierten Archiv.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 10000<br /> </td> 
  </tr> 
  <tr> 
   <td> compressionFormat<br /> </td> 
   <td> Komprimierungsformat, das bei der Archivierung (Auflistung) verwendet wird. Mögliche Werte sind "0"(keine Komprimierung) und "1"(komprimieren gesendeter Nachrichten im ZIP-Format).<br /> </td> 
   <td> Byte<br /> </td> 
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
   <td> Kennung des bei Prozessbeginn auszuführenden JavaScripts.<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Warnung zur Speicherbelegung: Warnhinweis bezüglich der von einem bestimmten Prozess verbrauchten RAM (in MB).<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Warnung zur Speicherbelegung: Warnung bezüglich der von einem bestimmten Prozess verbrauchten RAM (in MB).<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> pollDelay<br /> </td> 
   <td> Intervall in Sekunden zwischen 2 Archivierungsvorgängen.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Zeitpunkt des automatischen Neustarts des Prozesses. Siehe <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatischer Prozess-Neustart</a>.<br /> </td> 
   <td> String <br /> </td> 
   <td> "06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> purgeArchivesDelay<br /> </td> 
   <td> Anzahl Tage vor der Löschung der archivierten E-Mails.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 7<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Startpriorität. Module mit einer niedrigen Prioritätsziffer werden als erste gestartet und als letzte abgeschlossen. Das Syslogd-Modul muss daher die Priorität 0 aufweisen.<br /> </td> 
   <td> Kurz<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> smtpBccAddress<br /> </td> 
   <td> Archivieren des Zielziels<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> smtpEnableTLS<br /> </td> 
   <td> Aktivieren Sie die SMTPS-Unterstützung: Aktiviert den Versand von E-Mails im abgesicherten Modus (STARTTLS/SMTPS), wenn er vom Remote-Server unterstützt wird.<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> smtpNbConnection<br /> </td> 
   <td> Anzahl der Verbindungen zum SMTP-Archivierungsserver.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> smtpRelayAddress<br /> </td> 
   <td> Kommagetrennte Liste von DNS-Namen oder IP-Adressen der zu verwendenden SMTP-Relais. <br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> smtpRelayPort<br /> </td> 
   <td> IP-Port des SMTP-Servers<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 25<br /> </td> 
  </tr> 
 </tbody> 
</table>

## inMail {#inmail}

Im Folgenden finden Sie die verschiedenen Parameter der **inMail** Knoten. Dies ist die Konfiguration des Moduls E-Mail-Management.

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
   <td> Autostart<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> checkInstanceName<br /> </td> 
   <td> Überprüfen Sie den Instanznamen: Wenn "true", muss der Name der Adobe Campaign-Instanz, der in den Nachrichten-ID-Headern enthalten ist, mit dem der aktuellen Instanz übereinstimmen. <br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> defaultForwardAddress<br /> </td> 
   <td> Weiterleitungsadresse: Standard-E-Mail-Übertragungsadresse nicht von einer Regel verarbeitet. <br /> </td> 
   <td> String <br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> errorForwardAddress<br /> </td> 
   <td> Fehleradresse: Standardadresse zur Übertragung ungültiger E-Mails (ungültige MIME-Kodierung). <br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> ignoreSize<br /> </td> 
   <td> Ignorieren der Nachrichtengröße: wird verwendet, um die Größe einer von POP3-Servern zurückgegebenen Nachricht zu ignorieren. In diesem Fall erwartet das Modul einen "." am Ende der Nachrichten. <br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> inMailPeriodSec<br /> </td> 
   <td> Nachrichtenlesezeitraum: Abrufhäufigkeit der Nachrichtenwarteschlange.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> Kennung des bei Prozessbeginn auszuführenden JavaScripts.<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxBroadLog<br /> </td> 
   <td> Maximale Anzahl der zu aktualisierenden Protokolle: definiert die maximale Anzahl von Protokollmeldungen, die im Speicher aufbewahrt werden sollen, bevor die Datenbank aktualisiert wird.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 20<br /> </td> 
  </tr> 
  <tr> 
   <td> maxMsgPerSession<br /> </td> 
   <td> Im Laufe einer POP3-Sitzung maximal zu lesende Nachrichtenanzahl<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 200<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Warnung zur Speicherbelegung: Warnhinweis bezüglich der von einem bestimmten Prozess verbrauchten RAM (in MB).<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Warnung zur Speicherbelegung: Warnung bezüglich der von einem bestimmten Prozess verbrauchten RAM (in MB).<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSessionTTLSec<br /> </td> 
   <td> Sitzungsdauer: maximale Dauer der Nachrichtenverarbeitungssitzung.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> popMailPeriodSec<br /> </td> 
   <td> POP3-Abrufezeit<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> popQueueSize<br /> </td> 
   <td> Warteschlangengröße der gelesenen Nachrichten<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> popTimeoutSec<br /> </td> 
   <td> Zeitüberschreitung bei der Kommunikation mit dem POP3-Server. <br /> </td> 
   <td> Lang<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Zeitpunkt des automatischen Neustarts des Prozesses. Siehe <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatischer Prozess-Neustart</a>.<br /> </td> 
   <td> String <br /> </td> 
   <td> "06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> reloadPeriodSec<br /> </td> 
   <td> Intervall der Ladung der von der Datenbank abzurufenden Konten<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Startpriorität. Module mit einer niedrigen Prioritätsziffer werden als erste gestartet und als letzte abgeschlossen. Das Syslogd-Modul muss daher die Priorität 0 aufweisen.<br /> </td> 
   <td> Kurz<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

### msgDump {#msgdump}

Im **inMail > msgDump** Knoten konfigurieren Sie die folgenden Parameter. Dies ist die Konfiguration des Dump verarbeiteter Nachrichten.

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
   <td> dump<br /> </td> 
   <td> Speichern Sie alle eingehenden Nachrichten im Textformat. <br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> msgPath<br /> </td> 
   <td> Speicherpfad der Nachrichten<br /> </td> 
   <td> String <br /> </td> 
   <td> '/tmp/inMail'<br /> </td> 
  </tr> 
 </tbody> 
</table>

## interactiond {#interactiond}

Im Folgenden finden Sie die verschiedenen Parameter der **interactiond** Knoten. Dies ist die Konfiguration des SchreibDaemons für eingehende Interaktionsereignisse.

Weitere Informationen finden Sie unter [Interaction - Datenpuffer](../../installation/using/interaction---data-buffer.md).

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
   <td> Autostart<br /> </td> 
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
   <td> Kennung des bei Prozessbeginn auszuführenden JavaScripts<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Warnung zur Speicherbelegung: Warnhinweis bezüglich der von einem bestimmten Prozess verbrauchten RAM (in MB).<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Warnung zur Speicherbelegung: Warnung bezüglich der von einem bestimmten Prozess verbrauchten RAM (in MB).<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSharedEntries<br /> </td> 
   <td> Max. Anzahl der im gemeinsamen Speicher gespeicherten Ereignisse.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 25000<br /> </td> 
  </tr> 
  <tr> 
   <td> nextOffersSize<br /> </td> 
   <td> Maximale Anzahl an geeigneten Angeboten, die direkt im Anschluss an die Vorschläge kommen; zu statistischen Zwecken zu speichern.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Zeitpunkt des automatischen Neustarts des Prozesses. Siehe <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatischer Prozess-Neustart</a>.<br /> </td> 
   <td> String <br /> </td> 
   <td> "06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Startpriorität. Module mit einer niedrigen Prioritätsziffer werden als erste gestartet und als letzte abgeschlossen. Das Syslogd-Modul muss daher die Priorität 0 aufweisen.<br /> </td> 
   <td> Kurz<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> statsPeriod<br /> </td> 
   <td> Aggregationsdauer in Sekunden für die Antwortzeit-Statistiken. 0 bedeutet, dass die statistische Speicherung deaktiviert wurde.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> targetKeySize<br /> </td> 
   <td> Max. Anzahl der Zeichen, die im gemeinsamen Speicher zur Identifizierung von Einzelpersonen gespeichert werden.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 16<br /> </td> 
  </tr> 
 </tbody> 
</table>

## mta {#mta}

Im Folgenden finden Sie die verschiedenen Parameter der **mta** Knoten. Dies ist die Konfiguration der Versandagenten.

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
   <td> Autostart<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> dataLogPath<br /> </td> 
   <td> Pfad der gesendeten E-Mails speichern: Wenn nicht leer, der Pfad, in dem alle Quelldateien gesendeter E-Mails gespeichert werden. <br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> debugPath<br /> </td> 
   <td> Dump directory: Wenn nicht leer, kopieren Sie MIME-Hülls von gesendeten E-Mail-Nachrichten in dieses Verzeichnis. Dient zum Erschießen von Schwierigkeiten. <br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> dnsRequestLogDelayFrau<br /> </td> 
   <td> Verzögerung der DNS-Abfrageprotokolle: Zeit in Millisekunden, um die Protokolle anzuzeigen.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> errorPeriodSec<br /> </td> 
   <td> Häufigkeit der Fehlerstatistiken: Zeit zwischen der Erstellung von Statistiken und der Speicherung in der Datenbank. <br /> </td> 
   <td> Lang<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> Kennung des bei Prozessbeginn auszuführenden JavaScripts.<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> logEmailErrors<br /> </td> 
   <td> Erzeugt Fehlerstatistiken und speichert sie in der Datenbank<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> logLevel<br /> </td> 
   <td> Anzeigelevel der Lognachrichten Schweregrad der in die Datenbank geschriebenen Protokolle. Von MTA generierte Protokollmeldungen werden nicht immer in die Datenbank geschrieben. Mit diesem Parameter können Sie die Ebene definieren, von der aus Sie denken, dass eine Nachricht in die Datenbank geschrieben werden muss. Wenn Sie Stufe 2 definieren, werden auch Nachrichten der Stufe 1 und 0 geschrieben, während bei der Definition von Stufe 1 nur Nachrichten der Stufe 1 und 0 geschrieben werden. Mögliche Werte sind: 0 (errors), 1 (warning), 2 (info)<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> maxMemoryMb<br /> </td> 
   <td> Maximale Speicherkapazität in Megabyte, die ein MTA-Prozess verbrauchen darf. Bei Überschreiten muss der Vorgang gestoppt werden, um die Speicherkapazität freizugeben.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1024<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Warnung zur Speicherbelegung: Warnhinweis bezüglich der von einem bestimmten Prozess verbrauchten RAM (in MB).<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Warnung zur Speicherbelegung: Warnung bezüglich der von einem bestimmten Prozess verbrauchten RAM (in MB).<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> minConnectionsToLog<br /> </td> 
   <td> Zu berücksichtigende Verbindungsschwelle. Fehlerstatistiken werden für einen bestimmten Pfad nicht erzeugt, wenn die Gesamtzahl an Verbindungen seit der von errorPeriodSec bestimmten Dauer streng kleiner als diese Schwelle ist.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> minErrorsToLog<br /> </td> 
   <td> Zu berücksichtigender Fehlerschwellenwert: Fehlerstatistiken werden für einen bestimmten Pfad nicht generiert, wenn die Gesamtzahl der Fehler für den von errorPeriodSec angegebenen Zeitraum strikt unter dem Schwellenwert liegt.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> minMessagesToLog<br /> </td> 
   <td> Zu berücksichtigende Nachrichtenschwelle. Fehlerstatistiken werden für einen bestimmten Pfad nicht erzeugt, wenn die Gesamtzahl an gesendeten Nachrichten seit der von errorPeriodSec bestimmten Dauer streng kleiner als diese Schwelle ist.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
  <tr> 
   <td> notifRelay<br /> </td> 
   <td> Benachrichtigungsweiterleitung: HostName:Anschluss, der zum Weiterleiten von Benachrichtigungen verwendet wird.<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Zeitpunkt des automatischen Neustarts des Prozesses. Siehe <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatischer Prozess-Neustart</a>.<br /> </td> 
   <td> String <br /> </td> 
   <td> "06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> purgeDataLogDelay<br /> </td> 
   <td> Verzögerung vor dem Löschen archivierter E-Mails: Anzahl der Tage vor der Bereinigung archivierter E-Mails im Verzeichnis, das in dataLogPath angegeben ist.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 15<br /> </td> 
  </tr> 
  <tr> 
   <td> retryLostMessages<br /> </td> 
   <td> Verlorene Nachrichten wiederholen: Teile von Sendungen werden wiederholt, wenn der untergeordnete Prozess tot ist.<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Startpriorität. Module mit einer niedrigen Prioritätsziffer werden als erste gestartet und als letzte abgeschlossen. Das Syslogd-Modul muss daher die Priorität 0 aufweisen.<br /> </td> 
   <td> Kurz<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> signEmailLinks<br /> </td> 
   <td> Aktivieren Sie den Signaturmechanismus. Dies verbessert die Sicherheit bei Tracking-Links in E-Mails.<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> true<br /> </td> 
  </tr>
  <tr> 
   <td> statServerAddress<br /> </td> 
   <td> Adresse des Versandstatistiken-Servers, angegeben als 
    &lt;dns or="" ip=""&gt; 
      <code>[</code>: 
     &lt;port&gt; 
       <code>]</code>. Siehe 
      <a href="../../installation/using/email-deliverability.md#coordinates-of-the-statistics-server" target="_blank">Koordinaten des Statistikservers</a>. 
      <br /> 
     </td> 
   <td> String <br /> </td> 
   <td> Wenn der Standardanschluss nicht definiert ist, ist 7777.<br /> </td> 
  </tr> 
  <tr> 
   <td> statServerTLSSupport<br /> </td> 
   <td> TLS nach Domain aktivieren: aktiviert die durch MX konfigurierbaren TLS (erfordert einen aktuellen Statistikserver).<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> true <br /> </td> 
  </tr> 
  <tr> 
   <td> statServerVersion<br /> </td> 
   <td> Verwendete Protokollversion: Kommunikationsprotokollversion (1 für einen Server v5.11 und 6.0.2, 2 für einen Server v6.1).<br /> </td> 
   <td> String <br /> </td> 
   <td> Wenn nicht definiert, wird die neueste Version verwendet. <br /> </td> 
  </tr> 
  <tr> 
   <td> useMomentum<br /> </td> 
   <td> Wenn auf "true"gesetzt, verwendet Ihre Instanz die <a href="../../delivery/using/sending-with-enhanced-mta.md" target="_blank">Verbesserter MTA</a>.<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> <br /> </td>b 
  </tr>
  <tr> 
   <td> verifyMode<br /> </td> 
   <td> Überprüfungsmodus: aktiviert den Überprüfungsmodus (keine physische Übertragung von Nachrichten; für Simulationen und Tests verwendet werden).<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> workingPath<br /> </td> 
   <td> Arbeitsverzeichnis: Speicherort der temporären Dateien, die vom MTA zur Kommunikation mit seinen untergeordneten Prozessen verwendet werden.<br /> </td> 
   <td> String <br /> </td> 
   <td> '$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/mta/' <br /> </td> 
  </tr> 
  <tr> 
   <td> xMailer<br /> </td> 
   <td> X-Mailer-Feld: Wert des Felds 'X-Mailer' im SMTP-Mail-Header.<br /> </td> 
   <td> String <br /> </td> 
   <td> 'nlserver, Build $(PRODUCT_VERSION)'<br /> </td> 
  </tr>  
 </tbody> 
</table>

### cache {#cache}

Im **cache** Knoten konfigurieren Sie die folgenden Parameter. Dies ist die Konfiguration des lokalen Datei-Cache.

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
   <td> Recycling nach: Punkt in Sekunden, nach dem die Datei automatisch aus dem Cache gelöscht wird, um den Speicher wiederherzustellen.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 244800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSizeOnDiskMb<br /> </td> 
   <td> Maximale Größe des Cache-Speichers (MB)<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1024<br /> </td> 
  </tr> 
  <tr> 
   <td> purgePeriodSec<br /> </td> 
   <td> Bereinigungshäufigkeit: Zeitraum in Sekunden zwischen den Ausführungen des Cache-Bereinigungsmechanismus.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 3600<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Relais {#relay}

Im **mta > relay** Knoten konfigurieren Sie die folgenden Parameter. Dies ist die Konfiguration des E-Mail-Servers für den Nachrichtenversand.

Die Liste wird auf die gleiche Weise wie eine Liste von MX gehandhabt, die von einer MX-DNS-Abfrage zurückgegeben wird. Normalerweise wird der erste MX verwendet, solange er verfügbar ist, dann der nächste verwendet und so weiter.

Weitere Informationen finden Sie unter [SMTP-Relais](../../installation/using/configuring-campaign-server.md#smtp-relay).

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
   <td> Kommagetrennte Liste von DNS-Namen oder IP-Adressen der zu verwendenden SMTP-Relais. <br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> Port<br /> </td> 
   <td> IP-Port des SMTP-Servers<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 25<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Übergeordnet {#master}

Im **mta > Übergeordnet** Knoten konfigurieren Sie die folgenden Parameter. Dies ist die Konfiguration des Hauptservers.

Weitere Informationen finden Sie in diesem Abschnitt [Abschnitt](../../installation/using/configuring-campaign-server.md#mta-child-processes).

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
   <td> Intervall, in der die zu sendenden Vorgänge aus der Datenbank abgerufen werden Intervall in Sekunden zwischen zwei Datenbankabfragen durch den MTA. Der MTA ruft in regelmäßigen Abständen die ausstehenden Sendungen ab. Der Wert kommt nur zum Tragen, wenn kein Vorgang zur Verarbeitung ansteht. Sollte bei der vorhergehenden Abfrage für einen Vorgang kein untergeordneter Server zur Verfügung gestanden haben, wird das Intervall automatisch auf 1 Sekunde gesetzt, um den ausstehenden Vorgang so schnell wie möglich verarbeiten zu können, d. h. sobald ein untergeordneter Server zur Verfügung steht. Dies bedeutet nicht, dass jede Sekunde eine Datenbankabfrage durchgeführt wird. Dies geschieht nur, wenn mindestens ein untergeordneter Server verfügbar ist.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
  <tr> 
   <td> dataBaseRetryDelaySec<br /> </td> 
   <td> Wartezeit nach fehlgeschlagener Verbindung mit der Datenbank Sollte die Verbindung mit der Datenbank fehlschlagen, handelt es sich zumeist um ein Problem mit dem Datenbankserver. Er kann z. B. wegen Instandhaltungsmaßnahmen gestoppt worden sein. Der Parameter DataBaseRetryDelay legt die Wartezeit in Sekunden fest, bevor ein erneuter Anmeldeversuch unternommen wird.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> domainKeysReloadPeriodSec<br /> </td> 
   <td> Gültigkeit des Cache-Speichers der privaten Schlüssel (DomainKeys). Die für die Signatur gemäß der DomainKeys-Empfehlung (http://antispam.yahoo.com/domainkeys) verwendeten privaten Schlüssel werden in der Datenbank in Form von Optionen gespeichert. Der Parameter domainKeysReloadPeriodSec gibt an, wie lange der MTA diese Schlüssel im Cache speichern darf (in Sekunden). Nach Ablauf dieser Dauer müssen alle Schlüssel erneut aus der Datenbank geladen werden<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSpareServers<br /> </td> 
   <td> Maximale Anzahl an untergeordneten Servern Bezeichnet die maximale Anzahl an laufenden Servern. Es ist nicht empfehlenswert, ohne wirklichen Bedarf eine zu große Anzahl festzulegen, da dies unnötig Speicherkapazität beansprucht. Durch Analyse der Speicherkapazität während eines Versands können Sie feststellen, ob der angegebene Wert dem Bedarf entspricht. Die beanspruchte Kapazität darf nie ein Drittel des insgesamt verfügbaren Speichers Ihres Geräts übersteigen, da andernfalls Ihr SWAP einbezogen wird. Siehe <a href="../../installation/using/configuring-campaign-server.md#mta-child-processes" target="_blank">Untergeordnete MTA-Prozesse</a>.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> minSpareServers<br /> </td> 
   <td> Minimale Anzahl an untergeordneten Servern Der MTA versucht, mindestens die verfügbaren Server im Betrieb zu halten. Wenn weniger Server laufen, werden neue im Rhythmus von einem Server pro Sekunde gestartet, bis die angegebene Anzahl erreicht ist.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> startSpareServers<br /> </td> 
   <td> Anzahl an untergeordneten Servern beim Start Die Anzahl an untergeordneten Servern wird dynamisch kontrolliert. Beim Start des MTAs erstellt dieser die hier bestimmte Anzahl an untergeordneten Servern. Normalerweise werden untergeordnete Server maximal im Rhythmus von einem Server pro Sekunde gestartet, um das System nicht zu überlasten. Beim Start des MTAs kommt diese Beschränkung jedoch nicht zum Tragen und die untergeordneten Server werden so schnell wie möglich hinzugeschaltet.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
 </tbody> 
</table>

### child {#child}

Im **mta > child** Knoten konfigurieren Sie die folgenden Parameter. Dies ist die Konfiguration der untergeordneten Server.

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
   <td> Optionale Befehlzeilenargumente <br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> idleChildTimeoutSec<br /> </td> 
   <td> Timeout inaktiver untergeordneter Sitzungen Sollte ein untergeordneter Server länger als für diesen Parameter definiert inaktiv bleiben, wird er automatisch beendet, um unnötige Ressourcenbeanspruchung zu vermeiden.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> maxAgeSec<br /> </td> 
   <td> Maximale Rückhaltedauer einer Nachricht. Wenn eine vorbereitete Nachricht aufgrund der Flusskontrolle oder von MTA-Verbindungsproblemen nicht gesendet werden kann, wird sie bis zum nächsten Sendeversuch ausgesetzt.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxGCMConnectPerChild<br /> </td> 
   <td> Maximale Anzahl paralleler HTTP-Anfragen an FCM von jedem untergeordneten Server initiiert.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 8<br /> </td> 
  </tr> 
  <tr> 
   <td> maxMsgPerChild<br /> </td> 
   <td> Maximale Nachrichtenanzahl pro untergeordnetem Server Jedes untergeordnete MTA-Exemplar verarbeitet diese Anzahl an Nachrichten und stirbt. Die angegebene Anzahl muss gewährleisten, dass auch eine nachlässige Speicherverwaltung keine negativen Konsequenzen verursachen kann. Selbst wenn im MTA keine bekannten Lecks vorhanden sind, können XSL-Stylesheets oder JavaScript-Codes der Nachrichten hiervon betroffen sein.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 5000000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxWaitingMessages<br /> </td> 
   <td> Ausstehende Nachrichten: Maximale Anzahl an Nachrichten, die im Speicher warten, um zugestellt zu werden. <br /> </td> 
   <td> Lang<br /> </td> 
   <td> 2000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxWorkingSetMb<br /> </td> 
   <td> Maximale Speicherkapazität in Megabyte, die ein untergeordneter Server verbrauchen darf. Bei Überschreiten muss der Vorgang gestoppt werden, um die Speicherkapazität freizugeben. <br /> </td> 
   <td> Lang<br /> </td> 
   <td> 128<br /> </td> 
  </tr> 
  <tr> 
   <td> soapConnectorTimeoutSec<br /> </td> 
   <td> Timeout (in Sekunden), nach dem eine SOAP-Verbindung eines Versand-Connectors unterbrochen wird<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> startWithFirstMX<br /> </td> 
   <td> Immer mit dem prioritären MX beginnen.<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> timeToLive<br /> </td> 
   <td> Maximale Anzahl an aufeinanderfolgenden Versuchen<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 48<br /> </td> 
  </tr> 
 </tbody> 
</table>

Im **mta > child > smtp** Knoten konfigurieren Sie die folgenden Parameter. Dies ist die Konfiguration von SMTP-Sitzungen.

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
   <td> Aktiviert den gesicherten E-Mail-Versand (STARTTLS/SMTPS), wenn vom Remote-Server unterstützt<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> idleSessionTimeoutSec<br /> </td> 
   <td> Timeout inaktiver Sitzungen Dieser Parameter wird nur verwendet, wenn eine Sitzung zur Übertragung verschiedener Nachrichten an eine Domain genutzt wird. Die vom MTA verwendete SMTP-Sitzung wird nach erfolgter Nachrichtenübermittlung nicht automatisch geschlossen. Wenn eine Nachricht für dieselbe Domain versandfertig ist, wird dieselbe SMTP-Sitzung wiederverwendet und der MTA schließt die Sitzung nicht. Der Parameter IdleSessionTimeout gibt an, wie lange eine SMTP-Sitzung in Erwartung einer weiteren Nachrichtenübermittlung aktiv bleiben kann. Läuft die festgelegte Dauer ohne erneute Übertragung ab, wird die Sitzung automatisch geschlossen.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> initialDelaySec<br /> </td> 
   <td> Anfangswartezeit vor einem erneuten Verbindungsversuch. Diese Verzögerung wird bei jedem Verbindungsfehler verdoppelt.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSessionsPerChild<br /> </td> 
   <td> Maximale Anzahl an SMTP-Sitzungen pro untergeordnetem Server Um eine Nachricht zuzustellen, initiiert der MTA eine SMTP-Verbindung zum Empfänger-MTA. Die maximale Anzahl an simultan auf demselben untergeordneten Server aktiven SMTP-Sitzungen ist durch diesen Wert begrenzt. Das Produkt aus diesem Wert und maxSpareServers entspricht der maximalen Anzahl an parallel auf einen untergeordneten Server gesendeten Nachrichten.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
 </tbody> 
</table>

Im **mta > child > smtp > IPAffinity** Knoten konfigurieren Sie die folgenden Parameter. Dies ist die Konfiguration der Verwaltung von Affinitäten mit IP-Adressen für optimierten ausgehenden SMTP-Traffic.

Weitere Informationen finden Sie unter [Liste der zu verwendenden IP-Adressen](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use) und [Verwalten des ausgehenden SMTP-Traffics mit Affinitäten](../../installation/using/configuring-campaign-server.md#managing-outbound-smtp-traffic-with-affinities).

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
   <td> Domänenname: lokaler Domänenname, der mit der IP-Adresse verknüpft ist. Wird bei der Ausgabe eines SMTP-HELO-Befehls verwendet.<br /> </td> 
   <td> String <br /> </td> 
  </tr> 
  <tr> 
   <td> name<br /> </td> 
   <td> Logischer Name: Namen, die von Benutzern mit der Affinität verknüpft sind. Namen werden durch Semikolons getrennt.<br /> </td> 
   <td> String <br /> </td> 
  </tr> 
 </tbody> 
</table>

Im **mta > child > smtp > IP** Knoten konfigurieren Sie die folgenden Parameter.

Weitere Informationen finden Sie unter [Liste der zu verwendenden IP-Adressen](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use).

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
   <td> Zugeordnete physische Adresse, z. B. '192.168.0.1'<br /> </td> 
   <td> String <br /> </td> 
  </tr> 
  <tr> 
   <td> publicId<br /> </td> 
   <td> Kennung der zugeordneten öffentlichen Adresse. Wird vom Statistikserver als Schlüssel verwendet. Muss numerisch sein. Weitere Informationen finden Sie in diesem <a href="../../installation/using/email-deliverability.md#managing-ip-addresses">Abschnitt</a>.<br /> </td> 
   <td> Lang<br /> </td> 
  </tr> 
  <tr> 
   <td> Gewichtung.<br /> </td> 
   <td> Bestimmt die Verwendungsfrequenz dieser IP-Adresse im Vergleich zu anderen (je höher die Gewichtung, desto höher die Frequenz)<br /> </td> 
   <td> Lang<br /> </td> 
  </tr> 
  <tr> 
   <td> includeDomains<br /> </td> 
   <td> Maske für einzuschließende Domains, durch Kommata getrennt.<br /> </td> 
   <td> String <br /> </td> 
  </tr> 
  <tr> 
   <td> excludeDomains<br /> </td> 
   <td> Maske für auszuschließende Domains, durch Kommata getrennt.<br /> </td> 
   <td> String <br /> </td> 
  </tr> 
  <tr> 
   <td> heloHost<br /> </td> 
   <td> Name des der IP-Adresse entsprechenden Geräts. Wird vom SMTP-HELO-Befehl verwendet.<br /> </td> 
   <td> String <br /> </td> 
  </tr> 
 </tbody> 
</table>

## nmac {#nmac}

Im Folgenden finden Sie die verschiedenen Parameter der **nmac** Knoten. Dies ist die Konfiguration von für Push-Benachrichtigungsversand.

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
   <td> useHTTProxy<br /> </td> 
   <td> Use HTTP proxy defined in shared/proxyHTTP. <br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Relais {#relay-1}

Im Folgenden finden Sie die verschiedenen Parameter der **nmac > relay** Knoten. Dadurch wird die Verwendung eines Relais für den Nachrichtenversand (iOS HTTP2-Connector) konfiguriert.

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
   <td> Relationship Port<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 443<br /> </td> 
  </tr> 
  <tr> 
   <td> trustedCertsChain<br /> </td> 
   <td> Zertifikatskette (PEM-Datei). Nützlich bei der Verwendung eines Tracking-Servers.<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

## pipelined {#pipelined}

Im Folgenden finden Sie die verschiedenen Parameter der **pipelined** Knoten. Dies ist die Konfiguration des Ereignisverarbeitungsmoduls für Pipeline-Dienste.

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
   <td> Name der Anwendung, die in der Developer Connection beim Speichern des öffentlichen Schlüssels generiert wurde. <br /> </td> 
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
   <td> URL für den Erhalt eines Gateway-Tokens.<br /> </td> 
   <td> String <br /> </td> 
   <td> "https://api.omniture.com' <br /> </td> 
  </tr> 
  <tr> 
   <td> authPrivateKey<br /> </td> 
   <td> Privater Schlüssel für den Erhalt der Tokens (mit AES verschlüsselt, XtkKey-Option).<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Autostart <br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> disableAuth<br /> </td> 
   <td> Authentifizierung deaktivieren: Verbindung zu Pipeline-Diensten ohne Authentifizierung herstellen. <br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> discoverPipelineEndpoint<br /> </td> 
   <td> URL zum Auffinden der Pipeline-Services-URL.<br /> </td> 
   <td> String <br /> </td> 
   <td> "https://producer-pipeline-pnw.adobe.net'<br /> </td> 
  </tr> 
  <tr> 
   <td> dumpStatePeriodSec<br /> </td> 
   <td> Status-Speicherzeitraum: Häufigkeit, mit der die internen Informationen des Prozesses in einer Datei gespeichert werden. Inaktiv, wenn 0. <br /> </td> 
   <td> Lang<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> forcedPipelineEndpoint<br /> </td> 
   <td> Listening-URL: erzwingen die Listening-URL der Pipeline-Dienste. <br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> Kennung des bei Prozessbeginn auszuführenden JavaScripts.<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Warnung zur Speicherbelegung: Warnhinweis bezüglich der von einem bestimmten Prozess verbrauchten RAM (in MB).<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Warnung zur Speicherbelegung: Warnung bezüglich der von einem bestimmten Prozess verbrauchten RAM (in MB).<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> monitorServerPort<br /> </td> 
   <td> Status-Server-Port: HTTP-Server-Anschluss, über den Sie den Status des Prozesses abfragen können. Inaktiv, wenn 0.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 7781<br /> </td> 
  </tr> 
  <tr> 
   <td> pointerFlushMessageCount<br /> </td> 
   <td> Zeiger wird bei Erreichen der angegebenen Nachrichtenanzahl in der Datenbank gespeichert.<br /> </td> 
   <td> <br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
  <tr> 
   <td> pointerFlushPeriodSec<br /> </td> 
   <td> Verzögerung vor der Speicherung des Zeigers: Der Zeiger wird mindestens einmal während dieses Zeitraums in der Datenbank gespeichert (nützlich bei geringer Aktivität).<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Zeitpunkt des automatischen Neustarts des Prozesses. Siehe <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatischer Prozess-Neustart</a>.<br /> </td> 
   <td> String <br /> </td> 
   <td> "06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> processingJSThreads<br /> </td> 
   <td> Anzahl an Threads für die Verarbeitung von Ereignissen mit einem personalisierten JavaScript-Connector<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> processingThreads<br /> </td> 
   <td> Anzahl an Threads für die Verarbeitung von Ereignissen<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> retryPeriodSec<br /> </td> 
   <td> Intervall zwischen Verarbeitungsversuchen im Fall eines Fehlschlags.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
  <tr> 
   <td> retryValiditySec<br /> </td> 
   <td> Nach diesem Zeitraum wird abgebrochen: das Ereignis abbrechen, wenn die Verarbeitung nach diesem Zeitraum weiterhin fehlschlägt.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Startpriorität. Module mit einer niedrigen Prioritätsziffer werden als erste gestartet und als letzte abgeschlossen. Das Syslogd-Modul muss daher die Priorität 0 aufweisen.<br /> </td> 
   <td> Kurz<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Reparatur {#repair}

Im Folgenden finden Sie die verschiedenen Parameter der **Reparatur** Knoten. Dies ist die Konfiguration des Datenbankreparaturmoduls.

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
   <td> reparierenActionDelayMin<br /> </td> 
   <td> Reparaturmodul für Versandaktionen: Verzögerung (in Minuten), nach der Sendungen vom Reparaturmodul verarbeitet werden können. <br /> </td> 
   <td> Lang<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
 </tbody> 
</table>

## securityZone {#securityzone}

Im Folgenden finden Sie die verschiedenen Parameter der **securityZone** Knoten.

Weitere Informationen finden Sie unter [Sicherheitszonen definieren](../../installation/using/security-zones.md).

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
   <td> Debug-Modus in Webanwendungen zulassen.<br /> </td> 
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
   <td> Autorisieren Sie die Verwendung von HTTP für die Benutzeranmeldung.<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> allowSQLInjection<br /> </td> 
   <td> Autorisieren Sie die Verwendung von SQLDATA in Ausdrücken.<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> allowUserPassword<br /> </td> 
   <td> Benutzer-/Kennwort-Sitzungstoken zulassen.<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> label<br /> </td> 
   <td> Titel<br /> </td> 
   <td> String <br /> </td> 
   <td> NewLabel()<br /> </td> 
  </tr> 
  <tr> 
   <td> name<br /> </td> 
   <td> Interner Name<br /> </td> 
   <td> String <br /> </td> 
   <td> NewName() <br /> </td> 
  </tr> 
  <tr> 
   <td> sessionTokenOnly<br /> </td> 
   <td> Verwenden Sie nicht das Security-Token.<br /> </td> 
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

Dies ist die Standardkonfiguration:

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

### subNetwork {#subnetwork}

Im Folgenden finden Sie die verschiedenen Parameter der **securityZone > subNetwork** Knoten.

Weitere Informationen finden Sie unter [Sicherheitszonen definieren](../../installation/using/security-zones.md).

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
   <td> label<br /> </td> 
   <td> Titel<br /> </td> 
   <td> String <br /> </td> 
   <td> NewLabel()<br /> </td> 
  </tr> 
  <tr> 
   <td> mask<br /> </td> 
   <td> Maske oder Adresse<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> name<br /> </td> 
   <td> Interner Name<br /> </td> 
   <td> String <br /> </td> 
   <td> NewName() <br /> </td> 
  </tr> 
  <tr> 
   <td> Proxy<br /> </td> 
   <td> Maske oder Adresse des vom Sub-Netzwerk verwendeten (Reverse) Proxys, um auf die Instanz zuzugreifen. In diesem Fall wird der Header 'X-Forwarded-For' anstelle des Proxys getestet.<br /> </td> 
   <td> String <br /> </td> 
   <td> 127,0,0,1 <br /> </td> 
  </tr> 
 </tbody> 
</table>

## sms {#sms}

Im Folgenden finden Sie die verschiedenen Parameter der **sms** Knoten. Dies ist die Konfiguration des eingehenden SMS-Verwaltungsmoduls.

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
   <td> Autostart<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> dataRetentionDays<br /> </td> 
   <td> Maximale Rückhaltedauer der Arbeitsdateien des SMPP-Connectors (in Tagen)<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> dataSizeMo<br /> </td> 
   <td> Maximale Größe in MB der SMPP-Arbeitsdateien<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 512<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> Kennung des bei Prozessbeginn auszuführenden JavaScripts.<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> keepAlivePeriod<br /> </td> 
   <td> Wiederholung des Sitzungskontinuitätsrahmens: max. Zeitraum in Sekunden zwischen zwei Frames, um darauf hinzuweisen, dass die empfangende Sitzung weiterhin aktiviert ist.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 25<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Warnung zur Speicherbelegung: Warnhinweis bezüglich der von einem bestimmten Prozess verbrauchten RAM (in MB).<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Warnung zur Speicherbelegung: Warnung bezüglich der von einem bestimmten Prozess verbrauchten RAM (in MB).<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> pollPeriod<br /> </td> 
   <td> Suchhäufigkeit: Zeitraum der SMS-Kontoabfrage.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Zeitpunkt des automatischen Neustarts des Prozesses. Siehe <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatischer Prozess-Neustart</a>.<br /> </td> 
   <td> String <br /> </td> 
   <td> "06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> reloadPeriod<br /> </td> 
   <td> Häufigkeit der Kontoneuladung: Datenbank-Neuladungshäufigkeit der abzurufenden Konten.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Startpriorität. Module mit einer niedrigen Prioritätsziffer werden als erste gestartet und als letzte abgeschlossen. Das Syslogd-Modul muss daher die Priorität 0 aufweisen.<br /> </td> 
   <td> Kurz<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> srReadDelay<br /> </td> 
   <td> Anzahl der Sekunden für die SR-Verarbeitung: nur SRs mit einem Wiederherstellungsdatum, das vor der aktuellen Zeit liegt, abzüglich der von srReadDelay angegebenen Dauer in Sekunden. <br /> </td> 
   <td> Lang<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> timeout<br /> </td> 
   <td> Kommunikations-Timeout mit dem SMS-Gateway<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
 </tbody> 
</table>

### netsize {#netsize}

Im Folgenden finden Sie die verschiedenen Parameter der **sms > netsize** Knoten.

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
   <td> Timeout (in Sekunden) beim Netsize-Verbindungsaufbau.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
 </tbody> 
</table>

## stat {#stat}

Im Folgenden finden Sie die verschiedenen Parameter der **stat** Knoten. Dies ist die Konfiguration des MTA-Statistikmoduls.

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
   <td> Autostart<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> Kennung des bei Prozessbeginn auszuführenden JavaScripts.<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Warnung zur Speicherbelegung: Warnhinweis bezüglich der von einem bestimmten Prozess verbrauchten RAM (in MB).<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Warnung zur Speicherbelegung: Warnung bezüglich der von einem bestimmten Prozess verbrauchten RAM (in MB).<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> Port<br /> </td> 
   <td> Server-Listen-Port. Weitere Informationen finden Sie in diesem <a href="../../installation/using/email-deliverability.md#definition-of-the-server-port">Abschnitt</a>.<br /> </td> 
   <td> Kurz<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Zeitpunkt des automatischen Neustarts des Prozesses. Siehe <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatischer Prozess-Neustart</a>.<br /> </td> 
   <td> String <br /> </td> 
   <td> "06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Startpriorität. Module mit einer niedrigen Prioritätsziffer werden als erste gestartet und als letzte abgeschlossen. Das Syslogd-Modul muss daher die Priorität 0 aufweisen.<br /> </td> 
   <td> Kurz<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## syslogd {#syslogd}

Im Folgenden finden Sie die verschiedenen Parameter der **syslogd** Knoten. Dies ist die Konfiguration des Protokollverwaltungsmoduls.

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
   <td> Autostart<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> Kennung des bei Prozessbeginn auszuführenden JavaScripts.<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxFileSizeMb<br /> </td> 
   <td> Maximale Größe in MB für eine Protokolldatei. <br /> </td> 
   <td> Lang<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> maxNumberOfLoginsFiles<br /> </td> 
   <td> Maximale Anzahl der beizubehaltenden logins.log-Dateien. <br /> </td> 
   <td> Lang<br /> </td> 
   <td> 365<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Warnung zur Speicherbelegung: Warnhinweis bezüglich der von einem bestimmten Prozess verbrauchten RAM (in MB).<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Warnung zur Speicherbelegung: Warnung bezüglich der von einem bestimmten Prozess verbrauchten RAM (in MB).<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Zeitpunkt des automatischen Neustarts des Prozesses. Siehe <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatischer Prozess-Neustart</a>.<br /> </td> 
   <td> String <br /> </td> 
   <td> "06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Startpriorität. Module mit einer niedrigen Prioritätsziffer werden als erste gestartet und als letzte abgeschlossen. Das Syslogd-Modul muss daher die Priorität 0 aufweisen.<br /> </td> 
   <td> Kurz<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## tracking {#tracking}

Im Folgenden finden Sie die verschiedenen Parameter der **tracking** Knoten. Dies ist die Konfiguration des Tracking-Servers.

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
   <td> Autostart<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> blockRedirectForUnsignedTrackingLink<br /> </td> 
   <td> Deaktivieren Sie fehlerhafte URLs, die von früheren Builds generiert wurden.<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> ConsolidationPeriodSec<br /> </td> 
   <td> Konsolidierungszeitraum<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> dedupOpenPeriodMin<br /> </td> 
   <td> Öffnungen deduplizieren: Entfernen Sie doppelte Öffnungs-Trackinglogs, um die Auswirkungen von E-Mail-Vorschauen in E-Mail-Lesern wie Outlook zu begrenzen.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> errorIgnorePercent<br /> </td> 
   <td> Bis zu X % der Fehler ignorieren: Aktualisieren Sie die Trackingindikatoren nicht, solange das Verhältnis der nicht bereits berücksichtigten Zeitschriften diesen Wert nicht erreicht. <br /> </td> 
   <td> Byte<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> errorIgnorePeriod<br /> </td> 
   <td> Aktualisieren Sie die Fehlerindikatoren: maximale Dauer, bevor Fehlerindikatoren neu berechnet werden.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
  <tr> 
   <td> indicatorsDuration<br /> </td> 
   <td> Kennzahlen berechnen während: Dauer nach dem Gültigkeitsdatum eines Versands, nach dem die konsolidierten Indikatoren nicht mehr berechnet werden.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 2592000<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> Kennung des bei Prozessbeginn auszuführenden JavaScripts <br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> logCountPerRequest<br /> </td> 
   <td> Anzahl der pro Aufruf des Remote-Trackingservers abgerufenen Logs.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Warnung zur Speicherbelegung: Warnhinweis bezüglich der von einem bestimmten Prozess verbrauchten RAM (in MB).<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Warnung zur Speicherbelegung: Warnung bezüglich der von einem bestimmten Prozess verbrauchten RAM (in MB).<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> phishbowlServiceAPIKey<br /> </td> 
   <td> API-Schlüssel für die Phishbowl Service Endpoint-Integration. Dadurch wird die Umleitung von falsch formatierten URLs geschützt, die aus älteren Builds generiert wurden. <br /> </td> 
   <td> Lang<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> phishbowlServiceEndpoint<br /> </td> 
   <td> Endpunkt für die Phishbowl Service-Endpoint-Integration. Dadurch wird die Umleitung von falsch formatierten URLs geschützt, die aus älteren Builds generiert wurden.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Zeitpunkt des automatischen Neustarts des Prozesses. Siehe <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatischer Prozess-Neustart</a>.<br /> </td> 
   <td> String <br /> </td> 
   <td> "06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Startpriorität. Module mit einer niedrigen Prioritätsziffer werden als erste gestartet und als letzte abgeschlossen. Das Syslogd-Modul muss daher die Priorität 0 aufweisen.<br /> </td> 
   <td> Kurz<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> trackingIgnorePercent<br /> </td> 
   <td> Ignorieren Sie bis zu X % des Trackings: Aktualisieren Sie die Trackingindikatoren nicht, solange das Verhältnis der nicht bereits berücksichtigten Zeitschriften diesen Wert nicht erreicht.<br /> </td> 
   <td> Byte<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> trackingIgnorePeriod<br /> </td> 
   <td> Aktualisierung der Trackingindikatoren: maximale Dauer, bevor Trackingindikatoren neu berechnet werden.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
  <tr> 
   <td> userAgentCacheSize<br /> </td> 
   <td> Größe des Cache für die Browserkennung.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 500<br /> </td> 
  </tr> 
 </tbody> 
</table>

## trackinglogd {#trackinglogd}

Im Folgenden finden Sie die verschiedenen Parameter der **trackinglogd** Knoten. Dies ist die Konfiguration des Trackinglog-SchreibDaemons.

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
   <td> Autostart<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> Kennung des bei Prozessbeginn auszuführenden JavaScripts <br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxCreateFileRetry<br /> </td> 
   <td> Maximale Wiederholungsversuche beim Schreiben: maximale Anzahl von Dateien, die erstellt werden können, wenn das Schreiben in Protokolldateien fehlschlägt.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> maxLogsSizeOnDiskMb<br /> </td> 
   <td> Maximale Protokollgröße: maximaler Speicherplatz, der von Protokollen auf der Festplatte verwendet wird (in MB). Darf nicht kleiner als 100 MB sein. <br /> </td> 
   <td> Lang<br /> </td> 
   <td> 500<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Warnung zur Speicherbelegung: Warnhinweis bezüglich der von einem bestimmten Prozess verbrauchten RAM (in MB).<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Warnung zur Speicherbelegung: Warnung bezüglich der von einem bestimmten Prozess verbrauchten RAM (in MB).<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSharedLogs<br /> </td> 
   <td> Maximale Protokollanzahl: Maximale Anzahl der Protokolle, die im gemeinsamen Speicher gespeichert sind. Darf nicht weniger als 10000 sein. <br /> </td> 
   <td> Lang<br /> </td> 
   <td> 25000<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Zeitpunkt des automatischen Neustarts des Prozesses. Siehe <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatischer Prozess-Neustart</a>.<br /> </td> 
   <td> String <br /> </td> 
   <td> "06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> purgeLogsPeriod<br /> </td> 
   <td> Anzahl der Protokolle vor der Bereinigung: Anzahl der Protokolle, die vor Beginn der Bereinigung der Protokolldateien eingefügt wurden. Darf nicht unter 50000 liegen.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 50000<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Startpriorität. Module mit einer niedrigen Prioritätsziffer werden als erste gestartet und als letzte abgeschlossen. Das Syslogd-Modul muss daher die Priorität 0 aufweisen.<br /> </td> 
   <td> Kurz<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> webTrackingParamSize<br /> </td> 
   <td> Maximale Zeichenanzahl der Webtrackingparameter im geteilten Speicher.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 64<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Web {#web}

Im Folgenden finden Sie die verschiedenen Parameter der **Web** Knoten. Dies ist die Konfiguration des Webmoduls.

Weitere Informationen finden Sie in diesem Abschnitt [Abschnitt](configuring-campaign-server.md#default-port-for-tomcat).

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
   <td> Optionen der als String übergebenen JVM<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> MaxThreads<br /> </td> 
   <td> Maximale Thread-Anzahl.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 75<br /> </td> 
  </tr> 
  <tr> 
   <td> MinSpareThreads<br /> </td> 
   <td> Minimale Thread-Anzahl<br /> </td> 
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
   <td> Autostart<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> controlPort<br /> </td> 
   <td> Überwachungsanschluss von Tomcat: verweisen auf <a href="configure-tomcat.md" target="_blank">Tomcat konfigurieren</a>.<br /> </td> 
   <td> Kurz<br /> </td> 
   <td> 8005<br /> </td> 
  </tr> 
  <tr> 
   <td> httpPort<br /> </td> 
   <td> Tomcat HTTP-Listening-Port: verweisen auf <a href="configure-tomcat.md" target="_blank">Tomcat konfigurieren</a>.<br /> </td> 
   <td> Kurz<br /> </td> 
   <td> 8080<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> Kennung des bei Prozessbeginn auszuführenden JavaScripts.<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxDeliveryQueueSize<br /> </td> 
   <td> Größe der Warteschlange für SubmitDelivery-Aufrufe: Maximale Anzahl der SOAP-Aufrufe von SubmitDelivery, die in die Warteschlange gestellt werden können.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 50<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Warnung zur Speicherbelegung: Warnhinweis bezüglich der von einem bestimmten Prozess verbrauchten RAM (in MB).<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Warnung zur Speicherbelegung: Warnhinweis bezüglich der von einem bestimmten Prozess verbrauchten RAM (in MB)<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> notifRelay<br /> </td> 
   <td> Benachrichtigungsweiterleitung: HostName:Port zur Aktivierung der Weiterleitung von Benachrichtigungen.<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Zeitpunkt des automatischen Neustarts des Prozesses. Siehe <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatischer Prozess-Neustart</a>.<br /> </td> 
   <td> String <br /> </td> 
   <td> "06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Startpriorität. Module mit einer niedrigen Prioritätsziffer werden als erste gestartet und als letzte abgeschlossen. Das Syslogd-Modul muss daher die Priorität 0 aufweisen.<br /> </td> 
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

### jsp {#jsp}

Im Folgenden finden Sie die verschiedenen Parameter der **web > jsp** Knoten. Dies ist die Konfiguration der von den JSPs verwendeten Parameter.

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
   <td> debug<br /> </td> 
   <td> Ausführung von JSP im Debug-Modus oder nicht.<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> downloadPath<br /> </td> 
   <td> Ordner herunterladen: Download-Pfad der Installationsprogramme für die Clientkonsolen.<br /> </td> 
   <td> String <br /> </td> 
   <td> '$(XTK_INSTALL_DIR)/datakit/nl/eng/jsp'<br /> </td> 
  </tr> 
  <tr> 
   <td> foFileName<br /> </td> 
   <td> Pfad der .fo-Datei<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> soapRouter<br /> </td> 
   <td> URL des SOAP-Routers (http://myserver/xxx, http://jni oder mailto:xxx).<br /> </td> 
   <td> String <br /> </td> 
   <td> "http://jni'<br /> </td> 
  </tr> 
 </tbody> 
</table>

Die **web > jsp > classpath** -Knoten enthält die Liste aller Klassenpfade, die beim Starten von JVM verwendet werden sollen. Dies ist die Standardkonfiguration:

```
'$(XTK_INSTALL_DIR)/tomcat-8/bin/bootstrap.jar
          $(XTK_INSTALL_DIR)/tomcat-8/bin/tomcat-juli.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/tomcat-coyote.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/tomcat-util.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/tomcat-api.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/servlet-api.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/jsp-api.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/el-api.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/annotations-api.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/catalina.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/websocket-api.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/tomcat7-websocket.jar
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

### jssp {#jssp}

Im Folgenden finden Sie die verschiedenen Parameter der **web > jssp** Knoten. Dies ist die Konfiguration der von den JSSPs verwendeten Parameter.

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
   <td> Aktiviert die Garbage Collection des JavaScript-Kontexts nach jeder Abfrage<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> timeToLive<br /> </td> 
   <td> Maximale Anzahl von Seiten, die von einem JavaScript-Kontext bereitgestellt werden. <br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
 </tbody> 
</table>

Die **web > jsp > classpath** -Knoten enthält die Liste aller Klassenpfade, die beim Starten von JVM verwendet werden sollen.

### Relais {#relay-2}

Im Folgenden finden Sie die verschiedenen Parameter der **web > relay** Knoten. Dies ist die Konfiguration des Relais für HTTP-Anfragen zwischen zwei Bereichen.

Weitere Informationen finden Sie in diesem Abschnitt [Abschnitt](../../installation/using/deploying-an-instance.md#synchronizing-public-resources).

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
   <td> Startet das HTTP-Weiterleitungsmodul im Webserver im Debug-Modus.<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> forbiddenCharsInAuthority<br /> </td> 
   <td> Verbotene Zeichen (Domäne): Liste der unzulässigen Zeichen im Abschnitt "Authority"eines URI.<br /> </td> 
   <td> String <br /> </td> 
   <td> '.?#@/:' <br /> </td> 
  </tr> 
  <tr> 
   <td> forbiddenCharsInPath<br /> </td> 
   <td> Verbotene Zeichen (Pfad): Liste der unzulässigen Zeichen im Abschnitt "Pfad"eines URI.<br /> </td> 
   <td> String <br /> </td> 
   <td> '?#/'<br /> </td> 
  </tr> 
  <tr> 
   <td> modDir<br /> </td> 
   <td> Wert der Moduloption "mod_dir": Liste der Dateien, die bei einer Abfrage zu einem Ordner verwendet werden sollen.<br /> </td> 
   <td> String <br /> </td> 
   <td> 'index.md' <br /> </td> 
  </tr> 
  <tr> 
   <td> startRelay<br /> </td> 
   <td> Startet das HTTP-Weiterleitungsmodul.<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> startRelayInModule<br /> </td> 
   <td> Starten Sie das HTTP-Relais-Modul auf dem Webserver. <br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> timeout<br /> </td> 
   <td> Wartezeit vor Löschung der ausgeschlossenen URL.<br /> </td> 
   <td> String <br /> </td> 
   <td> "60"<br /> </td> 
  </tr> 
 </tbody> 
</table>

Hinzufügen einer **web > relay > url** Knoten für jede URL, die weitergeleitet werden soll (Einfügereihenfolge definiert Priorität) mit den folgenden Parametern.

Weitere Informationen finden Sie unter [Dynamische Seitensicherheit und Relais](../../installation/using/configuring-campaign-server.md#dynamic-page-security-and-relays) und [Abschnitt](../../installation/using/deploying-an-instance.md#synchronizing-public-resources).

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
   <td> Autorisierte IPs: Kommagetrennte Liste der Quell-IP-Adressen, die den Relais für diese Maske verwenden dürfen.<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> Ablehnen<br /> </td> 
   <td> Verweigert den Zugriff auf diese URLs (gibt HTTP 403 Fehler aus)<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> hostMask<br /> </td> 
   <td> DNS-Alias für die Weiterleitung: Kommagetrennte Liste von DNS-Alias Masken zum Weiterleiten (z. B.: '*.adobe.com').<br /> </td> 
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
   <td> relayHost<br /> </td> 
   <td> Hinzufügen des ursprünglichen Hosts: verwenden den HTTP-Header "Host"der ursprünglichen Anfrage bei der Wiedergabe.<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> relayPath<br /> </td> 
   <td> Fügen Sie den anfänglichen URL-Pfad hinzu: Hängen Sie den vollständigen Pfad der URLs an, um an die URL der Zielseite weiterzuleiten. <br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> status<br /> </td> 
   <td> Synchronisierungsstatus einer öffentlichen Ressource (Auflistung). Mögliche Werte sind "normal"(normale Ausführung), "Blacklist"(URL, die im Fall von Fehler 404 zur Blockierungsliste hinzugefügt wird) und "reserve"(Datei-Upload auf Reserveserver, falls vorhanden).<br /> </td> 
   <td> String <br /> </td> 
   <td> normal<br /> </td> 
  </tr> 
  <tr> 
   <td> targetUrl<br /> </td> 
   <td> URL der Zielseite: verweisen auf <a href="configure-tomcat.md" target="_blank">Tomcat konfigurieren</a>.<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> timeout<br /> </td> 
   <td> Maximale Ausführungszeit (in Sekunden) der zu wiederholenden Anfrage.<br /> </td> 
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

Dies ist die Standardkonfiguration:

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

Hinzufügen einer **web > relay > responseHeader** Knoten für jeden HTTP-Header, der zu den an den Relais weitergeleiteten Antworten hinzugefügt werden soll.

Weitere Informationen finden Sie unter [Verwalten von HTTP-Headern](../../installation/using/configuring-campaign-server.md#managing-http-headers).

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
   <td> name<br /> </td> 
   <td> Header-Name<br /> </td> 
   <td> String <br /> </td> 
  </tr> 
  <tr> 
   <td> value<br /> </td> 
   <td> Header-Wert <br /> </td> 
   <td> String <br /> </td> 
  </tr> 
 </tbody> 
</table>

Dies ist die Standardkonfiguration:

```
<responseHeader name="X-XSS-Protection" value="1; mode=block"/>
```

### Umleitung {#redirection}

Im Folgenden finden Sie die verschiedenen Parameter der **web > redirection** Knoten. Dies ist die Konfiguration des Umleitungsmoduls.

Weitere Informationen finden Sie in diesem Abschnitt [Abschnitt](../../installation/using/deploying-an-instance.md#synchronizing-public-resources).

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
   <td> Organisationskennung des Identity Management-Systems (IMS): eindeutige Organisationskennung innerhalb der Adobe Experience Cloud, die insbesondere für den VisitorID-Dienst und die IMS-SSO verwendet wird. <br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> P3PCompactPolicy<br /> </td> 
   <td> Wert, der die Richtlinie beschreibt, die für permanente Cookies verwendet wird (konform mit dem P3P Compact Policy-Format). <br /> </td> 
   <td> String <br /> </td> 
   <td> "CAO DSP COR CURa DEVa TAIa OUR BUS IND UNI COM NAV"<br /> </td> 
  </tr> 
  <tr> 
   <td> cookieDomain<br /> </td> 
   <td> Durch Kommata getrennte Liste von Domains, die so konfiguriert werden sollen, dass Ihre Domain zum Setzen von Cookies angegeben wird. <br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> databaseId<br /> </td> 
   <td> Kennung der der Trackinginstanz zugeordneten Datenbank.<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> defLogCount<br /> </td> 
   <td> Protokollanzahl nach Aufruf: Anzahl der Protokolle, die standardmäßig bei einem Aufruf der Methode GetTrackingLogs zurückgegeben werden.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
  <tr> 
   <td> expirationURL<br /> </td> 
   <td> Seite für abgelaufene Weiterleitungen: URL der Webseite, die standardmäßig vom Weiterleitungsserver verwendet wird, wenn die Weiterleitung für eine Versandaktion abgelaufen ist.<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxJobsInCache<br /> </td> 
   <td> Maximale Auftragsanzahl: Maximale Anzahl von Bereitstellungsaktionen im Cache. Darf nicht kleiner als 50 sein. <br /> </td> 
   <td> Lang<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> startRedirection<br /> </td> 
   <td> Startet den Weiterleitungsdienst<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> startRedirectionInModule<br /> </td> 
   <td> Startet den Weiterleitungsdienst im Modulmodus<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> trackWebVisitors<br /> </td> 
   <td> Webtracking: Erstellung von Protokollen für die Seiten, die von unbekannten Benutzern besucht wurden. <br /> </td> 
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

Im Folgenden finden Sie die verschiedenen Parameter der **web > redirection > reserveServer** Knoten.

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
   <td> Berücksichtigt, wenn der Tracking-Server berücksichtigt wird, wenn der Ausdruck "true"zurückgibt. <br /> </td> 
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
   <td> url<br /> </td> 
   <td> URL eines zusätzlichen Weiterleitungsservers<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

### spamCheck {#spamcheck}

Im Folgenden finden Sie die verschiedenen Parameter der **web > spamCheck** Knoten. Dies ist die Konfiguration der Bewertungsparameter E-Mail-Anti-Spam-Bewertung .

Weitere Informationen finden Sie unter [SpamAssassin konfigurieren](../../installation/using/configuring-spamassassin.md).

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
   <td> command<br /> </td> 
   <td> Zur Auswertung der Anti-Spam-Punktzahl einer E-Mail auszuführender Befehl (z. B.: 'perl spamcheck.pl').<br /> </td> 
   <td> String <br /> </td> 
  </tr> 
 </tbody> 
</table>

## wfserver {#wfserver}

Im Folgenden finden Sie die verschiedenen Parameter der **wfserver** Knoten. Dies ist die Workflow-Prozesskonfiguration.

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
   <td> Autostart<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> dataBasePoolPeriodSec<br /> </td> 
   <td> Beweglicher Zeitraum<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 20<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> Kennung des bei Prozessbeginn auszuführenden JavaScripts.<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Warnung zur Speicherbelegung: Warnhinweis bezüglich der von einem bestimmten Prozess verbrauchten RAM (in MB).<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Warnung zur Speicherbelegung: Warnung bezüglich der von einem bestimmten Prozess verbrauchten RAM (in MB).<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> notifRelay<br /> </td> 
   <td> Benachrichtigungsweiterleitung: HostName:Port zur Aktivierung der Weiterleitung von Benachrichtigungen.<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Zeitpunkt des automatischen Neustarts des Prozesses. Siehe <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatischer Prozess-Neustart</a>.<br /> </td> 
   <td> String <br /> </td> 
   <td> "06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Startpriorität. Module mit einer niedrigen Prioritätsziffer werden als erste gestartet und als letzte abgeschlossen. Das Syslogd-Modul muss daher die Priorität 0 aufweisen.<br /> </td> 
   <td> Kurz<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>
