---
title: Start und Ende
seo-title: Start und Ende
description: Start und Ende
seo-description: null
page-status-flag: never-activated
uuid: ec0c818c-c307-4f50-908c-507bce0ea27b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: flow-control-activities
discoiquuid: 8b239d5e-2317-42c8-9fee-7d40bea624da
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Start und Ende{#start-and-end}

Die **[!UICONTROL Start]** und **[!UICONTROL End]** Aktivitäten ermöglichen es Ihnen, den Beginn und das Ende eines Workflows grafisch zu markieren. Diese Tätigkeiten haben keine funktionalen Auswirkungen und sind daher fakultativ.

* **[!UICONTROL Start]**

   Die Ausführung eines Workflows beginnt mit Aktivitäten ohne eingehende Transition oder mit einer Beginnaktivität.

   ![](assets/s_user_segmentation_start_stop.png)

* **[!UICONTROL End]**

   Sie können die **[!UICONTROL End]** Aktivität so konfigurieren, dass alle derzeit ausgeführten Aufgaben unterbrochen werden. Doppelklicken Sie dazu auf die Aktivität, um deren Eigenschaften anzuzeigen, und aktivieren Sie die entsprechende Option.

   ![](assets/s_user_segmentation_end.png)

   Die Daten der Arbeitstabelle werden automatisch gelöscht, sobald die Endeaktivität aktiviert wird. Sollte dies nicht erforderlich sein und um eine unnötige Inanspruchnahme von Ressourcen zu vermeiden, kann die ausgehende Transition der letzten Workflow-Aktivität deaktiviert werden. Wenn beispielsweise ein Versand die letzte Aktivität eines Workflows ist, können Sie, wie unten abgebildet, die entsprechende Option deaktivieren:

   ![](assets/s_advuser_delivery_option_no_output.png)

