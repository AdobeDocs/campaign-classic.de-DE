---
product: campaign
title: Experience-Manager-Newsletter erstellen
description: Experience-Manager-Newsletter erstellen
feature: Experience Manager Integration
badge-v7: label="v7" type="Informative" tooltip="Gilt für Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Gilt auch für Campaign v8"
audience: integrations
content-type: reference
exl-id: 9fa3ce08-3007-4c65-9841-bad339428b7c
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 85%

---

# Erstellen eines Experience Manager-Newsletters{#creating-an-experience-manager-newsletter}



Mit dieser Integration kann beispielsweise ein Newsletter in Adobe Experience Manager erstellt werden, der danach in Adobe Campaign als Teil einer E-Mail-Kampagne verwendet wird.

**In Adobe Experience Manager:**

1. Wählen Sie in der AEM-Authoring-Instanz das **Adobe-Experience**-Logo oben links und danach **[!UICONTROL Sites]**.

   ![](assets/aem_uc_1.png)

1. Wählen Sie **[!UICONTROL Kampagnen > Name Ihres Unternehmens (hier We.Retail) > Hauptbereich > E-Mail-Kampagnen]** aus.
1. Wählen Sie rechts oben **[!UICONTROL Erstellen]** und danach **[!UICONTROL Seite]** aus.

   ![](assets/aem_uc_2.png)

1. Wählen Sie die Vorlage **[!UICONTROL Adobe Campaign Email (AC 6.1)]** aus und benennen Sie Ihren Newsletter.
1. Öffnen Sie nach der Erstellung Ihrer Seite das Menü **[!UICONTROL Seiteninformationen]** und danach **[!UICONTROL Eigenschaften öffnen]**.

   ![](assets/aem_uc_3.png)

1. Wählen Sie im Tab **[!UICONTROL Cloud-Services]** die Option **[!UICONTROL Adobe Campaign]** für **[!UICONTROL Cloud-Service-Konfigurationen]** und in der zweiten Dropdown-Liste Ihre Adobe-Campaign-Instanz.

   ![](assets/aem_uc_4.png)

1. Bearbeiten Sie den E-Mail-Inhalt, indem Sie Komponenten hinzufügen, z. B. Personalisierungsfelder aus Adobe Campaign.
1. Wenn Ihre E-Mail fertig ist, öffnen Sie das Menü **[!UICONTROL Seiteninformationen]** und wählen sie danach **[!UICONTROL Workflow starten]** aus.

   ![](assets/aem_uc_5.png)

1. Wählen Sie aus der ersten Dropdown-Liste als Workflow-Modell **[!UICONTROL In Adobe Campaign veröffentlichen]** aus und danach **[!UICONTROL Workflow starten]**.

   ![](assets/aem_uc_6.png)

1. Starten Sie dann wie im vorherigen Schritt den Workflow **[!UICONTROL Für Adobe Campaign genehmigen]**.
1. Am oberen Rand Ihrer Seite wird ein Haftungsausschluss angezeigt. Klicks **[!UICONTROL Fertig]** , um die Überprüfung zu bestätigen, und klicken Sie auf **[!UICONTROL Ok]**.

   ![](assets/aem_uc_7.png)

1. Wählen Sie erneut **[!UICONTROL Abgeschlossen]** aus und danach **[!UICONTROL Newsletter-Genehmigung]** in der Dropdown-Liste **[!UICONTROL Nächster Schritt]**.

   ![](assets/aem_uc_8.png)

Ihr Newsletter ist jetzt fertig und in Adobe Campaign synchronisiert.

**In Adobe Campaign:**

1. Wählen Sie im Tab **[!UICONTROL Kampagnen]** die Option **[!UICONTROL Sendungen]** und danach die Schaltfläche **[!UICONTROL Erstellen]** aus.

   ![](assets/aem_uc_9.png)

1. Wählen Sie in der Dropdown-Liste **[!UICONTROL Versandvorlage]** die Vorlage **[!UICONTROL E-Mail-Versand mit AEM-Inhalt (mailAEMContent)]** aus.

   ![](assets/aem_uc_10.png)

1. Fügen Sie zu Ihrem Versand einen **[!UICONTROL Titel]** hinzu und wählen Sie dann **[!UICONTROL Fortfahren]** aus.
1. Wählen Sie die Schaltfläche **[!UICONTROL Synchronisieren]** aus.

   Wenn diese Schaltfläche nicht in der Benutzeroberfläche angezeigt wird, klicken Sie auf die Schaltfläche **[!UICONTROL Eigenschaften]** und wählen Sie die **[!UICONTROL Erweitert]** Registerkarte. Die **[!UICONTROL Inhaltsbearbeitungsmodus]** -Feld auf **[!UICONTROL AEM]** mit Ihrer AEM -Instanz im **[!UICONTROL AEM]** -Feld.

   ![](assets/aem_uc_11.png)

1. Wählen Sie den zuvor in Adobe Experience Manager erstellten Versand und anschließend **[!UICONTROL Ok]** aus.
1. Wenn Änderungen am AEM-Versand vorgenommen werden, wählen Sie die Schaltfläche **[!UICONTROL Inhalt aktualisieren]**.

   ![](assets/aem_uc_12.png)

Ihre E-Mail kann jetzt an Ihre Audience gesendet werden.
