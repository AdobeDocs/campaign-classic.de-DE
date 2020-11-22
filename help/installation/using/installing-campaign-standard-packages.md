---
solution: Campaign Classic
product: campaign
title: Integrierte Campaign Classic-Pakete installieren
description: Erfahren Sie, wie Sie integrierte Kampagne-Pakete installieren
audience: installation
content-type: reference
topic-tags: initial-configuration
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1189'
ht-degree: 19%

---


# Installing Campaign Classic built-in packages{#installing-campaign-standard-packages}

## Integrierte Pakete {#campaign-standard-packages}

Integrierte Pakete enthalten eine Reihe von Funktionen, die je nach Bedarf und Vertrag installiert werden können. Die vollständige Liste der integrierten Kampagnen finden Sie unten.

>[!CAUTION]
>
>Sie dürfen nur Pakete installieren, die den in Ihrer Lizenzvereinbarung erwähnten Optionen entsprechen.
>
>Die Installation eines neuen Pakets kann sich auf Ihre gesamte Plattform auswirken: sie muss vor der endgültigen Bereitstellung getestet und validiert werden.
>
>Nachdem ein Paket installiert wurde, können Sie es nicht deinstallieren.

So installieren Sie ein integriertes Paket:

1. Greifen Sie über **[!UICONTROL Tools > Erweitert > Package-Import...]** in der Adobe-Campaign-Clientkonsole auf den Package-Import-Assistenten zu.
1. Wählen Sie **[!UICONTROL Standard-Package installieren]** aus.
1. Überprüfen Sie in der Liste &quot;Package&quot;die zu installierenden Pakete.
   >[!NOTE]
   >
   >Wenn ein Paket ausgegraut ist, bedeutet das, dass es bereits installiert ist oder nicht mit Ihrer Instanz kompatibel ist. Die Kompatibilität ist in der folgenden Tabelle aufgeführt.
1. Klicken Sie auf **[!UICONTROL Weiter]** und dann auf **[!UICONTROL Starten]**, um die Package-Installation zu starten.

   Sobald die Packages installiert sind, wird in der Fortschrittsleiste **100 %** angezeigt. Folgende Meldung wird in den Installationsprotokollen angezeigt: **[!UICONTROL Die Installation der Packages wurde erfolgreich beendet]**.

1. **[!UICONTROL Schließen]** Sie das Installationsfenster.

Die Pakete sind jetzt installiert.

### List of out-of-the-box Packages {#list-of-standard-packages}

In der folgenden Tabelle werden alle in der Kampagne integrierten Pakete Liste.

