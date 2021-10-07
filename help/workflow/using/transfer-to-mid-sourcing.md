---
product: campaign
title: Sendung an Mid-Sourcing-Server
description: Erfahren Sie mehr über die Workflows "Sendung an Mid-Sourcing-Server".
audience: workflow
content-type: reference
topic-tags: technical-workflows
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '107'
ht-degree: 100%

---


# Weiterleitung an Mid-Sourcing{#transfer-to-mid-sourcing}

![](../../assets/common.svg)

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
   <td> <p>Dieser Workflow ruft Informationen bezüglich der Zählung von Sendungen vom Mid-Sourcing-Server ab. Zu diesen Informationen gehören allgemeine Indikatoren zum Versand wie etwa die Anzahl der Sendungen.</p> <p>Trackinginformationen wie Öffnungen sind nicht enthalten.</p> <p>Dieser Workflow wird standardmäßig alle zehn Minuten gestartet.</p> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Mid-Sourcing (Versandlogs)</span> <br /> </td> 
   <td> <span class="uicontrol">defaultMidSourcingLog</span> <br /> </td> 
   <td> Ruft Versandlogs vom Mid-Sourcing-Server ab. Wird standardmäßig stündlich gestartet.<br /> </td> 
  </tr> 
 </tbody> 
</table>

