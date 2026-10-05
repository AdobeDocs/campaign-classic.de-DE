---
product: campaign
title: Kampagne
description: Campaign
feature: Workflows
hide: true
topic-tags: technical-workflows
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
source-wordcount: '166'
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
   <td> Dieser Workflow berechnet Ausgaben- und Kostenzeilen für Pläne, Programme, Kampagnen, Sendungen und Aufgaben.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Lager: Ergänzungen und Meldebestände</span> <br /> </td> 
   <td> <span class="uicontrol">stockMgt</span> <br /> </td> 
   <td> Dieser Workflow startet die Berechnung der Lagerbestände in den Bestellzeilen und verwaltet Warnschwellen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Bearbeitungsvorgänge bezüglich Kampagnensendungen</span> <br /> </td> 
   <td> <span class="uicontrol">deliveryMgt</span> <br /> </td> 
   <td> Dieser Workflow startet den Versand der validierten Sendungen und die Anschlussvorgänge des Dienstleisters bei externem Versand. Außerdem werden Validierungsbenachrichtigungen und Erinnerungen gesendet.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Kampagnenvorgänge</span> <br /> </td> 
   <td> <span class="uicontrol">operationMgt</span> <br /> </td> 
   <td> Verwaltet Vorgänge in Marketing-Kampagnen (Zielgruppenbestimmung, Dateiextraktion etc.). Erstellt darüber hinaus Workflows für wiederkehrende und periodische Kampagnen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Bearbeitungsvorgänge bezüglich der Dienstleister</span> <br /> </td> 
   <td> <span class="uicontrol">supplierMgt</span> <br /> </td> 
   <td> Dieser Workflow startet nach erfolgter Versandvalidierung Dienstleistervorgänge (E-Mail an den Router und Anschlussverarbeitung). <br /> </td> 
  </tr> 
 </tbody> 
</table>

