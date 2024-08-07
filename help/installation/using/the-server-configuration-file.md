---
product: campaign
title: Die Serverkonfigurationsdatei
description: Die Serverkonfigurationsdatei
feature: Installation, Instance Settings
audience: installation
content-type: reference
topic-tags: appendices
exl-id: 70cd6a4b-c839-4bd9-b9a7-5a12e59c0cbf
source-git-commit: f032ed3bdc0b402c8281bc34e6cb29f3c575aaf9
workflow-type: tm+mt
source-wordcount: '8067'
ht-degree: 6%

---

# Die Serverkonfigurationsdatei{#the-server-configuration-file}

Die Gesamtkonfiguration von Adobe Campaign wird in der Datei &quot;**serverConf.xml**&quot;definiert, die sich im Ordner &quot;**conf**&quot;des Installationsordners befindet. In diesem Abschnitt werden alle verschiedenen Knoten und Parameter der Datei **serverConf.xml** aufgelistet.

>[!NOTE]
>
>Serverseitige Konfigurationen können nur von Adobe für Bereitstellungen durchgeführt werden, die von Adobe gehostet werden. Weitere Informationen zu den verschiedenen Bereitstellungen finden Sie im Abschnitt [Hosting-Modelle](../../installation/using/hosting-models.md) oder auf [dieser Seite](../../installation/using/capability-matrix.md) . Die Installations- und Konfigurationsschritte für gehostete und hybride Modelle werden in diesem [Abschnitt](../../installation/using/hosting-models.md) beschrieben.

Die ersten Parameter befinden sich im Knoten **shared** . Diese beziehen sich auf die Instanz. Sie werden potenziell von allen nlserver-Befehlen verwendet (nlserver web, nlserver wfserver usw.). Die anderen Abschnitte beziehen sich auf einen bestimmten nlserver-Unterbefehl.

**Freigegebene Parameter**

