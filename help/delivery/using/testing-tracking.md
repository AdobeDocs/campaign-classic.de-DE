---
product: campaign
title: Testen des Nachrichten-Trackings
description: Erfahren Sie, wie Sie das Tracking von Nachrichten testen
badge-v7: label="v7" type="Informative" tooltip="Gilt für Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Gilt auch für Campaign v8"
feature: Monitoring
role: User
exl-id: 16ad36b7-c13e-4b77-86ca-41c9ef174172
source-git-commit: d2f5f2a662c022e258fb3cc56c8502c4f4cb2849
workflow-type: tm+mt
source-wordcount: '273'
ht-degree: 88%

---

# Testen des Nachrichten-Trackings{#testing-tracking}

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

1. Gehen Sie zur Profilseite des Testempfängers und wählen Sie die **Tracking** Registerkarte. Einige Datensätze sollten mit der Variablen **Mirrorseite** Wert in **Typ** Spalte.

   >[!NOTE]
   >
   >Standardmäßig befindet sich die Profilseite des Empfängers im Ordner **Profile und Zielgruppen > Empfänger**.

   Um das E-Mail-Logtracking zu überprüfen, sehen Sie sich in der Spalte **Typ** die Werte **Öffnen** und **[!UICONTROL E-Mail-Klick]** an.

   Wenn die Öffnen-Logs nicht angezeigt werden, gehen Sie zum Versand und überprüfen Sie in seinen **Eigenschaften**, ob sowohl die Optionen **Tracking aktivieren** als auch **[!UICONTROL Öffnungstracking]** angekreuzt sind.
