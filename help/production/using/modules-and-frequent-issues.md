---
product: campaign
title: Module und häufige Probleme
description: Module und häufige Probleme
feature: Monitoring, Troubleshooting
badge-v7-prem: label="Nur On-Premise/Hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Gilt nur für Hybrid- und On-Premise-Bereitstellungen"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: dbd50178-0a16-46ed-bfad-47beb3c2a420
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 10%

---

# Module und häufige Probleme{#modules-and-frequent-issues}



Im Folgenden finden Sie eine Liste der Module, die von häufigen Problemen betroffen sind:

<table> 
 <thead> 
  <tr> 
   <th> Modul </th> 
   <th> Ausführungsumfang </th> 
   <th> Fehlerbehebung </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Export </td> 
   <td> Ausführung eines Exportvorgangs<br /> </td> 
   <td> Der Benutzer, der diesen Export geplant hat, muss ihn neu starten. Entweder Delta oder vollständiger Neustart.<br /> </td> 
  </tr> 
  <tr> 
   <td> importieren </td> 
   <td> Ausführung eines Importvorgangs<br /> </td> 
   <td> Der Benutzer, der diesen Export geplant hat, muss ihn neu starten. Überprüfen Sie die Datenbank auf Duplikate.<br /> </td> 
  </tr> 
  <tr> 
   <td> inMail </td> 
   <td> Bounce-Message-Box wird gelesen<br /> </td> 
   <td> Überprüfen Sie dieses Modul, wenn Bounce Messages nicht mehr weitergeleitet werden.<br /> </td> 
  </tr> 
  <tr> 
   <td> mta </td> 
   <td> Versand von E-Mails<br /> </td> 
   <td> Überprüfen Sie dieses Modul, wenn keine E-Mails mehr gesendet werden.<br /> </td> 
  </tr> 
  <tr> 
   <td> Bundesland </td> 
   <td> Verwaltet MTA-Verbindungsstatistiken<br /> </td> 
   <td> Überprüfen Sie dieses Modul, wenn keine E-Mails mehr gesendet werden.<br /> </td> 
  </tr> 
  <tr> 
   <td> syslogd </td> 
   <td> Log-Schreiben<br /> </td> 
   <td> Wenn einige Protokolle in den Protokolldateien fehlen, stellen Sie sicher, dass das Modul Port 6666 verwendet. Siehe <a href="../../production/using/general-architecture.md#list-of-open-ports" target="_blank">Liste der offenen Ports</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> tracking </td> 
   <td> Konsolidierung und Abrufen von Trackinglogs<br /> </td> 
   <td> Überprüfen Sie dieses Modul, wenn keine Trackinglogs mehr weitergeleitet werden.<br /> </td> 
  </tr> 
  <tr> 
   <td> trackingLog </td> 
   <td> Trackinglog schreibt und bereinigt Server<br /> </td> 
   <td> Überprüfen Sie dieses Modul, wenn keine Trackinglogs mehr weitergeleitet werden und sich keine Logspuren in den Dateien auf dem Server befinden. Siehe <a href="../../production/using/tracking-logs-issues.md" target="_blank">Probleme mit Trackinglogs</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> Wachhund </td> 
   <td> Instanz starten und überwachen<br /> </td> 
   <td> Dieses Modul überprüfen, wenn keine Prozesse gestartet werden.<br /> </td> 
  </tr> 
  <tr> 
   <td> Web </td> 
   <td> Anwendungsserver (HTTP und SOAP)<br /> </td> 
   <td> Überprüfen Sie dieses Modul, wenn die Konsole und die Web-Verbindungen nicht funktionieren und ein Trigger vom Typ <strong>xtk:session</strong> auftritt<br /> </td> 
  </tr> 
  <tr> 
   <td> wfserver </td> 
   <td> Steuert die Ausführung der Workflow-Instanz.<br /> </td> 
   <td> Wenn Probleme auftreten, starten Sie dieses Modul neu. Falls erforderlich, wenden Sie das Verfahren an, um die Genauigkeit der Protokolle zu erhöhen, die im Abschnitt <a href="../../production/using/log-precision.md" target="_blank">Protokollgenauigkeit</a> beschrieben sind<br /> </td> 
  </tr> 
 </tbody> 
</table>
