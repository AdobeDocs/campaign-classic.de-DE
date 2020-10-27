---
title: Aktuelle Version
description: Aktuelle Version von Campaign Classic Anmerkungen
page-status-flag: never-activated
uuid: 269d590c-5a6d-40b9-a879-02f5033863fc
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rns
content-type: reference
topic-tags: latest-release-notes
discoiquuid: 5df34f55-135a-4ea8-afc2-f9427ce5ae7b
translation-type: tm+mt
source-git-commit: fe7ce92bde3405fed3429475cdd5681e5837876f
workflow-type: tm+mt
source-wordcount: '1824'
ht-degree: 4%

---


# Aktuelle Version{#latest-release}

Auf dieser Seite werden neue Funktionen, Verbesserungen und Fehlerbehebungen der **neuesten Campaign Classic Release Candidate-Version** Liste.

Campaign Classic Gold Standard Version (neueste GA Version), [siehe diese Seite](../../rn/using/gold-standard.md).

## ![](assets/do-not-localize/blue_2.png) Version 20.3.1 – Build 9228 {#release-20-3-1-build-9228}

_27. Oktober 2020_

**Neue Funktionen**

<table> 
<thead>
<tr> 
<th> <strong>Verbesserungen an iOS-Push-Benachrichtigungen</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>Wenn Sie Ihre mobile App mit Kampagne integrieren, müssen Sie Ihre Kommunikation mit dem Apple Push Notification Service (APNs) sichern. Sie können die zertifikatbasierte oder Token-basierte Authentifizierung verwenden.
</p>
<p>Diese beiden Authentifizierungsmodi sind jetzt für mobile iOS-Apps in Campaign Classic verfügbar:
</p>
<ul> 
<li><p>Token-basierte Authentifizierung (empfohlen): dieser Authentifizierungsmodus basiert auf einer .p8-Datei. Dieser Authentifizierungsmodus ist schneller, da jede Anforderung an APNs das Token enthält. <a href="https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_token-based_connection_to_apns">Mehr dazu</a></p></li>
<li><p>Zertifikatbasierte Authentifizierung: dieser Authentifizierungsmodus basiert auf einer .p12-Datei. Für jede App ist ein separates Zertifikat erforderlich. Dieses Zertifikat wird von Apple über Ihr Entwicklerkonto bereitgestellt. <a href="https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_certificate-based_connection_to_apns">Mehr dazu</a></p></li> 
</ul>
<p>Erfahren Sie, wie Sie den Authentifizierungsmodus in Kampagne in der <a href="../../delivery/using/configuring-the-mobile-application.md">ausführlichen Dokumentation</a>auswählen.</p>
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
<td> <p>Android-Push-Benachrichtigungen wurden verbessert, um die FCM HTTP v1 API für die Authentifizierung von Android-Push-Kanälen zu unterstützen. </p>
<p>Mit der neuen unterstützten API-Version können Sie jetzt FCM-Benachrichtigungsmeldungen senden, die verbesserte Rich-Push-Nachrichten-Funktionen bieten. <a href="https://firebase.google.com/docs/cloud-messaging/migrate-v1">Mehr dazu</a></p> 
<p>Informationen zum Konfigurieren der FCM HTTP v1 API für Android in Adobe Campaign finden Sie in <a href="../../delivery/using/configuring-the-mobile-application-android.md">diesem Abschnitt</a> .</p>
</td> 
</tr> 
</tbody> 
</table>

**Verbesserungen bei der Sicherheit**

