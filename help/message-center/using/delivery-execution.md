---
title: Transaktionsnachrichten-Versand
seo-title: Transaktionsnachrichten-Versand
description: Transaktionsnachrichten-Versand
seo-description: null
page-status-flag: never-activated
uuid: d4f4cea7-783b-45d3-b004-297104f0a906
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: event-processing
discoiquuid: afb375de-2de3-47ad-8b37-664cc04864e8
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 211556bbf023731ffeab2e90692410a852ab3555

---


# Transaktionsnachrichten-Versand{#delivery-execution}

>[!NOTE]
>
>Im MTA hat die Verarbeitung von Transaktionsnachrichten Priorität vor allen anderen Sendungen.

In der Ausführungsinstanz wird die Auslieferung gesendet, sobald die Anreicherungsschritte abgeschlossen sind und eine Bereitstellungsvorlage mit dem Ereignis verknüpft wurde. Alle Auslieferungen werden im **[!UICONTROL Administration > Production > Message Center > Default > Deliveries]** Ordner gruppiert.

![](assets/messagecenter_deliveries_execinstances_001.png)

Sie werden standardmäßig in Unterordnern nach Versandmonat gruppiert.

Diese Gruppierung kann in den Eigenschaften der jeweiligen Nachrichtenvorlage wie im folgenden Beispiel geändert werden:

![](assets/messagecenter_deliveries_properties_001.png)

>[!NOTE]
>
>Bei gehosteten oder hybriden Installationen können nach einem Upgrade auf die erweiterte MTA auch alle Transaktionsmeldungen mit der Adobe Campaign Enhanced MTA gesendet werden, um die Bereitstellung, den Durchsatz und die Absprungbehandlung zu verbessern. Alle Auswirkungen sind dieselben wie für Standard-Marketingmeldungen und werden im Dokument [Adobe Campaign Enhanced MTA](https://helpx.adobe.com/campaign/kb/campaign-enhanced-mta.html) beschrieben.