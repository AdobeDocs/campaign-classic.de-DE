---
solution: Campaign Classic
product: campaign
title: Konsolenaktualisierung
description: Konsolenaktualisierung
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '67'
ht-degree: 8%

---


# Konsolenaktualisierung{#console-update}

Wenn Sie die Option **[!UICONTROL Keine Anforderung der Aktualisierung]** der Konsole aktivieren und die Aktualisierungsanforderung erneut aktivieren möchten, führen Sie folgendes Verfahren aus:

1. Öffnen Sie den Editor der Registrierungsdatenbank mit dem Befehl **regedit** im Menü Windows **[!UICONTROL Beginn > Ausführen]** .

   ![](assets/ncs_console_update_1.png)

1. Zeigen Sie in der Struktur die Optionen des Knotens **[!UICONTROL HKEY_CURRENT_USERSoftwareneolaneNL_6nlclient]** an.
1. Löschen Sie den Eintrag **[!UICONTROL confAdvisedUpgrade]** und schließen Sie den Registrierungseditor.

   ![](assets/ncs_console_update_2.png)

