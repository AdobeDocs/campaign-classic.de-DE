---
product: campaign
title: Technische Workflows
description: Erfahren Sie mehr über die technischen Workflows, die mit Campaign Classic-Packages verfügbar sind
feature: Workflows
hide: true
exl-id: 9aed2665-cd4b-419c-b9f2-ea04fc1d8f01
TQID: https://experienceleague.adobe.com/XyvGCXDK-0pAX09kPyfGkZFTITlQRuMN0N-Yee-06EM
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: a075b2c1-7748-4328-b7f6-343aa314616aid: c5474392-5419-4296-9e41-f6f4ce4f6e9b
subfeature_v2: id: e3988c18-3cfa-4f16-b812-ac2d2b1056faid: ee25c34b-ea50-427b-9369-ba0a160f7d70
topic_v2: id: aa2f3246-cb95-4b30-8899-fdf7d73550ccid: eddd9b14-83bd-4ff4-9072-54a4a484abb7id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 1733
ht-degree: 80%

---

# Technische Workflows{#about-technical-workflows}



## Über technische Workflows {#overview}

Die in diesem Abschnitt beschriebenen Workflows werden mit den verschiedenen in Adobe Campaign integrierten Paketen installiert. Diese Pakete und die damit verbundenen technischen Workflows hängen von Ihrer Lizenzvereinbarung ab. Integrierte Packages werden in [diesem Abschnitt](../../installation/using/installing-campaign-standard-packages.md) beschrieben.

Standardmäßig sind technische Workflows in einem Unterordner des folgenden Knotens verfügbar: **[!UICONTROL Administration]** > **[!UICONTROL Betreibung]** > **[!UICONTROL Technische Workflows]**.

