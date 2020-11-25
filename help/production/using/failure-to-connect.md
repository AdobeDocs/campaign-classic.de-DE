---
solution: Campaign Classic
product: campaign
title: Verbindung schlägt fehl
description: Verbindung schlägt fehl
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 68fee697b65b2ba69f456803e0a7cebca9be3760
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 2%

---


# Verbindung schlägt fehl{#failure-to-connect}

Die Gründe für ein Verbindungsproblem können mehrere sein und von verschiedenen Kontexten abhängen.

Sie können die folgenden Tests durchführen. Sollte der Verbindungsfehler weiterhin auftreten, wenden Sie sich bitte an den **Adobe Campaign-Support**.



<table> 
 <thead> 
  <tr> 
   <th>Kontrollen<br /> </th> 
   <th>Lösung<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td>Haben Sie Internetzugang von Ihrem Computer?</td> 
   <td>Vergewissern Sie sich, dass Sie eine Verbindung zu Websites im Internet herstellen können (z. B.). Wenn Sie keine Verbindung herstellen können, liegt das Problem auf Ihrem Computer. Wenden Sie sich an Ihren Systemadministrator.</td>
  </tr>
  <tr> 
   <td>Können Sie über einen anderen Dienst eine Verbindung zum Server-Hosting-Adobe Campaign herstellen?</td> 
   <td>Stellen Sie eine Verbindung mit dem Server über SSH oder auf andere Weise her. Wenn dies nicht möglich ist, liegt ein Problem mit Ihrer Host-Firma vor. Wenden Sie sich an den Systemadministrator.</td>
  </tr>
  <tr> 
   <td>Reagiert der Webserver?</td> 
   <td>Stellen Sie mithilfe eines Webbrowsers eine Verbindung mit der Adobe Campaign-Server-Zugriffs-URL her: <b>http(s):// &lt;urlserver&gt;</b>. Wenn er nicht reagiert, wird der Webserver auf dem Computer angehalten. Wenden Sie sich an den Systemadministrator Ihrer Host-Firma, um den Dienst neu zu starten.</td>
  </tr>
  <tr> 
   <td>Wurde Adobe Campaign korrekt integriert?</td> 
   <td>Melden Sie sich bei: <b>http(s):///r/test</b> URL. Der Server sollte die folgende Art von Meldung zurückgeben: &lt;redir status='OK' date='YYYY/MM/DD HH:MM:SS' build='XXXX' host='&lt;hostname&gt;' localHost='&lt;server&gt;'/&gt; Wenn Sie dieses Ergebnis nicht erhalten, überprüfen Sie Ihre Webserverkonfiguration, dass die Integration berücksichtigt wird.</td>
  </tr>
  <tr> 
   <td>Stellen Sie eine Verbindung mit der folgenden URL her: <b>http(s)://&lt;URLSERVER&gt;/nl/jsp/logon.jsp</b></td>
   <td>Wenn Sie einen Tomcat-Java-Fehler erhalten, überprüfen Sie, ob die JAVA-Integration korrekt ausgeführt wurde. Es ist in die Datei [Pfad der Anwendung]/nl6/customer.sh integriert.</td>
  </tr>
  <tr> 
   <td>Stellen Sie eine Verbindung mit der folgenden URL her: <b>http(s)://&lt;URLSERVER&gt;/nl/jsp/logon.jsp</b></td>
   <td>Wenn Sie eine leere Seite erhalten, überprüfen Sie, ob das Adobe Campaign-Webmodul gestartet wurde. Der Befehl nlserver pdump sollte den Anwendungsserver für Adobe Campaign Classic (7.X YY.R Build XXX@SHA1) von TT/MM/JJJJ zurückgeben. Ist dies nicht der Fall, starten Sie das Modul mit dem Befehl nlserver Beginn web neu.</td>
  </tr>
   <tr>
  	<td>Überprüfen Sie die allgemeine Konfiguration der Sicherheitszonen.</td>
  	<td>Weitere Informationen zum Konfigurieren von Sicherheitszonen finden Sie in [diesem Abschnitt](../../installation/using/configuring-campaign-server.md#define-security-zones).</td>
  </tr>
 </tbody> 
</table>
