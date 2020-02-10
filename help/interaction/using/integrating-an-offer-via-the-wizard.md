---
title: Integration über den Assistenten
seo-title: Integration über den Assistenten
description: Integration über den Assistenten
seo-description: null
page-status-flag: never-activated
uuid: 0d8cf0b5-fc27-4bf4-bd1d-892fe6e3257b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: delivering-an-offer
discoiquuid: 181fcb70-9394-4091-93df-92c39273ec3d
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 209ac4d81d2d27c264ee6b288bcb7fcb1900ffc5

---


# Integration über den Assistenten{#integrating-an-offer-via-the-wizard}

Zwei Möglichkeiten stehen zur Verfügung, um Angebote zum Zeitpunkt der Versanderstellung zu integrieren:

* durch Abfrage des Angebotsmoduls im Nachrichten-Textkörper;
* durch Referenzierung der Angebote in einem Versandentwurf im Rahmen einer Kampagne. Diese Methode wird insbesondere bei Briefpostkampagnen verwendet.

## Versand mit Abfrage des Angebotsmoduls {#delivering-with-a-call-to-the-offer-engine}

Um während einer Marketingkampagne ein Angebot zu präsentieren, erstellen Sie einfach eine klassische Auslieferungsaktion, die auf dem ausgewählten Kanal basiert. Die Angebotsmaschine wird aufgerufen, wenn der Bereitstellungsinhalt definiert ist, indem auf das in der Symbolleiste verfügbare Symbol geklickt wird **[!UICONTROL Offers]** .

![](assets/offer_delivery_009.png)

Weiterführende Informationen zu Versandaktionen und Marketingkampagnen finden Sie in den Handbüchern [Delivery](../../delivery/using/about-direct-mail-channel.md) und [Campaign](../../campaign/using/setting-up-marketing-campaigns.md).

### Angebote in Sendungen einschließen {#main-steps-for-inserting-an-offer-into-a-delivery}

Gehen Sie wie folgt vor, um Angebotsvorschläge in Sendungen einzufügen:

1. Klicken Sie im Versandfenster auf das Angebotssymbol.

   ![](assets/offer_delivery_001.png)

1. Wählen Sie die Ihrer Angebotsumgebung entsprechende Platzierung aus.

   ![](assets/offer_delivery_002.png)

1. Wählen Sie die Kategorie aus, der die zu unterbreitenden Angebote angehören, oder ein oder mehrere Themen, um die vom Angebotsmodul getroffene Auswahl einzugrenzen. Es wird empfohlen, nur eins der beiden Felder zu verwenden, um die Auswahlmöglichkeiten nicht zu stark einzuschränken.

   ![](assets/offer_delivery_003.png)

   ![](assets/offer_delivery_004.png)

1. Geben Sie die Anzahl an Angeboten an, die im Nachrichten-Textkörper erscheinen sollen.

   ![](assets/offer_delivery_005.png)

