---
product: campaign
title: Netzwerkkonfiguration
description: Richtlinien zur Systemkommunikation
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: b86236ae-95e9-4406-b60f-6d90ad0d4a01
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '666'
ht-degree: 6%

---

# Netzwerkkonfiguration{#network-configuration}

![](../../assets/v7-only.svg)

## Kommunikation zwischen Prozessen {#communication-between-processes}

Bestimmte Prozesse der Anwendung müssen mit anderen kommunizieren oder auf LAN und Internet zugreifen. Dies bedeutet, dass einige TCP-Ports für diese Prozesse offen sein müssen.

Verwenden Sie den eingebetteten Apache Tomcat-Port als Priorität (standardmäßig 8080) für die interne Kommunikation zwischen den verschiedenen Anwendungsservern einer Adobe Campaign-Plattform.

### Versandserver {#delivery-server}

Für den Versandserver (**nlserver mta**) müssen die folgenden Ports geöffnet sein:

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
   <td> SMTP-Traffic für E-Mail-Sendungen.<br /> </td> 
  </tr> 
  <tr> 
   <td> 53/udp (domain)<br /> </td> 
   <td> DNS-Server<br /> </td> 
   <td> DNS-Abfragen.<br /> </td> 
  </tr> 
  <tr> 
   <td> 38000/tcp (Standardport)<br /> </td> 
   <td> SMS Gateway<br /> </td> 
   <td> Wird zum Senden von SMS-Traffic an den NetSize-SMS-Router verwendet [Option].<br /> </td> 
  </tr> 
  <tr> 
   <td> 7777/udp<br /> </td> 
   <td> Statistischer Server<br /> </td> 
   <td> Zugriff auf den Statistikserver.<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Eingehende E-Mails {#inbound-mail}

Für den Wiederherstellungsprozess von eingehenden E-Mails (**nlserver inMail**) müssen die folgenden Ports geöffnet sein:

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
   <td> POP3-Traffic zum Abruf von Bounce Messages.<br /> </td> 
  </tr> 
  <tr> 
   <td> 25/tcp (smtp)<br /> </td> 
   <td> Interner Mail-Server<br /> </td> 
   <td> SMTP-Traffic zum Senden verbleibender Bounce-Nachrichten, die nicht automatisch von den vordefinierten Regeln verarbeitet werden.<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Anwendungs-Server {#application-server}

Für den Anwendungsserver (**nlserver web**) müssen die folgenden Ports geöffnet sein:

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
   <td> HTTP- oder HTTPS-Traffic (auch für das Zustellbarkeits-Angebot).<br /> </td> 
  </tr> 
 </tbody> 
</table>

Wenn mehrere Anwendungsserver einer Adobe Campaign-Plattform miteinander kommunizieren müssen, empfehlen wir die Verwendung des Anschlusses des Apache Tomcat-Servers (standardmäßig: 8080) anstelle des HTTP-Ports des Webservers, mit dem die Umleitungsmodulintegration durchgeführt wurde. Dies bedeutet, dass der Port zwischen diesen Servern geöffnet sein muss.

### SMS-Versandstatus {#sms-delivery-status}

Um SMS-Sendungen (**nlserver sms**) zu verfolgen, muss der folgende Port geöffnet sein:

<table> 
 <tbody> 
  <tr> 
   <td> Ports<br /> </td> 
   <td> Ziel<br /> </td> 
   <td> Erklärung<br /> </td> 
  </tr> 
  <tr> 
   <td> 38000/tcp (Standardport)<br /> </td> 
   <td> SMS Gateway<br /> </td> 
   <td> Fragt den Status der Versandwarteschlange ab, der vom NetSize-SMS-Gateway verwaltet wird [Option].<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Rich-Client {#rich-client}

Für den Rich-Client von Adobe Campaign (**nlclient**) müssen die folgenden Ports geöffnet sein:

<table> 
 <tbody> 
  <tr> 
   <td> Ports<br /> </td> 
   <td> Ziel<br /> </td> 
   <td> Erklärung<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 80/tcp (http)</p><p>443/tcp (https)</p><br /> </td> 
   <td> Anwendungs-Server<br /> </td> 
   <td> SOAP-Traffic (HTTP).<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Datenbankzugriff {#database-access}

Alle Komponenten, die die Datenbank verwenden, müssen eine Verbindung mit ihr herstellen können. Dies gilt für die meisten Komponenten, mit Ausnahme des Umleitungsservers, der allein funktionieren kann, und des Thin Win32-Clients, der nur HTTP (oder HTTPS) verwendet, um mit dem Anwendungsserver zu kommunizieren.

Die Standardanschlüsse lauten wie folgt:

<table> 
 <tbody> 
  <tr> 
   <td> Datenbanktyp<br /> </td> 
   <td> Port (Standard)<br /> </td> 
   <td> Ziel<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Oracle</strong><br /> </td> 
   <td> 1521/tcp<br /> </td> 
   <td> Datenbank-Server<br /> </td> 
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

Darüber hinaus müssen bestimmte Komponenten über das öffentliche Internet zugänglich sein, damit E-Mail-Kampagnen, die direkt über Adobe Campaign ausgeführt werden, angezeigt werden können. Dies bedeutet, dass einige Ports für Komponenten geöffnet sein müssen.

### Weiterleitungsserver {#redirection-server}

<table> 
 <tbody> 
  <tr> 
   <td> Listening-Port<br /> </td> 
   <td> Location<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 80/tcp (http)</p><p> 443/tcp (https)</p><br /> </td> 
   <td> Überall. Jeder Klick auf einen verfolgten Link generiert eine HTTP-Anforderung auf dem Server.<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Externer Webserver {#external-web-server}

Dieser Server hostet Webformulare, Mirrorseiten usw. Die folgenden Ports müssen geöffnet sein:

<table> 
 <tbody> 
  <tr> 
   <td> Listening-Port<br /> </td> 
   <td> Location<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 80/tcp (http)</p><p> 443/tcp (https)</p><br /> </td> 
   <td> Überall. Erforderlich, wenn Webformulare direkt von der Adobe Campaign-Plattform aus verwaltet werden oder wenn Mirrorseiten verwendet werden.<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Interner Anwendungsserver (Web) {#internal-application-server--web-}

<table> 
 <tbody> 
  <tr> 
   <td> Listening-Port<br /> </td> 
   <td> Location<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 80/tcp (http)</p><p> 443/tcp (https)</p><br /> </td> 
   <td> Alle Computer, die den Thin Client oder Rich Client ausführen.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Integration mit Adobe Experience Manager {#integration-with-adobe-experience-manager}

Die Integration zwischen Adobe Campaign und Adobe Experience Manager erfordert das Öffnen mehrerer Ports, wenn die Installation &quot;On-Premise&quot;ist. Weitere Informationen zur Konfiguration dieser Integration finden Sie in der [ausführlichen Dokumentation](../../integrations/using/about-adobe-experience-manager.md).

<table> 
 <tbody> 
  <tr> 
   <td> Listening-Port<br /> </td> 
   <td> Beschreibung<br /> </td> 
  </tr> 
  <tr> 
   <td> 80<br /> </td> 
   <td> AEM Verbindung zu Adobe Campaign<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 4502</p><p> 4503</p><br /> </td> 
   <td> Adobe Campaign-Verbindung zu AEM "Authoring"- und "Publishing"-Instanzen. Die zu öffnenden Ports unterscheiden sich je nach AEM möglicherweise von den Standardanschlüssen.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Bandbreite {#bandwidth}

Ein weiterer Schlüsselparameter der zu berücksichtigenden Netzwerkkonfiguration. Es ist fast immer ausgehend und sehr gefragt bei E-Mail-Sendungen. Im Folgenden finden Sie einige Beispiele für Konfigurationen, die auf unserem Erlebnis basieren:

* 1 MB/s für 10.000 E-Mails pro Stunde (durchschnittliche Größe 30 KB)
* 8 bis 10 MB/s für 100.000 E-Mails pro Stunde (durchschnittliche Größe 30 KB)

Wenn Sie Bandbreiteneinschränkungen haben, ist es möglich, Kampagnen so zu planen, dass sie nachts ausgeführt werden, wenn die Nachfrage geringer ist.
