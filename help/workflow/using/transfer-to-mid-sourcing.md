---
solution: Campaign Classic
product: campaign
title: Sendung an Mid-Sourcing-Server
description: Weitere Informationen zur Übertragung auf Mid-Sourcing Workflows
audience: workflow
content-type: reference
topic-tags: technical-workflows
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 93%

---


# Sendung an Mid-Sourcing-Server{#transfer-to-mid-sourcing}

Die folgenden Workflows werden mit dem Modul **Sendung an Mid-Sourcing-Server** installiert. Weiterführende Informationen zum Modul finden Sie in diesem [Abschnitt](../../installation/using/mid-sourcing-deployment.md).

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

