---
product: campaign
title: Campaign-Server konfigurieren
description: Campaign-Server konfigurieren
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 46c8ed46-0947-47fb-abda-6541b12b6f0c
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '1580'
ht-degree: 3%

---

# Erste Schritte mit der Campaign-Serverkonfiguration{#gs-campaign-server-config}



In diesem Kapitel werden serverseitige Konfigurationen beschrieben, die entsprechend Ihren Anforderungen und Ihren Umgebungsspezifikationen durchgeführt werden können.

## Einschränkungen

Diese Verfahren beschränken sich auf **On-Premise**/**hybrid** Implementierungen und erfordern Administratorberechtigungen.

Für **gehostet** -Bereitstellungen können nur von Adobe konfiguriert werden. Einige Einstellungen können jedoch in [Campaign Control Panel](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/key-features.html?lang=de), wie die Verwaltung von IP-Zulassungslisten oder URL-Berechtigungen. [Weitere Informationen](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/ip-allow-listing-instance-access.html?lang=de).

Weitere Informationen finden Sie in den folgenden Abschnitten:

* [Control Panel-Dokumentation](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=de)
* [Hosting-Modelle](../../installation/using/hosting-models.md)
* [Funktionsmatrix für On-Premise- und gehostete Campaign Classic-Versionen](../../installation/using/capability-matrix.md)

## Konfigurationsdateien

Campaign Classic-Konfigurationsdateien werden im **conf** Ordner des Adobe Campaign-Installationsordners. Die Konfiguration umfasst zwei Dateien:

* **serverConf.xml**: allgemeine Konfiguration für alle Instanzen. Diese Datei kombiniert die technischen Parameter des Adobe Campaign-Servers: Diese werden von allen Instanzen gemeinsam genutzt. Die Beschreibung einiger dieser Parameter wird nachfolgend beschrieben. Die verschiedenen Knoten und Parameter, die in diesem [Abschnitt](../../installation/using/the-server-configuration-file.md).
* **config-`<instance>`.xml** , **instance** ist der Name der Instanz): spezifische Konfiguration der Instanz. Wenn Sie Ihren Server auf mehrere Instanzen aufteilen, geben Sie die für jede Instanz spezifischen Parameter in die entsprechende Datei ein.

## Konfigurationsbereich

Konfigurieren oder passen Sie den Campaign-Server entsprechend Ihren Anforderungen und Ihrer Konfiguration an. Sie haben folgende Möglichkeiten:

* Sichern Sie die [Interne Kennung](#internal-identifier)
* Aktivieren [Kampagnenprozesse](#enabling-processes)
* Konfigurieren [URL-Berechtigungen](url-permissions.md)
* Definieren [Sicherheitszonen](security-zones.md)
* Konfigurieren [Tomcat-Einstellungen](configure-tomcat.md)
* Anpassen [Versandparameter](configure-delivery-settings.md)
* Definieren [Dynamische Seitensicherheit und Relais](#dynamic-page-security-and-relays)
* Schränken Sie die Liste der [Zulässige externe Befehle](#restricting-authorized-external-commands)
* Einrichten [Redundantes Tracking](#redundant-tracking)
* Verwalten [Hohe Verfügbarkeit und Workflow-Affinitäten](#high-availability-workflows-and-affinities)
* Konfigurieren der Dateiverwaltung - [Weitere Infos](file-res-management.md)
   * Format für Upload-Dateien begrenzen
   * Zugriff auf öffentliche Ressourcen aktivieren
   * Proxy-Verbindung konfigurieren
* [Automatischer Prozess-Neustart](#automatic-process-restart)


## Interne Kennung {#internal-identifier}

Die **intern** identifier ist ein technisches Login, das für Installations-, Administrations- und Wartungszwecke verwendet wird. Diese Anmeldung ist keiner Instanz zugeordnet.

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

Adobe Campaign-Prozesse auf dem Server sind über die **config-default.xml** und **`config-<instance>.xml`** Dateien.

Wenn der Adobe Campaign-Dienst gestartet wird, müssen Sie die **nlserver config -reload** Befehl.

Es gibt zwei Arten von Prozessen: mehrere Instanzen und eine einzelne Instanz.

* **mehrere Instanzen**: Ein einzelner Prozess wird für alle Instanzen gestartet. Dies gilt für **Web**, **syslogd** und **trackinglogd** Prozesse.

  Die Aktivierung kann über das Menü **config-default.xml** -Datei.

  Deklarieren eines Adobe Campaign-Servers für den Zugriff auf Clientkonsolen und für die Weiterleitung (Tracking):

  ```
  vi nl6/conf/config-default.xml
  <web args="-tomcat" autoStart="true"/>  
  <!-- to start if the machine is also a redirection server -->  
  <trackinglogd autoStart="true"/>
  ```

  In diesem Beispiel wird die Datei mit einer **vi** -Befehl in Linux. Er kann mit einer beliebigen **.txt** oder **.xml** Editor.

* **Mono-Instanz**: Für jede Instanz wird ein Prozess gestartet (Module: **mta**, **wfserver**, **inMail**, **sms** und **stat**).

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

Sie können den Speicherordner konfigurieren (**var** Verzeichnis) von Adobe Campaign-Daten (Protokolle, Downloads, Weiterleitungen usw.). Verwenden Sie dazu die **XTK_VAR_DIR** Systemvariable:

* Geben Sie unter Windows den folgenden Wert in der **XTK_VAR_DIR** Systemvariable

  ```
  D:\log\AdobeCampaign
  ```

* Navigieren Sie unter Linux zum **customer.sh** und geben Sie an: **export XTK_VAR_DIR=/app/log/AdobeCampaign**.

  Weitere Informationen hierzu finden Sie unter [Parameter personalisieren](../../installation/using/installing-packages-with-linux.md#personalizing-parameters).


## Dynamische Seitensicherheit und Relais {#dynamic-page-security-and-relays}

Standardmäßig werden alle dynamischen Seiten automatisch mit dem **lokal** Tomcat-Server des Computers, dessen Webmodul gestartet wurde. Diese Konfiguration wird im **`<url>`** Abschnitt der Abfrageweiterleitungskonfiguration für die **ServerConf.xml** -Datei.

Sie können die Ausführung der dynamischen Seite auf eine **remote** Server; wenn das Webmodul auf dem Computer nicht aktiviert ist. Dazu müssen Sie die **localhost** mit dem Namen des Remote-Computers für JSP und JSSP, Webanwendungen, Berichte und Zeichenfolgen.

Die verfügbaren Parameter werden im Abschnitt **serverConf.xml** Konfigurationsdatei.

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

Es ist möglich, Clientmaschinenverbindungen von außen zu verhindern. Schränken Sie dazu einfach die Ausführung von **soaprouter.jsp** und nur die Ausführung von Mirrorseiten, viralen Links, Webformularen und öffentlichen Ressourcen zulassen.

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

In diesem Beispiel wird die **`<IP_addresses>`** -Wert entspricht der Liste der IP-Adressen (getrennt durch Kommas), die zur Verwendung des Relais-Moduls für diese Maske berechtigt sind.

>[!NOTE]
>
>Die Werte sind entsprechend Ihrer Konfiguration und Ihren Netzwerkbeschränkungen anzupassen, insbesondere wenn für Ihre Anlage spezifische Konfigurationen entwickelt wurden.

### Verwalten von HTTP-Headern {#managing-http-headers}

Standardmäßig werden nicht alle HTTP-Header weitergeleitet. Sie können bestimmte Header zu den Antworten hinzufügen, die per Relais gesendet werden. Gehen Sie dazu wie folgt vor:

1. Navigieren Sie zu **serverConf.xml** -Datei.
1. Im **`<relay>`** Knoten, wechseln Sie zur Liste der wiedergegebenen HTTP-Header.
1. Hinzufügen einer **`<responseheader>`** -Element mit den folgenden Attributen:

   * **name**: Kopfzeilenname
   * **value**: Wertname.

   Beispiel:

   ```
   <responseHeader name="Strict-Transport-Security" value="max-age=16070400; includeSubDomains"/>
   ```

## Eingrenzen autorisierter externer Befehle {#restricting-authorized-external-commands}

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

Im **exec** -Knoten der Server-Konfigurationsdatei verwenden, müssen Sie auf die zuvor erstellte Datei im **blacklistFile** -Attribut.

**Nur für Linux**: In der Serverkonfigurationsdatei empfehlen wir, einen Benutzer für die Ausführung externer Befehle anzugeben, um Ihre Sicherheitskonfiguration zu verbessern. Dieser Benutzer wird im **exec** -Knoten der Konfigurationsdatei. Alle in der **serverConf.xml** sind in dieser [Abschnitt](../../installation/using/the-server-configuration-file.md).

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

Die URLs der redundanten Server müssen in der Umleitungskonfiguration über die **serverConf.xml** -Datei.

**Beispiel:**

```
<spareserver enabledIf="$(hostname)!='front_srv1'" id="1" url="http://front_srv1:8080" />
<spareserver enabledIf="$(hostname)!='front_srv2'" id="2" url="http://front_srv2:8080" />
```

Die **enableIf** -Eigenschaft ist optional (standardmäßig leer) und ermöglicht es Ihnen, die Verbindung nur zu aktivieren, wenn das Ergebnis wahr ist. Auf diese Weise erhalten Sie auf allen Weiterleitungsservern eine identische Konfiguration.

Um den Hostnamen des Computers abzurufen, führen Sie den folgenden Befehl aus: **hostname -s**.



## Workflows und Affinitäten mit hoher Verfügbarkeit {#high-availability-workflows-and-affinities}

Sie können mehrere Workflow-Server (wfserver) konfigurieren und auf zwei oder mehr Computern verteilen. Wenn Sie diesen Architekturtyp auswählen, konfigurieren Sie den Verbindungsmodus der Lastenausgleichsmodule entsprechend dem Adobe Campaign-Zugriff.

Wählen Sie für den Zugriff über das Internet die **Lastenausgleich** -Modus, um die Verbindungszeiten zu begrenzen.

Wählen Sie beim Zugriff über die Adobe Campaign-Konsole **Hash** oder **Sticky-ip** -Modus. Dadurch können Sie die Verbindung zwischen dem Rich-Client und dem Server beibehalten und verhindern, dass eine Benutzersitzung beispielsweise während eines Import- oder Exportvorgangs unterbrochen wird.

Sie können die Ausführung eines Workflows oder einer Workflow-Aktivität auf einem bestimmten Computer erzwingen. Hierzu müssen Sie eine oder mehrere Affinitäten für den betreffenden Workflow oder die betreffende Aktivität definieren.

1. Erstellen Sie die Affinitäten des Workflows oder der Aktivität, indem Sie sie in die **[!UICONTROL Affinität]** -Feld.

   Sie können einen beliebigen Affinitätsnamen wählen, stellen Sie jedoch sicher, dass Sie keine Leerzeichen oder Satzzeichen verwenden. Wenn Sie verschiedene Server verwenden, geben Sie unterschiedliche Namen an.

   ![](assets/s_ncs_install_server_wf_affinity01.png)

   ![](assets/s_ncs_install_server_wf_affinity02.png)

   Die Dropdown-Liste enthält zuvor verwendete Affinitäten. Sie wird mit der Zeit mit den verschiedenen eingegebenen Werten ergänzt.

1. Öffnen Sie die **nl6/conf/config-`<instance>.xml`** -Datei.
1. Ändern Sie die Zeile, die der **[!UICONTROL wfserver]** -Modul wie folgt:

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

Gehen Sie dazu zum **serverConf.xml** -Datei, die sich im **conf** Repository Ihrer Installation.

Jeder in dieser Datei konfigurierte Prozess verfügt über eine **processRestartTime** -Attribut. Sie können den Wert dieses Attributs ändern, um die Startzeit jedes Prozesses entsprechend Ihren Anforderungen anzupassen.

>[!IMPORTANT]
>
>Löschen Sie dieses Attribut nicht. Alle Prozesse müssen täglich neu gestartet werden.
