---
product: campaign
title: Beschreibung des Adobe Campaign Classic-Datenmodells
description: Dieses Dokument beschreibt das Adobe Campaign-Datenmodell
feature: Data Model
role: Data Engineer, Developer
exl-id: fc0fd23c-f9ea-4e30-b47b-a84143d882ca
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '2404'
ht-degree: 2%

---

# Beschreibung des Campaign-Datenmodells{#data-model-description}


Adobe Campaign enthält ein vordefiniertes Datenmodell. In diesem Abschnitt finden Sie einige Details zu den integrierten Tabellen des Adobe Campaign-Datenmodells und deren Interaktion.

Um Beschreibungen der einzelnen Tabellen aufzurufen, navigieren Sie zu **[!UICONTROL &quot;Admin&quot; > &quot;Konfiguration&quot; > &quot;Datenschemata&quot;]**, wählen Sie eine Ressource aus der Liste und klicken Sie auf die Registerkarte **[!UICONTROL Dokumentation]**.

![](assets/data-model_documentation-tab.png)

>[!NOTE]
>
>Die physische und logische Struktur der in der Anwendung übertragenen Daten wird in XML beschrieben. Sie folgt einer Adobe Campaign-spezifischen Grammatik namens „Schema“. Weitere Informationen zu Adobe Campaign-Schemata finden Sie in [diesem Abschnitt](../../configuration/using/about-schema-reference.md).

## Beschreibung der Haupttabellen {#description-main-tables}

Adobe Campaign stützt sich auf eine relationale Datenbank mit Tabellen, die miteinander verknüpft sind.

Das folgende Diagramm zeigt die Verknüpfungen zwischen den wichtigsten Geschäftstabellen des Adobe Campaign-Datenmodells mit den jeweiligen Hauptfeldern.

<!--![](assets/data-model_diagram.png)-->

![](assets/data-model_simplified-diagram.png)

Das vordefinierte Adobe Campaign-Datenmodell enthält die unten aufgeführten Haupttabellen.

### NmsRecipient {#NmsRecipient}

Diese Tabelle entspricht dem Schema **nms:recipient** .

Dies ist die Standardtabelle, die für die **Empfänger von Sendungen** verwendet wird. Sie enthält daher die für Sendungen über die verschiedenen Kanäle erforderlichen Informationen:

* sEmail: email address.
* iEmailFormat: bevorzugtes Format für E-Mails (1 für Text, 2 für HTML und 0, wenn nicht definiert).
* sAddress1, sAddress2, sAddress3, sAddress4, sZipCode, sCity werden zur Erstellung der Postanschrift verwendet (gemäß XPZ 10-011 AFNOR-Standard vom Mai 1997).
* sPhone, sMobilePhone, sFax enthalten jeweils die Telefon-, Mobiltelefon- und Faxnummern.
* iBlackList ist das Standard-Opt-out-Flag, das für die Profile verwendet wird (1 bedeutet &quot;unsubscribed&quot;, 0 andernfalls).

