---
product: campaign
title: Erstellen einer Profilliste mit einem Workflow
description: Erfahren Sie, wie Sie in einem Workflow eine Profilliste erstellen
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
exl-id: 6b308299-4d07-4c9e-bd2f-a0860c41cf02
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 13%

---

# Erstellen einer Profilliste mit einem Workflow{#creating-a-profile-list-with-a-workflow}

![](../../assets/v7-only.svg)

Um eine auf der neuen Empfängertabelle basierende Liste vom Typ **[!UICONTROL Liste]** zu erstellen, müssen Sie einen Zielgruppen-Workflow erstellen, der die Liste generiert.

Weiterführende Informationen zu Listen in Campaign finden Sie in [diesem Abschnitt](../../platform/using/creating-and-managing-lists.md#about-lists-in-adobe-campaign).

![](assets/do-not-localize/how-to-video.png) [Entdecken Sie diese Funktion im Video](../../platform/using/creating-and-managing-lists.md#create-list-in-a-wf-video).

Gehen Sie wie folgt vor, um einen Zielgruppen-Workflow zu erstellen und Empfänger in einer benutzerdefinierten Empfängertabelle zu aktualisieren:

1. Gehen Sie zum Knoten **[!UICONTROL Profile und Zielgruppen > Vorgänge > Zielgruppen-Workflows]** des Explorer.
1. Erstellen Sie einen neuen Zielgruppen-Workflow.
1. Platzieren Sie eine **Abfrage** -Aktivität gefolgt von einer **Listen-Update** -Aktivität.

   ![](assets/mapping_create_list_workflow01.png)

1. Doppelklicken Sie auf die Aktivität **Abfrage** und klicken Sie dann auf **[!UICONTROL Abfrage bearbeiten]** , um eine Zielgruppendimension auszuwählen, die auf dem Schema der neuen Empfängertabelle basiert (in unserem Beispiel: **Individuell**). Klicken Sie zur Bestätigung auf **[!UICONTROL Beenden]**.

   ![](assets/mapping_create_list_workflow03.png)

1. Doppelklicken Sie auf die Aktivität **Listen-Update** und wählen Sie dann die Optionsschaltfläche **[!UICONTROL Liste bei Bedarf erstellen (Berechneter Name)]** aus.

   ![](assets/mapping_create_list_workflow02.png)

1. Wählen Sie den Erstellungsordner für die neue Liste aus.
1. Führen Sie den Workflow aus, um die Liste zu erstellen.
1. Zeigen Sie das Ergebnis im Knoten des Baums an, den Sie während der Aktivität **[!UICONTROL Listen-Update]** ausgewählt haben.

   Das Dashboard gibt das Schema an, auf dem die Liste basiert, wie unten dargestellt:

   ![](assets/mapping_list_view.png)
