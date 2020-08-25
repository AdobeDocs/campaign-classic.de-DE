---
title: Aktualisierung der Dokumentation für Adobe Campaign Classic
description: Auf dieser Seite finden Sie eine nach Version geordnete Übersicht neuer Funktionen und aktueller Änderungen in der Dokumentation für Adobe Campaign Classic.
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
source-git-commit: 70efc8a7f1fab68d73e36b4373116c4aaaa0af5d
workflow-type: tm+mt
source-wordcount: '7180'
ht-degree: 97%

---


# Aktualisierungen der Dokumentation{#documentation-updates}

Auf dieser Seite werden alle neuen Funktionen und Dokumentationsaktualisierungen pro Monat und Campaign-Version aufgeführt.

Sie können auch die [Adobe Campaign Classic-Versionshinweise](../../rn/using/latest-release.md) konsultieren, um aktuelle Informationen zu erhalten.

## August 2020 {#aug-2020}

In einem speziellen Abschnitt erfahren Sie, welche Best Practices im Zusammenhang mit dem Design von Versänden und dem Senden mit Kampagne gelten. [mehr dazu](../../delivery/using/delivery-best-practices.md)

Die Landingpage der Best Practices zur Lieferbarkeit wurde verbessert, um den Zugriff auf Unterabschnitte zu erleichtern. [mehr dazu](../../delivery/using/deliverability-key-points.md)

Anleitungen zu Videos stehen jetzt in den folgenden Themen zur Verfügung:

* [Einrichten des Ermüdungsmanagements mithilfe von Typologieregeln und Vordefinierte Filtern](../../campaign/using/about-campaign-typologies.md)

* [Erstellen einer E-Mail in einer Kampagne](../../campaign/using/marketing-campaign-deliveries.md)

* [So erstellen Sie einen mehrsprachigen Newsletter mit bedingten Inhalten](../../delivery/using/conditional-content.md)

* [Konfigurieren und Bereitstellen einer Versandvorlage](../../delivery/using/creating-a-delivery-template.md)

* [So aktivieren und verwenden Sie AMP für E-Mails](../../delivery/using/defining-interactive-content.md)

* [Personalisieren von E-Mails mit dynamischen Inhaltsbausteinen](../../delivery/using/personalization-blocks.md)

* [So personalisieren Sie E-Mails mit Personalisierungsfeldern](../../delivery/using/personalization-fields.md)

* [Verwalten von Saatgut und Testversänden in einer E-Mail](../../delivery/using/steps-defining-the-target-population.md)

* [So richten Sie einen wiederkehrenden Versand ein](../../workflow/using/recurring-delivery.md)

* [Einrichten eines kontinuierlichen Versands](../../workflow/using/continuous-delivery.md)

Es wurden Informationen zu den Prüfungen und Aktionen hinzugefügt, die durchgeführt werden sollen, wenn der Fehler &quot;Hostname konnte nicht aufgelöst werden&quot;nach dem Herstellen einer Verbindung mit einem FTP-Server ausgegeben wird. [mehr dazu](../../platform/using/sftp-server-usage.md)

In der Liste der Anwendungsfälle für [Arbeitsabläufe](../../workflow/using/about-workflow-use-cases.md)wurden neue Anwendungsfälle beschrieben:

* Automatisieren der Inhaltserstellung, -ausgabe und -veröffentlichung
* Einrichten eines Empfänger-Genehmigungsprozesses vor dem Senden eines Versands
* Instanzvariablen in Abfragen aufrufen
* Anwenden eines aufgeteilten Prozentsatzes auf eine Population

Der Bereich **[!UICONTROL AND-join]** Aktivität wurde um zusätzliche Informationen zur Verwendung der Variablen sowie einen Hinweis zur Verwendung von Variablen erweitert. [mehr dazu](../../workflow/using/and-join.md)

## Juli 2020 {#july-2020}

Den Workflow-Anwendungsfällen wurde ein Anwendungsfall zum automatischen Aktualisieren einer Liste mithilfe einer inkrementellen Abfrage hinzugefügt. [Mehr dazu](../../workflow/using/about-workflow-use-cases.md)

Die [Versionshinweise](../../rn/using/latest-release.md) wurden neu organisiert: Es wurde eine [Übersichtsseite](../../rn/using/latest-release.md) mit Informationen zu Build-Status, Upgrade-Prozess, Empfehlungen und wichtigen Links hinzugefügt. Eine spezielle Seite für [Gold Standard-Versionen](../../rn/using/gold-standard.md) wurde ebenfalls hinzugefügt und die [Kompatibilitätsmatrix](../../rn/using/compatibility-matrix.md) wurde integriert.

Es wurde ein neuer Abschnitt mit Richtlinien für die Überwachung in Campaign Classic hinzugefügt. [Mehr dazu](../../production/using/monitoring-guidelines.md)

Der Abschnitt &quot;Datenschutz und Einverständnis&quot; wurde um detailliertere Informationen und nützliche Links erweitert. [Mehr dazu](../../platform/using/privacy-and-recommendations.md)

