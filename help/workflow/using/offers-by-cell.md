---
product: campaign
title: Angebote pro Segment
description: Angebote pro Segment
feature: Workflows, Targeting Activity, Interaction
hide: true
exl-id: 72b17b48-093a-4eb9-a848-3c1570e49b61
TQID: https://experienceleague.adobe.com/ddCHWdqnyWjUtP3lcc3yIaUHffGkNCbnVKWiJVfhdjg
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
subfeature_v2:
  - id: ee25c34b-ea50-427b-9369-ba0a160f7d70
  - id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22f
  - id: d1110311-2ca4-442b-be37-088a6db845ee
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 162
ht-degree: 80%

---

# Angebote pro Segment{#offers-by-cell}



Mithilfe der Aktivität **[!UICONTROL Angebote pro Segment]** lässt sich die eingehende Population (die beispielsweise aus einer Abfrage hervorgeht) in mehrere Zielgruppen aufspalten, um so je Segment spezifische Angebote zu unterbreiten.

Diese Aktivität kann nur mit **Interaktion** verwendet werden. Weiterführende Informationen hierzu finden Sie in diesem [Abschnitt](../../interaction/using/about-outbound-channels.md).

Gehen Sie dazu wie folgt vor:

1. Platzieren Sie im Anschluss an die Abfrage der Zielpopulation eine Aktivität **[!UICONTROL Angebote pro Segment]** und öffnen Sie sie zur weiteren Bearbeitung.
1. Wählen Sie auf der Registerkarte **[!UICONTROL Allgemein]** die Platzierung, über die Sie Angebote unterbreiten möchten.
1. Definieren Sie nun auf der Registerkarte **[!UICONTROL Segmente]** über die Schaltfläche **[!UICONTROL Hinzufügen]** die verschiedenen Segmente:

   * Konfigurieren Sie anhand der verfügbaren Filter und Begrenzungen die Population des Segments.
   * Wählen Sie als Nächstes das Angebot aus, das Sie der Untergruppe unterbreiten möchten. Die verfügbaren Angebote sind diejenigen, die für die Platzierung infrage kommen, die im vorherigen Schritt ausgewählt wurde.

     ![](assets/int_offer_per_cell1.png)

1. Konfigurieren Sie dann eine Versandaktivität, die dem von Ihnen gewählten Kanal entspricht. Siehe [Kanalübergreifender Versand](cross-channel-deliveries.md).
