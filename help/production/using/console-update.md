---
product: campaign
title: Konsolenaktualisierung
description: Konsolenaktualisierung
feature: Monitoring, Upgrade
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 3a127bbe-9abb-4b5b-bd7e-e1ea550929ba
TQID: https://experienceleague.adobe.com/oNVXa9DaMu-b-GpfxT-Z0jFbWEd-MnsSzu8Jdb0S0Fw
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
feature_v2: []
subfeature_v2:
  - id: c03a11ff-bdf9-4e5b-b279-f468b4293464
  - id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 64
ht-degree: 9%

---

# Konsolenaktualisierung{#console-update}



Wenn Sie die Option **[!UICONTROL Konsolenaktualisierung nicht anfordern]** ausgewählt haben und die Aktualisierungsanfrage erneut aktivieren möchten, gehen Sie wie folgt vor:

1. Öffnen Sie den Editor der Registrierungsdatenbank mit dem Befehl **regedit** im Menü Windows **[!UICONTROL Start > Ausführen]**.

   ![](assets/ncs_console_update_1.png)

1. Zeigen Sie in der Baumstruktur die Optionen des Knotens **[!UICONTROL HKEY_CURRENT_USERSsoftwareneolaneNL_6nlclient]** an.
1. Löschen Sie den **[!UICONTROL confAdvisedUpgrade]**-Eintrag und schließen Sie den Registrierungs-Editor.

   ![](assets/ncs_console_update_2.png)
