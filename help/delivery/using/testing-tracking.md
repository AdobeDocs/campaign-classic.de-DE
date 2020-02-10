---
title: Tracking testen
seo-title: Tracking testen
description: Tracking testen
seo-description: null
page-status-flag: never-activated
uuid: 76d84ab4-b632-4498-96a1-ce9c773ec125
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: tracking-messages
discoiquuid: 4ed23249-4ecf-4e57-91b3-6fae1387bd6a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Tracking testen{#testing-tracking}

Sie können Tracking auf Mirrorseiten, E-Mail-Protokolle und Links testen. Gehen Sie dazu folgendermaßen vor:

1. Erstellen Sie einen neuen E-Mail-Versand, der getestet werden soll.
1. Geben Sie den Empfänger der E-Mail an. Da dieser die E-Mail öffnen und auf die darin enthaltenen Links klicken muss, wählen Sie eine Testempfänger-Adresse aus, auf die Sie Zugriff haben.
1. Fügen Sie dem E-Mail-Inhalt einen Mirrorseiten-Personalisierungsbaustein (MirrorPage) hinzu.
1. Senden Sie die den Mirrorseiten-Link enthaltende Nachricht an die Mirrorseite.
1. Öffnen Sie nach dem Erhalt die E-Mail und klicken Sie auf den Mirrorseiten-Link.
1. After you are correctly redirected to the mirror page, access the **Administration > Technical workflows** folder and open the **Tracking** workflow.
1. Start the workflow, right click the **Scheduler** activity and select **Execute pending task now**.
1. Warten Sie ca. 30 Sekunden und öffnen Sie dann den Tab **Verfolgung**. Vergewissern Sie sich, dass zumindest ein Trackinglog gefunden wurde.

   Falls Sie keine neuen Logs sehen, klicken Sie auf **Aktualisieren**.

1. Gehen Sie zur Profilseite des Testempfängers und wählen Sie den Tab **Tracking** aus. Dort sollten einige Datensätze angezeigt werden, wobei in der Spalte **Typ** der Wert **Mirrorseite** angegeben wird.

   >[!NOTE]
   >
   >The recipient&#39;s profile page is located in the **Profiles and Targets > Recipients** folder by default.

   To check the email log tracking, look for the values **Open** and **[!UICONTROL Email click]** in the **Type** column.

   If the open logs do not appear, go to the delivery and access its **Properties** to make sure that both **Activate tracking** and **[!UICONTROL Opens tracking]** options are checked.

