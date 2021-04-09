---
solution: Campaign Classic
product: campaign
title: Campaign-Server konfigurieren
description: Campaign-Server konfigurieren
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 46c8ed46-0947-47fb-abda-6541b12b6f0c
translation-type: tm+mt
source-git-commit: b0a1e0596e985998f1a1d02236f9359d0482624f
workflow-type: tm+mt
source-wordcount: '2577'
ht-degree: 2%

---

# Erste Schritte mit der Kampagne-Serverkonfiguration{#gs-campaign-server-config}

In diesem Kapitel werden serverseitige Konfigurationen beschrieben, die entsprechend Ihren Anforderungen und Ihren Umgebung ausgeführt werden können.

## Einschränkungen

Diese Verfahren sind auf **lokale**/**Hybrid**-Bereitstellungen beschränkt und erfordern Administratorberechtigungen.

Bei **gehosteten** Bereitstellungen können serverseitige Einstellungen nur durch Adobe konfiguriert werden. Einige Einstellungen können jedoch in der [Kampagne-Systemsteuerung](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/key-features.html), z. B. IP-Zulassungsliste-Management oder URL-Berechtigungen, eingerichtet werden. [Weitere Informationen](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/ip-allow-listing-instance-access.html).

Weitere Informationen finden Sie in den folgenden Abschnitten:

* [Control Panel-Dokumentation](https://docs.adobe.com/content/help/de-DE/control-panel/using/control-panel-home.html)
* [Hosting-Modelle](../../installation/using/hosting-models.md)
* [Campaign Classic-On-Premise- und gehostete Funktionsmatrix](../../installation/using/capability-matrix.md)

## Konfigurationsdateien

Campaign Classic-Konfigurationsdateien werden im Ordner **conf** des Adobe Campaign-Installationsordners gespeichert. Die Konfiguration erstreckt sich über zwei Dateien:

* **serverConf.xml**: allgemeine Konfiguration für alle Instanzen. Diese Datei enthält die technischen Parameter des Adobe Campaign-Servers: diese werden von allen Instanzen freigegeben. Die Beschreibung einiger dieser Parameter ist nachfolgend beschrieben. Die verschiedenen Knoten und Parameter, die in diesem [Abschnitt](../../installation/using/the-server-configuration-file.md) aufgeführt sind.
* **config-`<instance>`.xml** (wobei  **** instanceis der Name der Instanz ist): spezifische Konfiguration der Instanz. Wenn Sie Ihren Server für mehrere Instanzen freigeben, geben Sie bitte die für jede Instanz spezifischen Parameter in die entsprechende Datei ein.

Die allgemeinen Richtlinien zur Serverkonfiguration finden Sie unter [Serverkonfiguration für Kampagnen](../../installation/using/configuring-campaign-server.md).


## Konfigurationsbereich

Konfigurieren oder passen Sie den Kampagnen-Server je nach Bedarf und Konfiguration an. Sie haben folgende Möglichkeiten:

* [Interne Kennung](#internal-identifier) sichern
* [Kampagne-Prozesse](#enabling-processes) aktivieren
* [URL-Berechtigungen](url-permissions.md) konfigurieren
* Definieren Sie [Sicherheitszonen](security-zones.md)
* [Tomcat-Einstellungen](configure-tomcat.md) konfigurieren
* [Versand-Parameter](#delivery-settings) anpassen
* Definieren Sie [Dynamische Seitensicherheit und Relais](#dynamic-page-security-and-relays)
* Liste von [Zulässige externe Befehle](#restricting-authorized-external-commands) einschränken
* [Redundante Verfolgung](#redundant-tracking) einrichten
* Verwalten Sie [Affinitäten für hohe Verfügbarkeit und Workflow](#high-availability-workflows-and-affinities)
* Dateiverwaltung konfigurieren - [Weitere Informationen](#file-and-resmanagement)
   * Format für Hochladedateien begrenzen
   * Zugriff auf öffentliche Ressourcen aktivieren
   * Proxy-Verbindung konfigurieren
* [Automatischer Prozessneustart](#automatic-process-restart)


## Interne Kennung {#internal-identifier}

Der **internal**-Bezeichner ist eine technische Anmeldung, die für Installations-, Verwaltungs- und Wartungszwecke verwendet wird. Diese Anmeldung ist keiner Instanz zugeordnet.

Operatoren, die mit dieser Anmeldung verbunden sind, haben alle Rechte auf allen Instanzen. Bei einer Neuinstallation hat diese Anmeldung kein Kennwort. Sie müssen dieses Kennwort manuell definieren.

Verwenden Sie den folgenden Befehl:

```
nlserver config -internalpassword
```

Anschließend werden die folgenden Informationen angezeigt. Geben Sie das Kennwort ein und bestätigen Sie es:

```
17:33:57 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
Enter the current password.
Password:
Enter the new password.
Password: XXXX
Confirmation: XXXX
17:34:02 >   Password successfully changed for account 'internal' (authentication mode 'nl')
```

## Aktivieren von Prozessen {#enabling-processes}

Serverprozesse auf dem Adobe Campaign sind über die Dateien **config-default.xml** und **`config-<instance>.xml`** aktiviert (und deaktiviert).

Um die Änderungen auf diese Adobe Campaigne anzuwenden, müssen Sie beim Starten des Dateidiensts den Befehl **nlserver config -reload** ausführen.

Es gibt zwei Arten von Prozessen: mehrere Instanzen und eine einzelne Instanz.

* **mehrere Instanzen**: für alle Instanzen wird ein einzelner Prozess gestartet. Dies gilt für die Prozesse **web**, **syslogd** und **trackinglogd**.

   Die Aktivierung kann über die Datei **config-default.xml** konfiguriert werden.

   Deklarieren eines Adobe Campaign-Servers für den Zugriff auf Client-Konsolen und für die Weiterleitung (Verfolgung):

   ```
   vi nl6/conf/config-default.xml
   <web args="-tomcat" autoStart="true"/>  
   <!-- to start if the machine is also a redirection server -->  
   <trackinglogd autoStart="true"/>
   ```

   In diesem Beispiel wird die Datei unter Linux mit dem Befehl **vi** bearbeitet. Sie kann mit einem beliebigen **.txt**- oder **.xml**-Editor bearbeitet werden.

* **Monoinstanz**: Ein Prozess wird für jede Instanz gestartet (Module:  **mta**,  **wfserver**,  **inMail**,  **** smund  **stat**).

   Die Aktivierung kann mithilfe der Konfigurationsdatei der Instanz konfiguriert werden:

   ```
   config-<instance>.xml
   ```

   Deklarieren eines Servers für Versand, Ausführen von Workflow-Instanzen und Wiederherstellen der Absprung-Mail:

   ```
   <mta autoStart="true" statServerAddress="localhost"/>
   <wfserver autoStart="true"/>  
   <inMail autoStart="true"/>
   <stat autoStart="true"/>
   ```

**Datenspeicherung der Kampagne**

Sie können den Ordner &quot;Datenspeicherung&quot;(**var**) der Adobe Campaign-Daten (Protokolle, Downloads, Umleitungen usw.) konfigurieren. Verwenden Sie dazu die Systemvariable **XTK_VAR_DIR**:

* Geben Sie unter Windows den folgenden Wert in der Systemvariable **XTK_VAR_DIR** an

   ```
   D:\log\AdobeCampaign
   ```

* Wechseln Sie unter Linux zur Datei **customer.sh** und geben Sie Folgendes an: **export XTK_VAR_DIR=/app/log/AdobeCampaign**.

   Weitere Informationen finden Sie unter [Parameter personalisieren](../../installation/using/installing-packages-with-linux.md#personalizing-parameters).

## Versand-Einstellungen {#delivery-settings} konfigurieren

Die Versand-Parameter müssen im Ordner **serverConf.xml** konfiguriert werden.

* **DNS-Konfiguration**: Geben Sie die Domäne des Versands und die IP-Adressen (oder den Host) der DNS-Server an, die verwendet werden, um auf MX-Typ-DNS-Abfragen zu reagieren, die vom MTA-Modul ab  **`<dnsconfig>`** dem Zeitpunkt des Abschlusses vorgenommen werden.

   >[!NOTE]
   >
   >Der Parameter **nameServers** ist für eine Installation unter Windows unerlässlich. Bei einer Installation unter Linux muss sie leer bleiben.

   ```
   <dnsConfig localDomain="domain.com" nameServers="192.0.0.1,192.0.0.2"/>
   ```

Je nach Bedarf und Einstellungen können Sie außerdem die folgenden Konfigurationen durchführen: konfigurieren Sie einen [SMTP-Relais](#smtp-relay), passen Sie die Anzahl der [untergeordneten MTA-Prozesse](#mta-child-processes), [Verwalten des ausgehenden SMTP-Traffics](#managing-outbound-smtp-traffic-with-affinities) an.

### SMTP-Relais {#smtp-relay}

Das MTA-Modul fungiert als systemeigener E-Mail-Transfer-Agent für SMTP-Übertragungen (Port 25).

Es ist jedoch möglich, ihn durch einen Server zu ersetzen, wenn Ihre Sicherheitsrichtlinien dies erfordern. In diesem Fall ist der globale Durchsatz der Relaisdurchsatz (vorausgesetzt, dass der Relaisserver-Durchsatz niedriger ist als der Durchsatz des Adobe Campaigns).

In diesem Fall werden diese Parameter durch Konfiguration des SMTP-Servers im Abschnitt **`<relay>`** festgelegt. Sie müssen die IP-Adresse (oder den Host) des SMTP-Servers angeben, der zum Übertragen von E-Mails verwendet wird, und den zugehörigen Anschluss (standardmäßig 25).

```
<relay address="192.0.0.3" port="25"/>
```

>[!IMPORTANT]
>
>Dieser Betriebsmodus setzt erhebliche Einschränkungen für Versand voraus, da er den Durchsatz aufgrund der intrinsischen Performance des Relaisservers (Latenz, Bandwith...) stark reduzieren kann. Darüber hinaus wird die Fähigkeit, synchrone Versand-Fehler zu qualifizieren (durch Analyse des SMTP-Traffics erkannt), begrenzt sein, und das Senden ist nicht möglich, wenn der Server nicht verfügbar ist.

### MTA-untergeordnete Prozesse {#mta-child-processes}

Es ist möglich, die Anzahl der untergeordneten Prozesse (maxSpareServers standardmäßig 2) zu steuern, um die Übertragungsleistung entsprechend der CPU-Leistung der Server und der verfügbaren Netzwerkressourcen zu optimieren. Diese Konfiguration ist auf jedem einzelnen Computer im Abschnitt **`<master>`** der MTA-Konfiguration vorzunehmen.

```
<master dataBasePoolPeriodSec="30" dataBaseRetryDelaySec="60" maxSpareServers="2" minSpareServers="0" startSpareServers="0">
```

Siehe auch [Optimierung des E-Mail-Versands](../../installation/using/email-deliverability.md#email-sending-optimization).

### Verwalten des ausgehenden SMTP-Traffics mit Affinitäten {#managing-outbound-smtp-traffic-with-affinities}

>[!IMPORTANT]
>
>Die Konfiguration der Affinität muss von einem Server zum anderen konsistent sein. Es wird empfohlen, sich für die Konfiguration der Affinität an die Adobe zu wenden, da Konfigurationsänderungen auf allen Anwendungsservern, auf denen die MTA ausgeführt wird, repliziert werden sollten.

Sie können den ausgehenden SMTP-Traffic durch Affinitäten mit IP-Adressen verbessern.

Gehen Sie hierzu wie folgt vor:

1. Geben Sie die Affinitäten im Abschnitt **`<ipaffinity>`** der Datei **serverConf.xml** ein.

   Eine Affinität kann mehrere verschiedene Namen haben: zum Trennen verwenden Sie das Zeichen **;**.

   Beispiel:

   ```
    IPAffinity name="mid.Server;WWserver;local.Server">
             <IP address="XX.XXX.XX.XX" heloHost="myserver.us.campaign.net" publicId="123" excludeDomains="neo.*" weight="5"/
   ```

   Informationen zur Ansicht der entsprechenden Parameter finden Sie in der Datei **serverConf.xml**.

1. Um die Auswahl der Affinitäten in den Dropdown-Listen zu aktivieren, müssen Sie die Affinitäten in der Auflistung **IPAffinity** hinzufügen.

   ![](assets/ipaffinity_enum.png)

   >[!NOTE]
   >
   >Die Auflistungen sind in [diesem Dokument](../../platform/using/managing-enumerations.md) detailliert.

   Anschließend können Sie die zu verwendende Affinität auswählen, wie unten für Typologien dargestellt:

   ![](assets/ipaffinity_typology.png)

   >[!NOTE]
   >
   >Sie können auch auf [Serverkonfiguration des Versands](../../installation/using/email-deliverability.md#delivery-server-configuration) verweisen.



## Dynamische Seitensicherheit und Relais {#dynamic-page-security-and-relays}

Standardmäßig sind alle dynamischen Seiten automatisch mit dem **local** Tomcat-Server des Computers verknüpft, dessen Webmodul gestartet wurde. Diese Konfiguration wird im Abschnitt **`<url>`** der Abfrage-Relaiskonfiguration für die Datei **serverConf.xml** eingegeben.

Sie können die Ausführung der dynamischen Seite auf einem **remote**-Server weiterleiten. wenn das Webmodul auf dem Computer nicht aktiviert ist. Dazu müssen Sie **localhost** durch den Namen des Remote-Computers für JSP und JSSP, Webanwendungen, Berichte und Zeichenfolgen ersetzen.

Weitere Informationen zu den verschiedenen verfügbaren Parametern finden Sie in der Konfigurationsdatei **serverConf.xml**.

Für JSP-Seiten lautet die Standardkonfiguration:

```
<url relayHost="true" relayPath="true" targetUrl="http://localhost:8080" urlPath="*.jsp"/>
```

Adobe Campaign verwendet die folgenden JSP-Seiten:

* /nl/jsp/**soaprouter.jsp**: Client-Konsolen- und Webdienstverbindungen (SOAP-APIs),
* /nl/jsp/**m.jsp**: Mirrorseiten,
* /nl/jsp/**logon.jsp**: Webbasierter Zugriff auf Berichte und die Bereitstellung der Client-Konsole,
* /nl/jsp/**s.jsp** : Einsatz von viralem Marketing (Sponsoring und soziale Netzwerke).

Die für den Mobile App Kanal verwendeten JSSPs lauten wie folgt:

* nms/mobile/1/registerIOS.jssp
* nms/mobile/1/registerAndroid.jssp

**Beispiel:**

Es ist möglich, Clientmaschinenverbindungen von außen zu verhindern. Schränken Sie dazu einfach die Ausführung von **soaprouter.jsp** ein und genehmigen Sie nur die Ausführung von Mirrorseiten, viralen Links, Webformularen und öffentliche Ressourcen.

Die Parameter lauten wie folgt:

```
<url IPMask="<IP_addresses>" deny=""     hostMask="" relayHost="true"  relayPath="true"  targetUrl="http://localhost:8080" timeout="" urlPath="*.jsp"/>
<url IPMask="<IP_addresses>" deny=""     hostMask="" relayHost="true"  relayPath="true"  targetUrl="http://localhost:8080" timeout="" urlPath="*.jssp"/> 
<url IPMask=""               deny=""     hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080" timeout="" urlPath="m.jsp"/>
<url IPMask=""               deny=""     hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080" timeout="" urlPath="s.jsp"/>
<url IPMask=""               deny=""     hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080" timeout="" urlPath="webForm.jsp"/>
<url IPMask=""               deny=""     hostMask="" relayHost="true"  relayPath="true"  targetUrl="http://localhost:8080" timeout="" urlPath="/webApp/pub*"/>
<url IPMask=""               deny=""     hostMask="" relayHost="true"  relayPath="true"  targetUrl="http://localhost:8080" timeout="" urlPath="/jssp/pub*"/>
<url IPMask=""               deny=""     hostMask="" relayHost="true"  relayPath="true"  targetUrl="http://localhost:8080" timeout="" urlPath="/strings/pub*"/>
<url IPMask=""               deny=""     hostMask="" relayHost="true"  relayPath="true"  targetUrl="http://localhost:8080" timeout="" urlPath="/interaction/pub*"/>
<url IPMask=""               deny="true" hostMask="" relayHost="false" relayPath="false" targetUrl="http://localhost:8080" timeout="" urlPath="*.jsp"/>
<url IPMask=""               deny="true" hostMask="" relayHost="false" relayPath="false" targetUrl="http://localhost:8080" timeout="" urlPath="*.jssp"/>
```

In diesem Beispiel fällt der Wert **`<IP_addresses>`** mit der Liste der IP-Adressen (durch Kommas getrennt) zusammen, die zur Verwendung des Relaismoduls für diese Maske berechtigt sind.

>[!NOTE]
>
>Die Werte werden entsprechend Ihrer Konfiguration und Ihren Netzwerkeinschränkungen angepasst, insbesondere, wenn für Ihre Installation spezifische Konfigurationen entwickelt wurden.

### Verwalten von HTTP-Kopfzeilen {#managing-http-headers}

Standardmäßig werden nicht alle HTTP-Header wiedergegeben. Sie können bestimmte Kopfzeilen in den Antworten, die durch Relais gesendet werden, hinzufügen. Gehen Sie dazu wie folgt vor:

1. Wechseln Sie zur Datei **serverConf.xml**.
1. Wechseln Sie im Knoten **`<relay>`** zur Liste der weitergeleiteten HTTP-Header.
1. hinzufügen ein **`<responseheader>`**-Element mit den folgenden Attributen:

   * **name**: Kopfzeilenname
   * **Wert**: Wertname.

   Beispiel:

   ```
   <responseHeader name="Strict-Transport-Security" value="max-age=16070400; includeSubDomains"/>
   ```

## Eingrenzen von autorisierten externen Befehlen {#restricting-authorized-external-commands}

Ab Build 8780 können technische Administratoren die Liste autorisierter externer Befehle einschränken, die in Adobe Campaign verwendet werden können.

Dazu müssen Sie eine Textdatei mit der Liste von Befehlen erstellen, die Sie vermeiden möchten, z. B.:

```
ln
dd
openssl
curl
wget
python
python3
perl
ruby
sh
```

>[!IMPORTANT]
>
>Diese Liste ist nicht erschöpfend.

Im Knoten **exec** der Serverkonfigurationsdatei müssen Sie auf die zuvor erstellte Datei im Attribut **blacklistFile** verweisen.

**Nur** für Linux: in der Serverkonfigurationsdatei sollten Sie einen Benutzer angeben, der externe Befehle ausführen soll, um Ihre Sicherheitskonfiguration zu verbessern. Dieser Benutzer wird im Knoten **exec** der Konfigurationsdatei festgelegt. Alle in **serverConf.xml** verfügbaren Parameter sind in diesem [Abschnitt](../../installation/using/the-server-configuration-file.md) aufgeführt.

>[!NOTE]
>
>Wenn kein Benutzer angegeben ist, werden alle Befehle im Benutzerkontext der Adobe Campaign-Instanz ausgeführt. Der Benutzer muss sich von dem Benutzer, der Adobe Campaign ausführt, unterscheiden.

Beispiel:

```
<serverConf>
 <exec user="theUnixUser" blacklistFile="/pathtothefile/blacklist"/>
</serverConf>
```

Dieser Benutzer muss zur untergeordneten Liste des Adobe Campaign-Operators &quot;neolane&quot;hinzugefügt werden.

>[!IMPORTANT]
>
>Sie sollten kein benutzerdefiniertes Sudo verwenden. Ein Standard-Sudo muss auf dem System installiert sein.


## Redundante Verfolgung {#redundant-tracking}

Werden mehrere Server für die Weiterleitung verwendet, müssen sie über SOAP-Aufrufe miteinander kommunizieren können, um Informationen aus den zu umgeleitenden URLs freizugeben. Zum Zeitpunkt des Beginns des Versands sind möglicherweise nicht alle Umleitungsserver verfügbar; Sie verfügen daher möglicherweise nicht über den gleichen Informationsstand.

>[!NOTE]
>
>Bei Verwendung der Standard- oder Unternehmensarchitektur muss der Hauptanwendungsserver berechtigt sein, Verfolgungsinformationen auf jedem Computer hochzuladen.

Die URLs der redundanten Server müssen in der Umleitungskonfiguration über die Datei **serverConf.xml** angegeben werden.

**Beispiel:**

```
<spareserver enabledIf="$(hostname)!='front_srv1'" id="1" url="http://front_srv1:8080" />
<spareserver enabledIf="$(hostname)!='front_srv2'" id="2" url="http://front_srv2:8080" />
```

Die **enableIf**-Eigenschaft ist optional (standardmäßig leer) und ermöglicht es Ihnen, die Verbindung nur zu aktivieren, wenn das Ergebnis true ist. Auf diese Weise erhalten Sie auf allen Umleitungsservern eine identische Konfiguration.

Um den Hostnamen des Computers abzurufen, führen Sie den folgenden Befehl aus: **hostname -s**.

## Datei- und Ressourcenverwaltung{#file-and-resmanagement}

### Dateiformat für Upload-Dateien begrenzen {#limiting-uploadable-files}

Verwenden Sie das Attribut **uploadWhiteList**, um die Dateitypen einzuschränken, die auf dem Adobe Campaign-Server hochgeladen werden können.

Dieses Attribut ist im Element **dataStore** der Datei **serverConf.xml** verfügbar. Alle in **serverConf.xml** verfügbaren Parameter sind in diesem [Abschnitt](../../installation/using/the-server-configuration-file.md) aufgeführt.

Der Standardwert dieses Attributs ist **.+** und ermöglicht das Hochladen eines beliebigen Dateityps.

Um die möglichen Formate einzuschränken, ersetzen Sie den Attributwert durch einen gültigen regulären Java-Ausdruck. Sie können mehrere Werte eingeben, indem Sie sie durch ein Komma trennen.

Beispiel: **uploadWhiteList=&quot;.*.png,*.jpg&quot;** ermöglicht Ihnen das Hochladen von PNG- und JPG-Formaten auf dem Server. Andere Formate werden nicht akzeptiert.

>[!NOTE]
>
>In Internet Explorer muss der vollständige Dateipfad vom regulären Ausdruck überprüft werden.

Sie können auch verhindern, dass wichtige Dateien hochgeladen werden, indem Sie den Webserver konfigurieren. [Mehr dazu](web-server-configuration.md)

### Proxy-Verbindungskonfiguration {#proxy-connection-configuration}

Sie können den Dateiserver über einen Proxy mit einem externen Kampagne verbinden, indem Sie beispielsweise eine Workflow-Aktivität **Dateiübertragung** verwenden. Um dies zu erreichen, müssen Sie den Abschnitt **proxyConfig** der Datei **serverConf.xml** mithilfe eines bestimmten Befehls konfigurieren. Alle in **serverConf.xml** verfügbaren Parameter sind in diesem [Abschnitt](../../installation/using/the-server-configuration-file.md) aufgeführt.

Die folgenden Proxyverbindungen sind möglich: HTTP, HTTPS, FTP, SFTP. Bitte beachten Sie, dass die HTTP- und HTTPS-Protokollparameter ab Version 20.2 der Kampagne **nicht mehr verfügbar sind**. Diese Parameter werden weiter unten erwähnt, da sie in früheren Builds - einschließlich 9032 - weiterhin verfügbar sind.

>[!CAUTION]
>
>Nur der einfache Authentifizierungsmodus wird unterstützt. Die NTLM-Authentifizierung wird nicht unterstützt.
>
>SOCKS-Proxys werden nicht unterstützt.


Sie können den folgenden Befehl verwenden:

```
nlserver config -setproxy:[protocol]/[serverIP]:[port]/[login][:‘https’|'http’]
```

Protokollparameter können &quot;http&quot;, &quot;https&quot;oder &quot;ftp&quot;lauten.

Wenn Sie FTP für denselben Anschluss wie HTTP/HTTPS-Traffic festlegen, können Sie Folgendes verwenden:

```
nlserver config -setproxy:http/198.51.100.0:8080/user
```

Die Optionen &quot;http&quot;und &quot;https&quot;werden nur verwendet, wenn der Protokollparameter &quot;ftp&quot;ist, und geben an, ob das Tunneln am angegebenen Port über HTTPS oder über HTTP durchgeführt wird.

Wenn Sie verschiedene Anschlüsse für FTP/SFTP und HTTP/HTTPS-Datenverkehr über den Proxyserver verwenden, sollten Sie den FTP-Protokollparameter festlegen.


Beispiel:

```
nlserver config -setproxy:ftp/198.51.100.0:8080/user:’http’
```

Geben Sie dann das Kennwort ein.

HTTP-Verbindungen werden im Parameter proxyHTTP definiert:

```
<proxyConfig enabled=“1” override=“localhost*” useSingleProxy=“0”>
<proxyHTTP address=“198.51.100.0" login=“user” password=“*******” port=“8080”/>
</proxyConfig>
```

HTTPS-Verbindungen werden im Parameter proxyHTTPS definiert:

```
<proxyConfig enabled=“1" override=“localhost*” useSingleProxy=“0">
<proxyHTTPS address=“198.51.100.0” login=“user” password=“******” port=“8080"/>
</proxyConfig>
```

FTP-/FTPS-Verbindungen werden im Parameter proxyFTP definiert:

```
<proxyConfig enabled=“1" override=“localhost*” useSingleProxy=“0">
<proxyFTP address=“198.51.100.0” login=“user” password=“******” port=“5555" https=”true”/>
</proxyConfig>
```

Wenn Sie denselben Proxy für mehrere Verbindungstypen verwenden, wird nur das proxyHTTP mit useSingleProxy auf &quot;1&quot;oder &quot;true&quot;festgelegt.

Wenn Sie interne Verbindungen haben, die durch den Proxy gehen sollen, fügen Sie sie im Parameter override hinzu.

Wenn Sie die Proxyverbindung vorübergehend deaktivieren möchten, setzen Sie den Parameter enabled auf &quot;false&quot;oder &quot;0&quot;.

### Verwalten von öffentliche Ressourcen {#managing-public-resources}

Um öffentlich verfügbar zu sein, müssen die in E-Mails verwendeten Bilder und öffentliche Ressourcen, die mit Kampagnen verknüpft sind, auf einem extern zugänglichen Server vorhanden sein. Sie können dann externen Empfängern oder Operatoren zur Verfügung stehen. [Weitere Informationen](../../installation/using/deploying-an-instance.md#managing-public-resources).

öffentliche Ressourcen werden im Ordner **/var/res/instance** des Installationsordners des Adobe Campaigns gespeichert.