Die Seite &quot;Datenschutzverwaltung in Campaign Classic&quot; wurde mit Informationen zum Feld &quot;Vorschrift&quot; aktualisiert. Dieses Feld ist jetzt bei Verwendung der API verfügbar, die die Einrichtung eines automatischen Prozesses für Datenschutzanfragen ermöglicht. [Mehr dazu](https://helpx.adobe.com/de/campaign/kb/acc-privacy.html#ManagingPrivacyRequests)

Die Seite mit der Übersicht über die Datenschutzverwaltung wurde aktualisiert und enthält nun Informationen zum thailändischen Datenschutzgesetz (PDPA) und zum brasilianischen Datenschutzgesetz (Lei Geral de Proteção de Dados, LGPD) – [Mehr dazu](https://helpx.adobe.com/de/campaign/kb/campaign-privacy-overview.html#whatisgdpr)

Es wurden Informationen zu Unter-Workflow-Protokollen und dem Verhalten im Fehlerfall hinzugefügt. [Mehr dazu](../../workflow/using/sub-workflow.md)

Im Abschnitt **[!UICONTROL Planungsaktivität]** wurden Best Practices hinzugefügt. [Mehr dazu](../../workflow/using/scheduler.md)

## Juni 2020{#june-2020}

Der Abschnitt über das Entfernen einer unter Quarantäne gestellten Adresse wurde aktualisiert. Dies umfasst eine Klarstellung der Fälle, in denen Adressen automatisch aus der Quarantäneliste entfernt werden. [Mehr dazu](../../delivery/using/understanding-quarantine-management.md#removing-a-quarantined-address)

Es wurden Anwendungsfälle zum [Verschlüsseln](../../workflow/using/how-to-use-workflow-data.md#use-case-gpg-encrypt) und [Entschlüsseln](../../workflow/using/importing-data.md#use-case-gpg-decrypt) von Daten mit dem Control Panel und mit Campaign-Workflows hinzugefügt.

Die Begriffe &quot;Whitelist&quot; und &quot;Blacklist&quot; wurden aus der Dokumentation zu Adobe Campaign entfernt. Einige Vorkommen dieser Begriffe sind möglicherweise noch in der Benutzeroberfläche des Produkts, den Optionsnamen und dem internen Code vorhanden, werden jedoch in den kommenden Campaign-Versionen durch &quot;Blockierungsliste&quot; und &quot;Zulassungsliste&quot; ersetzt.

Die Seite über die Integration von Experience Cloud Triggers und Adobe Campaign Classic wurde [hierher](../../integrations/using/about-triggers.md) verschoben.

## 20.2 - 08/06/2020{#release-20-2}

**Neue Funktionen in der Version**

Unterstützung für Emoticons – [mehr dazu](../../delivery/using/customizing-emoticon-list.md)

Azure Synapse FDA-Connector – [mehr dazu](../../platform/using/specific-configuration-database.md#configure-access-to-azure-synapse)

Datenschutzgesetze in Thailand und Brasilien – [mehr dazu](https://helpx.adobe.com/de/campaign/kb/acc-privacy.html#ManagingPrivacyRequests)

**Weitere Aktualisierungen der Dokumentation zu dieser Version**

Die neue Option zum Rückgängigmachen der Veröffentlichung einer Transaktionsnachrichten-Vorlage wird in [diesem Abschnitt](../../message-center/using/template-unpublication.md) beschrieben.

Neue Optionen wurden zur Liste der Campaign Classic-Optionen hinzugefügt. Mit diesen Optionen können Einschränkungen beim Versand von E-Mails festgelegt werden, die von einer personalisierten URL und Anhängen heruntergeladene Bilder enthalten. [Mehr dazu](../../installation/using/configuring-campaign-options.md#delivery)

Die neue Option **Versandteile in der Datenbank vorbereiten** wird in [diesem Abschnitt](../../delivery/using/steps-validating-the-delivery.md#improving-delivery-analysis) beschrieben.

Der Abschnitt &quot;Validieren des Versands&quot; wurde klarer gestaltet und aktualisiert. [Mehr dazu](../../delivery/using/steps-validating-the-delivery.md)

Die Parameter für den neuen Trackinglink-Signaturmechanismus wurden dem Abschnitt [Server-Konfigurationsdatei](../../installation/using/the-server-configuration-file.md) hinzugefügt.

Die Kompatibilitätsmatrix wurde aktualisiert. [Mehr dazu](https://helpx.adobe.com/de/campaign/kb/compatibility-matrix.html)

Der Abschnitt zum Bereinigungs-Workflow wurde aktualisiert. [Mehr dazu](../../production/using/database-cleanup-workflow.md)

Die Campaign-Netzwerkendpunkte wurden in diesen [Abschnitt](../../installation/using/campaign-network-endpoints.md) verschoben.

Der Abschnitt &quot;Spam Assassin-Installation&quot; wurde mit dem Namen der neuen Installationsdatei aktualisiert. [Mehr dazu](../../installation/using/configuring-spamassassin.md#installing-spamassassin)

Der Abschnitt zur Duplizierung von Umgebungen wurde aktualisiert. [Mehr dazu](../../production/using/duplicating-environments.md#step-2---export-the-target-environment-configuration--dev-)

## Mai 2020 {#may-2020}

Der Abschnitt zum Monitoring der Zustellbarkeit wurde an eine andere Stelle verschoben und überarbeitet. [Mehr dazu](../../delivery/using/monitoring-deliverability.md)

Der Abschnitt zur Behebung von Problemen mit der Zustellbarkeit wurde verschoben und überarbeitet. [Mehr dazu](../../delivery/using/deliverability-faq.md)

Der Abschnitt zu Zustellbarkeitsrichtlinien beim Start einer neuen Plattform wurde überarbeitet. [Mehr dazu](../../delivery/using/starting-new-platform.md)

Der Abschnitt zum Senden von Transaktions-E-Mails mit Anhängen wurde an eine andere Stelle verschoben und aktualisiert. [Mehr dazu](../../message-center/using/transactional-email-with-attachments.md)

Der Abschnitt mit Best Practices für Datenpackages wurde verschoben und überarbeitet. [Mehr dazu](../../platform/using/working-with-data-packages.md#data-package-best-practices)

## April 2020 {#april-2020}

Die Tabelle mit den FDA-Berechtigungen wurde in die Dokumentation „Zugriff auf eine externe Datenbank (FDA)“ verschoben. [Mehr dazu](../../platform/using/remote-database-access-rights.md)

Die FAQs wurden um Tipps zum Löschen von Soft Cache und Hard Cache erweitert. [Mehr dazu](../../platform/using/faq-campaign-config.md#perform-soft-cache-clear)

Der Abschnitt mit Best Practices für das Datenmodell enthält jetzt zusätzliche Informationen über Indizes. [Mehr dazu](../../configuration/using/data-model-best-practices.md#indexes)

Der Abschnitt zum integrierten Datenmodell von Adobe Campaign enthält jetzt zusätzliche Details zu den einzelnen Tabellen. [Mehr dazu](../../configuration/using/data-model-description.md)

Anwendungsbeispiele für Workflows wurden aktualisiert und in thematische Bereiche neu angeordnet. [Mehr dazu](../../workflow/using/about-workflow-use-cases.md)

Die Abschnitte [Bounce-Message-Qualifizierung](../../delivery/using/understanding-delivery-failures.md#bounce-mail-qualification) und [E-Mail-Verwaltungsregeln](../../delivery/using/understanding-delivery-failures.md#email-management-rules) enthalten aktualisierte Informationen.

Der Artikel zum Adobe Campaign Enhanced MTA wurde aktualisiert. Er gilt jetzt nur für Campaign Classic. [Mehr dazu](https://helpx.adobe.com/de/campaign/kb/acc-campaign-enhanced-mta.html)

## März 2020 {#march-2020}

Die Seite mit Best Practices für das Datenmodell enthält jetzt neue Abschnitte wie [Sequenzen](../../configuration/using/data-model-best-practices.md#sequences), [Leistung](../../configuration/using/data-model-best-practices.md#performance) und [große Tabellen](../../configuration/using/data-model-best-practices.md#large-tables). [Mehr dazu](../../configuration/using/data-model-best-practices.md)

Ein neuer Abschnitt, in dem das integrierte Datenmodell von Adobe Campaign beschrieben wird; Interaktion zwischen Tabellen ist nun verfügbar. [Mehr dazu](../../configuration/using/data-model-description.md)

Zusätzliche wichtige Links wurden zur Startseite der Dokumentation hinzugefügt. [Mehr dazu](../../campaign-classic-home.md)

Es wurde ein Anwendungsfall hinzugefügt, der beschreibt, wie ein dynamisches Angebot aus Adobe Target in eine E-Mail in Adobe Campaign integriert werden kann. [Mehr dazu](../../integrations/using/inserting-a-dynamic-image.md)

Ein neuer Abschnitt mit den verschiedenen Sprachen, die in Adobe Campaign verfügbar sind, ist jetzt verfügbar. [Mehr dazu](../../platform/using/adobe-campaign-workspace.md#languages)

Die Seite zu Richtlinien für die Zugriffsverwaltung enthält jetzt zusätzliche Informationen zu spezifischen Berechtigungen. [Mehr dazu](../../platform/using/access-management.md#named-rights)

## Februar 2020 {#february-2020}

Es gibt jetzt einen neuen Abschnitt, in dem Best Practices und wichtige Empfehlungen zum Entwerfen des Adobe Campaign-Datenmodells erläutert werden. [Mehr dazu](../../configuration/using/data-model-best-practices.md)

Es gibt einen neuen Abschnitt zu technischen E-Mail-Konfigurationen. [Mehr dazu](../../installation/using/email-deliverability.md)

Die häufig gestellten Fragen zur Zustellbarkeit enthalten jetzt zusätzliche Details zur Fehlernachricht &quot;Kontingente ausgeschöpft&quot;. [Mehr dazu](https://helpx.adobe.com/de/campaign/kb/acc-deliverability-faq.html#FAQ)

AMP for E-Mail wird jetzt von neuen E-Mail-Anbietern unterstützt: Die zugehörige Dokumentation wurde aktualisiert. [Mehr dazu](../../delivery/using/defining-interactive-content.md)

Der Abschnitt zur E-Mail-Archivierung wurde verbessert. [Mehr dazu](../../installation/using/email-archiving.md#recommendations-and-limitations)

## 20.1 - 17/02/2020{#release-20-1}

**Neue Funktionen in der Version**

Snowflake FDA-Connector – [mehr dazu](../../platform/using/specific-configuration-database.md#configure-access-to-snowflake)

Hadoop FDA Connector-Erweiterungen – [mehr dazu](../../platform/using/specific-configuration-database.md#configure-access-to-hadoop-3)

**Weitere Dokumentationsaktualisierungen zu dieser Version**

Die Anleitungen für [Installation](../../installation/using/before-reading.md), [Produktion](../../production/using/foreword.md) und [Konfiguration](../../configuration/using/additional-parameters.md) wurden mit der neuen systemd-Einheit aktualisiert, die vom nlserver-Dienststart verwendet wird. Sie können weiterhin &quot;/etc/init.d/nlserver6&quot; verwenden. Adobe empfiehlt jedoch, für die Interaktion mit dem nlserver-Dienst ab jetzt den Befehl &quot;systemctl&quot; zu verwenden.

Das Installationshandbuch wurde aktualisiert und mit der neuesten Version der Kompatibilitätsmatrix synchronisiert. Neu unterstützte Systeme wurden hinzugefügt. Veraltete Vorfälle und nicht mehr unterstützte Systeme wurden entfernt. [Mehr dazu](../../installation/using/before-reading.md)

Die Kompatibilitätsmatrix wurde mit den Hadoop 3.0- und Snowflake-FDA-Connectoren aktualisiert. [Mehr dazu](https://helpx.adobe.com/de/campaign/kb/compatibility-matrix.html)

Eine Best Practice zur IP-Affinität wurde dem Installationshandbuch hinzugefügt. [Mehr dazu](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use)

Der Abschnitt zum Workflow für die Datenbankbereinigung wurde aktualisiert. Die bereitgestellten Batch-Zahlen spiegeln nun die Code-Implementierung wider. [Mehr dazu](../../production/using/database-cleanup-workflow.md)

Eine Einschränkung zu FDA über HTTP wurde dem Handbuch zu Transaktionsnachrichten hinzugefügt. [Mehr dazu](../../production/using/database-cleanup-workflow.md)

Es wurden Informationen zu der neuen Option hinzugefügt, mit der Sie einen Timeout-Zeitraum für die Workflow-Aktivitäten **[!UICONTROL JavaScript-Code]** und **[!UICONTROL Erweiterter JavaScript-Code]** definieren können. [Mehr dazu](../../workflow/using/sql-code-and-javascript-code.md)

Informationen wurden zur neuen Ansicht **[!UICONTROL Start ausstehend]** hinzugefügt, die unter dem Knoten **[!UICONTROL Administration]** > **[!UICONTROL Audit]** > **[!UICONTROL Status der Workflows]** verfügbar ist. [Mehr dazu](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

Der Leitfaden [Senden von Push-Benachrichtigungen](../../delivery/using/about-mobile-app-channel.md) wurde verschoben, neu organisiert und mit klareren Informationen optimiert.

Der neue Parameter für die URL-Berichtkonfiguration wird [hier](../../reporting/using/properties-of-the-report.md#defining-additional-settings) erläutert.

Die **On-Premise- und Hosted-Leistungsmatrix von Campaign Classic** wurde mit den neuen FDA-Connectoren aktualisiert. [Mehr dazu](https://helpx.adobe.com/de/campaign/kb/acc-on-prem-vs-hosted.html)

Die Seite mit der **Campaign Classic-Leistungsmatrix** wurde aktualisiert. [Mehr dazu](https://helpx.adobe.com/de/campaign/kb/compatibility-matrix.html)

Der neue Workflow zur **[!UICONTROL Bereinigung von Nmsaddress]** wird [hier](../../production/using/database-cleanup-workflow.md#cleanup-of-nmsaddress) erläutert.

Bei Verwendung einer Abfrageaktivität in einem Workflow wurde eine Einschränkung hinzugefügt. [Mehr dazu](../../workflow/using/query.md)

Es wurde ein neuer Abschnitt hinzugefügt, in dem die verbesserten Validierungsregeln für E-Mail-Adressen detailliert beschrieben werden, die im Falle eines Softbounce eine Adresse unter Quarantäne stellen. [Mehr dazu](../../delivery/using/understanding-quarantine-management.md#soft-error-management)

Der Parameter aus der Konfigurationsdatei, der angibt, ob eine Instanz den erweiterten MTA verwendet oder nicht, wurde in die Dokumentation aufgenommen. [Mehr dazu](../../installation/using/the-server-configuration-file.md#mta)

## Januar 2020 {#january-2020}

Der Abschnitt „Zulieferbarkeit“ wurde verschoben, neu organisiert und mit aktualisierten Inhalten erweitert. [Mehr dazu](../../delivery/using/about-deliverability.md)

Ein neuer Abschnitt mit den Grundlagen des Adobe Campaign Classic-Datenmodells und dem Zugriff auf die Beschreibung der einzelnen Tabellen ist jetzt verfügbar. [Mehr dazu](../../configuration/using/about-data-model.md)

Der Artikel zu Adobe Campaign Enhanced MTA wurde mit detaillierteren Informationen zur Installation eines spezifischen Typologie-Packages in Instanzen aktualisiert, die die erforderlichen Enhanced MTA-Header nicht zu jeder Nachricht hinzufügen. [Mehr dazu](https://helpx.adobe.com/de/campaign/kb/acc-campaign-enhanced-mta.html#impacts)

Die Anwendungsbeispiele im Zusammenhang mit der Abfragegestaltung wurden in separate Abschnitte umstrukturiert. [Mehr dazu](../../workflow/using/querying-recipient-table.md)

Ein neuer Abschnitt über Tipps und Tricks zur Angebotsverwaltung und zum Einsatz des Interaction-Modules in Adobe Campaign Classic ist jetzt verfügbar. [Mehr dazu](../../interaction/using/interaction-best-practices.md#tips-managing-offers)

Die Interaction-Dokumentation wurde mit Links zu verschiedenen Videos angereichert, die zum besseren Verständnis der Verwaltung von Angeboten beitragen. [Mehr dazu](../../interaction/using/interaction-and-offer-management.md)

Der Best Practice-Artikel über die Optimierung der auf Ihrer Instanz laufenden Abfragen wurde in die Dokumentation integriert. [Mehr dazu](../../workflow/using/query.md#optimizing-queries)

Das Reporting-Handbuch wurde aktualisiert und neu organisiert. [Mehr dazu](../../reporting/using/about-adobe-campaign-reporting-tools.md)

Es wurde ein Beispiel für die Verwendung einer Instanzvariablen in einem Workflow hinzugefügt. [Mehr dazu](../../workflow/using/javascript-scripts-and-templates.md)

## Dezember 2019 {#december-2019}

Die Option „WdbcOptions_TempDbName“ wurde der Liste der Kampagnenoptionen hinzugefügt. [Mehr dazu](../../installation/using/configuring-campaign-options.md)

Die Seite „FDA-Matrix“ wurde [hierher](../../platform/using/remote-database-access-rights.md) verschoben.

Die Seite „Zugriffsberechtigungsmatrix“ wurde [hierher](https://docs.adobe.com/content/help/de-DE/campaign-classic/using/getting-started/administration-basics/assets/accessrights.pdf) verschoben.

Der Abschnitt, der beschreibt, wie man interaktive Inhalte mit AMP definiert, wurde verschoben. [Mehr dazu](../../delivery/using/defining-interactive-content.md)

## 19.2 – 2.12.2019{#release-19-2}

**Neue Funktionen in der Version**

California Consumer Privacy Act (CCPA) – [mehr dazu](https://helpx.adobe.com/de/campaign/kb/acc-privacy.html)

Interaktive Inhalte mit AMP – [mehr dazu](../../delivery/using/defining-interactive-content.md)

Workflow-Live-Monitoring – [mehr dazu](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

Sicherer SMS-Versand (TLS) – [mehr dazu](https://helpx.adobe.com/de/campaign/kb/sms-connector-protocol-and-settings.html)

**Weitere Dokumentationsaktualisierungen zu dieser Version**

Die Adobe Campaign Enhanced MTA-Dokumentation ist jetzt verfügbar. [Mehr dazu](https://helpx.adobe.com/de/campaign/kb/acc-campaign-enhanced-mta.html)

Es wurde ein neuer Abschnitt hinzugefügt, in dem beschrieben wird, wie Sie Fehler in einem Workflow beheben können, der im Status „Schnellstmöglicher Start“ in einer Kampagne verbleibt.  [Mehr dazu](../../production/using/workflow-execution.md#start-as-soon-as-possible-in-campaigns)

Die neuen Optionen „NmsOperation_DeliveryPreparationWindow“ und „WdbcKillSessionPolicy“ wurden zur Liste der Campaign-Optionen hinzugefügt. [Mehr dazu](../../installation/using/configuring-campaign-options.md)

Ein neues Dokument mit den Grundlagen des Adobe Campaign Classic-Datenmodells ist jetzt verfügbar. [Mehr dazu](https://helpx.adobe.com/de/campaign/kb/acc-datamodel.html)

Die neue Option **Maximale Laufzeit der Personalisierung** in den Versandeigenschaften wird in diesem [Abschnitt](../../delivery/using/personalization-fields.md#timing-out-personalization) beschrieben.

Die Beispiele für API-Aufrufe mit **HttpServletRequest** mit logon() und query() wurden aktualisiert. [Mehr dazu](../../configuration/using/web-service-calls.md)

In der Schemadefinition wurde eine Empfehlung für das Attribut **sqlDefault** hinzugefügt. [Mehr dazu](../../configuration/using/elements-and-attributes.md#attribute-description)

Die Integration zwischen Adobe Campaign und der Adobe Echtzeit-Kundendatenplattform wird jetzt im Handbuch **Integration mit Adobe Experience Cloud** beschrieben. [Mehr dazu](../../integrations/using/about-campaign-integrations.md)

## November 2019 {#november-2019}

Den Abschnitten [Multiplexing des Mid-Sourcing-Servers](../../installation/using/mid-sourcing-server.md#multiplexing-the-mid-sourcing-server) und [Mehrere Kontrollinstanzen](../../message-center/using/transactional-messaging-architecture.md#supporting-several-control-instances) wurde eine Warnung hinzugefügt, die darauf hinweist, dass diese Implementierungen für vollständig gehostete und hybride Clients nicht unterstützt werden.

Es wurde ein neuer Abschnitt hinzugefügt, in dem beschrieben wird, wie die beim Senden einer E-Mail verwendete Zeichencodierung erzwungen wird. [Mehr dazu](../../delivery/using/sending-messages.md#character-encoding)

Der Abschnitt „Zugriffsverwaltung“ wurde mit dem **Datenschutzrecht** aktualisiert. [Mehr dazu](../../platform/using/access-management.md#named-rights)

Es wurden Informationen hinzugefügt, die festlegen, dass der Inhalt von Personalisierungsfeldern 1024 Zeichen nicht überschreiten darf. [Mehr dazu](../../delivery/using/personalization-fields.md)

Die Control Panel-Dokumentation wurde in den neuen kollaborativen Dokumentationssatz integriert – [Mehr dazu](https://docs.adobe.com/content/help/de-DE/control-panel/using/control-panel-home.html)

Die ersten Schritte zum Thema Best Practices für den Versand wurden aktualisiert – [Mehr dazu](../../delivery/using/delivery-best-practices.md)

## Oktober 2019 {#october-2019}

Die Liste der Fehlermeldungen für Campaign Standard und Campaign Classic wurde aktualisiert. [mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

Die ersten Schritte zum Thema DSGVO wurden verbessert und erweitert. Es handelt sich nun um eine Dokumentation rund um die Gewährleistung von Datenschutz gemäß den Bestimmungen der DSGVO und des CCPA – [Mehr dazu](https://helpx.adobe.com/content/help/de/campaign/kb/campaign-privacy.html)

Eine neue Seite zur Fehlerbehebung wurde zum Tracking in Campaign Classic hinzugefügt. [Mehr dazu](https://helpx.adobe.com/de/campaign/kb/classic-tracking-troubleshooting.html)

Eine neue Seite mit Best Practices für Adobe Analytics Data Connector wurde hinzugefügt. [Weitere Informationen zu Adobe Analytics Data Connector](../../platform/using/adobe-analytics-data-connector.md)

Die ersten Schritte zum Thema Best Practices bei der Zustellung wurden aktualisiert. [Mehr dazu](../../delivery/using/delivery-best-practices.md)

In der Dokumentation zum SMS-Kanal wurde eine Empfehlung hinzugefügt, um Probleme bei der Verwendung mehrerer externer Konten zu vermeiden, indem der erweiterte allgemeine SMPP-Connector mit demselben Provider-Konto genutzt wird. [Mehr dazu](../../delivery/using/sms-channel.md#automatic-reply)

In der Dokumentation zur Planungsaktivität wurden Informationen darüber hinzugefügt, wie mehrere gleichzeitige Ausführungen eines Workflows verhindert werden können. [Mehr dazu](../../workflow/using/scheduler.md)

Die Schritte zum Konfigurieren des Inbox Renderings für On-Premise-Installationen wurden der Dokumentation hinzugefügt. [Mehr dazu](../../delivery/using/inbox-rendering.md#activating-inbox-rendering)

## September 2019 {#september-2019}

Eine neue Seite wurde hinzugefügt, um allgemeine Richtlinien für die Wartung von Campaign Classic bereitzustellen. [Mehr dazu](../../production/using/monitoring-guidelines.md)

Die Informationen zum Workflow-Monitoring wurden in einem neuen Abschnitt zusammengefasst. [Mehr dazu](../../workflow/using/monitoring-workflow-execution.md)

Eine neue Seite mit allgemeinen Richtlinien für das Tracking in Adobe Campaign Classic wurde hinzugefügt. [Mehr dazu](https://helpx.adobe.com/de/campaign/kb/acc-tracking.html)

Die Best Practices für die Leistungsverbesserung von Workflows und Sendungen wurden aktualisiert. [Weitere Informationen zu Workflows](../../workflow/using/workflow-best-practices.md) und [Sendungen](../../delivery/using/monitoring-a-delivery.md#best-practices-performance).

## 19.1 – 30.5.2019{#release-19-1}

**Neue Funktionen in der Version**

Control Panel – [mehr dazu](https://docs.adobe.com/content/help/de-DE/control-panel/using/control-panel-home.html)

Audit-Protokoll – [mehr dazu](../../production/using/audit-trail.md)

**Weitere Dokumentationsaktualisierungen zu dieser Version**

Es wurden neue häufig gestellte Fragen zur Build-Aktualisierung erstellt. [Mehr dazu](https://helpx.adobe.com/de/campaign/kb/build-upgrade-faq.html)

Die [Kompatibilitätsmatrix](https://helpx.adobe.com/de/campaign/kb/compatibility-matrix.html) wurde aktualisiert. Die Liste der unterstützten Datenbanksysteme sowie die Android-/iOS-Versionen und die zugehörigen SDKs wurden aktualisiert. Die [Kompatibilitätsmatrix 19.0](https://helpx.adobe.com/de/campaign/kb/compatibility-matrix-19-0.html) wurde aktualisiert.

Die Seite mit veralteten und entfernten Funktionen in Campaign Classic wurde aktualisiert. [Mehr dazu](https://helpx.adobe.com/de/campaign/kb/deprecated-and-removed-features.html)

Die Beschreibung der Server-Konfigurationsdatei wurde dem Installationshandbuch hinzugefügt. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/INS_Appendices_The_server_configuration_file.html)

Es wurde ein Abschnitt hinzugefügt, in dem die Installations- und Konfigurationsschritte für gehostete und hybride Modelle beschrieben werden. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/INS_Hybrid_and_Hosted_models_Introduction.html)

Es wurde ein Abschnitt hinzugefügt, der die Deinstallationsschritte des Campaign-Servers beschreibt. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/INS_Appendices_Uninstalling_Campaign.html)

Die ersten Schritte zum Thema [Sicherheit](https://docs.campaign.adobe.com/doc/AC/getting_started/DE/security.html), [Zustellbarkeit](https://docs.adobe.com/content/help/de-DE/campaign-classic/using/sending-messages/deliverability-management/about-deliverability.html) und [Datenschutz](https://helpx.adobe.com/de/campaign/kb/acc-privacy.html) wurden aktualisiert.

Die Beschreibung der Workflow-Option für die Vorab-Bearbeitung wurde aktualisiert, um Produktänderungen widerzuspiegeln. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/WKF_Repository_of_activities_Action_activities.html#Data_loading__file_)

Die Technote zu den Marketing Cloud-Triggers wurde aktualisiert. [Mehr dazu](https://helpx.adobe.com/de/campaign/kb/triggers-and-campaign.html)

Die Liste der Fehlermeldungen wurde aktualisiert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

Es wurden weitere Informationen zu SOAP-Authentifizierungsmethoden für Transaktionsnachrichten hinzugefügt. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/MCE_Introduction_Event_description.html)

Die Apache-Konfigurationsschritte wurden aktualisiert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/INS_Installing_Campaign_in_Linux__Integration_into_a_Web_server.html#Configuring_Apache_web_server_in_RHEL)

Es wurde eine neue Seite mit der Liste der Endpunkte für Campaign Standard und Classic hinzugefügt. [Mehr dazu](https://helpx.adobe.com/de/campaign/kb/campaign-endpoints.html)

Der Artikel zu den Best Practices für Datenpackages wurde aktualisiert. [Mehr dazu](https://helpx.adobe.com/de/campaign/kb/data-package-best-practices.html)

Die Dokumentation zur Angebotsverwaltung wurde um einen neuen Abschnitt mit Best Practices erweitert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/ITA_Interaction_Overview_Interaction_best_practices.html)

Es wurde ein neuer Knowledgebase-Artikel zur Verwendung des Angebotskatalogs in Adobe Campaign Classic erstellt. [Mehr dazu](https://helpx.adobe.com/de/campaign/kb/offer-best-practices.html)

Der Abschnitt zur Unter-Workflow-Aktivität wurde um ein Anwendungsbeispiel erweitert. [Mehr dazu](../../workflow/using/sub-workflow.md)

Der Knowledgebase-Artikel [Funktionsmatrix für On-Premise- und gehostete Campaign-Versionen](https://helpx.adobe.com/de/campaign/kb/acc-on-prem-vs-hosted.html) wurde mit Informationen zur Archivierung von E-Mails erweitert.

Die Dokumentation zu Transaktionsnachrichten wurde mit einem Hinweis zur Vorlagenpublikation aktualisiert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/MCE_Template_publication.html)

Der Abschnitt über nicht verarbeitete Bounce Messages wurde um weitere Details zu den Feldern „Weiterleitungsadresse“ und „Fehleradresse“ erweitert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/INS_Initial_configuration_Deploying_an_instance.html#Unprocessed_bounce_mails)

Ein neuer Abschnitt über Best Practices zur Workflow-Planung wurde hinzugefügt. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Workflow_best_practices.html#Execution_and_performance)

Der Liste der Campaign-Optionen wurden zwei neue Optionen hinzugefügt: XtkSecurity_Restrict_EditXML und NmsOperation_OperationMgtDebug. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/INS_Appendices_Configuring_Campaign_options.html)

Es wurden Informationen zu den verschiedenen in Campaign Classic verfügbaren externen Konten und deren Konfiguration hinzugefügt. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/PTF_Administration_basics_External_accounts.html)

Der Abschnitt über Analytics Data Connector wurde aktualisiert, um Änderungen an der Benutzeroberfläche widerzuspiegeln. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/PTF_Connectors_Adobe_Analytics_Data_Connector.html)

Es wurden Informationen zum Billing-Bericht hinzugefügt. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/PRO_Production_procedures_Monitoring_processes.html#Billing_report)

Die Dokumentation zur Integration freigegebener Zielgruppen wurde aktualisiert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/ITG_Audience_sharing_Configuring_shared_audiences_integration_in_Adobe_Campaign.html)

Die folgenden Technotes wurden aktualisiert: [SMS-Connector-Protokoll und Einstellungen](https://helpx.adobe.com/de/campaign/kb/sms-connector-protocol-and-settings.html) und [Automatische Erzeugung von Sequenzen](https://helpx.adobe.com/de/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence).

Der Abschnitt „Technische Workflows“ wurde aktualisiert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/WKF_Technical_workflows_About_technical_workflows.html)

Das Installationserfahren für den Campaign-Domain-Namen wurde verbessert und aktualisiert. [Mehr dazu](https://helpx.adobe.com/de/campaign/kb/domain-name-delegation.html)

Das Migrationsverfahren für Android-Apps von Google Cloud Messaging (GCM) zu Firebase Cloud Messaging (FCM) wurde aktualisiert. [Mehr dazu](https://helpx.adobe.com/de/campaign/kb/migrate-to-fcm.html)

Das Handbuch zur Dimensionierung von Hardware für Campaign wurde aktualisiert. [Mehr dazu](https://helpx.adobe.com/de/campaign/kb/hardware-sizing-guide.html)

Informationen zum Query Banding für das externe Teradata-Konto wurden hinzugefügt. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/PTF_Administration_basics_External_accounts.html#External_database_external_account)

## Januar 2019{#release-doc-16-01-2019}

Die Technote zu den Marketing Cloud-Triggers wurde aktualisiert. [Mehr dazu](https://helpx.adobe.com/de/campaign/kb/triggers-and-campaign.html)

Im Abschnitt über die Angebotsvalidierung wurde ein Hinweis hinzugefügt, dass die Aussage „Validierter Inhalt“ darauf hinweist, dass der Prozess der Inhaltsvalidierung abgeschlossen wurde, unabhängig davon, ob alle Angebote aktiviert/validiert wurden oder nicht. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/ITA_Managing_an_offer_catalog_Approving_and_activating_an_offer.html#Approving_offer_content)

Im Installationshandbuch wurde ein neuer Abschnitt mit Optionen aus dem Knoten „Administration/Plattform/Optionen“ hinzugefügt. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/INS_Appendices_Configuring_Campaign_options.html)

Es wurden Informationen über die Verwendung von Testadressen zum Schutz Ihrer Mailing-Liste hinzugefügt. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/DLV_Using_seed_addresses_About_seed_addresses.html)

Wichtige Schritte beim Erstellen und Durchführen eines Versands wurden in einem neuen Abschnitt zusammengefasst, wobei bei Bedarf auf die verschiedenen Kanäle verwiesen wird. [Mehr dazu](../../delivery/using/steps-about-delivery-creation-steps.md)

Der Abschnitt [E-Mail-Archivierung](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html) wurde verschoben, neu organisiert und mit präziseren Informationen verbessert:

* Es wurden Best Practices hinsichtlich der Parameter für E-Mails pro Verbindung und BCC-Sende-IPs hinzugefügt. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html#Best_practices)

* Die Schritte zum Aktualisieren auf das neue E-Mail-Archivierungssystem (BCC) wurden aktualisiert, wenn Sie die E-Mail-Archivierung bereits mit einem älteren Build (vor Adobe Campaign 17.2 - Build 8795) verwendet haben. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html#Updated_email_archiving_system__BCC_)

Dem Handbuch für die Automatisierung mithilfe von Workflows wurde ein Anwendungsbeispiel hinzugefügt: Benutzern personalisierte Warnungen senden. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Sending_personalized_alerts_to_operators.html)

Der Abschnitt „Auf eine neue Version migrieren“ wurde aktualisiert. Die Dokumentation beschreibt jetzt nur die Schritte für eine Migration von einer älteren Version zu Adobe Campaign Classic v7, da eine Migration zu Adobe Campaign v6.11 nicht mehr möglich ist. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/MIG_Migration_overview_About_migration.html)

Der Abschnitt „Weitere Zustellversuche nach einem vorübergehend fehlgeschlagenen Versand“ wurde präzisiert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/DLV_Monitoring_deliveries_Understanding_delivery_failures.html#Retries_after_a_delivery_temporary_failure)

Dem Abschnitt „E-Mail-Inhalt erstellen“ wurden Links zum Abschnitt „Digital Content Editor“ hinzugefügt. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_emails_Defining_the_email_content.html#Message_content)

Der Abschnitt „Transaktionsnachrichten-Architektur“ wurde mit einer Warnung aktualisiert, in der angegeben wird, dass die Kontroll- und Ausführungsinstanzen nicht auf demselben Rechner installiert werden können. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/MCE_Introduction_Transactional_messaging_architecture.html)

Der Abschnitt „Workflow-Monitoring“ wurde mit einem Hinweis für Builds zwischen 8700 und 8977 (18.10) aktualisiert, einschließlich eines Links zur Technote zur Installation des Workflow-Heatmap-Packages für diese Builds. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/PRO_Production_procedures_Monitoring_processes.html#About_the_Workflow_HeatMap)

Es wurde ein Anwendungsbeispiel zum Senden einer E-Mail mit benutzerdefinierten Datenfeldern mithilfe der Anreicherungsaktivität in einem Workflow hinzugefügt. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Email_enrichment_with_custom_date_fields.html)

Die Funktionsvideos wurden [hierher](https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/overview.html) verschoben.

Es wurden zwei Technotes zu [Teradata](https://helpx.adobe.com/de/campaign/kb/campaign_fda_teradata.html) und [MySQL 5.7](https://helpx.adobe.com/de/campaign/kb/campaign_fda_mysql.html) hinzugefügt.

## 18.10 – 05.11.2018{#release-18-10}

**Neue Funktionen in der Version**

Verbesserungen bei Push-Benachrichtigungen – [mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_push_notifications_Setting_up_mobile_app_channel.html#Integrating_the_SDK_into_the_mobile_application)

SQL-Data-Management-Aktivität – [mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/WKF_Repository_of_activities_Action_activities.html#SQL_Data_Management)

Workflow-Monitoring – [mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/PRO_Production_procedures_Monitoring_processes.html#Workflow_monitoring)

**Weitere Dokumentationsaktualisierungen zu dieser Version**

Campaign-Classic-APIs sind jetzt auf einer [eigenen Seite](https://docs.campaign.adobe.com/doc/AC/en/jsapi/index.html) verfügbar. Wenn Sie die Jsapi.chm-Datei verwendet haben, sollten Sie jetzt die neue Online-Version nutzen.

Die Kompatibilitätsmatrix wurde aktualisiert. [Mehr dazu](https://helpx.adobe.com/de/campaign/kb/compatibility-matrix.html)

Die Seite mit veralteten und entfernten Funktionen in Campaign Classic wurde aktualisiert. [Mehr dazu](https://helpx.adobe.com/de/campaign/kb/deprecated-and-removed-features.html)

In den [Versionshinweisen](https://docs.adobe.com/content/help/de-DE/campaign-classic/using/release-notes/latest-release.html) und [älteren Versionshinweisen](https://docs.adobe.com/content/help/de-DE/campaign-classic/using/release-notes/latest-release.html) wurde eine Warnung für zurückgerufene Builds hinzugefügt. Es wurden außerdem kumulative Builds für 17.9, 18.4 und 18.6 hinzugefügt.

Die ersten Schritte zum Thema [Sicherheit](https://docs.campaign.adobe.com/doc/AC/getting_started/DE/security.html), [Zustellbarkeit](https://docs.adobe.com/content/help/de-DE/campaign-classic/using/sending-messages/deliverability-management/about-deliverability.html) und [Build-Aktualisierung](https://docs.campaign.adobe.com/doc/AC/getting_started/DE/buildUpgrade.html) wurden aktualisiert.

Die ersten Schritte zum Thema [Datenschutz](https://helpx.adobe.com/de/campaign/kb/acc-privacy.html) wurden aktualisiert und enthalten Informationen zum externen Aufrufen der API und dazu, wie mit queryDef der Status abgefragt und die DSGVO-Datei heruntergeladen werden kann.

Es wurde ein Anwendungsbeispiel für Transaktionsnachrichten hinzugefügt, in dem E-Mail-Anhänge dynamisch zu ausgehenden Sendungen hinzugefügt werden. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/MCE_Use_case_Purpose.html)

Der Abschnitt zur Fehlerbehebung bei Verbindungsschwellenwerten wurde aktualisiert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/PRO_Troubleshooting_Connection_thresholds.html)

Es wurde ein Abschnitt zum Konfigurieren einer Proxy-Verbindung hinzugefügt. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Configuring_Campaign_server.html#Proxy_connection_configuration)

Der Abschnitt zur Einschränkung autorisierter externer Befehle wurde aktualisiert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Configuring_Campaign_server.html#Restricting_authorized_external_commands)

Es wurde ein Abschnitt zur Fehlerbehebung im Zusammenhang mit der SFTP-Nutzung hinzugefügt. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/PTF_Importing_and_exporting_data_SFTP_server_usage.html)

Das Übersichtskapitel des Leitfadens zum Senden von Nachrichten wurde neu organisiert. Es wurden Informationen zum globalen Prozess der Versanderstellung und zu den verschiedenen Versandtypen hinzugefügt. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/DLV_About_deliveries_and_channels_Communication_channels.html)

Die Liste der Fehlermeldungen wurde aktualisiert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

Der Abschnitt zur Verwendung von Testadressen wurde in das Übersichtskapitel des Leitfadens zum Senden von Nachrichten verschoben. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/DLV_Using_seed_addresses_About_seed_addresses.html)

Es wurde ein neues Anwendungsbeispiel für den Workflow zum Verwalten von Updates aus gleichzeitigen Workflow-Ausführungen hinzugefügt. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Coordinating_data_updates.html)

Der Abschnitt „Inbox Rendering“ wurde mit weiteren Informationen zu Litmus und einem detaillierteren Verfahren aktualisiert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/DLV_Deliverability_management_Inbox_rendering.html#Multiplexing_the_mid-sourcing_server)

Der Abschnitt „SpamAssassin“ wurde verbessert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/DLV_Deliverability_management_SpamAssassin.html)

Im Abschnitt „Verwalten von Marketing-Müdigkeit mit Druckregeln“ wurde ein Anwendungsbeispiel hinzugefügt. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/CMP_Campaign_Optimization_Pressure_rules.html#Sending_only_the_highest-weighted_messages)

Ein neues Anwendungsbeispiel ist verfügbar, das beschreibt, wie ein kanalübergreifender Versand-Workflow erstellt wird. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Cross-channel_delivery_workflow.html)

Dem Abschnitt „E-Mails archivieren“ wurden einige Empfehlungen hinzugefügt. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_deliverability.html#Activating_emails_BCC_archiving)

Es wurde eine neue Empfehlung bezüglich der minimalen Bildschirmauflösung für die optimale Verwendung von Adobe Campaign hinzugefügt. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/PTF_Starting_with_Adobe_Campaign_Adobe_Campaign_workspace.html#Screen_resolution)

Das Integrationshandbuch für Experience Manager wurde mit einigen Erläuterungen zur Konfiguration dieser Integration aktualisiert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/ITG_Adobe_Experience_Manager_About_Adobe_Experience_Manager.html)

Es wurden Informationen zum Unterschied zwischen Listen vom Typ Gruppe und vom Typ Liste hinzugefügt. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/PTF_Profile_management_Creating_and_managing_lists.html#About_lists_in_Adobe_Campaign)

Der Code wurde aktualisiert, um eine Berichtextraktion als Anhang über E-Mail zu senden. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Sending_a_report_to_a_list.html#Step_3-_Creating_the_workflow)

Es wurde ein Beispiel für die Erstellung einer Abfrage zum Filtern von Empfängern hinzugefügt, die in den letzten sieben Tagen keine E-Mail geöffnet haben. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Designing_queries.html#Recipients_who_did_not_open_any_delivery)

Das Integrationshandbuch zur Zielgruppenfreigabe mit Adobe Experience Cloud wurde aktualisiert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/ITG_Audience_sharing_Sharing_audiences_with_Adobe_Experience_Cloud.html)

Die Hilfeseite mit häufig gestellten Fragen enthält jetzt Informationen zu den in Campaign verfügbaren Sprachen, zur Übersetzung von Webformularen und zu mehrsprachigen E-Mails. [Mehr dazu](../../platform/using/common-questions.md)

Die Unterschiede zwischen US-amerikanischen und britischen Instanzen sind jetzt in einem eigenen Abschnitt aufgeführt. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/PTF_Starting_with_Adobe_Campaign_Adobe_Campaign_workspace.html#Formats_and_units)

Die Hilfeseite [Häufige Fragen](../../platform/using/common-questions.md) enthält jetzt Links zur Seite mit den Fehlermeldungen.

Es wurden Informationen zum „offenen“ Tracking-Modus hinzugefügt. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/DLV_Tracking_messages_Personalizing_URL_tracking.html)

Es wurden Informationen zur Mindestauflösung für Webanwendungen und Webformulare hinzugefügt. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/WEB_Web_forms_About_web_forms.html)

Das Integrationshandbuch für Campaign- und Adobe Experience Cloud-Lösungen wurde aktualisiert und neu organisiert. [Mehr dazu](../../integrations/using/about-campaign-integrations.md)

Es wurde ein Abschnitt zur Verwendung von Textvariablen in Webformularen hinzugefügt. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/WEB_Web_forms_Static_elements_in_a_web_form.html#Using_text_variables)

Die URL-Tracking-Modi in Nachrichten sind jetzt detailliert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/DLV_Tracking_messages_How_to_configure_tracked_links.html)

Der Abschnitt zur Instanzerstellung wurde neu organisiert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/INS_Initial_configuration_Creating_an_instance_and_logging_on.html)

Das Senden von E-Mails auf japanischen Mobiltelefonen ist jetzt in einem neuen Abschnitt dokumentiert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_emails_Defining_the_email_content.html#Sending_emails_on_Japanese_mobiles)

Der Abschnitt „Personalisierung optimieren“ wurde um weitere Informationen ergänzt. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/DLV_Personalizing_deliveries_Personalization_fields.html#Optimizing_personalization)

## 18.6 – 09.07.2018{#release-18-6}

**Neue Funktionen in der Version**

Die Kompatibilitätsmatrix wurde aktualisiert. [Mehr dazu](https://helpx.adobe.com/de/campaign/kb/compatibility-matrix.html)

Die JSAPI-Dokumentation wurde aktualisiert. [Mehr dazu](https://support.neolane.net/webApp/extranetLogin)

Die Seite mit veralteten und entfernten Funktionen wurde aktualisiert. [Mehr dazu](https://helpx.adobe.com/de/campaign/kb/deprecated-and-removed-features.html)

**Weitere Dokumentationsaktualisierungen zu dieser Version**

Die Benutzerhandbücher von Campaign Classic wurden umbenannt, um die Navigation zu vereinfachen und die Benutzerfreundlichkeit und den Zugriff auf Informationen und Selbsthilfe zu verbessern. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/de/browseAC.html)

Die Liste verfügbarer Funktionen wurde im Ausdruckseditor aktualisiert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/PTF_Creating_queries_Defining_filter_conditions.html#List_of_functions)

Die erste Schritte zum Thema Sicherheit wurden aktualisiert und enthalten Informationen zum Schutz von Seiten, die PI enthalten. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/getting_started/DE/security.html)

Die Liste der Fehlermeldungen wurde aktualisiert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

In der Dokumentation zur IMS-Integration wurde ein Abschnitt zur Fehlerbehebung hinzugefügt. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/ITG_Connecting_via_an_Adobe_ID_IMS_troubleshooting.html)

Die erste Schritte zum Thema Build-Aktualisierungen wurden aktualisiert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/getting_started/DE/buildUpgrade.html)

Der Abschnitt zur Konfiguration der IP-Affinität wurde aktualisiert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Mid-sourcing_server.html#Multiplexing_the_mid-sourcing_server)

Es wurde ein Abschnitt zur Fehlerbehebung bei Leistungs- und Durchsatzproblemen hinzugefügt. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/PRO_Troubleshooting_Performance_and_throughput_issues.html)

Die Liste der nativen Gestaltungsbausteine wurde mit Beispielen aktualisiert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/DLV_Personalizing_deliveries_Personalization_blocks.html#Out-of-the-box_personalization_blocks)

Die Liste der Gründe für Versandfehler wurde aktualisiert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/DLV_Monitoring_deliveries_Understanding_delivery_failures.html#Delivery_failure_types_and_reasons)

Ein neuer Abschnitt zur Verwaltung der Package-Definitionen wurde hinzugefügt. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/PTF_Administration_basics_Working_with_data_packages.html#Managing_package_definitions)

Der Abschnitt zur Campaign-Integration mit Adobe Analytics Data Connector wurde verbessert und neu organisiert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/PTF_Connectors_Adobe_Analytics_Data_Connector.html)

Es wurde ein neuer Abschnitt „Tutorials“ mit Links zu schrittweisen Anleitungen und Videos hinzugefügt. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/PTF_Starting_with_Adobe_Campaign_Tutorials.html)

Es wurde eine neue Technote zum SMS-Connector-Protokoll und zu den Einstellungen erstellt. [Mehr dazu](https://helpx.adobe.com/de/campaign/kb/sms-connector-protocol-and-settings.html)

Die ersten Schritte zum Thema Best Practices für den Versand wurden aktualisiert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/getting_started/DE/deliveryBestPractices.html)

Die Microsoft Dynamics 365 Kontokonfiguration mit Web-API-Implementierung wurde aktualisiert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/PTF_Connectors_CRM_Connectors.html#Example_for_Microsoft_Dynamics)

Das Verfahren zur Installation von Adobe Campaign Classic auf einer Windows-Plattform wurde aktualisiert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/INS_Installing_Campaign_in_Windows__Installing_the_server.html)

Der Zeitrahmen für die Freigabe von Zielgruppen zwischen Adobe Experience Cloud und Campaign Classic wurde detailliert beschrieben. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/ITG_Audience_sharing_Importing_and_exporting_audiences.html)

Die Liste der Knowledgebase-Artikel für Campaign Classic wurde aktualisiert. [Mehr dazu](https://helpx.adobe.com/de/campaign/kb/article-list.html)

Eine neue Technote zu Leistungsverbesserungen und Best Practices ist live. [Mehr dazu](https://helpx.adobe.com/de/campaign/kb/best-practices-for-performance-improvement.html)

Die Probendefinition für A/B-Tests wurde aktualisiert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_A-B_testing.html)

Die Seite mit den häufig gestellten Fragen für Campaign Classic wurde aktualisiert. [Mehr dazu](../../platform/using/common-questions.md)

## 18.4 – 24.04.2018{#release-18-4}

**Neue Funktionen in der Version**

EU-Datenschutz-Grundverordnung (DSGVO) – [mehr dazu](https://helpx.adobe.com/de/campaign/kb/acc-privacy.html)

Aktive Profile – [mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/PTF_Profile_management_About_profiles.html#Active_profiles)

Verbesserung des Android-Connectors für Push-Benachrichtigungen – [mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_push_notifications_Setting_up_mobile_app_channel.html#Android_connectors)

**Weitere Dokumentationsaktualisierungen zu dieser Version**

Die Versionshinweise wurden für ein besseres Benutzererlebnis verbessert und enthalten jetzt alle Patches für Kundenanfragen. [Mehr dazu](https://docs.adobe.com/content/help/de-DE/campaign-classic/using/release-notes/latest-release.html)

Eine neue Seite mit den häufigsten Fragen zu Campaign Classic wurde hinzugefügt. [Mehr dazu](../../platform/using/common-questions.md)

Die Liste der Fehlermeldungen wurde aktualisiert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

Die Technote zu den Marketing Cloud-Triggers wurde aktualisiert. [Mehr dazu](https://helpx.adobe.com/de/campaign/kb/triggers-and-campaign.html)

Es wurde eine Technote zur Installation und Bereitstellung des Datenschutz-Packages (DSGVO) in älteren Campaign Classic-Versionen hinzugefügt. [Mehr dazu](https://helpx.adobe.com/de/campaign/kb/how-to-install-gdpr-package-on-legacy-versions.html)

Es wurde eine Technote zum neuen Mechanismus zur automatischen Sequenzgenerierung hinzugefügt. [Mehr dazu](https://helpx.adobe.com/de/campaign/kb/sequence_auto_generation.html)

Die JSAPI-Dokumentation wurde aktualisiert. [Mehr dazu](https://support.neolane.net/webApp/extranetLogin)

Die Kompatibilitätsmatrix wurde aktualisiert. [Mehr dazu](https://helpx.adobe.com/de/campaign/kb/compatibility-matrix.html)

Eine neue Seite mit veralteten Funktionen und Versionen ist jetzt verfügbar. [Mehr dazu](https://helpx.adobe.com/de/campaign/kb/deprecated-and-removed-features.html)

Es wurden einige bekannte Einschränkungen und Best Practices für RDBMS hinzugefügt. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/INS_Prerequisites_and_recommendations__Database.html)

Informieren Sie sich über Best Practices für die SFTP-Nutzung. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/PTF_Importing_and_exporting_data_SFTP_server_usage.html)

Die Liste der technischen Workflows wurde aktualisiert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/WKF_Technical_workflows_About_technical_workflows.html)

Die Liste der Knowledgebase-Artikel (früher bekannt als Technotes) ist jetzt hier verfügbar. [Mehr dazu](https://helpx.adobe.com/de/campaign/kb/article-list.html)

Die [Anleitungsvideos](https://docs.campaign.adobe.com/doc/AC/en/Videos/Videos.html) wurden aktualisiert.

Die LINE-Dokumentation wurde nach der Einstellung des LINE-Packages aktualisiert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_messages_on_mobiles_LINE_channel.html)

Die Dokumentation zur Berechnung der Berichtsindikatoren wurde aktualisiert. [Mehr dazu](../../reporting/using/indicator-calculation.md)

Es wurden Informationen zur Ausrichtung von Zeitzonendateien mit Oracle hinzugefügt. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/MIG_Configuration_General_configurations.html#Oracle)

Es wurde ein neuer Abschnitt „Sendungen beobachten“ mit aktualisierten Informationen zu Versandfehlern und zur Quarantäneverwaltung hinzugefügt. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/DLV_Monitoring_deliveries_Monitoring_a_delivery.html)

Der Abschnitt „Gestaltungsbausteine“ wurde um neue Informationen zu nativen Gestaltungsbausteinen erweitert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/DLV_Personalizing_deliveries_Personalization_blocks.html)

Der Abschnitt „E-Mails archivieren“ wurde mit neuen Informationen zur ```config-<instance name>.xml```-Dateikonfiguration umorganisiert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html#Activating_email_archiving__on_premise_)

Die Informationen zum technischen Workflow „Message Center (Kontrolle)“ wurde aktualisiert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/WKF_Technical_workflows_Message_Center__Control_.html)

Es wurden Informationen zu Durchsatzbeschränkungen beim Einrichten eines SMTP-Relais hinzugefügt. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Configuring_Campaign_server.html#Personalizing_delivery_parameters)

## 17.12 – 14.12.2017{#release-doc-14-12-2017}

Die [Dokumentation von Adobe Campaign Classic](https://helpx.adobe.com/de/support/campaign/classic.html) wurde neu organisiert, um die Benutzerfreundlichkeit zu verbessern.

Es wurde ein neuer Abschnitt „Tutorials“ hinzugefügt, um den Zugriff auf Hilfsmaterialien, Anleitungen, Beispiele und Videos zu den Campaign-Funktionen zu erleichtern. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/PTF_Starting_with_Adobe_Campaign_Tutorials.html)

Es wurde ein neuer Abschnitt hinzugefügt, in dem Sie Ihren Versandstatus, aber auch mögliche Fehler überwachen und lernen können, wie Sie diese beheben können. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/DLV_Monitoring_deliveries_Monitoring_a_delivery.html)

Die Liste der Fehlermeldungen wurde aktualisiert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

Die Technote zu den Marketing Cloud-Triggers wurde aktualisiert. [Mehr dazu](https://helpx.adobe.com/de/campaign/kb/triggers-and-campaign.html)

Der Campaign Classic-Migrationsleitfaden wurde der Kollektion hinzugefügt. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/MIG_Migration_overview_About_migration.html)

Die Campaign-Kompatibilitätsmatrix wurde aktualisiert. [Mehr dazu](https://helpx.adobe.com/de/campaign/kb/compatibility-matrix.html)

In den Konfigurations- und Installationsanweisungen wird nun gegebenenfalls angegeben, für welches Hosting-Modell sie gelten. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Configuring_Campaign_server.html)

Neuer Knowledgebase-Artikel zur Hervorhebung von Konfigurations- und Funktionsunterschieden zwischen On-Premise-, Hybrid- und Managed Services-Bereitstellungen. [Mehr dazu](https://helpx.adobe.com/de/campaign/kb/acc-on-prem-vs-hosted.html)

Es wurden Anweisungen zur Installation eines Standard-Packages hinzugefügt. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/INS_Initial_configuration_Installing_packages.html)

Es wurden Details zum Konfigurieren der Integration mit Audience Manager oder People Core Service hinzugefügt. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/ITG_Audience_sharing_Configuring_shared_audiences_integration_in_Adobe_Campaign.html)

Die Installationsdokumentation wurde dahingehend aktualisiert, dass pgcrypto jetzt für die Campaign-Installation erforderlich ist, wenn PostreSQL verwendet wird. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/INS_Installing_Campaign_in_Linux__Prerequisites.html#Database_access_layers)

## 17.9 – 25.09.2017{#release-17-9}

**Neue Funktionen in der Version**

Verbesserungen bei ACS Connector

SAP HANA-Connector – [mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/PTF_Connectors_Accessing_an_external_database.html#SAP_HANA)

Hadoop Connector über HiveSQL – [mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/PTF_Connectors_Accessing_an_external_database.html#Hadoop)

LINE-Kanal: Verbesserungen bei Nachrichten – [mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_messages_on_mobiles_LINE_channel.html)

**Weitere Dokumentationsaktualisierungen zu dieser Version**

Es wurden neue Abfragebeispiele hinzugefügt. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Designing_queries.html#Filtering_duplicated_recipients)

Das Handbuch zum Thema Best Practices für den Versand wurde aktualisiert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/getting_started/DE/deliveryBestPractices.html)

Die Probendefinition für A/B-Tests wurde mit fehlenden Anweisungen aktualisiert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_A-B_testing.html)

Die Anleitungsvideos wurden aktualisiert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/Videos/Videos.html)

Der Abschnitt zur E-Mail-Archivierung wurde aktualisiert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html)

Die Verwendung der Planung im Workflow wurde erläutert. [Mehr dazu](../../workflow/using/scheduler.md)

Best Practice bei ausgesetzten Workflows hinzugefügt [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Executing_a_workflow.html)

Neues Verfahren zur Vorab-Bearbeitung von Dateien beim Import und zur Nachbearbeitung beim Exportieren von Daten in einem Workflow. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Importing_data.html)!

Die Dokumentation zum Quarantänemechanismus für SMS-Nachrichten wurde aktualisiert, um die Besonderheiten des Fehlermanagements für den Connector „Erweitertes allgemeines SMPP“ widerzuspiegeln. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/DLV_Monitoring_deliveries_Understanding_quarantine_management.html#SMS_quarantines)

Die Dokumentation zum Mobile-App-Kanal (Mobile App Channel) wurde um ein detailliertes Verfahren zum Senden von Rich-Benachrichtigungen unter Android erweitert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_push_notifications_Setting_up_mobile_app_channel.html#Rich_notifications)

Die Dokumentation zum Inbox Rendering wurde aktualisiert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/DLV_Deliverability_management_Inbox_rendering.html)

Die Dokumentation zur Einrichtung von Webtracking wurde um ein aktualisiertes Beispiel und Hinweise erweitert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/CFG_Setting_up_web_tracking_Additional_parameters.html#Redirection_server_configuration)

Die Dokumentation zum SMS-Kanal wurde im Abschnitt „Automatische Antwort“ mit einigen Klarstellungen hinsichtlich des Connectors „Erweitertes allgemeines SMPP“ aktualisiert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_messages_on_mobiles_SMS_channel.html#Creating_an_SMPP_external_account)

Die Social Marketing-Dokumentation wurde aktualisiert. [Mehr dazu](../../social/using/about-social-marketing.md)

Es wurde eine neue Technote zum Thema IP-Warming hinzugefügt. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/Technotes/AdobeCampaign_Deliverability_IP_Warming_overview.pdf)

Es wurden neue erste Schritte zum Thema Build-Aktualisierung hinzugefügt. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/getting_started/DE/buildUpgrade.html)

## Mai 2017{#release-doc-30-05-2017}

Ein neues Erste-Schritte-Handbuch ist verfügbar: Es enthält Best Practices für den Versand mit Adobe Campaign, von der Erstellung von Nachrichten über die Zielgruppenbestimmung bis zum Senden und Verfolgen von Nachrichten. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/getting_started/DE/deliveryBestPractices.html)

Das Sicherheitshandbuch wurde aktualisiert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/getting_started/DE/security.html)

Die [Dokumentation zur E-Mail-Archivierung](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html) wurde um den Abschnitt [E-Mail-BCC](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html#Configuring_the_BCC_email_address__on_premise_) und eine [detaillierte Anleitung zur Aktivierung der Funktion](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_emails_Sending_messages.html#Archiving_emails) erweitert.

Einige Videos wurden hinzugefügt und aktualisiert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/Videos/Videos.html)

Sie erfahren, wie Sie einen Versand an Empfänger durchführen, die aus einer externen Datei geladen wurden, ohne die Datenbank zu aktualisieren. [Mehr dazu](../../delivery/using/steps-defining-the-target-population.md#selecting-external-recipients)

Außerdem wurde das Beispiel für ein Anmeldeverfahren mit doppelter Bestätigung aktualisiert. [Mehr dazu](../../web/using/use-cases--web-forms.md)

## März 2017{#release-doc-31-03-2017}

Zustellbarkeit: Das [Erste-Schritte-Handbuch](https://docs.adobe.com/content/help/de-DE/campaign-classic/using/sending-messages/deliverability-management/about-deliverability.html) wurde aktualisiert. Der Zustellbarkeitsabschnitt enthält jetzt eine detailliertere [Übersicht](https://docs.campaign.adobe.com/doc/AC/en/DLV_Deliverability_management_About_deliverability.html) sowie eine Beschreibung des [Implementierungsvorgangs und der wichtigsten Schritte](../../delivery/using/deliverability-key-points.md).

Der Abschnitt &quot;In Schüben versenden&quot; wurde verschoben und mit detaillierten Beispielen, Empfehlungen und Anwendungsbeispielen ergänzt. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_emails_Sending_messages.html#Sending_using_multiple_waves)

Im Abschnitt &quot;Quarantäne-Verwaltung&quot; wurde eine Tabelle hinzugefügt, in der typische Fehler im Zusammenhang mit SMS-Nachrichten beschrieben werden. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/DLV_Monitoring_deliveries_Understanding_quarantine_management.html#SMS_quarantines)

Workflows: Ein neues Beispiel für einen kanalübergreifenden Workflow wurde hinzugefügt. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/WKF_Repository_of_activities_Action_activities.html#Cross-channel_deliveries)

Marketing-Cloud-Triggers: Eine Technote zur Konfiguration und Verwendung mit Adobe Campaign wurde hinzugefügt. [Mehr dazu](https://helpx.adobe.com/de/campaign/kb/triggers-and-campaign.html)

Das Workflow-Hasndbuch wurde umstrukturiert und erweitert. Dies ermöglicht das einfache Auffinden von Informationen zum [Erstellen](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Building_a_workflow.html) und [Ausführen](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Executing_a_workflow.html) eines Workflows, zur [Zielgruppenauswahl](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Targeting_data.html) und [Verwaltung](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Targeting_data.html#Data_Management) Ihrer Daten, zum [Import](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Importing_data.html)[](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_How_to_use_workflow_data.html#Updating_the_database)[ von Daten und zur Nutzung von Workflow-Daten für die Aktualisierung der Datenbank oder für den Versand](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_How_to_use_workflow_data.html#Delivering_via_a_workflow).

Ein Beispiel für einen [Import-Workflow](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_How_to_use_workflow_data.html#Delivering_via_a_workflow) wurde hinzugefügt, der anhand von [Best Practices beim Datenimport](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Importing_data.html#Import_best_practices) erstellt wurde.
Das Installationshandbuch wurde entsprechend der neuen Version aktualisiert. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/INS_Architecture_and_hosting_models_General_architecture.html)

Die Kompatibilitätsmatrix wurde aktualisiert. [Mehr dazu](https://helpx.adobe.com/de/campaign/kb/compatibility-matrix.html)

Empfänger erhalten einen Mehrwert, wenn Sie Ihren E-Mail-Sendungen Coupons hinzufügen. [Mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/DLV_Personalizing_deliveries_Personalized_coupons.html)

## Adobe Campaign v7 - 16.03.2017{#release-17-2}

**Neue Funktionen in der Version**

ACS Connector

Web-API für Microsoft Dynamics – [mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/PTF_Connectors_CRM_Connectors.html#Example_for_Microsoft_Dynamics)

BCC-Methode zur E-Mail-Archivierung – [mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html#Updated_email_archiving_system__BCC_)

Amazon Simple Storage Service (S3) Connector – [mehr dazu](https://docs.campaign.adobe.com/doc/AC/en/WKF_Repository_of_activities_Event_activities.html#File_transfer)

