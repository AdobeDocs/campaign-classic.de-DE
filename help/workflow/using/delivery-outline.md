---
product: campaign
title: Versandentwurf
description: Erfahren Sie mehr über die Workflow-Aktivität "Versandentwurf".
feature: Workflows, Targeting Activity
hide: true
exl-id: b4dee085-ccc4-43fd-850d-1501a99272aa
TQID: https://experienceleague.adobe.com/-KNip5bdMEMgGw7dz6Y4SQ4ueu-iPvYDF0D01hvGn94
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
subfeature_v2:
  - id: ee25c34b-ea50-427b-9369-ba0a160f7d70
  - id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22f
  - id: d1110311-2ca4-442b-be37-088a6db845ee
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 273
ht-degree: 56%

---

# Versandentwurf{#delivery-outline}



Mit **Versandentwurf** können Sie einen Versandentwurf in einem Kampagnen-Workflow verwenden. Der Versandentwurf muss zuvor in der Kampagne erstellt worden sein.

Weiterführende Informationen zu Versandentwürfen finden Sie in diesem [Abschnitt](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline).

Zur Konfiguration der Aktivität wählen Sie einfach den gewünschten Versandentwurf sowie das geplante Kontaktdatum aus. Sie können Filterregeln hinzufügen, indem Sie Typologien oder Typologieregeln hinzufügen.

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

   * Wenn das Angebotsmodul aufgerufen werden soll, aktivieren Sie das Kontrollkästchen **[!UICONTROL Anzahl der ausgewählten Vorschläge]**. Geben Sie die Platzierung und die Anzahl der Vorschläge an, die im Versand unterbreitet werden sollen.

     Gewichtung und Eignungsregeln der Angebote werden vom Angebotsmodul berücksichtigt.

   * Versand ohne Abfrage an das Angebotsmodul: Alle im Versandentwurf enthaltenen Angebote werden unterbreitet.

   Die Vorschau berücksichtigt die Anzahl der im Versand angegebenen Angebote. Beim Ausführen eines Workflows wird die im Versandentwurf angegebene Zahl berücksichtigt.

   ![](assets/int_compo_offre_wf1.png)
