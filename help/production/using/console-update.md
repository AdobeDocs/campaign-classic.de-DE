---
product: campaign
title: Konsolenaktualisierung
description: Konsolenaktualisierung
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 3a127bbe-9abb-4b5b-bd7e-e1ea550929ba
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '67'
ht-degree: 8%

---

# Konsolenaktualisierung{#console-update}



Wenn Sie die Option **[!UICONTROL Konsolenaktualisierung nicht anfordern]** und Sie die Aktualisierungsanforderung erneut aktivieren möchten, gehen Sie wie folgt vor:

1. Öffnen Sie den Editor der Registrierungsdatenbank mithilfe der **regedit** Befehl unter Windows **[!UICONTROL Start > Ausführen]** Menü.

   ![](assets/ncs_console_update_1.png)

1. Zeigen Sie im Baum die Optionen der **[!UICONTROL HKEY_CURRENT_USERSoftwareneolaneNL_6nlclient]** Knoten.
1. Löschen Sie die **[!UICONTROL confAdvisedUpgrade]** den Registrierungs-Editor ein und schließen Sie ihn.

   ![](assets/ncs_console_update_2.png)
