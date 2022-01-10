---
product: campaign
title: Erstellen einer Profilliste mit einem Workflow
description: Erfahren Sie, wie Sie in einem Workflow eine Profilliste erstellen
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
exl-id: 6b308299-4d07-4c9e-bd2f-a0860c41cf02
source-git-commit: fb4b4c42b907e86813ea570f912312fccf893bfe
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 13%

---

# Erstellen einer Profilliste mit einem Workflow{#creating-a-profile-list-with-a-workflow}

![](../../assets/common.svg)

So erstellen Sie eine **[!UICONTROL Liste]** Listen basierend auf der neuen Empfängertabelle eingeben, müssen Sie einen Zielgruppen-Workflow erstellen, der die Liste generiert.

Weitere Informationen zu Listen in Campaign finden Sie unter [diesem Abschnitt](../../platform/using/creating-and-managing-lists.md#about-lists-in-adobe-campaign).

![](assets/do-not-localize/how-to-video.png) [Entdecken Sie diese Funktion im Video](../../platform/using/creating-and-managing-lists.md#create-list-in-a-wf-video).

Gehen Sie wie folgt vor, um einen Zielgruppen-Workflow zu erstellen und Empfänger in einer benutzerdefinierten Empfängertabelle zu aktualisieren:

1. Navigieren Sie zu **[!UICONTROL Profile und Zielgruppen > Vorgänge > Zielgruppen-Workflows]** -Knoten des Explorer.
1. Erstellen Sie einen neuen Zielgruppen-Workflow.
1. Platzieren Sie eine **Abfrage** -Aktivität, gefolgt von **Listen-Update** Aktivität.

   ![](assets/mapping_create_list_workflow01.png)

1. Doppelklicken Sie auf die **Abfrage** Aktivität und klicken Sie auf **[!UICONTROL Abfrage bearbeiten]** , um eine Zielgruppendimension basierend auf dem Schema der neuen Empfängertabelle zu wählen (im vorliegenden Beispiel: **Individuum**). Klicken Sie zur Bestätigung auf **[!UICONTROL Beenden]**.

   ![](assets/mapping_create_list_workflow03.png)

1. Doppelklicken Sie auf die **Listen-Update** -Aktivität und wählen Sie dann die **[!UICONTROL Erstellen Sie bei Bedarf die Liste (berechneter Name).]** Optionsfeld.

   ![](assets/mapping_create_list_workflow02.png)

1. Wählen Sie den Erstellungsordner für die neue Liste aus.
1. Führen Sie den Workflow aus, um die Liste zu erstellen.
1. Zeigen Sie das Ergebnis im Knoten des Baums an, den Sie während der **[!UICONTROL Listen-Update]** Aktivität.

   Das Dashboard gibt das Schema an, auf dem die Liste basiert, wie unten dargestellt:

   ![](assets/mapping_list_view.png)
