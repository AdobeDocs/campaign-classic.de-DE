---
title: Version 18.10
seo-title: Version 18.10
description: Version 18.10
seo-description: null
page-status-flag: never-activated
uuid: 269d590c-5a6d-40b9-a879-02f5033863fc
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rns
content-type: reference
topic-tags: latest-release-notes
discoiquuid: 5df34f55-135a-4ea8-afc2-f9427ce5ae7b
translation-type: ht
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: ht
source-wordcount: '2371'
ht-degree: 100%

---


# Version 18.10{#release-18-10}

## Version 18.10.6 - Build 8985{#release-18-10-6-build-8985}

_12. Juli 2019_

**Neuheiten**

* Jetzt können in Microsoft Dynamics erstellte Platzhaltereinträge während des Import-Workflows gelöscht werden.
* Fehlerkorrektur – In der Workflow-Aktivität &quot;Datei-Wächter&quot; werden keine Fehler mehr in einer Dauerschleife protokolliert, wenn der Zugriff auf eine Datei verweigert wird. (NEO-12085)
* Fehlerkorrektur – Berichte zu Benutzeraktivitäten und Tracking-Berichten für den offenen Versandindikator stimmen jetzt überein. (NEO-11742)
* Erweiterte Berechtigungen zur Ausführung des Sicherheitszonen-Package bei der Verwendung eines internen Kontos.
* Fehlerkorrektur – In den MTA-Kindprotokollen treten jetzt keine Fehler mehr auf. (NEO-8978)

## Version 18.10.5 - Build 8984{#release-18-10-5-build-8984}

_23. April 2019_

**Neuheiten**

* Fehlerkorrektur – Bei gleichzeitiger Analyse/gleichzeitigem Versand tritt jetzt kein SQL-Deadlock mehr auf. Zuvor wurde dadurch die Versandanalyse verhindert (wenn zwei Sendungen gleichzeitig analysiert wurden). (NEO-13026)
* Das Datensatzlimit von 10.000 wurde in der Workflow Heatmap entfernt, um ein Problem mit fehlenden Daten zu beheben. (NEO-12329)
* Fehlerkorrektur – Die Option &quot;Alle Zusatzdaten der Hauptmenge beibehalten&quot; funktioniert jetzt in einer Anreicherungsaktivität eines Workflows einwandfrei. (NEO-13291)

## Version 18.10.4 - Build 8983{#release-18-10-4-build-8983}

_15. April 2019_

**Neuheiten**

* Fehlerkorrektur – Beim Berechnungsprozess von Trackingindikatoren für Transaktionsmeldungen tritt jetzt kein Fehler mehr auf. (NEO-12529, NEO-12581)
* Fehlerkorrektur – Die HTTP-Abfrage-API wartet jetzt, bis alle Callbacks beendet sind. (NEO-12628)
* In den temporären Coupon-Tabellen wurden Indizes hinzugefügt, um den Versand zu optimieren. (NEO-12437)
* Fehlerkorrektur – Nachrichten an Empfänger in japanischen Domains (.JP) können jetzt problemlos analysiert werden. (NEO-12246)
* In der Analytics-Integration ist nun das Abrufen von AAM-Segmentdaten mit %-Zeichen erlaubt. (NEO-12025)
* Fehlerkorrektur – Beim Versand von Push-Benachrichtigungen über HTTP2 stürzt Tomcat nicht mehr ab. (NEO-12701)

## Version 18.10.3 - Build 8981{#release-18-10-3-build-8981}

_29. Januar 2019_

>[!CAUTION]
>
>Dieser Build wurde zurückgerufen. Bitte führen Sie eine [Aktualisierung auf den aktuellen Build](https://docs.campaign.adobe.com/doc/AC/getting_started/DE/buildUpgrade.html) durch oder kontaktieren Sie den [technischen Support](https://support.neolane.net/).

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

## Version 18.10.2 - Build 8978{#release-18-10-2-build-8978}

_6. Dezember 2018_

>[!CAUTION]
>
>Dieser Build wurde zurückgerufen. Bitte führen Sie eine [Aktualisierung auf den aktuellen Build](https://docs.campaign.adobe.com/doc/AC/getting_started/DE/buildUpgrade.html) durch oder kontaktieren Sie den [technischen Support](https://support.neolane.net/).

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


## Version 18.10 – Build 8977{#release-18-10-build-8977}

_5. November 2018_

>[!CAUTION]
>
>Dieser Build wurde zurückgerufen. Bitte führen Sie eine [Aktualisierung auf den aktuellen Build](https://docs.campaign.adobe.com/doc/AC/getting_started/DE/buildUpgrade.html) durch oder kontaktieren Sie den [technischen Support](https://support.neolane.net/).

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
    </ul> <p>Aufgrund der Beendigung von GCM durch Google ermöglicht der Android-V2-Connector jetzt nur Verbindungen zum FCM-Server.</p><p>Weiterführende Informationen finden Sie in der <a href="../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md">ausführlichen Dokumentation</a>. Das manuelle Upgrade auf FCM wird in diesem <a href="https://helpx.adobe.com/de/campaign/kb/migrate-to-fcm.html">Artikel</a> beschrieben. </p> </td> 
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
* Ein Problem bei XTK-Injections in der Anmelde-API wurde behoben (nms:subscription:Unsubscribe und nms:subscription:Subscribe).
* Ein Problem bei XTK-Injections in der Abmelde-Webanwendung wurde behoben.
* Passwörter, die in manchen SMS-Logs angezeigt wurden und daher ein Sicherheitsrisiko darstellten, wurden entfernt.

**Neuheiten**

* Campaign-Classic-APIs sind jetzt auf einer [eigenen Seite](https://docs.campaign.adobe.com/doc/AC/en/jsapi/index.html) verfügbar. Wenn Sie die Jsapi.chm-Datei verwendet haben, sollten Sie jetzt die neue Online-Version nutzen.
* PostgreSQL 10, Debian 9 und Teradata 16.20 werden jetzt unterstützt. Weiterführende Informationen dazu finden Sie in der [Kompatibilitätsmatrix](https://helpx.adobe.com/de/campaign/kb/compatibility-matrix.html).
* Bei der Erstellung einer SFTP-Verbindung kann jetzt Proxy-Authentifizierung verwendet werden. Weiterführende Informationen dazu finden Sie im [entsprechenden Handbuch](../../installation/using/configuring-campaign-server.md#proxy-connection-configuration). (NEO-9868)
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

