---
product: campaign
title: Integration mit Adobe Target konfigurieren
description: Integration mit Adobe Target konfigurieren
audience: integrations
content-type: reference
topic-tags: adobe-target
exl-id: ae8c680f-52a6-4d00-91cd-44d1c3807546
source-git-commit: b6e24c63ece12f25b7dafe3fede9e38b3aab2427
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 62%

---

# Integration mit Adobe Target konfigurieren{#configuring-the-integration-with-adobe-target}

![](../../assets/common.svg)


>[!CAUTION]
>
> Wenden Sie sich als gehosteter oder hybrider Kunde an Ihren Adobe-Support-Mitarbeiter, um diese Integration zu konfigurieren. Die folgenden Schritte gelten nur für On-Premise-Kunden.

## Voraussetzungen {#prerequisites}

Um die aus der Integration von Adobe Campaign und Adobe Target resultierenden Funktionen nutzen zu können, benötigen Sie folgende Elemente:

* Organisationen für Adobe Experience Cloud und Adobe Target;
* Adobe-Target-Rawbox für Adobe Campaign.

## Konfigurationen in Adobe Campaign {#configuring-adobe-campaign}

Gehen Sie wie folgt vor:

1. Installieren Sie die **[!UICONTROL Integration in Adobe Experience Cloud]** natives Paket. [Weitere Informationen](../../platform/using/working-with-data-packages.md#importing-packages)

   Mit diesem Paket erhalten Sie über Digital Asset Manager Zugriff auf die freigegebenen Assets.

1. Aktivieren Sie die Verbindung über IMS (Adobe ID-Verbindungsdienst), um in Ihren E-Mails freigegebene Bilder von Adobe Experience Cloud zu verwenden. [Weitere Informationen](../../integrations/using/about-adobe-id.md)
1. Navigieren Sie zu **[!UICONTROL Administration > Plattform > Optionen]** So konfigurieren Sie die Server- und Organisationsoptionen (Mandanten) für Adobe Target:

   ![](assets/tar_options.png)

   * **[!UICONTROL TNT_EdgeServer]** - für die Integration verwendeter Adobe-Target-Server. Diese Option ist standardmäßig ausgefüllt. Dieser Wert entspricht der Adobe-Target-**[!UICONTROL Server-Domain]** und wird vom Wert **/m2** gefolgt. Zum Beispiel: **tt.omtrdc.net/m2**.
   * **[!UICONTROL TNT_TenantName]** - Name der Adobe-Target-Organisation. Dieser Wert entspricht dem Adobe-Target-**[!UICONTROL Client]**-Namen.


>[!CAUTION]
>
>Bei hybriden und gehosteten Architekturen müssen diese Optionen auf allen Servern eingestellt werden, einschließlich [Mid-Sourcing-Server](../../installation/using/mid-sourcing-server.md) und [Ausführungsinstanz](../../message-center/using/configuring-instances.md#execution-instance).