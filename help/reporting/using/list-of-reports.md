---
product: campaign
title: Liste von Berichten
description: Liste von Berichten
badge: label="v7" type="Informative" tooltip="Gilt nur für Campaign Classic v7"
feature: Reporting, Monitoring
exl-id: c01f4850-ab17-44ac-a5e0-ff082ec206b3
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '1020'
ht-degree: 93%

---

# Liste von Berichten{#list-of-reports}



## Versandberichte {#reports-on-deliveries}

Die nativen Berichte von Adobe Campaign werden in der folgenden Tabelle aufgelistet.

Weitere Informationen zum Inhalt dieser Berichte erhalten Sie in diesem [Abschnitt](../../reporting/using/delivery-reports.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Titel und interner Name</strong><br /> </td> 
   <td> <strong>Beschreibung</strong><br /> </td> 
   <td> <strong>Schema</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Nutzer-Aktivitäten (recipientActivity)<br /> </td> 
   <td> Aufschlüsselung der Öffnungen, Klicks und Transaktionen der Nutzer nach Zeitspanne<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> Versanddurchsatz (throughput)<br /> </td> 
   <td> Grafiken zum Versanddurchsatz in Nachrichten/Stunde und Bits/Sekunde<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> Fehler und Bounces (errors)<br /> </td> 
   <td> Verteilung von unzustellbaren Nachrichten und Bounces nach Ursache und Domain<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> Trackingindikatoren (deliveryFeedback)<br /> </td> 
   <td> Zusammenfassung der Schlüsselindikatoren, die die Verfolgung des Empfängerverhaltens ermöglichen<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> Trackingindikatoren (mobileAppDeliveryFeedback)<br /> </td> 
   <td> Trackingindikatoren eines Mobile-App-Versands<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> Browser (browserStatistics)<br /> </td> 
   <td> Statistiken bezüglich der von den Empfängern, die in die Nachrichten geklickt haben, benutzten Browser<br /> </td> 
   <td> xtk:none<br /> </td> 
  </tr> 
  <tr> 
   <td> Teilen über soziale Netzwerke (deliveryForward)<br /> </td> 
   <td> Statistiken über Teilungen und Öffnungen<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> Klickposition (hoturls)<br /> </td> 
   <td> Zeigt den Nachrichteninhalt mit dem prozentualen Klickanteil für jeden Link<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> Hypothesenbericht (deliveryHypothesis)<br /> </td> 
   <td> Fasst die Berechnungen der Versandhypothesen zusammen<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> Versandstatistiken (statisticsPerDelivery)<br /> </td> 
   <td> Statistiken (verarbeitete Nachrichten, zugestellte Nachrichten, Hardbounces, Softbounces, Öffnungen, Klicks, Abmeldungen) nach E-Mail-Domain<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> Statistiken zu Teilungsaktivitäten (forwardActivities)<br /> </td> 
   <td> Zeitliche Entwicklung von Teilungen, Öffnungen und Anmeldungen<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> Trackingstatistiken (trackingStatistics)<br /> </td> 
   <td> Statistiken über Öffnungen, Klicks und Transaktionen über einen Zeitraum hinweg<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> Versandzusammenfassung (deliverySending)<br /> </td> 
   <td> Zusammenfassung der Versandindikatoren: Zielgruppe, Ausschlüsse und versandte Nachrichten<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> Versandzusammenfassung (deliveryStatistics)<br /> </td> 
   <td> Zusammenfassung der ausgewählten Sendungen: Zielgruppe, Ausschlüsse und versandte Nachrichten<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> Betriebssysteme (osStatistics)<br /> </td> 
   <td> Statistiken bezüglich der von den Empfängern, die in die Nachrichten geklickt haben, benutzten Betriebssysteme<br /> </td> 
   <td> xtk:none<br /> </td> 
  </tr> 
  <tr> 
   <td> Reaktionsrate (deliveryFeedbackSocial)<br /> </td> 
   <td> Feedback-Rate eines Versands und Feedback-Aufschlüsselung<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> URLs und Clickstreams (topUrlDelivery)<br /> </td> 
   <td> Reaktionsstärkste URLs und entsprechende Clickstreams<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Kampagnenberichte {#reports-on-campaigns}

Berichte über Kampagnen beziehen sich auf die Daten der Tabelle **nms:operation**.

Die nativen Berichte von Adobe Campaign werden in der folgenden Tabelle aufgelistet.

Weitere Informationen zum Inhalt dieser Berichte finden Sie in der Dokumentation zu [&#x200B; v8 &#x200B;](https://experienceleague.adobe.com/docs/campaign/campaign-v8/campaigns/campaigns.html?lang=de){target=_blank}.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Titel und interner Name</strong><br /> </td> 
   <td> <strong>Beschreibung</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Nutzer-Aktivitäten (operationRecipientActivity)<br /> </td> 
   <td> Aufschlüsselung der Öffnungen, Klicks und Transaktionen der Nutzer nach Zeitspanne; abhängig von Campaign<br /> </td> 
  </tr> 
  <tr> 
   <td> Versanddurchsatz (operationThroughput)<br /> </td> 
   <td> Grafiken zum Versanddurchsatz in Nachrichten/Stunde und Bits/Sekunde; abhängig von Campaign<br /> </td> 
  </tr> 
  <tr> 
   <td> Kampagnenausgaben (budgetOperationExpenses)<br /> </td> 
   <td> Detailanzeige der der Kampagne zugeordneten Ausgaben; abhängig von Campaign<br /> </td> 
  </tr> 
  <tr> 
   <td> Fehler und Bounces (operationErrors)<br /> </td> 
   <td> Verteilung von unzustellbaren Nachrichten und Bounces nach Ursache und Domain; abhängig von Campaign<br /> </td> 
  </tr> 
  <tr> 
   <td> Kostenzeilenanalyse (budgetExplorerOperation)<br /> </td> 
   <td> Deskriptive Kostenzeilenanalyse; abhängig von MRM<br /> </td> 
  </tr> 
  <tr> 
   <td> Trackingindikatoren (operationFeedback)<br /> </td> 
   <td> Zusammenfassung der wichtigsten Trackingindikatoren: Öffnungen, Klicks und Transaktionen; abhängig von Campaign<br /> </td> 
  </tr> 
  <tr> 
   <td> Teilen über soziale Netzwerke (operationForward)<br /> </td> 
   <td> Statistiken über Teilungen und Öffnungen; abhängig von Campaign<br /> </td> 
  </tr> 
  <tr> 
   <td> Hypothesenbericht (operationHypothesis)<br /> </td> 
   <td> Fasst die Berechnungen der Hypothesen über Versandkampagnen zusammen; abhängig von Campaign<br /> </td> 
  </tr> 
  <tr> 
   <td> Statistiken zu Teilungsaktivitäten (forwardActivityOpt)<br /> </td> 
   <td> Analyse von Teilungen, Öffnungen und Abonnements nach Zeiträumen; abhängig von Campaign<br /> </td> 
  </tr> 
  <tr> 
   <td> Versandzusammenfassung (operationStatistics)<br /> </td> 
   <td> Zusammenfassende Übersicht bezüglich der Kampagnensendungen: Zielgruppe, Ausschlüsse und versandte Nachrichten<br /> </td> 
  </tr> 
  <tr> 
   <td> URLs und Clickstreams (operationTopUrlDelivery)<br /> </td> 
   <td> Reaktionsstärkste URLs und entsprechende Clickstreams; abhängig von Campaign<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Dienstberichte {#reports-on-services}

Berichte über Services beziehen sich auf die Daten der Tabelle **nms:service**.

Die nativen Berichte von Adobe Campaign werden in der folgenden Tabelle aufgelistet.

Weitere Informationen zum Inhalt dieser Berichte erhalten Sie in den zugehörigen Handbüchern.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Titel und interner Name</strong><br /> </td> 
   <td> <strong>Beschreibung</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Fan-Akquise (socialAcquisitionsByWebapp)<br /> </td> 
   <td> Webanwendungen, über die Interessenten akquiriert wurden Hängt vom Social Marketing-Add-on ab.<br /> </td> 
  </tr> 
  <tr> 
   <td> Abonnement-Aufschlüsselung (mobileAppDistribution)<br /> </td> 
   <td> Aufschlüsselung der aktiven Abonnements pro Mobile App; abhängig vom Mobile-App-Kanal-Add-on<br /> </td> 
  </tr> 
  <tr> 
   <td> Abonnement-Verfolgung (subscriptionsProgress)<br /> </td> 
   <td> Entwicklung der Dienst-Anmeldungen<br /> </td> 
  </tr> 
  <tr> 
   <td> Reaktionsrate (socialReactionRate)<br /> </td> 
   <td> Reaktionsraten der letzten Sendungen Hängt vom Social Marketing-Add-on ab.<br /> </td> 
  </tr> 
  <tr> 
   <td> Reaktionsrate (mobileAppReactivityRate)<br /> </td> 
   <td> Reaktionsrate der letzten Sendungen; abhängig vom Mobile-App-Kanal-Add-on<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Budgetberichte {#budget-reports}

Die nativen Berichte von Adobe Campaign werden in der folgenden Tabelle aufgelistet.

Weitere Informationen zum Inhalt dieser Berichte finden Sie in der Dokumentation zu [&#x200B; v8 &#x200B;](https://experienceleague.adobe.com/docs/campaign/campaign-v8/campaigns/campaigns.html?lang=de){target=_blank}.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Titel und interner Name</strong><br /> </td> 
   <td> <strong>Beschreibung</strong><br /> </td> 
   <td> <strong>Schema</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Programmen zugeordnete Kosten (budgetProgramCost)<br /> </td> 
   <td> Aufschlüsselung der Programmkosten.<br /> </td> 
   <td> nms:program<br /> </td> 
  </tr> 
  <tr> 
   <td> Budget-Entwicklung (budgetEvolution)<br /> </td> 
   <td> Kostenentwicklung nach Verbindlichkeitsniveau<br /> </td> 
   <td> nms:budget<br /> </td> 
  </tr> 
  <tr> 
   <td> Kumulierte Entwicklung des Budgets (budgetCumulativeEvolution)<br /> </td> 
   <td> Entwicklung der kumulierten Budgetbeträge, verteilt nach Verbindlichkeitsniveau<br /> </td> 
   <td> nms:budget<br /> </td> 
  </tr> 
  <tr> 
   <td> Kostenzeilenanalyse (budgetExplorerBudget)<br /> </td> 
   <td> Deskriptive Kostenzeilenanalyse<br /> </td> 
   <td> nms:budget<br /> </td> 
  </tr> 
  <tr> 
   <td> Kostenzeilenanalyse (budgetExplorer)<br /> </td> 
   <td> Deskriptive Kostenzeilenanalyse<br /> </td> 
   <td> nms:costLine<br /> </td> 
  </tr> 
  <tr> 
   <td> Kostenzeilenanalyse (budgetExplorerPlan)<br /> </td> 
   <td> Deskriptive Kostenzeilenanalyse<br /> </td> 
   <td> nms:plan<br /> </td> 
  </tr> 
  <tr> 
   <td> Kostenzeilenanalyse (budgetExplorerProgram)<br /> </td> 
   <td> Deskriptive Kostenzeilenanalyse<br /> </td> 
   <td> nms:program<br /> </td> 
  </tr> 
  <tr> 
   <td> Budget-Zusammenfassung (budget)<br /> </td> 
   <td> Sofortübersicht der wichtigsten Kosten, Ausgabenkategorien und Budgets<br /> </td> 
   <td> nms:budget<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Simulationsberichte {#reports-on-simulations}

Berichte über Simulationen beziehen sich auf die Daten der Tabelle **nms:simulation**.

Die nativen Berichte von Adobe Campaign werden in der folgenden Tabelle aufgelistet.

Weitere Informationen zum Inhalt dieser Berichte erhalten Sie in den zugehörigen Handbüchern.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Titel und interner Name</strong><br /> </td> 
   <td> <strong>Beschreibung</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Detail der Simulationsausschlüsse (dlvSimuLossesDetail)<br /> </td> 
   <td> Detaillierte Tabelle aller Ausschlussgründe<br /> </td> 
  </tr> 
  <tr> 
   <td> Angebotsaufschlüsselung nach Rang (offerSimulationRanking)<br /> </td> 
   <td> Aufschlüsselung der simulierten Angebote nach Rang<br /> </td> 
  </tr> 
  <tr> 
   <td> Simulationszusammenfassung (dlvSimuLossesSummary)<br /> </td> 
   <td> Zusammenfassung Simulationsgesamtzahl und -ausschlüsse<br /> </td> 
  </tr> 
  <tr> 
   <td> Überschneidungsstatistiken (dlvSimuOverlapping)<br /> </td> 
   <td> Versandzielgruppenüberschneidungen<br /> </td> 
  </tr> 
  <tr> 
   <td> Zusammenfassung der simulationsbedingten Ausschlüsse (dlvSimuLossesSimu)<br /> </td> 
   <td> Tabelle der simulationsbedingten Ausschlüsse<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Berichte über Web-Anwendungen {#reports-on-web-applications}

Berichte über Web-Anwendungen beziehen sich auf die Daten der **nms:WebApp**-Tabelle.

Die nativen Berichte von Adobe Campaign werden in der folgenden Tabelle aufgelistet.

Weitere Informationen zum Inhalt dieser Berichte erhalten Sie in diesem [Abschnitt](../../web/using/about-web-applications.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Titel und interner Name</strong><br /> </td> 
   <td> <strong>Beschreibung</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Dokumentation (surveyDictionary)<br /> </td> 
   <td> Beschreibung der Umfragestruktur; abhängig vom Survey-Manager-Add-on<br /> </td> 
  </tr> 
  <tr> 
   <td> Allgemein (surveyProperties)<br /> </td> 
   <td> Eigenschaften der Umfrage<br /> </td> 
  </tr> 
  <tr> 
   <td> Aufschlüsselung der Antworten (surveyDistribution)<br /> </td> 
   <td> Aufschlüsselung der Umfrageantworten<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Andere Standardberichte {#other-ootb-reports}

Nachfolgende Berichte stehen ebenfalls nativ zur Verfügung. Weitere Informationen erhalten Sie im Handbuch der zugehörigen Anwendung.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Titel und interner Name</strong><br /> </td> 
   <td> <strong>Beschreibung</strong><br /> </td> 
   <td> <strong>Schema</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Angebotsanalyse (offerAnalysis)<br /> </td> 
   <td> Angebotsanalyse nach Datum und Kanal; abhängig vom Interaction-Add-on<br /> </td> 
   <td> nms:offer<br /> </td> 
  </tr> 
  <tr> 
   <td> Remarketing-Effizienz (remarketingEffect)<br /> </td> 
   <td> Messung der Remarketing-Effizienz<br /> </td> 
   <td> nms:webEvent<br /> </td> 
  </tr> 
  <tr> 
   <td> Verlauf der Akquise aus sozialen Netzwerken (socialVisitorStatistics)<br /> </td> 
   <td> Verlauf der Akquise aus X (ehemals Twitter) und Facebook, abhängig vom Social-Media-Marketing-Add-on.<br /> </td> 
   <td> nms:visitor<br /> </td> 
  </tr> 
  <tr> 
   <td> Verfolgung kürzlicher Vorschläge (recentPropositions)<br /> </td> 
   <td> Echtzeitverfolgung der Vorschläge<br /> </td> 
   <td> nms:propositionRcp<br /> </td> 
  </tr> 
 </tbody> 
</table>
