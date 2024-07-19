---
product: campaign
title: Fehlerbehebung
description: Fehlerbehebung
feature: Audiences, People Core Service Integration, Troubleshooting
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
audience: integrations
content-type: reference
topic-tags: audience-sharing
hide: true
hidefromtoc: true
exl-id: 61bb184e-affa-430c-8571-56e911cd5a3d
source-git-commit: b11185da8236d6100d98eabcc9dc1cf2cffa70af
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 100%

---

# Fehlerbehebung{#troubleshooting}



Im Fall von Fehlermeldungen achten Sie darauf, dass die folgenden Elemente richtig konfiguriert sind:

* **Externe Konten**

  Vergewissern Sie sich, dass die folgenden externen SFTP-Konten richtig in **[!UICONTROL Administration > Plattform > Externe Konten]** konfiguriert sind. Die genannten SFTP-Server müssen zuvor von Ihrem Berater in Adobe Experience Cloud konfiguriert werden.

   * **[!UICONTROL importSharedAudience]**: SFTP-Konto für den Zielgruppen-Import.
   * **[!UICONTROL exportSharedAudience]**: SFTP-Konto für den Zielgruppen-Export.

* **AMC Data source**

  Vergewissern Sie sich in **[!UICONTROL Administration > Plattform > AMC Data sources]**, dass die AMC-Datenquelle richtig konfiguriert ist.

Es kann vorkommen, dass manche Daten bei der Freigabe einer Zielgruppe über Experience Cloud Audience oder beim Import einer Zielgruppe fehlen. Es werden nämlich nur Einträge übertragen, deren ID („Visitor ID“ oder „Declared ID“) mit der Profildimension abgestimmt werden konnte. IDs aus Segmenten, die von Adobe Campaign nicht erkannt werden, werden nicht importiert.
