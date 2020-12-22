---
solution: Campaign Classic
product: campaign
title: Transaktionsnachrichten-Versand
description: Transaktionsnachrichten-Versand
audience: message-center
content-type: reference
topic-tags: event-processing
translation-type: tm+mt
source-git-commit: 5bc6c8a824929c6a61cf562fc961e5bdd1867837
workflow-type: tm+mt
source-wordcount: '139'
ht-degree: 97%

---


# Transaktionsnachrichten-Versand{#delivery-execution}

## Transaktionsnachricht senden {#transactional-message-send}

Sobald die Anreicherung abgeschlossen ist und eine Versandvorlage mit dem Ereignis verknüpft wurde, erfolgt der Versand in der Ausführungsinstanz.

>[!NOTE]
>
>Im MTA hat die Verarbeitung von Transaktionsnachrichten Priorität vor allen anderen Sendungen.

Alle Sendungen werden im Ordner **[!UICONTROL Administration > Betreibung > Message Center > Standard > Sendungen]** gruppiert.

![](assets/messagecenter_deliveries_execinstances_001.png)

Sie werden standardmäßig in Unterordnern nach Versandmonat gruppiert. Diese Gruppierung kann in den Eigenschaften der jeweiligen Nachrichtenvorlage wie im folgenden Beispiel geändert werden:

![](assets/messagecenter_deliveries_properties_001.png)

>[!NOTE]
>
>Bei gehosteten oder hybriden Installationen können nach einem Upgrade auf den Enhanced MTA auch alle Transaktionsmeldungen mit dem Adobe Campaign Enhanced MTA gesendet werden, um die Zustellbarkeit, den Durchsatz und die Bearbeitung von Bounces zu verbessern. Alle Folgen sind dieselben wie bei standardmäßigen Marketing-Nachrichten und werden im Dokument [Adobe Campaign Enhanced MTA](https://helpx.adobe.com/campaign/kb/acc-campaign-enhanced-mta.html) beschrieben.

<!--## Transactional message monitoring {#transactional-message-monitoring}

To monitor your transactional messages, check the delivery logs. Accessing the delivery logs is presented in [this section](../../delivery/using/monitoring-a-delivery.md#delivery-logs-and-history).

The transactional deliveries sent from the execution instance are synchronized back to the control instance as follows.

Let's take a [delivery template](../../message-center/using/introduction.md) labelled *Template_1*.

1. An event corresponding to *Template_1* is received on the execution instance.
1. The **Processing real time events** (rtEventsProcessing) workflow processes the event and searches for an existing delivery for the current month.

    >[!NOTE]
    >
    >If not found, a new delivery is created and the event is assigned to the new delivery.

1. The transactional email is sent and the delivery status changes to **[!UICONTROL Sent]**.
1. The **Message Center execution instance** (mcSync_mcExec) workflow retrieves the delivery logs from the execution instance and updates the delivery logs on the control instance.
1. The control instance searches for an existing delivery for week 40 (2020-09-28_Template_1).

    >[!NOTE]
    >
    >If not found, a new delivery is created.

1. The week after, an inbound bounce is received for the event.
1. The status of the event changes to **[!UICONTROL Delivery failed]**.
1. The **Message Center execution instance** (mcSync_mcExec) workflow retrieves the delivery logs from the execution instance and searches for a delivery for week 41 (2020-10-05_Template_1) to update the delivery logs. The delivery logs are then linked to a new delivery for the current week.

To summarize, the deliveries weekly accumulate the events based on the latest event update, and not on the event creation date.

Therefore, when extracting transactional messaging delivery logs from the control instance, the delivery ID associated with each delivery log ID changes every week.-->