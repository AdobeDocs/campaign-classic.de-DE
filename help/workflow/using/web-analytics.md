---
solution: Campaign Classic
product: campaign
title: Web Analytics
description: Weitere Informationen zum Web Analytics-Paket
audience: workflow
content-type: reference
topic-tags: technical-workflows
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '182'
ht-degree: 96%

---


# Web Analytics{#web-analytics}

Die folgenden Workflows werden mit dem **Web-Analytics-Connectoren-Modul** installiert. Weiterführende Informationen zum Modul finden Sie in diesem [Abschnitt](../../platform/using/adobe-analytics-data-connector.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Titel</strong><br /> </td> 
   <td> <strong>Interner Name</strong><br /> </td> 
   <td> <strong>Beschreibung</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Übermittlung der Kampagnen-Indikatoren und -Attribute</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsSendMetrics</span> <br /> </td> 
   <td> Steuert mithilfe des Adobe® Genesis Connectors die Übermittlung der E-Mail-Kampagnen-Indikatoren von Adobe Campaign an Adobe Experience Cloud. Folgende Indikatoren werden berücksichtigt: <strong>Gesendet</strong> (iSent), <strong>Öffnungen insgesamt</strong> (iTotalRecipientOpen), <strong>Gesamtzahl der Empfänger, die geklickt haben</strong> (iTotalRecipientClick), <strong>Fehler</strong> (iError), <strong>Abmeldungen</strong> (opt-out) (iOptOut).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Identifizierung der konvertierten Kontakte</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsFindConverted</span> <br /> </td> 
   <td> Ruft die Besucher ab, die nach einer Remarketing-Kampagne einen Kauf getätigt haben. Die von diesem Workflow ermittelten Daten werden im Bericht <span class="uicontrol">Remarketing-Effizienz</span> zur Verfügung gestellt (siehe diese <a href="../../platform/using/adobe-analytics-data-connector.md#creating-a-re-marketing-campaign">Seite</a>). <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Ereignislöschung</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsPurgeWebEvents</span> <br /> </td> 
   <td> Löscht alle Ereignisse aus der Datenbank, deren <span class="uicontrol">Lebensdauer</span> abgelaufen ist. <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Abruf der Web-Ereignisse</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsGetWebEvents</span> <br /> </td> 
   <td> Ruft stündlich die Segmente ab, die sich auf das Besucherverhalten der angegebenen Webseite beziehen, fügt die Daten zur Adobe-Campaign-Datenbank hinzu und startet den Remarketing-Workflow. <br /> </td> 
  </tr> 
 </tbody> 
</table>

