---
title: Erstellen einer Profilliste mit einem Workflow
seo-title: Erstellen einer Profilliste mit einem Workflow
description: Erstellen einer Profilliste mit einem Workflow
seo-description: null
page-status-flag: never-activated
uuid: a30f7217-fe82-4290-b1e6-e7a126a316c1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
discoiquuid: ba42c3cf-31fc-4fbc-b230-a2b3982328c5
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 681e6ec5fc9ed8c7e46af04f0ed62927b30e1b2e

---


# Erstellen einer Profilliste mit einem Workflow{#creating-a-profile-list-with-a-workflow}

Um eine **[!UICONTROL List]** Typliste basierend auf der neuen Empfängertabelle zu erstellen, müssen Sie einen Targeting-Arbeitsablauf erstellen, der die Liste generiert. Weitere Informationen zu Listen in Kampagne finden Sie in [diesem Abschnitt](../../platform/using/creating-and-managing-lists.md#about-lists-in-adobe-campaign).

1. Wechseln Sie zum **[!UICONTROL Profiles and Targets > Jobs > Targeting workflows]** Knoten des Explorers.
1. Erstellen Sie einen neuen Zielgruppen-Workflow.
1. Platzieren Sie eine **Abfrageaktivität** gefolgt von einer **Listenaktualisierung** .

   ![](assets/mapping_create_list_workflow01.png)

1. Doppelklicken Sie auf die **Abfrageaktivität** und klicken Sie dann auf **[!UICONTROL Edit the query]** , um eine Targeting-Dimension basierend auf dem Schema der neuen Empfängertabelle auszuwählen (in unserem Beispiel: **Individuell**). Klicken Sie **[!UICONTROL Finish]** zur Bestätigung.

   ![](assets/mapping_create_list_workflow03.png)

1. Doppelklicken Sie auf die Aktualisierungsaktivität für die **Liste** und wählen Sie dann das **[!UICONTROL Create the list if necessary (Computed name)]** Optionsfeld aus.

   ![](assets/mapping_create_list_workflow02.png)

1. Wählen Sie den Erstellungsordner für die neue Liste aus.
1. Führen Sie den Workflow aus, um die Liste zu erstellen.
1. Zeigen Sie das Ergebnis in der Node der Struktur an, die Sie während der **[!UICONTROL List update]** Aktivität ausgewählt haben.

   Das Dashboard gibt das Schema an, auf dem die Liste basiert, wie nachfolgend gezeigt:

   ![](assets/mapping_list_view.png)

>[!NOTE]
>
>Sie können auch auf das Video zum [Erstellen einer Liste von Empfängern](https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/getting-started/creating-a-list-of-recipients.html) verweisen.

