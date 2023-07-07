---
product: campaign
title: Campaign
description: Campaign
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows
topic-tags: technical-workflows
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 100%

---


# Campaign{#campaign}



Die folgenden Workflows werden standardmäßig mit dem Modul **Kampagne** installiert. Weiterführende Informationen zu dem Modul finden Sie in diesem [Abschnitt](../../campaign/using/designing-marketing-campaigns.md).

>[!CAUTION]
>
>Diese Workflows MÜSSEN gestartet werden, damit die auf Kampagnenebene notwendigen Prozesse ausgeführt werden können.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Titel</strong><br /> </td> 
   <td> <strong>Interner Name</strong><br /> </td> 
   <td> <strong>Beschreibung</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Kostenberechnung</span> <br /> </td> 
   <td> <span class="uicontrol">budgetMgt</span> <br /> </td> 
   <td> Berechnet Ausgaben- und Kostenzeilen für Pläne, Programme, Kampagnen, Sendungen und Aufgaben.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Lager: Ergänzungen und Meldebestände</span> <br /> </td> 
   <td> <span class="uicontrol">stockMgt</span> <br /> </td> 
   <td> Startet die Berechnung der Lagerbestände in den Bestellzeilen und verwaltet Warnschwellen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Bearbeitungsvorgänge bezüglich Kampagnensendungen</span> <br /> </td> 
   <td> <span class="uicontrol">deliveryMgt</span> <br /> </td> 
   <td> Dieser Workflow löst die genehmigten Sendungen aus und startet die Nachbearbeitung des Dienstleisters für einen externen Versand. Außerdem werden Validierungsbenachrichtigungen und Erinnerungen gesendet.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Kampagnenvorgänge</span> <br /> </td> 
   <td> <span class="uicontrol">operationMgt</span> <br /> </td> 
   <td> Verwaltet Vorgänge in Marketing-Kampagnen (Zielgruppenbestimmung, Dateiextraktion etc.). Erstellt darüber hinaus Workflows für wiederkehrende und periodische Kampagnen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Bearbeitungsvorgänge bezüglich der Dienstleister</span> <br /> </td> 
   <td> <span class="uicontrol">supplierMgt</span> <br /> </td> 
   <td> Startet nach erfolgter Versandvalidierung Dienstleistervorgänge (E-Mail an den Router und Anschlussvorgang). <br /> </td> 
  </tr> 
 </tbody> 
</table>

