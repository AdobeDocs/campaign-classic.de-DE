---
product: campaign
title: IMS konfigurieren
description: Machen Sie sich mit der Verbindung über eine Adobe ID vertraut.
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
exl-id: b70ca220-1c81-4b23-b07a-a2cd694877fe
source-git-commit: 02eebe83de49ee97e573b0c47ca1fddb2195b991
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 61%

---

# IMS konfigurieren{#configuring-ims}

![](../../assets/common.svg)

>[!IMPORTANT]
>
>Die Adobe IMS-Implementierung ist technischen Administratoren von Adobe vorbehalten. Wenden Sie sich an Ihren Ansprechpartner bei Adobe, um mit der Implementierung zu beginnen.

## Voraussetzungen {#prerequisites}

Für die Integration mit IMS:

* Sie müssen über einen Namen und eine Kennung der Adobe Experience Cloud-Organisation verfügen. Die Organisations-ID finden Sie unter [diese Seite](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=de){_blank}.
* müssen Sie in Experience Cloud Benutzer hinzufügen. Weitere Informationen hierzu finden Sie unter [diese Seite](https://experienceleague.adobe.com/docs/core-services/interface/administration/admin-getting-started.html){_blank}.

>[!NOTE]
>
>Vergewissern Sie sich, dass Ihre Benutzer mit Adobe Experience Cloud-Gruppen verknüpft sind, die mit Adobe Campaign synchronisiert werden. [Weitere Informationen](#configuring-the-external-account).

## Konsole aktualisieren {#updating-the-console}

Die Nutzung dieser Funktion setzt die Installation der neuesten Version der Konsole voraus.

## Package-Installation {#installing-the-package}

Sie müssen das integrierte **[!UICONTROL Integration in Adobe Experience Cloud]** Paket. Die Installation eines Integrationspakets entspricht der Installation eines Standard-Packages, die im Abschnitt [diese Seite](../../installation/using/installing-campaign-standard-packages.md).

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

* Organisations-ID: Ihre Organisations-ID finden Sie unter [diese Seite](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html){_blank}.
* Zuordnungsmaske: In diesem Feld können Sie die Syntax definieren, mit der Konfigurationsnamen im Enterprise Dashboard mit den Gruppen in Adobe Campaign synchronisiert werden können. Wenn Sie die Syntax &quot;Campaign - tenant_id - (.&#42;)&quot;, wird die in Adobe Campaign erstellte Sicherheitsgruppe mit dem Konfigurationsnamen &quot;Campaign - tenant_id - internal_name&quot;im Enterprise Dashboard verknüpft.

   >[!CAUTION]
   >
   >Die Zuordnungsmaske ist für die fehlerfreie Herstellung der Verbindung über die Adobe ID unerlässlich.

* Informationen zur Verbindung mit Adobe Experience Cloud, insbesondere der Name des Adobe Experience Cloud-Mandanten.