Das Feld iFolderId ist der Fremdschlüssel, der den Empfänger mit seinem Ausführungsordner verknüpft. Weiterführende Informationen dazu finden Sie unter [XtkFolder](#XtkFolder).

Das Feld sCountryCode ist der ISO-Code 3166-1 Alpha 2 (2 Zeichen) des Empfängerlandes. Dieses Feld ist tatsächlich ein Fremdschlüssel in der Länderreferenztabelle (NmsCountry), der die Länderbezeichnungen und andere Ländercodedaten enthält. Wenn das Land nicht ausgefüllt ist, wird der Wert &quot;XX&quot;gespeichert (und anstelle eines Null-ID-Datensatzes verwendet).

Weitere Informationen zur Empfängertabelle finden Sie in [diesem Abschnitt](../../configuration/using/about-data-model.md#default-recipient-table).

### NmsGroup {#NmsGroup}

Diese Tabelle entspricht dem Schema **nms:group** .

Damit können Sie **statische Empfängergruppen** erstellen. Es besteht eine Viele-zu-viele-Beziehung zwischen Empfängern und Gruppen. Beispielsweise kann ein Empfänger mehreren Gruppen angehören und eine Gruppe kann mehrere Empfänger enthalten. Gruppen können manuell, über einen Import oder über Versand-Targeting erstellt werden. Gruppen werden häufig als Versandziele verwendet. Es gibt einen eindeutigen Index im Feld, der den internen Namen der Gruppe sName darstellt. Die Gruppe ist mit einem Ordner verknüpft (der Schlüssel ist iFolderId. Weiterführende Informationen dazu finden Sie unter [XtkFolder](#XtkFolder)).

### NmsRcpGrpRel {#NmsRcpGrpRel}

Die Beziehungstabelle NmsRcpGrpRel enthält nur die beiden Felder, die den Kennungen der mit iRecipientId und iGroupId verknüpften Tabellen entsprechen.

### NmsService {#NmsService}

Diese Tabelle entspricht dem Schema **nms:service** .

In Adobe Campaign können Sie Abonnements für Informationsdienste erstellen und verwalten (Themen). Die Tabelle NmsService speichert die Definition der Informationsdienste (Themen), die Sie Ihren Empfängern anbieten, sich für einen Newsletter anzumelden (z. B. einen Newsletter).

Dienste sind Entitäten, die Gruppen ähnlich sind (statische Empfängergruppierungen), mit dem Unterschied, dass sie mehr Informationen verbreiten und eine einfache Verwaltung von An- und Abmeldungen über Formulare ermöglichen.

Es gibt einen eindeutigen Index im Feld, der den internen Namen des sName-Dienstes darstellt. Der Dienst ist mit einem Ordner verknüpft (der Schlüssel ist iFolderId. Weiterführende Informationen dazu finden Sie unter [XtkFolder](#XtkFolder)). Schließlich gibt das Feld iType den Versandkanal dieses Dienstes an (0 für E-Mail, 1 für SMS, 2 für Telefon, 3 für Briefpost und 4 für Fax).

### NmsSubscription {#NmsSubscription}

Diese Tabelle entspricht dem Schema **nms:subscription** .

Damit können Sie Empfängeranmeldungen für Informationsdienste verwalten.

### NmsSubHisto {#NmsSubHisto}

Diese Tabelle entspricht dem Schema **nms:subHisto** .

Wenn die Abonnements über Webformulare oder die Benutzeroberfläche der Anwendung verwaltet werden, werden alle Anmeldungen und Abmeldungen in der Tabelle NmsSubHisto verzeichnet. Das Feld iAction gibt die Aktion (0 für die Abmeldung und 1 für das Abonnement) an, die am im Feld tsDate gespeicherten Datum ausgeführt wird.

### NmsDelivery {#NmsDelivery}

Diese Tabelle entspricht dem Schema **nms:delivery** .

Jeder Datensatz in dieser Tabelle stellt eine **Versandaktion** oder eine **Versandvorlage** dar. Er enthält alle für die Durchführung des Versands erforderlichen Parameter (Zielgruppe, Inhalt usw.). Versandlogs (broadcast) (NmsBroadLog) und zugehörige Tracking-URLs (NmsTrackingUrl) werden während der Analysephase erstellt (weitere Informationen zu beiden Tabellen finden Sie unten).

Es gibt einen eindeutigen Index im Feld, der den internen Namen des Versands oder Szenarios sInternalName darstellt. Der Versand ist mit einem Ausführungsordner verknüpft (der Fremdschlüssel ist iFolderProcessId. Weiterführende Informationen dazu finden Sie unter [XtkFolder](#XtkFolder)).

### XtkFolder {#XtkFolder}

Sie enthält **alle Ordner im Baum**, die auf der Registerkarte **Navigation** der Konsole angezeigt werden.

Die Ordner werden eingegeben: Der Wert des Felds sModel gibt den Datentyp an, der im Ordner enthalten sein kann. Dieses Feld ermöglicht es der Clientkonsole auch, die Daten mit den entsprechenden Formularen korrekt anzuzeigen. Die möglichen Werte für dieses Feld werden im Navigationsbaum definiert.

Die Struktur wird von den Feldern iParentId und iChildCount verwaltet. Das Feld sFullName gibt den vollständigen Pfad des Ordners im Baum an. Schließlich gibt es einen eindeutigen Index im Feld, der den internen Namen des Ordners sName darstellt.

## Versand und Tracking {#delivery-and-tracking}

Dieser Tabellensatz ist mit dem Modul **Versand** verknüpft, mit dem Sendungen und etwaige Probleme beim Nachrichtenversand überwacht werden können. Weiterführende Informationen dazu finden Sie im Abschnitt [Sendungen beobachten](../../delivery/using/about-delivery-monitoring.md). Weitere Informationen zum Tracking finden Sie unter [Nachrichten tracken](../../delivery/using/about-message-tracking.md).

![](assets/data-model_delivery.png)

**NmsBroadLogMsg**: Diese Tabelle entspricht dem Schema **nms:broadLogMsg** . Dies ist eine Erweiterung der Versandlog-Tabelle.

## Kampagnenverwaltung {#campaign-management}

Dieser Tabellensatz ist mit dem Modul **Marketing-Kampagnen** verknüpft, mit dem Kommunikations- und Marketingkampagnen definiert, optimiert, ausgeführt und analysiert werden können. Weiterführende Informationen dazu finden Sie im Abschnitt [Über Marketingkampagnen](../../campaign/using/designing-marketing-campaigns.md).

![](assets/data-model_campaign.png)

* **NmsOperation**: Diese Tabelle entspricht dem Schema **nms:operation** . Sie enthält die Daten von Marketing-Kampagnen.
* **NmsDeliveryOutline**: Diese Tabelle entspricht dem Schema **nms:deliveryOutline** . Sie enthält die erweiterten Eigenschaften des Versands (Versandentwurf).
* **NmsDlvOutlineItem**: Diese Tabelle entspricht dem Schema **nms:dlvOutlineItem** . Sie enthält die Artikel eines Versandentwurfs.
* **NmsDeliveryCustomization**: Diese Tabelle entspricht dem Schema **nms:deliveryCustomization** . Sie enthält die Personalisierungsfelder eines Versands.
* **NmsBudget**: Diese Tabelle entspricht dem Schema **nms:budget** . Sie enthält Daten aus einem Budget einer Kampagne, eines Plans, eines Programms, einer Aufgabe und/oder Sendungen.
* **NmsDocument**: Diese Tabelle entspricht dem Schema **nms:document** . Es enthält die Marketing-Dokumente der Kampagne in Form von Dateien (Bilder, Excel- oder Wortdateien usw.)
* **XtkWorkflow**: Diese Tabelle entspricht dem Schema **xtk:workflow** . Sie enthält Kampagnen-Targeting.
* **NmsTask**: Diese Tabelle entspricht dem Schema **nms:task** . Es enthält die Definition einer Marketing-Aufgabe.
* **NmsAsset**: Diese Tabelle entspricht dem Schema **nms:asset** . Sie enthält die Definition einer Marketing-Ressource.

## Kommunikationskonsistenz {#communication-consistency}

Dieser Tabellensatz ist mit dem Modul **Kampagnenoptimierung** verknüpft, das die Kontrolle, Filterung und Überwachung des Versands von Sendungen ermöglicht. Weiterführende Informationen dazu finden Sie im Abschnitt [Über Kampagnentypologien](../../campaign-opt/using/about-campaign-typologies.md).

![](assets/data-model_typology.png)

* **NmsTypologyRule**: Diese Tabelle entspricht dem Schema **nms:typologyRule** . Sie enthält die Regeln, die je nach Typologie für Sendungen gelten.
* **NmsTypology**: Diese Tabelle entspricht dem Schema **nms:typology** . Sie enthält die Regeln, die auf Sendungen angewendet werden, die der Typologie entsprechen.
* **NmsTypologyRuleRel**: Diese Tabelle entspricht dem Schema **nms:typologyRuleRel** . Es enthält die Beziehungen zwischen Typologien und deren Regeln.
* **NmsVolumeLine**: Diese Tabelle entspricht dem Schema **nms:VolumeLine** . Sie enthält die Verfügbarkeitszeilen der Kapazitätsregeln.
* **NmsVolumeConsumed**: Diese Tabelle entspricht dem Schema **nms:VolumeConsumed** . Sie enthält alle Verbrauchszeilen der Kapazitätsregeln.

## Reaktionsverwaltung {#response-management}

Diese Tabellen sind mit dem Modul **Response Manager** verknüpft, mit dem der Erfolg und die Rentabilität von Marketing-Kampagnen oder Angebotsvorschlägen für alle Kommunikationskanäle gemessen werden kann. Weiterführende Informationen dazu finden Sie unter [Über den Antwort-Manager](../../response/using/about-response-manager.md).

![](assets/data-model_response.png)

### NmsRemaHypothesis {#NmsRemaHypothesis}

Diese Tabelle entspricht dem Schema **nms:remaHypothesis** . Sie enthält die Definition der Messhypothese.

Diese Tabelle enthält wichtige in XML gespeicherte Informationen, darunter:

**Ausführungskontext (in XML gespeicherte Informationen)**

Der Ausführungskontext füllt die Tabellen und Felder aus, die bei der Berechnung der Messung berücksichtigt werden sollen:
* Das Speicherschema des Reaktionslog-Speichers nms:remaMatchRcp.
* Das Transaktionstabelle-Schema (z. B. Käufe).
* Das Abfrageschema, mit dem Sie die Starttabelle der Hypothesenbedingungen definieren können.
* Die Relationen zu den Individuen, die die Identifizierung des Kontakts basierend auf dem Abfrageschema ermöglichen.
* Das Transaktionsdatum. Dieses Feld ist nicht zwingend erforderlich. Es wird jedoch empfohlen, den Berechnungsrahmen einzuschränken.
* Transaktionsbetrag: Es handelt sich um ein optionales Feld zur automatischen Berechnung der Umsatzindikatoren.

**Perimeter der Hypothese (in XML gespeicherte Informationen)**

Der Perimeter der Hypothese besteht aus der Filterung der Hypothese anhand der Tabelle des Abfrageschemas.

**Überlastungsskript für Hypothesen (in XML gespeicherte Informationen)**

Das Hypothesenüberlastungsskript ist ein JavaScript-Code, mit dem Sie den Inhalt der Hypothese während der Ausführung überschreiben können.

**Messindikatoren**

Die folgenden Indikatoren werden während der Ausführung der Hypothese automatisch aktualisiert:

* Anzahl der Reaktionen: **iTransaction** Anzahl der Zeilen in der Tabelle der Reaktionslogs.
* Anzahl der Kontakte: **iContactReact** Bestimmte Anzahl von Zielkontakten in der Hypothese.
* Kontrollgruppenanzahl: **iProofReact**. Bestimmte Anzahl von Zielgruppenkontakten in der Hypothese.
* Reaktionsrate kontaktiert: **dContactReactRate**. Reaktionsrate der in der Hypothese enthaltenen Kontakte.
* Reaktionsrate der Kontrollgruppe: **dProofReactRate**. Reaktionsrate der Hypothesenkontrollgruppe.
* Gesamtumsatz Kontakte: **dContactReactTotalAmount**. Gesamtumsatz der Kontakte in der Hypothese.
* Durchschnittlicher Umsatz Kontrollgruppe: **dContactReactAvgAmount**. Durchschnittlicher Umsatz der Zielgruppenkontakte in der Hypothese.
* Gesamtumsatz der Kontrollgruppe: **dProofReactTotalAmount**. Gesamtumsatz der Hypothesenkontrollgruppe.
* Durchschnittlicher Umsatz Kontrollgruppe: **dProofReactAvgAmount**. Durchschnittlicher Umsatz der Hypothesenkontrollgruppe.
* Gesamtspanne Kontakte: **dContactReactTotalMargin**. Gesamtspanne Kontakte, die in der Hypothese berücksichtigt wurden.
* Durchschnittliche Spanne pro Kontakt: **dContactReactAvgMargin**. Durchschnittliche Spanne Kontakte, die in der Hypothese berücksichtigt werden.
* Gesamtspanne der Kontrollgruppe: **dProofReactTotalMargin**. Gesamtspanne der in der Hypothese enthaltenen Kontrollgruppe.
* Durchschnittliche Spanne der Kontrollgruppe: **dProofReactAvgMargin**. Durchschnittliche Spanne der in der Hypothese enthaltenen Kontrollgruppe.
* Zusätzlicher Umsatz: **dAdditionalAmount**. (Durchschnittlicher Umsatz der Kontakte - Durchschnittlicher Umsatz der Individuen in der Kontrollgruppe) * Anzahl Kontakte.
* Zusätzlicher Rand: **dAdditionalMargin**. (Durchschnittliche Spanne der Kontakte - Durchschnittliche Spanne der Individuen in der Kontrollgruppe) / Anzahl Kontakte.
* Durchschnittliche Kosten pro Kontakt (SQL-Ausdruck). Berechnete Kosten des Versands / Anzahl Kontakte.
* ROI (SQL-Ausdruck). Berechnete Kosten des Versands / Gesamtspanne der Kontakte.
* Effektiver ROI (SQL-Ausdruck). Berechnete Kosten des Versands / Zusätzliche Spanne.
* Signifikanz: **Significativy** (SQL-Ausdruck). Enthält Werte von 0 bis 3 in Abhängigkeit von der Signifikanz der Kampagne.

### NmsRemaMatchRcp {#NmsRemaMatchRcp}

Diese Tabelle entspricht dem Schema **nms:remaMatchRcp** .

Es enthält einen Datensatz, der die Reaktion einer Person auf eine bestimmte Hypothese darstellt. Diese Datensätze wurden während der Ausführung der Hypothese erstellt.

## Simulation und Versand {#simulation-and-delivery}

Dieser Tabellensatz ist mit dem Modul **Simulation** verknüpft, mit dem die Verteilung der Angebote einer Kategorie oder einer Umgebung getestet werden kann, bevor der Vorschlag an die Empfänger gesendet wird. Weiterführende Informationen dazu finden Sie im Abschnitt [Über die Angebotssimulation](../../interaction/using/about-offers-simulation.md).

![](assets/data-model_simulation.png)

* **NmsSimulation**: Diese Tabelle entspricht dem Schema **nms:simulation** . Er stellt eine Simulation für eine Reihe von Sendungen oder Angeboten für eine bestimmte Population dar.
* **NmsDlvSimulationRel**: Diese Tabelle entspricht dem Schema **nms:dlvSimulationRel** . Er enthält die Liste der in der Simulation berücksichtigten Sendungen. Der Perimeter der Simulation wird in XML gespeichert.
* **NmsOfferSimulationRel**: Diese Tabelle entspricht dem Schema **nms:offerSimulationRel** . Damit können Sie eine Simulation mit einem Angebot verknüpfen.

## Interaktionsmodul {#interaction-module}

Dieser Tabellensatz ist mit dem Modul **Interaction** verknüpft, das es ermöglicht, in Echtzeit während einer Interaktion mit einem bestimmten Kontakt zu reagieren, indem es ihn zu einem oder mehreren angepassten Angeboten macht. Weiterführende Informationen dazu finden Sie unter [Interaction and offer management](../../interaction/using/interaction-and-offer-management.md).

* **NmsOffer**: Diese Tabelle entspricht dem Schema **nms:offer** . Sie enthält die Definition der einzelnen Marketing-Angebote.
* **NmsPropositionRcp**: Diese Tabelle entspricht dem Schema **nms:propositionRcp** . Es enthält das kanalübergreifende Protokoll der Marketing-Vorschläge, die an jede Person gesendet werden. Der Datensatz wird erstellt, wenn ein Vorschlag vorbereitet oder effektiv an eine Person unterbreitet wird.
* **NmsOfferSpace**: Diese Tabelle entspricht dem Schema **nms:offerSpace** . Sie enthält die Definition der Orte, an denen Vorschläge unterbreitet werden.
* **NmsOfferContext**: Diese Tabelle entspricht dem Schema **nms:offerContext** . Sie enthält zusätzliche Kriterien zur Anwendbarkeit des Vorschlags sowie die Bestimmung der Formel zur Gewichtsberechnung.
* **NmsOfferView**: Diese Tabelle entspricht der **nms:offerView**. Sie enthält die Angebotsdarstellungen.
* **NmsOfferCategory**: Diese Tabelle entspricht der **nms:offerCategory**. Es enthält die Angebotskategorien.
* **NmsOfferEnv**: Diese Tabelle entspricht dem Wert **nms:offerEnv**. Es enthält die Angebotsumgebungen.

## Message-Center-Modul {#message-center-module}

Der folgende Tabellensatz ist mit dem Modul **Transaktionsnachrichten** (Message Center) verknüpft, das die Verwaltung von individuellen und eindeutigen Nachrichten ermöglicht, die an einen Benutzer gesendet und von Ereignissen generiert werden, die von Informationssystemen ausgelöst werden. Weiterführende Informationen dazu finden Sie im Abschnitt [Über Transaktionsnachrichten](../../message-center/using/about-transactional-messaging.md).

### NmsRtEvent {#NmsRtEvent}

![](assets/data-model_message-center_rt.png)

Diese Tabelle entspricht dem Schema **nms:rtEvent** . Es enthält eine Definition von Echtzeit-Ereignissen.

### NmsBatchEvent {#NmsBatchEvent}

![](assets/data-model_message-center_batch.png)

Diese Tabelle entspricht dem Schema **nms:batchEvent** . Sie enthält die Definition von Ereignissen nach Batch.

<!--## Microsites Module {#microsites-module}

This set of tables is linked to the **Web applications** functionality, which allows to create and publish dynamic and interactive web applications with data from the database and content adapted to the rights of the connected user. For more on this, see [About web applications](../../web/using/about-web-applications.md).

![](assets/data-model_microsites.png)

* **NmsTrackingUrl**: This table matches the **nms:trackingUrl** schema.

* **NmsPurl**: This table matches the **nms:purl** schema.-->

## NMAC-Modul {#nmac-module}

Dieser Tabellensatz ist mit dem **Mobile-App-Kanal** verknüpft, mit dem personalisierte Benachrichtigungen über Apps an iOS- und Android-Terminals gesendet werden können. Weiterführende Informationen dazu finden Sie unter [Über den Mobile-App-Kanal](../../delivery/using/about-mobile-app-channel.md).

* **NmsMobileApp**: Diese Tabelle entspricht dem Schema **nms:mobileApp** . Sie enthält die in Adobe Campaign definierten Mobile Apps.
* **NmsAppSubscription**: Diese Tabelle entspricht dem Schema **nms:appSubscription** . Es enthält die Abonnenteninformationen zu einer oder mehreren Anwendungen.
* **NmsAppSubscriptionRcp**: Diese Tabelle entspricht dem Schema **nms:appSubscriptionRcp** . Dadurch können Sie Besucher, die sich für eine Anwendung angemeldet haben, mit der Empfängertabelle verknüpfen.
* **NmsExcludeLogAppSubRcp**: Diese Tabelle entspricht dem Schema **nms:excludeLogAppSubRcp** .
* **NmsTrackingLogAppSubRcp**: Diese Tabelle entspricht dem Schema **nms:trackingLogAppSubRcp** .
* **NmsBroadLogAppSubRcp**: Diese Tabelle entspricht dem Schema **nms:broadLogAppSubRcp** .

## Social Marketing-Modul {#social-marketing-module}

Diese Tabellen sind mit dem Modul **Social Networks verwalten** verknüpft, das die Interaktion mit Kunden und Interessenten über Facebook und X (ehemals Twitter) ermöglicht. Weiterführende Informationen dazu finden Sie im Abschnitt [Über Social Marketing](../../social/using/about-social-marketing.md).

![](assets/data-model_social.png)

* **NmsVisitor**: Diese Tabelle entspricht dem Schema **nms:visitor** . Es enthält Informationen zu Besuchern.
* **NmsVisitorSub**: Diese Tabelle entspricht dem Schema **nms:visitorSub** . Dadurch können Sie einen Besucher mit den Diensten verknüpfen, die er abonniert hat (X oder Facebook).
* **NmsFriendShipRel**: Diese Tabelle entspricht dem Schema **nms:friendlyRel** . Dadurch können Sie Besucher im Rahmen des Facebook-Dienstes mit ihren Freunden verknüpfen.
* **NmsVisitorInterestRel**: Diese Tabelle entspricht dem Schema **nms:visitorInterestRel** . Dadurch können Sie Besucher und deren Interessen miteinander verknüpfen.
* **NmsInterest**: Diese Tabelle entspricht dem Schema **nms:interest** . Es enthält die Liste der Interessen für jeden Besucher.
