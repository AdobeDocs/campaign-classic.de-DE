---
title: Die Serverkonfigurationsdatei
seo-title: Die Serverkonfigurationsdatei
description: Die Serverkonfigurationsdatei
seo-description: null
page-status-flag: never-activated
uuid: 8ef7168b-3543-4830-80b0-65a023158b3f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: appendices
discoiquuid: da2198a3-7cef-4419-894d-e5bb51bb480c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 09fa3751d94fd71a68470174dd0b4a48d94d3f44

---


# Die Serverkonfigurationsdatei{#the-server-configuration-file}

Die Gesamtkonfiguration von Adobe Campaign wird in der Datei &quot; **serverConf.xml** &quot;im **conf** -Ordner des Installationsordners definiert. In diesem Abschnitt werden alle verschiedenen Knoten und Parameter der Datei &quot; **serverConf.xml** &quot;aufgelistet.

>[!NOTE]
>
>Serverseitige Konfigurationen können nur von Adobe für Bereitstellungen ausgeführt werden, die von Adobe gehostet werden. Weitere Informationen zu den verschiedenen Bereitstellungen finden Sie im Abschnitt [Hosting-Modelle](../../installation/using/hosting-models.md) oder in [diesem Artikel](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html). Die Installations- und Konfigurationsschritte für gehostete und hybride Modelle werden in diesem [Abschnitt](../../installation/using/hosted-model.md)erläutert.

Die ersten Parameter befinden sich innerhalb des **freigegebenen** Knotens. Diese beziehen sich auf die Instanz. Sie werden potenziell von allen nlserver-Befehlen (nlserver web, nlserver wfserver usw.) verwendet. Die anderen Abschnitte beziehen sich auf einen bestimmten nlserver-Unterbefehl.

**Freigegebene Parameter**

