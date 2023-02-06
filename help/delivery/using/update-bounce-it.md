---
product: campaign
title: Aktualisierung der Bounce-Qualifizierung nach Italia Online-Ausfall
description: Erfahren Sie, wie Sie die Bounce-Qualifizierung nach einem Online-Ausfall von Italia aktualisieren
feature: Deliverability
hide: true
hidefromtow: true
source-git-commit: 3cf6ffb2b69d44b56615492dd9db8965ae3cf4e1
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 27%

---

# Aktualisieren falscher Hardbounces nach Italia Online-Ausfall {#update-bounce-italia}

![](../../assets/common.svg)

## Kontext{#outage-context}

Seit dem 22. Januar (Ortszeit) ist Italia Online durch einen Ausfall gekennzeichnet, der zu mehreren Verzögerungen und Zurückweisungen von E-Mails geführt hat. Der Dienst begann am 26. Januar mit begrenzter Kapazität wieder aufzunehmen.

Betroffene Domänen sind: **libero.it**, **virgilio.it**, **inwind.it**, **iol.it** und **blu.it**.

Dieses Problem trat vom 22.1.2023 bis zum 26.1.2023 auf, aber die meisten fälschlich unter Quarantäne gestellten Fälle wurden am 26. Januar durchgeführt.

Weitere Informationen finden Sie in der offiziellen Mitteilung [here](https://tecnologia.libero.it/avviato-il-ritorno-online-di-libero-mail-e-virgilio-mail-66832){_blank}.


## Auswirkung{#outage-impact}

Bei Ausfall eines ISP können über Campaign versendete E-Mails nicht erfolgreich an ihren Empfänger zugestellt werden: Diese E-Mails werden fälschlicherweise als Bounces markiert. Dies wirkt sich nicht nur auf die Adobe aus, sondern alle, die versuchen, E-Mails an Italia Online zukommen zu lassen.

Die Symptome sind:

* **Rückstellung** mit der Nachricht `452 requested action aborted: try again later` werden beobachtet - diese werden automatisch wiederholt und es sind keine Aktionen erforderlich. Sie sollten sich verbessern, da der ISP seine volle Kapazität wiederherstellt.

* **Hardbounces** mit der Nachricht `550 <email address> recipient rejected` wurden vom ISP am 26. Januar zwischen 8:00 und 14:00 Uhr Ortszeit zurückgegeben, um zu verhindern, dass Absender ihre Server weiterhin überlasten. Wie vom Italia Online Postmaster bestätigt, handelt es sich hierbei nicht um echte Hardbounces. Daher empfehlen wir, die Quarantäne für alle E-Mail-Adressen aufzuheben, die am 26. Januar 2023 aufgrund dieser Nachricht ausgeschlossen wurden.

## Aktualisierungsprozess{#outage-update}

Gemäß der Standardlogik für die Behandlung von Bounces hat Adobe Campaign diese Empfänger automatisch der Quarantäneliste mit dem **[!UICONTROL Status]** **[!UICONTROL Quarantäne]** hinzugefügt. Um dies zu korrigieren, müssen Sie Ihre Quarantänetabelle in Campaign aktualisieren, indem Sie diese Empfänger finden und entfernen oder ihren **[!UICONTROL Status]** auf **[!UICONTROL Gültig]** ändern, damit der nächtliche Bereinigungs-Workflow sie entfernt.

Informationen zu den Empfängern, die von diesem Problem betroffen waren, oder falls dies bei einem anderen ISP erneut der Fall ist, finden Sie in den Anweisungen . [auf dieser Seite](../../delivery/using/understanding-quarantine-management.md#unquarantine-bulk).
