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
translation-type: tm+mt
source-git-commit: 95dff2f3704e316e9ec9e454a8f3fb9835508ccd
workflow-type: tm+mt
source-wordcount: '106'
ht-degree: 50%

---


# Ereignisabruf{#event-collection}

Die vom Informationssystem erzeugten Ereignisse können auf zwei Weisen abgerufen werden:

* Durch Aufrufe der SOAP-Methoden können Sie Ereignis in Adobe Campaign verschieben: Mit der PushEvent-Methode können Sie ein Ereignis gleichzeitig senden. Mit der PushEvents-Methode können Sie mehrere gleichzeitig senden. Siehe [Ereignisbeschreibung](../../message-center/using/event-description.md).
* Creating a workflow lets you recover events by importing files or via an SQL gateway (with the **Federated Data Access** option).

Nach dem Abruf werden die Ereignisse von den technischen Workflows auf die Echtzeit- und Batch-Warteschlangen der Instanzen verteilt, bis sie einer Nachrichtenvorlage zugeordnet werden.

![](assets/messagecenter_events_queues_001.png)