1. Wählen Sie bei Bedarf die **[!UICONTROL Exclude non-eligible recipients]** Option aus. Weitere Informationen dazu finden Sie unter [Parameter für den Aufruf der Angebotsengine](#parameters-for-calling-offer-engine).

   ![](assets/offer_delivery_006.png)

1. Wählen Sie bei Bedarf die **[!UICONTROL Do not display anything if no offers are selected]** Option aus. Weitere Informationen dazu finden Sie unter [Parameter für den Aufruf der Angebotsengine](#parameters-for-calling-offer-engine).

   ![](assets/offer_delivery_007.png)

1. Fügen Sie nun mithilfe der Personalisierungsfelder die Angebotsvorschläge in den Versandinhalt ein. Die Anzahl der verfügbaren Vorschläge hängt von der Konfiguration der Abfrage an das Angebotsmodul, ihre Reihenfolge von der Angebotspriorität ab.

   ![](assets/offer_delivery_008.png)

1. Erstellen Sie den weiteren Versandinhalt und starten Sie den Versand wie gewohnt.

   ![](assets/offer_delivery_010.png)

### Parameter der Abfragen an das Angebotsmodul {#parameters-for-calling-offer-engine}

* **[!UICONTROL Space]** : Bereich der Angebotsumgebung, der ausgewählt werden muss, um die Angebotsmaschine zu aktivieren.
* **[!UICONTROL Category]** : bestimmter Ordner, in dem Angebote sortiert werden. Wenn keine Kategorie angegeben ist, werden alle in der Umgebung enthaltenen Angebote von der Angebotsengine berücksichtigt, es sei denn, ein Design wurde ausgewählt.
* **[!UICONTROL Themes]** : Schlüsselwörter, die in den Kategorien oben definiert werden. Diese dienen als Filter und ermöglichen es Ihnen, die Anzahl der anzuzeigenden Angebote zu verfeinern, indem Sie sie in einer Reihe von Kategorien auswählen.
* **[!UICONTROL Number of propositions]** : Anzahl der von der Engine zurückgegebenen Angebote, die in den Lieferkörper eingefügt werden können. Wenn sie nicht in die Nachricht eingefügt werden, werden die Angebote weiterhin generiert, aber nicht präsentiert.
* **[!UICONTROL Exclude non-eligible recipients]** : Mit dieser Option können Sie den Ausschluss von Empfängern aktivieren oder deaktivieren, für die nicht genügend berechtigte Angebote vorhanden sind. Die Zahl der förderfähigen Vorschläge kann niedriger sein als die angeforderte Anzahl von Vorschlägen. Wenn dieses Kontrollkästchen aktiviert ist, werden Empfänger, die nicht über genügend Vorschläge verfügen, von der Lieferung ausgeschlossen. Wenn Sie diese Option nicht auswählen, werden diese Empfänger nicht ausgeschlossen, aber sie verfügen nicht über die angeforderte Anzahl von Vorschlägen.
* **[!UICONTROL Do not display anything if no offer is selected]** : Mit dieser Option können Sie festlegen, wie die Nachricht verarbeitet werden soll, falls eines der Vorschläge nicht vorhanden ist. Wenn dieses Kontrollkästchen aktiviert ist, wird die Darstellung des fehlenden Vorschlags nicht angezeigt und es wird kein Inhalt in der Meldung für diesen Vorschlag angezeigt. Wenn das Feld nicht markiert ist, wird die Nachricht selbst beim Senden abgebrochen und die Empfänger erhalten keine Nachrichten mehr.

### Angebotsvorschläge in einen Versand einfügen {#inserting-an-offer-proposition-into-a-delivery}

Die Darstellung der zu unterbreitenden Angebote wird mithilfe der Personalisierungsfelder in den Body des Versands eingeschlossen. Die Anzahl der einzuschließenden Vorschläge wird in den Parametern der Angebotsmodul-Abfrage konfiguriert.

Die Nachrichtenpersonalisierung kann entweder über Felder des Angebots oder im Fall von E-Mails über Rendering-Funktionen geschehen.

![](assets/offer_delivery_011.png)

## Versand mit Versandentwurf {#delivering-with-delivery-outlines}

Eine weitere Möglichkeit ist die Verwendung von Versandentwürfen, um im Zuge von Kampagnen Angebote zu unterbreiten.

Weiterführende Informationen zu Versandentwürfen können Sie dem [Campaign](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline)-Handbuch entnehmen.

1. Erstellen Sie eine neue oder öffnen Sie eine existierende Kampagne.
1. Access the delivery outlines via the campaign&#39;s **[!UICONTROL Edit]** > **[!UICONTROL Documents]** tab.
1. Add an outline then insert as many offers as you like into it by right-clicking on the outline and selecting **[!UICONTROL New]** > **[!UICONTROL Offer]**, then save the campaign.

   ![](assets/int_compo_offre1.png)

1. Erstellen Sie nun einen Versand, in dem Sie auf Versandentwürfe zugreifen können, z. B. einen Briefpost-Versand.
1. Klicken Sie beim Bearbeiten der Bereitstellung auf **[!UICONTROL Select a delivery outline]**.

   >[!NOTE]
   >
   >Depending on the type of delivery, this option can be found in the **[!UICONTROL Properties]** > **[!UICONTROL Advanced]** menu (for email deliveries for example).

   ![](assets/int_compo_offre2.png)

1. Using the **[!UICONTROL Offers]** button, you can then configure the offer space as well as the number of offers to present in the delivery.

   ![](assets/int_compo_offre3.png)

1. Add the propositions into the delivery body using the personalization fields (for more on this, refer to the [Inserting an offer proposition into a delivery](#inserting-an-offer-proposition-into-a-delivery) section), or in the case of a direct mail delivery, by editing the extraction file format.

   Die Auswahl der zu unterbreiteten Angebote erfolgt aus denen, die im Versandentwurf referenziert wurden.

   >[!NOTE]
   >
   >Informationen bezüglich Rang und Gewichtung der Angebote werden nur dann in der Vorschlagstabelle gespeichert, wenn die Angebote direkt im Versand erzeugt werden.

