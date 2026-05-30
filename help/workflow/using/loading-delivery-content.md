---
product: campaign
title: Laden des Versandinhalts
description: Laden des Versandinhalts
feature: Workflows
hide: true
exl-id: a52baffd-402b-4b33-ab72-ac954e4dee85
TQID: https://experienceleague.adobe.com/xRyiD1VNPPhdRtnyRn6JX76vao1-b348bZPoQ3eraLQ
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2: id: c1579802-ddd4-4214-8a91-97b2066abe11id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
feature_v2: []
subfeature_v2: id: ee25c34b-ea50-427b-9369-ba0a160f7d70id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22fid: d1110311-2ca4-442b-be37-088a6db845ee
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 345
ht-degree: 64%

---

# Laden des Versandinhalts{#loading-delivery-content}



Wenn Ihr Versandinhalt in einer auf einem Amazon-S3-, FTP- oder SFTP-Server gespeicherten HTML-Datei verfügbar ist, können Sie diesen Inhalt einfach in Adobe Campaign-Sendungen laden.

Gehen Sie dazu wie folgt vor:

1. Wenn Sie noch keine Verbindung zwischen Adobe Campaign und dem (S)FTP-Server definiert haben, auf dem die Inhaltsdateien gehostet werden, erstellen Sie ein neues externes S3-, FTP- oder SFTP-Konto unter **[!UICONTROL Administration]** > **[!UICONTROL Plattform]** > **[!UICONTROL Externe Konten]**. Geben Sie in diesem externen Konto die Adresse und die Anmeldeinformationen an, die zum Herstellen der Verbindung mit dem S3- oder (S)FTP-Server verwendet werden.

   Hier ist ein Beispiel eines externen S3-Kontos:

   ![](assets/delivery_loadcontent_filetransfertexamples3.png)

1. Erstellen Sie einen neuen Workflow, beispielsweise in **[!UICONTROL Profile und Zielgruppen]** > **[!UICONTROL Aufträge]** > **[!UICONTROL Zielgruppen-Workflow]**.
1. Fügen Sie Ihrem Workflow die Aktivität **[!UICONTROL Dateiübertragung]** hinzu und konfigurieren Sie sie durch folgende Angaben:

   * das zu verwendende externe Konto für die Verbindung mit dem S3- oder (S)FTP-Server.
   * den Pfad der Datei auf dem S3- oder (S)FTP-Server.

   ![](assets/delivery_loadcontent_filetransfertexample.png)

1. Fügen Sie **[!UICONTROL Aktivität]** Versand“ hinzu und verbinden Sie sie mit der ausgehenden Transition der Aktivität **[!UICONTROL Dateiübertragung]** . Konfigurieren Sie ihn wie folgt:

   * Versand: nach Bedarf entweder ein bestimmter im System vorhandener Versand oder ein neuer Versand auf der Basis einer vorhandenen Vorlage.
   * Empfänger: In diesem Beispiel wurde die Zielgruppe im Versand selbst festgelegt.
   * Inhalt: Selbst wenn der Inhalt in der vorherigen Aktivität importiert wurde, wählen Sie **[!UICONTROL Im Versand angegeben]** aus. Da der Inhalt direkt aus einer auf einem Remote-Server gespeicherten Datei importiert wird, enthält er bei der Verarbeitung durch den Workflow keine Kennung und kann nicht als vom Eingangsereignis stammend identifiziert werden.
   * Auszuführende Aktion: Wählen Sie **[!UICONTROL Speichern]**, um den Versand zu speichern und darauf über **[!UICONTROL Kampagnenverwaltung]** > **[!UICONTROL Sendungen]** zugreifen zu können, wenn der Workflow ausgeführt wird.

   ![](assets/delivery_loadcontent_activityexample.png)

1. Fügen Sie in der Aktivität **[!UICONTROL Versand]** im Tab **[!UICONTROL Script]** den folgenden Befehl hinzu, um den Inhalt der importierten Datei in den Versand zu laden:

   ```
   delivery.content.html.source=loadFile(vars.filename)
   ```

   ![](assets/delivery_loadcontent_script.png)

1. Speichern und starten Sie den Workflow. Unter **[!UICONTROL Kampagnenverwaltung]** > **[!UICONTROL Sendungen]** wird ein neuer Versand mit dem geladenen Inhalt erstellt.

>[!NOTE]
>
>Best Practices und Problembehebung bei der Verwendung von SFTP-Servern finden Sie auf [dieser Seite](../../platform/using/sftp-server-usage.md).
