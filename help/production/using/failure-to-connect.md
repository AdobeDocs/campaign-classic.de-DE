---
solution: Campaign Classic
product: campaign
title: Verbindung schlägt fehl
description: Verbindung schlägt fehl
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 6464a61148fd12738d95953161aea4ac4d19c04b
workflow-type: tm+mt
source-wordcount: '349'
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
   <td>Melden Sie sich bei: <b>http(s):///r/test</b> URL. Der Server sollte die folgende Art von Meldung zurückgeben:

    &lt;pre>
    &lt;redir status=&#39;OK&#39; date=&#39;YYYY/MM/DD HH:MM:SS&#39; build=&#39;XXXX&#39; host=&#39;&lt;hostname>&#39; localHost=&#39;&lt;server>&#39;/>
    &lt;/pre>
    
    Wenn Sie dieses Ergebnis nicht erhalten, überprüfen Sie Ihre Webserverkonfiguration, dass die Integration berücksichtigt wird.&lt;/td>
</tr>
  <tr> 
   <td>Wurde das Adobe Campaign-Webmodul gestartet?</td> 
   <td>Stellen Sie eine Verbindung mit der folgenden URL her: <b>http(s)://&gt;URLSERVER&lt;/nl/jsp/logon.jsp</b>* Wenn Sie einen Tomcat Java-Fehler erhalten:

    Wird die JAVA-Integration korrekt ausgeführt? Adobe Campaign erfordert ein SUN-JDK.
    
    Es ist in die Datei [Pfad der Anwendung]/nl6/customer.sh integriert.

* Wenn Sie eine leere Seite erhalten:

       Hat das Adobe Campaign-Webmodul gestartet? Sie sollten Folgendes erhalten:
       
       &lt;pre>
     nlserver pdump
     HH:MM:SS > Application server for Adobe Campaign Classic (7.x YY.R-Build XXX@SHA1) of DD/MM/YYYY
     [..]
 web@default (27515) - 55.2 Mb     
     
     [...]&lt;/pre>
   
* Andernfalls starten Sie es mit dem folgenden Befehl neu:

       &lt;pre>
     nlserver Beginn web
     &lt;/pre>
     &lt;/td>
   </tr>
  <tr>
  	<td>Überprüfen Sie die allgemeine Konfiguration der Sicherheitszonen.</td>
  	<td>Weitere Informationen zum Konfigurieren von Sicherheitszonen finden Sie in [diesem Abschnitt](../../installation/using/configuring-campaign-server.md#define-security-zones).</td>
  </tr>
 </tbody> 
</table>
