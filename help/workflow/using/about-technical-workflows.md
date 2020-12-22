---
solution: Campaign Classic
product: campaign
title: Technische Workflows
description: Erfahren Sie mehr über die Technischen Workflows, die mit Campaign Classic-Paketen verfügbar sind.
audience: workflow
content-type: reference
topic-tags: technical-workflows
translation-type: tm+mt
source-git-commit: 3f2e984f85e517777751e3c36dc96437eefb3010
workflow-type: tm+mt
source-wordcount: '1849'
ht-degree: 68%

---


# Technische Workflows{#about-technical-workflows}

## Über technische Workflows {#overview}

Die in diesem Abschnitt beschriebenen Workflows werden mit den verschiedenen integrierten Adobe Campaignen installiert. Diese Pakete und zugehörige Technischen Workflows hängen von Ihrer Lizenzvereinbarung ab. Integrierte Pakete werden in [diesem Abschnitt](../../installation/using/installing-campaign-standard-packages.md) beschrieben.

Standardmäßig sind Technischen Workflows in einem Unterordner des folgenden Knotens verfügbar: **[!UICONTROL Administration]** > **[!UICONTROL Produktion]** > **[!UICONTROL Technischen Workflows]**.

>[!NOTE]
>
>Die mit dem Message Center verbundenen technischen Workflows sind standardmäßig im Knoten **[!UICONTROL Administration]** > **[!UICONTROL Betreibung]** > **[!UICONTROL Message Center]** > **[!UICONTROL Technische Workflows]** verfügbar.

Weiterführende Informationen zur Verfolgung technischer Workflows finden Sie in [diesem Abschnitt](../../workflow/using/monitoring-technical-workflows.md).

## Liste der technischen Workflows {#list-technical-workflows}

