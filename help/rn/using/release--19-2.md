---
title: Version 19.2
seo-title: Version 19.2
description: Version 19.2
seo-description: null
page-status-flag: never-activated
uuid: 269d590c-5a6d-40b9-a879-02f5033863fc
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rns
content-type: reference
topic-tags: latest-release-notes
discoiquuid: 5df34f55-135a-4ea8-afc2-f9427ce5ae7b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: eab67029d477044bc853f2a5c2de06ace70ebbee

---


# Version 19.2{#release-19-2}

[Build-Aktualisierung](https://helpx.adobe.com/de/campaign/kb/acc-build-upgrade.html) | [Control Panel-Versionen](https://docs.adobe.com/content/help/de-DE/control-panel/using/release-notes.html) | [Aktualisierungen der Dokumentation](../../rn/using/documentation-updates.md) | [Frühere Versionshinweise](../../rn/using/release--19-1.md) | [Eingestellte Funktionen](https://helpx.adobe.com/de/campaign/kb/deprecated-and-removed-features.html)

<table> 
 <tbody> 
  <tr> 
   <td><img src="assets/do-not-localize/green3.png"/><strong>Allgemeine Verfügbarkeit</strong></td>
   <td><img src="assets/do-not-localize/blue3.png"/><strong>Veröffentlichungskandidat</strong></td> 
   <td><img src="assets/do-not-localize/orange3.png"/><strong>Nicht mehr verfügbar</strong></td> 
   <td><img src="assets/do-not-localize/red3.png"/><strong>Veraltet</strong></td> 
  </tr> 
   <tr> 
   <td>Neuester verfügbarer stabiler Build. Build in Produktion validiert.<br> </td>
   <td>Build validiert von Adobe. Produktionstestversand ist ausstehend.<br> </td>
   <td>Neuerer Build mit Fehlerbehebungen verfügbar. Aktualisierung erforderlich.<br> </td>
   <td>Enthält bekannte Regressionen. Aktualisierung ist obligatorisch.<br> </td>
  </tr> 
 </tbody> 
</table>

Der **letzte stabile Build** ist 9032 (3a9dc9c). Click [here](../../rn/using/release--19-1.md#release-19-1-4-build-9032)

## ![](assets/do-not-localize/orange_2.png) Version 19.2.3 – Build 9081 {#release-19-2-3-build-9081}

_7. Februar 2020_

**Verbesserungen**

* Korrektur des Regressionsfehlers aufgrund der Implementierung der SSL-Zertifizierung, der dazu führte, dass die Benutzerverbindung auf dem Windows-Server fehlschlug. (NEO-20629)
* Es wurde ein Problem behoben, bei dem im Menü **Info** eine falsche Version-Tag-Nummer angezeigt wurde.

## ![](assets/do-not-localize/orange_2.png) Version 19.2 – Build 9080 {#release-19-2-build-9080}

_2. Dezember 2019_

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
      <li>Sie können nachverfolgen, ob ein Verbraucher sich gegen den Verkauf von persönlichen Informationen entschieden hat. Dazu müssen Sie die Tabelle „Profile“ erweitern und ein Feld <strong>Opt-out für CCPA</strong> hinzufügen – <a href="https://helpx.adobe.com/de/campaign/kb/acc-privacy.html#ccpa">mehr dazu</a></li></td> 
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
   <p>Weiterführende Informationen finden Sie in der <a href="../../delivery/using/defining-interactive-content.md">ausführlichen Dokumentation</a> und im <a href="https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/sending-messages/email-channel/defining-interactive-email-content-with-amp.html">Tutorial-Video</a>.</p><br /></td> 
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
* Das externe Microsoft Dynamics CRM-Konto kann jetzt mit Passwortdaten (Passwort + Benutzername) oder Zertifikat (privater Schlüssel) konfiguriert werden – [mehr dazu](../../platform/using/external-accounts.md#microsoft-dynamics-crm-external-account)
* Dem Hadoop FDA-Connector wurden einige Verbesserungen hinzugefügt, um die Zuverlässigkeit zu erhöhen
* Es wurde ein spezieller Schutzmechanismus hinzugefügt, bevor das Hochladen von öffentlichen Ressourcen auf den Server erlaubt wird.
* Es wurden neue [Campaign-Optionen](../../installation/using/configuring-campaign-options.md) hinzugefügt:
   * Mit der Konfigurationsoption **WdbcKillSessionPolicy** können Sie das Verhalten **Unbedingter Stopp** bei allen Workflows und PostgreSQL-Datenbankabfragen beeinflussen.
   * Mit der Option **NmsOperation_DeliveryVorbereitungsfenster** können Sie die Anzahl der Tage festlegen, ab denen Sendungen mit inkonsistentem Status von der Zählung laufender Sendungen ausgeschlossen werden.
   * Mit der Option **WdbcOptions_TempDbName** können Sie eine separate Datenbank für Tabellen auf Microsoft SQL Server konfigurieren. Dadurch werden Backups und Replikation optimiert – [mehr dazu](../../production/using/rdbms-specific-recommendations.md#microsoft-sql-server)
   * Die Option **XtkCleanup_NoStats** wurde für PostgreSQL erweitert, um das Verhalten des Speicheroptimierungsschritts des Workflows für die Datenbankbereinigung besser zu steuern – [mehr dazu](../../production/using/database-cleanup-workflow.md#statistics-update)
* Der **logon()**-API wurde ein Mechanismus zur Kontosperrung hinzugefügt. Er verhindert alle weiteren Anmeldeversuche nach einer bestimmten Anzahl aufeinander folgender fehlgeschlagener Anmeldeversuche innerhalb eines bestimmten Zeitraums.
* Mit der neuen Option **Maximale Laufzeit der Personalisierung** in den Versandeigenschaften können Sie einen Timeout-Zeitraum für die Laufzeit der Personalisierung definieren, um zu verhindern, dass die Personalisierungsphase zu lange läuft – [mehr dazu](../../delivery/using/personalization-fields.md#timing-out-personalization)
* Die Option **ftp-Protokoll** wurde hinzugefügt, um Ihnen die Verwendung einer Proxy-Konfiguration für SFTP-Verbindungen zu ermöglichen – [mehr dazu](../../installation/using/configuring-campaign-server.md#proxy-connection-configuration)
* Neue Unterstützung für den Proxy-Zugriff auf einen externen SFTP-Server für On-Premise-Umgebungen.
* Es wurde ein spezieller Schutzmechanismus hinzugefügt, um die Installation von Paketen zu verhindern, die nicht mit der Campaign-Instanz kompatibel sind – [mehr dazu](../../installation/using/installing-campaign-standard-packages.md)

_Veraltete Systeme_

Die folgenden Systeme sind jetzt für Campaign Classic-Implementierungen [veraltet](https://helpx.adobe.com/de/campaign/kb/deprecated-and-removed-features.html):
* Apache 2.2
* Centos 6

Vergewissern Sie sich, dass Sie unterstützte Versionen aller Systeme verwenden, die in der neuesten Campaign-Kompatibilitätsmatrix aufgeführt sind – [mehr dazu](https://helpx.adobe.com/de/campaign/kb/compatibility-matrix.html)

_Campaign Mobile SDK_

Version 1.0.26 des iOS-SDK ist jetzt verfügbar. In diesem neuen Build wurde Unterstützung für iOS 13 hinzugefügt. Diese neue Version unterstützt jetzt die Benachrichtigungspriorität und den neuen Anmeldetoken-Verwaltungsprozess für iOS 13-Push-Benachrichtigungen. Wenn Sie Anwendungen auf einer früheren Version des SDK ausführen, müssen Sie Ihre Anwendungen mit dem neuen SDK neu kompilieren. Wenden Sie sich an die Adobe-Kundenunterstützung, um das SDK zu erhalten.

**Korrekturen**

* Es wurde ein Absturz der Konsole behoben, der beim Hinzufügen einer leeren verknüpften Tabelle in der Workflow-Aktivität **Laden (DBMS)** auftrat. (NEO-12213)
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
* Es wurde ein Absturz der Konsole behoben, der auftreten konnte, wenn die Option „Getrackte URLs“ in einer E-Mail im Tab **Textinhalt** deaktiviert wurde. (NEO-13545)
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