Die passende URL lautet: **http://server/res/instance**, wobei **instance** der Name der Verfolgungsinstanz ist.

Sie können einen anderen Ordner angeben, indem Sie der Datei **conf-`<instance>`.xml** einen Knoten hinzufügen, um die Datenspeicherung auf dem Server zu konfigurieren. Dies bedeutet, dass die folgenden Zeilen hinzugefügt werden:

```
<serverconf>
  <shared>
    <dataStore hosts="media*" lang="fra">
      <virtualDir name="images" path="/var/www/images"/>
     <virtualDir name="publicFileRes" path="$(XTK_INSTALL_DIR)/var/res/$(INSTANCE_NAME)/"/>
    </dataStore>
  </shared>
</serverconf>
```

In diesem Fall sollte die neue URL für die öffentliche Ressourcen im oberen Bereich des Bereitstellungsassistenten auf diesen Ordner verweisen.

## Workflows und Affinitäten mit hoher Verfügbarkeit {#high-availability-workflows-and-affinities}

Sie können mehrere Workflow-Server (wfserver) konfigurieren und auf zwei oder mehr Computern verteilen. Wenn Sie diesen Architekturtyp auswählen, konfigurieren Sie den Verbindungsmodus der Lastenausgleicher entsprechend dem Adobe Campaign-Zugriff.

