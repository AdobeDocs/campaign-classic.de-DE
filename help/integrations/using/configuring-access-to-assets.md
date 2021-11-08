---
product: campaign
title: Zugriff auf Assets konfigurieren
description: Zugriff auf Assets konfigurieren
audience: integrations
content-type: reference
topic-tags: asset-sharing
exl-id: f3897a40-b080-47e5-9e31-4d861c1bacd5
source-git-commit: bd9f035db1cbad883e1f27fe901e34dfbc9c1229
workflow-type: tm+mt
source-wordcount: '540'
ht-degree: 100%

---

# Zugriff auf Assets konfigurieren{#configuring-access-to-assets}

![](../../assets/common.svg)

Dieser Abschnitt beschreibt die in Adobe Campaign erforderlichen Konfigurationsschritte, um die Funktionen der Integration mit Assets Core Service bzw. der Adobe Experience Manager Assets-Bibliothek nutzen zu können.

>[!CAUTION]
>
>Die Integrationen können sich mitunter gegenseitig beeinflussen. Lesen Sie deshalb aufmerksam folgende Informationen, bevor Sie irgendeine Konfiguration vornehmen.

* Bei der Integration mit **Experience Cloud Assets** besteht die Möglichkeit, Bilder aus Ihrer Adobe Experience Cloud-Bibliothek zu verwenden. Diese Integration muss eingerichtet werden, indem das integrierte Package **[!UICONTROL Integration mit Adobe Experience Cloud]** in Adobe Campaign installiert wird.
* Bei der Integration mit **AEM Assets** besteht die Möglichkeit, Bilder aus Ihrer Adobe Experience Manager Assets-Bibliothek zu verwenden. Diese Integration muss eingerichtet werden, indem das integrierte Package **[!UICONTROL Integration mit Adobe Experience Manager]** in Adobe Campaign installiert wird. Beachten Sie, dass diese Integration ab Adobe Experience Manager 6.4 nicht mehr verfügbar ist.

>[!NOTE]
>
>Wenn die beiden Packages (**[!UICONTROL Integration mit Adobe Experience Manager]** und **[!UICONTROL Integration mit Adobe Experience Cloud]**) installiert sind, können nur die in der Adobe Experience Cloud-Bibliothek verfügbaren Assets verwendet werden.

## Integration mit Experience Cloud Assets {#integrating-with-experience-cloud-assets}

Um die aus der Integration von Adobe Campaign und Experience Cloud Assets resultierenden Funktionen nutzen zu können, benötigen Sie folgende Elemente:

* Adobe Experience Cloud-Organisation,
* Aktivierten IMS-Authentifizierungsmodus von Adobe

Um die Verbindung zwischen Adobe Campaign und Adobe Experience Cloud zu aktivieren, konfigurieren Sie die Verbindung über IMS (Adobe-ID-Verbindungsservice). Weiterführende Informationen zu dieser Konfiguration finden Sie im Dokument [Verbindung mit Adobe ID](../../integrations/using/about-adobe-id.md). Sie umfasst:

* Die Installation des Packages **[!UICONTROL Integration mit Adobe Experience Cloud]**,
* die Konfiguration eines externen Adobe Experience Cloud-Kontos.

>[!NOTE]
>
>Auf die mit dieser Integration einhergehenden Funktionen können ausschließlich Benutzer zugreifen, die sich über IMS mit ihrer Adobe ID anmelden.

## Integration mit AEM Assets {#integrating-with-aem-assets}


>[!CAUTION]
>
>Diese Funktion wurde ab Adobe Experience Manager 6.4 eingestellt. [Weitere Informationen](https://experienceleague.adobe.com/docs/experience-manager-64/release-notes/deprecated-removed-features.html?lang=de#removed-features)

Vor der Integration von AEM Assets mit Adobe Campaign ist zunächst die Integration von Adobe Experience Manager und Adobe Campaign zu konfigurieren. Diese Konfiguration umfasst insbesondere:

* Installation des integrierten Packages **[!UICONTROL Integration mit Adobe Experience Manager]**
* Konfiguration eines externen Kontos speziell für Adobe Experience Manager

Über die Integration von Adobe Campaign und Adobe Experience Manager erfahren Sie im [entsprechenden Handbuch](../../integrations/using/about-adobe-experience-manager.md).

Nach der Integration können Sie eine neue Versandvorlage in Adobe Campaign konfigurieren, um die AEM-Assets-Bibliothek zu verwenden. Gehen Sie dazu folgendermaßen vor:

1. Erstellen Sie eine neue Versandvorlage oder duplizieren Sie eine vorhandene. Weiterführende Informationen zu Versandvorlagen finden Sie auf [dieser Seite](../../delivery/using/about-templates.md).
1. Bearbeiten Sie die **Eigenschaften** dieser Vorlage.
1. Wählen Sie im Tab **[!UICONTROL Erweitert]** für **[!UICONTROL Inhaltserstellung]** die Option **DCE**.
1. Wählen Sie das externe **[!UICONTROL AEM-Konto]**, mit dem Sie auf Ihre AEM-Assets-Bibliothek zugreifen.

   ![](assets/dam_aem_assets1.png)

Beim Einfügen von Bildern in Versandinhalte auf der Basis dieser Vorlage haben Sie nun die Möglichkeit, über die Option **[!UICONTROL Freigegebenes Asset auswählen]** die AEM-Assets-Bibliothek nach Bildern zu durchsuchen. Weiterführende Informationen dazu finden Sie in [diesem Abschnitt](../../integrations/using/inserting-a-shared-asset.md).

>[!NOTE]
>
>Wenn das Package **[!UICONTROL Integration mit Adobe Experience Cloud]** auch auf Ihrer Adobe Campaign-Instanz installiert ist, können Sie nur die in der Adobe Experience Cloud-Bibliothek verfügbaren Assets verwenden. Um auch auf die Assets in Ihrer AEM Assets-Bibliothek zuzugreifen, müssen Sie AEM Assets und Adobe Experience Cloud synchronisieren. Die Assets in AEM Assets werden dann auch in der Adobe Experience Cloud-Bibliothek verfügbar sein. In diesem Fall müssen Sie keine spezielle Versandvorlage erstellen.
