---
title: Version 19.1
seo-title: Version 19.1
description: Version 19.1
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
source-git-commit: edb8f495fff90f51ae00006453b6ec09d84a8f55
workflow-type: tm+mt
source-wordcount: '2654'
ht-degree: 82%

---


# Version 19.1{#release-19-1}

## ![](assets/do-not-localize/limited_2.png) Version 19.1.7 – Build 9036 {#release-19-1-7-build-9036}

_15. September 2020_

**Verbesserungen**

* Verbesserte nlsrvmod-Verwendung für Apache 2.4-Thread zur Korrektur von nlsrvmod-Abstürzen.
* Es wurde ein Problem bei der Verwendung der File Transfer-Aktivität mit einem leeren Externe Konto und einer SSL-Verschlüsselung behoben. Die Verbindung wurde über HTTP statt über HTTPS hergestellt. (NEO-26720)



* In den Eigenschaften des Versands wurde die Option **[!UICONTROL E-Mails]** archivieren in **[!UICONTROL E-Mail-BCC]** umbenannt, um eine bessere Benutzerfreundlichkeit zu erzielen.
* Es wurde ein Problem mit dem URL-Cache-Mechanismus behoben, bei dem die Beschriftung oder Kategorie nicht abgerufen wurde.
* Es wurde ein Fehler behoben, der dazu führte, dass Mirrorseiten-URLs in E-Mail-Versänden falsch definiert wurden (aufgrund einer fehlerhaften ASCII-Zeichensteuerung). (NEO-26084)
* Die Liste &quot;jarsToSkip&quot; in &quot;catalina.properties&quot; wurde aktualisiert, um den Verweis auf eine nicht mehr verwendete JAR-Datei zu entfernen (iOS-Benachrichtigungen).
* Korrektur des Regressionsfehlers, der nach der Veröffentlichung nach der Aktualisierung verhindert wurde.
* Korrektur einer Regression mit vordefinierten Versandberichten, die beim Exportieren in PDF abgeschnitten erschienen. (NEO-25757)
* Es wurde ein Problem behoben, durch das der Wert des Kodierungsparameters bei der Umleitung von einer Tracking-URL gelöscht wurde (Auswirkungen auf japanische Zeichen). (NEO-25637)
* Fehlerkorrektur – Nicht signierte Links von personalisierten Domains werden nicht mehr blockiert, wenn sie zulässig sind. (NEO-25210)
* Es wurde eine Regression behoben, die berechnete Felder in einem Workflow beeinflusste und dazu führte, dass der Workflow fehlschlug. (NEO-25194)
* Es wurde ein Kompatibilitätsproblem mit Microsoft Dynamics (ab Version 8.2) behoben, das die Ausführung einiger API-Aufrufe verhindern konnte (RetrieveAllEntities). (NEO-24528)
* Korrektur des Regressionsfehlers bei Verwendung der ACS Connector-Funktion, der die Verbindung zu einer Campaign Standard-Instanz verhinderte (fehlerhafte Verwaltung der FOH/FOH2-Verbindung). (NEO-23433)
* Korrektur des Regressionsfehlers bei der Datenbankverbindung, der dazu führte, dass der Webserver aufgrund eines Datenbankkodierungsproblems ständig neu gestartet wurde. Dies könnte zu einem Überkonsum führen. (NEO-23264)



