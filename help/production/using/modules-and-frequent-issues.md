---
product: campaign
title: Module und häufige Probleme
description: Module und häufige Probleme
feature: Monitoring, Troubleshooting
badge-v7-only: label="v7" type="Informative" tooltip="Gilt nur für Campaign Classic v7"
badge-v7-prem: label="On-Premise und Hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Gilt nur für Hybrid- und On-Premise-Bereitstellungen"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: dbd50178-0a16-46ed-bfad-47beb3c2a420
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 13%

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
   <td> export </td> 
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
   <td> Bounce Message Box lesen<br /> </td> 
   <td> Überprüfen Sie dieses Modul, wenn Bounce Messages nicht mehr weitergeleitet werden.<br /> </td> 
  </tr> 
  <tr> 
   <td> mta </td> 
   <td> E-Mails senden<br /> </td> 
   <td> Prüfen Sie dieses Modul, wenn keine E-Mails mehr gesendet werden.<br /> </td> 
  </tr> 
  <tr> 
   <td> stat </td> 
   <td> Führt Statistiken über MTA-Verbindungen<br /> </td> 
   <td> Prüfen Sie dieses Modul, wenn keine E-Mails mehr gesendet werden.<br /> </td> 
  </tr> 
  <tr> 
   <td> syslogd </td> 
   <td> Schreiben von Protokollen<br /> </td> 
   <td> Wenn einige Protokolle in den Protokolldateien fehlen, überprüfen Sie, ob das Modul Port 666 verwendet. Siehe Abschnitt <a href="../../production/using/general-architecture.md#list-of-open-ports" target="_blank">Liste offener Ports</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> tracking </td> 
   <td> Trackinglogs konsolidieren und abrufen<br /> </td> 
   <td> Überprüfen Sie dieses Modul, ob Trackinglogs nicht mehr weitergeleitet werden.<br /> </td> 
  </tr> 
  <tr> 
   <td> trackinglogd </td> 
   <td> Tracking von Protokollschreibungs- und Bereinigungs-Server<br /> </td> 
   <td> Überprüfen Sie dieses Modul, ob Trackinglogs nicht mehr weitergeleitet werden und es keine Protokolle in den Dateien auf dem Server gibt. Siehe Abschnitt <a href="../../production/using/tracking-logs-issues.md" target="_blank">Probleme mit Trackinglogs</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> watchdog </td> 
   <td> Start- und Überwachungsinstanz<br /> </td> 
   <td> Überprüfen Sie dieses Modul, wenn keine Prozesse gestartet werden.<br /> </td> 
  </tr> 
  <tr> 
   <td> Web </td> 
   <td> Anwendungsserver (HTTP und SOAP)<br /> </td> 
   <td> Überprüfen Sie dieses Modul, ob die Konsolen- und Webverbindungen nicht funktionieren und Trigger und <strong>xtk:session</strong> Typfehler<br /> </td> 
  </tr> 
  <tr> 
   <td> wfserver </td> 
   <td> Steuert die Ausführung der Workflow-Instanz.<br /> </td> 
   <td> Wenn Probleme auftreten, starten Sie dieses Modul neu. Wenden Sie bei Bedarf das Verfahren an, um die Genauigkeit der Protokolle zu erhöhen, die im Abschnitt <a href="../../production/using/log-precision.md" target="_blank">Protokollgenauigkeit</a> Abschnitt.<br /> </td> 
  </tr> 
 </tbody> 
</table>
