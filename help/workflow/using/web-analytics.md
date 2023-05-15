---
product: campaign
title: Web Analytics
description: Erfahren Sie mehr über das Web Analytics-Package.
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows, Analytics Integration
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '182'
ht-degree: 100%

---


# Web Analytics{#web-analytics}



Die folgenden Workflows werden standardmäßig mit dem Modul **Web-Analytics-Connectoren** installiert. Weiterführende Informationen zu dem Modul finden Sie in diesem [Abschnitt](../../platform/using/adobe-analytics-connector.md).

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
   <td> Dieser Workflow ermöglicht es, über den Adobe® Analytics-Connector Indikatoren zu E-Mail-Kampagnen von Adobe Campaign an Adobe Experience Cloud Suite zu senden. Dies betrifft die folgenden Indikatoren: <strong>Gesendet</strong> (iSent), <strong>Öffnungen insgesamt</strong> (iTotalRecipientOpen), <strong>Gesamtzahl der Empfänger, die geklickt haben</strong> (iTotalRecipientClick), <strong>Fehler</strong> (iError), <strong>Abmeldung</strong> (Opt-out) (iOptOut).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Identifizierung der konvertierten Kontakte</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsFindConverted</span> <br /> </td> 
   <td> Ruft die Besucher ab, die nach einer Remarketing-Kampagne einen Kauf getätigt haben. Die von diesem Workflow ermittelten Daten werden im Bericht <span class="uicontrol">Remarketing-Effizienz</span> zur Verfügung gestellt (siehe diese <a href="../../platform/using/adobe-analytics-connector.md#creating-a-re-marketing-campaign">Seite</a>). <br /> </td> 
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

