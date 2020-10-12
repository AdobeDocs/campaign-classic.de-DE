---
title: Version 20.1
description: Version 20.1
page-status-flag: never-activated
uuid: 269d590c-5a6d-40b9-a879-02f5033863fc
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rns
content-type: reference
topic-tags: campaign-release-notes, latest-release-notes
discoiquuid: 5df34f55-135a-4ea8-afc2-f9427ce5ae7b
translation-type: ht
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: ht
source-wordcount: '1344'
ht-degree: 100%

---


# Version 20.1{#release-20-1}

## ![](assets/do-not-localize/orange_2.png) Version 20.1.3 – Build 9124{#release-20-1-3-build-9124}

_6. Mai 2020_

* Es wurde ein Problem mit der Aktivität **Dateiübertragung** behoben, das bei Debian 9 eine SFTP-Schlüssel-basierte Authentifizierung verhinderte. (NEO-23183)

## ![](assets/do-not-localize/orange_2.png) Version 20.1.2 – Build 9123{#release-20-1-2-build-9123}

_Freitag, 13. März 2020_

* Die Bereitstellung von Versionen auf Red Hat 7-Servern funktioniert jetzt problemlos. (NEO-23332)

## ![](assets/do-not-localize/orange_2.png) Version 20.1 – Build 9122{#release-20-1-build-9122}

_17. Februar 2020_

**Neue Funktionen**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Snowflake FDA-Connector</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>Snowflake ist ein vollständig verwaltetes Cloud Data Warehouse, das sowohl auf der Speicher- als auch der Rechenebene skaliert werden kann. Mit dem neuen Connector kann Adobe Campaign jetzt die Leistung von Snowflake nutzen, um Big-Data-Segmentierungen durchzuführen. Dieser Connector steht allen Kunden zur Verfügung, einschließlich jenen, die von Adobe gehostet werden.</p>
    <p>Weiterführende Informationen finden Sie in der <a href="../../platform/using/specific-configuration-database.md#configure-access-to-snowflake">ausführlichen Dokumentation</a> und im <a href="https://docs.adobe.com/content/help/de-DE/campaign-classic-learn/tutorials/administrating/fda/big-data-segmentation-on-snowflake.html">Tutorial-Video</a>.</p>
   </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>Verbesserungen beim Hadoop FDA-Connector</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>Der Hadoop FDA-Connector wurde optimiert und unterstützt jetzt sowohl Hadoop 3.0 als auch Cloudera.</p>
    <p>Weitere Informationen finden Sie im <a href="../../platform/using/specific-configuration-database.md#configure-access-to-hadoop-3">entsprechenden Handbuch</a>.</p>
   </td> 
  </tr> 
 </tbody> 
</table>

**Verbesserungen bei der Sicherheit**

* Verbesserte Sicherheit in der Berichtkonfiguration zum Schutz vor Clickjacking. Dies gilt für neue Berichte. Alte Berichte müssen erneut veröffentlicht werden, damit die Änderungen übernommen werden. (NEO-13282)

* Korrektur eines kleinen Arbeitsspeicherproblems in cryptString. (NEO-20071)

* Verbessertes Überwachungs-JSP zur Korrektur einer internen IP-Offenlegung. (NEO-16821)

* Fehlerkorrektur – Stack-Trace-Informationen werden jetzt nur mehr Admin-Benutzern angezeigt. (NEO-12388)

* Die Verwaltung zwischengespeicherter Daten aus vorherigen Sitzungen wurde verbessert. (NEO-17039)

* Fehlerkorrektur – Die Datei „login.log“ erfasst jetzt erfolgreiche Anmeldeversuche über IMS. (NEO-11004)

**Neuheiten**

* iOS 13 wird jetzt mit dem HTTP2-Connector unterstützt.

