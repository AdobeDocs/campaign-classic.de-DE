---
title: Externes Signal
description: Weitere Informationen zur Workflow-Aktivität für externe Signale
page-status-flag: never-activated
uuid: dbe6624a-70cf-4ac4-adfd-bc72db9bb3f3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: flow-control-activities
discoiquuid: 3739593f-056c-4165-87ef-63c812bd3c43
translation-type: tm+mt
source-git-commit: 6be6c353c3464839a74ba857d8d93d0f68bc8865
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 95%

---


# Externes Signal{#external-signal}

Ein **Externes Signal** löst die Ausführung einer Reihe von Aufgaben innerhalb eines Workflows aus.

Wenn eine Aufgabe „Externes Signal“ aktiviert wird, wird sie unbegrenzt oder bis zum Ende des angegebenen Zeitraums ausgesetzt. Ihre Transition wird durch den SOAP-Aufruf **PostEvent(sessionToken, workflowId, activity, transitions, parameters, complete) aktiviert.** Der **[!UICONTROL complete]**-Parameter ermöglicht die Fertigstellung der Aufgabe, damit sie nicht mehr auf nachfolgende Aufrufe reagiert.

Weiterführende Hinweise zu SOAP-Aufrufen und der PostEvent-Funktion finden Sie in der einschlägigen Online-Literatur.

Es besteht die Möglichkeit, in der Aktivität Ereignisse zu konfigurieren, die bei Abwesenheit von Signalen wirksam werden. Öffnen Sie hierzu die Aktivität und gehen Sie in den Tab **[!UICONTROL Ablauf]**. Klicken Sie auf die Schaltfläche **[!UICONTROL Hinzufügen]**, um Ereignisse zu erstellen und zu konfigurieren.

![](assets/edit_signal.png)

Die Ablauf-Konfiguration wird im Abschnitt [Timeouts](../../workflow/using/defining-approvals.md) beschrieben.

In der Spalte **Timeout** kann die Zeitspanne vor Ablauf in den Einheiten Ihrer Wahl definiert werden. Siehe [Warten](../../workflow/using/wait.md).

Jede Zeile stellt einen Ablauftypen dar und entspricht einer Transition.

![](assets/external_sign_diag.png)

