---
title: Freigegebene Assets nutzen
seo-title: Freigegebene Assets nutzen
description: Freigegebene Assets nutzen
seo-description: null
page-status-flag: never-activated
uuid: ab661bfd-d0a3-4b5c-ba52-4c76c834d584
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: asset-sharing
discoiquuid: 3d01cc7e-5685-4101-bf4b-ef5f6e52b3c9
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0745b9c9d72538b8573ad18ff4054ecf788905f2

---


# Freigegebene Assets nutzen{#inserting-a-shared-asset}

Freigegebene Assets der Adobe Experience Cloud können in E-Mails und Landingpages wie nachfolgend beschrieben eingesetzt werden:

1. Erstellen Sie eine neue E-Mail oder eine neue Landingpage.

   Verwenden Sie beim Gebrauch von Assets aus der Adobe-Experience-Manager-Bibliothek eine bei der [Integrationskonfiguration](../../integrations/using/configuring-access-to-assets.md#integrating-with-aem-assets) erstellte Versandvorlage.

   If you do not have this specific template, make sure that in the delivery **Properties**, the **[!UICONTROL Content editing mode]** (**[!UICONTROL Advanced]** tab) is set to **DCE** and that the AEM external account that you want to use for accessing your AEM Assets resource library is provided.

1. Wählen Sie im Bearbeitungsfenster die Option zum Einfügen eines Bilds aus:

   * Wenn Sie den [Standard-Bearbeitungsmodus](../../delivery/using/defining-the-email-content.md#adding-images)verwenden, wählen Sie **[!UICONTROL Image]** > **[!UICONTROL Select a shared asset]**.

      ![](assets/dam_insert_image_standard.png)

   * If you are using the [advanced editing mode](../../web/using/about-campaign-html-editor.md) (DCE), go to an image block, then via the contextual menu, select **[!UICONTROL Select a shared asset]**.

      ![](assets/dam_insert_image_dce.png)

      >[!NOTE]
      >
      >Das Einfügen von freigegebenen Bildern steht im DCE bei Verwendung des [Webzugriffs](../../platform/using/adobe-campaign-workspace.md#console-and-web-access) von Adobe Campaign nicht zur Verfügung.

1. Wählen Sie im sich öffnenden Fenster das gewünschte Bild aus und bestätigen Sie Ihre Auswahl.

   Die verfügbaren Bilder stammen entweder aus Ihrer Adobe Experience Cloud-Bibliothek oder aus Ihrer AEM Assets-Bibliothek, je nachdem, wie Ihre Adobe Campaign-Instanz konfiguriert ist. Weitere Informationen finden Sie im Abschnitt Zugriff auf Assets [konfigurieren](../../integrations/using/configuring-access-to-assets.md) .

   ![](assets/dam_shared_image_selection.png)

>[!NOTE]
>
>Wenn Sie die Integration mit Adobe Target nutzen, haben Sie die Möglichkeit, ein freigegebenes Bild als Standardbild zu verwenden. Weiterführende Informationen dazu finden Sie auf [dieser Seite](../../integrations/using/integrating-with-adobe-target.md).

