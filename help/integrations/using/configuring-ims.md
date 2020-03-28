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
translation-type: ht
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# IMS konfigurieren{#configuring-ims}

## Voraussetzungen {#prerequisites}

Für die Integration mit IMS benötigen Sie folgende Elemente:

* Adobe-Marketing-Cloud-Organisation und IMS-Kennungen (erhältlich bei Anmeldung zur Adobe Marketing Cloud)
* Benutzer, die Sie in der Adobe Marketing Cloud hinzufügen müssen. Weiterführende Informationen hierzu finden Sie auf dieser Seite: [https://marketing.adobe.com/resources/help/de_DE/mcloud/admin_getting_started.html](https://marketing.adobe.com/resources/help/de_DE/mcloud/admin_getting_started.html)

>[!NOTE]
>
>Vergewissern Sie sich, dass Ihre Benutzer mit Adobe Marketing Cloud-Gruppen verknüpft sind, die mit Adobe Campaign synchronisiert werden. Siehe [Konfiguration des externen Kontos](#configuring-the-external-account).

## Konsole aktualisieren {#updating-the-console}

Die Nutzung dieser Funktion setzt die Installation der neuesten Version der Konsole voraus.

## Package-Installation {#installing-the-package}

Sie müssen das Package **[!UICONTROL Integration mit Adobe Experience Cloud]** installieren. Die Integration-Package-Installation entspricht der Installation eines Standard-Packages, die auf [dieser Seite](../../installation/using/installing-campaign-standard-packages.md) beschrieben wird.

![](assets/ims_6.png)

## Konfiguration des externen Kontos {#configuring-the-external-account}

Konfigurieren Sie das externe Konto für **Adobe Experience Cloud** im Knoten **[!UICONTROL Administration > Plattform > Externe Konten]**.

>[!CAUTION]
>
>Diese Konfiguration ist dem technischen Administrator vorbehalten.

![](assets/ims_5.png)

Folgende Angaben sind erforderlich:

* Informationen zur Verbindung mit dem verwendeten IMS-Server (Kennung und Secret). Wenden Sie sich diesbezüglich bitte an den Adobe-Support. Weiterführende Informationen finden Sie im Abschnitt [Häufig gestellte Fragen für Experience Cloud-Administratoren](https://marketing.adobe.com/resources/help/de_DE/mcloud/faq.html).

   Die **[!UICONTROL Callback-Server]**-Adresse muss in **https** angegeben werden. Dieses Feld enthält die URL zum Zugriff auf Ihre Adobe-Campaign-Instanz.

* Kennung der IMS-Organisations-ID (organization ID): Sie ist in Adobe Experience Cloud verfügbar (über **[!UICONTROL Administration > Experience Cloud Details]**). Diese Informationen erhalten Sie bei der Anmeldung zu Adobe Experience Cloud.
* Zuordnungsmaske: Dieses Feld dient dazu, die Syntax zu definieren, die die Synchronisation der Konfigurationsnamen aus dem Enterprise Dashboard mit den Adobe-Campaign-Gruppen ermöglicht. Wenn Sie die Syntax &quot;Campaign - tenant_id - (.*)&quot; verwenden, wird die in Adobe Campaign erstellte Sicherheitsgruppe dem Konfigurationsnamen &quot;Campaign - tenant_id - internal_name&quot; im Enterprise Dashboard zugeordnet.

   >[!CAUTION]
   >
   >Die Zuordnungsmaske ist für die fehlerfreie Herstellung der Verbindung über die Adobe ID unerlässlich.

* Informationen zur Verbindung mit Adobe Experience Cloud, insbesondere der Name des Adobe-Experience-Cloud-Mandanten.

