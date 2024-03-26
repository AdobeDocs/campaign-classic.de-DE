---
product: campaign
title: Konsolenaktualisierung
description: Konsolenaktualisierung
feature: Monitoring, Upgrade
badge-v7-only: label="v7" type="Informative" tooltip="Gilt nur für Campaign Classic v7"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 3a127bbe-9abb-4b5b-bd7e-e1ea550929ba
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '71'
ht-degree: 18%

---

# Konsolenaktualisierung{#console-update}



Wenn Sie die Option **[!UICONTROL Konsolenaktualisierung nicht anfordern]** und Sie die Aktualisierungsanforderung erneut aktivieren möchten, gehen Sie wie folgt vor:

1. Öffnen Sie den Editor der Registrierungsdatenbank mithilfe der **regedit** Befehl unter Windows **[!UICONTROL Start > Ausführen]** Menü.

   ![](assets/ncs_console_update_1.png)

1. Zeigen Sie im Baum die Optionen der **[!UICONTROL HKEY_CURRENT_USERSoftwareneolaneNL_6nlclient]** Knoten.
1. Löschen Sie die **[!UICONTROL confAdvisedUpgrade]** den Registrierungseditor eintragen und schließen.

   ![](assets/ncs_console_update_2.png)
