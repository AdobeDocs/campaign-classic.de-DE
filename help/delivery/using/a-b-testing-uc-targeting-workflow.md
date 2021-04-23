---
solution: Campaign Classic
product: campaign
title: Zielgruppen-Workflow erstellen
description: Erfahren Sie anhand eines speziellen Anwendungsbeispiels, wie Sie A/B-Tests durchführen.
audience: delivery
content-type: reference
topic-tags: a-b-testing
exl-id: aa21fa33-aef9-484a-b454-0cd5a6868a98
translation-type: ht
source-git-commit: 6854d06f8dc445b56ddfde7777f02916a60f2b63
workflow-type: ht
source-wordcount: '166'
ht-degree: 100%

---

# Zielgruppen-Workflow erstellen {#step-1--creating-a-targeting-workflow}

Zielgruppen-Workflows werden im Rahmen von Kampagnen im Tab **[!UICONTROL Zielbestimmungen und Workflows]** erstellt. Im vorliegenden Beispiel enthält der Workflow eine **[!UICONTROL Abfrage]**, eine **[!UICONTROL Aufspaltung]** mit je einem angeschlossenen **[!UICONTROL E-Mail-Versand]**, eine **[!UICONTROL Warten]**-Aktivität, eine **[!UICONTROL JavaScript-Code]**-Aktivität und einen **[!UICONTROL Versand]**.

1. Öffnen Sie eine existierende Kampagne oder erstellen Sie eine neue (siehe diesen [Abschnitt](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign)).

   ![](assets/use_case_abtesting_targetwkfl_001.png)

1. Gehen Sie in den Tab **[!UICONTROL Zielbestimmungen und Workflows]**.

   ![](assets/use_case_abtesting_targetwkfl_002.png)

1. Klicken Sie auf **[!UICONTROL Hinzufügen]**, um einen neuen Workflow zu erstellen oder verwenden Sie den Standard-Workflow und benennen Sie ihn. Lesen Sie diesbezüglich auch diesen [Abschnitt](../../campaign/using/marketing-campaign-deliveries.md#selecting-the-target-population).

   ![](assets/use_case_abtesting_targetwkfl_003.png)

1. Ziehen Sie mit der Maus die Aktivitäten in das Workflow-Diagramm und zwar aus dem Tab **[!UICONTROL Zielgruppenbestimmung]** eine **[!UICONTROL Abfrage]** und eine **[!UICONTROL Aufspaltung]**, aus dem Tab **[!UICONTROL Sendungen]** zwei **[!UICONTROL E-Mail-Versand]**-Aktivitäten, aus dem Tab **[!UICONTROL Steuerung]** eine **[!UICONTROL Warten]**-Aktivität und aus dem Tab **[!UICONTROL Aktionen]** eine **[!UICONTROL JavaScript-Code]**-Aktivität sowie einen **[!UICONTROL Versand]**.********

![](assets/use_case_abtesting_targetwkfl_004.png)

Sie können jetzt die Testpopulation konfigurieren (siehe [Schritt 2: Testpopulation konfigurieren](../../delivery/using/a-b-testing-uc-population-samples.md)).
