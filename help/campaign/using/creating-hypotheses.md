---
solution: Campaign Classic
product: campaign
title: Hypothesenerstellung
description: Hypothesenerstellung
audience: campaign
content-type: reference
topic-tags: response-manager
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1125'
ht-degree: 100%

---


# Hypothesenerstellung{#creating-hypotheses}

Es gibt folgende Möglichkeiten, Hypothesen einem Angebot oder einem Kampagnenversand zuzuordnen:

* über den Ordner **[!UICONTROL Messhypothesen]**: Erstellen Sie basierend auf einer Vorlage eine neue Hypothese und ordnen Sie sie einem bestehenden Versand zu;
* über den Tab **[!UICONTROL Bearbeiten]** > **[!UICONTROL Messung]** einer Kampagne;
* über die Option **[!UICONTROL Messung]** eines von einer Kampagne aus erstellten Versands.

Die Berechnung von Hypothesen erfolgt erst, wenn die entsprechende Marketing-Kampagne gestartet wurde und die Empfänger den Versand erhalten haben. Wenn die Hypothese einen Angebotsvorschlag betrifft, muss dieser bereits präsentiert worden und immer noch aktiv sein. Angebots- und Versandhypothesen werden über den Ordner **[!UICONTROL Messhypothesen]** erstellt und basieren auf einer Hypothesenvorlage. Sie haben des Weiteren die Möglichkeit, eine Hypothese direkt in einem Versand oder einer Kampagne zu referenzieren, bevor die Kampagne gestartet wird. In diesem Fall werden die Hypothesen nach dem Start der Marketing-Kampagne unter Berücksichtigung der Ausführungsparameter automatisch berechnet (Weitere Informationen hierzu finden Sie unter [Ausführungsparameter einer Hypothesenvorlage](../../campaign/using/hypothesis-templates.md#hypothesis-template-execution-settings)).

## Erstellen einer Hypothese direkt in einem Versand {#creating-a-hypothesis-on-the-fly-on-a-delivery}

Um eine Hypothese für einen bestehenden Versand zu erstellen, gehen Sie wie folgt vor:

>[!NOTE]
>
>Dieser Vorgang kann nur für Sendungen durchgeführt werden, die sich in Bearbeitung befinden.

1. Positionieren Sie sich im Knoten **[!UICONTROL Kampagnenverwaltung > Messhypothesen]** im Adobe-Campaign-Navigationsbaum.
1. Klicken Sie auf die Schaltlfäche **[!UICONTROL Neu]** oder machen Sie einen Rechtsklick in der Liste der Hypothesen und wählen Sie im Kontextmenü **[!UICONTROL Neu]** aus.

   ![](assets/response_hypothesis_instance_creation_002.png)

1. Wählen Sie im Hypothesenfenster eine zuvor erstellte Vorlage aus (siehe [Hypothesenvorlagen](../../campaign/using/hypothesis-templates.md)).

   ![](assets/response_hypothesis_instance_creation_003.png)

   Der in der ausgewählten Vorlage festgelegte Hypothesenkontext wird im Fenster angezeigt.

   >[!NOTE]
   >
   >Auch die in dieser Etappe nicht sichtbaren Parameter, die in der Vorlage bestimmt wurden, werden von der Hypothese übernommen.

   ![](assets/response_hypothesis_instance_creation_004.png)

1. Wählen Sie den Versand aus, dem die Hypothese hinzugefügt werden soll.

   ![](assets/response_hypothesis_instance_creation_005.png)

1. Sie können Ihre Hypothese personalisieren, indem Sie die Tabs **[!UICONTROL Allgemein]**, **[!UICONTROL Transaktionen]** und **[!UICONTROL Perimeter]** bearbeiten. Weitere Informationen hierzu finden Sie unter [Hypothesenvorlage erstellen](../../campaign/using/hypothesis-templates.md#creating-a-hypothesis-model).
1. Klicken Sie auf **[!UICONTROL Starten]**, um die Hypothesen auszuführen.

   Daraufhin wird automatisch ein Workflow erzeugt, der die Berechnung der Hypothese durchführt. Sein Titel wird ebenfalls automatisch bestimmt, entsprechend der Konfiguration der Hypothese.

   >[!CAUTION]
   >
   >Wenn Sie die Option **[!UICONTROL Ausführungs-Workflow beibehalten]** aktiviert haben, können Sie auf den Workflow zugreifen.\
   >Die Option sollte jedoch nur Debugging-Zwecken bei fehlerhaften Hypothesenausführungen aktiviert werden. Automatisch generierte Workflows werden im Ordner **[!UICONTROL Administration]** > **[!UICONTROL Betreibung]** > **[!UICONTROL Automatisch erstellte Objekte]** > **[!UICONTROL Kampagnen-Workflows]** des Adobe-Campaign-Explorers gespeichert.
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

1. Erstellen Sie je nach Bedarf eine oder mehrere Vorlagen vom Typ **[!UICONTROL Versand]** anhand der im Abschnitt [Hypothesenvorlage erstellen](../../campaign/using/hypothesis-templates.md#creating-a-hypothesis-model) beschriebenen Vorgehensweise.
1. Erstellen Sie Ihre Marketingkampagne und die entsprechenden Zielgruppen-Workflows.
1. Klicken Sie im Versandfenster auf das Symbol **[!UICONTROL Versandmessung]**.
1. Wählen Sie die Hypothesenvorlage aus. Die in der Vorlage konfigurierte Abfrage wird im Hypothesenfenster angezeigt.

   Die Hypothese wird automatisch berechnet, sobald die Kampagne abgeschlossen ist, entsprechend den in der Vorlage festgelegten Daten (siehe [Ausführungsparameter einer Hypothesenvorlage](../../campaign/using/hypothesis-templates.md#hypothesis-template-execution-settings)).

   ![](assets/response_hypothesis_instance_creation_008.png)

## Referenzieren einer Hypothese in allen Sendungen einer Kampagne {#adding-a-default-hypothesis-to-deliveries-for-a-campaign}

Sie haben die Möglichkeit, eine Hypothese auf Kampagnenebene zu referenzieren. Die Hypothese wird in diesem Fall allen in der jeweiligen Kampagne enthaltenen Sendungen zugeordnet. Gehen Sie hierzu wie folgt vor:

1. Klicken Sie auf den Tab **[!UICONTROL Bearbeiten]** der Kampagne.
1. Gehen Sie im Messungsbereich in den Tab **[!UICONTROL Standardhypothesen]**.

   ![](assets/response_hypothesis_instance_creation_010.png)

1. Klicken Sie auf **[!UICONTROL Hinzufügen]** und wählen Sie eine Hypothesenvorlage aus.

   ![](assets/response_hypothesis_instance_creation_011.png)

   Eine auf dieser Vorlage basierende Hypothese wird von nun an standardmäßig in jedem neuen Versand der Kampagne referenziert.

   ![](assets/response_hypothesis_instance_creation_012.png)

Sie können die Ergebnisse der Berechnung in den Tabs **[!UICONTROL Allgemein]** und **[!UICONTROL Reaktionen]** der Hypothese einsehen (siehe [Hypothesenverfolgung](../../campaign/using/hypothesis-tracking.md)).

Weiterführende Informationen finden Sie unter [Beispiel: Erstellen einer einem Versand zugeordneten Hypothese](#example--creating-a-hypothesis-linked-to-a-delivery).

## Angebotshypothese erstellen {#creating-a-hypothesis-on-an-offer}

Die Erstellung einer Hypothese zu einem Angebotsvorschlag ähnelt dem Erstellen einer unmittelbaren Versandhypothese. Die Hypothese kann ausgeführt werden, solange das Angebot aktiv ist. Der Berechnungszeitraum basiert auf dem Datum des Angebotsvorschlags. Wenn es Ihnen die Hypothese erlaubt, einen Empfänger mit einem Kauf zu verknüpfen, kann der Status jenes Angebotsvorschlags, der wahrscheinlich angenommen wird, automatisch geändert werden (Weitere Informationen hierzu finden Sie unter [Transaktionen](../../campaign/using/hypothesis-templates.md#transactions)).

1. Erstellen Sie eine oder mehrere Vorlagen vom Typ **[!UICONTROL Angebot]**, wie unter [Hypothesenvorlage erstellen](../../campaign/using/hypothesis-templates.md#creating-a-hypothesis-model) beschrieben.
1. Gehen Sie in den Knoten **[!UICONTROL Kampagnenverwaltung > Messhypothesen]**.
1. Erstellen Sie eine Hypothese vom Typ **[!UICONTROL Angebote]**, indem Sie die zuvor erstellte Vorlage auswählen.

   ![](assets/response_hypothesis_instance_offer_001.png)

   Die in der Vorlage erstellte Abfrage erscheint im Fenster.

   ![](assets/response_hypothesis_instance_offer_003.png)

1. Wählen Sie ein Angebot aus, auf das sich die Hypothese beziehen soll.

   ![](assets/response_hypothesis_instance_offer_004.png)

1. Schränken Sie die Abfrage bei Bedarf ein.
1. Klicken Sie auf **[!UICONTROL Starten]**, um die Hypothese auszuführen.
1. Die Ergebnisse der Berechnung können in den Tabs **[!UICONTROL Allgemein]** und **[!UICONTROL Reaktionen]** der Hypothese eingesehen werden (siehe [Hypothesenverfolgung](../../campaign/using/hypothesis-tracking.md)).

   Ausgeführte Hypothesen werden im Tab **[!UICONTROL Messung]** des jeweiligen Angebots referenziert.

   ![](assets/response_hypothesis_instance_offer_007.png)

   Wenn die Option **[!UICONTROL Vorschlagsstatus aktualisieren]** in der Hypothesenvorlage aktiviert wurde, wird der Status des Angebotsvorschlags automatisch geändert und informiert über die Auswirkungen der Kampagnen (siehe diesbezüglich [Transaktionen](../../campaign/using/hypothesis-templates.md#transactions)).

## Beispiel: Erstellen einer einem Versand zugeordneten Hypothese {#example--creating-a-hypothesis-linked-to-a-delivery}

In diesem Beispiel möchten wir eine Hypothese erstellen, die mit einem Versand verknüpft ist. Die Hypothese basiert auf der zuvor erstellten Vorlage (siehe [Beispiel: Erstellen einer Hypothesenvorlage für einen Versand](../../campaign/using/hypothesis-templates.md#example--creating-a-hypothesis-template-on-a-delivery)). Anschließend werden wir die von der Vorlage geerbte Abfrage verfeinern, um eine Hypothese zu einem bestimmten Artikel in der Bestelltabelle zu erstellen.

1. Erstellen Sie eine Kampagne und einen Versand (siehe hierzu [Kampagnen erstellen](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign)).

   In vorliegenden Beispiel handelt es sich um einen Briefpost-Versand.

1. Konfigurieren Sie eine Kontrolladresse: Die zuvor erstellte Hypothesenvorlage wurde so konfiguriert, dass eine Kontrollgruppe in den Reaktionsergebnissen berücksichtigt wird.

   ![](assets/response_hypothesis_delivery_example_007.png)

   >[!NOTE]
   >
   >Weiterführende Informationen finden Sie unter [Kontrollgruppe definieren](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group).

1. Öffnen Sie den zuvor erstellten Versand Ihrer Kampagne, klicken Sie auf das Symbol **[!UICONTROL Versandmessung]** und anschließend auf **[!UICONTROL Hinzufügen]****[!UICONTROL .]**

   ![](assets/response_hypothesis_delivery_example_002.png)

1. Wählen Sie die zuvor erstellte Hypothesenvorlage mithilfe der Dropdown-Liste aus.

   ![](assets/response_hypothesis_delivery_example_004.png)

   Die in der Vorlage erstellte Abfrage wird angezeigt.

   ![](assets/response_hypothesis_delivery_example_005.png)

1. Klicken Sie auf **[!UICONTROL Abfrage bearbeiten]** und schränken Sie unter Angabe des Produkts, auf das sich die Hypothese beziehen soll, die Abfrage ein.

   ![](assets/response_hypothesis_delivery_example_006.png)

   Über den Tab **[!UICONTROL Bearbeiten > Messung > Messhypothesen]** der Kampagne können Sie sicherstellen, dass die Hypothese dem Versand zugeordnet wurde.****

   ![](assets/response_hypothesis_delivery_example_008.png)

1. Starten Sie Ihren Zielgruppen-Workflow und führen Sie die erforderlichen Validierungen aus, bis die Kampagne abgeschlossen ist (lesen Sie diesbezüglich den Abschnitt [Starten eines Versands ](../../campaign/using/marketing-campaign-deliveries.md#starting-a-delivery)).

   ![](assets/response_hypothesis_delivery_example_009.png)

1. Positionieren Sie sich im Knoten **[!UICONTROL Kampagnenverwaltung > Messhypothesen]** des Adobe-Campaign-Navigationsbaums, um die von der Hypothese berechneten Indikatoren zu überprüfen.

   ![](assets/response_hypothesis_delivery_example_010.png)

