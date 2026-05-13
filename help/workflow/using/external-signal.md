---
product: campaign
title: Externes Signal
description: Erfahren Sie mehr über die Workflow-Aktivität "Externes Signal".
feature: Workflows
hide: true
exl-id: da84d3ff-1e64-45ef-bef0-da4a24d93461
TQID: https://experienceleague.adobe.com/2fWd7-VtAc2x-MQm-o5rpGmDsrn6rszSfZxjVDzleTw
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 171
ht-degree: 81%

---

# Externes Signal{#external-signal}



Ein **Externes Signal** löst die Ausführung einer Reihe von Aufgaben innerhalb eines Workflows aus.

Wenn eine Aufgabe „Externes Signal“ aktiviert wird, wird sie unbegrenzt oder bis zum Ende des angegebenen Zeitraums ausgesetzt. Die Transition wird durch den SOAP-Aufruf aktiviert **PostEvent(sessionToken, workflowId, activity, transition, parameters, complete).** Der **[!UICONTROL complete]**-Parameter ermöglicht die Fertigstellung der Aufgabe und reagiert daher nicht auf nachfolgende Aufrufe.

Weiterführende Hinweise zu SOAP-Aufrufen und der PostEvent-Funktion finden Sie in der einschlägigen Online-Literatur.

Sie können diese Aktivität so konfigurieren, dass Ereignisse definiert werden, wenn kein Signal empfangen wird. Bearbeiten Sie hierzu die Aktivität und klicken Sie auf die Registerkarte **[!UICONTROL Gültigkeit]**. Klicken Sie auf die Schaltfläche **[!UICONTROL Einfügen]**, um ein Ereignis zu erstellen und zu konfigurieren.

![](assets/edit_signal.png)

Die Ablauf-Konfiguration wird im Abschnitt [Timeouts](defining-approvals.md) beschrieben.

In der Spalte **Timeout** kann die Zeitspanne vor Ablauf in den Einheiten Ihrer Wahl definiert werden. Siehe [Warten](wait.md).

Jede Zeile stellt einen Ablauftypen dar und entspricht einer Transition.

![](assets/external_sign_diag.png)
