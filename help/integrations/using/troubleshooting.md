---
solution: Campaign Classic
product: campaign
title: Fehlerbehebung
description: Fehlerbehebung
audience: integrations
content-type: reference
topic-tags: audience-sharing
translation-type: ht
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: ht
source-wordcount: '141'
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

Es kann vorkommen, dass manche Daten bei der Freigabe einer Audience über People Core Service oder beim Import einer Audience fehlen. Es werden nämlich nur Datensätze übertragen, deren Kennung (&#39;Visitor ID&#39; oder &#39;Declared ID&#39;) mit der Profildimension abgestimmt werden konnte. Von Adobe Campaign nicht erkannte Kennungen, die People-Core-Service-Segmenten entstammen, werden nicht importiert.