Für den Zugriff über das Internet wählen Sie den Modus **Lastenausgleich** aus, um die Verbindungszeiten zu begrenzen.

Wählen Sie beim Zugriff über die Adobe Campaign-Konsole den Modus **hash** oder **sticky ip**. Auf diese Weise können Sie die Verbindung zwischen dem Rich-Client und dem Server aufrechterhalten und beispielsweise verhindern, dass eine Benutzersitzung während eines Import- oder Exportvorgangs unterbrochen wird.

Sie können die Ausführung eines Workflows oder einer Workflow-Aktivität auf einem bestimmten Computer erzwingen. Dazu müssen Sie eine oder mehrere Affinitäten für den betreffenden Workflow oder die betreffende Aktivität definieren.

1. Erstellen Sie die Affinitäten des Workflows oder der Aktivität, indem Sie sie in das Feld **[!UICONTROL Affinität]** eingeben.

   Sie können einen beliebigen Affinitäten-Namen wählen, stellen Sie jedoch sicher, dass Sie keine Leerzeichen oder Interpunktionszeichen verwenden. Wenn Sie verschiedene Server verwenden, geben Sie unterschiedliche Namen an.

   ![](assets/s_ncs_install_server_wf_affinity01.png)

   ![](assets/s_ncs_install_server_wf_affinity02.png)

   Die Dropdown-Liste enthält zuvor verwendete Affinitäten. Es wird mit der Zeit mit den verschiedenen eingegebenen Werten abgeschlossen.

