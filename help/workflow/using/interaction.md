---
product: campaign
title: Interaktion
description: Interaction
hide: true
hidefromtoc: true
feature: Workflows, Interaction, Offers
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '160'
ht-degree: 100%

---


# Interaktion{#interaction}



Die folgenden Workflows werden standardmäßig mit dem **Angebotsmodul (Interaction)** installiert.

Weitere Informationen hierzu finden Sie je nach Campaign-Version in den folgenden Abschnitten: 

![](assets/do-not-localize/v7.jpeg)[Dokumentation zu Campaign v7](../../interaction/using/interaction-and-offer-management.md)

![](assets/do-not-localize/v8.png)[Dokumentation zu Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/interaction/interaction.html?lang=de)


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
   <td> Dieser Workflow aktualisiert das <strong>full</strong>-Aggregat des <strong>Angebotsvorschlag</strong>-Cubes. Es wird standardmäßig täglich um 6 Uhr gestartet. Dieses Aggregat erfasst die folgenden Dimensionen: Kanal, Versand, Marketing-Angebot und Datum.<br /> Mit dem <strong>Angebotsvorschlag</strong>-Cube können anschließend Berichte auf der Basis von Angeboten erstellt werden. Weitere Informationen zu Cubes finden Sie in <a href="../../reporting/using/ac-cubes.md">diesem Abschnitt</a>.<br /> </td> 
  </tr> 
   <tr> 
   <td> <span class="uicontrol">Vollständige Message Center-Aggregatberechnung</span> <br /> </td> 
   <td> <span class="uicontrol">agg_messageCenter_full</span> <br /> </td> 
   <td> Dieser Workflow aktualisiert das <strong>vollständige</strong> Aggregat für den <strong>Message Center</strong>-Cube. Er wird standardmäßig jeden Tag um 3 Uhr morgens ausgelöst. Dieses Aggregat erfasst die folgenden Dimensionen: Kanal, Datum, Status und Ereignistyp.<br /> Der <strong>Message Center</strong>-Cube wird dann zur Erstellung von ereignisbasierten Berichten verwendet. Weitere Informationen zu Cubes finden Sie in <a href="../../reporting/using/ac-cubes.md">diesem Abschnitt</a>.<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

