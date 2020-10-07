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
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 22%

---


# Erstellen einer Profilliste mit einem Workflow{#creating-a-profile-list-with-a-workflow}

Um eine Liste des Typs &quot; **[!UICONTROL Liste]** &quot;basierend auf der neuen Empfänger-Tabelle zu erstellen, müssen Sie einen Targeting-Arbeitsablauf erstellen, der die Liste generiert. Weitere Informationen zu Listen in der Kampagne finden Sie in [diesem Abschnitt](../../platform/using/creating-and-managing-lists.md#about-lists-in-adobe-campaign).

1. Wechseln Sie zum Knoten **[!UICONTROL Profile und Zielgruppen > Aufträge > Targeting Workflows]** des Explorers.
1. Erstellen Sie einen neuen Zielgruppen-Workflow.
1. Platzieren Sie eine **Abfrage** -Aktivität gefolgt von einer **Liste-Update** -Aktivität.

   ![](assets/mapping_create_list_workflow01.png)

1. Klicken Sie bei Dublette auf die Aktivität **Abfrage** und dann auf Abfrage **** bearbeiten, um eine Zielgruppendimension auf Grundlage des Schemas der neuen Empfänger-Tabelle auszuwählen (in unserem Beispiel: **Individuell**). Klicken Sie zur Bestätigung auf **[!UICONTROL Beenden]**.

   ![](assets/mapping_create_list_workflow03.png)

1. Klicken Sie mit der Dublette auf die Aktivität zum Aktualisieren **der** Liste und wählen Sie dann bei Bedarf das Optionsfeld Liste **[!UICONTROL erstellen (Berechneter Name)]** .

   ![](assets/mapping_create_list_workflow02.png)

1. Wählen Sie den Erstellungsordner für die neue Liste aus.
1. Führen Sie den Workflow aus, um die Liste zu erstellen.
1. Ansicht des Ergebnisses in dem Knoten der Struktur, den Sie während der Aktivität zur Aktualisierung der **[!UICONTROL Liste]** ausgewählt haben.

   Das Dashboard gibt das Schema an, auf dem die Liste basiert, wie nachfolgend gezeigt:

   ![](assets/mapping_list_view.png)

>[!NOTE]
>
>Sie können auch das Video zum [Erstellen einer Liste von Empfängern](https://docs.adobe.com/content/help/de-DE/campaign-classic-learn/tutorials/getting-started/creating-a-list-of-recipients.html) lesen.

