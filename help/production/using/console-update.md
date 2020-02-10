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
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Konsolenaktualisierung{#console-update}

Wenn Sie die **[!UICONTROL Do not request console update]** Option ausgewählt haben und die Aktualisierungsanforderung erneut aktivieren möchten, führen Sie folgendes Verfahren aus:

1. Öffnen Sie den Editor der Registrierungsdatenbank mit dem Befehl **regedit** im Windows- **[!UICONTROL Start > Execute]** Menü.

   ![](assets/ncs_console_update_1.png)

1. Zeigen Sie in der Struktur die Optionen des **[!UICONTROL HKEY_CURRENT_USERSoftwareneolaneNL_6nlclient]** Knotens an.
1. Löschen Sie den **[!UICONTROL confAdvisedUpgrade]** Eintrag und schließen Sie den Registrierungseditor.

   ![](assets/ncs_console_update_2.png)

