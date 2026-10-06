---
product: campaign
title: Sendung an Mid-Sourcing-Server
description: Erfahren Sie mehr über die Workflows "Sendung an Mid-Sourcing-Server".
hide: true
feature: Workflows
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
subfeature_v2:
  - id: fcb46c0f-76e1-48bc-9dd0-fcf9d97526cf
    internal-label: Workflows
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '115'
ht-degree: 100%
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
   <td> <p>Dieser Workflow erfasst Zählinformationen für Sendungen auf dem Mid-Sourcing-Server. Zu diesen Informationen gehören allgemeine Versandindikatoren wie etwa die Anzahl der Sendungen.</p> <p>Trackinginformationen wie Öffnungen sind nicht enthalten.</p> <p>Dieser Workflow wird standardmäßig alle zehn Minuten gestartet.</p> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Mid-Sourcing (Versandlogs)</span> <br /> </td> 
   <td> <span class="uicontrol">defaultMidSourcingLog</span> <br /> </td> 
   <td> Ruft Versandlogs vom Mid-Sourcing-Server ab. Wird standardmäßig stündlich gestartet.<br /> </td> 
  </tr> 
 </tbody> 
</table>

