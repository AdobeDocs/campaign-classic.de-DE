---
solution: Campaign Classic
product: campaign
title: Ereignisabruf
description: Ereignisabruf
audience: message-center
content-type: reference
topic-tags: event-processing
translation-type: tm+mt
source-git-commit: d1130691e40c0cac183db37a4c0b410d00bb696a
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 100%

---


# Ereignisabruf{#event-collection}

Die vom Informationssystem erzeugten Ereignisse können auf zwei Weisen abgerufen werden:

* Nutzung von SOAP-Methoden, die die Ereignisse Adobe Campaign zuführen: Die PushEvent-Methode ermöglicht den Versand eines Ereignisses, die PushEvents-Methode den Versand mehrerer Ereignisse auf einmal. Siehe [Ereignisbeschreibung](../../message-center/using/event-description.md).
* Ausführung eines Workflows, der den Abruf der Ereignisse über einen Dateiimport oder ein SQL-Gateway ermöglicht (mit der Option **Federated Data Access**).

Nach dem Abruf werden die Ereignisse von den technischen Workflows auf die Echtzeit- und Batch-Warteschlangen der Instanzen verteilt, bis sie einer Nachrichtenvorlage zugeordnet werden.

![](assets/messagecenter_events_queues_001.png)

>[!NOTE]
>
>Auf den Ausführungsinstanzen dürfen die Ordner **[!UICONTROL Echtzeitereignisse]** oder **[!UICONTROL Batch-Ereignisse]** nicht als Ansichten festgelegt werden, da dies zu Problemen mit [Zugriffsrechten](../../platform/using/access-management.md#about-permissions) führen könnte. Weitere Informationen zum Festlegen eines Ordners als Ansicht finden Sie unter dem Abschnitt [Über Ansichten](../../platform/using/access-management.md#about-views).
