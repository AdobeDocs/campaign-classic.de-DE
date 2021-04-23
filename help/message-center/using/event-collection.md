---
solution: Campaign Classic
product: campaign
title: Ereignisabruf
description: Ereignisabruf
audience: message-center
content-type: reference
topic-tags: event-processing
exl-id: 63cde1c2-8f4c-4cb0-aa98-0c42f9e5f3c6
translation-type: ht
source-git-commit: 6854d06f8dc445b56ddfde7777f02916a60f2b63
workflow-type: ht
source-wordcount: '143'
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
>Auf den Ausführungsinstanzen dürfen die Ordner **[!UICONTROL Echtzeit-Ereignisse]** oder **[!UICONTROL Batch-Ereignisse]** nicht als Ansichten festgelegt werden, da dies zu Problemen mit Zugriffsrechten führen könnte. Weitere Informationen zum Festlegen eines Ordners als Ansicht finden Sie in [diesem Abschnitt](../../platform/using/access-management-folders.md).
