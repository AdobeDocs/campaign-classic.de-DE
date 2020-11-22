---
solution: Campaign Classic
product: campaign
title: Integration mit Adobe Target konfigurieren
description: Integration mit Adobe Target konfigurieren
audience: integrations
content-type: reference
topic-tags: adobe-target
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 100%

---


# Integration mit Adobe Target konfigurieren{#configuring-the-integration-with-adobe-target}

## Voraussetzungen {#prerequisites}

Um die aus der Integration von Adobe Campaign und Adobe Target resultierenden Funktionen nutzen zu können, benötigen Sie folgende Elemente:

* Organisationen für Adobe Experience Cloud und Adobe Target;
* Adobe-Target-Rawbox für Adobe Campaign.

## Konfigurationen in Adobe Campaign {#configuring-adobe-campaign}

Gehen Sie wie folgt vor:

1. Installieren Sie das Standard-Package **[!UICONTROL Integration mit Adobe Experience Cloud]**. Die Integrations-Package-Installation entspricht der Installation eines Standard-Packages, die im Abschnitt [Package-Import](../../platform/using/working-with-data-packages.md#importing-packages) beschrieben wird. Dies ermöglicht den Zugriff auf über Digital Asset Manager freigegebene Assets.
1. Aktivieren Sie die Verbindung über IMS (Adobe-ID-Verbindungsservice), wenn Sie in Ihren E-Mails freigegebene Bilder von Adobe Experience Cloud verwenden möchten. Lesen Sie diesbezüglich den Abschnitt [IMS](../../integrations/using/about-adobe-id.md).
1. Gehen Sie in den Knoten **[!UICONTROL Administration > Platform > Options]** und konfigurieren Sie die Server- und Organisations (Mandanten)-Optionen für Adobe Target:

   * **[!UICONTROL TNT_EdgeServer]** - für die Integration verwendeter Adobe-Target-Server. Diese Option ist standardmäßig ausgefüllt. Dieser Wert entspricht der Adobe-Target-**[!UICONTROL Server-Domain]** und wird vom Wert **/m2** gefolgt. Zum Beispiel: **tt.omtrdc.net/m2**.
   * **[!UICONTROL TNT_TenantName]** - Name der Adobe-Target-Organisation. Dieser Wert entspricht dem Adobe-Target-**[!UICONTROL Client]**-Namen.

   ![](assets/tar_options.png)

