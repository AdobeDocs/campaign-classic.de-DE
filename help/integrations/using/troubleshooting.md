---
title: Problembehebung
seo-title: Problembehebung
description: Problembehebung
seo-description: null
page-status-flag: never-activated
uuid: fb51ad18-221b-4058-b206-ca2ca045c507
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: audience-sharing
discoiquuid: f3ff8c8e-22b0-4d61-9f26-11f5ca3bc0be
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0745b9c9d72538b8573ad18ff4054ecf788905f2

---


# Problembehebung{#troubleshooting}

Im Fall von Fehlermeldungen achten Sie darauf, dass die folgenden Elemente richtig konfiguriert sind:

* **Externe Konten**

   Vergewissern Sie **[!UICONTROL Administration > Platform > External accounts]** sich, dass die folgenden externen SFTP-Konten korrekt konfiguriert sind. Die genannten SFTP-Server sollten von Ihrem Berater in Adobe Experience Cloud konfiguriert worden sein.

   * **[!UICONTROL importSharedAudience]** : SFTP-Konto für den Zielgruppen-Import.
   * **[!UICONTROL exportSharedAudience]** : SFTP-Konto für den Zielgruppen-Export.

* **AMC Data source**

   In **[!UICONTROL Administration > Platform > AMC Data sources]**, check that the AMC Data source is set properly.

Es kann vorkommen, dass manche Daten bei der Freigabe einer Audience über People Core Service oder beim Import einer Audience fehlen. Es werden nämlich nur Datensätze übertragen, deren Kennung (&#39;Visitor ID&#39; oder &#39;Declared ID&#39;) mit der Profildimension abgestimmt werden konnte. Von Adobe Campaign nicht erkannte Kennungen, die People-Core-Service-Segmenten entstammen, werden nicht importiert.
