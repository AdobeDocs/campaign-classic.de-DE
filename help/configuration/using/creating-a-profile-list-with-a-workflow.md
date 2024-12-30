---
product: campaign
title: Erstellen einer Profilliste mit einem Workflow
description: Erfahren Sie, wie Sie in einem Workflow eine Profilliste erstellen
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
feature: Workflows, Profiles
role: User
exl-id: 6b308299-4d07-4c9e-bd2f-a0860c41cf02
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 17%

---

# Erstellen einer Profilliste mit einem Workflow{#creating-a-profile-list-with-a-workflow}


Um eine Liste vom Typ **[!UICONTROL Liste]** basierend auf der neuen Empfängertabelle zu erstellen, müssen Sie einen Zielgruppen-Workflow erstellen, der die Liste generiert.

Weitere Informationen zu Listen in Campaign finden Sie [diesem Abschnitt](../../platform/using/creating-and-managing-lists.md#about-lists-in-adobe-campaign).

![](assets/do-not-localize/how-to-video.png) [Entdecken Sie diese Funktion im Video](../../platform/using/creating-and-managing-lists.md#create-list-in-a-wf-video)

Gehen Sie wie folgt vor, um einen Zielgruppen-Workflow zu erstellen und die Empfänger in einer benutzerdefinierten Empfängertabelle zu aktualisieren:

1. Wechseln Sie **[!UICONTROL Knoten Profile und Zielgruppen > Aufträge > Zielgruppen]** des Explorers.
1. Erstellen Sie einen neuen Zielgruppen-Workflow.
1. Platzieren Sie eine **Abfrage**-Aktivität gefolgt von einer **Listen-Update**-Aktivität.

   ![](assets/mapping_create_list_workflow01.png)

1. Doppelklicken Sie auf die Aktivität **Abfrage** und dann auf **[!UICONTROL Abfrage bearbeiten]**, um eine Zielgruppendimension basierend auf dem Schema der neuen Empfängertabelle auszuwählen (in unserem Beispiel: **Individuell**). Klicken Sie zur Bestätigung auf **[!UICONTROL Beenden]**.

   ![](assets/mapping_create_list_workflow03.png)

1. Doppelklicken Sie auf die Aktivität **Listen-Update** und wählen Sie dann das Optionsfeld **[!UICONTROL Bei Bedarf Liste erstellen (Berechneter Name)]** aus.

   ![](assets/mapping_create_list_workflow02.png)

1. Wählen Sie den Erstellungsordner für die neue Liste.
1. Führen Sie den Workflow aus, um die Liste zu erstellen.
1. Das Ergebnis im Knoten der Baumstruktur anzeigen, den Sie während der Aktivität **[!UICONTROL Listen-Update]** ausgewählt haben.

   Das Dashboard gibt das Schema an, auf dem die Liste basiert, wie unten dargestellt:

   ![](assets/mapping_list_view.png)
