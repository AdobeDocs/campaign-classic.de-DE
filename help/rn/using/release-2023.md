---
product: campaign
title: Campaign Classic-Versionen 2023
description: Weiterführende Informationen zu Campaign Classic-Versionen 2023
feature: Release Notes
role: User
level: Beginner
exl-id: 8ed11e96-9f23-4e2e-bae2-25c51cfb549a
source-git-commit: f39dc6077a7ddc3fb9b53d4082c08e65e7683f10
workflow-type: tm+mt
source-wordcount: '2337'
ht-degree: 97%

---

# Versionen 2023{#release-2023}

## Version 7.3.5 – Build 9368 {#release-7-3-5}

[!BADGE Eingeschränkte Verfügbarkeit]{type=Neutral url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=de#rn-statuses" tooltip="Eingeschränkte Verfügbarkeit"}

_5. Dezember 2023_

### Verbesserungen bei der Sicherheit  {#release-7-3-5-security}


* Mit Campaign Classic v7.3.5 wurde der Authentifizierungsprozess verbessert und sicherer gemacht. Technische Benutzende sollten sich jetzt über das Adobe Identity Management System (IMS) mit Campaign verbinden. Erfahren Sie in [dieser Technote](../../technotes/using/ims-migration.md), wie Sie Ihre vorhandenen technischen Konten migrieren können.

* Darüber hinaus empfiehlt Adobe Campaign im Rahmen der Bemühungen, die Sicherheit und den Authentifizierungsprozess zu verbessern, dringend, den Authentifizierungsmodus für Endbenutzende von der nativen Authentifizierung mit Login/Passwort auf das Adobe Identity Management System (IMS) zu migrieren. Erfahren Sie in [diesem technischen Hinweis](../../technotes/using/migrate-users-to-ims.md), wie Sie Ihre Benutzenden migrieren können.

* Wenn jetzt ein Web-Formular den Status **Veröffentlichung ausstehend** hat, wird es nicht automatisch live geschaltet. Um Sicherheitsprobleme zu vermeiden, muss es veröffentlicht werden, bevor es **online** und über die Web-Formular-URL in einem Webbrowser abrufbar ist. [Weitere Informationen](../../web/using/publishing-a-web-form.md#life-cycle-of-a-form)

### Weitere Verbesserungen {#release-7-3-5-other}

Ab dieser Version funktionieren Tracking-Links für bereits gesendete E-Mails während der Aktualisierung weiterhin. [Weitere Informationen](../../platform/using/faq-build-upgrade.md)

### Patches  {#release-7-3-5-patches}

* Fehlerkorrektur – Bei der Verwendung von Daten aus einer Google Big Query-Datenbank und der Aktualisierung von Daten in einer Oracle-Datenbank werden jetzt nicht mehr alle Schlüssel in der temporären Workflow-Tabelle auf `0` gesetzt. (NEO-65091)
* Fehlerkorrektur – Die Ausführung eines Workflows funktioniert jetzt auch dann, wenn zwei Abfragen einer Google Big Query-Datenbank in einer **Vereinigungs**-Workflow-Aktivität kombiniert werden. (NEO-63705)
* Fehlerkorrektur – Benutzende müssen sich jetzt nicht mehr neu authentifizieren, wenn sie in einem Kampagnenbericht auf `Back` klicken. (NEO-65087)
* Fehlerkorrektur – Im Workflow „Datenbankbereinigung“ tritt jetzt kein Fehler mehr auf, wenn ein Versand vor seinen Testsendungen gelöscht wird. (NEO-48114)
* Fehlerkorrektur – Beim Herstellen einer Verbindung zur Client Console tritt jetzt auch bei den neuesten Updates der TLS-Überprüfung kein Verbindungsfehler mehr auf. (NEO-50488)
* Fehlerkorrektur – Bei der HTTP-Proxy-Authentifizierung nach dem Campaign-Postupgrade auf 7.3.1 schlagen jetzt HTTP-Anforderungen in Campaign-Workflows nicht mehr mit `error 407 – proxy auth required is returned` fehl. (NEO-49624)
* Behebung eines zeitweiligen Fehlers bei der GPG-Entschlüsselung in **Skript** Workflow-Aktivitäten. Die entsprechende Fehlermeldung lautete: `gpg: decryption failed: No secret key`. (NEO-50257)
  <!--* Workflow temporary tables now have a primary index in Teradata with a Federated Data Access (FDA) connection. (NEO-62575)-->




## Version 7.3.4 – Build 9364 {#release-7-3-4}

[!BADGE Eingeschränkte Verfügbarkeit]{type=Neutral url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=de#rn-statuses" tooltip="Eingeschränkte Verfügbarkeit"}


>[!CAUTION]
>
>Die Aktualisierung der Client-Konsole ist obligatorisch. Auf dieser [Seite](../../installation/using/installing-the-client-console.md) erfahren Sie, wie Sie Ihre Client-Konsole aktualisieren.
>
>Wenn der [Campaign – Microsoft Dynamics CRM-Connector](../../platform/using/crm-connectors.md) verwendet wird, müssen sowohl die Marketing- als auch die Mid-Sourcing-Server mit diesem neuen Build aktualisiert werden.

_7. September 2023_

### Verbesserungen bei der Sicherheit  {#release-7-3-4-security}

* Die Sicherheit in IMS-APIs wurde verbessert. Kundensensible Informationen (d. h. Zugriffstoken) wurden aus den URL-Parametern entfernt. Diese Anmeldeinformationen werden jetzt in der Post-Daten- oder Autorisierungs-Kopfzeile gesendet, um einen sichereren Kommunikationsprozess zu gewährleisten. (NEO-63045)
* Die Sicherheit von Web-Apps wurde verbessert, um DDoS-Angriffe zu verhindern. (NEO-50757)
* Die Sicherheit wurde verbessert, um zu verhindern, dass personenbezogene Daten in den Web-Protokollfehlern offengelegt werden. (NEO-46827)
* Die Sicherheit wurde optimiert, um zu verhindern, dass das Sicherheits-Token in die URL der Campaign-Startseite aufgenommen wird. (NEO-38519)

### Aktualisierungen zur Kompatibilität  {#release-7-3-4-compat}

* Tomcat wurde auf Version 8.5.91 aktualisiert
* Die Bibliothek „libexpat“ wurde auf Version 2.5.0 aktualisiert, um die Sicherheit zu verbessern. (NEO-51023)

### Verbesserungen {#release-7-3-4-improvements}

* Der Parameter „MaxWorkingSetMb“ in der Server-Konfigurationsdatei (serverConf.xml) wurde geändert, um die Speicherzuordnung für Sendungen zu optimieren. (NEO-49204)
* Das externe BigQuery-Konto wurde um neue Optionen zur Einrichtung des GCloud-SDK erweitert. (NEO-63879) [Mehr dazu](../../installation/using/configure-fda-google-big-query.md#google-external)
* Es wurde ein neuer `cusHeader`-Abschnitt zur Server-Konfigurationsdatei (serverConf.xml) hinzugefügt. Damit können benutzerdefinierte Kopfzeilen hinzufügt werden, wenn eine Datei von einem externen Server hochgeladen wird. (NEO-58339) [Mehr dazu](../../installation/using/the-server-configuration-file.md#cusheaders).
* Die Verwaltung des Trackinglogs wurde verbessert, um negative IDs für lastMsgId zu vermeiden. Es wurde von int32 in int64 geändert. (NEO-52290)
* Der native Mid-Sourcing (Versandstatistiken)-Workflow wurde hinzugefügt. Dieser neue Workflow synchronisiert Versandstatistikdaten (nms:deliveryStat) von der Mid- bis zur Marketing-Instanz. (NEO-36802)

### Patches {#release-7-3-4-patches}

* Fehlerkorrektur – Beim Stellen einer Service-Anfrage vor der IMS-Anmeldung, bei der die Authentifizierung des Service-Anfrage-Aufrufs mit einem Service-Token erfolgte, tritt nun kein Problem mehr auf. (NEO-64903)
* Fehlerkorrektur – Bei der Verwendung des Editors für digitale Inhalte gibt es jetzt kein Regressionsproblem mehr, das zu Problemen beim Scrollen führen konnte. (NEO-64671, NEO-59256)
* Fehlerkorrektur – Beim Einfügen von Inhalten aus Excel in den Digital Content Editor tritt nun kein Regressionsproblem mehr auf. (NEO-63287)
* Fehlerkorrektur – Webapps werden jetzt im Kompatibilitätsmodus v5 korrekt angezeigt. (NEO-63174)
* Fehlerkorrektur – Benutzende ohne Administratorrechte können jetzt WebAnalytics-Sendungen senden. (NEO-62750)
* Fehlerkorrektur: Browser können jetzt zusätzliche Leerzeichen hinzufügen, wenn bedingte Inhalte in einem Versand verwendet werden. (NEO-62132)
* Fehlerkorrektur – Die Berechnung aktiver Kontakte funktioniert jetzt im Abrechnungs-Workflow korrekt, wenn Zielschemata verwendet werden, die mit mehreren Protokollschemata verknüpft sind. (NEO-61468)
* Fehlerkorrektur: Es tritt kein Fehler mehr auf, der das Scrollen beim Bearbeiten des Inhalts eines Versands verhinderte. (NEO-61364)
* Fehlerkorrektur: Es wird kein Pop-up-Fenster mehr geöffnet, wenn auf ein Bild im E-Mail-Inhaltseditor geklickt wird. (NEO-60752)
* Fehlerkorrektur: Sonderzeichen im HTML-Inhalt eines Versands werden jetzt in mehreren Browsern korrekt codiert. (NEO-60081)
* Fehlerkorrektur – Bei der Verwendung der Workflow-Aktivität inSMS tritt jetzt kein Synchronisierungsproblem mehr auf. (NEO-59544)
* Fehlerkorrektur – Bei der Verwendung des Big Query-Connectors mit Datum-/Uhrzeit-Feldern treten jetzt keine Fehler mehr auf. (NEO-59502, NEO-49768)
* Fehlerkorrektur – Kumulative Versandberichte können jetzt problemlos verwendet werden. (NEO-59211)
* Fehlerkorrektur – Bei der Freigabe von Zielgruppen mit dem People Core Service treten nun keine Fehler mehr auf. (NEO-58637)
* Fehlerkorrektur – Die Mirrorseite eines Versands wird jetzt korrekt angezeigt. (NEO-58325)
* Fehlerkorrektur – Der XtkLibrary.Right() xtk-Ausdruck funktioniert jetzt. (NEO-57870)
* Fehlerkorrektur – Das Stilattribut des Body-Tags wird jetzt beim Hochladen eines Bildes im Digital Content Editor nicht mehr geändert. (NEO-57697)
* Fehlerkorrektur – Bei der Durchführung von Batch-Exporten mit der CRM-Connector-Aktivität treten jetzt keine Probleme mehr mit Sonderzeichen auf. (NEO-54300)
* Fehlerkorrektur – Die Massenladung funktioniert jetzt mit Datentypen vom Typ „Zeichenfolge“ auch dann, wenn eine Aktivität zum Laden von Daten und der Big Query-Connector verwendet wird. (NEO-53748)
* Fehlerkorrektur – Der Cache-Schlüssel verursacht nun keine Probleme mehr bei der Darstellung von Angeboten. (NEO-51516, NEO-49995)
* Fehlerkorrektur – Beim Versand eines Briefpost-Versands mit targetMapping mit Genehmigungen tritt jetzt kein Validierungsfehler mehr auf. (NEO-50758)
* Fehlerkorrektur – Die Versand-Performance wird jetzt nicht mehr durch ein Problem bei der Abfrageverwaltung beeinträchtigt. (NEO-49991)
* Fehlerkorrektur – Bei der Verwendung von externen Konten in Kampagnen-Workflow-Versandaktivitäten tritt kein Fehler mehr auf, der zu Konfigurationsproblemen mit externen Konten führen konnte. (NEO-49959)
* Fehlerkorrektur – Beim Versand von Push-Benachrichtigungen treten keine Performance-Probleme mehr auf. (NEO-49953)
Fehlerkorrektur – Japanische Zeichen werden beim Exportieren von Berichten jetzt korrekt angezeigt (NEO-49308).
* Fehlerkorrektur – Der Tomcat-Fehlerbericht zeigt jetzt nicht mehr allzu viele Fehlerdetails an. (NEO-49029)
* Fehlerkorrektur – Bei der Verwendung einer großen Anzahl von Angeboten tritt nun kein Versandfehler mehr auf. (NEO-48807)
* Fehlerkorrektur – Die Workflow-Aktivität **Daten-Update** funktioniert jetzt ordnungsgemäß. (NEO-48140)
* Fehlerkorrektur – Klick-Tracking-Daten können jetzt für Sendungen auch mit einem externen Konto synchronisiert werden, das sich von der E-Mail-Adresse unterscheidet.(NEO-47277)
* Fehlerkorrektur – Trackinglogs in Echtzeit können jetzt in der Marketing-Instanz von Message Center synchronisiert werden. (NEO-42540)
* Fehlerkorrektur – Das Workspace-Präfix für Snowflake-Datenbanktabellen wird jetzt im Erkennungsfenster eines Schemas angezeigt. (NEO-40297)
* Fehlerkorrektur – `<img-amp>`-Tags können jetzt in E-Mail-Inhalten verwendet werden. (NEO-38685)
* Fehlerkorrektur – Der Archivierungs-Workflow von Message Center schlägt jetzt bei Verwendung eines HTTP-Relais nicht mehr fehl. (NEO-33783)
* Fehlerkorrektur – Schriftname- und -größe werden jetzt im E-Mail-Inhaltseditor richtig angezeigt. (NEO-61342)

## Version 7.3.3 – Build 9359 {#release-7-3-3}

[!BADGE Eingeschränkte Verfügbarkeit]{type=Neutral url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=de#rn-statuses" tooltip="Eingeschränkte Verfügbarkeit"}

>[!AVAILABILITY]
>
>Für diese Version ist ein spezifisches Patch-Upgrade von Campaign v7.3.3.IMS verfügbar, wenn kein anderer Patch auf Ihre Umgebung angewendet wurde. Es bringt [Sicherheitsaktualisierungen für das Adobe Identity Management System (IMS) aus v7.3.5](#release-7-3-5-security) in bestehende v7.3.3-Umgebungen ein.


_20. März 2023_


### Sicherheitsverbesserung {#release-7-3-3-security}

* Um die Sicherheit zu verbessern, wurde Tomcat von Version 8.5.81 auf 8.5.85 aktualisiert. (NEO-56936)


### Verbesserungen {#release-7-3-3-improvements}

* Der Abrechnungs-Workflow wurde verbessert, um die Performance zu optimieren. (NEO-47658)
* Der Tracking-Workflow wurde verbessert, um die Performance bei hoher Versandgröße zu optimieren. (NEO-45064)
* Die Tracking-Verwaltung wurde verbessert, um mögliche Probleme mit dynamischen Parametern in URLs zu beheben. Die Tracking-Verwaltung V3 verarbeitet jetzt URLs vom Typ AJAX (mit Parametern nach „#“) und verhindert, dass Drittanbieterprogramme Tracking-URLs ändern. Um diese Änderung anzuwenden, müssen Sie sich an Adobe wenden. (NEO-46535)
* Ab dieser Version funktionieren Tracking-Links für bereits gesendete E-Mails während der Aktualisierung weiterhin. [Weitere Informationen](../../platform/using/faq-build-upgrade.md)

<!--To apply this change, the marketing, tracking and mid servers need to be updated to 7.3.3. To enable the new tracking management mode, set the `emailLinksVersion` parameter to '3' in the configuration file of the marketing server. (NEO-46535)-->

>[!CAUTION]
>
>Die Aktualisierung der Client-Konsole ist obligatorisch. Auf dieser [Seite](../../installation/using/installing-the-client-console.md) erfahren Sie, wie Sie Ihre Client-Konsole aktualisieren.

### Patches {#release-7-3-3-patches}

* Der Versand von Push-Benachrichtigungen für iOS-Testsendungen von der Kontrollinstanz (Transaktionsnachrichten-Kontext) ist jetzt problemlos möglich. (NEO-54713)
* Das Scrollen in der Registerkarte **Bearbeiten** des Digital Content Editor (DCE) ist jetzt problemlos möglich. (NEO-54474)
* Jetzt können zwei Anreicherungsaktivitäten bei der Verknüpfung dieselbe Namenskennung verwenden, ohne dass die zweite Anreicherungsaktivität die Links der ersten verwendet. (NEO-48851)

## Version 7.3.2 – Build 9356 {#release-7-3-2}

[!BADGE Eingeschränkte Verfügbarkeit]{type=Neutral url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=de#rn-statuses" tooltip="Eingeschränkte Verfügbarkeit"}


>[!AVAILABILITY]
>
>Für diese Version ist ein spezifisches Patch-Upgrade von Campaign v7.3.2.IMS verfügbar, wenn kein anderer Patch auf Ihre Umgebung angewendet wurde. Es bringt [Sicherheitsaktualisierungen für das Adobe Identity Management System (IMS) aus v7.3.5](#release-7-3-5-security) in bestehende v7.3.3-Umgebungen ein.

_21. November 2022_

### Aktualisierungen zur Kompatibilität {#release-7-3-2-compat}

* Adobe Campaign ist jetzt mit PostgreSQL 14 kompatibel. Weiterführende Informationen befinden sich in dieser [Technote](../../technotes/using/tech-stack-upgrade.md).

* Nach dem Auslaufen von Microsoft Internet Explorer 11 verwendet die HTML-Render-Engine für Dashboards in der Client-Konsole nun Edge Chromium. (NEO-20741)

Weiterführende Informationen finden Sie in der [Campaign-Kompatibilitätsmatrix](../../rn/using/compatibility-matrix.md#RDBMSservers).

>[!CAUTION]
>
>Die Aktualisierung der Client-Konsole ist obligatorisch. Auf dieser [Seite](../../installation/using/installing-the-client-console.md) erfahren Sie, wie Sie Ihre Client-Konsole aktualisieren.

### Verbesserungen {#release-7-3-2-improvements}

* Der Google BigQuery-Connector unterstützt boolesche Felder jetzt uneingeschränkt. (NEO-49181)
* Sie können jetzt die Gültigkeitsdauer der IMS-Cookies im Abschnitt `Configuration for the redirection service` der Datei “serverConf.xml” konfigurieren. Dies gilt für die folgenden Cookies: `uuid230`, `nllastdelid` und `AMCV_` (NEO-42541)
* Die IP-Adresse kann jetzt in der &quot;/r/test&quot;-Anfrage ausgeblendet werden, indem `showSourceIP` im Umleitungsknoten der Datei &quot;serverConf.xml&quot; auf &quot;false&quot; festgelegt wird. [Weitere Informationen](../../installation/using/the-server-configuration-file.md#redirection-redirection)(NEO-46656)
* Ab dieser Version funktionieren Tracking-Links für bereits gesendete E-Mails während der Aktualisierung weiterhin. [Weitere Informationen](../../platform/using/faq-build-upgrade.md)


### Eingestellte Funktionen  {#release-7-3-2-deprecated}

* Social-Media-Marketing mit Facebook wird jetzt nicht mehr unterstützt. Sie können die Integration von X (früher bekannt als Twitter) verwenden, um in den sozialen Medien zu posten, oder in Zusammenarbeit mit Adobe einen benutzerdefinierten Kanal zu erstellen.
* ACS-Connector (Prime-Angebot) wird jetzt nicht mehr unterstützt. Sie können die Export-/Importfunktionen von Campaign verwenden, um Daten in beide Produkte einzufügen und sie aus ihnen zu extrahieren.

Weitere Informationen finden Sie auf der Seite [Eingestellte und entfernte Funktionen](deprecated-features.md).

### Sonstige Änderungen   {#release-7-3-2-other}

<!--* Web logs have been improved: `logonEscalation` warnings are now only displayed for users with admin privileges. (NEO-47167)-->
* Um Fehler zu vermeiden, wird der Workflow zum **Erfassen von Daten für den Heatmap-Service** (collectDataHeatMapService) jetzt standardmäßig angehalten. (NEO-33959)
* Es wurden verschiedene Verbesserungen implementiert, um die CPU-Auslastung für das Kampagnen-Dashboard zu optimieren. (NEO-46417)
* Um Abstürze zu verhindern, wurde die JS-Methode loadLibraryDebug entfernt. (NEO-46968)
* Die verbleibenden Verweise auf die log4j-Bibliothek wurden aus der Campaign-Installation unter Windows entfernt. (NEO-44851)

### Patches {#release-7-3-2-patches}

* Fehlerkorrektur: Die Workflow-Option **Ausgewählte Zeilen zusammenführen** kann jetzt verwendet werden. (NEO-48488)
* Fehlerkorrektur: Der Versandindikator **Erfolg** wird jetzt korrekt aktualisiert, wenn Adobe Campaign Enhanced MTA verwendet wird. (NEO-50462)
* Fehlerkorrektur: Nach dem Zurücksetzen der Inhaltsvalidierung eines E-Mail-Versands kann dieser Inhalt jetzt erneut validiert werden. (NEO-44259)
* Fehlerkorrektur: Die Schaltfläche **Versandvalidierung** wird jetzt angezeigt. (NEO-47547)
* Fehlerkorrektur: Bei umfangreichem HTML-Code in der HTML-Tabelle eines Versands tritt jetzt kein Performance-Problem mehr auf. (NEO-47440)
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
