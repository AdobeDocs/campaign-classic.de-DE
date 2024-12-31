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



Die Gründe für ein Verbindungsproblem können vielfältig sein und hängen von verschiedenen Kontexten ab.

Sie können die folgenden Tests versuchen. Wenn der Verbindungsfehler weiterhin besteht, wenden Sie sich an die [Adobe-Kundenunterstützung](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).



<table> 
<thead> 
<tr> 
<th>Prüfungen<br /> </th> 
<th>Lösung<br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td>Haben Sie von Ihrem Computer aus Internetzugang?</td> 
<td>Vergewissern Sie sich, dass Sie eine Verbindung zu Websites im Internet herstellen können (z. B. ). Wenn Sie keine Verbindung herstellen können, liegt das Problem auf Ihrem Computer. Wenden Sie sich an Ihren Systemadministrator.</td>
</tr>
<tr> 
<td>Kann über einen anderen Service eine Verbindung mit dem Server hergestellt werden, auf dem Adobe Campaign gehostet wird?</td> 
<td>Verbinden Sie sich über SSH oder eine andere Methode mit dem Server. Wenn dies nicht möglich ist, hat Ihr Gastunternehmen ein Problem. Wenden Sie sich an den Systemadministrator.</td>
</tr>
<tr> 
<td>Antwortet der Webserver?</td> 
<td>Stellen Sie mithilfe eines Webbrowsers eine Verbindung zur Adobe Campaign-Serverzugriffs-URL her<b> (http(s):// &lt;urlserver&gt;</b>. Wenn er nicht reagiert, wird der Webserver auf dem Computer angehalten. Wenden Sie sich an den Systemadministrator Ihrer Hostfirma, um den Dienst neu zu starten.</td>
</tr>
<tr> 
<td>Wurde Adobe Campaign korrekt integriert?</td> 
<td>Melden Sie sich bei der URL <b>http(s)://&lt;urlserver&gt;/r/test</b> an. Der Server sollte den folgenden Nachrichtentyp zurückgeben: &lt;redir status='OK' date='YYYY/MM/DD HH:MM:SS' build='XXXX' host='&lt;hostname&gt;' localHost='&lt;server&gt;'/&gt;
Wenn Sie dieses Ergebnis nicht erhalten, überprüfen Sie in Ihrer Webserver-Konfiguration, ob die Integration berücksichtigt wird.</td>
</tr>
<tr> 
<td>Stellen Sie eine Verbindung mit der folgenden URL her<b> (http(s)://&lt;URLSERVER&gt;/nl/jsp/logon.jsp</b></td>
<td>Wenn Sie einen Tomcat-Java-Fehler erhalten, überprüfen Sie, ob die JAVA-Integration korrekt durchgeführt wurde. Es ist in die Datei [Pfad des Programms]/nl6/customer.sh integriert</td>
</tr>
<tr> 
<td>Stellen Sie eine Verbindung mit der folgenden URL her<b> (http(s)://&lt;URLSERVER&gt;/nl/jsp/logon.jsp</b></td>
<td>Wenn Sie eine leere Seite erhalten, überprüfen Sie, ob das Adobe Campaign Web-Modul gestartet wurde. Der Befehl nlserver pdump sollte den Anwendungsserver für Adobe Campaign Classic (7.X YY.R build XXX@SHA1) von TT/MM/JJJJ zurückgeben. Wenn nicht, starten Sie das Modul mit dem Befehl nlserver start web</td>
</tr>
<tr>
<td>Überprüfen Sie die allgemeine Konfiguration der Sicherheitszonen.</td>
<td>Weiterführende Informationen zur Konfiguration von Sicherheitszonen finden Sie <a href="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/additional-configurations/configuring-campaign-server.html#configuring-campaign-server"/> diesem Abschnitt.</a></td>
</tr>
<tr>
<td>Der Befehl nlserver pdump gibt <b>Keine Aufgaben</b> zurück</td>
<td>Sie müssen die gesamte Adobe Campaign-Anwendung neu starten. Verwenden Sie dazu den folgenden Befehl: <b>nlserver watchdog -svc -noconsole</b></td>
</tr>
</tbody> 
</table>
