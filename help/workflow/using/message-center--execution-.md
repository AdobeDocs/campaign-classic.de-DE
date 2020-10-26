---
title: Message Center (Ausführung)
seo-title: Message Center (Ausführung)
description: Message Center (Ausführung)
seo-description: null
page-status-flag: never-activated
uuid: 8dfb09d1-da00-43fb-9df4-243bb915cbde
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: technical-workflows
discoiquuid: dc3d8998-9493-4d71-b3e2-6f9531cb9bac
translation-type: ht
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: ht
source-wordcount: '234'
ht-degree: 100%

---


# Message Center (Ausführung){#message-center-execution}

Die folgenden Workflows werden mit dem Modul **Message Center – Ausführung** installiert. Weiterführende Informationen zum Modul finden Sie in diesem [Abschnitt](../../message-center/using/about-transactional-messaging.md).

Weiterführende Informationen zur Konfiguration technischer Workflows für das Message-Center-Modul finden Sie auf [dieser Seite](../../message-center/using/technical-workflows.md).

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
   <td> Weist Ereignissen einen Status zu. Folgende Status sind möglich:<br /> 
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

