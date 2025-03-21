---
product: campaign
title: Campaign Classic-Versionen 2021
description: Weiterführende Informationen zu Campaign Classic-Versionen 2021
feature: Release Notes
role: User
level: Beginner
hidefromtoc: true
exl-id: 0cd6bf20-da72-4cf0-9f5d-d4e8acdd324d
source-git-commit: a1dbef3e1feca1e3347de013db8bd7809d315016
workflow-type: tm+mt
source-wordcount: '2586'
ht-degree: 100%

---

# Versionen 2021{#release-2021}

## Version 7.1 (21.1)

>[!CAUTION]
>Verwenden Sie das Menü **[!UICONTROL Hilfe > Über…]**, um Ihre Adobe Campaign[-Version und -Build-Nummer](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version) herauszufinden. Beachten Sie jedoch, dass für alle auf dieser Seite aufgelisteten Builds zwischen 9277 und 9343 als Versionsnummer 7.0 statt 7.1 angezeigt wird.
> 

### Version 21.1.4 – Build 9343 {#release-21-1-4-build-9343}

[!BADGE Veraltet]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=de#rn-statuses" tooltip="Veraltet"}

_8. Oktober 2021_

**Patches**

* Die Fehlerkorrektur des Abrechnungs-Workflows im Build 9342 wurde weiter verbessert. Der Workflow muss jetzt nicht mehr manuell neu gestartet werden, damit die Fehlerbehebung angewendet werden kann. Jetzt startet das Postupgrade automatisch den Workflow neu.

* Fehlerkorrektur - Die ordnungsgemäße Angebotsverwaltung bei Verwendung des Moduls **Interaction** mit der Option [Power Booster](../../installation/using/power-booster-and-power-cluster.md) ist jetzt möglich. (NEO-39263)

* Fehlerkorrektur - Beim Versand mit mehr als einer IP-Affinität in einer Multi-Mid-Sourcing-Instanz tritt jetzt der Fehler &#39;IP-Affinität xxx nicht in Mid-Server xxx gefunden&#39; nicht mehr auf. (NEO-37514)

### Version 21.1.4 – Build 9342 {#release-21-1-4-build-9342}

[!BADGE Veraltet]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=de#rn-statuses" tooltip="Veraltet"}

_7. September 2021_

**Sicherheitsverbesserung**

* Fehlerkorrektur – Der Schutz vor Directory-Traversal-Angriffen ist jetzt verbessert. (NEO-28547)

**Verbesserungen**

* Nach seinem End-of-Life wurde Flash aus allen damit verbundenen Campaign-Funktionen und -Komponenten entfernt und durch HTML5 ersetzt. Der Diagrammtyp **Tacho** wurde entfernt. (NEO-30330) [Mehr dazu](../../reporting/using/creating-a-chart.md)
* Bei der Installation der Client-Konsole unter Windows überprüft das Installationsprogramm jetzt, ob ein übergeordneter Registrierungsknoten vorhanden ist, und erstellt einen, wenn er fehlt. Dadurch werden potenzielle Probleme beim Starten der Konsole verhindert. (NEO-34854)
* Die Tracking-Signatur-Funktion wurde verbessert. So sollen Fehler verhindert werden, die in Zusammenhang damit stehen, wie Drittanbieter-Tools (E-Mail-Clients, Internet-Browser) Sonderzeichen verarbeiten. URL-Parameter sind jetzt codiert.

**Sonstige Änderungen**

