---
product: campaign
title: IMS konfigurieren
description: Machen Sie sich mit der Verbindung über eine Adobe ID vertraut.
feature: Configuration
badge-v7: label="v7" type="Informative" tooltip="Gilt für Campaign Classic v7"
badge-v7-prem: label="On-Premise und Hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Gilt nur für Hybrid- und On-Premise-Bereitstellungen"
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
exl-id: b70ca220-1c81-4b23-b07a-a2cd694877fe
source-git-commit: 49271e291953483ee14709b26ec053217a336718
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 52%

---

# IMS konfigurieren{#configuring-ims}

>[!IMPORTANT]
>
>Als Campaign-Benutzer für gehostete oder verwaltete Dienste gehört Ihre Adobe IMS-Implementierung zu Adobe. Die unten beschriebenen Schritte gelten nur für On-Premise- und Hybrid-Kunden.
> Die Adobe IMS-Implementierung darf nur von technischen Adobe-Administratoren durchgeführt werden. Wenden Sie sich an Ihren Adobe-Support-Mitarbeiter, um den Implementierungsprozess zu starten.

## Voraussetzungen {#prerequisites}

* Müssen Sie über einen Organisationsnamen und eine Organisations-ID für Adobe Experience Cloud verfügen. Auf [dieser Seite](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=de){_blank} erfahren Sie, wie Sie Ihre Organisations-ID finden.
* Müssen Sie in Experience Cloud Benutzer hinzufügen. Weitere Informationen hierzu finden Sie auf [dieser Seite](https://experienceleague.adobe.com/docs/core-services/interface/administration/admin-getting-started.html?lang=de){_blank}.

>[!NOTE]
>
>Vergewissern Sie sich, dass Ihre Benutzer mit Adobe Experience Cloud-Gruppen verknüpft sind, die mit Adobe Campaign synchronisiert werden. [Weitere Informationen](#configuring-the-external-account).

## Konsole aktualisieren {#updating-the-console}

Um diese Funktion verwenden zu können, müssen Sie die neueste Version der Client-Konsole installieren.

## Package-Installation {#installing-the-package}

Sie müssen das integrierte Paket **[!UICONTROL Integration mit Adobe Experience Cloud]** installieren. Die Installation eines Integrationspakets erfolgt auf die gleiche Weise wie die Installation eines Standardpakets, was auf [dieser Seite](../../installation/using/installing-campaign-standard-packages.md) beschrieben wird.

![](assets/ims_6.png)

## Konfiguration des externen Kontos {#configuring-the-external-account}

Konfigurieren Sie das externe Konto für **Adobe Experience Cloud** im Knoten **[!UICONTROL Administration > Plattform > Externe Konten]**.

![](assets/ims_5.png)

Folgende Angaben sind erforderlich:

* Verbindungsinformationen für den verwendeten IMS-Server (Kennung und Geheimnis). Diese Informationen werden vom Team der Adobe-Kundenunterstützung bereitgestellt. Weitere Informationen finden Sie im Abschnitt [Häufig gestellte Fragen für Adobe Experience Cloud-Administratoren](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/faq.html?lang=de).

  Die **[!UICONTROL Callback-Server]**-Adresse muss in **https** angegeben werden. Dieses Feld enthält die URL zum Zugriff auf Ihre Adobe Campaign-Instanz.

* Organisations-ID: Auf [dieser Seite](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=de){_blank} erfahren Sie, wie Sie Ihre Organisations-ID finden.

* Zuordnungsmaske: In diesem Feld können Sie die Syntax definieren, mit der Konfigurationsnamen im Enterprise Dashboard mit den Gruppen in Adobe Campaign synchronisiert werden können. Wenn Sie die Syntax &quot;Campaign - tenant_id - (.&#42;)&quot;, wird die in Adobe Campaign erstellte Sicherheitsgruppe mit dem Konfigurationsnamen &quot;Campaign - tenant_id - internal_name&quot;im Enterprise Dashboard verknüpft.

* Adobe Experience Cloud-Verbindungsinformationen, der Name des Adobe Experience Cloud-Mandanten.
