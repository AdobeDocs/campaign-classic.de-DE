---
product: campaign
title: Wiederkehrender Versand
description: Erfahren Sie mehr über die Workflow-Aktivität "Wiederkehrender Versand".
feature: Workflows
hide: true
exl-id: efd2cdfb-2e5f-4672-8be8-a424481b11ed
TQID: https://experienceleague.adobe.com/a33apxZWE9H0Y3ukmFMQMrep1aY95iswu40y-ZjOd0U
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2:
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
feature_v2: []
subfeature_v2:
  - id: ee25c34b-ea50-427b-9369-ba0a160f7d70
  - id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22f
  - id: d1110311-2ca4-442b-be37-088a6db845ee
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 298
ht-degree: 100%

---

# Wiederkehrender Versand{#recurring-delivery}

Ein **[!UICONTROL wiederkehrender Versand]** dient der Konfiguration einer Versandvorlageninstanz im Rahmen einer Kampagne.

![](assets/do-not-localize/how-to-video.png) [Funktion im Video kennenlernen](#recurring-delivery-video).

Diese Aktivität ist nur im Tab **[!UICONTROL Zielgruppenbestimmungen und Workflows]** von Kampagnen verfügbar.

Gehen Sie dazu wie folgt vor:

1. Wählen Sie die Versandvorlage aus, auf der die Aktivität basieren soll.

   ![](assets/recurring_delivery_001.png)

1. Konfigurieren Sie die Versandvorlage.

Die zur Konfiguration dieser Aktivität verfügbaren Optionen entsprechen denen einer Versandvorlage. Weitere Informationen hierzu finden Sie in [diesem Abschnitt](../../delivery/using/about-templates.md).

>[!CAUTION]
>
>Wiederkehrende Sendungen unterstützen nicht die Vorschau oder den Versand von Testsendungen, die [Zielgruppendaten](../../workflow/using/data-life-cycle.md#target-data)-Personalisierungselemente enthalten.

Ein Anwendungsbeispiel für diese Aktivität finden Sie in diesem [Abschnitt](sending-a-birthday-email.md#creating-a-recurring-delivery-in-a-targeting-workflow).

## Einrichten eines wiederkehrenden Versands {#set-up-recurring-delivery}

Ein **wiederkehrender Versand** erstellt bei jeder Ausführung eine neue Versandinstanz. Wenn der Workflow beispielsweise einmal pro Woche ausgeführt werden soll, führt dies nach einem Jahr zu 52 Sendungen. Dies bedeutet auch, dass das Broadlog und die Trackinglogs je Versandinstanz getrennt sind.

![Wiederkehrender Versand](assets/delivery_recurring.jpg)

Wenn Sie die Ausführung eines wiederkehrenden Versands stoppen möchten, sollten Sie die Kampagne vollständig abbrechen oder den Workflow, mit dem sie ausgeführt wird, stoppen. Wird der Versand über das Kampagnen-Dashboard gestoppt, wird nur der aktuelle Versand gestoppt, doch die nächsten Instanzen des wiederkehrenden Versands werden bei jeder Workflow-Ausführung weiterhin erstellt.

>[!NOTE]
>
>Die Durchführung von Testsendungen ist in der Aktivität **[!UICONTROL Wiederkehrender Versand]** nicht möglich.
> 
>Nutzen Sie zur direkten Erstellung von Sendungen in Kampagnen-Workflows die vorkonfigurierten kanalspezifischen Versandaktionen, wie z. B. **[!UICONTROL Wiederkehrender Versand]**.

## Anleitungsvideo {#recurring-delivery-video}

In diesem Video wird das Konfigurieren eines wiederkehrenden Versands und einer Planungsaktivität erläutert.

>[!VIDEO](https://video.tv.adobe.com/v/25040?quality=12)

Weitere Anleitungsvideos zu Campaign Classic finden Sie [hier](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=de).
