---
product: campaign
title: Beschreibung des Adobe Campaign Classic-Datenmodells
description: In diesem Dokument wird das Adobe Campaign-Datenmodell beschrieben.
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: fc0fd23c-f9ea-4e30-b47b-a84143d882ca
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '2379'
ht-degree: 4%

---

# Beschreibung des Campaign-Datenmodells{#data-model-description}

![](../../assets/v7-only.svg)

Adobe Campaign enthält ein vordefiniertes Datenmodell. Dieser Abschnitt enthält einige Details zu den integrierten Tabellen des Adobe Campaign-Datenmodells und deren Interaktion.

Um Beschreibungen der einzelnen Tabellen aufzurufen, navigieren Sie zu **[!UICONTROL &quot;Admin&quot; > &quot;Konfiguration&quot; > &quot;Datenschemata&quot;]**, wählen Sie eine Ressource aus der Liste und klicken Sie auf die Registerkarte **[!UICONTROL Dokumentation]**.

![](assets/data-model_documentation-tab.png)

>[!NOTE]
>
>Die physische und logische Struktur der in der Anwendung übertragenen Daten wird in XML beschrieben. Sie folgt einer Adobe Campaign-spezifischen Grammatik namens „Schema“. Weitere Informationen zu Adobe Campaign-Schemata finden Sie im Abschnitt [diesem Abschnitt](../../configuration/using/about-schema-reference.md).

## Beschreibung der wichtigsten Tabellen {#description-main-tables}

Adobe Campaign stützt sich auf eine relationale Datenbank mit Tabellen, die miteinander verknüpft sind.

Das folgende Diagramm zeigt die Verknüpfungen zwischen den wichtigsten Geschäftstabellen des Adobe Campaign-Datenmodells mit den jeweiligen Hauptfeldern.

<!--![](assets/data-model_diagram.png)-->

![](assets/data-model_simplified-diagram.png)

Das vordefinierte Adobe Campaign-Datenmodell enthält die unten aufgeführten Haupttabellen.

### NmsRecipient {#NmsRecipient}

Diese Tabelle entspricht dem **nms:recipient** Schema.

Dies ist die Standardtabelle, die für die **Empfänger von Sendungen**. Sie enthält daher die für Sendungen über die verschiedenen Kanäle erforderlichen Informationen:

* sEmail: E-Mail-Adresse.
* iEmailFormat: bevorzugtes Format für E-Mails (1 für Text, 2 für HTML und 0, wenn nicht definiert).
* sAddress1, sAddress2, sAddress3, sAddress4, sZipCode, sCity werden zur Erstellung der Postanschrift verwendet (gemäß XPZ 10-011 AFNOR-Standard vom Mai 1997).
* sPhone, sMobilePhone, sFax enthalten jeweils die Telefon-, Mobiltelefon- und Faxnummern.
* iBlackList ist das Standard-Opt-out-Flag, das für die Profile verwendet wird (1 bedeutet &quot;unsubscribed&quot;, 0 andernfalls).