* Es wurde ein Problem mit dem Arbeitsablauf für die Datenbankbereinigung behoben, das aufgrund nicht verwalteter Datenquelle fehlschlagen konnte. (NEO-23160, NEO-23364)
* Der Bereinigungsarbeitsablauf bereinigt abgelaufene Listen nun durch Stapel von 100 anstelle von 1 nach 1.
* Nach dem Wechsel zum [neuen Sequenz-ID-Mechanismus](https://helpx.adobe.com/de/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence) werden alle Webanwendungen, die die Empfänger-Tabelle aktualisieren, während des Postupgrads erneut veröffentlicht.
* Es wurde ein Fehler behoben, der verhinderte, dass E-Mails gesendet werden, wenn außerhalb des HTML-Inhalts-Tags Javascript-Code vorhanden war. (NEO-18628)
* Fehlerkorrektur – Trackingindikatoren für Transaktionsnachrichten werden jetzt vom Tracking-Workflow aktualisiert. (NEO-17770)
* Die Leistung des Datenbankaktualisierungsassistenten wurde verbessert, um weniger SQL-Anweisungen auszugeben, um die Reaktionszeit zu optimieren.
* Es wurde ein Problem mit einem Absturz der Konsole behoben, das beim Deaktivieren der Verfolgte URLs in einer E-Mail auf der Registerkarte **Textinhalt** aufgrund einer nicht initialisierten Variablen auftrat. (NEO-13545)
* Es wurde ein Problem behoben, das das Hochladen von Dateien in einer File Transfer-Aktivität mithilfe eines Azurblauch-Datenspeicherung-Externen Kontos aufgrund einer nicht initialisierten Variable (m_pCurlReader) verhinderte. (NEO-13717)



* Es wurde ein Problem nach der Aktualisierung behoben, durch das Apache und der Webserver vor der Webanwendungsveröffentlichung deaktiviert wurden. (NEO-27155)



* Korrektur einer Regression, die dazu führte, dass beim Festlegen der Zeit in einer Workflow-Aktivität der **Planung** eine falsche Zeitzone ausgewählt wurde.

## ![](assets/do-not-localize/orange_2.png) Version 19.1.6 – Build 9035 {#release-19-1-6-build-9035}

>[!CAUTION]
>
>Dieser Build ist nur für On-Premise-Installationen gedacht. Bei Hybridbereitstellungen wird von gehosteten Instanzen weiterhin Build 9032 ausgeführt. Aktualisieren Sie Ihre Marketing-Instanz nicht auf den Build 9035, da er nicht mit Build 9032 kompatibel ist.

_3. Oktober 2019_

**Neuheiten**

* Fehlerkorrektur – Die Verwendung von CRM-Connector für Salesforce funktioniert nun problemlos. (NEO-17712)
* Fehlerkorrektur – Ein Indexfehler verursacht beim Senden von Transaktionsnachrichten keine Leistungsprobleme mehr.
* Fehlerkorrektur – Beim Senden von Nachrichten treten keine Leistungsprobleme mehr auf. (NEO-17558)
* Es wurde ein Fehler behoben, der dazu führte, dass bestimmte Nachrichten nicht vom Mid-Sourcing-Server verarbeitet wurden. (NEO-12395)
* Fehlerkorrektur – Die SQL-Data-Management-Aktivität lässt sich jetzt voll nutzen (es fehlte die spezifische „SQL-Data-Management“-Berechtigung).

## ![](assets/do-not-localize/red_2.png) Version 19.1.5 – Build 9033{#release-19-1-5-build-9033}

_13. August 2019_

**Neuheiten**

* Fehlerkorrektur – Bei der SQL-Anweisung &#39;SELECT COUNT&#39; wird in der Data-Management-Aktivität nicht mehr die Standard-Datenbank, sondern die FDA-Datenbank zur Extraktion herangezogen.
* Um die Möglichkeiten der Kundeninfrastruktur zu verbessern, ist jetzt eine SFTP-Proxy-Deklaration in der Server-Konfigurationsdatei verfügbar.
* Es wurde ein Absturzfehler behoben, der auftrat, wenn das **Hinzufügen verknüpfte Tabellenfeld** in der Workflow-Aktivität **Data Loading (RDBMS)** leer war. (NEO-12213)
* Es wurde ein Problem mit der midEmitter-Paketinstallation über die Befehlszeile behoben.
* Eine neue Authentifizierungsoption wurde hinzugefügt, die in AC Connector in Verbindung mit Microsoft Dynamics OAuth-Zugangsdaten unterstützt. (NEO-11982)
* Es wurde ein Problem bei der Verwaltung der UUID (Unique Universal Identifier) behoben, das dazu führte, dass die Aktivitäten für den Arbeitsablauf zum Laden von Abfragen und Daten mit der Hive-FDA fehlschlugen.
* Korrektur einer Regression bei Oracle, die dazu führte, dass einige Funktionen nach der Aktualisierung als ungültig betrachtet wurden. (NEO-12759)



* Es wurde eine Regression behoben, die dazu führte, dass beim Festlegen der Planung in einer Workflow-Aktivität eine falsche Zeitzone ausgewählt wurde.

## ![](assets/do-not-localize/green_2.png) Version 19.1.4 – Build 9032{#release-19-1-4-build-9032}

>[!NOTE]
>
>Gold Standard Version 19.1.4 ist auf dieser [Seite](../../rn/using/gold-standard.md) aufgeführt.


## ![](assets/do-not-localize/red_2.png) Version 19.1.2 – Build 9029{#release-19-1-2-build-9029}

_21. Juni 2019_

**Verbesserungen bei der Sicherheit**

* Zur Verbesserung der Sicherheit wurde die Java-Bibliothek (Netty) auf die neueste Version (4.1.34) aktualisiert. (NEO-12788)

**Neuheiten**

* Korrektur der mit der Sdomain-Spaltenverwaltung zusammenhängenden Regression – E-Mails können jetzt bei allen Konfigurationen gesendet werden.
* Zur Leistungssteigerung wurde das Attribut _operation=&quot;none&quot; zu rtEvent-SOAP-Aufrufen hinzugefügt, um die Anfragen &quot;UPDATE AUSWÄHLEN&quot; zu vermeiden.
* Behebung eines Workflow-Anzeigeproblems bei ausgehenden Transitionen nach der Testaktivität. (NEO-12727)
* Jetzt können in Microsoft Dynamics erstellte Platzhaltereinträge während des Import-Workflows gelöscht werden.
* Erweiterte Berechtigungen zur Ausführung des Sicherheitszonen-Package bei der Verwendung eines internen Kontos.

## ![](assets/do-not-localize/red_2.png) Version 19.1 – Build 9026{#release-19-1-build-9026}

_30. Mai 2019_

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
   <td> <p>Sie können die Einstellungen Ihrer SFTP-Server mittels Speicherüberwachung verwalten, IP-Adressen auf die Zulassungsliste setzen und für jede Instanz SSH-Schlüssel installieren, um die Effizienz Ihrer Arbeit als Admin-Benutzer zu steigern. Beachten Sie, dass das Control Panel von jetzt an nur für Kunden verfügbar ist, die auf AWS gehostet werden (<a href="https://experiencecloud.adobe.com/campaign/controlpanel/">melden Sie sich noch heute über Experience Cloud an</a>).</p> <p>Weiterführende Informationen finden Sie in der <a href="https://docs.adobe.com/content/help/de-DE/control-panel/using/control-panel-home.html">ausführlichen Dokumentation</a> und in <a href="https://docs.adobe.com/content/help/de-DE/campaign-classic-learn/tutorials/administrating/control-panel-acc/control-panel-overview.html">diesem Video</a>. </p><p>Hinweis: Für den Zugriff auf das Control Panel ist keine Aktualisierung auf den neuesten Campaign-Build nötig.</p> </td> 
  </tr> 
    <tr> 
   <td> Audit-Protokoll<br /> </td> 
   <td> <p>Als Administrator können Sie die Produktivität steigern, indem Sie Änderungen in der Adobe Campaign Classic-Instanz überwachen und verwalten. Im Audit-Protokoll werden die Aktionen protokolliert, die in Quellschemata, Workflows und Optionen durchgeführt wurden. Damit können Sie schnell erkennen, ob ein Element angelegt, geändert oder gelöscht wurde.</p><p>Weiterführende Informationen finden Sie im <a href="../../production/using/audit-trail.md">entsprechenden Handbuch</a> und im <a href="https://docs.adobe.com/content/help/de-DE/campaign-classic-learn/tutorials/monitoring/audit-trail.html">Anleitungsvideo</a>.</p></td> 
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
* FDA über HTTP v2: Das FDA über HTTP-Protokoll wird häufig bei hybriden Implementierungen verwendet, insbesondere für den Abruf von Broadlogs und die Sendungsvorbereitung. Die Stabilität wurde verbessert, um Netzwerkprobleme und mögliche Fehler beim Abrufen oder Senden von Daten zu vermeiden. Dies setzt voraus, dass die Builds an beiden Enden der Verbindung auf dem neuesten Stand sind, da ansonsten das alte Protokoll weiterhin verwendet wird.
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
* Wenn während der Analyse eines Deco-mail-Versands der Publikationsmodus im Softwareverteilungs-Assistenten auf **[!UICONTROL Keine]** gesetzt ist, wird ein Fehler angezeigt und die Analyse wird angehalten: &quot;Für den Publikationsmodus ist Keiner ausgewählt: Bild kann nicht eingebettet werden. Bilder werden nicht auf Feature Phone angezeigt.&quot; (NEO-12208)
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
