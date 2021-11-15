---
product: campaign
title: Installieren von nativen Campaign Classic-Packages
description: Erfahren Sie, wie Sie native Campaign-Pakete installieren.
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: 2bc077c4-ed65-4157-bfc9-df5d0442f476
source-git-commit: 6c23dadb5b6523e17e242de43a908ca86ed7cc23
workflow-type: tm+mt
source-wordcount: '1223'
ht-degree: 23%

---

# Installieren von nativen Campaign Classic-Packages{#installing-campaign-standard-packages}

![](../../assets/v7-only.svg)

## Über native Packages {#campaign-standard-packages}

Integrierte Pakete enthalten eine Reihe von Funktionen, die je nach Ihren Anforderungen und Ihrem Vertrag installiert werden können. Die vollständige Liste der nativen Campaign-Packages finden Sie unten.

>[!CAUTION]
>
>Sie dürfen nur Pakete installieren, die den in Ihrem Lizenzvertrag erwähnten Optionen entsprechen.
>
>Die Installation eines neuen Packages kann sich auf Ihre gesamte Plattform auswirken: Sie muss vor der endgültigen Bereitstellung getestet und validiert werden.
>
>Nachdem ein Paket installiert wurde, kann es nicht mehr deinstalliert werden.
>
>Wenden Sie sich als gehosteter oder hybrider Kunde an die Adobe, um ein neues integriertes Paket bereitzustellen.

So installieren Sie ein integriertes Paket:

1. Greifen Sie über **[!UICONTROL Tools > Erweitert > Package-Import...]** in der Adobe Campaign-Client-Konsole auf den Package-Import-Assistenten zu.
1. Wählen Sie **[!UICONTROL Standard-Package installieren]** aus.
1. Überprüfen Sie in der Paketliste die Pakete, die Sie installieren möchten.
   >[!NOTE]
   >
   >Wenn ein Paket ausgegraut ist, bedeutet dies, dass bereits installiert ist oder nicht mit Ihrer Instanz kompatibel ist. Die Kompatibilität wird in der folgenden Tabelle beschrieben.
1. Klicken Sie auf **[!UICONTROL Weiter]** und dann auf **[!UICONTROL Starten]**, um die Package-Installation zu starten.

   Sobald die Packages installiert sind, wird in der Fortschrittsleiste **100 %** angezeigt. Folgende Meldung wird in den Installationsprotokollen angezeigt: **[!UICONTROL Die Installation der Packages wurde erfolgreich beendet]**.

1. **[!UICONTROL Schließen]** Sie das Installationsfenster.

Die Pakete sind jetzt installiert.

### Liste der nativen Pakete {#list-of-standard-packages}

In der folgenden Tabelle sind alle in Campaign integrierten Packages aufgeführt.