Technische Workflows können nur von Benutzern mit Administratorrechten gestartet und geändert werden. Weiterführende Informationen zu Berechtigungen finden Sie in diesem [Abschnitt](../../platform/using/access-management-groups.md#default-groups).

>[!NOTE]
>
>Die mit dem Message Center verbundenen technischen Workflows sind standardmäßig im Knoten **[!UICONTROL Administration]** > **[!UICONTROL Betreibung]** > **[!UICONTROL Message Center]** > **[!UICONTROL Technische Workflows]** verfügbar.

Weiterführende Informationen zur Verfolgung technischer Workflows finden Sie in [diesem Abschnitt](monitoring-technical-workflows.md).

## Liste der technischen Workflows {#list-technical-workflows}

| Technischer Workflow | Package | Beschreibung |
|------|--------|-----------|
| **Alias-Datenbereinigung** (aliasCleansing) | Versand | Vereinheitlicht Aufzählungswerte. Er wird standardmäßig jeden Tag um 3 Uhr morgens ausgelöst. |
| **Abrechnung** (billing) | Versand | Dieser Workflow übermittelt per E-Mail den Aktivitätsbericht des Systems an den fakturierungsverantwortlichen Benutzer (&#39;billing&#39;). Er wird am 25. jedes Monats in der Marketing-Instanz ausgelöst. |
| **Berechnung der Twitter-Statistiken** (statsTwitter) | Soziale Netzwerke (Social Marketing) – Nur Campaign v7 | Dieser Workflow berechnet Statistiken im Zusammenhang mit Retweets und Besuchen auf X (früher bekannt als Twitter). |
| **Aufträge bei Kampagnen** (operationMgt) | Marketing-Kampagnen (Campaign) | Verwaltet Vorgänge in Marketing-Kampagnen (Zielgruppenbestimmung, Dateiextraktion etc.). Außerdem werden Workflows für wiederkehrende und periodische Kampagnen erstellt. |
| **Erfassen von Daten für den HeatMap-Service** (collectDataHeatMapService) | Standardmäßig installiert | Dieser Workflow ruft die für den HeatMap-Service erforderlichen Daten ab. |
| **Erfassen von Datenschutzanfragen** (collectPrivacyRequests) | Datenschutzbestimmung | Mit diesem Workflow werden die in Adobe Campaign gespeicherten Empfängerdaten abgerufen und auf dem Bildschirm zur Datenschutzanfrage für den Download bereitgestellt. |
| **Kostenberechnung** (budgetMgt) | Marketing-Kampagnen (Campaign) | Dieser Workflow berechnet Ausgaben- und Kostenposten für Budgets, Pläne, Programme, Kampagnen, Sendungen und Aufgaben. |
| **Datenbankbereinigung** (cleanup) | Versand | Dieser Workflow ist der Datenbankwartungs-Workflow: Er führt verschiedene Berechnungen mit Statistiken und Prozessen durch und löscht gemäß der definierten Konfiguration im Bereitstellungsassistenten veraltete Daten aus der Datenbank. Er wird standardmäßig jeden Tag um 4 Uhr morgens ausgelöst. Weitere Informationen dazu finden Sie auf [dieser Seite](../../production/using/database-cleanup-workflow.md#monitoring-campaign-classic). |
| **Löschen von gesperrten LINE-Benutzern** (deleteBlockedLineUsersV2) | LINE-Kanal | Dieser Workflow stellt sicher, dass die Daten der LINE V2-Benutzer gelöscht werden, nachdem sie das offizielle LINE-Konto 180 Tage lang gesperrt haben. |
| **Löschen von Datenschutzanfragedaten** (deletePrivacyRequestsData) | Datenschutzbestimmung | Mit diesem Workflow werden die in Adobe Campaign gespeicherten Empfängerdaten gelöscht. |
| **Versandindikatoren** (deliveryIndicators) | Mid-Sourcing-Plattform | Aktualisiert Trackingindikatoren von Sendungen. Dieser Workflow wird standardmäßig stündlich ausgelöst. |
| **Vorgänge in Diskussionsforen** (newsgroupMgt) | Marketing-Ressourcen (MRM) | Sendet Benachrichtigungen in Diskussionsforen. Sie wird ausgelöst, wenn ein Validierungssignal empfangen wird |
| **Bearbeitungsvorgänge des verteilten Marketings** (centralLocalMgt) | Zentrales/lokales Marketing (verteiltes Marketing) | Führt die Vorgänge im Zusammenhang mit dem Distributed-Marketing-Modul aus. Sie startet die Erstellung lokaler Kampagnen und verwaltet Benachrichtigungen im Zusammenhang mit Bestellungen und der Verfügbarkeit von Kampagnenkits. |
| **Bereinigen von Ereignissen** (webAnalyticsPurgeWebEvents) | Web Analytics-Connectoren | Mit diesem Workflow können Sie jedes Ereignis aus dem Datenbankfeld entsprechend dem im Feld &quot;Lebensdauer&quot; konfigurierten Zeitraum löschen. |
| **Exportieren von Zielgruppen zu Adobe Experience Cloud** (exportSharedAudience) | Integration mit Adobe Experience Cloud | Dieser Workflow exportiert freigegebene Zielgruppen. Diese Zielgruppen können dann in den anderen von Ihnen verwendeten Adobe Experience Cloud-Lösungen genutzt werden. |
| **Prognosen** (forecasting) | Versand | Analysiert die im Planungskalender verzeichneten Sendungen (Erstellung von Planungslogs). Er wird standardmäßig jeden Tag um 1 Uhr morgens ausgelöst. |
| **Berechnung des vollständigen Aggregats (propositionrcp-Cube)** (agg_nmspropositionrcp_full) | Angebotsmodul (interaction) | Dieser Workflow aktualisiert das vollständige Aggregat für den Angebotsvorschlags-Cube. Er wird standardmäßig jeden Tag um 6 Uhr morgens ausgelöst. Dieses Aggregat erfasst die folgenden Dimensionen: Kanal, Versand, Marketing-Angebot und Datum. Der Cube „Angebotsvorschlag“ wird dann zur Erstellung von angebotsbasierten Berichten verwendet. Weitere Informationen zu Cubes finden Sie in [diesem Abschnitt](../../reporting/using/ac-cubes.md). |
| **Identifizierung der konvertierten Kontakte** (webAnalyticsFindConverted) | Web Analytics-Connectoren | Dieser Workflow indexiert die Besucher, die nach einer Remarketing-Kampagne einen Kauf getätigt haben. Die durch diesen Workflow gewonnenen Daten können im Bericht zur Remarketing-Effizienz abgerufen werden (siehe diese Seite). |
| **Importieren von Zielgruppen aus Adobe Experience Cloud** (importSharedAudience) | Integration mit Adobe Experience Cloud | Dieser Workflow ermöglicht den Import von Zielgruppen/Segmenten aus den unterschiedlichen Adobe Experience Cloud-Lösungen in Adobe Campaign. |
| **Bearbeitungsaufträge bezüglich Kampagnensendungen** (deliveryMgt) | Marketing-Kampagnen (Campaign) | Dieser Workflow startet den Versand der validierten Sendungen und die Anschlussvorgänge des Dienstleisters bei externem Versand. Außerdem werden Validierungsbenachrichtigungen und Erinnerungen gesendet. |
| **Bearbeitungsaufträge bezüglich der Dienstleister** (supplierMgt) | Marketing-Kampagnen (Campaign) | Dieser Workflow startet Provider-Vorgänge nach erfolgter Versandvalidierung (E-Mail an den Router und Anschlussvorgang). |
| **Update des LINE V2-Zugriffs-Tokens** (updateLineV2AccessToken) | LINE-Kanal – nur Campaign v7 | Dieser Workflow aktualisiert das Zugriffs-Token auf LINE V2. |
| **Migration von MID zu LineUserID** (MIDToUserIDMigration) | LINE-Kanal | Dieser Workflow erzeugt die Kennung von LINE V2-Benutzern für die Migration von LINE V1 nach LINE V2. |
| **Benachrichtigungen bezüglich Marketing-Ressourcen** (assetMgt) | Marketing-Ressourcen (MRM) | Dieser Workflow verwaltet die Benachrichtigungen bezüglich der Validierung und der Veröffentlichung von Marketing-Ressourcen. |
| **Message Center &lt;external_account_name>** (mcSynch_&lt;external_account_name>) | Kontrolle der Transaktionsnachrichten (Message Center – Kontrolle) | Dieser Workflow: <ul><li>Ruft die Liste der durch die Aktion(en) verarbeiteten Ereignisse ab.</li><li>Wird mit der NmsBroadLogMsg-Tabelle synchronisiert, um die Qualifizierung der Versandnachrichten abzurufen.</li><li>Ruft Ereignis-Versandlogs ab, sobald die Synchronisation mit der NmsBroadLogMsg-Tabelle abgeschlossen ist.</li><li>Wird mit der NmsTrackingUrl-Tabelle synchronisiert, um das Tracking für die Versand-URLs abzurufen.</li><li>Ruft Ereignis-Verfolgungs-URLs ab, sobald die Synchronisation mit der NmsTrackingUrl-Tabelle abgeschlossen ist.</li><li>Ruft alle drei Stunden die E-Mail-Adressen ab, die infolge eines Versands neu in Quarantäne gekommen sind.</li></ul> |
| **Berechnung des vollen Message Center-Aggregats** (agg_messageCenter_full) | Kontrolle der Transaktionsnachrichten (Message Center – Kontrolle) | Dieser Workflow aktualisiert das vollständige Aggregat für den Message Center-Cube. Er wird standardmäßig jeden Tag um 3 Uhr morgens ausgelöst. Dieses Aggregat erfasst die folgenden Dimensionen: Kanal, Datum, Status und Ereignistyp. Der Message Center-Cube wird dann zur Erstellung von ereignisbasierten Berichten verwendet. Weitere Informationen zu Cubes finden Sie in [diesem Abschnitt](../../reporting/using/ac-cubes.md) |
| **Mid-Sourcing (Versandzähler)** (defaultMidSourcingDlv) | Weiterleitung an Mid-Sourcing | Dieser Workflow erfasst Zählinformationen für Sendungen auf dem Mid-Sourcing-Server. Zu den Zählungsinformationen gehören allgemeine Versandindikatoren wie die Anzahl der gesendeten Sendungen usw. Tracking-Informationen wie Öffnungen sind nicht enthalten. Dieser Workflow wird standardmäßig alle zehn Minuten ausgelöst. |
| **Mid-Sourcing (Versand-Logs)** (defaultMidSourcingLog) | Weiterleitung an Mid-Sourcing | Ruft Versandlogs vom Mid-Sourcing-Server ab. Er wird standardmäßig stündlich ausgelöst. |
| **NMAC-Abmeldungsverwaltung** (mobileAppOptOutMgt) | Mobile-App-Kanal | Dieser Workflow aktualisiert die Abmeldungen von Benachrichtigungen auf Mobilgeräten. Er wird alle 6 Stunden zwischen 1 Uhr morgens und Mitternacht ausgelöst. Weitere Informationen finden Sie in [diesem Abschnitt](../../delivery/using/delivery-failures-quarantine.md#push-notification-quarantines). |
| **Benachrichtigung über Angebote** (offerMgt) | Versand | Dieser Workflow stellt validierte Angebote sowie die im Angebotskatalog enthaltenen Kategorien in die Online-Umgebung bereit. |
| **Bereinigung angehaltener Workflows** (cleanupPausedWorkflows) | Versand | Dieser Workflow analysiert pausierte Workflows, deren Schweregrad auf „Normal“ eingestellt ist, sowie Trigger- und Benachrichtigungswarnungen, wenn diese zu lange pausiert wurden. Nach einem Monat werden pausierte technische Workflows bedingungslos angehalten. Standardmäßig wird sie jeden Montag um 5 Uhr morgens ausgelöst. Weitere Informationen finden Sie unter [Handhabung angehaltener Workflows](monitoring-workflow-execution.md#handling-of-paused-workflows). |
| **Datenschutzanfragebereinigung** (cleanupPrivacyRequests) | Datenschutzbestimmung | Mit diesem Workflow werden Dateien mit Zugriffsanfragen gelöscht, die älter als 90 Tage sind. |
| **Verarbeitung von Batch-Ereignissen** (batchEventsProcessing) | Ausführung einer Transaktionsnachricht (Message Center – Ausführung) | Mit diesem Workflow können Sie Batch-Ereignisse in eine Warteschlange stellen, bevor ihnen eine Nachrichtenvorlage zugeordnet wird. |
| **Verarbeitung von Echtzeitereignissen** (rtEventsProcessing) | Ausführung einer Transaktionsnachricht (Message Center – Ausführung) | Mit diesem Workflow können Sie Echtzeitereignisse in eine Warteschlange stellen, bevor ihnen eine Nachrichtenvorlage zugeordnet wird. |
| **Synchronisation von Vorschlägen** (propositionSynch) | Steuerung des Angebotsmoduls durch die Ausführungsinstanz | Dieser Workflow synchronisiert Vorschläge zwischen der Marketing-Instanz und der Ausführungsinstanz, die für Interaktionen verwendet wird. |
| **Abruf von Web-Ereignissen** (webAnalyticsGetWebEvents) | Web Analytics-Connectoren | Dieser Workflow ruft stündlich die Segmente ab, die sich auf das Besucherverhalten einer gegebenen Website beziehen, fügt die Daten zur Adobe Campaign-Datenbank hinzu und startet den Remarketing-Workflow. |
| **Berichtsaggregate** (reportingAggregates) | Versand | Aktualisiert die in Berichten verwendeten Aggregate. Er wird standardmäßig jeden Tag um 2 Uhr morgens ausgelöst. |
| **Übermittlung von Indikatoren und Kampagnenattributen** (webAnalyticsSendMetrics) | Web Analytics-Connectoren | Dieser Workflow ermöglicht es Ihnen, Indikatoren für E-Mail-Kampagnen aus Adobe Campaign über Adobe® Analytics Connector an Adobe Experience Cloud Suite zu senden. Dies betrifft die folgenden Indikatoren: Gesendet (iSent), Öffnungen insgesamt (iTotalRecipientOpen), Gesamtzahl der Empfänger, die geklickt haben (iTotalRecipientClick), Fehler (iError), Abmeldung (Opt-out) (iOptOut). |
| **Lager: Bestellungen und Warnhinweise** (stockMgt) | Marketing-Kampagnen (Campaign) | Dieser Workflow startet die Berechnung der Lagerbestände in den Bestellzeilen und verwaltet Warnschwellen. |
| **Synchronisation von Facebook-Fans** (syncFacebookFans) | Soziale Netzwerke (Social Marketing) – Nur Campaign v7 | Dieser Workflow importiert täglich um 7 Uhr morgens Facebook-Fans in Adobe Campaign. |
| **Synchronisation von Facebook-Seiten** (syncFacebook) | Soziale Netzwerke (Social Marketing) – Nur Campaign v7 | Dieser Workflow synchronisiert täglich um 7 Uhr morgens Facebook-Seiten mit Adobe Campaign. |
| **Synchronisation von Twitter-Seiten** (syncTwitter) | Soziale Netzwerke (Social Marketing) – Nur Campaign v7 | Dieser Workflow importiert täglich um 7 Uhr morgens X-Follower in Adobe Campaign. |
| **Benachrichtigung über Aufgaben** (taskMgt) | Marketing-Ressourcen (MRM) – Nur Campaign v7 | Mit diesem Workflow können Sie Benachrichtigungen senden, die sich auf Aufgaben in Marketing-Kampagnen beziehen. |
| **Tracking** (tracking) | Versand | Dieser Workflow ermöglicht die Wiederherstellung und Konsolidierung von Tracking-Informationen. Darüber hinaus wird die Neuberechnung von Tracking- und Versandstatistiken sichergestellt, insbesondere derjenigen, die von Archivierungs-Workflows für Message Center verwendet werden. Standardmäßig wird sie einmal pro Stunde ausgelöst. |
| **Update des Ereignisstatus** (updateEventsStatus) | Ausführung einer Transaktionsnachricht (Message Center – Ausführung) | Mit diesem Workflow können Sie Ereignissen einen Status zuweisen. Ereignisstatus sind wie folgt:<ul><li>Ausstehend: Das Ereignis befindet sich in einer Warteschlange. Es wurde noch keine Nachrichtenvorlage damit verknüpft.</li><li>Versand ausstehend: Das Ereignis befindet sich in der Warteschlange. Ihm wurde eine Nachrichtenvorlage zugeordnet und die Versandverarbeitung ist im Gange.</li><li>Gesendet: Dieser Status wird aus den Versandlogs übernommen. Dies bedeutet, dass der Versand durchgeführt wurde.</li><li>Vom Versand ignoriert: Dieser Status wird aus den Versandlogs übernommen. Dies bedeutet, dass der Versand ignoriert wurde.</li><li>Versandfehler: Dieser Status wird aus den Versandlogs übernommen. Dies bedeutet, dass der Versand fehlgeschlagen ist.</li><li>Ereignis wurde nicht berücksichtigt: Das Ereignis konnte keiner Nachrichtenvorlage zugeordnet werden. Das Ereignis wird nicht erneut verarbeitet.</li></ul> |
| **Zustellbarkeit** (deliverabilityUpdate) | Versand | Dieser Workflow wird nächtlich ausgeführt und verwaltet die Qualifizierungsregeln für Bounce-E-Mails sowie die Liste der Domains und MXs. Dazu muss der HTTPS-Port auf der Plattform geöffnet sein. |