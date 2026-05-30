---
product: campaign
title: Start und Ende
description: Erfahren Sie mehr über die Workflow-Aktivitäten "Start" und "Ende".
feature: Workflows
hide: true
exl-id: 56dfbaf3-93de-4ade-b4ad-9b54d239c7a5
TQID: https://experienceleague.adobe.com/Vw3JK6VyMf4HrEkvYk4-34dGTp0e3e1xPZ8jG0bAxz8
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
subfeature_v2: id: ee25c34b-ea50-427b-9369-ba0a160f7d70id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22fid: d1110311-2ca4-442b-be37-088a6db845ee
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 140
ht-degree: 21%

---

# Start und Ende{#start-and-end}



Mit **[!UICONTROL Start]** und **[!UICONTROL End]**-Aktivitäten können Sie den Start und das Ende eines Workflows grafisch markieren. Diese Aktivitäten haben keine funktionalen Auswirkungen und sind daher optional.

* **[!UICONTROL Starten]**

  Die Ausführung eines Workflows beginnt mit Aktivitäten ohne eingehende Transition oder mit einer Beginnaktivität.

  ![](assets/s_user_segmentation_start_stop.png)

* **[!UICONTROL Ende]**

  Sie können die Aktivität **[!UICONTROL Ende]** so konfigurieren, dass alle laufenden Aufgaben unterbrochen werden. Doppelklicken Sie dazu auf die Aktivität, um deren Eigenschaften anzuzeigen, und aktivieren Sie die entsprechende Option.

  ![](assets/s_user_segmentation_end.png)

  Die Daten in der Arbeitstabelle werden automatisch gelöscht, wenn die Endaktivität aktiviert ist. Wenn dies nicht erforderlich ist, können Sie zur Vermeidung unnötiger Lasten die Transition bei der letzten Aktivitätsausgabe deaktivieren. Wenn beispielsweise an einer Versandausgabe kein Prozess geplant ist, deaktivieren Sie die entsprechende Option wie unten dargestellt:

  ![](assets/s_advuser_delivery_option_no_output.png)
