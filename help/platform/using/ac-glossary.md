---
product: campaign
title: Glossar für Adobe Campaign
description: Glossar für Adobe Campaign
role: User, Data Architect
level: Beginner
hide: true
hidefromtoc: true
source-git-commit: dea815b07f0b91ed550060fa00cf0501ae6594f7
workflow-type: tm+mt
source-wordcount: '6087'
ht-degree: 12%

---

# Adobe Campaign-Glossar{#ac-glossary}

Nachstehend finden Sie die wichtigsten Begriffe und Konzepte in Adobe Campaign mit Links zur zugehörigen Dokumentation. Klicken Sie auf einen Begriff, um dessen Definition anzuzeigen.

## A - D{#sec-1}

+++**A/B-Tests**

A/B-Tests sind eine Funktion, mit der der Benutzer zwei bis drei E-Mail-Varianten definieren kann: Jede Variante wird an Populationsproben gesendet, um zu bestimmen, welches das beste Ergebnis erzielt. Sobald die Gewinnervariante feststeht, wird sie an die verbleibende Zielpopulation gesendet.

Weitere Informationen [A/B-Tests](../../delivery/using/get-started-a-b-testing.md).
+++

+++**Zugriffsverwaltung**

Die Zugriffsverwaltung ermöglicht es Administratoren, Benutzern von Adobe Campaign Zugriff und Berechtigungen zuzuweisen. Zu den Berechtigungen gehört die Möglichkeit, Adobe Campaign-Funktionen anzuzeigen und/oder zu verwenden, z. B. Workflows auszuführen, Schemata zu definieren und Zielgruppen zu verwalten.

Weitere Informationen [Zugriffsverwaltung](access-management.md).
+++

+++**ACS Connector**

ACS Connector (Prime Offering) überbrücken Adobe Campaign v7 und Adobe Campaign Standard. Es handelt sich um eine integrierte Funktion in Campaign v7, mit der Daten automatisch an Campaign Standard repliziert werden, sodass die besten beider Anwendungen kombiniert werden können. Campaign v7 verfügt über erweiterte Tools zur Verwaltung der primären Marketing-Datenbank. Die Datenreplikation von Campaign v7 ermöglicht es Campaign Standards, die Rich-Daten in einer benutzerfreundlichen Umgebung zu nutzen.

Weitere Informationen [ACS Connector](../../integrations/using/acs-connector-principles-and-data-cycle.md).
+++

+++**Aktivität**

Eine Aktivität ist ein Palettenelement, das einem Workflow hinzugefügt wird, um eine Ausführungsfunktion zu definieren. Die Aktivität ist ein Container, der eine Aufgabe ausführt. In einem Workflow kann eine bestimmte Aktivität mehrere Aufgaben auslösen, insbesondere bei Schleifen oder wiederkehrenden (periodischen) Aktionen.

Weitere Informationen [Workflow-Aktivitäten](../../workflow/using/about-activities.md).
+++

+++**Aktives Profil**

Profile gelten als aktiv, wenn sie in den letzten 12 Monaten über einen beliebigen Kanal angesprochen wurden oder über einen beliebigen Kanal mit ihnen kommuniziert wurde. Gemäß Ihrem Vertrag erhalten alle Ihre Campaign-Instanzen eine bestimmte Anzahl aktiver Profile, die zu Abrechnungszwecken gezählt werden.

