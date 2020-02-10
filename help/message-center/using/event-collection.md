---
title: Ereignisabruf
seo-title: Ereignisabruf
description: Ereignisabruf
seo-description: null
page-status-flag: never-activated
uuid: 8c373962-40d4-4982-9bd1-ce1cf8261dd5
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: event-processing
discoiquuid: cfff302a-6ac0-461a-a1e4-8e4b617fe134
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Ereignisabruf{#event-collection}

Die vom Informationssystem erzeugten Ereignisse können auf zwei Weisen abgerufen werden:

* Aufrufe von SOAP-Methoden ermöglichen Ihnen das Senden von Ereignissen in Adobe Campaign: Mit der PushEvent-Methode können Sie jeweils ein Ereignis senden. Mit der PushEvents-Methode können Sie mehrere Ereignisse gleichzeitig senden. Siehe [Ereignisbeschreibung](../../message-center/using/event-description.md).
* Ausführung eines Workflows, der den Abruf der Ereignisse über einen Dateiimport oder ein SQL-Gateway ermöglicht (mit der Option **Federated Data Access**).

Nach dem Abruf werden die Ereignisse von den technischen Workflows auf die Echtzeit- und Batch-Warteschlangen der Instanzen verteilt, bis sie einer Nachrichtenvorlage zugeordnet werden.

![](assets/messagecenter_events_queues_001.png)

