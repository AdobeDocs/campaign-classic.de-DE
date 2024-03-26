---
product: campaign
title: Sendung an Mid-Sourcing-Server
description: Erfahren Sie mehr über die Workflows "Sendung an Mid-Sourcing-Server".
badge-v7-only: label="v7" type="Informative" tooltip="Gilt nur für Campaign Classic v7"
feature: Workflows
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '114'
ht-degree: 85%

---


# Weiterleitung an Mid-Sourcing{#transfer-to-mid-sourcing}



Die folgenden Workflows werden standardmäßig mit dem Modul **Sendung an Mid-Sourcing-Server** installiert. Weitere Informationen finden Sie im [Installationshandbuch zu Campaign Classic v7](../../installation/using/mid-sourcing-deployment.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Titel</strong><br /> </td> 
   <td> <strong>Interner Name</strong><br /> </td> 
   <td> <strong>Beschreibung</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Mid-Sourcing (Versandzähler)</span> <br /> </td> 
   <td> <span class="uicontrol">defaultMidSourcingDlv</span> <br /> </td> 
   <td> <p>Dieser Workflow ruft Informationen bezüglich der Zählung von Sendungen vom Mid-Sourcing-Server ab. Zu diesen Informationen gehören allgemeine Versandindikatoren wie etwa die Anzahl der Sendungen.</p> <p>Trackinginformationen wie Öffnungen sind nicht enthalten.</p> <p>Dieser Workflow wird standardmäßig alle zehn Minuten gestartet.</p> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Mid-Sourcing (Versandlogs)</span> <br /> </td> 
   <td> <span class="uicontrol">defaultMidSourcingLog</span> <br /> </td> 
   <td> Ruft Versandlogs auf dem Mid-Sourcing-Server ab. Er wird standardmäßig jede Stunde ausgelöst.<br /> </td> 
  </tr> 
 </tbody> 
</table>

