---
product: campaign
title: Versandentwurf
description: Erfahren Sie mehr über die Workflow-Aktivität "Versandentwurf".
feature: Workflows, Targeting Activity
hide: true
exl-id: b4dee085-ccc4-43fd-850d-1501a99272aa
TQID: 'https://experienceleague.adobe.com/-KNip5bdMEMgGw7dz6Y4SQ4ueu-iPvYDF0D01hvGn94'
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
  - id: ff84ab2f-a7c2-4ced-a3c8-5113f4348d99
    internal-label: Targeting Activity
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '273'
ht-degree: 100%
---
# Versandentwurf{#delivery-outline}



Der **Versandentwurf** ermöglicht Ihnen die Verwendung eines Entwurfs im Kampagnen-Workflow. Der Entwurf muss zuvor in der Kampagne erstellt worden sein.

Weiterführende Informationen zu Versandentwürfen finden Sie in diesem [Abschnitt](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline).

Zum Konfigurieren der Aktivität müssen Sie einfach den gewünschten Entwurf sowie das geplante Kontaktdatum auswählen. Sie können Filterregeln hinzufügen, indem Sie Typologien oder Typologieregeln hinzufügen.

## Anwendungsbeispiel: Einfügung eines Angebots mithilfe eines Versandentwurfs {#example--inserting-an-offer-via-a-delivery-outline}

Die in Kampagnen-Workflows zur Verfügung stehende Aktivität **Versandentwurf** erlaubt es, Angebote zu unterbreiten, die in einem Versandentwurf der aktuellen Kampagne referenziert wurden.

>[!NOTE]
>
>Für das vorliegende Anwendungsbeispiel benötigen Sie das **Interaction**-Package.

1. Platzieren Sie hierfür im Workflow die Versandentwurfsaktivität vor einer Versandaktivität.
1. Geben Sie in der Versandentwurfsaktivität den gewünschten Entwurf an.

   Nähere Informationen zu Versandentwürfen erhalten Sie in [diesem Abschnitt](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline).

1. Füllen Sie die verfügbaren Felder Ihrem Versand entsprechend aus.
1. Sie haben zwei Möglichkeiten:

   * Wenn Sie eine Abfrage des Angebotsmoduls durchführen möchten, aktivieren Sie das Feld **[!UICONTROL Anzahl der ausgewählten Vorschläge begrenzen]**. Geben Sie die Platzierung und die Anzahl der Vorschläge an, die im Versand unterbreitet werden sollen.

     Gewichtung und Eignungsregeln der Angebote werden vom Angebotsmodul berücksichtigt.

   * Versand ohne Abfrage an das Angebotsmodul: Alle im Versandentwurf enthaltenen Angebote werden unterbreitet.

   Die Vorschau berücksichtigt die im Versand angegebene Anzahl an Angeboten. Bei Ausführung eines Workflows wird die im Versandentwurf angegebene Anzahl berücksichtigt.

   ![](assets/int_compo_offre_wf1.png)
