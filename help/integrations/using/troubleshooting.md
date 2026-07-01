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
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
  - id: d5ef99fa-df0c-4153-bf94-105ad0724167
subfeature_v2:
  - id: cbcf4d90-26be-46e2-b16a-aebc529dc41e
  - id: df0d6518-6f49-46e2-b46e-3bcc513f553f
  - id: eb007b6d-6e57-46ab-9485-3f24d6102304
  - id: b1fd1501-3105-4d6b-b4d4-9af53126df75
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 147
ht-degree: 100%

---

# Fehlerbehebung{#troubleshooting}



Im Fall von Fehlermeldungen achten Sie darauf, dass die folgenden Elemente richtig konfiguriert sind:

* **Externe Konten**

  Versichern Sie sich in **[!UICONTROL Administration > Plattform > Externe Konten]**, dass die folgenden externen SFTP-Konten korrekt konfiguriert sind. Die genannten SFTP-Server sollten von Ihrer Beraterin bzw. Ihrem Berater in Adobe Experience Cloud konfiguriert worden sein.

   * **[!UICONTROL importSharedAudience]**: SFTP-Konto für den Zielgruppen-Import.
   * **[!UICONTROL exportSharedAudience]**: SFTP-Konto für den Zielgruppen-Export.

* **AMC Data source**

  Vergewissern Sie sich in **[!UICONTROL Administration > Plattform > AMC Data sources]**, dass die AMC-Datenquelle richtig konfiguriert ist.

Es kann vorkommen, dass manche Daten bei der Freigabe einer Zielgruppe über Experience Cloud Audience oder beim Import einer Zielgruppe fehlen. Es werden nämlich nur Einträge übertragen, deren ID („Visitor ID“ oder „Declared ID“) mit der Profildimension abgestimmt werden konnte. IDs aus Segmenten, die von Adobe Campaign nicht erkannt werden, werden nicht importiert.
