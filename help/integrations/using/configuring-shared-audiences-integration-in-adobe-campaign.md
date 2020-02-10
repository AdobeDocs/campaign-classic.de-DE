---
title: Integration mit freigegebenen Zielgruppen in Adobe Campaign konfigurieren
seo-title: Integration mit freigegebenen Zielgruppen in Adobe Campaign konfigurieren
description: Integration mit freigegebenen Zielgruppen in Adobe Campaign konfigurieren
seo-description: null
page-status-flag: never-activated
uuid: 6ed137e4-027f-4eb0-a0b5-4beb7deef51f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: audience-sharing
discoiquuid: 4443b0ca-80c6-467d-a4df-50864aae8496
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 6ae45cbd87fc0152fc654202e03501fc8d2abd06

---


# Integration mit freigegebenen Zielgruppen in Adobe Campaign konfigurieren{#configuring-shared-audiences-integration-in-adobe-campaign}

Nach Übermittlung dieses Antrags wird dieser von Adobe bearbeitet. Sie werden ersucht, Informationen bereitzustellen, und darauf hingewiesen, dass Sie die Konfiguration abschließen müssen:

1. [Schritt 1: Konfigurieren bzw. überprüfen Sie die externen Konten in Adobe Campaign.](#step-1--configure-or-check-the-external-accounts-in-adobe-campaign)
1. [Schritt 2: Konfigurieren Sie die Datenquellen.](#step-2--configure-the-data-source)
1. [Schritt 3: Konfigurieren Sie den Campaign Tracking Server.](#step-3--configure-campaign-tracking-server)
1. [Schritt 4: Konfigurieren Sie den Visitor-ID-Dienst.](#step-4--configure-the-visitor-id-service)

## Schritt 1: Konfigurieren bzw. überprüfen Sie die externen Konten in Adobe Campaign.   {#step-1--configure-or-check-the-external-accounts-in-adobe-campaign}

Gehen Sie folgendermaßen vor, um die externen Konten in Adobe Campaign zu konfigurieren bzw. zu überprüfen:

1. Click the **[!UICONTROL Explorer]** icon.
1. Go to **[!UICONTROL Administration > Platform > External accounts]**. Die entsprechenden SFTP-Konten sollten von Adobe konfiguriert und die erforderlichen Informationen sollten Ihnen übermittelt worden sein.

   * **[!UICONTROL importSharedAudience]** : SFTP-Konto für den Zielgruppen-Import.
   * **[!UICONTROL exportSharedAudience]** : SFTP-Konto für den Zielgruppen-Export.
   ![](assets/aam_config_1.png)

1. Füllen Sie das **[!UICONTROL Server]**-Feld aus: die Domain **ftp-out.demdex.com** für das externe Importkonto und die Domain **ftp-in.demdex.com** für das externe Exportkonto.

   Beachten Sie dabei, dass ein Export aus Campaign ein Import in Audience Manager oder People core service ist.

   >[!NOTE]
   >
   >Wenn Sie S3 verwenden, geben Sie die folgende **[!UICONTROL AWS S3 Account Server]** Syntax ein:\
   `<S3bucket name>.s3.amazonaws.com/<s3object path>`\
   For more information on how to configure your S3 account, refer to this [page](../../platform/using/external-accounts.md#amazon-simple-storage-service--s3--external-account).

   ![](assets/aam_config_2.png)

1. Fügen Sie die von Adobe bereitgestellten **[!UICONTROL Account]** und **[!UICONTROL Password]** -Dienste hinzu.

Ihre externen Konten sind somit konfiguriert.

## Schritt 2: Konfigurieren Sie die Datenquellen.{#step-2--configure-the-data-source}

Die **Empfänger - Besucher-ID** wird innerhalb von Audience Manager erstellt. Dies ist eine native Datenquelle, die standardmäßig für die Besucher-ID konfiguriert wird. In Campaign erstellte Segmente werden ebenfalls Teil dieser Datenquelle sein.

So konfigurieren Sie die **[!UICONTROL Recipient - Visitor ID]** Datenquelle:

1. Wählen Sie aus der **[!UICONTROL Explorer]** Node **[!UICONTROL Administration > Platform > AMC Data sources]**.
1. Auswählen **[!UICONTROL Recipient - Visitor ID]**.
1. Geben Sie die **[!UICONTROL Data Source ID]** und die von Adobe bereitgestellten **[!UICONTROL AAM Destination ID]** Werte ein.

   ![](assets/aam_config_3.png)

## Schritt 3: Konfigurieren Sie den Campaign Tracking Server.   {#step-3--configure-campaign-tracking-server}

Für die Konfiguration der Integration mit People Core Service oder Audience Manager muss auch der Campaign Tracking Server konfiguriert werden.

Der Campaign Tracking Server muss in der Domain (CNAME) registriert sein. Weitere Informationen zur Delegation von Domains finden Sie in [diesem Artikel](https://helpx.adobe.com/campaign/kb/domain-name-delegation.html).

## Schritt 4: Konfigurieren Sie den Visitor-ID-Dienst.{#step-4--configure-the-visitor-id-service}

Falls Ihr Visitor-ID-Dienst nie in Ihren Web-Parametern und Webseiten konfiguriert wurde, finden Sie im folgenden [Dokument](https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid-setup-aam-analytics.html) oder im folgenden [Video](https://helpx.adobe.com/marketing-cloud/how-to/email-marketing.html#step-two) nähere Informationen dazu .

Die Konfiguration und Einrichtung sind jetzt abgeschlossen. Die Integration kann somit zum Import und Export von Audiences und Segmenten verwendet werden.
