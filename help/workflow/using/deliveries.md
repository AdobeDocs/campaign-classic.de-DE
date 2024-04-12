---
product: campaign
title: Sendungen
description: Erfahren Sie mehr über die standardmäßigen Workflows für Sendungen.
feature: Workflows
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 56%

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
   <td> Dieser Workflow aktualisiert die in Berichten verwendeten Aggregate. Er wird standardmäßig täglich um 2 Uhr ausgelöst.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Fakturierung</span> <br /> </td> 
   <td> <span class="uicontrol">billing</span> <br /> </td> 
   <td> Dieser Workflow übermittelt per E-Mail den Aktivitätsbericht des Systems an den fakturierungsverantwortlichen Benutzer ('billing'). Er wird standardmäßig am 25. jedes Monats ausgelöst.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Alias-Verwaltung</span> <br /> </td> 
   <td> <span class="uicontrol">aliasCleansing</span> <br /> </td> 
   <td> Dieser Workflow standardisiert Auflistungswerte. Er wird standardmäßig täglich um 3 Uhr ausgelöst.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Zustellbarkeit</span> <br /> </td> 
   <td> <span class="uicontrol">deliverabilityUpdate</span> <br /> </td> 
   <td> Erstellt die Liste der Qualifizierungsregeln für Bounce Messages sowie die Liste der Domains und MXs der Plattform. Dieser Workflow funktioniert nur, wenn der HTTPS-Port geöffnet ist. Diese Listen werden nur aktualisiert, wenn das Zustellbarkeits-Modul installiert ist.<br /> </td> 
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
   <td> Dieser Workflow analysiert die im Planungskalender gespeicherten Sendungen (Erstellung von Planungslogs). Er wird standardmäßig täglich um 1 Uhr ausgelöst.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Tracking</span> <br /> </td> 
   <td> <span class="uicontrol">tracking</span> <br /> </td> 
   <td> Dieser Workflow ruft Tracking-Informationen ab und konsolidiert sie. Außerdem wird die Neuberechnung der Tracking- und Versandstatistiken, insbesondere der von den Archivierungs-Workflows des Message-Centers verwendeten, sichergestellt. Standardmäßig wird sie einmal pro Stunde ausgelöst. <br /> </td> 
  </tr> 
 </tbody> 
</table>

