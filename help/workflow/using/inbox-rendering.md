---
title: Technischer Arbeitsablauf für die Inbox-Wiedergabe in Adobe Campaign Classic
description: In diesem Abschnitt wird der technische Arbeitsablauf beschrieben, der mit dem Inbox-Renderingpaket in Adobe Campaign Classic installiert wurde.
page-status-flag: never-activated
uuid: f60a09f0-47a0-4fc0-b0ac-47178af6ad55
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: technical-workflows
discoiquuid: da0779dc-b734-483b-81e9-ff4706a2b6de
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: e1bd878c45576932e085b579f91eb72f5d36d6fd

---


# Inbox-Rendering (IR){#inbox-rendering}

Der unten beschriebene Workflow wird standardmäßig mit dem **Inbox-Rendering-Modul (IR)** installiert. For more on Inbox rendering, refer to this [section](../../delivery/using/inbox-rendering.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Titel</strong><br /> </td> 
   <td> <strong>Interner Name</strong><br /> </td> 
   <td> <strong>Beschreibung</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Aktualisieren des Seed-Netzwerks für das Inbox-Rendering</strong><br /> </td> 
   <td> <span class="uicontrol">updateRenderingSeeds</span><br /> </td> 
   <td> This workflow updates email addresses used for Inbox rendering and only works if the HTTPS port is open for <strong>deliverability.neolane.net</strong>.<br /> </td> 
  </tr> 
 </tbody> 
</table>

