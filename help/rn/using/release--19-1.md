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
translation-type: ht
source-git-commit: 3d6c304aaa0b3e6ba1156f1a65e93f5c284b0c0a
workflow-type: ht
source-wordcount: '2859'
ht-degree: 100%

---


# Version 19.1{#release-19-1}

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

Der **neueste stabile Build** ist 9032 (3a9dc9c). Klicken Sie [hier](../../rn/using/release--19-1.md#release-19-1-4-build-9032).

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

## ![](assets/do-not-localize/orange_2.png) Version 19.1.5 – Build 9033{#release-19-1-5-build-9033}

_13. August 2019_

**Neuheiten**

* Fehlerkorrektur – Bei der SQL-Anweisung &#39;SELECT COUNT&#39; wird in der Data-Management-Aktivität nicht mehr die Standard-Datenbank, sondern die FDA-Datenbank zur Extraktion herangezogen.
* Um die Möglichkeiten der Kundeninfrastruktur zu verbessern, ist jetzt eine SFTP-Proxy-Deklaration in der Server-Konfigurationsdatei verfügbar.
* Fehlerkorrektur – Jetzt stürzt die Clientkonsole nicht mehr ab, wenn eine unbenannte verknüpfte Tabelle in der Workflow-Aktivität &quot;Daten Laden (RDBMS)&quot; hinzugefügt wird. (NEO-12213)
* Fehlerkorrektur – Jetzt kann die midEmetter-Package-Installation über eine Befehlszeile fehlerfrei installiert werden.
* Eine neue Authentifizierungsoption wurde hinzugefügt, die in AC Connector in Verbindung mit Microsoft Dynamics OAuth-Zugangsdaten unterstützt. (NEO-11982)
* Fehlerkorrektur – Die Anreicherungsaktivität funktioniert jetzt bei Hive FDA mit der UUID (Unique Universal Identifier).

## Version 19.1.4 - Build 9032{#release-19-1-4-build-9032}

![](assets/do-not-localize/green_2.png) **22. Juni 2020**: neuer Build (9032@800be2e), der die folgenden Fehlerkorrekturen enthält:

* Der iOS-HTTP2-Connector wurde verbessert (Updates von Drittanbietern und Fehlerverwaltung). (NEO-25904, NEO-25903, NEO-25799)

Die folgenden Fehlerkorrekturen beziehen sich auf den Sicherheitsmechanismus von Trackinglinks:

* Fehlerkorrektur – Tracking von &quot;Benachrichtigungsklicks&quot; (iOS- und Android-Push-Benachrichtigungen) funktioniert jetzt. (NEO-25965)
* Fehlerkorrektur – Tracking-URLs können geöffnet/geklickt werden, wenn bestimmte veraltete Outlook-Versionen verwendet werden. (NEO-25688)
* Fehlerkorrektur – Tracking von URLs mithilfe von Fragmenten in Personalisierungsparametern (Anker-Tags mit Rautenzeichen) funktioniert jetzt. (NEO-25774)
* Fehlerkorrektur – Es wurde ein Problem mit dem Anti-Phishing-Dienst behoben. (NEO-25283)
* Fehlerkorrektur – Es wurde ein Problem beim Tracking mit spezifischen benutzerdefinierten Tracking-Formeln behoben. (NEO-25277)

![](assets/do-not-localize/orange_2.png) **29. April 2020**: neuer Build (9032@3a9dc9c), der die folgenden Fehlerbehebungen enthält:

* Verbesserte Sicherheit bei Tracking-Links in E-Mails. Dies ist für alle Kunden standardmäßig aktiviert. Es gibt eine zusätzliche, erweiterte Sicherheitsfunktion, die Sie aktivieren können, indem Sie sich an die Kundenunterstützung wenden. Weiterführende Informationen zu der Funktion und den Schritten zur Aktivierung für nicht gehostete Kunden finden Sie in der [Prüfliste für Sicherheit und Datenschutz](https://helpx.adobe.com/de/campaign/kb/acc-security.html#signature-mechanism).

>[!CAUTION]
>
>Wenn Sie Probleme mit Push-Benachrichtigungen unter Verwendung von Tracking-Links oder mit dem Versand mittels Anker-Tags haben, wird empfohlen, den neuen Signaturmechanismus für Trackinglinks zu deaktivieren. Das Verfahren wird auf dieser [Seite](https://helpx.adobe.com/de/campaign/kb/acc-security.html#signature-mechanism) beschrieben.

* Fehlerkorrektur – Die Anzeige von Bildern in Line-Sendungen wird jetzt nicht mehr verhindert. (NEO-23207)
* Fehlerkorrektur – Bei der Aktivität **Dateiübertragung** funktioniert jetzt die SFTP-Schlüssel-basierte Authentifizierung bei Debian 9. (NEO-23183)
* Fehlerkorrektur – Bei Push-Benachrichtigungen, die mit hoher Häufigkeit gesendet werden, tritt jetzt kein Problem mehr auf. (NEO-20516)
* Fehlerkorrektur – Die Verwaltung von Angebotsantworten führt jetzt nicht mehr zu Webserver-Abstürzen. (NEO-19482)
* Fehlerkorrektur – In der LibreOffice-Verwaltung ist jetzt das Exportieren von Berichten möglich. (NEO-20982)
* Fehlerkorrektur – Beim Aktualisieren verschiedener Workflows mit einer Umfrageaktivität tritt jetzt kein Fehler mehr auf.
* Die LibreOffice-Verwaltung wurde verbessert, um Fehler bei der E-Mail-Vorschau mit .odt-Dateien zu verhindern.
* Die Verwaltung der Apache-Verbindung wurde verbessert, um Latenzzeiten beim Web-Dienst zu vermeiden.
* Die Anzeige des Version-Tags (siebenstellig) im Menü **Versionsinformationen** wurde verbessert.
* Fehlerkorrektur – Es wurde ein Regressionsfehler bei der Listenverwaltung behoben, der die Publizierung von Angeboten verhinderte.
* Fehlerkorrektur – Es wurde ein Regressionsfehler behoben, der zum Absturz des Bereinigungs-Workflows führte.
* Fehlerkorrektur – Es wurde ein geringfügiger Regressionsfehler in den Bereinigungs-Workflow-Logs behoben.

![](assets/do-not-localize/orange_2.png) **5. März 2020**: neuer Build (9032@19f73c5), der folgende Fehlerkorrektur enthält:

* Fehlerkorrektur – Es gibt kein Problem mehr mit externen Konten, die FTP über SSL verwenden. (NEO-20498)

![](assets/do-not-localize/orange_2.png) **17. Dezember 2019**: neuer Build (9032@d6b8062), der folgende Fehlerkorrektur enthält:

* Fehlerkorrektur – Tracking-Fehler bei folgenden Kommunikationskanälen tritt nicht mehr auf: Mobile (SMS, MMS), Push (iOS, Android) und soziale Netzwerke (Facebook, Twitter). (NEO-19595)

![](assets/do-not-localize/orange_2.png) **11. Dezember 2019**: neuer Build (9032@bc4a935), der folgende Fehlerkorrektur enthält:

* Fehlerkorrektur – Keine Leistungsprobleme mehr beim Senden von Nachrichten mit einer MSSQL-Datenbank. (NEO-17558)

![](assets/do-not-localize/orange_2.png) **20. November 2019**: neuer Build (9032@3468c7b), der folgende Fehlerkorrekturen enthält:

* Fehlerkorrektur – Die Anmeldung per IMS-Authentifizierung funktioniert nun. (NEO-17312)
* Fehlerkorrektur – Kumulative Berichte zu mehreren Sendungen werden nun richtig angezeigt. (NEO-18165)
* Fehlerkorrektur – Der Webserver wird nicht mehr blockiert oder zum Absturz gebracht.

![](assets/do-not-localize/orange_2.png) **19. September 2019**: neuer Build (9032@cee805c), der folgende Fehlerkorrekturen enthält:

* Fehlerkorrektur – Die Verwendung von CRM-Connector für Salesforce funktioniert nun problemlos. (NEO-17712)
* Fehlerkorrektur – Ein Indexfehler verursacht beim Senden von Transaktionsnachrichten keine Leistungsprobleme mehr.

![](assets/do-not-localize/orange_2.png) **13. August 2019**: erster Build 19.1.4, der folgende Fehlerkorrekturen enthält:

* Fehlerkorrektur – In der Planungsaktivität werden jetzt bei der Konfiguration des Assistenten keine unbeabsichtigten Fehlernachrichten mehr erzeugt. Update NEO-11662 wurde rückgängig gemacht. (NEO-17097)
* Regressionskorrektur – Jetzt tritt kein durch NEO-12727 verursachter Fehler mehr auf, bei dem Workflows angehalten wurden, wenn eine Testaktivität zweimal ausgeführt wird. (NEO-16835)
* Fehlerkorrektur – Jetzt wird kein fehlerhafter HTTP-Code mehr zurückgegeben (HTTP 200 OK statt HTTP 403 Forbidden), wenn ein ungültiges oder abgelaufenes Sitzungstoken in API-Aufrufen verwendet wird. (NEO-16826)
* Fehlerkorrektur – Der DKIM-Schlüssel wird jetzt in E-Mails eingebettet, sodass der Versand fehlerfrei funktioniert. (NEO-16804)
* Fehlerkorrektur – Die Workflow-Planung funktioniert jetzt wieder einwandfrei, sodass Workflows entsprechend ihrer Konfiguration ausgeführt werden. (NEO-16619, NEO-16426)

## ![](assets/do-not-localize/orange_2.png) Version 19.1.2 – Build 9029{#release-19-1-2-build-9029}

_21. Juni 2019_

**Verbesserungen bei der Sicherheit**

* Zur Verbesserung der Sicherheit wurde die Java-Bibliothek (Netty) auf die neueste Version (4.1.34) aktualisiert. (NEO-12788)

**Neuheiten**

* Korrektur der mit der Sdomain-Spaltenverwaltung zusammenhängenden Regression – E-Mails können jetzt bei allen Konfigurationen gesendet werden.
* Zur Leistungssteigerung wurde das Attribut _operation=&quot;none&quot; zu rtEvent-SOAP-Aufrufen hinzugefügt, um die Anfragen &quot;UPDATE AUSWÄHLEN&quot; zu vermeiden.
* Behebung eines Workflow-Anzeigeproblems bei ausgehenden Transitionen nach der Testaktivität. (NEO-12727)
* Jetzt können in Microsoft Dynamics erstellte Platzhaltereinträge während des Import-Workflows gelöscht werden.
* Erweiterte Berechtigungen zur Ausführung des Sicherheitszonen-Package bei der Verwendung eines internen Kontos.

## ![](assets/do-not-localize/orange_2.png) Version 19.1 – Build 9026{#release-19-1-build-9026}

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
   <td> <p>Sie können die Einstellungen Ihrer SFTP-Server mittels Speicherüberwachung verwalten, IP-Adressen auf die Zulassungsliste setzen und für jede Instanz SSH-Schlüssel installieren, um die Effizienz Ihrer Arbeit als Admin-Benutzer zu steigern. Beachten Sie, dass das Control Panel von jetzt an nur für Kunden verfügbar ist, die auf AWS gehostet werden (<a href="https://experiencecloud.adobe.com/campaign/controlpanel/">melden Sie sich noch heute über Experience Cloud an</a>).</p> <p>Weiterführende Informationen finden Sie in der <a href="https://docs.adobe.com/content/help/de-DE/control-panel/using/control-panel-home.html">ausführlichen Dokumentation</a> und in <a href="https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/administrating/control-panel-acc/control-panel-overview.html">diesem Video</a>. </p><p>Hinweis: Für den Zugriff auf das Control Panel ist keine Aktualisierung auf den neuesten Campaign-Build nötig.</p> </td> 
  </tr> 
    <tr> 
   <td> Audit-Protokoll<br /> </td> 
   <td> <p>Als Administrator können Sie die Produktivität steigern, indem Sie Änderungen in der Adobe Campaign Classic-Instanz überwachen und verwalten. Im Audit-Protokoll werden die Aktionen protokolliert, die in Quellschemata, Workflows und Optionen durchgeführt wurden. Damit können Sie schnell erkennen, ob ein Element angelegt, geändert oder gelöscht wurde.</p><p>Weiterführende Informationen finden Sie im <a href="../../production/using/audit-trail.md">entsprechenden Handbuch</a> und im <a href="https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/monitoring/audit-trail.html">Anleitungsvideo</a>.</p></td> 
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
