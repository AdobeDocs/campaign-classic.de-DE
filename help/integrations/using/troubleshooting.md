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
exl-id: 61bb184e-affa-430c-8571-56e911cd5a3d
TQID: https://experienceleague.adobe.com/4de9cxyepP-REa2OTWniBFWInphApeUM79sZuFGcynI
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: c5474392-5419-4296-9e41-f6f4ce4f6e9bid: d5ef99fa-df0c-4153-bf94-105ad0724167
subfeature_v2: id: a39dbcf0-89cb-4765-9bcb-cf9dfbe2875fid: a8512b64-d668-4084-b4f0-34baa899e306
topic_v2: id: c1579802-ddd4-4214-8a91-97b2066abe11id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 147
ht-degree: 78%

---

# Fehlerbehebung{#troubleshooting}



Im Fall von Fehlermeldungen achten Sie darauf, dass die folgenden Elemente richtig konfiguriert sind:

* **Externe Konten**

  Stellen **[!UICONTROL unter Administration > Plattform > Externe]** sicher, dass die folgenden externen SFTP-Konten korrekt konfiguriert sind. Die genannten SFTP-Server sollten von Ihrem Berater in Adobe Experience Cloud konfiguriert worden sein.

   * **[!UICONTROL importSharedAudience]**: SFTP-Konto für den Zielgruppen-Import.
   * **[!UICONTROL exportSharedAudience]**: SFTP-Konto für den Zielgruppen-Export.

* **AMC Data source**

  Vergewissern Sie sich in **[!UICONTROL Administration > Plattform > AMC Data sources]**, dass die AMC-Datenquelle richtig konfiguriert ist.

Es kann vorkommen, dass manche Daten bei der Freigabe einer Zielgruppe über Experience Cloud Audience oder beim Import einer Zielgruppe fehlen. Es werden nämlich nur Einträge übertragen, deren ID („Visitor ID“ oder „Declared ID“) mit der Profildimension abgestimmt werden konnte. IDs aus Segmenten, die von Adobe Campaign nicht erkannt werden, werden nicht importiert.
