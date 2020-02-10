---
title: Integration über Workflows
seo-title: Integration über Workflows
description: Integration über Workflows
seo-description: null
page-status-flag: never-activated
uuid: 57c4d4e0-6594-46f0-b9ce-2c689fb2eaa2
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: delivering-an-offer
discoiquuid: 6e27caea-1f1a-457d-bdec-1f93a12b01cf
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 67dce820b7a90163032ee72263a9dd23b521ea69

---


# Integration über Workflows{#integrating-an-offer-via-a-workflow}

Neben der eigentlichen Versand-Aktivität bieten auch diverse andere Workflow-Aktivitäten die Möglichkeit, Angebotsunterbreitungen zu konfigurieren:

* Versandentwurf
* Anreicherung
* Angebotsmodul
* Angebote pro Segment

## Versandentwurf {#delivery-outline}

Die in Kampagnen-Workflows zur Verfügung stehende Versandentwurfsaktivität erlaubt es, Angebote zu unterbreiten, die in einem Versandentwurf der aktuellen Kampagne referenziert wurden.

1. Platzieren Sie hierfür im Workflow die Versandentwurfsaktivität vor einer Versandaktivität.
1. Geben Sie in der Versandentwurfsaktivität den gewünschten Entwurf an.

   Weiterführende Informationen zu Versandentwürfen können Sie dem [Campaign](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline)-Handbuch entnehmen.

1. Füllen Sie die verfügbaren Felder Ihrem Versand entsprechend aus.
1. Sie haben zwei Möglichkeiten:

   * Wenn Sie die Angebotsmaschine aufrufen möchten, markieren Sie das **[!UICONTROL Restrict the number of propositions selected]** Kästchen. Geben Sie den Angebotsbereich und die Anzahl der Vorschläge an, die in der Bereitstellung präsentiert werden sollen.

      Gewichtung und Eignungsregeln der Angebote werden vom Angebotsmodul berücksichtigt.

   * Versand ohne Abfrage an das Angebotsmodul: Alle im Versandentwurf enthaltenen Angebote werden unterbreitet.
   >[!NOTE]
   >
   >Die Vorschau berücksichtigt die im Versand konfigurierte Anzahl an Angeboten. Bei Ausführung des Workflows hingegen wird die im Versandentwurf konfigurierte Anzahl verwendet.

   ![](assets/int_compo_offre_wf1.png)

## Anreicherung {#enrichment}

Die Anreicherungsaktivität ermöglicht das Hinzufügen von Angeboten oder von Relationen zu Angeboten für Versandempfänger.

>[!NOTE]
>
>Weiterführende Informationen zur Anreicherung finden Sie im [Workflow](../../workflow/using/enrichment.md)-Handbuch.

Sie können beispielsweise aus einer Abfrage stammende Empfängerdaten vor Durchführung eines Versands anreichern.

![](assets/int_enrichment_offer1.png)

Zwei Methoden ermöglichen in diesem Fall die Auswahl der Angebotsvorschläge:

* Konfiguration eines Angebots oder einer Abfrage des Angebotsmoduls;
* Referenzierung einer Relation zu einem Angebot.

### Angebot oder Angebotsmodul-Abfrage konfigurieren {#specifying-an-offer-or-a-call-to-the-offer-engine}

After configuring your query (refer to the [Workflows guide](../../workflow/using/query.md)):

1. Platzieren Sie im Anschluss an die Abfrage eine Anreicherungsaktivität und öffnen Sie sie zur weiteren Bearbeitung.
1. Wählen Sie auf der **[!UICONTROL Enrichment]** Registerkarte **[!UICONTROL Add data]**.
1. Wählen Sie **[!UICONTROL An offer proposition]** in den hinzuzufügenden Datentypen aus.

   ![](assets/int_enrichment_offer2.png)

1. Geben Sie eine Kennung und einen Titel für den hinzuzufügenden Vorschlag an.
1. Konfigurieren Sie die Angebotsauswahl. Zwei Optionen stehen zur Auswahl:

   * **[!UICONTROL Search for the best offer in a category]** : Aktivieren Sie diese Option und geben Sie die Parameter für den Aufruf der Angebotsmaschine an (Angebotsumfang, Kategorie oder Thema(e), Kontaktdatum, Anzahl der zu pflegenden Angebote). Die Engine berechnet automatisch das Angebot/die Angebote, die entsprechend diesen Parametern hinzugefügt werden sollen. Es wird empfohlen, das Feld **[!UICONTROL Category]** oder das **[!UICONTROL Theme]** Feld gleichzeitig auszufüllen.

      ![](assets/int_enrichment_offer3.png)

   * **[!UICONTROL A predefined offer]** : Aktivieren Sie diese Option und geben Sie einen Angebotsbereich, ein bestimmtes Angebot und ein Kontaktzeitpunkt an, um das Angebot, das Sie hinzufügen möchten, direkt zu konfigurieren, ohne die Angebotsengine aufzurufen.

      ![](assets/int_enrichment_offer4.png)

