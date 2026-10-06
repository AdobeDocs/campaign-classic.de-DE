---
product: campaign
title: Erstellung einer Testumgebung
description: Erstellung einer Testumgebung
feature: Interaction, Offers
audience: interaction
content-type: reference
topic-tags: advanced-parameters
exl-id: 49ac279b-bc67-4311-b0a4-0e23f2a99c52
TQID: 'https://experienceleague.adobe.com/-V-tBgJnQ-1-W7MfUEqXQ5Zzd8GN32XT-9dWVsRa6FI'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b6fcaf36-3bc4-4604-94f3-81b5d3f41ecf
    internal-label: Offer Management
  - id: 65702805-0026-5ca1-843a-144fa79f0883
    internal-label: Interaction
  - id: ea08db70-4682-59a2-9408-9aedd9548e07
    internal-label: Offers
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '131'
ht-degree: 100%
---
# Erstellung einer Testumgebung{#creating-a-test-environment}



Gehen Sie wie folgt vor, um eine Testumgebung (Sandbox-Modus) zu erstellen:

>[!IMPORTANT]
>
>Verwenden Sie diese Erstellungsmethode für Umgebungen nur für Testumgebungen. Verwenden Sie in allen anderen Fällen den Assistenten für das Zielgruppen-Mapping. Weiterführende Informationen dazu finden Sie unter [Angebotsumgebungen](../../interaction/using/live-design-environments.md#creating-an-offer-environment).

1. Gehen Sie in den Adobe Campaign-Explorer und markieren Sie die Wurzel der Instanz.
1. Klicken Sie mit der rechten Maustaste und fügen Sie mithilfe des Kontextmenüs einen **[!UICONTROL Kind]**-Ordner hinzu.

   ![](assets/offer_env_creation_001.png)

1. Markieren Sie nun den zuvor erstellten Ordner und fügen Sie einen **[!UICONTROL Angbotsumgebung]**-Ordner hinzu.

   ![](assets/offer_env_creation_001bis.png)

1. Erstellen Sie auf die gleiche Weise die Unterordner und Elemente der Umgebung und führen Sie die gewünschten Tests durch.
1. Nach Abschluss Ihrer Tests können Sie die in der Testumgebung enthaltenen Elemente zur tatsächlichen Verwendung freigeben. Duplizieren Sie hierzu die Angebote und Platzierungen in Ihre Live-Umgebung (Rechtsklick > **[!UICONTROL Aktionen]** > **[!UICONTROL Bereitstellen]** ).

   ![](assets/migration_interaction_5.png)
