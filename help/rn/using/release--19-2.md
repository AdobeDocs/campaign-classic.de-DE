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
source-git-commit: 1d08730421c598873e272f305a819e3fb4509d90

---


# Version 19.2{#release-19-2}

[Build-Aktualisierung](https://helpx.adobe.com/campaign/kb/acc-build-upgrade.html) | [Systemsteuerung](https://docs.adobe.com/content/help/en/control-panel/using/release-notes.html) | [Aktualisierungen](../../rn/using/documentation-updates.md) der Dokumentation| [Frühere Versionen](../../rn/using/release--19-1.md) | [Veraltete Funktionen](https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html)

<table> 
 <tbody> 
  <tr> 
   <td><img src="assets/green3.png"/><strong>Allgemeine Verfügbarkeit</strong></td>
   <td><img src="assets/blue3.png"/><strong>Release Candidate</strong></td> 
   <td><img src="assets/orange3.png"/><strong>Nicht mehr verfügbar</strong></td> 
   <td><img src="assets/red3.png"/><strong>Veraltet</strong></td> 
  </tr> 
   <tr> 
   <td>Neueste stabile Version verfügbar. Erstellen validiert in Produktion.<br> </td>
   <td>Erstellen von Adobe validiert Warte auf Proof.<br> </td>
   <td>Neuere Version mit Fehlerbehebungen verfügbar. Aktualisierung erforderlich.<br> </td>
   <td>Enthält bekannte Regressionen. Aktualisierung ist obligatorisch.<br> </td>
  </tr> 
 </tbody> 
</table>

Der **letzte stabile Build** ist 9032 (205c981c3). Click [here](../../rn/using/release--19-1.md#release-19-1-4-build-9032)

## ![](assets/orange_2.png) Version 19.2.3 - Build 9081 {#release-19-2-3-build-9081}

_7. Februar 2020_

**Verbesserungen**

* Korrektur des Regressionsfehlers aufgrund der Implementierung der SSL-Zertifizierung, der dazu führte, dass die Benutzerverbindung auf dem Windows-Server fehlschlug. (NEO-20629)
* Es wurde ein Problem behoben, bei dem im Menü **Info** eine falsche Version-Tag-Nummer angezeigt wurde.

## ![](assets/orange_2.png) Version 19.2 - Build 9080 {#release-19-2-build-9080}

_02. Dezember 2019_

**Neue Funktionen**

<table> 
 <thead> 
  <tr> 
   <th> <strong>California Consumer Privacy Act (CCPA)</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>CCPA ist das neue Datenschutzgesetz des Bundesstaates Kalifornien, mit dem die Datenschutzvorschriften harmonisiert und modernisiert werden, die am 01. Januar 2020 in Kraft treten. Der CCPA gilt für Adobe Campaign-Kunden, die Daten von Personen ("Datensubjekten") erfassen, die in Kalifornien wohnhaft sind.</p>
    <p>Zusätzlich zu den bereits verfügbaren Datenschutzfunktionen (einschließlich Zustimmungsverwaltung, Einstellungen zur Datenspeicherung und Benutzerrollen) hilft Adobe Campaign Ihnen bei der Vorbereitung auf CCPA:</p>
    <ul>
      <li>Recht auf Zugriff und Recht auf Löschung: Dazu nutzen wir die Funktionen, die wir analog dazu für die DSGVO ergänzt haben – <a href="https://helpx.adobe.com/campaign/kb/acc-privacy.html#righttoaccess">Mehr dazu</a></li>
      <li>Sie können nachverfolgen, ob ein Verbraucher sich für den Verkauf von persönlichen Informationen entschieden hat. Dazu müssen Sie die Tabelle "Profile"erweitern und ein <strong>Ausschluss-Feld für CCPA</strong> hinzufügen. <a href="https://helpx.adobe.com/campaign/kb/acc-privacy.html#ccpa">Mehr dazu</a></li></td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>Live-Überwachung des Arbeitsablaufs</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>Sie können jetzt den Ausführungsstatus aller Workflows auf Ihrer Instanz mit vordefinierten Ansichten überwachen.</p>
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
<td> <p>Mit Adobe Campaign können Sie das neue interaktive <a href="https://amp.dev/about/email/">AMP für E-Mail</a> -Format ausprobieren, das es Marketingexperten ermöglicht, AMP-Komponenten in Nachrichten einzuschließen, um das E-Mail-Erlebnis mit komplexen, dynamischen und interaktiven Inhalten zu verbessern, die direkt in der Nachricht selbst verarbeitet werden können.</p>
   <p>Diese Funktion wird als öffentliche Betaversion veröffentlicht.</p>
   <p>For more information, refer to the <a href="../../delivery/using/defining-interactive-content.md">detailed documentation</a> and the <a href="https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/sending-messages/email-channel/defining-interactive-email-content-with-amp.html">tutorial video</a>.</p><br /></td> 
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
<td> <p>Sichere SMS werden nun über den erweiterten allgemeinen SMPP-Connector unterstützt. Dies ermöglicht eine verschlüsselte Verbindung zum Provider.</p> <p><strong>Warnung</strong> Diese Funktion erfordert ein aktuelles Zertifikat auf allen Servern. Ungültige, gesperrte oder abgelaufene Zertifikate führen zu Fehlern, die sich auf die gesamten SMS-Sendefunktionen auswirken.</p><p>Weitere Informationen finden Sie im <a href="https://helpx.adobe.com/campaign/kb/sms-connector-protocol-and-settings.html">entsprechenden Handbuch</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Verbesserungen bei der Sicherheit**

* Behebung von Sicherheitslücken beim Site-übergreifenden Scripting in der Benutzeroberfläche des Campaigns - Überprüfung der Eingabedaten und Ausgabekodierung. (NEO-16810)
* Es wurde ein Sicherheitsproblem bei der Autorisierung von Profilen behoben, das den Zugriff auf nicht autorisierte Daten durch eine Verstärkung der Anmeldeeinschränkungsrichtlinie ermöglichte. (NEO-14445)

**Verbesserungen**

* Optimierung des Speicherverbrauchs für Push-Benachrichtigungen.
* Zur Leistungsoptimierung und Datenspeicherung wurde die Verarbeitung der Datei **logins.log** verbessert. Die Datei wird nun in mehrere Dateien aufgeteilt, wobei pro Tag maximal 365 Dateien gespeichert werden. [Mehr dazu](../../production/using/log-files.md)
* Das Microsoft Dynamics CRM-Externe Konto kann jetzt mit Passwort-Anmeldeinformationen (Kennwort + Benutzername) oder mit Zertifikat (privater Schlüssel) konfiguriert werden. [Mehr dazu](../../platform/using/external-accounts.md#microsoft-dynamics-crm-external-account)
* Einige Verbesserungen wurden dem Hadoop FDA Connector hinzugefügt, um die Zuverlässigkeit zu verbessern
* Es wurde eine spezielle Garantie hinzugefügt, um den Speicherplatz auf der Festplatte zu überprüfen, bevor das Hochladen von öffentliche Ressourcen auf dem Server möglich ist.
* Neue [Campaign-Optionen](../../installation/using/configuring-campaign-options.md) wurden hinzugefügt:
   * Mit der **Konfigurationsoption WdbcKillSessionPolicy** können Sie das Verhalten &quot; **Unbedingter Stopp** &quot;auf allen Workflows- und PostgreSQL-Abfragen beeinflussen.
   * Mit der Option **NmsOperation_DeliveryVorbereitungsfenster** können Sie die Anzahl der Tage festlegen, ab denen Versand mit inkonsistentem Status von der Anzahl laufender Versand ausgeschlossen werden.
   * Mit der Option **WdbcOptions_TempDbName** können Sie eine separate Datenbank für Tabellen auf Microsoft SQL Server konfigurieren. Dadurch werden Backups und Replizierung optimiert. [Mehr dazu](../../production/using/rdbms-specific-recommendations.md#microsoft-sql-server)
   * Die Option **XtkCleanup_NoStats** wurde für PostgreSQL erweitert, um das Verhalten des Datenspeicherung-Optimierungsschritts des Datenbankbereinigungs-Workflows besser zu steuern. [Mehr dazu](../../production/using/database-cleanup-workflow.md#statistics-update)
* Der **Anmelde()** -API wurde ein Mechanismus zur Kontosperrung hinzugefügt. Es verhindert alle weiteren Anmeldeversuche nach einer bestimmten Anzahl aufeinander folgender fehlgeschlagener Anmeldeversuche innerhalb eines bestimmten Zeitraums.
* Mit der neuen Option **Maximale Personalisierungslaufzeit** in den Eigenschaften des Versands können Sie einen Timeout-Zeitraum für die Personalisierungslaufzeit definieren, um zu verhindern, dass die Personalisierungsphase zu lange läuft. [Mehr dazu](../../delivery/using/personalization-fields.md#timing-out-personalization)
* Die Option **ftp-Protokoll** wurde hinzugefügt, um Ihnen die Verwendung einer Proxykonfiguration für SFTP-Verbindungen zu ermöglichen. [Mehr dazu](../../installation/using/configuring-campaign-server.md#proxy-connection-configuration)
* Neue Unterstützung für den Proxyzugriff auf einen externen SFTP-Server für lokale Umgebung.
* Eine spezielle Garantie wurde hinzugefügt, um die Installation von Paketen zu verhindern, die nicht mit der Campaign-Instanz kompatibel sind. [Mehr dazu](../../installation/using/installing-campaign-standard-packages.md)

_Veraltete Systeme_

Die folgenden Systeme werden jetzt für Campaign Classic-Implementierungen [nicht mehr unterstützt](https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html) :
* Apache 2.2
* Centos 6

Vergewissern Sie sich, dass Sie die unterstützten Versionen aller in der aktuellen Campaign-Kompatibilitätsmatrix aufgelisteten Systeme verwenden. [Mehr dazu](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)

_Campaign Mobile SDK_

Version 1.0.26 des iOS-SDK ist jetzt verfügbar. In diesem neuen Build wurde die Unterstützung von iOS 13 hinzugefügt. Diese neue Version unterstützt jetzt die Benachrichtigungspriorität und den neuen Registrierungstoken-Verwaltungsprozess für iOS 13-Push-Benachrichtigungen. Wenn Sie Anwendungen auf einer früheren Version des SDK ausführen, müssen Sie Ihre Anwendungen mit dem neuen SDK neu kompilieren. Wenden Sie sich an den Adobe-Kundendienst, um das SDK zu erhalten.

**Korrekturen**

* Es wurde ein Absturz der Konsole behoben, der beim Hinzufügen einer leeren verknüpften Tabelle in der Workflow-Aktivität **Data Loading (RDBMS)** auftrat. (NEO-12213)
* Es wurde ein Problem behoben, das dazu führen konnte, dass bestimmte Meldungen nicht vom Mid-Sourcing-Server verarbeitet wurden. (NEO-12395)
* Es wurde ein Problem im Arbeitsablauf für die Datenbankbereinigung behoben, das bei Verwendung der Option zur Abfrage von Banding mit Teradata auftrat. (NEO-12399)
* Es wurde ein Problem behoben, das die Analyse des Versands mit der Typologieregel einschließlich der Domäne ne.jp betraf. (NEO-12609)
* Es wurde ein Problem mit SMS über TLS-Aktualisierungen behoben, das eine restriktivere Zertifikatrichtlinie beinhaltete. Diese Updates können bei einem veralteten Zertifikat zu einem Verbindungsfehler zwischen den Marketing- und Mid-Sourcing-Servern führen. (NEO-17698)
* Es wurde ein Problem behoben, das bei Verwendung der Schaltfläche **Verbindung** testen auf einem Externe Konto in einer Mid-Sourcing-Umgebung mit Vault-Authentifizierung auftrat. (NEO-12722)
* Es wurde ein Problem bei Abfragen behoben, bei denen Datumsfunktionen mit einer FDA-Hadoop-Verbindung verwendet wurden. (NEO-12847)
* Es wurde ein Problem behoben, das beim Ersetzen eines Bildes im E-Mail-Editor auftrat. (NEO-13098)
* Es wurde ein Problem behoben, das zu Fehlern nach der Aktualisierung bei Ordnern führte, die gelöscht oder an einen anderen Speicherort verschoben wurden. (NEO-13118)
* Es wurde ein Problem bei der Bildanzeige bei Verwendung der Option Bild pro Bildschirmgröße **des Geräts** definieren in LINE-Meldungen behoben. (NEO-13228)
* Es wurde ein Problem bei der Vorbereitung des Versands behoben, das auftrat, wenn die Option &quot;Adresse des Duplikats **beim Versand** ausschließen&quot;deaktiviert war. (NEO-13240)
* Es wurde ein Problem in Workflows behoben, das beim Verwenden der Aktivität für die **Dateiübertragung** zum Herunterladen von Dateien mit der Option Quelldateien nach der Übertragung **löschen** auftrat, wobei der Name ein Leerzeichen enthielt. (NEO-13411)
* Es wurde ein Problem mit der Tomcat-Cache-Bereinigung behoben, das zu Speicherproblemen führen konnte. (NEO-13456)
* Es wurde ein Fehler behoben, der beim Installieren der **Control of Angebot Engine mit dem integrierten Ausführungsinstanz** -Paket auf einer bestehenden Kontrollinstanz, die in Microsoft SQL 2017 ausgeführt wird, auftrat. (NEO-13539)
* Es wurde ein Absturz der Konsole behoben, der auftrat, wenn verfolgte URLs in einer E-Mail auf der Registerkarte &quot; **Textinhalt** &quot;nicht überprüft wurden. (NEO-13545)
* Es wurde ein Kodierungsfehler beim chinesischen Absendenamen behoben. (NEO-13837)
* Es wurde ein Fehler behoben, der auftrat, wenn Antwortdaten der Umfrage aus dem Explorer angezeigt wurden. (NEO-14590)
* Es wurde ein Problem behoben, das zu Diskrepanzen zwischen der Versand-Protokollklassifizierung und der Quarantäne-Tabelle führen konnte. (NEO-16547)
* Es wurde ein Problem mit DKIM-Schlüsseln behoben, die nicht in E-Mails eingebettet waren. (NEO-16804)
* Es wurde ein Problem behoben, bei dem der falsche Fehlercode angezeigt wurde, wenn ein ungültiges Sitzungstoken im Kontext von API-Aufrufen zum Auslösen von Ereignissen verwendet wurde. Der Fehlercode lautete &quot;HTTP 200 OK&quot;anstelle von &quot;HTTP 403 Verboten&quot;. (NEO-16826)
* Es wurde ein Problem bei der Anzeige von Versandberichten über den Webzugriff behoben. (NEO-17015)
* Es wurde ein IMS-Authentifizierungsproblem bei der Anmeldung bei Adobe Campaign behoben. (NEO-17312)
* Es wurde ein Fehler behoben, der verhinderte, dass in Quarantäne befindliche E-Mails vom Datenschutzverwaltungsprozess gelöscht wurden. (NEO-17314)
* Korrektur von Durchsatzproblemen nach der Aktualisierung auf 9031 mit SQL-Datenbank. (NEO-17558)
* Es wurde ein Problem behoben, das den CRM Connector mit Salesforce betraf. (NEO-17712)
* Korrektur eines Zeitüberschreitungsproblems beim Importieren von Daten aus einem externen SFTP. (NEO-19723)
* Es wurde ein Problem beim Zugriff auf Prognosemodelle behoben. (NEO-19713)
* Es wurde ein Fehler behoben, der sich auf die Stichprobenauswahl in der Aktivität des **Teilarbeitsablaufs** mit der Hadoop-FDA auswirkte. (NEO-16636)

