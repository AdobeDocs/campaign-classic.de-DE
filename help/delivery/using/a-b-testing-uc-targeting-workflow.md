---
product: campaign
title: Erstellen eines Zielgruppen-Workflows
description: Erfahren Sie anhand eines speziellen Anwendungsbeispiels, wie Sie A/B-Tests durchführen
badge-v7: label="v7" type="Informative" tooltip="Gilt für Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Gilt auch für Campaign v8"
feature: A/B Testing
role: User
exl-id: aa21fa33-aef9-484a-b454-0cd5a6868a98
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '177'
ht-degree: 96%

---

# AB-Tests: Erstellen eines Zielgruppen-Workflows {#step-1--creating-a-targeting-workflow}

Zielgruppen-Workflows werden im Rahmen von Kampagnen auf der Registerkarte **[!UICONTROL Zielgruppenbestimmungen und Workflows]** erstellt. Im vorliegenden Beispiel enthält der Workflow eine **[!UICONTROL Abfrage]**, eine **[!UICONTROL Aufspaltung]** mit je einem angeschlossenen **[!UICONTROL E-Mail-Versand]**, eine **[!UICONTROL Warten]**-Aktivität, eine **[!UICONTROL JavaScript-Code]**-Aktivität und einen **[!UICONTROL Versand]**.

1. Öffnen Sie eine existierende Kampagne oder erstellen Sie eine neue (siehe diesen [Abschnitt](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign)).

   ![](assets/use_case_abtesting_targetwkfl_001.png)

1. Gehen Sie auf die Registerkarte **[!UICONTROL Zielgruppenbestimmungen und Workflows]**.

   ![](assets/use_case_abtesting_targetwkfl_002.png)

1. Klicken Sie auf **[!UICONTROL Hinzufügen]**, um einen neuen Workflow zu erstellen oder verwenden Sie den bestehenden Workflow und benennen Sie ihn um. Lesen Sie diesbezüglich auch diesen [Abschnitt](../../campaign/using/marketing-campaign-deliveries.md#selecting-the-target-population).

   ![](assets/use_case_abtesting_targetwkfl_003.png)

1. Ziehen Sie mit der Maus die Aktivitäten in das Workflow-Diagramm und zwar aus der Registerkarte **[!UICONTROL Zielgruppenbestimmung]** eine **[!UICONTROL Abfrage]** und eine **[!UICONTROL Aufspaltung]**, aus der Registerkarte **[!UICONTROL Sendungen]** zwei **[!UICONTROL E-Mail-Versand]**-Aktivitäten, aus der Registerkarte **[!UICONTROL Steuerung]** eine **[!UICONTROL Warten]**-Aktivität und aus der Registerkarte **[!UICONTROL Aktionen]** eine **[!UICONTROL JavaScript-Code]**-Aktivität sowie einen **[!UICONTROL Versand]**.********

![](assets/use_case_abtesting_targetwkfl_004.png)

Jetzt können Sie die Beispielpopulationen konfigurieren. [Weitere Informationen](a-b-testing-uc-population-samples.md).
