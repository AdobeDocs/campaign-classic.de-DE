---
product: campaign
title: Message Center (Ausführung)
description: Message Center (Ausführung)
hide: true
hidefromtoc: true
feature: Workflows
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: ht
source-wordcount: '0'
ht-degree: 100%

---


# Message Center (Ausführung){#message-center-execution}



Die folgenden Workflows werden standardmäßig mit dem Add-on **Message Center – Ausführung** installiert.

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
   <td> <span class="uicontrol">Update des Ereignisstatus</span> <br /> </td> 
   <td> <span class="uicontrol">updateEventsStatus</span> <br /> </td> 
   <td> Mit diesem Workflow können Sie Ereignissen einen Status zuweisen. Folgende Ereignisstatus stehen zur Verfügung:<br /> 
    <ul> 
     <li> <p><strong>Ausstehend</strong>: Das Ereignis befindet sich in der Warteschlange. Ihm wurde noch keine Nachrichtenvorlage zugeordnet.</p> </li> 
     <li> <p><strong>Versand ausstehend</strong>: Das Ereignis befindet sich in der Warteschlange. Ihm wurde eine Nachrichtenvorlage zugeordnet und die Versandverarbeitung ist in Gang.</p> </li> 
     <li> <p><strong>Gesendet</strong>: Dieser Status wird aus den Versandlogs übernommen. Er bedeutet, dass die Nachricht gesendet wurde.</p> </li> 
     <li> <p><strong>Vom Versand ignoriert</strong>: Dieser Status wird aus den Versandlogs übernommen. Er bedeutet, dass der Versand ignoriert wurde.</p> </li> 
     <li> <p><strong>Versandfehler</strong>: Dieser Status wird aus den Versandlogs übernommen. Er bedeutet, dass der Versand fehlgeschlagen ist.</p> </li> 
     <li> <p><strong>Ereignis wurde nicht berücksichtigt</strong>: Dem Ereignis konnte keine Nachrichtenvorlage zugeordnet werden. Es erfolgt kein weiterer Verarbeitungsversuch.</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Verarbeitung der Batch-Ereignisse</span> <br /> </td> 
   <td> <span class="uicontrol">batchEventsProcessing</span> <br /> </td> 
   <td> Teilt die Batch-Ereignisse in eine Warteschlange ein, bevor ihnen eine Nachrichtenvorlage zugeordnet wird. <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Verarbeitung der Echtzeit-Ereignisse</span> <br /> </td> 
   <td> <span class="uicontrol">rtEventsProcessing</span> <br /> </td> 
   <td> Teilt die Echtzeit-Ereignisse in eine Warteschlange ein, bevor ihnen eine Nachrichtenvorlage zugeordnet wird. <br /> </td> 
  </tr> 
 </tbody> 
</table>

