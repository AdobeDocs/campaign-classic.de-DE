---
product: campaign
title: Campaign Classic-Versionen 2019
description: Weiterführende Informationen zu Campaign Classic-Versionen 2019
exl-id: 8a36a542-e095-4208-b624-e59845592863
source-git-commit: 96f2ae67a5b47b80533e759713cf5b36baa8cf36
workflow-type: ht
source-wordcount: '4854'
ht-degree: 100%

---

# Versionen 2019{#release-2019}

![](../../assets/v7-only.svg)

## Version 19.2{#release-19-2}

### ![](assets/do-not-localize/limited_2.png) Version 19.2.4 – Build 9082 {#release-19-2-4-build-9082}

_Donnerstag, 15. April 2021_

* Fehlerkorrektur – Es wurde eine Regression in der Client-Konsole korrigiert, die dazu führte, dass im IMS-Verbindungsfenster fortwährend Fehlermeldungen ausgegeben wurden. (NEO-34821)

**Es ist nur eine Konsolenaktualisierung obligatorisch. Eine Serveraktualisierung ist nicht erforderlich.**

>[!NOTE]
>
> Stellen Sie eine Verbindung zu [Adobe Softwareverteilung](https://experience.adobe.com/#/downloads/content/software-distribution/de/campaign.html) her, um die neue Version herunterzuladen. Erfahren Sie [auf dieser Seite](../../installation/using/client-console-availability-for-windows.md), wie Sie die Konsolenaktualisierung allen Endbenutzern vorschlagen können.

_Montag, 22. März 2021_

* Korrektur einer Regression, die die Verwendung einiger Konsolenkomponenten wie der Datumsauswahl und der Bildverwaltung in Sendungen verhinderte. (NEO-31453, NEO-31454)

**Es ist nur eine Konsolenaktualisierung obligatorisch. Eine Serveraktualisierung ist nicht erforderlich.**

>[!NOTE]
>
> Stellen Sie eine Verbindung zu [Adobe Softwareverteilung](https://experience.adobe.com/#/downloads/content/software-distribution/de/campaign.html) her, um die neue Version herunterzuladen. Erfahren Sie [auf dieser Seite](../../installation/using/client-console-availability-for-windows.md), wie Sie die Konsolenaktualisierung allen Endbenutzern vorschlagen können.

_Mittwoch, 23. Dezember 2020_

>[!CAUTION]
>
> * Diese Version enthält ein neues Verbindungsprotokoll: Wenn Sie über Adobe Identity Service (IMS) eine Verbindung zu Campaign herstellen, ist sowohl für den Campaign-Server als auch für die Client-Konsole eine Aktualisierung zwingend erforderlich, um auch nach dem **30. Juni 2021** eine Verbindung zu Campaign herstellen zu können. [Weitere Informationen](../../technotes/using/ims-updates.md)
>
> * Diese Version enthält eine [Sicherheitskorrektur](https://helpx.adobe.com/de/security/products/campaign/apsb21-04.html): Die Aktualisierung ist zwingend erforderlich, um die Sicherheit Ihrer Umgebung zu erhöhen.



* Das Verbindungsprotokoll wurde aktualisiert, sodass es dem neuen IMS-Authentifizierungsmechanismus entspricht.
* Fehlerkorrektur – Es wurde ein Sicherheitsproblem behoben, um den Schutz vor SSRF-Problemen (Server Side Request Forgery) zu verbessern. (NEO-27777)

### ![](assets/do-not-localize/red_2.png) Version 19.2.3 – Build 9081 {#release-19-2-3-build-9081}

_Freitag, 7. Februar 2020_

**Neuheiten**

* Korrektur eines Regressionsfehlers aufgrund der Implementierung der SSL-Zertifizierung, der dazu führte, dass die Benutzerverbindung auf einem Windows-Server fehlschlug. (NEO-20629)
* Es wurde ein Problem behoben, bei dem im Menü **Versionsinformationen** eine falsche Versions-Tag-Nummer angezeigt wurde.


### ![](assets/do-not-localize/red_2.png) Version 19.2 – Build 9080 {#release-19-2-build-9080}

_Montag, 2. Dezember 2019_

**Neue Funktionen**

<table> 
 <thead> 
  <tr> 
   <th> <strong>California Consumer Privacy Act (CCPA)</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>CCPA ist das neue Datenschutzgesetz des US-Bundesstaates Kalifornien, das am 01. Januar 2020 in Kraft tritt und in dem die Anforderungen an den Datenschutz harmonisiert und neu geregelt werden. Der CCPA gilt für Adobe Campaign-Kunden, die Daten von Personen ("Datensubjekten") erfassen, die in Kalifornien wohnhaft sind.</p>
    <p> Zusätzlich zu den bereits verfügbaren Datenschutzfunktionen (einschließlich Zustimmungsverwaltung, Einstellungen zur Datenspeicherung und Benutzerrollen) hilft Adobe Campaign Ihnen bei der Vorbereitung auf CCPA:</p>
    <ul>
      <li>Recht auf Zugriff und Recht auf Löschung: Dazu nutzen wir die Funktionen, die wir analog dazu für die DSGVO ergänzt haben – <a href="https://helpx.adobe.com/de/campaign/kb/acc-privacy.html#righttoaccess">mehr dazu</a></li>
      <li>Sie können nachverfolgen, ob ein Verbraucher sich gegen den Verkauf von personenbezogenen Informationen entschieden hat. Dazu müssen Sie die Tabelle „Profile“ erweitern und ein Feld <strong>Opt-out für CCPA</strong> hinzufügen – <a href="https://helpx.adobe.com/de/campaign/kb/acc-privacy.html#ccpa">mehr dazu</a></li></td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>Workflow-Live-Monitoring</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>Sie können jetzt den Ausführungsstatus aller Workflows in Ihrer Instanz mithilfe vordefinierter Ansichten überwachen.</p>
   <p>Weitere Informationen finden Sie im <a href="../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status">entsprechenden Handbuch</a>.</p></td> 
  </tr> 
 </tbody> 
</table>


<table> 
 <thead> 
  <tr> 
   <th> <strong>Interaktive Inhalte mit AMP</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
<td> <p>Mit Adobe Campaign können Sie das neue interaktive <a href="https://amp.dev/about/email/">AMP für E-Mail</a>-Format ausprobieren, das es Marketing-Experten ermöglicht, AMP-Komponenten in Nachrichten einzuschließen, um das E-Mail-Erlebnis mit komplexen, dynamischen und interaktiven Inhalten zu verbessern, die direkt in der Nachricht selbst verarbeitet werden können.</p>
   <p> Diese Funktion ist als öffentliche Betaversion verfügbar.</p>
   <p>Weiterführende Informationen finden Sie in der <a href="../../delivery/using/defining-interactive-content.md">ausführlichen Dokumentation</a> und im <a href="https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/sending-messages/email-channel/defining-interactive-email-content-with-amp.html?lang=de">Tutorial-Video</a>.</p><br /></td> 
  </tr> 
 </tbody> 
</table>


<table> 
 <thead> 
  <tr> 
   <th> <strong>Sicherer SMS-Versand (TLS)</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
<td> <p>Sichere SMS werden nun über den erweiterten allgemeinen SMPP-Connector unterstützt. Dies ermöglicht eine verschlüsselte Verbindung zum Provider.</p> <p><strong>Warnung</strong> Diese Funktion erfordert ein aktuelles Zertifikat auf allen Servern. Ungültige, gesperrte oder abgelaufene Zertifikate führen zu Fehlern, die sich auf die gesamten SMS-Sendefunktionen auswirken.</p><p>Weitere Informationen finden Sie im <a href="https://helpx.adobe.com/de/campaign/kb/sms-connector-protocol-and-settings.html">entsprechenden Handbuch</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Verbesserungen bei der Sicherheit**

* Behebung von Sicherheitslücken im Zusammenhang mit der Skripterstellung über mehrere Sites hinweg in der Campaign-Oberfläche – Überprüfung der Eingabedaten und Ausgabecodierung. (NEO-16810)
* Es wurde ein Sicherheitsproblem bei der Profilautorisierung behoben, das den Zugriff auf nicht autorisierte Daten ermöglichen konnte, indem die Richtlinien für Anmeldebeschränkungen verstärkt wurden. (NEO-14445)

**Neuheiten**

* Optimierung des Speicherverbrauchs für Push-Benachrichtigungen.
* Zur Optimierung der Leistung und des Speicherplatzes wurde die Handhabung der Datei **login.log** verbessert. Die Datei wird nun in mehrere Dateien aufgeteilt, wobei pro Tag maximal 365 Dateien gespeichert werden – [mehr dazu](../../production/using/log-files.md)
* Das externe Microsoft Dynamics CRM-Konto kann jetzt mit Passwortdaten (Passwort + Benutzername) oder Zertifikat (privater Schlüssel) konfiguriert werden – [mehr dazu](../../installation/using/external-accounts.md#microsoft-dynamics-crm-external-account)
* Dem Hadoop FDA-Connector wurden einige Verbesserungen hinzugefügt, um die Zuverlässigkeit zu erhöhen
* Es wurde ein spezieller Schutzmechanismus hinzugefügt, bevor das Hochladen von öffentlichen Ressourcen auf den Server erlaubt wird.
* Es wurden neue [Campaign-Optionen](../../installation/using/configuring-campaign-options.md) hinzugefügt:
   * Mit der Konfigurationsoption **WdbcKillSessionPolicy** können Sie das Verhalten **Unbedingter Stopp** bei allen Workflows und PostgreSQL-Datenbankabfragen beeinflussen.
   * Mit der Option **NmsOperation_DeliveryPreparationWindow** können Sie die Anzahl der Tage festlegen, ab denen Sendungen mit inkonsistentem Status von der Zählung laufender Sendungen ausgeschlossen werden.
   * Mit der Option **WdbcOptions_TempDbName** können Sie eine separate Datenbank für Tabellen auf Microsoft SQL Server konfigurieren. Dadurch werden Backups und Replikation optimiert – [mehr dazu](../../production/using/rdbms-specific-recommendations.md#microsoft-sql-server)
   * Die Option **XtkCleanup_NoStats** wurde für PostgreSQL erweitert, um das Verhalten des Speicheroptimierungsschritts des Workflows für die Datenbankbereinigung besser zu steuern – [mehr dazu](../../production/using/database-cleanup-workflow.md#statistics-update)
* Der **logon()**-API wurde ein Mechanismus zur Kontosperrung hinzugefügt. Er verhindert alle weiteren Anmeldeversuche nach einer bestimmten Anzahl aufeinander folgender fehlgeschlagener Anmeldeversuche innerhalb eines bestimmten Zeitraums.
* Mit der neuen Option **Maximale Laufzeit der Personalisierung** in den Versandeigenschaften können Sie einen Timeout-Zeitraum für die Laufzeit der Personalisierung definieren, um zu verhindern, dass die Personalisierungsphase zu lange läuft – [mehr dazu](../../delivery/using/personalization-fields.md#timing-out-personalization)
* Die Option **ftp-Protokoll** wurde hinzugefügt, um Ihnen die Verwendung einer Proxy-Konfiguration für SFTP-Verbindungen zu ermöglichen – [mehr dazu](../../installation/using/file-res-management.md)
* Neue Unterstützung für den Proxy-Zugriff auf einen externen SFTP-Server für On-Premise-Umgebungen.
* Es wurde ein spezieller Schutzmechanismus hinzugefügt, um die Installation von Paketen zu verhindern, die nicht mit der Campaign-Instanz kompatibel sind – [mehr dazu](../../installation/using/installing-campaign-standard-packages.md)

_Veraltete Systeme_

Die folgenden Systeme sind jetzt für Campaign Classic-Implementierungen [veraltet](deprecated-features.md):
* Apache 2.2
* Centos 6

Vergewissern Sie sich, dass Sie unterstützte Versionen aller Systeme verwenden, die in der aktuellen Campaign-Kompatibilitätsmatrix aufgeführt sind – [mehr dazu](https://helpx.adobe.com/de/campaign/kb/compatibility-matrix.html)

_Campaign Mobile SDK_

Version 1.0.26 des iOS-SDK ist jetzt verfügbar. In diesem neuen Build wurde Unterstützung für iOS 13 hinzugefügt. Diese neue Version unterstützt jetzt die Benachrichtigungspriorität und den neuen Anmeldetoken-Verwaltungsprozess für iOS 13-Push-Benachrichtigungen. Wenn Sie Anwendungen auf einer früheren Version des SDK ausführen, müssen Sie Ihre Anwendungen mit dem neuen SDK neu kompilieren. Wenden Sie sich an die [Adobe-Kundenunterstützung](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html), um das SDK zu erhalten.

**Korrekturen**

* Fehlerkorrektur – Es wurde ein Absturzfehler behoben, der auftrat, wenn das Feld **Verknüpfte Tabelle hinzufügen** in der Workflow-Aktivität **Laden (RDBMS)** leer war. (NEO-12213)
* Es wurde ein Fehler behoben, der dazu führte, dass bestimmte Nachrichten nicht vom Mid-Sourcing-Server verarbeitet wurden. (NEO-12395)
* Es wurde ein Problem im Datenbankbereinigungs-Workflow behoben, das bei der Verwendung der Query Banding-Option mit Teradata auftrat. (NEO-12399)
* Es wurde ein Problem behoben, der sich auf die Versandanalyse mit Typologieregel einschließlich der Domäne „ne.jp“ auswirkte. (NEO-12609)
* Es wurde ein Problem im Zusammenhang mit SMS über TLS-Updates behoben, das zu einer restriktiveren Zertifikatrichtlinie führte. Diese Updates könnten bei einem veralteten Zertifikat zu einem Verbindungsfehler zwischen Marketing- und Mid-Sourcing-Servern führen. (NEO-17698)
* Es wurde ein Problem behoben, das bei Verwendung der Schaltfläche **Verbindung testen** in einem externen Konto in einer Mid-Sourcing-Umgebung mit Vault-Authentifizierung auftrat. (NEO-12722)
* Es wurde ein Problem bei Abfragen mit Datumsfunktionen mit einer FDA-Hadoop-Verbindung behoben. (NEO-12847)
* Es wurde ein Problem beim Ersetzen eines Bildes im E-Mail-Editor behoben. (NEO-13098)
* Es wurde ein Problem behoben, das nach der Aktualisierung bei Ordnern zu Fehlern führen konnte, die gelöscht oder an einen anderen Ort verschoben worden waren. (NEO-13118)
* Es wurde ein Problem bei der Bildanzeige behoben, wenn die Option **Bilder nach Bildschirmgröße von Gerät definieren** in LINE-Nachrichten verwendet wurde. (NEO-13228)
* Es wurde ein Problem bei der Sendungsvorbereitung behoben, wenn die Option **Doppelte Adressen vom Versand ausschließen** nicht ausgewählt wurde. (NEO-13240)
* Es wurde ein Problem in den Workflows behoben, wenn die Aktivität **Dateiübertragung** zum Herunterladen von Dateien mit der Option **Quelldateien nach der Übertragung löschen** verwendet wurde, wobei der Name ein Leerzeichen enthielt. (NEO-13411)
* Es wurde ein Problem mit der Tomcat-Cache-Bereinigung behoben, das zu Speicherproblemen führen konnte. (NEO-13456)
* Es wurde ein Problem behoben, durch das das native Package **Angebotsmodul-Kontrolle durch die Ausführungsinstanz** auf einer vorhandenen Kontrollinstanz installiert wurde, die in Microsoft SQL 2017 ausgeführt wird. (NEO-13539)
* Fehlerkorrektur – Es wurde ein Absturzproblem der Konsole behoben, das auftreten konnte, wenn die Option &quot;Getrackte URLs&quot; in einer E-Mail im Tab **Textinhalt** aufgrund einer nicht initialisierten Variablen deaktiviert wurde. (NEO-13545)
* Es wurde ein Codierungsfehler bei chinesischen Absendernamen behoben. (NEO-13837)
* Es wurde ein Fehler behoben, der bei der Anzeige von Umfrageantwortdaten aus dem Explorer auftreten konnte. (NEO-14590)
* Es wurde ein Problem behoben, das zu Diskrepanzen zwischen der Klassifizierung des Versandlogs und der Quarantänetabelle führen konnte. (NEO-16547)
* Es wurde ein Problem mit DKIM-Schlüsseln behoben, die nicht in E-Mails eingebettet waren. (NEO-16804)
* Es wurde ein Problem behoben, bei dem der falsche Fehlercode angezeigt wurde, wenn ein ungültiges Sitzungstoken im Kontext von API-Aufrufen zum Auslösen von Ereignissen verwendet wurde. Der Fehlercode lautete „HTTP 200 OK“ anstelle von „HTTP 403 Forbidden“. (NEO-16826)
* Es wurde ein Problem bei der Anzeige von Berichten zum Versand über den Web-Zugriff behoben. (NEO-17015)
* Es wurde ein IMS-Authentifizierungsproblem bei der Anmeldung bei Adobe Campaign behoben. (NEO-17312)
* Es wurde ein Problem behoben, das verhinderte, dass E-Mails in Quarantäne durch den Datenschutzverwaltungsprozess gelöscht werden konnten. (NEO-17314)
* Es wurden Durchsatzprobleme mit der SQL-Datenbank nach dem Upgrade auf 9031 behoben. (NEO-17558)
* Es wurde ein Problem behoben, das den CRM-Connector mit Salesforce betraf. (NEO-17712)
* Es wurde ein Timeout-Problem beim Importieren von Daten aus einem externen SFTP behoben. (NEO-19723)
* Es wurde ein Problem beim Zugriff auf prädiktive Modelle behoben. (NEO-19713)
* Es wurde ein Problem behoben, das sich auf Stichproben in der **Aufspaltungs**-Aktivität im Workflow mit der Hadoop FDA-Datenbank auswirkte. (NEO-16636)
* Fehlerkorrektur – Es wurde eine Regression bei Oracle korrigiert, die dazu führte, dass einige Funktionen nach dem Postupgrade als ungültig angesehen wurden. (NEO-12759)


## Version 19.1{#release-19-1}

### ![](assets/do-not-localize/limited_2.png) Version 19.1.8 – Build 9039 {#release-19-1-8-build-9039}

_Donnerstag, 15. April 2021_

* Fehlerkorrektur – Es wurde eine Regression in der Client-Konsole korrigiert, die dazu führte, dass im IMS-Verbindungsfenster fortwährend Fehlermeldungen ausgegeben wurden. (NEO-34821)
* Fehlerkorrektur – Eine Regression blockiert nicht mehr den Export von Workflow-Daten in eine FDA-Datenbank (Teradata, Snowflake).

**Es ist nur eine Konsolenaktualisierung obligatorisch. Eine Serveraktualisierung ist nicht erforderlich.**

>[!NOTE]
>
> Stellen Sie eine Verbindung zu [Adobe Softwareverteilung](https://experience.adobe.com/#/downloads/content/software-distribution/de/campaign.html) her, um die neue Version herunterzuladen. Erfahren Sie [auf dieser Seite](../../installation/using/client-console-availability-for-windows.md), wie Sie die Konsolenaktualisierung allen Endbenutzern vorschlagen können.

_Montag, 22. März 2021_

* Korrektur einer Regression, die die Verwendung einiger Konsolenkomponenten wie der Datumsauswahl und der Bildverwaltung in Sendungen verhinderte. (NEO-31453, NEO-31454)

**Es ist nur eine Konsolenaktualisierung obligatorisch. Eine Serveraktualisierung ist nicht erforderlich.**

>[!NOTE]
>
> Stellen Sie eine Verbindung zu [Adobe Softwareverteilung](https://experience.adobe.com/#/downloads/content/software-distribution/de/campaign.html) her, um die neue Version herunterzuladen. Erfahren Sie [auf dieser Seite](../../installation/using/client-console-availability-for-windows.md), wie Sie die Konsolenaktualisierung allen Endbenutzern vorschlagen können.

_Mittwoch, 16. Dezember 2020_

>[!CAUTION]
>
> * Diese Version enthält ein neues Verbindungsprotokoll: Wenn Sie über Adobe Identity Service (IMS) eine Verbindung zu Campaign herstellen, ist sowohl für den Campaign-Server als auch für die Client-Konsole eine Aktualisierung zwingend erforderlich, um auch nach dem **30. Juni 2021** eine Verbindung zu Campaign herstellen zu können. [Weitere Informationen](../../technotes/using/ims-updates.md)
> * Diese Version enthält eine [Sicherheitskorrektur](https://helpx.adobe.com/de/security/products/campaign/apsb21-04.html): Die Aktualisierung ist zwingend erforderlich, um die Sicherheit Ihrer Umgebung zu erhöhen.
> * Wenn Sie die Experience Cloud-Triggers-Integration über die OAuth-Authentifizierung verwenden, müssen Sie wie [auf dieser Seite](../../integrations/using/configuring-adobe-io.md) beschrieben zu Adobe I/O wechseln. Die alte oAuth-Authentifizierungsmethode mit Campaign [wurde eingestellt](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411?profile.language=de) am **September 2021**. Gehostete Umgebungen profitieren von einer Verlängerung bis zum **23. Februar 2022**. Wenden Sie sich als On-Premise- oder Hybrid-Kunde an die Kundenunterstützung von Adobe, um den Support bis zum Februar 2022 zu verlängern. Dazu müssen Sie Adobe [die AppID der OAuth-Anwendung](../../integrations/using/configuring-pipeline.md?lang=en#step-optional) nennen.



**Verbesserungen**

* Das Verbindungsprotokoll wurde aktualisiert, um dem neuen IMS-Authentifizierungsmechanismus zu folgen.
* Die Authentifizierung für die Triggers-Integration, die ursprünglich auf der oAUTH-Authentifizierung basierte und für den Zugriff auf die Pipeline eingerichtet wurde, wurde geändert und in Adobe I/O verschoben. [Weitere Infos](../../integrations/using/configuring-adobe-io.md)
* Nach dem Ende der Unterstützung für das ältere Binärprotokoll von iOS-APN werden alle Instanzen, die dieses Protokoll verwenden, während des Postupgrades auf das HTTP/2-Protokoll aktualisiert.
* Fehlerkorrektur – Es wurde ein Sicherheitsproblem behoben, um den Schutz vor SSRF-Problemen (Server Side Request Forgery) zu verbessern. (NEO-27777)
* Fehlerkorrektur – Es wurde ein Problem behoben, das zur Deaktivierung des SMPP-Connectors nach einem Verbindungsfehler führte, was die Ausführung weiterer SMS-Sendungen verhinderte und zu Leistungsproblemen führte.
* Fehlerkorrektur – Beim Generieren eines Berichts mithilfe einer Workflow-Aktivität werden jetzt korrekte Prozentwerte angezeigt. (NEO-14314)
* Fehlerkorrektur – Es wurde ein Problem bei der Sendungsvorbereitung behoben, das auftrat, wenn die Option **Doppelte Adressen vom Versand ausschließen** nicht ausgewählt wurde. (NEO-13240)
* Fehlerkorrektur – Workflows schlagen beim Ausführen einer Aktivität vom Typ **Anreicherung** jetzt nicht mehr fehl. (NEO-17338)
* Fehlerkorrektur – Es wurde ein Fehler in Workflows behoben, der auftrat, wenn Datensätze aus einer externen Datenbank abgerufen und in die Campaign-Datenbank eingefügt wurden. (NEO-26359)
* Fehlerkorrektur – Es wurde ein Problem behoben, das zum Absturz des Servers führte, indem eine Speicherbeschädigung beim Bereinigen des Ausdrucks-Parsers verhindert wurde.
* Fehlerkorrektur – Es wurde ein Problem behoben, durch das die Funktion **NoNull** nach der Aktualisierung auf Build 9032 in Oracle-Datenbanken nicht mehr funktionierte. (NEO-26488)
* Fehlerkorrektur – Es wurde ein Fehler behoben, der beim Bearbeiten der Beschreibung einer Kampagnenvorlage dazu führte, dass die Schaltfläche **Speichern** beim Einfügen von Symbolen wie beispielsweise japanischen Zeichen nicht angezeigt wurde. (NEO-27071)
* Fehlerkorrektur – Es wurde ein Fehler behoben, durch den die Beschreibung einer Kampagne oder Kampagnenvorlage nicht gespeichert werden konnte, wenn vor dem Klicken auf die Schaltfläche **Speichern** außerhalb des Fensters geklickt wurde. (NEO-27449)
* Fehlerkorrektur – Es wurde ein Problem auf Proxy-Konfigurationsebene behoben, durch das Sie sich nach dem letzten Windows 10-Update nicht mehr bei Adobe Campaign anmelden konnten. (NEO-27813)
* Fehlerkorrektur – Es wurde ein Problem im Zusammenhang mit der Verwaltung von Leerzeilen in Protokolldateien behoben, das zu Fehlern im MTA-Prozessverhalten und zu Leistungseinbußen beim Versand führte.

**Technische Entwicklungen**

Tomcat wurde von Version 7 (7.0.103) auf Version 8 (8.5.57) aktualisiert. Das `tomcat-7`-Verzeichnis wird durch ein `tomcat-8`-Verzeichnis ersetzt. Unter Windows werden _is_neolane_setup.vbs_ und _apache_neolane.conf_ jetzt im `conf`-Verzeichnis installiert (anstatt wie bisher in `tomcat-7/conf`). Unter Linux wird _apache_neolane.conf_ jetzt im `conf`-Verzeichnis installiert.

Unter Linux verwendet der Start des nlserver-Dienstes jetzt eine systemd-Einheit anstelle des Scripts /etc/init.d/nlserver6. Die Migration zum neuen Startschema wird automatisch ausgeführt, wenn Sie das Package 19.1.8 installieren. Der Befehl /etc/init.d/nlserver6 ist weiterhin verfügbar, dient aber zum Interagieren mit dem nlserver-Dienst (Start, Neustart, Stopp, usw.). Wir empfehlen, direkt den Befehl systemctl zu verwenden.


### ![](assets/do-not-localize/red_2.png) Version 19.1.7 – Build 9036 {#release-19-1-7-build-9036}

_Dienstag, 15. September 2020_

**Verbesserungen**

* Die Verwendung von nlsrvmod für Apache 2.4-Threads wurde verbessert, um nlsrvmod-Abstürze zu beheben.
* Fehlerkorrektur – Es wurde ein Problem bei der Verwendung der Dateiübertragungsaktivität mit einem externen Azure-Konto und einer SSL-Verschlüsselung behoben. Die Verbindung wurde über HTTP statt über HTTPS hergestellt. (NEO-26720)
* Fehlerkorrektur – Es wurde ein Problem mit dem URL-Cache-Mechanismus behoben, bei dem die Bezeichnung oder Kategorie nicht abgerufen wurde.
* Fehlerkorrektur – Es wurde ein Problem behoben, das dazu führte, dass Mirrorseiten-URLs in E-Mail-Sendungen fehlerhaft definiert wurden (aufgrund einer falschen ASCII-Zeichensteuerung). (NEO-26084)
* Die Liste &quot;jarsToSkip&quot; in &quot;catalina.properties&quot; wurde aktualisiert, um den Verweis auf eine nicht mehr verwendete JAR-Datei zu entfernen (iOS-Benachrichtigungen).
* Fehlerkorrektur – Es wurde ein Regressionsfehler behoben, der eine Veröffentlichung nach einem Postupgrade verhinderte.
* Fehlerkorrektur – Es wurde eine Regression mit nativen Versandberichten korrigiert, die beim Exportieren in PDF abgeschnitten dargestellt wurden. (NEO-25757)
* Fehlerkorrektur – Der Codierungs-Parameterwert wird bei Weiterleitung von einer Tracking-URL nicht mehr gelöscht (Auswirkung auf japanische Zeichen). (NEO-25637)
* Fehlerkorrektur – Nicht signierte Links von personalisierten Domains werden nicht mehr blockiert, wenn sie zulässig sind. (NEO-25210)
* Fehlerkorrektur – Es wurde eine Regression korrigiert, die berechnete Felder in einem Workflow beeinträchtigte und dazu führte, dass der Workflow fehlschlug. (NEO-25194)
* Fehlerkorrektur – Es wurde ein Kompatibilitätsproblem mit Microsoft Dynamics (ab Version 8.2) behoben, das die Ausführung einiger API-Aufrufe verhindern konnte (RetrieveAllEntities). (NEO-24528)
* Fehlerkorrektur – Es wurde ein Regressionsfehler bei Verwendung der ACS Connector-Funktion behoben, der die Verbindung zu einer Campaign Standard-Instanz verhinderte (fehlerhafte Verwaltung der FOH-/FOH2-Verbindung). (NEO-23433)
* Fehlerkorrektur – Es wurde ein Regressionsfehler bei der Datenbankverbindung behoben, der dazu führte, dass der Webserver aufgrund eines Problems mit der Datenbankkodierung ständig neu gestartet wurde. Dies konnte zu einem übermäßigen Verbrauch führen. (NEO-23264)
* Fehlerkorrektur – Es wurde ein Problem mit dem Datenbankbereinigungs-Workflow behoben, der aufgrund einer nicht verwalteten Datenquelle fehlschlagen konnte. (NEO-23160, NEO-23364)
* Der Bereinigungs-Workflow bereinigt jetzt abgelaufene Listen in Stapeln von 100 anstelle einzeln.
* Nach dem Wechsel zum [neuen Sequenz-ID-Mechanismus](https://helpx.adobe.com/de/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence) werden alle Web-Anwendungen, die die Empfänger-Tabelle aktualisieren, während des Postupgrades erneut veröffentlicht.
* Fehlerkorrektur – E-Mails werden jetzt auch gesendet, wenn außerhalb des HTML-Inhalts-Tags Javascript-Code vorhanden ist. (NEO-18628)
* Fehlerkorrektur – Trackingindikatoren für Transaktionsnachrichten werden jetzt vom Tracking-Workflow aktualisiert. (NEO-17770)
* Die Leistung des Datenbankaktualisierungs-Assistenten wurde verbessert, um weniger SQL-Anweisungen auszugeben und die Antwortzeit zu optimieren.
* Fehlerkorrektur – Es wurde ein Absturzproblem der Konsole behoben, das auftreten konnte, wenn die Option &quot;Getrackte URLs&quot; in einer E-Mail im Tab **Textinhalt** aufgrund einer nicht initialisierten Variablen deaktiviert wurde. (NEO-13545)
* Fehlerkorrektur – Es wurde ein Problem behoben, das das Hochladen von Dateien in einer Dateiübertragungsaktivität mit einem externen Azure Blob Storage-Konto aufgrund einer nicht initialisierten Variablen (m_pCurlReader) verhinderte. (NEO-13717)
* Fehlerkorrektur – Es wurde ein Problem mit einem Postupgrade behoben, durch das Apache und der Webserver vor der erneuten Veröffentlichung der Web-Applikation deaktiviert wurden. (NEO-27155)
* Fehlerkorrektur – Es wurde eine Regression korrigiert, die dazu führte, dass bei der Zeiteinstellung in einer Workflow-Aktivität **Planung** eine falsche Zeitzone ausgewählt wurde.


### ![](assets/do-not-localize/red_2.png) Version 19.1.6 – Build 9035 {#release-19-1-6-build-9035}

>[!CAUTION]
>
>Dieser Build ist nur für On-Premise-Installationen gedacht. Bei Hybridbereitstellungen wird von gehosteten Instanzen weiterhin Build 9032 ausgeführt. Aktualisieren Sie Ihre Marketing-Instanz nicht auf den Build 9035, da er nicht mit Build 9032 kompatibel ist.

_Donnerstag, 3. Oktober 2019_

**Neuheiten**

* Fehlerkorrektur – Die Verwendung von CRM-Connector für Salesforce funktioniert nun problemlos. (NEO-17712)
* Fehlerkorrektur – Ein Indexfehler verursacht beim Senden von Transaktionsnachrichten keine Leistungsprobleme mehr.
* Fehlerkorrektur – Beim Senden von Nachrichten treten keine Leistungsprobleme mehr auf. (NEO-17558)
* Es wurde ein Fehler behoben, der dazu führte, dass bestimmte Nachrichten nicht vom Mid-Sourcing-Server verarbeitet wurden. (NEO-12395)
* Fehlerkorrektur – Die SQL-Data-Management-Aktivität lässt sich jetzt voll nutzen (es fehlte die spezifische „SQL-Data-Management“-Berechtigung).

### ![](assets/do-not-localize/red_2.png) Version 19.1.5 – Build 9033{#release-19-1-5-build-9033}

_Dienstag, 13. August 2019_

**Neuheiten**

* Fehlerkorrektur – Bei der SQL-Anweisung &#39;SELECT COUNT&#39; wird in der Data-Management-Aktivität nicht mehr die Standard-Datenbank, sondern die FDA-Datenbank zur Extraktion herangezogen.
* Um die Möglichkeiten der Kundeninfrastruktur zu verbessern, ist jetzt eine SFTP-Proxy-Deklaration in der Server-Konfigurationsdatei verfügbar.
* Fehlerkorrektur – Es wurde ein Absturzfehler behoben, der auftrat, wenn das Feld **Verknüpfte Tabelle hinzufügen** in der Workflow-Aktivität **Laden (RDBMS)** leer war. (NEO-12213)
* Fehlerkorrektur – Jetzt kann die midEmitter-Package-Installation über eine Befehlszeile fehlerfrei installiert werden.
* Eine neue Authentifizierungsoption wurde hinzugefügt, die in AC Connector in Verbindung mit Microsoft Dynamics OAuth-Zugangsdaten unterstützt. (NEO-11982)
* Fehlerkorrektur – Es wurde ein Problem bei der Verwaltung der UUID (Unique Universal Identifier) behoben, das dazu führte, dass die Workflow-Aktivitäten &quot;Abfrage&quot; und &quot;Laden der Daten&quot; mit Hive FDA fehlschlugen.
* Fehlerkorrektur – Es wurde eine Regression bei Oracle korrigiert, die dazu führte, dass einige Funktionen nach dem Postupgrade als ungültig angesehen wurden. (NEO-12759)
* Fehlerkorrektur – Es wurde eine Regression korrigiert, die dazu führte, dass bei der Zeiteinstellung in der Workflow-Aktivität &quot;Planung&quot; eine falsche Zeitzone ausgewählt wurde.

### ![](assets/do-not-localize/green_2.png) Version 19.1.4 – Build 9032{#release-19-1-4-build-9032}


>[!NOTE]
>
>[!DNL Gold Standard]-Versionen von 19.1.4 sind auf dieser [Seite](../../rn/using/gold-standard.md) aufgeführt.


### ![](assets/do-not-localize/red_2.png) Version 19.1.2 – Build 9029{#release-19-1-2-build-9029}

_Freitag, 21. Juni 2019_

**Verbesserungen bei der Sicherheit**

* Zur Verbesserung der Sicherheit wurde die Java-Bibliothek (Netty) auf die aktuelle Version (4.1.34) aktualisiert. (NEO-12788)

**Neuheiten**

* Korrektur der mit der Sdomain-Spaltenverwaltung zusammenhängenden Regression – E-Mails können jetzt bei allen Konfigurationen gesendet werden.
* Zur Leistungssteigerung wurde das Attribut _operation=&quot;none&quot; zu rtEvent-SOAP-Aufrufen hinzugefügt, um die Anfragen &quot;UPDATE AUSWÄHLEN&quot; zu vermeiden.
* Behebung eines Workflow-Anzeigeproblems bei ausgehenden Transitionen nach der Testaktivität. (NEO-12727)
* Jetzt können in Microsoft Dynamics erstellte Platzhaltereinträge während des Import-Workflows gelöscht werden.
* Erweiterte Berechtigungen zur Ausführung des Sicherheitszonen-Package bei der Verwendung eines internen Kontos.


### ![](assets/do-not-localize/red_2.png) Version 19.1 – Build 9026{#release-19-1-build-9026}

_Donnerstag, 30. Mai 2019_

**Neue Funktionen?**

<table> 
 <thead> 
  <tr> 
   <th> Funktion<br /> </th> 
   <th> Beschreibung<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Control Panel<br /> </td> 
   <td> <p>Sie können die Einstellungen Ihrer SFTP-Server mittels Speicherüberwachung verwalten, IP-Adressen auf die Zulassungsliste setzen und für jede Instanz SSH-Schlüssel installieren, um die Effizienz Ihrer Arbeit als Admin-Benutzer zu steigern. Beachten Sie, dass das Control Panel von jetzt an nur für Kunden verfügbar ist, die auf AWS gehostet werden (<a href="https://experiencecloud.adobe.com/campaign/controlpanel/">melden Sie sich noch heute über Experience Cloud an</a>).</p> <p>Weiterführende Informationen finden Sie in der <a href="https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=de">ausführlichen Dokumentation</a> und in <a href="https://experienceleague.adobe.com/docs/campaign-classic-learn/control-panel/control-panel-overview.html?lang=de">diesem Video</a>. </p><p>Hinweis: Für den Zugriff auf das Control Panel ist keine Aktualisierung auf den aktuellen Campaign-Build nötig.</p> </td> 
  </tr> 
    <tr> 
   <td> Audit-Protokoll<br /> </td> 
   <td> <p>Als Administrator können Sie die Produktivität steigern, indem Sie Änderungen in der Adobe Campaign Classic-Instanz überwachen und verwalten. Im Audit-Protokoll werden die Aktionen protokolliert, die in Quellschemata, Workflows und Optionen durchgeführt wurden. Damit können Sie schnell erkennen, ob ein Element angelegt, geändert oder gelöscht wurde.</p><p>Weiterführende Informationen finden Sie im <a href="../../production/using/audit-trail.md">entsprechenden Handbuch</a> und im <a href="https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/monitoring/audit-trail.html?lang=de">Anleitungsvideo</a>.</p></td> 
  </tr> 
  <tr> 
   <td> Schutzmechanismen, Stabilität und Skalierbarkeit<br /> </td> 
   <td> In Campaign Classic wurde eine Reihe von Verbesserungen vorgenommen. Die Änderungen in den Bereichen Schutzmechanismen, Stabilität und Skalierbarkeit werden im Folgenden erläutert.<br /> </td> 
  </tr> 
  <tr> 
   <td> Aktualisierung der Kompatibilitätsmatrix<br /> </td> 
   <td> Mit dieser neuen Version unterstützt Adobe Campaign nun die folgenden Datenbanksysteme. Siehe <a href="https://helpx.adobe.com/de/campaign/kb/compatibility-matrix.html">Kompatibilitätsmatrix</a>.<br /> 
    <ul> 
     <li> <p>Oracle 18c</p> </li> 
     <li> <p>MySQL 5.7 (FDA)</p> </li> 
     <li> <p>SQL Server 2017</p> </li> 
     <li> <p>Teradata 16 (FDA)</p> </li> 
     <li> <p>PostgreSQL 11</p> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

**Verbesserungen bei der Sicherheit**

* Aus Sicherheitsgründen können bei der Verwendung der Option **[!UICONTROL Vorab-Bearbeitung der Datei vorsehen]** in der Workflow-Aktivität **[!UICONTROL Laden (Datei)]** keine beliebigen Befehle mehr eingefügt werden. Eine Dropdown-Liste ist nun verfügbar, in der Sie aus drei Optionen auswählen können: **[!UICONTROL Keine]**, **[!UICONTROL Dekomprimierung]** (zcat) oder **[!UICONTROL Entschlüsseln]** (gpg). Das Sicherheits-Flag XtkSecurity_Disable_Preproc wurde hinzugefügt. Für Neukunden wird diese Option auf 0 gesetzt. Für Bestandskunden wird diese Option durch das Postupgrade auf 1 gesetzt, um das bisherige Verhalten beizubehalten. Siehe diesen [Abschnitt](../../workflow/using/data-loading--file-.md).
* Es wurde ein Problem mit der Sichtbarkeit des Passworts behoben, das auftrat, wenn beim Testen der Verbindung eines externen FDA-Kontos keine Zeitzone festgelegt war.
* Die PDFBox-Bibliothek wurde entfernt.
* Tomcat wurde auf Version 7.0.93 aktualisiert.
* Es wurde ein Problem mit der Token-Sichtbarkeit behoben, das auftrat, wenn das Security-Token ungültig war.
* Ein potenzielles Problem bei XTK-Injections in WSDL JSP (schemawsdl.jsp) wurde behoben.
* Die Speicherung von Zugangsdaten und Passwörtern im Quellcode und im Speicher der Anwendung wurde optimiert.
* Die Anzeige personenbezogener Daten wurde weiter eingeschränkt. (NEO-12339, NEO-12396, NEO-12398, NEO-12339, NEO-12667)
* Bei der Verwaltung von geheimen Schlüsseln treten jetzt keine Abweichungen mehr auf.
* Der gleiche allgemeine Fehler wird nun bei fehlgeschlagenen Anmeldeversuchen mit einem gültigen oder ungültigen Benutzernamen angezeigt.
* Die Benennung von hochgeladenen Dateien wurde verbessert.
* Die neue Option XtkSecurity_Disable_GetSetEnv wurde hinzugefügt, um die Verwendung der Funktionen setEnv und getEnv zu blockieren.
* Sensible Informationen werden jetzt im Stack Trace der Anwendung verborgen.

**Verbesserungen bei Schutzmechanismen, Stabilität und Skalierbarkeit**

* Lebensdauer – Nutzungsoptimierung der XtkNewId-Sequenz: Die leistungsintensivsten Tabellen wurden aus der XtkNewId-Sequenz in spezielle Sequenzen verschoben – [mehr dazu](https://helpx.adobe.com/de/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence)
* FDA über HTTP v2: Das FDA über HTTP-Protokoll wird häufig bei hybriden Implementierungen verwendet, insbesondere für den Abruf von Broadlogs und die Versandvorbereitung. Die Stabilität wurde verbessert, um Netzwerkprobleme und mögliche Fehler beim Abrufen oder Senden von Daten zu vermeiden. Dies setzt voraus, dass die Builds an beiden Enden der Verbindung auf dem neuesten Stand sind, da ansonsten das alte Protokoll weiterhin verwendet wird.
* Tracking-Workflow: Die Stabilität des Tracking-Workflows wurde verbessert. Mehrere Probleme im Zusammenhang mit Trackinglog-Einfügungen/-Aktualisierungen und der individuellen URL-Tracking-Anpassung wurden behoben. Darüber hinaus erkennt der Tracking-Workflow jetzt Trackinglog-Probleme, die zu Fehlern führen könnten, und stoppt den Workflow. Diese Probleme werden jetzt verworfen und nicht mehr verarbeitet.
* Bereinigungs-Workflow: Der Bereinigungs-Workflow wurde verbessert, um mögliche Fehler und Unterbrechungen zu vermeiden. Dadurch wird auch die Größe und Leistungsfähigkeit der Datenbank optimiert.
* In Transaktionsnachrichten eingebettete Bilder: Jetzt werden in Transaktionsnachrichten eingebettete Bilder vollständig unterstützt, um mögliche Abstürze oder das Fehlen von Bildern zu vermeiden.
* Datenbankgröße – XtkJobLog: Dieser Tabelle wurde ein Bereinigungsmechanismus hinzugefügt, der sich positiv auf die Datenbankgröße auswirkt.
* BCC-Archivierung: Die Standardparameter für die BCC-Archivierung wurden geändert, um die Archivierungsgeschwindigkeit zu erhöhen – [mehr dazu](../../installation/using/email-archiving.md#parameters)
* Aktualisierung der Datenbankstruktur: Die Ausführung von SQL-Anfragen, die mit dem Assistenten zur Aktualisierung der Datenbankstruktur erzeugt werden, wurde beschleunigt.
* Schutzmechanismen bei Benutzeraktionen: Mehrere Schutzmechanismen wurden implementiert, um Benutzer an der Durchführung von Aktionen zu hindern, die die Integrität der Plattform beeinträchtigen könnten. Eingebaute Schemata können nicht mehr über die Benutzeroberfläche gelöscht werden. Außerdem kann die XML-Quelldatei des Workflows nicht mehr von Nicht-Administratoren bearbeitet werden.
* Zwei neue Optionen wurden zur Verfügung gestellt: **XtkSecurity_Restrict_EditXML** (ermöglicht Ihnen, die Bearbeitung des XML-Codes von Sendungen zu deaktivieren) und **NmsOperation_OperationMgtDebug** (ermöglicht Ihnen, die Ausführung des technischen Workflows operationMgt zu überwachen) – [mehr dazu](../../installation/using/configuring-campaign-options.md)

**Sonstige Änderungen**

* Push-Benachrichtigungen: Die die Thread-ID-Option für iOS Push wird jetzt unterstützt.
* Die Verwaltung langer Indexnamen wurde verbessert, was andernfalls Probleme mit dem Postupgrade verursachen könnte.
* Wenn während der Analyse eines Deco-mail-Versands der Veröffentlichungsmodus im Softwareverteilungs-Assistenten auf **[!UICONTROL Keine]** gesetzt ist, wird ein Fehler angezeigt und die Analyse wird angehalten: &quot;Für den Veröffentlichungsmodus ist Keiner ausgewählt: Bild kann nicht eingebettet werden. Bilder werden nicht auf Feature Phone angezeigt.&quot; (NEO-12208)
* Die Broadlog-Verwaltung für Transaktionsnachrichten wurde verbessert. Wenn Broadlogs von der Ausführungsinstanz mit der Kontrollinstanz synchronisiert werden, wird das Feld @lastModified auf das aktuelle Systemdatum aktualisiert. Für Kontrollinstanzen wurde die Option MC_Update_BlLastModified hinzugefügt. &quot;True&quot; bedeutet, dass das aktuelle Datum in der Kontrollinstanz verwendet wird (Standardverhalten). &quot;False&quot; bedeutet, dass das @lastModified-Datum des Broadlogs der Ausführungsinstanz verwendet wird. (NEO-12579)
* In den temporären Coupon-Tabellen wurden Indizes hinzugefügt, um den Versand zu optimieren. (NEO-12437)
* In der Analytics-Integration ist nun das Abrufen von AAM-Segmentdaten mit %-Zeichen erlaubt. (NEO-12025)
* Das Datensatzlimit von 10.000 wurde in der Workflow Heatmap entfernt, um ein Problem mit fehlenden Daten zu beheben. (NEO-12329)
* Open Office wird nicht unterstützt und wurde nun vollständig aus der Anwendung entfernt. Wenn Sie Open Office verwendet haben, wechseln Sie zu Libre Office, da Open Office ab 19.1. nicht mehr funktioniert.
* Sie können nun den Schreibzugriff auf die Daten-Update-Aktivität in Workflows über die sysfilter-Attribute einschränken – [mehr dazu](../../configuration/using/filtering-schemas.md)

**Korrekturen**

* Fehlerkorrektur – Das Zertifikat kann jetzt für Benachrichtigungen in iOS Mobile Push hochgeladen werden.
* Fehlerkorrektur – Bei Push-Transaktionsbenachrichtigungen stürzt der Server nicht mehr ab. Weitere Absturzprobleme wurden behoben.
* Fehlerkorrektur – Berichte zu Benutzeraktivitäten und Tracking-Berichten für den offenen Versandindikator stimmen jetzt überein. (NEO-11742)
* Fehlerkorrektur – Die IMS-Anmeldung funktioniert jetzt einwandfrei.
* Fehlerkorrektur – Alle aus der Bibliothek hinzugefügten Bilder sind jetzt auch im Versand vorhanden. (NEO-11900)
* Fehlerkorrektur – Das Extrahieren von Angebotsdetails in einem Briefpost-Versand funktioniert jetzt einwandfrei. (NEO-11700)
* Fehlerkorrektur – Die Leistung von SMS-Transaktionsnachrichten wird nun nicht mehr beeinträchtigt. (NEO-9812)
* Fehlerkorrektur – Jetzt stürzt die Konsole nicht mehr ab, wenn die Option &quot;In einer externen Datei definiert&quot; für die Hauptzielgruppe eines Versands verwendet wird. (NEO-12349)
* Fehlerkorrektur – Nachrichten an Empfänger in japanischen Domains (.JP) können jetzt problemlos analysiert werden. (NEO-12246)
* Fehlerkorrektur – Die Werteverteilung mit einer 1:N-Relation wird jetzt korrekt angezeigt. (NEO-12212, NEO-11820)
* Fehlerkorrektur – Nach einem Postupgrade kommt es in den MTA-Logs zu keinen NmsMxDomain-Fehlern mehr. (NEO-12752)
* Fehlerkorrektur – Die Option &quot;Alle Zusatzdaten der Hauptmenge beibehalten&quot; funktioniert jetzt in einer Anreicherungsaktivität eines Workflows einwandfrei. (NEO-13291)
* Fehlerkorrektur – Beim Versand von Push-Benachrichtigungen über HTTP2 stürzt Tomcat nicht mehr ab. (NEO-12701)
* Fehlerkorrektur – Die HTTP-Abfrage-API wartet jetzt, bis alle Callbacks beendet sind. (NEO-12628)
* Fehlerkorrektur – Die Berechnung von Trackingindikatoren für Transaktionsnachrichten funktioniert jetzt einwandfrei. (NEO-12529)
* Fehlerkorrektur – Die Themen in der Angebotsverwaltung können jetzt problemlos verwendet werden. (NEO-11804)
* Fehlerkorrektur – Beim Versand von Push-Benachrichtigungen treten keine Leistungsprobleme mehr auf. (NEO-11787)
* Fehlerkorrektur – Die Vorschau einer ausgehenden XML- oder CSV-Datei in der Angebotsverwaltung für einen Briefpost-Versand funktioniert jetzt einwandfrei. (NEO-11290)
* Fehlerkorrektur – Die Installation des Packages **Managing Social Networks** (Social Marketing) funktioniert jetzt einwandfrei. (NEO-12081)
* Fehlerkorrektur – Jetzt können alle Webanwendungen gelöscht werden. Zuvor war dies auch dann nicht möglich, wenn Sie die richtigen Zugriffsberechtigungen hatten. (NEO-12072)
* Fehlerkorrektur – Jetzt werden beim Export und anschließendem Import eines Objekts über XML keine Werte mehr überschrieben. Die Option XtkExport_IncludeDefaultValues wurde hinzugefügt. Wenn der &quot;True&quot; (Standardverhalten) ausgewählt ist, werden alle Werte exportiert. Wenn &quot;False&quot; ausgewählt ist, werden Änderungen mit dem Standardwert überschrieben. (NEO-11979)
* Fehlerkorrektur – Die Workflow-Aktivität **[!UICONTROL Warnung]** funktioniert jetzt einwandfrei, wenn nach einer Abfrage die Aktivität &quot;Anreicherung&quot; hinzugefügt wird. (NEO-12132)
* Fehlerkorrektur – Bei Installationen mit Oracle werden Pipeline-(Triggers-)Offsets jetzt korrekt von der Datenbank abgerufen, sodass keine Duplikate mehr erzeugt werden. (NEO-12121)
* Fehlerkorrektur – In Pivot-Tabellen kommt es jetzt bei der Verwendung der Analytics-Integration nicht mehr zu Darstellungsfehlern (NEO-12103).
* Fehlerkorrektur – Der Deskriptive-Analyse-Bericht funktioniert jetzt einwandfrei (NEO-11414)
* Fehlerkorrektur – Jetzt tritt kein Fehler mehr auf, wenn ein Feld in einer Remote-Tabelle einen Namen mit Unterstrich enthält.
* Fehlerkorrektur – Währungssymbole werden jetzt in Hypothesenberichten ordnungsgemäß dargestellt. (NEO-11634)
* Fehlerkorrektur – Umleitungen und Tracking können jetzt problemlos durchgeführt werden, unabhängig von den in den Tracking-Links verwendeten Zeichen.
* Fehlerkorrektur – Die Angebotsvorschau funktioniert jetzt einwandfrei.
* Fehlerkorrektur – Softbounces werden jetzt aus der Adresstabelle entfernt.
* Fehlerkorrektur – Bei der Verwendung von Barcodes tritt jetzt kein JAVA-Fehler mehr auf.
* Fehlerkorrektur – Bei Webanwendungen tritt jetzt kein Übersetzungsproblem mehr auf (NEO-12460).
* Fehlerkorrektur – Bei der Workflow-Aktivität zur Dateiübertragung über S3 tritt jetzt kein Fehler mehr auf. (NEO-12473)
* Fehlerkorrektur – Die Datumsfelder in Webanwendungen funktionieren jetzt einwandfrei. (NEO-12496)
* Fehlerkorrektur – Bei der Verwendung von Testadressen in einem Versand sind IDs jetzt unbegrenzt verfügbar. (NEO-11842)
* Fehlerkorrektur – PhantomJS und Debian 9 sind jetzt vollständig kompatibel.
* Fehlerkorrektur – Der Inhalt eines Testversandes kann jetzt problemlos validiert werden. (NEO-12725)
* Fehlerkorrektur – Die Workflow-Funktion &quot;Teilmenge aus der Population ausschließen&quot; funktioniert jetzt einwandfrei. (NEO-12441)
* Fehlerkorrektur – Die HTTP-Abfrage-API wartet jetzt, bis alle Callbacks beendet sind. (NEO-12628)
* Fehlerkorrektur – Die Aufgabe &quot;Aktualisierung freigegebener Zielgruppe&quot; in einer Aufspaltungsaktivität funktioniert jetzt einwandfrei. (NEO-11562)
* Fehlerkorrektur – Der Webserver stützt jetzt nicht mehr ab. (NEO-12904)
* Fehlerkorrektur – Art-Parameter in Transaktionsvorlagen funktionieren jetzt einwandfrei. (NEO-12334)
* Fehlerkorrektur – Die Konsole stürzt nicht mehr ab, wenn die getrackten URLs im E-Mail-Texteditor angezeigt werden. (NEO-13122)
* Fehlerkorrektur – Die Aufspaltungsaktivität funktioniert jetzt beim Import von Audiences von Audience Manager einwandfrei. (NEO-11550)
* Fehlerkorrektur – Im Bericht zu Klickpositionen tritt kein Fehler mehr auf. (NEO-11459)
* Fehlerkorrektur – Das Rendering von Angeboten funktioniert jetzt einwandfrei. (NEO-11565)
* Fehlerkorrektur – Die Listen-Update-Aktivität funktioniert jetzt beim Import von Audiences von Audience Manager einwandfrei. (NEO-11226)
* Fehlerkorrektur – Bei der Planungsaktivität und Zeitzonenkonfiguration tritt jetzt kein Problem mehr auf. (NEO-11662)
* Fehlerkorrektur – Auch bei fehlerhaften URLs funktioniert der Tracking-Workflow jetzt einwandfrei.
* Fehlerkorrektur – Bei externen Konten tritt nach dem Import des Mobile App-Packages jetzt kein Fehler mehr auf.
* Fehlerkorrektur – Die Zuweisung einer Zeitzone zu einen Benutzer funktioniert jetzt einwandfrei. (NEO-12464)
* Fehlerkorrektur – In den MTA-Kindprotokollen treten jetzt keine Fehler mehr auf. (NEO-11539, NEO-8978)
* Fehlerkorrektur – Beim Klicken auf das Verlaufssymbol in einem gespeicherten Bericht tritt jetzt kein Fehler mehr auf. (NEO-11620)
* Fehlerkorrektur – Pivot-Tabellen in Berichten können jetzt problemlos bearbeitet werden. (NEO-12068)
