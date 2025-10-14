---
product: campaign
title: Campaign-Server konfigurieren
description: Campaign-Server konfigurieren
feature: Installation, Instance Settings
badge-v7-prem: label="Nur On-Premise/Hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Gilt nur für Hybrid- und On-Premise-Bereitstellungen"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 46c8ed46-0947-47fb-abda-6541b12b6f0c
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '1571'
ht-degree: 2%

---

# Erste Schritte mit der Campaign-Server-Konfiguration{#gs-campaign-server-config}



In diesem Kapitel werden Server-seitige Konfigurationen beschrieben, die entsprechend Ihren Anforderungen und den Besonderheiten Ihrer Umgebung durchgeführt werden können.

## Einschränkungen

Diese Verfahren sind auf On **Premise-/**&#x200B;**Hybrid** Bereitstellungen beschränkt und erfordern Administratorberechtigungen.

Bei **gehosteten** können Server-seitige Einstellungen nur von Adobe konfiguriert werden. Auf die Zulassungsliste setzen Einige Einstellungen können jedoch im Control Panel von [&#x200B; eingerichtet werden](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/key-features.html?lang=de) z. B. die IP-Dateiverwaltung oder URL-Berechtigungen. [Weitere Informationen](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/ip-allow-listing-instance-access.html?lang=de).

Weitere Informationen finden Sie in den folgenden Abschnitten:

* [Control Panel-Dokumentation](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=de)
* [Hosting-Modelle](../../installation/using/hosting-models.md)
* [Matrix mit On-Premise- und gehosteten Funktionen von Campaign Classic](../../installation/using/capability-matrix.md)

## Konfigurationsdateien

Campaign Classic-Konfigurationsdateien werden im **conf** des Adobe Campaign-Installationsordners gespeichert. Die Konfiguration umfasst zwei Dateien:

* **serverConf.xml**: allgemeine Konfiguration für alle Instanzen. In dieser Datei werden die technischen Parameter des Adobe Campaign-Servers kombiniert: Diese werden von allen Instanzen gemeinsam genutzt. Einige dieser Parameter werden im Folgenden beschrieben. Die verschiedenen Knoten und Parameter, die in diesem [Abschnitt) &#x200B;](../../installation/using/the-server-configuration-file.md) sind.
* **config-`<instance>`.xml** (wobei **instance** der Name der Instanz ist): spezifische Konfiguration der Instanz. Wenn Sie Ihren Server für mehrere Instanzen freigeben, geben Sie die für jede Instanz spezifischen Parameter in die entsprechende Datei ein.

## Konfigurationsumfang

Konfigurieren oder passen Sie den Campaign-Server je nach Ihren Anforderungen und Ihrer Konfiguration an. Sie haben folgende Möglichkeiten:

* Sichern Sie die [Interne Kennung](#internal-identifier)
* Aktivieren [Campaign-Prozesse](#enabling-processes)
* Konfigurieren von [URL-Berechtigungen](url-permissions.md)
* Definieren [Sicherheitszonen](security-zones.md)
* Konfigurieren Sie [Tomcat-Einstellungen](configure-tomcat.md)
* Anpassen [Versandparameter](configure-delivery-settings.md)
* Definieren [Dynamische Seitensicherheit und -relais](#dynamic-page-security-and-relays)
* Beschränken der Liste der [Zulässigen externen Befehle](#restricting-authorized-external-commands)
* Einrichten [redundanten Trackings](#redundant-tracking)
* Verwalten [Hochverfügbarkeit und Workflow-Affinitäten](#high-availability-workflows-and-affinities)
* Konfigurieren der Dateiverwaltung - [Weitere Informationen](file-res-management.md)
   * Upload-Dateiformat begrenzen
   * Zugriff auf öffentliche Ressourcen aktivieren
   * Proxy-Verbindung konfigurieren
* [Automatischer Prozessneustart](#automatic-process-restart)


## Interne Kennung {#internal-identifier}

Die **interne** Kennung ist ein technischer Login, der für Installations-, Administrations- und Wartungszwecke verwendet wird. Diese Anmeldung ist keiner Instanz zugeordnet.

Benutzer, die über diesen Login verbunden sind, haben alle Rechte für alle Instanzen. Dieser Login wird im Falle einer Neuinstallation kein Passwort haben. Sie müssen dieses Kennwort manuell definieren.

Verwenden Sie den folgenden Befehl:

```sql
nlserver config -internalpassword
```

Daraufhin werden die folgenden Informationen angezeigt. Geben Sie das Kennwort ein und bestätigen Sie es:

```sql
17:33:57 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
Enter the current password.
Password:
Enter the new password.
Password: XXXX
Confirmation: XXXX
17:34:02 >   Password successfully changed for account 'internal' (authentication mode 'nl')
```

## Prozesse aktivieren {#enabling-processes}

Adobe Campaign-Prozesse auf dem Server werden über die Dateien **config-default.xml** und **`config-<instance>.xml`** aktiviert (und deaktiviert).

Um die Änderungen auf diese Dateien anzuwenden, müssen Sie beim Starten des Adobe Campaign-Dienstes den Befehl **nlserver config -reload** ausführen.

Es gibt zwei Arten von Prozessen: Multi-Instanz und Einzelinstanz.

* **Multi-Instance**: Für alle Instanzen wird ein einzelner Prozess gestartet. Dies ist der Fall für **web**, **syslogd** und **trackinglogd**-Prozesse.

  Die Aktivierung kann über die Datei &quot;**-default.xml“** werden.

  Deklarieren eines Adobe Campaign-Servers für den Zugriff auf Client-Konsolen und für die Weiterleitung (Tracking):

  ```
  vi nl6/conf/config-default.xml
  <web args="-tomcat" autoStart="true"/>  
  <!-- to start if the machine is also a redirection server -->  
  <trackinglogd autoStart="true"/>
  ```

  In diesem Beispiel wird die Datei unter Linux mit einem **vi**-Befehl bearbeitet. Sie kann mit einem beliebigen **.txt** oder **.xml**-Editor bearbeitet werden.

* **monoinstance**: Für jede Instanz wird ein Prozess gestartet (Module: **mta**, **wfserver**, **inMail**, **sms** und **stat**).

  Die Aktivierung kann mithilfe der Konfigurationsdatei der Instanz konfiguriert werden:

  ```
  config-<instance>.xml
  ```

  Versand-Server deklarieren, Workflow-Instanzen ausführen und Bounce Messages wiederherstellen:

  ```
  <mta autoStart="true" statServerAddress="localhost"/>
  <wfserver autoStart="true"/>  
  <inMail autoStart="true"/>
  <stat autoStart="true"/>
  ```

**Campaign-Datenspeicherung**

Sie können das Speicherverzeichnis (**var**-Verzeichnis) der Adobe Campaign-Daten (Protokolle, Downloads, Umleitungen usw.) konfigurieren. Verwenden Sie dazu die Systemvariable **XTK_VAR_DIR**:

* Geben Sie unter Windows in der Systemvariablen **XTK_VAR_DIR** den folgenden Wert an

  ```
  D:\log\AdobeCampaign
  ```

* Gehen Sie unter Linux zur Datei **customer.sh** und geben Sie Folgendes an: **export XTK_VAR_DIR=/app/log/AdobeCampaign**.

  Weitere Informationen hierzu finden Sie unter [Parameter &#x200B;](../../installation/using/installing-packages-with-linux.md#personalizing-parameters).


## Dynamische Seitensicherheit und Relais {#dynamic-page-security-and-relays}

Standardmäßig beziehen sich alle dynamischen Seiten automatisch auf den Tomcat **lokalen**-Server des Computers, dessen Web-Modul gestartet wurde. Diese Konfiguration wird im Abschnitt **`<url>`** der Konfiguration des Abfrage-Relais für die Datei **ServerConf.xml** eingegeben.

Sie können die Ausführung der dynamischen Seite auf einen **Remote**-Server weiterleiten, wenn das Web-Modul auf dem Computer nicht aktiviert ist. Ersetzen Sie dazu den **localhost** durch den Namen des Remotecomputers für JSP und JSSP, Webanwendungen, Berichte und Zeichenfolgen.

Weitere Informationen zu den verschiedenen verfügbaren Parametern finden Sie in der Konfigurationsdatei **serverConf.xml**.

Für JSP-Seiten lautet die Standardkonfiguration:

```
<url relayHost="true" relayPath="true" targetUrl="http://localhost:8080" urlPath="*.jsp"/>
```

Adobe Campaign verwendet die folgenden JSP-Seiten:

* /nl/jsp/**soaprouter.jsp**: Client-Konsole und Webdienstverbindungen (SOAP-APIs),
* /nl/jsp/**m.jsp**: Mirrorseiten,
* /nl/jsp/**logon.jsp**: Web-basierter Zugriff auf Berichte und auf die Bereitstellung der Client-Konsole,
* /nl/jsp/**s.jsp** : Verwenden von viralem Marketing (Sponsoring und soziale Netzwerke).

Für den Mobile-App-Kanal werden folgende JSSPs verwendet:

* nms/mobile/1/registerIOS.jssp
* nms/mobile/1/registerAndroid.jssp

**Beispiel:**

Es ist möglich, Client-Computer-Verbindungen von außen zu verhindern. Beschränken Sie dazu einfach die Ausführung von **soaprouter.jsp** und erlauben Sie nur die Ausführung von Mirror-Seiten, viralen Links, Web-Formularen und öffentlichen Ressourcen.

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

In diesem Beispiel entspricht der **`<IP_addresses>`** der Liste der IP-Adressen (durch Kommata getrennt), die zur Verwendung des Relais-Moduls für diese Maske berechtigt sind.

>[!NOTE]
>
>Die Werte werden entsprechend Ihrer Konfiguration und Ihren Netzwerkeinschränkungen angepasst, insbesondere wenn für Ihre Installation spezifische Konfigurationen entwickelt wurden.

### HTTP-Header verwalten {#managing-http-headers}

Standardmäßig werden nicht alle HTTP-Kopfzeilen weitergeleitet. Sie können den vom Relais gesendeten Antworten bestimmte Kopfzeilen hinzufügen. Gehen Sie dazu wie folgt vor:

1. Navigieren Sie zur Datei **serverConf.xml**.
1. Wechseln Sie im Knoten **`<relay>`** zur Liste der zugehörigen HTTP-Kopfzeilen.
1. Fügen Sie ein **`<responseheader>`** mit den folgenden Attributen hinzu:

   * **name**: Kopfzeilenname
   * **value**: Wertname.

   Beispiel:

   ```
   <responseHeader name="Strict-Transport-Security" value="max-age=16070400; includeSubDomains"/>
   ```

## Zulässige externe Befehle einschränken {#restricting-authorized-external-commands}

Ab Build 8780 können technische Administratoren die Liste der autorisierten externen Befehle einschränken, die in Adobe Campaign verwendet werden können.

Dazu müssen Sie eine Textdatei mit einer Liste von Befehlen erstellen, deren Verwendung Sie verhindern möchten, z. B.:

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

Im Knoten **exec** der Server-Konfigurationsdatei müssen Sie im Attribut **blacklistFile** auf die zuvor erstellte Datei verweisen.

**Nur für Linux**: In der Server-Konfigurationsdatei empfehlen wir, einen Benutzer anzugeben, der zum Ausführen externer Befehle verwendet wird, um die Sicherheitskonfiguration zu verbessern. Dieser Benutzer wird im Knoten **exec** der Konfigurationsdatei festgelegt. Alle in der Datei **serverConf.xml** verfügbaren Parameter werden in diesem [Abschnitt](../../installation/using/the-server-configuration-file.md) aufgeführt.

>[!NOTE]
>
>Wenn kein Benutzer angegeben ist, werden alle Befehle im Benutzerkontext der Adobe Campaign-Instanz ausgeführt. Der Benutzer muss sich von dem Benutzer unterscheiden, der Adobe Campaign ausführt.

Beispiel:

```
<serverConf>
 <exec user="theUnixUser" blacklistFile="/pathtothefile/blacklist"/>
</serverConf>
```

Dieser Benutzer muss der Audier-Liste des Adobe Campaign-Benutzers „neolane“ hinzugefügt werden.

>[!IMPORTANT]
>
>Sie sollten kein benutzerdefiniertes sudo verwenden. Auf dem System muss ein Standard-Sudo installiert sein.


## Redundante Verfolgung {#redundant-tracking}

Wenn mehrere Server für die Umleitung verwendet werden, müssen sie in der Lage sein, über SOAP-Aufrufe miteinander zu kommunizieren, um Informationen aus den umzuleitenden URLs auszutauschen. Beim Start des Versands sind möglicherweise nicht alle Weiterleitungsserver verfügbar, sodass diese möglicherweise nicht über dieselbe Informationsstufe verfügen.

>[!NOTE]
>
>Bei Verwendung der Standard- oder Unternehmensarchitektur muss der Hauptanwendungsserver berechtigt sein, Tracking-Informationen auf jeden Computer hochzuladen.

Die URLs der redundanten Server müssen in der Umleitungskonfiguration über die Datei **serverConf.xml** angegeben werden.

**Beispiel:**

```
<spareserver enabledIf="$(hostname)!='front_srv1'" id="1" url="http://front_srv1:8080" />
<spareserver enabledIf="$(hostname)!='front_srv2'" id="2" url="http://front_srv2:8080" />
```

Die **enableIf**-Eigenschaft ist optional (standardmäßig leer) und ermöglicht es, die Verbindung nur zu aktivieren, wenn das Ergebnis „true“ ist. Auf diese Weise erhalten Sie eine identische Konfiguration für alle Weiterleitungsserver.

Um den Hostnamen des Computers abzurufen, führen Sie den folgenden Befehl aus: **hostname -s**.



## Workflows und Affinitäten mit hoher Verfügbarkeit {#high-availability-workflows-and-affinities}

Sie können mehrere Workflow-Server (wfserver) konfigurieren und auf zwei oder mehr Computern verteilen. Wenn Sie diesen Architekturtyp wählen, konfigurieren Sie den Verbindungsmodus der Lastenausgleichsmodule entsprechend dem Adobe Campaign-Zugriff.

Für den Zugriff über das Web wählen Sie den **Load-Balancer**-Modus aus, um die Verbindungszeiten zu begrenzen.

Wenn Sie über die Adobe Campaign-Konsole auf zugreifen, wählen Sie **Hash**- oder **Sticky-IP** Modus aus. Auf diese Weise können Sie die Verbindung zwischen dem Rich-Client und dem Server aufrechterhalten und verhindern, dass eine Benutzersitzung beispielsweise während eines Import- oder Exportvorgangs unterbrochen wird.

Sie können die Ausführung eines Workflows oder einer Workflow-Aktivität auf einem bestimmten Computer erzwingen. Dazu müssen Sie eine oder mehrere Affinitäten für den betreffenden Workflow oder die betreffende Aktivität definieren.

1. Erstellen Sie die Affinitäten des Workflows oder der Aktivität, indem Sie sie in das Feld **[!UICONTROL Affinität]** eingeben.

   Sie können einen beliebigen Affinitätsnamen auswählen, stellen Sie jedoch sicher, dass Sie keine Leerzeichen oder Satzzeichen verwenden. Wenn Sie unterschiedliche Server verwenden, geben Sie unterschiedliche Namen an.

   ![](assets/s_ncs_install_server_wf_affinity01.png)

   ![](assets/s_ncs_install_server_wf_affinity02.png)

   Die Dropdown-Liste enthält zuvor verwendete Affinitäten. Sie wird im Laufe der Zeit mit den verschiedenen eingegebenen Werten abgeschlossen.

1. Öffnen Sie die Datei **nl6/conf/config-`<instance>.xml`**.
1. Ändern Sie die Zeile, die mit dem Modul **[!UICONTROL wfserver]** übereinstimmt, wie folgt:

   ```
   <wfserver autoStart="true" affinity="XXX,"/>
   ```

   Wenn Sie mehrere Affinitäten definieren, müssen sie durch Kommas ohne Leerzeichen getrennt werden:

   ```
   <wfserver autoStart="true" affinity="XXX,YYY,"/>
   ```

   Das Komma nach dem Namen der Affinität ist für die Ausführung von Workflows erforderlich, für die keine Affinität definiert ist.

   Wenn Sie nur Workflows ausführen möchten, für die eine Affinität definiert ist, fügen Sie am Ende der Liste Ihrer Affinitäten kein Komma hinzu. Ändern Sie beispielsweise die Zeile wie folgt:

   ```
   <wfserver autoStart="true" affinity="XXX"/>
   ```

## Automatischer Neustart {#automatic-process-restart}

Standardmäßig werden die verschiedenen Adobe Campaign-Prozesse jeden Tag um 6 Uhr morgens (Serverzeit) automatisch neu gestartet.

Sie können diese Konfiguration jedoch ändern.

Navigieren Sie dazu zur Datei **serverConf.xml** im **conf**-Repository Ihrer Installation.

Jeder in dieser Datei konfigurierte Prozess verfügt über ein **processRestartTime**-Attribut. Sie können den Wert dieses Attributs ändern, um die Neustartzeit jedes Prozesses Ihren Anforderungen entsprechend anzupassen.

>[!IMPORTANT]
>
>Dieses Attribut nicht löschen. Alle Prozesse müssen täglich neu gestartet werden.