* [Authentifizierung](#authentication)
* [dataStore](#datastore)
* [dnsConfig](#dnsconfig)
* [exec](#exec)
* [htmlToPdf](#htmltopdf)
* [ims](#ims)
* [javaScript](#javascript)
* [mailExchanger](#mailexchanger)
* [Modul](#module)
* [Monitoring](#monitoring)
* [ooconv](#ooconv)
* [proxyConfig](#proxyconfig)
* [threadPool](#threadpool)
* [urlPermission](#urlpermission)
* [cusHeaders](#cusheaders)
* [xtkJobs](#xtkjobs)

**Sonstige Parameter**

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

Im Folgenden finden Sie die verschiedenen Parameter des Knotens **authentication** :

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
   <td> IP-Adressenüberprüfung aktivieren.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> defaultMode<br /> </td> 
   <td> Standardidentifizierungsmodus.<br /> </td> 
   <td> String <br /> </td> 
   <td> 'nl'<br /> </td> 
  </tr> 
  <tr> 
   <td> longSessionTimeOutSec<br /> </td> 
   <td> Zeitüberschreitung bei langen Sitzungen in Sekunden.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1296000<br /> </td> 
  </tr> 
  <tr> 
   <td> securityTimeOutSec<br /> </td> 
   <td> Zeitüberschreitung des Sicherheits-Tokens in Sekunden.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
  <tr> 
   <td> sessionCacheSec<br /> </td> 
   <td> Aufbewahrungsfrist im Cache: Cache der Sitzungsinformationen in Sekunden.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> sessionTimeOutSec<br /> </td> 
   <td> Sitzungs-Timeout in Sekunden.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
 </tbody> 
</table>

### XTK {#xtk}

Im Folgenden finden Sie die verschiedenen Parameter des Knotens **Authentifizierung > XTK** :

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
   <td> Interne Sicherheitszone des Kontos: autorisierter Bereich für das interne Konto.<br /> </td> 
   <td> String <br /> </td> 
   <td> 'lan'<br /> </td> 
  </tr> 
 </tbody> 
</table>

## dataStore {#datastore}

Im Folgenden finden Sie die verschiedenen Parameter des Knotens **dataStore** . Hier werden die Server-Datenquellen definiert.

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
   <td> '/home/customer/,/sftp/' <br /> </td> 
  </tr> 
  <tr> 
   <td> formCacheTimeToLive<br /> </td> 
   <td> Ablaufverzögerung für Formular-Cache: Zeitüberschreitung in Sekunden, nach der ein Cache-Eintrag ungültig gemacht wird. O bedeutet, dass Cache-Einträge nur zum Zeitpunkt der Veröffentlichung aktualisiert werden.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> hosts<br /> </td> 
   <td> DNS-Masken: Liste der DNS-Masken, die von dieser Instanz bereitgestellt werden (durch Kommas getrennt, kann * und ? Muster).<br /> </td> 
   <td> String <br /> </td> 
   <td> '*'<br /> </td> 
  </tr> 
  <tr> 
   <td> interactionCacheTimeToLive<br /> </td> 
   <td> Interaction JSSP-Cache-Ablaufverzögerung: Zeitüberschreitung in Sekunden, nach der ein Cache-Eintrag ungültig gemacht wird. Ein negativer Wert bedeutet, dass der Cache immer invalidiert wird. "0", leere oder ungültige Werte werden als 60 betrachtet.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> lang<br /> </td> 
   <td> Instanzsprache (Auflistung). Mögliche Werte sind "fr_FR"(Français), "en_GB"(Englisch (UK)), "en_US"(Englisch (US)), "de_DE"(Deutsch) und "ja_JP"(Japanisch).<br /> </td> 
   <td> String <br /> </td> 
   <td> 'en_US'<br /> </td> 
  </tr> 
  <tr> 
   <td> uploadDirectory<br /> </td> 
   <td> Ordner hochladen: Pfad des Zielverzeichnisses für die hochgeladenen Daten.<br /> </td> 
   <td> String <br /> </td> 
   <td> '$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/upload/' <br /> </td> 
  </tr> 
  <tr> 
   <td> uploadAllowlist<br /> </td> 
   <td> Zulässige Dateien, die durch ',' getrennt heruntergeladen werden. Die Zeichenfolge muss ein gültiger, regulärer Java-Ausdruck sein. Siehe <a href="file-res-management.md" target="_blank">Eingrenzen der hochzuladenden Dateien</a>.<br /> </td> 
   <td> String <br /> </td> 
   <td> '.+' <br /> </td> 
  </tr> 
  <tr> 
   <td> useVault<br /> </td> 
   <td> Geheimnisse im Vault speichern: Hashicorp Vault verwenden<br /> </td> 
   <td> Boolean<br /> </td> 
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
   <td> Lokaler Pfad der Datei mit dem Vault-Token. $(HOME) kann in diesem Pfad verwendet werden (aber nicht in anderen env-Variablen).<br /> </td> 
   <td> String <br /> </td> 
   <td> '$(HOME)/.vaultoken'<br /> </td> 
  </tr> 
  <tr> 
   <td> vaultUrl<br /> </td> 
   <td> Hashicorp Vault URL <br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> viewCacheTimeToLive<br /> </td> 
   <td> Gültigkeitsdauer des Ansichtscache: Zeitüberschreitung in Sekunden, nach der ein Cache-Eintrag ungültig gemacht wird. Ein negativer Wert bedeutet, dass der Cache immer invalidiert wird. "0", leere oder ungültige Werte werden als 60 betrachtet.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> workingDirectory<br /> </td> 
   <td> XPath des Arbeitsverzeichnisses.<br /> </td> 
   <td> String <br /> </td> 
   <td> workingDirectory : XPath des Arbeitsverzeichnisses. Standard: '$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/workspace/'<br /> </td> 
  </tr> 
 </tbody> 
</table>

### proxyAdjust {#proxyadjust}

Im Folgenden finden Sie die verschiedenen Parameter des Knotens **dataStore > proxyAdjust** . URLs, die mit dem regulären Ausdruck übereinstimmen, werden basierend auf der in urlBase definierten URL neu generiert.

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
   <td> Basis zur Verwendung beim Generieren externer URLs. Beispiel: https://server.domain.com<br /> </td> 
   <td> String <br /> </td> 
  </tr> 
  <tr> 
   <td> urlRegEx<br /> </td> 
   <td> Regulärer Ausdruck zum Abgleichen von URLs. Beispiel: http://server\.lan\.net.*<br /> </td> 
   <td> String <br /> </td> 
  </tr> 
 </tbody> 
</table>

### dataSource {#datasource}

Im Folgenden finden Sie die verschiedenen Parameter des Knotens **dataStore > dataSource** .

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
   <td> Data Source name<br /> </td> 
   <td> String <br /> </td> 
   <td> default<br /> </td> 
  </tr> 
 </tbody> 
</table>

Konfigurieren Sie im Knoten **dataStore > dataSource > dbcnx** die Verbindungseinstellungen:

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
   <td> Boolean<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> dbSchema<br /> </td> 
   <td> Workspace<br /> </td> 
   <td> String <br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> verschlüsselt<br /> </td> 
   <td> Verschlüsseltes Kennwort<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> login<br /> </td> 
   <td> Konto<br /> </td> 
   <td> String <br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> password<br /> </td> 
   <td> Kennwort<br /> </td> 
   <td> String <br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> provider<br /> </td> 
   <td> Typ (Auflistung). Mögliche Werte sind 'Oracle', 'MSSQL' (Microsoft SQL Server), 'PostgreSQL' (PostgreSQL), 'Teradata', 'MySQL', 'Netezza', 'AsterData', 'SAPHANA' (SAP HANA), 'RedShift' (Amazon Redshift), 'ODBC' (Sybase ASE, Sybase IQ), 'Relay'. HTTP-Weiterleitung auf Remote-Datenbank).<br /> </td> 
   <td> String <br /> </td> 
   <td> 'Oracle'<br /> </td> 
  </tr> 
  <tr> 
   <td> server<br /> </td> 
   <td> Server<br /> </td> 
   <td> String <br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> timezone<br /> </td> 
   <td> Zeitzone: siehe <a href="../../installation/using/time-zone-management.md" target="_blank">Zeitzonen-Management</a>.<br /> </td> 
   <td> String <br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> unicodeData<br /> </td> 
   <td> Unicode-Daten in der Datenbank<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> useTimestampTZ<br /> </td> 
   <td> Datumsfelder mit Zeitzone: siehe <a href="../../installation/using/time-zone-management.md" target="_blank">Zeitzonen-Management</a>.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

Konfigurieren Sie im Knoten **dataStore > dataSource > sqlParams** die SQL-Parameter:

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
   <td> Funktionspräfix<br /> </td> 
   <td> String <br /> </td> 
  </tr> 
 </tbody> 
</table>

Konfigurieren Sie im Knoten **dataStore > dataSource > pool** die Parameter des zugehörigen Verbindungspools:

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
   <td> Verzögerung zwischen der Überprüfung der Verbindungsgültigkeit.<br /> </td> 
   <td> short<br /> </td> 
  </tr> 
  <tr> 
   <td> freeCnx<br /> </td> 
   <td> Anzahl der kostenlosen Verbindungen, die im Pool beibehalten werden.<br /> </td> 
   <td> short<br /> </td> 
  </tr> 
  <tr> 
   <td> maxCnx<br /> </td> 
   <td> Maximale Anzahl der zulässigen Verbindungen, bevor eine neue Verbindung verweigert wird. Siehe diese <a href="https://helpx.adobe.com/campaign/kb/how-to-increase-the-maximum-number-of-database-connections-from-.html">Technote</a>.<br /> </td> 
   <td> short<br /> </td> 
  </tr> 
  <tr> 
   <td> maxIdleDelaySec<br /> </td> 
   <td> Maximale Leerlaufzeit der Verbindung. 0 bedeutet Standardwert.<br /> </td> 
   <td> short<br /> </td> 
  </tr> 
 </tbody> 
</table>

### virtualDir {#virtualdir}

Im Folgenden finden Sie die verschiedenen Parameter des Knotens **dataStore > virtualDir** . Dies ist die Konfiguration des virtuellen Verzeichnisses in das tatsächliche Verzeichnis-Mapping.

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

Im Folgenden finden Sie die verschiedenen Parameter des Knotens **dataStore > preprocessCommand** . Dies sind die autorisierten Befehle zur Vorverarbeitung der Workflow-Aktivität &quot;Datei laden&quot;.

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
   <td> Befehlszeilenbezeichnung<br /> </td> 
   <td> String <br /> </td> 
  </tr> 
  <tr> 
   <td> name<br /> </td> 
   <td> Befehlszeilenname<br /> </td> 
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

Im Folgenden finden Sie die verschiedenen Parameter des Knotens **dnsConfig** (DNS-Konfiguration) .

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
   <td> Domänenname: Standard-Domänenname. Wird vom SMTP HELO-Befehl verwendet. Standardmäßig verwendet die Netzwerkparameter der ersten unter Windows deklarierten Netzwerkschnittstelle oder analysiert file/etc/resolv.conf unter Linux (Domäne oder Sucheintrag). <br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> nameServers<br /> </td> 
   <td> DNS-Server: kommagetrennte Liste von Domain-Name-Servern (DNS). Siehe Hinweis unten.<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> retry<br /> </td> 
   <td> Anzahl weiterer Versuche für eine DNS-Abfrage.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> timeout<br /> </td> 
   <td> Zeitüberschreitung in Millisekunden für eine DNS-Abfrage.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 5000<br /> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Hinweis für **nameServer**: Standardmäßig wird das Netzwerk verwendet
>Parameter der ersten unter Windows deklarierten Netzwerkschnittstelle
>nicht in UNIX definiert. Definiert die Domänennamenserver (DNS)
>wird vom MTA verwendet, um den E-Mail-Ausdrucksserver zu erhalten, der für
>eine Domäne.
>
>Wenn dieser Wert nicht definiert ist, sucht der MTA diese Informationen in der Host-Netzwerkkonfiguration. Wenn mehrere DNS möglich sind, müssen die verschiedenen DNS-Adressen durch Kommas getrennt werden (Beispiel: 212.155.207.1,212.155.207.2). Wenn Ihr Versandserver über mehrere Netzwerkschnittstellen verfügt, ist die vom MTA verwendete DNS-Liste die erste. In diesem Fall wird empfohlen, den Parameter **nameServer** anzugeben, um Unklarheiten zu vermeiden.

>[!CAUTION]
>
>Wenn Ihre Netzwerk-Host-Konfiguration DHCP verwendet, findet der MTA nicht die DNS-Liste, die von DHCP bereitgestellt wird. In diesem Fall wird empfohlen, die DNS-Liste in den Netzwerkparametern der Windows-Systemsteuerung anzugeben.

## exec {#exec}

Im Folgenden finden Sie die verschiedenen Parameter des Knotens **exec** (Befehlsausführung).

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
   <td> user<br /> </td> 
   <td> Führen Sie Befehle als anderen Benutzer aus.<br /> </td> 
   <td> String <br /> </td> 
  </tr> 
 </tbody> 
</table>

## htmlToPdf {#htmltopdf}

Im Folgenden finden Sie die verschiedenen Parameter des Knotens **htmlToPdf** . Dies ist die Konfiguration des Diensts zum Konvertieren von Webseiten in PDF-Dokumente.

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
   <td> Befehlszeile zum Ausführen der Konvertierung (im "anderen" Modus).<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessusCount<br /> </td> 
   <td> Max. Anzahl der gleichzeitig auf einem Computer zulässigen Konvertierungsprozesse.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> mode<br /> </td> 
   <td> Tool für die Konvertierung. Mögliche Werte sind: phantomjs, wkhtmltopdf, other, disabled<br /> </td> 
   <td> String <br /> </td> 
   <td> 'phantomjs' <br /> </td> 
  </tr> 
  <tr> 
   <td> timeout<br /> </td> 
   <td> Zeitüberschreitung für eine Konversion: maximale Konvertierungsdauer in Sekunden. Über diesen Schwellenwert hinaus wird der Konvertierungsprozess angehalten und ein Fehler erzeugt.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 120<br /> </td> 
  </tr> 
  <tr> 
   <td> verbose<br /> </td> 
   <td> Verbose mode: Starten Sie im ausführlichen Modus, um mögliche Fehler zu diagnostizieren.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> waitTime<br /> </td> 
   <td> Verzögerung beim Warten auf einen Prozess: Verzögerung in Sekunden, wenn alle Prozesse gleichzeitig verwendet werden und darauf gewartet wird, dass ein Prozess freigegeben wird. Wenn diese Verzögerung überschritten wird, wird die Konvertierung angehalten und ein Fehler erzeugt. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 15<br /> </td> 
  </tr> 
 </tbody> 
</table>

Beispiel für Phantomjs:

```
phantomjs - -ignore-ssl-errors=true '$(XTK_INSTALL_DIR)/bin/htmlToPdf.js' '-out:{outPdf}' '-post:{postFile}' '-url:{originUrl}' -sessiontoken:{sessiontoken} -format:{format} -orientation:{orientation} -marginTop:{marginTop} -marginLeft:{marginLeft} -marginRight:{marginRight} -marginBottom:{marginBottom}
```

## ims {#ims}

Im Folgenden finden Sie die verschiedenen Parameter des Knotens **ims** . Dies ist die Konfiguration für die Verbindung von Campaign mit einem anderen Dienst mit [IMS](../../integrations/using/about-adobe-id.md).

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
   <td> Geheimer Schlüssel (in AES verschlüsselt)<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSCode<br /> </td> 
   <td> Autorisierungscode (in AES verschlüsselt)<br /> </td> 
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
   <td> Kundenkennung des technischen Kontos<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSTAClientSecret<br /> </td> 
   <td> Geheimnisschlüssel des technischen Kontos (in AES verschlüsselt)<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSTAId<br /> </td> 
   <td> Technische Konto-ID<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSTAPrivateKey<br /> </td> 
   <td> Privater Schlüssel des technischen Kontos (in AES verschlüsselt)<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

## JavaScript {#javascript}

Im Folgenden finden Sie die verschiedenen Parameter des Knotens **javaScript** . Dies ist die Konfiguration des JavaScript-Interpreters.

Weitere Informationen finden Sie in der [Dokumentation zur Berichterstellung](../../reporting/using/actions-on-reports.md#memory-allocation).

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
   <td> Maximale Größe in Megabyte, bevor der Speicherberater ausgeführt wird.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 512 <br /> </td> 
  </tr> 
  <tr> 
   <td> stackSizeKB<br /> </td> 
   <td> Größe jedes Stapelteils in Kilooctetten. Dies ist ein Parameter zur Optimierung der Speicherverwaltung, den die meisten Benutzer nicht anpassen sollten. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 8<br /> </td> 
  </tr> 
 </tbody> 
</table>

## mailExchanger {#mailexchanger}

Im Folgenden finden Sie die verschiedenen Parameter des Knotens **mailExchange** . Dies ist die Konfiguration des SMTP-Servers.

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
   <td> TCP-Port des für die E-Mail-Übertragung verwendeten SMTP-Servers<br /> </td> 
   <td> String <br /> </td> 
   <td> 25<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Modul {#module}

Im Folgenden finden Sie die verschiedenen Parameter des Knotens **module** . Dies ist die Konfiguration für das Namensraum-Einschränkungsmodul xtk.

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
   <td> Standard-Namespace, der beim Erstellen einer neuen Entität verwendet wird.<br /> </td> 
   <td> String <br /> </td> 
   <td> 'cus'<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Monitoring {#monitoring}

Im Folgenden finden Sie die verschiedenen Parameter des Knotens **monitoring** . Dies ist die Konfiguration des Überwachungsdienstes.

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
   <td> Long<br /> </td> 
   <td> 3600<br /> </td> 
  </tr> 
  <tr> 
   <td> unixScript<br /> </td> 
   <td> Vom Überwachungsdienst ausgeführtes Unix-Skript.<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> winScript<br /> </td> 
   <td> Vom Überwachungsdienst auszuführendes Windows-Skript.<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

## ooconv {#ooconv}

Im Folgenden finden Sie die verschiedenen Parameter des Knotens **oconv** . Dies ist die Konfiguration des Dokumentkonvertierungsservers.

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
   <td> Long<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxServerIdleSec<br /> </td> 
   <td> Maximale Leerlaufzeit des OpenOffice-Servers vor erzwungenem Schließen.<br /> </td> 
   <td> Long<br /> </td> 
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
   <td> 'http://localhost:8080/nl/jsp/ooconv.jsp'<br /> </td> 
  </tr> 
 </tbody> 
</table>

## proxyConfig {#proxyconfig}

Im Folgenden finden Sie die verschiedenen Parameter des Knotens **proxyConfig** . Dies ist die Konfiguration von Proxy-Parametern.

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
   <td> enabled<br /> </td> 
   <td> Verwenden Sie einen Proxyserver.<br /> </td> 
   <td> Boolean<br /> </td> 
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
   <td> Unique Proxy-Server: Verwenden Sie dieselbe Konfiguration für alle Proxytypen.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

### HTTP-Proxy/sicherer Proxy {#http-proxy---secure-proxy-}

Konfigurieren Sie im Knoten **proxyConfig > HTTP Proxy / Secure Proxy** die folgenden Parameter.

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
   <td> address<br /> </td> 
   <td> Adresse des Proxyservers<br /> </td> 
   <td> String <br /> </td> 
  </tr> 
  <tr> 
   <td> login<br /> </td> 
   <td> Anmeldung für die Verbindung zum Proxy-Server<br /> </td> 
   <td> String <br /> </td> 
  </tr> 
  <tr> 
   <td> password<br /> </td> 
   <td> Kennwort für die Verbindung mit dem Proxy-Server<br /> </td> 
   <td> String <br /> </td> 
  </tr> 
  <tr> 
   <td> port<br /> </td> 
   <td> Proxy-Server-Port<br /> </td> 
   <td> short<br /> </td> 
  </tr> 
 </tbody> 
</table>

## threadPool {#threadpool}

Im Folgenden finden Sie die verschiedenen Parameter des Knotens **threadPool** .

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
   <td> Long<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## urlPermission {#urlpermission}

Im Folgenden finden Sie die verschiedenen Parameter des Knotens **urlPermission** . Dies ist die Liste der URLs, auf die der JavaScript-Code zugreifen kann.

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
   <td> Standardaktion, wenn die URL nicht in der Liste der zulässigen Werte (Auflistung) enthalten ist. Mögliche Werte sind "ignore"(Autorisierung ohne Warnung, dazu muss der Schutz deaktiviert werden), "warn"(Autorisieren und Warnmeldung ausgeben) und "deny"(Zugriff auf die URL verbieten).<br /> </td> 
   <td> String <br /> </td> 
   <td> deny<br /> </td> 
  </tr> 
  <tr> 
   <td> debugTrace<br /> </td> 
   <td> Debugging-Trace des URL-Auswahlmechanismus: Gibt während des URL-Verifizierungsprozesses zusätzliche Meldungen aus.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

## cusHeaders {#cusheaders}

Mit diesem Knoten können Sie bestimmte Header zu Anforderungen hinzufügen, die beim Hochladen einer Datei von einem externen Server ausgeführt werden. Content Delivery Networks (CND) kann nach einem bestimmten Header fragen, um dem Anfragenden zu vertrauen. Diese Header können verwendet werden, um das Vertrauen in Campaign-Anforderungen zu verbessern, insbesondere beim Herunterladen personalisierter Dokumente für jeden Empfänger bei der Ausführung des Versands. Eine große Anzahl von Anfragen zum Herunterladen von Ressourcen kann als DoS-Angriff interpretiert werden. Mit dnsPattern können Sie bestimmte Kopfzeilennamen und Werte für verschiedene CDNs basierend auf ihrem Domänennamen festlegen.

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

Fügen Sie für jede URL einen Knoten **url** mit den folgenden Parametern hinzu:

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
   <td> Domänenname oder übergeordnete Domäne, die von der URL betroffen sind: zur Beschleunigung der Verifizierung die Domäne der URL, die vollständig oder teilweise überprüft werden soll. Die URL wird nur mit Bezug auf den regulären Ausdruck überprüft, wenn die Domäne dsnSuffix enthält.<br /> </td> 
   <td> String <br /> </td> 
  </tr> 
  <tr> 
   <td> urlRegEx<br /> </td> 
   <td> Regulärer Ausdruck zur Verfeinerung der Validierung von URLs, die zu dieser Domäne gehören: regulärer Ausdruck, den die URL überprüfen muss, falls er mit dnsSuffix übereinstimmt.<br /> </td> 
   <td> String <br /> </td> 
  </tr> 
 </tbody> 
</table>

Wenn ein Datensatz **dnsSuffix**, aber nicht **urlRegEx** erfüllt, wird der folgende Datensatz geprüft.

Um beispielsweise den Zugriff auf alle URLs der Domain business.com zu erlauben, können wir zwei Datensätze definieren:

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
<url dnsSuffix="localhost"                               urlRegEx="http://localhost:8080/nms/jsp/.*"              />
<url dnsSuffix="localhost"                               urlRegEx="http://localhost:8080/nl/jsp/.*"               />
<url dnsSuffix="localhost"                               urlRegEx="http://localhost:8080/xtk/jsp/.*"              />
```

## xtkJobs {#xtkjobs}

Im Folgenden finden Sie die verschiedenen Parameter des Knotens **xtkJobs** . Dies ist die Konfiguration der Serveraufträge.

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
   <td> Aktualisierungszeitraum des Speicherstatus für die Serververarbeitung (in ms).<br /> </td> 
   <td> Long<br /> </td> 
   <td> 500<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Archivierung {#archiving}

Im Folgenden finden Sie die verschiedenen Parameter des Knotens **archiving** . Dies ist die Konfiguration der ausgeführten Archivierungsvorgänge im Hintergrund.

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
   <td> Anzahl der gleichzeitig zu verarbeitenden EMLs<br /> </td> 
   <td> Long<br /> </td> 
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
   <td> Automatischer Start<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> compressBatchSize<br /> </td> 
   <td> Größe eines komprimierten Archivs: maximale Anzahl von Dateien in einem komprimierten Archiv.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 10000<br /> </td> 
  </tr> 
  <tr> 
   <td> compressionFormat<br /> </td> 
   <td> Komprimierungsformat, das bei der Archivierung (Auflistung) verwendet wird. Mögliche Werte sind "0"(keine Komprimierung) und "1"(komprimieren Sie gesendete Nachrichten im ZIP-Format).<br /> </td> 
   <td> Byte<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> expirationDelay<br /> </td> 
   <td> Verzögerung vor der automatischen Archivierung nicht verarbeiteter E-Mails: Anzahl der Tage bis zur Archivierung nicht verarbeiteter E-Mails.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID des JavaScript, der beim Starten des Prozesses ausgeführt werden soll.<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Warnhinweis zur Speicherbelegung: Warnhinweis bezüglich der von einem bestimmten Prozess verbrauchten RAM (in MB).<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Warnung zur Speicherbelegung: Warnhinweis bezüglich der von einem bestimmten Prozess verbrauchten RAM-Menge (in MB).<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> pollDelay<br /> </td> 
   <td> Verzögerung (in Sekunden) zwischen jedem Update-Ereignis.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Uhrzeit des automatischen Neustart des Prozesses. Siehe <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatischer Prozessneustart</a>.<br /> </td> 
   <td> String <br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> purgeArchivesDelay<br /> </td> 
   <td> Anzahl der Tage, bevor nicht verarbeitete E-Mails gelöscht werden.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 7<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priorität am Anfang. Module mit niedriger Priorität werden zuerst gestartet und zuletzt angehalten. Das syslogd-Modul muss daher die Priorität 0 haben.<br /> </td> 
   <td> short<br /> </td> 
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
   <td> SMTPS-Unterstützung aktivieren: Aktiviert den Versand von E-Mails im abgesicherten Modus (STARTTLS/SMTPS), wenn dieser vom Remote-Server unterstützt wird.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> smtpNbConnection<br /> </td> 
   <td> Anzahl der Verbindungen zum archivierenden SMTP-Server.<br /> </td> 
   <td> Long<br /> </td> 
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
   <td> IP-Port des SMTP-Servers.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 25<br /> </td> 
  </tr> 
 </tbody> 
</table>

## inMail {#inmail}

Im Folgenden finden Sie die verschiedenen Parameter des Knotens **inMail** . Dies ist die Konfiguration des Moduls E-Mail-Management.

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
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> checkInstanceName<br /> </td> 
   <td> Instanzname überprüfen: Wenn "true", muss der Name der Adobe Campaign-Instanz, die in den Nachrichten-ID-Headern enthalten ist, mit dem der aktuellen Instanz übereinstimmen. <br /> </td> 
   <td> Boolean<br /> </td> 
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
   <td> Adresse für Fehler: Standardadresse zur Übertragung ungültiger E-Mails (ungültige MIME-Kodierung). <br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> ignoreSize<br /> </td> 
   <td> Ignorieren der Nachrichtengröße: wird verwendet, um die Größe einer von POP3-Servern zurückgegebenen Nachricht zu ignorieren. In diesem Fall erwartet das Modul einen "." am Ende der Nachrichten. <br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> inMailPeriodSec<br /> </td> 
   <td> Nachrichtenlesezeitraum: Abrufhäufigkeit der Nachrichtenwarteschlange.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID des JavaScript, der beim Starten des Prozesses ausgeführt werden soll.<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxBroadLog<br /> </td> 
   <td> Maximale Anzahl zu aktualisierender Protokolle: definiert die maximale Anzahl von Protokollmeldungen, die im Speicher aufbewahrt werden sollen, bevor die Datenbank aktualisiert wird.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 20<br /> </td> 
  </tr> 
  <tr> 
   <td> maxMsgPerSession<br /> </td> 
   <td> Maximale Anzahl der Nachrichten, die während der POP3-Sitzung gelesen werden.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 200<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Warnhinweis zur Speicherbelegung: Warnhinweis bezüglich der von einem bestimmten Prozess verbrauchten RAM (in MB).<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Warnung zur Speicherbelegung: Warnhinweis bezüglich der von einem bestimmten Prozess verbrauchten RAM-Menge (in MB).<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSessionTTLSec<br /> </td> 
   <td> Sitzungsdauer: maximale Dauer der Nachrichtenverarbeitungssitzung.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> popMailPeriodSec<br /> </td> 
   <td> POP3-Abrufezeitraum<br /> </td> 
   <td> Long<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> popQueueSize<br /> </td> 
   <td> Warteschlangengröße der Lesesachrichten<br /> </td> 
   <td> Long<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> popTimeoutSec<br /> </td> 
   <td> Zeitüberschreitung bei der Kommunikation mit dem POP3-Server. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Uhrzeit des automatischen Neustart des Prozesses. Siehe <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatischer Prozessneustart</a>.<br /> </td> 
   <td> String <br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> reloadPeriodSec<br /> </td> 
   <td> Häufigkeit der Neuladungen der abzurufenden Konten.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priorität am Anfang. Module mit niedriger Priorität werden zuerst gestartet und zuletzt angehalten. Das syslogd-Modul muss daher die Priorität 0 haben.<br /> </td> 
   <td> short<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

### msgDump {#msgdump}

Konfigurieren Sie im Knoten **inMail > msgDump** die folgenden Parameter. Dies ist die Konfiguration des Dump verarbeiteter Nachrichten.

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
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> msgPath<br /> </td> 
   <td> Pfad für den Nachrichten-Dump.<br /> </td> 
   <td> String <br /> </td> 
   <td> '/tmp/inMail'<br /> </td> 
  </tr> 
 </tbody> 
</table>

## interactiond {#interactiond}

Im Folgenden finden Sie die verschiedenen Parameter des Knotens **interactiond** . Dies ist die Konfiguration des SchreibDaemons für eingehende Interaktionsereignisse.

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
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> callDataSize<br /> </td> 
   <td> Max. Anzahl der Zeichen, die im gemeinsamen Speicher für Aufrufdaten gespeichert sind.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID des JavaScript, der beim Starten des Prozesses ausgeführt werden soll<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Warnhinweis zur Speicherbelegung: Warnhinweis bezüglich der von einem bestimmten Prozess verbrauchten RAM (in MB).<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Warnung zur Speicherbelegung: Warnhinweis bezüglich der von einem bestimmten Prozess verbrauchten RAM-Menge (in MB).<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSharedEntries<br /> </td> 
   <td> Max. Anzahl der im gemeinsamen Speicher gespeicherten Ereignisse.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 25000<br /> </td> 
  </tr> 
  <tr> 
   <td> nextOffersSize<br /> </td> 
   <td> Maximale Anzahl zulässiger Angebote, die direkt nach Vorschlägen sortiert wurden und für Statistiken gespeichert werden sollen.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Uhrzeit des automatischen Neustart des Prozesses. Siehe <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatischer Prozessneustart</a>.<br /> </td> 
   <td> String <br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priorität am Anfang. Module mit niedriger Priorität werden zuerst gestartet und zuletzt angehalten. Das syslogd-Modul muss daher die Priorität 0 haben.<br /> </td> 
   <td> short<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> statsPeriod<br /> </td> 
   <td> Aggregationsdauer in Sekunden für die Zeitstatistiken der Antwort. 0 bedeutet, dass der statistische Speicher deaktiviert wurde.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> targetKeySize<br /> </td> 
   <td> Max. Anzahl der Zeichen, die im gemeinsamen Speicher zur Identifizierung von Einzelpersonen gespeichert werden.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 16<br /> </td> 
  </tr> 
 </tbody> 
</table>

## mta {#mta}

Im Folgenden finden Sie die verschiedenen Parameter des Knotens **mta** . Dies ist die Konfiguration der Versandagenten.

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
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> dataLogPath<br /> </td> 
   <td> Pfad der gesendeten E-Mails speichern: Wenn nicht leer, wird der Pfad gespeichert, in dem alle Quelldateien gesendeter E-Mails gespeichert werden. <br /> </td> 
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
   <td> Long<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> errorPeriodSec<br /> </td> 
   <td> Fehlerstatistiken: Zeit zwischen der Erstellung von Statistiken und der Speicherung in der Datenbank. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID des JavaScript, der beim Starten des Prozesses ausgeführt werden soll.<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> logEmailErrors<br /> </td> 
   <td> Erstellen Sie Fehlerstatistiken und speichern Sie sie in der Datenbank.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> logLevel<br /> </td> 
   <td> Anzeigeebene der Protokollmeldungen. Schweregrad der in die Datenbank geschriebenen Protokolle. Von MTA generierte Protokollmeldungen werden nicht immer in die Datenbank geschrieben. Mit diesem Parameter können Sie die Ebene definieren, von der aus Sie denken, dass eine Nachricht in die Datenbank geschrieben werden muss. Wenn Sie Stufe 2 definieren, werden auch Nachrichten der Stufe 1 und 0 geschrieben, während bei der Definition von Stufe 1 nur Nachrichten der Stufe 1 und 0 geschrieben werden. Mögliche Werte sind: 0 (errors), 1 (warning), 2 (info)<br /> </td> 
   <td> Long<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> maxMemoryMb<br /> </td> 
   <td> Maximale Speichergröße (in MB), die ein MTA-Prozess verwenden kann. Über diesem Grenzwert hinaus wird der Prozess neu gestartet, sodass der verwendete Speicher auf das System freigegeben wird.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1024<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Warnhinweis zur Speicherbelegung: Warnhinweis bezüglich der von einem bestimmten Prozess verbrauchten RAM (in MB).<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Warnung zur Speicherbelegung: Warnhinweis bezüglich der von einem bestimmten Prozess verbrauchten RAM-Menge (in MB).<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> minConnectionsToLog<br /> </td> 
   <td> Verbindungsschwellenwert, der berücksichtigt werden soll. Fehlerstatistiken werden für einen bestimmten Pfad nicht generiert, wenn die Gesamtanzahl der Verbindungen für den von errorPeriodSec angegebenen Zeitraum streng unter dem Schwellenwert liegt.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> minErrorsToLog<br /> </td> 
   <td> Zu berücksichtigender Fehlerschwellenwert: Fehlerstatistiken werden für einen bestimmten Pfad nicht generiert, wenn die Gesamtzahl der Fehler für den von errorPeriodSec angegebenen Zeitraum strikt unter dem Schwellenwert liegt.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> minMessagesToLog<br /> </td> 
   <td> Meldeschwelle, die berücksichtigt werden soll. Fehlerstatistiken werden für einen bestimmten Pfad nicht generiert, wenn die Gesamtzahl der gesendeten Nachrichten für den von errorPeriodSec angegebenen Zeitraum streng unter dem Schwellenwert liegt.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
  <tr> 
   <td> notifRelay<br /> </td> 
   <td> Benachrichtigungsweiterleitung: HostName:Port, der zum Weiterleiten von Benachrichtigungen verwendet wird.<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Uhrzeit des automatischen Neustart des Prozesses. Siehe <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatischer Prozessneustart</a>.<br /> </td> 
   <td> String <br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> purgeDataLogDelay<br /> </td> 
   <td> Verzögerung vor dem Löschen archivierter E-Mails: Anzahl der Tage vor der Bereinigung archivierter E-Mails im Ordner, der in dataLogPath angegeben ist.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 15<br /> </td> 
  </tr> 
  <tr> 
   <td> retryLostMessages<br /> </td> 
   <td> Verlorene Nachrichten erneut versuchen: Teile von Sendungen werden erneut versucht, wenn der untergeordnete Prozess tot ist.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priorität am Anfang. Module mit niedriger Priorität werden zuerst gestartet und zuletzt angehalten. Das syslogd-Modul muss daher die Priorität 0 haben.<br /> </td> 
   <td> short<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> signEmailLinks<br /> </td> 
   <td> Aktivieren Sie den Signaturmechanismus. Dies verbessert die Sicherheit bei Tracking-Links in E-Mails.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> true<br /> </td> 
  </tr>
  <tr> 
   <td> statServerAddress<br /> </td> 
   <td> Adresse des Versandstatistiken-Servers, angegeben als 
    &lt;dns oder ip&gt; 
      <code>[</code>: 
     &lt;Anschluss&gt; 
       <code>]</code> Siehe 
      <a href="../../installation/using/email-deliverability.md#coordinates-of-the-statistics-server" target="_blank">Koordinaten des Statistikservers</a>. 
      <br /> 
     </td> 
   <td> String <br /> </td> 
   <td> Wenn der Standardanschluss nicht definiert ist, ist 7777.<br /> </td> 
  </tr> 
  <tr> 
   <td> statServerTLSSupport<br /> </td> 
   <td> TLS nach Domäne aktivieren: aktiviert die durch MX konfigurierbaren TLS (erfordert einen aktuellen Statistikserver).<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> true <br /> </td> 
  </tr> 
  <!--tr> 
   <td> statServerVersion<br /> </td> 
   <td> Protocol version used: communication protocol version (1 for a v5.11 and 6.0.2 server, 2 for a v6.1 server).<br /> </td> 
   <td> String<br /> </td> 
   <td> If undefined, the latest version is used. <br /> </td> 
  </tr--> 
  <tr> 
   <td> useMomentum<br /> </td> 
   <td> Wenn der Wert auf "true"gesetzt ist, verwendet Ihre Instanz den <a href="../../delivery/using/sending-with-enhanced-mta.md" target="_blank">Enhanced MTA</a>.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> <br /> </td>b 
  </tr>
  <tr> 
   <td> verifyMode<br /> </td> 
   <td> Überprüfungsmodus: Aktiviert den Überprüfungsmodus (keine physische Übertragung von Nachrichten; für Simulation und Tests verwendet).<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> workingPath<br /> </td> 
   <td> Arbeitsverzeichnis: Speicherort temporärer Dateien, die vom MTA zur Kommunikation mit seinen untergeordneten Prozessen verwendet werden.<br /> </td> 
   <td> String <br /> </td> 
   <td> '$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/mta/' <br /> </td> 
  </tr> 
  <tr> 
   <td> xMailer<br /> </td> 
   <td> Feld "X-Mailer": Wert des Felds "X-Mailer" im SMTP-Mail-Header.<br /> </td> 
   <td> String <br /> </td> 
   <td> 'nlserver, build $(PRODUCT_VERSION)'<br /> </td> 
  </tr>  
 </tbody> 
</table>

### cache {#cache}

Konfigurieren Sie im Knoten **cache** die folgenden Parameter. Dies ist die Konfiguration des lokalen Datei-Cache.

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
   <td> Recycled after: Zeitraum, angegeben in Sekunden, nach dem die Datei automatisch aus dem Cache gelöscht wird, um den Speicher wiederherzustellen.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 244800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSizeOnDiskMb<br /> </td> 
   <td> Maximale Cachegröße (MB).<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1024<br /> </td> 
  </tr> 
  <tr> 
   <td> purgePeriodSec<br /> </td> 
   <td> Bereinigungshäufigkeit: Zeitraum in Sekunden zwischen den Ausführungen des Cache-Bereinigungsmechanismus.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 3600<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Relais {#relay}

Konfigurieren Sie im Knoten **mta > relay** die folgenden Parameter. Dies ist die Konfiguration des E-Mail-Servers für den Nachrichtenversand.

Die Liste wird auf die gleiche Weise wie eine Liste von MX gehandhabt, die von einer MX-DNS-Abfrage zurückgegeben wird. Normalerweise wird der erste MX verwendet, solange er verfügbar ist, dann der nächste verwendet und so weiter.

Weitere Informationen finden Sie unter [SMTP-Weiterleitung](../../installation/using/configuring-campaign-server.md#smtp-relay).

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
   <td> address<br /> </td> 
   <td> Kommagetrennte Liste von DNS-Namen oder IP-Adressen der zu verwendenden SMTP-Relais. <br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> port<br /> </td> 
   <td> IP-Port des SMTP-Servers.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 25<br /> </td> 
  </tr> 
 </tbody> 
</table>

### master {#master}

Konfigurieren Sie im Knoten **mta > master** die folgenden Parameter. Dies ist die Konfiguration des Hauptservers.

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
   <td> Häufigkeit der Datenbankabfragen für die auszuführenden Aufträge. Dieser Wert gibt die Häufigkeit der Datenbankabfragen an (in Sekunden). Um die Liste der Aufträge zu erhalten, die auf die Bereitstellung warten, fragt der MTA die Datenbank regelmäßig ab. Wenn kein Auftrag wartet, wird der Abrufezeitraum durch diesen Wert definiert. Andernfalls wird die Abruffrist automatisch auf eine Sekunde reduziert, wenn ein Auftrag auf einen untergeordneten Server übertragen wurde, sodass ein neuer Auftrag so bald wie möglich erneut verarbeitet werden kann, d. h. sobald ein untergeordneter Server wieder verfügbar ist. Dies bedeutet nicht, dass jede Sekunde eine Datenbankabfrage durchgeführt wird, bis ein untergeordneter Server erneut verfügbar ist. Tatsächlich wird ein Datenbankzugriff nur dann gewährt, wenn mindestens ein untergeordneter Server verfügbar ist.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
  <tr> 
   <td> dataBaseRetryDelaySec<br /> </td> 
   <td> Wartezeit nach einem Datenbankverbindungsfehler. Ein Fehler bei der Datenbankverbindung wird normalerweise vom Datenbankserver selbst verursacht. Der Server kann beispielsweise auch zu Wartungszwecken angehalten werden. Der Parameter DataBaseRetryDelay definiert die Dauer zwischen zwei Verbindungsversuchen im Fall eines Fehlers der Datenbankverbindung.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> domainKeysReloadPeriodSec<br /> </td> 
   <td> Gültigkeitszeitraum für den Cache privater Schlüssel (DomainKeys). Private Schlüssel, die zum Signieren von E-Mails gemäß der DomainKeys-Empfehlung (http://antispam.yahoo.com/domainkeys) verwendet werden, werden als Optionen in der Datenbank gespeichert. Der Parameter domainKeysReloadPeriodSec definiert, wie viele Sekunden der MTA diese Schlüssel in einem Cache speichern kann. Nach dieser Verzögerung müssen alle Schlüssel aus der Datenbank neu geladen werden.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSpareServers<br /> </td> 
   <td> Maximale Anzahl untergeordneter Server. Stellt die maximale Anzahl der ausgeführten Server dar. Es wird empfohlen, diese Anzahl auf eine optimale Weise zu begrenzen, die mit den Serverspeicherressourcen kompatibel ist. Dies kann während eines Versands überprüft werden. Der verwendete Speicher darf nicht mehr als ein Drittel des verfügbaren physischen Speichers betragen. Andernfalls wird der Swap verwendet. Siehe <a href="../../installation/using/configuring-campaign-server.md#mta-child-processes" target="_blank">untergeordnete MTA-Prozesse</a>.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> minSpareServers<br /> </td> 
   <td> Mindestanzahl untergeordneter Server. Der MTA versucht, mindestens diese Anzahl von Servern auszuführen. Wenn weniger vorhanden ist, werden alle Sekunden neue Server neu gestartet, bis dieser Wert erreicht ist.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> startSpareServers<br /> </td> 
   <td> Anzahl der untergeordneten Server beim Start. Die Anzahl der untergeordneten Server wird dynamisch überwacht. Wenn der MTA gestartet wird, werden so viele untergeordnete Server erstellt, wie durch diesen Wert angegeben. Normalerweise können untergeordnete Server nicht schneller als ein Server pro Sekunde gestartet werden, um Hostressourcen zu sparen. Beim Start des MTA wird diese Einschränkung jedoch außer Kraft gesetzt, sodass untergeordnete Server so bald wie möglich verfügbar sind.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
 </tbody> 
</table>

### child {#child}

Konfigurieren Sie im Knoten **mta > child** die folgenden Parameter. Dies ist die Konfiguration der untergeordneten Server.

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
   <td> Optionale Befehlszeilenargumente <br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> idleChildTimeoutSec<br /> </td> 
   <td> Zeitüberschreitung, bis inaktive untergeordnete Server angehalten werden. Wenn ein untergeordneter Server eine Leerlaufzeit hat, die größer als dieser Parameter ist, führt er automatisch den Abbruch durch, um Hostressourcen freizugeben.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> maxAgeSec<br /> </td> 
   <td> Maximale Dauer der Nachrichtenaufbewahrung. Wenn eine vorbereitete Nachricht aufgrund der Drosselung nicht gesendet werden konnte oder nicht in der Lage war, eine Verbindung zum MTA der Zielgruppe herzustellen, wird die Nachricht abgebrochen und beim nächsten erneuten Versuch verarbeitet.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxGCMConnectPerChild<br /> </td> 
   <td> Maximale Anzahl paralleler HTTP-Anfragen an den FCM, die von jedem untergeordneten Server initiiert wurden.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 8<br /> </td> 
  </tr> 
  <tr> 
   <td> maxMsgPerChild<br /> </td> 
   <td> Maximale Anzahl an Nachrichten pro untergeordnetem Server. Jedes untergeordnete MTA-Element verarbeitet diese Anzahl von Nachrichten und stirbt. Es ist wichtig, eine Zahl so anzugeben, dass Speicher- oder Ressourcenlecks im MTA harmlos sind (normalerweise einige Tausende). Selbst wenn im MTA-Code keine Speicherlecks bekannt sind, sind die eingebetteten JavaScript- und XSL-Engines nicht vollständig zuverlässig.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 5000000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxWaitingMessages<br /> </td> 
   <td> Ausstehende Nachrichten: Maximale Anzahl an Nachrichten, die im Speicher auf ihre Zustellung warten. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 2000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxWorkingSetMb<br /> </td> 
   <td> Maximale Speichergröße (in MB), die ein Kindprozess verwenden kann. Oberhalb dieses Grenzwerts wird der Prozess angehalten, sodass der verwendete Speicher auf das System freigegeben wird. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 128<br /> </td> 
  </tr> 
  <tr> 
   <td> soapConnectorTimeoutSec<br /> </td> 
   <td> Zeitüberschreitung (in Sekunden), nach der eine SOAP Verbindung für einen Versand-Connector abgebrochen wird.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> startWithFirstMX<br /> </td> 
   <td> Beginnen Sie immer mit der höchsten Priorität MX.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> timeToLive<br /> </td> 
   <td> Maximale Anzahl aufeinander folgender Versuche bei Wiederaufnahme.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 48<br /> </td> 
  </tr> 
 </tbody> 
</table>

Konfigurieren Sie im Knoten **mta > child > smtp** die folgenden Parameter. Dies ist die Konfiguration von SMTP-Sitzungen.

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
   <td> Aktiviert den Versand von E-Mails im abgesicherten Modus (STARTTLS/SMTPS), wenn dieser vom Remote-Server unterstützt wird.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> idleSessionTimeoutSec<br /> </td> 
   <td> Zeitüberschreitung bei inaktiver Sitzung. Dieser Parameter wird nur verwendet, wenn die Sitzung zum Senden mehrerer Nachrichten an eine bestimmte Domäne wiederverwendet wird. Wenn der MTA die Nachrichtenübertragung abgeschlossen hat, wird die verwendete SMTP-Sitzung nicht systematisch geschlossen. Wenn eine Nachricht für dieselbe Domain gesendet werden kann, wird dieselbe SMTP-Sitzung wiederverwendet. Aus diesem Grund wird die Sitzung nicht automatisch geschlossen. Mit dem Parameter IdleSessionTimeout können Sie den Zeitraum definieren, während dem eine SMTP-Sitzung aktiv bleiben kann, um auf eine andere Nachricht zu warten. Sobald die Dauer abgelaufen ist, wird die Sitzung automatisch geschlossen.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> initialDelaySec<br /> </td> 
   <td> Erste Verzögerung vor dem erneuten Versuch der Verbindung. Diese Verzögerung wird bei jedem Verbindungsfehler verdoppelt.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSessionsPerChild<br /> </td> 
   <td> Maximale Anzahl der SMTP-Sitzungen nach untergeordneten Servern. Um eine Nachricht zu senden, initialisiert der MTA eine SMTP-Verbindung mit dem MTA des Empfängers. Die maximale Anzahl gleichzeitiger und aktiver SMTP-Sitzungen für einen bestimmten untergeordneten Server ist durch diesen Wert begrenzt. Wenn Sie diesen Wert mit maxSpareServers multiplizieren, erhalten Sie die maximale Anzahl von Nachrichten, die gleichzeitig von einem bestimmten untergeordneten Server verarbeitet werden können.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
 </tbody> 
</table>

Konfigurieren Sie im Knoten **mta > child > smtp > IPAffinity** die folgenden Parameter. Dies ist die Konfiguration der Verwaltung von Affinitäten mit IP-Adressen für optimierten ausgehenden SMTP-Traffic.

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
   <td> Logischer Name: von Benutzern mit der Affinität verknüpfte Namen. Namen werden durch Semikolons getrennt;<br /> </td> 
   <td> String <br /> </td> 
  </tr> 
 </tbody> 
</table>

Konfigurieren Sie im Knoten **mta > child > smtp > IP** die folgenden Parameter.

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
   <td> address<br /> </td> 
   <td> Zugehörige physische Adresse. Beispiel: '192.168.0.1'<br /> </td> 
   <td> String <br /> </td> 
  </tr> 
  <tr> 
   <td> publicId<br /> </td> 
   <td> Zugehörige öffentliche Adressen-ID. Wird als Schlüssel für den Statistikserver verwendet. Muss numerisch sein. Siehe diesen <a href="../../installation/using/email-deliverability.md#managing-ip-addresses">Abschnitt</a>.<br /> </td> 
   <td> Long<br /> </td> 
  </tr> 
  <tr> 
   <td> weight<br /> </td> 
   <td> Gibt die Häufigkeit der Verwendung dieser IP im Vergleich zu anderen IPs an (größere Gewichtungen führen zu höheren Frequenzen).<br /> </td> 
   <td> Long<br /> </td> 
  </tr> 
  <tr> 
   <td> includeDomains<br /> </td> 
   <td> Kommagetrennte Liste von Domänenmasken, die eingeschlossen werden sollen.<br /> </td> 
   <td> String <br /> </td> 
  </tr> 
  <tr> 
   <td> excludeDomains<br /> </td> 
   <td> Kommagetrennte Liste von Domänenmasken, die ausgeschlossen werden sollen.<br /> </td> 
   <td> String <br /> </td> 
  </tr> 
  <tr> 
   <td> heloHost<br /> </td> 
   <td> Computername, der mit der IP-Adresse verknüpft ist. Wird bei der Ausgabe eines SMTP-HELO-Befehls verwendet.<br /> </td> 
   <td> String <br /> </td> 
  </tr> 
 </tbody> 
</table>

## nmac {#nmac}

Im Folgenden finden Sie die verschiedenen Parameter des Knotens **nmac** . Dies ist die Konfiguration von für Push-Benachrichtigungsversand.

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
   <td> Verwenden Sie den in shared/proxyHTTP definierten HTTP-Proxy <br />. </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Relais {#relay-1}

Im Folgenden finden Sie die verschiedenen Parameter des Knotens **nmac > relay** . Dadurch wird die Verwendung eines Relais für den Nachrichtenversand (iOS HTTP2-Connector) konfiguriert.

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
   <td> address<br /> </td> 
   <td> DNS-Adresse oder Name des zu verwendenden Relais. <br /> </td> 
   <td> String <br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> port<br /> </td> 
   <td> Relay Port<br /> </td> 
   <td> Long<br /> </td> 
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

Im Folgenden finden Sie die verschiedenen Parameter des Knotens **pipelined** . Dies ist die Konfiguration des Ereignisverarbeitungsmoduls für Pipeline-Dienste.

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
   <td> URL zum Abrufen eines Gateway-Tokens.<br /> </td> 
   <td> String <br /> </td> 
   <td> 'https://api.omniture.com' <br /> </td> 
  </tr> 
  <tr> 
   <td> authPrivateKey<br /> </td> 
   <td> Privater Schlüssel zum Abrufen von Token (in AES mit der XtkKey-Option verschlüsselt).<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Automatischer Start <br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> disableAuth<br /> </td> 
   <td> Authentifizierung deaktivieren: Verbindung zu Pipeline-Diensten ohne Authentifizierung herstellen. <br /> </td> 
   <td> Boolean<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> discoverPipelineEndpoint<br /> </td> 
   <td> URL zur Erkennung der Pipeline Services-URL.<br /> </td> 
   <td> String <br /> </td> 
   <td> 'https://producer-pipeline-pnw.adobe.net'<br /> </td> 
  </tr> 
  <tr> 
   <td> dumpStatePeriodSec<br /> </td> 
   <td> Speicherzeitraum des Status: Häufigkeit, mit der die internen Informationen des Prozesses in einer Datei gespeichert werden. Inaktiv, wenn 0. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> forcedPipelineEndpoint<br /> </td> 
   <td> Listening-URL: Erzwingen Sie die Listening-URL der Pipeline-Dienste. <br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID des JavaScript, der beim Starten des Prozesses ausgeführt werden soll.<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Warnhinweis zur Speicherbelegung: Warnhinweis bezüglich der von einem bestimmten Prozess verbrauchten RAM (in MB).<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Warnung zur Speicherbelegung: Warnhinweis bezüglich der von einem bestimmten Prozess verbrauchten RAM-Menge (in MB).<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> monitorServerPort<br /> </td> 
   <td> Status-Server-Port: HTTP-Server-Anschluss, über den Sie den Status des Prozesses abfragen können. Inaktiv, wenn 0.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 7781<br /> </td> 
  </tr> 
  <tr> 
   <td> pointerFlushMessageCount<br /> </td> 
   <td> Der Zeiger wird jedes Mal, wenn diese Anzahl von Nachrichten verarbeitet wird, in der Datenbank gespeichert.<br /> </td> 
   <td> <br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
  <tr> 
   <td> pointerFlushPeriodSec<br /> </td> 
   <td> Verzögerung vor der Speicherung des Zeigers: Der Zeiger wird während dieses Zeitraums mindestens einmal in der Datenbank gespeichert (nützlich bei geringer Aktivität).<br /> </td> 
   <td> Long<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Uhrzeit des automatischen Neustart des Prozesses. Siehe <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatischer Prozessneustart</a>.<br /> </td> 
   <td> String <br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> processingJSThreads<br /> </td> 
   <td> Anzahl der Threads für die Ereignisverarbeitung mit einem personalisierten JavaScript-Connector.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> processingThreads<br /> </td> 
   <td> Anzahl der Threads für die Ereignisverarbeitung.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> retryPeriodSec<br /> </td> 
   <td> Verzögerung zwischen der Verarbeitung bei Fehler.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
  <tr> 
   <td> retryValiditySec<br /> </td> 
   <td> Nach diesem Zeitraum beenden: Verlassen Sie das Ereignis, wenn die Verarbeitung nach diesem Zeitraum immer noch fehlschlägt.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priorität am Anfang. Module mit niedriger Priorität werden zuerst gestartet und zuletzt angehalten. Das syslogd-Modul muss daher die Priorität 0 haben.<br /> </td> 
   <td> short<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Reparatur {#repair}

Im Folgenden finden Sie die verschiedenen Parameter des Knotens **reparieren** . Dies ist die Konfiguration des Datenbankreparaturmoduls.

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
   <td> Reparaturmodul für Versandaktionen: Verzögerung (in Minuten), nach der Versandaktionen vom Reparaturmodul verarbeitet werden können. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
 </tbody> 
</table>

## securityZone {#securityzone}

Im Folgenden finden Sie die verschiedenen Parameter des Knotens **securityZone** .

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
   <td> Debug-Modus für Webanwendungen zulassen.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> allowEmptyPassword<br /> </td> 
   <td> Autorisieren Sie den Benutzer, die Anwendung ohne Kennwort zu verwenden.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> allowHTTP<br /> </td> 
   <td> Genehmigung der Verwendung von HTTP für die Anmeldung des Benutzers.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> allowSQLInjection<br /> </td> 
   <td> Autorisieren Sie die Verwendung von SQLDATA in Ausdrücken.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> allowUserPassword<br /> </td> 
   <td> Benutzer-/Kennwort-Sitzungstoken zulassen.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> label<br /> </td> 
   <td> Beschriftung<br /> </td> 
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
   <td> Verwenden Sie nicht das Sicherheits-Token<br />. </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> showErrors<br /> </td> 
   <td> Fehlerdetails anzeigen<br /> </td> 
   <td> Boolean<br /> </td> 
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

Im Folgenden finden Sie die verschiedenen Parameter des Knotens **securityZone > subNetwork** .

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
   <td> Beschriftung<br /> </td> 
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
   <td> proxy<br /> </td> 
   <td> Maske oder Adresse des (umgekehrten) Proxys, der von diesem Unternetzwerk für den Zugriff auf die Instanz verwendet wird. In diesem Fall wird der Header "X-Forwarded-For"anstelle dieses Proxys getestet.<br /> </td> 
   <td> String <br /> </td> 
   <td> 127.0.0.1 <br /> </td> 
  </tr> 
 </tbody> 
</table>

## sms {#sms}

Im Folgenden finden Sie die verschiedenen Parameter des Knotens **sms** . Dies ist die Konfiguration des eingehenden SMS-Verwaltungsmoduls.

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
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> dataRetentionDays<br /> </td> 
   <td> Maximale Anzahl der Tage, in denen Dateien bearbeitet werden, die vom SMPP-Connector aufbewahrt werden.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> dataSizeMo<br /> </td> 
   <td> Maximale Größe der SMPP-Arbeitsdateien in MB.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 512<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID des JavaScript, der beim Starten des Prozesses ausgeführt werden soll.<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> keepAlivePeriod<br /> </td> 
   <td> Wiederholung des Sitzungskontinuitätsrahmens: max. Zeitraum in Sekunden zwischen zwei Frames, um darauf hinzuweisen, dass die empfangende Sitzung weiterhin aktiviert ist.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 25<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Warnhinweis zur Speicherbelegung: Warnhinweis bezüglich der von einem bestimmten Prozess verbrauchten RAM (in MB).<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Warnung zur Speicherbelegung: Warnhinweis bezüglich der von einem bestimmten Prozess verbrauchten RAM-Menge (in MB).<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> pollPeriod<br /> </td> 
   <td> Suchhäufigkeit: Zeitraum der SMS-Kontoabfrage.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Uhrzeit des automatischen Neustart des Prozesses. Siehe <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatischer Prozessneustart</a>.<br /> </td> 
   <td> String <br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> reloadPeriod<br /> </td> 
   <td> Häufigkeit der Kontoneuladungen: Häufigkeit der Neuladungen der Datenbank bei den abzurufenden Konten.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priorität am Anfang. Module mit niedriger Priorität werden zuerst gestartet und zuletzt angehalten. Das syslogd-Modul muss daher die Priorität 0 haben.<br /> </td> 
   <td> short<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> srReadDelay<br /> </td> 
   <td> Anzahl der Sekunden für die SR-Verarbeitung: Nur SRs mit einem Wiederherstellungsdatum, das vor der aktuellen Zeit liegt, abzüglich der Dauer in Sekunden, die von srReadDelay angegeben wird. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> timeout<br /> </td> 
   <td> Zeitüberschreitung bei der Kommunikation mit dem SMS-Gateway.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
 </tbody> 
</table>

### netsize {#netsize}

Im Folgenden finden Sie die verschiedenen Parameter des Knotens **sms > netsize** .

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
   <td> Zeitüberschreitung in Sekunden beim Herstellen einer Verbindung mit Netsize.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
 </tbody> 
</table>

## stat {#stat}

Im Folgenden finden Sie die verschiedenen Parameter des Knotens **stat** . Dies ist die Konfiguration des MTA-Statistikmoduls.

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
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID des JavaScript, der beim Starten des Prozesses ausgeführt werden soll.<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Warnhinweis zur Speicherbelegung: Warnhinweis bezüglich der von einem bestimmten Prozess verbrauchten RAM (in MB).<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Warnung zur Speicherbelegung: Warnhinweis bezüglich der von einem bestimmten Prozess verbrauchten RAM-Menge (in MB).<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> port<br /> </td> 
   <td> Server-Listening-Anschluss. Siehe diesen <a href="../../installation/using/email-deliverability.md#definition-of-the-server-port">Abschnitt</a>.<br /> </td> 
   <td> short<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Uhrzeit des automatischen Neustart des Prozesses. Siehe <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatischer Prozessneustart</a>.<br /> </td> 
   <td> String <br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priorität am Anfang. Module mit niedriger Priorität werden zuerst gestartet und zuletzt angehalten. Das syslogd-Modul muss daher die Priorität 0 haben.<br /> </td> 
   <td> short<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## syslogd {#syslogd}

Im Folgenden finden Sie die verschiedenen Parameter des Knotens **syslogd** . Dies ist die Konfiguration des Protokollverwaltungsmoduls.

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
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID des JavaScript, der beim Starten des Prozesses ausgeführt werden soll.<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxFileSizeMb<br /> </td> 
   <td> Maximale Größe in MB für eine Protokolldatei. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> maxNumberOfLoginsFiles<br /> </td> 
   <td> Maximale Anzahl der beizubehaltenden logins.log-Dateien. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 365<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Warnhinweis zur Speicherbelegung: Warnhinweis bezüglich der von einem bestimmten Prozess verbrauchten RAM (in MB).<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Warnung zur Speicherbelegung: Warnhinweis bezüglich der von einem bestimmten Prozess verbrauchten RAM-Menge (in MB).<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Uhrzeit des automatischen Neustart des Prozesses. Siehe <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatischer Prozessneustart</a>.<br /> </td> 
   <td> String <br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priorität am Anfang. Module mit niedriger Priorität werden zuerst gestartet und zuletzt angehalten. Das syslogd-Modul muss daher die Priorität 0 haben.<br /> </td> 
   <td> short<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## tracking {#tracking}

Im Folgenden finden Sie die verschiedenen Parameter des Knotens **tracking** . Dies ist die Konfiguration des Tracking-Servers.

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
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> blockRedirectForUnsignedTrackingLink<br /> </td> 
   <td> Deaktivieren Sie fehlerhafte URLs, die von früheren Builds generiert wurden.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> ConsolidationPeriodSec<br /> </td> 
   <td> Konsolidierungszeitraum<br /> </td> 
   <td> Long<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> dedupOpenPeriodMin<br /> </td> 
   <td> Öffnungen deduplizieren: Entfernen Sie doppelte offene Trackinglogs, um die Auswirkungen von E-Mail-Vorschauen in E-Mail-Lesern wie Outlook zu begrenzen.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> errorIgnorePercent<br /> </td> 
   <td> Ignorieren Sie bis zu X % der Fehler: Aktualisieren Sie die Trackingindikatoren nicht, solange das Verhältnis der nicht bereits berücksichtigten Journale diesen Wert nicht erreicht. <br /> </td> 
   <td> Byte<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> errorIgnorePeriod<br /> </td> 
   <td> Aktualisieren Sie die Fehlerindikatoren: maximale Dauer, bevor die Fehlerindikatoren neu berechnet werden.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
  <tr> 
   <td> indicatorsDuration<br /> </td> 
   <td> Kennzahlen berechnen während: Dauer nach dem Gültigkeitsdatum eines Versands, nach dem konsolidierte Kennzahlen nicht mehr berechnet werden.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 2592000<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> Kennung von JavaScript, die beim Starten des Prozesses ausgeführt werden soll <br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> logCountPerRequest<br /> </td> 
   <td> Anzahl der Protokolle, die durch Aufruf des Remote-Tracking-Servers angefordert werden.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Warnhinweis zur Speicherbelegung: Warnhinweis bezüglich der von einem bestimmten Prozess verbrauchten RAM (in MB).<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Warnung zur Speicherbelegung: Warnhinweis bezüglich der von einem bestimmten Prozess verbrauchten RAM-Menge (in MB).<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> phishbowlServiceAPIKey<br /> </td> 
   <td> API-Schlüssel für die Phishbowl Service Endpoint-Integration. Dadurch wird die Umleitung von falsch formatierten URLs, die aus älteren Builds generiert wurden, geschützt. <br /> </td> 
   <td> Long<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> phishbowlServiceEndpoint<br /> </td> 
   <td> Endpunkt für die Phishbowl Service-Endpoint-Integration. Dies schützt die Umleitung von falsch formatierten URLs, die aus älteren Builds generiert wurden.<br /> </td> 
   <td> Long<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Uhrzeit des automatischen Neustart des Prozesses. Siehe <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatischer Prozessneustart</a>.<br /> </td> 
   <td> String <br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priorität am Anfang. Module mit niedriger Priorität werden zuerst gestartet und zuletzt angehalten. Das syslogd-Modul muss daher die Priorität 0 haben.<br /> </td> 
   <td> short<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> trackingIgnorePercent<br /> </td> 
   <td> Ignorieren Sie bis zu X % des Trackings: Aktualisieren Sie die Trackingindikatoren nicht, solange das Verhältnis der nicht bereits berücksichtigten Journale diesen Wert nicht erreicht.<br /> </td> 
   <td> Byte<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> trackingIgnorePeriod<br /> </td> 
   <td> Aktualisierung der Trackingindikatoren: maximale Dauer, bevor Trackingindikatoren neu berechnet werden.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
  <tr> 
   <td> userAgentCacheSize<br /> </td> 
   <td> Größe des Cache für die Browserkennung.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 500<br /> </td> 
  </tr> 
 </tbody> 
</table>

## trackinglogd {#trackinglogd}

Im Folgenden finden Sie die verschiedenen Parameter des Knotens **trackinglogd** . Dies ist die Konfiguration des Trackinglog-SchreibDaemons.

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
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> Kennung von JavaScript, die beim Starten des Prozesses ausgeführt werden soll <br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxCreateFileRetry<br /> </td> 
   <td> Maximale Wiederholungsversuche: Maximale Anzahl an Dateien, die erstellt werden können, wenn das Schreiben in Protokolldateien fehlschlägt.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> maxLogsSizeOnDiskMb<br /> </td> 
   <td> Maximale Protokollgröße: Maximaler Speicherplatz, der von Protokollen auf der Festplatte (in MB) verwendet wird. Darf nicht kleiner als 100 MB sein. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 500<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Warnhinweis zur Speicherbelegung: Warnhinweis bezüglich der von einem bestimmten Prozess verbrauchten RAM (in MB).<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Warnung zur Speicherbelegung: Warnhinweis bezüglich der von einem bestimmten Prozess verbrauchten RAM-Menge (in MB).<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSharedLogs<br /> </td> 
   <td> Maximale Protokollanzahl: Maximale Anzahl der im gemeinsamen Speicher gespeicherten Protokolle. Darf nicht weniger als 10000 sein. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 25000<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Uhrzeit des automatischen Neustart des Prozesses. Siehe <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatischer Prozessneustart</a>.<br /> </td> 
   <td> String <br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> purgeLogsPeriod<br /> </td> 
   <td> Anzahl der Protokolle vor der Bereinigung: Anzahl der Protokolle, die vor Beginn der Bereinigung der Protokolldateien eingefügt wurden. Darf nicht kleiner als 50000 sein.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 50000<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priorität am Anfang. Module mit niedriger Priorität werden zuerst gestartet und zuletzt angehalten. Das syslogd-Modul muss daher die Priorität 0 haben.<br /> </td> 
   <td> short<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> webTrackingParamSize<br /> </td> 
   <td> Maximale Anzahl von Zeichen, die im gemeinsamen Speicher für zusätzliche Webtracking-Parameter gespeichert werden.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 64<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Web {#web}

Im Folgenden finden Sie die verschiedenen Parameter des Knotens **web** . Dies ist die Konfiguration des Webmoduls.

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
   <td> Maximale Anzahl von Threads.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 75<br /> </td> 
  </tr> 
  <tr> 
   <td> MinSpareThreads<br /> </td> 
   <td> Mindestanzahl von Threads.<br /> </td> 
   <td> Long<br /> </td> 
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
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> controlPort<br /> </td> 
   <td> Überwachungsanschluss von Tomcat: siehe <a href="configure-tomcat.md" target="_blank">Konfigurieren von Tomcat</a>.<br /> </td> 
   <td> short<br /> </td> 
   <td> 8005<br /> </td> 
  </tr> 
  <tr> 
   <td> httpPort<br /> </td> 
   <td> Tomcat HTTP-Listening-Anschluss: siehe <a href="configure-tomcat.md" target="_blank">Tomcat konfigurieren</a>.<br /> </td> 
   <td> short<br /> </td> 
   <td> 8080<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID des JavaScript, der beim Starten des Prozesses ausgeführt werden soll.<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxDeliveryQueueSize<br /> </td> 
   <td> Größe der Warteschlange für SubmitDelivery-Aufrufe: Maximale Anzahl an SubmitDelivery-SOAP Aufrufen, die in die Warteschlange gestellt werden können.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 50<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Warnhinweis zur Speicherbelegung: Warnhinweis bezüglich der von einem bestimmten Prozess verbrauchten RAM (in MB).<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Warnung zur Speicherverbrauch: Warnmeldung bezüglich der von einem bestimmten Prozess verbrauchten RAM-Menge (in MB)<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> notifRelay<br /> </td> 
   <td> Benachrichtigungsweiterleitung: HostName:Port aktiviert die Weiterleitung von Benachrichtigungen.<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Uhrzeit des automatischen Neustart des Prozesses. Siehe <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatischer Prozessneustart</a>.<br /> </td> 
   <td> String <br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priorität am Anfang. Module mit niedriger Priorität werden zuerst gestartet und zuletzt angehalten. Das syslogd-Modul muss daher die Priorität 0 haben.<br /> </td> 
   <td> short<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> startSoapRouterInModule<br /> </td> 
   <td> Starten Sie den SOAP Router im Modulmodus.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

### jsp {#jsp}

Im Folgenden finden Sie die verschiedenen Parameter des Knotens **web > jsp** . Dies ist die Konfiguration der von den JSPs verwendeten Parameter.

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
   <td> Boolean<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> downloadPath<br /> </td> 
   <td> Download-Ordner: Download-Pfad der Installationsprogramme für die Clientkonsolen.<br /> </td> 
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
   <td> URL SOAP Routers (http://myserver/xxx, http://jni oder mailto:xxx).<br /> </td> 
   <td> String <br /> </td> 
   <td> 'http://jni'<br /> </td> 
  </tr> 
 </tbody> 
</table>

Der Knoten **web > jsp > classpath** enthält die Liste aller Klassenpfade, die beim Starten von JVM verwendet werden sollen. Dies ist die Standardkonfiguration:

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

### jssp {#jssp}

Im Folgenden finden Sie die verschiedenen Parameter des Knotens **web > jssp** . Dies ist die Konfiguration der von den JSSPs verwendeten Parameter.

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
   <td> Aktiviert den Garbage Collector des JavaScript-Kontexts nach jeder Abfrage.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> timeToLive<br /> </td> 
   <td> Maximale Anzahl von Seiten, die von einem JavaScript-Kontext bereitgestellt werden. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
 </tbody> 
</table>

Der Knoten **web > jsp > classpath** enthält die Liste aller Klassenpfade, die beim Starten von JVM verwendet werden sollen.

### Relais {#relay-2}

Im Folgenden finden Sie die verschiedenen Parameter des Knotens **web > relay** . Dies ist die Konfiguration des Relais für HTTP-Anfragen zwischen zwei Bereichen.

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
   <td> Starten Sie das HTTP-Relais-Modul auf dem Webserver im Debug-Modus.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> forbiddenCharsInAuthority<br /> </td> 
   <td> Verbotene Zeichen (Domäne): Liste der unzulässigen Zeichen im Abschnitt "Behörde"eines URI.<br /> </td> 
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
   <td> Starten Sie das HTTP-Relais-Modul.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> startRelayInModule<br /> </td> 
   <td> Starten Sie das HTTP-Relais-Modul auf dem Webserver. <br /> </td> 
   <td> Boolean<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> timeout<br /> </td> 
   <td> Wartezeit vor dem Löschen der verbotenen URL.<br /> </td> 
   <td> String <br /> </td> 
   <td> '60'<br /> </td> 
  </tr> 
 </tbody> 
</table>

Fügen Sie für jede URL, die weitergeleitet werden soll, den Knoten &quot;**web > relay > url**&quot; hinzu (Reihenfolge einfügen definiert Priorität), indem Sie die folgenden Parameter eingeben.

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
   <td> Autorisierte IP-Adressen: kommagetrennte Liste der Quell-IP-Adressen, die den Relais für diese Maske verwenden dürfen.<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> deny<br /> </td> 
   <td> Zugriff auf diese URLs verweigern (HTTP 403-Fehler zurückgeben)<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> hostMask<br /> </td> 
   <td> DNS-Alias für die Weiterleitung: kommagetrennte Liste von DNS-Alias-Masken für die Weiterleitung (z. B. '*.adobe.com').<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> httpAllowed<br /> </td> 
   <td> HTTP-Zugriff unabhängig von der Sicherheitszone (wie webApps) autorisiert. <br /> </td> 
   <td> Boolean<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> relayHost<br /> </td> 
   <td> Hinzufügen des ursprünglichen Hosts: Verwenden Sie den HTTP-Header "Host"der ursprünglichen Anforderung bei der Wiedergabe.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> relayPath<br /> </td> 
   <td> Initial-URL-Pfad hinzufügen: Hängen Sie den vollständigen Pfad der URLs an, um sie an die URL der Zielseite weiterzuleiten. <br /> </td> 
   <td> Boolean<br /> </td> 
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
   <td> URL der Zielseite: siehe <a href="configure-tomcat.md" target="_blank">Tomcat konfigurieren</a>.<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> timeout<br /> </td> 
   <td> Maximale Ausführungszeit (in Sekunden) der Anforderung, die weitergeleitet wird.<br /> </td> 
   <td> Long<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> urlPath<br /> </td> 
   <td> Maske der URLs, die weitergeleitet werden sollen (z. B. "/nl*", "*.jsp").<br /> </td> 
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

Fügen Sie für jeden HTTP-Header einen Knoten **web > relay > responseHeader** hinzu, um Antworten hinzuzufügen, die an den Relais weitergeleitet werden.

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
   <td> Kopfzeilenname<br /> </td> 
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

Im Folgenden finden Sie die verschiedenen Parameter des Knotens **web > redirection** . Dies ist die Konfiguration des Umleitungsmoduls.

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
   <td> Organisations-ID: eindeutige Organisationskennung innerhalb der Adobe Experience Cloud, die insbesondere für den VisitorID-Dienst und die IMS-SSO verwendet wird. <br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> P3PCompactPolicy<br /> </td> 
   <td> Wert, der die Richtlinie beschreibt, die für permanente Cookies verwendet wird (entspricht dem P3P Compact Policy-Format). <br /> </td> 
   <td> String <br /> </td> 
   <td> "CAO DSP COR CURa DEVa TAIa OUR BUS IND UNI COM NAV"<br /> </td> 
  </tr> 
  <tr> 
   <td> cookieDomain<br /> </td> 
   <td> Kommagetrennte Liste der Domänen, die konfiguriert werden sollen, um explizit anzugeben, welche Domäne Cookies setzen soll. <br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> databaseId<br /> </td> 
   <td> Datenbank-ID, die mit der Tracking-Instanz verknüpft ist.<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> defLogCount<br /> </td> 
   <td> Protokollanzahl nach Aufruf: Anzahl der Protokolle, die standardmäßig bei einem Aufruf der Methode GetTrackingLogs zurückgegeben werden.<br /> </td> 
   <td> Long<br /> </td> 
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
   <td> Maximale Auftragsanzahl: Maximale Anzahl an Versandaktionen im Cache. Darf nicht kleiner als 50 sein. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> showSourceIP<br /> </td> 
   <td> Wenn der Wert auf false gesetzt ist, ist der Wert von sourceIP in der Antwort, die von r/test zurückgegeben wird, eine leere Zeichenfolge. <br /> </td> 
   <td> Boolean<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> startRedirection<br /> </td> 
   <td> Starten Sie den Weiterleitungsdienst.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> startRedirectionInModule<br /> </td> 
   <td> Starten Sie den Weiterleitungsdienst im Modulmodus.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> trackWebVisitors<br /> </td> 
   <td> Webtracking: Erstellung von Protokollen für die Seiten, die von unbekannten Benutzern besucht werden. <br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> trackingPassword<br /> </td> 
   <td> Passwort, das vom Weiterleitungsserver verwendet wird.<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

Im Folgenden finden Sie die verschiedenen Parameter des Knotens **web > redirection > reserveServer** .

Weitere Informationen finden Sie unter [Redundant tracking](../../installation/using/configuring-campaign-server.md#redundant-tracking).

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
   <td> Berücksichtigt wenn: Der Tracking-Server wird berücksichtigt, wenn der Ausdruck "true"zurückgibt. <br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> id<br /> </td> 
   <td> Name<br /> </td> 
   <td> String <br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> url<br /> </td> 
   <td> Zusätzliche Umleitungsserver-URL<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

### spamCheck {#spamcheck}

Im Folgenden finden Sie die verschiedenen Parameter des Knotens **web > spamCheck** . Dies ist die Konfiguration der Bewertungsparameter E-Mail-Anti-Spam-Bewertung .

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
   <td> Befehl zum Ausführen, um den Anti-Spam-Wert einer E-Mail zu bewerten (z. B. 'perl spamcheck.pl').<br /> </td> 
   <td> String <br /> </td> 
  </tr> 
 </tbody> 
</table>

## wfserver {#wfserver}

Im Folgenden finden Sie die verschiedenen Parameter des Knotens **wfserver** . Dies ist die Workflow-Prozesskonfiguration.

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
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> dataBasePoolPeriodSec<br /> </td> 
   <td> Punkt<br /> </td> 
   <td> Long<br /> </td> 
   <td> 20<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID des JavaScript, der beim Starten des Prozesses ausgeführt werden soll.<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Warnhinweis zur Speicherbelegung: Warnhinweis bezüglich der von einem bestimmten Prozess verbrauchten RAM (in MB).<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Warnung zur Speicherbelegung: Warnhinweis bezüglich der von einem bestimmten Prozess verbrauchten RAM-Menge (in MB).<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> notifRelay<br /> </td> 
   <td> Benachrichtigungsweiterleitung: HostName:Port aktiviert die Weiterleitung von Benachrichtigungen.<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Uhrzeit des automatischen Neustart des Prozesses. Siehe <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatischer Prozessneustart</a>.<br /> </td> 
   <td> String <br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priorität am Anfang. Module mit niedriger Priorität werden zuerst gestartet und zuletzt angehalten. Das syslogd-Modul muss daher die Priorität 0 haben.<br /> </td> 
   <td> short<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>
