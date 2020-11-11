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
translation-type: ht
source-git-commit: 95dff2f3704e316e9ec9e454a8f3fb9835508ccd
workflow-type: ht
source-wordcount: '106'
ht-degree: 100%

---


# Ereignisabruf{#event-collection}

Die vom Informationssystem erzeugten Ereignisse können auf zwei Weisen abgerufen werden:

* Nutzung von SOAP-Methoden, die die Ereignisse Adobe Campaign zuführen: Die PushEvent-Methode ermöglicht den Versand eines Ereignisses, die PushEvents-Methode den Versand mehrerer Ereignisse auf einmal. Siehe [Ereignisbeschreibung](../../message-center/using/event-description.md).
* Ausführung eines Workflows, der den Abruf der Ereignisse über einen Dateiimport oder ein SQL-Gateway ermöglicht (mit der Option **Federated Data Access**).

Nach dem Abruf werden die Ereignisse von den technischen Workflows auf die Echtzeit- und Batch-Warteschlangen der Instanzen verteilt, bis sie einer Nachrichtenvorlage zugeordnet werden.

![](assets/messagecenter_events_queues_001.png)
