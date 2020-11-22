---
solution: Campaign Classic
product: campaign
title: Sendungen
description: Weitere Informationen zu Standard-Versänden Workflows
audience: workflow
content-type: reference
topic-tags: technical-workflows
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 98%

---


# Sendungen{#deliveries}

Die folgenden Workflows werden standardmäßig installiert.

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
   <td> <span class="uicontrol">Zählung aktiver Profile (Billing)</span><br /> </td> 
   <td> <span class="uicontrol">billingActiveContactCount</span> <br /> </td> 
   <td> <p>Mit diesem Workflow wird die Anzahl der aktiven Profile gezählt. Er wird standardmäßig jede Nacht um 1 Uhr ausgelöst.</p> <p><strong>Profile</strong> bezeichnet einen Datensatz, der einen Endkunden, einen Prospect oder Lead repräsentiert. Bei diesen Daten kann es sich z. B. um einen Datensatz in der nmsRecipient-Tabelle oder einer externen Tabelle handeln, die die Kennung eines Cookies, eines Kunden oder eines Mobiltelefons oder andere für einen bestimmten Kanal relevante Informationen enthält. Für die Fakturierung werden nur aktive Profile berücksichtigt. Ein Profil wird als aktiv erachtet, wenn es in den vergangenen zwölf Monaten über einen beliebigen Kanal angesprochen wurde oder mit ihm kommuniziert wurde.</p> <p>Die Kanäle Facebook und Twitter werden nicht berücksichtigt.</p> <p>Eine Übersicht über die <span class="uicontrol">Anzahl der aktiven Profile</span> erhalten Sie über das Menü <span class="uicontrol">Administration</span> &gt; <span class="uicontrol">Kampagnenverwaltung</span> &gt; <span class="uicontrol">Kundenmetriken</span>.</p> </td> 
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
   <td> <p>Bereinigt obsolete Daten gemäß der Konfiguration im Softwareverteilungs-Assistenten. Berechnet diverse Statistiken und Vorgänge. Wird standardmäßig täglich um 4 Uhr gestartet.</p> <p>Weiterführende Informationen dazu finden Sie auf dieser <a href="../../production/using/database-cleanup-workflow.md">Seite</a>.</p> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Bereinigung ausgesetzter Workflows</span> <br /> </td> 
   <td> <span class="uicontrol">cleanupPausedWorkflows</span> <br /> </td> 
   <td> <p>In diesem Workflow werden ausgesetzte Workflows analysiert, für die eine normale Prioritätsstufe festgelegt wurde und die Warnhinweise und Benachrichtigungen auslösen, wenn sie zu lange angehalten werden. Nach einem Monat werden ausgesetzte technische Workflows gestoppt. Standardmäßig werden sie jeden Montag um 5 Uhr ausgelöst.</p> <p>Weitere Informationen finden Sie unter <a href="../../workflow/using/monitoring-workflow-execution.md#handling-of-paused-workflows" target="_blank">Ausgesetzte Workflows handhaben</a>.</p></td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Angebotsbenachrichtigungen</span> <br /> </td> 
   <td> <span class="uicontrol">offerMgt</span> <br /> </td> 
   <td> Gibt stündlich validierte Angebote sowie im Angebotskatalog erstellte Kategorien in die Live-Umgebung frei.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Vorschau</span> <br /> </td> 
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

