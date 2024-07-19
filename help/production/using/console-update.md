---
product: campaign
title: Konsolenaktualisierung
description: Konsolenaktualisierung
feature: Monitoring, Upgrade
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 3a127bbe-9abb-4b5b-bd7e-e1ea550929ba
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '64'
ht-degree: 9%

---

# Konsolenaktualisierung{#console-update}



Wenn Sie die Option **[!UICONTROL Keine Konsolenaktualisierung anfordern]** ausgewählt haben und die Aktualisierungsanforderung erneut aktivieren möchten, gehen Sie wie folgt vor:

1. Öffnen Sie den Editor der Registrierungsdatenbank mithilfe des Befehls **regedit** im Menü Windows **[!UICONTROL Start > Ausführen]** .

   ![](assets/ncs_console_update_1.png)

1. Zeigen Sie im Baum die Optionen des Knotens **[!UICONTROL HKEY_CURRENT_USERSoftwareneolaneNL_6nlclient]** an.
1. Löschen Sie den Eintrag **[!UICONTROL confAdvisedUpgrade]** und schließen Sie den Registrierungs-Editor.

   ![](assets/ncs_console_update_2.png)
