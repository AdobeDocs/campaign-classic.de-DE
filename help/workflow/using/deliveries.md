---
product: campaign
title: Sendungen
description: Erfahren Sie mehr über die standardmäßigen Workflows für Sendungen.
hide: true
feature: Workflows
source-git-commit: 720a5f4edf534788f7fd143a476c25e58a6f1586
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 67%

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
   <td> Dieser Workflow übermittelt per E-Mail den Aktivitätsbericht des Systems an den fakturierungsverantwortlichen Benutzer ('billing'). Wird standardmäßig an jedem 25. des Monats gestartet.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Alias-Verwaltung</span> <br /> </td> 
   <td> <span class="uicontrol">aliasCleansing</span> <br /> </td> 
   <td> Vereinheitlicht Aufzählungswerte. Wird standardmäßig täglich um 3 Uhr gestartet.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Zustellbarkeit</span> <br /> </td> 
   <td> <span class="uicontrol">deliverabilityUpdate</span> <br /> </td> 
   <td> Mit diesem Workflow können Sie die Liste der Regeln für die Bounce-Message-Qualifizierung sowie die Liste der Domains und MXs in der Plattform erstellen. Dieser Workflow funktioniert nur, wenn der HTTPS-Port geöffnet ist. Wenn das Zustellbarkeitsmodul (Email Deliverability) nicht installiert ist, werden die Listen nicht aktualisiert.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Datenbankbereinigung</span> <br /> </td> 
   <td> <span class="uicontrol">cleanup</span> <br /> </td> 
   <td> <p>Dieser Workflow ist der Datenbankwartungs-Workflow: Er führt verschiedene Berechnungen mit Statistiken und Prozessen durch und löscht gemäß der definierten Konfiguration im Bereitstellungsassistenten veraltete Daten aus der Datenbank. Er wird standardmäßig jeden Tag um 4 Uhr morgens ausgelöst.</p> <p>Weiterführende Informationen dazu finden Sie auf dieser <a href="../../production/using/database-cleanup-workflow.md">Seite</a>.</p> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Bereinigung ausgesetzter Workflows</span> <br /> </td> 
   <td> <span class="uicontrol">cleanupPausedWorkflows</span> <br /> </td> 
   <td> <p>Dieser Workflow analysiert pausierte Workflows, deren Schweregrad auf „Normal“ eingestellt ist, sowie Trigger- und Benachrichtigungswarnungen, wenn diese zu lange pausiert wurden. Nach einem Monat werden pausierte technische Workflows bedingungslos angehalten. Standardmäßig wird sie jeden Montag um 5 Uhr morgens ausgelöst.</p> <p>Weitere Informationen finden Sie unter <a href="monitoring-workflow-execution.md#handling-of-paused-workflows" target="_blank">Ausgesetzte Workflows handhaben</a>.</p></td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Angebotsbenachrichtigungen</span> <br /> </td> 
   <td> <span class="uicontrol">offerMgt</span> <br /> </td> 
   <td> Dieser Workflow stellt validierte Angebote sowie im Angebotskatalog enthaltene Kategorien in die Live-Umgebung bereit.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Planungen</span> <br /> </td> 
   <td> <span class="uicontrol">forecasting</span> <br /> </td> 
   <td> Analysiert die im Planungskalender verzeichneten Sendungen (Erstellung von Planungslogs). Wird standardmäßig täglich um 1 Uhr gestartet.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Tracking</span> <br /> </td> 
   <td> <span class="uicontrol">tracking</span> <br /> </td> 
   <td> Dieser Workflow ermöglicht die Wiederherstellung und Konsolidierung von Tracking-Informationen. Darüber hinaus wird die Neuberechnung von Tracking- und Versandstatistiken sichergestellt, insbesondere derjenigen, die von Archivierungs-Workflows für Message Center verwendet werden. Standardmäßig wird er einmal pro Stunde ausgelöst. <br /> </td> 
  </tr> 
 </tbody> 
</table>

