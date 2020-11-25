---
solution: Campaign Classic
product: campaign
title: Verbindung schlägt fehl
description: Verbindung schlägt fehl
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: cb6a2247e3b7617511aecf3d2d19985af0216494
workflow-type: tm+mt
source-wordcount: '340'
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
   <td>Stellen Sie mithilfe eines Webbrowsers eine Verbindung mit der Adobe Campaign-Server-Zugriffs-URL her: **`http(s):// <urlserver>`**. Wenn er nicht reagiert, wird der Webserver auf dem Computer angehalten. Wenden Sie sich an den Systemadministrator Ihrer Host-Firma, um den Dienst neu zu starten.</td>
  </tr>
  <tr> 
   <td>Wurde Adobe Campaign korrekt integriert?</td> 
   <td>Melden Sie sich bei: **`http(s)://<urlserver>/r/test`** URL. Der Server sollte die folgende Art von Meldung zurückgeben

    &quot;
    &lt;redir status=&#39;OK&#39; date=&#39;YYYY/MM/DD HH:MM:SS&#39; build=&#39;XXXX&#39; host=&#39;&lt;hostname>&#39; localHost=&#39;&lt;server>&#39;/>
    &quot;
    
    Wenn Sie dieses Ergebnis nicht erhalten, überprüfen Sie Ihre Webserverkonfiguration, dass diese Integration berücksichtigt wird.&lt;/td>
</tr>
  <tr> 
   <td>Wurde das Adobe Campaign-Webmodul gestartet?</td> 
   <td>
   Stellen Sie eine Verbindung mit der folgenden URL her: **`http(s)://<URLSERVER>/nl/jsp/logon.jsp`** * Wenn Sie einen Tomcat-Java-Fehler erhalten:

    Wird die JAVA-Integration korrekt ausgeführt? Adobe Campaign erfordert ein SUN-JDK.
    
    Es ist in die Datei **`[Anwendungspfad]`/nl6/customer.sh**
    
    * Wenn Sie eine leere Seite erhalten:
    
    Hat das Adobe Campaign-Webmodul gestartet? Sie sollten Folgendes abrufen:
    
    &quot;
    nlserver
    pdumpHH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R-Build XXX@SHA1) of DD/MM/YYYY
    [...]
    web@default (27515) - 55.2 Mb
    [...]
    &quot;
    
    * Wenn nicht, starten Sie es mit folgendem Befehl neu:
    
    &quot;
    
    nlserver Beginn web&quot;&lt;/td>
</tr>
  <tr>
  	<td>Überprüfen Sie die allgemeine Konfiguration der Sicherheitszonen.</td>
  	<td>Weitere Informationen zum Konfigurieren von Sicherheitszonen finden Sie in [diesem Abschnitt](../../installation/using/configuring-campaign-server.md#define-security-zones).</td>
  </tr>
 </tbody> 
</table>