<table> 
 <thead> 
  <tr> 
   <th> Package </th> 
   <th> Beschreibung  </th> 
   <th> Instanzentyp </th>
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Versand<br /> </td> 
   <td> Überprüft Sendungen und etwaige Probleme beim Nachrichtenversand. <a href="../../delivery/using/about-delivery-monitoring.md">Weitere Informationen</a><br /> </td> 
   <td> Alle</td> 
  </tr> 
  <tr> 
   <td> Marketing-Kampagnen (Campaign)<br /> </td> 
   <td> Definiert, optimiert, führt und analysiert Kommunikations- und Marketing-Kampagnen. <a href="../../campaign/using/designing-marketing-campaigns.md">Weitere Informationen</a><br /> </td> 
   <td> Marketing</td>
  </tr> 
  <tr> 
   <td> Marketing-Ressourcen (MRM) <br /> </td> 
   <td> Steuerung kollaborativer Marketing-Aktionen durch Verwaltung und Verfolgung von Aufgaben, Budgets und Marketing-Ressourcen. <a href="../../mrm/using/about-marketing-resource-management.md">Weitere Informationen</a> <br /> </td> 
   <td> Marketing</td> 
  </tr> 
  <tr> 
   <td> Angebotsmodul (interaction)<br /> </td> 
   <td> Reagiert in Echtzeit auf eine Interaktion mit einem bestimmten Kontakt (einem Kunden oder einer Zielgruppe), indem er ihm ein oder mehrere angepasste Angebote unterbreitet.  Optional. <a href="../../interaction/using/interaction-and-offer-management.md#packages-configuration">Weitere Informationen</a> <br /> </td> 
   <td> Alle<br /> </td> 
  </tr> 
  <tr> 
   <td> Steuerung des Angebotsmoduls durch die Ausführungsinstanz. Optional.<br /> </td> 
   <td> Paket zur Installation auf Kontrollinstanz für Angebotsmodul (Interaktion). <a href="../../interaction/using/distributed-architectures.md#packages-configuration">Weitere Informationen</a> </td> 
   <td> Marketing<br /> </td>  
  </tr> 
  <tr> 
   <td> Angebotsmodul der Ausführungsinstanzen. Optional.<br /> </td> 
   <td> Package zur Installation auf Ausführungsinstanzen für das Angebotsmodul (Interaktion). <a href="../../interaction/using/distributed-architectures.md">Weitere Informationen</a> </td> 
   <td> Mid, Ausführung <br /> </td>  
  </tr> 
  <!--tr> 
   <td> Lead Management (Leads) (deprecated)<br /> </td> 
   <td> Simplifies the process of building and maintaining the entire leads management life cycle. <br /> </td> 
   <td> Yes<br /> </td> 
   <td> Optional, <a href="https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html">Learn More</a> </td> 
  </tr--> 
  <tr> 
   <td> Social Media (Social Marketing) <br /> </td> 
   <td> Synchronisiert Adobe Campaign mit Twitter und Facebook. <a href="../../social/using/about-social-marketing.md">Weitere Informationen</a> <br /> </td> 
   <td> Alle</td> 
  </tr> 
  <tr> 
   <td> Kontrolle der Transaktionsnachrichten (Message Center – Kontrolle)<br /> </td> 
   <td> Verwaltet Trigger-Nachrichten, die von Ereignissen generiert wurden, die von Informationssystemen ausgelöst wurden. Optional. <a href="../../message-center/using/about-transactional-messaging.md">Weitere Informationen</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Ausführung einer Transaktionsnachricht (Message Center – Ausführung) <br /> </td> 
   <td> Bietet höhere Verfügbarkeit und besseres Lastmanagement. Optional. <a href="../../message-center/using/about-transactional-messaging.md">Weitere Informationen</a><br /> </td> 
   <td> Ausführung<br /> </td>
  </tr> 
  <tr> 
   <td> LINE-Kanal<br /> </td> 
   <td> Sendet Sendungen über den LINE-Kanal mit Adobe Campaign. Optional. Transaktionsnachrichten (Message Center Package) erforderlich. <a href="../../delivery/using/line-channel.md">Weitere Informationen</a> <br /> </td> 
   <td> Alle<br /> </td> 
  </tr> 
  <tr> 
   <td> Briefpost-Kanal<br /> </td> 
   <td> Sendet Sendungen über den Briefpost-Kanal mit Adobe Campaign. Optional. <a href="../../delivery/using/about-direct-mail-channel.md">Weitere Informationen</a><br /> </td> 
   <td> Alle<br /> </td>
  </tr> 
  <tr> 
   <td> Mobile-Kanal (SMS) <br /> </td> 
   <td> Sendet Sendungen über den Mobiltelefon-/SMS-Kanal mit Adobe Campaign. Optional. <a href="../../delivery/using/sms-channel.md">Weitere Informationen</a> <br /> </td> 
   <td> Alle<br /> </td> 
  </tr> 
   <tr> 
   <td> Telefon-Kanal<br /> </td> 
   <td> Sendet Sendungen über den Telefonkanal mit Adobe Campaign. Wird für Callcenter verwendet. Optional. <a href="../../delivery/using/communication-channels.md">Weitere Informationen</a> <br /> </td> 
   <td> Alle<br /> </td> 
  </tr> 
  <tr> 
   <td> Mobile-App-Kanal (Mobile App Channel)<br /> </td> 
   <td> Verwendet die Adobe Campaign-Plattform zum Senden personalisierter Benachrichtigungen über Apps an iOS- und Android-Geräte. Optional. <a href="../../delivery/using/about-mobile-app-channel.md">Weitere Informationen</a> <br /> </td> 
   <td> Alle<br /> </td> 
  </tr> 
  <tr> 
   <td> Content Manager<br /> </td> 
   <td> Erstellt wiederkehrende Newsletter oder Websites und validiert und veröffentlicht Ihre Nachrichten. <a href="../../delivery/using/about-content-management.md">Weitere Informationen</a> <br /> </td> 
   <td> </td>
  </tr> 
  <tr> 
   <td> Online-Umfragen (Survey Manager)<br /> </td> 
   <td> Erstellt und verwaltet Online-Formulare, um Profilinformationen hinzuzufügen oder zu ändern, sich anzumelden, sich abzumelden oder ein Gewinnspielformular zu erstellen. Optional. <a href="../../surveys/using/about-surveys.md">Weitere Informationen</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Marketing Analytics<br /> </td> 
   <td> Ermöglicht die Analyse und Messung von Daten, die Berechnung von Statistiken, die Vereinfachung und Optimierung der Berichterstellung und -berechnung. Außerdem können Sie Berichte erstellen und Zielpopulationen erstellen. Optional. <a href="../../reporting/using/about-cubes.md">Weitere Informationen</a><br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Reaktionsverwaltung<br /> </td> 
   <td> Misst den Erfolg und die Rentabilität von Marketing-Kampagnen oder Angebotsvorschlägen für alle Kommunikationskanäle.  Optional. <a href="../../response/using/about-response-manager.md">Weitere Informationen</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Zugriff auf externe Daten (Federated Data Access)<br /> </td> 
   <td> Bietet die Option Federated Data Access (FDA), um in externen Datenbanken gespeicherte Informationen zu verarbeiten, sodass Sie auf externe Daten zugreifen können, ohne die Datenstruktur in Adobe Campaign zu verändern.  Optional. <a href="../../workflow/using/accessing-an-external-database--fda-.md">Weitere Informationen</a> <br /> </td> 
   <td> Alle<br /> </td> 
  </tr> 
  <tr> 
   <td> Kampagnenoptimierung (Campaign Optimization)<br /> </td> 
   <td> Die Kontrolle, Filterung und Überwachung des Versands von Nachrichten, damit die gesendeten Nachrichten entsprechend den Kommunikationsrichtlinien des Unternehmens den Anforderungen und Erwartungen der Kunden am besten entsprechen. Optional. <a href="../../campaign-opt/using/about-campaign-typologies.md">Weitere Informationen</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Zustellbarkeits-Monitoring (Email Deliverability)<br /> </td> 
   <td> Misst den Erfolg Ihrer Kampagnen, die in den Posteingang Ihrer Empfänger gelangen, ohne dass ein Absprung erfolgt oder sie als Spam gekennzeichnet werden. Optional. <a href="../../delivery/using/about-deliverability.md">Weitere Informationen</a> <br /> </td> 
   <td> Alle </td> 
  </tr> 
  <tr> 
   <td> Couponverwaltung<br /> </td> 
   <td> Erstellt eine Reihe von Coupons, die zu anstehenden Marketing-Angeboten hinzugefügt werden sollen. Optional. <a href="../../delivery/using/personalized-coupons.md">Weitere Informationen</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Rendering des Posteingangs (Inbox Rendering, IR)<br /> </td> 
   <td> Ermöglicht die Vorschau der Nachricht in den verschiedenen Kontexten, in denen sie empfangen werden kann, und die Überprüfung der Kompatibilität mit den wichtigsten Desktops und Anwendungen. Optional. <a href="../../delivery/using/inbox-rendering.md">Weitere Informationen</a><br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Zentrales/lokales Marketing (verteiltes Marketing)<br /> </td> 
   <td> Durchführung von Kooperationskampagnen zwischen Zentralstellen (Hauptsitz, Marketingabteilungen usw.) und Lokalstellen (Verkaufsstellen, regionale Agenturen usw.). Optional. <a href="../../distributed/using/about-distributed-marketing.md">Weitere Informationen</a><br /> </td> 
   <td> Marketing </td> 
  </tr> 
  <tr> 
   <td> CRM-Connectoren<br /> </td> 
   <td> Bietet verschiedene CRM-Connectoren zum Verknüpfen Ihrer Adobe Campaign-Plattform mit Drittanbietersystemen.  <a href="../../platform/using/crm-connectors.md">Weitere Informationen</a> <br /> </td> 
   <td> Marketing</td> 
  </tr> 
  <tr> 
   <td> Web Analytics-Connectoren<br /> </td> 
   <td> Ermöglicht die Interaktion zwischen Adobe Campaign und Adobe Analytics über das Web Analytics Connectors-Paket. Nicht kompatibel mit Transaktionsnachrichten (Message Center Package). <a href="../../platform/using/adobe-analytics-connector.md">Weitere Informationen</a><br /> </td> 
   <td> Marketing </td> 
  </tr> 
  <tr> 
   <td> AEM<br /> </td> 
   <td> Ermöglicht die direkte Verwaltung des Inhalts Ihres E-Mail-Versands und Ihrer Formulare in Adobe Experience Manager, um von AEM Inhaltsbearbeitungsfunktionen sowie den Versandkapazitäten von Adobe Campaign zu profitieren. <a href="../../integrations/using/about-adobe-experience-manager.md">Weitere Informationen</a> <br /> </td> 
   <td> Marketing</td> 
  </tr> 
  <tr> 
   <td> Integration mit Adobe Experience Cloud Zielgruppen-Freigabe<br /> </td> 
   <td> Ermöglicht den Austausch und die Freigabe von Zielgruppen/Segmenten mit Adobe Experience Cloud-Lösungen und Hauptdiensten. Erfordert IMS. <a href="../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md">Weitere Informationen</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Integration mit Adobe Experience Cloud<br /> </td> 
   <td> Ermöglicht den Import und Export von Zielgruppen/Segmenten aus verschiedenen Adobe Experience Cloud-Lösungen in Adobe Campaign. Optional. <a href="../../integrations/using/configuring-ims.md#installing-the-package">Weitere Informationen</a> </td> 
   <td> Marketing</td> 
  </tr> 
  <tr> 
   <td> Datenschutzbestimmung<br /> </td> 
   <td> Enthält zusätzliche Funktionen, die Ihnen bei der Einhaltung Ihrer Datenschutzbestimmungen in Campaign Classic helfen. <a href="https://helpx.adobe.com/de/campaign/kb/acc-privacy.html">Weitere Informationen</a> <br /> </td> 
   <td> Alle</td> 
  </tr> 
  <tr> 
   <td> Sendung an Mid-Sourcing-Server <br /> </td> 
   <td> Details zur Installation und Konfiguration eines Mid-Sourcing-Servers sowie zur Bereitstellung einer Instanz, die es Dritten ermöglicht, Nachrichten im Mid-Sourcing-Modus zu senden. Optional. <a href="../../installation/using/mid-sourcing-server.md">Weitere Informationen</a> <br /> </td> 
   <td> Marketing </td> 
  </tr> 
  <tr> 
   <td> Mid-Sourcing-Plattform<br /> </td> 
   <td> Diese Konfiguration ist eine optimale Zwischenlösung zwischen einer gehosteten (ASP)-Konfiguration und der Internalisierung. Die nach außen gerichteten Ausführungskomponenten werden auf einem "Mid-Sourcing"-Server ausgeführt, der in Adobe Campaign gehostet wird. Optional. <a href="../../installation/using/mid-sourcing-server.md">Weitere Informationen</a> <br /> </td> 
   <td> Mid-Sourcing </td> 
  </tr> 
  <tr> 
   <td> AMP-Unterstützung<br /> </td> 
   <td> Ermöglicht die Verwendung des neuen interaktiven AMP für das E-Mail-Format und das Senden dynamischer E-Mails. Optional. <a href="../../delivery/using/defining-interactive-content.md">Weitere Informationen</a> <br /> </td> 
   <td> Alle </td> 
  </tr> 
  <tr> 
   <td> ACS Connector<br /> </td> 
   <td> Bridges Adobe Campaign v7 and Adobe Campaign Standard. Es handelt sich um eine integrierte Funktion in Campaign v7, mit der Daten automatisch an Campaign Standard repliziert werden, sodass die besten beider Anwendungen kombiniert werden können. Optional. <a href="../../integrations/using/acs-connector-principles-and-data-cycle.md">Weitere Informationen</a> <br /> </td> 
   <td> Marketing </td> 
  </tr> 
 </tbody> 
