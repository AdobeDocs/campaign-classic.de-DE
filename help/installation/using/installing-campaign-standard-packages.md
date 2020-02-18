---
title: Installieren von Campaign Classic-Standardpaketen
seo-title: Installieren von Campaign Classic-Standardpaketen
description: Installieren von Campaign Classic-Standardpaketen
seo-description: null
page-status-flag: never-activated
uuid: 1cba9487-52fc-442f-ae99-f8a2c157f25e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: initial-configuration
discoiquuid: dd8f9adf-208c-42d9-b1a7-bfc8a690687e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: a37daa8e31afd3d2ab7d5b70bd8ae02c59ce9ee0

---


# Installieren von Campaign Classic-Standardpaketen{#installing-campaign-standard-packages}

## Standardpakete {#campaign-standard-packages}

Pakete sind eine Reihe von Funktionen, die je nach Bedarf installiert werden können. Dadurch können Sie Ihrer Instanz weitere Optionen hinzufügen.

>[!CAUTION]
>
>Sie dürfen nur Pakete installieren, die den in Ihrem Lizenzvertrag erwähnten Optionen entsprechen.
>
>Nachdem ein Paket installiert wurde, können Sie es nicht deinstallieren. Die Installation eines neuen Pakets kann sich auf Ihre gesamte Plattform auswirken: sie muss vor der endgültigen Bereitstellung getestet und validiert werden.

So installieren Sie ein Standardpaket:

1. Greifen Sie über **[!UICONTROL Tools > Advanced > Package import...]** die Adobe Campaign-Client-Konsole auf den Paketimportassistenten zu.
1. Auswählen **[!UICONTROL Install a standard package]**.
1. Überprüfen Sie in der angezeigten Liste die Pakete, die Sie installieren möchten.
   >[!NOTE]
   >
   >Wenn ein Paket ausgegraut ist, können Sie es nicht installieren. Dies bedeutet, dass diese bereits installiert ist oder nicht mit Ihrer Instanz kompatibel ist. Beispielsweise können Sie das **Mid-Sourcing-Plattform** -Paket nicht auf einer Marketing-Instanz installieren. Diese Informationen finden Sie in der unten stehenden Tabelle.
1. Klicken Sie auf **[!UICONTROL Next]** und **[!UICONTROL Start]** starten Sie die Paketinstallation.

   Nach der Installation der Pakete wird in der Fortschrittsleiste **100%** angezeigt. Die folgende Meldung wird in den Installationsprotokollen angezeigt: **[!UICONTROL Installation of packages successful]**.

1. **[!UICONTROL Close]** das Installationsfenster.

Die Pakete sind jetzt installiert.

### Liste der vordefinierten Pakete {#list-of-standard-packages}

In der folgenden Tabelle sind alle Standardpakete mit ihrer Beschreibung und dem Instanztyp aufgeführt, auf dem sie installiert werden können (Marketing, Mittel usw.) und zusätzliche Informationen.