Das Feld iFolderId ist der Fremdschlüssel, der den Empfänger mit seinem Ausführungsordner verknüpft. Weitere Informationen hierzu finden Sie unter [XtkFolder](#XtkFolder).

Das Feld sCountryCode ist der ISO-Code 3166-1 Alpha 2 (2 Zeichen) des mit dem Empfänger verknüpften Landes. Dieses Feld ist tatsächlich ein Fremdschlüssel in der Länderreferenztabelle (NmsCountry), der die Länderbezeichnungen und andere Ländercodedaten enthält. Wenn das Land nicht ausgefüllt ist, wird der Wert &quot;XX&quot;gespeichert (und anstelle eines Null-ID-Datensatzes verwendet).

Weitere Informationen zur Empfängertabelle finden Sie in [diesem Abschnitt](../../configuration/using/about-data-model.md#default-recipient-table).

### NmsGroup {#NmsGroup}

Diese Tabelle entspricht dem **nms:group** Schema.

Damit können Sie **Statistische Empfängergruppen**. Es besteht eine Viele-zu-viele-Beziehung zwischen Empfängern und Gruppen. Beispielsweise kann ein Empfänger mehreren Gruppen angehören und eine Gruppe kann mehrere Empfänger enthalten. Gruppen können manuell, über einen Import oder über Versand-Targeting erstellt werden. Gruppen werden häufig als Versandziele verwendet. Es gibt einen eindeutigen Index im Feld, der den internen Namen der Gruppe sName darstellt. Die Gruppe ist mit einem Ordner verknüpft (der Schlüssel ist iFolderId. Weitere Informationen hierzu finden Sie unter [XtkFolder](#XtkFolder)).

### NmsRcpGrpRel {#NmsRcpGrpRel}

Die Beziehungstabelle NmsRcpGrpRel enthält nur die beiden Felder, die den Kennungen der mit iRecipientId und iGroupId verknüpften Tabellen entsprechen.

### NmsService {#NmsService}

Diese Tabelle entspricht dem **nms:service** Schema.

In Adobe Campaign können Sie Abonnements für Informationsdienste erstellen und verwalten (Themen). Die Tabelle NmsService speichert die Definition der Informationsdienste (Themen), die Sie Ihren Empfängern anbieten, sich für einen Newsletter anzumelden (z. B. einen Newsletter).

Dienste sind Entitäten, die Gruppen ähnlich sind (statische Empfängergruppierungen), mit dem Unterschied, dass sie mehr Informationen verbreiten und eine einfache Verwaltung von An- und Abmeldungen über Formulare ermöglichen.

Es gibt einen eindeutigen Index im Feld, der den internen Namen des sName-Dienstes darstellt. Der Dienst ist mit einem Ordner verknüpft (der Schlüssel ist iFolderId. Weitere Informationen hierzu finden Sie unter [XtkFolder](#XtkFolder)). Schließlich gibt das Feld iType den Versandkanal dieses Dienstes an (0 für E-Mail, 1 für SMS, 2 für Telefon, 3 für Briefpost und 4 für Fax).

### NmsSubscription {#NmsSubscription}

Diese Tabelle entspricht dem **nms:subscription** Schema.

Damit können Sie Empfängeranmeldungen für Informationsdienste verwalten.

### NmsSubHisto {#NmsSubHisto}

Diese Tabelle entspricht dem **nms:subHisto** Schema.

Wenn die Abonnements über Webformulare oder die Benutzeroberfläche der Anwendung verwaltet werden, werden alle Anmeldungen und Abmeldungen in der Tabelle NmsSubHisto verzeichnet. Das Feld iAction gibt die Aktion (0 für die Abmeldung und 1 für das Abonnement) an, die am im Feld tsDate gespeicherten Datum ausgeführt wird.

### NmsDelivery {#NmsDelivery}

Diese Tabelle entspricht dem **nms:delivery** Schema.

Jeder Datensatz in dieser Tabelle stellt eine **Versandaktion** oder **Versandvorlage**. Er enthält alle für die Durchführung des Versands erforderlichen Parameter (Zielgruppe, Inhalt usw.). Versandlogs (broadcast) (NmsBroadLog) und zugehörige Tracking-URLs (NmsTrackingUrl) werden während der Analysephase erstellt (weitere Informationen zu beiden Tabellen finden Sie unten).

Es gibt einen eindeutigen Index im Feld, der den internen Namen des Versands oder Szenarios sInternalName darstellt. Der Versand ist mit einem Ausführungsordner verknüpft (der Fremdschlüssel ist iFolderProcessId. Weitere Informationen hierzu finden Sie unter [XtkFolder](#XtkFolder)).

### XtkFolder {#XtkFolder}

Enthält **alle Ordner in der Struktur** sichtbar im **Navigation** Registerkarte der Konsole.

Die Ordner werden eingegeben: Der Wert des Felds sModel gibt den Datentyp an, der im Ordner enthalten sein kann. Dieses Feld ermöglicht der Clientkonsole auch die korrekte Anzeige der Daten mit den entsprechenden Formularen. Die möglichen Werte für dieses Feld werden im Navigationsbaum definiert.

Die Struktur wird von den Feldern iParentId und iChildCount verwaltet. Das Feld sFullName gibt den vollständigen Pfad des Ordners im Baum an. Schließlich gibt es einen eindeutigen Index im Feld, der den internen Namen des Ordners sName darstellt.

## Versand und Tracking {#delivery-and-tracking}

Dieser Tabellensatz ist mit der Variablen **Versand** -Modul, mit dem Sendungen und etwaige Probleme beim Nachrichtenversand überwacht werden können. Weitere Informationen hierzu finden Sie unter [Sendungen beobachten](../../delivery/using/about-delivery-monitoring.md). Weitere Informationen zum Tracking finden Sie unter [Nachrichten tracken](../../delivery/using/about-message-tracking.md).

![](assets/data-model_delivery.png)

**NmsBroadLogMsg**: Diese Tabelle entspricht dem **nms:broadLogMsg** Schema. Dies ist eine Erweiterung der Versandlog-Tabelle.

## Kampagnenverwaltung {#campaign-management}

Dieser Tabellensatz ist mit der Variablen **Marketing-Kampagnen** ermöglicht die Definition, Optimierung, Ausführung und Analyse von Kommunikations- und Marketingkampagnen. Weitere Informationen hierzu finden Sie unter [Über Marketingkampagnen](../../campaign/using/designing-marketing-campaigns.md).

![](assets/data-model_campaign.png)

* **NmsOperation**: Diese Tabelle entspricht dem **nms:operation** Schema. Sie enthält die Daten von Marketing-Kampagnen.
* **NmsDeliveryOutline**: Diese Tabelle entspricht dem **nms:deliveryOutline** Schema. Sie enthält die erweiterten Eigenschaften des Versands (Versandentwurf).
* **NmsDlvOutlineItem**: Diese Tabelle entspricht dem **nms:dlvOutlineItem** Schema. Sie enthält die Artikel eines Versandentwurfs.
* **NmsDeliveryCustomization**: Diese Tabelle entspricht dem **nms:deliveryCustomization** Schema. Sie enthält die Personalisierungsfelder eines Versands.
* **NmsBudget**: Diese Tabelle entspricht dem **nms:budget** Schema. Sie enthält Daten aus einem Budget einer Kampagne, eines Plans, eines Programms, einer Aufgabe und/oder Sendungen.
* **NmsDocument**: Diese Tabelle entspricht dem **nms:document** Schema. Es enthält die Marketing-Dokumente der Kampagne in Form von Dateien (Bilder, Excel- oder Wortdateien usw.)
* **XtkWorkflow**: Diese Tabelle entspricht dem **xtk:workflow** Schema. Sie enthält Kampagnen-Targeting.
* **NmsTask**: Diese Tabelle entspricht dem **nms:task** Schema. Es enthält die Definition einer Marketing-Aufgabe.
* **NmsAsset**: Diese Tabelle entspricht dem **nms:asset** Schema. Sie enthält die Definition einer Marketing-Ressource.

## Kommunikationskonsistenz {#communication-consistency}

Dieser Tabellensatz ist mit der Variablen **Kampagnenoptimierung** -Modul, das die Kontrolle, Filterung und Überwachung des Versands von Sendungen ermöglicht. Weitere Informationen hierzu finden Sie unter [Über Kampagnentypologien](../../campaign-opt/using/about-campaign-typologies.md).

![](assets/data-model_typology.png)

* **NmsTypologyRule**: Diese Tabelle entspricht dem **nms:typologyRule** Schema. Sie enthält die Regeln, die je nach Typologie für Sendungen gelten.
* **NmsTypology**: Diese Tabelle entspricht dem **nms:typology** Schema. Sie enthält die Regeln, die auf Sendungen angewendet werden, die der Typologie entsprechen.
* **NmsTypologyRuleRel**: Diese Tabelle entspricht dem **nms:typologyRuleRel** Schema. Es enthält die Beziehungen zwischen Typologien und deren Regeln.
* **NmsVolumeLine**: Diese Tabelle entspricht dem **nms:VolumeLine** Schema. Sie enthält die Verfügbarkeitszeilen der Kapazitätsregeln.
* **NmsVolumeConsumed**: Diese Tabelle entspricht dem **nms:volumenConsumed** Schema. Sie enthält alle Verbrauchszeilen der Kapazitätsregeln.

## Reaktionsverwaltung {#response-management}

Dieser Tabellensatz ist mit der Variablen **Response Manager** -Modul, das die Messung des Erfolgs und der Rentabilität von Marketingkampagnen oder Angebotsvorschlägen für alle Kommunikationskanäle ermöglicht. Weitere Informationen hierzu finden Sie unter [Über die Reaktionsverwaltung](../../response/using/about-response-manager.md).

![](assets/data-model_response.png)

### NmsRemaHypothesis {#NmsRemaHypothesis}

Diese Tabelle entspricht dem **nms:remaHypothesis** Schema. Sie enthält die Definition der Messhypothese.

Diese Tabelle enthält wichtige in XML gespeicherte Informationen, darunter:

**Ausführungskontext (in XML gespeicherte Informationen)**

Der Ausführungskontext füllt die Tabellen und Felder aus, die bei der Berechnung der Messung berücksichtigt werden sollen:
* Das Speicherschema des Reaktionslog-Speichers nms:remaMatchRcp.
* Das Transaktionstabelle-Schema (z. B. Käufe).
* Das Abfrageschema, mit dem Sie die Starttabelle der Hypothesenbedingungen definieren können.
* Die Relationen zu den Individuen, die die Identifizierung des Kontakts auf der Basis des Abfrageschemas ermöglichen.
* Das Transaktionsdatum. Dieses Feld ist nicht zwingend erforderlich. Es wird jedoch empfohlen, den Berechnungsrahmen einzuschränken.
* Transaktionsbetrag: Es handelt sich um ein optionales Feld für die automatische Berechnung von Umsatzindikatoren.

**Perimeter (in XML gespeicherte Informationen)**

Der Perimeter der Hypothese besteht aus der Filterung der Hypothese anhand der Tabelle des Abfrageschemas.

**Hypothesenüberlastungsskript (in XML gespeicherte Informationen)**

Das Hypothesenüberlastungsskript ist ein JavaScript-Code, mit dem Sie den Inhalt der Hypothese während der Ausführung überschreiben können.

**Messindikatoren**

Die folgenden Indikatoren werden während der Ausführung der Hypothese automatisch aktualisiert:

* Anzahl der Reaktionen: **iTransaction**. Anzahl der Zeilen in der Tabelle der Reaktionslogs.
* Anzahl Kontakte: **iContactReact**. Bestimmte Anzahl von Zielkontakten in der Hypothese.
* Kontrollgruppenanzahl: **iProofReact**. Bestimmte Anzahl von Zielgruppenkontakten in der Hypothese.
* Reaktionsrate Kontakte: **dContactReactRate**. Reaktionsrate der in der Hypothese enthaltenen Kontakte.
* Reaktionsrate der Kontrollgruppe: **dProofReactRate**. Reaktionsrate der Hypothesenkontrollgruppe.
* Gesamtumsatz Kontakte: **dContactReactTotalAmount**. Gesamtumsatz der Kontakte in der Hypothese.
* Durchschnittlicher Umsatz Kontrollgruppe: **dContactReactAvgAmount**. Durchschnittlicher Umsatz der Zielgruppenkontakte in der Hypothese.
* Gesamtumsatz der Kontrollgruppe: **dProofReactTotalAmount**. Gesamtumsatz der in der Hypothese bestimmten Kontrollgruppe.
* Durchschnittlicher Umsatz Kontrollgruppe: **dProofReactAvgAmount**. Durchschnittlicher Umsatz der Hypothesenkontrollgruppe.
* Gesamtspanne Kontakte: **dContactReactTotalMargin**. Gesamtspanne der in der Hypothese bestimmten Kontakte.
* Durchschnittliche Spanne Kontakte: **dContactReactAvgMargin**. Durchschnittliche Spanne Kontakte, die in der Hypothese berücksichtigt werden.
* Gesamtspanne der Kontrollgruppe: **dProofReactTotalMargin**. Gesamtspanne der in der Hypothese enthaltenen Kontrollgruppe.
* Durchschnittliche Spanne der Kontrollgruppe: **dProofReactAvgMargin**. Durchschnittliche Spanne der in der Hypothese enthaltenen Kontrollgruppe.
* Zusätzliche Einnahmen: **dAdditionnalAmount**. (Durchschnittlicher Umsatz der Kontakte - Durchschnittlicher Umsatz der Individuen in der Kontrollgruppe) * Anzahl Kontakte.
* Zusätzliche Spanne: **dAdditionnalMargin**. (Durchschnittliche Spanne der Kontakte - Durchschnittliche Spanne der Individuen in der Kontrollgruppe) / Anzahl Kontakte.
* Durchschnittliche Kosten pro Kontakt (SQL-Ausdruck). Berechnete Kosten des Versands / Anzahl Kontakte.
* ROI (SQL-Ausdruck). Berechnete Kosten des Versands / Gesamtspanne der Kontakte.
* Effektiver ROI (SQL-Ausdruck). Berechnete Kosten des Versands / Zusätzliche Spanne.
* Signifikanz: **Signifikanz** (SQL-Ausdruck). Enthält Werte von 0 bis 3 in Abhängigkeit von der Signifikanz der Kampagne.

### NmsRemaMatchRcp {#NmsRemaMatchRcp}

Diese Tabelle entspricht dem **nms:remaMatchRcp** Schema.

Es enthält einen Datensatz, der die Reaktion einer Person auf eine bestimmte Hypothese darstellt. Diese Datensätze wurden während der Ausführung der Hypothese erstellt.

## Simulation und Versand {#simulation-and-delivery}

Dieser Tabellensatz ist mit der Variablen **Simulation** -Modul, mit dem die Verteilung von Angeboten aus einer Kategorie oder einer Umgebung getestet werden kann, bevor der Vorschlag an Empfänger gesendet wird. Weitere Informationen hierzu finden Sie unter [Über die Angebotssimulation](../../interaction/using/about-offers-simulation.md).

![](assets/data-model_simulation.png)

* **NmsSimulation**: Diese Tabelle entspricht dem **nms:simulation** Schema. Er stellt eine Simulation für eine Reihe von Sendungen oder Angeboten für eine bestimmte Population dar.
* **NmsDlvSimulationRel**: Diese Tabelle entspricht dem **nms:dlvSimulationRel** Schema. Er enthält die Liste der in der Simulation berücksichtigten Sendungen. Der Perimeter der Simulation wird in XML gespeichert.
* **NmsOfferSimulationRel**: Diese Tabelle entspricht dem **nms:offerSimulationRel** Schema. Damit können Sie eine Simulation mit einem Angebot verknüpfen.

## Interaktionsmodul {#interaction-module}

Dieser Tabellensatz ist mit der Variablen **Interaction** -Modul, das es ermöglicht, während einer Interaktion mit einem bestimmten Kontakt in Echtzeit zu reagieren, indem es ihn zu einem oder mehreren angepassten Angeboten macht. Weitere Informationen hierzu finden Sie unter [Interaction- und Angebotsverwaltung](../../interaction/using/interaction-and-offer-management.md).

* **NmsOffer**: Diese Tabelle entspricht dem **nms:offer** Schema. Sie enthält die Definition der einzelnen Marketing-Angebote.
* **NmsPropositionRcp**: Diese Tabelle entspricht dem **nms:propositionRcp** Schema. Es enthält das kanalübergreifende Protokoll der Marketing-Vorschläge, die an jede Person gesendet werden. Der Datensatz wird erstellt, wenn ein Vorschlag vorbereitet oder effektiv an eine Person unterbreitet wird.
* **NmsOfferSpace**: Diese Tabelle entspricht dem **nms:offerSpace** Schema. Sie enthält die Definition der Orte, an denen Vorschläge unterbreitet werden.
* **NmsOfferContext**: Diese Tabelle entspricht dem **nms:offerContext** Schema. Sie enthält zusätzliche Kriterien zur Anwendbarkeit des Vorschlags sowie die Bestimmung der Formel zur Gewichtsberechnung.
* **NmsOfferView**: Diese Tabelle entspricht dem **nms:offerView**. Sie enthält die Angebotsdarstellungen.
* **NmsOfferCategory**: Diese Tabelle entspricht dem **nms:offerCategory**. Es enthält die Angebotskategorien.
* **NmsOfferEnv**: Diese Tabelle entspricht dem **nms:offerEnv**. Es enthält die Angebotsumgebungen.

## Message-Center-Modul {#message-center-module}

Die folgenden Tabellen sind mit dem **Transaktionsnachrichten** (Message Center)-Modul, das die Verwaltung von individuellen und eindeutigen Nachrichten ermöglicht, die an einen Benutzer gesendet und von Ereignissen generiert werden, die von Informationssystemen ausgelöst werden. Weitere Informationen hierzu finden Sie unter [Über Transaktionsnachrichten](../../message-center/using/about-transactional-messaging.md).

### NmsRtEvent {#NmsRtEvent}

![](assets/data-model_message-center_rt.png)

Diese Tabelle entspricht dem **nms:rtEvent** Schema. Es enthält eine Definition von Echtzeit-Ereignissen.

### NmsBatchEvent {#NmsBatchEvent}

![](assets/data-model_message-center_batch.png)

Diese Tabelle entspricht dem **nms:batchEvent** Schema. Sie enthält die Definition von Ereignissen nach Batch.

<!--## Microsites Module {#microsites-module}

This set of tables is linked to the **Web applications** functionality, which allows to create and publish dynamic and interactive web applications with data from the database and content adapted to the rights of the connected user. For more on this, see [About web applications](../../web/using/about-web-applications.md).

![](assets/data-model_microsites.png)

* **NmsTrackingUrl**: This table matches the **nms:trackingUrl** schema.

* **NmsPurl**: This table matches the **nms:purl** schema.-->

## NMAC-Modul {#nmac-module}

Dieser Tabellensatz ist mit der Variablen **Mobile App Channel**, mit dem über Apps personalisierte Benachrichtigungen an iOS- und Android-Terminals gesendet werden können. Weitere Informationen hierzu finden Sie unter [Über den Mobile-App-Kanal](../../delivery/using/about-mobile-app-channel.md).

* **NmsMobileApp**: Diese Tabelle entspricht dem **nms:mobileApp** Schema. Sie enthält die in Adobe Campaign definierten Mobile Apps.
* **NmsAppSubscription**: Diese Tabelle entspricht dem **nms:appSubscription** Schema. Es enthält die Abonnenteninformationen zu einer oder mehreren Anwendungen.
* **NmsAppSubscriptionRcp**: Diese Tabelle entspricht dem **nms:appSubscriptionRcp** Schema. Dadurch können Sie Besucher, die sich für eine Anwendung angemeldet haben, mit der Empfängertabelle verknüpfen.
* **NmsExcludeLogAppSubRcp**: Diese Tabelle entspricht dem **nms:excludeLogAppSubRcp** Schema.
* **NmsTrackingLogAppSubRcp**: Diese Tabelle entspricht dem **nms:trackingLogAppSubRcp** Schema.
* **NmsBroadLogAppSubRcp**: Diese Tabelle entspricht dem **nms:broadLogAppSubRcp** Schema.

## Social Marketing-Modul {#social-marketing-module}

Dieser Tabellensatz ist mit der Variablen **Verwaltung sozialer Netzwerke** -Modul, das die Interaktion mit Kunden und Interessenten über Facebook und Twitter ermöglicht. Weitere Informationen hierzu finden Sie unter [Über Social Marketing](../../social/using/about-social-marketing.md).

![](assets/data-model_social.png)

* **NmsVisitor**: Diese Tabelle entspricht dem **nms:visitor** Schema. Es enthält Informationen zu Besuchern.
* **NmsVisitorSub**: Diese Tabelle entspricht dem **nms:visitorSub** Schema. Dadurch können Sie einen Besucher mit den Diensten verknüpfen, die er abonniert hat (Twitter oder Facebook).
* **NmsFriendShipRel**: Diese Tabelle entspricht dem **nms:friendlyRel** Schema. Dadurch können Sie Besucher im Rahmen des Facebook-Dienstes mit ihren Freunden verknüpfen.
* **NmsVisitorInterestRel**: Diese Tabelle entspricht dem **nms:visitorInterestRel** Schema. Dadurch können Sie Besucher und deren Interessen miteinander verknüpfen.
* **NmsInterest**: Diese Tabelle entspricht dem **nms:interest** Schema. Es enthält die Liste der Interessen für jeden Besucher.
