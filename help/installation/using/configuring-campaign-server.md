---
solution: Campaign Classic
product: campaign
title: Campaign-Server konfigurieren
description: Campaign-Server konfigurieren
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 46c8ed46-0947-47fb-abda-6541b12b6f0c
source-git-commit: bce114f36d1ec4582fc79e750d48155ba0d7cd1f
workflow-type: tm+mt
source-wordcount: '1580'
ht-degree: 2%

---

# Erste Schritte mit der Konfiguration des Campaign-Servers{#gs-campaign-server-config}

In diesem Kapitel werden serverseitige Konfigurationen beschrieben, die entsprechend Ihren Anforderungen und Ihren Umgebungsspezifikationen durchgeführt werden können.

## Einschränkungen

Diese Verfahren sind auf **On-Premise**/**hybride** -Implementierungen beschränkt und erfordern Administratorberechtigungen.

Bei **gehosteten** -Bereitstellungen können serverseitige Einstellungen nur von Adobe konfiguriert werden. Einige Einstellungen können jedoch innerhalb von [Campaign Control Panel](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/key-features.html) eingerichtet werden, z. B. die Verwaltung von IP-Zulassungslisten oder URL-Berechtigungen. [Weitere Informationen](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/ip-allow-listing-instance-access.html).

Weitere Informationen finden Sie in den folgenden Abschnitten:

* [Control Panel-Dokumentation](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=de)
* [Hosting-Modelle](../../installation/using/hosting-models.md)
* [Funktionsmatrix für On-Premise- und gehostete Campaign Classic-Versionen](../../installation/using/capability-matrix.md)

## Konfigurationsdateien

Campaign Classic-Konfigurationsdateien werden im Ordner **conf** des Adobe Campaign-Installationsordners gespeichert. Die Konfiguration umfasst zwei Dateien:

* **serverConf.xml**: allgemeine Konfiguration für alle Instanzen. Diese Datei kombiniert die technischen Parameter des Adobe Campaign-Servers: Diese werden von allen Instanzen gemeinsam genutzt. Die Beschreibung einiger dieser Parameter wird nachfolgend beschrieben. Die verschiedenen Knoten und Parameter, die in diesem Abschnitt [Abschnitt](../../installation/using/the-server-configuration-file.md) aufgeführt sind.
* **config-`<instance>`.xml**  (wobei  **** instanceName der Instanz ist): spezifische Konfiguration der Instanz. Wenn Sie Ihren Server auf mehrere Instanzen aufteilen, geben Sie die für jede Instanz spezifischen Parameter in die entsprechende Datei ein.

## Konfigurationsbereich

Konfigurieren oder passen Sie den Campaign-Server entsprechend Ihren Anforderungen und Ihrer Konfiguration an. Sie haben folgende Möglichkeiten:

* Sichern Sie die [Interne Kennung](#internal-identifier).
* [Kampagnenprozesse](#enabling-processes) aktivieren
* [URL-Berechtigungen](url-permissions.md) konfigurieren
* Definieren Sie [Sicherheitszonen](security-zones.md)
* [Tomcat-Einstellungen](configure-tomcat.md) konfigurieren
* [Versandparameter](configure-delivery-settings.md) anpassen
* Definieren Sie [Dynamische Seitensicherheit und Relais](#dynamic-page-security-and-relays)
* Schränken Sie die Liste der zulässigen externen Befehle [a1/> ein.](#restricting-authorized-external-commands)
* [Redundantes Tracking](#redundant-tracking) einrichten
* Verwalten Sie [Hohe Verfügbarkeit und Workflow-Affinitäten](#high-availability-workflows-and-affinities)
* Dateiverwaltung konfigurieren - [Weitere Informationen](file-res-management.md)
   * Format für Upload-Dateien begrenzen
   * Zugriff auf öffentliche Ressourcen aktivieren
   * Proxy-Verbindung konfigurieren
* [Automatischer Prozess-Neustart](#automatic-process-restart)


## Interne Kennung {#internal-identifier}

Die **internal**-Kennung ist ein technisches Login, das für Installations-, Administrations- und Wartungszwecke verwendet wird. Diese Anmeldung ist keiner Instanz zugeordnet.

Benutzer, die mit dieser Anmeldung verbunden sind, haben alle Rechte auf allen Instanzen. Bei einer Neuinstallation wird dieses Login kein Passwort enthalten. Sie müssen dieses Kennwort manuell definieren.

Verwenden Sie den folgenden Befehl:

```
nlserver config -internalpassword
```

Die folgenden Informationen werden angezeigt. Geben Sie das Kennwort ein und bestätigen Sie es:

```
17:33:57 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
Enter the current password.
Password:
Enter the new password.
Password: XXXX
Confirmation: XXXX
17:34:02 >   Password successfully changed for account 'internal' (authentication mode 'nl')
```

## Prozesse aktivieren {#enabling-processes}

Adobe Campaign-Prozesse auf dem Server sind über die Dateien **config-default.xml** und **`config-<instance>.xml`** aktiviert (und deaktiviert).

Um die Änderungen auf diese Dateien anzuwenden, müssen Sie beim Starten des Adobe Campaign-Dienstes den Befehl **nlserver config -reload** ausführen.

Es gibt zwei Arten von Prozessen: mehrere Instanzen und eine einzelne Instanz.

* **mehrere Instanzen**: Ein einzelner Prozess wird für alle Instanzen gestartet. Dies gilt für die Prozesse **web**, **syslogd** und **trackinglogd**.

   Die Aktivierung kann über die Datei **config-default.xml** konfiguriert werden.

   Deklarieren eines Adobe Campaign-Servers für den Zugriff auf Clientkonsolen und für die Weiterleitung (Tracking):

   ```
   vi nl6/conf/config-default.xml
   <web args="-tomcat" autoStart="true"/>  
   <!-- to start if the machine is also a redirection server -->  
   <trackinglogd autoStart="true"/>
   ```

   In diesem Beispiel wird die Datei unter Linux mit einem **vi**-Befehl bearbeitet. Sie kann mit einem beliebigen **.txt**- oder **.xml**-Editor bearbeitet werden.

* **Mono-Instanz**: Für jede Instanz wird ein Prozess gestartet (Module:  **mta**,  **wfserver**,  **inMail**,  **** smsand  **stat**).

   Die Aktivierung kann mithilfe der Konfigurationsdatei der Instanz konfiguriert werden:

   ```
   config-<instance>.xml
   ```

   Deklarieren eines Servers für den Versand, Ausführen von Workflow-Instanzen und Wiederherstellen von Bounce Messages:

   ```
   <mta autoStart="true" statServerAddress="localhost"/>
   <wfserver autoStart="true"/>  
   <inMail autoStart="true"/>
   <stat autoStart="true"/>
   ```

**Datenspeicherung in Campaign**

Sie können den Speicherordner (**var** -Ordner) der Adobe Campaign-Daten (Protokolle, Downloads, Weiterleitungen usw.) konfigurieren. Verwenden Sie dazu die Systemvariable **XTK_VAR_DIR**:

* Geben Sie unter Windows den folgenden Wert in der Systemvariable **XTK_VAR_DIR** an

   ```
   D:\log\AdobeCampaign
   ```

* Wechseln Sie unter Linux zur Datei **customer.sh** und geben Sie Folgendes an: **export XTK_VAR_DIR=/app/log/AdobeCampaign**.

   Weitere Informationen hierzu finden Sie unter [Parameter personalisieren](../../installation/using/installing-packages-with-linux.md#personalizing-parameters).


## Dynamische Seitensicherheit und Relais {#dynamic-page-security-and-relays}

Standardmäßig sind alle dynamischen Seiten automatisch mit dem **lokalen** Tomcat-Server des Computers verbunden, dessen Webmodul gestartet wurde. Diese Konfiguration wird im Abschnitt **`<url>`** der Query Relais-Konfiguration für die Datei **ServerConf.xml** eingegeben.

Sie können die Ausführung der dynamischen Seite auf einem **Remote**-Server weiterleiten. wenn das Webmodul auf dem Computer nicht aktiviert ist. Dazu müssen Sie **localhost** durch den Namen des Remote-Computers für JSP und JSSP, Webanwendungen, Berichte und Zeichenfolgen ersetzen.

Weiterführende Informationen zu den verfügbaren Parametern finden Sie in der Konfigurationsdatei **serverConf.xml** .

Für JSP-Seiten lautet die Standardkonfiguration:

```
<url relayHost="true" relayPath="true" targetUrl="http://localhost:8080" urlPath="*.jsp"/>
```

Adobe Campaign verwendet die folgenden JSP-Seiten:

* /nl/jsp/**soaprouter.jsp**: Clientkonsole und Webdienstverbindungen (SOAP-APIs),
* /nl/jsp/**m.jsp**: Mirrorseiten,
* /nl/jsp/**logon.jsp**: Webbasierter Zugriff auf Berichte und die Bereitstellung der Clientkonsole,
* /nl/jsp/**s.jsp** : Verwendung von viralem Marketing (Sponsoring und soziale Netzwerke).

Die für den Mobile-App-Kanal verwendeten JSSPs lauten wie folgt:

* nms/mobile/1/registerIOS.jssp
* nms/mobile/1/registerAndroid.jssp

**Beispiel:**

Es ist möglich, Clientmaschinenverbindungen von außen zu verhindern. Schränken Sie dazu einfach die Ausführung von **soaprouter.jsp** ein und genehmigen Sie nur die Ausführung von Mirrorseiten, viralen Links, Webformularen und öffentlichen Ressourcen.

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

In diesem Beispiel entspricht der Wert **`<IP_addresses>`** der Liste der IP-Adressen (getrennt durch Kommas), die zur Verwendung des Relais-Moduls für diese Maske berechtigt sind.

>[!NOTE]
>
>Die Werte sind entsprechend Ihrer Konfiguration und Ihren Netzwerkbeschränkungen anzupassen, insbesondere wenn für Ihre Anlage spezifische Konfigurationen entwickelt wurden.

### Verwalten von HTTP-Headern {#managing-http-headers}

Standardmäßig werden nicht alle HTTP-Header weitergeleitet. Sie können bestimmte Header zu den Antworten hinzufügen, die per Relais gesendet werden. Gehen Sie dazu wie folgt vor:

1. Wechseln Sie zur Datei **serverConf.xml** .
1. Navigieren Sie im Knoten **`<relay>`** zur Liste der wiedergegebenen HTTP-Header.
1. Fügen Sie ein **`<responseheader>`** -Element mit den folgenden Attributen hinzu:

   * **name**: Kopfzeilenname
   * **Wert**: Wertname.

   Beispiel:

   ```
   <responseHeader name="Strict-Transport-Security" value="max-age=16070400; includeSubDomains"/>
   ```

## Einschränken autorisierter externer Befehle {#restricting-authorized-external-commands}

Ab Build 8780 können technische Administratoren die Liste zulässiger externer Befehle einschränken, die in Adobe Campaign verwendet werden können.

Dazu müssen Sie eine Textdatei mit der Liste der Befehle erstellen, die Sie verhindern möchten, z. B.:

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
>Diese Liste ist nicht vollständig.

Im Knoten **exec** der Server-Konfigurationsdatei müssen Sie auf die zuvor erstellte Datei im Attribut **blacklistFile** verweisen.

**Nur** für Linux: in der Server-Konfigurationsdatei angeben, empfehlen wir, einen Benutzer für die Ausführung externer Befehle anzugeben, um Ihre Sicherheitskonfiguration zu verbessern. Dieser Benutzer wird im Knoten **exec** der Konfigurationsdatei festgelegt. Alle in **serverConf.xml** verfügbaren Parameter sind in diesem [Abschnitt](../../installation/using/the-server-configuration-file.md) aufgeführt.

>[!NOTE]
>
>Wenn kein Benutzer angegeben ist, werden alle Befehle im Benutzerkontext der Adobe Campaign-Instanz ausgeführt. Der Benutzer muss sich von dem Benutzer unterscheiden, der Adobe Campaign ausführt.

Beispiel:

```
<serverConf>
 <exec user="theUnixUser" blacklistFile="/pathtothefile/blacklist"/>
</serverConf>
```

Dieser Benutzer muss zur Unterliste des Adobe Campaign-Operators &quot;neolane&quot;hinzugefügt werden.

>[!IMPORTANT]
>
>Sie sollten kein benutzerdefiniertes Sudo verwenden. Auf dem System muss ein Standardsudo installiert sein.


## Redundantes Tracking {#redundant-tracking}

Wenn mehrere Server für die Weiterleitung verwendet werden, müssen sie über SOAP-Aufrufe miteinander kommunizieren können, um Informationen über die URLs freizugeben, die umgeleitet werden sollen. Zum Zeitpunkt des Starts des Versands ist es möglich, dass nicht alle Weiterleitungsserver verfügbar sind. Sie verfügen daher möglicherweise nicht über den gleichen Informationsstand.

>[!NOTE]
>
>Bei Verwendung der Standard- oder Unternehmensarchitektur muss der Hauptanwendungsserver berechtigt sein, Tracking-Informationen auf jeden Computer hochzuladen.

Die URLs der redundanten Server müssen in der Umleitungskonfiguration über die Datei **serverConf.xml** angegeben werden.

**Beispiel:**

```
<spareserver enabledIf="$(hostname)!='front_srv1'" id="1" url="http://front_srv1:8080" />
<spareserver enabledIf="$(hostname)!='front_srv2'" id="2" url="http://front_srv2:8080" />
```

Die Eigenschaft **enableIf** ist optional (standardmäßig leer) und ermöglicht es Ihnen, die Verbindung nur zu aktivieren, wenn das Ergebnis wahr ist. Auf diese Weise erhalten Sie auf allen Weiterleitungsservern eine identische Konfiguration.

Um den Hostnamen des Computers abzurufen, führen Sie den folgenden Befehl aus: **hostname -s**.



## Workflows und Affinitäten mit hoher Verfügbarkeit {#high-availability-workflows-and-affinities}

Sie können mehrere Workflow-Server (wfserver) konfigurieren und auf zwei oder mehr Computern verteilen. Wenn Sie diesen Architekturtyp auswählen, konfigurieren Sie den Verbindungsmodus der Lastenausgleichsmodule entsprechend dem Adobe Campaign-Zugriff.

Wählen Sie für den Zugriff über das Internet den Modus **Load Balancer** aus, um die Verbindungszeiten zu begrenzen.

Wählen Sie beim Zugriff über die Adobe Campaign-Konsole den Modus **hash** oder **sticky ip**. Dadurch können Sie die Verbindung zwischen dem Rich-Client und dem Server beibehalten und verhindern, dass eine Benutzersitzung beispielsweise während eines Import- oder Exportvorgangs unterbrochen wird.

Sie können die Ausführung eines Workflows oder einer Workflow-Aktivität auf einem bestimmten Computer erzwingen. Hierzu müssen Sie eine oder mehrere Affinitäten für den betreffenden Workflow oder die betreffende Aktivität definieren.

1. Erstellen Sie die Affinitäten des Workflows oder der Aktivität, indem Sie sie in das Feld **[!UICONTROL Affinität]** eingeben.

   Sie können einen beliebigen Affinitätsnamen wählen, stellen Sie jedoch sicher, dass Sie keine Leerzeichen oder Satzzeichen verwenden. Wenn Sie verschiedene Server verwenden, geben Sie unterschiedliche Namen an.

   ![](assets/s_ncs_install_server_wf_affinity01.png)

   ![](assets/s_ncs_install_server_wf_affinity02.png)

   Die Dropdown-Liste enthält zuvor verwendete Affinitäten. Sie wird mit der Zeit mit den verschiedenen eingegebenen Werten ergänzt.

1. Öffnen Sie die Datei **nl6/conf/config-`<instance>.xml`** .
1. Ändern Sie die Zeile, die mit dem Modul **[!UICONTROL wfserver]** übereinstimmt, wie folgt:

   ```
   <wfserver autoStart="true" affinity="XXX,"/>
   ```

   Wenn Sie mehrere Affinitäten definieren, müssen diese durch Kommas ohne Leerzeichen getrennt werden:

   ```
   <wfserver autoStart="true" affinity="XXX,YYY,"/>
   ```

   Das Komma, das dem Namen der Affinität folgt, ist für die Ausführung von Workflows erforderlich, für die keine Affinität definiert ist.

   Wenn Sie nur Workflows ausführen möchten, für die eine Affinität definiert ist, fügen Sie am Ende der Liste Ihrer Affinitäten kein Komma hinzu. Ändern Sie beispielsweise die Zeile wie folgt:

   ```
   <wfserver autoStart="true" affinity="XXX"/>
   ```

## Automatischer Neustart {#automatic-process-restart}

Standardmäßig werden die verschiedenen Adobe Campaign-Prozesse täglich um 6 Uhr (Serverzeit) automatisch neu gestartet.

Sie können diese Konfiguration jedoch ändern.

Wechseln Sie dazu zur Datei **serverConf.xml** im Repository **conf** Ihrer Installation.

Jeder in dieser Datei konfigurierte Prozess hat ein **processRestartTime** -Attribut. Sie können den Wert dieses Attributs ändern, um die Startzeit jedes Prozesses entsprechend Ihren Anforderungen anzupassen.

>[!IMPORTANT]
>
>Löschen Sie dieses Attribut nicht. Alle Prozesse müssen täglich neu gestartet werden.
