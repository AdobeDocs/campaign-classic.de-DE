---
product: campaign
title: Technischer Workflow für Inbox Rendering
description: In diesem Abschnitt wird der technische Workflow beschrieben, der mit dem Inbox Rendering-Package installiert wird.
feature: Workflows, Inbox Rendering
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: ht
source-wordcount: '75'
ht-degree: 100%

---


# Inbox Rendering (IR){#inbox-rendering}

![](../../assets/v7-only.svg)

Der unten beschriebene Workflow wird mit dem **Inbox Rendering (IR)**-Modul standardmäßig installiert. Weiterführende Informationen zu Inbox Rendering finden Sie in diesem [Abschnitt](../../delivery/using/inbox-rendering.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Titel</strong><br /> </td> 
   <td> <strong>Interner Name</strong><br /> </td> 
   <td> <strong>Beschreibung</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Testnetzwerk-Update für das Inbox Rendering</strong><br /> </td> 
   <td> <span class="uicontrol">updateRenderingSeeds</span> <br /> </td> 
   <td> Dieser Workflow aktualisiert E-Mail-Adressen, die für die Darstellung des Posteingangs verwendet werden, und funktioniert nur, wenn der HTTPS-Port für <strong>https://deliverability-app.neolane.net/deliverability</strong> geöffnet ist.<br /> </td> 
  </tr> 
 </tbody> 
</table>

