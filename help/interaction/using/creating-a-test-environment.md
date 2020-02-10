---
title: Erstellung einer Testumgebung
seo-title: Erstellung einer Testumgebung
description: Erstellung einer Testumgebung
seo-description: null
page-status-flag: never-activated
uuid: 60ce42d5-6c0c-4a0d-bfd6-c778b42563a7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: advanced-parameters
discoiquuid: 7a92bc51-24cf-4ce6-bd50-a315f8f6e34e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Erstellung einer Testumgebung{#creating-a-test-environment}

Gehen Sie wie folgt vor, um eine Testumgebung (Sandbox) zu erstellen:

>[!CAUTION]
>
>Verwenden Sie diese Methode zur Umgebungserstellung nur für Testumgebungen. In allen anderen Fällen verwenden Sie den Assistenten für die Zielzuordnung. Weitere Informationen finden Sie unter [Erstellen einer Angebotsumgebung](../../interaction/using/live-design-environments.md#creating-an-offer-environment).

1. Gehen Sie in den Adobe-Campaign-Explorer und markieren Sie die Wurzel der Instanz.
1. Right-click and add a **[!UICONTROL Generic folder]** using the drop-down menus.

   ![](assets/offer_env_creation_001.png)

1. Next, go to the folder you just created and add an **[!UICONTROL Offer environment]** using the right-click menus.

   ![](assets/offer_env_creation_001bis.png)

1. Erstellen Sie auf die gleiche Weise die Unterordner und Elemente der Umgebung und führen Sie die gewünschten Tests durch.
1. Once your tests have finished and you wish to use the environment in production, duplicate the offers and spaces in your design environment. (Right-click > **[!UICONTROL Actions]** > **[!UICONTROL Deploy]** ).

   ![](assets/migration_interaction_5.png)

