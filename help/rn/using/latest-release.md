---
product: campaign
title: Aktuelle Version
description: Aktuelle Version von Campaign Classic      Anmerkungen
feature: Übersicht
role: Business Practitioner
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: 28083eb0271c8c148955fa33978479dc3683eaed
workflow-type: tm+mt
source-wordcount: '1953'
ht-degree: 53%

---

# Aktuelle Version{#latest-release}

Auf dieser Seite werden neue Funktionen, Verbesserungen und Fehlerbehebungen der **aktuellen Campaign Classic Release Candidate-Version** aufgelistet.

>[!NOTE]
>
>**Allgemein verfügbare Builds (General Availability, GA)** von Campaign sind: [[!DNL Gold Standard] Version 11](../../rn/using/gold-standard.md#gs-11) und [Campaign Version 20.2.5](../../rn/using/release--20-2.md).

## ![](assets/do-not-localize/blue_2.png) Version 21.1.3 – Build 9330 {#release-21-1-3-build-9330}

_5. Juni 2021_

**Neue Funktionen**

<table>
<thead>
<tr>
<th><strong>Integration mit Adobe Journey Orchestration</strong><br/></th>
</tr>
</thead>
<tbody>
<tr>
<td>
<p>Die Integration zwischen Journey Orchestration und Adobe Campaign Classic ist jetzt allgemein verfügbar. Sie ermöglicht Journey Orchestration das Senden von E-Mails, Push-Benachrichtigungen und SMS mithilfe von Adobe Campaign Classic-Funktionen für Transaktionsnachrichten.</p>
<p>Die Verbindung zwischen der Journey Orchestration- und der Campaign Classic-Instanz wird bei der Bereitstellung von Adobe hergestellt.</p>
<p>Weitere Informationen finden Sie in der <a href="https://experienceleague.adobe.com/docs/journeys/using/action-journeys/acc-action.html">Dokumentation zur Journey Orchestration</a>. Ein schrittweises Anwendungsbeispiel wird in diesem <a href="https://experienceleague.adobe.com/docs/journeys/using/use-cases-journeys/campaign-classic-use-case.html">Abschnitt</a> vorgestellt</p>
</td>
</tr>
</tbody>
</table>

<table> 
<thead>
<tr> 
<th> <strong>LINE-Kanal-Verbesserungen</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>Die folgenden Verbesserungen wurden dem LINE-Kanal hinzugefügt:
</p>
<ul> 
<li><p>Unterstützung für LINE-Videomeldungstyp</p></li>
<li><p>Unterstützung der LINE Partner Registration API</p></li>
<li><p>Unterstützung eines erneuten Nachrichtenversands im Fall eines serverseitigen LINE-Fehlers oder Netzwerktimeouts</p></li>
</ul>
<p>Weitere Informationen finden Sie im <a href="../../delivery/using/line-channel.md">entsprechenden Handbuch</a>.</p>
</td> 
</tr> 
</tbody> 
</table>

<table> 
<thead>
<tr> 
<th> <strong>Vertica FDA-Connector</strong><br/> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>Jetzt können Sie Ihre Adobe Campaign Classic-Instanz mit Ihrer externen Vertikaldatenbank verbinden. Diese Verbindung wird über ein neues externes Konto verwaltet.</p>
<p>Weitere Informationen finden Sie im <a href="../../installation/using/configure-fda-vertica.md">entsprechenden Handbuch</a>.</p>
</td> 
</tr> 
</tbody> 
</table>

<table> 
<thead>
<tr> 
<th> <strong>Google Big Query FDA-Connector</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>Jetzt können Sie Ihre Adobe Campaign Classic-Instanz mit Ihrer externen Google Big Query-Datenbank verbinden. Diese Verbindung wird über ein neues externes Konto verwaltet.
</p>
<p>Weitere Informationen finden Sie im <a href="../../installation/using/configure-fda-google-big-query.md">entsprechenden Handbuch</a>.</p>
</td> 
</tr> 
</tbody> 
</table>

**Verbesserungen bei der Sicherheit**

* Der Zugriff auf die API-Methode **xtk:session#GetConxInfo**, die die vollständigen Details zur Datenbankverbindung zurückgibt, ist jetzt nur noch für Admin-Benutzer verfügbar. (NEO-27779)
* Die veraltete decryptString -Funktion wurde in CRM-bezogenen JavaScript-Dateien durch decryptPassword ersetzt.
* Die Tracking-Signaturfunktion wurde verbessert, um das Risiko von Tracking-Weiterleitungsfehlern zu verringern, wenn Drittanbieter-Tools (E-Mail-Clients, Internetbrowser, sichere Link-Sicherheitstools) den verfolgten Link ändern.
* Fehlerkorrektur - Getrackte URLs funktionieren jetzt, wenn sie Großbuchstaben enthalten. Beim Signierungsmechanismus für getrackte URLs wird jetzt zwischen Groß- und Kleinschreibung unterschieden. (NEO-28414)

**Aktualisierungen zur Kompatibilität**

Die folgenden Systeme werden jetzt von Campaign unterstützt:
* Google Big Query FDA-Connector
* Vertica FDA-Connector
* PostgreSQL 13

Weiterführende Informationen finden Sie in der [Campaign-Kompatibilitätsmatrix](../../rn/using/compatibility-matrix.md).

**Eingestellte Funktionen**

* Ab Campaign-Version 21.1 wird Adobe Analytics Data Connector nicht mehr unterstützt. Wenn Sie diesen Connector verwenden, müssen Sie Ihre Implementierung entsprechend mit dem neuen Connector Adobe Analytics Connector anpassen.
Weitere Informationen finden Sie im [entsprechenden Handbuch](../../platform/using/adobe-analytics-connector.md).
* Die Unterstützung für Debian 8 ist jetzt veraltet.
* Nach der Einstellung von Oracle CRM in Version 20.3 wurde das zugehörige externe Konto aus der Benutzeroberfläche entfernt.

Weitere Informationen finden Sie auf der Seite [Eingestellte und entfernte Funktionen ](../../rn/using/deprecated-features.md).

**Verbesserungen**

* Beim Speichern eines Workflows wurden zusätzliche Prüfungen hinzugefügt, um sicherzustellen, dass die Aktivitätsnamen eindeutig sind und dass Transitionen immer von einer Aktivität gefolgt werden.
* Der technische Workflow **Rechnungsstellung (billing)** enthält jetzt die Aufgaben, die ursprünglich vom **Anzahl der aktiven Rechnungsstellungsprofile** (billingActiveContactCount) -Workflow ausgeführt wurden, der entfernt wurde. Der monatlich vom Workflow gesendete E-Mail-Bericht enthält jetzt Informationen zur Anzahl der aktiven Profile in der Instanz. [Mehr dazu](../../workflow/using/about-technical-workflows.md)
* Es wurde ein neues **_keyOnMData** -Attribut hinzugefügt, um einen Schlüssel für Vorgänge zu Memodaten verwenden zu können.

**Sonstige Änderungen**

* Der Drittanbieter openssl für Windows wurde auf Version 1.1.1h aktualisiert.
* In der Debian-Paketbeschreibung wurde nlserver auf den Adobe Campaign Classic-Server geändert.

**Korrekturen**

* Fehlerkorrektur - Beim Bearbeiten des Sitzungs-Timeouts werden Benutzer nach einer bestimmten Zeit nicht mehr abgemeldet, wenn Benutzer auch nach der festgelegten Zeit angemeldet geblieben sind.
* Fehlerkorrektur - Sendungen werden jetzt nicht mehr als schreibgeschützt angezeigt, können aber weiterhin in den Versandeigenschaften bearbeitet werden.
* Fehlerkorrektur - die Symbolleiste für die Bearbeitung verschwindet beim Entwerfen einer Webanwendung nicht mehr.
* Fehlerkorrektur - die Textversion einer E-Mail mit Adobe Campaign Classic-Headern wird beim Hinzufügen eines Links zu einer E-Mail nun korrekt angezeigt. (NEO-29211
* Bei Verwendung von FDA über HTTP-Verbindung wurde der Workflow **Mid-Sourcing (Versandlogs)** (defaultMidSourcingLog) in dem von der Option **NmsMidSourcing_LogsPeriodHour** festgelegten Zeitrahmen festgehalten. Dadurch wird verhindert, dass Datensätze mit Daten aktualisiert werden, die nach diesem festgelegten Zeitraum aufgetreten sind. (NEO-30833)
* Fehlerkorrektur - Jetzt tritt kein Fehler mehr auf, nachdem der Synchronisations-Workflow für das Message Center ausgeführt wurde. Jedes Mal, wenn ein Ordner mit Versandobjekten in einen benutzerdefinierten Ordner verschoben wurde, verschiebte der Workflow die Sendungen zurück in den Ordner **Transaktionsnachrichten-Verlauf** . (NEO-27445)
* Fehlerkorrektur - jetzt wird keine Fehlermeldung mehr angezeigt, wenn versucht wird, die Berichte **Versandstatistiken**, **Trackingindikatoren** und **Statistiken der Teilungsaktivitäten** anzuzeigen.
* Die Workflow-Aktivität **Oracle On Demand** wurde nach der Einstellung des Oracle CRM-Connectors aus der Benutzeroberfläche entfernt.
* Fehlerkorrektur - Die Ausführung von Verarbeitungs-Workflows wird jetzt nach dem täglichen Neustart des Workflow-Server-Moduls (wfserver) nicht mehr angehalten. (NEO-30047)
* Fehlerkorrektur - Das MX-Verwaltungsdokument kann jetzt aktualisiert werden, was sich negativ auf die IP-Reputation auswirken kann. (NEO-29897)
* Es wurden Probleme behoben, die zu Webprozessabstürzen beim Empfang eines SOAP-Aufrufs führten. (NEO-28796) (NEO-29600)
* Es wurde ein Fehler behoben, der dazu führte, dass die Erstellung des SAP HANA-FDA-Index fehlschlug. (NEO-29664)
* Fehlerkorrektur - Transaktionsnachrichten bleiben jetzt nicht mehr im Status **Warten**, wenn SOAP-Aufrufe mit einem Header ausgeführt werden. (NEO-28737)
* Fehlerkorrektur - Bei der Verwendung des Teradata FDA-Connectors tritt jetzt kein Fehler mehr auf: alle temporären Tabellen wurden nur auf einem Knoten des Clusters erstellt, was letztendlich den gesamten Spool-Speicherplatz belegen und zu einem Absturz von Teradata führen konnte. Die temporären Tabellen werden jetzt auf vielen Knoten generiert. (NEO-28230)
* Fehlerkorrektur - Bei der Verwendung von Webanwendungen werden jetzt keine falschen Primärschlüssel mehr von Trackingtags im **nms:trackingURL**-Schema erzeugt. (NEO-27931)
* Die Kompatibilität mit ODBC 3.x wurde verbessert, um die Genauigkeit von Fehlermeldungen sicherzustellen.
* Fehlerkorrektur - Jetzt stürzt die Konsole nicht mehr ab, wenn benutzerdefinierte Inhaltsvorlagen in E-Mail-Sendungen verwendet werden. (NEO-31547)
* Es wurde ein Problem behoben, durch das Tomcat aufgrund einer langsamen Verbindung oder einer großen Antwortgröße keine gültigen Antworten senden konnte.
* Fehlerkorrektur - Beim Lesen der UUID aus einer PostgreSQL-Datenbank tritt jetzt kein Fehler mehr auf.
* Fehlerkorrektur - bei der Suche nach Vorschlagsdaten in Verbindung mit Angeboten treten keine Leistungsprobleme mehr auf. (NEO-27554)
* Fehlerkorrektur - Der Webprozess reagiert jetzt, wenn der IMS-Dienst aktiviert, aber nicht reagiert.
* Fehlerkorrektur - Versand mit Testsendungen ist jetzt möglich, da ein bestimmter Join-Mechanismus zur Verfügung steht, der die Versandpersonalisierung fehlgeschlagen ist. (NEO-14391)
* Fehlerkorrektur - Jetzt wird kein Warnhinweis mehr mit der Warnungsaktivität gesendet, wenn in der Versandtabelle eine Abfrage und eine Anreicherungsaktivität enthalten sind. (NEO-25157)

## ![](assets/do-not-localize/red_2.png) Version 21.1.2 – Build 9282 {#release-21-1-2-build-9282}

_15. April 2021_

* Die Verwaltung von Passwörtern wurde verbessert, um die Sicherheit zu optimieren.
* Fehlerkorrektur – Es wurde ein Problem behoben, das zum Absturz des MTA führen konnte.

## ![](assets/do-not-localize/red_2.png) Version 21.1.1 – Build 9277 {#release-21-1-1-build-9277}

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

**Email Feedback Service (EFS)** ist ein skalierbarer Dienst, der das Feedback direkt vom Enhanced MTA erfasst und damit die Reporting-Genauigkeit verbessert. Diese Funktion wird als private Betaversion veröffentlicht und wird in zukünftigen Versionen nach und nach allen Kunden zur Verfügung stehen.

* Alle Kategorien von Feedback werden jetzt für vollständiges und genaues Reporting erfasst.
* Die Berechnung des Indikators &quot;Zugestellt&quot; basiert nun auf Echtzeit-Feedback des Enhanced MTA, um Genauigkeit und Reaktivität zu verbessern.
* EFS löst das Problem der Verzögerungen beim Reporting zu synchronen Softbounces.

Weitere Informationen finden Sie im [entsprechenden Handbuch](../../delivery/using/sending-with-enhanced-mta.md#efs).
Wenn Sie an dieser privaten Beta teilnehmen möchten, füllen Sie dieses [Formular](https://forms.office.com/Pages/ResponsePage.aspx?id=Wht7-jR7h0OUrtLBeN7O4Rol2vQGupxItW9_BerXV6VUQTJPN1Q5WUI4OFNTWkYzQjg3WllUSDAxWi4u) aus. Wir werden uns bei Ihnen melden.

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
* Fehlerkorrektur – In der MSSQL-Datenbank tritt jetzt während Massenladevorgängen kein Problem mehr mit der Zeitstempelverwaltung in einer Spalte vom Typ &quot;Datum/Uhrzeit&quot; auf.
* Fehlerkorrektur – Die Workflow-Abfrage funktioniert bei Verwendung von Redshift-xtk-Funktionen jetzt fehlerfrei. Die SubDays-, SubSeconds-, SubMinutes- und SubHours-Funktionen akzeptieren nun beide Redshift-Zeitstempeltypen (NEO-24962).
* Fehlerkorrektur – Jetzt wird keine Skript-Fehlermeldung mehr angezeigt, wenn versucht wird, eine Vorschau eines Berichts mit anonymem Zugriff zu erstellen. (NEO-27081)
* Fehlerkorrektur – Bei der Durchführung der Versandanalyse wird die Speichernutzung auf dem Server nicht mehr verringert.
* Fehlerkorrektur – Bei der Ausführung bestimmter komplexer Abfragen funktioniert die Instanz jetzt einwandfrei.
* Fehlerkorrektur – Der technische Workflow zum **Synchronisieren von Twitter-Seiten** kann jetzt problemlos ausgeführt werden. (NEO-28634)
* Fehlerkorrektur – Jetzt wird im Zusammenhang mit der Funktion &quot;decryptPassword&quot; keine Fehlermeldung mehr angezeigt, wenn versucht wird, mithilfe der Versandvorlage **Tweet (Twitter)** Inhalte auf Twitter zu veröffentlichen. (NEO-28216)
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
