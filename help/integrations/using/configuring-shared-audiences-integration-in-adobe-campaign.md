---
title: Integration mit freigegebenen Zielgruppen in Adobe Campaign konfigurieren
description: Informationen zum Konfigurieren der Integration freigegebener Audiencen
page-status-flag: never-activated
uuid: 6ed137e4-027f-4eb0-a0b5-4beb7deef51f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: audience-sharing
discoiquuid: 4443b0ca-80c6-467d-a4df-50864aae8496
translation-type: tm+mt
source-git-commit: cb2fb5a338220c54aba96b510a7371e520c2189e
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 98%

---


# Integration mit freigegebenen Zielgruppen in Adobe Campaign konfigurieren{#configuring-shared-audiences-integration-in-adobe-campaign}

Nach Übermittlung dieses Antrags wird dieser von Adobe bearbeitet. Sie werden ersucht, Informationen bereitzustellen, und darauf hingewiesen, dass Sie die Konfiguration abschließen müssen:

1. [Schritt 1: Konfigurieren bzw. überprüfen Sie die externen Konten in Adobe Campaign.](#step-1--configure-or-check-the-external-accounts-in-adobe-campaign)
1. [Schritt 2: Konfigurieren Sie die Datenquellen.](#step-2--configure-the-data-source)
1. [Schritt 3: Konfigurieren Sie den Campaign Tracking Server.](#step-3--configure-campaign-tracking-server)
1. [Schritt 4: Konfigurieren Sie den Visitor-ID-Dienst.](#step-4--configure-the-visitor-id-service)

>[!IMPORTANT]
>
>Wenn Sie die demdex-Domain verwenden und die Syntax **ftp-out.demdex.com** für das externe Importkonto und **ftp-in.demdex.com** für das externe Exportkonto befolgen, müssen Sie Ihre Implementierung entsprechend anpassen und zum Amazon S3-Connector (Simple Storage Service) wechseln, um Daten zu importieren oder zu exportieren. Weitere Informationen zur Konfiguration von externen Konten mit Amazon S3 finden Sie in [diesem Abschnitt](../../integrations/using/configuring-shared-audiences-integration-in-adobe-campaign.md#step-1--configure-or-check-the-external-accounts-in-adobe-campaign).

## Schritt 1: Konfigurieren bzw. überprüfen Sie die externen Konten in Adobe Campaign.     {#step-1--configure-or-check-the-external-accounts-in-adobe-campaign}

Gehen Sie folgendermaßen vor, um die externen Konten in Adobe Campaign zu konfigurieren bzw. zu überprüfen:

1. Wählen Sie das **[!UICONTROL Explorer]**-Symbol aus.
1. Gehen Sie zu **[!UICONTROL Administration > Plattform > Externe Konten]**. Die entsprechenden SFTP-Konten sollten von Adobe konfiguriert und die erforderlichen Informationen sollten Ihnen übermittelt worden sein.

   * **[!UICONTROL importSharedAudience]**: Konto für den Zielgruppen-Import.
   * **[!UICONTROL exportSharedAudience]**: Konto für den Zielgruppen-Export.

   ![](assets/aam_config_1.png)

1. Wählen Sie das externe Konto **[!UICONTROL Zielgruppenexport in Adobe Experience Cloud]** aus.

1. Wählen Sie aus der Dropdown-Liste **[!UICONTROL Typ]** die Option **[!UICONTROL AWS S3]** aus.

1. Geben Sie die folgenden Details an:

   * **[!UICONTROL AWS-S3-Konto-Server]**
URL Ihres Servers; sollte wie folgt ausgefüllt werden:

      ```
      <S3bucket name>.s3.amazonaws.com/<s3object path>
      ```

   * **[!UICONTROL Kennung des AWS-Zugriffsschlüssels]**
Informationen dazu, wo Sie Ihre Kennung des AWS-Zugangsschlüssels finden, erhalten Sie auf [dieser Seite](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys).

   * **[!UICONTROL Geheimer Zugriffsschlüssel für AWS]**
Informationen dazu, wo Sie Ihren geheimen Zugriffsschlüssel für AWS finden, erhalten Sie auf [dieser Seite](https://aws.amazon.com/fr/blogs/security/wheres-my-secret-access-key/).

   * **[!UICONTROL AWS-Region]** 
Weitere Informationen zur AWS-Region finden Sie auf [dieser Seite](https://aws.amazon.com/about-aws/global-infrastructure/regions_az/).
   ![](assets/aam_config_2.png)

1. Klicken Sie auf **[!UICONTROL Speichern]** und konfigurieren Sie das externe Konto **[!UICONTROL Zielgruppenexport zu Adobe Experience Cloud]**, wie in den vorherigen Schritten beschrieben.

Ihre externen Konten sind somit konfiguriert.

## Schritt 2: Konfigurieren Sie die Datenquellen.{#step-2--configure-the-data-source}

Die **Empfänger - Besucher-ID** wird innerhalb von Audience Manager erstellt. Dies ist eine native Datenquelle, die standardmäßig für die Besucher-ID konfiguriert wird. In Campaign erstellte Segmente werden ebenfalls Teil dieser Datenquelle sein.

So konfigurieren Sie die Datenquelle **[!UICONTROL Empfänger - Besucher-ID]**:

1. Wählen Sie im Knoten **[!UICONTROL Explorer]** **[!UICONTROL Administration > Plattform > AMC Data sources]** aus.
1. Wählen Sie **[!UICONTROL Empfänger - Besucher-ID]** aus.
1. Geben Sie die von Adobe bereitgestellte **[!UICONTROL ID der Datenquelle]** und die **[!UICONTROL AAM Destination ID]** ein.

   ![](assets/aam_config_3.png)

## Schritt 3: Konfigurieren Sie den Campaign Tracking Server.    {#step-3--configure-campaign-tracking-server}

Für die Konfiguration der Integration mit People Core Service oder Audience Manager muss auch der Campaign Tracking Server konfiguriert werden.

Der Campaign Tracking Server muss in der Domain (CNAME) registriert sein. Weitere Informationen zur Delegation von Domains finden Sie in [diesem Artikel](https://helpx.adobe.com/de/campaign/kb/domain-name-delegation.html).

## Schritt 4: Konfigurieren Sie den Visitor-ID-Dienst.{#step-4--configure-the-visitor-id-service}

Falls Ihr Visitor-ID-Dienst nie in Ihren Web-Parametern und Webseiten konfiguriert wurde, finden Sie im folgenden [Dokument](https://docs.adobe.com/content/help/de-DE/id-service/using/implementation/setup-aam-analytics.html) oder im folgenden [Video](https://helpx.adobe.com/de/marketing-cloud/how-to/email-marketing.html#step-two) nähere Informationen dazu .

Die Konfiguration und Einrichtung sind jetzt abgeschlossen. Die Integration kann somit zum Import und Export von Audiences und Segmenten verwendet werden.
