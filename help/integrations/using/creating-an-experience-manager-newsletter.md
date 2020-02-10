---
title: Experience-Manager-Newsletter erstellen
seo-title: Experience-Manager-Newsletter erstellen
description: Experience-Manager-Newsletter erstellen
seo-description: null
page-status-flag: never-activated
uuid: 75cf4891-06a6-42d2-9b22-b4d93e0dc64a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 627ade78-96b3-4a6e-9ace-74610a3c8d1a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0745b9c9d72538b8573ad18ff4054ecf788905f2

---


# Experience-Manager-Newsletter erstellen{#creating-an-experience-manager-newsletter}

Mit dieser Integration kann beispielsweise ein Newsletter in Adobe Experience Manager erstellt werden, der danach in Adobe Campaign als Teil einer E-Mail-Kampagne verwendet wird.

Ein detailliertes Beispiel für die Verwendung dieser Integration finden Sie in dieser [schrittweisen Anleitung](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/aem.html).

**In Adobe Experience Manager:**

1. Wählen Sie in der AEM-Authoring-Instanz das **Adobe-Experience**-Logo oben links und danach **[!UICONTROL Sites]**.

   ![](assets/aem_uc_1.png)

1. Auswählen **[!UICONTROL Campaigns > Name of your brand (here We.Retail) > Master Area > Email campaigns]**.
1. Click the **[!UICONTROL Create]** button in the upper right side of the page then select **[!UICONTROL Page]**.

   ![](assets/aem_uc_2.png)

1. Select the **[!UICONTROL Adobe Campaign Email (AC 6.1)]** template and name your newsletter.
1. Sobald die Seite erstellt wurde, öffnen Sie das **[!UICONTROL Page information]** Menü und klicken Sie auf **[!UICONTROL Open Properties]**.

   ![](assets/aem_uc_3.png)

1. Wählen Sie auf der **[!UICONTROL Cloud Services]** Registerkarte **[!UICONTROL Adobe Campaign]** als **[!UICONTROL Cloud service configuration]** und Ihre Adobe Campaign-Instanz in der zweiten Dropdown-Liste aus.

   ![](assets/aem_uc_4.png)

1. Bearbeiten Sie den E-Mail-Inhalt, indem Sie Komponenten hinzufügen, z. B. Personalisierungsfelder aus Adobe Campaign.
1. Wenn Ihre E-Mail fertig ist, öffnen Sie das **[!UICONTROL Page information]** Menü und klicken Sie auf **[!UICONTROL Start workflow]**.

   ![](assets/aem_uc_5.png)

1. Wählen Sie aus der ersten Dropdownliste **[!UICONTROL Publish to Adobe Campaign]** als Workflow-Modell aus und klicken Sie auf **[!UICONTROL Start workflow]**.

   ![](assets/aem_uc_6.png)

1. Starten Sie dann wie im vorherigen Schritt den **[!UICONTROL Approve for Campaign]** Workflow.
1. Über Ihrer Seite wird ein Haftungsausschluss angezeigt. Klicken Sie **[!UICONTROL Complete]** zur Bestätigung der Überprüfung auf **[!UICONTROL Ok]**.

   ![](assets/aem_uc_7.png)

1. Klicken Sie erneut **[!UICONTROL Complete]** und wählen Sie **[!UICONTROL Newsletter approval]** in der **[!UICONTROL Next Step]** Dropdownliste aus.

   ![](assets/aem_uc_8.png)

Ihr Newsletter ist jetzt fertig und in Adobe Campaign synchronisiert.

**In Adobe Campaign:**

1. Klicken Sie auf der **[!UICONTROL Campaigns]** Registerkarte **[!UICONTROL Deliveries]** dann **[!UICONTROL Create]**.

   ![](assets/aem_uc_9.png)

1. Wählen Sie in der **[!UICONTROL Delivery template]** Dropdownliste die **[!UICONTROL Email delivery with AEM content (mailAEMContent)]** Vorlage aus.

   ![](assets/aem_uc_10.png)

1. Add a **[!UICONTROL Label]** to your delivery and click **[!UICONTROL Continue]**.
1. Click the **[!UICONTROL Synchronize]** button.

   Wenn diese Schaltfläche nicht in Ihrer Benutzeroberfläche angezeigt wird, klicken Sie auf die **[!UICONTROL Properties]** Schaltfläche und wählen Sie die **[!UICONTROL Advanced]** Registerkarte aus. Das **[!UICONTROL Content editing mode]** Feld sollte auf **[!UICONTROL AEM]** Ihre AEM-Instanz im **[!UICONTROL AEM account]** Feld eingestellt werden.

   ![](assets/aem_uc_11.png)

1. Wählen Sie den zuvor in Adobe Experience Manager erstellten Versand und anschließend **[!UICONTROL Ok]** aus.
1. Click the **[!UICONTROL Refresh content]** button as soon as some changes are made to your AEM delivery.

   ![](assets/aem_uc_12.png)

Ihre E-Mail kann jetzt an Ihre Audience gesendet werden.
