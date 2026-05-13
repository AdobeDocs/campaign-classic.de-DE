---
product: campaign
title: Experience-Manager-Newsletter erstellen
description: Experience-Manager-Newsletter erstellen
feature: Experience Manager Integration
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
audience: integrations
content-type: reference
exl-id: 9fa3ce08-3007-4c65-9841-bad339428b7c
TQID: https://experienceleague.adobe.com/-5orLjm8w8PjA4t4Swox55NP2MTw3rGZzGq42JwuzeQ
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: a075b2c1-7748-4328-b7f6-343aa314616aid: d5ef99fa-df0c-4153-bf94-105ad0724167
subfeature_v2: id: df0d6518-6f49-46e2-b46e-3bcc513f553f
topic_v2: id: e0eb8757-182f-49f3-94a4-1587d16f5094
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 363
ht-degree: 100%

---

# Erstellen eines Experience Manager-Newsletters{#creating-an-experience-manager-newsletter}



Mit dieser Integration kann beispielsweise ein Newsletter in Adobe Experience Manager erstellt werden, der danach in Adobe Campaign als Teil einer E-Mail-Kampagne verwendet wird.

**In Adobe Experience Manager:**

1. Wählen Sie in der AEM-Autoreninstanz das **Adobe-Experience**-Logo oben links und danach **[!UICONTROL Sites]**.

   ![](assets/aem_uc_1.png)

1. Wählen Sie **[!UICONTROL Kampagnen > Name Ihres Unternehmens (hier We.Retail) > Hauptbereich > E-Mail-Kampagnen]** aus.
1. Wählen Sie rechts oben **[!UICONTROL Erstellen]** und danach **[!UICONTROL Seite]** aus.

   ![](assets/aem_uc_2.png)

1. Wählen Sie die Vorlage **[!UICONTROL Adobe Campaign Email (AC 6.1)]** aus und benennen Sie Ihren Newsletter.
1. Öffnen Sie nach der Erstellung Ihrer Seite das Menü **[!UICONTROL Seiteninformationen]** und danach **[!UICONTROL Eigenschaften öffnen]**.

   ![](assets/aem_uc_3.png)

1. Wählen Sie im Tab **[!UICONTROL Cloud-Services]** die Option **[!UICONTROL Adobe Campaign]** für **[!UICONTROL Cloud-Service-Konfigurationen]** und in der zweiten Dropdown-Liste Ihre Adobe Campaign-Instanz.

   ![](assets/aem_uc_4.png)

1. Bearbeiten Sie den E-Mail-Inhalt, indem Sie Komponenten hinzufügen, z. B. Personalisierungsfelder aus Adobe Campaign.
1. Wenn Ihre E-Mail fertig ist, öffnen Sie das Menü **[!UICONTROL Seiteninformationen]** und wählen sie danach **[!UICONTROL Workflow starten]** aus.

   ![](assets/aem_uc_5.png)

1. Wählen Sie aus der ersten Dropdown-Liste als Workflow-Modell **[!UICONTROL In Adobe Campaign veröffentlichen]** aus und danach **[!UICONTROL Workflow starten]**.

   ![](assets/aem_uc_6.png)

1. Starten Sie dann wie im vorherigen Schritt den Workflow **[!UICONTROL Für Adobe Campaign genehmigen]**.
1. Am oberen Seitenrand wird ein Hinweis zum Haftungsausschluss angezeigt. Wählen Sie **[!UICONTROL Abgeschlossen]** aus, um die Überprüfung zu bestätigen, und danach **[!UICONTROL Ok]**.

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

   Wenn diese Schaltfläche nicht in der Benutzeroberfläche zu sehen ist, wählen Sie die Schaltfläche **[!UICONTROL Eigenschaften]** und danach den Tab **[!UICONTROL Erweitert]** aus. Im Feld **[!UICONTROL Inhaltserstellung]** sollte **[!UICONTROL AEM]** und im Feld **[!UICONTROL AEM-Konto]** sollte Ihre AEM-Instanz stehen.

   ![](assets/aem_uc_11.png)

1. Wählen Sie den zuvor in Adobe Experience Manager erstellten Versand und anschließend **[!UICONTROL Ok]** aus.
1. Wenn Änderungen am AEM-Versand vorgenommen werden, wählen Sie die Schaltfläche **[!UICONTROL Inhalt aktualisieren]**.

   ![](assets/aem_uc_12.png)

Ihre E-Mail kann jetzt an Ihre Zielgruppe gesendet werden.
