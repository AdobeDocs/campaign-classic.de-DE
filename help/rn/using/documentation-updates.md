---
product: campaign
title: Aktualisierungen der Dokumentation zu Adobe Campaign Classic v7
description: Auf dieser Seite werden alle neuen Funktionen und Aktualisierungen in der Dokumentation zu Adobe Campaign Classic aufgelistet.
feature: Release Notes
badge-v7-only: label="v7" type="Informative" tooltip="Gilt nur für Campaign Classic v7"
role: User
level: Beginner
exl-id: 07c1f4a3-cf16-4a9b-b402-e13258799f91
source-git-commit: 8ecb5aba9a070276927e97586ed463ab485717d6
workflow-type: tm+mt
source-wordcount: '3668'
ht-degree: 98%

---

# Aktualisierungen der Dokumentation{#documentation-updates}

Auf dieser Seite werden alle neuen Funktionen und Dokumentationsaktualisierungen pro Monat und Campaign-Version aufgeführt.

Die entsprechenden Aktualisierungen finden Sie in den [Versionshinweisen zu Adobe Campaign Classic](../../rn/using/latest-release.md).

## 2023

### November 2023

JWT (JSON Web Tokens) wird derzeit abgeschrieben und durch OAuth ersetzt. Die Umstellung erfolgt schrittweise innerhalb der kommenden Campaign-Versionen. Die Dokumentation wird entsprechend diesen Aktualisierungen aktualisiert.

### August 2023

Es wurde eine Begrenzung hinzugefügt, die besagt, dass Sie mit Adobe Campaign keine komprimierten Dateien entpacken können, die größer als 4 GB sind. [Weitere Informationen](../../platform/using/unzip-decrypt.md)

### April 2023

Es wurde eine Technote zur Aktivierung von Microsoft Edge Chromium in On-Premise-/Hybridumgebungen hinzugefügt. [Weitere Informationen](../../technotes/using/edge-chromium.md)

### März 2023

Der Abschnitt zu den Versionshinweisen wurde aktualisiert und enthält jetzt Verbesserungen und Patches in Version 7.3.3. [Weitere Informationen](latest-release.md)


+++ 2022


## November 2022 {#nov-2022}

Der Abschnitt zu den Versionshinweisen wurde aktualisiert und enthält jetzt Verbesserungen und Patches in Version 7.3.2. [Weitere Informationen](latest-release.md)

Die Kompatibilitätsmatrix wurde aktualisiert und durch die Teradata 17-Unterstützung ergänzt. [Weitere Informationen](compatibility-matrix.md)

Der Abschnitt zur Datei- und Ressourcenverwaltung wurde durch zusätzliche Informationen zum Attribut **uploadWhiteList** ergänzt. [Weitere Informationen](../../installation/using/file-res-management.md)

