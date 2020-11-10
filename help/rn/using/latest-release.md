---
title: Aktuelle Version
description: Aktuelle Version von Campaign Classic  Anmerkungen
page-status-flag: never-activated
uuid: 269d590c-5a6d-40b9-a879-02f5033863fc
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rns
content-type: reference
topic-tags: latest-release-notes
discoiquuid: 5df34f55-135a-4ea8-afc2-f9427ce5ae7b
translation-type: tm+mt
source-git-commit: 36fef519be93b33d55a96992c1ce234f2eaea696
workflow-type: tm+mt
source-wordcount: '1824'
ht-degree: 100%

---


# Aktuelle Version{#latest-release}

Auf dieser Seite werden neue Funktionen, Verbesserungen und Fehlerbehebungen der **aktuellen Campaign Classic Release Candidate-Version** aufgelistet.

Die Informationen für die Campaign Classic Gold Standard-Version (aktueller allgemein verfügbarer Build) [finden Sie auf dieser Seite](../../rn/using/gold-standard.md).

## ![](assets/do-not-localize/blue_2.png) Version 20.3.1 – Build 9228 {#release-20-3-1-build-9228}

_27. Oktober 2020_

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
<li><p>Token-basierte Authentifizierung (empfohlen): dieser Authentifizierungsmodus basiert auf einer .p8-Datei. Dieser Authentifizierungsmodus ist schneller, da jede Anfrage an APNs das Token enthält. <a href="https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_token-based_connection_to_apns">Mehr dazu</a></p></li>
<li><p>Zertifikatbasierte Authentifizierung: dieser Authentifizierungsmodus basiert auf einer .p12-Datei. Für jede App ist ein separates Zertifikat erforderlich. Dieses Zertifikat wird von Apple über Ihr Entwicklerkonto bereitgestellt. <a href="https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_certificate-based_connection_to_apns">Mehr dazu</a></p></li> 
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
<p>Mit der neuen unterstützten API-Version können Sie jetzt FCM-Benachrichtigungsinhalte senden, die erweiterte Funktionen für Push-Nachrichten bieten. <a href="https://firebase.google.com/docs/cloud-messaging/migrate-v1">Mehr dazu</a></p> 
<p>Informationen zum Konfigurieren der Version 1 der FCM HTTP-API für Android in Adobe Campaign finden Sie in <a href="../../delivery/using/configuring-the-mobile-application-android.md">diesem Abschnitt</a>.</p>
</td> 
</tr> 
</tbody> 
</table>

**Verbesserungen bei der Sicherheit**

* Sicheres Laden von Bibliotheken: Zum Schutz vor DLL-Vorladeangriffen lädt Campaign jetzt beim Laden des Campaign-Clients (nlclient) Windows-DLLs nur aus dem Windows-Standard-System-DLL-Pfad. [Mehr dazu](https://support.microsoft.com/de-de/help/2389418/secure-loading-of-libraries-to-prevent-dll-preloading-attacks) (NEO-24147)
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

* Die demdex-Domain, die zum Importieren und Exportieren von Audiences nach Adobe Experience Cloud verwendet wird, wird nicht mehr unterstützt. Wenn Sie die demdex-Domain für Ihre externen Import-/Export-Konten verwenden, müssen Sie Ihre Implementierung entsprechend anpassen. [Mehr dazu](../../integrations/using/configuring-shared-audiences-integration-in-adobe-campaign.md)
* Die Authentifizierung für die Triggers-Integration, die ursprünglich auf der oAUTH-Authentifizierung basierte und für den Zugriff auf die Pipeline eingerichtet wurde, wurde geändert und in Adobe I/O verschoben. [Mehr dazu](../../integrations/using/configuring-adobe-io.md)

Weitere Informationen finden Sie auf der Seite [Eingestellte und entfernte Funktionen ](../../rn/using/deprecated-features.md).

**Verbesserungen**

* An der **Client-Konsole** wurden verschiedene Verbesserungen vorgenommen:
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
* Fehlerkorrektur – Es wurde ein Problem im technischen Workflow **Ereignisstatus-Update** behoben: Um die Größe der entsprechenden eingehenden Felder in der Aktivität **Versandstatistiken** anzupassen, wurde die Größe von drei Zielfeldern in der Aktivität **Versandstatistiken aktualisieren** von 32 auf 64 Bit geändert. (NEO-11557) Weitere Informationen zum Workflow **Ereignisstatus-Update** finden Sie in [diesem Abschnitt](../../workflow/using/message-center--execution-.md).
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