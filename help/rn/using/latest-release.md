---
title: Neueste Version
description: Neueste Version
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
source-git-commit: cb55216e75559e1ce7eefa24d2302fe2c2224d40
workflow-type: tm+mt
source-wordcount: '1739'
ht-degree: 15%

---


# Neueste Version{#latest-release}

[Build-Aktualisierung](https://helpx.adobe.com/de/campaign/kb/acc-build-upgrade.html) | [Control Panel-Versionen](https://docs.adobe.com/content/help/de-DE/control-panel/using/release-notes.html) | [Aktualisierungen der Dokumentation](../../rn/using/documentation-updates.md) | [Frühere Versionshinweise](../../rn/using/release--20-1.md) | [Eingestellte Funktionen](../../rn/using/deprecated-features.md)

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

## ![](assets/do-not-localize/blue_2.png) Version 20.2.1 – Build 9178 {#release-20-2-1-build-9178}

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
   <td> <p>Wenn Sie eine Nachricht in Kampagne entwerfen, können Sie nun einfach Emoticons in den Nachrichtentext einfügen, indem Sie eine entsprechende Schaltfläche verwenden. Sie können auch in der Betreffzeile der E-Mail hinzugefügt werden. Sie können die Liste der verfügbaren Emoticons in der Benutzeroberfläche anpassen.</p>
    <p>Weitere Informationen zum Hinzufügen von Emoticons finden Sie in der <a href="../../delivery/using/defining-the-email-content.md#inserting-emoticons">ausführlichen Dokumentation</a>. Erfahren Sie, wie Sie die Emoticon-Liste <a href="../../delivery/using/customizing-emoticon-list.md">in diesem Abschnitt</a>anpassen.</p>
   </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>Azurblase Synapse FDA Connector</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>Sie können Ihre Kampagne-Instanz jetzt mit Ihrer Azurblase Synapse-externen Datenbank verbinden. Diese Verbindung wird über ein neues Externe Konto verwaltet.</p>
    <p>Azurblauer Synapse ist nur für Hybrid- und On-Premise-Umgebung erhältlich. Weitere Informationen finden Sie im <a href="../../platform/using/specific-configuration-database.md#configure-access-to-azure-synapse">entsprechenden Handbuch</a>.</p>
   </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>Thailand und Brasilien - Datenschutzgesetze</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>Der thailändische Datenschutzgesetz (PDPA) ist das neue Datenschutzgesetz, mit dem die Datenschutzanforderungen für Thailand harmonisiert und modernisiert werden. </p>
   <p>Brasiliens Lei Geral de Proteção de Dados (LGPD) wird ab dem 16. August für alle Firmen, die personenbezogene Daten in Brasilien sammeln oder verarbeiten, wirksam sein.</p>
   <p>Diese Vorschriften gelten für Adobe Campaign-Kunden, die Daten für in diesen Ländern wohnhafte Datensubjekte besitzen. Zusätzlich zu den bereits in der Kampagne verfügbaren Datenschutzfunktionen (einschließlich Zustimmungsverwaltung, Einstellungen zur Datenspeicherung und Benutzerrollen) bieten wir Ihnen hier zusätzliche Funktionen an, um Ihre Bereitschaft für PDPA und LGPD zu erleichtern:</p>
   <ul> 
     <li><p>Recht auf Zugriff und Recht auf Löschung: Hierfür werden die Funktionen genutzt, die für die DSGVO und PPDA hinzugefügt wurden – <a href="https://helpx.adobe.com/de/campaign/kb/acc-privacy.html">mehr dazu</a></p></li> 
     <li> <p>Beim Erstellen einer Datenschutzanforderung mithilfe der Benutzeroberfläche oder API wählen Sie jetzt den <strong>Regeltyp</strong> aus: PDPA, LGPD, GDPR, CCPA. <a href="https://helpx.adobe.com/campaign/kb/acc-privacy.html#ManagingPrivacyRequests">mehr dazu</a></p></li>
    </ul>
   </td> 
  </tr> 
 </tbody> 
</table>

**Verbesserungen bei der Sicherheit**

* Verbesserte Sicherheit bei der Verfolgung von Links in E-Mails ist standardmäßig für alle Kunden aktiviert. Es gibt eine zusätzliche, erweiterte Sicherheitsfunktion, die Sie aktivieren können, indem Sie sich an die Kundenunterstützung wenden. Weiterführende Informationen zu der Funktion und den Schritten zur Aktivierung für nicht gehostete Kunden finden Sie in der [Prüfliste für Sicherheit und Datenschutz](https://helpx.adobe.com/de/campaign/kb/acc-security.html). (NEO-24232)

* Um die Sicherheit zu optimieren, wurde der MD5-Hashing-Algorithmus, der zum Generieren von Dateinamen verwendet wurde, mit sha256 für das Hochladen öffentlicher Dateien verstärkt. (NEO-17044)

* Um die Sicherheit gegen XSS-Angriffe zu erhöhen, werden clientseitige Skripte beim Ausführen einer Mirrorseite deaktiviert. (NEO-17987)

* Es wurde ein Fehler behoben, der verhinderte, dass der technische Arbeitsablauf zur Bereinigung von **Datenschutzanfragen** die Abgleichdaten löscht. (NEO-25168, NEO-21004)

* Fehlerkorrektur – Bei der Aktivität **Dateiübertragung** funktioniert jetzt die SFTP-Schlüssel-basierte Authentifizierung bei Debian 9. (NEO-23183)

**Kompatibilitätsverbesserungen**

Die folgenden Systeme werden jetzt mit Kampagne unterstützt:
* Betriebssysteme: Debian 10
* RDBMS: Oracle 18c und Oracle 19c
* FDA: Azurblase Synapse Analytics

Weitere Informationen finden Sie in der Kompatibilitätsmatrix für [Kampagnen](https://helpx.adobe.com/de/campaign/kb/compatibility-matrix.html).

**Verbesserungen**

* Die Transaktionsnachrichten wurden verbessert, um die Benutzererfahrung zu verbessern. Sie können jetzt die Veröffentlichung einer Transaktionsnachrichtenvorlage rückgängig machen, wodurch sie aus den Ausführungsinstanzen gelöscht wird. [Mehr dazu](../../message-center/using/template-unpublication.md).

* Es stehen neue Optionen zur Verfügung, um Einschränkungen beim Senden von E-Mails mit Bildern oder Anlagen festzulegen. Diese Garantien können Leistungsprobleme vermeiden, die besonders bei transaktionalen Nachrichten nützlich sind. [mehr dazu](../../installation/using/configuring-campaign-options.md#delivery)

* Mit der neuen Option **Vorbereiten der Datenbankteile** können Versand direkt in der Datenbank vorbereitet werden, was die Analyse erheblich beschleunigen kann. Diese Option steht nur für bestimmte Konfigurationen zur Verfügung. [Mehr dazu](../../delivery/using/steps-validating-the-delivery.md#improving-delivery-analysis). (NEO-23886)

* Die Performance der [CRM Connector Aktivität](../../workflow/using/crm-connector.md) für Microsoft Dynamics wurde verbessert. (NEO-13303, NEO-12710)

* Die Version des gemeinsamen Speichers wurde erhöht.

   >[!WARNING]
   >
   >Diese Verbesserung erfordert einen zusätzlichen Schritt nach der Aktualisierung. Lesen Sie den Abschnitt **Technische Entwicklungen** weiter unten.

* Der Bereinigungsarbeitsablauf wurde verbessert. Die entpackten Arbeitstische aller gelöschten Workflows werden jetzt auch automatisch vom Bereinigungsarbeitsablauf gelöscht. [Mehr dazu](../../production/using/database-cleanup-workflow.md#cleanup-of-workflow-instances).

* Zertifikate für iOS-Mobilanwendungen mit dem iOS-HTTP2-Connector werden jetzt vor dem Senden von Push-Benachrichtigungen validiert, wodurch verhindert wird, dass Versand aufgrund abgelaufener Zertifikate fehlschlagen.

* Die Verwaltung von HTTP-Proxyverbindungen wurde verbessert. [Mehr dazu](../../installation/using/configuring-campaign-server.md#proxy-connection-configuration).

**Sonstige Änderungen**

* Legacy-SMS-Connectors werden jetzt nicht mehr unterstützt. Weitere Informationen finden Sie auf der Seite zu [veralteten Funktionen](../../rn/using/deprecated-features.md).

* Sie können Ihr eigenes Litmus-Konto nicht mehr für die Bereitstellung und Verwendung des Inbox-Renderings in Adobe Campaign verwenden. [Mehr dazu](../../delivery/using/inbox-rendering.md).

* Um Ansichten besser von Ordnern zu unterscheiden, wurde die Farbe der Ansichten von dunkelblau in dunkelblau geändert. [mehr dazu](../../platform/using/access-management.md#about-views)

* Campaign Classic kann nun mit Microsoft Dynamics CRM-Konten in Großbritannien, Indien und Kanada verbunden werden. Dies gilt für die Bereitstellungstypen Office 365 und On Premise (Dynamics 2015).

* Kampagne führt nun eine TLS-Überprüfung durch, um zu überprüfen, ob der Hostname des Servers mit dem Hostnamen im bereitgestellten Zertifikat übereinstimmt.

* Die Tabelle mit den Statistiken zu Versand und Verfolgung zeigt jetzt einen Eintrag pro Versand für den SMS-Kanal anstelle eines Eintrags pro Versand-Empfänger an.

* Es wurde eine Fehlermeldung in der Protokolldatei hinzugefügt, die Benutzer warnt, wenn die heruntergeladene Datei größer als der Speicherplatz ist.

* Die folgenden Funktionen sind jetzt für den Snowflake-Connector verfügbar: Vor Monaten, TageAgoInt, ToDateTime, Jahre zuvor.

**Technische Entwicklungen**

Dieser neue Build aktualisiert den gemeinsamen Speicher und erfordert zusätzliche Schritte, um die Aktualisierung durchzuführen. Als Kampagne-Administrator müssen Sie Speichersegmente entfernen. Diese Schritte sind obligatorisch, da alte Segmente verhindern, dass nlserver/nlsrvmod gestartet wird.

Unter Windows ist ein Neustart des Systems erforderlich.

Bei Debian/CentOs ist eine Löschung des gemeinsamen Speichers erforderlich. Im Folgenden werden die Schritte beschrieben:

Vor der Aktualisierung müssen Sie die folgenden Schritte ausführen:

1. Beenden Sie den Dienst apache2 (http2 auf CentOS), wenn er ausgeführt wird.
1. Beenden Sie den nlserver-Dienst (nlserver6 für ältere Builds), wenn er ausgeführt wird.

Nach der Aktualisierung:

1. Entfernen Sie den gemeinsamen Speicher mit dem **Befehl ipcrm** , wenn die Version älter als die aktuelle Version ist.
1. Beginn des nlserver-Dienstes, wenn er ausgeführt wurde.
1. Beginn des Apache2-Dienstes, wenn er ausgeführt wurde.

Hier sind die Befehlszeilen für Debian:

```
/etc/init.d/nlserver* stop
/etc/init.d/apache2 stop
```

```
for i in `ipcs -s | awk '/www-data/
{print $2}'`; do (ipcrm -s $i); done
```

```
for i in `ipcs -m | awk '/www-data/ {print $2}
'`; do (ipcrm shm $i); done
```

```
for i in `ipcs -m | awk '/neolane/
{print $2}'`; do (ipcrm shm $i); done
```

```
for i in `ipcs -s | awk '/neolane/ {print $2}
'`; do (ipcrm -s $i); done
```

```
/etc/init.d/apache2 restart
/etc/init.d/nlserver* start
```

Ein Beispiel für Linux ist auf dieser [Seite](../../configuration/using/additional-parameters.md#redirection-server-configuration)verfügbar.

**Patches**

* Fehlerkorrektur – Es wurde ein geringfügiger Regressionsfehler in den Bereinigungs-Workflow-Logs behoben.
* Es wurde ein Problem in der Aktivität **Laden (SOAP)** des Workflows beim Analysieren von WSDL-Dateien behoben.
* Es wurde ein Fehler behoben, der beim Aktualisieren zahlreicher Workflows mit einer **Umfrage** -Aktivität zur effizienten Verarbeitung einer hohen Anzahl von Workflows auftrat.
* Es wurde ein zeitweilig auftretendes Verbindungsproblem bei der Verarbeitung von InMail-Nachrichten aus dem erweiterten MTA behoben. (NEO-20380)
* Es wurde ein Fehler behoben, der verhinderte, dass die Prozentwerte für Hotclick korrekt angezeigt wurden, wenn Bilder mit einer Breite von 100 % im HTML-Code angezeigt wurden. (NEO-23203)
* Es wurde ein Fehler behoben, der verhinderte, dass der bedingte Inhalt des Versands vollständig im Bericht &quot;Hotclicks&quot;angezeigt wurde. (NEO-18729)
* Es wurde ein Problem behoben, bei dem der Genehmigungsvorgang für die Zielgruppe beim Wiederaufnehmen eines Workflows zum Senden eines wiederkehrenden Versands übersprungen wurde. (NEO-18166)
* Es wurde ein Fehler behoben, der dazu führte, dass die Schaltfläche zur Vorbereitung **der Meldung** neu starten den Versand nach Beheben eines Fehlers im Workflow nicht wieder aufnehmen konnte. (NEO-13488)
* Es wurde ein Fehler behoben, der dazu führte, dass Versand im Mid-Sourcing-Modus während der Aufstiegsphase, in der die Zielgruppe Empfänger mit japanischen E-Mail-Formaten enthielt, fehlschlugen. (NEO-23846)
* Korrektur des Zeitzonenkonvertierungsproblems mit dem Snowflake Connector (NEO-20105)
* Es gibt kein Problem mehr mit externen Konten, die FTP über SSL verwenden. (NEO-20498)
* Es wurde ein Problem behoben, das die Anzeige von Bildern in Line-Versänden verhinderte. (NEO-23207)
* Es wurde ein Fehler behoben, der beim Veröffentlichen eines Angebots zu einem Fehler führte. (NEO-23312)
* Es wurde ein Problem mit Push-Benachrichtigungen behoben, durch das Testverbindungen in mobilen Anwendungen funktionierten, selbst wenn das Zertifikat abgelaufen war. (NEO-22991)
* Es wurde ein Problem behoben, das sich auf Push-Benachrichtigungen auswirken konnte, wenn diese mit hoher Frequenz gesendet wurden. (NEO-20516)
* Es wurde ein Fehler behoben, der dazu führte, dass die Verfolgungsdaten Duplikat enthielten, obwohl die Trackinglogs dies nicht taten. (NEO-20040)
* Es wurde ein Fehler behoben, der dazu führte, dass transaktionsbedingte E-Mails an Duplikate gesendet wurden, nachdem ein Kommunikationsfehler beim Tracking-Server behoben wurde. (NEO-23640)
* Es wurde ein Problem behoben, durch das der Wert des Kodierungsparameters bei der Umleitung von einer Tracking-URL gelöscht wurde. (NEO-25637)
* Es wurde ein Fehler behoben, der dazu führte, dass eine Abfrage beim Vergleich von Fließkommazahlen nicht funktionierte. (NEO-23243)
* Es wurde ein Problem behoben, das die Anzeige des Inhalts &quot; **Geändert durch** Spalte&quot;nach dem Neustart des Workflows verhinderte. (NEO-23035)
* Es wurde ein Fehler behoben, der dazu führte, dass der technische Arbeitsablauf zur Verfolgung beim Herunterladen von Protokollen von einem zweiten Container fehlschlug. (NEO-23159)
* Es wurde ein Fehler behoben, der dazu führte, dass Workflows beim Ausführen einer **Anreicherung** -Aktivität fehlschlugen. (NEO-17338)
* Zu den **Dubletten wurde eine Prüfung hinzugefügt, um das Feld in der Aktivität für den** Deduplizierung-Duplikate **** -Workflow zu belassen, um die Eingabe von Null- oder Negativwerten zu verhindern.
* Der Assistent **für die** Planung wurde aus den wiederkehrenden Kampagnen entfernt, um zu vermeiden, dass Stunden und Minuten erwähnt werden. Es werden nur Daten berücksichtigt.
* Es wurde ein Problem mit zusätzlichen Datenspeicherung behoben, das beim Erstellen von Versänden mithilfe der Skriptoption **Berechnet** in der Aktivität für den **Skriptarbeitsablauf** auftrat. (NEO-20609)
* Es wurde ein Fehler behoben, der verhinderte, dass Ghost Workflows in den Aufgaben zur Datenbankbereinigung gelöscht werden konnte.
* Es wurde ein Fehler behoben, der dazu führte, dass der Arbeitsablauf für die **Rechnungsstellung (aktive Profil)** fehlschlug. (NEO-19777)
* Es wurde ein Problem beim Testen der Verbindung des acsDefaultAccount-Externen Kontos behoben. (NEO-23433)
* Es wurde ein Fehler behoben, der verhinderte, dass Sie eine Schema-Erweiterung für einen Primärschlüssel mit mehreren Spalten mit einer Hadoop-Tabelle erstellen konnten. (NEO-17390)
* Es wurde ein Problem in der Aktivität **Laden (SOAP)** behoben, das das Laden von WSDL-Dateien aus einer URL verhindern konnte. (NEO-16924)
* Es wurde ein Fehler behoben, der verhinderte, dass Sie einen **bedingungslosen Stopp** über die Konsole durchführen konnten, wenn mehrere aktive Workflow-Server Lastenausgleich durchführten. (NEO-19556)
* Fehlerkorrektur – Es wurde ein Regressionsfehler behoben, der zum Absturz des Bereinigungs-Workflows führte.
* Es wurde ein Problem behoben, das beim Veröffentlichen einer Vorlage auf einer Ausführungsinstanz auftreten konnte.
* Es wurde ein Problem behoben, das die Ausführung des technischen Arbeitsablaufs &quot;collectionPrivacyRequests&quot;verhindern konnte. (NEO-20513, NEO-25169)
* Es wurden Probleme behoben, die auftreten konnten, wenn nach dem Hochladen auf Build 9080 versucht wurde, eine Verbindung mit Audience Manager herzustellen. (NEO-20511, NEO-25167)
* Es wurden Probleme behoben, die beim Exportieren von Berichten im PDF- oder XLS-Format auftraten. (NEO-20982, NEO-23493, NEO-23348)
* Es wurde ein Problem behoben, durch das ein Versand in der Liste Versand zweimal angezeigt werden konnte, nachdem er gesendet wurde.
* Es wurde ein Problem bei der Vorbereitung des Versands behoben, das auftrat, wenn die Routing-Konfiguration so eingestellt war, dass der Versand über Mid-Sourcing gesendet wurde.
* Es wurde ein Fehler behoben, der beim Klicken auf einen Webanwendungslink in einer Zeilenmeldung eine Fehlermeldung anzeigen konnte.
* Es wurde ein Problem behoben, durch das Microsoft Dynamics CRM nicht alle Entitäten abrufen konnte. (NEO-24528)
* Es wurde ein Problem behoben, durch das der Verlauf der **Inkrementelle Abfrage** -Aktivität nach der Ausführung des Bereinigungsarbeitsablaufs gelöscht wurde.
* Es wurde ein Fehler behoben, der beim Erstellen eines Mid-Sourcing-Externen Kontos auftrat, bei dem die Option NmsMidSourcing_LastBroadLog_&lt;InternalName> fehlte