</table>

### Message Center Package {#message-center-package}

Sie müssen Versandkanäle (E-Mail, Mobile-Kanal, Mobile-App-Kanal usw.) installieren. vor der Installation von Transaktionsnachrichten (Message Center-Package). Wenn Sie ein E-Mail-spezifisches Message-Center-Projekt gestartet haben und danach einen neuen Kanal hinzufügen müssen, müssen Sie die folgenden Schritte ausführen:

1. Installieren Sie den neuen Kanal, z. B. die **Mobile Kanal**&#x200B;über den Package-Import-Assistenten ( **[!UICONTROL Tools > Erweitert > Package importieren > Adobe Campaign-Package]**).
1. Importieren Sie die Datei ( **[!UICONTROL Tools > Erweitert > Package importieren > Datei]**) und wählen Sie:

   ```
   \datakit\nms\[Your language]\package\messageCenter.xml
   ```

1. Im **[!UICONTROL Zu importierender XML-Dateninhalt]** beibehalten, sollten Sie nur die Nachrichtencenter-Versandvorlage beibehalten, die dem entsprechenden Kanal entspricht. Wenn Sie beispielsweise die Variable **Mobile Kanal**, behalten Sie nur die **entity** Element, das dem **[!UICONTROL Mobile Transaktionsnachricht]** (smsTriggerMessage). Wenn Sie die **Mobile App Channel**, behalten Sie nur die **iOS-Transaktionsnachricht** templates (iosTriggerMessage) und **Android-Transaktionsnachricht** (androidTriggerMessage).

   ![](assets/messagecenter_install_channel.png)

>[!CAUTION]
>
>Die Message-Center-Versandvorlagen für LINE sind nicht verfügbar, wenn die Message-Center-Packages vor LINE installiert sind.