<table> 
 <thead> 
  <tr> 
   <th> Paket </th> 
   <th> Beschreibung </th> 
   <th> Instanztyp </th> 
   <th> Weitere Informationen </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Versand<br /> </td> 
   <td> Überprüft die Auslieferung und eventuell aufgetretene Probleme beim Senden von Nachrichten.<br /> </td> 
   <td> Alle</td> 
   <td> <a href="../../delivery/using/monitoring-a-delivery.md">mehr dazu</a></td> 
  </tr> 
  <tr> 
   <td> Marketingkampagnen (Kampagne)<br /> </td> 
   <td> Definiert, optimiert, führt und analysiert Kommunikations- und Marketingkampagnen.<br /> </td> 
   <td> Marketing</td> 
   <td> <a href="../../campaign/using/designing-marketing-campaigns.md">Mehr erfahren</a> </td> 
  </tr> 
  <tr> 
   <td> Marketing resources (MRM)<br /> </td> 
   <td> Steuert Marketingaktionen im kollaborativen Modus, indem sie die Verwaltung und Verfolgung der Aufgaben, Budgets und Marketingressourcen bereitstellt.<br /> </td> 
   <td> Marketing</td> 
   <td> <a href="../../campaign/using/about-marketing-resource-management.md">Mehr erfahren</a> </td> 
  </tr> 
  <tr> 
   <td> Angebotsmodul (Interaktion)<br /> </td> 
   <td> Reagiert in Echtzeit auf eine Interaktion mit einem bestimmten Kontakt (Kunde oder Ziel), indem er ein oder mehrere angepasste Angebote erstellt. <br /> </td> 
   <td> Alle<br /> </td> 
   <td> Optional, <a href="../../interaction/using/interaction-and-offer-management.md">weitere Informationen</a></td> 
  </tr> 
  <tr> 
   <td> Steuerung der Angebotsmaschine mit Ausführungsinstanz<br /> </td> 
   <td> </td> 
   <td> Marketing<br /> </td> 
   <td> Optional</td> 
  </tr> 
  <tr> 
   <td> Angebotsengine für Ausführungsinstanzen<br /> </td> 
   <td> </td> 
   <td> Mid, Ausführung <br /> </td> 
   <td> Optional</td> 
  </tr> 
  <!--tr> 
   <td> Lead Management (Leads) (deprecated)<br /> </td> 
   <td> Simplifies the process of building and maintaining the entire leads management life cycle. <br /> </td> 
   <td> Yes<br /> </td> 
   <td> Optional, <a href="https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html">Learn More</a> </td> 
  </tr--> 
  <tr> 
   <td> Soziale Netzwerke (Social Marketing) <br /> </td> 
   <td> Synchronisiert Adobe Campaign mit Twitter und Facebook.<br /> </td> 
   <td> Alle</td> 
   <td> <a href="../../social/using/starting-workflows.md">Mehr erfahren</a> </td> 
  </tr> 
  <tr> 
   <td> Steuerung der Transaktionsnachricht (Message Center - Control)<br /> </td> 
   <td> Verwaltet Auslösermeldungen, die aus Ereignissen generiert wurden, die aus Informationssystemen ausgelöst wurden.<br /> </td> 
   <td> Marketing<br /> </td> 
   <td> Optional, <a href="../../message-center/using/about-transactional-messaging.md">weitere Informationen</a> </td> 
  </tr> 
  <tr> 
   <td> Ausführung von Transaktionsmeldungen (Message Center - Execution) <br /> </td> 
   <td> Stellt eine höhere Verfügbarkeit und ein besseres Lastmanagement sicher.<br /> </td> 
   <td> Ausführung<br /> </td> 
   <td> Optional, <a href="../../message-center/using/about-transactional-messaging.md">weitere Informationen</a> </td> 
  </tr> 
  <tr> 
   <td> LINE-Kanal<br /> </td> 
   <td> Sendet Auslieferungen über den LINE-Kanal mit Adobe Campaign,<br /> </td> 
   <td> Alle<br /> </td> 
   <td> Optional, Meldungscenter obligatorisch</td> 
  </tr> 
  <tr> 
   <td> Direct Mail channel<br /> </td> 
   <td> Sendet Auslieferungen über den Direct Mail-Kanal mit Adobe Campaign.<br /> </td> 
   <td> Alle<br /> </td> 
   <td> Optional, <a href="../../delivery/using/about-direct-mail-channel.md">weitere Informationen</a> </td> 
  </tr> 
  <tr> 
   <td> Mobile-Kanal (SMS) <br /> </td> 
   <td> Sendet Auslieferungen über den Mobil-/SMS-Kanal mit Adobe Campaign.<br /> </td> 
   <td> Alle<br /> </td> 
   <td> Optional, <a href="../../delivery/using/sms-channel.md">weitere Informationen</a> </td> 
  </tr> 
  <tr> 
   <td> Telefonkanal<br /> </td> 
   <td> Sendet Auslieferungen über den Telefonkanal mit Adobe Campaign.<br /> </td> 
   <td> Alle<br /> </td> 
   <td> Optional</td> 
  </tr> 
  <tr> 
   <td> Faxkanal<br /> </td> 
   <td> Sendet Auslieferungen über den Faxkanal mit Adobe Campaign.<br /> </td> 
   <td> Alle<br /> </td> 
   <td> Optional</td> 
  </tr> 
  <tr> 
   <td> Mobile-App-Kanal (Mobile App Channel)<br /> </td> 
   <td> Verwendet die Adobe Campaign-Plattform, um personalisierte Benachrichtigungen über Apps an iOS- und Android-Terminals zu senden. <br /> </td> 
   <td> Alle<br /> </td> 
   <td> Optional, <a href="../../delivery/using/about-mobile-app-channel.md">weitere Informationen</a> </td> 
  </tr> 
  <tr> 
   <td> Content Manager<br /> </td> 
   <td> Erstellt wiederkehrende Newsletter oder Websites und überprüft und veröffentlicht dann Ihre Nachrichten.<br /> </td> 
   <td> </td> 
   <td> <a href="../../delivery/using/about-content-management.md">Mehr erfahren</a> </td> 
  </tr> 
  <tr> 
   <td> Online-Umfragen (Survey Manager)<br /> </td> 
   <td> Erstellt und verwaltet Online-Formulare zum Hinzufügen oder Ändern von Profilinformationen, zum Abonnieren, zum Abmelden oder zum Abbestellen eines Konkurrenzformulars.<br /> </td> 
   <td> Marketing<br /> </td> 
   <td> Optional, <a href="../../web/using/about-surveys.md">weitere Informationen</a> </td> 
  </tr> 
  <tr> 
   <td> Marketing Analytics<br /> </td> 
   <td> Ermöglicht die Analyse und Messung von Daten, die Berechnung von Statistiken, die Vereinfachung und Optimierung der Berichterstellung und -berechnung. Außerdem können Sie Berichte erstellen und Zielgruppen erstellen. <br /> </td> 
   <td> Marketing<br /> </td> 
   <td> Optional, <a href="../../reporting/using/about-cubes.md">weitere Informationen</a> </td> 
  </tr> 
  <tr> 
   <td> Reaktionsverwaltung<br /> </td> 
   <td> Misst den Erfolg und die Rentabilität von Marketingkampagnen oder Angebotsvorschlägen für alle Kommunikationskanäle.<br /> </td> 
   <td> Marketing<br /> </td> 
   <td> Optional, <a href="../../campaign/using/about-response-manager.md">weitere Informationen</a> </td> 
  </tr> 
  <tr> 
   <td> Zugriff auf externe Daten (Federated Data Access)<br /> </td> 
   <td> Provides the Federated Data Access (FDA) option in order to process information stored in one or more external databases so that you can access external data without changing the structure of Adobe Campaign data.<br /> </td> 
   <td> Alle<br /> </td> 
   <td> Optional, <a href="../../workflow/using/accessing-an-external-database--fda-.md">weitere Informationen</a> </td> 
  </tr> 
  <tr> 
   <td> Kampagnenoptimierung (Campaign Optimization)<br /> </td> 
   <td> Kontrolliert, filtert und überwacht den Versand von Sendungen, damit die gesendeten Nachrichten den Anforderungen und Erwartungen der Kunden am besten entsprechen, im Einklang mit den Richtlinien der Unternehmenskommunikation. <br /> </td> 
   <td> Marketing<br /> </td> 
   <td> Optional, <a href="../../campaign/using/about-campaign-typologies.md">weitere Informationen</a> </td> 
  </tr> 
  <tr> 
   <td> Überwachung der Auslieferbarkeit (E-Mail-Auslieferung)<br /> </td> 
   <td> Measures the success of your campaigns reaching your recipients' inbox without bouncing, or being marked as spam.<br /> </td> 
   <td> Alle </td> 
   <td> Optional, <a href="https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliverability.html">weitere Informationen</a> </td> 
  </tr> 
  <tr> 
   <td> Gutscheinverwaltung<br /> </td> 
   <td> Erstellt eine Reihe von Coupons, die zu den bevorstehenden Marketingangeboten hinzugefügt werden sollen.<br /> </td> 
   <td> Marketing<br /> </td> 
   <td> Optional, <a href="../../delivery/using/personalized-coupons.md">weitere Informationen</a> </td> 
  </tr> 
  <tr> 
   <td> Inbox-Rendering (IR)<br /> </td> 
   <td> Ermöglicht die Vorschau der gesendeten Nachricht in den verschiedenen Kontexten, in denen sie empfangen werden kann, und die Überprüfung der Kompatibilität in wichtigen Desktops und Anwendungen. Du brauchst ein Litmus-Konto.<br /> </td> 
   <td> Marketing<br /> </td> 
   <td> Optional, <a href="../../delivery/using/inbox-rendering.md">weitere Informationen</a> </td> 
  </tr> 
  <tr> 
   <td> Zentrales/lokales Marketing (verteiltes Marketing)<br /> </td> 
   <td> Implementiert Kooperationskampagnen zwischen zentralen Stellen (Hauptsitz, Marketingabteilungen usw.) und lokalen Stellen (Verkaufsstellen, regionale Agenturen usw.).<br /> </td> 
   <td> Marketing </td> 
   <td> Optional, <a href="../../campaign/using/about-distributed-marketing.md">weitere Informationen</a> </td> 
  </tr> 
  <tr> 
   <td> CRM-Connectoren<br /> </td> 
   <td> Bietet verschiedene CRM-Connectors zum Verknüpfen Ihrer Adobe Campaign-Plattform mit Ihren Drittanbietersystemen.<br /> </td> 
   <td> Marketing</td> 
   <td> <a href="../../platform/using/crm-connectors.md">Mehr erfahren</a> </td> 
  </tr> 
  <tr> 
   <td> Web-Analytics-Connectoren<br /> </td> 
   <td> Ermöglicht Adobe Campaign und Adobe Analytics die Interaktion über das Web Analytics Connectors-Paket.<br /> </td> 
   <td> Marketing </td> 
   <td> Nicht kompatibel mit Transaktionsnachrichten, <a href="../../platform/using/adobe-analytics-data-connector.md">weitere Informationen</a> </td> 
  </tr> 
  <tr> 
   <td> AEM integration<br /> </td> 
   <td> Ermöglicht Ihnen die Verwaltung der Inhalte Ihrer E-Mail-Auslieferungen sowie Ihrer Formulare direkt in Adobe Experience Manager, um die Funktionen zur Inhaltsbearbeitung von AEM sowie die Bereitstellungskapazitäten von Adobe Campaign nutzen zu können.<br /> </td> 
   <td> Marketing</td> 
   <td> <a href="../../integrations/using/about-adobe-experience-manager.md">Mehr erfahren</a> </td> 
  </tr> 
  <tr> 
   <td> Adobe Marketing Cloud Shared Audiences Integration<br /> </td> 
   <td> Ermöglicht den Austausch und die Freigabe von Zielgruppen/Segmenten mit Adobe Experience Cloud-Lösungen und -Hauptdiensten.<br /> </td> 
   <td> Marketing<br /> </td> 
   <td> Erfordert IMS, <a href="../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md">weitere Informationen</a> </td> 
  </tr> 
  <tr> 
   <td> Integration in Adobe Marketing Cloud<br /> </td> 
   <td> Ermöglicht Ihnen den Import und Export von Zielgruppen/Segmenten aus verschiedenen Adobe Marketing Cloud-Lösungen in Adobe Campaign. </td> 
   <td> Marketing</td> 
   <td> Optional, <a href="../../integrations/using/configuring-ims.md#installing-the-package">weitere Informationen</a> </td> 
  </tr> 
  <tr> 
   <td> Datenschutzbestimmung<br /> </td> 
   <td> Enthält zusätzliche Funktionen, die Ihnen bei der Einhaltung Ihrer Datenschutzbestimmungen in Campaign Classic helfen.<br /> </td> 
   <td> Alle</td> 
   <td> <a href="https://helpx.adobe.com/campaign/kb/acc-privacy.html">Mehr erfahren</a> </td> 
  </tr> 
  <tr> 
   <td> Transfer to Mid-Sourcing <br /> </td> 
   <td> Details zur Installation und Konfiguration eines Mid-Sourcing-Servers sowie zur Bereitstellung einer Instanz, die es Dritten ermöglicht, Nachrichten im Mid-Sourcing-Modus zu senden.<br /> </td> 
   <td> Marketing </td> 
   <td> Optional, <a href="../../installation/using/mid-sourcing-server.md">weitere Informationen</a> </td> 
  </tr> 
  <tr> 
   <td> Mid-Sourcing-Plattform<br /> </td> 
   <td> Diese Konfiguration ist eine optimale Zwischenlösung zwischen einer gehosteten (ASP) Konfiguration und Internalisierung. Die nach außen gerichteten Ausführungskomponenten werden auf einem "Mid-Sourcing"-Server ausgeführt, der bei Adobe Campaign gehostet wird.<br /> </td> 
   <td> Mid-Sourcing </td> 
   <td> Optional, <a href="../../installation/using/mid-sourcing-server.md">weitere Informationen</a> </td> 
  </tr> 
  <tr> 
   <td> ACS Connector<br /> </td> 
   <td> Brilliert Adobe Campaign v7 und Adobe Campaign Standard. Es handelt sich dabei um eine integrierte Funktion in Campaign v7, mit der Daten automatisch in Campaign Standard repliziert werden, wobei die besten beider Anwendungen zusammengeführt werden. <br /> </td> 
   <td> Marketing </td> 
   <td> Optional, <a href="../../integrations/using/acs-connector-principles-and-data-cycle.md">weitere Informationen</a> </td> 
  </tr> 
 </tbody> 
