---
product: campaign
title: Aktuelle Version
description: Aktuelle Versionshinweise von Campaign Classic v7
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Overview
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '2949'
ht-degree: 100%

---

# Aktuelle Version{#latest-release}



Auf dieser Seite werden neue Funktionen, Verbesserungen und Fehlerbehebungen der **aktuellen Version Campaign Classic v7** aufgelistet. Jeder neue Build weist einen Status auf, der durch eine bestimmte Farbe dargestellt wird. Sie erfahren mehr über den Build-Status von Campaign Classic v7 auf [dieser Seite](rn-overview.md).

## ![](assets/do-not-localize/green_2.png) Version 7.3.3 – Build 9359 {#release-7-3-3}

>[!CAUTION]
>
>Die Aktualisierung der Client-Konsole ist obligatorisch. Auf dieser [Seite](../../installation/using/installing-the-client-console.md) erfahren Sie, wie Sie Ihre Client-Konsole aktualisieren.

_20. März 2023_

**Sicherheitsverbesserung**

* Um die Sicherheit zu verbessern, wurde Tomcat von Version 8.5.81 auf 8.5.85 aktualisiert. (NEO-56936)

**Verbesserungen**

* Der Abrechnungs-Workflow wurde verbessert, um die Leistung zu optimieren. (NEO-47658)
* Der Tracking-Workflow wurde verbessert, um die Leistung bei hoher Versandgröße zu optimieren. (NEO-45064)
* Die Tracking-Verwaltung wurde verbessert, um mögliche Probleme mit dynamischen Parametern in URLs zu beheben. Die Tracking-Verwaltung V3 verarbeitet jetzt URLs vom Typ AJAX (mit Parametern nach „#“) und verhindert, dass Drittanbieterprogramme Tracking-URLs ändern. Um diese Änderung anzuwenden, müssen Sie sich an Adobe wenden. (NEO-46535)

<!--To apply this change, the marketing, tracking and mid servers need to be updated to 7.3.3. To enable the new tracking management mode, set the `emailLinksVersion` parameter to '3' in the configuration file of the marketing server. (NEO-46535)-->

**Patches**

* Der Versand von Push-Benachrichtigungen für iOS-Testsendungen von der Kontrollinstanz (Transaktionsnachrichten-Kontext) ist jetzt problemlos möglich. (NEO-54713)
* Das Scrollen in der Registerkarte **Bearbeiten** des Digital Content Editor (DCE) ist jetzt problemlos möglich. (NEO-54474)
* Jetzt können zwei Anreicherungsaktivitäten bei der Verknüpfung dieselbe Namenskennung verwenden, ohne dass die zweite Anreicherungsaktivität die Links der ersten verwendet. (NEO-48851)

## ![](assets/do-not-localize/orange_2.png) Version 7.3.2 – Build 9356 {#release-7-3-2}

_21. November 2022_

>[!CAUTION]
>
>Die Aktualisierung der Client-Konsole ist obligatorisch. Auf dieser [Seite](../../installation/using/installing-the-client-console.md) erfahren Sie, wie Sie Ihre Client-Konsole aktualisieren.

**Aktualisierungen zur Kompatibilität**

* Adobe Campaign ist jetzt mit PostgreSQL 14 kompatibel. Weiterführende Informationen befinden sich in dieser [Technote](../../technotes/using/tech-stack-upgrade.md).

* Nach dem Auslaufen von Microsoft Internet Explorer 11 verwendet die HTML-Render-Engine für Dashboards in der Client-Konsole nun Edge Chromium. (NEO-20741)

Weiterführende Informationen finden Sie in der [Campaign-Kompatibilitätsmatrix](../../rn/using/compatibility-matrix.md#RDBMSservers).

**Verbesserungen**

* Der Google BigQuery-Connector unterstützt boolesche Felder jetzt uneingeschränkt. (NEO-49181)
* Sie können jetzt die Gültigkeitsdauer der IMS-Cookies im Abschnitt `Configuration for the redirection service` der Datei “serverConf.xml” konfigurieren. Dies gilt für die folgenden Cookies: `uuid230`, `nllastdelid` und `AMCV_` (NEO-42541)
* Die IP-Adresse kann jetzt in der &quot;/r/test&quot;-Anfrage ausgeblendet werden, indem `showSourceIP` im Umleitungsknoten der Datei &quot;serverConf.xml&quot; auf &quot;false&quot; festgelegt wird. [Weitere Informationen](../../installation/using/the-server-configuration-file.md#redirection-redirection)(NEO-46656)

**Eingestellte Funktionen**

* Social Marketing mit Facebook wird jetzt nicht mehr unterstützt. Sie können die Twitter-Integration verwenden, um in den sozialen Medien zu posten, oder in Zusammenarbeit mit Adobe einen benutzerdefinierten Kanal erstellen.
* ACS-Connector (Prime-Angebot) wird jetzt nicht mehr unterstützt. Sie können die Export-/Importfunktionen von Campaign verwenden, um Daten in beide Produkte einzufügen und sie aus ihnen zu extrahieren.

Weitere Informationen finden Sie auf der Seite [Eingestellte und entfernte Funktionen](deprecated-features.md).

**Sonstige Änderungen**

* Web-Protokolle wurden verbessert: `logonEscalation`-Warnungen werden jetzt nur mehr Benutzenden mit Administratorrechten angezeigt. (NEO-47167)
* Um Fehler zu vermeiden, wird der Workflow zum **Erfassen von Daten für den Heatmap-Service** (collectDataHeatMapService) jetzt standardmäßig angehalten. (NEO-33959)
* Es wurden verschiedene Verbesserungen implementiert, um die CPU-Auslastung für das Kampagnen-Dashboard zu optimieren. (NEO-46417)
* Um Abstürze zu verhindern, wurde die JS-Methode loadLibraryDebug entfernt. (NEO-46968)
* Die verbleibenden Verweise auf die log4j-Bibliothek wurden aus der Campaign-Installation unter Windows entfernt. (NEO-44851)

**Patches**

* Fehlerkorrektur: Die Workflow-Option **Ausgewählte Zeilen zusammenführen** kann jetzt verwendet werden. (NEO-48488)
* Fehlerkorrektur: Der Versandindikator **Erfolg** wird jetzt korrekt aktualisiert, wenn Adobe Campaign Enhanced MTA verwendet wird. (NEO-50462)
* Fehlerkorrektur: Nach dem Zurücksetzen der Inhaltsvalidierung eines E-Mail-Versands kann dieser Inhalt jetzt erneut validiert werden. (NEO-44259)
* Fehlerkorrektur: Die Schaltfläche **Versandvalidierung** wird jetzt angezeigt. (NEO-47547)
* Fehlerkorrektur: Bei umfangreichem HTML-Code in der HTML-Tabelle eines Versands tritt jetzt kein Leistungsproblem mehr auf. (NEO-47440)
* Fehlerkorrektur: Der Status des Versandprotokolls auf der MID-Instanz kann jetzt problemlos aktualisiert werden, wenn die Option `FeatureFlag_GZIP_Compression` aktiviert ist. (NEO-49183)
* Fehlerkorrektur: Mobile-App-Benachrichtigungen von iOS können jetzt von einer Ausführungsinstanz gesendet werden, wenn die Token-basierte Authentifizierung verwendet wird. (NEO-45961)
* Fehlerkorrektur: Der Workflow **Zustellbarkeit** (deliverabilityUpdate) wird nicht mehr blockiert, wenn sehr viele Broadlogs zum Synchronisieren vorhanden sind. (NEO-48287)
* Fehlerkorrektur: Es wurde ein Problem mit einem Ereignistyp behoben, durch das der Workflow **Message Center-Synchronisation** (mcSynch) blockiert wurde.
* Fehlerkorrektur: Beim Hinzufügen des Indikators **Empfänger, die geöffnet haben** (estimatedRecipientOpen) zu den Zusatzdaten einer **Abfrage**-Workflow-Aktivität tritt kein Fehler mehr auf. (NEO-46665)
* Fehlerkorrektur: Der Workflow **Abrechnung** schlägt nicht mehr fehl, wenn Message Center Control- und Execution-Packages auf derselben Instanz installiert werden. (NEO-47674)
* Fehlerkorrektur: Der Workflow **Abrechnung** schlägt nicht mehr fehl, wenn Tabellen vorhanden sind, deren Primärschlüssel als Zeichenfolge statt als Ganzzahl definiert sind. (NEO-46254)
* Fehlerkorrektur: Bei Heatmap-Filtern tritt jetzt kein Fehler mehr auf, wenn der Workflow-Name zu lang ist. (NEO-46301)
* Fehlerkorrektur: Datensätze werden bei Verwendung von &quot;Einfache Verknüpfung mit Kardinalität 0 oder 1&quot; während der Anreicherung nicht mehr gelöscht. Dieses Problem entstand mit Version 7.3.1 im Snowflake-FDA-Connector. (NEO-48737)
* Fehlerkorrektur: Bei Snowflake FFDA tritt bei Verwendung des Sortierparameters in der Workflow-Aktivität **Aufspaltung** jetzt kein Problem mehr auf. (NEO-45899)
* Fehlerkorrektur: Die Konfiguration externer Konten kann jetzt gespeichert werden. Das externe Konto wird jetzt nach dem Verbindungstest automatisch für Connectoren mit Parser-Funktion (Snowflake und Google BigQuery) gespeichert. (NEO-47636)
* Fehlerkorrektur: Ein Zeitdatentyp kann jetzt in die Workflow-Aktivität **Datenaktualisierung** in MSSQL eingefügt werden. (NEO-47763)
* Fehlerkorrektur: Der MTA-Prozess stürzt jetzt nicht mehr ab, wenn die Zeitzone der Engine nicht festgelegt ist (spezifisch für MSSQL). (NEO-46619)
* Fehlerkorrektur: Beim HTML-Dateiimport tritt jetzt kein Fehler mehr auf, wenn Bildknoten (img) URLs mit Personalisierungsfeldern enthalten. (NEO-48396)
* Fehlerkorrektur: Der HTTP-Fehler 500 tritt nicht mehr bei dem Versuch auf, eine Verbindung zu einer Instanz herzustellen, bei der der `limit`-Knoten nicht in der Datei &quot;serverConf.xml&quot; konfiguriert wurde.
* Fehlerkorrektur: Bei Verwendung bestimmter Funktionen wie `to_nclob` mit einer Oracle-Unicode-Datenbank, in der NChar nicht aktiviert ist, tritt der Fehler &quot;Zeichensätze stimmen nicht überein&quot; nicht mehr auf. (NEO-49361)
* Fehlerkorrektur: Jetzt tritt kein Fehler mehr auf, wenn ein Benutzer bzw. eine Benutzerin mit Lesezugriffsrechten für den Ordner &quot;nmsDeliveryMapping&quot; versucht, eine Kampagne oder einen Workflow auszuführen. (NEO-48230)
* Fehlerkorrektur: Die Funktion `JSPContext.sqlExecWithOneParam` funktioniert jetzt. (NEO-50066)
* Fehlerkorrektur: Diverse Weiterleitungsfehler wurden behoben. (NEO-50030)

## ![](assets/do-not-localize/orange_2.png) Version 7.3.1 – Build 9352 {#release-7-3-1}

_1. Juli 2022_

**Neue Funktionen**

<table> 
<thead>
<tr> 
<th> <strong>Zeitkritische Benachrichtigungen</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>In iOS 15 fügte Apple das Konzept der „Dringlichen Mitteilungen“ hinzu, das dem App-Entwickler die Möglichkeit gibt, den Fokusmodus zu umgehen, wenn eine Benachrichtigung als dringlich eingestuft wird und den Benutzer in Echtzeit erreichen muss.</p>
<p>Erfahren Sie in der <a href="../../delivery/using/create-notifications-ios.md">ausführlichen Dokumentation</a>, wie Sie eine vertrauliche Benachrichtigung erstellen.</p>
</td> 
</tr> 
</tbody> 
</table>

**Aktualisierungen zur Kompatibilität**

* Das Adobe Campaign-SDK unterstützt jetzt Android 12 und iOS 15 für Push-Benachrichtigungen.
* Adobe Campaign ist jetzt mit MySQL 8 kompatibel.
* Adobe Campaign ist jetzt mit Windows 11 kompatibel.
* Adobe Campaign ist jetzt mit Debian 11 kompatibel. Weiterführende Informationen befinden sich in dieser [Technote](../../technotes/using/tech-stack-upgrade.md).

Weitere Informationen finden Sie in der [Kompatibilitätsmatrix für Campaign](../../rn/using/compatibility-matrix.md#OperatingSystems).

**Verbesserungen**

* Nach dem Auslaufen von Microsoft Internet Explorer 11 verwendet die HTML-Rendering-Engine für Adobe Services (Anmeldeseite) in der Client-Konsole jetzt Edge Chromium. Beachten Sie, dass Microsoft Internet Explorer 11 weiterhin die HTML-Rendering-Engine für Dashboards in der Client-Konsole ist. Außerdem ist jetzt die Installation von Microsoft Edge Webview 2 Runtime für jede Client-Konsolen-Installation erforderlich (ab Campaign Classic Build-Version 7.3). [Weitere Informationen](../../installation/using/installing-the-client-console.md)
* Die Datenbankverbindungsverwaltung in Adobe Campaign wurde verbessert, um die Stabilität zu optimieren.
* Die Microsoft Exchange Online OAuth 2.0-Authentifizierung für POP3 wird jetzt in Campaign unterstützt. [Mehr dazu](../../installation/using/external-accounts.md#bounce-mails-external-account)
* Fehlerkorrektur – Bei der Verwendung einer Anreicherungs-Workflow-Aktivität mit externen Daten treten jetzt keine Fehler mehr auf. (NEO-38069)
* Der SAP Hana FDA-Connector wurde aktualisiert, um mit der neuesten SAP Hana-Datenbankversion (2.x) zu funktionieren.
* Der Teradata FDA-Connector wurde aktualisiert, um mit der neuesten Teradata-Version (17) zu funktionieren.
* In Version 20.2 wurde für neue Sendungen und Versandvorlagen die Unterstützung der Token-basierten Authentifizierung für iOS-Sendungen eingeführt. In 7.2 wurde dem Postugrade ein Patch hinzugefügt, um die Token-basierte Authentication-Unterstützung auf maximal 10.000 zuvor erstellte Sendungen und Versandvorlagen anzuwenden. In Version 7.3 wurde der Patch verbessert und die Begrenzung entfernt.

**Patches**

* Fehlerkorrektur – Die Größe der IMS-Anmeldeseite kann nun im Gegensatz zum vorherigen Build geändert werden. (NEO-30085)
* Fehlerkorrektur – Bei der Installation des Content-Manager-Packages auf einer vorhandenen Instanz tritt nun kein Fehler mehr auf. (NEO-32349)
* Fehlerkorrektur – Im Menü **Kampagnen** wird nicht mehr ständig die Meldung &quot;Vorgang läuft&quot; angezeigt. (NEO-44904)
* Fehlerkorrektur – Bei aktiviertem Adobe Analytics werden die BID (Broadlog-ID) und CID (Kampagnen-ID) nun nicht mehr aus der URL entfernt, wenn eine E-Mail mit einer URL gesendet wird, ohne den Versand zu speichern. (NEO-38678)
* Fehlerkorrektur – Beim Hochladen eines Bildes im Ordner &quot;Öffentliche Ressourcen&quot; in einer Instanz mit Message Center-spezifischer Konfiguration tritt jetzt kein Fehler mehr auf. Es wird nicht mehr die Fehlermeldung &quot;Bilder können nicht auf die Tracking-Server hochgeladen werden&quot; angezeigt. (NEO-38546, NEO-45572)
* Es wurde ein Problem behoben, das zum Absturz des Systems führte, wenn die Konfiguration im Falle von fehlerhaften Konfigurationsdateien neu generiert wurde. (NEO-38752)
* Fehlerkorrektur – Versandindikatoren werden jetzt korrekt aktualisiert. (NEO-44827)
* Fehlerkorrektur – Bei der Verwendung komplexer Abfragen tritt jetzt kein Postupgrade-Fehler mehr auf. (NEO-43648)
* Fehlerkorrektur – Die Vorschau von webApps funktioniert jetzt. (NEO-43242)
* Fehlerkorrektur – Die Versandvorbereitung schlägt jetzt nicht mehr fehl, wenn eine externe Zielgruppen-Mapping-Datei in einem Workflow mit der Aktivität Laden (Datei) verwendet wird. (NEO-43691)
* Es wurde ein Problem behoben, das zu Abstürzen führen konnte und einen vollständigen Neustart der Instanz erforderlich machte. (NEO-44645)
* Fehlerkorrektur – Die Workflow-Heatmap lädt jetzt Ergebnisse. (NEO-43360)
* Fehlerkorrektur – Bei der Verwendung des externen FDA-Connectors treten jetzt keine Verbindungsprobleme mehr auf. (NEO-42722)
* Fehlerkorrektur – Bei Testsendungen tritt jetzt kein Fehler mehr auf, wenn Adressersetzung und Ausschluss von Kontrollgruppen verwendet werden. (NEO-39695)
* Fehlerkorrektur – Es gibt jetzt kein Problem mehr mit dem Snowflake-Connector, der Workflow-Fehler verursachte. (NEO-46299)
* Fehlerkorrektur – Die Client-Konsole bleibt jetzt nicht mehr aufgrund eines ungültigen Zeichens in einem Gestaltungsbaustein hängen. (NEO-45761)
* Fehlerkorrektur – Beim Erstellen eines externen Kontos für Snowflake als externe Datenbank treten jetzt keine Verbindungsprobleme mehr auf. (NEO-45744)
* Fehlerkorrektur – Tabelleninformationen, die durch ein Attribut „visibleIf“ geschützt sind, werden jetzt nicht mehr angezeigt. (NEO-37865)
* Fehlerkorrektur – Während der Analysephase des Versands wird jetzt nicht mehr die Fehlermeldung „$ ist nicht definiert“ angezeigt. (NEO-32940)
* Fehlerkorrektur – Sendungen werden jetzt nicht mehr mit einem falschen eventType-Wert verknüpft. (NEO-45743)
* Fehlerkorrektur – Es gibt jetzt keine Core-Dumps (NEO-30549) mehr, die zu Abstürzen führen könnten.
* Fehlerkorrektur – Bei der Verwendung von fehlerhaftem HTML-Code in einem Versand kommt es jetzt nicht mehr zu Abstürzen. (NEO-40385)
* Fehlerkorrektur – Auch Benutzende ohne Administratorrechte können jetzt in den Versandeigenschaften auf die Registerkarte **Analyse** zugreifen. (NEO-34025)
* Fehlerkorrektur – Bilder können jetzt während der Nachrichtenvorbereitung von einem externen Server im Chunk-Modus hochgeladen werden. (NEO-40307)
* Ein Fehler wurde behoben, wodurch der Versand an eine größere Anzahl von Empfangenden als erwartet gesendet wurde. (NEO-45108)

## ![](assets/do-not-localize/green_2.png) Version 7.2.2 – Build 9349 {#release-7-2-2}

_1. März 2022_

>[!NOTE]
>
> Dieser Build ist mit der Client-Konsole v7.2.1 kompatibel.

**Patches**

* Fehlerkorrektur – Bei der Konfiguration des externen **Web-Analyse**-Kontos wird nun nicht mehr der Status &quot;Integration erfolgreich&quot; angezeigt, wenn Fehler auftreten. (NEO-36672)
* Fehlerkorrektur – Diverse Postupgrade-Fehler im Zusammenhang mit dem Sequenz-ID-Mechanismus bei negativen IDs wurden behoben. (NEO-43205, NEO-42846, NEO-42845)
* Fehlerkorrektur – Bei der Verwendung des externen **Web-Analyse**-Kontos mit wiederkehrenden und kontinuierlichen Sendungen gehen jetzt keine Daten des externen Kontos mehr verloren. (NEO-38548)
* Fehlerkorrektur – Das Postupgrade wird jetzt nicht mehr verlangsamt, wenn die NmsActiveContact-Tabelle aktualisiert wird. (NEO-43206)
* Fehlerkorrektur – Es gibt nun keinen Fehler mehr beim Postupgrade, wenn native Ordner vom Knoten **Administration** an einen anderen Ort verschoben werden. (NEO-42875)
* Fehlerkorrektur – Bei der Verwendung der Workflow-Aktivität **Daten aktualisieren** wird jetzt das Empfängerschema mit Empfängerdaten aus einer externen Google Cloud-Datenbank aktualisiert. (NEO-42343)
* Fehlerkorrektur – Beim Postupgrade tritt jetzt kein Fehler mehr im Zusammenhang mit dem Adobe Analytics-Connector auf. (NEO-43318, NEO-38136)
* Fehlerkorrektur – Beim Postupgrade wird jetzt eine CUID nicht mehr durch &quot;VALUE_TO_CHANGE&quot; überschrieben. (NEO-43267)
* Fehlerkorrektur – Beim Synchronisieren der Mid-Sourcing- und Marketing-Instanzen in einer Multi-Mid-Konfiguration treten jetzt keine Fehler mehr auf. (NEO-10432)
* Fehlerkorrektur – Beim Aktualisieren des Zustellbarkeits-Workflows tritt jetzt kein Fehler mehr auf, auch wenn mehr als 1.000 Broadlogs gleichzeitig verwendet werden. (NEO-40276)
* Fehlerkorrektur – Die Versandindikatoren &quot;Öffnungsverhältnis&quot; und &quot;Klick-Verhältnis&quot; werden jetzt automatisch aktualisiert. (NEO-43253)

## ![](assets/do-not-localize/limited_2.png) Version 7.2.1 – Build 9346 {#release-7-2-1}

_10. Januar 2022_

**Sicherheitsverbesserung**

An den FDA-Konten wurden verschiedene Sicherheitsverbesserungen vorgenommen:

* Bei der Konfiguration Ihres externen FDA-Kontos können Sie sich jetzt mit der Schlüsselpaar-Authentifizierung bei Ihrem Snowflake-Konto anmelden, wodurch die Authentifizierungssicherheit verbessert ist. [Mehr dazu](../../installation/using/configure-fda-snowflake.md)
* Beim Konfigurieren Ihres externen FDA-Kontos können Sie sich jetzt mit der vom System zugewiesenen verwalteten Identität bei Ihrem Azure Synapse Analytics-Konto anmelden. [Mehr dazu](../../installation/using/configure-fda-synapse.md#azure-external)
* Alle Verweise auf die log4j-Bibliothek wurden aus Campaign entfernt, um optimale Sicherheit zu gewährleisten.

**Aktualisierungen zur Kompatibilität**

Adobe Campaign ist jetzt mit Windows Server 2019 kompatibel. Weitere Informationen finden Sie in der [Kompatibilitätsmatrix für Campaign](../../rn/using/compatibility-matrix.md#OperatingSystems).

**Verbesserungen**

* Microsoft Dynamics CRM 365-Connector

   Es wurden kritische Fehlerbehebungen bei der Web-API des Microsoft Dynamics-Connectors vorgenommen:

   * Fehlerkorrektur – Beim Import, der durch einen Workflow ausgelöst wird, werden jetzt die Nullwerte von Feldern vom Typ Zeichenfolge als leere Werte statt als Null gespeichert.
   * Fehlerkorrektur – Beim Datenimport oder -export mithilfe von Web-API-Aufrufen tritt jetzt nicht mehr der Fehler „Ungültiger URI: Das URI-Schema ist zu lang“ auf:
   * Es wurden verschiedene Probleme beim Importieren von Daten mit Suchfeldern aus Microsoft Dynamics 365 behoben.

* Google BigQuery FDA-Connector

   * Der Google BigQuery FDA-Connector ist jetzt für gehostete Bereitstellungen verfügbar. [Mehr dazu](../../installation/using/configure-fda-google-big-query.md)
   * Es wurde Unterstützung zum Aktivieren von Verbindungen zu einem Proxy-Server für den Google BigQuery FDA-Connector hinzugefügt. Die erforderlichen Proxy-Optionen können über das Feld &quot;Optionen&quot; in der Konfiguration des externen Kontos festgelegt werden. [Weitere Informationen](../../installation/using/configure-fda-google-big-query.md#google-external)

**Sonstige Änderungen**

* Nach der Einstellung wurden die Aktionsaktivitäten von Microsoft CRM, Salesforce und Oracle CRM On Demand aus der Benutzeroberfläche entfernt. Um die Datensynchronisation zwischen Adobe Campaign und einem CRM-System zu konfigurieren, können Sie die Aktivität &quot;CRM-Connector&quot; verwenden. [Mehr dazu](../../workflow/using/crm-connector.md)
* Das Feld **[!UICONTROL Verschlüsselte Kennung]** wurde zum Besucherschema hinzugefügt (nms:visitor). Dieses Feld wird berechnet und ist für Web-Programme vorgesehen. Dies gilt, wenn der Kanal &quot;Line&quot; in der Mid-Sourcing-Instanz konfiguriert ist.
* CRM-Datenquellen können jetzt mit der Aktivität **Datenquelle ändern** verwendet werden.
* Eine neue Option wurde in den Eigenschaften zum **Umgang mit Fehlern** bei Workflow-Aktivitäten ergänzt: Die Option **Abbruch bei Fehler** sorgt dafür, dass der Workflow automatisch angehalten wird. Danach können Sie ihn nicht mehr neu starten (NEO-29661). [Mehr dazu](../../workflow/using/advanced-parameters.md#in-case-of-errors)
* Die Primärschlüssel der nmsGroup-Tabelle, die zur Erstellung statistischer Empfängergruppen verwendet wird, werden jetzt in einer speziellen Sequenz erzeugt. Zuvor wurde die Sequenz &quot;xtknewId&quot; verwendet. (NEO-30832)
* Es wurde Unterstützung für Batch-Aktualisierungsvorgänge mit der Aktivität &quot;CRM-Connector&quot; hinzugefügt.
* Die Leistung bei der Verarbeitungszeit für Transaktionsnachrichten wurde verbessert. (NEO-40370)

**Patches**

* Fehlerkorrektur – Bei der Erstellung eines Versands tritt jetzt kein Fehler mehr auf, der zu einem Fehler auf der Registerkarte **Bilder** im Fenster **Tracking &amp; Bilder** führt. Dies trat bei der Verwendung einer automatischen Proxy-Konfiguration auf. (NEO-33260)
* Es wurde ein Problem behoben, das das Hochladen einer Datei auf einen Debian 10-Server (HTTPS) im synchronen Modus verhindern konnte.
* Fehlerkorrektur – Es kommt jetzt nicht mehr vor, dass Datensätze aus der Versandstatistiktabelle (`nmsDeliveryLogStats`) während der Datenbankbereinigung nicht korrekt aus der Mid-Sourcing-Instanz bereinigt werden, nachdem die entsprechenden Sendungen gelöscht wurden. (NEO-31034)
* Fehlerkorrektur – Es tritt jetzt kein Fehler mehr auf, durch den auf iOS während der Token-basierten Authentifizierung keine Mobile-App-Benachrichtigungen gesendet werden können (NEO-38640).
* Fehlerkorrektur – Beim Erstellen und Konfigurieren von Berichten kommt es jetzt nicht mehr zur Anzeige von Scriptfehlermeldungen. (NEO-38393)
* Fehlerkorrektur – Auf Oracle kommt es jetzt nicht mehr zu einem Fehlschlagen des Tracking-Workflows, wenn zahlreiche Versandindikatoren gleichzeitig aktualisiert werden (NEO-39653).
* Fehlerkorrektur – Bei der Ausführung einer Kontrolltypologie kommt es jetzt nicht mehr dazu, dass ein Versand nicht erfolgt (NEO-39833).
* Fehlerkorrektur – Auf Landingpages kommt es jetzt nicht mehr dazu, dass Sonderzeichen auf den HTML-Seiten von Online-Umfrageantworten nicht korrekt angezeigt werden (NEO-39438).
* Fehlerkorrektur – In der Campaign Classic-Konsole tritt beim Rechtsklick auf einen der Ordner auf der Registerkarte &quot;Explorer&quot; kein Fehler mehr auf (NEO-38884).
* Fehlerkorrektur – Bei einem neuen Versand, bei dem die Web Analytics-Konfiguration fehlt, tritt jetzt kein Fehler mehr auf wenn eine zuvor erstellte Versandvorlage verwendet wird, die mit einem Web Analytics-Konto verknüpft ist. (NEO-28666)
* Fehlerkorrektur – Die Vorschau von Mobile-Sendungen, die mit einem Workflow verbunden sind, wird jetzt angezeigt.
* Fehlerkorrektur – Personalisierte Tracking-URLs werden jetzt umgeleitet, wenn der URL-Signaturmechanismus für Tracking-Links aktiviert ist.
* Fehlerkorrektur – Das Indexverwaltungsproblem wurde behoben, das zu Ausfällen nach einem Upgrade führen konnte.
* Fehlerkorrektur – Bei der Verwendung von Such-Felddatentypen mit Microsoft Dynamics CRM bei Aktivitäten in den Workflows **Import** oder **Export** tritt jetzt kein Fehler mehr auf.
* Fehlerkorrektur – Das Proxy-Konfigurationsproblem wurde behoben, aufgrund dessen eine Anmeldung bei der Konsole nicht möglich war. (NEO-38388)
* Es wurde ein Regressionsproblem behoben, das dazu führte, dass die Funktion **Ordner bereinigen** nicht ordnungsgemäß funktionierte. (NEO-37459)
* Fehlerkorrektur – Bei Verwendung von XML-Datenfeldern mit dem Microsoft Dynamics CRM-Konto kommt es jetzt nciht mehr zu einer fehlerhaften Anfrage, wenn die referenzierte XML doppelte Anführungszeichen enthält.
* Fehlerkorrektur – Probleme mit Netzwerküberschreitungen werden jetzt nicht mehr fälschlicherweise als Scriptunterbrechungsprobleme anstatt als Netzwerkfehler protokolliert. Dieses Problem trat bei HTTP-Anfragen auf, die in JavaScript-Aktivitäten enthalten waren. (NEO-38079)
* Es wurde ein Problem behoben, durch das beim Ausführen der HoursDiff- und MinutesDiff-Funktionen von Amazon Redshift beim Versuch, die Zeitkomponente zu extrahieren, falsche Ergebnisse ausgegeben wurden.(NEO-31673)
* Fehlerkorrektur – Der Fehler beim Laden des Berichts **Klicks** für Sendungen, der seit Build 9182 vorlag, tritt jetzt nicht mehr auf. (NEO-28900)
* Fehlerkorrektur – Das Symbol &quot;&amp;&quot; in einer URL wird jetzt nicht mehr durch die Zeichenentitätsreferenz (`&amp;`) ersetzt wurde, was Benutzer daran hinderte, auf die mit einem QR-Code verknüpfte URL zuzugreifen. (NEO-28621)
* Fehlerkorrektur – Es wird jetzt kein neues externes Konto mehr erstellt, wenn ein Benutzer einen neuen Kampagnen-Workflow und eine mit einem Web Analytics-Konto verknüpfte Versandaktivität erstellt. Dies wurde durch eine fehlende ID im Versandobjekt &quot;webAnalyticsAccount&quot; verursacht. (NEO-39691)
* Es wurde ein Problem behoben, das dazu führen konnte, dass die Workflow-Aktivität **Liste lesen** nicht funktionierte, wenn die Liste in der Datenbank mit einer negativen ID identifiziert wurde. (NEO-39607)
* Fehlerkorrektur – Der Workflow **Mid-Sourcing (Versandlogs)** schlägt jetzt nicht mehr fehl. (NEO-39662)
* Fehlerkorrektur – Bei der Vorschau von E-Mail-Sendungen, die mit einem Workflow verbunden sind, treten jetzt keine Anzeigefehler mehr auf. (NEO-37840)
* Fehlerkorrektur – Gültige Tabellen mit Listenwerten werden jetzt nicht mehr vom Datenbankbereinigungs-Workflow gelöscht. (NEO-34911)
* Fehlerkorrektur – Der Abrechnungs-Workflows bei Marketing-Instanzen stürzt jetzt nicht mehr ab.
