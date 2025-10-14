---
product: campaign
title: Erstellen eines Zielgruppen-Workflows
description: Erfahren Sie anhand eines speziellen Anwendungsbeispiels, wie Sie A/B-Tests durchführen
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
feature: A/B Testing
role: User
exl-id: aa21fa33-aef9-484a-b454-0cd5a6868a98
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 75%

---

# A/B-Tests: Erstellen eines Zielgruppenbestimmungs-Workflows {#step-1--creating-a-targeting-workflow}

Zielgruppen-Workflows werden im Rahmen von Kampagnen auf der Registerkarte **[!UICONTROL Zielgruppenbestimmungen und Workflows]** erstellt. Im vorliegenden Beispiel enthält der Workflow eine **[!UICONTROL Abfrage]**, eine **[!UICONTROL Aufspaltung]** mit je einem angeschlossenen **[!UICONTROL E-Mail-Versand]**, eine **[!UICONTROL Warten]**-Aktivität, eine **[!UICONTROL JavaScript-Code]**-Aktivität und einen **[!UICONTROL Versand]**.

1. Wenn Sie dies noch nicht getan haben, erstellen Sie eine Kampagne. Weitere Informationen hierzu finden Sie in der [&#x200B; zu Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/set-up-campaigns.html?lang=de){target=_blank}.

   ![](assets/use_case_abtesting_targetwkfl_001.png)

1. Gehen Sie auf die Registerkarte **[!UICONTROL Zielgruppenbestimmungen und Workflows]**.

   ![](assets/use_case_abtesting_targetwkfl_002.png)

1. Ändern Sie den Titel des vorhandenen Workflows oder klicken Sie auf **[!UICONTROL Hinzufügen]** um einen neuen zu erstellen (weitere Informationen hierzu finden Sie in der [&#x200B; zu Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/marketing-campaign-target.html?lang=de){target="_blank"}.

   ![](assets/use_case_abtesting_targetwkfl_003.png)

1. Ziehen Sie mit der Maus die Aktivitäten in das Workflow-Diagramm und zwar aus der Registerkarte **[!UICONTROL Zielgruppenbestimmung]** eine **[!UICONTROL Abfrage]** und eine **[!UICONTROL Aufspaltung]**, aus der Registerkarte **[!UICONTROL Sendungen]** zwei **[!UICONTROL E-Mail-Versand]**-Aktivitäten, aus der Registerkarte **[!UICONTROL Steuerung]** eine **[!UICONTROL Warten]**-Aktivität und aus der Registerkarte **[!UICONTROL Aktionen]** eine **[!UICONTROL JavaScript-Code]**-Aktivität sowie einen **[!UICONTROL Versand]**.**&#x200B;**&#x200B;**&#x200B;**

![](assets/use_case_abtesting_targetwkfl_004.png)

Jetzt können Sie die Beispielpopulationen konfigurieren. [Weitere Informationen](a-b-testing-uc-population-samples.md).
