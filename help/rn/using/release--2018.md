---
product: campaign
title: Campaign Classic-Versionen 2018
description: Weiterführende Informationen zu Campaign Classic-Versionen 2018
hidefromtoc: true
exl-id: f70fceba-4bbf-4f33-8746-e4405a1cdae6
source-git-commit: c929557ee9f5467f9c3b8eb1ed25fae5399820ba
workflow-type: ht
source-wordcount: '5423'
ht-degree: 100%

---

# Versionen 2018{#release-2018}

![](../../assets/v7-only.svg)

## Version 18.10

### Version 18.10.6 – Build 8985{#release-18-10-6-build-8985}

_12. Juli 2019_

**Neuheiten**

* Jetzt können in Microsoft Dynamics erstellte Platzhaltereinträge während des Import-Workflows gelöscht werden.
* Fehlerkorrektur – In der Workflow-Aktivität &quot;Datei-Wächter&quot; werden keine Fehler mehr in einer Dauerschleife protokolliert, wenn der Zugriff auf eine Datei verweigert wird. (NEO-12085)
* Fehlerkorrektur – Berichte zu Benutzeraktivitäten und Tracking-Berichten für den offenen Versandindikator stimmen jetzt überein. (NEO-11742)
* Erweiterte Berechtigungen zur Ausführung des Sicherheitszonen-Package bei der Verwendung eines internen Kontos.
* Fehlerkorrektur – In den MTA-Kindprotokollen treten jetzt keine Fehler mehr auf. (NEO-8978)

### Version 18.10.5 – Build 8984{#release-18-10-5-build-8984}

_23. April 2019_

**Neuheiten**

* Fehlerkorrektur – Bei gleichzeitiger Analyse/gleichzeitigem Versand tritt jetzt kein SQL-Deadlock mehr auf. Zuvor wurde dadurch die Versandanalyse verhindert (wenn zwei Sendungen gleichzeitig analysiert wurden). (NEO-13026)
* Das Datensatzlimit von 10.000 wurde in der Workflow Heatmap entfernt, um ein Problem mit fehlenden Daten zu beheben. (NEO-12329)
* Fehlerkorrektur – Die Option &quot;Alle Zusatzdaten der Hauptmenge beibehalten&quot; funktioniert jetzt in einer Anreicherungsaktivität eines Workflows einwandfrei. (NEO-13291)

### Version 18.10.4 – Build 8983{#release-18-10-4-build-8983}

_15. April 2019_

**Neuheiten**

* Fehlerkorrektur – Die Berechnung von Tracking-Indikatoren für Transaktionsnachrichten funktioniert jetzt einwandfrei. (NEO-12529, NEO-12581)
* Fehlerkorrektur – Die HTTP-Abfrage-API wartet jetzt, bis alle Callbacks beendet sind. (NEO-12628)
* In den temporären Coupon-Tabellen wurden Indizes hinzugefügt, um den Versand zu optimieren. (NEO-12437)
* Fehlerkorrektur – Nachrichten an Empfänger in japanischen Domains (.JP) können jetzt problemlos analysiert werden. (NEO-12246)
* In der Analytics-Integration ist nun das Abrufen von AAM-Segmentdaten mit %-Zeichen erlaubt. (NEO-12025)
* Fehlerkorrektur – Beim Versand von Push-Benachrichtigungen über HTTP2 stürzt Tomcat nicht mehr ab. (NEO-12701)

### Version 18.10.3 – Build 8981{#release-18-10-3-build-8981}

&#x200B;29. Januar 2019

