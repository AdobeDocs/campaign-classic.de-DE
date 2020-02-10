---
title: Netzwerkkonfiguration
seo-title: Netzwerkkonfiguration
description: Netzwerkkonfiguration
seo-description: null
page-status-flag: never-activated
uuid: 17357170-7440-4603-bea6-2e4b9086ae72
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
discoiquuid: 639d2f42-e397-4694-942c-b2b8ad94ce9c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 46f5bfb41bfe9c938ac0ffa767ead3e47a32047d

---


# Netzwerkkonfiguration{#network-configuration}

## Kommunikation zwischen Prozessen {#communication-between-processes}

Bestimmte Prozesse der Anwendung müssen mit anderen kommunizieren oder auf LAN und Internet zugreifen. Dies bedeutet, dass einige TCP-Ports für diese Prozesse geöffnet sein müssen.

Verwenden Sie den eingebetteten Apache Tomcat-Anschluss als Priorität (standardmäßig 8080) für die interne Kommunikation zwischen den verschiedenen Anwendungsservern einer Adobe Campaign-Plattform.

### Auslieferungsserver {#delivery-server}

Für den Bereitstellungsserver (**nlserver-Metadaten**) müssen die folgenden Anschlüsse geöffnet sein:

<table> 
 <tbody> 
  <tr> 
   <td> Ports<br /> </td> 
   <td> Ziel<br /> </td> 
   <td> Erklärung<br /> </td> 
  </tr> 
  <tr> 
   <td> 25/tcp (smtp)<br /> </td> 
   <td> Anywhere<br /> </td> 
   <td> SMTP-Traffic für E-Mail-Übertragungen.<br /> </td> 
  </tr> 
  <tr> 
   <td> 53/udp (Domäne)<br /> </td> 
   <td> DNS-Server<br /> </td> 
   <td> DNS-Abfragen.<br /> </td> 
  </tr> 
  <tr> 
   <td> 38000/tcp (Standardanschluss)<br /> </td> 
   <td> SMS-Gateway<br /> </td> 
   <td> Dient zum Senden von SMS-Traffic an den NetSize-SMS-Router [Option].<br /> </td> 
  </tr> 
  <tr> 
   <td> 7777/udp<br /> </td> 
   <td> Statistischer Server<br /> </td> 
   <td> Zugriff auf den Statistikserver.<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Inbound Mail {#inbound-mail}

Für den Inbound Mail Recovery-Prozess (**nlserver inMail**) müssen die folgenden Anschlüsse geöffnet sein:

<table> 
 <tbody> 
  <tr> 
   <td> Ports<br /> </td> 
   <td> Ziel<br /> </td> 
   <td> Erklärung<br /> </td> 
  </tr> 
  <tr> 
   <td> 110/tcp (pop3)<br /> </td> 
   <td> Interner Mail-Server<br /> </td> 
   <td> POP3-Traffic zur Erfassung von Absprungmeldungen.<br /> </td> 
  </tr> 
  <tr> 
   <td> 25/tcp (smtp)<br /> </td> 
   <td> Interner Mail-Server<br /> </td> 
   <td> SMTP-Traffic zum Senden verbleibender Absprungmeldungen, die nicht automatisch von den vordefinierten Regeln verarbeitet werden.<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Application server {#application-server}

Für den Anwendungsserver (**nlserver web**) müssen die folgenden Anschlüsse geöffnet sein:

<table> 
 <tbody> 
  <tr> 
   <td> Ports<br /> </td> 
   <td> Ziel<br /> </td> 
   <td> Erklärung<br /> </td> 
  </tr> 
  <tr> 
   <td> 80/tcp (http)<br /> 443/tcp (https)<br /> </td> 
   <td> Anywhere<br /> </td> 
   <td> HTTP- oder HTTPS-Traffic (einschließlich des Bereitstellungsangebots).<br /> </td> 
  </tr> 
 </tbody> 
</table>

Wenn mehrere Anwendungsserver einer Adobe Campaign-Plattform miteinander kommunizieren müssen, empfehlen wir die Verwendung des Apache Tomcat-Servers (standardmäßig: 8080) und nicht der HTTP-Anschluss des Webservers, mit dem die Integration von Umleitungsmodulen durchgeführt wurde. Dies bedeutet, dass der Anschluss zwischen diesen Servern geöffnet sein muss.

### Status der SMS-Zustellung {#sms-delivery-status}

Zur Verfolgung von SMS-Auslieferungen (**nlserver sms**) muss der folgende Anschluss geöffnet sein:

<table> 
 <tbody> 
  <tr> 
   <td> Ports<br /> </td> 
   <td> Ziel<br /> </td> 
   <td> Erklärung<br /> </td> 
  </tr> 
  <tr> 
   <td> 38000/tcp (Standardanschluss)<br /> </td> 
   <td> SMS-Gateway<br /> </td> 
   <td> Sucht den Status der Bereitstellungswarteschlange, der vom NetSize SMS Gateway verwaltet wird [Option].<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Rich-Client {#rich-client}

Für den Rich-Client von Adobe Campaign (**nlclient**) müssen die folgenden Anschlüsse geöffnet sein:

<table> 
 <tbody> 
  <tr> 
   <td> Ports<br /> </td> 
   <td> Ziel<br /> </td> 
   <td> Erklärung<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 80/tcp (http)</p><p>443/tcp (https)</p><br /> </td> 
   <td> Application server<br /> </td> 
   <td> SOAP-Traffic (HTTP).<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Datenbankzugriff {#database-access}

Alle Komponenten, die die Datenbank verwenden, müssen eine Verbindung zu ihr herstellen können. Dies ist bei den meisten Komponenten der Fall, mit Ausnahme des Umleitungsservers, der allein funktionieren kann, und des Thin Win32-Clients, der HTTP (oder HTTPS) nur zur Kommunikation mit dem Anwendungsserver verwendet.

Die Standardanschlüsse lauten wie folgt:

<table> 
 <tbody> 
  <tr> 
   <td> Datenbanktyp<br /> </td> 
   <td> Anschluss (Standard)<br /> </td> 
   <td> Ziel<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Oracle</strong><br /> </td> 
   <td> 1521/tcp<br /> </td> 
   <td> Datenbankserver<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>PostgreSQL</strong><br /> </td> 
   <td> 5432/tcp<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Microsoft SQL Server</strong><br /> </td> 
   <td> 1433/tcp<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>DB2</strong><br /> </td> 
   <td> 50000/tcp<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Externer Zugriff {#external-access}

Darüber hinaus müssen bestimmte Komponenten über das öffentliche Internet zugänglich sein, damit E-Mail-Kampagnen, die direkt von Adobe Campaign ausgeführt werden, angezeigt werden können. Dies bedeutet, dass einige Anschlüsse für Komponenten offen sein müssen.

### Weiterleitungsserver {#redirection-server}

<table> 
 <tbody> 
  <tr> 
   <td> Überwachungsanschluss<br /> </td> 
   <td> Location<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 80/tcp (http)</p><p> 443/tcp (https)</p><br /> </td> 
   <td> Überall. Jeder Klick auf einen verfolgten Link generiert eine HTTP-Anforderung auf dem Server.<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Externer Webserver {#external-web-server}

Dieser Server hostet Webformulare, Spiegelseiten usw. Die folgenden Anschlüsse müssen geöffnet sein:

<table> 
 <tbody> 
  <tr> 
   <td> Überwachungsanschluss<br /> </td> 
   <td> Location<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 80/tcp (http)</p><p> 443/tcp (https)</p><br /> </td> 
   <td> Überall. Erforderlich, wenn Webformulare direkt von der Adobe Campaign-Plattform verwaltet werden oder wenn Spiegelseiten verwendet werden.<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Interner Anwendungsserver (Web) {#internal-application-server--web-}

<table> 
 <tbody> 
  <tr> 
   <td> Überwachungsanschluss<br /> </td> 
   <td> Location<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 80/tcp (http)</p><p> 443/tcp (https)</p><br /> </td> 
   <td> Alle Computer, die den Thin Client oder Rich Client ausführen.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Integration mit Adobe Experience Manager {#integration-with-adobe-experience-manager}

Zur Integration zwischen Adobe Campaign und Adobe Experience Manager müssen mehrere Anschlüsse geöffnet werden, wenn die Installation &quot;lokal&quot;erfolgt. For more information on configuring this integration, refer to the [detailed documentation](../../integrations/using/about-adobe-experience-manager.md).

<table> 
 <tbody> 
  <tr> 
   <td> Überwachungsanschluss<br /> </td> 
   <td> Beschreibung<br /> </td> 
  </tr> 
  <tr> 
   <td> 80<br /> </td> 
   <td> AEM-Verbindung mit Adobe Campaign<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 4502</p><p> 4503</p><br /> </td> 
   <td> Verbindung von Adobe Campaign mit den Instanzen "Authoring"und "Veröffentlichung"von AEM. Die zu öffnenden Anschlüsse unterscheiden sich je nach AEM-Konfiguration möglicherweise von den Standardanschlüssen.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Bandbreite {#bandwidth}

Ein weiterer wichtiger Parameter der Netzwerkkonfiguration, der berücksichtigt werden muss. Es ist fast immer ausgehende und viel in der Nachfrage während E-Mail-Sendungen. Nachfolgend sind einige Beispiele für Konfigurationen aufgeführt, die auf unserer Erfahrung basieren:

* 1 MB/s für 10.000 E-Mails pro Stunde (durchschnittliche Größe 30 KB)
* 8 bis 10 Mb/s für 100.000 E-Mails pro Stunde (durchschnittliche Größe 30 Kb)

Wenn Sie Beschränkungen hinsichtlich der Bandbreite haben, ist es möglich, Kampagnen so zu planen, dass sie in der Nacht ausgeführt werden, wenn die Nachfrage niedriger ist.
