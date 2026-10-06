---
product: campaign
title: Message Center (Kontrolle)
description: Message Center (Kontrolle)
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
source-wordcount: '152'
ht-degree: 100%
---

# Message Center (Kontrolle){#message-center-control}



Der folgende Workflow ist so geplant, dass er stündlich ausgeführt wird. Er wird standardmäßig mit dem Modul **Message Center – Kontrolle** installiert.


Weitere Informationen hierzu finden Sie je nach Campaign-Version in den folgenden Abschnitten:

![](assets/do-not-localize/v7.jpeg)[Dokumentation zu Campaign v7](../../message-center/using/about-transactional-messaging.md)

![](assets/do-not-localize/v8.png)[Dokumentation zu Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/transactional.html?lang=de)


<table> 
 <tbody> 
  <tr> 
   <td> <strong>Titel</strong><br /> </td> 
   <td> <strong>Interner Name</strong><br /> </td> 
   <td> <strong>Beschreibung</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Message Center &lt;external_account_name&gt;<br /> </td> 
   <td> mcSynch_&lt;external_account_name&gt;<br /> </td> 
   <td> Dieser Workflow:<br /> 
    <ul> 
     <li> <p>Ruft die Liste der durch die Aktion(en) verarbeiteten Ereignisse ab.</p> </li> 
     <li> <p>Wird mit der NmsBroadLogMsg-Tabelle synchronisiert, um die Qualifizierung der Versandnachrichten abzurufen.</p> </li> 
     <li> <p>Ruft Ereignis-Versandlogs ab, sobald die Synchronisation mit der NmsBroadLogMsg-Tabelle abgeschlossen ist.</p> </li> 
     <li> <p>Wird mit der NmsTrackingUrl-Tabelle synchronisiert, um das Tracking für die Versand-URLs abzurufen.</p> </li> 
     <li> <p>Ruft Ereignis-Verfolgungs-URLs ab, sobald die Synchronisation mit der NmsTrackingUrl-Tabelle abgeschlossen ist.</p> </li> 
     <li> <p>Ruft alle drei Stunden die E-Mail-Adressen ab, die infolge eines Versands neu in Quarantäne gekommen sind.</p> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

