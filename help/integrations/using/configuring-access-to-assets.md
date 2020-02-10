---
title: Zugriff auf Assets konfigurieren
seo-title: Zugriff auf Assets konfigurieren
description: Zugriff auf Assets konfigurieren
seo-description: null
page-status-flag: never-activated
uuid: dc8c0016-92c8-41ab-98c6-d0fe0bfd6c41
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: asset-sharing
discoiquuid: df1b6ead-3471-404a-b43f-a68fb86cb14c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0745b9c9d72538b8573ad18ff4054ecf788905f2

---


# Zugriff auf Assets konfigurieren{#configuring-access-to-assets}

Der folgende Abschnitt beschreibt die in Adobe Campaign erforderlichen Konfigurationsschritte, um die Funktionen der Integration mit Assets Core Service bzw. der Adobe-Experience-Manager-Assets-Bibliothek nutzen zu können.

>[!CAUTION]
>
>Die Integrationen können sich mitunter gegenseitig beeinflussen. Lesen Sie deshalb aufmerksam folgende Informationen, bevor Sie irgendeine Konfiguration vornehmen.

* Integration mit **Experience Cloud-Assets**: Mit dieser Integration können Sie Bilder aus Ihrer Adobe Experience Cloud-Bibliothek einfügen. Abhängig von Ihrem Konfigurations- und Lizenzmodell kann es sich bei dieser Bibliothek um den Hauptdienst Assets on Demand handeln. Diese Integration muss durch Installieren des **[!UICONTROL Integration with the Adobe Experience Cloud]** integrierten Pakets in Adobe Campaign eingerichtet werden.
* Integration mit **AEM Assets**: Mit dieser Integration können Sie Bilder aus der Asset-Bibliothek von Adobe Experience Manager einfügen. Diese Integration muss durch Installieren des **[!UICONTROL AEM Integration]** integrierten Pakets in Adobe Campaign eingerichtet werden.

>[!NOTE]
>
>Wenn die beiden Pakete (**[!UICONTROL AEM Integration]** und **[!UICONTROL Integration with the Adobe Experience Cloud]** ) installiert sind, können nur die in der Adobe Experience Cloud-Bibliothek verfügbaren Assets verwendet werden. Um auch auf die Assets in Ihrer AEM Assets-Bibliothek zugreifen zu können, müssen Sie AEM Assets und Adobe Experience Cloud synchronisieren. Die Assets in AEM Assets stehen dann auch in der Adobe Experience Cloud-Bibliothek zur Verfügung. Weitere Informationen zum Synchronisieren von AEM Assets und Adobe Experience Cloud finden Sie in der [ausführlichen Dokumentation](https://docs.adobe.com/docs/en/aod/overview/collaborating/aem-assets-aod-sync.html).

## Integration mit Experience Cloud Assets {#integrating-with-experience-cloud-assets}

Um die aus der Integration von Adobe Campaign und Experience Cloud Assets resultierenden Funktionen nutzen zu können, benötigen Sie folgende Elemente:

* Adobe-Experience-Cloud-Organisation,
* Aktivierten IMS-Authentifizierungsmodus von Adobe

Um die Verbindung zwischen Adobe Campaign und Adobe Experience Cloud zu aktivieren, konfigurieren Sie die Verbindung über IMS (Adobe-ID-Verbindungsservice). Weiterführende Informationen zu dieser Konfiguration finden Sie im Dokument [Verbindung mit Adobe ID](../../integrations/using/about-adobe-id.md). Sie umfasst:

* Installing the **[!UICONTROL Integration with the Adobe Experience Cloud]** package.
* die Konfiguration eines externen Adobe-Experience-Cloud-Kontos.

>[!NOTE]
>
>Auf die mit dieser Integration einhergehenden Funktionen können ausschließlich Benutzer zugreifen, die sich über IMS mit ihrer Adobe ID anmelden.

## Integration mit AEM Assets {#integrating-with-aem-assets}

Vor der Integration von AEM Assets mit Adobe Campaign ist zunächst die Integration von Adobe Experience Manager und Adobe Campaign zu konfigurieren. Diese Konfiguration umfasst insbesondere:

* Installieren des **[!UICONTROL AEM Integration]** integrierten Pakets
* Konfiguration eines externen Kontos speziell für Adobe Experience Manager

Über die Integration von Adobe Campaign und Adobe Experience Manager erfahren Sie im [entsprechenden Handbuch](../../integrations/using/about-adobe-experience-manager.md).

Nach der Integration können Sie eine neue Versandvorlage in Adobe Campaign konfigurieren, um die AEM-Assets-Bibliothek zu verwenden. Gehen Sie dazu folgendermaßen vor:

1. Erstellen Sie eine neue Versandvorlage oder duplizieren Sie eine vorhandene. Weiterführende Informationen zu Versandvorlagen finden Sie auf [dieser Seite](../../delivery/using/about-templates.md).
1. Bearbeiten Sie die **Eigenschaften** dieser Vorlage.
1. Legen Sie auf der **[!UICONTROL Advanced]** Registerkarte **[!UICONTROL Content editing mode]** die Einstellung **DCE** fest.
1. Select the external **[!UICONTROL AEM account]** that you need to use to access your AEM Assets library.

   ![](assets/dam_aem_assets1.png)

Wenn Sie Bilder basierend auf dieser Vorlage in den Inhalt einer Bereitstellung einfügen, können Sie mit der **[!UICONTROL Select a shared asset]** Option in der AEM Assets-Bibliothek nach Bildern suchen. Weitere Informationen finden Sie in [diesem Abschnitt](../../integrations/using/inserting-a-shared-asset.md).

>[!NOTE]
>
>Wenn das **[!UICONTROL Integration with the Adobe Experience Cloud]** Paket auch auf Ihrer Adobe Campaign-Instanz installiert ist, können Sie nur die in der Adobe Experience Cloud-Bibliothek verfügbaren Assets verwenden. Um auch auf die Assets in Ihrer AEM Assets-Bibliothek zugreifen zu können, müssen Sie AEM Assets und Adobe Experience Cloud synchronisieren. Die Assets in AEM Assets stehen dann auch in der Adobe Experience Cloud-Bibliothek zur Verfügung. In diesem Fall müssen Sie keine bestimmte Bereitstellungsvorlage erstellen. Weitere Informationen zur Synchronisierung zwischen AEM Assets und Adobe Experience Cloud finden Sie in der [ausführlichen Dokumentation](https://docs.adobe.com/docs/en/aod/overview/collaborating/aem-assets-aod-sync.html).

