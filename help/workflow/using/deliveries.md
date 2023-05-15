---
product: campaign
title: Sendungen
description: Erfahren Sie mehr über die standardmäßigen Workflows für Sendungen.
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 100%

---


# Sendungen{#deliveries}



Die folgenden Workflows werden standardmäßig mit dem Modul **Sendungen** installiert.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Titel</strong><br /> </td> 
   <td> <strong>Interner Name</strong><br /> </td> 
   <td> <strong>Beschreibung</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Bericht-Aggregate</span> <br /> </td> 
   <td> <span class="uicontrol">reportingAggregates</span> <br /> </td> 
   <td> Aktualisiert die in Berichten verwendeten Aggregate. Wird standardmäßig täglich um 2 Uhr gestartet.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Fakturierung</span> <br /> </td> 
   <td> <span class="uicontrol">billing</span> <br /> </td> 
   <td> Übermittelt per E-Mail den Aktivitätsbericht des Systems an den fakturierungsverantwortlichen Benutzer ('billing'). Wird standardmäßig an jedem 25. des Monats gestartet.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Alias-Verwaltung</span> <br /> </td> 
   <td> <span class="uicontrol">aliasCleansing</span> <br /> </td> 
   <td> Vereinheitlicht Aufzählungswerte. Wird standardmäßig täglich um 3 Uhr gestartet.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Zustellbarkeit</span> <br /> </td> 
   <td> <span class="uicontrol">deliverabilityUpdate</span> <br /> </td> 
   <td> Erstellt die Liste der Qualifizierungsregeln für Bounce-Messages sowie die Liste der Domains und MX der Plattform. Der Workflow wird nur bei geöffnetem HTTPS-Port ausgeführt. Wenn das Zustellbarkeitsmodul (Email Deliverability) nicht installiert ist, werden die Listen nicht aktualisiert.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Datenbankbereinigung</span> <br /> </td> 
   <td> <span class="uicontrol">cleanup</span> <br /> </td> 
   <td> <p>Dieser Workflow ist der Datenbankwartungs-Workflow: Er führt verschiedene Berechnungen mit Statistiken und Prozessen durch und löscht gemäß der definierten Konfiguration im Bereitstellungsassistenten veraltete Daten aus der Datenbank. Er wird standardmäßig jeden Tag um 4 Uhr morgens ausgelöst.</p> <p>Weiterführende Informationen dazu finden Sie auf dieser <a href="../../production/using/database-cleanup-workflow.md">Seite</a>.</p> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Bereinigung ausgesetzter Workflows</span> <br /> </td> 
   <td> <span class="uicontrol">cleanupPausedWorkflows</span> <br /> </td> 
   <td> <p>In diesem Workflow werden ausgesetzte Workflows analysiert, für die eine normale Prioritätsstufe festgelegt wurde und die Warnhinweise und Benachrichtigungen auslösen, wenn sie zu lange angehalten werden. Nach einem Monat werden ausgesetzte technische Workflows gestoppt. Standardmäßig werden sie jeden Montag um 5 Uhr ausgelöst.</p> <p>Weitere Informationen finden Sie unter <a href="monitoring-workflow-execution.md#handling-of-paused-workflows" target="_blank">Ausgesetzte Workflows handhaben</a>.</p></td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Angebotsbenachrichtigungen</span> <br /> </td> 
   <td> <span class="uicontrol">offerMgt</span> <br /> </td> 
   <td> Stellt stündlich validierte Angebote sowie im Angebotskatalog erstellte Kategorien in die Live-Umgebung bereit.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Planungen</span> <br /> </td> 
   <td> <span class="uicontrol">forecasting</span> <br /> </td> 
   <td> Analysiert die im Planungskalender verzeichneten Sendungen (Erstellung von Planungslogs). Wird standardmäßig täglich um 1 Uhr gestartet.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Tracking</span> <br /> </td> 
   <td> <span class="uicontrol">tracking</span> <br /> </td> 
   <td> Ruft Trackinginformationen ab und konsolidiert sie. Aktualisiert außerdem die Berechnung der Tracking- und Versandstatistiken, insbesondere die von den Message-Center-Archivierungs-Workflows verwendeten. Wird standardmäßig stündlich gestartet. <br /> </td> 
  </tr> 
 </tbody> 
</table>

