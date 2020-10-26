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
translation-type: ht
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: ht
source-wordcount: '256'
ht-degree: 100%

---


# Tracking testen{#testing-tracking}

Sie können Tracking auf Mirrorseiten, E-Mail-Protokolle und Links testen. Gehen Sie dazu folgendermaßen vor:

1. Erstellen Sie einen neuen E-Mail-Versand, der getestet werden soll.
1. Geben Sie den Empfänger der E-Mail an. Da dieser die E-Mail öffnen und auf die darin enthaltenen Links klicken muss, wählen Sie eine Testempfänger-Adresse aus, auf die Sie Zugriff haben.
1. Fügen Sie dem E-Mail-Inhalt einen Mirrorseiten-Personalisierungsbaustein (MirrorPage) hinzu.
1. Senden Sie die den Mirrorseiten-Link enthaltende Nachricht an die Mirrorseite.
1. Öffnen Sie nach dem Erhalt die E-Mail und klicken Sie auf den Mirrorseiten-Link.
1. Wenn Sie ordnungsgemäß auf die Mirrorseite weitergeleitet werden, gehen Sie zu **Administration > Technische Workflows** und öffnen Sie den Workflow **Tracking**.
1. Starten Sie den Workflow, indem Sie mit der rechten Maustaste auf die Aktivität **Planung** klicken und **Vorgezogene Ausführung der ausstehenden Aufgaben** auswählen.
1. Warten Sie ca. 30 Sekunden und öffnen Sie dann den Tab **Verfolgung**. Vergewissern Sie sich, dass zumindest ein Trackinglog gefunden wurde.

   Falls Sie keine neuen Logs sehen, klicken Sie auf **Aktualisieren**.

1. Gehen Sie zur Profilseite des Testempfängers und wählen Sie den Tab **Tracking** aus. Dort sollten einige Datensätze angezeigt werden, wobei in der Spalte **Typ** der Wert **Mirrorseite** angegeben wird.

   >[!NOTE]
   >
   >Standardmäßig befindet sich die Profilseite des Empfängers im Ordner **Profile und Zielgruppen > Empfänger**.

   Um das E-Mail-Logtracking zu überprüfen, sehen Sie sich in der Spalte **Typ** die Werte **Öffnen** und **[!UICONTROL E-Mail-Klick]** an.

   Wenn die Öffnen-Logs nicht angezeigt werden, gehen Sie zum Versand und überprüfen Sie in seinen **Eigenschaften**, ob sowohl die Optionen **Tracking aktivieren** als auch **[!UICONTROL Öffnungstracking]** angekreuzt sind.

