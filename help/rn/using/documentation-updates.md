---
title: Aktualisierungen der Dokumentation zu Adobe Campaign Classic
description: Diese Seite listet alle neuen Funktionen und Dokumentationsaktualisierungen für jede Version von Adobe Campaign Classic auf.
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
source-git-commit: cc6f0f2989977c5a199dbfd413c6a2bac4628545

---


# Aktualisierungen der Dokumentation{#documentation-updates}

Erfahren Sie mehr über die neuesten Aktualisierungen der Dokumentation zu Adobe Campaign Classic.

Diese Seite listet alle neuen Funktionen und Dokumentationsaktualisierungen für jede Version von Adobe Campaign Classic auf.

You can also consult the [Adobe Campaign Classic Release Notes](../../rn/using/latest-release.md).

## 20.1 - 17/02/2020{#release-20-1}

**Neue Funktionen in der Version**

Snowflake FDA Connector - [Weitere Informationen](../../platform/using/specific-configuration-database.md#configure-access-to-snowflake)

Hadoop FDA Connector-Verbesserungen - [Weitere Informationen](../../platform/using/specific-configuration-database.md#configure-access-to-hadoop-3)

**Weitere Dokumentationsaktualisierungen zu dieser Version**

Die [Installations](../../installation/using/before-reading.md)-, [Produktions](../../production/using/foreword.md) - und [Konfigurationsanleitungen](../../configuration/using/additional-parameters.md) wurden mit der neuen Systemeinheit aktualisiert, die vom nlserver-Dienst-Start verwendet wird. Sie können weiterhin /etc/init.d/nlserver6 verwenden. Es wird jedoch empfohlen, jetzt den Befehl systemCtl für die Interaktion mit dem nlserver-Dienst zu verwenden.

Das Installationshandbuch wurde aktualisiert und mit der neuesten Version der Kompatibilitätsmatrix synchronisiert. Neue unterstützte Systeme wurden hinzugefügt. Vorfälle zu nicht mehr unterstützten und nicht unterstützten Systemen wurden entfernt. [Mehr dazu](../../installation/using/before-reading.md)

Die Kompatibilitätsmatrix wurde mit den Hadoop 3.0- und Snowflake FDA-Anschlüssen aktualisiert. [Mehr dazu](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)

Eine Best Practice zur IP-Affinität wurde dem Installationshandbuch hinzugefügt. [Mehr dazu](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use)

Der Abschnitt zum Arbeitsablauf für die Datenbankbereinigung wurde aktualisiert. Die bereitgestellten Stapelzahlen spiegeln nun die Codeimplementierung wider. [Mehr dazu](../../production/using/database-cleanup-workflow.md)

Eine Einschränkung der FDA über HTTP wurde dem Handbuch für Transaktionsnachrichten hinzugefügt. [Mehr dazu](../../production/using/database-cleanup-workflow.md)

Es wurden Informationen zur neuen Option hinzugefügt, mit der Sie einen Timeout-Zeitraum für die Aktivitäten **[!UICONTROL JavaScript code]** und den **[!UICONTROL Advanced JavaScript code]** Workflow definieren können. [Mehr dazu](../../workflow/using/sql-code-and-javascript-code.md)

Informationen wurden zu der neuen **[!UICONTROL Start Pending]** Ansicht hinzugefügt, die im Knoten **[!UICONTROL Administration]** > **[!UICONTROL Audit]** > **[!UICONTROL Workflows Status]** verfügbar ist. [Mehr dazu](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

Der Leitfaden [für gesendete Push-Benachrichtigungen](../../delivery/using/about-mobile-app-channel.md) wurde mit klareren Informationen verschoben, neu organisiert und verbessert.

Der neue Parameter für die URLs-Berichtskonfiguration wurde [hier](../../reporting/using/properties-of-the-report.md#defining-additional-settings)dokumentiert.

Die Seite mit der Funktionsmatrix **für** Campaign Classic On-Premise und Hosted wurde mit den neuen FDA-Connectors aktualisiert. [Mehr dazu](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html)

Die Seite mit der **Campaign Classic Capability Matrix** wurde aktualisiert. [Mehr dazu](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)

Der neue **[!UICONTROL Cleanup of Nmsaddress]** Arbeitsablauf wurde [hier](../../production/using/database-cleanup-workflow.md#cleanup-of-nmsaddress)dokumentiert.

Bei Verwendung einer Abfrageaktivität in einem Workflow wurde eine Einschränkung hinzugefügt. [Mehr dazu](../../workflow/using/query.md).

Es wurde ein neuer Abschnitt hinzugefügt, in dem die verbesserten Validierungsregeln für E-Mail-Adressen detailliert beschrieben werden, um im Falle eines weichen Fehlers eine Adresse an die Quarantäne zu senden. [Mehr dazu](../../delivery/using/understanding-quarantine-management.md#soft-error-management)

Der Parameter aus der Konfigurationsdatei, der angibt, dass eine Instanz die erweiterte MTA verwendet oder nicht, wird jetzt dokumentiert. [Mehr dazu](../../installation/using/the-server-configuration-file.md#mta)

## February 2020 {#february-2020}

AMP für E-Mail wird jetzt von drei E-Mail-Anbietern (Gmail, Outlook und Mail.ru) unterstützt. Der Abschnitt, der beschreibt, wie interaktive Inhalte mit AMP definiert werden, wurde aktualisiert. [Mehr dazu](../../delivery/using/defining-interactive-content.md)

Der Abschnitt zur E-Mail-Archivierung wurde geklärt. [Mehr dazu](../../installation/using/email-archiving.md#recommendations-and-limitations)

## Januar 2020 {#january-2020}

Der Abschnitt &quot;Auslieferbarkeit&quot;wurde verschoben, neu organisiert und mit aktualisierten Inhalten erweitert. [Mehr dazu](../../delivery/using/about-deliverability.md)

Ein neuer Abschnitt mit den Grundlagen des Adobe Campaign Classic-Datenmodells und dem Zugriff auf die Beschreibung der einzelnen Tabellen ist jetzt verfügbar. [Mehr dazu](../../configuration/using/about-data-model.md)

Der Adobe Campaign Enhanced MTA-Artikel wurde mit detaillierteren Informationen zur Installation eines bestimmten Typologiepakets in Instanzen aktualisiert, die nicht die erforderlichen erweiterten MTA-Kopfzeilen zu jeder Nachricht hinzufügen. [Mehr dazu](https://helpx.adobe.com/campaign/kb/campaign-enhanced-mta.html#impacts)

Die Anwendungsfälle im Zusammenhang mit der Abfragegestaltung wurden in separate Abschnitte umstrukturiert. [Mehr dazu](../../workflow/using/querying-recipient-table.md)

Ein neuer Abschnitt über Tipps und Tricks zur Angebotsverwaltung und zum Einsatz des Interaktionsmoduls in Adobe Campaign Classic ist jetzt verfügbar. [Mehr dazu](../../interaction/using/interaction-best-practices.md#tips-managing-offers)

Die Interaktionsdokumentation wurde mit Links zu verschiedenen Videos erweitert, mit denen Sie besser verstehen können, wie Sie Angebote verwalten. [Mehr dazu](../../interaction/using/interaction-and-offer-management.md)

Der Artikel zu Best Practices zur Optimierung der Abfragen, die auf Ihrer Instanz ausgeführt werden, wurde in die Dokumentation integriert. [Mehr dazu](../../workflow/using/query.md#optimizing-queries)

Das Berichterstellungshandbuch wurde aktualisiert und neu organisiert. [Mehr dazu](../../reporting/using/about-adobe-campaign-reporting-tools.md)

Ein Beispiel für die Verwendung einer Instanzvariablen in einem Workflow wurde hinzugefügt. [Mehr dazu](../../workflow/using/javascript-scripts-and-templates.md)

## Dezember 2019 {#december-2019}

Die Option &quot;WdbcOptions_TempDbName&quot;wurde der Liste der Kampagnenoptionen hinzugefügt. [Mehr dazu](../../installation/using/configuring-campaign-options.md)

Die FDA-Matrixseite wurde [hier](/help/rn/using/assets/fda_rdbms_rights.pdf)verschoben.

Die Seite &quot;Rights Matrix für den Zugriff&quot;wurde [hier](https://docs.adobe.com/content/help/en/campaign-classic/using/getting-started/administration-basics/assets/accessrights.pdf)verschoben.

Der Abschnitt, der beschreibt, wie interaktive Inhalte mit AMP definiert werden, wurde verschoben. [Mehr dazu](../../delivery/using/defining-interactive-content.md)

## 19.2 - 02/12/2019{#release-19-2}

**Neue Funktionen in der Version**

California Consumer Privacy Act (CCPA) – [mehr dazu](https://helpx.adobe.com/campaign/kb/acc-privacy.html)

Interaktive Inhalte mit AMP - [Weitere Informationen](../../delivery/using/defining-interactive-content.md)

Workflow-Live-Überwachung - [Weitere Informationen](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

Secure SMS Messaging (TLS) - [Weitere Informationen](https://helpx.adobe.com/campaign/kb/sms-connector-protocol-and-settings.html)

**Weitere Dokumentationsaktualisierungen zu dieser Version**

Die Adobe Campaign Enhanced MTA-Dokumentation ist jetzt verfügbar. [Mehr dazu](https://helpx.adobe.com/campaign/kb/campaign-enhanced-mta.html)

Es wurde ein neuer Abschnitt hinzugefügt, in dem beschrieben wird, wie Sie Fehler in einem Workflow beheben können, der im Status &quot;So bald wie möglich starten&quot;in einer Kampagne verbleibt. [mehr dazu](../../production/using/workflow-execution.md#start-as-soon-as-possible-in-campaigns)

Die neuen Optionen &quot;NmsOperation_DeliveryVorbereitungsfenster&quot;und &quot;WdbcKillSessionPolicy&quot;wurden zur Liste der Kampagnenoptionen hinzugefügt. [Mehr dazu](../../installation/using/configuring-campaign-options.md)

Ein neues Dokument mit den Grundlagen des Adobe Campaign Classic-Datenmodells ist jetzt verfügbar. [Mehr dazu](https://helpx.adobe.com/campaign/kb/acc-datamodel.html)

Die neue Option **Maximale Personalisierungslaufzeit** in den Auslieferungseigenschaften wird in diesem [Abschnitt](../../delivery/using/personalization-fields.md#timing-out-personalization)beschrieben.

Die Beispiele für API-Aufrufe mit **HttpServletRequest** mit logon() und query() wurden aktualisiert. [Mehr dazu](../../configuration/using/web-service-calls.md).

Eine Empfehlung für das **Attribut &quot;sqlDefault** &quot;in der Schemadefinition wurde hinzugefügt. [Mehr dazu](../../configuration/using/elements-and-attributes.md#attribute-description).

Die Integration zwischen Adobe Campaign und Adobe Echtzeit-Kundendatenplattform wird jetzt im Handbuch **Integration mit Adobe Experience Cloud** beschrieben. [Mehr dazu](../../integrations/using/about-campaign-integrations.md).

## November 2019 {#november-2019}

Dem [Multiplexing-Server](../../installation/using/mid-sourcing-server.md#multiplexing-the-mid-sourcing-server) und den Abschnitten [Unterstützung verschiedener Kontrollinstanzen](../../message-center/using/transactional-messaging-architecture.md#supporting-several-control-instances) wurde eine Warnung hinzugefügt, in der darauf hingewiesen wird, dass diese Implementierungen für vollständig gehostete und hybride Clients nicht unterstützt werden.

Es wurde ein neuer Abschnitt hinzugefügt, in dem beschrieben wird, wie die beim Senden einer E-Mail verwendete Zeichenkodierung erzwungen wird. [Mehr dazu](../../delivery/using/sending-messages.md#character-encoding)

Der Bereich Zugriffsverwaltung wurde mit dem **Datenschutzrecht** aktualisiert. [Mehr dazu](../../platform/using/access-management.md#named-rights)

Es wurden Informationen hinzugefügt, die festlegen, dass der Inhalt von Personalisierungsfeldern 1024 Zeichen nicht überschreiten darf. [mehr dazu](../../delivery/using/personalization-fields.md)

Die Control Panel-Dokumentation wurde in den neuen kollaborativen Dokumentationssatz integriert. [mehr dazu](https://docs.adobe.com/content/help/en/control-panel/using/control-panel-home.html)

Die ersten Schritte zum Thema Best Practices für den Versand wurden aktualisiert – [mehr dazu](https://helpx.adobe.com/campaign/kb/delivery-best-practices.html)

## October 2019 {#october-2019}

Die Liste der Fehlermeldungen für Campaign Standard und Campaign Classic wurde aktualisiert – [mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

Die ersten Schritte zum Thema DSGVO wurden verbessert und erweitert. Es handelt sich nun um eine Dokumentation rund um die Gewährleistung von Datenschutz gemäß den Bestimmungen der DSGVO und des CCPA – [mehr dazu](https://helpx.adobe.com/content/help/en/campaign/kb/campaign-privacy.html)

Eine neue Seite zur Fehlerbehebung wurde zur Verfolgung in Campaign Classic hinzugefügt. [Mehr dazu](https://helpx.adobe.com/campaign/kb/classic-tracking-troubleshooting.html).

Eine neue Seite mit Best Practices für Adobe Analytics Data Connector wurde hinzugefügt. [Mehr darüber unter Adobe Analytics Data Connector](../../platform/using/adobe-analytics-data-connector.md)

Die ersten Schritte zum Thema Best Practices bei der Zustellung wurden aktualisiert. [Mehr dazu](https://helpx.adobe.com/campaign/kb/delivery-best-practices.html)

In der Dokumentation zum SMS-Kanal wurde eine Empfehlung hinzugefügt, um Probleme bei der Verwendung mehrerer externer Konten zu vermeiden, indem der erweiterte allgemeine SMPP-Connector mit demselben Provider-Konto genutzt wird. [Mehr dazu](../../delivery/using/sms-channel.md#automatic-reply)

In der Dokumentation zur Scheduler-Aktivität wurden Informationen darüber hinzugefügt, wie die gleichzeitige Ausführung eines Workflows verhindert werden kann. [Mehr dazu](../../workflow/using/scheduler.md)

Die Schritte zum Konfigurieren des Inbox-Renderings für lokale Installationen wurden der Dokumentation hinzugefügt. [Mehr dazu](../../delivery/using/inbox-rendering.md#activating-inbox-rendering)

## September 2019 {#september-2019}

Eine neue Seite wurde hinzugefügt, um allgemeine Richtlinien für die Wartung von Campaign Classic bereitzustellen. [Mehr dazu](https://helpx.adobe.com/campaign/kb/acc-maintenance.html)

Die Informationen zur Überwachung der Arbeitsabläufe wurden in einem neuen Abschnitt zusammengefasst. [Mehr dazu](../../workflow/using/monitoring-workflow-execution.md).

Eine neue Seite mit allgemeinen Richtlinien für die Verfolgung in Adobe Campaign Classic wurde hinzugefügt. [Mehr dazu](https://helpx.adobe.com/campaign/kb/acc-tracking.html).

Die Best Practices für die Leistungsverbesserung von Workflows und Auslieferungen wurden aktualisiert. [Lesen Sie mehr über Arbeitsabläufe](../../workflow/using/workflow-best-practices.md) und [mehr über Auslieferungen](../../delivery/using/monitoring-a-delivery.md#best-practices-performance).

## 19.1 - 30/05/2019{#release-19-1}

**Neue Funktionen in der Version**

Control Panel – [mehr dazu](https://docs.adobe.com/content/help/en/control-panel/using/control-panel-home.html)

Prüfpfad - [Mehr](https://docs.campaign.adobe.com/doc/AC/en/PRO_Production_procedures_Audit_trail.html)

**Weitere Dokumentationsaktualisierungen zu dieser Version**

Eine neue Häufig gestellte Fragen zur Build-Aktualisierung wurde erstellt. [Mehr dazu](https://helpx.adobe.com/campaign/kb/build-upgrade-faq.html)

The [Compatibility matrix](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html) has been updated. Die Liste der unterstützten Datenbanksysteme sowie die Android-/iOS-Versionen und die zugehörigen SDKs wurden aktualisiert. The [19.0 Compatibility matrix](https://helpx.adobe.com/campaign/kb/compatibility-matrix-19-0.html) has been archived.

Die Seite &quot;Veraltete und entfernte Funktionen in Campaign Classic&quot;wurde aktualisiert. [Mehr dazu](https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html)

Die Beschreibung der Serverkonfigurationsdatei wurde dem Installationshandbuch hinzugefügt. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/INS_Appendices_The_server_configuration_file.html)

Es wurde ein Abschnitt hinzugefügt, in dem die Installations- und Konfigurationsschritte für gehostete und hybride Modelle beschrieben werden. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/INS_Hybrid_and_Hosted_models_Introduction.html)

Es wurde ein Abschnitt hinzugefügt, der die Deinstallationsschritte des Campaign-Servers beschreibt. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/INS_Appendices_Uninstalling_Campaign.html)

Die [Sicherheits](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/security.html)-, [Bereitstellungs](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliverability.html) - und [Datenschutzrichtlinien](https://helpx.adobe.com/campaign/kb/acc-privacy.html) wurden aktualisiert.

Die Beschreibung der Option für den vorbereiten Arbeitsablauf wurde aktualisiert, um Produktänderungen widerzuspiegeln. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/WKF_Repository_of_activities_Action_activities.html#Data_loading__file_)

Die Marketing Cloud-Auslöser-Technote wurde aktualisiert. [Mehr dazu](https://helpx.adobe.com/campaign/kb/triggers-and-campaign.html)

Die Liste der Fehlermeldungen wurde aktualisiert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

Es wurden weitere Informationen zu SOAP-Authentifizierungsmethoden für Transaktionsnachrichten hinzugefügt. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/MCE_Introduction_Event_description.html)

Die Apache-Konfigurationsschritte wurden aktualisiert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/INS_Installing_Campaign_in_Linux__Integration_into_a_Web_server.html#Configuring_Apache_web_server_in_RHEL)

Eine neue Seite wurde hinzugefügt, einschließlich der Liste der Endpunkte für Campaign Standard und Classic. [Mehr dazu](https://helpx.adobe.com/campaign/kb/campaign-endpoints.html)

Der Artikel Best Practices für das Datenpaket wurde aktualisiert. [Mehr dazu](https://helpx.adobe.com/campaign/kb/data-package-best-practices.html)

Die Dokumentation &quot;Verwalten von Angeboten&quot;wurde um einen neuen Abschnitt mit Best Practices erweitert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/ITA_Interaction_Overview_Interaction_best_practices.html)

Es wurde ein neuer Knowledge Base-Artikel zur Verwendung des Angebotskatalogs in Adobe Campaign Classic erstellt. [Mehr dazu](https://helpx.adobe.com/campaign/kb/offer-best-practices.html)

Der Abschnitt für die Aktivität unter dem Workflow wurde um ein Verwendungsbeispiel erweitert. [Mehr dazu](../../workflow/using/sub-workflow.md)

Der Knowledge Base-Artikel zur Wissensdatenbank von [Campaign Classic für lokale und gehostete Funktionen wurde um Informationen zum Archivieren von E-Mails ergänzt](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html) .

Die Dokumentation zu Transactional Messaging wurde mit einem Hinweis zur Vorlagenveröffentlichung aktualisiert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/MCE_Template_publication.html)

Der Abschnitt &quot;Nicht verarbeitete Absprungmeldungen&quot;wurde um weitere Details zu den Feldern &quot;Weiterleitungsanschrift&quot;und &quot;Adresse für Fehler&quot;erweitert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/INS_Initial_configuration_Deploying_an_instance.html#Unprocessed_bounce_mails)

Ein neuer Abschnitt zu Best Practices für die Workflow-Planung wurde hinzugefügt. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Workflow_best_practices.html#Execution_and_performance)

Der Liste der Kampagnenoptionen wurden zwei neue Optionen hinzugefügt: XtkSecurity_Restrict_EditXML und NmsOperation_OperationMgtDebug.
[Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/INS_Appendices_Configuring_Campaign_options.html)

Es wurden Informationen zu den verschiedenen in Campaign Classic verfügbaren externen Konten und deren Konfiguration hinzugefügt.
[Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/PTF_Administration_basics_External_accounts.html)

Der Analytics Data Connector-Abschnitt wurde aktualisiert, um Änderungen an der Benutzeroberfläche widerzuspiegeln.
[Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/PTF_Connectors_Adobe_Analytics_Data_Connector.html)

Es wurden Informationen zum Rechnungsbericht hinzugefügt.
[Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/PRO_Production_procedures_Monitoring_processes.html#Billing_report)

Die Dokumentation zur Integration freigegebener Zielgruppen wurde aktualisiert.
[Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/ITG_Audience_sharing_Configuring_shared_audiences_integration_in_Adobe_Campaign.html)

Die folgenden technischen Hinweise wurden aktualisiert: Protokoll und Einstellungen[ des ](https://helpx.adobe.com/campaign/kb/sms-connector-protocol-and-settings.html)SMS-Anschlusses und [automatische Erstellung](https://helpx.adobe.com/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence)der Sequenz.

Der Abschnitt Technische Arbeitsabläufe wurde aktualisiert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/WKF_Technical_workflows_About_technical_workflows.html)

Das Setup-Verfahren für den Kampagnendomänennamen wurde verbessert und aktualisiert. [Mehr dazu](https://helpx.adobe.com/campaign/kb/domain-name-delegation.html)

Das Migrationsverfahren für Android-Apps von Google Cloud Messaging (GCM) zu Firebase Cloud Messaging (FCM) wurde aktualisiert. [Mehr dazu](https://helpx.adobe.com/campaign/kb/migrate-to-fcm.html)

Das Handbuch zur Hardware-Größe der Kampagne wurde aktualisiert. [Mehr dazu](https://helpx.adobe.com/campaign/kb/hardware-sizing-guide.html)

Informationen wurden zu Abfragebanding für das externe Teradata-Konto hinzugefügt. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/PTF_Administration_basics_External_accounts.html#External_database_external_account)

## Januar 2019{#release-doc-16-01-2019}

Die Marketing Cloud-Auslöser-Technote wurde aktualisiert. [Mehr dazu](https://helpx.adobe.com/campaign/kb/triggers-and-campaign.html)

Im Abschnitt zur Genehmigung von Angeboten wurde ein Hinweis hinzugefügt, der angibt, dass die Erwähnung &quot;Genehmigte Inhalte&quot;darauf hinweist, dass der Prozess der Inhaltsgenehmigung erreicht wurde, ob alle Angebote aktiviert/genehmigt wurden oder nicht. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/ITA_Managing_an_offer_catalog_Approving_and_activating_an_offer.html#Approving_offer_content)

Im Installationshandbuch wurde ein neuer Abschnitt mit Optionen aus dem Knoten Administration/Plattform/Optionen hinzugefügt. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/INS_Appendices_Configuring_Campaign_options.html)

Es wurden Informationen über die Verwendung von Seed-Adressen zum Schutz Ihrer Mailingliste hinzugefügt. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/DLV_Using_seed_addresses_About_seed_addresses.html)

Wichtige Schritte beim Erstellen und Senden einer Bereitstellung wurden in einem neuen Abschnitt zusammengefasst, wobei bei Bedarf auf die verschiedenen Kanäle verwiesen wird. [Mehr dazu](../../delivery/using/steps-about-delivery-creation-steps.md)

Der [Abschnitt &quot;E-Mail-Archivierung](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html) &quot;wurde verschoben, neu organisiert und mit geklärten Informationen verbessert:

* Bewährte Verfahren wurden für E-Mails pro Verbindung und für BCC-Parameter zum Senden von IPs hinzugefügt. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html#Best_practices)

* Die Schritte zum Aktualisieren auf das neue E-Mail-Archivierungssystem (BCC) wurden aktualisiert, wenn Sie bereits mit einem älteren Build (vor Adobe Campaign 17.2 - Build 8795) E-Mail-Archivierung verwendet haben. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html#Updated_email_archiving_system__BCC_)

Dem Handbuch Automatisieren mit Workflows wurde ein Anwendungsfall hinzugefügt: Senden personalisierter Warnungen an Operatoren [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Sending_personalized_alerts_to_operators.html)

Der Abschnitt &quot;Migration zu einer neuen Version&quot;wurde aktualisiert. Die Dokumentation beschreibt jetzt nur die Schritte für eine Migration von einer älteren Version zu Adobe Campaign Classic v7, da eine Migration zu Adobe Campaign v6.11 nicht mehr möglich ist. Mehr [dazu](https://docs.campaign.adobe.com/doc/AC/en/MIG_Migration_overview_About_migration.html)

Der Abschnitt &quot;Wiederholungen nach einem vorübergehenden Lieferausfall&quot;wurde geklärt. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/DLV_Monitoring_deliveries_Understanding_delivery_failures.html#Retries_after_a_delivery_temporary_failure)

Links zum Abschnitt &quot;Digital Content Editor&quot;wurden zum Abschnitt &quot;Definieren des E-Mail-Inhalts&quot;hinzugefügt. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_emails_Defining_the_email_content.html#Message_content)

Der Abschnitt &quot;Architektur für Transaktionsnachrichten&quot;wurde mit einer Warnung aktualisiert, in der angegeben wird, dass das Steuerelement und die Ausführungsinstanzen nicht auf demselben Computer installiert werden können. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/MCE_Introduction_Transactional_messaging_architecture.html)

Der Abschnitt &quot;Workflow-Überwachung&quot;wurde mit einem Hinweis für Builds zwischen 8700 und 8977 (18.10) aktualisiert, einschließlich eines Links zum technischen Hinweis zur Installation des Workflow HeatMap-Pakets für diese Builds. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/PRO_Production_procedures_Monitoring_processes.html#About_the_Workflow_HeatMap)

Es wurde ein Anwendungsfall hinzugefügt, der beschreibt, wie eine E-Mail mit benutzerdefinierten Datenfeldern über die Anreicherungsaktivität in einem Workflow gesendet werden kann. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Email_enrichment_with_custom_date_fields.html)

Funktionsvideos wurden [hier](https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/overview.html)verschoben.

Zwei Technotes wurden zu [Teradata](https://helpx.adobe.com/campaign/kb/campaign_fda_teradata.html) und [MySQL 5.7](https://helpx.adobe.com/campaign/kb/campaign_fda_mysql.html)hinzugefügt.

## 18.10 - 05/11/2018{#release-18-10}

**Neue Funktionen in der Version**

Push notification improvements - [Read more](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_push_notifications_Setting_up_mobile_app_channel.html#Integrating_the_SDK_into_the_mobile_application)

SQL-Datenverwaltungsaktivität - [Weitere Informationen](https://docs.campaign.adobe.com/doc/AC/en/WKF_Repository_of_activities_Action_activities.html#SQL_Data_Management)

Workflow-Überwachung - [Weitere Informationen](https://docs.campaign.adobe.com/doc/AC/en/PRO_Production_procedures_Monitoring_processes.html#Workflow_monitoring)

**Weitere Dokumentationsaktualisierungen zu dieser Version**

Campaign-Classic-APIs sind jetzt auf einer [eigenen Seite](https://docs.campaign.adobe.com/doc/AC/en/jsapi/index.html) verfügbar. Wenn Sie die Jsapi.chm-Datei verwendet haben, sollten Sie jetzt die neue Online-Version nutzen.

Die Kompatibilitätsmatrix wurde aktualisiert. [Mehr dazu](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)

Die Seite &quot;Veraltete und entfernte Funktionen in Campaign Classic&quot;wurde aktualisiert. [Mehr dazu](https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html)

In den [Versionshinweisen](https://docs.campaign.adobe.com/doc/AC/en/RN.html) und [veralteten Versionshinweisen](https://docs.campaign.adobe.com/doc/AC/en/RN_legacy.html)wurde eine Warnung für zurückgerufene Builds hinzugefügt. Kumulative Builds für 17.9, 18.4 und 18.6 wurden ebenfalls hinzugefügt.

Die Anleitungen zu [Sicherheit](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/security.html), [Lieferbarkeit](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliverability.html) und [Build-Upgrade](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/buildUpgrade.html) für die ersten Schritte wurden aktualisiert.

Das Handbuch [zum Einstieg in den Datenschutz](https://helpx.adobe.com/campaign/kb/acc-privacy.html) wurde aktualisiert und enthält Informationen dazu, wie die API extern aufgerufen und wie mit queryDef der Status abgefragt und die GDPR-Datei heruntergeladen werden kann.

Es wurde ein Anwendungsfall für Transaktionsnachrichten hinzugefügt, um E-Mail-Anhänge direkt zu ausgehenden Dispatches hinzuzufügen. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/MCE_Use_case_Purpose.html)

Der Abschnitt zur Fehlerbehebung bei Verbindungsschwellenwerten wurde aktualisiert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/PRO_Troubleshooting_Connection_thresholds.html)

Es wurde ein Abschnitt zum Konfigurieren einer Proxyverbindung hinzugefügt. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Configuring_Campaign_server.html#Proxy_connection_configuration)

Der Abschnitt zur Beschränkung autorisierter externer Befehle wurde aktualisiert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Configuring_Campaign_server.html#Restricting_authorized_external_commands)

Es wurde ein Abschnitt zur Fehlerbehebung im Zusammenhang mit der SFTP-Nutzung hinzugefügt. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/PTF_Importing_and_exporting_data_SFTP_server_usage.html)

Der Übersichtsbereich des Leitfadens &quot;Nachrichten senden&quot;wurde neu organisiert. Es wurden Informationen zum globalen Lieferprozess und den verschiedenen Bereitstellungstypen hinzugefügt. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/DLV_About_deliveries_and_channels_Communication_channels.html)

Die Liste der Fehlermeldungen wurde aktualisiert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

Der Abschnitt zur Verwendung von Seed-Adressen wurde in das Übersichtshandbuch zum Senden von Nachrichten verschoben. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/DLV_Using_seed_addresses_About_seed_addresses.html)

Es wurde ein neuer Anwendungsfall für den Workflow hinzugefügt: Verwalten von Updates aus gleichzeitigen Workflow-Ausführungen [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Coordinating_data_updates.html)

Der Abschnitt &quot;Inbox-Rendering&quot;wurde mit weiteren Informationen zu Litmus und einem detaillierteren Verfahren aktualisiert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/DLV_Deliverability_management_Inbox_rendering.html#Multiplexing_the_mid-sourcing_server)

Der Abschnitt &quot;SpamAssassin&quot;wurde verbessert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/DLV_Deliverability_management_SpamAssassin.html)

Im Abschnitt &quot;Verwalten von Marketingmüdigkeit mit Druckregeln&quot;wurde ein Anwendungsfall hinzugefügt. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/CMP_Campaign_Optimization_Pressure_rules.html#Sending_only_the_highest-weighted_messages)

Ein neuer Anwendungsfall, der beschreibt, wie ein kanalübergreifender Bereitstellungsarbeitsablauf erstellt wird, ist jetzt verfügbar. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Cross-channel_delivery_workflow.html)

Einige Empfehlungen wurden zum Abschnitt &quot;Archivieren von E-Mails&quot;hinzugefügt. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_deliverability.html#Activating_emails_BCC_archiving)

Es wurde eine neue Empfehlung zur minimalen Bildschirmauflösung für eine optimale Verwendung von Adobe Campaign hinzugefügt. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/PTF_Starting_with_Adobe_Campaign_Adobe_Campaign_workspace.html#Screen_resolution)

Das Integrationsleitfaden für Experience Manager wurde mit einigen Erläuterungen zur Konfiguration dieser Integration aktualisiert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/ITG_Adobe_Experience_Manager_About_Adobe_Experience_Manager.html)

Es wurden Informationen zum Unterschied zwischen der Liste der Gruppentypen und der Liste der Listentypen hinzugefügt. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/PTF_Profile_management_Creating_and_managing_lists.html#About_lists_in_Adobe_Campaign)

Der Code wurde aktualisiert, um eine Berichtsextrahierung als Anhang über E-Mail zu senden. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Sending_a_report_to_a_list.html#Step_3-_Creating_the_workflow)

Es wurde ein Beispiel hinzugefügt, wie eine Abfrage erstellt wird, um Empfänger zu filtern, die in den letzten 7 Tagen keine E-Mail geöffnet haben. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Designing_queries.html#Recipients_who_did_not_open_any_delivery)

Handbuch zur Freigabe von Zielgruppen mit Adobe Experience Cloud-Integration aktualisiert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/ITG_Audience_sharing_Sharing_audiences_with_Adobe_Experience_Cloud.html)

Die Hilfeseite &quot;Allgemeine Fragen&quot;enthält jetzt Informationen zu den verfügbaren Kampagnensprachen, zur Webformular-Übersetzung und zu mehrsprachigen E-Mails. [Mehr dazu](../../platform/using/common-questions.md)

Die Unterschiede zwischen englischen und englischen Instanzen in den USA sind jetzt in einem speziellen Abschnitt aufgeführt. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/PTF_Starting_with_Adobe_Campaign_Adobe_Campaign_workspace.html#Formats_and_units)

Die Hilfeseite [Häufige Fragen](../../platform/using/common-questions.md) enthält jetzt Links zur Seite Fehlermeldungen.

Informationen zum &quot;offenen&quot;Verfolgungsmodus wurden hinzugefügt. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/DLV_Tracking_messages_Personalizing_URL_tracking.html)

Fügen Sie Informationen zur Mindestauflösung für Webanwendungen und Webformulare hinzu. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/WEB_Web_forms_About_web_forms.html)

Integrationshandbuch für Kampagnen und Adobe Experience Cloud-Lösungen wurde aktualisiert und neu organisiert. [Mehr dazu](../../integrations/using/about-campaign-integrations.md)

Es wurde ein Abschnitt zur Verwendung von Textvariablen in Webformularen hinzugefügt. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/WEB_Web_forms_Static_elements_in_a_web_form.html#Using_text_variables)

URL-Verfolgungsmodi in Nachrichten sind jetzt detailliert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/DLV_Tracking_messages_How_to_configure_tracked_links.html)

Der Abschnitt zur Instanzerstellung wurde neu organisiert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/INS_Initial_configuration_Creating_an_instance_and_logging_on.html)

Das Senden von E-Mails auf japanischen Mobiltelefonen ist jetzt in einem neuen Abschnitt dokumentiert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_emails_Defining_the_email_content.html#Sending_emails_on_Japanese_mobiles)

Der Abschnitt &quot;Optimierende Personalisierung&quot;wurde um weitere Informationen ergänzt. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/DLV_Personalizing_deliveries_Personalization_fields.html#Optimizing_personalization)

## 18.6 - 09/07/2018{#release-18-6}

**Neue Funktionen in der Version**

Die Kompatibilitätsmatrix wurde aktualisiert. [Mehr dazu](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)

Die JSAPI-Dokumentation wurde aktualisiert. [Mehr dazu](https://support.neolane.net/webApp/extranetLogin)

Die Seite &quot;Veraltete und entfernte Funktionen&quot;wurde aktualisiert. [Mehr dazu](https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html)

**Weitere Dokumentationsaktualisierungen zu dieser Version**

Die Benutzerhandbücher von Campaign Classic wurden umbenannt, um die Navigation zu vereinfachen, die Benutzerfreundlichkeit zu verbessern, Zugriff auf Informationen und Selbsthilfe zu erhalten. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/browseAC.html)

Die Liste der im Ausdruckseditor verfügbaren Funktionen wurde aktualisiert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/PTF_Creating_queries_Defining_filter_conditions.html#List_of_functions)

Das Handbuch &quot;Erste Schritte mit Sicherheit&quot;wurde aktualisiert und enthält Informationen zum Schutz von Seiten, die PI enthalten. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/security.html)

Die Liste der Fehlermeldungen wurde aktualisiert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

In der Dokumentation zur IMS-Integration wurde ein Abschnitt zur Fehlerbehebung hinzugefügt. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/ITG_Connecting_via_an_Adobe_ID_IMS_troubleshooting.html)

Das Handbuch Erste Schritte mit der Aktualisierung auf Build wurde aktualisiert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/buildUpgrade.html)

Der Abschnitt zur Konfiguration der IP-Affinität wurde aktualisiert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Mid-sourcing_server.html#Multiplexing_the_mid-sourcing_server)

Der Abschnitt zur Fehlerbehebung bei Leistung und Durchsatz wurde hinzugefügt. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/PRO_Troubleshooting_Performance_and_throughput_issues.html)

Die Liste der integrierten Personalisierungsblöcke wurde mit Beispielen aktualisiert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/DLV_Personalizing_deliveries_Personalization_blocks.html#Out-of-the-box_personalization_blocks)

Die Liste der Gründe für Lieferfehler wurde aktualisiert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/DLV_Monitoring_deliveries_Understanding_delivery_failures.html#Delivery_failure_types_and_reasons)

Ein neuer Abschnitt zur Paketdefinitionsverwaltung wurde hinzugefügt. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/PTF_Administration_basics_Working_with_data_packages.html#Managing_package_definitions)

Die Kampagnenintegration mit Adobe Analytics - Data Connector wurde verbessert und neu organisiert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/PTF_Connectors_Adobe_Analytics_Data_Connector.html)

Es wurde ein neuer Abschnitt &quot;Tutorials&quot;mit Links zu schrittweisen Anleitungen und Anleitungen zu Videos hinzugefügt. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/PTF_Starting_with_Adobe_Campaign_Tutorials.html)

Es wurde eine neue Technote zum SMS-Connector-Protokoll und zu den Einstellungen erstellt. [Mehr dazu](https://helpx.adobe.com/campaign/kb/sms-connector-protocol-and-settings.html)

Das Handbuch &quot;Best Practices für die Bereitstellung - Erste Schritte&quot;wurde aktualisiert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliveryBestPractices.html)

Die Microsoft Dynamics 365 Kontokonfiguration mit Web API-Bereitstellung wurde aktualisiert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/PTF_Connectors_CRM_Connectors.html#Example_for_Microsoft_Dynamics)

Das Verfahren zur Installation von Adobe Campaign Classic auf einer Windows-Plattform wurde aktualisiert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/INS_Installing_Campaign_in_Windows__Installing_the_server.html)

Der Zeitrahmen für die Freigabe von Zielgruppen zwischen Adobe Experience Cloud und Campaign Classic wurde detailliert beschrieben. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/ITG_Audience_sharing_Importing_and_exporting_audiences.html)

Der Knowledge Base-Artikel, der für die Campaign Classic-Liste voll ist, wurde aktualisiert. [Mehr dazu](https://helpx.adobe.com/campaign/kb/article-list.html)

Ein neuer Technote über Leistungsverbesserungen und Best Practices ist live. [Mehr dazu](https://helpx.adobe.com/campaign/kb/best-practices-for-performance-improvement.html)

Das A/B-Testmuster wurde aktualisiert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_A-B_testing.html)

Die Seite &quot;Häufige Fragen/FAQ&quot;von Campaign Classic wurde aktualisiert. [Mehr dazu](../../platform/using/common-questions.md)

## 18.4 - 24/04/2018{#release-18-4}

**Neue Funktionen in der Version**

EU-Datenschutz-Grundverordnung (DSGVO) – [mehr dazu](https://helpx.adobe.com/campaign/kb/acc-privacy.html)

Aktive Profile - [Weitere Informationen](https://docs.campaign.adobe.com/doc/AC/en/PTF_Profile_management_About_profiles.html#Active_profiles)

Verbesserung für Android Push Connector - [Weitere Informationen](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_push_notifications_Setting_up_mobile_app_channel.html#Android_connectors)

**Weitere Dokumentationsaktualisierungen zu dieser Version**

Die Versionshinweise wurden für eine bessere Benutzererfahrung verbessert und enthalten jetzt alle Patches, die mit Kundenanforderungen zusammenhängen.  [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/RN.html)

Eine neue Seite mit den häufigsten Fragen zu Campaign Classic wurde hinzugefügt. [Mehr dazu](../../platform/using/common-questions.md)

Die Liste der Fehlermeldungen wurde aktualisiert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

Die Marketing Cloud-Auslöser-Technote wurde aktualisiert. [Mehr dazu](https://helpx.adobe.com/campaign/kb/triggers-and-campaign.html)

Es wurde eine TechNote zur Installation und Bereitstellung des Datenschutzpakets (GDPR) in älteren Campaign Classic-Versionen hinzugefügt. [Mehr dazu](https://helpx.adobe.com/campaign/kb/how-to-install-gdpr-package-on-legacy-versions.html)

Es wurde eine Technote zum neuen Mechanismus zur automatischen Sequenzgenerierung hinzugefügt. [Mehr dazu](https://helpx.adobe.com/campaign/kb/sequence_auto_generation.html)

Die JSAPI-Dokumentation wurde aktualisiert. [Mehr dazu](https://support.neolane.net/webApp/extranetLogin)

Die Kompatibilitätsmatrix wurde aktualisiert. [Mehr dazu](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)

Eine neue Seite mit nicht mehr unterstützten Funktionen und Versionen ist jetzt verfügbar. [Mehr dazu](https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html)

Einige bekannte Einschränkungen und Best Practices für RDBMS wurden hinzugefügt. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/INS_Prerequisites_and_recommendations__Database.html)

Erfahren Sie, welche Best Practices für die SFTP-Nutzung gelten. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/PTF_Importing_and_exporting_data_SFTP_server_usage.html)

Die Liste der technischen Arbeitsabläufe wurde aktualisiert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/WKF_Technical_workflows_About_technical_workflows.html)

Die Liste der Artikel der Wissensdatenbank (früher &quot;Technotes&quot;) ist jetzt hier verfügbar. [Mehr dazu](https://helpx.adobe.com/campaign/kb/article-list.html)

Die [Anleitungsvideos](https://docs.campaign.adobe.com/doc/AC/en/Videos/Videos.html) wurden aktualisiert.

Die LINE-Dokumentation wurde nach der Abschreibung des LINE-Pakets aktualisiert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_messages_on_mobiles_LINE_channel.html)

Die Dokumentation zur Berechnung der Berichtsindikatoren wurde aktualisiert. [Mehr dazu](../../reporting/using/indicator-calculation.md)

Es wurden Informationen zur Zeitzone-Dateiausrichtung mit Oracle hinzugefügt. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/MIG_Configuration_General_configurations.html#Oracle)

Es wurde ein neuer Abschnitt &quot;Überwachung der Auslieferungen&quot;mit aktualisierten Informationen zu Auslieferungsfehlern und zum Quarantänemanagement hinzugefügt. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/DLV_Monitoring_deliveries_Monitoring_a_delivery.html)

Der Abschnitt &quot;Personalisierungsblöcke&quot;wurde um neue Informationen zu vordefinierten Personalisierungsblöcken erweitert.
[Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/DLV_Personalizing_deliveries_Personalization_blocks.html)

Der Abschnitt &quot;Archivieren von E-Mails&quot;wurde mit neuen Informationen zur ```config-<instance name>.xml``` Dateikonfiguration umstrukturiert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html#Activating_email_archiving__on_premise_)

Informationen zum technischen Arbeitsablauf für das Nachrichtencenter (Control) aktualisiert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/WKF_Technical_workflows_Message_Center__Control_.html)

Es wurden Informationen zu Durchsatzbeschränkungen beim Einrichten eines SMTP-Relais hinzugefügt. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Configuring_Campaign_server.html#Personalizing_delivery_parameters)

## 17.12 - 14/12/2017{#release-doc-14-12-2017}

Der Dokumentationssatz[ für ](https://helpx.adobe.com/support/campaign/classic.html)Adobe Campaign Classic wurde neu organisiert, um die Benutzerfreundlichkeit zu verbessern.

Ein neuer Abschnitt &quot;Tutorials&quot;wurde hinzugefügt, um den Zugriff auf Hilfsmaterialien, Anleitungen, Beispiele und Videos zu den Kampagnenfunktionen zu erleichtern. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/PTF_Starting_with_Adobe_Campaign_Tutorials.html)

Es wurde ein neuer Abschnitt hinzugefügt, mit dem Sie Ihren Lieferstatus, aber auch mögliche Fehler überwachen und deren Behebung erfahren können. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/DLV_Monitoring_deliveries_Monitoring_a_delivery.html)

Die Liste der Fehlermeldungen wurde aktualisiert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

Die Marketing Cloud-Auslöser-Technote wurde aktualisiert. [Mehr dazu](https://helpx.adobe.com/campaign/kb/triggers-and-campaign.html)

Der Campaign Classic-Migrationsleitfaden wurde der Sammlung hinzugefügt. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/MIG_Migration_overview_About_migration.html)

Die Kompatibilitätsmatrix für Kampagnen wurde aktualisiert. [Mehr dazu](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)

Falls zutreffend, werden in den Konfigurations- und Installationsanweisungen nun angegeben, für welches Hostmodell sie gelten. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Configuring_Campaign_server.html)

Neuer Artikel der Wissensdatenbank, in dem die Unterschiede bei der Konfiguration und den Funktionen zwischen lokalen, hybriden und verwalteten Services hervorgehoben werden. [Mehr dazu](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html)

Es wurden Anweisungen zur Installation eines Standardpakets hinzugefügt. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/INS_Initial_configuration_Installing_packages.html)

Es wurden Details zum Konfigurieren der Integration mit Audience Manager oder dem Hauptdienst &quot;Personen&quot;hinzugefügt. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/ITG_Audience_sharing_Configuring_shared_audiences_integration_in_Adobe_Campaign.html)

Die Installationsdokumentation wurde dahingehend aktualisiert, dass pgcrypto jetzt für die Campaign-Installation erforderlich ist, wenn PostreSQL verwendet wird. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/INS_Installing_Campaign_in_Linux__Prerequisites.html#Database_access_layers)

## 17.9 - 25/09/2017{#release-17-9}

**Neue Funktionen in der Version**

ACS Connector-Verbesserungen

SAP HANA Connector - [Weitere Informationen](https://docs.campaign.adobe.com/doc/AC/en/PTF_Connectors_Accessing_an_external_database.html#SAP_HANA)

Hadoop Connector via HiveSQL - [Weitere Informationen](https://docs.campaign.adobe.com/doc/AC/en/PTF_Connectors_Accessing_an_external_database.html#Hadoop)

LINE-Kanal: Messaging-Verbesserungen - [Weitere Informationen](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_messages_on_mobiles_LINE_channel.html)

**Weitere Dokumentationsaktualisierungen zu dieser Version**

Neue Abfragebeispiele wurden hinzugefügt. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Designing_queries.html#Filtering_duplicated_recipients)

Leitfaden zu Best Practices zur Bereitstellung wurde aktualisiert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliveryBestPractices.html)

Das A/B-Testmuster wurde mit fehlenden Anweisungen aktualisiert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_A-B_testing.html)

Videoanleitungen wurden aktualisiert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/Videos/Videos.html)

Abschnitt zum Aktualisieren der E-Mail-Archivierung. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html)

Klärung der Verwendung des Zeitplaners in einem Workflow. [Mehr dazu](../../workflow/using/scheduler.md)

Best Practice zum Hinzufügen eines angehaltenen Workflows [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Executing_a_workflow.html)

Neues Verfahren zur Vorverarbeitung von Dateien beim Import und bei der Nachverarbeitung beim Exportieren von Daten in einen Workflow. Lies [hier](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Importing_data.html)!

Der Quarantänemechanismus für die Dokumentation zu SMS-Nachrichten wurde aktualisiert, um die Besonderheiten des Fehlermanagements für den erweiterten generischen SMPP-Connector widerzuspiegeln. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/DLV_Monitoring_deliveries_Understanding_quarantine_management.html#SMS_quarantines).

Die Dokumentation zum Mobile App Channel wurde um ein detailliertes Verfahren zum Senden von Rich-Benachrichtigungen unter Android erweitert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_push_notifications_Setting_up_mobile_app_channel.html#Rich_notifications).

Die Dokumentation zur Inbox-Wiedergabe wurde aktualisiert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/DLV_Deliverability_management_Inbox_rendering.html).

Die Dokumentation zur Einrichtung der Web-Verfolgung wurde um ein aktualisiertes Beispiel und Hinweise erweitert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/CFG_Setting_up_web_tracking_Additional_parameters.html#Redirection_server_configuration).

Die Dokumentation zum SMS-Kanal wurde mit einigen Klarstellungen zum Abschnitt Automatische Antwort aktualisiert, die auf den erweiterten generischen SMPP-Anschluss angewendet werden. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_messages_on_mobiles_SMS_channel.html#Creating_an_SMPP_external_account).

Die Dokumentation zum Social Marketing wurde aktualisiert. [Mehr dazu](../../social/using/about-social-marketing.md).

Eine neue technische Anmerkung zur IP-Erwärmung wurde hinzugefügt. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/Technotes/AdobeCampaign_Deliverability_IP_Warming_overview.pdf).

Ein neuer Einstieg in die Build-Aktualisierung wurde hinzugefügt. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/buildUpgrade.html).

## May 2017{#release-doc-30-05-2017}

Ein neues Erste-Schritte-Handbuch ist verfügbar: Es enthält Best Practices für den Versand mit Adobe Campaign, von der Erstellung von Nachrichten über die Zielgruppenbestimmung bis zum Senden und Verfolgen von Nachrichten – [mehr dazu](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliveryBestPractices.html)

Das Sicherheitshandbuch wurde aktualisiert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/security.html)

The [&quot;Archiving emails&quot; documentation&quot;](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html) has been updated with the [&quot;Email BCC&quot;](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html#Configuring_the_BCC_email_address__on_premise_) section and the [detailed steps to activate the feature](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_emails_Sending_messages.html#Archiving_emails).

Einige Videos wurden hinzugefügt und aktualisiert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/Videos/Videos.html)

Sie erfahren, wie Sie einen Versand an Empfänger durchführen, die aus einer externen Datei geladen wurden, ohne die Datenbank zu aktualisieren. [Mehr dazu](../../delivery/using/steps-defining-the-target-population.md#selecting-external-recipients)

Außerdem wurde das Beispiel für ein Anmeldeverfahren mit doppelter Bestätigung aktualisiert. [Mehr dazu](../../web/using/use-cases--web-forms.md)

## March 2017{#release-doc-31-03-2017}

Zustellbarkeit: Das [Erste-Schritte-Handbuch](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliverability.html) wurde aktualisiert. Der Zustellbarkeitsabschnitt enthält jetzt eine detailliertere [Übersicht](https://docs.campaign.adobe.com/doc/AC/en/DLV_Deliverability_management_About_deliverability.html) sowie eine Beschreibung des [Implementierungsvorgangs und der wichtigsten Schritte](../../delivery/using/deliverability-key-points.md).

Der Abschnitt &quot;In Schüben versenden&quot; wurde verschoben und mit detaillierten Beispielen, Empfehlungen und Anwendungsbeispielen ergänzt.    [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_emails_Sending_messages.html#Sending_using_multiple_waves)

Im Abschnitt &quot;Quarantäne-Verwaltung&quot; wurde eine Tabelle hinzugefügt, in der typische Fehler im Zusammenhang mit SMS-Nachrichten beschrieben werden. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/DLV_Monitoring_deliveries_Understanding_quarantine_management.html#SMS_quarantines)

Workflows: Ein neues Beispiel für einen kanalübergreifenden Workflow wurde hinzugefügt. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/WKF_Repository_of_activities_Action_activities.html#Cross-channel_deliveries)

Marketing-Cloud-Trigger: Eine Technote zur Konfiguration und Verwendung mit Adobe Campaign wurde hinzugefügt. [mehr dazu](https://helpx.adobe.com/campaign/kb/triggers-and-campaign.html)

Das Workflow-Handbuch wurde umstrukturiert und erweitert. Dies ermöglicht das einfache Auffinden von Informationen zum [Erstellen](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Building_a_workflow.html) und [Ausführen](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Executing_a_workflow.html) eines Workflows, zur [Zielgruppenauswahl](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Targeting_data.html) und [Verwaltung](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Targeting_data.html#Data_Management) Ihrer Daten, zum [Import](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Importing_data.html)[](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_How_to_use_workflow_data.html#Updating_the_database)[ von Daten und zur Nutzung von Workflow-Daten für die Aktualisierung der Datenbank oder für den Versand](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_How_to_use_workflow_data.html#Delivering_via_a_workflow).

Ein Beispiel für einen [Import-Workflow](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_How_to_use_workflow_data.html#Delivering_via_a_workflow) wurde hinzugefügt, der anhand von [Best Practices beim Datenimport](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Importing_data.html#Import_best_practices) erstellt wurde.
Das Installationshandbuch wurde entsprechend der neuen Version aktualisiert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/INS_Architecture_and_hosting_models_General_architecture.html)

Die Kompatibilitätsmatrix wurde aktualisiert. [Mehr dazu](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)

Empfänger erhalten einen Mehrwert, wenn Sie Ihren E-Mail-Sendungen Coupons hinzufügen. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/DLV_Personalizing_deliveries_Personalized_coupons.html)

## Adobe Campaign v7 - 16.03.2017{#release-17-2}

**Neue Funktionen in der Version**

ACS Connector

Web API für Microsoft Dynamics - [Weitere Informationen](https://docs.campaign.adobe.com/doc/AC/en/PTF_Connectors_CRM_Connectors.html#Example_for_Microsoft_Dynamics)

BCC-Methode zur E-Mail-Archivierung - [Weitere Informationen](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html#Updated_email_archiving_system__BCC_)

Amazon Simple Storage Service (S3) Connector – [mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/WKF_Repository_of_activities_Event_activities.html#File_transfer)

