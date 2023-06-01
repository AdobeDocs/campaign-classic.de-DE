---
product: campaign
title: "[!DNL Gold Standard] Versionen"
description: Versionshinweise und Kompatibilitätsmatrix für Campaign Classic [!DNL Gold Standard]
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Overview
role: User
level: Beginner
exl-id: 9e3a11b1-3070-4d90-91d5-7c559bdd500e
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: ht
source-wordcount: '1670'
ht-degree: 100%

---

# [!DNL Gold Standard]-Versionen {#gold-standard}



Auf dieser Seite finden Sie Versionshinweise und Kompatibilitätsmatrix für [!DNL Gold Standard]-Versionen.

## [!DNL Gold Standard] – Versionshinweise


### ![](assets/do-not-localize/limited_2.png) [!DNL Gold Standard]-Version 12{#gs-12}

_7. September 2021_

Build 9032@554dbcd umfasst die folgende Fehlerkorrektur:

* Fehlerkorrektur – Jetzt tritt kein 500-Fehler mehr auf, wenn der Link zu einer Web-Anwendung in einem LINE-Versand mit aktiviertem Tracking geöffnet wird.

_Freitag, 27. August 2021_

Build 9032@99a3894 umfasst die folgenden Fehlerkorrekturen:

* Die Tracking-Signaturfunktion wurde verbessert, um Fehler zu verhindern, die in Zusammenhang mit der Art und Weise stehen, in der Drittanbieter-Tools (E-Mail-Clients, Internet-Browser usw.) Sonderzeichen verarbeiten. URL-Parameter sind jetzt codiert.
* Fehlerkorrektur – Bei der Datumsauswahl wird in der Konsole keine Blocker-Fehlermeldung mehr angezeigt. (NEO-36345)

### ![](assets/do-not-localize/limited_2.png) [!DNL Gold Standard]-Version 11{#gs-11}

_Mittwoch, 14. April 2021_

Build 9032@d030c36 umfasst die folgende Fehlerkorrektur:

* Fehlerkorrektur – Es wurde eine Regression in der Client-Konsole korrigiert, die dazu führte, dass im IMS-Verbindungsfenster fortwährend Fehlermeldungen ausgegeben wurden. (NEO-34821)
* Dieser Konsolen-Build ist erforderlich, um den [IMS-Zugriff](../../technotes/using/ims-updates.md) aufrechtzuerhalten.

**Es ist nur eine Konsolenaktualisierung obligatorisch. Eine Serveraktualisierung ist nicht erforderlich.**