* Es wurde eine Fehlfunktion behoben, die in Version 21.1.3 mit der Einführung der neuen Schutzmaßnahme des Abrechnungs-Workflows auftrat. Der Abrechnungs-Workflow wurde auf falschen Instanzen ausgeführt und stürzte beim Versuch ab, den nicht generierten Abrechnungsbericht zu senden. Sie müssen den Workflow manuell neu starten, damit die Fehlerbehebung angewendet wird.
* Bereits veraltete Microsoft CRM-Connectoren (Office 365- und On-Premise-Bereitstellungen) wurden aus der Benutzeroberfläche entfernt. [Mehr dazu](../../platform/using/crm-ms-dynamics.md#configure-acc-for-microsoft)
* Nach der Migration zu Tomcat 8 wurde das IIS-Setup-Skript aktualisiert, um Probleme mit der IIS-Integration zu beheben. (NEO-31019)
* In den Daten- und Schema-Tabs des Fensters **Population ansehen** der Workflow-Transitionen wurde die Identifizierung der Datenquelle verbessert.
* Fehlende Datenbankindizes wurden den folgenden Schemata hinzugefügt, um Probleme bei der Datenbankaktualisierung zu vermeiden: xtk:rights, nms:dlvExclusion, nms:seedMember, nms:trackingUrl

**Korrekturen**

* Fehlerkorrektur – Der Bericht &quot;Klicks&quot; funktioniert jetzt, wenn Angebote mit dem Versand verknüpft sind. (NEO-26295)
* Fehlerkorrektur – Die Aktivität **Unter-Workflow** erzeugt bei ihrer Ausführung jetzt zuverlässig eine Ausgabetabelle. (NEO-36242)
* Das Exportieren des Berichts **Deskriptive Analyse** in PDF funktioniert jetzt problemlos. (NEO-25847)
* Fehlerkorrektur – Sendungen können jetzt problemlos über einen externen E-Mail-Versand durchgeführt werden. (NEO-37435)
* Fehlerkorrektur – Die Verbindung mit Microsoft CRM über die Web-API funktioniert jetzt fehlerfrei. Die Fehlermeldung wurde entfernt, da keine Funktionen betroffen waren.
* Fehlerkorrektur – Wenn der Mid-Server als Relais zwischen Tracking- und Marketing-Servern festgelegt wird, funktioniert die Trackinglog-Deduplizierung jetzt problemlos. (NEO-36285)
* Fehlerkorrektur – Bei einer Regression kann Vault als spezifischer Code-Store verwendet werden.
* Fehlerkorrektur – Variablen können jetzt in einer Workflow-Aktivität vom Typ **Anreicherung** verwendet werden, wenn die eingehende Transition aus einer FDA-Datenquelle stammt.
* Fehlerkorrektur – URLs in E-Mail-Nachrichten werden jetzt nicht mehr beschädigt.

### Version 21.1.3 – Build 9330 {#release-21-1-3-build-9330}

[!BADGE Veraltet]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=de#rn-statuses" tooltip="Veraltet"}

_5. Juni 2021_

**Neue Funktionen**


<table>
<thead>
<tr>
<th><strong>Neue Workflow-Aktivität: Datenquelle ändern</strong><br/></th>
</tr>
</thead>
<tbody>
<tr>
<td>
<p>Mit der neuen Workflow-Aktivität <b>Datenquelle ändern</b> können Sie die Datenquelle der Arbeitstabelle eines Workflows ändern. Dies bietet eine höhere Flexibilität bei der Verwaltung von Daten in verschiedenen Datenquellen (FDA und lokale Datenbanken).</p>
<p>In Adobe Campaign-Workflows werden Daten mithilfe von Arbeits- (oder temporären) Tabellen verwaltet. Während der Workflow-Ausführung geben Arbeitstabellen Daten für Workflow-Aktivitäten frei. Standardmäßig werden die Arbeitstabellen auf derselben Datenbank erstellt wie die Quelle der Daten, die abgefragt werden.</p>
<p>Weitere Informationen finden Sie im <a href="../../workflow/using/change-data-source.md">entsprechenden Handbuch</a>.</p>
</td>
</tr>
</tbody>
</table>

<table>
<thead>
<tr>
<th><strong>Integration mit Adobe Journey Orchestration</strong><br/></th>
</tr>
</thead>
<tbody>
<tr>
<td>
<p>Die Integration zwischen Journey Orchestration und Adobe Campaign Classic ist jetzt allgemein verfügbar. Diese Integration ermöglicht Journey Orchestration das Senden von E-Mails, Push-Benachrichtigungen und SMS mit der Transaktionsnachrichtenfunktion von Adobe Campaign Classic.</p>
<p>Die Verbindung zwischen der Journey Orchestration- und der Campaign Classic-Instanz wird bei der Bereitstellung von Adobe hergestellt.</p>
<p>Weitere Informationen finden Sie in der <a href="https://experienceleague.adobe.com/docs/journeys/using/action-journeys/acc-action.html?lang=de">Dokumentation zu Journey Orchestration</a>. In diesem <a href="https://experienceleague.adobe.com/docs/journeys/using/use-cases-journeys/campaign-classic-use-case.html?lang=de">Abschnitt</a> wird ein Anwendungsfall schrittweise beschrieben.</p>
</td>
</tr>
</tbody>
</table>

<table> 
<thead>
<tr> 
<th> <strong>Verbesserungen am LINE-Kanal</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>Die folgenden Verbesserungen wurden dem LINE-Kanal hinzugefügt:
</p>
<ul> 
<li><p>Unterstützung für den LINE-Video-Nachrichten-Typ</p></li>
<li><p>Unterstützung der LINE-Partnerregistrierungs-API</p></li>
<li><p>Unterstützung eines erneuten Nachrichtenversands im Fall eines Server-seitigen LINE-Fehlers oder Netzwerk-Timeouts</p></li>
</ul>
<p>Weitere Informationen finden Sie im <a href="../../delivery/using/line-channel.md">entsprechenden Handbuch</a>.</p>
</td> 
</tr> 
</tbody> 
</table>

<table> 
<thead>
<tr> 
<th> <strong>Vertica Analytics FDA-Connector</strong><br/> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>Jetzt können Sie Ihre Adobe Campaign Classic-Instanz mit Ihrer externen Vertica-Datenbank verbinden. Diese Verbindung wird über ein neues externes Konto verwaltet.</p>
<p>Weitere Informationen finden Sie im <a href="../../installation/using/configure-fda-vertica.md">entsprechenden Handbuch</a>.</p>
</td> 
</tr> 
</tbody> 
</table>

<table> 
<thead>
<tr> 
<th> <strong>Google BigQuery FDA-Connector</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>Jetzt können Sie Ihre Adobe Campaign Classic-Instanz mit Ihrer externen Google BigQuery-Datenbank verbinden. Diese Verbindung wird über ein neues externes Konto verwaltet.
</p>
<p>Weitere Informationen finden Sie im <a href="../../installation/using/configure-fda-google-big-query.md">entsprechenden Handbuch</a>.</p>
</td> 
</tr> 
</tbody> 
</table>

**Verbesserungen bei der Sicherheit**

* Der Zugriff auf die API-Methode **xtk:session#GetCnxInfo**, die die vollständigen Details zur Datenbankverbindung zurückgibt, ist jetzt nur noch für Admin-Benutzer verfügbar. (NEO-27779)
* Die veraltete Funktion decryptString wurde in CRM-bezogenen JavaScript-Dateien durch decryptPassword ersetzt.
* Die Funktion zum Tracking von Signaturen wurde verbessert, um das Risiko von Tracking-Weiterleitungsfehlern zu verringern, wenn Drittanbieter-Tools (E-Mail-Clients, Internetbrowser, Sicherheits-Tools für sichere Links) den getrackten Link ändern.
* Fehlerkorrektur – Getrackte URLs funktionieren jetzt auch, wenn sie Großbuchstaben enthalten. Beim Signierungsmechanismus für getrackte URLs wird jetzt zwischen Groß- und Kleinschreibung unterschieden. (NEO-28414)

**Aktualisierungen zur Kompatibilität**

Die folgenden Systeme werden jetzt von Campaign unterstützt:
* Google BigQuery FDA-Connector
* Vertica Analytics FDA-Connector
* PostgreSQL 13

Weiterführende Informationen finden Sie in der [Campaign-Kompatibilitätsmatrix](../../rn/using/compatibility-matrix.md).

**Eingestellte Funktionen**

* Ab Campaign Version 21.1 wird der Adobe Analytics Data Connector nicht mehr unterstützt. Wenn Sie diesen Connector verwenden, müssen Sie Ihre Implementierung auf den neuen Adobe Analytics Connector anpassen.
* Debian 8 wird jetzt nicht mehr unterstützt.
* Nach der Einstellung von Oracle CRM in Version 20.3 wurde das zugehörige externe Konto aus der Benutzeroberfläche entfernt.

Weitere Informationen finden Sie auf der Seite [Eingestellte und entfernte Funktionen ](../../rn/using/deprecated-features.md).

**Verbesserungen**

* Beim Speichern eines Workflows wurden zusätzliche Prüfungen hinzugefügt, um sicherzustellen, dass Aktivitätsnamen eindeutig sind und dass auf Transitionen immer eine Aktivität folgt.
* Der technische Workflow **Abrechnung (Billing)** enthält jetzt die Aufgaben, die ursprünglich vom mittlerweile entfernten Workflow **Zählung aktiver Profile** (billingActiveContactCount) ausgeführt wurden. Der monatlich vom Workflow gesendete E-Mail-Bericht enthält jetzt Informationen zur Anzahl der aktiven Profile in der Instanz. [Mehr dazu](../../workflow/using/about-technical-workflows.md)
* Es wurde das neue Attribut **_keyOnMData** hinzugefügt, um einen Schlüssel für Vorgänge zu Memo-Daten verwenden zu können.

**Sonstige Änderungen**

* Es wurde ein Schutzmechanismus hinzugefügt, der sicherstellt, dass nur der [technische Abrechnungs-Workflow](../../production/using/monitoring-processes.md#billing-report) auf der Marketing-Instanz ausgeführt wird.
* Der Drittanbieter openssl für Windows wurde auf Version 1.1.1h aktualisiert.
* In der Debian-Kit-Beschreibung wurde &quot;nlserver&quot; in &quot;Adobe Campaign Classic-Server&quot; geändert.

**Korrekturen**

* Fehlerkorrektur – Beim Bearbeiten des Sitzungs-Timeouts zum Abmelden von Benutzern nach einer bestimmten Zeitspanne bleiben Benutzer nicht mehr über die eingestellte Zeit hinaus angemeldet.
* Fehlerkorrektur – Sendungen können nicht mehr in den Eigenschaften der Sendungen bearbeitet werden, wenn sie als schreibgeschützt angezeigt werden.
* Fehlerkorrektur – Die Symbolleiste zur Bearbeitung verschwindet beim Entwerfen einer Web-Anwendung nicht mehr.
* Fehlerkorrektur – Beim Hinzufügen eines Links zu einer E-Mail wird nun nicht mehr die Textversion einer E-Mail mit Adobe Campaign Classic-Headern angezeigt. (NEO-29211
* Bei Verwendung einer FDA-over-HTTPs-Verbindung blieb der Workflow **Mid-Sourcing** (Versandlogs) (defaultMidSourcingLog) in dem durch die Option **NmsMidSourcing_LogsPeriodHour** festgelegten Zeitrahmen stecken. Dadurch wurde verhindert, dass Datensätze mit Daten nach diesem festgelegten Zeitraum aktualisiert wurden. (NEO-30833)
* Fehlerkorrektur – Jetzt tritt nach dem Ausführen des Synchronisations-Workflows für das Message Center kein Fehler mehr auf. Jedes Mal, wenn ein Ordner mit Versandobjekten in einen benutzerdefinierten Ordner verschoben wurde, verschob der Workflow die Sendungen zurück in den Ordner **Transaktionsnachrichten-Verlauf**. (NEO-27445)
* Fehlerkorrektur – Jetzt wird keine Fehlermeldung mehr angezeigt, wenn versucht wird, die Berichte **Versandstatistiken**, **Tracking-Indikatoren** und **Statistiken zu Teilungsaktivitäten** anzuzeigen.
* Die Workflow-Aktivität **Oracle On Demand** wurde nach der Einstellung des Oracle CRM-Connectors aus der Benutzeroberfläche entfernt.
* Fehlerkorrektur – Die Ausführung von Verarbeitungs-Workflows wird jetzt nach dem täglichen Neustart des Workflow-Server-Moduls (wfserver) nicht mehr angehalten. (NEO-30047)
* Fehlerkorrektur – Das MX-Verwaltungsdokument kann jetzt zuverlässig aktualisiert werden. Zuvor konnte sich dieses Problem negativ auf die IP-Reputation auswirken. (NEO-29897)
* Fehlerkorrektur – Beim Empfang eines SOAP-Aufrufs kommt es nicht mehr zu Abstürzen von Web-Prozessen. (NEO-28796) (NEO-29600)
* Fehlerkorrektur – Die Erstellung des SAP HANA-FDA-Index wird jetzt zuverlässig ausgeführt. (NEO-29664)
* Fehlerkorrektur – Transaktionsnachrichten verbleiben jetzt nicht mehr im Status **Ausstehend**, wenn SOAP-Aufrufe mit einem Header ausgeführt werden. (NEO-28737)
* Fehlerkorrektur – Bei der Verwendung des Teradata FDA-Connectors tritt jetzt kein Fehler mehr auf. Das Problem bestand darin, dass alle temporären Tabellen nur auf einem Knoten des Clusters erstellt wurden, was letztendlich den gesamten Spool-Speicherplatz belegen und zu einem Absturz von Teradata führen konnte. Die temporären Tabellen werden jetzt auf vielen Knoten generiert. (NEO-28230)
* Fehlerkorrektur – Bei der Verwendung von Web-Anwendungen werden von Trackingtags jetzt keine falschen Primärschlüssel mehr im **nms:trackingURL**-Schema erzeugt. (NEO-27931)
* Die Kompatibilität mit ODBC 3.x wurde verbessert, um die Richtigkeit von Fehlermeldungen sicherzustellen.
* Fehlerkorrektur – Jetzt stürzt die Konsole nicht mehr ab, wenn benutzerdefinierte Inhaltsvorlagen in E-Mail-Sendungen verwendet werden. (NEO-31547)
* Fehlerkorrektur – Tomcat sendet jetzt auch bei langsamen Verbindungen oder einer großen Antwortgröße gültige Antworten. (NEO-30858)
* Fehlerkorrektur – Beim Lesen der UUID aus einer PostgreSQL-Datenbank tritt jetzt kein Fehler mehr auf.
* Fehlerkorrektur – Die Suche nach Vorschlagsdaten in Verbindung mit Angeboten führt nicht mehr zu Performance-Problemen. (NEO-27554)
* Fehlerkorrektur – Der Web-Prozess reagiert jetzt auch, wenn der IMS-Dienst aktiviert ist, aber nicht reagiert.
* Fehlerkorrektur – Das Durchführen eines Versandes mit einer Gruppe von Testsendungen ist jetzt zuverlässig möglich. Ein bestimmter Verbindungsmechanismus führte dazu, dass die Versandpersonalisierung fehlschlug. (NEO-14391)
* Fehlerkorrektur – Die Warnungsaktivität sendet jetzt einen Warnhinweis, wenn eine Abfrage und eine Anreicherungsaktivität an die Versandtabelle gerichtet ist. (NEO-25157)

### Version 21.1.2 – Build 9282 {#release-21-1-2-build-9282}

[!BADGE Veraltet]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=de#rn-statuses" tooltip="Veraltet"}

_15. April 2021_

* Die Verwaltung von Passwörtern wurde verbessert, um die Sicherheit zu optimieren.
* Fehlerkorrektur – Es wurde ein Problem behoben, das zum Absturz des MTA führen konnte.

### Version 21.1.1 – Build 9277 {#release-21-1-1-build-9277}

[!BADGE Veraltet]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=de#rn-statuses" tooltip="Veraltet"}

_22. Februar 2021_

**Verbesserungen bei der Sicherheit**

* Der Authentifizierungsmechanismus der Konsole wurde verbessert, um die Sicherheit zu optimieren. (NEO-26944)
* Fehlerkorrektur – Es wurde ein Sicherheitsproblem behoben, um den Schutz vor SSRF-Problemen (Server Side Request Forgery) zu verbessern. (NEO-28532)

**Aktualisierungen zur Kompatibilität**

Die folgenden Systeme werden jetzt von Campaign unterstützt:

* Die Salesforce-API-Version 49 wird jetzt bei Verwendung eines externen Salesforce CRM-Kontos unterstützt.

**Eingestellte Funktionen**

Der Bericht zum **technischen Zustellbarkeits-Monitoring** wird jetzt nicht mehr unterstützt.

Weitere Informationen finden Sie auf der Seite [Eingestellte und entfernte Funktionen ](../../rn/using/deprecated-features.md).

**Verbesserungen**

**E-Mail-Feedback-Service (EFS)** ist ein skalierbarer Dienst, der das Feedback direkt vom Enhanced MTA erfasst und damit die Reporting-Genauigkeit verbessert. Diese Funktion wird als private Betaversion veröffentlicht und wird in zukünftigen Versionen nach und nach allen Kunden zur Verfügung stehen.

* Alle Kategorien von Feedback werden jetzt für vollständiges und genaues Reporting erfasst.
* Die Berechnung des Indikators &quot;Zugestellt&quot; basiert nun auf Echtzeit-Feedback des Enhanced MTA, um Genauigkeit und Reaktivität zu verbessern.
* EFS löst das Problem der Verzögerungen beim Reporting zu synchronen Softbounces.

**Sonstige Änderungen**

* Die Übertragungsgeschwindigkeit für große Trackinglogs wurde durch Komprimierung verbessert.
* Workflow-Heatmap wurde verbessert, um Zeitüberschreitungen zu vermeiden, wenn Workflows mit mehreren Aktivitäten ausgeführt werden. (NEO-27423).
* Es wurde ein Problem behoben, durch das ein Angebot auch dann präsentiert werden konnte, wenn das Enddatum überschritten wurde. Campaign Classic berücksichtigt nun den gesamten Zeitstempel des Enddatums und nicht nur das Datum. (NEO-27590)
* Der Google+-Link wurde aus dem Gestaltungsbaustein **Teilen-Links der sozialen Netzwerke** entfernt.
* Es wurde ein Problem behoben, das nach der Implementierung einer Fehlerbehebung in der letzten Version auftrat. Beim Verbinden mit SSL/TLS wurde eine Prüfung des Host-Namens hinzugefügt, die dazu führte, dass der SMS-Sendungen fehlschlugen. Die Überprüfung des Host-Namens wurde für die meisten Protokolle wie POP3, SMS und HTTP mit Proxy deaktiviert, und die Zertifikatsprüfung für das externe SMS-Konto wurde mithilfe von drei Werten verbessert (NEO-29581). [Weitere Infos](../../delivery/using/sms-protocol.md#skip-tls)

**Korrekturen**

* Fehlerkorrektur – Die Tastenkürzel &quot;Tab&quot;, &quot;Eingabe&quot; und &quot;Escape&quot; können jetzt auf dem neuen Anmeldebildschirm angezeigt werden.
* Fehlerkorrektur – Der Name eines neu erstellten Workflows wird jetzt nach dem Speichern nicht mehr durch den Standardwert ersetzt (NEO-26106).
* Fehlerkorrektur – Beim Ausführen von Workflows, bei denen vor einer **Versandaktivität** ein neues Feld als Teil einer **Anreicherungsaktivität** mithilfe eines Zielgruppen-Mappings auf der Basis von **externen Dateien** hinzugefügt wird, besteht jetzt kein Problem mehr. Zuvor wurden dem Zielgruppen-Mapping auf der Basis von **externen Dateien** unerwünschte Felder hinzugefügt. (NEO-27687)
* Fehlerkorrektur – Jetzt werden beim erneuten Öffnen einer zuvor erstellten und gespeicherten Web-Anwendung keine Zeichen im Quellcode mehr geändert. (NEO-27597)
* Fehlerkorrektur – Beim Aktualisieren auf einen Build, der den neuen Signaturmechanismus zum Tracking von Links bereitstellt (ab Build 19.1.4 und Campaign 20.2), tritt jetzt kein Problem mehr auf. Wenn mehrere Vorlagen mit einem Ereignis verknüpft waren, konnte die Aktualisierung zuvor dazu führen, dass beim Senden der Transaktionsnachricht die falsche Vorlage ausgewählt wurde. (NEO-28326)
* Fehlerkorrektur – Mit dem MTA tritt jetzt kein Problem mehr auf. Zuvor konnte es passieren, dass er nicht mehr reagierte und keine Sendungen mehr verarbeiten konnte, sodass er neu gestartet werden musste. (NEO-27455)
* Fehlerkorrektur – In der MSSQL-Datenbank tritt jetzt während Massenladevorgängen kein Problem mehr mit der Zeitzonenverwaltung in einer Spalte vom Typ „Datum/Uhrzeit“ auf. (NEO-27375)
* Fehlerkorrektur – Die Workflow-Abfrage funktioniert bei Verwendung von Redshift-xtk-Funktionen jetzt fehlerfrei. Die SubDays-, SubSeconds-, SubMinutes- und SubHours-Funktionen akzeptieren nun beide Redshift-Zeitstempeltypen (NEO-24962).
* Fehlerkorrektur – Jetzt wird keine Skript-Fehlermeldung mehr angezeigt, wenn versucht wird, eine Vorschau eines Berichts mit anonymem Zugriff zu erstellen. (NEO-27081)
* Fehlerkorrektur – Bei der Durchführung der Versandanalyse wird die Speichernutzung auf dem Server nicht mehr verringert.
* Fehlerkorrektur – Bei der Ausführung bestimmter komplexer Abfragen funktioniert die Instanz jetzt einwandfrei.
* Fehlerkorrektur – Der technische Workflow zum **Synchronisieren von Twitter-Seiten** kann jetzt problemlos ausgeführt werden. (NEO-28634)
* Es wurde ein Problem behoben, bei dem eine Fehlermeldung im Zusammenhang mit der Funktion „decryptPassword“ angezeigt werden konnte, wenn versucht wurde, auf X (früher bekannt als Twitter) unter Verwendung der Vorlage **Tweet (twitter)** zu veröffentlichen. (NEO-28216)
* Fehlerkorrektur – Jetzt tritt kein Problem mehr auf, wenn zum Erstellen einer HTTP-Anfrage in einem Workflow eine **JavaScript**-Aktivität verwendet wird. Nach der Definition der Port-Nummer im Host-Namen schlug der Aufruf fehl, und folgender Fehler wurde angezeigt (NEO-29146):

```
IOB-090020 Error in SSL library: 'IOB-090013 error:14090086:SSL routines:ssl3_get_server_certificate:certificate verify failed (code 336134278)'
```

* Fehlerkorrektur – Jetzt können neue Sendungen mit personalisierten Zielgruppendaten durchgeführt wurden (NEO-30323).
* Fehlerkorrektur – In der Marketing-Instanz treten keine Abstürze mehr auf, die Core-Dateien erzeugen.
* Fehlerkorrektur – Der **Tracking**-Workflow schlägt nicht mehr fehl. Zuvor wurde folgender Fehler angezeigt (NEO-25206):

```
There is no index on the sourceId field of the 'NmsTrackingLogRcp' table required for the current Web tracking mode. Please add this index.
```

* Fehlerkorrektur – Beim Erstellen und Speichern eines Versands in der Registerkarte **Zielgruppenbestimmungen und Workflows** einer Kampagne tritt jetzt kein Fehler mehr auf. Zuvor schlug die Vorschau fehl und folgender Fehler wurde angezeigt (NEO-29440):

```
XTK-170024 The temporary 'temp:deliveryEmail-all' schema is not defined in the current context
```

* Fehlerkorrektur – Beim Einrichten eines externen Kontos zwischen einer Marketing-Instanz und einer Adobe Campaign Standard-Instanz oder einer Campaign Classic-Mid-Sourcing-Instanz tritt bei Verwendung der Option &quot;DisableFOH2 = 1&quot; jetzt kein Fehler mehr auf. Bei Verwendung der Option &quot;DisableFOH2 = 1&quot; im externen Konto wurden die Verbindungen nicht ordnungsgemäß geschlossen und stauten sich, was zu folgendem Fehler führte (NEO-26258):

```
The maximum number of connections has been reached (50) by connections pool 'nms:extAccount:acsDefaultRelayAccount XXX'. The server is overloaded. Please try again later.
```

* Fehlerkorrektur – Beim SMS-Versand tritt jetzt kein Fehler mehr auf, wenn Verbindungsprobleme zwischen Server und Provider bestehen. Zuvor wurde die Verbindung vom untergeordneten MTA-Element automatisch deaktiviert. Adobe Campaign Classic versuchte erst wieder, eine neue Verbindung herzustellen, wenn ein neues untergeordnetes Element gestartet wurde. 