>[!CAUTION]
>
>Dieser Build wurde zurückgerufen. Bitte [aktualisieren Sie auf den neuesten Build](../../production/using/build-upgrade.md) oder wenden Sie sich an die [Adobe Kundenunterstützung](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

**Neuheiten**

* Fehlerkorrektur – Bei der Workflow-Aktivität zur Dateiübertragung über S3 tritt jetzt kein Fehler mehr auf. (NEO-12473)
* Fehlerkorrektur – Beim Tracking-Workflow tritt jetzt kein Fehler mehr auf. (NEO-12520)
* Fehlerkorrektur – Die IMS-Anmeldung funktioniert jetzt einwandfrei.
* Fehlerkorrektur – Die Vorschau und Inhaltsvalidierung von Transaktionsnachrichten funktioniert jetzt auch bei Verwendung einer langen Angebotskennung.
* Fehlerkorrektur – Beim Workflow zum Mid-Sourcing (Versandzähler) tritt jetzt kein Fehler mehr auf.
* Fehlerkorrektur – Bei der Aktualisierung der Datenbankstruktur gehen jetzt keine neuen Indizes mehr auf NmsRecipient verloren.
* Fehlerkorrektur – Jetzt stürzt die Konsole nicht mehr ab, wenn die Option &quot;In einer externen Datei definiert&quot; für die Hauptzielgruppe eines Versands verwendet wird. (NEO-12349)
* Fehlerkorrektur – Jetzt treten keine InMail-Abstürze mehr auf.
* Fehlerkorrektur – Die in einer FDA-Teradata-Datenbank gespeicherten Datensätze können jetzt mit der Workflow-Aktivität &quot;Daten-Update&quot; gelöscht werden.
* Bei der Verwaltung von geheimen Schlüsseln treten jetzt keine Abweichungen mehr auf.
* Fehlerkorrektur – In der Anreicherungsaktivität tritt jetzt kein Fehler mehr auf, wenn Folgendes in ein Feld eingegeben wird: xml=true und calculated=true k.
* Fehlerkorrektur – Beim Senden einer Push-Benachrichtigung auf einer Mobile App tritt kein Escaping-Fehler mehr auf.
* Fehlerkorrektur – In einem externen Mid-Sourcing-Konto kann jetzt von der FDA- zur SOAP-Synchronisationsmethode gewechselt werden.

### Version 18.10.2 – Build 8978{#release-18-10-2-build-8978}

&#x200B;6. Dezember 2018

>[!CAUTION]
>
>Dieser Build wurde zurückgerufen. Bitte [aktualisieren Sie auf den neuesten Build](../../production/using/build-upgrade.md) oder wenden Sie sich an die [Adobe Kundenunterstützung](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

**Neuheiten**

* Mehrere Probleme bei der Ausführung von Workflows unter Verwendung von MySQL bei FDA wurden beseitigt. (NEO-11652)
* Fehlerkorrektur – Beim Versand von Push-Benachrichtigungen treten keine Leistungsprobleme mehr auf. (NEO-11787)
* Fehlerkorrektur – Bei der Verwendung von Testadressen in einem Versand sind IDs jetzt unbegrenzt verfügbar. (NEO-11842)
* Fehlerkorrektur – Bei der Verwendung von komplexen Workflows friert der Client nicht mehr ein. (NEO-11847)
* Fehlerkorrektur – Die Werteverteilung mit einer 1:N-Relation wird jetzt korrekt angezeigt. (NEO-11820)
* Fehlerkorrektur – In der Workflow-Heatmap tritt kein Oracle-Fehler mehr auf.
* Fehlerkorrektur – Beim Hinzufügen eines Angebotsvorschlags in einer Anreicherungsaktivität tritt kein Rechtefehler mehr auf.
* Fehlerkorrektur – Bei der SQL-Daten-Management-Verbindung tritt kein Fehler mehr auf.
* Fehlerkorrektur – Temporäre Workflow-Tabellennamen können jetzt mit negativen IDs erstellt werden.
* Fehlerkorrektur – Die Workflow-Dauer in Workflow-Heatmap wird jetzt korrekt berechnet.


### Version 18.10.1 – Build 8977{#release-18-10-build-8977}

&#x200B;5. November 2018

>[!CAUTION]
>
>Dieser Build wurde zurückgerufen. Bitte [aktualisieren Sie auf den neuesten Build](../../production/using/build-upgrade.md) oder wenden Sie sich an die [Adobe Kundenunterstützung](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

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
   <td> Verbesserung bei Push-Benachrichtigungen<br /> </td> 
   <td> In Adobe Campaign wurden für Push-Benachrichtigungen einige Verbesserungen implementiert:<br /> 
    <ul> 
     <li> <p>Tracken stiller Benachrichtigungen unter iOS </p> </li> 
     <li> <p>Implementieren von Feedback zu Registrierungsaufrufen unter iOS</p> </li> 
     <li> <p>Beschleunigte iOS-Versandvorbereitung</p> </li> 
    </ul> <p>Aufgrund der Beendigung von GCM durch Google ermöglicht der Android-V2-Connector jetzt nur Verbindungen zum FCM-Server.</p><p>Weitere Informationen finden Sie in der <a href="../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md">entsprechenden Dokumentation</a>.</p> </td> 
  </tr> 
  <tr> 
   <td> SQL-Data-Management-Aktivität<br /> </td> 
   <td> <p>Eine neue Data-Management-Workflow-Aktivität wurde hinzugefügt. Mit der <strong>SQL-Data-Management</strong>-Aktivität können Sie für Arbeitstabellen eigene SQL-Scripts schreiben oder mit Copy &amp; Paste einfügen (nur FDA). </p> <p>Weitere Informationen finden Sie im <a href="../../workflow/using/sql-data-management.md">entsprechenden Handbuch</a>.</p></td> 
  </tr> 
  <tr> 
   <td> Workflow-Monitoring<br /> </td> 
   <td> <p>Mit der neuen Workflow-HeatMap von Adobe Campaign haben Plattformadministratoren die Möglichkeit, alle gleichzeitig ausgeführten Workflows rasch grafisch darzustellen, um so die Auslastung der Instanz zu überwachen und Workflows entsprechend zu planen.</p> <p>Weitere Informationen finden Sie im <a href="../../workflow/using/heatmap.md">entsprechenden Handbuch</a>.</p> <p>Das Workflow-HeatMap-Package ist auch auf Anfrage für Builds vor 8977 erhältlich (ab Build 8700). Weiterführende Informationen zur Anfrage und Installation finden Sie auf <a href="https://helpx.adobe.com/de/campaign/kb/install-workflow-heatmap-package.html">dieser Seite</a>.</p> </td> 
  </tr> 
 </tbody> 
</table>

**Verbesserungen bei der Sicherheit**

* Eine Sicherheitslücke wurde geschlossen, die potenzielle SSRF- (Server Side Request Forgery) und DoS-Angriffe (Denial of Service) ermöglicht hätte. (NEO-11453)
* Inhalt (Tracking-Umleitung, Mirrorseiten, Umfragen etc.) wird jetzt von Campaign mit dem X-Robots-Tag-Header nocache bereitgestellt. Dadurch wird verhindert, dass dieser Inhalt von Internet-Suchmaschinen indexiert wird. (NEO-11101)
* Fehlerkorrektur – EXTK-Injections in der Anmelde-API funktionieren jetzt problemlos (nms:subscription:Unsubscribe und nms:subscription:Subscribe).
* Ein Problem bei XTK-Injections in der Abmelde-Webanwendung wurde behoben.
* Passwörter, die in manchen SMS-Logs angezeigt wurden und daher ein Sicherheitsrisiko darstellten, wurden entfernt.

**Neuheiten**

* Campaign-Classic-APIs sind jetzt auf einer [eigenen Seite](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=de) verfügbar. Wenn Sie die Jsapi.chm-Datei verwendet haben, sollten Sie jetzt die neue Online-Version nutzen.
* PostgreSQL 10, Debian 9 und Teradata 16.20 werden jetzt unterstützt. Weiterführende Informationen dazu finden Sie in der [Kompatibilitätsmatrix](https://helpx.adobe.com/de/campaign/kb/compatibility-matrix.html).
* Bei der Erstellung einer SFTP-Verbindung kann jetzt Proxy-Authentifizierung verwendet werden. Weiterführende Informationen dazu finden Sie im [entsprechenden Handbuch](../../installation/using/file-res-management.md). (NEO-9868)
* Bei der Erstellung eines einzelnen Versands unter Verwendung der Briefpost-Versandvorlage ist jetzt in den Versandeigenschaften eine Option mit einer **Datumsberechnungsformel** verfügbar. (NEO-9792)
* Die Domain-Namensverwaltung wurde für Cookie-Tracking und Webanwendungen verbessert. Weiterführende Informationen dazu finden Sie im Abschnitt &quot;Technische Entwicklungen&quot; weiter unten.
* Der Import von freigegebenen Assets aus Adobe Marketing Cloud in einen Versand oder eine Landingpage wurde im Hinblick auf Sicherheit und Leistung verbessert.
* Über ein neues Kästchen im für den Mobile-Kanal verwendeten externen Konto können ausführliche SMPP-Protokolle in der Protokolldatei aktiviert werden. Dadurch sind diese Daten jetzt direkt über die Adobe-Campaign-Benutzeroberfläche abrufbar.
* In den Broadlogs wird jetzt zwischen der maximalen Anzahl der Verbindungen und der maximalen Anzahl der Nachrichten pro Stunde unterschieden. Wenn das Limit erreicht wurde, wird jetzt der Grund für den beschränkten Durchsatz angegeben. Zuvor wurde in beiden Fällen dieselbe Mitteilung angezeigt (‘quota met’).
* Jetzt können Sie ein SQL-Script spezifizieren, das ausgeführt werden soll, wenn eine Verbindung aus dem Pool wiederverwendet wird. Dieses Script kann zum Festlegen des Standardschemas verwendet werden und wird im Anschluss an das Query Banding angewendet. (NEO-11256)
* In Übereinstimmung mit unseren Regeln zu personenbezogenen Daten speichert Campaign SDK die Nutzerkennung nicht mehr. Daten werden jetzt als Hash gespeichert.
* Beim Import einer XML-Datei eines Package-Exports unterstützt Campaign jetzt das Vorhandensein von BOM in der Datei, selbst wenn die Codierung darin explizit deklariert ist.

**Technische Entwicklungen**

Client- und Server-Upgrade

>[!CAUTION]
>
>Wenn Ihr Server auf Version 18.10 aktualisiert wurde, müssen Sie einen Client der Version 18.10 verwenden, um auf den Server zugreifen zu können. Der 18.10-Client kann auch eine Verbindung mit einer älteren Serverversion herstellen.

Domain-Namensverwaltung

Die Domain-Namensverwaltung wurde für Cookie-Tracking und Webanwendungen verbessert.

Jetzt werden alle aus zwei Buchstaben bestehenden Second-Level-Domain-Namen standardmäßig unterstützt (z. B.: .aa.com). Komplexere Domain-Namen (z. B. aus drei Buchstaben bestehende Second-Level-Domains wie .com.au) müssen in der Option **cookieDomains** in serverConf hinzugefügt werden (unter dem Weiterleitungs-Tag). Hier ist ein Beispiel:

```
<redirection cookiedomain="http://toureiffel.paris">
```

Index-Verbesserungen

Indizes in NmsRecipient wurden überarbeitet. Das verbessert die Abfrageleistung in Verbindung mit dieser Tabelle. Falls Sie NmsRecipient erweitert haben, sollten Sie sicherstellen, dass keine doppelten Indizes vorhanden sind (um den Platzbedarf auf dem Datenbankserver zu minimieren). (NEO-8228)

Bei der Verwendung einer UTF-8-Kollation in PostgreSql ist es jetzt möglich, Indizes zu erstellen, die Operationen vom Typ &quot;LIKE &#39;string%&#39;&quot; (oder &quot;beginnt mit&quot;) optimieren. Wenn Sie andere Operationen in derselben Spalte ausführen (z. B. &quot;Ordnen nach&quot; oder &quot;Verbinden&quot;), ist ein weiterer Standardindex erforderlich. Auf der Schemaseite erfolgt dies durch das Hinzufügen von indexOption=&quot;searchFromStart&quot; in der Indexdefinition (dadurch wird ein varchar_pattern_ops-Index anstelle eines Standard-btree-Index erstellt). Beispiel (in NmsRecipient):

```
<dbindex name="email2"> <!-- optimize order by/join (and startWith if not PostgreSql with an UTF-8 collation) operations -->
  <keyfield xpath="@email"/>
</dbindex>
<dbindex name="email3" indexOption="searchFromStart"><!-- optimize startsWith operation on PostgreSql when a UTF-8 collation is used; create no index in other cases-->
  <keyfield xpath="@email" />
</dbindex>
```

Neue Indizes wurden zu NmsRtEvent und NmsEventHisto hinzugefügt (in der Spalte &quot;Geplant&quot;). Dadurch wird die Anzeigedauer des entsprechenden Formulars verbessert (NEO-11738).

Durch diese Indexänderungen kann es vorkommen, dass die Durchführung des Postupgrade länger dauert.

**Korrekturen**

* Fehlerkorrektur – Dateien aus der Workflow-Aktivität **HTTP-Übertragung** können jetzt heruntergeladen werden. (NEO-11105)
* Fehlerkorrektur – Der Workflow **Übermittlung der Kampagnen-Indikatoren und -Attribute** endet jetzt nicht mehr gelegentlich mit einem Fehlerstatus (NEO-10820).
* Fehlerkorrektur – Die nach der Listen-Update-Aktivität in einem Workflow erstellte Empfängerliste wird jetzt nicht mehr gelöscht. (NEO-11696)
* Fehlerkorrektur – Kampagnen im Campaign-Kalender werden nicht mehr einen Monat zu früh dargestellt (japanische Instanz). (NEO-11445)
* Fehlerkorrektur – Die Analytics-Konfiguration ist jetzt im Web-Analytics-Tab der Versandeigenschaften sichtbar. (NEO-11619)
* Fehlerkorrektur – Beim Bearbeiten und Speichern des Eingabeformulars nms:delivery wird kein Fehler mehr angezeigt. (NEO-10973)
* Fehlerkorrektur – Bei externen Konten tritt kein Konfigurationsfehler mehr auf, wenn ein Workflow mit einer Datenübertragungs-Aktivität ausgeführt wird. (NEO-11012)
* Fehlerkorrektur – Jetzt werden keine leeren Zeilen mehr zurückgegeben, wenn in der Laden-der-Daten-Aktivität die zcat-Funktion zum Laden von Dateien verwendet wird. (NEO-11273)
* Fehlerkorrektur – Bei der Versandanalyse werden keine doppelten Broadlogs mehr erzeugt. (NEO-11360)
* Fehlerkorrektur – Nach der Ausführung der Anreicherungs-Aktivität in einem Workflow tritt kein Versandfehler mehr wegen eines fehlenden Fremdschlüssels einer Relation auf. (NEO-11537)
* Fehlerkorrektur – Adobe Campaign kann jetzt korrekt deinstalliert oder repariert werden, auch wenn der Installationspfad bestimmte chinesische GB18030-Zeichen enthält.
* Fehlerkorrektur – Trackinglogs werden jetzt nicht mehr dem falschen Versand zugeordnet. (NEO-11412)
* Fehlerkorrektur – Manche Teile der Versandlogs bleiben nicht mehr unerwartet lange im Status &quot;Ausstehend&quot;. (NEO-11336)
* Fehlerkorrektur – Jetzt tritt kein Fehler mehr auf, wenn eine Abfrage bearbeitet wird, um einem Versand einen Gutschein hinzuzufügen. (NEO-11037)
* Fehlerkorrektur – In Berichten wird jetzt von den Grafiken nicht mehr unabhängig vom ausgewählten aggregierten Operator die Summe der Werte berechnet. (NEO-10913)
* Die veraltete Funktion &quot;request.scheme&quot; wurde aus der JSAPI-Dokumentation entfernt. (NEO-10828)
* Fehlerkorrektur – Jetzt können sich alle Benutzer unabhängig von der Zeitzonenkonfiguration bei Adobe Campaign anmelden. (NEO-10712)
* Fehlerkorrektur – Jetzt tritt kein Fehler mehr auf, wenn ein externes Konto für den Mobile-Kanal unter Verwendung des Connectors &quot;Erweitertes allgemeines SMPP&quot; eingerichtet wird. Wenn Sie für den Empfänger die Verwendung unterschiedlicher Parameter spezifiziert hatten, verwendete der Transmitter irrtümlich diese Parameter anstelle seiner eigenen.
* Fehlerkorrektur – Geplante Sendungen können jetzt fehlerfrei durchgeführt werden, wenn für die Druckregel eine Frequenz festgelegt wird. Zuvor waren die Sendungen nach der ersten Schlichtung immer wieder neu berechnet worden. (NEO-10016)
* Fehlerkorrektur – Der IIS-Webserver stürzt nicht mehr während des Recycling-Vorgangs des Anwendungspools ab (in nlsrvmod.dll-Bibliothek). (NEO-10862)
* Fehlerkorrektur – Jetzt ist es möglich, einen Empfänger im Fenster **Profile und Zielgruppen** zu suchen. (NEO-8228)
* Fehlerkorrektur – Jetzt tritt kein Zeitüberschreitungsfehler mehr auf, wenn Sie auf den Ereignisverlauf-Ordner zugreifen und eine größere Anzahl von Datensätzen vorhanden ist. (NEO-11738)
* Fehlerkorrektur – Empfänger von LINE-Sendungen werden nicht mehr fälschlicherweise als &quot;Unerreichbar&quot; zurückgegeben. (NEO-10833)
* Fehlerkorrektur – Jetzt tritt kein Fehler mehr auf, wenn eine Workflow-Abfrage mit einer zusätzlichen Spalte in Oracle durchgeführt wird. (NEO-11615)
* Eine Verbesserung wurde vorgenommen, damit geschlossene Verbindungen nicht zu lange im Verbindungspool bleiben. (NEO-11392)
* Fehlerkorrektur – Jetzt tritt kein Fehler mehr auf bei der Verwendung einer Zielgruppen-Workflow-Aktivität (Abfrage, Laden (DBMS) etc.), die per FDA mit einer externen Oracle-Tabelle verbunden ist, die sowohl UTF8-Zeichen (im Tabellennamen, Feldnamen etc.) als auch eine Primärschlüssel-Einschränkung mit einem vom System generierten Standard-Einschränkungsnamen enthält. (NEO-10714)
* Fehlerkorrektur – Der HTML-Inhalt eines Versands kann jetzt problemlos gelöscht werden. (NEO-11327)
* Fehlerkorrektur – Jetzt tritt kein Problem mehr bei der Vorschau von XML- und CSV-Dateien in einer Briefpost auf, nachdem eine Kampagne durchgeführt worden ist. (NEO-11290)
* Fehlerkorrektur – Daten können jetzt in einer Anreicherungs-Workflow-Aktivität problemlos sortiert werden. (NEO-11394)
* Fehlerkorrektur – Daten können jetzt in einem benutzerdefinierten Bericht problemlos sortiert werden. (NEO-10896)
* Fehlerkorrektur – Die useVault-Einstellung kann jetzt problemlos mit Teradata verwendet werden. (NEO-11399)
* Fehlerkorrektur – Jetzt stürzt die Adobe-Campaign-Clientkonsole nicht mehr ab, wenn mehrere Abfragezeilen gelöscht werden. (NEO-10744)
* Fehlerkorrektur – Jetzt können bei allen Briefpost-Sendungen Druckregeln angewendet werden. (NEO-9004)
* Fehlerkorrektur – Mit der Aktivität &quot;Laden der Daten&quot; kann jetzt eine Spalte importiert werden, die den Datentyp &quot;Uhrzeit&quot; enthält. Zuvor wurde das Trennzeichen auch nach dem Entfernen zurückgesetzt. (NEO-10743)
* Fehlerkorrektur – Der Versandordner wird jetzt im Ausführungsordner in den Versandeigenschaften angezeigt, wenn ein wiederkehrender Versand bearbeitet wird. (NEO-11094)
* Fehlerkorrektur – Im Fenster &quot;Population ansehen&quot; werden jetzt auch mehr als 200 Datensätze als resultierende Zielgruppe aus einer Abfrageaktivität in einem Workflow angezeigt. (NEO-11195)
* Fehlerkorrektur – In Oracle wird eine DELETE-Abfrage jetzt auch mit über 1.000 ausgewählten Elementen ausgeführt. (NEO-11171)
* Fehlerkorrektur – URLs werden jetzt nicht mehr in den zusätzlichen Parametern eines Android-Push-Benachrichtigungsversands als getrackte URLs codiert. (NEO-11468)
* Fehlerkorrektur – Jetzt tritt kein Scriptfehler im Bericht &quot;Nutzer-Aktivitäten&quot; mehr auf, wenn die Parameter auf &quot;Verteilung nach Tagen&quot; und &quot;Öffnungen&quot; gesetzt werden. (NEO-11655)
* Fehlerkorrektur – Jetzt tritt kein Fehler mehr auf, wenn eine Verbindung mit dem Mid-Sourcing-Server oder dem Message Center über eine authentifizierte Web Proxy hergestellt wird. (NEO-11309)
* Fehlerkorrektur – Jetzt tritt kein Oracle-Fehler mehr auf, wenn ein neuer Versand gespeichert wird, nachdem ein Element eines bestimmten Schemas **auf der Basis einer SQL-Ansicht** ausgewählt wurde. (NEO-11682)
* Fehlerkorrektur – Jetzt werden keine Zurückweisungsdateien mit False Positives mehr erstellt, wenn eine ZIP-Datei, die eine CSV-Datei enthält, über eine Datei-laden-Aktivität unter Verwendung der Dekomprimierungsoption verarbeitet wird.
* Die Bereinigung von xtkjoblog funktioniert jetzt.

## Version 18.6

### Version 18.6.2 – Build 8949{#release-18-6-3-build-8949}

&#x200B;22. August 2018

>[!CAUTION]
>
>Dieser Build wurde zurückgerufen. Bitte [aktualisieren Sie auf den neuesten Build](../../production/using/build-upgrade.md) oder wenden Sie sich an die [Adobe Kundenunterstützung](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

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
   <td> Query Banding<br /> </td> 
   <td> <p>Wenn mehrere Campaign-Benutzer auf dasselbe externe FDA-Teradata-Konto zugreifen, können Sie jetzt für jeden Benutzer ein Query Banding (Schlüssel/Wert-Paar) vergeben. Jedes Mal, wenn ein Campaign-Benutzer eine Abfrage für die Teradata-Datenbank durchführt, kann Adobe Campaign nun Metadaten im Zusammenhang mit dem Benutzer senden. Diese Daten, die aus einer Liste von Schlüsseln und Werten bestehen, können dann von Teradata-Administratoren beispielsweise für Audits oder zum Verwalten der Zugriffsberechtigungen verwendet werden.</p><p>Weitere Informationen finden Sie im <a href="../../installation/using/external-accounts.md">entsprechenden Handbuch</a>.</p> </td>
  </tr> 
 </tbody> 
</table>

**Neuheiten**

* E-Mail-Archivierungs-Logs wurden verbessert. Dank der BCC-Archivierung kann jetzt einfacher festgestellt werden, welche E-Mails erfolgreich gesendet wurden oder fehlgeschlagen sind. (NEO-10675)
* Fehlerkorrektur – In den Tracking-Broadlogs werden jetzt Kunden-IPs anstatt Lastverteilungs-IPs angezeigt. (NEO-11295)
* Fehlerkorrektur – Die Eigenschaften eines Versands werden nicht mehr fälschlicherweise überschrieben. (NEO-11015)
* Fehlerkorrektur – Beim Sortieren der Ergebnisse von Anreicherungsaktivitäten tritt kein Syntaxfehler mehr auf. (NEO-11394)
* Fehlerkorrektur – Bei der Verwendung von berechneten Feldern in der Workflow-Aktivität **[!UICONTROL Umfrageantworten]** tritt kein Fehler mehr auf. (NEO-11382)
* Tomcat wurde aktualisiert, um zu verhindern, dass Schwachstellen ausgenutzt werden können. (NEO-11503)
* Fehlerkorrektur – Bei der LATIN1-Codierung tritt jetzt kein Fehler mehr auf, wenn eine FDA-Verbindung zu einer PostgreSQL-Datenbank verwendet wird. (NEO-11299)
* Fehlerkorrektur – Bei der Verwendung der Versandoption **[!UICONTROL Personalisierungsdaten mit einem Workflow vorbereiten]** tritt kein Fehler mehr auf. (NEO-11047)
* Fehlerkorrektur – SMS können jetzt in Verbindung mit einem erweiterten Connector gesendet werden, ohne dass ein Postupgrade-Fehler auftritt.
* Verbesserter Package-Import/-Export (in der Benutzeroberfläche wurden Log und Region hinzugefügt).
* Fehlerkorrektur – Im Postupgrade-Log werden keine unnützen Fehler mehr angezeigt, wenn die Workflow-Aktivität **[!UICONTROL Umfrageantworten]** nicht vollständig konfiguriert ist.

**Technische Entwicklungen**

Query Banding

Die Zuordnung eines Teradata-Benutzers bzw. einer Teradata-Rolle zum jeweiligen Campaign-Benutzer erfolgt über einen speziellen Schlüssel (PROXYUSER oder PROXYROLE). Jetzt wurde eine neue Berechtigung hinzugefügt, um die Verwendung dieser Proxy-Benutzer/-Rollen zu ermöglichen. Sie müssen dazu die Zugriffsberechtigung GRANT CONNECT THROUGH zum Datenbankkonto hinzufügen (das im externen Teradata-Konto definiert wurde).

In den externen Teradata-Konten wurde ein neuer Tab hinzugefügt. Der Tab **[!UICONTROL Query Banding]** weist die folgenden Optionen auf:

* **[!UICONTROL Aktiv]**: Aktivieren Sie dieses Kontrollkästchen, um die Funktion zu aktivieren.
* **[!UICONTROL Standard]**: Geben Sie einen Standardwert für Query Banding ein, der verwendet wird, wenn einem Benutzer kein Query Banding zugeordnet ist. Wenn kein Standardwert für Query Banding definiert ist, können Benutzer ohne Query Banding Teradata nicht verwenden.
* **[!UICONTROL Benutzer]**: Geben Sie für jeden Benutzer einen Query Banding-Wert an. Sie können so viele Schlüssel/Wert-Paare wie benötigt hinzufügen. Beispiel: ‘priority=1;workload=high;’

Weitere Informationen zu Query Banding finden Sie in diesen Artikeln.

* [https://docs.teradata.com/reader/cY5B~oeEUFWjgN2kBnH3Vw/a5G1iz~ve68yTMa24kVjVw](https://docs.teradata.com/reader/cY5B%7EoeEUFWjgN2kBnH3Vw/a5G1iz%7Eve68yTMa24kVjVw)
* [https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/qVNfdszBssrZ7ttrE7AtmQ](https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/qVNfdszBssrZ7ttrE7AtmQ)

### Version 18.6.1 – Build 8947{#release-18-6-build-8947}

_25. Juni 2018_

>[!CAUTION]
>
>Dieser Build wurde zurückgerufen. Bitte führen Sie eine [Aktualisierung auf den aktuellen Build](../../production/using/build-upgrade.md) durch oder kontaktieren Sie den [technischen Support](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

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
   <td> Verbesserungen bezüglich der Sicherheit<br /> </td> 
   <td> In Campaign Classic wurde eine Reihe von Verbesserungen bezüglich der Sicherheit vorgenommen. Nachfolgend finden Sie eine Liste der Verbesserungen und Fehlerkorrekturen.<br /> </td> 
  </tr> 
  <tr> 
   <td> Unterstützung von Windows Server 2016<br /> </td> 
   <td> Adobe Campaign ist jetzt mit Windows Server 2016 kompatibel. Weiterführende Informationen dazu finden Sie in der <a href="https://helpx.adobe.com/de/campaign/kb/compatibility-matrix.html">Kompatibilitätsmatrix von Campaign Classic</a>.<br /> </td> 
  </tr> 
 </tbody> 
</table>

**Verbesserungen bei der Sicherheit**

decryptString

Die **decryptString**-Funktion ist veraltet. Weitere Informationen finden Sie im Artikel [Veraltete und entfernte Funktionen](deprecated-features.md).

Für Neukunden wird diese Funktion nun nur zum Entschlüsseln der verschlüsselten ID des Empfängers auf Landingpages verwendet. Zum Entschlüsseln von in einem externen Konto gespeicherten Passwörtern verwenden Sie die neue **decryptPassword**-Funktion.

Für Bestandskunden ist das Verhalten dieser Funktion unverändert. Wir empfehlen jedoch, **decryptPassword** anstelle von **decryptString** zu verwenden. Die Kompatibilitätsoption **XtkSecurity_Unsafe_DecryptString** wird vom Postupgrade hinzugefügt und standardmäßig aktiviert, weshalb Sie die Funktion auch weiterhin verwenden können. Wenn Sie **decryptString** deaktivieren möchten, deaktivieren Sie diese Option.

decryptPassword

Die **decryptPassword**-Funktion wurde hinzugefügt. Hiermit können Sie ein in einem externen Konto gespeichertes Passwort entschlüsseln. Weitere Informationen finden Sie in der [JSAPI](https://helpx.adobe.com/de/campaign/kb/compatibility-matrix.html)-Dokumentation.

Datei-APIs

Für Neuinstallationen ist der Ordnerzugriff über Datei-APIs auf **var**, **sftp** und temporäre Ordner von Adobe Campaign beschränkt.

Für Bestandskunden haben Datei-APIs keinen Zugriff mehr auf den Ordner **conf** von Adobe Campaign. Die Kompatibilitätsoption **XtkSecurity_Disable_JSFileSandboxing** wird vom Postupgrade hinzugefügt und standardmäßig aktiviert, weshalb Sie auch weiterhin auf die anderen Ordner zugreifen können. Wenn Sie den Zugriff auf **var**, **sftp** und die temporären Ordner von Adobe Campaign beschränken möchten, deaktivieren Sie diese Option.

**Korrektur**

* Fehlerkorrektur – Die Leistung von SMS-Transaktionsnachrichten wird nun nicht mehr beeinträchtigt. (NEO-9812)

## Version 18.4

### Version 18.4.5 – Build 8937{#release-18-4-5-build-8937}

_21. November 2018_

**Neuheiten**

* Mehrere Probleme bei der Ausführung von Workflows unter Verwendung von MySQL bei FDA wurden beseitigt. (NEO-11652)
* Fehlerkorrektur – Jetzt verharrt kein Teil der Versandpopulation mehr im Status &quot;Ausstehend&quot;. (NEO-11336)
* Fehlerkorrektur – Jetzt tritt bei der automatischen SMS-Antwort kein Problem mehr auf. (NEO-11811)
* Fehlerkorrektur – Bei der Verwendung von Testadressen in einem Versand sind IDs jetzt unbegrenzt verfügbar. (NEO-11842)
* Fehlerkorrektur – Beim Sortieren in einer Anreicherungsaktivität in einem Workflow tritt kein Syntaxfehler mehr auf. (NEO-11394)
* Fehlerkorrektur – Beim Neustart von IIS besteht nicht mehr die Gefahr eines Webserver-Absturzes. (NEO-10862)
* Fehlerkorrektur – Im Tracking-Workflow tritt nach einer Build-Aktualisierung kein Fehler mehr auf (FDA - SQL). (NEO-11635)
* Fehlerkorrektur – Workflow-Listendaten gehen jetzt nicht mehr verloren. (NEO-11696)
* Fehlerkorrektur – Beim Versand von Push-Benachrichtigungen treten keine Leistungsprobleme mehr auf. (NEO-11787)
* Fehlerkorrektur – Webtracking funktioniert jetzt für &quot;com.au&quot;-Domains. (NEO-4385)
* Fehlerkorrektur – Bei der Verwendung von komplexen Workflows friert der Client nicht mehr ein. (NEO-11847)
* Fehlerkorrektur – Jetzt tritt beim Speichern eines neuen Versands nach der Auswahl eines Elements eines bestimmten Schemas kein Oracle-Fehler mehr auf. (NEO-11682)
* Fehlerkorrektur – Jetzt tritt beim Aufrufen eines Feldes, das Zeichen mit Akzenten enthält, kein Fehler mehr auf (FDA/Teradata). Sie können die Kodierung zur Kommunikation mit dem Teradata-Treiber jetzt über das externe Konto ändern. (NEO-11818).
* Fehlerkorrektur – Die Mobile App erhält jetzt keine falsch formatierten oder falschen Daten mehr, wenn URLs in zusätzlichen Variablen in einer Push-Benachrichtigung weitergegeben werden. (NEO-11468, NEO-11960)
* Fehlerkorrektur – Die Werteverteilung mit einer 1:N-Relation wird jetzt korrekt angezeigt. (NEO-11820)
* Fehlerkorrektur – Bulk-Load funktioniert in Teradata 16 jetzt einwandfrei.
* Die Puffergröße für den Zeitstempel bei Teradata wurde erhöht, um Bind-Probleme beim 15.10-Treiber zu vermeiden.
* Die Verwaltung langer Indexnamen wurde verbessert, was andernfalls Probleme mit dem Postupgrade verursachen könnte.
* Die Verfügbarkeitsdauer des gemeinsamen Speichers bei der Verarbeitung von untergeordneten Zombieprozessen wurde verlängert (MTA).
* In Apache wurde ein potenzieller Deadlock behoben (Tracking).


### Version 18.4.4 – Build 8936{#release-18-4-4-build-8936}

1. August 2018

**Neuheiten**

* E-Mail-Archivierungs-Logs wurden verbessert. Dank der BCC-Archivierung kann jetzt einfacher festgestellt werden, welche E-Mails erfolgreich gesendet wurden oder fehlgeschlagen sind. (NEO-10675)
* Fehlerkorrektur – In den Tracking-Broadlogs werden jetzt Kunden-IPs anstatt Lastverteilungs-IPs angezeigt. (NEO-11295)
* Fehlerkorrektur – Bei der LATIN1-Codierung tritt jetzt kein Fehler mehr auf, wenn eine FDA-Verbindung zu einer PostgreSQL-Datenbank verwendet wird. (NEO-11299)
* Fehlerkorrektur – Bei der Verwendung der Versandoption **[!UICONTROL Personalisierungsdaten mit einem Workflow vorbereiten]** tritt kein Fehler mehr auf. (NEO-11047, NEO-11301)
* Fehlerkorrektur – Die Eigenschaften eines Versands werden nicht mehr fälschlicherweise überschrieben. (NEO-11015)
* Fehlerkorrektur – Bei der Verwendung von berechneten Feldern in der Workflow-Aktivität **[!UICONTROL Umfrageantworten]** tritt kein Fehler mehr auf. (NEO-11382)
* Es wurde ein Problem behoben, das bei der Verwendung von in XML gespeicherten Daten in einer Workflow-Aktivität **[!UICONTROL Umfrageantworten]** auftrat. (NEO-10816)
* Es wurde ein Problem bei der Server-Aktualisierung mit Build 8935 behoben.
* Fehlerkorrektur – Im Postupgrade-Log werden keine unnützen Fehler mehr angezeigt, wenn die Workflow-Aktivität **[!UICONTROL Umfrageantworten]** nicht vollständig konfiguriert ist.
* FDA-Teradata: Es wurde ein Problem mit automatisch inkrementierten Feldern und Indizes in SQL-Tabellen behoben.

### Version 18.4.3 – Build 8935{#release-18-4-3-build-8935}

_22. Juni 2018_

**Neuheiten**

* Fehlerkorrektur – die Tracking-Kodierung bei Microsoft Edge und Internet Explorer funktioniert nun fehlerfrei. (NEO-11257)
* Fehlerkorrektur – Bildlinks beim LINE-Versand können nun personalisiert werden. (NEO-11077)
* Fehlerkorrektur – der Mechanismus für die Generierung von ID-Sequenzen wird nun ordnungsgemäß ausgeführt. (NEO-11115)
* Fehlerkorrektur – Datenschutzanfragen (DSGVO) funktionieren nun, wenn ein benutzerdefinierter Namespace mit einem Integer-Abstimmschlüssel verwendet wird. (NEO-11123)
* Fehlerkorrektur – die Verwendung der Option **[!UICONTROL Werteverteilung]** in **[!UICONTROL Abfrage]**-Workflow-Aktivitäten funktioniert nun fehlerfrei. (NEO-10958)
* Fehlerkorrektur – die Synchronisierung von Platzierungen zwischen der Marketinginstanz und der Interaktionsinstanz funktioniert nun fehlerfrei. (NEO-11162)
* Die Verwaltung langer Indexnamen während des Postupgrades wurde verbessert.

### Version 18.4.2 – Build 8932{#release-18-4-2-build-8932}

_22. Mai 2018_

**Neuheiten**

* Fehlerkorrektur – das Update für Windows Server wird nun ordnungsgemäß ausgeführt.
* Fehlerkorrektur – für die Aktivität **[!UICONTROL Umfrageergebnis]** wird der Bericht bei Verwendung von in XML gespeicherten Daten nun ordnungsgemäß angezeigt. (NEO-10816)
* Fehlerkorrektur – für den inMail-Prozess tritt bei Verwendung eines Bounce Message-Servers kein Leistungsproblem mehr auf. (NEO-10641)
* Fehlerkorrektur – bei der Aktualisierung von mehr als 1.000 Schemata gibt es kein Problem mehr beim Datenbank-Update.

### Version 18.4.1 – Build 8931{#release-18-4-build-8931}

_24. April 2018_

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
   <td> EU-Datenschutz-Grundverordnung (DSGVO)<br /> </td> 
   <td> <p>Die DSGVO ist die neue Datenschutz-Grundverordnung der Europäischen Union (EU), die am 25. Mai 2018 in Kraft tritt und in der die Anforderungen an den Datenschutz harmonisiert und neu geregelt werden. Die DSGVO gilt für Adobe Campaign-Kunden, die Daten von Personen erfassen, die in der EU wohnhaft sind.</p> <p>Aus diesem Grund möchten wir als Datenverarbeiter Ihnen als Datenverantwortlichen zusätzlich zu den bereits in Adobe Campaign verfügbaren Datenschutzoptionen (Einverständnisverwaltung, Einstellungen für die Datenbeibehaltung und Benutzerrollen etc.) weitere Funktionen bereitstellen, mit deren Hilfe Sie DSGVO-konformes Verhalten sicherstellen können:</p> 
    <ul> 
     <li> <p>Recht auf Zugriff: Die betroffene Person hat das Recht, eine Kopie seiner personenbezogenen Daten, die vom Datenverantwortlichen erfasst werden, zu erhalten. Hierzu zählen unter Umständen auch die in Adobe Campaign gespeicherten Daten.</p> </li> 
     <li> <p>Recht auf Löschung: Die betroffene Person hat das Recht, seine personenbezogenen Daten, die vom Datenverantwortlichen erfasst werden, löschen zu lassen. Hierzu zählen unter Umständen auch die in Adobe Campaign gespeicherten Daten.</p> </li> 
    </ul> Lesen Sie für weiterführende Informationen das <a href="https://helpx.adobe.com/de/campaign/kb/acc-privacy.html">entsprechende Handbuch</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> Aktive Profile<br /> </td> 
   <td> <p>Adobe Campaign stellt nun eine Liste aktiver Profile zur Verfügung, die jeden Monat mithilfe eines speziellen Workflows aktualisiert wird.</p> <p>Weitere Informationen finden Sie im <a href="../../platform/using/about-profiles.md#active-profiles">entsprechenden Handbuch</a>.</p> </td> 
  </tr> 
  <tr> 
   <td> Verbesserung des Android-Connectors für Push-Benachrichtigungen<br /> </td> 
   <td> <p>Der Android-Connector wurde verbessert und bietet jetzt höheren Durchsatz. </p> <p>Weitere Informationen finden Sie im <a href="../../delivery/using/configuring-the-mobile-application.md">entsprechenden Handbuch</a>.</p> </td> 
  </tr> 
 </tbody> 
</table>

**Verbesserungen bei der Sicherheit**

* Die Erweiterung externer Entitäten ist jetzt deaktiviert, um potenzielle Angriffe von nicht authentifizierten Benutzern zu verhindern. (NEO-10173)
* Die Berechtigungen werden jetzt strenger gehandhabt, um Standardbenutzer daran zu hindern, die Konfigurationsparameter der Instanz zu verändern, wie etwa URLs zum Zugriff auf Anwendungen, LDAP-Einstellungen etc. (NEO-10171)
* Fehlerkorrektur – Jetzt werden keine sensiblen Daten mehr über Stack Traces offengelegt. Fehlerdetails werden jetzt im Backend an einem Ort protokolliert, der nicht vom externen Netzwerk aus zugänglich ist. (NEO-10176)
* Die Berechtigungen werden jetzt strenger gehandhabt, um Standardbenutzer daran zu hindern, die von einem Administrator hochgeladenen Dokumente und/oder exportierten Packages zu sehen. (NEO-10170)

**Neuheiten**

* **LINE-Kanal - verbesserte Architektur**: Der LINE-Kanal wird jetzt wie alle anderen Kanäle in Adobe Campaign in allen Installationstypen unterstützt: gehostet, Hybrid und On-Premise.
* **Automatische Erzeugung von Sequenzen**: Der Mechanismus zur ID-Erzeugung wurde verbessert, sodass nun die Lebensdauer von Campaign-Instanzen bei großen Objektmengen verlängert ist.

**Sonstige Änderungen**

* Für den Package-Import ist ein neuer Modus verfügbar, bei dem die Befehlszeile verwendet wird. Dadurch sind zirkuläre Abhängigkeiten möglich (nicht empfohlen für große Packages). Weiterführende Informationen dazu finden Sie im Abschnitt &quot;Technische Entwicklungen&quot;. (NEO-8979)
* Die Leistung für große, in Teradata geladene Datenmengen wurde verbessert. Außerdem wurde ein Fehler behoben, sodass nun der richtige Wert verarbeiteter Daten im Log angezeigt wird. (NEO-10429)
* Der Import von Audiences aus Audience Manager funktioniert jetzt mit aufgesplitteten Dateien. Zuvor wurde vom technischen Workflow importSharedAudience nur die letzte Datei des Segments importiert. (NEO-10156)
* Unter Windows hat sich der Standard-Installationspfad für den Campaign-Server geändert. Beim Setup der 64-Bit-Version lautet der standardmäßige Installationspfad jetzt: **C:\Program Files\Adobe\Adobe Campaign Classic v7** anstatt **C:\Program Files (x86)\Adobe\Adobe Campaign Classic v7**.
* Die Standard-MX-Regeln wurden verbessert und enthalten jetzt mehr Domains und ermöglichen höheren Durchsatz.
* Zugriffsbeschränkungen für den SOAP-Aufruf des Softwareverteilungs-Assistenten wurden verstärkt (xtk:serverOptions#SaveOptions).
* Die veraltete Bibliothek weka.jar wurde entfernt und die OpenSSL-Bibliothek wurde zur Optimierung der Sicherheit aktualisiert.
* Der technische Fakturierungs-Workflow wurde verbessert, um eine ausreichende Leistung der Instanzen sicherzustellen.
* Administratoren haben jetzt wieder die Möglichkeit, das Passwort von Benutzern festzulegen oder zurückzusetzen. Klicken Sie dazu mit der rechten Maustaste auf einen Benutzer, wählen Sie **[!UICONTROL Aktionen]** > **[!UICONTROL Passwort zurücksetzen]** und geben Sie das neue Passwort des Benutzers ein. Wir empfehlen Benutzern, ihr Passwort bei der ersten Anmeldung zu ändern. Weiterführende Informationen dazu finden Sie im [entsprechenden Handbuch](../../production/using/lost-password.md).
* Um die neue Mandantenfähigkeit in Adobe Target zu unterstützen, kann jetzt ein neuer &quot;at_property&quot;-Parameter zu URLs hinzugefügt werden, wenn Optionen und externe Konten für die Integration mit Target konfiguriert werden. Der für diesen Parameter zu verwendende Wert kann Adobe Target entnommen werden und wird von Campaign bei Abrufen in Target verwendet. Weiterführende Informationen dazu finden Sie im [entsprechenden Handbuch](../../integrations/using/inserting-a-dynamic-image.md).
* Jetzt kann eine Standard-Landingpage spezifiziert werden, die sich öffnet, wenn auf ein von Adobe Target ausgegebenes Bild geklickt wird. Zuvor wurde bei Klick nur zum bei der E-Mail-Erstellung eingefügten Standard-Bild weitergeleitet. Weiterführende Informationen dazu finden Sie im [entsprechenden Handbuch](../../integrations/using/inserting-a-dynamic-image.md).
* Im externen Konto wurde das Kästchen **Enable SMPP traces** hinzugefügt, um die Spurenausgabe zu erzwingen. Weiterführende Informationen dazu finden Sie im [entsprechenden Handbuch](../../delivery/using/sms-set-up.md#creating-an-smpp-external-account).

**Technische Entwicklungen**

queryDef

queryDef wurde in Bezug auf die Bedingung &quot;orderBy&quot; geändert. Vor der Änderung wurde der Primärschlüssel der abgefragten Tabelle implizit zur Bedingung &quot;orderBy&quot; hinzugefügt. Bei manchen Datenbank-Engines (zumindest postgresql) verhindert dies die Verwendung von Indizes (alle Felder der Bedingung orderBy müssen im selben Index eingeschlossen sein). Wenn Ihre Konfiguration vom früheren Verhalten abhängt, müssen Sie nun den Primärschlüssel in Ihrer Bedingung &quot;orderBy&quot; explizit hinzufügen.

Angenommen, Sie haben die folgende Abfrage:

```
<queryDef operation="select" schema="xtk:job" startPath="/" xtkschema="xtk:queryDef">
  <select>
     <node expr="@id"/>
   </select>
   <orderBy>
     <node expr="@logDate"/>
   </orderBy>
</queryDef>`
```

Diese würde implizit so gehandhabt werden (vor den Änderungen von 18.4):

```
<queryDef operation="select" schema="xtk:job" startPath="/" xtkschema="xtk:queryDef">
  <select>
     <node expr="@id"/>
   </select>
   <orderBy>
      <node expr="@logDate"/>
      <node expr="@id"/> <!-- implicitly added before 18.4, you can add it manually on your query, if you relied on this implicit order clauses --!>
   </orderBy>
</queryDef>
```

urlEncode function

Die JavaScript-Funktion &quot;urlEncode&quot; hat für Nicht-ASCII-Zeichen nicht ordnungsgemäß funktioniert. Das wurde jetzt korrigiert und die Funktion kann jetzt mit allen Unicode-Zeichen verwendet werden (einschließlich japanischer Zeichen). Wenn Sie für Nicht-ASCII-Zeichen das &quot;urlEncode&quot;-Verhalten benötigen, müssen Sie Ihren Code anpassen.

Neuer Modus für Package-Import

Für den Package-Import ist ein neuer Modus verfügbar, bei dem die Befehlszeile verwendet wird, was zirkuläre Abhängigkeiten ermöglicht (nicht empfohlen für große Packages). Die vorhandene Funktion wird beibehalten. Für diese Packages mit zirkulären Abhängigkeiten wurde das neue Flag **-usejs** zum Befehlszeilen-Package-Import hinzugefügt. Bei der Ausführung wird die JSEngine so verwendet, als würde der Package-Import in der Benutzeroberfläche durchgeführt.

```
nlserver package -instance:fresh -import:sup-packInstallTest.xml -verbose -usejs
```

**Korrekturen**

* Fehlerkorrektur - jetzt tritt kein Synchronisationsfehler mehr auf, wenn Versand- und Trackinglogs von Adobe Campaign Standard nach Adobe Campaign Classic repliziert werden. (NEO-10023)
* Fehlerkorrektur - jetzt können Fehler- und Log-Tabellen problemlos in Teradata verwendet werden, wenn ein ETL-Workflow nach einem Fehler bei einem Schnellladevorgang fortgesetzt wird. Die Fehler- und Log-Tabellen werden jetzt beim Fortsetzen des Workflows ordnungsgemäß gelöscht. (NEO-10672)
* Fehlerkorrektur - jetzt wird beim Postupgrade das Hive-Package automatisch installiert (für Hadoop erforderlich), wenn das FDA-Package installiert ist. (NEO-10592)
* Fehlerkorrektur - ungültige Domains werden jetzt nicht mehr als **nicht definierter** Fehler gehandhabt. (NEO-10248)
* Fehlerkorrektur - Logs werden jetzt nicht mehr in der deliveryLogStats-Tabelle dupliziert, wenn Android-Push-Benachrichtigungen gesendet werden. (NEO-10234)
* Fehlerkorrektur – jetzt können alle Barcodeformate von Barcodescannern gelesen werden. (NEO-10125)
* Fehlerkorrektur - die JavaScript-Funktion &quot;urlEncode&quot; kann jetzt mit Nicht-ASCII-Zeichen verwendet werden. Weiterführende Informationen dazu finden Sie im Abschnitt &quot;Technische Entwicklungen&quot;. (NEO-10123)
* Fehlerkorrektur - Abfragen mit sha256-Funktionen in Teradata-Datenbanken können jetzt fehlerfrei durchgeführt wird. (NEO-10119)
* Fehlerkorrektur - jetzt treten bei der SalesForce-Aktivität keine Workflow-Speicherfehler mehr auf, wenn sehr große SalesForce-Tabellen verwendet werden. (NEO-9900)
* Fehlerkorrektur - Bei Verwendung von FDA tritt in Zielgruppen-Workflow-Aktivitäten bei der Verwendung der Option **Komplement erzeugen** jetzt kein Fehler mehr auf. (NEO-9878)
* Fehlerkorrektur - die Metriken **Verarbeitet** und **Erfolg** werden jetzt in der Marketinginstanz aktualisiert, wenn Mid-Sourcing verwendet wird. (NEO-9454)
* Korrektur der Interaktionsregeln zur Verhinderung von Neuvorschlägen bei mehr als 10.000 Angeboten auf der Plattform. (NEO-9352)
* Fehlerkorrektur - die Zielgruppe eines Versands kann jetzt bei der Verwendung einer externen XML-Datei spezifiziert werden. (NEO-9312)
* Fehlerkorrektur - jetzt treten keine Workflow-Fehler mehr auf, wenn eine Hypothese für ein Angebot ausgeführt und der Status des Vorschlags aktualisiert wird. (NEO-9304)
* Fehlerkorrektur - die Versandanalyse wird jetzt fehlerfrei ausgeführt, wenn Werbedruck-Regeln auf der Basis eines Attributs des Android-Versand-Mappings verwendet werden. (NEO-9202)
* Fehlerkorrektur - Spalten in Empfängerlisten können jetzt sortiert werden, ohne Leistungsprobleme hervorzurufen. Weiterführende Informationen zu den queryDef-Änderungen finden Sie unten im Abschnitt &quot;Technische Entwicklungen&quot;. (NEO-9042)
* Fehlerkorrektur - die Links in einer Validierungs-E-Mail verweisen nicht mehr auf eine falsche Anmelde-URL. Dieser Fehler trat insbesondere auf, wenn ein Login vom Typ &quot;Federated ID&quot; verwendet wurde. (NEO-9011)
* Fehlerkorrektur - jetzt werden in der Datumsauswahl von Berichten keine falschen Daten mehr für gewisse Zeitzonen angezeigt. (NEO-9007)
* Fehlerkorrektur - die Zielgruppe eines ausgehenden Versands kann jetzt bei der Verwendung einer FDA-SQL-Datenbank angezeigt werden. (NEO-8924)
* Fehlerkorrektur - der CRM-Connector MS Dynamics ruft jetzt auch Daten für die ersten sieben Tage eines Monats ab. (NEO-8803)
* Fehlerkorrektur - bei der Analytics-Integration können jetzt auch internationale Zeichen einbezogen werden. (NEO-8719)
* Fehlerkorrektur - die Bearbeitung eines Workflows ist jetzt nur mehr mit den entsprechenden Rechten möglich. (NEO-8708)
* Fehlerkorrektur - bei FDA über HTTP treten jetzt keine Verbindungsunterbrechungen oder Verbindungsverluste (durch Zeitüberschreitung) mehr auf, wenn das Message Center in einer Hybridarchitektur verwendet wird. (NEO-8438)
* Fehlerkorrektur - jetzt treten bei der Aktivität &quot;Inkrementelle Abfrage&quot; keine Workflow-Fehler mehr für negative IDs auf. (NEO-8229)
* Fehlerkorrektur - jetzt werden Bildlaufleisten auf manchen Bildschirmen nicht mehr doppelt angezeigt. (NEO-8208)
* Fehlerkorrektur - jetzt wird keine Fehlermeldung mehr angezeigt, wenn der Assistent zur Aktualisierung der Datenbankstruktur ausgeführt wird. Im Postupgrade werden Indizes mit Namen mit mehr als 30 Zeichen umbenannt. Beachten Sie bitte, dass bei großen Tabellen das Ersetzen der Indizes einige Zeit in Anspruch nimmt. (NEO-7983)
* Fehlerkorrektur - Trackinglogs werden jetzt korrekt von der Message-Center-Ausführungsinstanz zur Kontrollinstanz synchronisiert. (NEO-7286)
* Fehlerkorrektur - bei der Angebotsanreicherungsaktivität tritt kein Leistungsproblem mehr auf. (NEO-7263)
* Fehlerkorrektur - die DaysAgo-Funktion kann jetzt verwendet werden, wenn eine Redshift-Datenbank über FDA abgefragt wird. (NEO-7099)
* Fehlerkorrektur - bei der Datenverwaltung tritt keine Regression mehr auf, sodass bei Workflow-Aktivitäten zur Anreicherung jetzt Indizes erstellt werden können.
* Fehlerkorrektur - jetzt tritt kein Fehler mehr auf, wenn externe Ressourcen mit dem Titel @id erstellt werden.
* Fehlerkorrektur - beim Hochladen von komprimierten Dateien über einen FTP-Server oder mit Wildcards im Dateinamen tritt jetzt kein Fehler mehr auf.
* Fehlerkorrektur - bei in Campaign Standard erstellten externen benutzerdefinierten Ressourcen, die Auflistungen mit Datentyp &quot;long&quot; enthalten, tritt kein Fehler mehr auf.
* Fehlerkorrektur - SMS werden jetzt nur mehr gesendet, wenn eine Verbindung mit dem Provider hergestellt werden kann. Zuvor hatte dies den Verlust von SMS zur Folge.
* Fehlerkorrektur - Der SMTP-Verbindungsaufbau kann jetzt nicht mehr unbegrenzte Zeit in Anspruch nehmen.
* Fehlerkorrektur - jetzt tritt bei Druck-Typologieregeln während der Nachrichtenvorbereitung kein Fehler mehr auf, wenn LINE-Mapping verwendet wird oder wenn die Filter- und Zielgruppenschemata unterschiedlich sind.