>[!CAUTION]
>
> * Wenn Sie über Adobe Identity Management Service (IMS) mit Ihrer Adobe ID eine Verbindung zu Campaign herstellen, ist eine Aktualisierung erforderlich, damit sowohl der Campaign-Server als auch die Client-Konsole nach dem **30. Juni 2021** eine Verbindung zu Campaign herstellen können. [Weitere Informationen](../../technotes/using/ims-updates.md)
> * Diese Version enthält eine [Sicherheitskorrektur](https://helpx.adobe.com/de/security/products/campaign/apsb21-04.html): Die Aktualisierung ist zwingend erforderlich, um die Sicherheit Ihrer Umgebung zu erhöhen.
> * Wenn Sie die Experience Cloud-Triggers-Integration über die OAuth-Authentifizierung verwenden, müssen Sie wie [auf dieser Seite](../../integrations/using/configuring-adobe-io.md) beschrieben zu Adobe I/O wechseln. Die alte oAuth-Authentifizierungsmethode mit Campaign [wurde eingestellt](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411?profile.language=de) am **September 2021**. Gehostete Umgebungen profitieren von einer Verlängerung bis zum **23. Februar 2022**. Wenden Sie sich als On-Premise- oder Hybrid-Kunde an die Kundenunterstützung von Adobe, um den Support bis Februar 2022 zu verlängern. Dazu müssen Sie Adobe [die App-ID der OAuth-Anwendung](../../integrations/using/configuring-pipeline.md#step-optional) bereitstellen.
>
>Weitere Informationen finden in diesem [[!DNL Gold Standard] Abschnitt](../../rn/using/gold-standard.md).

_Dienstag, 2. März 2021_

Build 9032@10c2709 umfasst die folgende Fehlerkorrektur:

* Korrektur einer Regression, die die Verwendung einiger Konsolenkomponenten wie der Datumsauswahl und der Bildverwaltung in Sendungen verhinderte. (NEO-31453, NEO-31454)

**Es ist nur eine Konsolenaktualisierung obligatorisch. Eine Serveraktualisierung ist nicht erforderlich.**

>[!NOTE]
>
> Stellen Sie eine Verbindung zu [Adobe Softwareverteilung](https://experience.adobe.com/#/downloads/content/software-distribution/de/campaign.html) her, um die neue Version herunterzuladen. Erfahren Sie [auf dieser Seite](../../installation/using/client-console-availability-for-windows.md), wie Sie die Konsolenaktualisierung allen Endbenutzern vorschlagen können.

_Dienstag, 22. Dezember 2020_

Der Build 9032@d3b452f umfasst die folgenden Verbesserungen und Fehlerbehebungen:

* Das Verbindungsprotokoll wurde aktualisiert, sodass es dem neuen IMS-Authentifizierungsmechanismus entspricht.

* Die Authentifizierung der Triggers-Integration, die ursprünglich auf der oAUTH-Authentifizierung basierte und für den Zugriff auf Pipeline eingerichtet wurde, wurde geändert und in Adobe I/O verschoben. [Weitere Infos](../../integrations/using/configuring-adobe-io.md)

* Nach dem [Ende der Unterstützung für das ältere Binärprotokoll von iOS-APNs](https://developer.apple.com/news/?id=c88acm2b) werden alle Instanzen, die dieses Protokoll verwenden, während des Postupgrades auf das HTTP/2-Protokoll aktualisiert.

* Fehlerkorrektur – Es wurde ein Sicherheitsproblem behoben, um den Schutz vor SSRF-Problemen (Server Side Request Forgery) zu verbessern. (NEO-27777)

* Fehlerkorrektur – Workflows schlagen beim Ausführen einer Aktivität vom Typ **Anreicherung** jetzt nicht mehr fehl. (NEO-17338)

### ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard]-Version 10{#gs-10}

_Dienstag, 7. Juli 2020_

Build 9032@efd8a94 umfasst die folgende Fehlerkorrektur:

Fehlerkorrektur – Tracking funktioniert jetzt, wenn die Signaturfunktion deaktiviert ist. (NEO-26411)

>[!CAUTION]
>
>Es wird empfohlen, die Clientkonsole mit der in dieser Version verfügbaren zu aktualisieren. Mehr dazu erfahren Sie auf [dieser Seite](../../installation/using/installing-the-client-console.md).

### ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard]-Version 9{#gs-9}

_22. Juni 2020_

Build 9032@800be2e umfasst die folgenden Fehlerkorrekturen:

* Der iOS-HTTP2-Connector wurde verbessert (Updates von Drittanbietern und Fehlerverwaltung). (NEO-25904, NEO-25903, NEO-25799)

Die folgenden Fehlerkorrekturen beziehen sich auf den Sicherheitsmechanismus von Trackinglinks (weitere Informationen finden Sie in der [Checkliste für Sicherheit und Datenschutz](https://helpx.adobe.com/de/campaign/kb/acc-security.html#signature-mechanism)):

* Fehlerkorrektur – Tracking von &quot;Benachrichtigungsklicks&quot; (iOS- und Android-Push-Benachrichtigungen) funktioniert jetzt. (NEO-25965)
* Fehlerkorrektur – Tracking-URLs können geöffnet/geklickt werden, wenn bestimmte veraltete Outlook-Versionen verwendet werden. (NEO-25688)
* Fehlerkorrektur – Tracking von URLs mithilfe von Fragmenten in Personalisierungsparametern (Anker-Tags mit Rautenzeichen) funktioniert jetzt. (NEO-25774)
* Fehlerkorrektur – Es wurde ein Problem mit dem Anti-Phishing-Dienst behoben. (NEO-25283)
* Fehlerkorrektur – Es wurde ein Problem beim Tracking mit spezifischen benutzerdefinierten Tracking-Formeln behoben. (NEO-25277)





### ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard]-Version 8{#gs-8}

_Mittwoch, 29. April 2020_

Build 9032@3a9dc9c umfasst die folgenden Fehlerkorrekturen:

* Verbesserte Sicherheit bei Tracking-Links in E-Mails. Dies ist für alle Kunden standardmäßig aktiviert. Es gibt eine zusätzliche, erweiterte Sicherheitsfunktion, die Sie aktivieren können, indem Sie sich an die Kundenunterstützung wenden. Weiterführende Informationen zu der Funktion und den Schritten zur Aktivierung für nicht gehostete Kunden finden Sie in der [Prüfliste für Sicherheit und Datenschutz](https://helpx.adobe.com/de/campaign/kb/acc-security.html#signature-mechanism).

>[!CAUTION]
>
>Wenn Sie Probleme mit Push-Benachrichtigungen unter Verwendung von Tracking-Links oder mit dem Versand mittels Anker-Tags haben, wird empfohlen, den neuen Signaturmechanismus für Trackinglinks zu deaktivieren. Das Verfahren wird auf [dieser Seite](https://helpx.adobe.com/de/campaign/kb/acc-security.html#signature-mechanism) beschrieben.

* Fehlerkorrektur – Die Anzeige von Bildern in Line-Sendungen wird jetzt nicht mehr verhindert. (NEO-23207)
* Fehlerkorrektur – Bei der Aktivität **Dateiübertragung** funktioniert jetzt die SFTP-Schlüssel-basierte Authentifizierung bei Debian 9. (NEO-23183)
* Fehlerkorrektur – Bei Push-Benachrichtigungen, die mit hoher Häufigkeit gesendet werden, tritt jetzt kein Problem mehr auf. (NEO-20516)
* Fehlerkorrektur – Die Verwaltung von Angebotsantworten führt jetzt nicht mehr zu Webserver-Abstürzen. (NEO-19482)
* Fehlerkorrektur – In der LibreOffice-Verwaltung ist jetzt das Exportieren von Berichten möglich. (NEO-20982)
* Fehlerkorrektur – Beim Aktualisieren verschiedener Workflows mit einer Umfrageaktivität tritt jetzt kein Fehler mehr auf.
* Die LibreOffice-Verwaltung wurde verbessert, um Fehler bei der E-Mail-Vorschau mit .odt-Dateien zu verhindern.
* Die Verwaltung der Apache-Verbindung wurde verbessert, um Latenzen beim Web-Dienst zu vermeiden.
* Die Anzeige des Version-Tags (siebenstellig) im Menü **Versionsinformationen** wurde verbessert.
* Fehlerkorrektur – Es wurde ein Regressionsfehler bei der Listenverwaltung behoben, der die Veröffentlichung von Angeboten verhinderte.
* Fehlerkorrektur – Es wurde ein Regressionsfehler behoben, der zum Absturz des Bereinigungs-Workflows führte.
* Fehlerkorrektur – Es wurde ein geringfügiger Regressionsfehler in den Bereinigungs-Workflow-Logs behoben.

### ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard]-Version 6{#gs-6}

_Montag, 9. März 2020_

Build 9032@19f73c5 umfasst die folgende Fehlerkorrektur:

* Fehlerkorrektur – Es gibt kein Problem mehr mit externen Konten, die FTP über SSL verwenden. (NEO-20498)

### ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard]-Version 5{#gs-5}

_Dienstag, 17. Dezember 2019_

Build 9032@d6b8062 umfasst die folgende Fehlerkorrektur:

* Fehlerkorrektur – Tracking-Fehler bei folgenden Kommunikationskanälen tritt nicht mehr auf: Mobile (SMS, MMS), Push (iOS, Android) und soziale Netzwerke (Facebook, Twitter). (NEO-19595)

### ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard]-Version 4{#gs-4}

_Mittwoch, 11. Dezember 2019_

Build 9032@bc4a935 umfasst die folgende Fehlerkorrektur:

* Fehlerkorrektur – Keine Leistungsprobleme mehr beim Senden von Nachrichten mit einer MSSQL-Datenbank. (NEO-17558)

### ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard]-Version 3{#gs-3}

_Mittwoch, 20. November 2019_

Build 9032@3468c7b umfasst die folgenden Fehlerkorrekturen:

* Fehlerkorrektur – Die Anmeldung per IMS-Authentifizierung funktioniert nun. (NEO-17312)
* Fehlerkorrektur – Kumulative Berichte zu mehreren Sendungen werden nun richtig angezeigt. (NEO-18165)
* Fehlerkorrektur – Der Webserver wird nicht mehr blockiert oder zum Absturz gebracht.

### ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard]-Version 2{#gs-2}

_Donnerstag, 19. September 2019_

Build 9032@cee805c umfasst die folgenden Fehlerkorrekturen:

* Fehlerkorrektur – Die Verwendung von CRM-Connector für Salesforce funktioniert nun problemlos. (NEO-17712)
* Fehlerkorrektur – Ein Indexfehler verursacht beim Senden von Transaktionsnachrichten keine Leistungsprobleme mehr.

### ![](assets/do-not-localize/red_2.png) Version 19.1.4 – Build 9032{#release-19-1-4-build-9032}

_Dienstag, 13. August 2019_

Der erste Build 19.1.4 enthält die folgenden Fehlerkorrekturen:

* Fehlerkorrektur – In der Planungsaktivität werden jetzt bei der Konfiguration des Assistenten keine unbeabsichtigten Fehlernachrichten mehr erzeugt. Update NEO-11662 wurde rückgängig gemacht. (NEO-17097)
* Regressionskorrektur – Jetzt tritt kein durch NEO-12727 verursachter Fehler mehr auf, bei dem Workflows angehalten wurden, wenn eine Testaktivität zweimal ausgeführt wird. (NEO-16835)
* Fehlerkorrektur – Jetzt wird kein fehlerhafter HTTP-Code mehr zurückgegeben (HTTP 200 OK statt HTTP 403 Forbidden), wenn ein ungültiges oder abgelaufenes Sitzungstoken in API-Aufrufen verwendet wird. (NEO-16826)
* Fehlerkorrektur – Der DKIM-Schlüssel wird jetzt in E-Mails eingebettet, sodass der Versand fehlerfrei funktioniert. (NEO-16804)
* Fehlerkorrektur – Die Workflow-Planung funktioniert jetzt wieder einwandfrei, sodass Workflows entsprechend ihrer Konfiguration ausgeführt werden. (NEO-16619, NEO-16426)


## [!DNL Gold Standard] – Kompatibilitätsmatrix{#compatibility-matrix-gs}

In diesem Abschnitt sind alle Systeme und Komponenten aufgeführt, die für Builds von **Adobe Campaign Classic[!DNL Gold Standard]** 19.1 unterstützt werden. Produkte und Versionen, die nicht in dieser Liste enthalten sind, sind nicht mit dieser Version von Adobe Campaign kompatibel.

>[!CAUTION]
>Sofern nicht anders angegeben, werden alle Nebenversionen unterstützt.
>
>Adobe Campaign Classic ist mit allen Systemen und Tools kompatibel, die auf dieser Seite aufgelistet sind. Wenn bestimmte Versionen dieser Drittanbietersysteme und -Tools bei ihren Erstanbietern das Ende des Lebenszyklus (End of Life, EOL) erreichen, ist Adobe Campaign nicht mehr mit ihnen kompatibel. Diese Versionen werden daher mit der nächsten Produktversion aus unserer Kompatibilitätsmatrix entfernt. Verwenden Sie, um Probleme zu vermeiden, ausschließlich unterstützte Versionen von Systemen, die in der Kompatibilitätsmatrix aufgeführt sind.

### Betriebssysteme{#OperatingSystems-gs}

<table> 
<tbody> 
<tr> 
<td>CentOs</td>
<td>
<p>8.x (64 Bit)</p>
<p>7.x (64 Bit)</p>
</td>
</tr>
<tr>
<td>Debian</td>
<td>
<p>9 (64 Bit)</p>
<p>8 (64 Bit)</p>
</td>
</tr>
<tr>
<td>RHEL</td>
<td>
<p>7.x (64 Bit)</p>
<p><strong>Wichtig:</strong> Wenn Sie RHEL verwenden, müssen Sie SELinux deaktivieren oder Ihre Programmierer benutzerdefinierte SELinux-Regeln schreiben lassen, um zu überprüfen, ob ein aktiviertes SELinux keine Probleme mit Campaign-Vorgängen verursacht.</p>
</td>
</tr>
<tr>
<td>Windows Server</td>
<td>
<p>2016</p>
<p>2012 R2</p>
<p>2012</p>
</td>
</tr>
</tbody>
</table>

### Webserver{#WebServers-gs}

<table>
<tbody>
<tr>
<td>Microsoft IIS</td>
<td>
<p>10.0 auf Windows-Server 2016</p>
<p>8.5 auf Windows-Server 2012 R2</p>
<p>8.0 auf Windows-Server 2012 – Windows 8</p>
</td>
</tr>
<tr>
<td>Apache</td>
<td>
<p>2.4 für RHEL 7– CentOS 7, Debian 8/9, Windows (64 Bit)</p>
<p>2.2 nur für RHEL6 – nur CentOS 6 (64 Bit)</p>
</td>
</tr>
</tbody>
</table>

### Tools{#Tools-gs}

<table>
<tbody>
<tr>
<td>Java Development Kit (JDK)</td>
<td>
<p>8</p>
<p>Die Anwendung wurde für das Java Development Kit (JDK), das von Oracle entwickelt wurde, sowie für OpenJDK genehmigt.</p>
</td>
</tr>
<tr>
<td>Libre Office</td>
<td>
<p>6 (und frühere Versionen, sofern in Ihrem System eingebettet)</p>
</td>
</tr>
<tr>
<td>SpamAssassin</td>
<td>
<p>3.4.x</p>
</td>
</tr>
</tbody>
</table>

### RDBMS-Server{#RDBMSservers-gs}

>[!NOTE]
>
>RDBMS-Treiber muss der RDBMS-Server-Version entsprechen.

<table>
<tbody>
<tr>
<td>Oracle</td>
<td>
<p>18c</p>
<p>12c</p>
<p>11g R2</p>
</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>11.x</p>
<p>10.x</p>
<p>9.6.x</p>
<p>9.5.x</p>
<p>9.4.x</p>
<p>Hinweis: Sie können für PostgreSQL auch Amazon RDS mit den oben angegebenen Versionen verwenden.</p>
</td>
</tr>
<tr>
<td>SQL-Server</td>
<td>
<p>2019</p>
<p>2017</p>
<p>2016</p>
<p>2014</p>
<p>2012 – SP1 und SP2</p>
<p>Warnung: Microsoft SQL Server wird nicht als primäre Datenbank unterstützt, wenn der Campaign-Server auf Linux läuft.</p>
</td>
</tr>
<tr>
<td>DB2 UDB</td>
<td>
<p>9.7</p>
<p>Warnung: DB2 UDB ist für Neuinstallationen nicht zulässig.</p>
</td>
</tr>
</tbody>
</table>

>[!NOTE]
>
>PostgreSQL ist der Standarddatenbankserver für gehostete Umgebungen.

### CRM-Connectoren{#CRMconnectors-gs}

<table>
<tbody>
<tr>
<td>Salesforce Connector-API</td>
<td>
<p>API-Version 37</p>
</td>
</tr>
<tr>
<td>SFDC-API</td>
<td>
<p>API-Version 21</p>
<p>API-Version 15</p>
</td>
</tr>
<tr>
<td>Microsoft Dynamics</td>
<td>
<p>Soap-API – On-Premise: 2007, 2015, 2016</p>
<p>Soap-API – Online: 2015, 2016</p>
<p>Web-API – On-Premise und Online: 365, 2016, 2016 Update 1</p>
</td>
</tr>
</tbody>
</table>

### Federated Data Access (FDA){#FederatedDataAccessFDA-gs}

<table>
<tbody>
<tr>
<td>Amazon Redshift</td>
<td><p> </p>
</td>
</tr>
<tr>
<td>Oracle</td>
<td>
<p>12c</p>
<p>11g</p>
</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>11.x</p>
<p>10.x</p>
<p>9.6.x</p>
<p>9.4.x</p>
</td>
</tr>
<tr><td>SQL-Server</td>
<td>
<p>2019</p>
<p>2017</p>
<p>2016</p>
<p>2014</p>
<p>2012 SP1 und SP2</p>
</td>
</tr>
<tr><td>MySQL</td>
<td>
<p>5.7</p>
</td>
</tr>
<tr>
<td>Teradata</td>
<td>
<p>16.20</p>
<p>16</p>
<p>15.10</p>
<p>15.0</p>
</td>
</tr>
<tr>
<td>Netezza</td>
<td>
<p>7.2</p>
</td>
</tr>
<tr>
<td>Sybase</td>
<td>
<p>IQ 16</p>
<p>ASE 15.7</p>
</td>
</tr>
<tr>
<td>SAP HANA</td>
<td>
<p>Version 1 SPS 12</p>
</td>
</tr>
<tr><td>Hadoop über HiveSQL</td>
<td>
<p>HortonWorks HDP 2.4.X, 2.5.x, 2.6.x</p>
<p>HDInsight 3.4 (HDP 2.4), 3.5 (HDP 2.5), 3.6 (HDP 2.6)</p>
</td>
</tr>
</tbody>
</table>

### Client-Konsole {#ClientConsoleoperatingsystems}

:warning: Für die Verwendung der Campaign-Client-Konsole sind die folgenden Betriebssysteme und Browser erforderlich.

#### Betriebssysteme

<table>
<tbody>
<tr>
<td>Microsoft Windows Server</td>
<td>
<p>2016</p>
<p>2012</p>
</td>
</tr>
<tr>
<td>Microsoft Windows</td>
<td>
<p>8</p>
<p>10 (empfohlen für japanische Instanzen)</p>
</td>
</tr>
</tbody>
</table>

#### Browser

<table>
<tbody>
<tr>
<td>
<p>Microsoft Internet Explorer</p>
</td>
<td>
<p>11</p>
</td>
</tr>
</tbody>
</table>

### Mobile SDK{#MobileSDK}

<table>
<tbody>
<tr>
<td>Android</td>
<td>
<p>7.x, 8.x, 9.0</p>
<p>mit Mobile SDK Build 1.0.27.</p>
</td>
</tr>
<tr>
<td>iOS</td>
<td>
<p>iOS 9 bis 14</p>
<p>mit Mobile SDK (Build 1.0.26), kompatibel mit 32- und 64-Bit-Versionen.</p>
</td>
</tr>
</tbody>
</table>

### Browser{#Browsers}

Die folgenden Browser sind mit Campaign für Web-Zugriff kompatibel.

<table>
<tbody>
<tr>
<td>
<p>Microsoft Edge</p>
</td>
<td>
<p>Neueste Version</p>
</td>
</tr>
<tr>
<td>
<p>Mozilla Firefox</p>
</td>
<td>
<p>Neueste Version</p>
</td>
</tr>
<tr>
<td>
<p>Google Chrome</p>
</td>
<td>
<p>Neueste Version</p>
</td>
</tr>
<tr>
<td>
<p>Safari</p>
</td>
<td>
<p>Neueste Version</p>
</td>
</tr>
<tr>
<td>
<p>Microsoft Internet Explorer</p>
</td>
<td>
<p>11</p>
</td>
</tr>
</tbody>
</table>
