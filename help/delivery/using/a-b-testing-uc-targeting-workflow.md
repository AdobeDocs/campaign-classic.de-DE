---
product: campaign
title: Erstellen eines Zielgruppen-Workflows
description: Erfahren Sie anhand eines speziellen Anwendungsbeispiels, wie Sie A/B-Tests durchführen
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
feature: A/B Testing
role: User
exl-id: aa21fa33-aef9-484a-b454-0cd5a6868a98
TQID: https://experienceleague.adobe.com/D4O223FYCiIwT-P4WCXa1gYjxB56lCGVIuGL3x-fDRo
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: a075b2c1-7748-4328-b7f6-343aa314616aid: b631758a-142d-425f-b9aa-f756d85cb979id: c858a28b-ea19-49b0-8d48-828717fad89c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
subfeature_v2: id: d5bbe3da-ba85-4242-817e-54f7c4b943e0id: e739ee2b-6228-412e-878f-45de0791417d
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 198
ht-degree: 100%

---

# A/B-Tests: Erstellen eines Zielgruppenbestimmungs-Workflows {#step-1--creating-a-targeting-workflow}

Sie müssen in der Registerkarte **[!UICONTROL Zielgruppenbestimmungen und Workflows]** einer Kampagne einen Workflow erstellen. Er besteht aus einer **[!UICONTROL Abfrage]**-Aktivität, einer **[!UICONTROL Aufspaltung]**-Aktivität, die mit zwei **[!UICONTROL E-Mail-Versand]**-Aktivitäten verknüpft ist, einer **[!UICONTROL Warten]**-Aktivität, einer **[!UICONTROL JavaScript-Code]**-Aktivität und einer **[!UICONTROL Versand]**-Aktivität.

1. Erstellen Sie eine Kampagne, falls noch nicht geschehen. Weiterführende Informationen finden Sie in der [Dokumentation zu Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/set-up-campaigns.html?lang=de){target=_blank}.

   ![](assets/use_case_abtesting_targetwkfl_001.png)

1. Gehen Sie auf die Registerkarte **[!UICONTROL Zielgruppenbestimmungen und Workflows]**.

   ![](assets/use_case_abtesting_targetwkfl_002.png)

1. Ändern Sie den Titel eines vorhandenen Workflows oder klicken Sie auf **[!UICONTROL Hinzufügen]**, um einen neuen zu erstellen. Weitere Informationen finden Sie in der [Dokumentation zu Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/marketing-campaign-target.html?lang=de){target="_blank"}.

   ![](assets/use_case_abtesting_targetwkfl_003.png)

1. Ziehen Sie mit der Maus die Aktivitäten in das Workflow-Diagramm und zwar aus der Registerkarte **[!UICONTROL Zielgruppenbestimmung]** eine **[!UICONTROL Abfrage]** und eine **[!UICONTROL Aufspaltung]**, aus der Registerkarte **[!UICONTROL Sendungen]** zwei **[!UICONTROL E-Mail-Versand]**-Aktivitäten, aus der Registerkarte **[!UICONTROL Steuerung]** eine **[!UICONTROL Warten]**-Aktivität und aus der Registerkarte **[!UICONTROL Aktionen]** eine **[!UICONTROL JavaScript-Code]**-Aktivität sowie einen **[!UICONTROL Versand]**.********

![](assets/use_case_abtesting_targetwkfl_004.png)

Jetzt können Sie die Beispielpopulationen konfigurieren. [Weitere Informationen](a-b-testing-uc-population-samples.md).
