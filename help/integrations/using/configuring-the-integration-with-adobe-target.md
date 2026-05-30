---
product: campaign
title: Konfigurieren der Integration mit Adobe Target
description: Erfahren Sie, wie Sie die Integration mit Adobe Target konfigurieren.
feature: Target Integration
audience: integrations
content-type: reference
topic-tags: adobe-target
exl-id: ae8c680f-52a6-4d00-91cd-44d1c3807546
TQID: https://experienceleague.adobe.com/k6TljRgymSefOITPaogJdR7HOrl1BnnZm9jbkemrcyg
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
  - id: d5ef99fa-df0c-4153-bf94-105ad0724167
subfeature_v2:
  - id: cbcf4d90-26be-46e2-b16a-aebc529dc41e
  - id: df0d6518-6f49-46e2-b46e-3bcc513f553f
  - id: eb007b6d-6e57-46ab-9485-3f24d6102304
  - id: b1fd1501-3105-4d6b-b4d4-9af53126df75
topic_v2:
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 212
ht-degree: 96%

---

# Konfigurieren der Integration mit Adobe Target{#configuring-the-integration-with-adobe-target}




>[!CAUTION]
>
> Wenden Sie sich als Kunde mit gehostetem oder hybridem System an Ihren Adobe-Support-Mitarbeiter, um diese Integration zu konfigurieren. Die folgenden Schritte gelten nur für On-Premise-Kunden.

Diese Integration erfordert:

* Organisationen für Adobe Experience Cloud und Adobe Target;
* Adobe-Target-Rawbox für Adobe Campaign.

Gehen Sie wie folgt vor, um diese Integration in Adobe Campaign zu konfigurieren:

1. Installieren Sie das integrierte Paket **[!UICONTROL Integration mit Adobe Experience Cloud]**. [Weitere Informationen](../../platform/using/working-with-data-packages.md#importing-packages)

   Mit diesem Paket erhalten Sie über Digital Asset Manager Zugriff auf die freigegebenen Assets.

1. Aktivieren Sie die Verbindung über IMS (Adobe ID-Verbindungs-Service), wenn Sie in Ihren E-Mails freigegebene Bilder von Adobe Experience Cloud verwenden möchten. [Weitere Informationen](../../integrations/using/about-adobe-id.md)
1. Navigieren Sie zu **[!UICONTROL Administration > Plattform > Optionen]** und konfigurieren Sie die Server- und Organisations (Mandanten)-Optionen für Adobe Target:

   ![](assets/tar_options.png)

   * **[!UICONTROL TNT_EdgeServer]** : Für die Integration verwendeter Adobe Target-Server. Diese Option ist standardmäßig ausgefüllt. Dieser Wert entspricht der Adobe-Target-**[!UICONTROL Server-Domain]** und wird vom Wert **/m2** gefolgt. Beispiel: **tt.omtrdc.net/m2**.
   * **[!UICONTROL TNT_TenantName]** - Name der Adobe-Target-Organisation. Dieser Wert entspricht dem Adobe-Target-**[!UICONTROL Client-Namen]**.


>[!CAUTION]
>
>Bei hybriden und gehosteten Architekturen müssen diese Optionen auf allen Servern eingestellt werden, einschließlich [Mid-Sourcing-Server](../../installation/using/mid-sourcing-server.md) und [Ausführungsinstanz](../../message-center/using/configuring-instances.md#execution-instance).