---
product: campaign
title: Planung
description: Erfahren Sie mehr über die Workflow-Aktivität "Planung".
feature: Workflows
hide: true
exl-id: 30a9bd2a-afb1-481c-ab5f-5acebd9cbb5a
TQID: https://experienceleague.adobe.com/SQfzWYlYCgUZXRpV3FDQEeGEBneTZHr-iW55Cy6lBXk
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
subfeature_v2: id: ee25c34b-ea50-427b-9369-ba0a160f7d70id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22fid: d1110311-2ca4-442b-be37-088a6db845ee
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 341
ht-degree: 100%

---

# Planung {#scheduler}



Die **Planung** ist eine persistente Aufgabe, die ihre ausgehende Transition zum konfigurierten Zeitpunkt aktiviert.

Eine **[!UICONTROL Planung]** entspricht einem programmierten Start, daher sind die gleichen Regeln zu beachten wie für die **[!UICONTROL Start]**-Aktivität. So darf die Planung beispielsweise keine eingehende Transition aufweisen.

## Best Practices {#best-practices}

* Es wird empfohlen, Workflows nicht öfter als alle 15 Minuten auszuführen, da die Gesamt-Performance des Systems beeinträchtigt werden kann und Blöcke in der Datenbank entstehen können.

* Verwenden Sie in einem Workflow nie mehr als eine **[!UICONTROL Planungs]**-Aktivität pro Verzweigung. Siehe [Verwenden von Aktivitäten](workflow-best-practices.md#using-activities).

* Die Verwendung einer Planungsaktivität kann dazu führen, dass mehrere Workflow-Ausführungen gleichzeitig vorgenommen werden. Beispielsweise kann eine Planung die Workflow-Ausführung stündlich auslösen, während die Ausführung des gesamten Workflows aber mehr als eine Stunde dauert.

  Sie können die Ausführung ggf. überspringen, wenn der Workflow bereits ausgeführt wird. Weitere Informationen hierzu, wie Sie gleichzeitige Ausführungen eines Workflows verhindern können, finden Sie auf [dieser Seite](monitoring-workflow-execution.md#preventing-simultaneous-multiple-executions).

* Beachten Sie, dass die Transition mehrere Stunden später aktiviert werden kann, wenn der Workflow eine langfristige Aufgabe ausgeführt hat, wie z. B. einen Import, oder wenn das wfserver-Modul eine bestimmte Zeit lang angehalten wurde. In diesem Fall kann es erforderlich sein, die Ausführung der von der Planung aktivierten Aufgabe auf einen bestimmten Zeitraum zu beschränken.

## Konfigurieren der Planungsaktivität {#configuring-scheduler-activity}

Die Planung definiert die Aktivierungsplanung der Transition. Doppelklicken Sie zur Konfiguration auf das grafische Objekt und klicken Sie auf **[!UICONTROL Ändern...]**

![](assets/s_user_segmentation_scheduler.png)

In den folgenden Schritten des Assistenten lassen sich die Frequenz der Ausführungen und die Gültigkeit der Aktivität festlegen. Die Konfiguration stellt sich wie folgt dar:

1. Kreuzen Sie die gewünschte Häufigkeit an und klicken Sie auf **[!UICONTROL Weiter]**.

   ![](assets/s_user_segmentation_scheduler2.png)

1. Geben Sie die Aktivierungszeiten und -tage an. Die Parameter für diesen Schritt hängen von der im vorherigen Schritt ausgewählten Häufigkeit ab. Wenn Sie die Aktivität mehrmals täglich starten möchten, sind folgende Konfigurationsoptionen verfügbar:

   ![](assets/s_user_segmentation_scheduler3.png)

1. Definieren Sie im nächsten Schritt die Gültigkeit der Planung oder die maximale Anzahl an Ausführungen.

   ![](assets/s_user_segmentation_scheduler4.png)

1. Prüfen Sie im letzten Schritt die Konfiguration und klicken Sie auf **[!UICONTROL Beenden]**, um sie zu speichern.

   ![](assets/s_user_segmentation_scheduler5.png)
