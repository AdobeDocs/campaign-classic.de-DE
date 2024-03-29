---
product: campaign
title: Erstellung einer Testumgebung
description: Erstellung einer Testumgebung
feature: Interaction, Offers
badge-v7-only: label="v7" type="Informative" tooltip="Gilt nur für Campaign Classic v7"
audience: interaction
content-type: reference
topic-tags: advanced-parameters
exl-id: 49ac279b-bc67-4311-b0a4-0e23f2a99c52
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 80%

---

# Erstellen einer Testumgebung{#creating-a-test-environment}



Gehen Sie wie folgt vor, um eine Testumgebung (Sandbox) zu erstellen:

>[!IMPORTANT]
>
>Verwenden Sie diese Erstellungsmethode für Umgebungen nur für Testumgebungen. Verwenden Sie in allen anderen Fällen den Assistenten für das Zielgruppen-Mapping. Weiterführende Informationen dazu finden Sie unter [Angebotsumgebungen](../../interaction/using/live-design-environments.md#creating-an-offer-environment).

1. Gehen Sie in den Adobe-Campaign-Explorer und markieren Sie die Wurzel der Instanz.
1. Klicken Sie mit der rechten Maustaste und fügen Sie mithilfe des Kontextmenüs einen **[!UICONTROL Kind]**-Ordner hinzu.

   ![](assets/offer_env_creation_001.png)

1. Markieren Sie nun den zuvor erstellten Ordner und fügen Sie einen **[!UICONTROL Angbotsumgebung]**-Ordner hinzu.

   ![](assets/offer_env_creation_001bis.png)

1. Erstellen Sie auf die gleiche Weise die Unterordner und Elemente der Umgebung und führen Sie die gewünschten Tests durch.
1. Duplizieren Sie nach Abschluss Ihrer Tests die Angebote und Platzierungen in Ihrer Design-Umgebung, indem Sie die Produktionsumgebung verwenden. (Rechtsklick > **[!UICONTROL Aktionen]** > **[!UICONTROL Bereitstellen]** ).

   ![](assets/migration_interaction_5.png)
