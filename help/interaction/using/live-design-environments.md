---
title: Live-/Design-Umgebungen
seo-title: Live-/Design-Umgebungen
description: Live-/Design-Umgebungen
seo-description: null
page-status-flag: never-activated
uuid: 38ee2f6a-e446-4ac6-b962-40b648eeaf66
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: managing-environments
discoiquuid: 3cea2be4-4da4-4ebd-a241-1bbaa5abb16e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Live-/Design-Umgebungen{#live-design-environments}

## Grundprinzip {#operating-principle}

Interaction arbeitet mit zwei Angebotsumgebungstypen:

* **[!UICONTROL Design]** Angebotsumgebungen mit Angeboten, die bearbeitet werden und geändert werden können. Diese Angebote wurden noch nicht im Genehmigungszyklus durchgeführt und werden nicht an Kontakte geliefert.
* **[!UICONTROL Live]** Angebotsumgebungen, die genehmigte Angebote enthalten, während sie Kontakten präsentiert werden. Die Angebote in dieser Umgebung sind schreibgeschützt.

![](assets/offer_environments_overview_001.png)

Jede **[!UICONTROL Design]** Umgebung ist mit einer **[!UICONTROL Live]** Umgebung verknüpft. Nach Abschluss eines Angebots werden dessen Inhalt und die Förderfähigkeitsregeln einem Genehmigungszyklus unterzogen. Nach Abschluss dieses Zyklus wird das betreffende Angebot automatisch in die **[!UICONTROL Live]** Umgebung bereitgestellt. Ab diesem Moment wird es zur Lieferung verfügbar sein.

Interaktion ist standardmäßig mit einer **[!UICONTROL Design]** Umgebung und einer damit verbundenen **[!UICONTROL Live]** Umgebung verbunden. Beide Umgebungen sind für das Targeting der vordefinierten Empfängertabelle vorkonfiguriert.

>[!NOTE]
>
>Um eine andere Tabelle als Ziel festzulegen (Besuchertabelle für anonyme Angebote oder eine bestimmte Empfängertabelle), müssen Sie den Assistenten für die Zielzuordnung verwenden, um die Umgebungen zu erstellen. Weitere Informationen finden Sie unter [Erstellen einer Angebotsumgebung](#creating-an-offer-environment).

![](assets/offer_environments_overview_002.png)

Angebotsmanager und Liefermanager haben Zugriff auf verschiedene Ansichten der Umgebung. Bereitstellungsmanager können nur die **[!UICONTROL Live]** Angebotsumgebung anzeigen und Angebote zur Bereitstellung verwenden. Angebotsmanager können die **[!UICONTROL Design]** Umgebung anzeigen und ändern und die **[!UICONTROL Live]** Umgebung anzeigen. For more on this, refer to [Operator profiles](../../interaction/using/operator-profiles.md).

## Angebotsumgebungen {#creating-an-offer-environment}

Standardmäßig wird Interaction mit einer Umgebung geliefert, die für ein Zielgruppenmapping der Empfängertabelle konfiguriert ist, also für Angebote an identifizierte Kontakte. Sollten Sie eine andere Tabelle (beispielsweise die Besuchertabelle für anonyme Angebote oder eine spezifische Empfängertabelle) verwenden wollen, gehen Sie wie folgt vor:

1. Platzieren Sie den Cursor auf dem Knoten **[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Delivery mappings]** . Klicken Sie mit der rechten Maustaste auf die gewünschte Zuordnungsoption (**[!UICONTROL Visitors]** wenn Sie anonyme Angebote verwenden möchten) und wählen Sie **[!UICONTROL Actions]** > **[!UICONTROL Modify the options of the targeting dimension]**.

   ![](assets/offer_env_anonymous_001.png)

1. Klicken Sie auf **[!UICONTROL Next]** , um zum nächsten Bildschirm im Assistenten zu gelangen, markieren Sie das **[!UICONTROL Generate a storage schema for propositions]** Feld und klicken Sie auf **[!UICONTROL Save]**.

   ![](assets/offer_env_anonymous_002.png)

   >[!NOTE]
   >
   >Falls das Feld bereits angekreuzt war, muss es zunächst deaktiviert und dann erneut aktiviert werden.

1. Adobe Campaign erstellt zwei Umgebungen (**[!UICONTROL Design]** und **[!UICONTROL Live]** ) mit Targeting-Informationen aus der zuvor aktivierten Zielzuordnung. Die Umgebung ist mit den Targeting-Informationen vorkonfiguriert.

   Wenn Sie die **[!UICONTROL Visitor]** Zuordnung aktiviert haben, wird das **[!UICONTROL Environment dedicated to incoming anonymous interactions]** Feld automatisch auf der **[!UICONTROL General]** Registerkarte der Umgebung markiert.

   Diese Option ermöglicht die Aktivierung von für anonyme Interaktionen reservierten Funktionen, beispielsweise in Bezug auf die Konfiguration der Umgebungsplatzierungen. Dies ermöglicht es, Optionen zu konfigurieren, die den Wechsel von &quot;identifizierten&quot; zu &quot;anonymen&quot; Umgebungen erlauben.

   Sie können beispielsweise eine Empfängerumgebung mit einem Angebotsumfeld verknüpfen, das einer Besucherumgebung entspricht (nicht identifizierter Kontakt). Auf diese Weise werden dem Kontakt je nachdem, ob er identifiziert wird oder nicht, verschiedene Angebote zur Verfügung gestellt. For more on this, refer to [Creating offer spaces](../../interaction/using/creating-offer-spaces.md).

   ![](assets/offer_env_anonymous_003.png)

>[!NOTE]
>
>For more information on anonymous interactions on an inbound channel, refer to [Anonymous interactions](../../interaction/using/anonymous-interactions.md).

