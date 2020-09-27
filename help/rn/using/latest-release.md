---
title: Neueste Version
description: Neueste Version des Campaign Classic
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
source-git-commit: eccf0e9899426c2517748c7a72611ff098291cd2
workflow-type: tm+mt
source-wordcount: '2163'
ht-degree: 99%

---


# Neueste Version{#latest-release}

![](assets/do-not-localize/cp-icon.png) **Neue Control Panel-Version im Juni** mit der Überwachung aktiver Profile, der Prüfung der Subdomain-Zustellbarkeit und der GPG-Schlüsselverwaltung. [Mehr dazu](https://docs.adobe.com/content/help/de-DE/control-panel/using/release-notes.html).

## ![](assets/do-not-localize/blue_2.png) Version 20.2.3 – Build 9182 {#release-20-2-3-build-9182}

_11. September 2020_

* Fehlerkorrektur – Es wurde eine Regression korrigiert, die dazu führte, dass die Sendungsvorbereitung aufgrund einer einzigen fehlerhaften Funktion im Versand blockiert wurde, was zu einer Speicherüberlastung führte. (NEO-27346)
* Fehlerkorrektur – Es wurde ein Problem mit einem Postupgrade behoben, durch das Apache und der Webserver vor der erneuten Publikation der Web-Applikation deaktiviert wurden. (NEO-27155)
* Fehlerkorrektur – Es wurde eine Regression bei der Verwaltung von HTML-Vorlagen korrigiert, die dazu führte, dass Tracking-URLs aufgrund einer falschen Interpretation von Tabs sichtbar wurden. (NEO-25909)
* Fehlerkorrektur – Es wurde ein Problem mit dem Datenbankbereinigungs-Workflow behoben, der aufgrund einer nicht verwalteten Datenquelle fehlschlagen konnte. (NEO-23160, NEO-23364)
* Der Bereinigungs-Workflow bereinigt jetzt abgelaufene Listen in Stapeln von 100 anstelle einzeln.
* Fehlerkorrektur – Es wurde eine Regression korrigiert, die verhinderte, dass Sie den internen Namen eines externen Kontos ändern konnten. (NEO-27323)
* Fehlerbehebung – Es wurde eine Regression während eines Postupgrades korrigiert, die einen fehlerhaften Start von nlserver verursachte (Fehlerprotokolle).
* Die Aktualisierungsverwaltung für gemeinsamen Speicher wurde verbessert. Die in Version 20.2 erforderlichen zusätzlichen Schritte werden nicht mehr benötigt.

## ![](assets/do-not-localize/orange_2.png) Version 20.2.2 – Build 9180 {#release-20-2-2-build-9180}

_22. Juli 2020_

* Fehlerkorrektur – Tracking funktioniert jetzt, wenn die Signaturfunktion deaktiviert ist. (NEO-26411)
* Fehlerkorrektur – Nicht signierte Links von personalisierten Domains werden nicht mehr blockiert, wenn sie zulässig sind. (NEO-25210)
* Fehlerkorrektur – Tracking-URLs können geöffnet/geklickt werden, wenn bestimmte veraltete Outlook-Versionen verwendet werden. (NEO-25688)
* Fehlerkorrektur – Es wurde ein Problem behoben, das dazu führte, dass Mirrorseiten-URLs in E-Mail-Sendungen fehlerhaft definiert wurden (aufgrund einer falschen ASCII-Zeichensteuerung). (NEO-26084)
* Fehlerkorrektur – Es wurde ein Problem mit der Kodierungsverwaltung von URLs im Anti-Phishing-Dienst behoben. (NEO-25283)
* Fehlerkorrektur – Tracking von URLs mithilfe von Fragmenten in Personalisierungsparametern (Anker-Tags mit Rautenzeichen) funktioniert jetzt. (NEO-25774)
* Fehlerkorrektur – Es wurde ein Problem beim Tracking mit spezifischen benutzerdefinierten Tracking-Formeln behoben. (NEO-25277)




* Fehlerkorrektur – Tracking von &quot;Benachrichtigungsklicks&quot; (iOS- und Android-Push-Benachrichtigungen) funktioniert jetzt. (NEO-25965)
* Fehlerkorrektur – Es wurde eine Regression korrigiert, die berechnete Felder in einem Workflow beeinträchtigte und dazu führte, dass der Workflow fehlschlug. (NEO-25194)
* Fehlerkorrektur – Eine Regression, die verhinderte, dass die spontane Erstellung von Web-Tracking-URLs funktioniert, wurde korrigiert. (NEO-20999)
* Fehlerkorrektur – Es wurde ein Regressionsfehler mit nativen Versandberichten behoben, die beim Exportieren in PDF abgeschnitten dargestellt wurden. (NEO-25757)
* Es wurde ein Absturzproblem im Softwareverteilungs-Assistenten behoben.
* Fehlerkorrektur – Der Angebotsbenachrichtigungs-Workflow funktioniert jetzt nach einem Postupgrade richtig.
* Der iOS-HTTP2-Connector wurde verbessert (Updates von Drittanbietern und Fehlerverwaltung). (NEO-25904, NEO-25903)
* Die Liste &quot;jarsToSkip&quot; in &quot;catalina.properties&quot; wurde aktualisiert, um den Verweis auf eine nicht mehr verwendete JAR-Datei zu entfernen (iOS-Benachrichtigungen).
* Fehlerkorrektur – Es wurde ein Problem behoben, das die Sendungsvorbereitung nach einem Postupgrade blockierte.
* Nach dem Wechsel zum [neuen Sequenz-ID-Mechanismus](https://helpx.adobe.com/de/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence) werden alle Webanwendungen, die die Empfänger-Tabelle aktualisieren, während des Postupgrads erneut veröffentlicht.
* Es wurde eine potenzielle XSS-Schwachstelle in Versandinhalt behoben. (NEO-17987, NEO-26073)

## ![](assets/do-not-localize/orange_2.png) Version 20.2.1 – Build 9178 {#release-20-2-1-build-9178}

_8. Juni 2020_

**Neue Funktionen**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Unterstützung von Emoticons</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>Wenn Sie eine Nachricht in Campaign entwerfen, können Sie nun mit einer entsprechenden Schaltfläche bequem Emoticons in den Nachrichtentext einfügen. Emoticons können auch der Betreffzeile einer E-Mail hinzugefügt werden. Die Liste der verfügbaren Emoticons lässt sich in der Benutzeroberfläche anpassen.</p>
    <p>Weiterführende Informationen zum Hinzufügen von Emoticons finden Sie im <a href="../../delivery/using/defining-the-email-content.md#inserting-emoticons">entsprechenden Handbuch</a>. <a href="../../delivery/using/customizing-emoticon-list.md">In diesem Abschnitt</a> erfahren Sie, wie Sie die Emoticon-Liste anpassen können.</p>
   </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>Azure Synapse FDA-Connector</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>Sie können Ihre Campaign-Instanz jetzt mit Ihrer externen Azure Synapse-Datenbank verbinden. Diese Verbindung wird über ein neues externes Konto verwaltet.</p>
    <p>Azure Synapse ist nur für Hybrid- und On-Premise-Umgebungen verfügbar. Weitere Informationen finden Sie im <a href="../../platform/using/specific-configuration-database.md#configure-access-to-azure-synapse">entsprechenden Handbuch</a>.</p>
   </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>Datenschutzgesetze in Thailand und Brasilien</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>Das thailändische Datenschutzgesetz (PDPA) ist ein neues Datenschutzgesetz, mit dem die Datenschutzanforderungen für Thailand harmonisiert und modernisiert werden. </p>
   <p>Das brasilianische Lei Geral de Proteção de Dados (LGPD) wird Anfang 2021 für alle Firmen in Kraft treten, die in Brasilien personenbezogene Daten sammeln oder verarbeiten.</p>
   <p>Die Vorschriften gelten für Adobe Campaign-Kunden, die Daten über in diesen Ländern wohnhafte Datensubjekte besitzen. Zusätzlich zu den bereits in Campaign verfügbaren Datenschutzoptionen (Einverständnisverwaltung, Einstellungen für die Datenbeibehaltung und Benutzerrollen usw.) werden weitere Funktionen bereitgestellt, mit deren Hilfe PDPA- und LGPD-konformes Verhalten sichergestellt werden kann:</p>
   <ul> 
     <li><p>Recht auf Zugriff und Recht auf Löschung: Hierfür werden die Funktionen genutzt, die für die DSGVO und PPDA hinzugefügt wurden. <a href="https://helpx.adobe.com/de/campaign/kb/acc-privacy.html">Mehr dazu</a></p></li> 
     <li> <p>Beim Erstellen einer Datenschutzanfrage mithilfe der Campaign-Benutzeroberfläche oder API können Sie nun den <strong>Regulierungstyp</strong> wählen: PDPA, LGPD, DSGVO oder CCPA. <a href="https://helpx.adobe.com/de/campaign/kb/acc-privacy.html#ManagingPrivacyRequests">Mehr dazu</a></p></li>
    </ul>
   </td> 
  </tr> 
 </tbody> 
</table>

**Verbesserungen bei der Sicherheit**

* Mehr Sicherheit bei Trackinglinks in E-Mails wurde standardmäßig für alle Kunden aktiviert. Es gibt eine zusätzliche, erweiterte Sicherheitsfunktion, die Sie aktivieren können, indem Sie sich an die Kundenunterstützung wenden. Weiterführende Informationen zu der Funktion und den Schritten zur Aktivierung für nicht gehostete Kunden finden Sie in der [Prüfliste für Sicherheit und Datenschutz](https://helpx.adobe.com/de/campaign/kb/acc-security.html). (NEO-24232)

* Für zusätzliche Sicherheit wurde der MD5-Hashing-Algorithmus, der zum Generieren von Dateinamen dient, für den öffentlichen Dateiversand durch SHA256 verstärkt. (NEO-17044)

* Für mehr Schutz gegen XSS-Angriffe werden Client-seitige Scripte beim Ausführen einer Mirrorseite deaktiviert. (NEO-17987)

* Fehlerkorrektur – Der technische Workflow zur **Bereinigung von Datenschutzanfragen** kann jetzt Abstimmungsdaten löschen. (NEO-25168, NEO-21004)

* Fehlerkorrektur – Bei der Aktivität **Dateiübertragung** funktioniert jetzt die SFTP-Schlüssel-basierte Authentifizierung bei Debian 9. (NEO-23183)

**Kompatibilitätsverbesserungen**

Die folgenden Systeme werden jetzt von Campaign unterstützt:
* Betriebssysteme: Debian 10
* RDBMS: Oracle 18c und Oracle 19c
* FDA: Azure Synapse Analytics

Weiterführende Informationen finden Sie in der [Campaign-Kompatibilitätsmatrix ](https://helpx.adobe.com/de/campaign/kb/compatibility-matrix.html).

**Verbesserungen**

* Transaktionsnachrichten wurden optimiert, um ein besseres Benutzererlebnis zu bieten. Sie können die Publikation einer Transaktionsnachrichten-Vorlage jetzt rückgängig machen, womit sie aus den Ausführungsinstanzen gelöscht wird. [Mehr dazu](../../message-center/using/template-unpublication.md).

* Es gibt neue Optionen zum Festlegen von Einschränkungen beim Senden von E-Mails, die Bilder oder Anhänge enthalten. Damit lassen sich Leistungsprobleme verhindern, was besonders bei Transaktionsnachrichten nützlich ist. [Mehr dazu](../../installation/using/configuring-campaign-options.md#delivery)

* Mit der neuen Option **Versandteile in der Datenbank vorbereiten** kann die Versandvorbereitung direkt in der Datenbank vorgenommen werden, was die Analyse erheblich beschleunigen kann. Diese Option steht nur bei bestimmten Konfigurationen zur Verfügung. [Mehr dazu](../../delivery/using/steps-validating-the-delivery.md#improving-delivery-analysis). (NEO-23886)

* Die Leistung der [CRM Connector-Aktivität](../../workflow/using/crm-connector.md) für Microsoft Dynamics wurde verbessert. (NEO-13303, NEO-12710)

* Die Version mit gemeinsamem Speicher wurde verbessert.

   >[!WARNING]
   >
   >Die Optimierung setzt einen zusätzlichen Schritt nach dem Upgrade voraus. Lesen Sie diesbezüglich den Abschnitt **Technische Entwicklungen** weiter unten.

* Der Bereinigungs-Workflow wurde verbessert. Verwaiste Arbeitstabellen aller gelöschten Workflows werden vom Bereinigungs-Workflow jetzt auch automatisch gelöscht. [Mehr dazu](../../production/using/database-cleanup-workflow.md#cleanup-of-workflow-instances).

* Zertifikate für iOS-Mobile Apps mit dem iOS-HTTP2-Connector werden jetzt vor dem Senden von Push-Benachrichtigungen validiert, was verhindert, dass Sendungen aufgrund abgelaufener Zertifikate fehlschlagen.

* Die Verwaltung von HTTP-Proxy-Verbindungen wurde verbessert. [Mehr dazu](../../installation/using/configuring-campaign-server.md#proxy-connection-configuration).

**Sonstige Änderungen**

* Alte SMS-Connectoren werden jetzt nicht mehr unterstützt. Weiterführende Informationen finden Sie auf der [Seite zu eingestellten Funktionen](../../rn/using/deprecated-features.md).

* Sie können Ihr eigenes Litmus-Konto nicht mehr zur Bereitstellung und Verwendung von Inbox Rendering in Adobe Campaign nutzen. [Mehr dazu](../../delivery/using/inbox-rendering.md).

* Zur leichteren Unterscheidung von Ansichten und Ordnern wurde die Farbe der Ansichtnamen von dunkelblau in dunkeltürkis geändert. [Mehr dazu](../../platform/using/access-management.md#about-views)

* Campaign Classic kann nun mit Microsoft Dynamics CRM-Konten verbunden werden, die in Großbritannien, Indien und Kanada gehostet werden. Dies gilt für die Bereitstellungstypen &quot;Office 365&quot; und &quot;On-Premise&quot; (Dynamics 2015).

* Campaign führt nun eine TLS-Verifizierung durch, um zu prüfen, ob der Hostname des Servers mit dem Hostnamen im angegebenen Zertifikat übereinstimmt.

* Die Tabelle mit Versand- und Trackingstatistiken zeigt für den SMS-Kanal jetzt einen Eintrag pro Versand anstelle eines Eintrags pro Versandempfänger an.

* Es wurde eine Fehlermeldung in der Protokolldatei hinzugefügt, die Benutzer warnt, wenn die heruntergeladene Datei größer als der verfügbare Speicherplatz ist.

* Folgende Funktionen sind jetzt beim Snowflake-Connector verfügbar: MonthsAgo, DaysAgoInt, ToDateTime, YearsAgo.

**Technische Entwicklungen**

Dieser neue Build aktualisiert den gemeinsamen Speicher und erfordert zusätzliche Schritte bei der Durchführung des Upgrades. Als Campaign-Administrator müssen Sie Speichersegmente entfernen. Diese Schritte sind obligatorisch, da alte Segmente das Starten von &quot;nlserver/nlsrvmod&quot; verhindern.

Unter Windows ist ein Neustart des Systems erforderlich.

Unter Debian/CentOs ist eine Löschung des gemeinsamen Speichers erforderlich. Im Folgenden werden die Schritte beschrieben:

Vor dem Upgrade müssen Sie folgende Schritte ausführen:

1. Beenden Sie den Dienst &quot;apache2&quot; (&quot;http2&quot; unter CentOS), sollte er ausgeführt werden.
1. Beenden Sie den Dienst &quot;nlserver&quot; (&quot;nlserver6&quot; bei älteren Builds), sollte er ausgeführt werden.

Nach dem Upgrade:

1. Entfernen Sie den gemeinsamen Speicher mit dem Befehl **ipcrm**, wenn die Version älter als die aktuelle Version ist.
1. Starten Sie den nlserver-Dienst, wenn er zuvor ausgeführt wurde.
1. Starten Sie den apache2-Dienst, wenn er zuvor ausgeführt wurde.

Hier sind die Befehlszeilen für Debian:

```
/etc/init.d/nlserver* stop
/etc/init.d/apache2 stop

for i in `ipcs -s | awk '/www-data/
{print $2}'`; do (ipcrm -s $i); done

for i in `ipcs -m | awk '/www-data/ {print $2}
'`; do (ipcrm shm $i); done

for i in `ipcs -m | awk '/neolane/
{print $2}'`; do (ipcrm shm $i); done

for i in `ipcs -s | awk '/neolane/ {print $2}
'`; do (ipcrm -s $i); done

/etc/init.d/apache2 restart
/etc/init.d/nlserver* start
```

Ein Beispiel für Linux ist auf dieser [Seite](../../configuration/using/additional-parameters.md#redirection-server-configuration) verfügbar.

**Korrekturen**

* Fehlerkorrektur – Es wurde ein geringfügiger Regressionsfehler in den Bereinigungs-Workflow-Logs behoben.
* Fehlerkorrektur – In der Workflow-Aktivität **Laden (SOAP)** tritt beim Analysieren von WSDL-Dateien jetzt kein Fehler mehr auf.
* Fehlerkorrektur – Beim Upgraden zahlreicher Workflows mit einer **Umfrage**-Aktivität zur effizienten Verarbeitung einer großen Zahl von Workflows tritt jetzt kein Fehler mehr auf.
* Fehlerkorrektur – Bei der Verarbeitung von InMail-Nachrichten aus dem Enhanced MTA tritt jetzt kein Verbindungsproblem mehr auf. (NEO-20380)
* Fehlerkorrektur – Die Prozentwerte für Klickposition werden jetzt richtig angezeigt, wenn Bilder in HTML mit einer Breite von 100 % angezeigt werden. (NEO-23203)
* Fehlerkorrektur – Der bedingte Inhalt eines Versands im Bericht &quot;Klickposition&quot; wird jetzt vollständig angezeigt. (NEO-18729)
* Fehlerkorrektur – Der Schritt für die Zielgruppenvalidierung beim Wiederaufnehmen eines Workflows zum Senden eines wiederkehrenden Versands wird jetzt nicht mehr übersprungen. (NEO-18166)
* Fehlerkorrektur – Mit der Schaltfläche **Nachrichtenvorbereitung neu starten** kann der Versand nach Beheben eines Fehlers im Workflow jetzt wieder aufgenommen werden. (NEO-13488)
* Fehlerkorrektur – Sendungen im Mid-Sourcing-Modus schlagen jetzt in der Anfangsphase nicht mehr fehl, wenn die Zielgruppe Empfänger mit japanischen E-Mail-Formaten enthält. (NEO-23846)
* Fehlerkorrektur – Die Zeitzonenkonvertierung beim Snowflake-Connector funktioniert jetzt fehlerfrei (NEO-20105)
* Fehlerkorrektur – Es gibt kein Problem mehr mit externen Konten, die FTP über SSL verwenden. (NEO-20498)
* Fehlerkorrektur – Die Anzeige von Bildern in Line-Sendungen wird jetzt nicht mehr verhindert. (NEO-23207)
* Fehlerkorrektur – Das Publizieren eines Angebots führt jetzt nicht mehr zu einem Fehler. (NEO-23312)
* Fehlerkorrektur – Bei Push-Benachrichtigungen funktionieren Testverbindungen in Mobile Apps jetzt nicht mehr, wenn das Zertifikat bereits abgelaufen ist. (NEO-22991)
* Fehlerkorrektur – Bei Push-Benachrichtigungen, die mit hoher Häufigkeit gesendet werden, tritt jetzt kein Problem mehr auf. (NEO-20516)
* Fehlerkorrektur – Tracking-Daten enthalten jetzt auch keine Duplikate, wenn die Trackinglogs keine enthalten. (NEO-20040)
* Fehlerkorrektur – Transaktions-E-Mails werden jetzt nicht mehr doppelt gesendet, nachdem ein Kommunikationsfehler mit dem Trackingserver behoben wurde. (NEO-23640)
* Fehlerkorrektur – Der Codierungs-Parameterwert wird bei Weiterleitung von einer Tracking-URL nicht mehr gelöscht (Auswirkung auf japanische Zeichen). (NEO-25637)
* Fehlerkorrektur – Eine Abfrage funktioniert jetzt beim Vergleich von Fließkommazahlen. (NEO-23243)
* Fehlerkorrektur – Die Anzeige des Spalteninhalts von **Geändert von** ist jetzt nach dem Neustart eines Workflows möglich. (NEO-23035)
* Fehlerkorrektur – Der technische Workflow zum Tracking beim Herunterladen von Protokollen aus einem zweiten Container schlägt jetzt nicht mehr fehl. (NEO-23159)
* Fehlerkorrektur – Workflows schlagen beim Ausführen einer Aktivität vom Typ **Anreicherung** jetzt nicht mehr fehl. (NEO-17338)
* Zum Feld **Beizubehaltende Dubletten** in der Workflow-Aktivität **Deduplizierung** wurde eine Prüfung hinzugefügt, um die Eingabe von Null- oder Negativwerten zu verhindern.
* Der **Planungsassistent** wurde aus den wiederkehrenden Kampagnen entfernt, um zu verhindern, dass Stunden und Minuten erwähnt werden. Es werden nur Datumswerte berücksichtigt.
* Fehlerkorrektur – Es wurde ein Problem mit zusätzlichen Speicherfeldern behoben, das beim Erstellen von Sendungen mithilfe der Option **Wird durch ein Script erstellt** in der Workflow-Aktivität **Script** auftrat. (NEO-20609)
* Fehlerkorrektur – Geister-Workflows werden jetzt im Rahmen der Aufgaben zur Datenbankbereinigung gelöscht.
* Fehlerkorrektur – Der technische Workflow **Abrechnung (aktive Profile)** schläft jetzt nicht mehr fehl. (NEO-19777)
* Fehlerkorrektur – Es wurde ein Regressionsfehler bei Verwendung der ACS Connector-Funktion behoben, der die Verbindung zu einer Campaign Standard-Instanz verhinderte (fehlerhafte Verwaltung der FOH-/FOH2-Verbindung). (NEO-23433)
* Fehlerkorrektur – Das Erstellen einer Schemaerweiterung für einen Primärschlüssel mit mehreren Spalten in einer Hadoop-Tabelle wird jetzt nicht mehr verhindert. (NEO-17390)
* Fehlerkorrektur – Es wurde ein Fehler in der Aktivität **Laden (SOAP)** behoben, der das Laden von WSDL-Dateien über eine URL verhindern konnte. (NEO-16924)
* Fehlerkorrektur – Über die Konsole kann jetzt ein **unbedingter Stopp** ausgeführt werden, wenn mehrere aktive Workflow-Server einen Lastenausgleich durchführen. (NEO-19556)
* Fehlerkorrektur – Jetzt tritt kein Regressionsfehler mehr auf, der zum Absturz des Bereinigungs-Workflows führt.
* Beim Veröffentlichen einer Vorlage in einer Ausführungsinstanz tritt jetzt kein Fehler mehr auf.
* Fehlerkorrektur – Die Ausführung des technischen Workflows &quot;collectPrivacyRequests&quot; wird jetzt nicht mehr verhindert. (NEO-20513, NEO-25169)
* Fehlerkorrektur – Wenn nach dem Upgrade auf Build 9080 versucht wird, eine Verbindung mit Audience Manager herzustellen, treten jetzt keine Fehler mehr auf. (NEO-20511, NEO-25167)
* Fehlerkorrektur – Beim Exportieren von Berichten im PDF- oder XLS-Format treten jetzt keine Fehler mehr auf. (NEO-20982, NEO-23493, NEO-23348)
* Fehlerkorrektur – Ein Versand in der Versandliste wird nach dem Senden jetzt nicht mehr zweimal angezeigt.
* Fehlerkorrektur – Bei der Versandvorbereitung tritt jetzt kein Fehler mehr auf, wenn die Routing-Konfiguration so eingerichtet ist, dass der Versand über Mid-Sourcing erfolgt.
* Fehlerkorrektur – Beim Klicken auf den Link einer Web-Anwendung in einer Line-Nachricht wird jetzt keine Fehlermeldung mehr angezeigt.
* Fehlerkorrektur – Der Verlauf der Aktivität **Inkrementelle Abfrage** nach Ausführung des Bereinigungs-Workflows wird jetzt nicht mehr gelöscht.
* Fehlerkorrektur – Beim Erstellen eines externen Mid-Sourcing-Kontos tritt jetzt kein Fehler mehr auf, wenn die Option &quot;NmsMidSourcing_LastBroadLog_&lt;InternalName>&quot; fehlt..
* Fehlerkorrektur – Es wurde ein Regressionsfehler bei der Datenbankverbindung behoben, der dazu führte, dass der Webserver aufgrund eines Problems mit der Datenbankkodierung ständig neu gestartet wurde. Dies konnte zu einem übermäßigen Verbrauch führen. (NEO-23264)
