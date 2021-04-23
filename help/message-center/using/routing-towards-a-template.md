---
solution: Campaign Classic
product: campaign
title: Weiterleitung zu Vorlagen
description: Weiterleitung zu Vorlagen
audience: message-center
content-type: reference
topic-tags: event-processing
exl-id: 2c18c557-f49b-4af8-8795-3d59bd78e63f
translation-type: ht
source-git-commit: 6854d06f8dc445b56ddfde7777f02916a60f2b63
workflow-type: ht
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
* der auf dem Veröffentlichungsdatum basierenden letzten Versandvorlage
