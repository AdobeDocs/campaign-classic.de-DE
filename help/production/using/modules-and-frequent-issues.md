---
solution: Campaign Classic
product: campaign
title: Module und häufige Probleme
description: Module und häufige Probleme
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 7%

---


# Module und häufige Probleme{#modules-and-frequent-issues}

Im Folgenden finden Sie eine Liste von Modulen, die von häufigen Problemen betroffen sind:

<table> 
 <thead> 
  <tr> 
   <th> Modul </th> 
   <th> Ausführungsbereich </th> 
   <th> Fehlerbehebung </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> export </td> 
   <td> Ausführung eines Exportvorgangs<br /> </td> 
   <td> Der Operator, der diesen Export geplant hat, muss ihn erneut starten. Entweder Delta oder vollständige Neustartphase.<br /> </td> 
  </tr> 
  <tr> 
   <td> importieren </td> 
   <td> Ausführung eines Importvorgangs<br /> </td> 
   <td> Der Operator, der diesen Export geplant hat, muss ihn erneut starten. Überprüfen Sie die Datenbank auf Duplikat.<br /> </td> 
  </tr> 
  <tr> 
   <td> inMail </td> 
   <td> Lesen des Absprungmailfelds<br /> </td> 
   <td> Aktivieren Sie dieses Modul, wenn keine AbsprungMails mehr weitergeleitet werden.<br /> </td> 
  </tr> 
  <tr> 
   <td> mta </td> 
   <td> Liefert E-Mails<br /> </td> 
   <td> Aktivieren Sie dieses Modul, wenn keine E-Mails mehr gesendet werden.<br /> </td> 
  </tr> 
  <tr> 
   <td> stat </td> 
   <td> Führt Statistiken über MTA-Verbindungen<br /> </td> 
   <td> Aktivieren Sie dieses Modul, wenn keine E-Mails mehr gesendet werden.<br /> </td> 
  </tr> 
  <tr> 
   <td> syslogd </td> 
   <td> Protokollschrift<br /> </td> 
   <td> Wenn einige Protokolle in den Protokolldateien fehlen, überprüfen Sie, ob das Modul Port 6666 verwendet. Siehe <a href="../../production/using/general-architecture.md#list-of-open-ports" target="_blank">Liste der geöffneten Anschlüsse</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> tracking </td> 
   <td> Konsolidieren und Abrufen von Trackinglogs<br /> </td> 
   <td> Aktivieren Sie dieses Modul, wenn keine Trackinglogs mehr weitergeleitet werden.<br /> </td> 
  </tr> 
  <tr> 
   <td> trackinglogd </td> 
   <td> Tracking-Protokoll Schreiben und Bereinigen des Servers<br /> </td> 
   <td> Überprüfen Sie dieses Modul, wenn Trackinglogs nicht mehr weitergeleitet werden und keine Protokollspuren in den Dateien auf dem Server vorhanden sind. Siehe <a href="../../production/using/tracking-logs-issues.md" target="_blank">Probleme mit Trackinglogs</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> watchdog </td> 
   <td> Start- und Überwachungsinstanz<br /> </td> 
   <td> Überprüfen Sie dieses Modul, wenn kein Process Beginn vorhanden ist.<br /> </td> 
  </tr> 
  <tr> 
   <td> web </td> 
   <td> Anwendungsserver (HTTP und SOAP)<br /> </td> 
   <td> Überprüfen Sie dieses Modul, wenn die Konsolen- und Webverbindungen nicht funktionieren und Trigger eines <strong>xtk:session</strong>-Typfehler<br /> </td> 
  </tr> 
  <tr> 
   <td> wfserver </td> 
   <td> Steuert die Ausführung der Workflow-Instanz.<br /> </td> 
   <td> Wenn Probleme auftreten, starten Sie dieses Modul neu. Wenden Sie ggf. das Verfahren an, um die Genauigkeit der Protokolle zu erhöhen, die im Abschnitt <a href="../../production/using/log-precision.md" target="_blank">Protokollgenauigkeit</a> aufgeführt sind.<br /> </td> 
  </tr> 
 </tbody> 
</table>

