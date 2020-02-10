---
title: Externes Signal
seo-title: Externes Signal
description: Externes Signal
seo-description: null
page-status-flag: never-activated
uuid: dbe6624a-70cf-4ac4-adfd-bc72db9bb3f3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: flow-control-activities
discoiquuid: 3739593f-056c-4165-87ef-63c812bd3c43
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Externes Signal{#external-signal}

Ein **Externes Signal** löst die Ausführung einer Reihe von Aufgaben innerhalb eines Workflows aus.

Wenn eine &quot;externe Signal&quot;-Aufgabe aktiviert wird, wird sie unbegrenzt oder bis zum Ende des angegebenen Zeitraums angehalten. Der Übergang wird durch den SOAP-Aufruf **PostEvent(sessionToken, workflowId, activity, transitions, parameters, complete) aktiviert.** Der **[!UICONTROL complete]** Parameter ermöglicht die Fertigstellung der Aufgabe, sodass er nicht auf nachfolgende Aufrufe reagiert.

Weiterführende Hinweise zu SOAP-Aufrufen und der PostEvent-Funktion finden Sie in der einschlägigen Online-Literatur.

Sie können diese Aktivität so konfigurieren, dass Ereignisse definiert werden, wenn kein Signal empfangen wird. Bearbeiten Sie dazu die Aktivität und klicken Sie auf die **[!UICONTROL Expiration]** Registerkarte. Klicken Sie auf die **[!UICONTROL Insert]** Schaltfläche, um ein Ereignis zu erstellen und zu konfigurieren.

![](assets/edit_signal.png)

The configuration of expirations is detailed in [Expirations](../../workflow/using/executing-a-workflow.md#expirations).

The **Delay** field lets you specify an expiration delay in the units of your choice. Siehe [Warten](../../workflow/using/wait.md).

Jede Zeile stellt einen Ablauftypen dar und entspricht einer Transition.

![](assets/external_sign_diag.png)

