---
solution: Campaign Classic
product: campaign
title: Erstellung einer Testumgebung
description: Erstellung einer Testumgebung
audience: interaction
content-type: reference
topic-tags: advanced-parameters
exl-id: 49ac279b-bc67-4311-b0a4-0e23f2a99c52
translation-type: ht
source-git-commit: 6854d06f8dc445b56ddfde7777f02916a60f2b63
workflow-type: ht
source-wordcount: '126'
ht-degree: 100%

---

# Erstellung einer Testumgebung{#creating-a-test-environment}

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
1. Nach Abschluss Ihrer Tests können Sie die in der Testumgebung enthaltenen Elemente zur tatsächlichen Verwendung freigeben. Duplizieren Sie hierzu die Angebote und Platzierungen in Ihre Live-Umgebung (Rechtsklick > **[!UICONTROL Aktionen]** > **[!UICONTROL Freigeben]** ).

   ![](assets/migration_interaction_5.png)
