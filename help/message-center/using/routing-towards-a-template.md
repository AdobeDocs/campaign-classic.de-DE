---
solution: Campaign Classic
product: campaign
title: Weiterleitung zu Vorlagen
description: Weiterleitung zu Vorlagen
audience: message-center
content-type: reference
topic-tags: event-processing
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '121'
ht-degree: 100%

---


# Weiterleitung zu Vorlagen{#routing-towards-a-template}

Wenn eine Nachrichtenvorlage auf der oder den Ausführungsinstanz(en) veröffentlicht wurde, werden jeweils zwei Vorlagen automatisch erzeugt, die Echtzeit- bzw. Batch-Ereignissen zugeordnet werden. Bei der Weiterleitung des Ereignisses wird dieses der ihm entsprechenden Vorlage zugeordnet. Die Zuordnung von Ereignis und Nachrichtenvorlage hängt von dem in den Eigenschaften des Ereignisses und der Vorlage festgelegten Ereignistyp ab.

Bestimmung des Ereignistyps in den Ereigniseigenschaften:

![](assets/messagecenter_event_type_001.png)

Bestimmung des Ereignistyps in den Vorlageneigenschaften:

![](assets/messagecenter_event_type_002.png)

Standardmäßig basiert die Weiterleitung auf folgenden Informationen:

* dem Ereignistyp
* dem verwendeten Kanal (standardmäßig: E-Mail)
* der auf dem Publikationsdatum basierenden letzten Versandvorlage
