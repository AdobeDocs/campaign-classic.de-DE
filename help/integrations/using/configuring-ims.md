---
title: IMS konfigurieren
seo-title: IMS konfigurieren
description: IMS konfigurieren
seo-description: null
page-status-flag: never-activated
uuid: b659d29f-2a27-4a7b-b5ca-f44c3271dd4e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
discoiquuid: 279d0548-c876-4d5f-a195-48618bd5e9d1
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0a4272ae13b469c7c17b8c3afa9748cbfbcf07ff

---


# IMS konfigurieren{#configuring-ims}

## Voraussetzungen {#prerequisites}

Für die Integration mit IMS benötigen Sie folgende Elemente:

* Sie müssen über eine Adobe Experience Cloud-Organisation und IMS-IDs verfügen (bereitgestellt, wenn Sie zum ersten Mal eine Verbindung zur Adobe Experience Cloud herstellen).
* Sie müssen Benutzer in der Experience Cloud hinzufügen. Weiterführende Informationen hierzu finden Sie auf dieser [Seite](https://docs.adobe.com/content/help/en/core-services/interface/manage-users-and-products/admin-getting-started.html).

>[!NOTE]
>
>Vergewissern Sie sich, dass Ihre Benutzer mit den Adobe Experience Cloud-Gruppen verknüpft sind, die mit Adobe Campaign synchronisiert werden. Siehe [Konfiguration des externen Kontos](#configuring-the-external-account).

## Konsole aktualisieren {#updating-the-console}

Die Nutzung dieser Funktion setzt die Installation der neuesten Version der Konsole voraus.

## Package-Installation {#installing-the-package}

Sie müssen das **[!UICONTROL Integration with the Adobe Experience Cloud]** Paket installieren. Das Installieren eines Integrationspakets ist mit dem Installieren eines Standardpakets identisch, das auf [dieser Seite](../../installation/using/installing-campaign-standard-packages.md)beschrieben wird.

![](assets/ims_6.png)

## Konfiguration des externen Kontos {#configuring-the-external-account}

Konfigurieren Sie das **Adobe Experience Cloud** -Externe Konto in **[!UICONTROL Administration > Platform > External accounts]**.

>[!CAUTION]
>
>Diese Konfiguration ist dem technischen Administrator vorbehalten.

![](assets/ims_5.png)

Folgende Angaben sind erforderlich:

* Informationen zur Verbindung mit dem verwendeten IMS-Server (Kennung und Secret). Wenden Sie sich diesbezüglich bitte an den Adobe-Support. Weiterführende Informationen finden Sie im Abschnitt [Häufig gestellte Fragen für Experience Cloud-Administratoren](https://docs.adobe.com/content/help/en/core-services/interface/manage-users-and-products/faq.html).

   Die **[!UICONTROL Callback server]** Adresse muss in **https** angegeben werden. Dieses Feld entspricht der Zugriffs-URL Ihrer Adobe Campaign-Instanz.

* Kennung der IMS-Organisations-ID (organization ID): Sie ist in Adobe Experience Cloud verfügbar (über **[!UICONTROL Administration > Experience Cloud Details]**). Diese Informationen erhalten Sie bei der Anmeldung zu Adobe Experience Cloud.
* Zuordnungsmaske: Dieses Feld dient dazu, die Syntax zu definieren, die die Synchronisation der Konfigurationsnamen aus dem Enterprise Dashboard mit den Adobe-Campaign-Gruppen ermöglicht. Wenn Sie die Syntax &quot;Campaign - tenant_id - (.*)&quot; verwenden, wird die in Adobe Campaign erstellte Sicherheitsgruppe dem Konfigurationsnamen &quot;Campaign - tenant_id - internal_name&quot; im Enterprise Dashboard zugeordnet.

   >[!CAUTION]
   >
   >Die Zuordnungsmaske ist für die fehlerfreie Herstellung der Verbindung über die Adobe ID unerlässlich.

* Informationen zur Verbindung mit Adobe Experience Cloud, insbesondere der Name des Adobe-Experience-Cloud-Mandanten.