<table> 
 <thead> 
  <tr> 
   <th> Paket </th> 
   <th> Beschreibung  </th> 
   <th> Instanzentyp </th>
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Versand<br /> </td> 
   <td> Überwacht Versand und eventuell aufgetretene Probleme beim Senden von Nachrichten. <a href="../../delivery/using/monitoring-a-delivery.md">Mehr dazu</a><br /> </td> 
   <td> Alle</td> 
  </tr> 
  <tr> 
   <td> Marketing-Kampagnen (Kampagne)<br /> </td> 
   <td> Definiert, optimiert, führt und analysiert Kommunikations- und Marketing-Kampagnen. <a href="../../campaign/using/designing-marketing-campaigns.md">Mehr erfahren</a><br /> </td> 
   <td> Marketing</td>
  </tr> 
  <tr> 
   <td> Marketing resources (MRM)<br /> </td> 
   <td> Steuert Marketingaktionen im kollaborativen Modus, indem sie die Verwaltung und Verfolgung der Aufgaben, Budgets und Marketing-Ressourcen bereitstellt. <a href="../../campaign/using/about-marketing-resource-management.md">Mehr erfahren</a> <br /> </td> 
   <td> Marketing</td> 
  </tr> 
  <tr> 
   <td> Angebot Engine (Interaktion)<br /> </td> 
   <td> Reagiert in Echtzeit auf eine Interaktion mit einem bestimmten Ansprechpartner (Kunde oder Zielgruppe), indem er diese zu einem oder mehreren angepassten Angeboten macht.  Optional. <a href="../../interaction/using/interaction-and-offer-management.md#packages-configuration">Mehr erfahren</a> <br /> </td> 
   <td> Alle<br /> </td> 
  </tr> 
  <tr> 
   <td> Steuerung des Angebot-Motors mit Ausführungsinstanz. Optional.<br /> </td> 
   <td> Paket, das auf Kontrollinstanz für Angebot Engine installiert werden soll (Interaktion). <a href="../../interaction/using/distributed-architectures.md#packages-configuration">Mehr erfahren</a> </td> 
   <td> Marketing<br /> </td>  
  </tr> 
  <tr> 
   <td> Angebot-Engine für Ausführungsinstanzen. Optional.<br /> </td> 
   <td> Paket, das auf Ausführungsinstanzen für die Angebot-Engine installiert werden soll (Interaktion). <a href="../../interaction/using/distributed-architectures.md">Mehr erfahren</a> </td> 
   <td> Mid, Ausführung <br /> </td>  
  </tr> 
  <!--tr> 
   <td> Lead Management (Leads) (deprecated)<br /> </td> 
   <td> Simplifies the process of building and maintaining the entire leads management life cycle. <br /> </td> 
   <td> Yes<br /> </td> 
   <td> Optional, <a href="https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html">Learn More</a> </td> 
  </tr--> 
  <tr> 
   <td> Soziale Netzwerke (Social Marketing) <br /> </td> 
   <td> Synchronisiert Adobe Campaign mit Twitter und Facebook. <a href="../../social/using/about-social-marketing.md">Mehr erfahren</a> <br /> </td> 
   <td> Alle</td> 
  </tr> 
  <tr> 
   <td> Kontrolle der Transaktionsnachricht (Message Center - Control)<br /> </td> 
   <td> Verwaltet Auslösermeldungen, die aus Ereignissen generiert wurden, die aus Informationssystemen ausgelöst wurden. Optional. <a href="../../message-center/using/about-transactional-messaging.md">Mehr erfahren</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Ausführung der Transaktionsnachricht (Nachrichtencenter - Ausführung) <br /> </td> 
   <td> Stellt eine höhere Verfügbarkeit und ein besseres Lastmanagement sicher. Optional. <a href="../../message-center/using/about-transactional-messaging.md">Mehr erfahren</a><br /> </td> 
   <td> Ausführung<br /> </td>
  </tr> 
  <tr> 
   <td> LINE-Kanal<br /> </td> 
   <td> Sendet Versand mit dem LINE-Kanal mit Adobe Campaign. Optional. Transaktionsnachrichten (Message Center-Paket) obligatorisch. <a href="../../delivery/using/line-channel.md">Mehr erfahren</a> <br /> </td> 
   <td> Alle<br /> </td> 
  </tr> 
  <tr> 
   <td> Direct Mail channel<br /> </td> 
   <td> Sendet Versand mit dem Direct Mail-Kanal mit Adobe Campaign. Optional. <a href="../../delivery/using/about-direct-mail-channel.md">Mehr erfahren</a><br /> </td> 
   <td> Alle<br /> </td>
  </tr> 
  <tr> 
   <td> Mobile-Kanal (SMS) <br /> </td> 
   <td> Sendet Versand mit dem Mobile/SMS Kanal mit Adobe Campaign. Optional. <a href="../../delivery/using/sms-channel.md">Mehr erfahren</a> <br /> </td> 
   <td> Alle<br /> </td> 
  </tr> 
  <tr> 
   <td> Mobile-App-Kanal (Mobile App Channel)<br /> </td> 
   <td> Verwendet die Adobe Campaign-Plattform, um personalisierte Benachrichtigungen über Apps an iOS- und Android-Terminals zu senden. Optional. <a href="../../delivery/using/about-mobile-app-channel.md">Mehr erfahren</a> <br /> </td> 
   <td> Alle<br /> </td> 
  </tr> 
  <tr> 
   <td> Content Manager<br /> </td> 
   <td> Erstellt wiederkehrende Newsletter oder Websites und überprüft und veröffentlicht dann Ihre Nachrichten. <a href="../../delivery/using/about-content-management.md">Mehr erfahren</a> <br /> </td> 
   <td> </td>
  </tr> 
  <tr> 
   <td> Online-Umfragen (Umfrage Manager)<br /> </td> 
   <td> Erstellt und verwaltet Online-Formulare zum Hinzufügen oder Ändern von Profil-Informationen, zum Abonnieren, zum Abmelden oder einem Konkurrenzformular. Optional. <a href="../../web/using/about-surveys.md">Mehr erfahren</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Marketing Analytics<br /> </td> 
   <td> Ermöglicht die Analyse und Messung von Daten, die Berechnung von Statistiken, die Vereinfachung und Optimierung der Berichterstellung und -berechnung. Außerdem können Sie Berichte erstellen und Populationen zu Zielgruppen erstellen. Optional. <a href="../../reporting/using/about-cubes.md">Mehr erfahren</a><br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Reaktionsverwaltung<br /> </td> 
   <td> Misst den Erfolg und die Rentabilität von Marketing-Kampagnen oder Angebotsvorschlägen für alle Kommunikations-Kanal.  Optional. <a href="../../campaign/using/about-response-manager.md">Mehr erfahren</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Zugriff auf externe Daten (Federated Data Access)<br /> </td> 
   <td> Bietet die Option "Federated Data Access (FDA)", um in einer oder mehreren externen Datenbanken gespeicherte Informationen zu verarbeiten, sodass Sie auf externe Daten zugreifen können, ohne die Struktur der Adobe Campaign-Daten zu ändern.  Optional. <a href="../../workflow/using/accessing-an-external-database--fda-.md">Mehr erfahren</a> <br /> </td> 
   <td> Alle<br /> </td> 
  </tr> 
  <tr> 
   <td> Kampagnenoptimierung (Campaign Optimization)<br /> </td> 
   <td> Kontrolliert, Filter und überwacht den Versand von Versänden, damit die gesendeten Nachrichten den Bedürfnissen und Erwartungen der Kunden am besten entsprechen, im Einklang mit den Kommunikationsrichtlinien der Firma. Optional. <a href="../../campaign/using/about-campaign-typologies.md">Mehr erfahren</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Zustellbarkeits-Monitoring (Email Deliverability)<br /> </td> 
   <td> Misst den Erfolg Ihrer Kampagnen, die den Posteingang Ihrer Empfänger erreichen, ohne zu springen oder als Spam gekennzeichnet zu werden. Optional. <a href="../../delivery/using/about-deliverability.md">Mehr erfahren</a> <br /> </td> 
   <td> Alle </td> 
  </tr> 
  <tr> 
   <td> Gutscheinverwaltung<br /> </td> 
   <td> Erstellt eine Reihe von Coupons, die zu kommenden Marketing-Angeboten hinzugefügt werden sollen. Optional. <a href="../../delivery/using/personalized-coupons.md">Mehr erfahren</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Inbox Rendering (IR)<br /> </td> 
   <td> Ermöglicht die Vorschau der Nachricht, die in den verschiedenen Kontexten gesendet wird, in denen sie empfangen werden kann, und die Überprüfung der Kompatibilität von Desktop-PCs und Anwendungen. Optional. <a href="../../delivery/using/inbox-rendering.md">Mehr erfahren</a><br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Zentrales/lokales Marketing (Dezentrale Marketing)<br /> </td> 
   <td> Implementiert kooperative Kampagnen zwischen Zentralstellen (Hauptsitz, Marketingabteilungen usw.) und Lokalstellen (Verkaufsstellen, Regionalbüros usw.). Optional. <a href="../../campaign/using/about-distributed-marketing.md">Mehr erfahren</a><br /> </td> 
   <td> Marketing </td> 
  </tr> 
  <tr> 
   <td> CRM-Connectoren<br /> </td> 
   <td> Bietet verschiedene CRM-Connectors zum Verknüpfen Ihrer Adobe Campaign-Plattform mit Ihren Drittanbietersystemen.  <a href="../../platform/using/crm-connectors.md">Mehr erfahren</a> <br /> </td> 
   <td> Marketing</td> 
  </tr> 
  <tr> 
   <td> Web-Analytics-Connectoren<br /> </td> 
   <td> Ermöglicht Adobe Campaign und Adobe Analytics die Interaktion über das Web Analytics Connectors-Paket. Nicht kompatibel mit Transaktionsnachrichten (Message Center-Paket). <a href="../../platform/using/adobe-analytics-data-connector.md">Mehr erfahren</a><br /> </td> 
   <td> Marketing </td> 
  </tr> 
  <tr> 
   <td> AEM integration<br /> </td> 
   <td> Ermöglicht die direkte Verwaltung des Inhalts Ihrer E-Mail-Versand sowie Ihrer Formulare in Adobe Experience Manager, um AEM Funktionen zur Inhaltsbearbeitung und die Versand-Kapazitäten von Adobe Campaign nutzen zu können. <a href="../../integrations/using/about-adobe-experience-manager.md">Mehr erfahren</a> <br /> </td> 
   <td> Marketing</td> 
  </tr> 
  <tr> 
   <td> Integration mit Adobe Experience Cloud Zielgruppen-Freigabe<br /> </td> 
   <td> Ermöglicht den Austausch und die Freigabe von Audiencen/Segmenten mit Adobe Experience Cloud-Lösungen und Hauptdiensten. Erfordert IMS. <a href="../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md">Mehr erfahren</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Integration with Adobe Experience Cloud<br /> </td> 
   <td> Ermöglicht das Importieren und Exportieren von Audiencen/Segmenten aus verschiedenen Adobe Experience Cloud-Lösungen in Adobe Campaign. Optional. <a href="../../integrations/using/configuring-ims.md#installing-the-package">Mehr erfahren</a> </td> 
   <td> Marketing</td> 
  </tr> 
  <tr> 
   <td> Datenschutzbestimmung<br /> </td> 
   <td> Enthält zusätzliche Funktionen, die Ihnen bei der Einhaltung Ihrer Datenschutzbestimmungen in Campaign Classic helfen. <a href="https://helpx.adobe.com/de/campaign/kb/acc-privacy.html">Mehr erfahren</a> <br /> </td> 
   <td> Alle</td> 
  </tr> 
  <tr> 
   <td> Transfer to Mid-Sourcing <br /> </td> 
   <td> Details zur Installation und Konfiguration eines Mid-Sourcing-Servers sowie zur Bereitstellung einer Instanz, die es Dritten ermöglicht, Nachrichten im Mid-Sourcing-Modus zu senden. Optional. <a href="../../installation/using/mid-sourcing-server.md">Mehr erfahren</a> <br /> </td> 
   <td> Marketing </td> 
  </tr> 
  <tr> 
   <td> Mid-Sourcing-Plattform<br /> </td> 
   <td> Diese Konfiguration ist eine optimale Zwischenlösung zwischen einer gehosteten (ASP) Konfiguration und Internalisierung. Die nach außen gerichteten Ausführungskomponenten werden auf einem "Mid-Sourcing"-Server ausgeführt, der bei Adobe Campaign gehostet wird. Optional. <a href="../../installation/using/mid-sourcing-server.md">Mehr erfahren</a> <br /> </td> 
   <td> Mid-Sourcing </td> 
  </tr> 
  <tr> 
   <td> AMP-Unterstützung<br /> </td> 
   <td> Ermöglicht die Verwendung des neuen interaktiven AMP zum E-Mail-Format und das Senden dynamischer E-Mails. Optional. <a href="../../delivery/using/defining-interactive-content.md">Mehr erfahren</a> <br /> </td> 
   <td> Alle </td> 
  </tr> 
  <tr> 
   <td> ACS Connector<br /> </td> 
   <td> Bridges Adobe Campaign v7 und Adobe Campaign Standard Es handelt sich um eine integrierte Funktion in Kampagne v7, die Daten automatisch an Campaign Standard repliziert und die besten beider Anwendungen zusammenführt. Optional. <a href="../../integrations/using/acs-connector-principles-and-data-cycle.md">Mehr erfahren</a> <br /> </td> 
   <td> Marketing </td> 
  </tr> 
 </tbody> 