1. Öffnen Sie die Datei **nl6/conf/config-`<instance>.xml`**.
1. Ändern Sie die Zeile, die mit dem Modul **[!UICONTROL wfserver]** übereinstimmt, wie folgt:

   ```
   <wfserver autoStart="true" affinity="XXX,"/>
   ```

   Wenn Sie mehrere Affinitäten definieren, müssen diese durch Kommas ohne Leerzeichen getrennt werden:

   ```
   <wfserver autoStart="true" affinity="XXX,YYY,"/>
   ```

   Das Komma nach dem Namen der Affinität ist erforderlich, um Workflows auszuführen, für die keine Affinität definiert ist.

   Wenn Sie nur Workflows ausführen möchten, für die eine Affinität definiert ist, fügen Sie am Ende der Liste Ihrer Affinitäten kein Komma hinzu. Ändern Sie beispielsweise die Zeile wie folgt:

   ```
   <wfserver autoStart="true" affinity="XXX"/>
   ```

## Automatischer Neustart {#automatic-process-restart}

Standardmäßig werden die verschiedenen Adobe Campaign-Prozesse jeden Tag um 6 Uhr (Serverzeit) automatisch neu gestartet.

Sie können diese Konfiguration jedoch ändern.

Gehen Sie dazu zur Datei **serverConf.xml**, die sich im **conf**-Repository Ihrer Installation befindet.

Jeder in dieser Datei konfigurierte Prozess hat das Attribut **processRestartTime**. Sie können den Wert dieses Attributs ändern, um die Startzeit jedes Prozesses entsprechend Ihren Anforderungen anzupassen.

>[!IMPORTANT]
>
>Löschen Sie dieses Attribut nicht. Alle Prozesse müssen jeden Tag neu gestartet werden.
