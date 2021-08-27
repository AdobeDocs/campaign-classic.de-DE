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

Wenn Sie die Option **[!UICONTROL Keine Konsolenaktualisierung anfordern]** ausgewählt haben und die Aktualisierungsanforderung reaktivieren möchten, gehen Sie wie folgt vor:

1. Öffnen Sie den Editor der Registrierungsdatenbank mithilfe des Befehls **regedit** im Menü Windows **[!UICONTROL Start > Ausführen]** .

   ![](assets/ncs_console_update_1.png)

1. Zeigen Sie im Baum die Optionen des Knotens **[!UICONTROL HKEY_CURRENT_USERSoftwareneolaneNL_6nlclient]** an.
1. Löschen Sie den Eintrag **[!UICONTROL confAdvisedUpgrade]** und schließen Sie den Registrierungs-Editor.

   ![](assets/ncs_console_update_2.png)