</table>

### Message Center-Paket {#message-center-package}

Sie müssen Versand-Kanal installieren (E-Mail, Mobile Kanal, Mobile App Kanal usw.) vor der Installation von Transaktionsnachrichten (Message Center-Paket). Wenn Sie ein reines E-Mail-Nachrichtencenter-Projekt gestartet haben und anschließend einen neuen Kanal hinzufügen müssen, führen Sie die folgenden Schritte aus:

1. Install the new channel, for example the **Mobile channel**, using the package import wizard ( **[!UICONTROL Tools > Advanced > Import package > Adobe Campaign package]**).
1. Importieren Sie die Datei (&quot; **[!UICONTROL Extras&quot;> &quot;Erweitert&quot;> &quot;Paket importieren&quot;> &quot;Datei]**&quot;) und wählen Sie:

   ```
   \datakit\nms\[Your language]\package\messageCenter.xml
   ```

1. Behalten Sie im zu importierenden **** XML-Dateninhalt nur die Message Center-Versandvorlage bei, die dem zugehörigen Kanal entspricht. Wenn Sie beispielsweise den **Mobile-Kanal** hinzugefügt haben, sollten Sie nur das **Entitätselement** beibehalten, das der Vorlage für die **[!UICONTROL Mobile-Transaktionsnachricht]** (smsTriggerMessage) entspricht. Wenn Sie den **Mobile App Kanal** hinzugefügt haben, sollten Sie nur die **iOS-Transaktionsnachrichten** -Vorlagen (iosTriggerMessage) und die **Android-Transaktionsnachricht** (androidTriggerMessage) beibehalten.

   ![](assets/messagecenter_install_channel.png)

>[!CAUTION]
>
>Die Message Center-Versandvorlagen für LINE stehen nicht zur Verfügung, wenn die Message Center-Pakete vor LINE installiert wurden.

