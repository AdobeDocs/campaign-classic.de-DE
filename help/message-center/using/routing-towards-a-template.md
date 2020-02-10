---
title: Weiterleitung zu Vorlagen
seo-title: Weiterleitung zu Vorlagen
description: Weiterleitung zu Vorlagen
seo-description: null
page-status-flag: never-activated
uuid: 1f8252c4-7f96-4759-9544-39b8f854961f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: event-processing
discoiquuid: 8fa464e6-3c88-441c-8179-0c54960469a7
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Weiterleitung zu Vorlagen{#routing-towards-a-template}

Wenn eine Nachrichtenvorlage auf der oder den Ausführungsinstanz(en) veröffentlicht wurde, werden jeweils zwei Vorlagen automatisch erzeugt, die Echtzeit- bzw. Batch-Ereignissen zugeordnet werden. Bei der Weiterleitung des Ereignisses wird dieses der ihm entsprechenden Vorlage zugeordnet. Die Zuordnung von Ereignis und Nachrichtenvorlage hängt von dem in den Eigenschaften des Ereignisses und der Vorlage festgelegten Ereignistyp ab.

Bestimmung des Ereignistyps in den Ereigniseigenschaften:

![](assets/messagecenter_event_type_001.png)

Bestimmung des Ereignistyps in den Vorlageneigenschaften:

![](assets/messagecenter_event_type_002.png)

Standardmäßig basiert die Weiterleitung auf folgenden Informationen:

* dem Ereignistyp,
* dem verwendeten Kanal (standardmäßig: E-Mail),
* der auf dem Publikationsdatum basierenden letzten Versandvorlage.