1. Konfigurieren Sie dann eine Auslieferungsaktivität, die Ihrem ausgewählten Kanal entspricht. Weitere Informationen finden Sie im Abschnitt zum [Einfügen eines Angebotsprojekts in eine Bereitstellung](../../interaction/using/integrating-an-offer-via-the-wizard.md#inserting-an-offer-proposition-into-a-delivery) .

   >[!NOTE]
   >
   >Die Anzahl an für die Vorschau verfügbaren Vorschlägen hängt von der Konfiguration der Anreicherung und nicht von im Versand konfigurierten Parametern ab.

### Relation zu einem Angebot referenzieren {#referencing-a-link-to-an-offer}

In einer Anreicherungsaktivität besteht darüber hinaus die Möglichkeit, eine Relation zu einem Angebot zu referenzieren.

Gehen Sie dazu wie folgt vor:

1. Wählen Sie **[!UICONTROL Add data]** auf der **[!UICONTROL Enrichment]** Registerkarte der Aktivität aus.
1. In the window where you choose the type of data to add, select **[!UICONTROL A link]**.
1. Definieren Sie nun den Relationstyp und das Ziel der Relation. Im vorliegenden Beispiel handelt es sich beim Ziel um das Angebotsschema.

   ![](assets/int_enrichment_link1.png)

1. Definieren Sie die Art der Relation zwischen den Daten der Eingangstabelle der Anreicherungsaktivität (hier die Empfängertabelle) und der Angebotstabelle. Sie können beispielsweise einem Empfänger einen Angebotscode zuordnen.

   ![](assets/int_enrichment_link2.png)

1. Konfigurieren Sie dann eine Auslieferungsaktivität, die Ihrem ausgewählten Kanal entspricht. Weitere Informationen finden Sie im Abschnitt zum [Einfügen eines Angebotsprojekts in eine Bereitstellung](../../interaction/using/integrating-an-offer-via-the-wizard.md#inserting-an-offer-proposition-into-a-delivery) .

   >[!NOTE]
   >
   >Die Anzahl an für die Vorschau verfügbaren Vorschlägen hängt von den im Versand konfigurierten Parametern ab.

### Rang und Gewichtung von Angeboten speichern {#storing-offer-rankings-and-weights}

Standardmäßig werden Rang und Gewichtung bei Verwendung der Aktivität **Anreicherung** nicht in der Vorschlagstabelle gespeichert.

>[!NOTE]
>
>Remember: The **[!UICONTROL Offer engine]** activity does store this information by default.

Gehen Sie wie folgt vor, wenn Sie diese Informationen dennoch speichern möchten:

1. Erstellen Sie einen Aufruf an die Angebotsmaschine in einer Anreicherungsaktivität, die nach einer Abfrage und vor einer Bereitstellungsaktivität platziert wird. Weitere Informationen finden Sie im Abschnitt [Angeben eines Angebots oder Aufrufen der Angebotsengine](../../interaction/using/integrating-an-offer-via-a-workflow.md#specifying-an-offer-or-a-call-to-the-offer-engine) .
1. Wählen Sie im Hauptfenster der Aktivität die Option **[!UICONTROL Edit additional data...]**.

   ![](assets/ita_enrichment_rankweight_1.png)

1. Add the **[!UICONTROL @rank]** columns for the ranking and **[!UICONTROL @weight]** for the offer weight.

   ![](assets/ita_enrichment_rankweight_2.png)

1. Bestätigen Sie Ihre Wahl und speichern Sie den Workflow.

Die Lieferung speichert automatisch das Ranking und Gewicht der Angebote. Diese Informationen werden auf der **[!UICONTROL Offers]** Registerkarte &quot;Bereitstellung&quot;angezeigt.

## Angebotsmodul {#offer-engine}

The **[!UICONTROL Offer engine]** activity also lets you specify a call to the offer engine prior to the delivery.

Das Prinzip dieser Aktivität entspricht dem der Anreicherung. Auch hier werden die Daten der Eingangspopulation mit einem vom Modul berechneten Angebot angereichert, bevor die eigentliche Versandaktivität startet.

![](assets/int_offerengine_activity2.png)

After configuring your query (refer to the [Workflows guide](../../workflow/using/query.md)):

1. Add and open an **[!UICONTROL Offer engine]** activity.
1. Konfigurieren Sie die verschiedenen Parameter der Abfrage des Angebotsmoduls (Platzierung, Kategorie oder Themen, Kontaktdatum, Anzahl beizubehaltender Angebote). Das Modul berechnet automatisch die den Parametern entsprechenden Angebote.

   >[!NOTE]
   >
   >Wenn Sie diese Aktivität nutzen, werden nur die im Versand verwendeten Vorschläge gespeichert.

   ![](assets/int_offerengine_activity1.png)

1. Konfigurieren Sie dann eine Auslieferungsaktivität, die Ihrem ausgewählten Kanal entspricht. Weitere Informationen finden Sie im Abschnitt zum [Einfügen eines Angebotsprojekts in eine Bereitstellung](../../interaction/using/integrating-an-offer-via-the-wizard.md#inserting-an-offer-proposition-into-a-delivery) .

## Angebote pro Segment {#offers-by-cell}

The **[!UICONTROL Offers by cell]** activity lets you distribute the inbound population (from a query for example) into several segments and to specify an offer to present for each of these segments.

Gehen Sie dazu wie folgt vor:

1. Add the **[!UICONTROL Offers by cell]** activity once you have specified the target population, then open it.
1. In the **[!UICONTROL General]** tab, select the offer space on which you want to present the offers.
1. In the **[!UICONTROL Cells]** tab, specify the different sub-sets using the **[!UICONTROL Add]** button:

   * Konfigurieren Sie anhand der verfügbaren Filter und Begrenzungen die Population des Segments.
   * Wählen Sie dann das Angebot aus, das Sie dem Segment unterbreiten möchten. Es stehen die Angebote zur Verfügung, die der Konfiguration der zuvor ausgewählten Platzierung entsprechen.

      ![](assets/int_offer_per_cell1.png)

1. Konfigurieren Sie dann eine Auslieferungsaktivität, die Ihrem ausgewählten Kanal entspricht. Weitere Informationen finden Sie im Abschnitt zum [Einfügen eines Angebotsprojekts in eine Bereitstellung](../../interaction/using/integrating-an-offer-via-the-wizard.md#inserting-an-offer-proposition-into-a-delivery) .

