---
solution: Campaign Classic
product: campaign
title: Wiederkehrender Versand
description: Weitere Informationen zur Aktivität des Arbeitsablaufs für wiederkehrende Versand
audience: workflow
content-type: reference
topic-tags: action-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '208'
ht-degree: 96%

---


# Wiederkehrender Versand{#recurring-delivery}

Ein **[!UICONTROL wiederkehrender Versand]** dient der Konfiguration einer Versandvorlageninstanz im Rahmen einer Kampagne.

Diese Aktivität ist nur im Tab **[!UICONTROL Zielbestimmungen und Workflows]** von Kampagnen verfügbar.

Gehen Sie dazu wie folgt vor:

1. Wählen Sie die Versandvorlage aus, auf der die Aktivität basieren soll.

   ![](assets/recurring_delivery_001.png)

1. Konfigurieren Sie die Versandvorlage.

Die zur Verfügung stehenden Optionen entsprechen denen einer klassischen Versandvorlage. Weiterführende Informationen finden Sie in diesem [Abschnitt](../../delivery/using/about-templates.md).

Ein Anwendungsbeispiel für diese Aktivität ist in diesem [Abschnitt](../../workflow/using/sending-a-birthday-email.md#creating-a-recurring-delivery-in-a-targeting-workflow) enthalten.

## Einrichten eines wiederkehrenden Versands

Ein **wiederkehrender Versand** erstellt bei jeder Ausführung eine neue Versandinstanz. Wenn der Workflow beispielsweise einmal pro Woche ausgeführt werden soll, führt dies nach einem Jahr zu 52 Sendungen. Dies bedeutet auch, dass das Broadlog und die Trackinglogs je Versandinstanz getrennt sind.

![Wiederkehrender Versand](assets/delivery_recurring.jpg)

In diesem Video wird das Konfigurieren eines wiederkehrenden Versands und einer Planungsaktivität erläutert.

>[!VIDEO](https://video.tv.adobe.com/v/25040?quality=12)

>[!NOTE]
>
>Die Durchführung von Testsendungen ist in der Aktivität **[!UICONTROL Wiederkehrender Versand]** nicht möglich.\
>Nutzen Sie zur direkten Erstellung von Sendungen in Kampagnen-Workflows die vorkonfigurierten kanalspezifischen Versandaktionen, wie z. B. **[!UICONTROL E-Mail-Versand]**.
