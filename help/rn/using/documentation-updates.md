---
product: campaign
title: Aktualisierungen der Dokumentation zu Adobe Campaign Classic v7
description: Auf dieser Seite werden alle neuen Funktionen und Aktualisierungen in der Dokumentation zu Adobe Campaign Classic aufgelistet.
feature: Overview
role: User
level: Beginner
exl-id: 07c1f4a3-cf16-4a9b-b402-e13258799f91
source-git-commit: 87067a0cca1a4a7f8ea1137ece6d513d58fcdb42
workflow-type: tm+mt
source-wordcount: '4816'
ht-degree: 100%

---

# Aktualisierungen der Dokumentation{#documentation-updates}

![](../../assets/v7-only.svg)

Auf dieser Seite werden alle neuen Funktionen und Dokumentationsaktualisierungen pro Monat und Campaign-Version aufgeführt.

Die entsprechenden Aktualisierungen finden Sie in den [Versionshinweisen zu Adobe Campaign Classic](../../rn/using/latest-release.md).

## 2022

### Januar

**Dokumentationsaktualisierungen in Version 7.2.1**

Aktualisierte Kompatibilitätsmatrix. [Mehr dazu](compatibility-matrix.md)

Der Abschnitt zu Versionshinweisen wurde aktualisiert. [Mehr dazu](rn-overview.md)

Die Konfiguration des externen FDA-Kontos für Snowflake wurde aktualisiert. [Mehr dazu](../../installation/using/configure-fda-snowflake.md)

