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



Wenn Sie die Option **[!UICONTROL Konsolenaktualisierung nicht anfordern]** ausgewählt haben und die Aktualisierungsanfrage erneut aktivieren möchten, gehen Sie wie folgt vor:

1. Öffnen Sie den Editor der Registrierungsdatenbank mit dem Befehl **regedit** im Menü Windows **[!UICONTROL Start > Ausführen]**.

   ![](assets/ncs_console_update_1.png)

1. Zeigen Sie in der Baumstruktur die Optionen des Knotens **[!UICONTROL HKEY_CURRENT_USERSsoftwareneolaneNL_6nlclient]** an.
1. Löschen Sie den **[!UICONTROL confAdvisedUpgrade]**-Eintrag und schließen Sie den Registrierungs-Editor.

   ![](assets/ncs_console_update_2.png)
