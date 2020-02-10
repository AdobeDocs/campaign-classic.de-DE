---
title: Interaction
seo-title: Interaction
description: Interaction
seo-description: null
page-status-flag: never-activated
uuid: 5c8e2353-bb76-4e8d-95d7-61b6c111b6b3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: technical-workflows
discoiquuid: 1683477a-9233-4a25-b0d0-0c81051eb440
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 28a32c9a5300c28784ae7a2837075b4dc3aad1fa

---


# Interaction{#interaction}

Der folgende Workflow wird mit dem **Angebotsmodul (Interaction)** installiert. Weiterführende Informationen zum Modul finden Sie in diesem [Abschnitt](../../interaction/using/interaction-and-offer-management.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Titel</strong><br /> </td> 
   <td> <strong>Interner Name</strong><br /> </td> 
   <td> <strong>Beschreibung</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Berechnung des full-Aggregats (cube propositionrcp)</span> <br /> </td> 
   <td> <span class="uicontrol">agg_nmspropositionrcp_full</span> <br /> </td> 
   <td> Dieser Workflow aktualisiert das <strong>full</strong>-Aggregat des <strong>Angebotsvorschlag</strong>-Cubes. Es wird standardmäßig täglich um 6 Uhr gestartet. Dieses Aggregat erfasst die folgenden Dimensionen: Kanal, Versand, Marketingangebot und Datum.<br /> Mit dem <strong>Angebotsvorschlag</strong>-Cube können anschließend Berichte auf der Basis von Angeboten erstellt werden. Weiterführende Informationen zu Cubes finden Sie in <a href="../../reporting/using/about-cubes.md">diesem Abschnitt</a>.<br /> </td> 
  </tr> 
   <tr> 
   <td> <span class="uicontrol">Vollständige Berechnung</span> von MessageCenter <br /> </td> 
   <td> <span class="uicontrol">agg_messageCenter_full</span><br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