Die Dokumentation zu Sicherheitszonen wurde durch zusätzliche Informationen zum Attribut **allowDebug** ergänzt. [Weitere Informationen](../../installation/using/security-zones.md#recommendations)

Das Migrationshandbuch wurde aktualisiert. Verweise auf nicht unterstützte Adobe Campaign-Versionen wurden entfernt. [Weitere Informationen](../../migration/using/about-migration.md)


## Juli 2022 {#july-2022}

Der Wechsel zum neuen Zustellbarkeits-Server wird in einer neuen Technote beschrieben. [Weitere Informationen](../../technotes/using/deliverability-server.md)

**Dokumentationsaktualisierungen für Version 7.3.1**

Aktualisierte Kompatibilitätsmatrix. [Mehr dazu](compatibility-matrix.md)

Der Abschnitt zu Versionshinweisen wurde aktualisiert. [Mehr dazu](rn-overview.md)

Zeitkritische Benachrichtigungen mit iOS 15. [Weitere Informationen](../../delivery/using/create-notifications-ios.md)


## März 2022 {#mar-2022}

Eine detaillierte Beschreibung für die Option **[!UICONTROL SMTP-Versand testen]** wurde hinzugefügt. [Mehr dazu](../../delivery/using/steps-sending-the-delivery.md#delivery-additiona-parameters)

Die Seite &quot;Erste Schritte mit Upgrades&quot; wurde aktualisiert, um die Upgrade-Richtlinien für die Campaign-Konsole zu erläutern. [Mehr dazu](../../rn/using/rn-overview.md)

Der neue Campaign-Build v7.2.2 ist jetzt verfügbar. [Mehr dazu](../../rn/using/latest-release.md)

<!--Added troubleshooting information related to the ACS connector. [Read more](../../integrations/using/troubleshooting-the-acs-connector.md)-->

Legacy-PostgreSQL-Versionen, die das Ende des Lebenszyklus erreicht haben, wurden zur Seite [Eingestellte und entfernte Funktionen](../../rn/using/deprecated-features.md#dbe-eol) hinzugefügt.

## Februar 2022 {#february-2022}

Der Abschnitt zur Aktivität **Dateiversand** wurde mit einer Erinnerung ergänzt, in der darauf hingewiesen wird, dass die Größe des archivierten Inhalts im SFTP-Verzeichnis manuell überwacht werden muss, falls die Option **Quelldateien nach der Übertragung löschen** nicht ausgewählt wird. [Weitere Informationen](../../workflow/using/file-transfer.md#properties)

Der Abschnitt &quot;Quarantäne vs. Blockierungsliste&quot; wurde klarer formuliert. [Weitere Informationen](../../delivery/using/understanding-quarantine-management.md#quarantine-vs-denylist)

Die Abschnitte darüber, wie eine Adresse in Quarantäne gesendet wird und wie Adressen aus der Quarantäneliste entfernt werden, wurden aktualisiert. [Weitere Informationen](../../delivery/using/understanding-quarantine-management.md#removing-a-quarantined-address)

Es wurde eine Best Practice für Workflows hinzugefügt, in der empfohlen wird, nicht mehrere Stopp-Anfragen für denselben Workflow durchzuführen. [Mehr dazu](../../workflow/using/workflow-best-practices.md)

Es wurden Informationen darüber hinzugefügt, wie verhindert werden kann, dass ein wiederkehrender Versand innerhalb einer Kampagne ausgeführt wird. [Weitere Informationen](../../workflow/using/recurring-delivery.md)

## Januar 2022 {#january-2022}

**Dokumentationsaktualisierungen in Version 7.2.1**

Aktualisierte Kompatibilitätsmatrix. [Mehr dazu](compatibility-matrix.md)

Der Abschnitt zu Versionshinweisen wurde aktualisiert. [Mehr dazu](rn-overview.md)

Die Konfiguration des externen FDA-Kontos für Snowflake wurde aktualisiert. [Mehr dazu](../../installation/using/configure-fda-snowflake.md)

Die Konfiguration des externen FDA-Kontos für Azure Synapse Analytics wurde aktualisiert. [Mehr dazu](../../installation/using/configure-fda-synapse.md#azure-external)

Der Google BigQuery FDA-Connector wurde aktualisiert. [Mehr dazu](../../installation/using/configure-fda-google-big-query.md)

Nach der Einstellung wurden die Aktionsaktivitäten für Microsoft CRM, Salesforce und Oracle CRM On Demand aus der Dokumentation entfernt.

Die neue Option **Abbruch bei Fehler** wurde zum Abschnitt zum Umgang mit Fehlern im Workflow hinzugefügt. [Mehr dazu](../../workflow/using/advanced-parameters.md#in-case-of-errors)

Die Option zur Stapel-Aktualisierung wurde in der CRM-Connector-Aktivität hinzugefügt. [Mehr dazu](../../workflow/using/crm-connector.md)

+++

+++ 2021

## Dezember 2021{#dec-2021}

Die Versionshinweise zu Campaign Classic v7 wurden neu geordnet, um die Navigation zu vereinfachen. [Mehr dazu](rn-overview.md)

Die Dokumentation zur Formularbearbeitung in Campaign wurde aktualisiert und verbessert. [Mehr dazu](../../configuration/using/editing-forms.md)

CentOS 8 hat das Ende der Lebensdauer erreicht und wird jetzt von Adobe Campaign Classic nicht mehr unterstützt. [Mehr dazu](deprecated-features.md)

## November 2021{#nov-2021}

Es wurde eine Beschränkung für eingehende SMS (MO) hinzugefügt. [Mehr dazu](../../delivery/using/sms-protocol.md#multipart)

Die Details der Migrationsprozess-Protokolle für die Bereitstellung des CRM-Connectors wurden aktualisiert. [Mehr dazu](../../migration/using/testing-the-migration.md#verification-process)

Es wurden Anforderungen bezüglich der IMS-Berechtigungen zur Implementierung der Integration zwischen Adobe Campaign und Adobe Analytics hinzugefügt. [Mehr dazu](../../platform/using/adobe-analytics-provisioning.md)

Das Datum für das Auslaufen von Adobe Analytics Data Connector wurde vom 1. März 2022 auf den 17. August 2022 geändert. [Mehr dazu](deprecated-features.md)

Es wurde ein Link zur Adobe Experience Platform Mobile SDK-Dokumentation hinzugefügt, in dem beschrieben wird, wie die Campaign-Erweiterung in Adobe Launch konfiguriert werden kann. [Mehr dazu](../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md)

Es wurde ein Abschnitt hinzugefügt, in dem beschrieben wird, wie Sie mit JavaScript Werte berechnen, Daten austauschen und bestimmte Vorgänge mithilfe von SOAP-Aufrufen ausführen können.[Mehr dazu](../../workflow/using/javascript-scripts-and-templates.md)

Es wurden Beispiele für die Implementierung von JavaScript-Codes in Workflows hinzugefügt. [Mehr dazu](../../workflow/using/javascript-in-workflows.md)


## Oktober 2021{#oct-2021}

Vorhandene Technotes wurden in den neuen Abschnitt **Technote** gruppiert.

Die Seite **Empfehlungen zur Hardware-Dimensionierung** wurde aktualisiert und zum Abschnitt **Technotes** hinzugefügt. [Mehr dazu](../../technotes/using/hardware-sizing.md)

## September 2021{#sept-2021}

**Dokumentationsaktualisierungen in Version 21.1.4**

Der Diagrammtyp **Tacho** wurde entfernt.

Screenshots und Parameter von Berichten und Web-Anwendungen wurden nach der Entfernung von Adobe Flash aktualisiert.

Die Beschreibung des technischen Workflows [Rechnungsstellung](../../production/using/monitoring-processes.md#billing-report) wurde mit einer neuen Leitplanke aktualisiert.

## August 2021{#aug-2021}

Neue Workflow-Aktivität hinzugefügt: Datenquelle ändern – [Mehr dazu](../../workflow/using/change-data-source.md)

Den Dokumentationsseiten wurden Anwendungs-Kennzeichen hinzugefügt: **Gilt für v7** nur für Campaign Classic v7-Funktionen und **für v7 und v8** für allgemeine Funktionen.

Es wurde ein Hinweis zur Integration zwischen Campaign und AEM Assets hinzugefügt, die seit Adobe Experience Manager 6.4 nicht mehr unterstützt wird. [Mehr dazu](../../integrations/using/configuring-access-to-assets.md)


## Juli 2021 {#july-2021}

Die [Campaign-Version 21.1.3](../../rn/using/latest-release.md#release-21-1-3-build-9330) ist jetzt allgemein verfügbar (General Availability, GA).


## Juni 2021 {#june-2021}

Der Abschnitt **Transaktionsnachrichten** wurde umstrukturiert. Zusätzlich wurde der Abschnitt &quot;Erste Schritte&quot; einschließlich eines [erweiterten Schemas](../../message-center/using/about-transactional-messaging.md#transactional-messaging-operating-principle) hinzugefügt, um den Prozess besser verständlich zu machen. [Mehr dazu](../../message-center/using/about-transactional-messaging.md)

**Dokumentationsaktualisierungen zu Version 21.1.3**

Integration mit Adobe Journey Orchestration – [Mehr dazu](https://experienceleague.adobe.com/docs/journeys/using/action-journeys/acc-action.html?lang=de). Auf dieser [Seite](https://experienceleague.adobe.com/docs/journeys/using/use-cases-journeys/campaign-classic-use-case.html?lang=de) wird ein Anwendungsfall im Detail vorgestellt.

Verbesserungen am LINE-Kanal – [Mehr dazu](../../delivery/using/line-channel.md)

Neuer Vertica Analytics FDA-Connector – [Weitere Infos](../../installation/using/configure-fda-vertica.md)

Neuer Google BigQuery FDA-Connector – [Weitere Informationen](../../installation/using/configure-fda-google-big-query.md)

Die technische Workflow-Beschreibung &quot;Rechnungsstellung (billing)&quot;enthält jetzt die Aufgaben, die ursprünglich von der &quot;Anzahl der aktiven Abrechnungsprofile (billingActiveContactCount)&quot;ausgeführt wurden. [Weitere Informationen](../../workflow/using/about-technical-workflows.md)

## Mai 2021 {#may-2021}

Die Dokumentation zum Workflow-Heatmap-Bericht wurde aktualisiert und verbessert. [Mehr dazu](../../workflow/using/heatmap.md)

Die Anforderungen an die Client-Konsole von Campaign wurden in der Kompatibilitätsmatrix aktualisiert. [Mehr dazu](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems)

Die Installationsschritte für die Client-Konsole von Campaign wurden verbessert und verdeutlicht. [Mehr dazu](../../installation/using/installing-the-client-console.md)

Es wurde eine neue Technote zum Signaturproblem für getrackte URLs erstellt. [Mehr dazu](../../technotes/using/tracked-urls.md)

## April 2021 {#april-2021}

Ein neuer Abschnitt beschreibt die Verwendung von Adobe Experience Platform-Quellen und -Zielen, um Daten zwischen Campaign Classic und der Echtzeit-Kundendatenplattform (RTCDP) von Adobe auszutauschen. [Mehr dazu](../../integrations/using/get-started-sources-destinations.md)

Es wurde eine neue Technote erstellt, in der erklärt wird, wie die Bounce-Qualifizierung nach einem ISP-Ausfall aktualisiert werden kann. [Mehr dazu](../../delivery/using/update-bounce-qualification.md)

## März 2021 {#march-2021}

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

Im Abschnitt zur Aktivität **[!UICONTROL Erweitertes JavaScript]** finden Sie Informationen dazu, wie Sie die Methode „task.setCompleted()“ verwenden können, um die Aufgabe zu beenden und künftige Rückrufe zu verhindern. [Weitere Informationen](../../workflow/using/sql-code-and-javascript-code.md#adv-js-code-desc)

Der Abschnitt [Zustellbarkeit](../../delivery/using/about-deliverability.md) wurde aktualisiert und enthält nun Links zum neuen [Adobe-Handbuch mit Best Practices zur Zustellbarkeit](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=de). Alle allgemeinen Informationen zur Zustellbarkeit, die für verschiedene Adobe-Lösungen gelten können, wurden in den [Anhang des Handbuchs mit Best Practices](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/general-resources.html?lang=de#additional-resources) verschoben.

## Februar 2021 {#release-21.1}

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

## Januar 2021 {#jan-2021}

Der Abschnitt zur **[!UICONTROL Verzweigungsaktivität]** wurde um Best Practices erweitert. [Mehr dazu](../../workflow/using/fork.md)

Der Abschnitt **CRM-Connectoren** wurde aktualisiert, verbessert und neu organisiert. [Mehr dazu](../../platform/using/crm-connectors.md).

Die Schritte zum Verbinden von **Adobe Campaign und Microsoft Dynamics** werden jetzt auf einer eigenen Seite ausführlich erläutert. [Mehr dazu](../../platform/using/crm-ms-dynamics.md).

Die Oracle On Demand-API wird jetzt als mit Campaign verbundene CRM-Lösung nicht mehr unterstützt. [Mehr dazu](../../rn/using/deprecated-features.md).

Erfahren Sie [hier](../../production/using/locate-tomcat-version.md), wie Sie die aktuelle Version des eingebetteten Tomcat-Webservlets ermitteln, das in einer Instanz von Adobe Campaign verwendet wird.

Die Liste der technischen Workflows und den ihnen zugehörigen Paketen wurde erweitert und auf einer Seite zusammengefasst. [Mehr dazu](../../workflow/using/about-technical-workflows.md)

Der Abschnitt zur Fehlerbehebung im **Überwachungshandbuch** wurde neu strukturiert und durch eine Landingpage erweitert. [Mehr dazu](../../production/using/troubleshooting.md).

Es wurde ein neuer Abschnitt zum **Datenimport und -export** einschließlich neuer Seiten mit Best Practices für Workflows, Datenkomprimierung, Verschlüsselung und Import ergänzt. [Mehr dazu](../../platform/using/get-started-data-import-export.md)

+++


+++ 2020


## Dezember 2020 {#dec-2020}

Der Bereich **Versand-Monitoring** wurde nach Themenbereichen strukturiert. [Mehr dazu](../../delivery/using/about-delivery-monitoring.md)

Ein neuer Anwendungsfall zeigt, wie die IP-Adressen von Absendern zu den Versandlogs hinzugefügt werden können. [Mehr dazu](../../delivery/using/delivery-dashboard.md#use-case)

Die häufig gestellten Fragen zum Datenschutz wurden in [diesen Abschnitt](../../platform/using/privacy-faq.md) verschoben.

Es wurde ein Anwendungsfall zur Verwendung der Zusammenführungsfunktion der **[!UICONTROL Deduplizierungsaktivität]** hinzugefügt. [Mehr dazu](../../workflow/using/deduplication-merge.md)

Die vollständige Beschreibung des SMS-Connector-Protokolls und der Einstellungsseite ist jetzt [hier](../../delivery/using/sms-protocol.md) verfügbar.

Der Abschnitt **Transaktionsnachrichten** wurde um ein Hinweis dazu ergänzt, dass die Ereignis-Ordner nicht als Ansichten für die Ausführungsinstanzen festgelegt werden dürfen, da dies zu Problemen mit Zugriffsrechten führt. [Mehr dazu](../../message-center/using/about-event-processing.md#event-collection)

## November 2020 {#nov-2020}

Die Übersicht über das Datenmodell von Campaign wurde verbessert und neu organisiert. [Mehr dazu](../../configuration/using/about-data-model.md).

Die Konfiguration des externen Kontos wurde in [diesen Abschnitt](../../installation/using/external-accounts.md) verschoben.

Die Dokumentation zum Federated Data Access (FDA) von Campaign wurde mit Details zu den einzelnen externen Datenbankkonfigurationen verbessert und in [diesen Abschnitt](../../installation/using/about-fda.md) verschoben.

Die Campaign-Version 20.2.3 ist jetzt allgemein verfügbar (General Availability, GA).

Der Abschnitt zum Datenschutz wurde um zwei neue Seiten erweitert: [Datenschutzverwaltung](../../platform/using/privacy-management.md) und [Verwaltung von Datenschutzanfragen](../../platform/using/privacy-requests.md).

Auf der Seite zur Mid-Sourcing-Server-Konfiguration wurde ein Hinweis hinzugefügt, um zu präzisieren, dass der interne Name des externen Kontos nach dem Einrichten des Servers nicht aktualisiert werden darf. [Mehr dazu](../../installation/using/mid-sourcing-server.md)

Es wurden Informationen zur Syntax hinzugefügt, die beim Festlegen eines Pfades zu einem externen SFTP-Server verwendet werden muss. [Mehr dazu](../../platform/using/sftp-server-usage.md#external-SFTP-server)

Der Abschnitt über persönliche Daten und Personen wurde um ein Verwendungsfallszenario bereichert, um zu veranschaulichen, wie die verschiedenen Personen in Bezug auf die Privatsphäre interagieren. [Mehr dazu](../../platform/using/privacy-and-recommendations.md#use-case-scenario)

Ein neuer Abschnitt mit häufig gestellten Fragen zum Datenschutz wurde hinzugefügt – [Weitere Informationen](../../platform/using/privacy-faq.md)

## Oktober 2020 {#oct-2020}

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

Dem Abschnitt &quot;Aktualisieren von Adobe Campaign Classic&quot; wurden Richtlinien zum Durchführen einer Build-Aktualisierung hinzugefügt. [Mehr dazu](../../production/using/build-upgrade.md)

Den allgemeinen Fragen zu Campaign wurden häufig gestellte Fragen zur Campaign-Build-Aktualisierung hinzugefügt. Mehr dazu [mehr dazu](../../platform/using/faq-build-upgrade.md)

Die On-Premise-, gehosteten und hybriden Hosting-Modelle von Campaign werden jetzt in einem eigenen Abschnitt beschrieben. [Mehr dazu](../../installation/using/hosting-models.md)

Die Funktionsmatrix pro Campaign-Hosting-Modell wurde aktualisiert und in das Installationshandbuch verschoben. [Mehr dazu](../../installation/using/capability-matrix.md)

Der Abschnitt mit den erweiterten Funktionen von Campaign Reporting wurde verbessert, um genau zu zeigen, wie sich URL-Parameter und Variablen in benutzerspezifischen Berichten verwenden lassen – [Mehr dazu](../../reporting/using/advanced-functionalities.md)

Die Seite mit den Berichtseigenschaften wurde neu organisiert und erweitert, um die Konfiguration zu erleichtern – [Weitere Informationen](../../reporting/using/properties-of-the-report.md)

## September 2020 {#september-2020}

Es wurde ein Hinweis hinzugefügt, dass die Anzahl der aktiven Profile nur für Marketing-Instanzen verfügbar ist – [Mehr dazu](../../platform/using/about-profiles.md#active-profiles)

Es wurde ein neues Beispiel zur Schemabearbeitung hinzugefügt, um ein Feld mit einer vorhandenen Referenztabelle zu verknüpfen – [Mehr dazu](../../configuration/using/examples-of-schemas-edition.md#uc-link)

Es wurde ein Hinweis zur Verwendung zusätzlicher Daten mit Testadressen in Sendungen hinzugefügt – [Weitere Informationen](../../delivery/using/creating-seed-addresses.md#defining-addresses)

## August 2020 {#aug-2020}

Informationen zu Best Practices im Zusammenhang mit der Versandgestaltung und dem Versand mit Campaign finden Sie in einem eigenen Abschnitt – [Mehr dazu](../../delivery/using/delivery-best-practices.md)

Die Landingpage für die Best Practices für die Zustellbarkeit wurde verbessert, um den Zugriff auf Unterabschnitte zu erleichtern – [Mehr dazu](../../delivery/using/about-deliverability.md)

Zu den folgenden Themen sind jetzt Anleitungsvideos verfügbar:

* [Einrichten der Ermüdungsverwaltung mithilfe von Typologieregeln und vordefinierten Filtern](../../campaign-opt/using/about-campaign-typologies.md)

* [Erstellen einer E-Mail in einer Kampagne](../../campaign/using/marketing-campaign-deliveries.md)

* [Erstellen eines mehrsprachigen Newsletters mit bedingten Inhalten](../../delivery/using/conditional-content.md)

* [Konfigurieren und Bereitstellen einer Versandvorlage](../../delivery/using/creating-a-delivery-template.md)

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

Der Abschnitt über die **[!UICONTROL Und-Verknüpfungsaktivität]** wurde um zusätzliche Informationen über deren Verwendung und um einen Hinweis zur Verwendung von Variablen erweitert. [Mehr dazu](../../workflow/using/and-join.md)

## Juli 2020 {#july-2020}

Den Workflow-Anwendungsfällen wurde ein Anwendungsfall zum automatischen Aktualisieren einer Liste mithilfe einer inkrementellen Abfrage hinzugefügt. [Mehr dazu](../../workflow/using/about-workflow-use-cases.md)

Die [Versionshinweise](../../rn/using/latest-release.md) wurden neu organisiert: Es wurde eine [Übersichtsseite](../../rn/using/latest-release.md) mit Informationen zu Build-Status, Upgrade-Prozess, Empfehlungen und wichtigen Links hinzugefügt. Eine spezielle Seite für [[!DNL Gold Standard] Versionen](../../rn/using/gold-standard.md) wurde ebenfalls hinzugefügt und die [Kompatibilitätsmatrix](../../rn/using/compatibility-matrix.md) wurde integriert.

Es wurde ein neuer Abschnitt mit Richtlinien für die Überwachung in Campaign Classic hinzugefügt. [Mehr dazu](../../production/using/monitoring-guidelines.md)

Der Abschnitt &quot;Datenschutz und Einverständnis&quot; wurde um detailliertere Informationen und nützliche Links erweitert. [Mehr dazu](../../platform/using/privacy-and-recommendations.md)

Die Seite &quot;Datenschutzverwaltung in Campaign Classic&quot; wurde mit Informationen zum Feld &quot;Vorschrift&quot; aktualisiert. Dieses Feld ist jetzt bei Verwendung der API verfügbar, die die Einrichtung eines automatischen Prozesses für Datenschutzanfragen ermöglicht. [Mehr dazu](https://helpx.adobe.com/ie/campaign/kb/acc-privacy.html#ManagingPrivacyRequests)

Die Seite mit der Übersicht über die Datenschutzverwaltung wurde aktualisiert und enthält nun Informationen zum thailändischen Datenschutzgesetz (PDPA) und zum brasilianischen Datenschutzgesetz (Lei Geral de Proteção de Dados, LGPD). [Weitere Informationen](../../platform/using/privacy-and-recommendations.md)

Es wurden Informationen zu Sub-Workflow-Protokollen und dem Verhalten im Fehlerfall hinzugefügt. [Mehr dazu](../../workflow/using/sub-workflow.md)

Im Abschnitt **[!UICONTROL Planungsaktivität]** wurden Best Practices hinzugefügt. [Mehr dazu](../../workflow/using/scheduler.md)

## Juni 2020 {#june-2020}

Der Abschnitt über das Entfernen einer unter Quarantäne gestellten Adresse wurde aktualisiert. Dies umfasst eine Klarstellung der Fälle, in denen Adressen automatisch aus der Quarantäneliste entfernt werden. [Mehr dazu](../../delivery/using/understanding-quarantine-management.md#removing-a-quarantined-address)

Es wurden Anwendungsfälle zum [Verschlüsseln](../../platform/using/zip-encrypt.md) und [Entschlüsseln](../../platform/using/unzip-decrypt.md) von Daten mit dem Control Panel und mit Campaign-Workflows hinzugefügt.

Die Seite über die Integration von Experience Cloud Triggers und Adobe Campaign Classic wurde [hierher](../../integrations/using/about-triggers.md) verschoben.

## Juli 2020 {#release-20-2}

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

## Mai 2020 {#may-2020}

Der Abschnitt zum Monitoring der Zustellbarkeit wurde an eine andere Stelle verschoben und überarbeitet. [Mehr dazu](../../delivery/using/monitoring-deliverability.md)

Der Abschnitt zur Behebung von Problemen mit der Zustellbarkeit wurde verschoben und überarbeitet. [Mehr dazu](../../delivery/using/deliverability-faq.md)

Die Zustellbarkeitsrichtlinien beim Start einer neuen Plattform wurden überarbeitet. [Mehr dazu](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=de#transition-process)

Der Abschnitt zum Senden von Transaktions-E-Mails mit Anhängen wurde an eine andere Stelle verschoben und aktualisiert. [Mehr dazu](../../message-center/using/transactional-email-with-attachments.md)

Der Abschnitt mit Best Practices für Datenpackages wurde verschoben und überarbeitet. [Weitere Informationen](../../platform/using/working-with-data-packages.md#data-package-best-practices)

## April 2020 {#april-2020}

Die Tabelle mit den FDA-Berechtigungen wurde in die Dokumentation „Zugriff auf eine externe Datenbank (FDA)“ verschoben. [Mehr dazu](../../installation/using/remote-database-access-rights.md)

Die FAQs wurden um Tipps zum Löschen von Soft Cache und Hard Cache erweitert. [Mehr dazu](../../platform/using/faq-campaign-config.md#perform-soft-cache-clear)

Der Abschnitt mit Best Practices für das Datenmodell enthält jetzt zusätzliche Informationen über Indizes. [Mehr dazu](../../configuration/using/data-model-best-practices.md#indexes)

Der Abschnitt zum integrierten Datenmodell von Adobe Campaign enthält jetzt zusätzliche Details zu den einzelnen Tabellen. [Mehr dazu](../../configuration/using/data-model-description.md)

Anwendungsbeispiele für Workflows wurden aktualisiert und in thematische Bereiche neu angeordnet. [Mehr dazu](../../workflow/using/about-workflow-use-cases.md)

Die Abschnitte [Bounce-Message-Qualifizierung](../../delivery/using/understanding-delivery-failures.md#bounce-mail-qualification) und [E-Mail-Verwaltungsregeln](../../delivery/using/understanding-delivery-failures.md#email-management-rules) enthalten aktualisierte Informationen.

Der Artikel zum Adobe Campaign Enhanced MTA wurde aktualisiert. Er gilt jetzt nur für Campaign Classic. [Weitere Informationen](https://helpx.adobe.com/de/campaign/kb/acc-campaign-enhanced-mta.html)

## März 2020 {#march-2020}

Die Seite mit Best Practices für das Datenmodell enthält jetzt neue Abschnitte wie [Sequenzen](../../configuration/using/data-model-best-practices.md#sequences), [Leistung](../../configuration/using/data-model-best-practices.md#performance) und [große Tabellen](../../configuration/using/data-model-best-practices.md#large-tables). [Mehr dazu](../../configuration/using/data-model-best-practices.md)

Ein neuer Abschnitt, in dem das integrierte Datenmodell von Adobe Campaign beschrieben wird; Interaktion zwischen Tabellen ist nun verfügbar. [Mehr dazu](../../configuration/using/data-model-description.md)

Zusätzliche wichtige Links wurden zur Startseite der Dokumentation hinzugefügt. [Mehr dazu](../../campaign-classic-home.md)

Es wurde ein Anwendungsfall hinzugefügt, der beschreibt, wie ein dynamisches Angebot aus Adobe Target in eine E-Mail in Adobe Campaign integriert werden kann. [Mehr dazu](../../integrations/using/inserting-a-dynamic-image.md)

Ein neuer Abschnitt mit den verschiedenen Sprachen, die in Adobe Campaign verfügbar sind, ist jetzt verfügbar. [Mehr dazu](../../platform/using/adobe-campaign-workspace.md#languages)

Die Seite zu Richtlinien für die Zugriffsverwaltung enthält jetzt zusätzliche Informationen zu spezifischen Berechtigungen. [Mehr dazu](../../platform/using/access-management-named-rights.md)

## Februar 2020 {#february-2020}

Es gibt jetzt einen neuen Abschnitt, in dem Best Practices und wichtige Empfehlungen zum Entwerfen des Adobe Campaign-Datenmodells erläutert werden. [Mehr dazu](../../configuration/using/data-model-best-practices.md)

Es gibt einen neuen Abschnitt zu technischen E-Mail-Konfigurationen. [Mehr dazu](../../installation/using/email-deliverability.md)

Die häufig gestellten Fragen zur Zustellbarkeit enthalten jetzt zusätzliche Details zur Fehlernachricht &quot;Kontingente ausgeschöpft&quot;. [Mehr dazu](https://helpx.adobe.com/de/campaign/kb/acc-deliverability-faq.html#FAQ)

AMP for E-Mail wird jetzt von neuen E-Mail-Anbietern unterstützt: Die zugehörige Dokumentation wurde aktualisiert. [Mehr dazu](../../delivery/using/defining-interactive-content.md)

Der Abschnitt zur E-Mail-Archivierung wurde verbessert. [Weitere Informationen](../../installation/using/email-archiving.md#recommendations-and-limitations)

## Januar 2020 {#release-20-1}

**Neue Funktionen in Version 20.1**

Snowflake FDA-Connector – [mehr dazu](../../installation/using/configure-fda-snowflake.md)

Hadoop FDA Connector-Erweiterungen – [mehr dazu](../../installation/using/configure-fda-hadoop.md)

**Weitere Dokumentationsaktualisierungen zu dieser Version**

Die Anleitungen für [Installation](../../installation/using/general-architecture.md), [Produktion](../../production/using/foreword.md) und [Konfiguration](../../configuration/using/additional-parameters.md) wurden mit der neuen systemd-Einheit aktualisiert, die vom nlserver-Dienststart verwendet wird. Sie können weiterhin &quot;/etc/init.d/nlserver6&quot; verwenden. Adobe empfiehlt jedoch, für die Interaktion mit dem nlserver-Dienst ab jetzt den Befehl &quot;systemctl&quot; zu verwenden.

Das Installationshandbuch wurde aktualisiert und mit der neuesten Version der Kompatibilitätsmatrix synchronisiert. Neue unterstützte Systeme wurden hinzugefügt. Vorkommen von veralteten und nicht mehr unterstützten Systemen wurden entfernt. [Mehr dazu](../../installation/using/general-architecture.md)

Die Kompatibilitätsmatrix wurde mit den Hadoop 3.0- und Snowflake-FDA-Connectoren aktualisiert. [Mehr dazu](https://helpx.adobe.com/de/campaign/kb/compatibility-matrix.html)

Eine Best Practice zur IP-Affinität wurde dem Installationshandbuch hinzugefügt. [Mehr dazu](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use)

Der Abschnitt zum Workflow für die Datenbankbereinigung wurde aktualisiert. Die bereitgestellten Batch-Zahlen spiegeln nun die Code-Implementierung wider. [Mehr dazu](../../production/using/database-cleanup-workflow.md)

Eine Einschränkung zu FDA über HTTP wurde dem Handbuch zu Transaktionsnachrichten hinzugefügt. [Mehr dazu](../../production/using/database-cleanup-workflow.md)

Es wurden Informationen zu der neuen Option hinzugefügt, mit der Sie einen Timeout-Zeitraum für die Workflow-Aktivitäten **[!UICONTROL JavaScript-Code]** und **[!UICONTROL Erweiterter JavaScript-Code]** definieren können. [Mehr dazu](../../workflow/using/sql-code-and-javascript-code.md)

Informationen wurden zur neuen Ansicht **[!UICONTROL Start ausstehend]** hinzugefügt, die unter dem Knoten **[!UICONTROL Administration]** > **[!UICONTROL Audit]** > **[!UICONTROL Status der Workflows]** verfügbar ist. [Mehr dazu](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

Der Leitfaden [Senden von Push-Benachrichtigungen](../../delivery/using/about-mobile-app-channel.md) wurde verschoben, neu organisiert und mit klareren Informationen optimiert.

Der neue Parameter für die URL-Berichtkonfiguration wird [hier](../../reporting/using/properties-of-the-report.md#defining-additional-settings) erläutert.

Die **On-Premise- und Hosted-Leistungsmatrix von Campaign Classic** wurde mit den neuen FDA-Connectoren aktualisiert. [Mehr dazu](../../installation/using/capability-matrix.md).

Die Seite mit der **Campaign Classic-Leistungsmatrix** wurde aktualisiert. [Mehr dazu](https://helpx.adobe.com/de/campaign/kb/compatibility-matrix.html)

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

+++

<!--

### December 2019 {#december-2019}

The "WdbcOptions_TempDbName" option has been added to the list of Campaign options. [Read more](../../installation/using/configuring-campaign-options.md)

The FDA matrix page has been moved [here](../../installation/using/remote-database-access-rights.md).

The Access Rights Matrix page has been moved [here](https://experienceleague.adobe.com/docs/campaign-classic/assets/access-rights-matrix.pdf).

The section describing how to define interactive content with AMP has been moved. [Read more](../../delivery/using/defining-interactive-content.md)

**New capabilities included in 19.2 release**

California Consumer Privacy Act (CCPA) - [Read more](https://helpx.adobe.com/campaign/kb/acc-privacy.html)

Interactive content with AMP - [Read more](../../delivery/using/defining-interactive-content.md)

Workflow live monitoring - [Read more](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

Secure SMS Messaging (TLS) - [Read more](https://helpx.adobe.com/campaign/kb/sms-connector-protocol-and-settings.html)

**Other documentation updates coming with the release**

The Adobe Campaign Enhanced MTA documentation is now available. [Read more](https://helpx.adobe.com/campaign/kb/acc-campaign-enhanced-mta.html)

A new section has been added on how to troubleshoot a workflow staying in the "Start as soon as possible" state within a campaign. [Read more](../../production/using/workflow-execution.md#start-as-soon-as-possible-in-campaigns)

The new "NmsOperation_DeliveryPreparationWindow" and "WdbcKillSessionPolicy" options have been added to the list of Campaign options. [Read more](../../installation/using/configuring-campaign-options.md)

A new document describing the Adobe Campaign Classic data model basics is now available. [Read more](https://helpx.adobe.com/campaign/kb/acc-datamodel.html)

The new **Maximum personalization run time** option in the delivery properties is documented in this [section](../../delivery/using/personalization-fields.md#timing-out-personalization).

The examples for API calls using an **HttpServletRequest** with logon() and query() have been updated. [Read more](../../configuration/using/web-service-calls.md).

A recommendation for **sqlDefault** attribute in schema definition has been added. [Read more](../../configuration/using/schema/attribute.md)).

The integration between Adobe Campaign and Adobe Real-time Customer Data Platform is now referenced in the **Integrating with Adobe Experience Cloud** guide. [Read more](../../integrations/using/about-campaign-integrations.md).

### November 2019 {#november-2019}

A warning has been added to the [Multiplexing the mid-sourcing server](../../installation/using/mid-sourcing-server.md#multiplexing-the-mid-sourcing-server) and [Supporting several control instances](../../message-center/using/transactional-messaging-architecture.md#supporting-several-control-instances) sections mentioning that these deployments are not supported for fully hosted and hybrid clients.

A new section has been added to describe how to force the character encoding used when sending an email. [Read more](../../delivery/using/sending-messages.md#character-encoding)

The Access management section has been updated with the **Privacy Data right**. [Read more](../../platform/using/access-management-named-rights.md)

Information was added to specify that personalization fields content cannot exceed 1024 characters. [Read more](../../delivery/using/personalization-fields.md)

The Control Panel documentation has been integrated into the new collaborative documentation set. [Read more](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html)

The Delivery Best Practices getting started guide has been updated. [Read more](../../delivery/using/delivery-best-practices.md)

### October 2019 {#october-2019}

The list of error messages for Campaign has been updated. [Read more](https://experienceleague.adobe.com/developer/campaign-errors/error_codes.html)

The GDPR getting started guide has been improved and enriched. It is now a privacy management documentation including GDPR and CCPA. [Read more](https://helpx.adobe.com/content/help/en/campaign/kb/campaign-privacy.html)

A new troubleshooting page has been added for tracking in Campaign Classic. [Read more](https://helpx.adobe.com/campaign/kb/classic-tracking-troubleshooting.html).

A new page of best practices for Adobe Analytics Connector has been added. [Read more on Adobe Analytics Connector](../../platform/using/adobe-analytics-connector.md)

The Delivery Best Practices getting started guide has been moved and updated. [Read more](../../delivery/using/delivery-best-practices.md)

A recommendation has been added to the SMS channel documentation to avoid issues when using multiple external accounts leveraging the Extended generic SMPP connector with the same provider account. [Read more](../../delivery/using/sms-set-up.md#automatic-reply)

Information was added in the Scheduler activity documentation on how to prevent simultaneous executions of a workflow. [Read more](../../workflow/using/scheduler.md)

The steps to configure Inbox rendering for on-premise installations have been added to documentation. [Read more](../../delivery/using/inbox-rendering.md#activating-inbox-rendering)

### September 2019 {#september-2019}

A new page has been added to provide general guidelines for maintaining Campaign Classic. [Read more](../../production/using/monitoring-guidelines.md)

Information related to workflows monitoring has been centralized into a new dedicated section. [Read more](../../workflow/using/monitoring-workflow-execution.md).

A new page about general guidelines for tracking in Adobe Campaign Classic has been added. [Read more](https://helpx.adobe.com/campaign/kb/acc-tracking.html).

The best practices for performance improvements of workflows and deliveries have been updated. [Read more on workflows](../../workflow/using/workflow-best-practices.md) and [more on deliveries](../../delivery/using/delivery-performances.md#best-practices-performance).

### May 2019 {#release-19-1}

**New capabilities included in 19.1 release**

Control Panel - [Read more](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html)

Audit trail - [Read more](../../production/using/audit-trail.md)

**Other documentation updates coming with the release**

A new Build upgrade FAQ has been created. [Read more](https://helpx.adobe.com/campaign/kb/build-upgrade-faq.html)

The [Compatibility matrix](compatibility-matrix.md) has been updated. The list of supported database systems has been updated, Android/iOS versions and related SDKs. The 19.0 Compatibility matrix has been archived.

The 'Deprecated and Removed Features in Campaign Classic' page has been updated. [Read more](deprecated-features.md)

The description of the server configuration file has been added to the Installation guide. [Read more](../../installation/using/the-server-configuration-file.md)

A section has been added describing the installation and configuration steps for hosted and hybrid models. [Read more](../../installation/using/hosting-models.md)

A section has been added describing the Campaign server uninstallation steps. [Read more](../../installation/using/uninstalling-campaign.md)

The [security](https://helpx.adobe.com/campaign/kb/acc-security.html), [deliverability](../../delivery/using/about-deliverability.md) and [privacy](../../platform/using/privacy-management.md) getting started guides have been updated.

The description of the pre-process workflow option has been updated to reflect product changes. [Read more](../../workflow/using/data-loading--file-.md)

The Experience Cloud Triggers technote has been updated. [Read more](../../integrations/using/about-triggers.md)

The list of error messages has been updated. [Read more](https://experienceleague.adobe.com/developer/campaign-errors/error_codes.html)

Added more information on SOAP authentication methods for transactional messaging. [Read more](../../message-center/using/event-description.md)

The Apache configuration steps have been updated. [Read more](../../installation/using/integration-into-a-web-server-for-linux.md)

A new page has been added including the list of endpoints for Classic. [Read more](../../installation/using/campaign-network-endpoints.md)

The Data package best practices article has been updated. [Read more](../../configuration/using/data-model-best-practices.md)

The Managing Offers documentation has been updated with a new section listing best practices. [Read more](../../interaction/using/interaction-best-practices.md)

A new Knowledge base article on using the offer catalog in Adobe Campaign Classic has been created. [Read more](https://helpx.adobe.com/campaign/kb/offer-best-practices.html)

The Sub-workflow activity section has been enhanced with an example of usage. [Read more](../../workflow/using/sub-workflow.md)

The [Campaign Classic On-premise & Hosted capability matrix](../../installation/using/capability-matrix.md) page has been updated with information relating to Email BCC.

The Transactional Messaging documentation has been updated with a note regarding template publication. [Read more](../../message-center/using/publishing-message-templates.md#template-publication)

The Unprocessed bounce mails section has been updated with more details on the Forwarding address and Address for errors fields. [Read more](../../installation/using/deploying-an-instance.md)

A new section on workflow planning best practices has been added. [Read more](../../workflow/using/workflow-best-practices.md)

Added two new options to the list of Campaign options: XtkSecurity_Restrict_EditXML and NmsOperation_OperationMgtDebug.
 [Read more](../../installation/using/configuring-campaign-options.md)

Added information on the different external accounts available in Campaign Classic and how to configure them.
 [Read more](../../installation/using/external-accounts.md)

Updated Analytics Connector section to reflect interface changes.
 [Read more](../../platform/using/adobe-analytics-connector.md)

Added information on the Billing report.
 [Read more](../../production/using/monitoring-processes.md)

Updated documentation on the Shared audiences integration.
 [Read more](../../integrations/using/configuring-shared-audiences-integration-in-adobe-campaign.md)

The following technote has been updated: [SMS connector protocol and settings](https://helpx.adobe.com/campaign/kb/sms-connector-protocol-and-settings.html).

The Technical workflows section has been updated. [Read more](../../workflow/using/about-technical-workflows.md)

The Campaign Domain Name Setup procedure has been improved and updated.

The Campaign Hardware Sizing Guide has been updated. [Read more](https://helpx.adobe.com/campaign/kb/hardware-sizing-guide.html)

Information was added on Query Banding for the Teradata external account. [Read more](../../installation/using/external-accounts.md)

### January 2019{#release-doc-16-01-2019}

The Experience Cloud Triggers technote has been updated. [Read more](../../integrations/using/about-triggers.md)

A note was added in the offer approval section to specify  that the "Content approved" mention indicates that the content approval process has been achieved, whether all offers have been enabled/approved or not. [Read more](../../interaction/using/offer-catalog-overview.md)

A new section was added in the Installation guide, listing options from the Administration / Platform / Options node. [Read more](../../installation/using/configuring-campaign-options.md)

Information was added about the use of seed addresses to protect your mailing list. [Read more](../../delivery/using/creating-seed-addresses.md)

Key steps when creating and sending a delivery have been regrouped into a new section, with references to the various channels when needed. [Read more](../../delivery/using/steps-about-delivery-creation-steps.md)

The [Email archiving](../../installation/using/email-archiving.md) section has been moved, reorganized and improved with clarified information:

* Best practices have been added regarding emails per connection and BCC sending IPs parameters.

* We've updated the steps to upgrade to the new email archiving system (BCC) if you were already using email archiving with an older build (prior to Adobe Campaign 17.2 – build 8795).

A use case has been added to the Automating with Workflows guide: Sending personalized alerts to operators. [Read more](../../workflow/using/sending-personalized-alerts-to-operators.md)

The "Migrating to a new version" section has been updated. The documentation now only details the steps for a migration to Adobe Campaign Classic v7 from any older version, as it is no longer possible to migrate to Adobe Campaign v6.11. [Read more](../../migration/using/about-migration.md)

The "Retries after a delivery temporary failure" section has been clarified. [Read more](../../delivery/using/understanding-delivery-failures.md)

Links to the "Digital Content Editor" section have been added to the "Defining the email content" section. [Read more](../../delivery/using/defining-the-email-content.md)

The "Transactional messaging architecture" section has been updated with a warning specifying that the control and the execution instances cannot be installed on the same machine. [Read more](../../message-center/using/transactional-messaging-architecture.md)

The "Workflow monitoring" section has been updated with a note for builds between 8700 and 8977 (18.10), including a link to the technote on how to install the Workflow HeatMap package for these builds. [Read more](../../workflow/using/heatmap.md)

Added a use case on how to send an email with custom data fields using the Enrichment activity in a workflow. [Read more](../../workflow/using/email-enrichment-with-custom-date-fields.md)

Feature videos have been moved [here](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html).
-->
