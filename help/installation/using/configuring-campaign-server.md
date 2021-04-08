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
source-git-commit: 0c83c989c7e3718a989a4943f5cde7ad4717fddc
workflow-type: tm+mt
source-wordcount: '2812'
ht-degree: 8%

---

# Campaign-Server konfigurieren{#configuring-campaign-server}

Im folgenden Abschnitt werden serverseitige Konfigurationen beschrieben, die entsprechend Ihren Anforderungen und Ihren Umgebung durchgeführt werden können.

Diese Konfigurationen müssen von Administratoren und nur für Hostingmodelle von **On-Premise** durchgeführt werden.

Bei **Hosted**-Bereitstellungen können serverseitige Einstellungen nur durch Adobe konfiguriert werden. Einige Einstellungen können jedoch in der Systemsteuerung eingerichtet werden (z. B. IP-Zulassungsliste-Management oder URL-Berechtigungen).

>[!NOTE]
>
>Das Control Panel steht allen Administratoren zur Verfügung. Die Schritte, um einem Benutzer Administratorzugriff zu gewähren, finden Sie in [diesem Abschnitt](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=de#discover-control-panel).
>
>Beachten Sie, dass Ihre Instanz auf AWS gehostet und mit dem neuesten [Gold Standard](../../rn/using/gs-overview.md) Build oder dem [neuesten GA-Build (21.1)](../../rn/using/latest-release.md) aktualisiert werden muss. Erfahren Sie, wie Sie Ihre Version in [diesem Abschnitt](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version) überprüfen. Um zu überprüfen, ob Ihre Instanz auf AWS gehostet wird, führen Sie die unter [Diese Seite](https://experienceleague.adobe.com/docs/control-panel/using/faq.html) beschriebenen Schritte aus.

Weitere Informationen finden Sie in den folgenden Abschnitten:

* [Control Panel-Dokumentation](https://docs.adobe.com/content/help/de-DE/control-panel/using/control-panel-home.html)
* [Hosting-Modelle](../../installation/using/hosting-models.md)
* [Campaign Classic-On-Premise- und gehostete Funktionsmatrix](../../installation/using/capability-matrix.md)
* [Konfigurationsschritte für Hybrid- und gehostete Modelle](../../installation/using/hosting-models.md)

Campaign Classic-Konfigurationsdateien werden im Ordner **conf** des Adobe Campaign-Installationsordners gespeichert. Die Konfiguration erstreckt sich über zwei Dateien:

* **serverConf.xml**: allgemeine Konfiguration für alle Instanzen. Diese Datei enthält die technischen Parameter des Adobe Campaign-Servers: diese werden von allen Instanzen freigegeben. Die Beschreibung einiger dieser Parameter ist nachfolgend beschrieben. Die verschiedenen Knoten und Parameter, die in diesem [Abschnitt](../../installation/using/the-server-configuration-file.md) aufgeführt sind.
* **config-`<instance>`.xml** (wobei  **** instanceis der Name der Instanz ist): spezifische Konfiguration der Instanz. Wenn Sie Ihren Server für mehrere Instanzen freigeben, geben Sie bitte die für jede Instanz spezifischen Parameter in die entsprechende Datei ein.

## Tomcat {#configuring-tomcat} konfigurieren

### Standardanschluss für Tomcat {#default-port-for-tomcat}

Wenn der 8080-Listening-Anschluss des Tomcat-Servers bereits mit einer anderen Anwendung besetzt ist, die für Ihre Konfiguration erforderlich ist, müssen Sie den 8080-Port durch einen kostenlosen ersetzen (z. B. 8090). Um sie zu ändern, bearbeiten Sie die Datei **server.xml**, die im Ordner **/tomcat-8/conf** des Installationsordners des Adobe Campaigns gespeichert ist.

Ändern Sie dann den Anschluss der JSP-Relaisseiten. Ändern Sie dazu die Datei **serverConf.xml**, die im Ordner **/conf** des Installationsordners des Adobe Campaigns gespeichert ist. Alle in **serverConf.xml** verfügbaren Parameter sind in diesem [Abschnitt](../../installation/using/the-server-configuration-file.md) aufgeführt.

```
<serverConf>
   ...
   <web controlPort="8005" httpPort="8090"...
   <url ... targetUrl="http://localhost:8090"...
```

### Zuordnen eines Ordners in Tomcat {#mapping-a-folder-in-tomcat}

Um kundenspezifische Einstellungen zu definieren, können Sie eine Datei **user_Kontexte.xml** im Ordner **/tomcat-8/conf** erstellen, die auch die Datei **Kontexte.xml** enthält.

Diese Datei enthält die folgenden Informationen:

```
 <Context path='/foo' docBase='../customers/foo'   crossContext='true' debug='0' reloadable='true' trusted='false'/>
```

Bei Bedarf kann dieser Vorgang serverseitig reproduziert werden.

## Personalisieren von Versand-Parametern {#personalizing-delivery-parameters}

Die Versand-Parameter werden in der Konfigurationsdatei **serverConf.xml** definiert. Alle in **serverConf.xml** verfügbaren Parameter sind in diesem [Abschnitt](../../installation/using/the-server-configuration-file.md) aufgeführt.

Allgemeine Serverkonfiguration und -befehle finden Sie unter [Kampagne-Serverkonfiguration](../../installation/using/campaign-server-configuration.md).

Je nach Bedarf und Einstellungen können Sie außerdem die folgenden Konfigurationen durchführen.

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

Es ist möglich, die Population von untergeordneten Prozessen (maxSpareServers standardmäßig 2) zu steuern, um die Übertragungsleistung entsprechend der CPU-Leistung der Server und der verfügbaren Netzwerkressourcen zu optimieren. Diese Konfiguration ist auf jedem einzelnen Computer im Abschnitt **`<master>`** der MTA-Konfiguration vorzunehmen.

```
<master dataBasePoolPeriodSec="30" dataBaseRetryDelaySec="60" maxSpareServers="2" minSpareServers="0" startSpareServers="0">
```

Siehe auch [Optimierung des E-Mail-Versands](../../installation/using/email-deliverability.md#email-sending-optimization).

### Verwalten des ausgehenden SMTP-Traffics mit Affinitäten {#managing-outbound-smtp-traffic-with-affinities}

>[!IMPORTANT]
>
>Die Konfiguration der Affinität muss von einem Server zum anderen kohärent sein. Es wird empfohlen, sich für die Konfiguration der Affinität an die Adobe zu wenden, da Konfigurationsänderungen auf allen Anwendungsservern, auf denen die MTA ausgeführt wird, repliziert werden sollten.

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

## URL-Genehmigungen {#url-permissions}

Die Liste der URLs, die standardmäßig von JavaScript-Codes (Workflows usw.) über Ihre Campaign Classic-Instanzen aufgerufen werden können, ist begrenzt. Diese URLs ermöglichen das ordnungsgemäße Funktionieren der Instanzen.

Standardmäßig sind Instanzen nicht berechtigt, eine Verbindung zu externen URLs herzustellen. Es ist jedoch möglich, einige externe URLs zur Liste autorisierter URLs hinzuzufügen, damit Ihre Instanz eine Verbindung zu ihnen herstellen kann. Dadurch können Sie zwischen Ihren Campaign-Instanzen und externen Systemen, wie z. B. SFTP-Servern oder Websites, eine Verbindung herstellen, um den Datei- und/oder Datentransfer zu ermöglichen.

Nach dem Hinzufügen einer URL wird sie in der Konfigurationsdatei der Instanz referenziert (serverConf.xml).

Wie Sie URL-Berechtigungen verwalten können, hängt von Ihrem Hostmodell ab:

* **** Hybridor  **vor Ort**: fügen Sie die URLs hinzu, die in der Datei  **&quot;serverConf.xml&quot;zulässig sind**. Ausführliche Informationen finden Sie im folgenden Abschnitt.
* **gehostet**: fügen Sie die URLs hinzu, die über die  **Systemsteuerung** zulässig sind. Weitere Informationen finden Sie in der [entsprechenden Dokumentation](https://docs.adobe.com/content/help/de-DE/control-panel/using/instances-settings/url-permissions.html).

   >[!NOTE]
   >
   >Das Control Panel steht allen Administratoren zur Verfügung. Die Schritte, um einem Benutzer Administratorzugriff zu gewähren, finden Sie in [diesem Abschnitt](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=en#discover-control-panel).
   >
   >Beachten Sie, dass Ihre Instanz auf AWS gehostet und mit dem neuesten [Gold Standard](../../rn/using/gs-overview.md) Build aktualisiert werden muss. Erfahren Sie, wie Sie Ihre Version in [diesem Abschnitt](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version) überprüfen. Um zu überprüfen, ob Ihre Instanz auf AWS gehostet wird, führen Sie die unter [Diese Seite](https://experienceleague.adobe.com/docs/control-panel/using/faq.html) beschriebenen Schritte aus.

Bei den Hostmodellen **Hybrid** und **On-Premise** muss der Administrator auf eine neue **urlPermission** in der Datei **serverConf.xml** verweisen. Alle in **serverConf.xml** verfügbaren Parameter sind in diesem [Abschnitt](../../installation/using/the-server-configuration-file.md) aufgeführt.

Es gibt drei Modi für den Verbindungsschutz:

* **Blockierung**: alle URLs, die nicht zur Zulassungsliste gehören, werden mit einer Fehlermeldung blockiert. Dies ist der Standardmodus nach einem Postupgrade.
* **Zulässig**: alle URLs, die nicht zur Zulassungsliste gehören, sind zulässig.
* **Warnung**: alle URLs, die nicht zur Zulassungsliste gehören, sind zulässig, der JS-Interpreter gibt jedoch eine Warnung aus, sodass der Administrator sie erfassen kann. In diesem Modus werden Warnmeldungen für JST-310027 hinzugefügt.

```
<urlPermission action="warn" debugTrace="true">
  <url dnsSuffix="abc.company1.com" urlRegEx=".*" />
  <url dnsSuffix="def.partnerA_company1.com" urlRegEx=".*" />
  <url dnsSuffix="xyz.partnerB_company1.com" urlRegEx=".*" />
</urlPermission>
```

>[!IMPORTANT]
>
>Der Client neuer Kunden verwendet standardmäßig den Blockiermodus **a1/>.** Wenn sie eine neue URL zulassen müssen, sollten sie sich an ihren Administrator wenden, um sie der Zulassungsliste hinzuzufügen.
>
>Vorhandene Kunden, die aus einer Migration kommen, können den **Warnungsmodus** für eine Weile verwenden. In der Zwischenzeit müssen sie den ausgehenden Traffic analysieren, bevor sie die URLs autorisieren. Sobald die Liste autorisierter URLs definiert ist, sollten sie sich an ihren Administrator wenden, um die URLs zur Zulassungsliste hinzuzufügen und den **Blockierungsmodus** zu aktivieren.

## Dynamische Seitensicherheit und Relais {#dynamic-page-security-and-relays}

Standardmäßig sind alle dynamischen Seiten automatisch mit dem **local** Tomcat-Server des Computers verknüpft, dessen Webmodul gestartet wurde. Diese Konfiguration wird im Abschnitt **`<url>`** der Abfrage-Relaiskonfiguration für die Datei **serverConf.xml** eingegeben. Alle in **serverConf.xml** verfügbaren Parameter sind in diesem [Abschnitt](../../installation/using/the-server-configuration-file.md) aufgeführt.

So übertragen Sie die Ausführung der dynamischen Seite auf einem **remote**-Server wenn das Webmodul auf dem Computer nicht aktiviert ist. Dazu müssen Sie **localhost** durch den Namen des Remote-Computers für JSP und JSSP, Webanwendungen, Berichte und Zeichenfolgen ersetzen.

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

## Eingrenzen autorisierter externer Befehle {#restricting-authorized-external-commands}

>[!NOTE]
>
>Die folgende Konfiguration ist nur für lokale Installationen erforderlich.

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

## Verwalten von HTTP-Kopfzeilen {#managing-http-headers}

Standardmäßig werden nicht alle HTTP-Header wiedergegeben. Sie können bestimmte Kopfzeilen in den Antworten, die durch Relais gesendet werden, hinzufügen. Gehen Sie dazu wie folgt vor:

1. Wechseln Sie zur Datei **serverConf.xml**. Alle in **serverConf.xml** verfügbaren Parameter sind in diesem [Abschnitt](../../installation/using/the-server-configuration-file.md) aufgeführt.
1. Wechseln Sie im Knoten **`<relay>`** zur Liste der weitergeleiteten HTTP-Header.
1. hinzufügen ein **`<responseheader>`**-Element mit den folgenden Attributen:

   * **name**: Kopfzeilenname
   * **Wert**: Wertname.

   Beispiel:

   ```
   <responseHeader name="Strict-Transport-Security" value="max-age=16070400; includeSubDomains"/>
   ```

## Redundante Verfolgung {#redundant-tracking}

Werden mehrere Server für die Weiterleitung verwendet, müssen sie über SOAP-Aufrufe miteinander kommunizieren können, um Informationen aus den zu umgeleitenden URLs freizugeben. Zum Zeitpunkt des Beginns des Versands sind möglicherweise nicht alle Umleitungsserver verfügbar; Sie verfügen daher möglicherweise nicht über den gleichen Informationsstand.

>[!NOTE]
>
>Bei Verwendung der Standard- oder Unternehmensarchitektur muss der Hauptanwendungsserver berechtigt sein, Verfolgungsinformationen auf jedem Computer hochzuladen.

Die URLs der redundanten Server müssen in der Umleitungskonfiguration über die Datei **serverConf.xml** angegeben werden. Alle in **serverConf.xml** verfügbaren Parameter sind in diesem [Abschnitt](../../installation/using/the-server-configuration-file.md) aufgeführt.

**Beispiel:**

```
<spareserver enabledIf="$(hostname)!='front_srv1'" id="1" url="http://front_srv1:8080" />
<spareserver enabledIf="$(hostname)!='front_srv2'" id="2" url="http://front_srv2:8080" />
```

Die **enableIf**-Eigenschaft ist optional (standardmäßig leer) und ermöglicht es Ihnen, die Verbindung nur zu aktivieren, wenn das Ergebnis true ist. Auf diese Weise erhalten Sie auf allen Umleitungsservern eine identische Konfiguration.

Um den Hostnamen des Computers abzurufen, führen Sie den folgenden Befehl aus: **hostname -s**.

## Verwalten von öffentliche Ressourcen {#managing-public-resources}

öffentliche Ressourcen finden Sie unter [Verwalten von öffentliche Ressourcen](../../installation/using/deploying-an-instance.md#managing-public-resources).

Sie werden im Ordner **/var/res/instance** des Installationsordners des Adobe Campaigns gespeichert.

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

   Sie können die Affinitäten frei wählen. Achten Sie jedoch darauf, keine Leerzeichen oder Satzzeichen zu verwenden. Wenn Sie verschiedene Server verwenden, geben Sie unterschiedliche Namen an.

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

## Automatischer Prozess-Neustart {#automatic-process-restart}

Standardmäßig werden die verschiedenen Adobe Campaign-Prozesse jeden Tag um 6 Uhr (Serverzeit) automatisch neu gestartet.

Sie können diese Konfiguration jedoch ändern.

Gehen Sie dazu zur Datei **serverConf.xml**, die sich im **conf**-Repository Ihrer Installation befindet. Alle in **serverConf.xml** verfügbaren Parameter sind in diesem [Abschnitt](../../installation/using/the-server-configuration-file.md) aufgeführt.

Jeder in dieser Datei konfigurierte Prozess hat das Attribut **processRestartTime**. Sie können den Wert dieses Attributs ändern, um die Startzeit jedes Prozesses entsprechend Ihren Anforderungen anzupassen.

>[!IMPORTANT]
>
>Löschen Sie dieses Attribut nicht. Alle Prozesse müssen jeden Tag neu gestartet werden.

## Beschränkungen für hochladbare Dateien {#limiting-uploadable-files}

Mit dem neuen Attribut **uploadWhiteList** können Sie die Dateitypen einschränken, die auf dem Adobe Campaign-Server hochgeladen werden können.

Dieses Attribut ist im Element **dataStore** der Datei **serverConf.xml** verfügbar. Alle in **serverConf.xml** verfügbaren Parameter sind in diesem [Abschnitt](../../installation/using/the-server-configuration-file.md) aufgeführt.

Der Standardwert dieses Attributs ist **.+** und es ermöglicht Ihnen, jeden Dateityp hochzuladen.

Um die möglichen Formate einzuschränken, müssen Sie den Attributwert durch einen gültigen regulären Java-Ausdruck ersetzen. Sie können mehrere Werte eingeben, indem Sie sie durch ein Komma trennen.

Beispiel: **uploadWhiteList=&quot;.*.png,*.jpg&quot;** ermöglicht Ihnen das Hochladen von PNG- und JPG-Formaten auf dem Server. Andere Formate werden nicht akzeptiert.

>[!IMPORTANT]
>
>In Internet Explorer muss der vollständige Dateipfad vom regulären Ausdruck überprüft werden.

## Proxy-Verbindungskonfiguration {#proxy-connection-configuration}

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
