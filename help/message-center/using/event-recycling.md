---
solution: Campaign Classic
product: campaign
title: Ereignis-Recycling
description: Ereignis-Recycling
audience: message-center
content-type: reference
topic-tags: event-processing
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 100%

---


# Ereignis-Recycling{#event-recycling}

Wenn der Versand einer Nachricht über einen bestimmten Kanal fehlschlägt, kann Adobe Campaign über einen anderen Kanal einen erneuten Versandversuch starten. Wenn beispielsweise der Versand einer Nachricht über den SMS-Kanal fehlschlägt, wird die Nachricht über den E-Mail-Kanal erneut versandt.

Konfigurieren Sie hierzu einen Workflow, der alle Ereignisse mit **Versandfehler** neu erstellt und ihnen einen sich vom ersten Kanal unterscheidenden Kanal zuordnet.

>[!CAUTION]
>
>Diese Etappe ist nur mithilfe eines Workflows durchführbar und richtet sich daher an fortgeschrittene Benutzer. Für weiterführende Informationen kontaktieren Sie bitte Ihren Adobe-Kundenbetreuer.