* Sicheres Laden von Bibliotheken: Zum Schutz vor DLL-Preloading-Angriffen lädt Kampagne jetzt Windows-DLLs nur noch vom Windows-Standardsystem-DLL-Pfad, während der Kampagne Client (nlclient) geladen wird. [Weitere Informationen](https://support.microsoft.com/en-us/help/2389418/secure-loading-of-libraries-to-prevent-dll-preloading-attacks) (NEO-24147)
* Es wurde ein Sicherheitsproblem behoben, um den Schutz gegen SSRF-Angriffe (Server Side Request Forgery) zu verbessern. (NEO-25661)
* Es wurde ein Fehler behoben, der beim Bearbeiten von GDPR-Datenschutzanforderungen auftrat und verhindert hat, dass Datensätze aus benutzerdefinierten Tabellen mit einer Beziehung der zweiten Ebene zur Empfänger-Tabelle gelöscht wurden. (NEO-25967)
* Es wurde ein Sicherheitsproblem mit API-Aufrufen behoben, die von Nicht-Admin-Benutzern beim Synchronisieren von Adobe Experience Manager-Vorlagen ausgeführt wurden. (NEO-23487)

**Kompatibilitätsaktualisierungen**

Die folgenden Systeme werden jetzt von Campaign unterstützt:
* iOS 14
* PostgreSQL 12
* CentOS/RedHat 8
* MSSQL2019

Learn more in the [Campaign Compatibility matrix](../../rn/using/compatibility-matrix.md).

**Eingestellte Funktionen**

Die folgenden Funktionen sind in Version 20.3 veraltet:

* Die demdex-Domäne, die zum Importieren und Exportieren von Audiencen in das Adobe Experience Cloud verwendet wird, wird nicht mehr unterstützt. Wenn Sie die demdex-Domäne für Ihre Import/Export-Externe Konti verwenden, müssen Sie Ihre Implementierung entsprechend anpassen. [Mehr dazu](../../integrations/using/configuring-shared-audiences-integration-in-adobe-campaign.md)
* Die Trigger-Integrationsauthentifizierung, die ursprünglich auf der Einrichtung der AUTH-Authentifizierung für den Zugriff auf die Pipeline beruhte, wurde jetzt geändert und in die Adobe I/O verschoben. [Weitere Informationen](../../integrations/using/about-triggers.md)

Weitere Informationen finden Sie auf der Seite [Veraltete und entfernte Funktionen](../../rn/using/deprecated-features.md).

**Verbesserungen**

* An der **Client-Konsole** wurden verschiedene Verbesserungen vorgenommen:
   * Um eine Inkompatibilität mit einigen GPO-Regelbeschränkungen für Internetsicherheit zu vermeiden, wurde der Anmeldebildschirm der Kampagne-Client-Konsole durch ein integriertes Windows-Standardformular ersetzt.
   * Es wurde ein Problem behoben, das beim Kopieren/Einfügen von Aktivitäten in einen Workflow mit der 64-Bit-Client-Konsole auftrat. (NEO-27635)
   * Im Menü **Info** wurden Informationen hinzugefügt, um 64- und 32-Bit-Konsolen zu unterscheiden.
* Die Workflow-ID wird jetzt beim Wiederaufnehmen eines Workflows in den Protokollen angezeigt, sodass Sie besser erkennen können, welcher Workflow fortgesetzt wurde.
* Es wurde ein neues ständiges Cookie eingeführt: nllastdelid. Dieses Cookie (außer UUID230) speichert deliveryId. Wenn kein Sitzungs-Cookie vorhanden ist, werden Breitbandinformationen aus der in diesem Cookie vorhandenen deliveryId entnommen.
Diese Änderung behebt ein Problem, das beim Beenden der Browsersitzung aufgetreten ist: das Sitzungs-Cookie mit deliveryId und extenlogId wurde gelöscht. Ohne deliveryId konnten keine Broadlog-Informationen gefunden werden, und bei einer permanenten Verfolgung (letzter Versand) fehlten die Verfolgungstabelle-Informationen.
Learn more about cookies in [this section](../../platform/using/privacy-and-recommendations.md#cookies).
* Verbesserte Leistung beim Durchsatz von Versänden mit hohem Volumen mit dem Bereitstellungsserver, indem der MTA-Prozess vor dem Senden des Versands neu gestartet wurde.

**Sonstige Änderungen**

* Bei Verwendung des relativen Pfads für SFTP werden keine Zeichen mehr automatisch hinzugefügt `~/` . Bei Bedarf können Sie Ihrem Pfad `~/` Zeichen manuell hinzufügen. Adobe empfiehlt jedoch die Verwendung eines **absoluten Pfads**.
* Die Windows NT-Authentifizierung wurde bei der Konfiguration einer neuen Datenbank mit einem Microsoft SQL Server aus den verfügbaren Authentifizierungsmethoden entfernt. [Mehr dazu](../../installation/using/creating-and-configuring-the-database.md#step-1---selecting-the-database-engine)
* Der Arbeitsablauf zur Datenbankbereinigung wurde für Teradata optimiert, um die Leistung zu verbessern. (NEO-19959)
* Die Fehlermeldung beim Einfügen eines Bildes aus Adobe Target wurde verbessert und der Mandantenname war leer im Externe Konto.
* In den Eigenschaften des Versands wurde die Option E-Mails **[!UICONTROL archivieren]** in **[!UICONTROL E-Mail-BCC]** umbenannt.
* Um die Stabilität zu verbessern, werden alle Abfragen mit ungültigen Knoten jetzt abgelehnt. Wenn Sie die Prüfung deaktivieren und zum vorherigen Verhalten zurückkehren müssen, können Sie XtkSecurity_Disable_QueryCheck auf 0 setzen.

**Technische Entwicklungen**

Tomcat wurde von Version 7 (7.0.103) auf Version 8 (8.5.57) aktualisiert.

Der `tomcat-7` Ordner wird durch einen `tomcat-8` Ordner ersetzt.

Unter Windows sind _is_neolane_setup.vbs_ und _apache_neolane.conf_ jetzt im `conf` Ordner installiert (anstatt `tomcat-7/conf` zuvor).

Unter Linux wird _apache_neolane.conf_ jetzt im `conf` Verzeichnis installiert.

**Korrekturen**

* Es wurde ein Problem behoben, das die Neuberechnung von Versand-Statistiken verhindern konnte.
* Es wurde ein Problem behoben, bei dem beim Hochladen einer CSV-Datei eine Fehlermeldung angezeigt wurde, wenn ein mit einem älteren Build verbundener Campaign Classic 9080 verwendet wurde. (NEO-23218)
* Es wurde ein Fehler behoben, der beim Konfigurieren des Microsoft Dynamics CRM-Assistenten für ein Externe Konto eine Fehlermeldung anzeigen konnte. Dies war auf ein Kompatibilitätsproblem mit der neuesten MS Dynamics CRM API Version zurückzuführen. (NEO-24528)
* Es wurde ein Fehler behoben, der verhinderte, dass Sie mithilfe des CRM-Connectors Nachschlagedatensätze (d. h. Daten aus ausländischen Schlüsseldatensätzen, die mit anderen Tabellen verbunden sind) von Campaign Classic nach Microsoft Dynamics exportieren konnten. (NEO-23864)
* Es wurde ein Fehler behoben, der dazu führte, dass Microsoft Dynamics-Daten nicht abgerufen wurden, wenn die Option **Automatischer Index** im CRM-Connector aktiviert war. (NEO-25981)
* Es wurde ein Problem mit der IMS-Authentifizierung behoben, durch das Verbindungen geöffnet bleiben konnten, selbst wenn sie beendet wurden. Terminierte Verbindungen werden nun automatisch geschlossen, sobald sie beendet sind, um zu vermeiden, dass Verbindungen akkumuliert werden und Systemressourcen verbraucht werden. (NEO-25996)
* Es wurde ein Problem behoben, bei dem keine Fehlermeldung angezeigt wurde, wenn die Synchronisierung von Adobe Experience Manager-Inhalten aufgrund einer Fehlkonfiguration des Externen Kontos (falsches Konto oder Kennwort) für einen Versand fehlschlug. Im Falle eines Fehlers wird jetzt eine Meldung angezeigt, mit der Sie das Problem leichter identifizieren können. (NEO-25586)
* Es wurde ein Problem behoben, das bei der Auswahl des **Aktualisierungsvorgangs** in der Aktivität **Daten** aktualisieren auftrat. Wenn die zu aktualisierenden Daten nicht korrekt waren, wird der Workflow fehlerhaft ausgeführt. Bei falschen Daten schlägt der Workflow nicht fehl, und die Datensätze werden in einer ausgehenden Transition **Ablehnen** gespeichert. (NEO-23794)
* Es wurde ein Fehler behoben, der dazu führte, dass Workflows mit Workflows nicht funktionierten. (NEO-24036)
* Es wurde ein Fehler behoben, der beim Bearbeiten einer Beschreibung der Kampagnenvorlage dazu führte, dass die Schaltfläche **Speichern** beim Einfügen von Symbolen, z. B. japanischen Zeichen, nicht angezeigt wurde. (NEO-27071)
* Es wurde ein Problem behoben, durch das verhindert werden konnte, dass Sie den Tracking-Server im Instanzkonfigurationsassistenten ändern.
* Es wurde ein Fehler behoben, der verhinderte, dass die Beschreibung einer Kampagne oder Kampagnenvorlage gespeichert wurde, wenn vor dem Klicken auf die Schaltfläche **Speichern** auf eine andere Seite des Fensters geklickt wurde. (NEO-27449)
* Es wurde ein Fehler behoben, der dazu führte, dass der Arbeitsablauf für die **Anzahl der aktiven Rechnungsstellungs-Profil** (billingActiveContactCount) nicht funktionierte. Dies kann vorkommen, wenn ein Link für ein berechnetes Feld in einer Schema-Erweiterung ausgeführt wurde. Es wurden große Datenmengen erstellt, wodurch der Datenbank der temporäre Speicherplatz entzogen werden könnte. (NEO-24062)
* Es wurde ein Problem mit der Aktivität zum Laden von **Daten (Datei)** behoben, durch das verhindert werden konnte, dass japanische Zeichen aus TXT- und CSV-Dateien importiert werden, wenn sie am Dateiende positioniert wurden. (NEO-24957)
* Es wurde ein Problem mit kontinuierlichen Versänden behoben, durch die verhindert werden konnte, dass die **Felder &quot;Analyse gestartet** &quot;und &quot; **Analyse abgeschlossen** &quot;ordnungsgemäß ausgefüllt wurden. (NEO-20755)
* Es wurde ein Fehler behoben, der beim Versuch, nach einer Abfrage auf einem anderen Schema als dem **Empfänger** SMS-Nachrichten Vorschau, eine Fehlermeldung anzeigen konnte (nms:Empfänger). (NEO-27517)
* Es wurde ein Problem bei der Verwendung des Snowflake FDA Connectors behoben. Ein Benutzer mit Zugriffsrechten auf die Snowflake-FDA konnte keine Abfrage auf einem Snowflake-Schema ausführen. In den Protokollen wurde ein Fehler des Typs &quot;Kennwort nicht gefunden&quot;angezeigt. (NEO-23851)
* Es wurde ein Problem bei der Verwendung eines FDA Connectors behoben, das auftrat, wenn der Name des verknüpften FDA-Schemas eine Teilzeichenfolge des Elementnamens des aktuellen Schemas war. Dies trat beispielsweise auf, wenn das Schema FDA &quot;cust&quot;lautete und eines der Elemente im Empfänger-Schema &quot;customer&quot;lautete. Beim Abrufen der Spalte innerhalb des &quot;customer&quot;-Elements und Hinzufügen einer Spalte aus dem Schema &quot;cust&quot;-FDA fehlte der Wert für die lokale Spalte. (NEO-20193)
* Es wurde ein Fehler in Workflows behoben, der auftrat, wenn Datensätze aus einer externen Datenbank abgerufen und in die Kampagne-Datenbank eingefügt wurden. (NEO-26359)
* Es wurde ein Fehler im technischen Arbeitsablauf zum Status **des Ereignisses** aktualisieren behoben: Um die Größe der eingehenden entsprechenden Felder in der Aktivität für die **Versand-Statistik** anzupassen, wurde die Größe von drei Zielfeldern in der Aktivität für die Statistik **des Versands** aktualisieren von 32 auf 64 Bit geändert. (NEO-11557) Erfahren Sie mehr über den Arbeitsablauf zum Status **von** Ereignissen in [diesem Abschnitt](../../workflow/using/message-center--execution-.md).
* Es wurde ein Fehler im **Meldungscenter-Bericht zum** Ereignis-Verlauf behoben, der Skriptfehler verursachte, wenn versucht wurde, Filter anzuwenden, und den Filter nach Datumsbereich unmöglich machte. (NEO-23365)
* Korrektur eines Interferenzfehlers zwischen den Technischen Workflows für **Kampagnen** (operationMgt) und **Vorschau** (Prognose). Dies trat auf, wenn geplante Versand im Status &quot;Zielgruppe bereit&quot;oder &quot;Bereitwillig bereitstehen&quot;blieben. (NEO-20819)
* Es wurde ein XML-Parsing-Problem behoben, das auftrat, wenn der XML-Bezeichner nicht im Feld mdata in xtkOperator vorhanden war. Es verursachte einen Fehler nach der Aktualisierung. (NEO-26113)
* Es wurde ein Problem bei der Verwendung der **File Transfer** -Aktivität behoben, die mit einem in SSL verschlüsselten Azurblauen Externe Konto verknüpft ist und bei dem die Verbindung mit HTTP statt mit HTTPS hergestellt wurde. (NEO-26720)
* Es wurde ein Problem bei der MSSQL-Datenbank behoben, bei dem während des Bereinigungs-Workflows ein Fehler beim Vorgang up_updatestats aufgetreten ist.
* Es wurde ein Absturz behoben, der beim Herunterfahren des Webprozesses auftrat, wenn Interaktionsanforderungen weiterhin verarbeitet wurden. (NEO-26447)
* Es wurde ein Problem behoben, bei dem die Funktion **NoNull** in Oracle DB nach der Aktualisierung 9032 nicht mehr funktionierte. (NEO-26488)
* Es wurde ein Problem behoben, bei dem der Verfolgungsarbeitsablauf nach der Aktualisierung 9171 fehlschlug, wenn das LINEV2-Paket ohne das Message Center-Paket installiert wurde.
* Es wurde ein Problem mit der Skalierbarkeit behoben, bei dem der Verbindungspool nicht auf die gewünschte Anzahl von Verbindungen erhöht werden konnte, da die Datenbankverbindungszeichenfolge für das Attribut &quot;APP&quot;am Ende einen ungültigen Wert erhielt. (NEO-25105)
* Es wurde ein Problem auf Proxykonfigurationsebene behoben, durch das Sie sich nach dem letzten Windows 10-Update nicht bei Adobe Campaign anmelden konnten. (NEO-27813)
* Es wurde ein Fehler behoben, der dazu führte, dass unerwünschte URLs in den gesendeten E-Mails angezeigt wurden, nachdem HTML-Vorlagen importiert wurden, die Verfolgungslinks enthielten. (NEO-25909)
* Es wurde ein Fehler behoben, der dazu führte, dass der Server abstürzte, wenn die Daten zur Zielgruppe des Rest einer **geteilten** Aktivität in einem Workflow angezeigt wurden.
* Ein Serverabsturzproblem wurde behoben, das Speicherkorruption beim Reinigen des Ausdruck-Parsers verhinderte. (NEO-26856)
* Es wurde ein Problem in der Aktivität Anreicherung behoben, bei dem Nicht-Admin-Benutzer Instanzvariablen definiert haben. (NEO-25653)