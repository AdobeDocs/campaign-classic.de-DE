---
product: campaign
title: Versionen 2020
description: Weiterführende Informationen zu Campaign Classic-Versionen 2020
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Overview
role: User
level: Beginner
hidefromtoc: true
exl-id: e2eb7e04-faaa-4df0-913d-471c291eeb03
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '6610'
ht-degree: 100%

---

# Versionen 2020 {#release-2020}




## Version 20.3{#release-20-3}

### ![](assets/do-not-localize/red_2.png) Version 20.3.3 – Build 9234 {#release-20-3-3-build-9234}

_11. Januar 2021_

* Fehlerkorrektur – Es wurde ein Sicherheitsproblem behoben, um den Schutz vor SSRF-Problemen (Server Side Request Forgery) zu verbessern. (NEO-27777)
* Es wurde ein Regressionsproblem im Zusammenhang mit der Broadlog-Generierung behoben, das zum Absturz des MTA-Prozesses führen konnte.

### ![](assets/do-not-localize/red_2.png) Version 20.3.1 – Build 9228 {#release-20-3-1-build-9228}

_27. Oktober 2020_

>[!CAUTION]
>
> * Diese Version enthält ein neues Verbindungsprotokoll: Wenn Sie über Adobe Identity Service (IMS) eine Verbindung zu Campaign herstellen, ist sowohl für den Campaign-Server als auch für die Client-Konsole eine Aktualisierung zwingend erforderlich, um auch nach dem **30. Juni 2021** eine Verbindung zu Campaign herstellen zu können. [Weitere Informationen](../../technotes/using/ims-updates.md)
> * Diese Version enthält eine [Sicherheitskorrektur](https://helpx.adobe.com/de/security/products/campaign/apsb21-04.html): Die Aktualisierung ist zwingend erforderlich, um die Sicherheit Ihrer Umgebung zu erhöhen.
> * Wenn Sie die Experience Cloud-Triggers-Integration über die OAuth-Authentifizierung verwenden, müssen Sie wie [auf dieser Seite](../../integrations/using/configuring-adobe-io.md) beschrieben zu Adobe I/O wechseln. Die alte oAuth-Authentifizierungsmethode mit Campaign [wurde eingestellt](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411?profile.language=de) am **September 2021**. Gehostete Umgebungen profitieren von einer Verlängerung bis zum **23. Februar 2022**. Wenden Sie sich als On-Premise- oder Hybrid-Kunde an die Kundenunterstützung von Adobe, um den Support bis Februar 2022 zu verlängern. Dazu müssen Sie Adobe [die AppID der OAuth-Anwendung](../../integrations/using/configuring-pipeline.md?lang=en#step-optional) nennen.


**Neue Funktionen**

<table> 
<thead>
<tr> 
<th> <strong>Verbesserungen bei iOS-Push-Benachrichtigungen</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>Wenn Sie Ihre App mit Campaign integrieren, müssen Sie Ihre Kommunikation mit Apple Push Notification Service (APNs) schützen. Sie können die zertifikatbasierte oder Token-basierte Authentifizierung verwenden.
</p>
<p>Diese beiden Authentifizierungsmodi sind jetzt für mobile iOS-Apps in Campaign Classic verfügbar:
</p>
<ul> 
<li><p>Token-basierte Authentifizierung (empfohlen): dieser Authentifizierungsmodus basiert auf einer .p8-Datei. Dieser Authentifizierungsmodus ist schneller, da jede Anfrage an APNs das Token enthält. <a href="https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_token-based_connection_to_apns">Weitere Informationen</a></p></li>
<li><p>Zertifikatbasierte Authentifizierung: dieser Authentifizierungsmodus basiert auf einer .p12-Datei. Für jede App ist ein separates Zertifikat erforderlich. Dieses Zertifikat wird von Apple über Ihr Entwicklerkonto bereitgestellt. <a href="https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_certificate-based_connection_to_apns">Weitere Informationen</a></p></li> 
</ul>
<p>In der <a href="../../delivery/using/configuring-the-mobile-application.md">entsprechenden Dokumentation</a> erfahren Sie, wie Sie den Authentifizierungsmodus in Campaign auswählen.</p>
</td> 
</tr> 
</tbody> 
</table>

<table> 
<thead>
<tr> 
<th> <strong>Verbesserungen bei Android-Push-Benachrichtigungen</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p><a href="../../delivery/using/configuring-the-mobile-application-android.md#creating-notification-message">Android-Push-Benachrichtigungen wurden verbessert, um die Version 1 der FCM HTTP-API für die Authentifizierung von Android-Push-Kanälen zu unterstützen.</a> </p>
<p>Mit der neuen unterstützten API-Version können Sie jetzt FCM-Benachrichtigungsinhalte senden, die erweiterte Funktionen für Push-Nachrichten bieten. <a href="https://firebase.google.com/docs/cloud-messaging/migrate-v1">Weitere Informationen</a></p> 
<p>Informationen zum Konfigurieren der Version 1 der FCM HTTP-API für Android in Adobe Campaign finden Sie in <a href="../../delivery/using/configuring-the-mobile-application-android.md">diesem Abschnitt</a>.</p>
</td> 
</tr> 
</tbody> 
</table>

**Verbesserungen bei der Sicherheit**

* Sicheres Laden von Bibliotheken: Zum Schutz vor DLL-Vorladeangriffen lädt Campaign jetzt beim Laden des Campaign-Clients (nlclient) Windows-DLLs nur aus dem Windows-Standard-System-DLL-Pfad. [Weitere Infos](https://support.microsoft.com/de-DE/help/2389418/secure-loading-of-libraries-to-prevent-dll-preloading-attacks) (NEO-24147)
* Fehlerkorrektur – Es wurde ein Sicherheitsproblem behoben, um den Schutz vor SSRF-Angriffen (Server Side Request Forgery) zu verbessern. (NEO-25661)
* Fehlerkorrektur – Es wurde ein Fehler behoben, der beim Bearbeiten von DSGVO-Datenschutzanfragen auftrat und verhinderte, dass Datensätze aus benutzerdefinierten Tabellen mit einer Beziehung zweiter Ebene zur Empfängertabelle gelöscht wurden. (NEO-25967)
* Fehlerkorrektur – Es wurde ein Sicherheitsproblem mit API-Aufrufen behoben, die von Benutzern ohne Administratorrechte beim Synchronisieren von Adobe Experience Manager-Vorlagen ausgeführt wurden. (NEO-23487)

**Aktualisierungen zur Kompatibilität**

Die folgenden Systeme werden jetzt von Campaign unterstützt:
* iOS 14
* PostgreSQL 12
* CentOS / RedHat 8
* MSSQL2019

Weiterführende Informationen finden Sie in der [Campaign-Kompatibilitätsmatrix](../../rn/using/compatibility-matrix.md).

**Eingestellte Funktionen**

Die folgenden Funktionen werden in Version 20.3 eingestellt:

* Die demdex-Domain, die zum Importieren und Exportieren von Audiences nach Adobe Experience Cloud verwendet wird, wird nicht mehr unterstützt. Wenn Sie die demdex-Domain für Ihre externen Import-/Export-Konten verwenden, müssen Sie Ihre Implementierung entsprechend anpassen. [Weitere Informationen](../../integrations/using/configuring-shared-audiences-integration-in-adobe-campaign.md)
* Die Authentifizierung für die Triggers-Integration, die ursprünglich auf der oAUTH-Authentifizierung basierte und für den Zugriff auf die Pipeline eingerichtet wurde, wurde geändert und in Adobe I/O verschoben. [Weitere Infos](../../integrations/using/configuring-adobe-io.md)

Weitere Informationen finden Sie auf der Seite [Eingestellte und entfernte Funktionen ](../../rn/using/deprecated-features.md).

**Verbesserungen**

* An der **Client-Konsole** wurden verschiedene Verbesserungen vorgenommen:
   * Das Verbindungsprotokoll wurde aktualisiert, sodass es dem neuen IMS-Authentifizierungsmechanismus entspricht. Das Upgrade der Server- und Client-Konsole ist obligatorisch, damit auch nach dem 30. Juni 2021 eine Verbindung hergestellt werden kann.
   * Um eine Inkompatibilität mit einigen Einschränkungen der Internet-Sicherheitsrichtlinien für Gruppenrichtlinienobjekte zu vermeiden, wurde der Anmeldebildschirm der Campaign-Client-Konsole durch ein integriertes Standard-Windows-Formular ersetzt.
   * Fehlerkorrektur – Es wurde ein Problem beim Kopieren/Einfügen von Aktivitäten in einem Workflow mit der 64-Bit-Client-Konsole behoben. (NEO-27635)
   * Im Menü **Info** wurden Informationen hinzugefügt, um 64- und 32-Bit-Konsolen zu unterscheiden.
* Die Workflow-Kennung wird jetzt beim Fortsetzen eines Workflows in den Logs angezeigt, sodass Sie besser erkennen können, welcher Workflow fortgesetzt wurde.
* Es wurde ein neues permanentes Cookie eingeführt: nllastdelid. Dieses Cookie (anders als UUID230) speichert die Versandkennung „deliveryId“. Wenn kein Sitzungs-Cookie vorhanden ist, werden Broadlog-Informationen aus der in diesem Cookie vorhandenen Versandkennung &quot;deliveryId&quot; entnommen.
Diese Änderung behebt ein Problem, das beim Beenden der Browser-Sitzung auftrat: das Sitzungs-Cookie mit deliveryId und broadlogId wurde gelöscht. Ohne deliveryId konnten die Broadlog-Informationen nicht gefunden werden und die Informationen der Tracking-Tabelle fehlten beim permanenten Tracking (letzter Versand).
Weiterführende Informationen zu Cookies finden Sie in [diesem Abschnitt](../../platform/using/privacy-and-recommendations.md#cookies).
* Verbesserter Versanddurchsatz bei hohem Volumen mit dem Zustellbarkeits-Server, indem der MTA-Prozess vor dem Versand neu gestartet wird.

**Sonstige Änderungen**

* Bei Verwendung des relativen Pfads für SFTP werden `~/`-Zeichen nicht mehr automatisch hinzugefügt. Bei Bedarf können Sie Ihrem Pfad `~/`-Zeichen manuell hinzufügen. Adobe empfiehlt jedoch die Verwendung eines **absoluten Pfads**.
* Die Windows NT-Authentifizierung wurde bei der Konfiguration einer neuen Datenbank mit einem Microsoft SQL Server aus den verfügbaren Authentifizierungsmechanismen entfernt. [Mehr dazu](../../installation/using/creating-and-configuring-the-database.md#step-1---selecting-the-database-engine)
* Der Datenbankbereinigungs-Workflow wurde für Teradata optimiert, um die Leistung zu verbessern. (NEO-19959)
* Die Fehlermeldung wurde verbessert, die angezeigt wird, wenn ein Bild aus Adobe Target eingefügt wird und der Name des Mandanten im externen Konto leer ist.
* In den Versandeigenschaften wurde die Option **[!UICONTROL E-Mails archivieren]** in **[!UICONTROL E-Mail-BCC]** umbenannt.
* Um die Stabilität zu verbessern, werden alle selectAll-Abfragen mit ungültigen Knoten jetzt abgelehnt. Wenn Sie die Prüfung deaktivieren und zum vorherigen Verhalten zurückkehren müssen, können Sie XtkSecurity_Disable_QueryCheck auf 0 setzen.
* Für die Sequenz nmsBroadlogId wurde die Unterstützung für negative ID-Bereiche hinzugefügt. Dieser Build passt den min_value der Sequenz nmsBroadlogId an, um den negativen Bereich einzuschließen. Falls Sie einen strikten Anwendungsfall haben, der keine negativen IDs zulässt, setzen Sie den min_value der Sequenz auf 1 zurück.

**Technische Entwicklungen**

Tomcat wurde von Version 7 (7.0.103) auf Version 8 (8.5.57) aktualisiert.

Der `tomcat-7`-Verzeichnis wird durch einen `tomcat-8`-Verzeichnis ersetzt.

Unter Windows werden _is_neolane_setup.vbs_ und _apache_neolane.conf_ jetzt im `conf`-Verzeichnis installiert (anstatt wie bisher in `tomcat-7/conf`).

Unter Linux wird _apache_neolane.conf_ jetzt im `conf`-Verzeichnis installiert.

**Korrekturen**

* Fehlerkorrektur – Es wurde ein Problem behoben, das die Neuberechnung von Versandstatistiken verhindern konnte.
* Fehlerkorrektur – Es wurde ein Problem behoben, bei dem beim Hochladen einer CSV-Datei eine Fehlermeldung angezeigt wurde, wenn Campaign Classic-Build 9080 mit einem Server verwendet wurde, der einen älteren Build verwendet. (NEO-23218)
* Fehlerkorrektur – Es wurde ein Fehler behoben, durch den beim Konfigurieren des Microsoft Dynamics CRM-Assistenten für ein externes Konto eine Fehlermeldung anzeigt werden konnte. Dies war auf ein Kompatibilitätsproblem mit der aktuellen Version der MS Dynamics CRM-API zurückzuführen. (NEO-24528)
* Fehlerkorrektur – Es wurde ein Fehler behoben, der den Export von Look-up-Datensätzen (d. h. Daten, die aus Fremdschlüsseldatensätzen bestehen, die mit anderen Tabellen verbunden sind) aus Campaign Classic nach Microsoft Dynamics über den CRM-Connector verhinderte. (NEO-23864)
* Fehlerkorrektur – Es wurde ein Fehler behoben, der das Aufrufen von Microsoft Dynamics-Daten verhindern konnte, wenn die Option **Automatischer Index** im CRM-Connector aktiviert war. (NEO-25981)
* Fehlerkorrektur – Es wurde ein Problem mit der IMS-Authentifizierung behoben, durch das Verbindungen geöffnet bleiben konnten, selbst wenn sie beendet wurden. Abgebrochene Verbindungen werden jetzt automatisch geschlossen, sobald sie beendet werden, um zu vermeiden, dass sich Verbindungen ansammeln und Systemressourcen verbrauchen. (NEO-25996)
* Fehlerkorrektur – Es wurde ein Problem behoben, bei dem keine Fehlermeldung angezeigt wurde, wenn die Synchronisation von Adobe Experience Manager-Inhalten aufgrund einer Fehlkonfiguration des externen Kontos (falsches Konto oder Kennwort) für einen Versand fehlschlug. Im Falle eines Fehlers wird jetzt eine Meldung angezeigt, mit der Sie das Problem leichter identifizieren können. (NEO-25586)
* Fehlerkorrektur – Es wurde ein Problem behoben, das bei der Auswahl des **Aktualisierungsvorgangs** in der Aktivität **Daten aktualisieren** auftrat. Wenn die zu aktualisierenden Daten falsch waren, war der Workflow fehlerhaft und schlug fehl. Bei falschen Daten schlägt der Workflow nicht fehl und die Datensätze werden in der ausgehenden Transition **Zurückweisungen** gespeichert. (NEO-23794)
* Fehlerkorrektur – Es wurde ein Fehler behoben, der dazu führte, dass Workflows mit Unter-Workflows nicht funktionierten. (NEO-24036)
* Fehlerkorrektur – Es wurde ein Fehler behoben, der beim Bearbeiten der Beschreibung einer Kampagnenvorlage dazu führte, dass die Schaltfläche **Speichern** beim Einfügen von Symbolen wie beispielsweise japanischen Zeichen nicht angezeigt wurde. (NEO-27071)
* Fehlerkorrektur – Es wurde ein Problem behoben, durch das verhindert werden konnte, dass Sie den Tracking-Server im Softwareverteilungs-Assistenten der Instanz ändern.
* Fehlerkorrektur – Es wurde ein Fehler behoben, durch den die Beschreibung einer Kampagne oder Kampagnenvorlage nicht gespeichert werden konnte, wenn vor dem Klicken auf die Schaltfläche **Speichern** außerhalb des Fensters geklickt wurde. (NEO-27449)
* Fehlerkorrektur – Es wurde ein Fehler behoben, der dazu führte, dass der technische Workflow **Anzahl der aktiven Rechnungsstellungsprofile** (billingActiveContactCount) nicht funktionierte. Dies konnte vorkommen, wenn ein Link für ein berechnetes Feld in einer Schemaerweiterung ausgeführt wurde. Es wurde eine große Datenmenge erzeugt, die dazu führen konnte, dass der Datenbank der temporäre Speicherplatz ausgeht. (NEO-24062)
* Fehlerkorrektur – Es wurde ein Problem mit der Aktivität **Laden (Datei)** behoben, durch das Sie möglicherweise keine japanischen Zeichen aus TXT- und CSV-Dateien importieren konnten, wenn diese am Ende der Datei positioniert waren. (NEO-24957)
* Fehlerkorrektur – Es wurde ein Problem mit dem Versand (kontinuierlich) behoben, durch das verhindert werden konnte, dass die Felder **Analysebeginn** und **Analyse abgeschlossen** ordnungsgemäß ausgefüllt wurden. (NEO-20755)
* Fehlerkorrektur – Es wurde ein Fehler behoben, durch den eine Fehlermeldung angezeigt werden konnte, wenn versucht wurde, SMS-Nachrichten nach einer Abfrage in einem anderen Schema als **Empfänger** (nms:recipient) in der Vorschau anzuzeigen. (NEO-27517)
* Fehlerkorrektur – Es wurde ein Problem bei der Verwendung des Snowflake FDA Connectors behoben. Ein Benutzer mit Zugriffsrechten auf Snowflake FDA konnte für ein Snowflake-Schema keine Abfrage ausführen. In den Logs wurde ein Fehler vom Typ &quot;Kennwort nicht gefunden&quot; angezeigt. (NEO-23851)
* Fehlerkorrektur – Es wurde ein Problem bei der Verwendung eines FDA Connectors behoben, das auftrat, wenn der Name des verknüpften FDA-Schemas eine Teilzeichenfolge des Elementnamens des aktuellen Schemas war. Dies trat beispielsweise auf, wenn das FDA-Schema &quot;cust&quot; und eines der Elemente innerhalb des Empfängerschemas &quot;customer&quot; war. Beim Abrufen der Spalte innerhalb des Elements &quot;customer&quot; und Hinzufügen einer Spalte aus dem FDA-Schema &quot;cust&quot; fehlte der Wert für die lokale Spalte. (NEO-20193)
* Fehlerkorrektur – Es wurde ein Fehler in Workflows behoben, der auftrat, wenn Datensätze aus einer externen Datenbank abgerufen und in die Campaign-Datenbank eingefügt wurden. (NEO-26359)
* Fehlerkorrektur – Es wurde ein Problem im technischen Workflow **Ereignisstatus-Update** behoben: Um die Größe der entsprechenden eingehenden Felder in der Aktivität **Versandstatistiken** anzupassen, wurde die Größe von drei Zielfeldern in der Aktivität **Versandstatistiken aktualisieren** von 32 auf 64 Bit geändert. (NEO-11557) Weitere Informationen zum Workflow **Ereignisstatus-Update** finden Sie in [diesem Abschnitt](../../workflow/using/about-technical-workflows.md).
* Fehlerkorrektur – Es wurde ein Fehler im Bericht **Message Center-Ereignisverlauf** behoben, der beim Anwenden von Filtern zu Skriptfehlern führte und das Filtern nach einem Datumsbereich unmöglich machte. (NEO-23365)
* Fehlerkorrektur – Es wurde ein Interferenzfehler zwischen den technischen Workflows für **Campaign-Vorgänge** (operationMgt) und **Vorschau** (forceasting) behoben. Dieser trat auf, wenn geplante Sendungen im Status &quot;Zielgruppenbestimmung abgeschlossen&quot; oder &quot;Versandbereit&quot; verblieben. (NEO-20819)
* Fehlerkorrektur – Es wurde ein XML-Parsing-Problem behoben, das auftrat, wenn die XML-Kennung nicht im Feld &quot;mdata&quot; in xtkOperator vorhanden war. Dadurch wurden Postupgrade-Fehler verursacht. (NEO-26113)
* Fehlerkorrektur – Es wurde ein Problem bei der Verwendung der Aktivität **Datenübertragung** behoben, die mit einem mit SSL verschlüsselten externen Azure-Konto verknüpft war, wobei die Verbindung mit HTTP statt HTTPS hergestellt wurde. (NEO-26720)
* Fehlerkorrektur – Es wurde ein Problem bei der MSSQL-Datenbank behoben, bei dem während des Bereinigungs-Workflows ein Fehler beim Vorgang &quot;up_updatestats&quot; aufgetreten ist.
* Fehlerkorrektur – Es wurde ein Absturz behoben, der beim Herunterfahren des Webprozesses auftrat, wenn Interaktionsanfragen weiterhin verarbeitet wurden. (NEO-26447)
* Fehlerkorrektur – Es wurde ein Problem behoben, bei dem die Funktion **NoNull** in Oracle DB nach der Aktualisierung 9032 nicht mehr funktionierte. (NEO-26488)
* Fehlerkorrektur – Es wurde ein Problem behoben, bei dem der Tracking-Workflow nach der Aktualisierung 9171 fehlschlug, wenn das LINEV2-Paket ohne das Message Center-Paket installiert wurde.
* Fehlerkorrektur – Es wurde ein Problem mit der Skalierbarkeit behoben, bei dem der Verbindungspool nicht auf die gewünschte Anzahl von Verbindungen erhöht werden konnte, da die Datenbankverbindungszeichenfolge für das Attribut &quot;APP&quot; am Ende einen ungültigen Wert erhielt. (NEO-25105)
* Fehlerkorrektur – Es wurde ein Problem auf Proxy-Konfigurationsebene behoben, durch das Sie sich nach dem letzten Windows 10-Update nicht mehr bei Adobe Campaign anmelden konnten. (NEO-27813)
* Fehlerkorrektur – Es wurde ein Fehler behoben, der dazu führte, dass unerwünschte URLs in den gesendeten E-Mails angezeigt wurden, nachdem HTML-Vorlagen mit Trackinglinks importiert wurden. (NEO-25909)
* Fehlerkorrektur – Es wurde ein Fehler behoben, der dazu führte, dass der Server abstürzte, wenn die Zieldaten des Rests einer **Aufspaltungsaktivität** in einem Workflow angezeigt wurden.
* Fehlerkorrektur – Es wurde ein Problem behoben, das zum Absturz des Servers führte, indem eine Speicherbeschädigung beim Bereinigen des Ausdrucks-Parsers verhindert wurde. (NEO-26856)
* Fehlerkorrektur – Es wurde ein Problem in der Anreicherungsaktivität behoben, bei dem Benutzer ohne Administratorrechte Instanzvariablen definiert haben. (NEO-25653)
* Fehlerkorrektur – Eine Regression blockiert nicht mehr den Export von Workflow-Daten in eine FDA-Datenbank (Teradata, Snowflake).

## Version 20.2{#release-20-2}

### ![](assets/do-not-localize/limited_2.png) Version 20.2.5 – Build 9188 {#release-20-2-5-build-9188}

_Donnerstag, 15. April 2021_

* Fehlerkorrektur – Es wurde eine Regression in der Client-Konsole korrigiert, die dazu führte, dass im IMS-Verbindungsfenster fortwährend Fehlermeldungen ausgegeben wurden. (NEO-34821)

**Es ist nur eine Konsolenaktualisierung obligatorisch. Eine Serveraktualisierung ist nicht erforderlich.**

>[!NOTE]
>
> Stellen Sie eine Verbindung zu [Adobe Softwareverteilung](https://experience.adobe.com/#/downloads/content/software-distribution/de/campaign.html) her, um die neue Version herunterzuladen. Erfahren Sie [auf dieser Seite](../../installation/using/client-console-availability-for-windows.md), wie Sie die Konsolenaktualisierung allen Endbenutzern vorschlagen können.

_Mittwoch, 31. März 2021_

**Verbesserungen**

* Es wurde eine Verbesserung vorgenommen, um Abstürze bei ungültigen SOAP-Aufrufen zu verhindern. Dies kann dazu führen, dass die Instanz beim Versuch, bestimmte komplexe Abfragen auszuführen, nicht mehr funktioniert. (NEO-28796, NEO-30553)
* Korrektur einer Regression, die dazu führte, dass SMS-Sendungen mit TLS aufgrund der Host-Namenüberprüfung nicht ausgeführt wurden. (NEO-29581)
* Fehlerkorrektur – Signierte Tracking-Links funktionieren jetzt auf allen E-Mail-Clients. (NEO-28414, NEO-29615)
* Fehlerkorrektur – Eine Tracking-Kennung-Sequenz bei der Verwendung von webApp-Tracking-Tags wurde korrigiert, die zu Konflikten mit doppelten IDs führen konnte. (NEO-27931)
* Fehlerkorrektur – Laufende Workflows werden jetzt nicht mehr durch den täglichen Neustart des wfserver gestoppt. (NEO-30047)
* Fehlerkorrektur – Es wurde ein Sicherheitsproblem mit API-Aufrufen behoben, die von Benutzern ohne Administratorrechte beim Synchronisieren von Adobe Experience Manager-Vorlagen ausgeführt wurden. (NEO-32389, NEO-23487)
* Fehlerkorrektur – Die Konsole stürzt jetzt nicht mehr ab, wenn ein Versanddialog für einen Versand geschlossen wurde, der mit einer Vorlage erstellt wurde. (NEO-31547)
* Fehlerkorrektur – Beim Erstellen und Speichern eines Versands in der Registerkarte **Targeting und Workflows** einer Kampagne tritt jetzt kein Fehler mehr auf. Zuvor schlug die Vorschau fehl und folgender Fehler wurde angezeigt.(NEO-29440)
* Fehlerkorrektur – Tomcat 8.5 sendet jetzt keine ungültigen Antworten mehr. Zuvor führte dies zu Fehlern in den Transaktionsnachrichten-Protokollen. (NEO-30858)
* Fehlerkorrektur – Jetzt tritt kein Regressionsproblem mehr auf. Zuvor führte dies zu einer Speicherbeschädigung in der externen Thread-Verwaltung und beeinträchtigte die Leistung.
* Fehlerkorrektur – Jetzt schlägt der Fakturierungs-Workflow bei der Verwendung eines benutzerdefinierten Zielgruppen-Mappings nicht mehr fehl. Der Primärschlüssel des benutzerdefinierten Schemas wird in der Spalte &quot;sourceId&quot; gespeichert, in der nur ganzzahlige Werte zulässig sind. Jetzt sind sowohl Ganzzahl- als auch Zeichenfolgenwerte zulässig. (NEO-25914, NEO-28146)
* Korrektur einer Regression, die die Verwendung einiger Konsolenkomponenten wie der Datumsauswahl und der Bildverwaltung in Sendungen verhinderte. (NEO-31453)

### ![](assets/do-not-localize/red_2.png) Version 20.2.4 – Build 9187 {#release-20-2-4-build-9187}

_Donnerstag, 15. April 2021_

* Fehlerkorrektur – Es wurde eine Regression in der Client-Konsole korrigiert, die dazu führte, dass im IMS-Verbindungsfenster fortwährend Fehlermeldungen ausgegeben wurden. (NEO-34821)
* Korrektur einer Regression, die die Verwendung einiger Konsolenkomponenten wie der Datumsauswahl und der Bildverwaltung in Sendungen verhinderte. (NEO-31453, NEO-31454)

**Es ist nur eine Konsolenaktualisierung obligatorisch. Eine Serveraktualisierung ist nicht erforderlich.**

>[!NOTE]
>
> Stellen Sie eine Verbindung zu [Adobe Softwareverteilung](https://experience.adobe.com/#/downloads/content/software-distribution/de/campaign.html) her, um die neue Version herunterzuladen. Erfahren Sie [auf dieser Seite](../../installation/using/client-console-availability-for-windows.md), wie Sie die Konsolenaktualisierung allen Endbenutzern vorschlagen können.

_Dienstag, 22. Dezember 2020_

>[!CAUTION]
>
> * Diese Version enthält ein neues Verbindungsprotokoll: Wenn Sie über Adobe Identity Service (IMS) eine Verbindung zu Campaign herstellen, ist sowohl für den Campaign-Server als auch für die Client-Konsole eine Aktualisierung zwingend erforderlich, um auch nach dem **30. Juni 2021** eine Verbindung zu Campaign herstellen zu können.  [Weitere Informationen](../../technotes/using/ims-updates.md)
> * Diese Version enthält eine [Sicherheitskorrektur](https://helpx.adobe.com/de/security/products/campaign/apsb21-04.html): Die Aktualisierung ist zwingend erforderlich, um die Sicherheit Ihrer Umgebung zu erhöhen.
> * Wenn Sie die Experience Cloud-Triggers-Integration über die OAuth-Authentifizierung verwenden, müssen Sie wie [auf dieser Seite](../../integrations/using/configuring-adobe-io.md) beschrieben zu Adobe I/O wechseln. Die alte oAuth-Authentifizierungsmethode mit Campaign [wurde eingestellt](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411?profile.language=de) am **September 2021**. Gehostete Umgebungen profitieren von einer Verlängerung bis zum **23. Februar 2022**. Wenden Sie sich als On-Premise- oder Hybrid-Kunde an die Kundenunterstützung von Adobe, um den Support bis Februar 2022 zu verlängern. Dazu müssen Sie Adobe [die AppID der OAuth-Anwendung](../../integrations/using/configuring-pipeline.md?lang=en#step-optional) nennen.


**Verbesserungen**

* Das Verbindungsprotokoll wurde aktualisiert, um dem neuen IMS-Authentifizierungsmechanismus zu folgen.
* Die Authentifizierung für die Triggers-Integration, die ursprünglich auf der oAUTH-Authentifizierung basierte und für den Zugriff auf die Pipeline eingerichtet wurde, wurde geändert und in Adobe I/O verschoben. [Weitere Infos](../../integrations/using/configuring-adobe-io.md)
* Nach dem [Ende der Unterstützung für das ältere Binärprotokoll von iOS-APNs](https://developer.apple.com/news/?id=c88acm2b) werden alle Instanzen, die dieses Protokoll verwenden, während des Postupgrades auf das HTTP/2-Protokoll aktualisiert.
* Fehlerkorrektur – Es wurde ein Sicherheitsproblem behoben, um den Schutz vor SSRF-Problemen (Server Side Request Forgery) zu verbessern. (NEO-27777)
* Fehlerkorrektur – Es wurde ein Problem behoben, das zur Deaktivierung des SMPP-Connectors nach einem Verbindungsfehler führte, was die Ausführung weiterer SMS-Sendungen verhinderte und zu Leistungsproblemen führte. (NEO-28609)
* Fehlerkorrektur – Es wurde ein Problem behoben, das zum Absturz des Servers führte, indem eine Speicherbeschädigung beim Bereinigen des Ausdrucks-Parsers verhindert wurde. (NEO-26856)
* Fehlerkorrektur – Es wurde ein Fehler behoben, der dazu führte, dass der Server abstürzte, wenn die Zieldaten des Rests einer **Aufspaltungsaktivität** in einem Workflow angezeigt wurden.
* Fehlerkorrektur – Es wurde ein Fehler behoben, durch den eine Fehlermeldung angezeigt werden konnte, wenn versucht wurde, SMS-Nachrichten nach einer Abfrage in einem anderen Schema als **Empfänger** (nms:recipient) in der Vorschau anzuzeigen. (NEO-27517)
* Fehlerkorrektur – Es wurde ein Problem behoben, wenn eine HTTPS-Verbindungsanforderung mit der im Hostnamen explizit definierten Port-Nummer gestellt wurde. Der Aufruf schlug wegen eines Zertifikatfehlers fehl. (NEO-29146)
* Fehlerkorrektur – Es wurde ein Problem im POSIX-Thread-Management behoben, durch das große Core-Dump-Dateien in der Marketing-Instanz generiert wurden. (NEO-28117, NEO-29281)
* Fehlerkorrektur – Es wurden Probleme behoben, die bei der Sendungsvorbereitung oder der Vorschau eines wiederkehrenden Versands zum Absturz des Web-Prozesses führten. (NEO-27790, NEO-27517)
* Fehlerkorrektur – Es wurde ein Fehler behoben, der zum Fehlschlagen von Sendungen oder Testsendungen führte, wenn diese von einem Benutzer ohne Administratorrechte ausgelöst wurden. (NEO-28597)

![](assets/do-not-localize/cp-icon.png) **Neue Control Panel-Version vom Oktober** mit Domain-Konfiguration unter Verwendung von CNAMEs und neuen Funktionen zur Datenbanküberwachung. [Weitere Informationen](https://experienceleague.adobe.com/docs/control-panel/using/release-notes.html?lang=de).

### ![](assets/do-not-localize/red_2.png) Version 20.2.3 – Build 9182 {#release-20-2-3-build-9182}

_Freitag, 11. September 2020_

* Fehlerkorrektur – Es wurde eine Regression korrigiert, die dazu führte, dass die Sendungsvorbereitung aufgrund einer einzigen fehlerhaften Funktion im Versand blockiert wurde, was zu einer Speicherüberlastung führte. (NEO-27346)
* Fehlerkorrektur – Es wurde ein Problem mit einem Postupgrade behoben, durch das Apache und der Webserver vor der erneuten Veröffentlichung der Web-Applikation deaktiviert wurden. (NEO-27155)
* Fehlerkorrektur - Eine Regression bei der Verwaltung von HTML-Vorlagen, die dazu führte, dass Tracking-URLs aufgrund einer falschen Interpretation von Tabs sichtbar wurden, wurde behoben. (NEO-25909)
* Fehlerkorrektur – Es wurde ein Problem mit dem Datenbankbereinigungs-Workflow behoben, der aufgrund einer nicht verwalteten Datenquelle fehlschlagen konnte. (NEO-23160, NEO-23364)
* Der Bereinigungs-Workflow bereinigt jetzt abgelaufene Listen in Stapeln von 100 anstelle einzeln.
* Fehlerkorrektur – Es wurde eine Regression korrigiert, die verhinderte, dass Sie den internen Namen eines externen Kontos ändern konnten. (NEO-27323)
* Fehlerbehebung – Es wurde eine Regression während eines Postupgrades korrigiert, die einen fehlerhaften Start von nlserver verursachte (Fehlerprotokolle).
* Die Aktualisierungsverwaltung für gemeinsamen Speicher wurde verbessert. Die in Version 20.2 erforderlichen zusätzlichen Schritte werden nicht mehr benötigt.

### ![](assets/do-not-localize/red_2.png) Version 20.2.2 – Build 9180 {#release-20-2-2-build-9180}

_Mittwoch, 22. Juli 2020_

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
* Es wurde ein Absturzproblem im Bereitstellungassistenten behoben.
* Fehlerkorrektur – Der Angebotsbenachrichtigungs-Workflow funktioniert jetzt nach einem Postupgrade richtig.
* Der iOS-HTTP2-Connector wurde verbessert (Updates von Drittanbietern und Fehlerverwaltung). (NEO-25904, NEO-25903)
* Die Liste &quot;jarsToSkip&quot; in &quot;catalina.properties&quot; wurde aktualisiert, um den Verweis auf eine nicht mehr verwendete JAR-Datei zu entfernen (iOS-Benachrichtigungen).
* Fehlerkorrektur – Es wurde ein Problem behoben, das die Versandvorbereitung nach einem Postupgrade blockierte.
* Nach dem Wechsel zum neuen Sequenz-ID-Mechanismus werden alle Web-Anwendungen, die die Empfänger-Tabelle aktualisieren, während des Postupgrades erneut veröffentlicht.
* Es wurde eine potenzielle XSS-Schwachstelle in Versandinhalt behoben. (NEO-17987, NEO-26073)

![](assets/do-not-localize/cp-icon.png) **Neue Control Panel-Version im Juni** mit der Überwachung aktiver Profile, der Prüfung der Subdomain-Zustellbarkeit und der GPG-Schlüsselverwaltung. [Weitere Informationen](https://experienceleague.adobe.com/docs/control-panel/using/release-notes.html?lang=de).

### ![](assets/do-not-localize/red_2.png) Version 20.2.1 – Build 9178 {#release-20-2-1-build-9178}

_Montag, 8. Juni 2020_

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
    <p>Azure Synapse ist nur für Hybrid- und On-Premise-Umgebungen verfügbar. Weitere Informationen finden Sie im <a href="../../installation/using/configure-fda-synapse.md">entsprechenden Handbuch</a>.</p>
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

* Für mehr Schutz gegen XSS-Angriffe werden Client-seitige Skripte beim Ausführen einer Mirror-Seite deaktiviert. (NEO-17987)

* Fehlerkorrektur – Der technische Workflow zur **Bereinigung von Datenschutzanfragen** kann jetzt Abstimmungsdaten löschen. (NEO-25168, NEO-21004)

* Fehlerkorrektur – Bei der Aktivität **Dateiübertragung** funktioniert jetzt die SFTP-Schlüssel-basierte Authentifizierung bei Debian 9. (NEO-23183)

**Kompatibilitätsverbesserungen**

Die folgenden Systeme werden jetzt von Campaign unterstützt:
* Betriebssysteme: Debian 10
* RDBMS: Oracle 18c und Oracle 19c
* FDA: Azure Synapse Analytics

Weiterführende Informationen finden Sie in der [Campaign-Kompatibilitätsmatrix ](https://helpx.adobe.com/de/campaign/kb/compatibility-matrix.html).

**Verbesserungen**

* Transaktionsnachrichten wurden optimiert, um ein besseres Benutzererlebnis zu bieten. Sie können die Veröffentlichung einer Transaktionsnachrichten-Vorlage jetzt aufheben, womit sie aus den Ausführungsinstanzen gelöscht wird. [Weitere Informationen](../../message-center/using/publishing-message-templates.md#template-unpublication).

* Es gibt neue Optionen zum Festlegen von Einschränkungen beim Senden von E-Mails, die Bilder oder Anhänge enthalten. Damit lassen sich Leistungsprobleme verhindern, was besonders bei Transaktionsnachrichten nützlich ist. [Mehr dazu](../../installation/using/configuring-campaign-options.md#delivery)

* Mit der neuen Option **Versandteile in der Datenbank vorbereiten** kann die Versandvorbereitung direkt in der Datenbank vorgenommen werden, was die Analyse erheblich beschleunigen kann. Diese Option steht nur bei bestimmten Konfigurationen zur Verfügung. [Weitere Informationen](../../delivery/using/steps-validating-the-delivery.md#improving-delivery-analysis). (NEO-23886)

* Die Leistung der [CRM Connector-Aktivität](../../workflow/using/crm-connector.md) für Microsoft Dynamics wurde verbessert. (NEO-13303, NEO-12710)

* Die Version mit gemeinsamem Speicher wurde verbessert.

   >[!WARNING]
   >
   >Die Optimierung setzt einen zusätzlichen Schritt nach dem Upgrade voraus. Lesen Sie diesbezüglich den Abschnitt **Technische Entwicklungen** weiter unten.

* Der Bereinigungs-Workflow wurde verbessert. Verwaiste Arbeitstabellen aller gelöschten Workflows werden vom Bereinigungs-Workflow jetzt auch automatisch gelöscht. [Weitere Informationen](../../production/using/database-cleanup-workflow.md#cleanup-of-workflow-instances).

* Zertifikate für iOS-Mobile Apps mit dem iOS-HTTP2-Connector werden jetzt vor dem Senden von Push-Benachrichtigungen validiert, was verhindert, dass Sendungen aufgrund abgelaufener Zertifikate fehlschlagen.

* Die Verwaltung von HTTP-Proxy-Verbindungen wurde verbessert. [Weitere Informationen](../../installation/using/file-res-management.md).

* Neue Option in den Workflow-Aktivitäten **[!UICONTROL JavaScript-Code]** und **[!UICONTROL Erweiterter JavaScript-Code]**, um die Ausführung nach einer Begrenzung zu beenden. Der Standardwert ist 1 Stunde. [Weitere Informationen](../../workflow/using/sql-code-and-javascript-code.md#javascript-code).

**Sonstige Änderungen**

* Alte SMS-Connectoren werden jetzt nicht mehr unterstützt. Weiterführende Informationen finden Sie auf der [Seite zu eingestellten Funktionen](../../rn/using/deprecated-features.md).

* Sie können Ihr eigenes Litmus-Konto nicht mehr zur Bereitstellung und Verwendung von Inbox Rendering in Adobe Campaign nutzen. [Weitere Informationen](../../delivery/using/inbox-rendering.md).

* Zur leichteren Unterscheidung von Ansichten und Ordnern wurde die Farbe der Ansichtnamen von dunkelblau in dunkeltürkis geändert. [Mehr dazu](../../platform/using/access-management-folders.md)

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
* Fehlerkorrektur – Das Veröffentlichen eines Angebots führt jetzt nicht mehr zu einem Fehler. (NEO-23312)
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
* Fehlerkorrektur – Es wurde ein Problem mit zusätzlichen Speicherfeldern behoben, das beim Erstellen von Sendungen mithilfe der Option **Wird durch ein Skript erstellt** in der Workflow-Aktivität **Skript** auftrat. (NEO-20609)
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


## Version 20.1{#release-20-1}

### ![](assets/do-not-localize/limited_2.png) Version 20.1.4 – Build 9126 {#release-20-1-4-build-9126}

_Donnerstag, 15. April 2021_

* Fehlerkorrektur – Es wurde eine Regression in der Client-Konsole korrigiert, die dazu führte, dass im IMS-Verbindungsfenster fortwährend Fehlermeldungen ausgegeben wurden. (NEO-34821)

**Es ist nur eine Konsolenaktualisierung obligatorisch. Eine Serveraktualisierung ist nicht erforderlich.**

>[!NOTE]
>
> Stellen Sie eine Verbindung zu [Adobe Softwareverteilung](https://experience.adobe.com/#/downloads/content/software-distribution/de/campaign.html) her, um die neue Version herunterzuladen. Erfahren Sie [auf dieser Seite](../../installation/using/client-console-availability-for-windows.md), wie Sie die Konsolenaktualisierung allen Endbenutzern vorschlagen können.

_Montag, 22. März 2021_

* Korrektur einer Regression, die die Verwendung einiger Konsolenkomponenten wie der Datumsauswahl und der Bildverwaltung in Sendungen verhinderte. (NEO-31453, NEO-31454)

**Es ist nur eine Konsolenaktualisierung obligatorisch. Eine Serveraktualisierung ist nicht erforderlich.**

>[!NOTE]
>
> Stellen Sie eine Verbindung zu [Adobe Softwareverteilung](https://experience.adobe.com/#/downloads/content/software-distribution/de/campaign.html) her, um die neue Version herunterzuladen. Erfahren Sie [auf dieser Seite](../../installation/using/client-console-availability-for-windows.md), wie Sie die Konsolenaktualisierung allen Endbenutzern vorschlagen können.

_Mittwoch, 23. Dezember 2020_

>[!CAUTION]
>
> * Diese Version enthält ein neues Verbindungsprotokoll: Wenn Sie über Adobe Identity Service (IMS) eine Verbindung zu Campaign herstellen, ist sowohl für den Campaign-Server als auch für die Client-Konsole eine Aktualisierung zwingend erforderlich, um auch nach dem **30. Juni 2021** eine Verbindung zu Campaign herstellen zu können. [Weitere Informationen](../../technotes/using/ims-updates.md)
>
> * Diese Version enthält eine [Sicherheitskorrektur](https://helpx.adobe.com/de/security/products/campaign/apsb21-04.html): Die Aktualisierung ist zwingend erforderlich, um die Sicherheit Ihrer Umgebung zu erhöhen.


* Das Verbindungsprotokoll wurde aktualisiert, sodass es dem neuen IMS-Authentifizierungsmechanismus entspricht.
* Fehlerkorrektur – Es wurde ein Sicherheitsproblem behoben, um den Schutz vor SSRF-Problemen (Server Side Request Forgery) zu verbessern. (NEO-27777)

### ![](assets/do-not-localize/red_2.png) Version 20.1.3 – Build 9124{#release-20-1-3-build-9124}

_Mittwoch, 6. Mai 2020_

* Es wurde ein Problem mit der Aktivität **Dateiübertragung** behoben, das bei Debian 9 eine SFTP-Schlüssel-basierte Authentifizierung verhinderte. (NEO-23183)

### ![](assets/do-not-localize/red_2.png) Version 20.1.2 – Build 9123{#release-20-1-2-build-9123}

_Freitag, 13. März 2020_

* Die Bereitstellung von Versionen auf Red Hat 7-Servern funktioniert jetzt problemlos. (NEO-23332)

### ![](assets/do-not-localize/red_2.png) Version 20.1 – Build 9122{#release-20-1-build-9122}

_Montag, 17. Februar 2020_

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
    <p>Weiterführende Informationen finden Sie in der <a href="../../installation/using/configure-fda-snowflake.md">ausführlichen Dokumentation</a> und im <a href="https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/administrating/fda/big-data-segmentation-on-snowflake.html?lang=de">Tutorial-Video</a>.</p>
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
    <p>Weitere Informationen finden Sie im <a href="../../installation/using/configure-fda-hadoop.md">entsprechenden Handbuch</a>.</p>
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

* Die verbrauchsintensivsten benutzerdefinierten Tabellen wurden aus der Sequenz **xtkNewId** in dedizierte Sequenzen verschoben.

* Die Abfrageleistung wurde verbessert, die zuvor durch unnötige Datenbankverbindungen beeinträchtigt sein konnte.

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
