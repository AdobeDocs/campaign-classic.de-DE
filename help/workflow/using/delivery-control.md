---
title: Versand bearbeiten
seo-title: Versand bearbeiten
description: Versand bearbeiten
seo-description: null
page-status-flag: never-activated
uuid: f9cef2d9-a6a5-45bd-8c7a-fabc11879628
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: 0b5ee05c-4b96-425a-ab0f-60b930de21bd
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: cfb1b02a6261c001392b5cc6430f00206e802bb8

---


# Versand bearbeiten{#delivery-control}

Die Aktivität **Versand bearbeiten** ermöglicht es, einen Versand zu starten, auszusetzen oder anzuhalten.

Dies kann die im Übergang angegebene Bereitstellung, eine explizit ausgewählte Bereitstellung oder eine durch ein Skript berechnete Bereitstellung sein. For more on this, refer to [Delivery](../../workflow/using/delivery.md).

![](assets/edit_diffusion_act.png)

Wenn Sie **[!UICONTROL Start]** diese Option auswählen, führt die Aktivität alle zum Starten der Bereitstellung erforderlichen Schritte aus (Zielberechnung, Inhaltsvorbereitung, Bereitstellung). Wenn einige dieser Schritte bereits von einer vorherigen Workflow-Aktivität ausgeführt wurden, werden sie nicht erneut ausgeführt. Wenn die Zielschätzung beispielsweise bereits von einer **[!UICONTROL Delivery]** Typaktivität durchgeführt wurde (siehe [Bereitstellung](../../workflow/using/delivery.md)**[!UICONTROL Act on the delivery]** ), startet die Aktivität die verbleibenden Schritte (Inhaltsvorbereitung und -bereitstellung).

Folgende Optionen stehen zur Verfügung:

* **[!UICONTROL Generate an outbound transition]**

   Erzeugt eine ausgehende Transition im Anschluss an die Aktivität. Sie haben die Wahl, die Zielgruppe der Versandaktion in der Transition zu übermitteln, oder nicht.

* **[!UICONTROL Processing errors]**

   Siehe [Verarbeitungsfehler](../../workflow/using/monitoring-workflow-execution.md#processing-errors).

## Eingabeparameter {#input-parameters}

* deliveryId

Lieferkennung, wenn die ausgewählte Aktion **[!UICONTROL Specified in the transition]** ausgewählt ist.
