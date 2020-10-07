---
title: Konsolenaktualisierung
seo-title: Konsolenaktualisierung
description: Konsolenaktualisierung
seo-description: null
page-status-flag: never-activated
uuid: d2193d4f-b98c-47b1-88f1-7e5ccf4c453c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: 9281808b-1c2f-4095-9051-f181f089f205
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '69'
ht-degree: 11%

---


# Konsolenaktualisierung{#console-update}

Wenn Sie die Option **[!UICONTROL Keine Anforderung der Aktualisierung]** der Konsole aktivieren und die Aktualisierungsanforderung erneut aktivieren möchten, führen Sie folgendes Verfahren aus:

1. Öffnen Sie den Editor der Registrierungsdatenbank mit dem Befehl **regedit** im Menü Windows **[!UICONTROL Beginn > Ausführen]** .

   ![](assets/ncs_console_update_1.png)

1. Zeigen Sie in der Struktur die Optionen des Knotens **[!UICONTROL HKEY_CURRENT_USERSoftwareneolaneNL_6nlclient]** an.
1. Löschen Sie den Eintrag **[!UICONTROL confAdvisedUpgrade]** und schließen Sie den Registrierungseditor.

   ![](assets/ncs_console_update_2.png)

