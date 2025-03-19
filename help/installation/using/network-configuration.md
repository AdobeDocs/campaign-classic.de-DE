---
product: campaign
title: Netzwerkkonfiguration
description: Kennenlernen der Systemkommunikationsrichtlinien
feature: Installation, Instance Settings
badge-v7-prem: label="Nur On-Premise/Hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Gilt nur für Hybrid- und On-Premise-Bereitstellungen"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: b86236ae-95e9-4406-b60f-6d90ad0d4a01
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '704'
ht-degree: 3%

---

# Netzwerkkonfiguration{#network-configuration}



## Kommunikation zwischen Prozessen {#communication-between-processes}

Bestimmte Prozesse der Anwendung müssen mit anderen kommunizieren oder auf das LAN und das Internet zugreifen. Dies bedeutet, dass einige TCP-Ports für diese Prozesse offen sein müssen.

Verwenden Sie den eingebetteten Apache Tomcat-Port als Priorität (standardmäßig 8080) für die interne Kommunikation zwischen den verschiedenen Anwendungsservern einer Adobe Campaign-Plattform.

### Versand-Server {#delivery-server}

Für den Versandserver (**nlserver mta**) müssen die folgenden Ports offen sein:

<table> 
 <tbody> 
  <tr> 
   <td> Ports<br /> </td> 
   <td> Ziel<br /> </td> 
   <td> Kommentare<br /> </td> 
  </tr> 
  <tr> 
   <td> 25/TCP (SMTP)<br /> </td> 
   <td> Überall<br /> </td> 
   <td> SMTP-Traffic für E-Mail-Broadcasting.<br /> </td> 
  </tr> 
  <tr> 
   <td> 53/UDP (Domain)<br /> </td> 
   <td> DNS-Server<br /> </td> 
   <td> DNS-Abfragen.<br /> </td> 
  </tr> 
  <tr> 
   <td> 38000/TCP (Standard-Port)<br /> </td> 
   <td> SMS-Gateway<br /> </td> 
   <td> Wird verwendet, um SMS-Traffic an den NetSize-SMS-Router zu senden [option].<br /> </td> 
  </tr> 
  <tr> 
   <td> 7777/UDP<br /> </td> 
   <td> Statistik-Server<br /> </td> 
   <td> Zugriff auf den Statistikserver.<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Posteingang {#inbound-mail}

Für den Wiederherstellungsprozess eingehender E-Mails (**nlserver inMail**) müssen die folgenden Ports geöffnet sein:

<table> 
 <tbody> 
  <tr> 
   <td> Ports<br /> </td> 
   <td> Ziel<br /> </td> 
   <td> Kommentare<br /> </td> 
  </tr> 
  <tr> 
   <td> 110/TCP (POP3)<br /> </td> 
   <td> Interner Mailserver<br /> </td> 
   <td> POP3-Traffic zum Erfassen von Bounce-Nachrichten.<br /> </td> 
  </tr> 
  <tr> 
   <td> 25/TCP (SMTP)<br /> </td> 
   <td> Interner Mailserver<br /> </td> 
   <td> SMTP-Traffic zum Senden verbleibender Bounce-Nachrichten, die nicht automatisch durch die vordefinierten Regeln verarbeitet werden.<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Anwendungs-Server {#application-server}

Für den Anwendungs-Server (**nlserver web**) müssen die folgenden Ports offen sein:

<table> 
 <tbody> 
  <tr> 
   <td> Ports<br /> </td> 
   <td> Ziel<br /> </td> 
   <td> Kommentare<br /> </td> 
  </tr> 
  <tr> 
   <td> 80/TCP (HTTP)<br /> 443/TCP (HTTPS)<br /> </td> 
   <td> Überall<br /> </td> 
   <td> HTTP- oder HTTPS-Traffic (einschließlich für das Zustellbarkeitsangebot).<br /> </td> 
  </tr> 
 </tbody> 
</table>

Wenn mehrere Anwendungs-Server einer Adobe Campaign-Plattform miteinander kommunizieren müssen, empfehlen wir, den Port des Apache Tomcat-Servers (standardmäßig: 8080) anstelle des HTTP-Ports des Webservers zu verwenden, mit dem die Umleitungsmodul-Integration durchgeführt wurde. Dies bedeutet, dass der Port zwischen diesen Servern offen sein muss.

### Status des SMS-Versands {#sms-delivery-status}

Um SMS-Sendungen (**nlserver sms**) zu verfolgen, muss der folgende Port offen sein:

<table> 
 <tbody> 
  <tr> 
   <td> Ports<br /> </td> 
   <td> Ziel<br /> </td> 
   <td> Kommentare<br /> </td> 
  </tr> 
  <tr> 
   <td> 38000/TCP (Standard-Port)<br /> </td> 
   <td> SMS-Gateway<br /> </td> 
   <td> Fragt den Status der vom NetSize SMS-Gateway verwalteten Versandwarteschlange ab [option].<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Rich-Client {#rich-client}

Für den Adobe Campaign Rich-Client **nlclient**) müssen die folgenden Ports offen sein:

<table> 
 <tbody> 
  <tr> 
   <td> Ports<br /> </td> 
   <td> Ziel<br /> </td> 
   <td> Kommentare<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 80/TCP (HTTP)</p><p>443/TCP (HTTPS)</p><br /> </td> 
   <td> Anwendungs-Server<br /> </td> 
   <td> SOAP-Traffic (HTTP).<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Datenbankzugriff {#database-access}

Alle Komponenten, die die Datenbank verwenden, müssen eine Verbindung zu ihr herstellen können. Dies ist bei den meisten Komponenten der Fall, mit Ausnahme des Weiterleitungsservers, der allein funktionieren kann, und des dünnen Win32-Clients, der HTTP (oder HTTPS) nur zur Kommunikation mit dem Anwendungsserver verwendet.

Die Standardanschlüsse sind:

<table> 
 <tbody> 
  <tr> 
   <td> Datenbanktyp<br /> </td> 
   <td> Port (Standard)<br /> </td> 
   <td> Ziel<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Oracle</strong><br /> </td> 
   <td> 1521/TCP<br /> </td> 
   <td> Datenbank-Server<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>PostgreSQL</strong><br /> </td> 
   <td> 5432/TCP<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Microsoft SQL Server</strong><br /> </td> 
   <td> 1433/TCP<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Externer Zugriff {#external-access}

Darüber hinaus müssen bestimmte Komponenten über das öffentliche Internet zugänglich sein, damit E-Mail-Kampagnen, die direkt von Adobe Campaign ausgeführt werden, angezeigt werden können. Das bedeutet, dass einige Ports für Komponenten offen sein müssen.

### Weiterleitungs-Server {#redirection-server}

<table> 
 <tbody> 
  <tr> 
   <td> Listen-Port<br /> </td> 
   <td> Standort<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 80/TCP (HTTP)</p><p> 443/TCP (HTTPS)</p><br /> </td> 
   <td> Überall. Jeder Klick auf einen getrackten Link generiert eine HTTP-Anfrage auf dem Server.<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Externer Webserver {#external-web-server}

Auf diesem Server werden Web-Formulare, Mirrorseiten usw. gehostet. Die folgenden Ports müssen geöffnet sein:

<table> 
 <tbody> 
  <tr> 
   <td> Listen-Port<br /> </td> 
   <td> Standort<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 80/TCP (HTTP)</p><p> 443/TCP (HTTPS)</p><br /> </td> 
   <td> Überall. Erforderlich, wenn Web-Formulare direkt über die Adobe Campaign-Plattform verwaltet werden oder wenn Mirrorseiten verwendet werden.<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Interner Anwendungs-Server (Web) {#internal-application-server--web-}

<table> 
 <tbody> 
  <tr> 
   <td> Listen-Port<br /> </td> 
   <td> Standort<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 80/TCP (HTTP)</p><p> 443/TCP (HTTPS)</p><br /> </td> 
   <td> Alle Computer, die den Thin-Client oder Rich-Client ausführen.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Integration mit Adobe Experience Manager {#integration-with-adobe-experience-manager}

Für die Integration zwischen Adobe Campaign und Adobe Experience Manager müssen mehrere Ports geöffnet werden, wenn die Installation „On-Premise“ erfolgt. Weitere Informationen zur Konfiguration dieser Integration finden Sie in der [ Dokumentation](../../integrations/using/about-adobe-experience-manager.md).

<table> 
 <tbody> 
  <tr> 
   <td> Listen-Port<br /> </td> 
   <td> Beschreibung<br /> </td> 
  </tr> 
  <tr> 
   <td> 80 <br /> </td> 
   <td> AEM-Verbindung zu Adobe Campaign<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 4502</p><p> 4503</p><br /> </td> 
   <td> Adobe Campaign-Verbindung zu den „Authoring“- und „Publishing“-Instanzen von AEM. Die zu öffnenden Ports unterscheiden sich möglicherweise von den Standard-Ports, je nach Ihrer AEM-Konfiguration.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Bandbreite {#bandwidth}

Ein weiterer Schlüsselparameter der Netzwerkkonfiguration, der zu berücksichtigen ist. Es ist fast immer ausgehend und wird bei E-Mail-Übertragungen stark nachgefragt. Im Folgenden finden Sie einige Beispiele für Konfigurationen, die auf unseren Erfahrungen basieren:

* 1 MB/s für 10.000 E-Mails pro Stunde (durchschnittliche Größe von 30 KB)
* 8 bis 10 MB/s für 100.000 E-Mails pro Stunde (durchschnittliche Größe von 30 KB)

Wenn Sie Einschränkungen in Bezug auf die Bandbreite haben, ist es möglich, Kampagnen so zu planen, dass sie während der Nacht ausgeführt werden, wenn die Nachfrage geringer ist.
