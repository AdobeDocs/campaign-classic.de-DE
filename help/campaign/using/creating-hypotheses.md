---
title: Hypothesenerstellung
seo-title: Hypothesenerstellung
description: Hypothesenerstellung
seo-description: null
page-status-flag: never-activated
uuid: 48b74772-473f-4fbc-a228-ce8e35a7b9ba
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: response-manager
discoiquuid: 0f73de0e-e589-4e39-9895-209dad75db75
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Hypothesenerstellung{#creating-hypotheses}

Es gibt folgende Möglichkeiten, Hypothesen einem Angebot oder einem Kampagnenversand zuzuordnen:

* Via the **[!UICONTROL Measurement hypotheses]** folder by creating a new hypothesis based on an existing template and linking it to an existing delivery.
* Über die Registerkarte **[!UICONTROL Edit]** > **[!UICONTROL Measurement]** in einer Kampagne.
* Via the **[!UICONTROL Measurement]** option of a delivery created from a campaign.

Hypothesen können erst berechnet werden, nachdem die Marketingkampagne gestartet und die Empfänger die Lieferung erhalten haben. Wenn die Hypothese auf einem Angebotsvorschlag beruht, muss diese zumindest vorgelegt werden und weiterhin aktiv sein. Angebots- und Lieferhypothesen werden über den **[!UICONTROL Measurement hypotheses]** Ordner erstellt und basieren auf einer Hypothese-Vorlage. Es ist jedoch möglich, eine Hypothese direkt in der Bereitstellung oder der Kampagne zu referenzieren, bevor die Kampagne beginnt. In diesem Fall werden die Hypothesen automatisch berechnet, sobald die Marketingkampagne gestartet wird, basierend auf den Ausführungseinstellungen (weitere Informationen dazu finden Sie unter [Hypothese-Vorlagenausführungseinstellungen](../../campaign/using/hypothesis-templates.md#hypothesis-template-execution-settings)).

## Erstellen einer Hypothese direkt in einem Versand {#creating-a-hypothesis-on-the-fly-on-a-delivery}

Um eine Hypothese für einen bestehenden Versand zu erstellen, gehen Sie wie folgt vor:

>[!NOTE]
>
>Dieser Vorgang kann nur für Sendungen durchgeführt werden, die sich in Bearbeitung befinden.

1. Wechseln Sie in der Struktur von Adobe Campaign zu **[!UICONTROL Campaign management > Measurement hypotheses]**.
1. Click the **[!UICONTROL New]** button or right-click on the list of hypotheses and select **[!UICONTROL New]** in the drop-down list.

   ![](assets/response_hypothesis_instance_creation_002.png)

1. In the hypothesis window, select a previously created template (refer to [Hypothesis templates](../../campaign/using/hypothesis-templates.md)).

   ![](assets/response_hypothesis_instance_creation_003.png)

   Der in der ausgewählten Vorlage festgelegte Hypothesenkontext wird im Fenster angezeigt.

   >[!NOTE]
   >
   >Auch die in dieser Etappe nicht sichtbaren Parameter, die in der Vorlage bestimmt wurden, werden von der Hypothese übernommen.

   ![](assets/response_hypothesis_instance_creation_004.png)

1. Wählen Sie den Versand aus, dem die Hypothese hinzugefügt werden soll.

   ![](assets/response_hypothesis_instance_creation_005.png)

1. Sie können Ihre Hypothese personalisieren, indem Sie die **[!UICONTROL General]**, **[!UICONTROL Transactions]** und **[!UICONTROL Scope]** Registerkarten bearbeiten. Weitere Informationen hierzu finden Sie unter [Erstellen eines Hypothese-Modells](../../campaign/using/hypothesis-templates.md#creating-a-hypothesis-model).
1. Start the hypothesis by clicking **[!UICONTROL Start]**.

   Daraufhin wird automatisch ein Workflow erzeugt, der die Berechnung der Hypothese durchführt. Sein Titel wird ebenfalls automatisch bestimmt, entsprechend der Konfiguration der Hypothese.

   >[!CAUTION]
   >
   >You can access this if you have checked the **[!UICONTROL Keep execution workflow]** box.\
   >Diese Option sollte nur zu Debugging-Zwecken bei fehlerhaften Hypothesenausführungen aktiviert werden. Die automatisch erstellten Arbeitsabläufe werden im Ordner **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Objects created automatically]** > **[!UICONTROL Campaign workflows]** im Adobe Campaign Explorer gespeichert.
   > 
   >Automatisch generierte Workflows sollten zudem nicht verändert werden. Jede dennoch vorgenommene Änderung wird nur für nachfolgende Berechnungen berücksichtigt.
   >
   >Denken Sie daran, den Workflow nach seiner Ausführung zu löschen, wenn Sie diese Option aktiviert haben.

   ![](assets/response_hypothesis_instance_creation_006.png)

   Nach Abschluss der Berechnung werden die Messindikatoren automatisch aktualisiert.

   ![](assets/response_hypothesis_instance_creation_007.png)

1. Ändern Sie bei Bedarf die Parameter und starten Sie die Hypothese erneut.

## Referenzieren einer Hypothese im Versand einer Kampagne {#referencing-a-hypothesis-in-a-campaign-delivery}

Sie haben die Möglichkeit, eine Hypothese in einer Marketingkampagne zu referenzieren, bevor diese gestartet wird. Die Hypothese wird in diesem Fall automatisch nach dem Versand gestartet, entsprechend der in der Hypothesenvorlage festgelegten Ausführungsparameter. Um eine Hypothese in einem Kampagnenversand zu erstellen, gehen Sie wie folgt vor:

1. Depending on your needs, you can create one or more **[!UICONTROL Delivery]** type templates, as described in [Creating a hypothesis model](../../campaign/using/hypothesis-templates.md#creating-a-hypothesis-model)
1. Erstellen Sie Ihre Marketingkampagne und die entsprechenden Zielgruppen-Workflows.
1. In the delivery window, click the **[!UICONTROL Delivery measurement]** icon.
1. Wählen Sie die Hypothesenvorlage aus. Die in der Vorlage konfigurierte Abfrage wird im Hypothesenfenster angezeigt.

   The hypothesis will be calculated automatically once the campaign is finished, based on the dates configured in the model (refer to [Hypothesis template execution settings](../../campaign/using/hypothesis-templates.md#hypothesis-template-execution-settings)).

   ![](assets/response_hypothesis_instance_creation_008.png)

## Referenzieren einer Hypothese in allen Sendungen einer Kampagne {#adding-a-default-hypothesis-to-deliveries-for-a-campaign}

Sie haben die Möglichkeit, eine Hypothese auf Kampagnenebene zu referenzieren. Die Hypothese wird in diesem Fall allen in der jeweiligen Kampagne enthaltenen Sendungen zugeordnet. Gehen Sie hierzu wie folgt vor:

1. Go to the **[!UICONTROL Edit]** tab of the campaign.
1. In the measurement section, click the **[!UICONTROL Default hypotheses]** tab.

   ![](assets/response_hypothesis_instance_creation_010.png)

1. Click **[!UICONTROL Add]** and select a hypothesis template.

   ![](assets/response_hypothesis_instance_creation_011.png)

   Eine auf dieser Vorlage basierende Hypothese wird von nun an standardmäßig in jedem neuen Versand der Kampagne referenziert.

   ![](assets/response_hypothesis_instance_creation_012.png)

The hypothesis results can be viewed in the **[!UICONTROL General]** and **[!UICONTROL Reactions]** tabs of the hypothesis (refer to [Hypothesis tracking](../../campaign/using/hypothesis-tracking.md))

Weitere Informationen finden Sie unter [Beispiel: Erstellen einer Hypothese in Verbindung mit einer Lieferung](#example--creating-a-hypothesis-linked-to-a-delivery).

## Angebotshypothese erstellen {#creating-a-hypothesis-on-an-offer}

Eine Hypothese über einen Angebotsvorschlag zu erstellen, ist ähnlich wie eine Hypothese über die Lieferung per Fliege. Die Hypothese kann ausgeführt werden, solange das Angebot aktiv ist. Der Berechnungszeitraum basiert auf dem Angebotsstichtag. Wenn Sie mit der Hypothese einen Empfänger mit einem Kauf verknüpfen können, kann der Status des Angebotsprojekts, das wahrscheinlich angenommen wird, automatisch geändert werden (weitere Informationen dazu finden Sie unter [Transaktionen](../../campaign/using/hypothesis-templates.md#transactions)).

1. Erstellen Sie eines oder mehrere **[!UICONTROL Offer]** Mustermodelle, wie unter [Erstellen eines Hypothese-Modells](../../campaign/using/hypothesis-templates.md#creating-a-hypothesis-model)beschrieben.
1. Wechseln Sie zum **[!UICONTROL Campaign management > Measurement hypotheses]** Knoten.
1. Create an **[!UICONTROL Offers]** type hypothesis by selecting the model created previously.

   ![](assets/response_hypothesis_instance_offer_001.png)

   Die in der Vorlage erstellte Abfrage erscheint im Fenster.

   ![](assets/response_hypothesis_instance_offer_003.png)

1. Wählen Sie ein Angebot aus, auf das sich die Hypothese beziehen soll.

   ![](assets/response_hypothesis_instance_offer_004.png)

1. Schränken Sie die Abfrage bei Bedarf ein.
1. Click **[!UICONTROL Start]** to run the hypothesis.
1. Die Ergebnisse der Hypothese können auf ihren **[!UICONTROL General]** und **[!UICONTROL Reactions]** Registerkarten angezeigt werden (siehe [Hypothese-Verfolgung](../../campaign/using/hypothesis-tracking.md)).

   Hypotheses made on an offer are referenced in the **[!UICONTROL Measurement]** tab.

   ![](assets/response_hypothesis_instance_offer_007.png)

   If the **[!UICONTROL Update offer proposition status]** option was enabled in the hypothesis template, the status of the offer proposition is changed automatically, thereby providing feedback on the impact of the campaign (for more on this, refer to [Transactions](../../campaign/using/hypothesis-templates.md#transactions)).

## Beispiel: Erstellen einer einem Versand zugeordneten Hypothese {#example--creating-a-hypothesis-linked-to-a-delivery}

In diesem Beispiel möchten wir eine Hypothese erstellen, die mit einer Lieferung verknüpft ist. Diese Hypothese basiert auf dem zuvor erstellten Modell (siehe [Beispiel: Erstellen einer Hypothese-Vorlage bei der Bereitstellung](../../campaign/using/hypothesis-templates.md#example--creating-a-hypothesis-template-on-a-delivery)). Anschließend werden wir die vom Modell geerbte Abfrage verfeinern, um eine Hypothese zu einem bestimmten Artikel der Kauftabelle zu erstellen.

1. Create a campaign and a delivery (For more on this, refer to [Creating a campaign](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign)).

   In vorliegenden Beispiel handelt es sich um einen Briefpost-Versand.

1. Konfigurieren Sie eine Kontrolladresse: Die zuvor erstellte Hypothesenvorlage wurde so konfiguriert, dass eine Kontrollgruppe in den Reaktionsergebnissen berücksichtigt wird.

   ![](assets/response_hypothesis_delivery_example_007.png)

   >[!NOTE]
   >
   >Weitere Informationen finden Sie unter [Definieren einer Kontrollgruppe](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group).

1. Öffnen Sie die Datei **[!UICONTROL Direct mail delivery]** und klicken Sie auf das **[!UICONTROL Delivery measurement]** Symbol und dann auf **[!UICONTROL Add]**.

   ![](assets/response_hypothesis_delivery_example_002.png)

1. Wählen Sie die zuvor erstellte Hypothesenvorlage mithilfe der Dropdown-Liste aus.

   ![](assets/response_hypothesis_delivery_example_004.png)

   Die in der Vorlage erstellte Abfrage wird angezeigt.

   ![](assets/response_hypothesis_delivery_example_005.png)

1. Click **[!UICONTROL Edit query...]** and refine the query by entering the product that the hypothesis will concern.

   ![](assets/response_hypothesis_delivery_example_006.png)

   You can check that the hypothesis is linked to the delivery in the **[!UICONTROL Edit]** > **[!UICONTROL Measurement]** tab of the campaign.

   ![](assets/response_hypothesis_delivery_example_008.png)

1. Launch your targeting workflow and run the necessary checks until the campaign is finished (for more on this, refer to [Starting a delivery](../../campaign/using/marketing-campaign-deliveries.md#starting-a-delivery)).

   ![](assets/response_hypothesis_delivery_example_009.png)

1. In the Adobe Campaign tree, go to the **[!UICONTROL Campaign management > Measurement hypotheses]** node to check the indicators calculated by the hypothesis.

   ![](assets/response_hypothesis_delivery_example_010.png)

