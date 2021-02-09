---
solution: Campaign Classic
product: campaign
title: Die Server-Konfigurationsdatei
description: Die Server-Konfigurationsdatei
audience: installation
content-type: reference
topic-tags: appendices
translation-type: tm+mt
source-git-commit: f39a84108c1f3327a469d5a230518652647ed63e
workflow-type: tm+mt
source-wordcount: '7846'
ht-degree: 27%

---


# Die Server-Konfigurationsdatei{#the-server-configuration-file}

Die Gesamtkonfiguration des Adobe Campaigns wird in der Datei **serverConf.xml** definiert, die sich im Ordner **conf** des Installationsordners befindet. In diesem Abschnitt werden alle verschiedenen Knoten und Parameter der Datei **serverConf.xml** Liste.

>[!NOTE]
>
>Serverseitige Konfigurationen können nur von der Adobe für Bereitstellungen ausgeführt werden, die von der Adobe gehostet werden. Weitere Informationen zu den verschiedenen Bereitstellungen finden Sie im Abschnitt [Hosting models](../../installation/using/hosting-models.md) oder auf [dieser Seite](../../installation/using/capability-matrix.md). Die Installations- und Konfigurationsschritte für gehostete und hybride Modelle werden in diesem [Abschnitt](../../installation/using/hosted-model.md) beschrieben.

Die ersten Parameter befinden sich im Knoten **shared**. Diese beziehen sich auf die Instanz. Sie werden potenziell von allen nlserver-Befehlen (nlserver web, nlserver wfserver usw.) verwendet. Die anderen Abschnitte beziehen sich auf einen bestimmten nlserver-Unterbefehl.

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

Nachfolgend sind die verschiedenen Parameter des Knotens **authentication** aufgeführt:

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
   <td> Cache-Dauer: Cache mit Sitzungsinformationen in Sekunden.<br /> </td> 
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

Hier sind die verschiedenen Parameter des Knotens **Authentifizierung > XTK**:

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
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> internalSecurityZone<br /> </td> 
   <td> Sicherheitszone des internen Kontos: autorisierte Zone für das interne Konto.<br /> </td> 
   <td> String <br /> </td> 
   <td> 'lan'<br /> </td> 
  </tr> 
 </tbody> 
</table>

## dataStore {#datastore}

Hier sind die verschiedenen Parameter des Knotens **dataStore**. Hier werden die Serverdatenquellen definiert.

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
   <td> Exportverzeichnis: Zielverzeichnis für die exportierten Daten.<br /> </td> 
   <td> String <br /> </td> 
   <td> '$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/export/' <br /> </td> 
  </tr> 
  <tr> 
   <td> extraSandboxedDirectories<br /> </td> 
   <td> Extra-Sandbox-Ordner: andere Pfade, die in der Sandbox hinzugefügt werden sollen (durch Kommas getrennt).<br /> </td> 
   <td> String <br /> </td> 
   <td> '/home/Customers/,/sftp/' <br /> </td> 
  </tr> 
  <tr> 
   <td> formCacheTimeToLive<br /> </td> 
   <td> Ablaufverzögerung für Formular-Cache: Zeitüberschreitung in Sekunden, nach der ein Cache-Eintrag ungültig wird. O bedeutet, dass Cache-Einträge nur zur Veröffentlichungszeit aktualisiert werden.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> hosts<br /> </td> 
   <td> DNS-Masken: liste der DNS-Masken, die diese Instanz bereitstellt (durch Kommas getrennt, kann * und ? Muster).<br /> </td> 
   <td> String <br /> </td> 
   <td> '*'<br /> </td> 
  </tr> 
  <tr> 
   <td> interactionCacheTimeToLive<br /> </td> 
   <td> JSSP-Cache-Ablaufverzögerung der Interaktion: Zeitüberschreitung in Sekunden, nach der ein Cache-Eintrag ungültig wird. Ein negativer Wert bedeutet, dass der Cache immer ungültig ist. '0', leere oder ungültige Werte gelten als 60.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> lang<br /> </td> 
   <td> Instanzsprache (Auflistung). Mögliche Werte sind "fr_FR" (Français), "en_GB" (Englisch (UK)), "en_US" (Englisch (USA)), "de_DE" (Deutsch) und "ja_JP" (Japanisch).<br /> </td> 
   <td> String <br /> </td> 
   <td> 'en_US'<br /> </td> 
  </tr> 
  <tr> 
   <td> uploadDirectory<br /> </td> 
   <td> Ordner hochladen: Zielverzeichnis für die hochgeladenen Daten.<br /> </td> 
   <td> String <br /> </td> 
   <td> '$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/upload/' <br /> </td> 
  </tr> 
  <tr> 
   <td> uploadAllowlist<br /> </td> 
   <td> Dateien, die hochgeladen werden dürfen, durch ',' getrennt. String muss ein gültiger regulärer Java-Ausdruck sein. Siehe <a href="../../installation/using/configuring-campaign-server.md#limiting-uploadable-files" target="_blank">Eingrenzen hochladbarer Dateien</a>.<br /> </td> 
   <td> String <br /> </td> 
   <td> '.+' <br /> </td> 
  </tr> 
  <tr> 
   <td> useVault<br /> </td> 
   <td> Geheimnisse im Vault speichern: Hashicorp Vault verwenden.<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> vaultSecretPath<br /> </td> 
   <td> Geheimer Pfad in Vault<br /> </td> 
   <td> String <br /> </td> 
   <td> '/v1/secret/Kampagne/'<br /> </td> 
  </tr> 
  <tr> 
   <td> vaultTokenPath<br /> </td> 
   <td> Lokaler Pfad der Datei, die den Volt-Token enthält. $(HOME) kann in diesem Pfad verwendet werden (aber nicht in anderen env Variablen).<br /> </td> 
   <td> String <br /> </td> 
   <td> '$(HOME)/.vaulttoken'<br /> </td> 
  </tr> 
  <tr> 
   <td> vaultUrl<br /> </td> 
   <td> Vault-URL von HashiCorp <br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> viewCacheTimeToLive<br /> </td> 
   <td> Gültigkeitsdauer des Ansichten-Cache: Zeitüberschreitung in Sekunden, nach der ein Cache-Eintrag ungültig wird. Ein negativer Wert bedeutet, dass der Cache immer ungültig ist. '0', leere oder ungültige Werte gelten als 60.<br /> </td> 
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

Hier sind die verschiedenen Parameter des Knotens **dataStore > proxyAdjust**. URLs, die mit dem regulären Ausdruck übereinstimmen, werden basierend auf der in urlBase definierten URL neu generiert.

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

Hier sind die verschiedenen Parameter des Knotens **dataStore > dataSource**.

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
   <td> Name der Datenquelle<br /> </td> 
   <td> String <br /> </td> 
   <td> Standard<br /> </td> 
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
   <td> Unicode-Datenspeicherung<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> dbSchema<br /> </td> 
   <td> Arbeitsbereich    <br /> </td> 
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
   <td> Typ (Auflistung). Mögliche Werte sind "Oracle", "MSSQL" (Microsoft SQL Server), "PostgreSQL" (PostgreSQL, Greenplum), "Teradata", "DB2", "MySQL", "Netezza", "AsterData", "SAPHANA" (SAP HANA), "RedShift" (Amazon Redshift), "ODBC" (Sybase, Sybase IQ) , 'Relay' (HTTP-Relay zur Remote-Datenbank).<br /> </td> 
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
   <td> Zeitzone: siehe <a href="../../installation/using/time-zone-management.md" target="_blank">Zeitzonenverwaltung</a>.<br /> </td> 
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
   <td> Datumsfelder mit Zeitzone: siehe <a href="../../installation/using/time-zone-management.md" target="_blank">Zeitzonenverwaltung</a>.<br /> </td> 
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
   <td> Präfix für Funktionen<br /> </td> 
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
   <td> liveTestDelaySec<br /> </td> 
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
   <td> Maximale Anzahl von zulässigen Verbindungen, bevor der Zugriff verweigert wird Siehe diese <a href="https://helpx.adobe.com/campaign/kb/how-to-increase-the-maximum-number-of-database-connections-from-.html">Technote</a>.<br /> </td> 
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

