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
source-git-commit: bc227c2da2e8b1a78714748809ad40bbcefe0458

---


# Transaktionsnachrichten-Versand{#delivery-execution}

>[!NOTE]
>
>Im MTA hat die Verarbeitung von Transaktionsnachrichten Priorität vor allen anderen Sendungen.

Auf der Ausführungsinstanz wird der Versand gesendet, sobald die Anreicherung abgeschlossen ist und eine Versandvorlage mit dem Ereignis verknüpft wurde. Alle Versand sind im **[!UICONTROL Administration > Production > Message Center > Default > Deliveries]** Ordner gruppiert.

![](assets/messagecenter_deliveries_execinstances_001.png)

Sie werden standardmäßig in Unterordnern nach Versandmonat gruppiert.

Diese Gruppierung kann in den Eigenschaften der jeweiligen Nachrichtenvorlage wie im folgenden Beispiel geändert werden:

![](assets/messagecenter_deliveries_properties_001.png)

>[!NOTE]
>
>Bei gehosteten oder hybriden Installationen können, wenn Sie auf die erweiterte MTA aktualisiert haben, alle Transaktionsnachrichten auch mit der Adobe Campaign Enhanced MTA gesendet werden, um die Bereitstellung, den Durchsatz und die Absprungbehandlung zu verbessern. Alle Auswirkungen sind dieselben wie bei standardmäßigen Marketing-Nachrichten und werden im Dokument [Erweiterter MTA von Adobe Campaign](https://helpx.adobe.com/campaign/kb/campaign-enhanced-mta.html) beschrieben.