Die Konfiguration des externen FDA-Kontos für Azure Synapse Analytics wurde aktualisiert. [Mehr dazu](../../installation/using/configure-fda-synapse.md#azure-external)

Der Google BigQuery FDA-Connector wurde aktualisiert. [Mehr dazu](../../installation/using/configure-fda-google-big-query.md)

Nach der Einstellung wurden die Aktionsaktivitäten für Microsoft CRM, Salesforce und Oracle CRM On Demand aus der Dokumentation entfernt.

Die neue Option **Abbruch bei Fehler** wurde zum Abschnitt zum Umgang mit Fehlern im Workflow hinzugefügt. [Mehr dazu](../../workflow/using/advanced-parameters.md#in-case-of-errors)

Die Option zur Stapel-Aktualisierung wurde in der CRM-Connector-Aktivität hinzugefügt. [Mehr dazu](../../workflow/using/crm-connector.md)

## 2021

### Dezember 2021{#dec-2021}

Die Versionshinweise zu Campaign Classic v7 wurden neu geordnet, um die Navigation zu vereinfachen. [Mehr dazu](rn-overview.md)

Die Dokumentation zur Formularbearbeitung in Campaign wurde aktualisiert und verbessert. [Mehr dazu](../../configuration/using/editing-forms.md)

CentOS 8 hat das Ende der Lebensdauer erreicht und wird jetzt von Adobe Campaign Classic nicht mehr unterstützt. [Mehr dazu](deprecated-features.md)

### November 2021{#nov-2021}

Es wurde eine Beschränkung für eingehende SMS (MO) hinzugefügt. [Mehr dazu](../../delivery/using/sms-protocol.md#multipart)

Die Details der Migrationsprozess-Protokolle für die Bereitstellung des CRM-Connectors wurden aktualisiert. [Mehr dazu](../../migration/using/testing-the-migration.md#verification-process)

Es wurden Anforderungen bezüglich der IMS-Berechtigungen zur Implementierung der Integration zwischen Adobe Campaign und Adobe Analytics hinzugefügt. [Mehr dazu](../../platform/using/adobe-analytics-provisioning.md)

Das Datum für das Auslaufen von Adobe Analytics Data Connector wurde vom 1. März 2022 auf den 17. August 2022 geändert. [Mehr dazu](deprecated-features.md)

Es wurde ein Link zur Adobe Experience Platform Mobile SDK-Dokumentation hinzugefügt, in dem beschrieben wird, wie die Campaign-Erweiterung in Adobe Launch konfiguriert werden kann. [Mehr dazu](../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md)

Es wurde ein Abschnitt hinzugefügt, in dem beschrieben wird, wie Sie mit JavaScript Werte berechnen, Daten austauschen und bestimmte Vorgänge mithilfe von SOAP-Aufrufen ausführen können.[Mehr dazu](../../workflow/using/javascript-scripts-and-templates.md)

Es wurden Beispiele für die Implementierung von JavaScript-Codes in Workflows hinzugefügt. [Mehr dazu](../../workflow/using/javascript-in-workflows.md)


### Oktober 2021{#oct-2021}

Vorhandene Technotes wurden in den neuen Abschnitt **Technote** gruppiert.

Die Seite **Empfehlungen zur Hardware-Dimensionierung** wurde aktualisiert und zum Abschnitt **Technotes** hinzugefügt. [Mehr dazu](../../technotes/using/hardware-sizing.md)

### September 2021{#sept-2021}

**Dokumentationsaktualisierungen in Version 21.1.4**

Der Diagrammtyp **Tacho** wurde entfernt.

Screenshots und Parameter von Berichten und Web-Anwendungen wurden nach der Entfernung von Adobe Flash aktualisiert.

Die Beschreibung des technischen Workflows [Rechnungsstellung](../../production/using/monitoring-processes.md#billing-report) wurde mit einem neuen Limit aktualisiert.

### August 2021{#aug-2021}

Neue Workflow-Aktivität hinzugefügt: Datenquelle ändern – [Mehr dazu](../../workflow/using/change-data-source.md)

Den Dokumentationsseiten wurden Anwendungs-Kennzeichen hinzugefügt: **Gilt für v7** nur für Campaign Classic v7-Funktionen und **für v7 und v8** für allgemeine Funktionen.

Es wurde ein Hinweis zur Integration zwischen Campaign und AEM Assets hinzugefügt, die seit Adobe Experience Manager 6.4 nicht mehr unterstützt wird. [Mehr dazu](../../integrations/using/configuring-access-to-assets.md)


### Juli 2021 {#july-2021}

Die [Campaign-Version 21.1.3](../../rn/using/latest-release.md#release-21-1-3-build-9330) ist jetzt allgemein verfügbar (General Availability, GA).


### Juni 2021 {#june-2021}

Der Abschnitt **Transaktionsnachrichten** wurde umstrukturiert und mit dem neuen Abschnitt &quot;Erste Schritte&quot;, einschließlich eines [erweiterten Schemas](../../message-center/using/about-transactional-messaging.md#transactional-messaging-operating-principle), klarer gestaltet, um den Prozess besser verständlich zu machen. [Mehr dazu](../../message-center/using/about-transactional-messaging.md)

**Dokumentationsaktualisierungen zu Version 21.1.3**

Integration mit Adobe Journey Orchestration – [Mehr dazu](https://experienceleague.adobe.com/docs/journeys/using/action-journeys/acc-action.html?lang=de). Auf dieser [Seite](https://experienceleague.adobe.com/docs/journeys/using/use-cases-journeys/campaign-classic-use-case.html?lang=de) wird ein Anwendungsfall im Detail vorgestellt.

Verbesserungen am LINE-Kanal – [Mehr dazu](../../delivery/using/line-channel.md)

Neuer Vertica FDA-Connector – [Mehr dazu](../../installation/using/configure-fda-vertica.md)

Neuer Google BigQuery FDA-Connector – [Weitere Informationen](../../installation/using/configure-fda-google-big-query.md)

Die Beschreibung des technischen Workflows &quot;Abrechnung (Billing)&quot; enthält jetzt die Aufgaben, die ursprünglich vom Workflow &quot;Zählung aktiver Profile (Billing) (billingActiveContactCount)&quot; ausgeführt wurden. [Mehr dazu](../../workflow/using/about-technical-workflows.md)

### Mai 2021 {#may-2021}

Die Dokumentation zum Workflow-Heatmap-Bericht wurde aktualisiert und verbessert. [Mehr dazu](../../workflow/using/heatmap.md)

Die Anforderungen an die Client-Konsole von Campaign wurden in der Kompatibilitätsmatrix aktualisiert. [Mehr dazu](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems)

Die Installationsschritte für die Client-Konsole von Campaign wurden verbessert und verdeutlicht. [Mehr dazu](../../installation/using/installing-the-client-console.md)

Es wurde eine neue Technote zum Signaturproblem für getrackte URLs erstellt. [Mehr dazu](../../technotes/using/tracked-urls.md)

### April 2021 {#april-2021}

Ein neuer Abschnitt beschreibt die Verwendung von Adobe Experience Platform-Quellen und -Zielen, um Daten zwischen Campaign Classic und der Echtzeit-Kundendatenplattform (RTCDP) von Adobe auszutauschen. [Mehr dazu](../../integrations/using/get-started-sources-destinations.md)

Es wurde eine neue Technote erstellt, in der erklärt wird, wie die Bounce-Qualifizierung nach einem ISP-Ausfall aktualisiert werden kann. [Mehr dazu](../../delivery/using/update-bounce-qualification.md)

### März 2021 {#march-2021}

Der Abschnitt [Erste Schritte mit SMS](../../delivery/using/sms-channel.md) wurde neu organisiert und verbessert. In speziellen Abschnitten erfahren Sie nun, wie Sie [den SMS-Kanal konfigurieren](../../delivery/using/sms-set-up.md), [eine SMS erstellen](../../delivery/using/sms-create.md) sowie [SMS senden und verfolgen](../../delivery/using/sms-send.md) können.

Die Seite &quot;Hilfe und Support-Optionen&quot; für Campaign Standard wurde in die Hauptdokumentation integriert. [Mehr dazu](../../support.md)

Es wurde ein neuer Abschnitt zu Best Practices und Überprüfungen für Sicherheit und Datenschutz hinzugefügt. [Mehr dazu](../../installation/using/get-started-security-privacy.md)

Das [Kapitel zur Verwaltung von Berechtigungen](../../platform/using/access-management.md) wurde überarbeitet und in verschiedene Abschnitte unterteilt, einschließlich Details zu [Operatoren](../../platform/using/access-management-operators.md) , [Benutzergruppen](../../platform/using/access-management-groups.md), [spezifischen Berechtigungen](../../platform/using/access-management-named-rights.md) und [Ordnerverwaltung](../../platform/using/access-management-folders.md).

Näheres zur Erstellung und Verwaltung von Kampagnen finden Sie auf den folgenden Seiten:
* [Erstellen und Konfigurieren von Kampagnenvorlagen](../../campaign/using/marketing-campaign-templates.md)
* [Sendungen für eine Marketing-Kampagne](../../campaign/using/marketing-campaign-deliveries.md)
* [Auswählen der Audience für Ihre Kampagnen](../../campaign/using/marketing-campaign-target.md)
* [Verwalten der zugehörigen Dokumente](../../campaign/using/marketing-campaign-assets.md)
* [Einrichten und Verwalten des Validierungsprozesses](../../campaign/using/marketing-campaign-approval.md)

Im Abschnitt zur Aktivität **[!UICONTROL Erweitertes JavaScript]** finden Sie Informationen dazu, wie Sie die Methode „task.setCompleted()“ verwenden können, um die Aufgabe zu beenden und künftige Rückrufe zu verhindern. [Mehr dazu](../../workflow/using/sql-code-and-javascript-code.md#adv-js-code-desc)

Der Abschnitt [Zustellbarkeit](../../delivery/using/about-deliverability.md) wurde aktualisiert und enthält nun Links zum neuen [Adobe-Handbuch mit Best Practices zur Zustellbarkeit](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=de). Alle allgemeinen Informationen zur Zustellbarkeit, die für verschiedene Adobe-Lösungen gelten können, wurden in den [Anhang des Handbuchs mit Best Practices](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/general-resources.html?lang=de#additional-resources) verschoben.

### Februar 2021 {#release-21.1}

**Dokumentationsaktualisierungen zu Version 21.1**

Die neue Funktion **E-Mail-Feedback-Service** (private Betaversion) ist [hier](../../delivery/using/sending-with-enhanced-mta.md#email-feedback-service) dokumentiert.

Der Abschnitt **Server-Konfigurationsdatei** wurde mit den Konfigurationsparametern aktualisiert, die für die Verbindung von Campaign mit einem anderen Service über IMS erforderlich sind. [Mehr dazu](../../installation/using/the-server-configuration-file.md#ims)

In der Liste der Versandstatus wurde die Beschreibung für **Vom Dienstleister berücksichtigt** aktualisiert: Dieser Status wird nun auch für E-Mail-Sendungen verwendet, die über den [E-Mail-Feedback-Service](../../delivery/using/sending-with-enhanced-mta.md#email-feedback-service) versendet werden. [Mehr dazu](../../delivery/using/delivery-statuses.md#list-delivery-statuses)

Die Tastaturkürzel, die auf dem neuen Anmeldebildschirm zur Verbindung mit Adobe Campaign verfügbar sind, sind jetzt dokumentiert. [Mehr dazu](../../platform/using/launching-adobe-campaign.md#connecting-to-adobe-campaign)

**Weitere Aktualisierungen**

Es wurde ein neuer Abschnitt mit detaillierten Informationen zur Durchführung von A/B-Tests mit Workflows hinzugefügt. [Mehr dazu](../../delivery/using/get-started-a-b-testing.md)

Der Bereich zum Adobe Campaign Enhanced MTA wurde [hierher](../../delivery/using/sending-with-enhanced-mta.md) verschoben.

Es wurde eine neue Seite hinzugefügt, die einen Überblick über die Tracking-Funktionen in [!DNL Campaign Classic] bietet. [Mehr dazu](../../delivery/using/about-message-tracking.md)

Es wurde ein Abschnitt zur Fehlerbehebung hinzugefügt, der Ihnen bei der Behebung häufiger Probleme im Zusammenhang mit dem Tracking hilft. [Mehr dazu](../../delivery/using/tracking-troubleshooting.md)

Der Abschnitt **E-Mail-Versand** wurde in neue Unterabschnitte umorganisiert und präzisiert. [Mehr dazu](../../delivery/using/sending-messages.md)

Es wurden Informationen zum Hinzufügen von Links in E-Mails hinzugefügt, die personalisiert werden können und das Tracking unterstützen. [Mehr dazu](../../delivery/using/tracking-personalized-links.md).

### Januar 2021 {#jan-2021}

Der Abschnitt zur **[!UICONTROL Verzweigungsaktivität]** wurde um Best Practices erweitert. [Mehr dazu](../../workflow/using/fork.md)

Der Abschnitt **CRM-Connectoren** wurde aktualisiert, verbessert und neu organisiert. [Mehr dazu](../../platform/using/crm-connectors.md).

Die Schritte zum Verbinden von **Adobe Campaign und Microsoft Dynamics** werden jetzt auf einer eigenen Seite ausführlich erläutert. [Mehr dazu](../../platform/using/crm-ms-dynamics.md).

Die Oracle On Demand-API wird jetzt als mit Campaign verbundene CRM-Lösung nicht mehr unterstützt. [Mehr dazu](../../rn/using/deprecated-features.md).

Erfahren Sie [hier](../../production/using/locate-tomcat-version.md), wie Sie die aktuelle Version des eingebetteten Tomcat-Webservlets ermitteln, das in einer Instanz von Adobe Campaign verwendet wird.

Die Liste der technischen Workflows und den ihnen zugehörigen Paketen wurde erweitert und auf einer Seite zusammengefasst. [Mehr dazu](../../workflow/using/about-technical-workflows.md)

Der Abschnitt zur Fehlerbehebung im **Überwachungshandbuch** wurde neu strukturiert und durch eine Landingpage erweitert. [Mehr dazu](../../production/using/troubleshooting.md).

Es wurde ein neuer Abschnitt zum **Datenimport und -export** einschließlich neuer Seiten mit Best Practices für Workflows, Datenkomprimierung, Verschlüsselung und Import ergänzt. [Mehr dazu](../../platform/using/get-started-data-import-export.md)






## 2020

### Dezember 2020 {#dec-2020}

Der Bereich **Versand-Monitoring** wurde nach Themenbereichen strukturiert. [Mehr dazu](../../delivery/using/about-delivery-monitoring.md)

Ein neuer Anwendungsfall zeigt, wie die IP-Adressen von Absendern zu den Versandlogs hinzugefügt werden können. [Mehr dazu](../../delivery/using/delivery-dashboard.md#use-case)

Die häufig gestellten Fragen zum Datenschutz wurden in [diesen Abschnitt](../../platform/using/privacy-faq.md) verschoben.

Es wurde ein Anwendungsfall zur Verwendung der Zusammenführungsfunktion der **[!UICONTROL Deduplizierungsaktivität]** hinzugefügt. [Mehr dazu](../../workflow/using/deduplication-merge.md)

Die vollständige Beschreibung des SMS-Connector-Protokolls und der Einstellungsseite ist jetzt [hier](../../delivery/using/sms-protocol.md) verfügbar.

Der Abschnitt **Transaktionsnachrichten** wurde um ein Hinweis dazu ergänzt, dass die Ereignis-Ordner nicht als Ansichten für die Ausführungsinstanzen festgelegt werden dürfen, da dies zu Problemen mit Zugriffsrechten führt. [Mehr dazu](../../message-center/using/about-event-processing.md#event-collection)

### November 2020 {#nov-2020}

Die Übersicht über das Datenmodell von Campaign wurde verbessert und neu organisiert. [Mehr dazu](../../configuration/using/about-data-model.md).

Die Konfiguration des externen Kontos wurde in [diesen Abschnitt](../../installation/using/external-accounts.md) verschoben.

Die Dokumentation zum Federated Data Access (FDA) von Campaign wurde mit Details zu den einzelnen externen Datenbankkonfigurationen verbessert und in [diesen Abschnitt](../../installation/using/about-fda.md) verschoben.

Die [Campaign-Version 20.2.3](../../rn/using/release--2020.md#release-20-2-3-build-9182) ist jetzt allgemein verfügbar (General Availability, GA).

Der Abschnitt zum Datenschutz wurde um zwei neue Seiten erweitert: [Datenschutzverwaltung](../../platform/using/privacy-management.md) und [Verwaltung von Datenschutzanfragen](../../platform/using/privacy-requests.md).

Auf der Seite zur Mid-Sourcing-Server-Konfiguration wurde ein Hinweis hinzugefügt, um zu präzisieren, dass der interne Name des externen Kontos nach dem Einrichten des Servers nicht aktualisiert werden darf. [Mehr dazu](../../installation/using/mid-sourcing-server.md)

Es wurden Informationen zur Syntax hinzugefügt, die beim Festlegen eines Pfades zu einem externen SFTP-Server verwendet werden muss. [Mehr dazu](../../platform/using/sftp-server-usage.md#external-SFTP-server)

Der Abschnitt über persönliche Daten und Personen wurde um ein Verwendungsfallszenario bereichert, um zu veranschaulichen, wie die verschiedenen Personen in Bezug auf die Privatsphäre interagieren. [Mehr dazu](../../platform/using/privacy-and-recommendations.md#use-case-scenario)

Ein neuer Abschnitt mit häufig gestellten Fragen zum Datenschutz wurde hinzugefügt – [mehr dazu](../../platform/using/privacy-faq.md)

### Oktober 2020 {#oct-2020}

**Neue Funktionen in Version 20.3**

Verbesserungen bei Push-Benachrichtigungen für iOS – [mehr dazu](../../delivery/using/configuring-the-mobile-application.md)

Verbesserungen bei Push-Benachrichtigungen für Android – [mehr dazu](../../delivery/using/configuring-the-mobile-application-android.md)

**Weitere Dokumentationsaktualisierungen zu dieser Version**

Die Kompatibilitätsmatrix wurde aktualisiert. [Mehr dazu](../../rn/using/compatibility-matrix.md)

Die Seite mit veralteten und entfernten Funktionen wurde aktualisiert. [Mehr dazu](../../rn/using/deprecated-features.md)

Versionshinweise und Kompatibilitätsmatrix für die Version [!DNL Gold Standard] sind jetzt auf einer speziellen Seite verfügbar.
[Mehr dazu](../../rn/using/gold-standard.md)

Die Triggers-Integration, die ursprünglich auf der oAUTH-Authentifizierung basierte und für den Zugriff auf die Pipeline eingerichtet wurde, wurde geändert und in Adobe I/O verschoben. [Mehr dazu](../../integrations/using/configuring-adobe-io.md)

**Weitere Aktualisierungen**

Die Dokumentationsseiten wurden aktualisiert, um die Aktualisierung von Tomcat 8 widerzuspiegeln.

In der Beschreibung des Felds &quot;Info&quot; im Abschnitt &quot;Abrufen Ihrer Adobe Campaign-Version&quot; wurden Details hinzugefügt. [Mehr dazu](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)

Dem Abschnitt &quot;Aktualisieren von Adobe Campaign Classic&quot; wurden Richtlinien zum Durchführen einer Build-Aktualisierung hinzugefügt. Mehr dazu [Mehr dazu](../../production/using/build-upgrade.md)

Den allgemeinen Fragen zu Campaign wurden häufig gestellte Fragen zur Campaign-Build-Aktualisierung hinzugefügt. Mehr dazu [mehr dazu](../../platform/using/faq-build-upgrade.md)

Die On-Premise-, gehosteten und hybriden Hosting-Modelle von Campaign werden jetzt in einem eigenen Abschnitt beschrieben. [Mehr dazu](../../installation/using/hosting-models.md)

Die Funktionsmatrix pro Campaign-Hosting-Modell wurde aktualisiert und in das Installationshandbuch verschoben. [Mehr dazu](../../installation/using/capability-matrix.md)

Der Abschnitt mit den erweiterten Funktionen von Campaign Reporting wurde verbessert, um genau zu zeigen, wie sich URL-Parameter und Variablen in benutzerspezifischen Berichten verwenden lassen – [Mehr dazu](../../reporting/using/advanced-functionalities.md)

Die Seite mit den Berichtseigenschaften wurde neu organisiert und erweitert, um die Konfiguration zu erleichtern – [Mehr dazu](../../reporting/using/properties-of-the-report.md)

Es wurde eine neue Technote mit Details zur Migration vom Legacy-Binärprotokoll zur HTTP/2-basierten APNs Provider-API erstellt – [Mehr dazu](https://helpx.adobe.com/de/campaign/kb/migrate-to-apns-http2.html)

### September 2020 {#september-2020}

Es wurde ein Hinweis hinzugefügt, dass die Anzahl der aktiven Profile nur für Marketing-Instanzen verfügbar ist – [Mehr dazu](../../platform/using/about-profiles.md#active-profiles)

Es wurde ein neues Beispiel zur Schemabearbeitung hinzugefügt, um ein Feld mit einer vorhandenen Referenztabelle zu verknüpfen – [Mehr dazu](../../configuration/using/examples-of-schemas-edition.md#uc-link)

Es wurde ein Hinweis zur Verwendung zusätzlicher Daten mit Testadressen in Sendungen hinzugefügt – [Mehr dazu](../../delivery/using/creating-seed-addresses.md#defining-addresses)

### August 2020 {#aug-2020}

Informationen zu Best Practices im Zusammenhang mit der Versandgestaltung und dem Versand mit Campaign finden Sie in einem eigenen Abschnitt – [Mehr dazu](../../delivery/using/delivery-best-practices.md)

Die Landingpage für die Best Practices für die Zustellbarkeit wurde verbessert, um den Zugriff auf Unterabschnitte zu erleichtern – [Mehr dazu](../../delivery/using/about-deliverability.md)

Zu den folgenden Themen sind jetzt Anleitungsvideos verfügbar:

* [Einrichten der Ermüdungsverwaltung mithilfe von Typologieregeln und vordefinierten Filtern](../../campaign-opt/using/about-campaign-typologies.md)

* [Erstellen einer E-Mail in einer Kampagne](../../campaign/using/marketing-campaign-deliveries.md)

* [Erstellen eines mehrsprachigen Newsletters mit bedingten Inhalten](../../delivery/using/conditional-content.md)

* [Konfigurieren und Implementieren einer Versandvorlage](../../delivery/using/creating-a-delivery-template.md)

* [Aktivieren und Verwenden von AMP für E-Mails](../../delivery/using/defining-interactive-content.md)

* [Personalisieren von E-Mails mit dynamischen Inhaltsbausteinen](../../delivery/using/personalization-blocks.md)

* [Personalisieren von E-Mails mit Personalisierungsfeldern](../../delivery/using/personalization-fields.md)

* [Verwalten von Testadressen und Testsendungen in einer E-Mail](../../delivery/using/steps-defining-the-target-population.md)

* [Einrichten eines wiederkehrenden Versands](../../workflow/using/recurring-delivery.md)

* [Einrichten eines Versands (fortlaufend)](../../workflow/using/continuous-delivery.md)

Es wurden Informationen zu den Prüfungen und Aktionen hinzugefügt, die durchzuführen sind, wenn der Fehler &quot;Hostname konnte nicht aufgelöst werden&quot; nach der Verbindung zu einem FTP-Server auftritt – [Mehr dazu](../../platform/using/sftp-server-usage.md)

In der Liste der [Workflow-Anwendungsfälle](../../workflow/using/about-workflow-use-cases.md) wurden neue Anwendungsfälle referenziert:

* Automatisieren der Inhaltserstellung, -bearbeitung und -veröffentlichung
* Einrichten eines Empfängergenehmigungsverfahrens vor der Ausführung eines Versands
* Aufrufen von Instanzvariablen in Abfragen
* Anwenden einer prozentualen Aufspaltung auf eine Population

Der Abschnitt über die **[!UICONTROL Und-Verknüpfungsaktivität]** wurde um zusätzliche Informationen über deren Verwendung sowie um einen Hinweis zur Verwendung von Variablen erweitert – [Mehr dazu](../../workflow/using/and-join.md)

### Juli 2020 {#july-2020}

Den Workflow-Anwendungsfällen wurde ein Anwendungsfall zum automatischen Aktualisieren einer Liste mithilfe einer inkrementellen Abfrage hinzugefügt. [Mehr dazu](../../workflow/using/about-workflow-use-cases.md)

Die [Versionshinweise](../../rn/using/latest-release.md) wurden neu organisiert: Es wurde eine [Übersichtsseite](../../rn/using/latest-release.md) mit Informationen zu Build-Status, Upgrade-Prozess, Empfehlungen und wichtigen Links hinzugefügt. Eine spezielle Seite für [[!DNL Gold Standard] Versionen](../../rn/using/gold-standard.md) wurde ebenfalls hinzugefügt und die [Kompatibilitätsmatrix](../../rn/using/compatibility-matrix.md) wurde integriert.

Es wurde ein neuer Abschnitt mit Richtlinien für die Überwachung in Campaign Classic hinzugefügt. [Mehr dazu](../../production/using/monitoring-guidelines.md)

Der Abschnitt &quot;Datenschutz und Einverständnis&quot; wurde um detailliertere Informationen und nützliche Links erweitert. [Mehr dazu](../../platform/using/privacy-and-recommendations.md)

Die Seite &quot;Datenschutzverwaltung in Campaign Classic&quot; wurde mit Informationen zum Feld &quot;Vorschrift&quot; aktualisiert. Dieses Feld ist jetzt bei Verwendung der API verfügbar, die die Einrichtung eines automatischen Prozesses für Datenschutzanfragen ermöglicht. [Mehr dazu](https://helpx.adobe.com/ie/campaign/kb/acc-privacy.html#ManagingPrivacyRequests)

Die Seite mit der Übersicht über die Datenschutzverwaltung wurde aktualisiert und enthält nun Informationen zum thailändischen Datenschutzgesetz (PDPA) und zum brasilianischen Datenschutzgesetz (Lei Geral de Proteção de Dados, LGPD) – [mehr dazu](../../platform/using/privacy-and-recommendations.md)

Es wurden Informationen zu Sub-Workflow-Protokollen und dem Verhalten im Fehlerfall hinzugefügt. [Mehr dazu](../../workflow/using/sub-workflow.md)

Im Abschnitt **[!UICONTROL Planungsaktivität]** wurden Best Practices hinzugefügt. [Mehr dazu](../../workflow/using/scheduler.md)

### Juni 2020 {#june-2020}

Der Abschnitt über das Entfernen einer unter Quarantäne gestellten Adresse wurde aktualisiert. Dies umfasst eine Klarstellung der Fälle, in denen Adressen automatisch aus der Quarantäneliste entfernt werden. [Mehr dazu](../../delivery/using/understanding-quarantine-management.md#removing-a-quarantined-address)

Es wurden Anwendungsfälle zum [Verschlüsseln](../../platform/using/zip-encrypt.md) und [Entschlüsseln](../../platform/using/unzip-decrypt.md) von Daten mit dem Control Panel und mit Campaign-Workflows hinzugefügt.

Die Seite über die Integration von Experience Cloud Triggers und Adobe Campaign Classic wurde [hierher](../../integrations/using/about-triggers.md) verschoben.

### Juli 2020 {#release-20-2}

**Neue Funktionen in Version 20.2**

Unterstützung für Emoticons – [mehr dazu](../../delivery/using/customizing-emoticon-list.md)

Azure Synapse FDA-Connector – [mehr dazu](../../installation/using/configure-fda-synapse.md)

Datenschutzgesetze in Thailand und Brasilien – [mehr dazu](https://helpx.adobe.com/de/campaign/kb/acc-privacy.html#ManagingPrivacyRequests)

**Weitere Dokumentationsaktualisierungen zu dieser Version**

Die neue Option zum Rückgängigmachen der Veröffentlichung einer Transaktionsnachrichtenvorlage wird in [diesem Abschnitt](../../message-center/using/publishing-message-templates.md#template-unpublication) beschrieben.

Neue Optionen wurden zur Liste der Campaign Classic-Optionen hinzugefügt. Mit diesen Optionen können Einschränkungen beim Versand von E-Mails festgelegt werden, die von einer personalisierten URL und Anhängen heruntergeladene Bilder enthalten. [Mehr dazu](../../installation/using/configuring-campaign-options.md#delivery)

Die neue Option **Versandteile in der Datenbank vorbereiten** wird in [diesem Abschnitt](../../delivery/using/steps-validating-the-delivery.md#improving-delivery-analysis) beschrieben.

Der Abschnitt &quot;Validieren des Versands&quot; wurde klarer gestaltet und aktualisiert. [Mehr dazu](../../delivery/using/steps-validating-the-delivery.md)

Die Parameter für den neuen Trackinglink-Signaturmechanismus wurden dem Abschnitt [Server-Konfigurationsdatei](../../installation/using/the-server-configuration-file.md) hinzugefügt.

Die Kompatibilitätsmatrix wurde aktualisiert. [Mehr dazu](https://helpx.adobe.com/de/campaign/kb/compatibility-matrix.html)

Der Abschnitt zum Bereinigungs-Workflow wurde aktualisiert. [Weitere Informationen](../../production/using/database-cleanup-workflow.md)

Die Campaign-Netzwerkendpunkte wurden in diesen [Abschnitt](../../installation/using/campaign-network-endpoints.md) verschoben.

Der Abschnitt &quot;Spam Assassin-Installation&quot; wurde mit dem Namen der neuen Installationsdatei aktualisiert. [Weitere Informationen](../../installation/using/configuring-spamassassin.md#installing-spamassassin)

Der Abschnitt zur Duplizierung von Umgebungen wurde aktualisiert. [Weitere Informationen](../../production/using/duplicating-environments.md#step-2---export-the-target-environment-configuration--dev-)

### Mai 2020 {#may-2020}

Der Abschnitt zum Monitoring der Zustellbarkeit wurde an eine andere Stelle verschoben und überarbeitet. [Mehr dazu](../../delivery/using/monitoring-deliverability.md)

Der Abschnitt zur Behebung von Problemen mit der Zustellbarkeit wurde verschoben und überarbeitet. [Mehr dazu](../../delivery/using/deliverability-faq.md)

Die Zustellbarkeitsrichtlinien beim Start einer neuen Plattform wurden überarbeitet. [Mehr dazu](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=de#transition-process)

Der Abschnitt zum Senden von Transaktions-E-Mails mit Anhängen wurde an eine andere Stelle verschoben und aktualisiert. [Mehr dazu](../../message-center/using/transactional-email-with-attachments.md)

Der Abschnitt mit Best Practices für Datenpackages wurde verschoben und überarbeitet. [Mehr dazu](../../platform/using/working-with-data-packages.md#data-package-best-practices)

### April 2020 {#april-2020}

Die Tabelle mit den FDA-Berechtigungen wurde in die Dokumentation „Zugriff auf eine externe Datenbank (FDA)“ verschoben. [Mehr dazu](../../installation/using/remote-database-access-rights.md)

Die FAQs wurden um Tipps zum Löschen von Soft Cache und Hard Cache erweitert. [Mehr dazu](../../platform/using/faq-campaign-config.md#perform-soft-cache-clear)

Der Abschnitt mit Best Practices für das Datenmodell enthält jetzt zusätzliche Informationen über Indizes. [Mehr dazu](../../configuration/using/data-model-best-practices.md#indexes)

Der Abschnitt zum integrierten Datenmodell von Adobe Campaign enthält jetzt zusätzliche Details zu den einzelnen Tabellen. [Mehr dazu](../../configuration/using/data-model-description.md)

Anwendungsbeispiele für Workflows wurden aktualisiert und in thematische Bereiche neu angeordnet. [Mehr dazu](../../workflow/using/about-workflow-use-cases.md)

Die Abschnitte [Bounce-Message-Qualifizierung](../../delivery/using/understanding-delivery-failures.md#bounce-mail-qualification) und [E-Mail-Verwaltungsregeln](../../delivery/using/understanding-delivery-failures.md#email-management-rules) enthalten aktualisierte Informationen.

Der Artikel zum Adobe Campaign Enhanced MTA wurde aktualisiert. Er gilt jetzt nur für Campaign Classic. [Mehr dazu](https://helpx.adobe.com/de/campaign/kb/acc-campaign-enhanced-mta.html)

### März 2020 {#march-2020}

Die Seite mit Best Practices für das Datenmodell enthält jetzt neue Abschnitte wie [Sequenzen](../../configuration/using/data-model-best-practices.md#sequences), [Leistung](../../configuration/using/data-model-best-practices.md#performance) und [große Tabellen](../../configuration/using/data-model-best-practices.md#large-tables). [Mehr dazu](../../configuration/using/data-model-best-practices.md)

Ein neuer Abschnitt, in dem das integrierte Datenmodell von Adobe Campaign beschrieben wird; Interaktion zwischen Tabellen ist nun verfügbar. [Mehr dazu](../../configuration/using/data-model-description.md)

Zusätzliche wichtige Links wurden zur Startseite der Dokumentation hinzugefügt. [Mehr dazu](../../campaign-classic-home.md)

Es wurde ein Anwendungsfall hinzugefügt, der beschreibt, wie ein dynamisches Angebot aus Adobe Target in eine E-Mail in Adobe Campaign integriert werden kann. [Mehr dazu](../../integrations/using/inserting-a-dynamic-image.md)

Ein neuer Abschnitt mit den verschiedenen Sprachen, die in Adobe Campaign verfügbar sind, ist jetzt verfügbar. [Mehr dazu](../../platform/using/adobe-campaign-workspace.md#languages)

Die Seite zu Richtlinien für die Zugriffsverwaltung enthält jetzt zusätzliche Informationen zu spezifischen Berechtigungen. [Mehr dazu](../../platform/using/access-management-named-rights.md)

### Februar 2020 {#february-2020}

Es gibt jetzt einen neuen Abschnitt, in dem Best Practices und wichtige Empfehlungen zum Entwerfen des Adobe Campaign-Datenmodells erläutert werden. [Mehr dazu](../../configuration/using/data-model-best-practices.md)

Es gibt einen neuen Abschnitt zu technischen E-Mail-Konfigurationen. [Mehr dazu](../../installation/using/email-deliverability.md)

Die häufig gestellten Fragen zur Zustellbarkeit enthalten jetzt zusätzliche Details zur Fehlernachricht &quot;Kontingente ausgeschöpft&quot;. [Mehr dazu](https://helpx.adobe.com/de/campaign/kb/acc-deliverability-faq.html#FAQ)

AMP for E-Mail wird jetzt von neuen E-Mail-Anbietern unterstützt: Die zugehörige Dokumentation wurde aktualisiert. [Mehr dazu](../../delivery/using/defining-interactive-content.md)

Der Abschnitt zur E-Mail-Archivierung wurde verbessert. [Mehr dazu](../../installation/using/email-archiving.md#recommendations-and-limitations)

### Januar 2020 {#release-20-1}

**Neue Funktionen in Version 20.1**

Snowflake FDA-Connector – [mehr dazu](../../installation/using/configure-fda-snowflake.md)

Hadoop FDA Connector-Erweiterungen – [mehr dazu](../../installation/using/configure-fda-hadoop.md)

**Weitere Dokumentationsaktualisierungen zu dieser Version**

Die Anleitungen für [Installation](../../installation/using/general-architecture.md), [Produktion](../../production/using/foreword.md) und [Konfiguration](../../configuration/using/additional-parameters.md) wurden mit der neuen systemd-Einheit aktualisiert, die vom nlserver-Dienststart verwendet wird. Sie können weiterhin &quot;/etc/init.d/nlserver6&quot; verwenden. Adobe empfiehlt jedoch, für die Interaktion mit dem nlserver-Dienst ab jetzt den Befehl &quot;systemctl&quot; zu verwenden.

Das Installationshandbuch wurde aktualisiert und mit der neuesten Version der Kompatibilitätsmatrix synchronisiert. Neue unterstützte Systeme wurden hinzugefügt. Vorkommen von veralteten und nicht mehr unterstützten Systemen wurden entfernt. [Mehr dazu](../../installation/using/general-architecture.md)

Die Kompatibilitätsmatrix wurde mit den Hadoop 3.0- und Snowflake-FDA-Connectoren aktualisiert. [Mehr dazu](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)

Eine Best Practice zur IP-Affinität wurde dem Installationshandbuch hinzugefügt. [Mehr dazu](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use)

Der Abschnitt zum Workflow für die Datenbankbereinigung wurde aktualisiert. Die bereitgestellten Batch-Zahlen spiegeln nun die Code-Implementierung wider. [Mehr dazu](../../production/using/database-cleanup-workflow.md)

Eine Einschränkung zu FDA über HTTP wurde dem Handbuch zu Transaktionsnachrichten hinzugefügt. [Mehr dazu](../../production/using/database-cleanup-workflow.md)

Es wurden Informationen zu der neuen Option hinzugefügt, mit der Sie einen Timeout-Zeitraum für die Workflow-Aktivitäten **[!UICONTROL JavaScript-Code]** und **[!UICONTROL Erweiterter JavaScript-Code]** definieren können. [Mehr dazu](../../workflow/using/sql-code-and-javascript-code.md)

Informationen wurden zur neuen Ansicht **[!UICONTROL Start ausstehend]** hinzugefügt, die unter dem Knoten **[!UICONTROL Administration]** > **[!UICONTROL Audit]** > **[!UICONTROL Status der Workflows]** verfügbar ist. [Mehr dazu](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

Der Leitfaden [Senden von Push-Benachrichtigungen](../../delivery/using/about-mobile-app-channel.md) wurde verschoben, neu organisiert und mit klareren Informationen optimiert.

Der neue Parameter für die URL-Berichtkonfiguration wird [hier](../../reporting/using/properties-of-the-report.md#defining-additional-settings) erläutert.

Die **On-Premise- und Hosted-Leistungsmatrix von Campaign Classic** wurde mit den neuen FDA-Connectoren aktualisiert. [Mehr dazu](../../installation/using/capability-matrix.md).

Die Seite mit der **Campaign Classic-Leistungsmatrix** wurde aktualisiert. [Mehr dazu](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)

Der neue Workflow zur **[!UICONTROL Bereinigung von Nmsaddress]** wird [hier](../../production/using/database-cleanup-workflow.md#cleanup-of-nmsaddress) erläutert.

Bei Verwendung einer Abfrageaktivität in einem Workflow wurde eine Einschränkung hinzugefügt. [Mehr dazu](../../workflow/using/query.md)

Es wurde ein neuer Abschnitt hinzugefügt, in dem die verbesserten Validierungsregeln für E-Mail-Adressen detailliert beschrieben werden, die im Falle eines Softbounce eine Adresse unter Quarantäne stellen. [Mehr dazu](../../delivery/using/understanding-quarantine-management.md#soft-error-management)

Der Parameter aus der Konfigurationsdatei, der angibt, ob eine Instanz den erweiterten MTA verwendet oder nicht, wurde in die Dokumentation aufgenommen. [Mehr dazu](../../installation/using/the-server-configuration-file.md#mta)

Der Abschnitt „Zulieferbarkeit“ wurde verschoben, neu organisiert und mit aktualisierten Inhalten erweitert. [Mehr dazu](../../delivery/using/about-deliverability.md)

Ein neuer Abschnitt mit den Grundlagen des Adobe Campaign Classic-Datenmodells und dem Zugriff auf die Beschreibung der einzelnen Tabellen ist jetzt verfügbar. [Mehr dazu](../../configuration/using/about-data-model.md)

Der Artikel zu Adobe Campaign Enhanced MTA wurde mit detaillierteren Informationen zur Installation eines spezifischen Typologie-Packages in Instanzen aktualisiert, die die erforderlichen Enhanced MTA-Header nicht zu jeder Nachricht hinzufügen. [Mehr dazu](https://helpx.adobe.com/de/campaign/kb/acc-campaign-enhanced-mta.html#impacts)

Die Anwendungsbeispiele im Zusammenhang mit der Abfragegestaltung wurden in separate Abschnitte umstrukturiert. [Mehr dazu](../../workflow/using/querying-recipient-table.md)

Ein neuer Abschnitt über Tipps und Tricks zur Angebotsverwaltung und zum Einsatz des Interaction-Modules in Adobe Campaign Classic ist jetzt verfügbar. [Mehr dazu](../../interaction/using/interaction-best-practices.md#tips-managing-offers)

Die Interaction-Dokumentation wurde mit Links zu verschiedenen Videos angereichert, die zum besseren Verständnis der Verwaltung von Angeboten beitragen. [Mehr dazu](../../interaction/using/interaction-and-offer-management.md)

Der Best Practice-Artikel über die Optimierung der auf Ihrer Instanz laufenden Abfragen wurde in die Dokumentation integriert. [Mehr dazu](../../workflow/using/query.md#optimizing-queries)

Das Reporting-Handbuch wurde aktualisiert und neu organisiert. [Mehr dazu](../../reporting/using/about-adobe-campaign-reporting-tools.md)

Es wurde ein Beispiel für die Verwendung einer Instanzvariablen in einem Workflow hinzugefügt. [Mehr dazu](../../workflow/using/javascript-scripts-and-templates.md)

## 2019

### Dezember 2019 {#december-2019}

Die Option „WdbcOptions_TempDbName“ wurde der Liste der Kampagnenoptionen hinzugefügt. [Mehr dazu](../../installation/using/configuring-campaign-options.md)

Die Seite „FDA-Matrix“ wurde [hierher](../../installation/using/remote-database-access-rights.md) verschoben.

Die Seite „Zugriffsberechtigungsmatrix“ wurde [hierher](https://experienceleague.adobe.com/docs/campaign-classic/assets/access-rights-matrix.pdf?lang=de) verschoben.

Der Abschnitt, der beschreibt, wie man interaktive Inhalte mit AMP definiert, wurde verschoben. [Mehr dazu](../../delivery/using/defining-interactive-content.md)

**Neue Funktionen in Version 19.2**

California Consumer Privacy Act (CCPA) – [mehr dazu](https://helpx.adobe.com/de/campaign/kb/acc-privacy.html)

Interaktive Inhalte mit AMP – [mehr dazu](../../delivery/using/defining-interactive-content.md)

Workflow-Live-Monitoring – [mehr dazu](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

Sicherer SMS-Versand (TLS) – [mehr dazu](https://helpx.adobe.com/de/campaign/kb/sms-connector-protocol-and-settings.html)

**Weitere Dokumentationsaktualisierungen zu dieser Version**

Die Adobe Campaign Enhanced MTA-Dokumentation ist jetzt verfügbar. [Mehr dazu](https://helpx.adobe.com/campaign/kb/acc-campaign-enhanced-mta.html)

Es wurde ein neuer Abschnitt hinzugefügt, in dem beschrieben wird, wie Sie Fehler in einem Workflow beheben können, der im Status „Schnellstmöglicher Start“ in einer Kampagne verbleibt.  [Mehr dazu](../../production/using/workflow-execution.md#start-as-soon-as-possible-in-campaigns)

Die neuen Optionen „NmsOperation_DeliveryPreparationWindow“ und „WdbcKillSessionPolicy“ wurden zur Liste der Campaign-Optionen hinzugefügt. [Mehr dazu](../../installation/using/configuring-campaign-options.md)

Ein neues Dokument mit den Grundlagen des Adobe Campaign Classic-Datenmodells ist jetzt verfügbar. [Mehr dazu](https://helpx.adobe.com/de/campaign/kb/acc-datamodel.html)

Die neue Option **Maximale Laufzeit der Personalisierung** in den Versandeigenschaften wird in diesem [Abschnitt](../../delivery/using/personalization-fields.md#timing-out-personalization) beschrieben.

Die Beispiele für API-Aufrufe mit **HttpServletRequest** mit logon() und query() wurden aktualisiert. [Mehr dazu](../../configuration/using/web-service-calls.md)

In der Schemadefinition wurde eine Empfehlung für das Attribut **sqlDefault** hinzugefügt. [Mehr dazu](../../configuration/using/schema/attribute.md)).

Die Integration zwischen Adobe Campaign und der Adobe Echtzeit-Kundendatenplattform wird jetzt im Handbuch **Integration mit Adobe Experience Cloud** beschrieben. [Mehr dazu](../../integrations/using/about-campaign-integrations.md)

### November 2019 {#november-2019}

Den Abschnitten [Multiplexing des Mid-Sourcing-Servers](../../installation/using/mid-sourcing-server.md#multiplexing-the-mid-sourcing-server) und [Mehrere Kontrollinstanzen](../../message-center/using/transactional-messaging-architecture.md#supporting-several-control-instances) wurde eine Warnung hinzugefügt, die darauf hinweist, dass diese Implementierungen für vollständig gehostete und hybride Clients nicht unterstützt werden.

Es wurde ein neuer Abschnitt hinzugefügt, in dem beschrieben wird, wie die beim Senden einer E-Mail verwendete Zeichencodierung erzwungen wird. [Mehr dazu](../../delivery/using/sending-messages.md#character-encoding)

Der Abschnitt „Zugriffsverwaltung“ wurde mit dem **Datenschutzrecht** aktualisiert. [Mehr dazu](../../platform/using/access-management-named-rights.md)

Es wurden Informationen hinzugefügt, die festlegen, dass der Inhalt von Personalisierungsfeldern 1024 Zeichen nicht überschreiten darf. [Mehr dazu](../../delivery/using/personalization-fields.md)

Die Control Panel-Dokumentation wurde in den neuen kollaborativen Dokumentationssatz integriert. [Mehr dazu](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=de)

Die ersten Schritte zum Thema Best Practices für den Versand wurden aktualisiert. [Mehr dazu](../../delivery/using/delivery-best-practices.md)

### Oktober 2019 {#october-2019}

Die Liste der Fehlermeldungen für Campaign wurde aktualisiert – [Mehr dazu](https://experienceleague.adobe.com/developer/campaign-errors/error_codes.html?lang=de)

Die ersten Schritte zum Thema DSGVO wurden verbessert und erweitert. Es handelt sich nun um eine Dokumentation rund um die Gewährleistung von Datenschutz gemäß den Bestimmungen der DSGVO und des CCPA. [Mehr dazu](https://helpx.adobe.com/content/help/de/campaign/kb/campaign-privacy.html)

Eine neue Seite zur Fehlerbehebung wurde zum Tracking in Campaign Classic hinzugefügt. [Mehr dazu](https://helpx.adobe.com/de/campaign/kb/classic-tracking-troubleshooting.html)

Eine neue Seite mit Best Practices für Adobe Analytics Connector wurde hinzugefügt. [Weitere Informationen zu Adobe Analytics Connector](../../platform/using/adobe-analytics-connector.md)

Die ersten Schritte zum Thema Best Practices beim Versand wurden aktualisiert – [Mehr dazu](../../delivery/using/delivery-best-practices.md)

In der Dokumentation zum SMS-Kanal wurde eine Empfehlung hinzugefügt, um Probleme bei der Verwendung mehrerer externer Konten zu vermeiden, indem der erweiterte allgemeine SMPP-Connector mit demselben Provider-Konto genutzt wird. [Mehr dazu](../../delivery/using/sms-set-up.md#automatic-reply)

In der Dokumentation zur Planungsaktivität wurden Informationen darüber hinzugefügt, wie mehrere gleichzeitige Ausführungen eines Workflows verhindert werden können. [Mehr dazu](../../workflow/using/scheduler.md)

Die Schritte zum Konfigurieren des Inbox Renderings für On-Premise-Installationen wurden der Dokumentation hinzugefügt. [Mehr dazu](../../delivery/using/inbox-rendering.md#activating-inbox-rendering)

### September 2019 {#september-2019}

Eine neue Seite wurde hinzugefügt, um allgemeine Richtlinien für die Wartung von Campaign Classic bereitzustellen. [Mehr dazu](../../production/using/monitoring-guidelines.md)

Die Informationen zum Workflow-Monitoring wurden in einem neuen Abschnitt zusammengefasst. [Mehr dazu](../../workflow/using/monitoring-workflow-execution.md)

Eine neue Seite mit allgemeinen Richtlinien für das Tracking in Adobe Campaign Classic wurde hinzugefügt. [Mehr dazu](https://helpx.adobe.com/de/campaign/kb/acc-tracking.html)

Die Best Practices für die Leistungsverbesserung von Workflows und Sendungen wurden aktualisiert. [Weitere Informationen zu Workflows](../../workflow/using/workflow-best-practices.md) und [Sendungen](../../delivery/using/delivery-performances.md#best-practices-performance).

### Mai 2019 {#release-19-1}

**Neue Funktionen in Version 19.1**

Control Panel – [mehr dazu](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html)

Audit-Protokoll – [mehr dazu](../../production/using/audit-trail.md)

**Weitere Dokumentationsaktualisierungen zu dieser Version**

Es wurden neue häufig gestellte Fragen zur Build-Aktualisierung erstellt. [Mehr dazu](https://helpx.adobe.com/de/campaign/kb/build-upgrade-faq.html)

Die [Kompatibilitätsmatrix](compatibility-matrix.md) wurde aktualisiert. Die Liste der unterstützten Datenbanksysteme sowie die Android-/iOS-Versionen und die zugehörigen SDKs wurden aktualisiert. Die Kompatibilitätsmatrix 19.0 wurde archiviert.

Die Seite mit veralteten und entfernten Funktionen in Campaign Classic wurde aktualisiert. [Mehr dazu](deprecated-features.md)

Die Beschreibung der Server-Konfigurationsdatei wurde dem Installationshandbuch hinzugefügt. [Mehr dazu](../../installation/using/the-server-configuration-file.md)

Es wurde ein Abschnitt hinzugefügt, in dem die Installations- und Konfigurationsschritte für gehostete und hybride Modelle beschrieben werden. [Mehr dazu](../../installation/using/hosting-models.md)

Es wurde ein Abschnitt hinzugefügt, der die Deinstallationsschritte des Campaign-Servers beschreibt. [Mehr dazu](../../installation/using/uninstalling-campaign.md)

Die ersten Schritte zum Thema [Sicherheit](https://helpx.adobe.com/de/campaign/kb/acc-security.html), [Zustellbarkeit](../../delivery/using/about-deliverability.md) und [Datenschutz](../../platform/using/privacy-management.md) wurden aktualisiert.

Die Beschreibung der Workflow-Option für die Vorab-Bearbeitung wurde aktualisiert, um Produktänderungen widerzuspiegeln. [Mehr dazu](../../workflow/using/data-loading--file-.md)

Die Technote zu den Marketing Cloud-Triggers wurde aktualisiert. [Mehr dazu](../../integrations/using/about-triggers.md)

Die Liste der Fehlermeldungen wurde aktualisiert. [Mehr dazu](https://experienceleague.adobe.com/developer/campaign-errors/error_codes.html)

Es wurden weitere Informationen zu SOAP-Authentifizierungsmethoden für Transaktionsnachrichten hinzugefügt. [Mehr dazu](../../message-center/using/event-description.md)

Die Apache-Konfigurationsschritte wurden aktualisiert. [Mehr dazu](../../installation/using/integration-into-a-web-server-for-linux.md)

Es wurde eine neue Seite mit der Liste der Endpunkte für Campaign Classic hinzugefügt. [Mehr dazu](../../installation/using/campaign-network-endpoints.md)

Der Artikel zu den Best Practices für Datenpackages wurde aktualisiert. [Mehr dazu](../../configuration/using/data-model-best-practices.md)

Die Dokumentation zur Angebotsverwaltung wurde um einen neuen Abschnitt mit Best Practices erweitert. [Mehr dazu](../../interaction/using/interaction-best-practices.md)

Es wurde ein neuer Knowledgebase-Artikel zur Verwendung des Angebotskatalogs in Adobe Campaign Classic erstellt. [Mehr dazu](https://helpx.adobe.com/de/campaign/kb/offer-best-practices.html)

Der Abschnitt zur Unter-Workflow-Aktivität wurde um ein Anwendungsbeispiel erweitert. [Mehr dazu](../../workflow/using/sub-workflow.md)

Die Seite [Funktionsmatrix für On-Premise- und gehostete Campaign Classic-Versionen](../../installation/using/capability-matrix.md) wurde um Informationen zu E-Mail-BCC erweitert.

Die Dokumentation zu Transaktionsnachrichten wurde mit einem Hinweis zur Vorlagenveröffentlichung aktualisiert. [Mehr dazu](../../message-center/using/publishing-message-templates.md#template-publication)

Der Abschnitt über nicht verarbeitete Bounce Messages wurde um weitere Details zu den Feldern „Weiterleitungsadresse“ und „Fehleradresse“ erweitert. [Mehr dazu](../../installation/using/deploying-an-instance.md)

Ein neuer Abschnitt über Best Practices zur Workflow-Planung wurde hinzugefügt. [Mehr dazu](../../workflow/using/workflow-best-practices.md)

Der Liste der Campaign-Optionen wurden zwei neue Optionen hinzugefügt: XtkSecurity_Restrict_EditXML und NmsOperation_OperationMgtDebug. [Mehr dazu](../../installation/using/configuring-campaign-options.md)

Es wurden Informationen zu den verschiedenen in Campaign Classic verfügbaren externen Konten und deren Konfiguration hinzugefügt. [Mehr dazu](../../installation/using/external-accounts.md)

Der Abschnitt über Analytics Connector wurde entsprechend den an der Benutzeroberfläche vorgenommenen Änderungen aktualisiert. [Mehr dazu](../../platform/using/adobe-analytics-connector.md)

Es wurden Informationen zum Billing-Bericht hinzugefügt. [Mehr dazu](../../production/using/monitoring-processes.md)

Die Dokumentation zur Integration freigegebener Audiences wurde aktualisiert.
[Mehr dazu](../../integrations/using/configuring-shared-audiences-integration-in-adobe-campaign.md)

Die folgenden Technotes wurden aktualisiert: [SMS-Connector-Protokoll und Einstellungen](https://helpx.adobe.com/campaign/kb/sms-connector-protocol-and-settings.html) und [Automatische Erzeugung von Sequenzen](https://helpx.adobe.com/de/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence).

Der Abschnitt „Technische Workflows“ wurde aktualisiert. [Mehr dazu](../../workflow/using/about-technical-workflows.md)

Die Namenseinrichtung für die Campaign-Domain wurde verbessert und aktualisiert.

Das Migrationsverfahren für Android-Apps von Google Cloud Messaging (GCM) zu Firebase Cloud Messaging (FCM) wurde aktualisiert. [Mehr dazu](https://helpx.adobe.com/de/campaign/kb/migrate-to-fcm.html)

Das Handbuch zur Dimensionierung von Hardware für Campaign wurde aktualisiert. [Mehr dazu](https://helpx.adobe.com/de/campaign/kb/hardware-sizing-guide.html)

Informationen zum Query Banding für das externe Teradata-Konto wurden hinzugefügt. [Mehr dazu](../../installation/using/external-accounts.md)

### Januar 2019{#release-doc-16-01-2019}

Die Technote zu den Marketing Cloud-Triggers wurde aktualisiert. [Mehr dazu](../../integrations/using/about-triggers.md)

Im Abschnitt über die Angebotsvalidierung wurde ein Hinweis hinzugefügt, dass die Aussage „Validierter Inhalt“ darauf hinweist, dass der Prozess der Inhaltsvalidierung abgeschlossen wurde, unabhängig davon, ob alle Angebote aktiviert/validiert wurden oder nicht. [Mehr dazu](../../interaction/using/offer-catalog-overview.md)

Im Installationshandbuch wurde ein neuer Abschnitt mit Optionen aus dem Knoten „Administration/Plattform/Optionen“ hinzugefügt. [Mehr dazu](../../installation/using/configuring-campaign-options.md)

Es wurden Informationen über die Verwendung von Testadressen zum Schutz Ihrer Mailing-Liste hinzugefügt. [Mehr dazu](../../delivery/using/creating-seed-addresses.md)

Wichtige Schritte beim Erstellen und Durchführen eines Versands wurden in einem neuen Abschnitt zusammengefasst, wobei bei Bedarf auf die verschiedenen Kanäle verwiesen wird. [Mehr dazu](../../delivery/using/steps-about-delivery-creation-steps.md)

Der Abschnitt [E-Mail-Archivierung](../../installation/using/email-archiving.md) wurde verschoben, neu organisiert und mit präziseren Informationen verbessert:

* Es wurden Best Practices hinsichtlich der Parameter für E-Mails pro Verbindung und BCC-Sende-IPs hinzugefügt.

* Die Schritte zum Aktualisieren auf das neue E-Mail-Archivierungssystem (BCC) wurden aktualisiert, falls Sie die E-Mail-Archivierung bereits mit einem älteren Build (vor Adobe Campaign 17.2 – Build 8795) verwendet haben.

Dem Handbuch für die Automatisierung mithilfe von Workflows wurde ein Anwendungsbeispiel hinzugefügt: Benutzern personalisierte Warnungen senden. [Mehr dazu](../../workflow/using/sending-personalized-alerts-to-operators.md)

Der Abschnitt „Auf eine neue Version migrieren“ wurde aktualisiert. Die Dokumentation beschreibt jetzt nur die Schritte für eine Migration von einer älteren Version zu Adobe Campaign Classic v7, da eine Migration zu Adobe Campaign v6.11 nicht mehr möglich ist. [Mehr dazu](../../migration/using/about-migration.md)

Der Abschnitt „Weitere Zustellversuche nach einem vorübergehend fehlgeschlagenen Versand“ wurde präzisiert. [Mehr dazu](../../delivery/using/understanding-delivery-failures.md)

Dem Abschnitt „E-Mail-Inhalt erstellen“ wurden Links zum Abschnitt „Digital Content Editor“ hinzugefügt. [Mehr dazu](../../delivery/using/defining-the-email-content.md)

Der Abschnitt „Transaktionsnachrichten-Architektur“ wurde mit einer Warnung aktualisiert, in der angegeben wird, dass die Kontroll- und Ausführungsinstanzen nicht auf demselben Rechner installiert werden können. [Mehr dazu](../../message-center/using/transactional-messaging-architecture.md)

Der Abschnitt „Workflow-Monitoring“ wurde mit einem Hinweis für Builds zwischen 8700 und 8977 (18.10) aktualisiert, einschließlich eines Links zur Technote zur Installation des Workflow-Heatmap-Packages für diese Builds. [Mehr dazu](../../workflow/using/heatmap.md)

Es wurde ein Anwendungsbeispiel zum Senden einer E-Mail mit benutzerdefinierten Datenfeldern mithilfe der Anreicherungsaktivität in einem Workflow hinzugefügt. [Mehr dazu](../../workflow/using/email-enrichment-with-custom-date-fields.md)

Die Funktionsvideos wurden [hierher](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=de) verschoben.