| Technischer Workflow | Package | Beschreibung  |
|------|--------|-----------|
| **Alias-Datenbereingung** (aliasCleansing) | Versand | Vereinheitlicht Aufzählungswerte. Wird standardmäßig täglich um 3 Uhr gestartet. |
| **Rechnungsstellung**  (Rechnungsstellung) | Versand | Übermittelt per E-Mail den Aktivitätsbericht des Systems an den fakturierungsverantwortlichen Benutzer (&#39;billing&#39;). Wird standardmäßig an jedem 25. des Monats gestartet. |
| **Berechnung der Twitter-Statistik** (statsTwitter) | Soziale Netzwerke (Social Marketing) | Berechnet Statistiken in Bezug auf Retweets und Besuchen auf Twitter. |
| **Kampagne jobs** (operationMgt) | Marketing-Kampagnen (Kampagne) | Verwaltet Vorgänge in Marketingkampagnen (Zielgruppenbestimmung, Dateiextraktion etc.). Erstellt darüber hinaus Workflows für wiederkehrende und periodische Kampagnen. |
| **Erfassen von Datenschutzanfragen** (collectionPrivacyRequests) | Datenschutzbestimmung | Mit diesem Workflow werden die in Adobe Campaign gespeicherten Empfängerdaten abgerufen und im Datenschutzanfrage-Fenster für den Download bereitgestellt. |
| **Kostenberechnung** (budgetMgt) | Marketing-Kampagnen (Kampagne) | Berechnet Ausgaben- und Kostenzeilen für Pläne, Programme, Kampagnen, Sendungen und Aufgaben. |
| **Datenbankbereinigung** (Bereinigung) | Versand | Bereinigt obsolete Daten gemäß der Konfiguration im Softwareverteilungs-Assistenten. Berechnet diverse Statistiken und Vorgänge. Wird standardmäßig täglich um 4 Uhr gestartet. Weitere Informationen dazu finden Sie auf dieser [Seite](../../production/using/database-cleanup-workflow.md#monitoring-campaign-classic). |
| **Blockierte LINE-Benutzer**  löschen(deleteBlockedLineUsersV2) | LINE-Kanal | Dieser Workflow stellt sicher, dass die Daten der LINE V2-Benutzer gelöscht werden, nachdem sie das offizielle LINE-Konto 180 Tage lang gesperrt haben. |
| **Daten**  zu Datenschutzanfragen löschen(deletePrivacyRequestsData) | Datenschutzbestimmung | Mit diesem Workflow werden die in Adobe Campaign gespeicherten Empfängerdaten gelöscht. |
| **Versand-Indikatoren** (deliveryIndicators) | Mid-Sourcing-Plattform | Aktualisiert Trackingindikatoren von Sendungen. Wird standardmäßig stündlich gestartet. |
| **Diskussionsforum-Prozesse** (newsgroupMgt) | Marketing-Ressourcen (MRM) | Sendet Benachrichtigungen in Diskussionsforen. Wird gestartet, sobald ein Validierungssignal empfangen wird |
| **Verteilte Marketingprozesse** (centralLocalMgt) | Zentrales/lokales Marketing (Dezentrale Marketing) | Führt die Vorgänge im Zusammenhang mit dem Distributed-Marketing-Modul aus. Erstellt lokale Kampagnen und verwaltet Benachrichtigungen in Bezug auf Bestellungen und der Verfügbarkeit von Kampagnenkits. |
| **Ereignis purge** (webAnalyticsPurgeWebEvents) | Web-Analytics-Connectoren | Mit diesem Arbeitsablauf können Sie jedes Ereignis entsprechend dem im Feld &quot;Lebensdauer&quot;konfigurierten Zeitraum aus dem Datenbankfeld löschen. |
| **Audiencen in das Adobe Experience Cloud**  exportieren (exportSharedAudience) | Integration in Adobe Experience Cloud | Dieser Workflow exportiert freigegebene Zielgruppen. Diese können dann in anderen von Ihnen verwendeten Lösungen der Adobe Experience Cloud genutzt werden. |
| **Prognosen** (Prognosen) | Versand | Analysiert die im Planungskalender verzeichneten Sendungen (Erstellung von Planungslogs). Wird standardmäßig täglich um 1 Uhr gestartet. |
| **Berechnung des vollständigen Aggregats (propositionrcp-Cube)** (agg_nmspropositionrcp_full) | Angebot Engine (Interaktion) | Dieser Workflow aktualisiert das full-Aggregat des Angebotsvorschlag-Cubes. Es wird standardmäßig täglich um 6 Uhr gestartet. Dieses Aggregat erfasst die folgenden Dimensionen: Kanal, Versand, Marketingangebot und Datum. Mit dem Angebotsvorschlag-Cube können anschließend Berichte auf der Basis von Angeboten erstellt werden. Weiterführende Informationen zu Cubes finden Sie in [diesem Abschnitt](../../reporting/using/about-cubes.md). |
| **Identifizierung konvertierter Kontakte**  (webAnalyticsFindConverted) | Web-Analytics-Connectoren | Dieser Arbeitsablauf indiziert Site-Besucher, die ihren Einkauf nach einer Remarketing-Kampagne abgeschlossen haben. Die durch diesen Workflow wiederhergestellten Daten können im Bericht zur Effizienz des Remarketing (siehe diese Seite) abgerufen werden. |
| **Audiencen aus dem Adobe Experience Cloud**  importieren (importSharedAudience) | Integration in Adobe Experience Cloud | Dieser Workflow ermöglicht den Import von Zielgruppen/Segmenten aus den unterschiedlichen Lösungen der Adobe Experience Cloud in Adobe Campaign. |
| **Aufträge auf Versänden in Kampagnen** (deliveryMgt) | Marketing-Kampagnen (Kampagne) | Startet den Versand der validierten Sendungen und die Anschlussvorgänge des Dienstleisters bei externen Sendungen. Außerdem werden Validierungsbenachrichtigungen und Erinnerungen gesendet. |
| **Aufträge auf Dienstleistern** (providerMgt) | Marketing-Kampagnen (Kampagne) | Startet nach erfolgter Versandvalidierung Dienstleistervorgänge (E-Mail an den Router und Anschlussvorgang).  |
| **LINE V2 Zugriffstoken update** (updateLineV2AccessToken) | LINE-Kanal | Dieser Workflow aktualisiert das Zugriffstoken auf LINE V2. |
| **MID zu LineUserID-Migration** (MIDToUserIDMigration) | LINE-Kanal | Dieser Workflow erzeugt die Kennung von LINE V2-Benutzern für die Migration von LINE V1 nach LINE V2. |
| **Benachrichtigungen**  zur Marketing-Ressource (assetMgt) | Marketing-Ressourcen (MRM) | Verwaltet die Benachrichtigungen bezüglich der Validierung und der Freigabe von Marketing-Ressourcen. |
| **Message Center  &lt;external_account_name>** (mcSynch_&lt;external_account_name>) | Kontrolle der Transaktionsnachricht (Message Center - Control) | Dieser Workflow: <ul><li>Ruft die Liste der durch die Aktion(en) verarbeiteten Ereignisse ab.</li><li>Wird mit der NmsBroadLogMsg-Tabelle synchronisiert, um die Qualifizierung der Versandnachrichten abzurufen.</li><li>Ruft Ereignis-Versandlogs ab, sobald die Synchronisation mit der NmsBroadLogMsg-Tabelle abgeschlossen ist.</li><li>Wird mit der NmsTrackingUrl-Tabelle synchronisiert, um das Tracking für die Versand-URLs abzurufen.</li><li>Ruft Ereignis-Verfolgungs-URLs ab, sobald die Synchronisation mit der NmsTrackingUrl-Tabelle abgeschlossen ist.</li><li>Ruft alle drei Stunden die E-Mail-Adressen ab, die infolge eines Versands neu in Quarantäne gekommen sind.</ul> |
| **Berechnung**  des vollständigen MessageCenter-Aggregats (agg_messageCenter_full) | Angebot Engine (Interaktion) | Dieser Arbeitsablauf aktualisiert das vollständige Aggregat für die Cube des Nachrichtenzentrums. Es wird standardmäßig jeden Tag um 3 Uhr morgens ausgelöst. Dieses Aggregat erfasst die folgenden Dimensionen: Kanal, Datum, Status und Ereignistyp. Die Message Center-Cube wird dann verwendet, um Berichte auf der Grundlage von Ereignissen zu erstellen. Weitere Informationen zu Cuben finden Sie in [diesem Abschnitt](../../reporting/using/about-cubes.md) |
| **Mid-Sourcing (Versand-Zähler)** (defaultMidSourcingDlv) | Sendung an Mid-Sourcing-Server | Dieser Workflow ruft Informationen bezüglich der Zählung von Sendungen vom Mid-Sourcing-Server ab. Zu diesen Informationen gehören allgemeine Indikatoren zum Versand wie etwa die Anzahl der Sendungen. Trackinginformationen wie Öffnungen sind nicht enthalten. Dieser Workflow wird standardmäßig alle zehn Minuten gestartet. |
| **Mid-Sourcing (Versandlogs)** (defaultMidSourcingLog) | Sendung an Mid-Sourcing-Server | Ruft Versandlogs vom Mid-Sourcing-Server ab. Wird standardmäßig stündlich gestartet. |
| **NMAC-Opt-out-Management** (mobileAppOptOutMgt) | Mobile-App-Kanal (Mobile App Channel) | Aktualisiert die Abmeldungen von Benachrichtigungen auf Mobile-Geräten. Wird standardmäßig alle sechs Stunden zwischen 1 Uhr und Mitternacht gestartet. Weitere Informationen finden Sie in [diesem Abschnitt](../../delivery/using/understanding-quarantine-management.md#push-notification-quarantines). |
| **Anzahl der aktiven Profil**  zur Rechnungsstellung (billingActiveContactCount) | angebot-Engine (Interaktion) | Mit diesem Workflow wird die Anzahl der aktiven Profile gezählt. Er wird standardmäßig jede Nacht um 1 Uhr ausgelöst. Profil bezeichnet einen Datensatz, der einen Endkunden, einen Prospect oder Lead repräsentiert. Bei diesen Daten kann es sich z. B. um einen Datensatz in der nmsRecipient-Tabelle oder einer externen Tabelle handeln, die die Kennung eines Cookies, eines Kunden oder eines Mobiltelefons oder andere für einen bestimmten Kanal relevante Informationen enthält. Die Abrechnung betrifft nur Profil, die &quot;aktiv&quot;sind. Ein Profil gilt als &quot;aktiv&quot;, wenn das Profil innerhalb der letzten 12 Monate über einen beliebigen Kanal anvisiert oder kommuniziert wurde. Die Kanäle Facebook und Twitter werden nicht berücksichtigt. Eine Übersicht über die Anzahl der aktiven Profile erhalten Sie über das Menü Administration > Kampagnenverwaltung > Kundenmetriken. |
| **Angebot Notification** (offerMgt) | Versand | Gibt stündlich validierte Angebote sowie im Angebotskatalog erstellte Kategorien in die Live-Umgebung frei. |
| **Angehaltene Workflows Bereinigung**  (cleanupPausedWorkflows) | Versand | In diesem Workflow werden ausgesetzte Workflows analysiert, für die eine normale Prioritätsstufe festgelegt wurde und die Warnhinweise und Benachrichtigungen auslösen, wenn sie zu lange angehalten werden. Nach einem Monat werden ausgesetzte technische Workflows gestoppt. Standardmäßig werden sie jeden Montag um 5 Uhr ausgelöst. Weitere Informationen finden Sie unter [Handhabung der angehaltenen Workflows](../../workflow/using/monitoring-workflow-execution.md#handling-of-paused-workflows). |
| **Bereinigung**  von Datenschutzanfragen (cleanupPrivacyRequests) | Datenschutzbestimmung | Mit diesem Workflow werden Zugriffsanfragen gelöscht, die älter als 90 Tage sind. |
| **Verarbeiten von Batch-Ereignissen** (batchEventsProcessing) | Ausführung der Transaktionsnachricht (Nachrichtencenter - Ausführung) | Teilt die Batch-Ereignisse in eine Warteschlange ein, bevor ihnen eine Nachrichtenvorlage zugeordnet wird. |
| **Verarbeiten von Echtzeit-Ereignissen** (rtEventsProcessing) | Ausführung der Transaktionsnachricht (Nachrichtencenter - Ausführung) | Teilt die Echtzeit-Ereignisse in eine Warteschlange ein, bevor ihnen eine Nachrichtenvorlage zugeordnet wird. |
| **Proposition synchronization** (propositionSynch) | Steuerung des Angebotsmoduls durch die Ausführungsinstanz | Dieser Workflow synchronisiert Vorschläge zwischen der Marketinginstanz und der Ausführungsinstanz, die für Interaktionen verwendet wird. |
| **Wiederherstellung von Web-Ereignissen** (webAnalyticsGetWebEvents) | Web-Analytics-Connectoren | Ruft stündlich die Segmente ab, die sich auf das Besucherverhalten der angegebenen Webseite beziehen, fügt die Daten zur Adobe-Campaign-Datenbank hinzu und startet den Remarketing-Workflow. |
| **Für Lieferbarkeit**  aktualisieren (DeliveryUpdate) | Zustellbarkeits-Monitoring (Email Deliverability) | Sobald das Paket zur Überwachung der Auslieferbarkeit (E-Mail-Auslieferung) installiert ist, wird dieser Arbeitsablauf jeden Abend ausgeführt, um die Liste der Regeln regelmäßig zu aktualisieren und die Plattformbereitstellung aktiv zu verwalten. |
| **Berichte-Aggregat** (reportingAggregates) | Versand | Aktualisiert die in Berichten verwendeten Aggregate. Wird standardmäßig täglich um 2 Uhr gestartet. |
| **Senden von Indikatoren und Kampagnen-Attributen**  (webAnalyticsSendMetrics) | Web-Analytics-Connectoren | Mit diesem Arbeitsablauf können Sie E-Mail-Kampagnen über den Adobe® Genesis Connector von Adobe Campaign an die Adobe Experience Cloud Suite senden. Es handelt sich um folgende Indikatoren: Gesendet (gesendet), Gesamtzahl der &quot;open&quot;(iTotalRecipientOpen), Gesamtzahl der angeklickten Empfänger (iTotalRecipientClick), Fehler (iError), Ausschluss (Opt-out) (iOptOut). |
| **Bestand: Bestellungen und Warnungen** (stockMgt) | Marketing-Kampagnen (Kampagne) | Startet die Berechnung der Lagerbestände in den Bestellzeilen und verwaltet Warnschwellen. |
| **Synchronisieren von Facebook-Fans** (syncFacebookFans) | Soziale Netzwerke (Social Marketing) | Importiert täglich um 7 Uhr Facebook-Fans in Adobe Campaign. |
| **Synchronisieren von Facebook-Seiten**  (syncFacebook) | Soziale Netzwerke (Social Marketing) | Synchronisiert täglich um 7 Uhr Facebook-Seiten mit Adobe Campaign. |
| **Synchronisieren von Twitter-Seiten**  (syncTwitter) | Soziale Netzwerke (Social Marketing) | Importiert täglich um 7 Uhr Twitter-Followers in Adobe Campaign. |
| **Aufgabe Notification** (taskMgt) | Marketing-Ressourcen (MRM) | Sendet Benachrichtigungen bezüglich Aufgaben in Marketingkampagnen. |
| **Verfolgung** (Verfolgung) | Versand | Ruft Trackinginformationen ab und konsolidiert sie. Aktualisiert außerdem die Berechnung der Tracking- und Versandstatistiken, insbesondere die von den Message-Center-Archivierungs-Workflows verwendeten. Wird standardmäßig stündlich gestartet. |
| **Status**  des Ereignisses aktualisieren(updateEventsStatus) | Ausführung der Transaktionsnachricht (Nachrichtencenter - Ausführung) | Weist Ereignissen einen Status zu. Folgende Status sind möglich:<ul><li>Ausstehend: Das Ereignis befindet sich in der Warteschlange. Ihm wurde noch keine Nachrichtenvorlage zugeordnet.</li><li>Versand ausstehend: Das Ereignis befindet sich in der Warteschlange. Ihm wurde eine Nachrichtenvorlage zugeordnet und die Versandverarbeitung ist in Gang.</li><li>Gesendet: Dieser Status wird aus den Versandlogs übernommen. Er bedeutet, dass die Nachricht gesendet wurde.</li><li>Vom Versand ignoriert: Dieser Status wird aus den Versandlogs übernommen. Er bedeutet, dass der Versand ignoriert wurde.</li><li>Versandfehler: Dieser Status wird aus den Versandlogs übernommen. Er bedeutet, dass der Versand fehlgeschlagen ist.</li><li>Ereignis wurde nicht berücksichtigt: Dem Ereignis konnte keine Nachrichtenvorlage zugeordnet werden. Es erfolgt kein weiterer Verarbeitungsversuch.</li></ul> |
| **Aktualisierung der Lieferbarkeit**  (DeliveryUpdate) | Versand | Erstellt die Liste der Qualifizierungsregeln für Bounce-Messages sowie die Liste der Domains und MX der Plattform. Der Workflow wird nur bei geöffnetem HTTPS-Port ausgeführt. Wenn das Zustellbarkeitsmodul (Email Deliverability) nicht installiert ist, werden die Listen nicht aktualisiert. |
| **Aktualisieren des Seed-Netzwerks für das Inbox-Rendering** (updateRenderingSeeds) | Inbox Rendering (IR) | Dieser Arbeitsablauf aktualisiert E-Mail-Adressen, die für das Inbox-Rendering verwendet werden, und funktioniert nur, wenn der HTTPS-Anschluss für &quot;delivery.neolane.net&quot;geöffnet ist. |
