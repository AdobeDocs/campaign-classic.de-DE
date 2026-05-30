---
product: campaign
title: Freigegebene Assets nutzen
description: Freigegebene Assets nutzen
feature: Asset Sharing
audience: integrations
content-type: reference
topic-tags: asset-sharing
exl-id: 30a94bce-6d96-4a6d-a62f-7451c822f0e3
TQID: https://experienceleague.adobe.com/5SrvIw1sYSNd4Hw1we554AfxDj3VgeTeqIOOzTTrWuY
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: d5ef99fa-df0c-4153-bf94-105ad0724167
subfeature_v2:
  - id: cbcf4d90-26be-46e2-b16a-aebc529dc41e
  - id: df0d6518-6f49-46e2-b46e-3bcc513f553f
  - id: eb007b6d-6e57-46ab-9485-3f24d6102304
  - id: b1fd1501-3105-4d6b-b4d4-9af53126df75
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 246
ht-degree: 100%

---

# Freigegebene Assets nutzen{#inserting-a-shared-asset}

Freigegebene Assets der Adobe Experience Cloud können in E-Mails und Landingpages wie nachfolgend beschrieben eingesetzt werden:

1. Erstellen Sie eine neue E-Mail oder eine neue Landingpage.

   Verwenden Sie beim Gebrauch von Assets aus der Adobe-Experience-Manager-Bibliothek eine bei der [Integrationskonfiguration](../../integrations/using/configuring-access-to-assets.md#integrating-with-aem-assets) erstellte Versandvorlage.

   Sollten Sie über keine spezielle Vorlage verfügen, vergewissern Sie sich, dass in den **Eigenschaften** des Versands im Feld **[!UICONTROL Inhaltserstellung]** (im **[!UICONTROL Erweitert]**-Tab) die Option **DCE** ausgewählt ist und dass das externe AEM-Konto, das Sie für den Zugriff auf Ihre AEM-Assets-Bibliothek verwenden möchten, angegeben ist.

1. Wählen Sie im Bearbeitungsfenster die Option zum Einfügen eines Bilds aus:

   * Wenn Sie sich im [Standard-Bearbeitungsmodus](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/defining-the-email-content.html?lang=de#adding-images){target="_blank"} befinden, wählen Sie aus der **[!UICONTROL Bild]**-Dropdown-Liste die Option **[!UICONTROL Freigegebenes Asset auswählen]** aus.

     ![](assets/dam_insert_image_standard.png)

   * Wenn Sie sich im [erweiterten Bearbeitungsmodus](../../web/using/about-campaign-html-editor.md) (DCE) befinden, markieren Sie einen Inhaltsbaustein und wählen Sie im Kontextmenü die Option **[!UICONTROL Freigegebenes Asset auswählen]** aus.

     ![](assets/dam_insert_image_dce.png)

     >[!NOTE]
     >
     >Das Einfügen von freigegebenen Bildern steht im DCE bei Verwendung des [Webzugriffs](../../platform/using/adobe-campaign-workspace.md#console-and-web-access) von Adobe Campaign nicht zur Verfügung.

1. Wählen Sie im sich öffnenden Fenster das gewünschte Bild aus und bestätigen Sie Ihre Auswahl.

   Die verfügbaren Bilder stammen je nach der Konfiguration Ihrer Adobe Campaign-Instanz entweder aus Ihrer Adobe Experience Cloud-Bibliothek oder aus Ihrer AEM Assets-Bibliothek. Weitere Informationen finden Sie im Abschnitt [Zugriff auf Assets konfigurieren](../../integrations/using/configuring-access-to-assets.md).

   ![](assets/dam_shared_image_selection.png)

>[!NOTE]
>
>Wenn Sie die Integration mit Adobe Target nutzen, haben Sie die Möglichkeit, ein freigegebenes Bild als Standardbild zu verwenden. Mehr dazu erfahren Sie auf [dieser Seite](../../integrations/using/integrating-with-adobe-target.md).