</table>

### Message Center-Paket {#message-center-package}

Um einen Bereitstellungskanal hinzuzufügen (Mobilkanal, Mobilanwendungskanal usw.), muss dieser vor der Installation des Message Center-Pakets ausgeführt werden. Wenn Sie ein Message Center-Projekt auf dem E-Mail-Kanal gestartet haben und sich dann mitten im Projekt entscheiden, einen neuen Kanal hinzuzufügen, müssen Sie folgende Schritte ausführen:

1. Installieren Sie den gewünschten Kanal, z. B. den **Mobilkanal**, mithilfe des Paketimportassistenten ( **[!UICONTROL Tools > Advanced > Import package > Adobe Campaign package]**).
1. Importieren Sie die Datei ( **[!UICONTROL Tools > Advanced > Import package > File]**) und wählen Sie:

   ```
   \datakit\nms\[Your language]\package\messageCenter.xml
   ```

1. Behalten Sie im **[!UICONTROL XML data content to import]** Abschnitt nur die Nachrichtencenter-Bereitstellungsvorlage bei, die dem angeschlossenen Kanal entspricht. Wenn Sie beispielsweise den **Mobilkanal** hinzugefügt haben, sollten Sie nur das Element **Entitäten** beibehalten, das der Vorlage (smsTriggerMessage) entspricht **[!UICONTROL Mobile transactional message]** . Wenn Sie den **Mobilanwendungskanal** hinzugefügt haben, behalten Sie nur die **iOS-Transaktionsmeldungsvorlagen** (iosTriggerMessage) und die **Android-Transaktionsmeldung** (androidTriggerMessage) bei.

   ![](assets/messagecenter_install_channel.png)

### LINE-Paket {#line-package}

Um Auslieferungen über den LINE-Kanal mit Adobe Campaign senden zu können, müssen Sie das LINE-Paket installieren.

Die Installation des LINE-Pakets ist eine Standardinstallation, die im Abschnitt [Pakete](../../platform/using/working-with-data-packages.md#importing-packages) importieren beschrieben wird.

![](assets/line_config_1.png)

>[!CAUTION]
>
>Die Nachrichtencenter-Bereitstellungsvorlagen für LINE sind nicht verfügbar, wenn die Message Center-Pakete vor LINE installiert wurden.
