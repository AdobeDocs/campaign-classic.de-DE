---
product: campaign
title: Versand bearbeiten
description: Erfahren Sie mehr über die Workflow-Aktivität "Versand bearbeiten".
feature: Workflows
hide: true
exl-id: c7cface2-0837-4e6a-91dc-b8353010a7a4
TQID: 'https://experienceleague.adobe.com/WVXqtjcGQQOQJfVi58BqtLPqgG7AkgslAzQk4Vjbl9k'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
subfeature_v2:
  - id: ee25c34b-ea50-427b-9369-ba0a160f7d70
    internal-label: HeatMap
  - id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22f
    internal-label: Execution activities
  - id: d1110311-2ca4-442b-be37-088a6db845ee
    internal-label: Data Management activities
  - id: fcb46c0f-76e1-48bc-9dd0-fcf9d97526cf
    internal-label: Workflows
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 100%
---
# Versand bearbeiten{#delivery-control}



Die Aktivität **Versand bearbeiten** ermöglicht es, einen Versand zu starten, zu stoppen oder anzuhalten.

Hierbei kann es sich um einen durch die eingehende Transition bezeichneten, einen explizit angegebenen oder einen durch ein Script berechneten Versand handeln. Weitere Informationen hierzu finden Sie im Abschnitt [Versand](delivery.md).

![](assets/edit_diffusion_act.png)

Wenn Sie **[!UICONTROL Starten]** auswählen, führt die Aktivität alle zum Starten des Versands erforderlichen Schritte aus (Zielgruppenberechnung, Inhaltsvorbereitung, Versand). Wenn einige dieser Schritte bereits von einer vorherigen Workflow-Aktivität ausgeführt wurden, werden sie nicht erneut ausgeführt. Wenn zum Beispiel die Zielgruppenschätzung bereits von einer Aktivität vom Typ **[!UICONTROL Versand]** durchgeführt wurde (siehe [Versand](delivery.md)), startet die Aktivität **[!UICONTROL Mit Versand arbeiten]** die verbleibenden Schritte (Inhaltsvorbereitung und Versand).

Folgende Optionen stehen zur Verfügung:

* **[!UICONTROL Ausgehende Transition erzeugen]**

  Erstellt eine ausgehende Transition, die am Ende der Ausführung aktiviert wird. Sie können die Zielgruppe des ausgehenden Versands entweder abrufen oder auch nicht.

* **[!UICONTROL Fehler verarbeiten]**

  Siehe [Fehler verarbeiten](monitoring-workflow-execution.md#processing-errors).

## Eingabeparameter {#input-parameters}

* deliveryId

Kennung des Versands, wenn die Option **[!UICONTROL Wird durch die Transition angegeben]** ausgewählt wurde.
