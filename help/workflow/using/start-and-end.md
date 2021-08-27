---
product: campaign
title: Start und Ende
description: Erfahren Sie mehr über die Workflow-Aktivitäten "Start" und "Ende".
audience: workflow
content-type: reference
topic-tags: flow-control-activities
exl-id: 56dfbaf3-93de-4ade-b4ad-9b54d239c7a5
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '138'
ht-degree: 100%

---

# Start und Ende{#start-and-end}

![](../../assets/common.svg)

**[!UICONTROL Beginn]**- und **[!UICONTROL Ende]**-Aktivitäten markieren grafisch den Anfangs- bzw. Endpunkt eines Workflows. Sie haben keine funktionale Auswirkung und sind daher optional.

* **[!UICONTROL Starten]**

   Die Ausführung eines Workflows beginnt mit Aktivitäten ohne eingehende Transition oder mit einer Beginnaktivität.

   ![](assets/s_user_segmentation_start_stop.png)

* **[!UICONTROL Ende]**

   Das **[!UICONTROL Ende]** kann dahingehend konfiguriert werden, dass es alle laufenden Aufgaben unterbricht. Öffnen Sie hierzu die Aktivität und kreuzen Sie die entsprechende Option an.

   ![](assets/s_user_segmentation_end.png)

   Die Daten der Arbeitstabelle werden automatisch gelöscht, sobald die Endeaktivität aktiviert wird. Sollte dies nicht erforderlich sein und um eine unnötige Inanspruchnahme von Ressourcen zu vermeiden, kann die ausgehende Transition der letzten Workflow-Aktivität deaktiviert werden. Wenn beispielsweise ein Versand die letzte Aktivität eines Workflows ist, können Sie, wie unten abgebildet, die entsprechende Option deaktivieren:

   ![](assets/s_advuser_delivery_option_no_output.png)
