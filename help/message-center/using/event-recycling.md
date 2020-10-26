---
title: Ereignis-Recycling
seo-title: Ereignis-Recycling
description: Ereignis-Recycling
seo-description: null
page-status-flag: never-activated
uuid: 55624a41-65a1-4759-8087-6e5d2c5c5b62
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: event-processing
discoiquuid: 568a9dec-5818-4666-b858-aa41fe827b92
translation-type: ht
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: ht
source-wordcount: '97'
ht-degree: 100%

---


# Ereignis-Recycling{#event-recycling}

Wenn der Versand einer Nachricht über einen bestimmten Kanal fehlschlägt, kann Adobe Campaign über einen anderen Kanal einen erneuten Versandversuch starten. Wenn beispielsweise der Versand einer Nachricht über den SMS-Kanal fehlschlägt, wird die Nachricht über den E-Mail-Kanal erneut versandt.

Konfigurieren Sie hierzu einen Workflow, der alle Ereignisse mit **Versandfehler** neu erstellt und ihnen einen sich vom ersten Kanal unterscheidenden Kanal zuordnet.

>[!CAUTION]
>
>Diese Etappe ist nur mithilfe eines Workflows durchführbar und richtet sich daher an fortgeschrittene Benutzer. Für weiterführende Informationen kontaktieren Sie bitte Ihren Adobe-Kundenbetreuer.