Weitere Informationen [Aktive Profile](../../platform/using/about-profiles.md#active-profiles).
+++

+++**Validierungs-Workflow-Aktivität**

*Kontext: Distributed Marketing von Campaign*

Die Aktivität Lokale Validierung ist eine Workflow-Aktivität, mit der vor dem Versand der Nachrichten ein Validierungsprozess für den Versand eingerichtet wird.

Weitere Informationen zum [Lokale Validierung](../../workflow/using/local-approval.md).
+++

+++**Audience**

Eine Zielgruppe ist der resultierende Satz von Profilen, die den Kriterien einer Filterdefinition entsprechen und auf Regeln und Attributen basieren.

Weitere Informationen [Zielgruppen](../../campaign/using/marketing-campaign-target.md).
+++

+++**Audit-Protokoll**

Das Audit-Protokoll erfasst in Echtzeit eine umfassende Liste von Aktionen und Ereignissen, die in Ihrer Adobe Campaign-Instanz auftreten. Es bietet eine Self-Service-Möglichkeit, auf einen Datenverlauf zuzugreifen, um Fragen zu beantworten, z. B.: was mit Ihren Workflows passiert ist und wer sie zuletzt aktualisiert hat oder was Ihre Benutzer in der Instanz getan haben.

Weitere Informationen [Audit-Protokoll](../../production/using/audit-trail.md).
+++

<!--
----DUPLICATE WITH THE "CAMPAIGN" ENTRY?---
+++**Automated campaigns**

Campaigns that run on a schedule, such as for targeting recipients who have a birthday or an anniversary. Can also be used to execute look-ahead and look-back logic, such as who purchased yesterday or who has a payment due tomorrow.

Learn more about [Campaigns](../../campaign/using/designing-marketing-campaigns.md).
+++
-->

+++**Batch-Modus**

*Kontext: Kampagneninteraktion*

Im Kontext von Campaign Interaction kann die Angebotsmodul im Batch-Modus das beste Angebot (oder die besten Angebote) für eine Gruppe von Kontakten auswählen. Eignungs-/Prioritätsregeln werden auf alle Kontakte der Gruppe angewendet.

Weitere Informationen [Interaction](../../interaction/using/interaction-and-offer-management.md).
+++

+++**Kampagne**

Campaign ist eine Schnittstelle zur Koordinierung, Definition und Ausführung von Marketingkampagnen. Kampagnen können einen oder mehrere Workflows, Sendungen, Dokumente und andere zugehörige Datenpunkte in einer einzigen, benutzerfreundlichen Benutzeroberfläche enthalten.

Weitere Informationen [Kampagnen](../../campaign/using/designing-marketing-campaigns.md).
+++

<!--
-----NOT USEFUL HERE?-----
+++**Changeover process**

*Context: Campaign Interaction*

In the context of Campaign Interaction, the changeover process is an activated process in an identified environment, responsible for directing the call to an anonymous environment if the contact has not been explicitly and/or implicitly identified.

Learn more about [Interaction](../../interaction/using/interaction-and-offer-management.md).
+++
-->

+++**Kanal**

Ein Kanal ist ein Medium, über das eine Kommunikation gesendet wird. Integrierte Kanäle in Adobe Campaign sind E-Mail, SMS, Briefpost, Push-Benachrichtigungen, LINE und Twitter. Benutzerdefinierte Kanäle können für nicht standardmäßige Kanalanforderungen implementiert werden.

Weitere Informationen [Kanäle](../../delivery/using/communication-channels.md).
+++

+++**Client-Konsole**

Die Campaign-Clientkonsole ist ein Rich-Client, mit dem Sie eine Verbindung zu Ihren Campaign-Anwendungsservern herstellen können. Die ausführbare Clientkonsole (.exe)-Anwendung wird auf einem Computer mit einem Microsoft Windows-Betriebssystem installiert. Die Campaign Client-Konsole zentralisiert alle Funktionen und Einstellungen.

Weitere Informationen [Client-Konsole](../../platform/using/adobe-campaign-workspace.md).
+++

+++**Inhaltsvalidierung**

Bei der Inhaltsvalidierung wird der Inhalt eines Versands von einem separaten Benutzer oder einer Benutzergruppe validiert, bevor er gesendet werden kann.

Weitere Informationen [Inhaltsvalidierung](../../campaign/using/marketing-campaign-approval.md).
+++

+++**Kontrollgruppen**

Verwenden Sie Kontrollgruppen, um die Wirkung Ihrer Kampagnen zu messen, indem Sie einen Teil ihrer Audience ausschließen. Benutzer können das Verhalten der Zielpopulation, die die Nachricht erhalten hat, mit dem Verhalten der Kontakte vergleichen, die nicht kontaktiert wurden. Auf der Basis der Versandlogs können Benutzer auch eine Kontrollgruppe in zukünftigen Kampagnen auswählen.

Weitere Informationen [Inhaltsvalidierung](../../campaign/using/marketing-campaign-target.md#defining-a-control-group).
+++

+++**Control Panel**

Mit dem Control Panel können Sie als Produktadministrator von Adobe Campaign die Effizienz Ihrer Arbeit steigern, indem Sie Einstellungen verwalten und die Nutzung für jede Ihrer Instanzen verfolgen können. Dank der intuitiven Benutzeroberfläche können die Nutzung wichtiger Ressourcen überwacht und administrative Aufgaben einfach durchgeführt werden. So können beispielsweise IP-Adressen auf die Zulassungsliste gesetzt, der Speicher von SFTP-Servern überwacht und die Schlüssel verwaltet werden.

Weitere Informationen [Inhaltsvalidierung](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/key-features.html?lang=de).
+++

+++**Cubes**

*Kontext: Marketing Analytics*

Cube ist ein intuitives Adobe Campaign-Tool zur Datenexploration, mit dem Benutzer dynamische Berichte erstellen und freigeben können.

Weitere Informationen [Cubes](../../reporting/using/about-cubes.md).
+++

+++**Benutzerdefinierte Ressourcen**

Adobe Campaign verfügt über ein vordefiniertes Datenmodell, bei dem Datentypen durch die Installation verschiedener Packages definiert werden. Benutzer können das bereitgestellte Datenmodell anreichern, indem sie die Ressourcen erweitern, um benutzerdefinierte Felder oder benutzerdefinierte Tabellen wie Transaktions- oder Produkttabellen hinzuzufügen.

Weitere Informationen [Benutzerdefinierte Ressourcen](../../configuration/using/about-schema-edition.md).
+++

+++**Datenmodell**

Das Campaign-Datenmodell ist ein Satz von Schemas, die die Datentypen und ihre Beziehungen definieren (Links). Das Datenmodell ist eine abstrakte Definition, die physisch mit einer Datenbank implementiert wird, die die tatsächlichen Daten enthält.

Weitere Informationen [Benutzerdefinierte Ressourcen](../../configuration/using/about-data-model.md).
+++

+++**Datenbankbereinigungs-Workflow**

Der Datenbankbereinigungs-Workflow löscht veraltete Daten, um das exponentielle Anwachsen der Datenbank zu vermeiden. Der Workflow wird automatisch ohne Benutzereingriff ausgelöst.

Weitere Informationen [Datenbankbereinigungs-Workflow](../../production/using/database-cleanup-workflow.md).
+++

<!--
----UNCLEAR----
+++**Dedicated server**

*Context: Transactional Messaging*

Dedicated execution server(s) to leverage Transactional Messaging. A server can typically process up to 50,000 Engine Calls per hour. The “Per-Dedicated Server” designation does not necessarily have a 1:1 correlation with a physical server as Adobe may utilize virtualization technologies to achieve the equivalent effect.

Learn more about [Transactional Messaging](../../message-center/using/about-transactional-messaging.md).
+++
-->

+++**Zustellbarkeit**

*Kontext: Email Deliverability*

Mit der Zustellbarkeit können Sie messen, wie erfolgreich Ihre Kampagnen bei der Zustellung an die Empfängerpostfächer sind, ohne dass der Zustellvorgang abgebrochen oder als Spam gekennzeichnet wird. Genauer gesagt bezieht sich die Zustellbarkeit von E-Mails auf die Merkmale, die bestimmen, ob eine Nachricht innerhalb kurzer Zeit über eine persönliche E-Mail-Adresse ihr Ziel erreichen kann und die die erwartete Qualität in Bezug auf Inhalt und Format aufweisen.

Weitere Informationen [Zustellbarkeit](../../delivery/using/about-deliverability.md).
+++

+++**Versand**

Ein Versand ist ein spezielles Marketing-Kommunikationselement, das an eine Audience in einem bestimmten Kanal gesendet wird (E-Mail, SMS, Push-Benachrichtigung usw.). Auch in der Marketing-Terminologie als &quot;Touch&quot;bezeichnet.

Weitere Informationen [Sendungen](../../delivery/using/communication-channels.md).
+++

+++**Versandanalyse**

Die Versandanalyse ist die Vorbereitung des Versands. Dieser Prozess kombiniert den Inhalt mit den Empfängerprofildaten, um die personalisierte E-Mail zu erstellen, die der Empfänger erhält. Die Logik der Versandanalyse kann Empfänger aus der Zielgruppe ausschließen oder den Versand ganz stoppen, basierend auf der definierten Logik. Dieser Prozess umfasst auch die Bewertung der dynamischen Inhaltslogik und das Einfügen von Angeboten, die spezifisch für das jeweilige Empfängerprofil sind.

Weitere Informationen [Versandanalyse](../../delivery/using/steps-validating-the-delivery.md#analyzing-the-delivery).
+++

+++**Versandlogs**

Versandlogs enthalten Informationen, die beim Versand einer Nachricht erzeugt werden. In diesen Logs wird die Detailansicht des Versands angezeigt, welche Nachricht vorbereitet, ignoriert, gesendet oder fehlgeschlagen ist. Sie können direkt über das Versand-Dashboard aufgerufen werden.

Weitere Informationen [Versandlogs](../../delivery/using/delivery-dashboard.md#delivery-logs-and-history).
+++

<!--
----STRANGE IN DOCS?----
+++**Delivery fundamentals**

*Context: Email Deliverability*

Adobe Campaign Deliverability Fundamentals Consulting Service provides email deliverability consultation and reputation management to support customers using Adobe Campaign deliveries.

Learn more about [Deliverability](../../delivery/using/about-deliverability.md).
+++
-->

+++**Versandentwurf**

*Kontext: Briefpost*

Ein Versandentwurf ist ein strukturierter Satz von Elementen (Dokumente, Geschäfte, Gutscheine usw.), der vom Unternehmen für eine bestimmte Kampagne erstellt wurde. Er wird im Zusammenhang mit Briefpost-Sendungen verwendet.

Weitere Informationen [Briefpost](../../delivery/using/about-direct-mail-channel.md).
+++

+++**Bereitstellungsassistent**

Der Softwareverteilungs-Assistent definiert die Parameter der Campaign-Instanz, wie z. B. den Standard-Namespace, den Zeitplan für die Datenbankbereinigung, die Fristen für die Datenaufbewahrung und andere technische Einstellungen.

Weitere Informationen [Bereitstellungsassistent](../../installation/using/deploying-an-instance.md#deployment-wizard).
+++

+++**Deskriptive Analyse**

Deskriptive Analyse ist ein kontextbezogenes Reporting-Tool, mit dem Daten in der Arbeitstabelle eines Workflows, in einem Ordner ausgewählte Daten oder tief greifende Einblicke in die Ziele und Ausschlüsse ausgewählter Sendungen möglich sind.

Weitere Informationen [Deskriptive Analyse](../../reporting/using/about-descriptive-analysis.md)
+++

+++**Distributed Marketing**

*Kontext: Distributed Marketing*

Das Add-on für dezentrales Marketing bietet Campaign-Benutzern einen gemeinsamen Arbeitsbereich zur Implementierung von Kampagnen zwischen Zentralstellen (Hauptsitz, Marketingabteilungen usw.) und lokalen Stellen (Verkaufsstellen, regionale Agenturen usw.). Diese Zusammenarbeit basiert auf einem gemeinsamen Arbeitsbereich, der als **Liste der Campaign-Packages**: zentral erstellte Kampagnenvorlagen und -instanzen werden den Lokalstellen angeboten.

Weitere Informationen [Dezentrales Marketing](../../distributed/using/about-distributed-marketing.md)
+++

+++**Werteverteilung**

Die Werteverteilung ist ein Tool, das die Verteilung der Werte für ein Schemaattribut anzeigt, das derzeit in der Datenbank vorhanden ist. Auf diese Weise können Sie feststellen, welche Werte verfügbar sind, wie viele Werte es gibt und wie hoch die Prozentsätze sind. Außerdem können Sie bei der Erstellung einer Abfrage oder eines Ausdrucks Probleme mit der Groß- und Kleinschreibung von Werten vermeiden.

Weitere Informationen [Dezentrales Marketing](../../platform/using/defining-filter-conditions.md#selecting-data-to-extract)
+++

+++**Delegation von Domains**

Mit der Subdomain-Konfiguration können Sie einen Unterabschnitt Ihrer Domain (technisch eine &quot;DNS-Zone&quot;) für die Verwendung mit Adobe Campaign konfigurieren.
Die Domain-Delegation ermöglicht der Adobe die Kontrolle und Pflege aller DNS-Aspekte, die für die Bereitstellung, Darstellung und Verfolgung von E-Mail-Kampagnen erforderlich sind.

Weitere Informationen [Domain-Zuweisung](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/setting-up-new-subdomain.html?lang=de)
+++

## E - H {#sec-2}

<!--
----DEPREACTED----
+++**E4X**

The version of Javascript that is used in Adobe Campaign Classic. Sometimes called ECMAScript, it is an extension of Javascript that allows the mixing of Javascript and XML primitives in the same code. Note that E4X is classified as a deprecated language. 
+++
-->

+++**Eignungsregeln**

*Kontext: Kampagneninteraktion*

Eignungsregeln sind Einschränkungen, die auf eine Umgebung, eine Kategorie oder ein Angebot bezüglich Gültigkeitsdauer, Zielgruppe und Gewichtung angewendet werden. Benutzer können damit sicherstellen, dass ein Angebot mit dem Zielkontakt übereinstimmt. In der Angebotsumgebung umfassen die Eignungsregeln Unterbreitungsregeln, die auf die Angebote und die Zielgruppenempfänger angewendet werden. In der Kategorie ermöglichen es die Eignungsregeln Benutzern, die Gültigkeit der Kategorie zeitlich zu begrenzen, Anwendungsthemen zu definieren und die Empfänger zu bestimmen. Sie können auch eine Multiplikatorgewichtung für einen bestimmten Zeitraum definieren. Auf diese Weise können Benutzer die Regeln für Angebote in anderen Kategorien teilen und so ihre Verwaltung vereinfachen. In Angeboten können Benutzer mithilfe von Eignungsregeln die Gültigkeit von Angeboten zeitlich begrenzen und die Zielgruppe der Angebote bestimmen.

Weitere Informationen [Eignungsregeln](../../interaction/using/interaction-and-offer-management.md).
+++

+++**Geeignetes Angebot**

*Kontext: Kampagneninteraktion*

Ein geeignetes Angebot ist ein Angebot, das die zuvor definierten Bedingungen erfüllt und somit einer Zielgruppe auf kohärente Weise unterbreitet werden kann.

Weitere Informationen [Interaction](../../interaction/using/interaction-and-offer-management.md).
+++

+++**E-Mail-BCC**

Die E-Mail-BCC-Funktion sendet eine exakte Kopie einer entsprechenden zugestellten E-Mail im EML-Format, die in einer dedizierten BCC-E-Mail-Adresse gespeichert wird, an der die E-Mails vom Absender in einem externen System verarbeitet und archiviert werden können.

Weitere Informationen [E-Mail-BCC](../../delivery/using/email-parameters.md#email-bcc).
+++

<!--
-----STRANGE FOR DOCS?----
+++**Email volume commitment**

The anticipated emails sent per year as set forth in the Sales Order. This is the total annual email volume commitment, including emails sent but not delivered due to delivery errors such as: non-delivery of a message including but not limited to email address errors, hard bounces, soft bounces, email filters of mail clients, and email blacklists. 
+++
-->

<!--
-----USEFUL FOR DOCS?----
+++**Engine call**

An engine call is a server call that starts real-time processing on server side for the extraction of data, such as data relating to surveys, WebApps, JSSP, APIs, mobile app registrations, etc. Engine calls must be licensed in packs of 5,000 Engine Calls per day.
+++
-->

+++**Anreicherungsaktivität**

Die Anreicherungsaktivität ist eine erweiterte Workflow-Aktivität, mit der Benutzer die erzeugten, im Workflow verarbeiteten Tabellendaten anreichern können. Diese Aktivität wird im Allgemeinen im Anschluss an Zielgruppenbestimmungs- oder Dateiimportaktivitäten und vor Aktivitäten verwendet, die Zieldaten verwenden. Anreicherungen können die eingehenden Transitionsdaten transformieren und die Aktivität so konfigurieren, dass die ausgehende Transition mit erweiterten Daten abgeschlossen wird. Dadurch kann der Operator Daten aus mehreren Datensätzen kombinieren oder Links zu einer temporären Ressource erstellen.

Weitere Informationen [Anreicherungsaktivität](../../workflow/using/enrichment.md).
+++

+++**Auflistungen**

Eine Auflistung ist ein Datentyp, der in Schemata oder auf Platform-Ebene definiert wird und die gültigen Eingabewerte für ein Feld definiert. Auflistungen werden in der Benutzeroberfläche und in Query Builder als Auswahlliste angezeigt.

Weitere Informationen [Auflistungen](../../platform/using/managing-enumerations.md).
+++

+++**Explorer-Ansicht**

Die Explorer-Ansicht ist eine hierarchische Darstellung der Ordner, die Adobe Campaign-Artefakte und -Daten enthalten. Beachten Sie, dass das Ordnersystem in Adobe Campaign nicht wie eine typische Vorschau funktioniert, da jeder Ordner Daten eines bestimmten Typs enthält, z. B. Sendungen, Workflows oder Angebote.

Weitere Informationen [Explorer-Ansicht](../../platform/using/adobe-campaign-explorer.md).
+++

+++**Externe Konten**

Externe Konten sind Ein- und Ausstiegspunkte für das Produkt, um eine Verbindung zu anderen Umgebungen und Technologien herzustellen. Externe Konten definieren die Verbindungsparameter, die das Produkt verwendet, um Daten an andere Quellen zu senden oder von diesen zu empfangen. Typische Typen externer Konten sind Verbindungen für SFTP-Sites, Telekommunikationen zur Unterstützung des Versands von SMS, Postfächern für Verarbeitungsabsprünge oder Verbindungen zu externen Datenbanken.

Weitere Informationen [Externe Konten](../../installation/using/external-accounts.md).
+++

+++**Ermüdungsverwaltung**

*Kontext: Kampagnenoptimierung*

Mit der Ermüdungsverwaltung können Sie die Häufigkeit und Anzahl der Nachrichten steuern, um eine Überforderung von Empfängern zu vermeiden. Häufig wird dies mithilfe einer Typologieregel durchgeführt.

Weitere Informationen [Ermüdungsverwaltung](../../campaign-opt/using/pressure-rules.md).
+++

+++**Federated Data Access (FDA)**

Federated Data Access unterstützt die Erweiterung des Client-Datenmodells um eine Drittanbieter-Datenbank. Sie erkennt automatisch die Struktur der ausgewählten Tabellen und verwendet Daten aus den SQL-Quellen. Sie können auf externe Daten zugreifen, ohne die Struktur der Adobe Campaign-Daten zu ändern.

Weitere Informationen [Federated Data Access](../../installation/using/about-fda.md).
+++

+++**Validierung der Dateiextraktion**

*Kontext: Briefpost*

Bei der Validierung der Dateiextraktion muss ein separater Benutzer oder eine Benutzergruppe den Inhalt und die Konfiguration einer extrahierten Datei validieren, bevor sie an einen externen Anbieter gesendet wird, z. B. für einen Briefpost-Versand.

Weitere Informationen [Validierung der Dateiextraktion](../../delivery/using/validating.md).
+++

+++**Filterdimension**

Die Filterdimension ist das Schema, das die Daten oder Attribute enthält, die von einer Abfrage zum Filtern der gewünschten Zeilen verwendet werden. Das Filterdimension-Schema muss direkt mit der definierten Zielgruppendimension verknüpft sein, damit Adobe Campaign die Datenbankverknüpfung durchlaufen und die reagierenden Zeilen zurückgeben kann.

Weitere Informationen [Filterdimension](../../workflow/using/building-a-workflow.md#targeting-and-filtering-dimensions).
+++

+++**Ordner**

Ein Ordner ist ein Explorer-Anzeigeelement, das Datenbankdatensätze eines bestimmten Datentyps enthält. Die Ausnahme ist der allgemeine Ordnertyp, der als Organisationselement verwendet wird und keine Daten selbst, sondern nur andere Ordner enthält.

Weitere Informationen [Ordner](../../platform/using/adobe-campaign-explorer.md).
+++

+++**Ordneransicht**

Die Ordneransicht ist ein spezieller Explorer-Ordnertyp, der verwendet wird, um alle Datensätze eines ausgewählten Datentyps anzuzeigen, unabhängig davon, zu welchem Ordner er gehört. Ordneransichten werden als Verwaltungswerkzeug verwendet, um partitionierte Daten oder Daten zu verwalten, die in vielen Ordnern verteilt sind.

Weitere Informationen [Ordneransicht](../../platform/using/adobe-campaign-explorer.md).
+++

+++**Formulare**

Forms definiert die Darstellung der Benutzeroberfläche für einen bestimmten Schematyp. Forms ermöglicht die einfache Erstellung und Bearbeitung von Datenelementen wie Empfängern, Sendungen und Kampagnen im Produkt. Alle Elemente der Benutzeroberfläche in Adobe Campaign werden im Produkt selbst mithilfe von Forms erstellt. Beachten Sie, dass Formulare optional sind und nicht alle Schemata Formulare haben.

Weitere Informationen [Forms](../../configuration/using/identifying-a-form.md).
+++

<!--
-----USEFUL HERE?-----
+++**Generated SQL query**

The SQL code generated for the underlying database when an operator manipulates a schema. Schemas define the data types that are then implemented using database tables and columns. The SQL generated for schema manipulation (such as in a query) is based on the installed database type. Thus, the database can be swapped to a different type and the queries in Campaign remain unchanged. Adobe refers to this functionality as being database-agnostic.

Learn more about [Generated SQL queries](../../platform/using/steps-to-create-a-query.md#step-6---preview-data).
+++
-->

+++**Heatmap**

Campaign Heatmap ist eine Tabelle mit Informationen zur Workflow-Ausführung für einen Zeitraum von 24 Stunden. Sie zeigt die Verteilung der Workflows über den Zeitraum nach Stunde und in Intervallen von 5 Minuten an. Heatmap wird verwendet, um die Serverlast zu bewerten und die Workflow-Aktivitäten zu bestimmen, die die meisten Ressourcen verbrauchen.

Weitere Informationen [Heatmap](../../workflow/using/heatmap.md).
+++

+++**Hybride Bereitstellung**

Die Hybrid-Implementierung ist eine Kombination aus On-Demand-Diensten und On-Premise-Software, die bereitgestellt wird, um zusammen zu funktionieren.

Weitere Informationen [Hybride Bereitstellung](../../installation/using/hosting-models.md#hybrid).

+++

## I - L {#sec-3}

<!-- added more details but maybe still not clear/useful here? -->
+++**Identifizierungsmodus**

*Kontext: Kampagneninteraktion*

Der Identifikationsmodus bezieht sich auf den Status eines Kontakts. Sie kann explizit, implizit oder anonym sein.

* **explizit**: Der Kontakt konnte identifiziert werden, da er sich in der Kanalschnittstelle mit seinen Kundendaten angemeldet hat.
* **implizit**: Der Kontakt konnte mithilfe eines Cookies (Sitzungs- oder permanenter Cookie) identifiziert werden. Er kann entweder wie ein anonymer oder wie ein identifizierter Kontakt behandelt werden.
* **anonym**: Der Kontakt konnte nicht identifiziert werden.

Weitere Informationen [Interaction](../../interaction/using/interaction-and-offer-management.md).
+++

<!--
----NOT USEFUL HERE?----
+++**Image serving**

The functionality that supplies the images embedded in emails to the delivery’s recipients. The insertion of the images based on an emails system’s “download images” functionality is what generates an “open” entry in Campaign’s tracking logs.

Learn more about [Image serving](../../delivery/using/defining-the-email-content.md#adding-images).
+++
-->

+++**Eingehende Interaktionen**

*Kontext: Kampagneninteraktion*

Eine eingehende Interaktion ist eine Interaktion, die auf einen eingehenden Aufruf folgt, der durch die Aktion eines Kontakts in einem Kanal (z. B. Web, Callcenter oder Mobile) generiert wurde. Dieser Interaktionstyp wird im Allgemeinen im Einzelmodus verarbeitet (d. h. pro Empfänger).

Weitere Informationen [Eingehende Interaktionen](../../interaction/using/about-inbound-channels.md).
+++

+++**Inbox Rendering**

Beim Inbox Rendering handelt es sich um die Erstellung von E-Mail-Vorschauen, die sicherstellen, dass die Nachricht den Empfängern in unterschiedlichen Web-Clients, Web-Mails und Geräten optimal dargestellt wird. Adobe Campaign nutzt Litmus, das es Erstellern von E-Mail-Inhalten ermöglicht, ihren Nachrichteninhalt in über 70 E-Mail-Renderern als Vorschau anzuzeigen, z. B. im Gmail-Posteingang oder im Apple Mail Client.

Weitere Informationen [Inbox Rendering](../../delivery/using/delivery-dashboard.md#delivery-rendering).
+++

+++**Instanzeneinstellungen**

Instanzeneinstellungen sind Konfigurationsdetails einer Adobe Campaign-Instanz. Diese Einstellungen werden im Softwareverteilungs-Assistenten (Tools > Erweitert > Softwareverteilungs-Assistent) oder in den Konfigurationsdateien des Servers bzw. der Instanz definiert.

Weitere Informationen [Instanzeneinstellungen](../../installation/using/about-initial-configuration.md).

+++

+++**Vorgänge (Import und Export)**

Aufträge werden über ein Assistentensystem verwaltet, das den Import und Export von Daten in das und aus dem Produkt vereinfacht. Aufträge verwenden das Vorlagensystem zur Vereinfachung und Konsistenz und können für die Ausführung nach einem Zeitplan definiert werden.

Weitere Informationen [Import- und Exportvorgänge](../../platform/using/get-started-data-import-export.md).
+++

+++**Listen**

Eine Liste ist ein statischer Datensatz. Listen sind Zielgruppen oder Segmente, die aus anderen Quellen (Audience Manager, Experience Platform, Datenbank usw.) in Campaign importiert und auf der Benutzeroberfläche als importierte Listen angezeigt werden.

Weitere Informationen [Listen](../../platform/using/creating-and-managing-lists.md).
+++

+++**Lokaler Cache**

Der lokale Cache ist die Information, die lokal auf dem Computer des Benutzers gespeichert wird. Zwischengespeicherte Informationen werden von der Konsole verwendet, um den erforderlichen Traffic auf den Server zu reduzieren und die Leistung zu verbessern. Das regelmäßige Löschen des lokalen Caches (im Menü Datei ) aktualisiert die gespeicherten Informationen und verbessert die Leistung und Stabilität.

Weitere Informationen [Lokaler Cache](../../platform/using/faq-campaign-config.md#perform-soft-cache-clear).
+++

## M - P {#sec-4}

+++**Marketing Resource Management (MRM)**

*Kontext: Marketing Resource Management (MRM)*

Die **Marketing Resource Management (MRM)** -Modul in Adobe Campaign ermöglicht die Steuerung kollaborativer Marketing-Aktionen durch eine vollständige Verwaltung und Echtzeit-Verfolgung der damit verbundenen Aufgaben, Budgets und Marketing-Ressourcen. Adobe Campaign-Benutzer können ihre Aktionen koordinieren und über vollständige Validierungsprozesse und geeignete Tracking-Tools ihren Fortschritt in allen Phasen validieren: Berichte, Verfolgung von Genehmigungen, Benachrichtigungen, Diskussionsforen usw.

Weitere Informationen [MRM](../../mrm/using/about-marketing-resource-management.md).
+++

<!--
----ACS?----
+++**Localization**

This template type is used to manage multilingual messages.  It is available for Email and SMS messages and useable in standalone mode, within a workflow or in a recurring delivery. In the multilingual feature templates, the language management is based on variants. Each variant represents one language.  This functionality is available only in Adobe Campaign Standard.  
+++
-->

+++**Spezifische Berechtigungen**

Die granularen Datenbankzugriffsberechtigungen, die zum Definieren des Benutzergruppenzugriffs und der Berechtigungen (Rollen) verwendet werden. Spezifische Berechtigungen werden während der Installation des Produkts und durch den Import verschiedener Packages, die bestimmte Funktionen des Tools definieren, ausgefüllt. Benutzerdefinierte spezifische spezifische Berechtigungen können erstellt werden, um die geschäftlichen Anforderungen des Kunden zu unterstützen.

Weitere Informationen [Spezifische Berechtigungen](../../platform/using/access-management-named-rights.md).
+++

+++**Namespace**

Der Namespace ist eine Partition, die Kundendatentypen von den nativen Datentypen von Adobe Campaign im Datenmodell trennt. Dient auch dazu, die Migration von Definitionen von einer Instanz in eine andere zu erleichtern, z. B. das Verschieben eines Schemas oder einer Vorlage von der Entwicklungsinstanz in die Produktionsinstanz.

Weitere Informationen [Namespace](../../configuration/using/about-schema-reference.md#identification-of-a-schema).
+++

+++**Navigationsleiste**

Die Navigationsleiste ist das Navigationselement, das oben auf der Benutzeroberfläche ausgeführt wird. Die Navigationsleiste enthält die verschiedenen Kernfunktionen der Plattform. Klicken Sie auf einen Link in der Navigationsleiste, um die mit dieser Funktion verbundenen Funktionen anzuzeigen. Die Liste der Rubriken hängt von den installierten Packages und Add-ons sowie den Zugriffsberechtigungen des aktuellen Benutzers ab. Die Navigationsleiste soll die Bildschirmverwaltung vereinfachen und die Produktivität steigern.

Weitere Informationen [Navigationsleiste](../../platform/using/adobe-campaign-workspace.md#browsing-pages).
+++

+++**Navigationsbaum**

Die Navigationsstruktur ist die Hauptnavigation in der Explorer-Ansicht von Adobe Campaign. Der Navigationsbaum funktioniert wie ein Datei-Browser (z. B. Windows Explorer). Ordner können Unterordner enthalten. Wenn Sie einen Knoten auswählen, wird die dem Knoten entsprechende Ansicht angezeigt. Die angezeigte Ansicht ist eine Liste, die mit einem Schema und einem Eingabeformular zur Bearbeitung der ausgewählten Zeile verknüpft ist. Sie können die Navigationsstruktur anpassen und Berechtigungen für Ordner festlegen.

Weitere Informationen [Navigationsstruktur](../../platform/using/adobe-campaign-explorer.md#about-navigation-hierarch).
+++

+++**Einleitung**

*Kontext: Marketing Resource Management (MRM)*

Im Rahmen der Kampagne, des Programms oder des Plans können die Benutzer eine Liste der Ziele angeben. Dies sind quantifizierte Werte, die erreicht werden sollen. Am Ende der Kampagne, des Programms oder des Plans ermöglicht das MRM-Modul den Benutzern, die Zielsetzungen und Ergebnisse in speziellen Berichten zu vergleichen.

Weitere Informationen [Ziele](../../mrm/using/creating-and-managing-tasks.md#expenses-and-revenues).
+++

+++**Angebotskatalog**

*Kontext: Kampagneninteraktion*

Ein Angebotskatalog ist ein in Adobe Campaign definierter Satz von Angeboten, die während einer Interaktion ausgewählt werden können. Der Katalog ist hierarchisch strukturiert, wobei jeder Knoten einer Kategorie entspricht.

Weitere Informationen [Angebotskatalog](../../interaction/using/offer-catalog-overview.md).
+++

+++**Angebotskontakt**

*Kontext: Kampagneninteraktion*

Bei einem Angebotskontakt handelt es sich um einen Kontakt aus einer eingehenden Interaktion. Bei der Verarbeitung der Engine-Aufrufe wird der Kontakt mit einer Zielgruppendimension verknüpft. Nicht identifizierbare anonyme Kontakte werden der Zielgruppendimension der Besucher zugeordnet. Es gibt zwei Arten von Kontakten: identifiziert und anonym:

* **Identifizierter Kontakt**: Kontakt, der sich explizit im Kanal identifiziert hat (z. B. durch Angabe einer Benutzerkennung und eines Kennworts). Bei ausgehenden Interaktionen sind alle Kontakte systematisch identifiziert.
* **Anonymer Kontakt**: Kontakt, der sich nicht explizit im Kanal identifiziert hat, der jedoch mithilfe eines Cookies implizit identifiziert werden kann. Diese Art von Kontakten tritt nur bei eingehenden Interaktionen auf.

Weitere Informationen [Interaction](../../interaction/using/interaction-and-offer-management.md).
+++

+++**Angebotserstellungsumgebung**

*Kontext: Kampagneninteraktion*

Das Angebot **Design-Umgebung** ist die Umgebung, in der Benutzer Angebote erstellen, Typologieregeln definieren und das Schema auswählen, auf das sich die Angebote beziehen sollen. Die Tabelle zum Speichern der erstellten Angebotsvorschläge wird ebenfalls von der Umgebung definiert. Standardmäßig enthält das Interaction-Add-on eine **Design** Umwelt und **Live** verknüpfte Umgebung. Beide Umgebungen sind für die integrierte Empfängertabelle vorkonfiguriert.

Weitere Informationen [Design-Umgebungen](../../interaction/using/fundamental-principles.md).
+++

+++**Angebotsmodul-Arbitrage**

*Kontext: Kampagneninteraktion*

Das Angebotsmodul wählt die Angebote aus, die in einer Umgebung angezeigt werden (geeignete Angebote). Das Arbitrage-Prinzip ordnet Angebote nach Priorität nach den in den Kategorien und Angeboten definierten Kriterien.

Weitere Informationen [Interaction](../../interaction/using/interaction-and-offer-management.md).
+++

+++**Beschneiden von Angebotsmodulen**

*Kontext: Kampagneninteraktion*

Beim Beschneiden des Angebotsmoduls werden Angebote gelöscht, die nicht für eine Auswahl infrage kommen. Wird vor dem Arbitrage-Schritt des Angebotsmoduls ausgeführt.

Weitere Informationen [Interaction](../../interaction/using/interaction-and-offer-management.md).
+++

+++**Angebotsumgebung**

*Kontext: Kampagneninteraktion*

Die Angebotsumgebung ist der Stammordner, der einen Angebotskatalog, seine verfügbaren Platzierungen und die vordefinierten Filter der Umgebung definiert. Benutzer müssen für jede Zielgruppendimension eine Umgebung erstellen. Es gibt zwei Arten von Angebotsumgebungen: Design und Live.

Weitere Informationen [Umgebungen](../../interaction/using/fundamental-principles.md).
+++

+++**Live-Umgebung des Angebots**

*Kontext: Kampagneninteraktion*

Die Live-Umgebung des Angebots ist mit einer Kampagne verknüpft. **Design-Umgebung**. Es enthält schreibgeschützte Angebote, deren Inhalt und Berechtigung über die Variable **Design-Umgebung**. Sie können zur Präsentation auf einer Website oder zur Einfügung in eine ausgehende Nachricht ausgewählt werden.

Weitere Informationen [Live-Umgebungen](../../interaction/using/fundamental-principles.md).
+++

+++**Angebotsunterbreitungsregeln**

*Kontext: Kampagneninteraktion*

Angebotsunterbreitungsregeln sind Typologieregeln, auf die in der Angebotsumgebung verwiesen wird und die es Benutzern ermöglichen, bestimmte Angebote auszuschließen, indem der Vorschlagsverlauf des Empfängers berücksichtigt wird.

Weitere Informationen [Angebotsunterbreitungsregeln](../../interaction/using/managing-offer-presentation.md#presentation-rules-overview).
+++

+++**Angebotsvorschau**

*Kontext: Kampagneninteraktion*

Dies ist die Vorschau des Angebots, wie es in seinem Ordner angezeigt wird. Der Zugriff erfolgt über den Tab Angebotsvorschau oder über das Kontaktprofil.

Weitere Informationen [Angebotsvorschau](../../interaction/using/creating-an-offer.md#previewing-the-offer).
+++

+++**Angebotsvorschläge**

*Kontext: Kampagneninteraktion*

Ein Angebotsvorschlag ist das Ergebnis einer Aktion, die darin besteht, einem Kontakt in einer Platzierung ein Angebot zu unterbreiten, z. B. das Banner auf einer Website, eine E-Mail oder SMS-Inhalt. Dieses Ergebnis wird in der Tabelle der Angebotsvorschläge gespeichert, die das Angebot, den Empfänger und den Zeitstempel definiert und einen Datensatz mit allen Angeboten enthält, die ein Empfänger erhalten hat.

Weitere Informationen [Angebotsvorschläge](../../interaction/using/creating-offer-spaces.md#offer-proposition-statuses).
+++

+++**Angebotsdarstellung**

*Kontext: Kampagneninteraktion*

Ein Angebotsvorschlag ist das Ergebnis einer Aktion, die darin besteht, einem Kontakt in einer Platzierung ein Angebot zu unterbreiten, z. B. das Banner auf einer Website, eine E-Mail oder SMS-Inhalt. Dieses Ergebnis wird in der Tabelle der Angebotsvorschläge gespeichert, die das Angebot, den Empfänger und den Zeitstempel definiert und einen Datensatz mit allen Angeboten enthält, die ein Empfänger erhalten hat.

Weitere Informationen [Interaction](../../interaction/using/interaction-and-offer-management.md).
+++

+++**Angebotssimulation**

*Kontext: Kampagneninteraktion*

Mit einer Angebotssimulation können Benutzer die Verteilung des Angebots über einen bestimmten Zeitraum hinweg testen (Versanddatum, Zielsegment, Anzahl der Angebote, Thema usw.). vor dem tatsächlichen Versand der Angebote. Er kann verwendet werden, um Angebotsprioritäten und Eignungsregeln anzupassen und so die Effektivität des Angebots zu maximieren.

Weitere Informationen [Angebotssimulation](../../interaction/using/about-offers-simulation.md).
+++

+++**Angebotsplatzierung**

*Kontext: Kampagneninteraktion*

Eine Platzierung ist ein Ordner, der den Ort definiert, an dem das Angebot angezeigt wird. Durch die Definition einer Platzierung können Sie den verwendeten Kanal festlegen, den Inhalt des Angebots erstellen und die vorgeschlagenen Angebote angeben. Die Platzierung bildet die Schnittstelle zwischen Kanal und Angebotsmodul.

Weitere Informationen [Angebotssimulation](../../interaction/using/creating-offer-spaces.md).
+++

+++**Angebotsthemen**

*Kontext: Kampagneninteraktion*

Angebotsthemen sind in einer Kategorie definierte Suchbegriffe, mit denen Benutzer Angebote bei ihrer Präsentation filtern können. Themen ermöglichen eine nicht hierarchische Auswahl von Angeboten aus der Katalogstruktur.

Weitere Informationen [Angebotsthemen](../../interaction/using/integrating-an-offer-via-the-wizard.md).
+++

+++**Angebotsgewichtung**

*Kontext: Kampagneninteraktion*

Die Gewichtung basiert auf Formeln, die die Relevanz eines Angebots genau definieren, damit das Angebotsmodul das relevanteste Angebot auswählen kann. Die Gewichtung wird in den Angeboten definiert und die Multiplikatoren werden in den Kategorien definiert. Geeignete Angebote werden in absteigender Reihenfolge der Gewichtung berücksichtigt.

Weitere Informationen [Angebotsgewichtung](../../interaction/using/creating-an-offer.md#offer-weight).
+++

+++**Operator**

Ein Operator ist ein Benutzer von Adobe Campaign, der die Berechtigung besitzt, sich anzumelden und Aktionen durchzuführen. Benutzer sind Benutzergruppen zugeordnet und erben die Rechte und Rechte dieser Gruppen. Sie können Benutzern auch direkt spezifische Berechtigungen zuweisen.

Weitere Informationen [Benutzer](../../platform/using/access-management-operators.md).
+++

+++**Benutzergruppen**

Benutzergruppen ermöglichen die Verwaltung von Rollen für Campaign-Benutzer. Definieren Sie Benutzergruppen, denen Sie Berechtigungen zuweisen, und verbinden Sie dann die Benutzer mit einer oder mehreren Gruppen. Auf diese Weise können Sie Berechtigungen wiederverwenden und die Konsistenz von Benutzerprofilen verbessern. Außerdem wird die Verwaltung und Pflege von Profilen erleichtert.

Weitere Informationen [Benutzergruppen](../../platform/using/access-management-groups.md).
+++

+++**Optionen**

Optionen sind Variablen auf Plattformebene, mit denen Einstellungen der Campaign-Instanz definiert werden. Optionen können Zeitrahmen (z. B. für Datenbankbereinigungs-Workflows) oder andere globale Definitionen auf Plattformebene definieren.

Weitere Informationen [Optionen](../../installation/using/configuring-campaign-options.md).
+++

+++**Ausgehende Interaktionen**

*Kontext: Kampagneninteraktion*

Eine ausgehende Interaktion ist ein Aufruf des Angebotsmoduls über eine Kontaktliste (zum Versand von E-Mails, Briefpost usw.). Auf jeden Kontakt werden die gleichen Regeln und Prozesse angewendet. Dieser Interaktionstyp wird im Allgemeinen im Batch-Modus verarbeitet.

Weitere Informationen [Ausgehende Interaktion](../../interaction/using/about-outbound-channels.md).
+++

+++**Package-Export/-Import**

Ein Package-Export ist ein Vorgang, bei dem eine XML-Datei erzeugt wird, die Definitionen von Objekten enthält. Pakete werden verwendet, um Funktionen und Definitionen von einer Instanz in eine andere zu migrieren. Sie werden auch verwendet, um wichtige Produktdefinitionen zu Sicherungs- und Quellkontrollsystemen hinzuzufügen.

Weitere Informationen [Package-Export/-Import](../../platform/using/working-with-data-packages.md).
+++

+++**Palette**

In der Workflow-Palette werden die verfügbaren Aktivitäten angezeigt, die einem Workflow hinzugefügt werden können. Diese Komponente wird in Tabs angezeigt, wobei Workflow-Aktivitäten logisch nach ihrer Verwendung gruppiert werden. Die in der Palette verfügbaren Aktivitäten werden durch die in der Campaign-Instanz installierten Add-ons und durch den Kontext bestimmt, der den Workflow anzeigt.

Weitere Informationen [Palette](../../workflow/using/building-a-workflow.md#adding-and-linking-activities).
+++

+++**Leistungsüberwachung**

Informationen zur Leistungsüberwachung werden auf der Registerkarte Überwachung angezeigt. Es werden Metriken für das zugrunde liegende System angezeigt, z. B. Speicher- und CPU-Auslastung, SMTP-Serverstatistiken, Serverprozesse und andere relevante Informationen.

Weitere Informationen [Leistungsüberwachung](../../production/using/monitoring-processes.md).
+++

+++**Gestaltungsbausteine**

Adobe Campaign bietet integrierte Gestaltungsbausteine, die Sie in Ihre Sendungen einfügen können. Sie sind dynamisch, personalisiert und enthalten ein bestimmtes Rendering. Sie ermöglichen beispielsweise das Einfügen eines Logos, einer bestimmten Anrede oder auch eines Links zur Mirror-Seite. Standardmäßig sind mehrere Gestaltungsbausteine verfügbar. Sie können auch benutzerdefinierte Gestaltungsbausteine definieren, mit denen Sie Ihre Versandpersonalisierung optimieren können. Die tatsächlichen Daten werden während der Analysephase des Versands in jede erzeugte Nachricht eingefügt.

Weitere Informationen [Gestaltungsbausteine](../../delivery/using/personalization-blocks.md).
+++

+++**Personalisierungsfeld**

Ein Personalisierungsfeld ist eine Referenz für einzelne Datenfelder, die bei der Personalisierung eines Versands für einen bestimmten Empfänger verwendet wird. Der tatsächliche Datenwert wird während der Versandanalyse eingefügt.

Weitere Informationen [Personalisierungsfelder](../../delivery/using/personalization-fields.md).
+++

+++**Personalisierungsvariablen**

Personalisierungsvariablen sind Code-Abschnitte in einem Versand, die je nach Empfängerinformationen unterschiedlichen Text anzeigen können. Diese Felder können entweder als Personalisierungsfeld oder -block implementiert werden.

Weitere Informationen [Personalisierungsvariablen](../../delivery/using/about-personalization.md).
+++

+++**Plan**

Ein Plan ist ein Ordnertyp, der zum Organisieren von Marketingaktivitäten auf Kalenderbasis verwendet wird. In der Explorer-Ansicht können Sie Ordner planen und zeitbasierte Einheiten definieren, z. B. ein Jahr, ein Quartal oder einen Monat. Planordner können verschachtelt sein und andere Planungsordner, Programmordner oder Kampagnen enthalten.

Weitere Informationen [Pläne](../../campaign/using/setting-up-marketing-campaigns.md).
+++

+++**Vordefinierte Filter**

Vordefinierte Filter sind Abfragen, die zur Wiederverwendung gespeichert wurden. Die Verwendung vordefinierter Filter steigert die Produktivität (da sie nur einmal erstellt werden), hilft bei der Konsistenz (da alle Marketing-Experten sie verwenden können) und senkt die für den Marketing-Experten erforderlichen Fähigkeiten, da sie Code oder Logik verwenden können, die sie möglicherweise nicht selbst erstellen können.

Weitere Informationen [Vordefinierte Filter](../../platform/using/creating-filters.md#filtering-recipients).
+++

<!--
----DEPRECATED----
+++**Predictive Engagement Scoring**

Predictive engagement scoring predicts the probability of a recipient engaging with a message and the probability of opting out (unsubscribing) within the next seven days after the next email send. The probabilities are further divided into buckets according to the specific risk of disengagement, medium, or low. The model also provides the risk percentile rank for the customers to understand where the rank of a certain customer in relation to others. 

Learn more about [Predictive Engagement Scoring](../../platform/using/creating-filters.md).
+++
-->

+++**Primärschlüssel**

Der Primärschlüssel ist die eindeutige Kennung für jeden Datensatz in einer Datenbanktabelle. Eine Tabelle muss mindestens einen Schlüssel haben. In der Regel werden Schlüssel nach dem Hauptelement des Schemas und der Indizes deklariert. Primäre Schlüssel können nicht zusammengesetzt sein (mehrere Felder enthalten).

Weitere Informationen [Primärer Schlüssel](../../configuration/using/schema/key.md).
+++

+++**Profil**

Ein Profil ist ein Datensatz mit Informationen, die einen Endkunden, einen Interessenten oder einen Lead repräsentieren. Jedes Profil entspricht einem Datensatz in der nmsRecipient -Tabelle oder einer externen Tabelle, die Cookie-ID, Kunden-ID, mobile Kennung oder andere für einen bestimmten Kanal relevante Informationen enthält.

Weitere Informationen [Profile](../../platform/using/about-profiles.md).
+++

+++**Programm**

Programme und Unterprogramme organisieren Marketingaktivitäten im Hinblick auf ein Geschäftsziel, wie z. B. Treue, Akquise oder Crosssell. Sie können auch fiskalische Zeiträume oder Kampagnentaktiken darstellen, wie z. B. Ereignisse oder Newsletter. Jedes Programm enthält Kampagnen, die mit einem Kalender verknüpft sind, der eine Gesamtübersicht bietet.

Weitere Informationen [Programme](../../campaign/using/setting-up-marketing-campaigns.md).
+++

+++**Öffentliche Ressourcen**

Der Ordner Öffentliche Ressourcen in Adobe Campaign enthält Bilder, die vom Anwendungsserver gehostet werden. Bilder in Sendungen müssen auf dem Anwendungsserver (oder, falls Campaign so konfiguriert ist, auf einem Image-Hosting-Server) veröffentlicht werden, damit sie in Sendungen wie E-Mails angezeigt werden.

Weitere Informationen [Öffentliche Mittel](../../installation/using/deploying-an-instance.md#managing-public-resources).
+++

+++**Push-Benachrichtigung**

*Kontext: Mobile App Channel*

Push-Benachrichtigungen sind Nachrichten, die von Mobile Apps empfangen werden. Push-Benachrichtigungen werden für die Verwendung mit Adobe Campaign konfiguriert, indem der Experience Platform SDK-Code in die Mobile App eingefügt wird. Für Push stehen zwei Versandkanäle zur Verfügung: iOS und Android.

Weitere Informationen [Push](../../delivery/using/about-mobile-app-channel.md).
+++

## Q - T {#sec-5}

+++**Empfänger**

In Adobe Campaign sind Empfänger die Standardprofile für den Versand von Nachrichten (E-Mails, SMS usw.) an Ihre Kunden. Die in der Datenbank gespeicherten Empfängerdaten ermöglichen die Filterung der Zielgruppe und das Hinzufügen von Personalisierungsdaten. In der Regel handelt es sich hierbei um personenbezogene, Kontakt-, demografische und Transaktionsinformationen. Es kann sich jedoch um jede Art von Informationen handeln, die Marketing- und Analysefunktionen unterstützt.

Weitere Informationen [Empfänger](../../configuration/using/about-data-model.md).
+++

+++**Rendering-Funktion**

*Kontext: Kampagneninteraktion*

Die Rendering-Funktion wird in einer Platzierung definiert. Sie wird verwendet, um ihre Angebotsdarstellung basierend auf den im Angebot definierten Attributen zu erstellen. Es bestehen drei verschiedene Rendering-Funktionsmodi: HTML, XML und Text.

Weitere Informationen [Rendering-Funktion](../../interaction/using/creating-offer-spaces.md).
+++

<!--
-----DID NOT FIND IN ACC DOCS, ACS?----
+++**Retargeting campaigns**

Campaigns that re-target the recipients of a previous delivery or deliveries.
+++
-->

+++**Schema**

Ein Schema ist ein mit einer Datenbanktabelle verknüpftes XML-Dokument. Es definiert die Datenstruktur und beschreibt die SQL-Definition der Tabelle. Benutzer bearbeiten Schemata in Campaign, und das Produkt übersetzt ihre Aktionen in die erforderliche SQL, die dann mit der Datenbank ausgeführt wird.

Weitere Informationen [Schemas](../../configuration/using/about-schema-reference.md).
+++

+++**Schemaerweiterung**

Mit der Schemaerweiterung können Sie die nativen Schemata so anpassen, dass sie Ihren geschäftlichen Anwendungsfällen am besten entsprechen. Sie können beispielsweise das Feld &quot;Treueprogramm&quot;zur Empfängertabelle hinzufügen.

Weitere Informationen [Schemaerweiterung](../../configuration/using/extending-a-schema.md).
+++

+++**Testadressen**

Testadressen ermöglichen den Versand an Empfänger, die nicht den vorliegenden Zielgruppenkriterien entsprechen. Auf diese Weise können Empfänger, die außerhalb des Versandperimeters liegen, die Nachricht so wie jeder andere Empfänger innerhalb der Zielgruppe erhalten. Sie werden zur Audience einer Nachricht hinzugefügt, um Missbrauch bei der Nutzung Ihrer Empfängerdatenbank zu erkennen oder die Zustellung sicherzustellen.

Weitere Informationen [Testadressen](../../delivery/using/about-seed-addresses.md).
+++

<!--
-------ACS?-----
+++**Send-time optimization**

To improve the open rate of your messages, you can manually define a sending time per recipient. Each profile will receive the message at the specified date and time, whenever possible. Defining a sending time can be done at the delivery level or using a workflow.

Learn more about [Send-time optimization](../../delivery/using/about-seed-addresses.md:).
+++
-->

+++**Dienst**

Mit Adobe Campaign können Sie Informationsdienste wie Newsletter oder Produktaktualisierungen erstellen und verwalten und die Abonnements für diese Dienste verwalten. Mehrere Dienste können parallel definiert werden.

Weitere Informationen [Dienste](../../delivery/using/about-services-and-subscriptions.md).
+++

+++**SFTP-Verwaltung**

Über das Control Panel können Sie alle SFTP-Server verwalten, die mit den Campaign-Instanzen verbunden sind, auf die Sie Zugriff haben. Im Control Panel können Sie Aktionen für Ihre SFTP-Server ausführen, z. B. die Speicherkapazität überwachen, IP-Adressen-Zulassungslisten verwalten und öffentliche SSH-Schlüssel verwalten.

Weitere Informationen [SFTP-Verwaltung](https://experienceleague.adobe.com/docs/control-panel/using/sftp-management/about-sftp-management.html?lang=de).
+++

+++**Aktivität &quot;Anmeldedienste&quot;**

Mit der Workflow-Aktivität An-/Abmeldedienst können Sie ein Abonnement für einen Informationsdienst für die in der Transition angegebene Population erstellen oder löschen.

Weitere Informationen [Aktivität &quot;Anmeldedienste&quot;](../../workflow/using/subscription-services.md).
+++

+++**Validierung der Zielgruppe**

*Kontext: Distributed Marketing von Campaign*

Bei der Zielgruppenvalidierung wird die endgültige Zielgruppe eines Versands durch einen separaten Benutzer oder eine Benutzergruppe validiert (nachdem die Zielgruppe in der Analysephase erzeugt wurde), bevor der Versand durchgeführt werden kann.

Weitere Informationen [Zielgruppenvalidierung](../../workflow/using/local-approval.md).
+++

+++**Zielgruppendaten**

Zieldaten sind die in der Arbeitstabelle (Transition) eines Workflows gespeicherten Daten. Diese Daten stehen innerhalb des Versands zur Personalisierung des Versandinhalts oder zur Definition der Logik dynamischer Elemente des Versands zur Verfügung.

Weitere Informationen [Zielgruppendaten](../../workflow/using/data-life-cycle.md#target-data).
+++

+++**Zielgruppen-Mapping**

Zielgruppen-Mapping ist die Zuordnung von Versandkanälen zu einem bestimmten Datentyp. Zielgruppen-Mappings definieren, wie verschiedene Versandkanäle mit den Datenfeldern eines Schemas verknüpft werden. Sie definiert, wie Campaign mit einem bestimmten Feld oder Ausdruck an diesen Datentyp sendet.

Weitere Informationen [Zielzuordnung](../../delivery/using/selecting-a-target-mapping.md).
+++

+++**Zielgruppenaktivitäten**

Zielgruppenbestimmungsaktivitäten sind Workflow-Aktivitäten, die speziell für Zielgruppen-, Bearbeitungs- und Filteraktivitäten gelten. Benutzer können eine oder mehrere Zielgruppen erstellen, indem sie Sets definieren und diese mithilfe von Schnittmengen, Vereinigungen oder Ausschlüssen teilen oder kombinieren.

Weitere Informationen [Zielgruppenbestimmungsaktivitäten](../../workflow/using/about-targeting-activities.md).
+++

+++**Targeting dimension**

Die Zielgruppendimension ist der Datentyp, der von einer Abfrage oder anderen Workflow-Aktivitäten erzeugt (zurückgegeben) wird. Beachten Sie, dass Adobe Campaign nur den Primären Schlüssel der reagierenden Datenbankzeilen zurückgibt, unabhängig davon, welche Abfrage zum Abrufen verwendet wurde.

Weitere Informationen [Zielgruppendimension](../../workflow/using/targeting-data.md).
+++

+++**Aufgabenaktivität**

*Kontext: Marketing Resource Management (MRM)*

Die Workflow-Aktivität &quot;Aufgabe&quot;integriert menschliche Aktionen in die Logik eines Workflows. Sie können zwei Szenarien festlegen: das erste, wenn die Aufgabe abgeschlossen ist, und das zweite, wenn die Aufgabe nicht abgeschlossen ist. Typische Anwendungsfälle sind die Integration von Offline-Aktionen in eine Kampagne oder benutzerdefinierte Aktionen wie Genehmigungen.

Weitere Informationen [Aufgabenaktivität](../../workflow/using/task.md).
+++

<!--
-----NOT USEFUL, detail-----
+++**Task**

One iteration of the defined functionality of a workflow activity. Each execution of a task has a unique task identifier.   

Learn more about [Tasks](../../workflow/using/about-workflows.md).
+++
-->

+++**Template**

Eine Vorlage ist ein Designelement, mit dem ein Objekt erstellt wird. Es enthält Objekteinstellungen und optional den Inhalt des Objekts. Das Vorlagensystem dient zur Erstellung von Sendungen, Kampagnen, Workflows und vielen anderen Elementen von Adobe Campaign. Die verfügbaren Werksvorlagen werden durch die installierten Packages definiert. Vorlagen können dann von Campaign-Benutzern nach Bedarf dupliziert und angepasst werden.
+++

<!--
-----ACS -> SEEDS IN ACC-----
+++**Test profiles**

Allows targeting of additional recipients who do not match the defined targeting criteria. They are added to a message’s audience to detect any fraudulent use of your recipient database or to ensure delivery. Seen as the Seed type in the Campaign interface.

Learn more about [Test profiles](../../workflow/using/about-workflows.md).
+++
-->

<!--
-----NOT FOR DOCS?-----
+++**Total database storage**

The aggregate size of the production and non-production instance(s) database storage managed by Adobe. 

Learn more about [Total database storage](../../workflow/using/about-workflows.md).
+++
-->

+++**Trackinglogs**

Der technische Tracking-Workflow ruft die Tracking-Daten ab, sobald der Versand ausgeführt und das Tracking aktiviert wurde.
Diese Daten finden Sie auf der Registerkarte &quot;Tracking&quot; Ihres Versands. Sie finden Informationen zu Öffnungen und Klicks auf eine E-Mail oder andere Interaktionen mit einer vom Empfänger empfangenen Nachricht.

Weitere Informationen [Trackinglogs](../../delivery/using/accessing-the-tracking-logs.md).
+++

+++**Transaktionsnachrichtenversand**

Transaktionsnachrichten sind ein Campaign-Modul zur Verwaltung von Benachrichtigungen bezüglich benutzerdefinierter Trigger, die aus von einem externen Informationssystem gesendeten Ereignissen generiert wurden. Bei einer Transaktionsnachricht handelt es sich um eine individuell zugeschnittene, eindeutige Mitteilung, die beispielsweise über eine Website in Echtzeit übermittelt wird. Sie wird erwartet, weil sie wichtige Informationen enthält, die der Empfänger überprüfen oder bestätigen möchte.

Weitere Informationen [Transaktionsnachrichten](../../message-center/using/about-transactional-messaging.md).
+++

<!------- USEFUL HERE??----->
+++**Ausgelöste Kampagnen**

Ausgelöste Kampagnen sind Kampagnen, die ausgeführt werden, wenn in einem Workflow eine API-Anfrage empfangen wird. API-Aufrufe werden von einer Signal -Aktivität im Workflow genutzt, der die Ausführung des Workflows initiiert.

Weitere Informationen [Ausgelöste Kampagnen](../../workflow/using/external-signal.md).
+++

<!--
-----NOT USEFUL-----
+++**Triggers**

Signals that initiate execution of a workflow, delivery or other action. Typically an API call. 

Learn more about [Triggers](../../workflow/using/about-workflows.md).
+++
-->

+++**Typology**

*Kontext: Kampagnenoptimierung*

Eine Typologie ist eine Gruppierung von Typologieregeln, die auf die Analysephase eines Versands angewendet werden. Eine Kampagnentypologie kann mehrere Typologieregeln enthalten, ein Versand kann jedoch nur eine Typologie referenzieren.

Weitere Informationen [Typologien](../../campaign-opt/using/about-campaign-typologies.md#typologies).
+++

+++**Typologieregel**

*Kontext: Kampagnenoptimierung*

Typologieregeln sind Geschäftsregeln, die im Rahmen der Analysephase des Versands implementiert werden. Typologieregeln sind Prüfungen des Versandinhalts (Kontrollregeln) oder der Zielgruppe des Versands (Filterregeln) oder andere Logiken (Druckregeln), die geschäftliche Anforderungen durchsetzen. Regeln sind granulare Elemente, die in einer oder mehreren Typologien enthalten sein können.

Weitere Informationen [Typologieregeln](../../campaign-opt/using/about-campaign-typologies.md#typology-rules).
+++

## U - Z {#sec-6}

+++**Einzelmodus**

*Kontext: Kampagneninteraktion, Transaktionsnachrichten*

Im Einzelmodus wird ein einzelner Kontakt vom Angebotsmodul zur Laufzeit verarbeitet. Dieser Modus wird im Allgemeinen für eingehende Interaktionen und Transaktionsnachrichten verwendet.

Weitere Informationen [Einzelmodus](../../interaction/using/about-inbound-channels.md).
+++

<!--
-----NO OCCURRENCE IN ACC, OLD v6 CONCEPT?----
+++**Universes**

Application pages hosted by the Campaign instance. Used for approval forms, landing pages, opt-out forms, preference pages or to implement other business requirements.  

Learn more about [Universes](../../workflow/using/about-workflows.md).
+++
-->

+++**Web-Anwendungen**

Webanwendungen sind dynamische und interaktive Anwendungsseiten, die von der Campaign-Instanz gehostet werden. Sie enthalten Daten aus der Datenbank und Inhalte, die an die Rechte des verbundenen Benutzers angepasst sind. Sie können beispielsweise ein Bearbeitungsformular für ein Extranet oder Benachrichtigungsformulare erstellen, die Daten aus der Datenbank mit Tabellen, Diagrammen, Formularen usw. enthalten. Mit dieser Funktion können Sie Webseiten entwerfen und posten, auf denen Benutzer Informationen suchen oder eingeben können.

Weitere Informationen [Webanwendungen](../../web/using/about-web-applications.md).
+++

+++**Workflow**

Ein Workflow ist eine visuelle Darstellung des Ausführungsflusses einer Kampagne. Damit können Sie das gesamte Spektrum an Prozessen und Aufgaben über die verschiedenen Module des Anwendungsservers hinweg koordinieren. Diese grafische Umgebung ermöglicht die Konzeption von Prozessen wie Segmentierung, Kampagnenausführung, Dateiverarbeitung, Beteiligung von Personen usw. Die Workflow-Engine führt diese Prozesse aus und verfolgt sie.

Weitere Informationen [Workflows](../../workflow/using/about-workflows.md).
+++

+++**Workflow-Protokoll**

Das Workflow-Journal ist das schrittweise Ausführungsprotokoll eines Workflows. Es enthält den gesamten Verlauf oder das Audit-Protokoll des Workflows. Sie wird für Entwicklungs-, Fehlerbehebungs- oder Debugging-Zwecke verwendet.

Weitere Informationen [Workflow-Protokoll](../../workflow/using/monitoring-workflow-execution.md).
+++

+++**Arbeitstabellen**

Die Arbeitstabelle enthält alle von Workflow-Transitionen übermittelten Informationen. Jeder Workflow verwendet mehrere Arbeitstabellen. Die Arbeitstabelle enthält die Ergebnisse der ursprünglichen Aktivität und deren Inhalt wird als Eingabe für die nächste (verbundene) Aktivität im Workflow verwendet.  Die Manipulation (Erweiterung, Anpassung) der Arbeitstabelle gehört zu den wichtigsten Fähigkeiten eines Adobe Campaign-Benutzers.

Weitere Informationen [Arbeitstabellen](../../workflow/using/about-workflows.md).
+++