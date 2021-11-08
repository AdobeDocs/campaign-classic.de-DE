---
product: campaign
title: Konsolenaktualisierung
description: Konsolenaktualisierung
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 3a127bbe-9abb-4b5b-bd7e-e1ea550929ba
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '67'
ht-degree: 8%

---

# Konsolenaktualisierung{#console-update}

![](../../assets/v7-only.svg)

Wenn Sie die Option **[!UICONTROL Konsolenaktualisierung nicht anfordern]** und Sie die Aktualisierungsanforderung erneut aktivieren möchten, gehen Sie wie folgt vor:

1. Öffnen Sie den Editor der Registrierungsdatenbank mithilfe der **regedit** Befehl unter Windows **[!UICONTROL Start > Ausführen]** Menü.

   ![](assets/ncs_console_update_1.png)

1. Zeigen Sie im Baum die Optionen der **[!UICONTROL HKEY_CURRENT_USERSoftwareneolaneNL_6nlclient]** Knoten.
1. Löschen Sie die **[!UICONTROL confAdvisedUpgrade]** den Registrierungs-Editor ein und schließen Sie ihn.

   ![](assets/ncs_console_update_2.png)
