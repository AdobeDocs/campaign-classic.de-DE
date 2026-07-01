---
product: campaign
title: Live-/Design-Umgebungen
description: Live-/Design-Umgebungen
feature: Interaction, Offers
audience: interaction
content-type: reference
topic-tags: managing-environments
exl-id: 965c4a6a-6535-454d-bd37-e9c8312b4d13
TQID: https://experienceleague.adobe.com/82MTqZNuWiPJj0YM70MnN1OVuWjvvdbGjDr5e9iFbjU
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2:
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
feature_v2:
  - id: b6fcaf36-3bc4-4604-94f3-81b5d3f41ecf
subfeature_v2: []
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 494
ht-degree: 100%

---

# Live-/Design-Umgebungen{#live-design-environments}



## Grundprinzip {#operating-principle}

Interaction arbeitet mit zwei Angebotsumgebungstypen:

* **[!UICONTROL Design]**-Angebotsumgebungen, in denen Angebote bearbeitet werden und verändert werden können. Diese Angebote haben den Validierungszyklus nicht durchlaufen und werden nicht an Kontakte gesendet.
* **[!UICONTROL Live]**-Angebotsumgebungen, in denen validierte Angebote so zur Verfügung stehen, wie sie Kontakten unterbreitet werden.Die Angebote in dieser Umgebung sind schreibgeschützt.

![](assets/offer_environments_overview_001.png)

Jede **[!UICONTROL Design]**-Umgebung ist mit einer **[!UICONTROL Live]**-Umgebung verknüpft. Nach Erstellung eines Angebots durchlaufen sein Inhalt und seine Eignungsregeln einen Validierungszyklus. Das Angebot wird automatisch für die **[!UICONTROL Live-Umgebung]** bereitgestellt. Ab diesem Zeitpunkt ist es für den Versand verfügbar.

Standardmäßig verfügt Campaign über eine **[!UICONTROL Design]**-Umgebung und eine **[!UICONTROL Live]**-Umgebung, die mit der Design-Umgebung verknüpft ist. Beide Umgebungen sind für die integrierte Empfängertabelle vorkonfiguriert.

>[!NOTE]
>
>Sollten Sie eine andere Tabelle (beispielsweise die Besuchertabelle für anonyme Angebote oder eine spezifische Empfängertabelle) verwenden wollen, steht Ihnen ein Assistent zur Verfügung, um die Umgebungen mit den entsprechenden Zielgruppen-Mappings zu erstellen. Weiterführende Informationen dazu finden Sie unter [Angebotsumgebungen](#creating-an-offer-environment).

![](assets/offer_environments_overview_002.png)

Angebots- und versandverantwortliche Benutzer greifen auf unterschiedliche Weise auf die Umgebungen zu. Versandverantwortliche haben nur Lesezugriff auf die **[!UICONTROL Design-Umgebung]**, deren Angebote sie in Sendungen verwenden können. Angebotsverantwortliche hingegen haben Schreibzugriff auf die **[!UICONTROL Design-Umgebung]**, aber nur Lesezugriff auf die **[!UICONTROL Live-Umgebung]**. Weitere Informationen hierzu finden Sie im Abschnitt [Benutzerprofile](../../interaction/using/operator-profiles.md).

## Erstellen einer Angebotsumgebung {#creating-an-offer-environment}

Interactio verfügt standardmäßig über eine vorab konfigurierte Umgebung, in der die Empfängertabelle (identifizierte Angebote) ausgewählt werden kann. Wenn Sie eine andere Tabelle verwenden möchten (Besuchertabelle für anonyme Angebote oder eine bestimmte Empfängertabelle), müssen Sie die folgenden Konfigurationen anwenden:

1. Markieren Sie den Knoten **[!UICONTROL Administration]** > **[!UICONTROL Kampagnen]** > **[!UICONTROL Zielgruppen-Mappings]**. Klicken Sie mit der rechten Maustaste auf das Mapping, das Sie verwenden möchten (**[!UICONTROL Besucher]** im Fall von anonymen Angeboten) und wählen Sie im Kontextmenü die Option **[!UICONTROL Aktionen]** > **[!UICONTROL Optionen der Zielgruppendimension ändern...]** aus.

   ![](assets/offer_env_anonymous_001.png)

1. Klicken Sie auf **[!UICONTROL Weiter]** und aktivieren Sie im nächsten Bildschirm das Feld **[!UICONTROL Speicherschema für Vorschläge erzeugen]**. Klicken Sie zum Abschluss auf **[!UICONTROL Speichern]**.

   ![](assets/offer_env_anonymous_002.png)

   >[!NOTE]
   >
   >Falls das Feld bereits angekreuzt war, muss es zunächst deaktiviert und dann erneut aktiviert werden.

1. Adobe Campaign erstellt zwei Umgebungen (**[!UICONTROL Design]** und **[!UICONTROL Live]**) mit Zielgruppenbestimmungsinformationen vom zuvor aktivierten Zielgruppen-Mapping. Die Umgebung ist mit den Zielgruppenbestimmungsinformationen vorkonfiguriert.

   Im Falle eines Mappings mit der **[!UICONTROL Besuchertabelle]** ist das Feld **[!UICONTROL Für anonyme eingehende Interaktionen reservierte Umgebung]** im Tab **[!UICONTROL Allgemein]** der Umgebung automatisch ausgewählt.

   Mit dieser Option können Sie anonyme, für Interaktionen spezifische Funktionen aktivieren, insbesondere bei der Konfiguration von Platzierungen in der Umgebung. Sie können außerdem Optionen konfigurieren, die es Ihnen ermöglichen von einer „identifizierten“ Umgebung zu einer „anonymen“ Umgebung zu wechseln.

   Sie können beispielsweise eine Platzierung der Empfängerumgebung (identifizierter Kontakt) mit einer Platzierung verknüpfen, die einer Besucherumgebung (nicht identifizierter Kontakt) entspricht. Auf diese Weise werden dem Kontakt verschiedene Angebote unterbreitet, je nachdem, ob er identifiziert wurde oder nicht. Weitere Informationen hierzu finden Sie unter [Angebotsplatzierungen](../../interaction/using/creating-offer-spaces.md).

   ![](assets/offer_env_anonymous_003.png)

>[!NOTE]
>
>Weiterführende Informationen zu anonymen Interaktionen in einem eingehenden Kanal finden Sie im Abschnitt [Anonyme Interaktionen](../../interaction/using/anonymous-interactions.md).