* Verbesserte Verwaltung der Quarantäne und Bereinigung von Tabellen, die von der Push-Benachrichtigungsfunktion verwendet werden (nms:address und nms:appSubscriptionRcp). Deaktivierte Token werden jetzt unter iOS (nur HTTP2-Connector) genauso gehandhabt wie unter Android. Das disable-Flag ist in der Tabelle „NmsAppSubscriptionRcp“ jetzt gesetzt. [mehr dazu](../../production/using/database-cleanup-workflow.md#subscription-cleanup--nmac-)

* Eine neue Option wurde den Workflow-Aktivitäten **JavaScript-Code** und **Erweiterter JavaScript-Code** hinzugefügt, um einen Timeout-Zeitraum zu definieren. Dadurch wird verhindert, dass die JavaScript-Ausführungsphase zu lange dauert. Sobald der Timeout-Zeitraum abgelaufen ist, wird der Workflow gestoppt. Der Standardwert für das Timeout beträgt 1 Stunde. [mehr dazu](../../workflow/using/sql-code-and-javascript-code.md)

* Wenn keine übereinstimmende Affinität auf dem Mid-Sourcing-Server gefunden wird, wird die Versandanalyse jetzt angehalten und die entsprechende Fehlernachricht angezeigt.

* Datenbank-Failover für Postgres wird nun unterstützt: Wenn der Datenbank-Server abstürzt und neu gestartet wird, stellt Campaign jetzt automatisch eine erneute Verbindung her.

* Die Ansicht **Start ausstehend** wurde dem Knoten „Administration“ > „Audit“ > „Status der Workflows“ hinzugefügt. Dadurch können Sie alle Workflows in Ihrer Instanz überwachen, die darauf warten, vom Prozess **operationMgt** gestartet zu werden. Diese Ansicht ist im Marketing-Kampagnen-Package enthalten. [mehr dazu](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

**Sonstige Änderungen**

* Unter Linux verwendet der Start des nlserver-Dienstes jetzt eine systemd-Einheit anstelle des Scripts /etc/init.d/nlserver6. Die Migration zum neuen Startschema wird automatisch ausgeführt, wenn Sie das Package 20.1 installieren. Der Befehl /etc/init.d/nlserver6 ist weiterhin verfügbar, dient aber zum Interagieren mit dem nlserver-Dienst (Start, Neustart, Anhalten usw.). Wir empfehlen, direkt den Befehl systemctl zu verwenden.

* Die verbrauchsintensivsten benutzerdefinierten Tabellen wurden von der Sequenz **xtkNewId** in dedizierte Sequenzen verschoben. [mehr dazu](https://helpx.adobe.com/de/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence)

* Die Abfrageleistung, die zuvor durch unnötige Datenbankverbindungen beeinträchtigt sein konnte, wurde verbessert.

* Die Leistung des Datenbankaktualisierungs-Assistenten wurde verbessert, um weniger SQL-Anweisungen auszugeben und die Antwortzeit zu optimieren.

* Das Datenbankdatensatz-Management wurde verbessert.

* Die Stabilität des Verbindungs-Pools wurde verbessert, sodass unerwartete Verbindungsfehler nicht mehr so oft auftreten.

* Die Validierungsregeln für E-Mail-Adressen, mit denen eine Adresse bei einem Softbounce unter Quarantäne gestellt werden soll, wurden verbessert. [mehr dazu](../../delivery/using/understanding-quarantine-management.md#soft-error-management)

* Für Debian verwendet Campaign jetzt PCRE-Systembibliotheken, wenn sie verfügbar sind.

* Campaign ermöglicht nun die Nutzung einer aktuelleren ODBC-Systembibliothek.

* Dem LINE-Servlet wurde beim Öffnen einer Verbindung zum Laden eines Rich-Bilds ein Timeout hinzugefügt. Wenn das Laden des Bilds zu lange dauert, stoppt das Servlet die Verbindung, um Engpässe zu verhindern.

**Korrekturen**

* Fehlerkorrektur – Die Verschlüsselung von Kontoschlüsseln bei Verwendung des Hadoop-Connectors ist jetzt problemlos möglich.

* Fehlerkorrektur – Korrektur eines Regressionsfehlers aufgrund der Implementierung der SSL-Zertifizierung. Die Benutzerverbindung auf einem Windows-Server schläft jetzt nicht mehr fehl. (NEO-20629)

* Fehlerkorrektur – Bei negativen Workflow-IDs tritt jetzt kein Problem mehr mit der inkrementellen Abfrageaktivität auf. (NEO-19779)

* Fehlerkorrektur – Beim Ausführen von Abfragen über den Netezza FDA-Connector tritt jetzt kein Kodierungsproblem mehr auf. (NEO-19594)

* Fehlerkorrektur – Die Verwendung der POST-Methode in der Workflow-Ereignisaktivität **HTTP-Übertragung** führt jetzt zu keinem Fehler mehr.

* Fehlerkorrektur – Die Generierung von Angebotsvorschlägen funktioniert jetzt einwandfrei. (NEO-18176)

* Fehlerkorrektur – Mit der Fußzeilenanzeige tritt jetzt bei Verwendung der Akquise-Webformularvorlage kein Problem mehr auf.

* Fehlerkorrektur – Beim Parsen der URLs im Inhalt von fortlaufenden Sendungen wird kein Absturz mehr verursacht. (NEO-16910)

* Fehlerkorrektur – Die Felder **Start** und **Ende** werden jetzt beim Erstellen einer neuen Kampagne berechnet.

* Fehlerkorrektur – Bei Verwendung einer URL mit der Workflow-Aktivität **Dateiempfang** tritt jetzt kein Problem mehr auf.

* Fehlerkorrektur – Bei der Vorschau einer importierten Liste in einer Abfrageaktivität eines Berichts tritt jetzt kein Problem mehr auf. (NEO-13119)

* Fehlerkorrektur – Im E-Mail-Editor wird jetzt kein veraltetes Bild mehr angezeigt, wenn der Gestaltungsbaustein **Powered by Campaign** ausgewählt wird.

* Die Netzwerkkommunikation zwischen Client und Server wurde optimiert.

* Fehlerkorrektur – Jetzt tritt kein Problem mehr auf, wenn zu viele Workflows in derselben Kampagne erstellt werden. Die Anzahl der Workflows ist jetzt auf 28 beschränkt. Bei Überschreitung wird eine Warnung angezeigt.

* Fehlerkorrektur – Die Abstimmoption **Auswahl an Spalten** kann jetzt problemlos in der Workflow-Aktivität **Vereinigung** verwendet werden.

* Fehlerkorrektur – Die Konsole stürzt jetzt nicht mehr ab, wenn in einem Workflow eine beschädigte Anreicherungsliste verwendet wird. (NEO-18096)

* Fehlerkorrektur – Verschiedene Konsolenabsturzprobleme wurden behoben, die in Workflows auftreten konnten (NEO-18010, NEO-18032).

* Fehlerkorrektur – Eine Workflow-Aktivität vom Typ **Externes Signal** ist jetzt nur mehr möglich, wenn diese aktiviert ist. (NEO-17524)

* Fehlerkorrektur – Ein neues Schema kann jetzt problemlos erstellt werden.

* Fehlerkorrektur – Beim Senden von SMS-Nachrichten tritt jetzt kein Tracking-Problem mehr auf. (NEO-19595)

* Fehlerkorrektur – In Versandindikatoren wird jetzt die korrekte Ziel-Audience-Zahl angezeigt.

* Fehlerkorrektur – Beim Generieren eines Berichts mithilfe einer Workflow-Aktivität werden jetzt korrekte Prozentwerte angezeigt. (NEO-14314)

* Fehlerkorrektur – Im Bericht zum Versanddurchsatz werden bei der Änderung der Zeitparameter jetzt nicht mehr abweichende Zahlen angezeigt. (NEO-11783)

* Fehlerkorrektur – Trackingindikatoren für Transaktionsnachrichten werden jetzt vom Tracking-Workflow aktualisiert. (NEO-17770)

* Fehlerkorrektur – Jetzt tritt kein Regressionsfehler mehr auf, der dazu führte, dass der Web-Prozess abstürzte und neu gestartet werden musste, wenn ein Angebot über SOAP angefordert wurde. (NEO-19482)

* Fehlerkorrektur – Daten können jetzt in öffentliche Ressourcen hochgeladen werden, wenn das Upload-Verzeichnis ein freigegebener Remote-Speicherort ist. (NEO-19361)

* Fehlerkorrektur – Der technische Workflow **Zielgruppenimport aus Adobe Experience Cloud** schlägt jetzt nicht mehr fehl. (NEO-18463)

* Fehlerkorrektur – Sendungen können jetzt durchgeführt werden, wenn Vorlagen aus Experience Manager importiert werden. (NEO-17540)

* Fehlerkorrektur – Nach der Aktualisierung auf Version 9032 kann jetzt die Instanz über das SSL-Protokoll eine Verbindung zum FTP-Server herstellen. (NEO-20498)

* Fehlerkorrektur – Beim Löschen, Einfügen oder Aktualisieren einer großen Datenmenge in einem Workflow mit der Aktivität **Daten-Update**, wobei ein FDA-Schema als Zielgruppendimension verwendet wird, tritt jetzt kein Problem mehr auf. (NEO-13280)

* Fehlerkorrektur – E-Mails werden jetzt auch gesendet, wenn außerhalb des HTML-Inhalts-Tags Javascript-Code vorhanden ist. (NEO-18628)

* Fehlerkorrektur – Die Mirrorseite kann jetzt in den Versandlogs einer gesendeten Nachricht angezeigt werden. (NEO-17976)

* Fehlerkorrektur – Der Gestaltungsbaustein **Mirrorseiten-Link** wird jetzt auf dem Tab **Textinhalt** angezeigt, wenn in einem Versand auf **HTML importieren** geklickt wird. (NEO-17568)

* Fehlerkorrektur – Die Fehlermeldung, die beim Klicken auf einen Link zu einer abgelaufenen Mirrorseite angezeigt wird, ist nun klarer formuliert. (NEO-17340)

* Fehlerkorrektur – Jetzt können alle Schaltflächen im Erstellungsbildschirm für die **Datenverteilung** verwendet werden.

* Fehlerkorrektur – Beim Planen einer Versandaktivität in einer Instanz mit der Zeitzone Asien/Kalkutta tritt jetzt kein Problem mehr auf. (NEO-20001)

* Es wird nun eine Fehlernachricht angezeigt, wenn die Affinitätskonfiguration beim Versand ein Problem verursacht.

* Fehlerkorrektur – Im Menü **Versionsinformationen** wird jetzt keine falsche Versions-Tag-Nummer mehr angezeigt.

* Fehlerkorrektur – Beim Versuch, das Routing-Konto über die Eigenschaften eines wiederkehrenden Versands in einem Workflow zu aktualisieren, tritt jetzt kein Problem mehr auf. (NEO-18684)

* Fehlerkorrektur – Beim Herstellen einer Verbindung mit der Instanz über das Umleitungsmodul tritt jetzt kein Problem mehr auf und die Verbindung wird nach dem Schließen ordnungsgemäß bereinigt.
