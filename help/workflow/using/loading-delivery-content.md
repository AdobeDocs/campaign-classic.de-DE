---
title: Versandinhalt laden
seo-title: Versandinhalt laden
description: Versandinhalt laden
seo-description: null
page-status-flag: never-activated
uuid: f2004fb0-9beb-463f-9903-10f291b3663e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 3667da3d-4940-4128-8878-f1ee67216f56
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# Versandinhalt laden{#loading-delivery-content}

Wenn Ihr Versandinhalt in einer auf einem Amazon-S3-, FTP- oder SFTP-Server gespeicherten HTML-Datei verfügbar ist, können Sie diesen Inhalt einfach in Adobe-Campaign-Sendungen laden.

Gehen Sie dazu wie folgt vor:

1. If you haven&#39;t already defined a connection between Adobe Campaign and the (S)FTP server hosting the content files, create a new S3, FTP or SFTP external account in **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL External Accounts]**. Specify in this external account the address and credentials used to establish the connection to the S3 or (S)FTP server.

   Hier ist ein Beispiel eines externen S3-Kontos:

   ![](assets/delivery_loadcontent_filetransfertexamples3.png)

1. Erstellen Sie einen neuen Workflow, z. B. über **[!UICONTROL Profiles and Targets]** > **[!UICONTROL Jobs]** > **[!UICONTROL Targeting workflows]**.
1. Add a **[!UICONTROL File transfer]** activity into your workflow, and configure it by specifying

   * das zu verwendende externe Konto für die Verbindung mit dem S3- oder (S)FTP-Server.
   * den Pfad der Datei auf dem S3- oder (S)FTP-Server.
   ![](assets/delivery_loadcontent_filetransfertexample.png)

1. Fügen Sie eine **[!UICONTROL Delivery]** Aktivität hinzu und verbinden Sie sie mit dem ausgehenden Übergang der **[!UICONTROL File transfer]** Aktivität. Konfigurieren Sie es wie folgt:

   * Versand: nach Bedarf entweder ein bestimmter im System vorhandener Versand oder ein neuer Versand auf der Basis einer vorhandenen Vorlage.
   * Empfänger: In diesem Beispiel wurde die Zielgruppe im Versand selbst festgelegt.
   * Content: Even if the content is imported in the previous activity, select **[!UICONTROL Specified in the delivery]**. As the content is imported directly from a file located on a remote server, it has no identifier when processed by the workflow and cannot be identified as coming from the inbound event.
   * Action to perform: Select **[!UICONTROL Save]** to save the delivery and be able to access it from **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]** once the workflow is executed.
   ![](assets/delivery_loadcontent_activityexample.png)

1. In the **[!UICONTROL Script]** tab of the **[!UICONTROL Delivery]** activity, add the following command to load the content of the imported file in the delivery:

   ```
   delivery.content.md.source=loadFile(vars.filename)
   ```

   ![](assets/delivery_loadcontent_script.png)

1. Speichern und starten Sie den Workflow. Eine neue Bereitstellung mit dem geladenen Inhalt wird unter **[!UICONTROL Campaign management]** > erstellt **[!UICONTROL Deliveries]**.

>[!NOTE]
>
>Best Practices und Problembehebung bei der Verwendung von SFTP-Servern finden Sie auf [dieser Seite](../../platform/using/sftp-server-usage.md).

