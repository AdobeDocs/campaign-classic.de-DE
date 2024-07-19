---
product: campaign
title: Verbindung schlägt fehl
description: Verbindung schlägt fehl
feature: Monitoring
badge-v7-prem: label="Nur On-Premise/Hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Gilt nur für Hybrid- und On-Premise-Bereitstellungen"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 3c793dc1-9654-4289-a3d2-30c3078fd848
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 5%

---

# Verbindung schlägt fehl{#failure-to-connect}



Die Gründe für ein Verbindungsproblem können mehrere sein und hängen von verschiedenen Kontexten ab.

Sie können die folgenden Tests durchführen. Wenn der Verbindungsfehler weiterhin auftritt, wenden Sie sich an die [Adobe-Kundenunterstützung](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).



<table> 
<thead> 
<tr> 
<th>Prüfungen<br /> </th> 
<th>Auflösung<br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td>Haben Sie von Ihrem Computer aus Internetzugang?</td> 
<td>Überprüfen Sie, ob Sie eine Verbindung zu Websites im Internet herstellen können (z. B.). Wenn Sie keine Verbindung herstellen können, liegt das Problem auf Ihrem Computer. Wenden Sie sich an Ihren Systemadministrator.</td>
</tr>
<tr> 
<td>Können Sie über einen anderen Dienst eine Verbindung zum Server herstellen, auf dem Adobe Campaign gehostet wird?</td> 
<td>Stellen Sie eine Verbindung zum Server über SSH oder andere Mittel her. Ist dies nicht möglich, hat Ihr Gastunternehmen ein Problem. Wenden Sie sich an den Systemadministrator.</td>
</tr>
<tr> 
<td>Reagiert der Webserver?</td> 
<td>Stellen Sie mithilfe eines Webbrowsers eine Verbindung zur Adobe Campaign-Server-Zugriffs-URL her: <b>http(s):// &lt;urlserver&gt;</b>. Wenn er nicht reagiert, wird der Webserver auf dem Computer angehalten. Wenden Sie sich an den Systemadministrator Ihres Hostunternehmens, um den Dienst neu zu starten.</td>
</tr>
<tr> 
<td>Wurde Adobe Campaign ordnungsgemäß integriert?</td> 
<td>Melden Sie sich bei der URL <b>http(s)://&lt;urlserver&gt;/r/test</b> an. Der Server sollte den folgenden Nachrichtentyp zurückgeben: &lt;redir status='OK' date='YYY/MM/DD HH:MM:SS' build='XXXX' host='&lt;Hostname&gt;' localHost='&lt;Server&gt;'/&gt;
Wenn Sie dieses Ergebnis nicht erhalten, überprüfen Sie in Ihrer Webserverkonfiguration, ob die Integration berücksichtigt wird.</td>
</tr>
<tr> 
<td>Stellen Sie eine Verbindung zur folgenden URL her: <b>http(s)://&lt;URLSERVER&gt;/nl/jsp/logon.jsp</b></td>
<td>Wenn Sie einen Tomcat-Java-Fehler erhalten, überprüfen Sie, ob die JAVA-Integration ordnungsgemäß durchgeführt wurde. Es ist in die Datei [Anwendungspfad]/nl6/customer.sh integriert.</td>
</tr>
<tr> 
<td>Stellen Sie eine Verbindung zur folgenden URL her: <b>http(s)://&lt;URLSERVER&gt;/nl/jsp/logon.jsp</b></td>
<td>Wenn Sie eine leere Seite erhalten, überprüfen Sie, ob das Adobe Campaign-Webmodul gestartet wurde. Der Befehl nlserver pdump sollte den Anwendungsserver für Adobe Campaign Classic (7.X YY.R Build XXX@SHA1) von TT/MM/JJJJ zurückgeben. Wenn nicht, starten Sie das Modul mit dem Befehl nlserver start web neu.</td>
</tr>
<tr>
<td>Überprüfen Sie die allgemeine Konfiguration der Sicherheitszonen.</td>
<td>Weitere Informationen zum Konfigurieren von Sicherheitszonen finden Sie in <a href="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/additional-configurations/configuring-campaign-server.html#configuring-campaign-server"/>diesem Abschnitt.</a></td>
</tr>
<tr>
<td>Der Befehl nlserver pdump gibt <b>Keine Aufgaben</b> zurück.</td>
<td>Sie müssen die gesamte Adobe Campaign-Anwendung neu starten. Verwenden Sie dazu den folgenden Befehl: <b>nlserver watchdog -svc -noconsole</b></td>
</tr>
</tbody> 
</table>