Hier sind die verschiedenen Parameter des Knotens **dataStore > virtualDir**. Dies ist die Konfiguration des virtuellen Ordners zu einer echten Ordnerzuordnung.

Weitere Informationen finden Sie unter [Verwalten von öffentliche Ressourcen](../../installation/using/configuring-campaign-server.md#managing-public-resources).

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

Die Standardkonfiguration lautet:

```
<virtualDir name="images" path="$(XTK_INSTALL_DIR)/var/res/img/"/>
<virtualDir name="formCache" path="$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/formCache/"/>
<virtualDir name="publicFileRes" path="$(XTK_INSTALL_DIR)/var/res/$(INSTANCE_NAME)"/>
```

### preprocessCommand {#preprocesscommand}

Hier sind die verschiedenen Parameter des Knotens **dataStore > preprocessCommand**. Dies sind die autorisierten Befehle zur Vorverarbeitung der Workflow-Aktivität &quot;Datei laden&quot;.

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

Die Standardkonfiguration lautet:

```
<preprocessCommand command="" label="None" name="none"/>
<preprocessCommand command="zcat &quot;$fileName&quot;" label="Decompression" name="zcat"/><preprocessCommand command="gpg --decrypt &quot;$fileName&quot;" label="Decrypt" name="gpg"/>
```

## dnsConfig {#dnsconfig}

Hier sind die verschiedenen Parameter des Knotens **dnsConfig** (DNS-Konfiguration).

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
   <td> Domänenname: Standarddomänenname. Wird vom SMTP HELO-Befehl verwendet. Nutzt standardmäßig die Netzwerkparameter der ersten unter Windows erklärten Netzwerkschnittstelle oder parst die Datei /etc/resolv.conf unter Linux (Angabe des Domain-Namens oder Search-Eintrag). <br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> nameServers<br /> </td> 
   <td> DNS-Server: Kommagetrennte Liste der Domänennamenserver (DNS). Siehe Hinweis unten.<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> wiederholen<br /> </td> 
   <td> Anzahl der weitere Zustellversuche für eine DNS-Abfrage.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> timeout<br /> </td> 
   <td> Timeout in Millisekunden für eine DNS-Abfrage.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 5000<br /> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Hinweis auf **nameServer**: verwendet standardmäßig das Netzwerk
>Parameter der ersten unter Windows deklarierten Netzwerkschnittstelle
>nicht in UNIX definiert. Definiert die Domänennamenserver (DNS)
>von MTA verwendet, um den Mail-Exchange für
>eine Domäne.
>
>Wenn dieser Wert nicht definiert ist, sucht die MTA diese Informationen in der Konfiguration des Host-Netzwerks. Wenn mehrere DNS-Adressen möglich sind, müssen die verschiedenen DNS-Adressen durch ein Komma getrennt werden (Beispiel: 212.155.207.1,212.155.207.2). Wenn Ihr Versand-Server über mehrere Netzwerkschnittstellen verfügt, ist die von der MTA verwendete DNS-Liste die erste. In diesem Fall sollten Sie den Parameter **nameServer** angeben, um Unklarheiten zu vermeiden.

>[!CAUTION]
>
>Wenn Ihre Netzwerk-Hostkonfiguration DHCP verwendet, findet die MTA die DNS-Liste nicht, die von DHCP bereitgestellt wird. In diesem Fall sollten Sie die DNS-Liste in den Netzwerkparametern des Windows-Bedienfelds angeben.

## exec {#exec}

Hier sind die verschiedenen Parameter des Knotens **exec** (Befehlsausführung).

Weitere Informationen finden Sie unter [Eingrenzen autorisierter externer Befehle](../../installation/using/configuring-campaign-server.md#restricting-authorized-external-commands).

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
   <td> Pfad zu der Datei, die die Befehle enthält, die der Zulassungsliste hinzugefügt werden sollen. <br /> </td> 
   <td> String <br /> </td> 
  </tr> 
  <tr> 
   <td> Benutzer<br /> </td> 
   <td> Befehle als ein anderer Benutzer ausführen.<br /> </td> 
   <td> String <br /> </td> 
  </tr> 
 </tbody> 
</table>

## htmlToPdf {#htmltopdf}

Hier sind die verschiedenen Parameter des Knotens **htmlToPdf**. Dies ist die Konfiguration des Dienstes zum Konvertieren von Webseiten in PDF-Dokumente.

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
   <td> Befehlszeile zum Ausführen der Konvertierung (im 'anderen' Modus).<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessusCount<br /> </td> 
   <td> Max. Anzahl der gleichzeitig auf einem Computer zulässigen Konvertierungsprozesse.<br /> </td> 
   <td> Lang<br /> </td> 
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
   <td> Timeout für eine Konversion: maximale Konvertierungszeit in Sekunden. Über diesen Schwellenwert hinaus wird der Konvertierungsprozess gestoppt und ein Fehler ausgegeben.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 120<br /> </td> 
  </tr> 
  <tr> 
   <td> verbose<br /> </td> 
   <td> Funktionsmodus: beginn im ausführlichen Modus zur Fehlerdiagnose.<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> waitTime<br /> </td> 
   <td> Verzögerung beim Warten auf einen Prozess: Verzögerung in Sekunden, wenn alle Prozesse gleichzeitig verwendet werden und auf die Freigabe eines Prozesses gewartet wird. Wenn diese Verzögerung überschritten wird, wird die Konvertierung beendet und ein Fehler ausgegeben. <br /> </td> 
   <td> Lang<br /> </td> 
   <td> 15<br /> </td> 
  </tr> 
 </tbody> 
</table>

Beispiel für phantomjs:

```
phantomjs - -ignore-ssl-errors=true '$(XTK_INSTALL_DIR)/bin/htmlToPdf.js' '-out:{outPdf}' '-post:{postFile}' '-url:{originUrl}' -sessiontoken:{sessiontoken} -format:{format} -orientation:{orientation} -marginTop:{marginTop} -marginLeft:{marginLeft} -marginRight:{marginRight} -marginBottom:{marginBottom}
```

## javaScript {#javascript}

Hier sind die verschiedenen Parameter des Knotens **javaScript**. Dies ist die Konfiguration des JavaScript-Interpreters.

Weitere Informationen finden Sie in der [Berichte-Dokumentation](../../reporting/using/actions-on-reports.md#memory-allocation) und dieser [Technote](https://helpx.adobe.com/campaign/kb/out-of-memory-error-in-js-code-activity-in-workflows.html).

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
   <td> stapelSizeKB<br /> </td> 
   <td> Größe in Kilobyte für jeden Stapelblock. Dies ist ein Optimierungsparameter für die Speicherverwaltung, den die meisten Benutzer nicht anpassen sollten. <br /> </td> 
   <td> Lang<br /> </td> 
   <td> 8<br /> </td> 
  </tr> 
 </tbody> 
</table>

## mailExchange {#mailexchanger}

Hier sind die verschiedenen Parameter des Knotens **mailExchange**. Dies ist die Konfiguration des SMTP-Servers.

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
   <td> TCP-Anschluss des für die E-Mail-Übertragung verwendeten SMTP-Servers.<br /> </td> 
   <td> String <br /> </td> 
   <td> 25<br /> </td> 
  </tr> 
 </tbody> 
</table>

## module {#module}

Hier sind die verschiedenen Parameter des Knotens **module**. Dies ist die Konfiguration für die Namensraum Restriktionsmodul xtk.

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

## monitoring {#monitoring}

Hier sind die verschiedenen Parameter des Knotens **monitoring**. Dies ist die Konfiguration des Überwachungsdienstes.

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
   <td> maxZubereitungJobsSec<br /> </td> 
   <td> Maximale Vorbereitungszeit: Dauer in Sekunden, nach der eine Versand-Aktion nicht mehr vorbereitet werden soll.<br /> </td> 
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

Hier sind die verschiedenen Parameter des Knotens **ooconv**. Dies ist die Konfiguration des Dokument-Konvertierungsservers.

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
   <td> Maximale Leerlaufzeit des OpenOffice-Servers vor dem erzwungenen Schließen.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 7200<br /> </td> 
  </tr> 
  <tr> 
   <td> portRange<br /> </td> 
   <td> Intervall der Anschlüsse, auf denen die OpenOffice-Server lauschen.<br /> </td> 
   <td> String <br /> </td> 
   <td> 8101-8110<br /> </td> 
  </tr> 
  <tr> 
   <td> url<br /> </td> 
   <td> URL des Dokument-Konvertierungsservers.<br /> </td> 
   <td> String <br /> </td> 
   <td> "http://localhost:8080/nl/jsp/ooconv.jsp'<br /> </td> 
  </tr> 
 </tbody> 
</table>

## proxyConfig {#proxyconfig}

Hier sind die verschiedenen Parameter des Knotens **proxyConfig**. Dies ist die Konfiguration von Proxyparametern.

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
   <td> Proxy-Server benutzen.<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> override<br /> </td> 
   <td> Ausnahmen: liste von Adressen, für die Proxy-Parameter ignoriert werden sollen.<br /> </td> 
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

Hier sind die verschiedenen Parameter des Knotens **threadPool**.

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

Hier sind die verschiedenen Parameter des Knotens **urlPermission**. Dies ist die Liste der URLs, auf die der JavaScript-Code zugreifen kann.

Liste von Domänen und regulären Ausdrücken, die angeben, ob eine im JavaScript-Code gefundene URL vom Adobe Campaign-Server verwendet werden kann oder nicht.

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
   <td> Standardaktion, wenn sich die URL nicht in der autorisierten Liste (Auflistung) befindet. Mögliche Werte sind 'ignore' (autorisieren ohne Warnmeldung, dies erfordert die Deaktivierung des Schutzes), 'warn' (autorisieren und eine Warnmeldung ausgeben) und 'Ablehnen' (Zugriff auf die URL verbieten).<br /> </td> 
   <td> String <br /> </td> 
   <td> Ablehnen<br /> </td> 
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

Fügen Sie für jede URL einen Knoten **url** mit den folgenden Parametern hinzu:

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
   <td> Domänenname oder Domänenname des übergeordneten Elements, der von der URL betroffen ist: die Domäne der URL ganz oder teilweise zu überprüfen, um die Überprüfung zu beschleunigen. Die URL wird nur in Bezug auf den regulären Ausdruck überprüft, wenn die Domäne dsnSuffix enthält.<br /> </td> 
   <td> String <br /> </td> 
  </tr> 
  <tr> 
   <td> urlRegEx<br /> </td> 
   <td> Regulärer Ausdruck zum Präzisieren der Validierung von URLs, die zu dieser Domäne gehören: regulärer Ausdruck, den die URL überprüfen muss, falls er mit dem dnsSuffix übereinstimmt.<br /> </td> 
   <td> String <br /> </td> 
  </tr> 
 </tbody> 
</table>

Wenn ein Datensatz **dnsSuffix**, aber nicht **urlRegEx** erfüllt, wird der folgende Datensatz untersucht.

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

Hier sind die verschiedenen Parameter des Knotens **xtkJobs**. Dies ist die Konfiguration der Serveraufträge.

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
   <td> Lang<br /> </td> 
   <td> 500<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Archivieren von {#archiving}

Hier sind die verschiedenen Parameter des Knotens **Archivierung**. Dies ist die Konfiguration der ausgeführten Archivierungsvorgänge im Hintergrund.

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
   <td> Lang<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> archivingType<br /> </td> 
   <td> Archivierungsstrategie für gesendete Nachrichten (Auflistung). Mögliche Werte sind '0' (kein Archivieren) und '1' (Transfer Archivierung gesendeter Nachrichten an einen SMTP-Server).<br /> </td> 
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
   <td> Größe eines komprimierten Archivs: Maximale Anzahl von Dateien in einem komprimierten Archiv.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 10000<br /> </td> 
  </tr> 
  <tr> 
   <td> compressionFormat<br /> </td> 
   <td> Komprimierungsformat, das während der Archivierung verwendet wird (Auflistung). Mögliche Werte sind '0' (keine Komprimierung) und '1' (komprimieren Sie gesendete Nachrichten im ZIP-Format).<br /> </td> 
   <td> Byte<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> expirationDelay<br /> </td> 
   <td> Verzögerung vor der automatischen Archivierung nicht verarbeiteter E-Mails: Anzahl der Tage, bevor unverarbeitete E-Mails archiviert werden.<br /> </td> 
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
   <td> Speicherverbrauchswarnung: Warnhinweis über die von einem bestimmten Prozess benötigte RAM (in MB).<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Speicherverbrauchswarnung: Warnung bezüglich der von einem bestimmten Prozess belegten RAM (in MB).<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> pollDelay<br /> </td> 
   <td> Verzögerung (in Sekunden) zwischen jedem Update-Ereignis.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Zeitpunkt des automatischen Neustarts des Prozesses. Siehe <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Neustarten des automatischen Prozesses</a>.<br /> </td> 
   <td> String <br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> purgeArchivesDelay<br /> </td> 
   <td> Anzahl Tage bevor unverarbeitete E-Mails gelöscht werden.<br /> </td> 
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
   <td> Archivierungsziel der Zielgruppe<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> smtpEnableTLS<br /> </td> 
   <td> Aktivieren Sie die SMTPS-Unterstützung: Aktiviert den Versand von E-Mails im abgesicherten Modus (STARTTLS/SMTPS), wenn diese vom Remoteserver unterstützt werden.<br /> </td> 
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

Hier sind die verschiedenen Parameter des Knotens **inMail**. Dies ist die Konfiguration des Inbound Email Management Moduls.

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
   <td> Instanzname überprüfen: Wenn "true", muss der Name der Adobe Campaign-Instanz in den Message-ID-Headern mit der aktuellen Instanz übereinstimmen. <br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> defaultForwardAddress<br /> </td> 
   <td> Anschrift: Standard-E-Mail-Übertragungsadresse wird nicht von einer Regel verarbeitet. <br /> </td> 
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
   <td> Nachrichtengröße ignorieren: wird verwendet, um die Größe einer von POP3-Servern zurückgegebenen Meldung zu ignorieren. In diesem Fall erwartet das Modul ein '. am Ende der Nachrichten. <br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> inMailPeriodSec<br /> </td> 
   <td> Lesezeitraum der Nachricht: Abruffrequenz der Meldungswarteschlange.<br /> </td> 
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
   <td> Maximale Anzahl der zu aktualisierenden Protokolle: definiert die maximale Anzahl von Protokollmeldungen, die vor der Aktualisierung der Datenbank im Arbeitsspeicher bleiben müssen.<br /> </td> 
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
   <td> Speicherverbrauchswarnung: Warnhinweis über die von einem bestimmten Prozess benötigte RAM (in MB).<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Speicherverbrauchswarnung: Warnung bezüglich der von einem bestimmten Prozess belegten RAM (in MB).<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSessionTTLSec<br /> </td> 
   <td> Sitzungsdauer: maximale Dauer der Sitzung zur Nachrichtenverarbeitung.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> popMailPeriodSec<br /> </td> 
   <td> POP3-Abrufzeitraum<br /> </td> 
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
   <td> Zeitpunkt des automatischen Neustarts des Prozesses. Siehe <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Neustarten des automatischen Prozesses</a>.<br /> </td> 
   <td> String <br /> </td> 
   <td> '06:00:00' <br /> </td> 
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
   <td> Speicherpfad der Nachrichten<br /> </td> 
   <td> String <br /> </td> 
   <td> '/tmp/inMail'<br /> </td> 
  </tr> 
 </tbody> 
</table>

## interactiond {#interactiond}

Hier sind die verschiedenen Parameter des Knotens **interactiond**. Dies ist die Konfiguration des Write-Daemons für Inbound Interaction-Ereignis.

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
   <td> Max. Anzahl der Zeichen, die im gemeinsamen Speicher für Aufrufdaten gespeichert werden.<br /> </td> 
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
   <td> Speicherverbrauchswarnung: Warnhinweis über die von einem bestimmten Prozess benötigte RAM (in MB).<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Speicherverbrauchswarnung: Warnung bezüglich der von einem bestimmten Prozess belegten RAM (in MB).<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSharedEntries<br /> </td> 
   <td> Max. Anzahl der im gemeinsamen Speicher gespeicherten Ereignis.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 25000<br /> </td> 
  </tr> 
  <tr> 
   <td> nextOffersSize<br /> </td> 
   <td> HöchstAnzahl der förderfähigen Angebot, die direkt nach den Vorschlägen sortiert werden und für statistische Zwecke zu speichern sind.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Zeitpunkt des automatischen Neustarts des Prozesses. Siehe <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Neustarten des automatischen Prozesses</a>.<br /> </td> 
   <td> String <br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Startpriorität. Module mit einer niedrigen Prioritätsziffer werden als erste gestartet und als letzte abgeschlossen. Das Syslogd-Modul muss daher die Priorität 0 aufweisen.<br /> </td> 
   <td> Kurz<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> statsPeriod<br /> </td> 
   <td> Aggregationsdauer in Sekunden für die Antwortzeitstatistik. 0 bedeutet, dass die statistische Datenspeicherung deaktiviert wurde.<br /> </td> 
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

Hier sind die verschiedenen Parameter des Knotens **mta**. Dies ist die Konfiguration von Versand-Agenten.

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
   <td> Pfad der gesendeten E-Mails speichern: wenn nicht leer, der Pfad, in dem alle Quelldateien gesendeter E-Mails gespeichert werden. <br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> debugPath<br /> </td> 
   <td> Dump-Verzeichnis: Wenn nicht leer, kopieren Sie MIME-Hüllkurven der gesendeten E-Mail-Nachrichten in diesen Ordner. Dient zum Schießen von Schwierigkeiten. <br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> dnsRequestLogDelayMs<br /> </td> 
   <td> Verzögerung bei DNS-Abfragen-Protokollen: Zeit in Millisekunden, um die Protokolle anzuzeigen.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> errorPeriodSec<br /> </td> 
   <td> Häufigkeit der Fehlerstatistiken: Zeit zwischen der Erstellung von Statistiken und der Datenspeicherung in der Datenbank. <br /> </td> 
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
   <td> Erstellen Sie Fehlerstatistiken und speichern Sie sie in der Datenbank.<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> logLevel<br /> </td> 
   <td> Anzeigelevel der Lognachrichten Schweregrad der in die Datenbank geschriebenen Protokolle. Von der MTA generierte Protokollmeldungen werden nicht immer in die Datenbank geschrieben. Mit diesem Parameter können Sie festlegen, auf welcher Ebene eine Nachricht in die Datenbank geschrieben werden soll. Wenn Sie Stufe 2 definieren, werden auch Nachrichten der Stufe 1 und 0 geschrieben, während bei der Definition von Stufe 1 nur Nachrichten der Stufe 1 und 0 geschrieben werden. Mögliche Werte sind: 0 (Fehler), 1 (Warnung), 2 (Info)<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> maxMemoryMb<br /> </td> 
   <td> Maximale Speichergröße (in MB), die ein Datenverarbeitungsprozess verwenden kann. Über dieser Grenze hinaus wird der Prozess neu gestartet, sodass der verwendete Speicher an das System freigegeben wird.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1024<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Speicherverbrauchswarnung: Warnhinweis über die von einem bestimmten Prozess benötigte RAM (in MB).<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Speicherverbrauchswarnung: Warnung bezüglich der von einem bestimmten Prozess belegten RAM (in MB).<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> minConnectionsToLog<br /> </td> 
   <td> Zu berücksichtigender Verbindungsschwellenwert. Fehlerstatistiken werden nicht für einen bestimmten Pfad generiert, wenn die Gesamtanzahl der Verbindungen für den von errorPeriodSec angegebenen Zeitraum strikt unter dem Schwellenwert liegt.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> minErrorsToLog<br /> </td> 
   <td> Zu berücksichtigender Fehlerschwellenwert: Fehlerstatistiken werden für einen angegebenen Pfad nicht generiert, wenn die Gesamtfehleranzahl für den von errorPeriodSec angegebenen Zeitraum strikt unter dem Schwellenwert liegt.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> minMessagesToLog<br /> </td> 
   <td> Zu berücksichtigender Meldungsschwellenwert. Fehlerstatistiken werden nicht für einen bestimmten Pfad generiert, wenn die Gesamtzahl der Nachrichten, die für den von errorPeriodSec angegebenen Zeitraum gesendet wurden, strikt unter dem Schwellenwert liegt.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
  <tr> 
   <td> notificationRelay<br /> </td> 
   <td> Benachrichtigungsrelais: HostName:Anschluss zum Weiterleiten von Benachrichtigungen.<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Zeitpunkt des automatischen Neustarts des Prozesses. Siehe <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Neustarten des automatischen Prozesses</a>.<br /> </td> 
   <td> String <br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> purgeDataLogDelay<br /> </td> 
   <td> Verzögerung vor dem Löschen archivierter E-Mails: Anzahl Tage vor archivierten E-Mails im in dataLogPath angegebenen Verzeichnis entfernt.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 15<br /> </td> 
  </tr> 
  <tr> 
   <td> retryLostMessages<br /> </td> 
   <td> Verlorene Nachrichten wiederholen: Teile von Versänden werden erneut versucht, wenn der untergeordnete Prozess leer ist.<br /> </td> 
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
   <td> Aktivieren Sie den Signaturmechanismus. Dies verbessert die Sicherheit bei der Verfolgung von Links in E-Mails.<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> true<br /> </td> 
  </tr>
  <tr> 
   <td> statServerAddress<br /> </td> 
   <td> Adresse des Versand-Statistikservers, angegeben als 
    &lt;dns oder ip&gt; 
      <code>[</code>: 
     &lt;Anschluss&gt; 
       <code>]</code>. Siehe 
      <a href="../../installation/using/email-deliverability.md#coordinates-of-the-statistics-server" target="_blank">Koordinaten des Statistikservers</a>. 
      <br /> 
     </td> 
   <td> String <br /> </td> 
   <td> Wenn nicht definiert, ist der Standardanschluss 7777.<br /> </td> 
  </tr> 
  <tr> 
   <td> statServerTLSSupport<br /> </td> 
   <td> TLS nach Domäne aktivieren: aktiviert die durch MX konfigurierbaren TLS (erfordert einen aktuellen Statistikserver).<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> true <br /> </td> 
  </tr> 
  <tr> 
   <td> statServerVersion<br /> </td> 
   <td> Verwendete Protokollversion: Version des Kommunikationsprotokolls (1 für einen Server der Version 5.11 und 6.0.2, 2 für einen Server der Version 6.1).<br /> </td> 
   <td> String <br /> </td> 
   <td> Wenn nicht definiert, wird die neueste Version verwendet. <br /> </td> 
  </tr> 
  <tr> 
   <td> useMomentum<br /> </td> 
   <td> Wenn "true"festgelegt ist, verwendet Ihre Instanz die <a href="../../delivery/using/sending-with-enhanced-mta.md" target="_blank">Erweiterte MTA</a>.<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> <br /> </td>b 
  </tr>
  <tr> 
   <td> verifyMode<br /> </td> 
   <td> Überprüfungsmodus: Aktiviert den Überprüfungsmodus (keine physische Übertragung von Nachrichten); wird für Simulation und Tests verwendet).<br /> </td> 
   <td> Boolesch<br /> </td> 
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
   <td> X-Mailer-Feld: Wert des Felds 'X-Mailer' in der SMTP-Mail-Kopfzeile.<br /> </td> 
   <td> String <br /> </td> 
   <td> 'nlserver, Build $(PRODUCT_VERSION)'<br /> </td> 
  </tr>  
 </tbody> 
</table>

### cache {#cache}

Konfigurieren Sie im Knoten **cache** die folgenden Parameter. Dies ist die lokale Dateicache-Konfiguration.

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
   <td> Recycling nach: Punkt, ausgedrückt in Sekunden, nach dem die Datei automatisch aus dem Cache gelöscht wird, um die Datenspeicherung wiederherzustellen.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 244800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSizeOnDiskMb<br /> </td> 
   <td> Maximale Cachegröße (Mb).<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1024<br /> </td> 
  </tr> 
  <tr> 
   <td> purgePeriodSec<br /> </td> 
   <td> Purge Frequenz: Zeitraum in Sekunden zwischen der Ausführung des Cache-Bereinigungsmechanismus.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 3600<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Relais {#relay}

Konfigurieren Sie im Knoten **mta > relais** die folgenden Parameter. Dies ist die Konfiguration des E-Mail-Servers für den message-Versand.

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

### übergeordnet {#master}

Konfigurieren Sie im Knoten **mta > Übergeordnet** die folgenden Parameter. Dies ist die Konfiguration des Hauptservers.

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
   <td> Intervall, in der die zu sendenden Vorgänge aus der Datenbank abgerufen werden Dieser Wert gibt die Abrufhäufigkeit der Datenbank (in Sekunden) an. Um die Liste von auf Versand wartenden Aufträgen zu erhalten, fragt die MTA die Datenbank regelmäßig ab. Wenn kein Auftrag abgewartet wird, wird der Abrufezeitraum durch diesen Wert definiert. Andernfalls, wenn ein Auftrag auf einen untergeordneten Server übertragen wurde, wird diese Abruffrist automatisch auf eine Sekunde reduziert, sodass ein neuer Auftrag so bald wie möglich erneut verarbeitet werden kann, d. h. sobald ein untergeordneter Server wieder verfügbar ist. Dies bedeutet nicht, dass die Datenbanküberprüfung jede Sekunde durchgeführt wird, bis ein untergeordneter Server wieder verfügbar ist. Ein Datenbankzugriff erfolgt nur dann, wenn mindestens ein untergeordneter Server verfügbar ist.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
  <tr> 
   <td> dataBaseRetryDelaySec<br /> </td> 
   <td> Wartezeit nach fehlgeschlagener Verbindung mit der Datenbank Ein Datenbankverbindungsfehler wird in der Regel vom Datenbankserver selbst verursacht. Der Server kann beispielsweise auch zu Wartungszwecken gestoppt werden. Der DataBaseRetryDelay-Parameter definiert die Dauer zwischen zwei Verbindungsverversuchen bei einem Datenbankverbindungsfehler.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> domainKeysReloadPeriodSec<br /> </td> 
   <td> Gültigkeitsdauer für den Cache privater Schlüssel (DomainKeys). Die für die Signatur gemäß der DomainKeys-Empfehlung (http://antispam.yahoo.com/domainkeys) verwendeten privaten Schlüssel werden in der Datenbank in Form von Optionen gespeichert. Der Parameter domainKeysReloadPeriodSec gibt an, wie lange der MTA diese Schlüssel im Cache speichern darf (in Sekunden). Nach Ablauf dieser Dauer müssen alle Schlüssel erneut aus der Datenbank geladen werden<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSpareServers<br /> </td> 
   <td> Maximale Anzahl der untergeordneten Server. Stellt die maximale Anzahl der ausgeführten Server dar. Es wird empfohlen, diese Zahl auf ein optimales Maß zu beschränken, das mit den Serverspeicherressourcen kompatibel ist. Dies kann während eines Versands überprüft werden. Der verwendete Speicher sollte nicht mehr als ein Drittel des verfügbaren physischen Speichers betragen, da andernfalls der Swap verwendet wird. Siehe <a href="../../installation/using/configuring-campaign-server.md#mta-child-processes" target="_blank">untergeordnete MTA-Prozesse</a>.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> minSpareServers<br /> </td> 
   <td> Mindestanzahl der untergeordneten Server. Die MTA versucht, mindestens diese Anzahl von Servern auszuführen. Wenn weniger vorhanden ist, werden neue Server jede Sekunde neu gestartet, bis dieser Wert erreicht ist.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> startSpareServers<br /> </td> 
   <td> Anzahl der untergeordneten Server beim Beginn. Die Anzahl der untergeordneten Server wird dynamisch überwacht. bei MTA-Beginn so viele untergeordnete Server wie durch diesen Wert angegeben erstellt werden. Normalerweise können untergeordnete Server nicht schneller als ein Server pro Sekunde gestartet werden, um Hostressourcen zu sparen. Bei MTA-Beginn wird diese Einschränkung jedoch außer Kraft gesetzt, sodass untergeordnete Server so bald wie möglich verfügbar sind.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
 </tbody> 
</table>

### child {#child}

Konfigurieren Sie im Knoten **mta > child** die folgenden Parameter. Dies ist die Konfiguration von untergeordneten Servern.

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
   <td> Zeitüberschreitung, bis leere untergeordnete Server beendet wurden. Wenn ein untergeordneter Server eine Leerlaufzeit hat, die größer als dieser Parameter ist, wird er automatisch abgeschaltet, um Hostressourcen freizugeben.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> maxAgeSec<br /> </td> 
   <td> Maximale Dauer der Nachrichtenspeicherung. Wenn eine vorbereitete Nachricht aufgrund von Einschränkungen nicht gesendet werden konnte oder keine Verbindung zur Zielgruppe-MTA hergestellt werden konnte, wird die Meldung abgebrochen und beim nächsten Versuch verarbeitet.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxGCMConnectPerChild<br /> </td> 
   <td> Maximale Anzahl paralleler Http-Anfragen an FCM von jedem Kindserver initiiert.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 8<br /> </td> 
  </tr> 
  <tr> 
   <td> maxMsgPerChild<br /> </td> 
   <td> Maximale Anzahl der Nachrichten pro untergeordneter Server. Jedes untergeordnete MTA-Objekt verarbeitet diese Anzahl von Nachrichten und stirbt. Es ist wichtig, eine Zahl anzugeben, mit der Speicher- oder Ressourcenlecks im MTA harmlos sind (normalerweise einige Tausend). Auch wenn im MTA-Code keine Speicherlecks bekannt sind, sind die eingebetteten JavaScript- und XSL-Engines nicht vollständig zuverlässig.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 5000000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxWaitingMessages<br /> </td> 
   <td> Ausstehende Nachrichten: maximale Anzahl von Nachrichten, die im Speicher ausgeliefert werden. <br /> </td> 
   <td> Lang<br /> </td> 
   <td> 2000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxWorkingSetMb<br /> </td> 
   <td> Maximale Speichergröße (in MB), die ein untergeordneter Prozess verwenden kann. Über dieser Grenze hinaus wird der Prozess gestoppt, sodass der verwendete Speicher an das System freigegeben wird. <br /> </td> 
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
   <td> Beginn mit der höchsten Priorität MX.<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> timeToLive<br /> </td> 
   <td> Maximale Anzahl aufeinander folgender Versuche bei Wiederaufnahme.<br /> </td> 
   <td> Lang<br /> </td> 
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
   <td> Aktiviert den Versand von E-Mails im abgesicherten Modus (STARTTLS/SMTPS), wenn diese vom Remoteserver unterstützt werden.<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> idleSessionTimeoutSec<br /> </td> 
   <td> Timeout inaktiver Sitzungen Dieser Parameter wird nur verwendet, wenn die Sitzung zur Übertragung mehrerer Nachrichten an eine bestimmte Domäne wiederverwendet wird. Wenn die MTA die Nachrichtenübertragung abgeschlossen hat, wird die verwendete SMTP-Sitzung nicht systematisch geschlossen. Wenn eine Nachricht für dieselbe Domäne gesendet werden kann, wird dieselbe SMTP-Sitzung wiederverwendet, weshalb die Sitzung nicht automatisch geschlossen wird. Mit dem Parameter IdleSessionTimeout können Sie festlegen, wie lange eine SMTP-Sitzung aktiv bleiben kann, um auf eine weitere Nachricht zu warten. Sobald die Dauer abgelaufen ist, wird die Sitzung automatisch geschlossen.<br /> </td> 
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
   <td> Maximale Anzahl an SMTP-Sitzungen pro untergeordnetem Server Um eine Nachricht zu senden, initialisiert das MTA eine SMTP-Verbindung mit dem Empfänger-MTA. Die maximale Anzahl gleichzeitiger und aktiver SMTP-Sitzungen für einen bestimmten untergeordneten Server ist durch diesen Wert begrenzt. Wenn Sie diesen Wert mit maxSpareServers multiplizieren, erhalten Sie die maximale Anzahl von Meldungen, die gleichzeitig von einem bestimmten untergeordneten Server verarbeitet werden können.<br /> </td> 
   <td> Lang<br /> </td> 
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
   <td> Domänenname: lokaler Domänenname, der mit der IP-Adresse verknüpft ist. Wird verwendet, wenn ein SMTP-HELO-Befehl ausgegeben wird.<br /> </td> 
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
   <td> Zugehörige physische Adresse. z. B.: '192.168.0.1'<br /> </td> 
   <td> String <br /> </td> 
  </tr> 
  <tr> 
   <td> publicId<br /> </td> 
   <td> Kennung der zugeordneten öffentlichen Adresse. Wird vom Statistikserver als Schlüssel verwendet. Muss numerisch sein. Siehe diesen <a href="../../installation/using/email-deliverability.md#managing-ip-addresses">Abschnitt</a>.<br /> </td> 
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

Hier sind die verschiedenen Parameter des Knotens **nmac**. Dies ist die Konfiguration von für Push-Benachrichtigungs-Versand.

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
   <td> Use HTTP proxy defined in shared/proxyHTTP. <br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Relais {#relay-1}

Hier sind die verschiedenen Parameter des Knotens **nmac > relais**. Dadurch wird die Verwendung eines Relais für den Message Versand (ios HTTP2 Connector) konfiguriert.

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
   <td> Port<br /> </td> 
   <td> Relay Port<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 443<br /> </td> 
  </tr> 
  <tr> 
   <td> trustCertsChain<br /> </td> 
   <td> Zertifikatskette (PEM-Datei). Nützlich bei der Verwendung eines Trackservers.<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

## pipeliniert {#pipelined}

Hier sind die verschiedenen Parameter des Knotens **pipelined**. Dies ist die Konfiguration des Ereignis-Verarbeitungsmoduls für Pipeline-Services.

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
   <td> "https://api.omniture.com' <br /> </td> 
  </tr> 
  <tr> 
   <td> authPrivateKey<br /> </td> 
   <td> Privater Schlüssel zum Abrufen von Token (verschlüsselt in AES mit der XtkKey-Option).<br /> </td> 
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
   <td> Authentifizierung deaktivieren: Verbindung zu Pipeline-Diensten ohne Authentifizierung herzustellen. <br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> discoverPipelineEndpoint<br /> </td> 
   <td> URL, um die URL der Pipeline-Dienste zu ermitteln.<br /> </td> 
   <td> String <br /> </td> 
   <td> "https://producer-pipeline-pnw.adobe.net'<br /> </td> 
  </tr> 
  <tr> 
   <td> dumpStatePeriodSec<br /> </td> 
   <td> Statusspeicherzeitraum: Häufigkeit, mit der die internen Informationen des Prozesses in einer Datei gespeichert werden. Inaktiv, wenn 0. <br /> </td> 
   <td> Lang<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> forcedPipelineEndpoint<br /> </td> 
   <td> Listening-URL: erzwingen Sie die Listening-URL der Pipeline-Dienste. <br /> </td> 
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
   <td> Speicherverbrauchswarnung: Warnhinweis über die von einem bestimmten Prozess benötigte RAM (in MB).<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Speicherverbrauchswarnung: Warnung bezüglich der von einem bestimmten Prozess belegten RAM (in MB).<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> monitorServerPort<br /> </td> 
   <td> Statusserveranschluss: HTTP-Serveranschluss, über den der Prozessstatus Abfrage werden kann. Inaktiv, wenn 0.<br /> </td> 
   <td> Lang<br /> </td> 
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
   <td> Verzögerung vor der Speicherung des Zeigers: Der Zeiger wird während dieser Zeit mindestens einmal in der Datenbank gespeichert (bei niedriger Aktivität nützlich).<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Zeitpunkt des automatischen Neustarts des Prozesses. Siehe <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Neustarten des automatischen Prozesses</a>.<br /> </td> 
   <td> String <br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> processingJSThreads<br /> </td> 
   <td> Anzahl der Threads für die Verarbeitung von Ereignissen mit einem personalisierten JavaScript-Connector.<br /> </td> 
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
   <td> Verzögerung zwischen der Verarbeitung bei Fehler.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
  <tr> 
   <td> retryValiditySec<br /> </td> 
   <td> Nach diesem Zeitraum wird beendet: das Ereignis verlassen, wenn die Verarbeitung nach diesem Zeitraum immer noch fehlschlägt.<br /> </td> 
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

## reparieren {#repair}

Hier sind die verschiedenen Parameter des Knotens **restore**. Dies ist die Konfiguration des Datenbankreparaturmoduls.

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
   <td> Reparaturmodul für Versand-Aktionen: Verzögerung (in Minuten), nach der Versand-Aktionen vom Reparaturmodul verarbeitet werden können. <br /> </td> 
   <td> Lang<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
 </tbody> 
</table>

## securityZone {#securityzone}

Hier sind die verschiedenen Parameter des Knotens **securityZone**.

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
   <td> Verwenden Sie kein Sicherheitstoken.<br /> </td> 
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

Hier sind die verschiedenen Parameter des Knotens **securityZone > subNetwork**.

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
   <td> Maske oder Adresse des vom Sub-Netzwerk verwendeten (Reverse) Proxys, um auf die Instanz zuzugreifen. In diesem Fall wird der Header 'X-Forwarded-For' anstelle des Proxys getestet.<br /> </td> 
   <td> String <br /> </td> 
   <td> 127.0.0.1 <br /> </td> 
  </tr> 
 </tbody> 
</table>

## sms {#sms}

Hier sind die verschiedenen Parameter des Knotens **sms**. Dies ist die Konfiguration des eingehenden SMS-Verwaltungsmoduls.

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
   <td> Maximale Anzahl Tage, in denen Dateien vom SMPP-Connector gespeichert werden.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> dataSizeMo<br /> </td> 
   <td> Maximale Größe in MB der SMPP-Arbeitsdateien.<br /> </td> 
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
   <td> Wiederholung des Rahmens für die Sitzungskontinuität: max. Zeitraum in Sekunden zwischen zwei Frames, um darauf hinzuweisen, dass die empfangende Sitzung weiterhin aktiviert ist.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 25<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Speicherverbrauchswarnung: Warnhinweis über die von einem bestimmten Prozess benötigte RAM (in MB).<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Speicherverbrauchswarnung: Warnung bezüglich der von einem bestimmten Prozess belegten RAM (in MB).<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> pollPeriod<br /> </td> 
   <td> Suchfrequenz: SMS-Kontoabfragezeitraum.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Zeitpunkt des automatischen Neustarts des Prozesses. Siehe <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Neustarten des automatischen Prozesses</a>.<br /> </td> 
   <td> String <br /> </td> 
   <td> '06:00:00' <br /> </td> 
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
   <td> Anzahl der Sekunden für die SR-Verarbeitung: nur SRs mit einem Wiederherstellungsdatum vor der aktuellen Zeit abzüglich der Dauer in Sekunden, die von srReadDelay angegeben wird. <br /> </td> 
   <td> Lang<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> timeout<br /> </td> 
   <td> Zeitüberschreitung bei der Kommunikation mit dem SMS-Gateway.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
 </tbody> 
</table>

### netsize {#netsize}

Hier sind die verschiedenen Parameter des Knotens **sms > netsize**.

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

## stat {#stat}

Hier sind die verschiedenen Parameter des Knotens **stat**. Dies ist die Konfiguration des MTA-Statistikmoduls.

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
   <td> Speicherverbrauchswarnung: Warnhinweis über die von einem bestimmten Prozess benötigte RAM (in MB).<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Speicherverbrauchswarnung: Warnung bezüglich der von einem bestimmten Prozess belegten RAM (in MB).<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> Port<br /> </td> 
   <td> Server-Listen-Port. Siehe diesen <a href="../../installation/using/email-deliverability.md#definition-of-the-server-port">Abschnitt</a>.<br /> </td> 
   <td> Kurz<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Zeitpunkt des automatischen Neustarts des Prozesses. Siehe <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Neustarten des automatischen Prozesses</a>.<br /> </td> 
   <td> String <br /> </td> 
   <td> '06:00:00' <br /> </td> 
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

Hier sind die verschiedenen Parameter des Knotens **syslogd**. Dies ist die Konfiguration des Protokollverwaltungsmoduls.

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
   <td> Speicherverbrauchswarnung: Warnhinweis über die von einem bestimmten Prozess benötigte RAM (in MB).<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Speicherverbrauchswarnung: Warnung bezüglich der von einem bestimmten Prozess belegten RAM (in MB).<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Zeitpunkt des automatischen Neustarts des Prozesses. Siehe <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Neustarten des automatischen Prozesses</a>.<br /> </td> 
   <td> String <br /> </td> 
   <td> '06:00:00' <br /> </td> 
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

Hier sind die verschiedenen Parameter des Knotens **tracking**. Dies ist die Konfiguration des Tracking-Servers.

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
   <td> Deaktivieren Sie falsch geformte URLs, die von vorherigen Builds generiert wurden.<br /> </td> 
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
   <td> Duplizieren von Öffnungen: Entfernen Sie Duplikat-offene Trackinglogs, um die Auswirkungen von E-Mail-Vorschauen in E-Mail-Lesern wie Outlook zu begrenzen.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> errorIgnorePercent<br /> </td> 
   <td> Bis zu X % der Fehler ignorieren: aktualisieren Sie keine Verfolgungsindikatoren, solange das Verhältnis der nicht bereits berücksichtigten Protokoll diesen Wert nicht erreicht. <br /> </td> 
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
   <td> Indikatoren berechnen während: Dauer nach dem Gültigkeitsdatum eines Versands, nach dem keine konsolidierten Indikatoren mehr berechnet werden.<br /> </td> 
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
   <td> Speicherverbrauchswarnung: Warnhinweis über die von einem bestimmten Prozess benötigte RAM (in MB).<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Speicherverbrauchswarnung: Warnung bezüglich der von einem bestimmten Prozess belegten RAM (in MB).<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> phishbowlServiceAPIKey<br /> </td> 
   <td> API-Schlüssel für die Phishbowl Service Endpoint-Integration. Dadurch wird die Umleitung von fehlerhaften URLs, die aus älteren Builds generiert wurden, geschützt. <br /> </td> 
   <td> Lang<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> phishbowlServiceEndpoint<br /> </td> 
   <td> Endpunkt für die Phishbowl Service Endpoint-Integration. Dadurch wird die Umleitung von fehlerhaften URLs, die aus älteren Builds generiert wurden, geschützt.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Zeitpunkt des automatischen Neustarts des Prozesses. Siehe <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Neustarten des automatischen Prozesses</a>.<br /> </td> 
   <td> String <br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Startpriorität. Module mit einer niedrigen Prioritätsziffer werden als erste gestartet und als letzte abgeschlossen. Das Syslogd-Modul muss daher die Priorität 0 aufweisen.<br /> </td> 
   <td> Kurz<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> trackingIgnorePercent<br /> </td> 
   <td> Ignorieren Sie bis zu X % der Verfolgung: Aktualisieren Sie keine Tracking-Indikatoren, solange das Verhältnis der nicht bereits berücksichtigten Protokoll diesen Wert nicht erreicht.<br /> </td> 
   <td> Byte<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> trackingIgnorePeriod<br /> </td> 
   <td> Aktualisieren von Verfolgungsindikatoren: maximale Dauer vor der Neuberechnung der Tracking-Indikatoren.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
  <tr> 
   <td> userAgentCacheSize<br /> </td> 
   <td> Größe des Browser-ID-Cache.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 500<br /> </td> 
  </tr> 
 </tbody> 
</table>

## trackinglogd {#trackinglogd}

Hier sind die verschiedenen Parameter des Knotens **trackinglogd**. Dies ist die Konfiguration des Verfolgungsprotokolls Schreibdaemon.

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
   <td> Max. weitere Zustellversuche zum Schreiben: Maximale Anzahl von Dateien, die bei einem Schreibfehler in Protokolldateien erstellt werden können.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> maxLogsSizeOnDiskMb<br /> </td> 
   <td> Maximale Protokollgröße: Maximaler Speicherplatz, der von Protokollen auf dem Datenträger (in MB) verwendet wird. Darf nicht kleiner als 100 MB sein. <br /> </td> 
   <td> Lang<br /> </td> 
   <td> 500<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Speicherverbrauchswarnung: Warnhinweis über die von einem bestimmten Prozess benötigte RAM (in MB).<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Speicherverbrauchswarnung: Warnung bezüglich der von einem bestimmten Prozess belegten RAM (in MB).<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSharedLogs<br /> </td> 
   <td> Maximale Protokollanzahl: maximale Anzahl von Protokollen, die im gemeinsamen Speicher gespeichert sind. Darf nicht weniger als 10000 sein. <br /> </td> 
   <td> Lang<br /> </td> 
   <td> 25000<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Zeitpunkt des automatischen Neustarts des Prozesses. Siehe <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Neustarten des automatischen Prozesses</a>.<br /> </td> 
   <td> String <br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> purgeLogsPeriod<br /> </td> 
   <td> Anzahl der Protokolle vor der Bereinigung: Anzahl der Protokolle, die vor der Bereinigung der Protokolldateien eingefügt wurden. Darf nicht kleiner als 50000 sein.<br /> </td> 
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

## web {#web}

Hier sind die verschiedenen Parameter des Knotens **web**. Dies ist die Konfiguration des Webmoduls.

Weitere Informationen finden Sie in diesem [Abschnitt](../../installation/using/configuring-campaign-server.md#default-port-for-tomcat).

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
   <td> Überwachungsanschluss für Tomcat: Siehe <a href="../../installation/using/configuring-campaign-server.md#configuring-tomcat" target="_blank">Konfigurieren von Tomcat</a>.<br />. </td> 
   <td> Kurz<br /> </td> 
   <td> 8005<br /> </td> 
  </tr> 
  <tr> 
   <td> httpPort<br /> </td> 
   <td> Tomcat HTTP-Listening-Anschluss: Siehe <a href="../../installation/using/configuring-campaign-server.md#configuring-tomcat" target="_blank">Konfigurieren von Tomcat</a>.<br />. </td> 
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
   <td> Größe der Warteschlange für SubmitDelivery-Aufrufe: Maximale Anzahl von SubmitDelivery SOAP-Aufrufen, die in die Warteschlange gestellt werden können.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 50<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Speicherverbrauchswarnung: Warnhinweis über die von einem bestimmten Prozess benötigte RAM (in MB).<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Speicherverbrauchswarnung: Warnung bezüglich der von einem bestimmten Prozess (in MB) belegten RAM-Menge<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> notificationRelay<br /> </td> 
   <td> Benachrichtigungsrelais: HostName:Port aktiviert die Übertragung von Benachrichtigungen.<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Zeitpunkt des automatischen Neustarts des Prozesses. Siehe <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Neustarten des automatischen Prozesses</a>.<br /> </td> 
   <td> String <br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Startpriorität. Module mit einer niedrigen Prioritätsziffer werden als erste gestartet und als letzte abgeschlossen. Das Syslogd-Modul muss daher die Priorität 0 aufweisen.<br /> </td> 
   <td> Kurz<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> startSoapRouterInModule<br /> </td> 
   <td> Beginn des SOAP-Routers im Modulmodus.<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

### jsp {#jsp}

Hier sind die verschiedenen Parameter des Knotens **web > jsp**. Dies ist die Konfiguration der von den JSPs verwendeten Parameter.

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
   <td> Ordner herunterladen: Downloadpfad der Programm für die Clientkonsolen.<br /> </td> 
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

Der Knoten **web > jsp > classpath** enthält die Liste aller Klassenpfade, die beim Starten von JVM verwendet werden. Die Standardkonfiguration lautet:

```
'$(XTK_INSTALL_DIR)/tomcat-8/bin/bootstrap.jar
          $(XTK_INSTALL_DIR)/tomcat-8/bin/tomcat-juli.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/tomcat-coyote.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/tomcat-util.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/tomcat-api.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/servlet-api.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/jsp-api.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/el-api.jar
          $(XTK_INSTALL_DIR)/java/lib/log4j-1.2.11.jar
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

Hier sind die verschiedenen Parameter des Knotens **web > jssp**. Dies ist die Konfiguration der von den JSSPs verwendeten Parameter.

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

Der Knoten **web > jsp > classpath** enthält die Liste aller Klassenpfade, die beim Starten von JVM verwendet werden.

### Relais {#relay-2}

Hier sind die verschiedenen Parameter des Knotens **web > relais**. Dies ist die Konfiguration des Relais für HTTP-Anfragen zwischen zwei Zonen.

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
   <td> Startet das HTTP-Weiterleitungsmodul im Webserver im Debug-Modus.<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> forbiddenCharsInAuthority<br /> </td> 
   <td> Verbotene Zeichen (Domäne): liste von verbotenen Zeichen im Abschnitt 'Autorität' eines URI.<br /> </td> 
   <td> String <br /> </td> 
   <td> '.?#@/:' <br /> </td> 
  </tr> 
  <tr> 
   <td> forbiddenCharsInPath<br /> </td> 
   <td> Verbotene Zeichen (Pfad): liste von verbotenen Zeichen im Abschnitt 'Pfad' eines URI.<br /> </td> 
   <td> String <br /> </td> 
   <td> '?#/'<br /> </td> 
  </tr> 
  <tr> 
   <td> modDir<br /> </td> 
   <td> Wert der Moduloption "mod_dir": liste der Dateien, die während einer Abfrage in einem Ordner verwendet werden sollen.<br /> </td> 
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
   <td> Beginn des HTTP-Relaismoduls innerhalb des Webservers. <br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> timeout<br /> </td> 
   <td> Wartezeit vor Löschung der ausgeschlossenen URL.<br /> </td> 
   <td> String <br /> </td> 
   <td> '60'<br /> </td> 
  </tr> 
 </tbody> 
</table>

hinzufügen Sie einen **web > relais > url**-Knoten für jede URL, die weitergeleitet werden soll (die Einfügereihenfolge definiert Priorität) mit den folgenden Parametern.

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
   <td> DNS-Alias für Relais: Kommagetrennte Liste von DNS-Aliasmasken an Relais (z. B.: '*.adobe.com').<br /> </td> 
   <td> String <br /> </td> 
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
   <td> hinzufügen Originalhost: Verwenden Sie den HTTP 'Host' Header der ursprünglichen Anforderung bei der Wiedergabe.<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> relaisPath<br /> </td> 
   <td> hinzufügen anfänglichen URL-Pfad: Hängen Sie den vollständigen Pfad der URLs an, die an die URL der Zielgruppe weitergeleitet werden sollen. <br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> status<br /> </td> 
   <td> Synchronisierungsstatus einer öffentliche Ressource (Auflistung). Mögliche Werte sind 'normal' (normale Ausführung), 'Blacklist' (URL wird bei Fehler 404 der Blockierungsliste hinzugefügt) und 'reserve' (Datei-Upload auf Reserverserver, falls vorhanden).<br /> </td> 
   <td> String <br /> </td> 
   <td> normal<br /> </td> 
  </tr> 
  <tr> 
   <td> targetUrl<br /> </td> 
   <td> URL der Seite "Zielgruppe": Siehe <a href="../../installation/using/configuring-campaign-server.md#configuring-tomcat" target="_blank">Konfigurieren von Tomcat</a>.<br />. </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> timeout<br /> </td> 
   <td> Maximale Ausführungszeit (in Sekunden) der zu wiederholenden Anforderung.<br /> </td> 
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

hinzufügen Sie für jeden HTTP-Header einen **Web > Relais > responseHeader**-Knoten, der den an den Relaisserver weitergeleiteten Antworten hinzugefügt wird.

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

Die Standardkonfiguration lautet:

```
<responseHeader name="X-XSS-Protection" value="1; mode=block"/>
```

### Umleitung {#redirection}

Hier sind die verschiedenen Parameter des Knotens **web > redirect**. Dies ist die Konfiguration des Umleitungsmoduls.

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
   <td> Organisations-ID des Identity Management Systems (IMS): eindeutige Organisationskennung innerhalb des Adobe Experience Cloud, die insbesondere für den VisitorID-Dienst und die IMS-SSO verwendet wird. <br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> P3PCompactPolicy<br /> </td> 
   <td> Wert, der die Richtlinie beschreibt, die für permanente Cookies verwendet wird (konform mit dem P3P Compact Policy-Format). <br /> </td> 
   <td> String <br /> </td> 
   <td> 'CAO DSP COR CURa DEVa TAIa OUR BUS IND UNI COM NAV'<br /> </td> 
  </tr> 
  <tr> 
   <td> cookieDomain<br /> </td> 
   <td> Durch Kommata getrennte Liste von Domains, die so konfiguriert werden sollen, dass Ihre Domain zum Setzen von Cookies angegeben wird. <br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> databaseId<br /> </td> 
   <td> Mit der Verfolgungsinstanz verknüpfte Datenbank-ID.<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> defLogCount<br /> </td> 
   <td> Anzahl der Protokolle nach Aufruf: Anzahl der Protokolle, die standardmäßig bei einem Aufruf der Methode GetTrackingLogs zurückgegeben werden.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
  <tr> 
   <td> expirationURL<br /> </td> 
   <td> Seite für abgelaufene Umleitungen: URL der Webseite, die standardmäßig vom Umleitungsserver verwendet wird, wenn die Weiterleitung für eine Versand-Aktion abgelaufen ist.<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxJobsInCache<br /> </td> 
   <td> Maximale Anzahl der Aufträge: Maximale Anzahl von Versand-Aktionen im Cache. Darf nicht kleiner als 50 sein. <br /> </td> 
   <td> Lang<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> startRedirect<br /> </td> 
   <td> Startet den Weiterleitungsdienst<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> startRedirectInModule<br /> </td> 
   <td> Beginn des Weiterleitungsdiensts im Modulmodus.<br /> </td> 
   <td> Boolesch<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> trackWebVisitors<br /> </td> 
   <td> Webtracking: Erstellung von Protokollen für die von Unbekannten Nutzern besuchten Seiten. <br /> </td> 
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

Hier sind die verschiedenen Parameter des Knotens **web > redirect > reserveServer**.

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

Hier sind die verschiedenen Parameter des Knotens **web > SpamCheck**. Dies ist die Konfiguration der E-Mail Anti-Spam Bewertung Parameter.

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

Hier sind die verschiedenen Parameter des Knotens **wfserver**. Dies ist die Workflow-Prozesskonfiguration.

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
   <td> affinität<br /> </td> 
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
   <td> Speicherverbrauchswarnung: Warnhinweis über die von einem bestimmten Prozess benötigte RAM (in MB).<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Speicherverbrauchswarnung: Warnung bezüglich der von einem bestimmten Prozess belegten RAM (in MB).<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> notificationRelay<br /> </td> 
   <td> Benachrichtigungsrelais: HostName:Port aktiviert die Übertragung von Benachrichtigungen.<br /> </td> 
   <td> String <br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Zeitpunkt des automatischen Neustarts des Prozesses. Siehe <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Neustarten des automatischen Prozesses</a>.<br /> </td> 
   <td> String <br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Startpriorität. Module mit einer niedrigen Prioritätsziffer werden als erste gestartet und als letzte abgeschlossen. Das Syslogd-Modul muss daher die Priorität 0 aufweisen.<br /> </td> 
   <td> Kurz<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