* [Authentifizierung](#authentication)
* [dataStore](#datastore)
* [dnsConfig](#dnsconfig)
* [exec](#exec)
* [htmlToPdf](#htmltopdf)
* [javaScript](#javascript)
* [mailExchanger](#mailexchanger)
* [module](#module)
* [Überwachung](#monitoring)
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
* [pipeliniert](#pipelined)
* [Reparatur](#repair)
* [securityZone](#securityzone)
* [sms](#sms)
* [stat](#stat)
* [syslogd](#syslogd)
* [tracking](#tracking)
* [trackinglogd](#trackinglogd)
* [web](#web)
* [wfserver](#wfserver)

## authentication {#authentication}

Im Folgenden finden Sie die verschiedenen Parameter des **Authentifizierungsknotens** :

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
   <td> Aktivieren Sie die IP-Adressprüfung.<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> defaultMode<br /> </td> 
   <td> Standardidentifizierungsmodus.<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> 'nl'<br /> </td> 
  </tr> 
  <tr> 
   <td> longSessionTimeOutSec<br /> </td> 
   <td> Timeout langer Sitzungen in Sekunden.<br /> </td> 
   <td> lang<br /> </td> 
   <td> 1296000<br /> </td> 
  </tr> 
  <tr> 
   <td> securityTimeOutSec<br /> </td> 
   <td> Sicherheits-Token-Timeout in Sekunden.<br /> </td> 
   <td> lang<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
  <tr> 
   <td> sessionCacheSec<br /> </td> 
   <td> Cache-Dauer: Cache mit Sitzungsinformationen in Sekunden.<br /> </td> 
   <td> lang<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> sessionTimeOutSec<br /> </td> 
   <td> Sitzungs-Timeout in Sekunden.<br /> </td> 
   <td> lang<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
 </tbody> 
</table>

### XTK {#xtk}

Hier sind die verschiedenen Parameter des Knotens **Authentication > XTK** :

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
   <td> Kennwort des internen Kontos.<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> internalSecurityZone<br /> </td> 
   <td> Sicherheitszone des internen Kontos: autorisierte Zone für das interne Konto.<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> 'lan'<br /> </td> 
  </tr> 
 </tbody> 
</table>

## dataStore {#datastore}

Hier sind die verschiedenen Parameter des **dataStore** -Knotens. Hier werden die Serverdatenquellen definiert.

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
   <td> Zeichenfolge<br /> </td> 
   <td> '$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/export/' <br /> </td> 
  </tr> 
  <tr> 
   <td> extraSandboxedDirectories<br /> </td> 
   <td> Extra sandboxed directories: other paths to be added in the sandbox (coma separated).<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> '/home/Customers/,/sftp/' <br /> </td> 
  </tr> 
  <tr> 
   <td> formCacheTimeToLive<br /> </td> 
   <td> Ablaufverzögerung für Formular-Cache: Zeitüberschreitung in Sekunden, nach der ein Cache-Eintrag ungültig wird. O bedeutet, dass Cache-Einträge erst zur Veröffentlichungszeit aktualisiert werden.<br /> </td> 
   <td> lang<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> hosts<br /> </td> 
   <td> DNS-Masken: Liste der DNS-Masken, die diese Instanz bereitstellt (kommagetrennt, kann * und ? Muster).<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> '*'<br /> </td> 
  </tr> 
  <tr> 
   <td> interactionCacheTimeToLive<br /> </td> 
   <td> JSSP-Cache-Ablaufverzögerung der Interaktion: Zeitüberschreitung in Sekunden, nach der ein Cache-Eintrag ungültig wird. Ein negativer Wert bedeutet, dass der Cache immer ungültig ist. '0', leere oder ungültige Werte werden als 60 angesehen.<br /> </td> 
   <td> lang<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> lang<br /> </td> 
   <td> Instanzsprache (Enumeration). Mögliche Werte sind "fr_FR" (Français), "en_GB" (Englisch (UK)), "en_US" (Englisch (USA)), "de_DE" (Deutsch) und "ja_JP" (Japanisch).<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> 'en_US'<br /> </td> 
  </tr> 
  <tr> 
   <td> uploadDirectory<br /> </td> 
   <td> Ordner hochladen: Pfad des Zielverzeichnisses für die hochgeladenen Daten.<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> '$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/upload/' <br /> </td> 
  </tr> 
  <tr> 
   <td> uploadWhitelist<br /> </td> 
   <td> Autorisierte Dateien zum Herunterladen, getrennt durch ','. Die Zeichenfolge muss ein gültiger, regulärer Java-Ausdruck sein. Siehe <a href="../../installation/using/configuring-campaign-server.md#limiting-uploadable-files" target="_blank">Beschränkungen für hochladbare Dateien</a>.<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
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
   <td> Zeichenfolge<br /> </td> 
   <td> '/v1/secret/campaign/'<br /> </td> 
  </tr> 
  <tr> 
   <td> vaultTokenPath<br /> </td> 
   <td> Lokaler Pfad der Datei, die den Volt-Token enthält. $(HOME) kann in diesem Pfad verwendet werden (aber nicht andere ENV-Variablen).<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> '$(HOME)/.vaulttoken'<br /> </td> 
  </tr> 
  <tr> 
   <td> vaultUrl<br /> </td> 
   <td> Vault-URL von HashiCorp <br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> viewCacheTimeToLive<br /> </td> 
   <td> Gültigkeitsdauer des Ansichtscache: Zeitüberschreitung in Sekunden, nach der ein Cache-Eintrag ungültig wird. Ein negativer Wert bedeutet, dass der Cache immer ungültig ist. '0', leere oder ungültige Werte werden als 60 angesehen.<br /> </td> 
   <td> lang<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> workingDirectory<br /> </td> 
   <td> XPath des Arbeitsverzeichnisses.<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> workingDirectory :XPath des Arbeitsverzeichnisses. Standard: '$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/workspace/'<br /> </td> 
  </tr> 
 </tbody> 
</table>

### proxyAdjust {#proxyadjust}

Hier sind die verschiedenen Parameter des Knotens **dataStore > proxyAdjust** . URLs, die mit dem regulären Ausdruck übereinstimmen, werden basierend auf der in urlBase definierten URL neu generiert.

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
   <td> Basis, die beim Generieren externer URLs verwendet wird. Ex: https://server.domain.com<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
  </tr> 
  <tr> 
   <td> urlRegEx<br /> </td> 
   <td> Regulärer Ausdruck zur Übereinstimmung mit URLs. Ex: http://server\.lan\.net.*<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
  </tr> 
 </tbody> 
</table>

### dataSource {#datasource}

Hier sind die verschiedenen Parameter des Knotens **dataStore > dataSource** .

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
   <td> Zeichenfolge<br /> </td> 
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
   <td> Boolesch<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> dbSchema<br /> </td> 
   <td> Arbeitsbereich<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> verschlüsselt<br /> </td> 
   <td> Verschlüsseltes Kennwort<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> login<br /> </td> 
   <td> Konto<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> password<br /> </td> 
   <td> Passwort<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Anbieter<br /> </td> 
   <td> Typ (Aufzählung). Mögliche Werte sind "Oracle", "MSSQL" (Microsoft SQL Server), "PostgreSQL" (PostgreSQL, Greenplum), "Teradata", "DB2", "MySQL", "Netezza", "AsterData", "SAPHANA" (SAP HANA), "RedShift" (Amazon Redshift), ODBC (C (Sybase ASE, Sybase IQ)), 'Relay' (HTTP Relay to remote database).<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> 'Oracle'<br /> </td> 
  </tr> 
  <tr> 
   <td> server<br /> </td> 
   <td> Server<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> timezone<br /> </td> 
   <td> Zeitzone: Siehe <a href="../../installation/using/time-zone-management.md" target="_blank">Zeitzonenverwaltung</a>.<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
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
   <td> Datumsfelder mit Zeitzone: Siehe <a href="../../installation/using/time-zone-management.md" target="_blank">Zeitzonenverwaltung</a>.<br /> </td> 
   <td> Boolesch<br /> </td> 
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
   <td> Zeichenfolge<br /> </td> 
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
   <td> liveTestDelaySec<br /> </td> 
   <td> Verzögerung zwischen Überprüfung der Verbindungs-Gültigkeit.<br /> </td> 
   <td> Short<br /> </td> 
  </tr> 
  <tr> 
   <td> freeCnx<br /> </td> 
   <td> Anzahl der kostenlosen Verbindung im Pool.<br /> </td> 
   <td> Short<br /> </td> 
  </tr> 
  <tr> 
   <td> maxCnx<br /> </td> 
   <td> Maximale Anzahl der zulässigen Verbindungen, bevor eine neue Verbindung verweigert wird. Siehe diese <a href="https://helpx.adobe.com/campaign/kb/how-to-increase-the-maximum-number-of-database-connections-from-.html">technischen Hinweise</a>.<br /> </td> 
   <td> Short<br /> </td> 
  </tr> 
  <tr> 
   <td> maxIdleDelaySec<br /> </td> 
   <td> Maximale Leerlaufzeit der Verbindung. 0 bedeutet Standardwert.<br /> </td> 
   <td> Short<br /> </td> 
  </tr> 
 </tbody> 
</table>

### virtualDir {#virtualdir}

Hier sind die verschiedenen Parameter des Knotens **dataStore > virtualDir** . Dies ist die Konfiguration des virtuellen Ordners zu einer echten Ordnerzuordnung.

Weitere Informationen finden Sie unter [Verwalten öffentlicher Ressourcen](../../installation/using/configuring-campaign-server.md#managing-public-resources).

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
   <td> Name des virtuellen Ordners <br /> </td> 
   <td> Zeichenfolge<br /> </td> 
  </tr> 
  <tr> 
   <td> path<br /> </td> 
   <td> Vollständiger Pfad des tatsächlichen Ordners<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
  </tr> 
 </tbody> 
</table>

Die Standardkonfiguration lautet:

```
<virtualDir name="images" path="$(XTK_INSTALL_DIR)/var/res/img/"/>
<virtualDir name="formCache" path="$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/formCache/"/>
<virtualDir name="publicFileRes" path="$(XTK_INSTALL_DIR)/var/res/$(INSTANCE_NAME)"/>
```

### preprocessCommand {#preprocesscommand}

Hier sind die verschiedenen Parameter des Knotens **dataStore > preprocessCommand** . Dies sind die autorisierten Befehle zur Vorverarbeitung der Workflow-Aktivität &quot;Datei laden&quot;.

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
   <td> Zeichenfolge<br /> </td> 
  </tr> 
  <tr> 
   <td> label<br /> </td> 
   <td> Titel der Befehlszeile<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
  </tr> 
  <tr> 
   <td> name<br /> </td> 
   <td> Name der Befehlszeile<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
  </tr> 
 </tbody> 
</table>

Die Standardkonfiguration lautet:

```
<preprocessCommand command="" label="None" name="none"/>
<preprocessCommand command="zcat &quot;$fileName&quot;" label="Decompression" name="zcat"/><preprocessCommand command="gpg --decrypt &quot;$fileName&quot;" label="Decrypt" name="gpg"/>
```

## dnsConfig {#dnsconfig}

Hier sind die verschiedenen Parameter des Knotens **dnsConfig** (DNS-Konfiguration).

For additional information, refer to this [section](../../installation/using/configuring-campaign-server.md).

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
   <td> Domänenname: Standarddomänenname. Wird vom SMTP HELO-Befehl verwendet. Standardmäßig werden die Netzwerkparameter der ersten unter Windows deklarierten Netzwerkschnittstelle verwendet. oder analysiert das file/etc/resolv.conf unter Linux (Domäne oder Sucheintrag). <br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> nameServers<br /> </td> 
   <td> DNS-Server: Kommagetrennte Liste der Domänennamenserver (DNS). Siehe den Hinweis unten.<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> retry<br /> </td> 
   <td> Anzahl der Wiederholungen für eine DNS-Abfrage.<br /> </td> 
   <td> lang<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> timeout<br /> </td> 
   <td> Timeout in Millisekunden für eine DNS-Abfrage.<br /> </td> 
   <td> lang<br /> </td> 
   <td> 5000<br /> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Hinweis zu **nameServer**: verwendet standardmäßig das Netzwerk
>Parameter der ersten unter Windows deklarierten Netzwerkschnittstelle
>nicht in UNIX definiert. Definiert die Domänennamenserver (DNS)
>von MTA verwendet, um den Mail-Exchange für
>eine Domäne.
>
>Wenn dieser Wert nicht definiert ist, sucht die MTA diese Informationen in der Konfiguration des Host-Netzwerks. Wenn mehrere DNS-Adressen möglich sind, müssen die verschiedenen DNS-Adressen durch ein Komma getrennt werden (Beispiel: 212.155.207.1,212.155.207.2). Wenn Ihr Lieferserver mehrere Netzwerkschnittstellen hat, ist die von der MTA verwendete DNS-Liste die erste. In diesem Fall sollten Sie den Parameter **nameServer** angeben, um Unklarheiten zu vermeiden.

>[!CAUTION]
>
>Wenn Ihre Netzwerk-Host-Konfiguration DHCP verwendet, findet die MTA nicht die DNS-Liste, die von DHCP bereitgestellt wird. In diesem Fall sollten Sie die DNS-Liste in den Netzwerkparametern des Windows-Bedienfelds angeben.

## exec {#exec}

Hier sind die verschiedenen Parameter des **exec** -Knotens (Befehlsausführung).

Weitere Informationen finden Sie unter [Eingrenzen von autorisierten externen Befehlen](../../installation/using/configuring-campaign-server.md#restricting-authorized-external-commands).

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
   <td> Pfad zur Datei, die die Befehle zur schwarzen Liste enthält. <br /> </td> 
   <td> Zeichenfolge<br /> </td> 
  </tr> 
  <tr> 
   <td> Benutzer<br /> </td> 
   <td> Führen Sie Befehle als ein anderer Benutzer aus.<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
  </tr> 
 </tbody> 
</table>

## htmlToPdf {#htmltopdf}

Hier sind die verschiedenen Parameter des **Knotens htmlToPdf** . Dies ist die Konfiguration des Dienstes zum Konvertieren von Webseiten in PDF-Dokumente.

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
   <td> Zeichenfolge<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessusCount<br /> </td> 
   <td> Max. Anzahl der Konvertierungsprozesse, die gleichzeitig auf einem Computer zulässig sind.<br /> </td> 
   <td> lang<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> mode<br /> </td> 
   <td> Tool für die Konvertierung. Mögliche Werte sind: phantomjs, wkhtmltopdf, andere, deaktiviert<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> "phantomjs" <br /> </td> 
  </tr> 
  <tr> 
   <td> timeout<br /> </td> 
   <td> Timeout für eine Konversion: maximale Konvertierungszeit in Sekunden. Über diesen Schwellenwert hinaus wird der Konvertierungsprozess gestoppt und ein Fehler ausgegeben.<br /> </td> 
   <td> lang<br /> </td> 
   <td> 120<br /> </td> 
  </tr> 
  <tr> 
   <td> verbose<br /> </td> 
   <td> Funktionsmodus: im ausführlichen Modus starten, um mögliche Fehler zu diagnostizieren.<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> waitTime<br /> </td> 
   <td> Verzögerung beim Warten auf einen Prozess: Verzögerung in Sekunden, wenn alle Prozesse gleichzeitig verwendet werden und auf die Freigabe eines Prozesses gewartet wird. Wenn diese Verzögerung überschritten wird, wird die Konvertierung beendet und ein Fehler ausgegeben. <br /> </td> 
   <td> lang<br /> </td> 
   <td> 15<br /> </td> 
  </tr> 
 </tbody> 
</table>

Beispiel für phantomjs:

```
phantomjs - -ignore-ssl-errors=true '$(XTK_INSTALL_DIR)/bin/htmlToPdf.js' '-out:{outPdf}' '-post:{postFile}' '-url:{originUrl}' -sessiontoken:{sessiontoken} -format:{format} -orientation:{orientation} -marginTop:{marginTop} -marginLeft:{marginLeft} -marginRight:{marginRight} -marginBottom:{marginBottom}
```

## javaScript {#javascript}

Hier sind die verschiedenen Parameter des **javaScript** -Knotens. Dies ist die Konfiguration des JavaScript-Interpreters.

Weitere Informationen finden Sie in der [Berichterstellungsdokumentation](../../reporting/using/actions-on-reports.md#memory-allocation) und in dieser [TechNote](https://helpx.adobe.com/campaign/kb/out-of-memory-error-in-js-code-activity-in-workflows.html).

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
   <td> Maximale Größe in Megabyte, bevor der Müllsammler ausgeführt wird.<br /> </td> 
   <td> lang<br /> </td> 
   <td> 512 <br /> </td> 
  </tr> 
  <tr> 
   <td> stapelSizeKB<br /> </td> 
   <td> Größe der einzelnen Stack-Stücke in Kilobit. Dies ist ein Optimierungsparameter für die Speicherverwaltung, den die meisten Benutzer nicht anpassen sollten. <br /> </td> 
   <td> lang<br /> </td> 
   <td> 8<br /> </td> 
  </tr> 
 </tbody> 
</table>

## mailExchanger {#mailexchanger}

Hier sind die verschiedenen Parameter des **mailExchange-Knotens** . Dies ist die Konfiguration des SMTP-Servers.

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
   <td> Zeichenfolge<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> mxPort<br /> </td> 
   <td> TCP-Anschluss des SMTP-Servers, der für die E-Mail-Übertragung verwendet wird.<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> 25<br /> </td> 
  </tr> 
 </tbody> 
</table>

## module {#module}

Hier sind die verschiedenen Parameter des **Modulknotens** . Dies ist die Konfiguration für die Namespaces Restriktionsmodul xtk.

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
   <td> Standardnamespace, der beim Erstellen einer neuen Entität verwendet wird.<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> 'cus'<br /> </td> 
  </tr> 
 </tbody> 
</table>

## monitoring {#monitoring}

Hier sind die verschiedenen Parameter des **Überwachungsknotens** . Dies ist die Konfiguration des Überwachungsdienstes.

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
   <td> maxVorbereitungJobsSec<br /> </td> 
   <td> Maximale Vorbereitungszeit: Dauer in Sekunden, nach der eine Übermittlungsaktion nicht mehr vorbereitet werden sollte.<br /> </td> 
   <td> lang<br /> </td> 
   <td> 3600<br /> </td> 
  </tr> 
  <tr> 
   <td> unixScript<br /> </td> 
   <td> Vom Überwachungsdienst ausgeführtes Unix-Skript.<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> winScript<br /> </td> 
   <td> Vom Überwachungsdienst auszuführendes Windows-Skript.<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

## ooconv {#ooconv}

Hier sind die verschiedenen Parameter des **ooconv** -Knotens. Dies ist die Konfiguration des Dokumentkonvertierungsservers.

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
   <td> lang<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxServerIdleSec<br /> </td> 
   <td> Maximale Leerlaufzeit des OpenOffice-Servers vor dem erzwungenen Schließen.<br /> </td> 
   <td> lang<br /> </td> 
   <td> 7200<br /> </td> 
  </tr> 
  <tr> 
   <td> portRange<br /> </td> 
   <td> Intervall der Anschlüsse, auf denen die OpenOffice-Server lauschen.<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> 8101-8110<br /> </td> 
  </tr> 
  <tr> 
   <td> url<br /> </td> 
   <td> URL des Dokumentkonvertierungsservers.<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> http://localhost:8080/nl/jsp/ooconv.jsp'<br /> </td> 
  </tr> 
 </tbody> 
</table>

## proxyConfig {#proxyconfig}

Hier sind die verschiedenen Parameter des **Knoten proxyConfig** . Dies ist die Konfiguration von Proxyparametern.

Weitere Informationen finden Sie unter [Proxy-Verbindungskonfiguration](../../installation/using/configuring-campaign-server.md#proxy-connection-configuration).

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
   <td> Verwenden Sie einen Proxyserver.<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> override<br /> </td> 
   <td> Ausnahmen: Liste der Adressen, bei denen die Parameter der Proxy-Klasse ignoriert werden.<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
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

### HTTP-Proxy/Secure-Proxy {#http-proxy---secure-proxy-}

Konfigurieren Sie im Knoten **proxyConfig > HTTP Proxy / Secure proxy** die folgenden Parameter.

Weitere Informationen finden Sie unter [Proxy-Verbindungskonfiguration](../../installation/using/configuring-campaign-server.md#proxy-connection-configuration).

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
   <td> Zeichenfolge<br /> </td> 
  </tr> 
  <tr> 
   <td> login<br /> </td> 
   <td> Für die Verbindung zum Proxyserver anmelden<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
  </tr> 
  <tr> 
   <td> password<br /> </td> 
   <td> Kennwort für die Verbindung mit dem Proxyserver<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
  </tr> 
  <tr> 
   <td> port<br /> </td> 
   <td> Proxyserver-Anschluss<br /> </td> 
   <td> Short<br /> </td> 
  </tr> 
 </tbody> 
</table>

## threadPool {#threadpool}

Hier sind die verschiedenen Parameter des Knotens **threadPool** .

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
   <td> lang<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## urlPermission {#urlpermission}

Hier sind die verschiedenen Parameter des **urlPermission** -Knotens. Dies ist die Liste der URLs, auf die der JavaScript-Code zugreifen kann.

Liste der Domänen und regulären Ausdrücke, die angeben, ob eine im JavaScript-Code gefundene URL vom Adobe Campaign-Server verwendet werden kann oder nicht.

Wenn die URL nicht gefunden werden kann, wird die Standardaktion gemäß dem angegebenen Standardmodus ausgeführt.

Weitere Informationen finden Sie unter Schutz [ausgehende Verbindungen](../../installation/using/configuring-campaign-server.md#url-permissions).

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
   <td> Standardaktion, wenn die URL nicht in der Liste der autorisierten Benutzer enthalten ist (Aufzählung). Mögliche Werte sind "ignore"(autorisieren ohne Warnmeldung, dies erfordert die Deaktivierung des Schutzes), "warn"(autorisieren und geben Sie eine Warnmeldung) und "Ablehnen"(verbieten Sie den Zugriff auf die URL).<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> deny<br /> </td> 
  </tr> 
  <tr> 
   <td> debugTrace<br /> </td> 
   <td> Debugging-Ablaufverfolgung des URL-Auswahlmechanismus: gibt während der URL-Überprüfung zusätzliche Meldungen aus.<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

### url {#url}

Fügen Sie für jede URL einen **URL** -Knoten mit den folgenden Parametern hinzu:

Weitere Informationen finden Sie unter Schutz [ausgehende Verbindungen](../../installation/using/configuring-campaign-server.md#url-permissions).

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
   <td> Domänenname oder Domänenname des übergeordneten Elements, der von der URL betroffen ist: die Domäne der URL ganz oder teilweise zu überprüfen, um die Überprüfung zu beschleunigen. Die URL wird nur in Bezug auf den regulären Ausdruck überprüft, wenn die Domäne dsnSuffix enthält.<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
  </tr> 
  <tr> 
   <td> urlRegEx<br /> </td> 
   <td> Regulärer Ausdruck zum Präzisieren der Validierung von URLs, die zu dieser Domäne gehören: regulärer Ausdruck, den die URL überprüfen muss, sollte sie mit dnsSuffix übereinstimmen.<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
  </tr> 
 </tbody> 
</table>

Wenn ein Datensatz **dnsSuffix** , aber nicht urlRegEx **** erfüllt, wird der folgende Datensatz untersucht.

Um beispielsweise den Zugriff auf alle URLs der Domäne &quot;business.com&quot;zu genehmigen, können wir zwei Datensätze definieren:

dnsSuffix=&quot;business.com&quot; urlRegEx=&quot;http://.*&quot;

and

dnsSuffix=&quot;business.com&quot; urlRegEx=&quot;https://.*&quot;

Die Standardkonfiguration lautet:

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

Hier sind die verschiedenen Parameter des **xtkJobs** -Knotens. Dies ist die Konfiguration der Serveraufträge.

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
   <td> Aktualisierungszeitraum des Speicherstatus bei der Serververarbeitung (in ms).<br /> </td> 
   <td> lang<br /> </td> 
   <td> 500<br /> </td> 
  </tr> 
 </tbody> 
</table>

## archiving {#archiving}

Hier sind die verschiedenen Parameter des **Archivierungsknotens** . Dies ist die Konfiguration der ausgeführten Archivierungsvorgänge im Hintergrund.

Weitere Informationen finden Sie unter [Aktivieren der E-Mail-Archivierung (lokal)](../../installation/using/email-archiving.md#activating-email-archiving--on-premise-).

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
   <td> lang<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> archivingType<br /> </td> 
   <td> Archivierungsstrategie für gesendete Nachrichten (Aufzählung). Mögliche Werte sind '0' (kein Archivieren) und '1' (Transfer Archivierung gesendeter Nachrichten an einen SMTP-Server).<br /> </td> 
   <td> Byte<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> args<br /> </td> 
   <td> Startparameter<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
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
   <td> Größe eines komprimierten Archivs: maximale Anzahl von Dateien in einem komprimierten Archiv.<br /> </td> 
   <td> lang<br /> </td> 
   <td> 10000<br /> </td> 
  </tr> 
  <tr> 
   <td> compressionFormat<br /> </td> 
   <td> Komprimierungsformat, das bei der Archivierung verwendet wird (Aufzählung). Mögliche Werte sind '0' (keine Komprimierung) und '1' (komprimieren gesendeter Nachrichten im ZIP-Format).<br /> </td> 
   <td> Byte<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> expirationDelay<br /> </td> 
   <td> Verzögerung vor der automatischen Archivierung nicht verarbeiteter E-Mails: Anzahl der Tage, bevor unverarbeitete E-Mails archiviert werden.<br /> </td> 
   <td> lang<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID von JavaScript, das beim Starten des Prozesses ausgeführt wird.<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Speicherverbrauchswarnung: Warnhinweis über die von einem bestimmten Prozess belegte RAM (in MB).<br /> </td> 
   <td> lang<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Speicherverbrauchswarnung: Warnhinweis über die von einem bestimmten Prozess belegte RAM (in MB).<br /> </td> 
   <td> lang<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> pollDelay<br /> </td> 
   <td> Verzögerung (in Sekunden) zwischen jedem Update-Ereignis.<br /> </td> 
   <td> lang<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Die Uhrzeit, zu der der Prozess automatisch neu gestartet wird. Siehe <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatischer Prozessneustart</a>.<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> purgeArchivesDelay<br /> </td> 
   <td> Anzahl der Tage, bevor unverarbeitete E-Mails gelöscht werden.<br /> </td> 
   <td> lang<br /> </td> 
   <td> 7<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priorität am Anfang. Module mit niedriger Priorität werden zuerst gestartet und zuletzt beendet. Das syslogd-Modul muss daher die Priorität 0 haben.<br /> </td> 
   <td> Short<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> smtpBccAddress<br /> </td> 
   <td> Archivieren des Zielziels<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> smtpEnableTLS<br /> </td> 
   <td> Aktivieren Sie die SMTPS-Unterstützung: Aktiviert die Bereitstellung von E-Mails im abgesicherten Modus (STARTTLS/SMTPS), wenn sie vom Remote-Server unterstützt werden.<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> smtpNbConnection<br /> </td> 
   <td> Anzahl der Verbindungen zum SMTP-Archivierungsserver.<br /> </td> 
   <td> lang<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> smtpRelayAddress<br /> </td> 
   <td> Kommagetrennte Liste der DNS-Namen oder IP-Adressen der zu verwendenden SMTP-Relais. <br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> smtpRelayPort<br /> </td> 
   <td> IP-Anschluss des SMTP-Servers.<br /> </td> 
   <td> lang<br /> </td> 
   <td> 25<br /> </td> 
  </tr> 
 </tbody> 
</table>

## inMail {#inmail}

Hier sind die verschiedenen Parameter des **InMail** -Knotens. Dies ist die Konfiguration des Inbound Email Management Moduls.

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
   <td> Zeichenfolge<br /> </td> 
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
   <td> Instanzname überprüfen: Wenn "true", muss der Name der Adobe Campaign-Instanz in den Nachrichten-ID-Headern mit dem Namen der aktuellen Instanz übereinstimmen. <br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> defaultForwardAddress<br /> </td> 
   <td> Anschrift: Standard-E-Mail-Übertragungsadresse wird nicht von einer Regel verarbeitet. <br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> errorForwardAddress<br /> </td> 
   <td> Fehleradresse: Standardadresse zur Übertragung ungültiger E-Mails (ungültige MIME-Kodierung). <br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> ignoreSize<br /> </td> 
   <td> Nachrichtengröße ignorieren: wird verwendet, um die Größe einer von POP3-Servern zurückgegebenen Meldung zu ignorieren. In diesem Fall erwartet das Modul ein '. at the end of the messages. <br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> inMailPeriodSec<br /> </td> 
   <td> Lesezeitraum der Nachricht: Abrufhäufigkeit der Meldungswarteschlange.<br /> </td> 
   <td> lang<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID von JavaScript, das beim Starten des Prozesses ausgeführt wird.<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxBroadLog<br /> </td> 
   <td> Maximale Anzahl der zu aktualisierenden Protokolle: definiert die maximale Anzahl von Protokollmeldungen, die im Speicher aufbewahrt werden sollen, bevor die Datenbank aktualisiert wird.<br /> </td> 
   <td> lang<br /> </td> 
   <td> 20<br /> </td> 
  </tr> 
  <tr> 
   <td> maxMsgPerSession<br /> </td> 
   <td> Maximale Anzahl der Nachrichten, die während der POP3-Sitzung gelesen werden.<br /> </td> 
   <td> lang<br /> </td> 
   <td> 200<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Speicherverbrauchswarnung: Warnhinweis über die von einem bestimmten Prozess belegte RAM (in MB).<br /> </td> 
   <td> lang<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Speicherverbrauchswarnung: Warnhinweis über die von einem bestimmten Prozess belegte RAM (in MB).<br /> </td> 
   <td> lang<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSessionTTLSec<br /> </td> 
   <td> Sitzungsdauer: maximale Dauer der Sitzung zur Nachrichtenverarbeitung.<br /> </td> 
   <td> lang<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> popMailPeriodSec<br /> </td> 
   <td> POP3-Abrufzeitraum<br /> </td> 
   <td> lang<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> popQueueSize<br /> </td> 
   <td> Warteschlangengröße für Lesemeldungen<br /> </td> 
   <td> lang<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> popTimeoutSec<br /> </td> 
   <td> Zeitüberschreitung bei der Kommunikation mit dem POP3-Server. <br /> </td> 
   <td> lang<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Die Uhrzeit, zu der der Prozess automatisch neu gestartet wird. Siehe <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatischer Prozessneustart</a>.<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> reloadPeriodSec<br /> </td> 
   <td> Häufigkeit der Neuladung von zu abzurufenden Konten.<br /> </td> 
   <td> lang<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priorität am Anfang. Module mit niedriger Priorität werden zuerst gestartet und zuletzt beendet. Das syslogd-Modul muss daher die Priorität 0 haben.<br /> </td> 
   <td> Short<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

### msgDump {#msgdump}

Konfigurieren Sie im Knoten **inMail > msgDump** die folgenden Parameter. Dies ist die Konfiguration des Speicherplatzes für verarbeitete Nachrichten.

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
   <td> Meldungsdump-Pfad.<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> '/tmp/inMail'<br /> </td> 
  </tr> 
 </tbody> 
</table>

## interactiond {#interactiond}

Hier sind die verschiedenen Parameter des **interaktiven** Knotens. Dies ist die Konfiguration des Write-Daemons für Inbound Interaction-Ereignisse.

Weitere Informationen finden Sie unter [Interaktion - Datenpuffer](../../installation/using/interaction---data-buffer.md).

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
   <td> Zeichenfolge<br /> </td> 
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
   <td> Max. Anzahl der Zeichen, die im gemeinsamen Speicher für Aufrufdaten gespeichert werden.<br /> </td> 
   <td> lang<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID von JavaScript, das beim Starten des Prozesses ausgeführt wird<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Speicherverbrauchswarnung: Warnhinweis über die von einem bestimmten Prozess belegte RAM (in MB).<br /> </td> 
   <td> lang<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Speicherverbrauchswarnung: Warnhinweis über die von einem bestimmten Prozess belegte RAM (in MB).<br /> </td> 
   <td> lang<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSharedEntries<br /> </td> 
   <td> Max. Anzahl der Ereignisse, die im gemeinsamen Speicher gespeichert werden.<br /> </td> 
   <td> lang<br /> </td> 
   <td> 25000<br /> </td> 
  </tr> 
  <tr> 
   <td> nextOffersSize<br /> </td> 
   <td> Maximale Anzahl der förderfähigen Angebote, die direkt nach den Vorschlägen sortiert und für Statistiken zu speichern sind.<br /> </td> 
   <td> lang<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Die Uhrzeit, zu der der Prozess automatisch neu gestartet wird. Siehe <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatischer Prozessneustart</a>.<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priorität am Anfang. Module mit niedriger Priorität werden zuerst gestartet und zuletzt beendet. Das syslogd-Modul muss daher die Priorität 0 haben.<br /> </td> 
   <td> Short<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> statsPeriod<br /> </td> 
   <td> Aggregationsdauer in Sekunden für die Antwortzeitstatistik. 0 bedeutet, dass der statistische Speicher deaktiviert wurde.<br /> </td> 
   <td> lang<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> targetKeySize<br /> </td> 
   <td> Max. Anzahl der Zeichen, die im gemeinsamen Speicher zur Identifizierung von Einzelpersonen gespeichert werden.<br /> </td> 
   <td> lang<br /> </td> 
   <td> 16<br /> </td> 
  </tr> 
 </tbody> 
</table>

## mta {#mta}

Hier sind die verschiedenen Parameter des **mta** -Knotens. Dies ist die Konfiguration der Bereitstellungsagenten.

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
   <td> Zeichenfolge<br /> </td> 
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
   <td> Pfad der gesendeten E-Mails speichern: wenn nicht leer, der Pfad, in dem alle Quelldateien gesendeter E-Mails gespeichert werden. <br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> debugPath<br /> </td> 
   <td> Dump-Verzeichnis: Wenn nicht leer, kopieren Sie MIME-Hüllkurven der gesendeten E-Mail-Nachrichten in diesen Ordner. Dient zum Schießen von Schwierigkeiten. <br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> dnsRequestLogDelayMs<br /> </td> 
   <td> Verzögerung von DNS-Abfrageprotokollen: Zeit in Millisekunden, um die Protokolle anzuzeigen.<br /> </td> 
   <td> lang<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> errorPeriodSec<br /> </td> 
   <td> Häufigkeit der Fehlerstatistiken: Zeit zwischen der Erstellung von Statistiken und der Speicherung in der Datenbank. <br /> </td> 
   <td> lang<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID von JavaScript, das beim Starten des Prozesses ausgeführt wird.<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> logEmailErrors<br /> </td> 
   <td> Erstellen Sie Fehlerstatistiken und speichern Sie sie in der Datenbank.<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> logLevel<br /> </td> 
   <td> Anzeigeebene der Protokollmeldungen. Schweregrad der in die Datenbank geschriebenen Protokolle. Von der MTA generierte Protokollmeldungen werden nicht immer in die Datenbank geschrieben. Mit diesem Parameter können Sie festlegen, auf welcher Ebene eine Nachricht in die Datenbank geschrieben werden soll. Wenn Sie Stufe 2 definieren, werden auch Nachrichten der Stufe 1 und 0 geschrieben, während bei der Definition von Stufe 1 nur Nachrichten der Stufe 1 und 0 geschrieben werden. Mögliche Werte sind: 0 (Fehler), 1 (Warnung), 2 (Info)<br /> </td> 
   <td> lang<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> maxMemoryMb<br /> </td> 
   <td> Maximale Speichergröße (in MB), die ein Datenverarbeitungsprozess verwenden kann. Über dieser Grenze hinaus wird der Prozess neu gestartet, sodass der verwendete Speicher an das System freigegeben wird.<br /> </td> 
   <td> lang<br /> </td> 
   <td> 1024<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Speicherverbrauchswarnung: Warnhinweis über die von einem bestimmten Prozess belegte RAM (in MB).<br /> </td> 
   <td> lang<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Speicherverbrauchswarnung: Warnhinweis über die von einem bestimmten Prozess belegte RAM (in MB).<br /> </td> 
   <td> lang<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> minConnectionsToLog<br /> </td> 
   <td> Zu berücksichtigender Verbindungsschwellenwert. Fehlerstatistiken werden für einen bestimmten Pfad nicht generiert, wenn die Gesamtanzahl der Verbindungen für den von errorPeriodSec angegebenen Zeitraum strikt unter dem Schwellenwert liegt.<br /> </td> 
   <td> lang<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> minErrorsToLog<br /> </td> 
   <td> Zu berücksichtigender Fehlerschwellenwert: Fehlerstatistiken werden für einen bestimmten Pfad nicht generiert, wenn die Gesamtanzahl der Fehler für den von errorPeriodSec angegebenen Zeitraum strikt unter dem Schwellenwert liegt.<br /> </td> 
   <td> lang<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> minMessagesToLog<br /> </td> 
   <td> Zu berücksichtigender Meldungsschwellenwert. Fehlerstatistiken werden für einen bestimmten Pfad nicht generiert, wenn die Gesamtzahl der Nachrichten, die für den von errorPeriodSec angegebenen Zeitraum gesendet werden, strikt unter dem Schwellenwert liegt.<br /> </td> 
   <td> lang<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
  <tr> 
   <td> notifRelay<br /> </td> 
   <td> Benachrichtigungsrelais: HostName:Anschluss, der zum Weiterleiten von Benachrichtigungen verwendet wird.<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Die Uhrzeit, zu der der Prozess automatisch neu gestartet wird. Siehe <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatischer Prozessneustart</a>.<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> purgeDataLogDelay<br /> </td> 
   <td> Verzögerung vor dem Löschen archivierter E-Mails: Anzahl der Tage vor dem Löschen archivierter E-Mails im in dataLogPath angegebenen Ordner.<br /> </td> 
   <td> lang<br /> </td> 
   <td> 15<br /> </td> 
  </tr> 
  <tr> 
   <td> retryLostMessages<br /> </td> 
   <td> Verlorene Nachrichten wiederholen: Teile der Lieferungen werden erneut versucht, wenn der Kindprozess tot ist.<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priorität am Anfang. Module mit niedriger Priorität werden zuerst gestartet und zuletzt beendet. Das syslogd-Modul muss daher die Priorität 0 haben.<br /> </td> 
   <td> Short<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> statServerAddress<br /> </td> 
   <td> Adresse des Bereitstellungsstatistikservers, angegeben als &lt;dns oder ip&gt; [: 
     &lt;Anschluss&gt; ]. Siehe <a href="../../installation/using/email-deliverability.md#coordinates-of-the-statistics-server" target="_blank">Koordinaten des Statistikservers</a>. 
      <br /> 
     </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> Wenn nicht definiert, ist der Standardanschluss 7777.<br /> </td> 
  </tr> 
  <tr> 
   <td> statServerTLSSsupport<br /> </td> 
   <td> TLS nach Domäne aktivieren: aktiviert die durch MX konfigurierbaren TLS (erfordert einen aktuellen Statistikserver).<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> true <br /> </td> 
  </tr> 
  <tr> 
   <td> statServerVersion<br /> </td> 
   <td> Verwendete Protokollversion: Kommunikationsprotokoll-Version (1 für einen Server der Version 5.11 und 6.0.2, 2 für einen Server der Version 6.1).<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> Wenn nicht definiert, wird die neueste Version verwendet. <br /> </td> 
  </tr> 
  <tr> 
   <td> useMomentum<br /> </td> 
   <td> Bei der Einstellung "true"verwendet Ihre Instanz die <a href="https://helpx.adobe.com/campaign/kb/campaign-enhanced-mta.html" target="_blank">erweiterte MTA</a>.<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> <br /> </td>b 
  </tr>
  <tr> 
   <td> verifyMode<br /> </td> 
   <td> Überprüfungsmodus: aktiviert den Überprüfungsmodus (keine physische Übertragung von Nachrichten); für Simulation und Tests verwendet werden).<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> workingPath<br /> </td> 
   <td> Arbeitsverzeichnis: Speicherort temporärer Dateien, die vom MTA zur Kommunikation mit seinen untergeordneten Prozessen verwendet werden.<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> '$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/mta/' <br /> </td> 
  </tr> 
  <tr> 
   <td> xMailer<br /> </td> 
   <td> X-Mailer-Feld: Wert des Felds 'X-Mailer' in der SMTP-Mail-Kopfzeile.<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> 'nlserver, Build $(PRODUCT_VERSION)'<br /> </td> 
  </tr>  
 </tbody> 
</table>

### cache {#cache}

Konfigurieren Sie im **Cache** -Knoten die folgenden Parameter. Dies ist die lokale Dateicache-Konfiguration.

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
   <td> Recycling nach: Zeitraum in Sekunden, nach dem die Datei automatisch aus dem Cache gelöscht wird, um den Speicher wiederherzustellen.<br /> </td> 
   <td> lang<br /> </td> 
   <td> 244800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSizeOnDiskMb<br /> </td> 
   <td> Maximale Cachegröße (Mb).<br /> </td> 
   <td> lang<br /> </td> 
   <td> 1024<br /> </td> 
  </tr> 
  <tr> 
   <td> purgePeriodSec<br /> </td> 
   <td> Purge Frequenz: Zeitraum in Sekunden zwischen der Ausführung des Cache-Bereinigungsmechanismus.<br /> </td> 
   <td> lang<br /> </td> 
   <td> 3600<br /> </td> 
  </tr> 
 </tbody> 
</table>

### relay {#relay}

Konfigurieren Sie im Knoten **mta > relais** die folgenden Parameter. Dies ist die Konfiguration des E-Mail-Servers für die Nachrichtenübermittlung.

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
   <td> address<br /> </td> 
   <td> Kommagetrennte Liste der DNS-Namen oder IP-Adressen der zu verwendenden SMTP-Relais. <br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> port<br /> </td> 
   <td> IP-Anschluss des SMTP-Servers.<br /> </td> 
   <td> lang<br /> </td> 
   <td> 25<br /> </td> 
  </tr> 
 </tbody> 
</table>

### master {#master}

Konfigurieren Sie im Knoten **mta > master** die folgenden Parameter. Dies ist die Konfiguration des Hauptservers.

For additional information, refer to this [section](../../installation/using/configuring-campaign-server.md#mta-child-processes).

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
   <td> Häufigkeit der Datenbankabfrage für die auszuführenden Aufträge. Dieser Wert gibt die Abrufhäufigkeit der Datenbank (in Sekunden) an. Um die Liste der Aufträge zu erhalten, die auf die Auslieferung warten, fragt die MTA die Datenbank regelmäßig ab. Wenn kein Auftrag abgewartet wird, wird der Abrufezeitraum durch diesen Wert definiert. Andernfalls, wenn ein Auftrag auf einen untergeordneten Server übertragen wurde, wird diese Abruffrist automatisch auf eine Sekunde reduziert, sodass ein neuer Auftrag so bald wie möglich erneut verarbeitet werden kann, d. h. sobald ein untergeordneter Server wieder verfügbar ist. Das bedeutet nicht, dass die Datenbankabfrage jede Sekunde durchgeführt wird, bis ein untergeordneter Server wieder verfügbar ist. Ein Datenbankzugriff erfolgt nur, wenn mindestens ein untergeordneter Server verfügbar ist.<br /> </td> 
   <td> lang<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
  <tr> 
   <td> dataBaseRetryDelaySec<br /> </td> 
   <td> Wartezeit nach einem Datenbankverbindungsfehler. Ein Datenbankverbindungsfehler wird normalerweise vom Datenbankserver selbst verursacht. Der Server kann beispielsweise auch zu Wartungszwecken angehalten werden. Der DataBaseRetryDelay-Parameter definiert die Dauer zwischen zwei Verbindungsversuchen im Fall eines Datenbankverbindungsfehlers.<br /> </td> 
   <td> lang<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> domainKeysReloadPeriodSec<br /> </td> 
   <td> Gültigkeitsdauer für den Cache privater Schlüssel (DomainKeys). Private Schlüssel zum Signieren von E-Mails nach der DomainKeys-Empfehlung (http://antispam.yahoo.com/domainkeys) werden als Optionen in der Datenbank gespeichert. Der Parameter domainKeysReloadPeriodSec legt fest, wie viele Sekunden die MTA diese Schlüssel im Cache aufbewahren kann. Nach dieser Verzögerung müssen alle Schlüssel aus der Datenbank neu geladen werden.<br /> </td> 
   <td> lang<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSpareServers<br /> </td> 
   <td> Maximale Anzahl der untergeordneten Server. Stellt die maximale Anzahl der ausgeführten Server dar. Es wird empfohlen, diese Zahl auf ein optimales Maß zu beschränken, das mit den Serverspeicherressourcen kompatibel ist. Dies kann während einer Lieferung überprüft werden. Der verwendete Speicher sollte nicht mehr als ein Drittel des verfügbaren physischen Speichers betragen, da andernfalls der Austausch verwendet wird. Siehe <a href="../../installation/using/configuring-campaign-server.md#mta-child-processes" target="_blank">Untergeordnete MTA-Prozesse</a>.<br /> </td> 
   <td> lang<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> minSpareServers<br /> </td> 
   <td> Mindestanzahl der untergeordneten Server. Die MTA versucht, mindestens diese Anzahl von Servern auszuführen. Wenn weniger vorhanden ist, werden neue Server jede Sekunde neu gestartet, bis dieser Wert erreicht ist.<br /> </td> 
   <td> lang<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> startSpareServers<br /> </td> 
   <td> Anzahl der untergeordneten Server beim Start. Die Anzahl der untergeordneten Server wird dynamisch überwacht. beim Start des MTA so viele untergeordnete Server wie durch diesen Wert angegeben erstellt werden. Normalerweise können untergeordnete Server nicht schneller als ein Server pro Sekunde gestartet werden, um Hostressourcen zu sparen. Beim Start der MTA wird diese Einschränkung jedoch außer Kraft gesetzt, damit die untergeordneten Server so bald wie möglich verfügbar sind.<br /> </td> 
   <td> lang<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Kind {#child}

Konfigurieren Sie im Knoten **mta > child** die folgenden Parameter. Dies ist die Konfiguration von untergeordneten Servern.

Weitere Informationen finden Sie unter Optimierung des [E-Mail-Versands](../../installation/using/email-deliverability.md#email-sending-optimization).

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
   <td> Zeichenfolge<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> idleChildTimeoutSec<br /> </td> 
   <td> Zeitüberschreitung, bis leere untergeordnete Server beendet wurden. Wenn ein untergeordneter Server eine Leerlaufzeit hat, die größer als dieser Parameter ist, wird er automatisch abgetötet, um Hostressourcen freizugeben.<br /> </td> 
   <td> lang<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> maxAgeSec<br /> </td> 
   <td> Maximale Dauer der Nachrichtenspeicherung. Wenn eine vorbereitete Nachricht aufgrund von Einschränkungen nicht gesendet werden konnte oder nicht mit der Ziel-MTA verbunden werden konnte, wird die Nachricht abgebrochen und beim nächsten Versuch verarbeitet.<br /> </td> 
   <td> lang<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxGCMConnectPerChild<br /> </td> 
   <td> Maximale Anzahl paralleler Http-Anfragen an FCM von jedem Kindserver initiiert.<br /> </td> 
   <td> lang<br /> </td> 
   <td> 8<br /> </td> 
  </tr> 
  <tr> 
   <td> maxMsgPerChild<br /> </td> 
   <td> Maximale Anzahl der Nachrichten pro untergeordneter Server. Jedes untergeordnete MTA-Objekt verarbeitet diese Anzahl von Nachrichten und stirbt. Es ist wichtig, eine Zahl anzugeben, mit der Speicher- oder Ressourcenlecks im MTA harmlos sind (normalerweise einige Tausend). Auch wenn im MTA-Code keine Speicherlecks bekannt sind, sind die eingebetteten JavaScript- und XSL-Engines nicht vollständig zuverlässig.<br /> </td> 
   <td> lang<br /> </td> 
   <td> 5000000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxWaitingMessages<br /> </td> 
   <td> Ausstehende Nachrichten: maximale Anzahl von Nachrichten, die im Speicher ausgeliefert werden. <br /> </td> 
   <td> lang<br /> </td> 
   <td> 2000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxWorkingSetMb<br /> </td> 
   <td> Maximale Speichergröße (in MB), die ein untergeordneter Prozess verwenden kann. Über dieser Grenze hinaus wird der Prozess gestoppt, sodass der verwendete Speicher an das System freigegeben wird. <br /> </td> 
   <td> lang<br /> </td> 
   <td> 128<br /> </td> 
  </tr> 
  <tr> 
   <td> soapConnectorTimeoutSec<br /> </td> 
   <td> Timeout (in Sekunden), nach dem eine SOAP-Verbindung für einen Auslieferungsstecker abgebrochen wird.<br /> </td> 
   <td> lang<br /> </td> 
   <td> 600<br /> </td> 
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
   <td> lang<br /> </td> 
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
   <td> Aktiviert die Bereitstellung von E-Mails im abgesicherten Modus (STARTTLS/SMTPS), wenn diese vom Remote-Server unterstützt werden.<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> idleSessionTimeoutSec<br /> </td> 
   <td> Zeitüberschreitung während der Leersitzung. Dieser Parameter wird nur verwendet, wenn die Sitzung zur Übertragung mehrerer Nachrichten an eine bestimmte Domäne wiederverwendet wird. Wenn die MTA die Nachrichtenübertragung abgeschlossen hat, wird die verwendete SMTP-Sitzung nicht systematisch geschlossen. Wenn eine Nachricht für dieselbe Domäne gesendet werden kann, wird dieselbe SMTP-Sitzung wiederverwendet, weshalb die Sitzung nicht automatisch geschlossen wird. Mit dem Parameter IdleSessionTimeout können Sie festlegen, wie lange eine SMTP-Sitzung aktiv bleiben kann, um auf eine weitere Nachricht zu warten. Nach Ablauf der Dauer wird die Sitzung automatisch geschlossen.<br /> </td> 
   <td> lang<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> initialDelaySec<br /> </td> 
   <td> Erste Verzögerung vor dem erneuten Versuch der Verbindung. Diese Verzögerung wird bei jedem Verbindungsfehler verdoppelt.<br /> </td> 
   <td> lang<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSessionsPerChild<br /> </td> 
   <td> Maximale Anzahl der SMTP-Sitzungen nach untergeordnetem Server. Um eine Nachricht zu senden, initialisiert das MTA eine SMTP-Verbindung mit dem Empfänger-MTA. Die maximale Anzahl gleichzeitiger und aktiver SMTP-Sitzungen für einen bestimmten untergeordneten Server ist durch diesen Wert begrenzt. Wenn Sie diesen Wert mit maxSpareServers multiplizieren, erhalten Sie die maximale Anzahl von Meldungen, die gleichzeitig von einem bestimmten untergeordneten Server verarbeitet werden können.<br /> </td> 
   <td> lang<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
 </tbody> 
</table>

Konfigurieren Sie im Knoten **mta > child > smtp > IPAffinity** die folgenden Parameter. Dies ist die Konfiguration der Verwaltung von Affinitäten mit IP-Adressen für optimierten ausgehenden SMTP-Traffic.

Weitere Informationen finden Sie in der [Liste der IP-Adressen, die für die Verwendung](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use) und [Verwaltung des ausgehenden SMTP-Traffics mit Affinitäten](../../installation/using/configuring-campaign-server.md#managing-outbound-smtp-traffic-with-affinities)verwendet werden sollen.

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
   <td> Domänenname: lokaler Domänenname, der mit der IP-Adresse verknüpft ist. Wird verwendet, wenn ein SMTP-HELO-Befehl ausgegeben wird.<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
  </tr> 
  <tr> 
   <td> name<br /> </td> 
   <td> Logischer Name: Namen, die mit der Affinität der Benutzer verknüpft sind. Namen werden durch Semikolons getrennt.<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
  </tr> 
 </tbody> 
</table>

Konfigurieren Sie im Knoten **mta > child > smtp > IP** die folgenden Parameter.

Weitere Informationen finden Sie unter [Liste der zu verwendenden](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use)IP-Adressen.

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
   <td> Zugehörige physische Adresse. z. B.: '192.168.0.1'<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
  </tr> 
  <tr> 
   <td> publicId<br /> </td> 
   <td> Zugehörige öffentliche Adresse-ID. Wird als Schlüssel für den Statistikserver verwendet. Muss numerisch sein. See this <a href="../../installation/using/email-deliverability.md#managing-ip-addresses">section</a>.<br /> </td> 
   <td> lang<br /> </td> 
  </tr> 
  <tr> 
   <td> Gewichtung.<br /> </td> 
   <td> Gibt die Häufigkeit der Verwendung für diese IP im Vergleich zu anderen IPs an (größere Gewichtungen führen zu höheren Frequenzen).<br /> </td> 
   <td> lang<br /> </td> 
  </tr> 
  <tr> 
   <td> includeDomains<br /> </td> 
   <td> Kommagetrennte Liste der einzuschließenden Domänenmasken.<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
  </tr> 
  <tr> 
   <td> excludeDomains<br /> </td> 
   <td> Kommagetrennte Liste der auszuschließenden Domänenmasken.<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
  </tr> 
  <tr> 
   <td> heloHost<br /> </td> 
   <td> Computername, der mit der IP-Adresse verknüpft ist. Wird verwendet, wenn ein SMTP-HELO-Befehl ausgegeben wird.<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
  </tr> 
 </tbody> 
</table>

## nmac {#nmac}

Hier sind die verschiedenen Parameter des **nmac** Knotens. Dies ist die Konfiguration von für Push-Benachrichtigungs-Auslieferungen.

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

### relay {#relay-1}

Hier sind die verschiedenen Parameter des Knotens **nmac > relais** . Dadurch wird die Verwendung eines Relais für die Nachrichtenübermittlung konfiguriert (iOS HTTP2 Connector).

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
   <td> Zeichenfolge<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> port<br /> </td> 
   <td> Relay Port<br /> </td> 
   <td> lang<br /> </td> 
   <td> 443<br /> </td> 
  </tr> 
  <tr> 
   <td> trustCertsChain<br /> </td> 
   <td> Zertifikatskette (PEM-Datei). Nützlich bei der Verwendung eines Trackservers.<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

## pipeliniert {#pipelined}

Hier sind die verschiedenen Parameter des **pipelinierten** Knotens. Dies ist die Konfiguration des Ereignisverarbeitungsmoduls für Pipeline-Dienste.

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
   <td> Name der Anwendung, die in der Developer-Verbindung beim Speichern des öffentlichen Schlüssels generiert wurde. <br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> args<br /> </td> 
   <td> Startparameter<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authGatewayEndpoint<br /> </td> 
   <td> URL zum Abrufen eines Gateway-Tokens.<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> https://api.omniture.com' <br /> </td> 
  </tr> 
  <tr> 
   <td> authPrivateKey<br /> </td> 
   <td> Privater Schlüssel zum Abrufen von Token (verschlüsselt in AES mit der XtkKey-Option).<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Automatischer Start <br /> </td> 
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
   <td> URL, um die URL der Pipeline-Dienste zu ermitteln.<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> https://producer-pipeline-pnw.adobe.net'<br /> </td> 
  </tr> 
  <tr> 
   <td> dumpStatePeriodSec<br /> </td> 
   <td> Statusspeicherzeitraum: Häufigkeit, mit der die internen Informationen des Prozesses in einer Datei gespeichert werden. Inaktiv, wenn 0. <br /> </td> 
   <td> lang<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> forcedPipelineEndpoint<br /> </td> 
   <td> Listening-URL: erzwingen Sie die Listening-URL der Pipeline-Dienste. <br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID von JavaScript, das beim Starten des Prozesses ausgeführt wird.<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Speicherverbrauchswarnung: Warnhinweis über die von einem bestimmten Prozess belegte RAM (in MB).<br /> </td> 
   <td> lang<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Speicherverbrauchswarnung: Warnhinweis über die von einem bestimmten Prozess belegte RAM (in MB).<br /> </td> 
   <td> lang<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> monitorServerPort<br /> </td> 
   <td> Statusserveranschluss: HTTP-Serveranschluss, mit dem Sie den Status des Prozesses abfragen können. Inaktiv, wenn 0.<br /> </td> 
   <td> lang<br /> </td> 
   <td> 7781<br /> </td> 
  </tr> 
  <tr> 
   <td> cursorFlushMessageCount<br /> </td> 
   <td> Der Zeiger wird bei jeder Verarbeitung dieser Anzahl von Nachrichten in der Datenbank gespeichert.<br /> </td> 
   <td> <br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
  <tr> 
   <td> cursorFlushPeriodSec<br /> </td> 
   <td> Verzögerung vor der Speicherung des Zeigers: Der Zeiger wird mindestens einmal während dieses Zeitraums in der Datenbank gespeichert (bei geringer Aktivität nützlich).<br /> </td> 
   <td> lang<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Die Uhrzeit, zu der der Prozess automatisch neu gestartet wird. Siehe <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatischer Prozessneustart</a>.<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> processingJSThreads<br /> </td> 
   <td> Anzahl der Threads zur Ereignisverarbeitung mit einem personalisierten JavaScript-Connector.<br /> </td> 
   <td> lang<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> processingThreads<br /> </td> 
   <td> Anzahl der Threads zur Ereignisverarbeitung.<br /> </td> 
   <td> lang<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> retryPeriodSec<br /> </td> 
   <td> Verzögerung zwischen der Verarbeitung bei Fehler.<br /> </td> 
   <td> lang<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
  <tr> 
   <td> retryValiditySec<br /> </td> 
   <td> Nach diesem Zeitraum wird beendet: das Ereignis abbrechen, wenn die Verarbeitung nach diesem Zeitraum immer noch fehlschlägt.<br /> </td> 
   <td> lang<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priorität am Anfang. Module mit niedriger Priorität werden zuerst gestartet und zuletzt beendet. Das syslogd-Modul muss daher die Priorität 0 haben.<br /> </td> 
   <td> Short<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Reparatur {#repair}

Hier sind die verschiedenen Parameter des **Reparaturknotens** . Dies ist die Konfiguration des Datenbankreparaturmoduls.

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
   <td> restoreActionDelayMin<br /> </td> 
   <td> Reparaturmodul für Bereitstellungsaktionen: Verzögerung (in Minuten), nach der Auslieferungsaktionen vom Reparaturmodul verarbeitet werden können. <br /> </td> 
   <td> lang<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
 </tbody> 
</table>

## securityZone {#securityzone}

Hier sind die verschiedenen Parameter des **Knotens securityZone** .

Weitere Informationen finden Sie unter [Definieren von Sicherheitszonen](../../installation/using/configuring-campaign-server.md#defining-security-zones).

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
   <td> Autorisieren des Debug-Modus für Webanwendungen.<br /> </td> 
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
   <td> Autorisieren Sie die Verwendung von HTTP für die Operatoranmeldung.<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> allowSQLInject<br /> </td> 
   <td> Autorisieren Sie die Verwendung von SQLDATA in Ausdrücken.<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> allowUserPassword<br /> </td> 
   <td> Benutzer-/Kennwort-Sitzungstoken autorisieren.<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> label<br /> </td> 
   <td> Titel<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> NewLabel()<br /> </td> 
  </tr> 
  <tr> 
   <td> name<br /> </td> 
   <td> Interner Name<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> NewName() <br /> </td> 
  </tr> 
  <tr> 
   <td> sessionTokenOnly<br /> </td> 
   <td> Verwenden Sie nicht das Sicherheitstoken.<br /> </td> 
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

Die Standardkonfiguration lautet:

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

Hier sind die verschiedenen Parameter des Knotens **securityZone > subNetwork** .

Weitere Informationen finden Sie unter [Definieren von Sicherheitszonen](../../installation/using/configuring-campaign-server.md#defining-security-zones).

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
   <td> Zeichenfolge<br /> </td> 
   <td> NewLabel()<br /> </td> 
  </tr> 
  <tr> 
   <td> Maske<br /> </td> 
   <td> Maske oder Adresse<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> name<br /> </td> 
   <td> Interner Name<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> NewName() <br /> </td> 
  </tr> 
  <tr> 
   <td> proxy<br /> </td> 
   <td> Maske oder Adresse des (umgekehrten) Proxys, der von diesem Unternetzwerk verwendet wird, um auf die Instanz zuzugreifen. In diesem Fall wird der Header "X-Forwarded-For"anstelle dieses Proxys getestet.<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> 127.0.0.1 <br /> </td> 
  </tr> 
 </tbody> 
</table>

## sms {#sms}

Hier sind die verschiedenen Parameter des **sms** Knotens. Dies ist die Konfiguration des eingehenden SMS-Verwaltungsmoduls.

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
   <td> Zeichenfolge<br /> </td> 
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
   <td> Maximale Anzahl der Tage, in denen Dateien vom SMPP-Connector verwaltet werden.<br /> </td> 
   <td> lang<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> dataSizeMo<br /> </td> 
   <td> Maximale Größe der SMPP-Arbeitsdateien in MB.<br /> </td> 
   <td> lang<br /> </td> 
   <td> 512<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID von JavaScript, das beim Starten des Prozesses ausgeführt wird.<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> keepAlivePeriod<br /> </td> 
   <td> Wiederholung des Rahmens für die Sitzungskontinuität: max. Zeitraum in Sekunden zwischen zwei Frames, um anzuzeigen, dass die empfangende Sitzung weiterhin aktiviert ist.<br /> </td> 
   <td> lang<br /> </td> 
   <td> 25<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Speicherverbrauchswarnung: Warnhinweis über die von einem bestimmten Prozess belegte RAM (in MB).<br /> </td> 
   <td> lang<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Speicherverbrauchswarnung: Warnhinweis über die von einem bestimmten Prozess belegte RAM (in MB).<br /> </td> 
   <td> lang<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> pollPeriod<br /> </td> 
   <td> Suchfrequenz: SMS-Kontoabfragezeitraum.<br /> </td> 
   <td> lang<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Die Uhrzeit, zu der der Prozess automatisch neu gestartet wird. Siehe <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatischer Prozessneustart</a>.<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> reloadPeriod<br /> </td> 
   <td> Häufigkeit der Kontoneuladung: Datenbank-Neuladungshäufigkeit der abzurufenden Konten.<br /> </td> 
   <td> lang<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priorität am Anfang. Module mit niedriger Priorität werden zuerst gestartet und zuletzt beendet. Das syslogd-Modul muss daher die Priorität 0 haben.<br /> </td> 
   <td> Short<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> srReadDelay<br /> </td> 
   <td> Anzahl der Sekunden für die SR-Verarbeitung: nur SRs mit einem Wiederherstellungsdatum vor der aktuellen Zeit abzüglich der Dauer in Sekunden, die von srReadDelay angegeben wird. <br /> </td> 
   <td> lang<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> timeout<br /> </td> 
   <td> Zeitüberschreitung bei der Kommunikation mit SMS Gateway.<br /> </td> 
   <td> lang<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
 </tbody> 
</table>

### netsize {#netsize}

Hier sind die verschiedenen Parameter des Knotens **sms > netsize** .

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
   <td> lang<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
 </tbody> 
</table>

## stat {#stat}

Hier sind die verschiedenen Parameter des **stat** Knotens. Dies ist die Konfiguration des MTA-Statistikmoduls.

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
   <td> Zeichenfolge<br /> </td> 
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
   <td> ID von JavaScript, das beim Starten des Prozesses ausgeführt wird.<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Speicherverbrauchswarnung: Warnhinweis über die von einem bestimmten Prozess belegte RAM (in MB).<br /> </td> 
   <td> lang<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Speicherverbrauchswarnung: Warnhinweis über die von einem bestimmten Prozess belegte RAM (in MB).<br /> </td> 
   <td> lang<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> port<br /> </td> 
   <td> Server-Listening-Anschluss. See this <a href="../../installation/using/email-deliverability.md#definition-of-the-server-port">section</a>.<br /> </td> 
   <td> Short<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Die Uhrzeit, zu der der Prozess automatisch neu gestartet wird. Siehe <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatischer Prozessneustart</a>.<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priorität am Anfang. Module mit niedriger Priorität werden zuerst gestartet und zuletzt beendet. Das syslogd-Modul muss daher die Priorität 0 haben.<br /> </td> 
   <td> Short<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## syslogd {#syslogd}

Hier sind die verschiedenen Parameter des **syslogd** Knotens. Dies ist die Konfiguration des Protokollverwaltungsmoduls.

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
   <td> Zeichenfolge<br /> </td> 
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
   <td> ID von JavaScript, das beim Starten des Prozesses ausgeführt wird.<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxFileSizeMb<br /> </td> 
   <td> Maximale Größe in MB für eine Protokolldatei. <br /> </td> 
   <td> lang<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> maxNumberOfLoginsFiles<br /> </td> 
   <td> Maximale Anzahl der beizubehaltenden logins.log-Dateien. <br /> </td> 
   <td> lang<br /> </td> 
   <td> 365<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Speicherverbrauchswarnung: Warnhinweis über die von einem bestimmten Prozess belegte RAM (in MB).<br /> </td> 
   <td> lang<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Speicherverbrauchswarnung: Warnhinweis über die von einem bestimmten Prozess belegte RAM (in MB).<br /> </td> 
   <td> lang<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Die Uhrzeit, zu der der Prozess automatisch neu gestartet wird. Siehe <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatischer Prozessneustart</a>.<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priorität am Anfang. Module mit niedriger Priorität werden zuerst gestartet und zuletzt beendet. Das syslogd-Modul muss daher die Priorität 0 haben.<br /> </td> 
   <td> Short<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## tracking {#tracking}

Hier sind die verschiedenen Parameter des **Tracking** -Knotens. Dies ist die Konfiguration des Tracking-Servers.

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
   <td> Zeichenfolge<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Automatischer Start<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> ConsolidationPeriodSec<br /> </td> 
   <td> Konsolidierungszeitraum<br /> </td> 
   <td> lang<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> dedupOpenPeriodMin<br /> </td> 
   <td> Duplizieren von Öffnungen: Entfernen Sie doppelte offene Verfolgungsprotokolle, um die Auswirkungen von E-Mail-Vorschauen in E-Mail-Lesern wie Outlook zu begrenzen.<br /> </td> 
   <td> lang<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> errorIgnorePercent<br /> </td> 
   <td> Bis zu X % der Fehler ignorieren: Aktualisierung von Tracking-Indikatoren nicht, solange das Verhältnis der nicht bereits berücksichtigten Zeitschriften diesen Wert nicht erreicht. <br /> </td> 
   <td> Byte<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> errorIgnorePeriod<br /> </td> 
   <td> Aktualisieren Sie die Fehlerindikatoren: maximale Dauer, bevor Fehlerindikatoren neu berechnet werden.<br /> </td> 
   <td> lang<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
  <tr> 
   <td> indicatorsDuration<br /> </td> 
   <td> Indikatoren berechnen während: Dauer nach dem Gültigkeitsdatum einer Lieferung, nach der keine konsolidierten Indikatoren mehr berechnet werden.<br /> </td> 
   <td> lang<br /> </td> 
   <td> 2592000<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID von JavaScript, das beim Starten des Prozesses ausgeführt wird <br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> logCountPerRequest<br /> </td> 
   <td> Anzahl der Protokolle, die durch Aufruf des Remote-Tracking-Servers angefordert werden.<br /> </td> 
   <td> lang<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Speicherverbrauchswarnung: Warnhinweis über die von einem bestimmten Prozess belegte RAM (in MB).<br /> </td> 
   <td> lang<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Speicherverbrauchswarnung: Warnhinweis über die von einem bestimmten Prozess belegte RAM (in MB).<br /> </td> 
   <td> lang<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Die Uhrzeit, zu der der Prozess automatisch neu gestartet wird. Siehe <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatischer Prozessneustart</a>.<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priorität am Anfang. Module mit niedriger Priorität werden zuerst gestartet und zuletzt beendet. Das syslogd-Modul muss daher die Priorität 0 haben.<br /> </td> 
   <td> Short<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> trackingIgnorePercent<br /> </td> 
   <td> Bis zu X % der Verfolgung ignorieren: Aktualisierung von Tracking-Indikatoren nicht, solange das Verhältnis der nicht bereits berücksichtigten Zeitschriften diesen Wert nicht erreicht.<br /> </td> 
   <td> Byte<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> trackingIgnorePeriod<br /> </td> 
   <td> Aktualisieren von Verfolgungsindikatoren: maximale Dauer vor der Neuberechnung der Verfolgungsanzeiger.<br /> </td> 
   <td> lang<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
  <tr> 
   <td> userAgentCacheSize<br /> </td> 
   <td> Größe des Browser-ID-Cache.<br /> </td> 
   <td> lang<br /> </td> 
   <td> 500<br /> </td> 
  </tr> 
 </tbody> 
</table>

## trackinglogd {#trackinglogd}

Hier sind die verschiedenen Parameter des **Knoten trackinglogd** . Dies ist die Konfiguration des Verfolgungsprotokolls Schreibdaemon.

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
   <td> Zeichenfolge<br /> </td> 
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
   <td> ID von JavaScript, das beim Starten des Prozesses ausgeführt wird <br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxCreateFileRetry<br /> </td> 
   <td> Max. Schreibwiederholen: maximale Anzahl von Dateien, die bei einem Schreibfehler in Protokolldateien erstellt werden können.<br /> </td> 
   <td> lang<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> maxLogsSizeOnDiskMb<br /> </td> 
   <td> Maximale Protokollgröße: Maximaler Speicherplatz, der von Protokollen auf dem Datenträger (in MB) verwendet wird. Darf nicht kleiner als 100 MB sein. <br /> </td> 
   <td> lang<br /> </td> 
   <td> 500<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Speicherverbrauchswarnung: Warnhinweis über die von einem bestimmten Prozess belegte RAM (in MB).<br /> </td> 
   <td> lang<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Speicherverbrauchswarnung: Warnhinweis über die von einem bestimmten Prozess belegte RAM (in MB).<br /> </td> 
   <td> lang<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSharedLogs<br /> </td> 
   <td> Maximale Protokollanzahl: maximale Anzahl von Protokollen, die im gemeinsamen Speicher gespeichert sind. Darf nicht weniger als 10000 sein. <br /> </td> 
   <td> lang<br /> </td> 
   <td> 25000<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Die Uhrzeit, zu der der Prozess automatisch neu gestartet wird. Siehe <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatischer Prozessneustart</a>.<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> purgeLogsPeriod<br /> </td> 
   <td> Anzahl der Protokolle vor der Bereinigung: Anzahl der Protokolle, die vor der Bereinigung der Protokolldateien eingefügt wurden. Darf nicht unter 50000 liegen.<br /> </td> 
   <td> lang<br /> </td> 
   <td> 50000<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priorität am Anfang. Module mit niedriger Priorität werden zuerst gestartet und zuletzt beendet. Das syslogd-Modul muss daher die Priorität 0 haben.<br /> </td> 
   <td> Short<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> webTrackingParamSize<br /> </td> 
   <td> Maximale Anzahl von Zeichen, die im gemeinsamen Speicher gespeichert werden, um zusätzliche Webverfolgungsparameter zu erhalten.<br /> </td> 
   <td> lang<br /> </td> 
   <td> 64<br /> </td> 
  </tr> 
 </tbody> 
</table>

## web {#web}

Hier sind die verschiedenen Parameter des **Web** -Knotens. Dies ist die Konfiguration des Webmoduls.

For additional information, refer to this [section](../../installation/using/configuring-campaign-server.md#default-port-for-tomcat).

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
   <td> Optionen der als String übergebenen JVM.<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> MaxThreads<br /> </td> 
   <td> Maximum number of threads.<br /> </td> 
   <td> lang<br /> </td> 
   <td> 75<br /> </td> 
  </tr> 
  <tr> 
   <td> MinSpareThreads<br /> </td> 
   <td> Mindestanzahl von Threads.<br /> </td> 
   <td> lang<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> args<br /> </td> 
   <td> Startparameter<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
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
   <td> Überwachungsanschluss für Tomcat: Siehe <a href="../../installation/using/configuring-campaign-server.md#configuring-tomcat" target="_blank">Konfigurieren von Tomcat</a>.<br /> </td> 
   <td> Short<br /> </td> 
   <td> 8005<br /> </td> 
  </tr> 
  <tr> 
   <td> httpPort<br /> </td> 
   <td> Tomcat HTTP-Listening-Anschluss: Siehe <a href="../../installation/using/configuring-campaign-server.md#configuring-tomcat" target="_blank">Konfigurieren von Tomcat</a>.<br /> </td> 
   <td> Short<br /> </td> 
   <td> 8080<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID von JavaScript, das beim Starten des Prozesses ausgeführt wird.<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxDeliveryQueueSize<br /> </td> 
   <td> Größe der Warteschlange für SubmitDelivery-Aufrufe: Maximale Anzahl der SOAP-Aufrufe von SubmitDelivery, die in die Warteschlange gestellt werden können.<br /> </td> 
   <td> lang<br /> </td> 
   <td> 50<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Speicherverbrauchswarnung: Warnhinweis über die von einem bestimmten Prozess belegte RAM (in MB).<br /> </td> 
   <td> lang<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Speicherverbrauchswarnung: Warnung bezüglich der von einem bestimmten Prozess verbrauchten RAM (in MB)<br /> </td> 
   <td> lang<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> notifRelay<br /> </td> 
   <td> Benachrichtigungsrelais: HostName:Port, der das Weiterleiten von Benachrichtigungen ermöglicht.<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Die Uhrzeit, zu der der Prozess automatisch neu gestartet wird. Siehe <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatischer Prozessneustart</a>.<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priorität am Anfang. Module mit niedriger Priorität werden zuerst gestartet und zuletzt beendet. Das syslogd-Modul muss daher die Priorität 0 haben.<br /> </td> 
   <td> Short<br /> </td> 
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

Hier sind die verschiedenen Parameter des Knotens **web > jsp** . Dies ist die Konfiguration der von den JSPs verwendeten Parameter.

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
   <td> Ordner herunterladen: Downloadpfad von Installationsprogrammen für die Client-Konsolen.<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> '$(XTK_INSTALL_DIR)/datakit/nl/eng/jsp'<br /> </td> 
  </tr> 
  <tr> 
   <td> foFileName<br /> </td> 
   <td> Pfad der .fo-Datei.<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> soapRouter<br /> </td> 
   <td> URL des SOAP-Routers (http://myserver/xxx, http://jni oder mailto:xxx).<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> http://jni'<br /> </td> 
  </tr> 
 </tbody> 
</table>

Der Knoten **web > jsp > classpath** enthält die Liste aller Klassenpfade, die beim Starten von JVM verwendet werden. Die Standardkonfiguration lautet:

```
'$(XTK_INSTALL_DIR)/tomcat-7/bin/bootstrap.jar
          $(XTK_INSTALL_DIR)/tomcat-7/bin/tomcat-juli.jar
          $(XTK_INSTALL_DIR)/tomcat-7/lib/tomcat-coyote.jar
          $(XTK_INSTALL_DIR)/tomcat-7/lib/tomcat-util.jar
          $(XTK_INSTALL_DIR)/tomcat-7/lib/tomcat-api.jar
          $(XTK_INSTALL_DIR)/tomcat-7/lib/servlet-api.jar
          $(XTK_INSTALL_DIR)/tomcat-7/lib/jsp-api.jar
          $(XTK_INSTALL_DIR)/tomcat-7/lib/el-api.jar
          $(XTK_INSTALL_DIR)/java/lib/log4j-1.2.11.jar
          $(XTK_INSTALL_DIR)/tomcat-7/lib/annotations-api.jar
          $(XTK_INSTALL_DIR)/tomcat-7/lib/catalina.jar
          $(XTK_INSTALL_DIR)/tomcat-7/lib/websocket-api.jar
          $(XTK_INSTALL_DIR)/tomcat-7/lib/tomcat7-websocket.jar
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
   <td> collectsGarbageAfterRequest<br /> </td> 
   <td> Aktiviert den Garbage Collector des JavaScript-Kontexts nach jeder Abfrage.<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> timeToLive<br /> </td> 
   <td> Maximale Anzahl von Seiten, die von einem JavaScript-Kontext bereitgestellt werden. <br /> </td> 
   <td> lang<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
 </tbody> 
</table>

Der Knoten **web > jsp > classpath** enthält die Liste aller Klassenpfade, die beim Starten von JVM verwendet werden.

### relay {#relay-2}

Hier sind die verschiedenen Parameter des **Web > Relais** Knotens. Dies ist die Konfiguration des Relais für HTTP-Anfragen zwischen zwei Zonen.

For additional information, refer to this [section](../../installation/using/deploying-an-instance.md#synchronizing-public-resources).

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
   <td> Starten Sie das HTTP-Relay-Modul innerhalb des Webservers im Debug-Modus.<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> forbiddenCharsInAuthority<br /> </td> 
   <td> Verbotene Zeichen (Domäne): Liste der verbotenen Zeichen im Abschnitt 'Authority' eines URI.<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> '.?#@/:' <br /> </td> 
  </tr> 
  <tr> 
   <td> forbiddenCharsInPath<br /> </td> 
   <td> Verbotene Zeichen (Pfad): Liste der verbotenen Zeichen im Abschnitt 'Pfad' eines URI.<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> '?#/'<br /> </td> 
  </tr> 
  <tr> 
   <td> modDir<br /> </td> 
   <td> Wert der Moduloption "mod_dir": Liste der Dateien, die bei einer Abfrage in einem Ordner verwendet werden sollen.<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> 'index.md' <br /> </td> 
  </tr> 
  <tr> 
   <td> startRelay<br /> </td> 
   <td> Starten Sie das HTTP-Relaismodul.<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> startRelayInModule<br /> </td> 
   <td> Starten Sie das HTTP-Relaismodul innerhalb des Webservers. <br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> timeout<br /> </td> 
   <td> Warten Sie, bevor Sie die verbotene URL löschen.<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> '60'<br /> </td> 
  </tr> 
 </tbody> 
</table>

Fügen Sie eine **Web- > Relay- > URL** -Node für jede URL zum Relais (Einfügereihenfolge definiert Priorität) mit den folgenden Parametern hinzu.

Weitere Informationen finden Sie unter [Dynamische Seitensicherheit, Relais](../../installation/using/configuring-campaign-server.md#dynamic-page-security-and-relays) und [Abschnitt](../../installation/using/deploying-an-instance.md#synchronizing-public-resources).

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
   <td> Zeichenfolge<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> deny<br /> </td> 
   <td> Zugriff auf diese URLs verweigern (HTTP 403-Fehler zurückgeben)<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> hostMask<br /> </td> 
   <td> DNS-Alias für Relais: Kommagetrennte Liste der DNS-Aliasmasken an Relais (z. B.: '*.adobe.com').<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> httpAllowed<br /> </td> 
   <td> HTTP-Zugriff autorisiert, unabhängig von der Sicherheitszone (wie webApps). <br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> relaisHost<br /> </td> 
   <td> Originalhost hinzufügen: verwenden Sie beim Übergeben die HTTP 'Host'-Kopfzeile der ursprünglichen Anforderung.<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> relaisPath<br /> </td> 
   <td> Fügen Sie den anfänglichen URL-Pfad hinzu: Hängen Sie den vollständigen Pfad der URLs an, die an die URL der Zielseite weitergeleitet werden sollen. <br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> status<br /> </td> 
   <td> Synchronisierungsstatus einer öffentlichen Ressource (Aufzählung). Mögliche Werte sind 'normal' (normale Ausführung), 'blacklist' (URL-Blacklist bei Fehler 404) und 'reserve' (Datei-Upload auf Reserveserver, falls vorhanden).<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> normal<br /> </td> 
  </tr> 
  <tr> 
   <td> targetUrl<br /> </td> 
   <td> URL der Zielseite: Siehe <a href="../../installation/using/configuring-campaign-server.md#configuring-tomcat" target="_blank">Konfigurieren von Tomcat</a>.<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> timeout<br /> </td> 
   <td> Maximale Ausführungszeit (in Sekunden) der Anforderung, die wiedergegeben wird.<br /> </td> 
   <td> lang<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> urlPath<br /> </td> 
   <td> Maske der URLs zum Relais (z. B.: '/nl*', '*.jsp').<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

Die Standardkonfiguration lautet:

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

Fügen Sie für jeden HTTP-Header einen **Web-Knoten > Relais > responseHeader** -Knoten hinzu, um Antworten hinzuzufügen, die an den Relaisserver weitergeleitet werden.

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
   <td> Zeichenfolge<br /> </td> 
  </tr> 
  <tr> 
   <td> Wert<br /> </td> 
   <td> Kopfzeilenwert <br /> </td> 
   <td> Zeichenfolge<br /> </td> 
  </tr> 
 </tbody> 
</table>

Die Standardkonfiguration lautet:

```
<responseHeader name="X-XSS-Protection" value="1; mode=block"/>
```

### umleiten {#redirection}

Hier sind die verschiedenen Parameter des Knotens **web > redirect** . Dies ist die Konfiguration des Umleitungsmoduls.

For additional information, refer to this [section](../../installation/using/deploying-an-instance.md#synchronizing-public-resources).

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
   <td> IMS organization identifier: unique organization identifier within the Adobe Marketing Cloud, used in particular for the VisitorID service and the IMS SSO. <br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> P3PCompactPolicy<br /> </td> 
   <td> Wert, der die Richtlinie beschreibt, die für permanente Cookies verwendet wird (konform mit dem P3P Compact Policy-Format). <br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> 'CAO DSP COR CURa DEVa TAIa OUR BUS IND UNI COM NAV'<br /> </td> 
  </tr> 
  <tr> 
   <td> cookieDomain<br /> </td> 
   <td> Durch Kommata getrennte Liste von Domains, die so konfiguriert werden sollen, dass Ihre Domain zum Setzen von Cookies angegeben wird. <br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> databaseId<br /> </td> 
   <td> Mit der Verfolgungsinstanz verknüpfte Datenbank-ID.<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> defLogCount<br /> </td> 
   <td> Protokollanzahl nach Aufruf: Anzahl der Protokolle, die standardmäßig bei einem Aufruf der Methode GetTrackingLogs zurückgegeben werden.<br /> </td> 
   <td> lang<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
  <tr> 
   <td> expirationURL<br /> </td> 
   <td> Seite für abgelaufene Umleitungen: URL der Webseite, die standardmäßig vom Umleitungsserver verwendet wird, wenn die Umleitung für eine Auslieferungsaktion abgelaufen ist.<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxJobsInCache<br /> </td> 
   <td> Maximale Auftragsanzahl: Maximale Anzahl der Bereitstellungsaktionen im Cache. Darf nicht kleiner als 50 sein. <br /> </td> 
   <td> lang<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> startReleitung<br /> </td> 
   <td> Starten Sie den Umleitungsdienst.<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> startRedirectInModule<br /> </td> 
   <td> Starten Sie den Umleitungsdienst im Modulmodus.<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> trackWebVisitors<br /> </td> 
   <td> Webverfolgung: Erstellung von Protokollen für die von unbekannten Benutzern besuchten Seiten. <br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> trackingPassword<br /> </td> 
   <td> Das vom Umleitungsserver verwendete Kennwort.<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

Im Folgenden finden Sie die verschiedenen Parameter des Knotens **web > redirect > reserveServer** .

Weitere Informationen finden Sie unter [Redundante Verfolgung](../../installation/using/configuring-campaign-server.md#redundant-tracking).

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
   <td> Berücksichtigt, wenn der Tracking-Server berücksichtigt wird, wenn der Ausdruck true zurückgibt. <br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> id<br /> </td> 
   <td> Name<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> url<br /> </td> 
   <td> Extra-Umleitungsserver-URL<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

### spamCheck {#spamcheck}

Hier sind die verschiedenen Parameter des Knotens **Web > SpamCheck** . Dies ist die Konfiguration der E-Mail Anti-Spam Bewertung Parameter.

Weitere Informationen finden Sie unter SpamAssassin [konfigurieren](../../installation/using/configuring-spamassassin.md).

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
   <td> Befehl zum Ausführen, um den Anti-Spam-Wert einer E-Mail (z. 'perl spamcheck.pl').<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
  </tr> 
 </tbody> 
</table>

## wfserver {#wfserver}

Hier sind die verschiedenen Parameter des **wfserver** -Knotens. Dies ist die Workflow-Prozesskonfiguration.

Weitere Informationen finden Sie unter Arbeitsabläufe und Affinitäten mit [hoher Verfügbarkeit](../../installation/using/configuring-campaign-server.md#high-availability-workflows-and-affinities).

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
   <td> affinity<br /> </td> 
   <td> Affinität<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> args<br /> </td> 
   <td> Startparameter<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
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
   <td> Beweglicher Zeitraum<br /> </td> 
   <td> lang<br /> </td> 
   <td> 20<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID von JavaScript, das beim Starten des Prozesses ausgeführt wird.<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Speicherverbrauchswarnung: Warnhinweis über die von einem bestimmten Prozess belegte RAM (in MB).<br /> </td> 
   <td> lang<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Speicherverbrauchswarnung: Warnhinweis über die von einem bestimmten Prozess belegte RAM (in MB).<br /> </td> 
   <td> lang<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> notifRelay<br /> </td> 
   <td> Benachrichtigungsrelais: HostName:Port, der das Weiterleiten von Benachrichtigungen ermöglicht.<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Die Uhrzeit, zu der der Prozess automatisch neu gestartet wird. Siehe <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatischer Prozessneustart</a>.<br /> </td> 
   <td> Zeichenfolge<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priorität am Anfang. Module mit niedriger Priorität werden zuerst gestartet und zuletzt beendet. Das syslogd-Modul muss daher die Priorität 0 haben.<br /> </td> 
   <td> Short<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

