---
product: campaign
title: Fehlerbehebung
description: Fehlerbehebung
audience: integrations
content-type: reference
topic-tags: audience-sharing
exl-id: 61bb184e-affa-430c-8571-56e911cd5a3d
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 100%

---

# Fehlerbehebung{#troubleshooting}

![](../../assets/common.svg)

Im Fall von Fehlermeldungen achten Sie darauf, dass die folgenden Elemente richtig konfiguriert sind:

* **Externe Konten**

   Vergewissern Sie sich, dass die folgenden externen SFTP-Konten richtig in **[!UICONTROL Administration > Plattform > Externe Konten]** konfiguriert sind. Die genannten SFTP-Server müssen zuvor von Ihrem Berater in Adobe Experience Cloud konfiguriert werden.

   * **[!UICONTROL importSharedAudience]**: SFTP-Konto für den Zielgruppen-Import.
   * **[!UICONTROL exportSharedAudience]**: SFTP-Konto für den Zielgruppen-Export.

* **AMC Data source**

   Vergewissern Sie sich in **[!UICONTROL Administration > Plattform > AMC Data sources]**, dass die AMC-Datenquelle richtig konfiguriert ist.

Es kann vorkommen, dass manche Daten bei der Freigabe einer Audience über People Core Service oder beim Import einer Audience fehlen. Es werden nämlich nur Datensätze übertragen, deren Kennung (&#39;Visitor ID&#39; oder &#39;Declared ID&#39;) mit der Profildimension abgestimmt werden konnte. Von Adobe Campaign nicht erkannte Kennungen, die People-Core-Service-Segmenten entstammen, werden nicht importiert.
