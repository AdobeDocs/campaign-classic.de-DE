---
product: campaign
title: IMS konfigurieren
description: Machen Sie sich mit der Verbindung über eine Adobe ID vertraut.
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
exl-id: b70ca220-1c81-4b23-b07a-a2cd694877fe
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 100%

---

# IMS konfigurieren{#configuring-ims}



>[!IMPORTANT]
>
>Die Adobe IMS-Implementierung ist technischen Administratoren von Adobe vorbehalten. Wenden Sie sich an Ihren Ansprechpartner bei Adobe, um mit der Implementierung zu beginnen.

## Voraussetzungen {#prerequisites}

Damit Sie die Integration mit IMS nutzen können:

* Müssen Sie über einen Organisationsnamen und eine Organisations-ID für Adobe Experience Cloud verfügen. Auf [dieser Seite](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=de){_blank} erfahren Sie, wie Sie Ihre Organisations-ID finden.
* Müssen Sie in Experience Cloud Benutzer hinzufügen. Weitere Informationen hierzu finden Sie auf [dieser Seite](https://experienceleague.adobe.com/docs/core-services/interface/administration/admin-getting-started.html?lang=de){_blank}.

>[!NOTE]
>
>Vergewissern Sie sich, dass Ihre Benutzer mit Adobe Experience Cloud-Gruppen verknüpft sind, die mit Adobe Campaign synchronisiert werden. [Weitere Informationen](#configuring-the-external-account).

## Konsole aktualisieren {#updating-the-console}

Die Nutzung dieser Funktion setzt die Installation der neuesten Version der Konsole voraus.

## Package-Installation {#installing-the-package}

Sie müssen das integrierte Paket **[!UICONTROL Integration mit Adobe Experience Cloud]** installieren. Die Installation eines Integrationspakets erfolgt auf die gleiche Weise wie die Installation eines Standardpakets, was auf [dieser Seite](../../installation/using/installing-campaign-standard-packages.md) beschrieben wird.

![](assets/ims_6.png)

## Konfiguration des externen Kontos {#configuring-the-external-account}

Konfigurieren Sie das externe Konto für **Adobe Experience Cloud** im Knoten **[!UICONTROL Administration > Plattform > Externe Konten]**.

>[!CAUTION]
>
>Diese Konfiguration ist dem technischen Administrator vorbehalten.

![](assets/ims_5.png)

Folgende Angaben sind erforderlich:

* Informationen zur Verbindung mit dem verwendeten IMS-Server (Kennung und Secret). Wenden Sie sich diesbezüglich bitte an den Adobe-Support. Weiterführende Informationen finden Sie im Abschnitt [Häufig gestellte Fragen für Experience Cloud-Administratoren](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/faq.html?lang=de).

   Die **[!UICONTROL Callback-Server]**-Adresse muss in **https** angegeben werden. Dieses Feld enthält die URL zum Zugriff auf Ihre Adobe Campaign-Instanz.

* Organisations-ID: Auf [dieser Seite](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=de){_blank} erfahren Sie, wie Sie Ihre Organisations-ID finden.
* Zuordnungsmaske: In diesem Feld können Sie die Syntax festlegen, mit der Konfigurationsnamen in Enterprise Dashboard mit den Gruppen in Adobe Campaign synchronisiert werden können. Wenn Sie die Syntax &quot;Campaign - tenant_id - (.&#42;)&quot; verwenden, wird die in Adobe Campaign erstellte Sicherheitsgruppe mit dem Konfigurationsnamen &quot;Campaign - tenant_id - internal_name&quot; in Enterprise Dashboard verknüpft.

   >[!CAUTION]
   >
   >Die Zuordnungsmaske ist für die fehlerfreie Herstellung der Verbindung über die Adobe ID unerlässlich.

* Informationen zur Verbindung mit Adobe Experience Cloud, insbesondere der Name des Adobe Experience Cloud-Mandanten.
