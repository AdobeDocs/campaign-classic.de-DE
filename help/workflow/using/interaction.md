---
solution: Campaign Classic
product: campaign
title: Interaction
description: Interaction
audience: workflow
content-type: reference
topic-tags: technical-workflows
translation-type: ht
source-git-commit: affc541c480ad7e618120fe90270841add06b711
workflow-type: ht
source-wordcount: '153'
ht-degree: 100%

---


# Interaction{#interaction}

Die folgenden Workflows werden standardmäßig mit dem **Angebotsmodul (Interaction)** installiert. Weiterführende Informationen zu dem Modul finden Sie in diesem [Abschnitt](../../interaction/using/interaction-and-offer-management.md).

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
   <td> <span class="uicontrol">Vollständige Message Center-Aggregatberechnung</span> <br /> </td> 
   <td> <span class="uicontrol">agg_messageCenter_full</span> <br /> </td> 
   <td> Dieser Workflow aktualisiert das <strong>vollständige</strong> Aggregat für den <strong>Message Center</strong>-Cube. Es wird standardmäßig jeden Tag um 3 Uhr morgens ausgelöst. Dieses Aggregat erfasst die folgenden Dimensionen: Kanal, Datum, Status und Ereignistyp.<br /> Der <strong>Message Center</strong>-Cube wird dann zur Erstellung von ereignisbasierten Berichten verwendet. Weitere Informationen zu Cubes finden Sie in <a href="../../reporting/using/about-cubes.md">diesem Abschnitt</a>.<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

