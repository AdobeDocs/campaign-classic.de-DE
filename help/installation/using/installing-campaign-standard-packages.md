---
product: campaign
title: Installieren von nativen Campaign Classic-Packages
description: Erfahren Sie, wie Sie native Campaign-Pakete installieren.
feature: Installation, Application Settings
badge-v7-prem: label="Nur On-Premise/Hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Gilt nur für Hybrid- und On-Premise-Bereitstellungen"
exl-id: 2bc077c4-ed65-4157-bfc9-df5d0442f476
source-git-commit: b11185da8236d6100d98eabcc9dc1cf2cffa70af
workflow-type: tm+mt
source-wordcount: '1299'
ht-degree: 11%

---

# Installieren von nativen Campaign Classic-Packages{#installing-campaign-standard-packages}



## Über native Packages {#campaign-standard-packages}

Integrierte Pakete enthalten eine Reihe von Funktionen, die je nach Ihren Anforderungen und Ihrem Vertrag installiert werden können. Die vollständige Liste der nativen Campaign-Packages finden Sie unten.

>[!CAUTION]
>
>Sie dürfen nur Pakete installieren, die den in Ihrem Lizenzvertrag erwähnten Optionen entsprechen.
>
>Die Installation eines neuen Packages kann sich auf Ihre gesamte Plattform auswirken: Es muss vor der endgültigen Bereitstellung getestet und validiert werden.
>
>Nachdem ein Paket installiert wurde, kann es nicht mehr deinstalliert werden.
>
>Wenden Sie sich als gehosteter oder hybrider Kunde an Adobe, um ein neues integriertes Paket bereitzustellen.

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
   <td> Marketing-Kampagnen (Kampagne)<br /> </td> 
   <td> Definiert, optimiert, führt und analysiert Kommunikations- und Marketing-Kampagnen. <a href="../../campaign/using/designing-marketing-campaigns.md">Mehr erfahren</a><br /> </td> 
   <td> Marketing</td>
  </tr> 
  <tr> 
   <td> Marketing-Ressourcen (MRM)<br /> </td> 
   <td> Steuerung kollaborativer Marketing-Aktionen durch Verwaltung und Verfolgung von Aufgaben, Budgets und Marketing-Ressourcen. <a href="../../mrm/using/about-marketing-resource-management.md">Mehr erfahren</a> <br /> </td> 
   <td> Marketing</td> 
  </tr> 
  <tr> 
   <td> Angebotsmodul (interaction)<br /> </td> 
   <td> Reagiert in Echtzeit auf eine Interaktion mit einem bestimmten Kontakt (einem Kunden oder einer Zielgruppe), indem er ihm ein oder mehrere angepasste Angebote unterbreitet.  Optional. <a href="../../interaction/using/interaction-and-offer-management.md#packages-configuration">Mehr erfahren</a> <br /> </td> 
   <td> Alle<br /> </td> 
  </tr> 
  <tr> 
   <td> Steuerung des Angebotsmoduls mit der Ausführungsinstanz. Optional.<br /> </td> 
   <td> Paket zur Installation auf Kontrollinstanz für Angebotsmodul (Interaktion). <a href="../../interaction/using/distributed-architectures.md#packages-configuration">Mehr erfahren</a> </td> 
   <td> Marketing<br /> </td>  
  </tr> 
  <tr> 
   <td> Angebotsmodul für Ausführungsinstanzen. Optional.<br /> </td> 
   <td> Package zur Installation auf Ausführungsinstanzen für das Angebotsmodul (Interaktion). <a href="../../interaction/using/distributed-architectures.md">Mehr erfahren</a> </td> 
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
   <td> Synchronisiert Adobe Campaign mit X (früher Twitter) und Facebook. <a href="../../social/using/about-social-marketing.md">Mehr erfahren</a> <br /> </td> 
   <td> Alle</td> 
  </tr> 
  <tr> 
   <td> Kontrolle von Transaktionsnachrichten (Message Center - Kontrolle)<br /> </td> 
   <td> Verwaltet Trigger-Nachrichten, die von Ereignissen generiert wurden, die von Informationssystemen ausgelöst wurden. Optional. <a href="../../message-center/using/about-transactional-messaging.md">Mehr erfahren</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Ausführung von Transaktionsnachrichten (Message Center - Ausführung) <br /> </td> 
   <td> Bietet höhere Verfügbarkeit und besseres Lastmanagement. Optional. <a href="../../message-center/using/about-transactional-messaging.md">Mehr erfahren</a><br /> </td> 
   <td> Ausführung<br /> </td>
  </tr> 
  <tr> 
   <td> LINE-Kanal<br /> </td> 
   <td> Sendet Sendungen über den LINE-Kanal mit Adobe Campaign. Optional. Transaktionsnachrichten (Message Center Package) erforderlich. <a href="../../delivery/using/line-channel.md">Mehr erfahren</a> <br /> </td> 
   <td> Alle<br /> </td> 
  </tr> 
  <tr> 
   <td> Briefpost-Kanal<br /> </td> 
   <td> Sendet Sendungen über den Briefpost-Kanal mit Adobe Campaign. Optional. <a href="../../delivery/using/about-direct-mail-channel.md">Mehr erfahren</a><br /> </td> 
   <td> Alle<br /> </td>
  </tr> 
  <tr> 
   <td> Mobiltelefon-Kanal (SMS) <br /> </td> 
   <td> Sendet Sendungen über den Mobiltelefon-/SMS-Kanal mit Adobe Campaign. Optional. <a href="../../delivery/using/sms-channel.md">Mehr erfahren</a> <br /> </td> 
   <td> Alle<br /> </td> 
  </tr> 
   <tr> 
   <td> Telefonkanal<br /> </td> 
   <td> Sendet Sendungen über den Telefonkanal mit Adobe Campaign. Wird für Callcenter verwendet. Optional. <a href="../../delivery/using/communication-channels.md">Mehr erfahren</a> <br /> </td> 
   <td> Alle<br /> </td> 
  </tr> 
  <tr> 
   <td> Mobile-App-Kanal (Mobile App Channel)<br /> </td> 
   <td> Verwendet die Adobe Campaign-Plattform zum Senden personalisierter Benachrichtigungen an iOS- und Android-Terminals über Apps. Optional. <a href="../../delivery/using/about-mobile-app-channel.md">Mehr erfahren</a> <br /> </td> 
   <td> Alle<br /> </td> 
  </tr> 
  <tr> 
   <td> Content Manager<br /> </td> 
   <td> Erstellt wiederkehrende Newsletter oder Websites und validiert und veröffentlicht Ihre Nachrichten. <a href="../../delivery/using/about-content-management.md">Mehr erfahren</a> <br /> </td> 
   <td> </td>
  </tr> 
  <tr> 
   <td> Online-Umfragen (Survey Manager)<br /> </td> 
   <td> Erstellt und verwaltet Online-Formulare, um Profilinformationen hinzuzufügen oder zu ändern, sich anzumelden, sich abzumelden oder ein Gewinnspielformular zu erstellen. Optional. <a href="../../surveys/using/about-surveys.md">Mehr erfahren</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Marketing Analytics<br /> </td> 
   <td> Ermöglicht die Analyse und Messung von Daten, die Berechnung von Statistiken, die Vereinfachung und Optimierung der Berichterstellung und -berechnung. Außerdem können Sie Berichte erstellen und Zielpopulationen erstellen. Optional. <a href="../../reporting/using/ac-cubes.md">Mehr erfahren</a><br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Reaktionsverwaltung<br /> </td> 
   <td> Misst den Erfolg und die Rentabilität von Marketing-Kampagnen oder Angebotsvorschlägen für alle Kommunikationskanäle.  Optional. <a href="../../response/using/about-response-manager.md">Mehr erfahren</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Zugriff auf externe Daten (Federated Data Access)<br /> </td> 
   <td> Bietet die Option Federated Data Access (FDA), um in externen Datenbanken gespeicherte Informationen zu verarbeiten, sodass Sie auf externe Daten zugreifen können, ohne die Datenstruktur in Adobe Campaign zu verändern.  Optional. <a href="../../workflow/using/accessing-an-external-database-fda.md">Mehr erfahren</a> <br /> </td> 
   <td> Alle<br /> </td> 
  </tr> 
  <tr> 
   <td> Kampagnenoptimierung (Campaign Optimization)<br /> </td> 
   <td> Die Kontrolle, Filterung und Überwachung des Versands von Nachrichten, damit die gesendeten Nachrichten entsprechend den Kommunikationsrichtlinien des Unternehmens den Anforderungen und Erwartungen der Kunden am besten entsprechen. Optional. <a href="../../campaign-opt/using/about-campaign-typologies.md">Mehr erfahren</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Zustellbarkeits-Monitoring (Email Deliverability)<br /> </td> 
   <td> Misst den Erfolg Ihrer Kampagnen, die in den Posteingang Ihrer Empfänger gelangen, ohne dass ein Absprung erfolgt oder sie als Spam gekennzeichnet werden. Optional. <a href="../../delivery/using/about-deliverability.md">Mehr erfahren</a> <br /> </td> 
   <td> Alle </td> 
  </tr> 
  <tr> 
   <td> Couponverwaltung<br /> </td> 
   <td> Erstellt eine Reihe von Coupons, die zu anstehenden Marketing-Angeboten hinzugefügt werden sollen. Optional. <a href="../../delivery/using/personalized-coupons.md">Mehr erfahren</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Inbox Rendering (IR)<br /> </td> 
   <td> Ermöglicht die Vorschau der Nachricht in den verschiedenen Kontexten, in denen sie empfangen werden kann, und die Überprüfung der Kompatibilität mit den wichtigsten Desktops und Anwendungen. Optional. <a href="../../delivery/using/inbox-rendering.md">Mehr erfahren</a><br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Zentrales/lokales Marketing (dezentrales Marketing)<br /> </td> 
   <td> Durchführung von Kooperationskampagnen zwischen Zentralstellen (Hauptsitz, Marketingabteilungen usw.) und lokalen Einheiten (Verkaufsstellen, regionale Agenturen usw.). Optional. <a href="../../distributed/using/about-distributed-marketing.md">Mehr erfahren</a><br /> </td> 
   <td> Marketing </td> 
  </tr> 
  <tr> 
   <td> CRM-Connectoren<br /> </td> 
   <td> Bietet verschiedene CRM-Connectoren zum Verknüpfen Ihrer Adobe Campaign-Plattform mit Drittanbietersystemen.  <a href="../../platform/using/crm-connectors.md">Mehr erfahren</a> <br /> </td> 
   <td> Marketing</td> 
  </tr> 
  <tr> 
   <td> Web Analytics-Connectoren<br /> </td> 
   <td> Ermöglicht die Interaktion zwischen Adobe Campaign und Adobe Analytics über das Web Analytics Connectors-Paket. Nicht kompatibel mit Transaktionsnachrichten (Message Center Package). <a href="../../integrations/using/gs-aa.md">Mehr erfahren</a><br /> </td> 
   <td> Marketing </td> 
  </tr> 
  <tr> 
   <td> AEM Integration<br /> </td> 
   <td> Ermöglicht die direkte Verwaltung des Inhalts Ihres E-Mail-Versands und Ihrer Formulare in Adobe Experience Manager, um von den AEM Inhaltsbearbeitungsfunktionen sowie den Versandkapazitäten von Adobe Campaign zu profitieren. <a href="../../integrations/using/about-adobe-experience-manager.md">Mehr erfahren</a> <br /> </td> 
   <td> Marketing</td> 
  </tr> 
  <tr> 
   <td> Integration von freigegebenen Adobe Experience Cloud-Zielgruppen<br /> </td> 
   <td> Ermöglicht den Austausch und die Freigabe von Zielgruppen/Segmenten mit Adobe Experience Cloud-Lösungen und -Apps. Erfordert IMS. <a href="../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md">Mehr erfahren</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Integration mit Adobe Experience Cloud<br /> </td> 
   <td> Ermöglicht den Import und Export von Zielgruppen/Segmenten aus verschiedenen Adobe Experience Cloud-Lösungen in Adobe Campaign. Optional. <a href="../../integrations/using/configuring-ims.md#installing-the-package">Mehr erfahren</a> </td> 
   <td> Marketing</td> 
  </tr> 
  <tr> 
   <td> Datenschutzbestimmung<br /> </td> 
   <td> Enthält zusätzliche Funktionen, die Ihnen bei der Einhaltung von Datenschutzbestimmungen in Campaign Classic helfen. <a href="https://helpx.adobe.com/de/campaign/kb/acc-privacy.html">Mehr erfahren</a> <br /> </td> 
   <td> Alle</td> 
  </tr> 
  <tr> 
   <td> Sendung an Mid-Sourcing-Server <br /> </td> 
   <td> Details zur Installation und Konfiguration eines Mid-Sourcing-Servers sowie zur Bereitstellung einer Instanz, die es Dritten ermöglicht, Nachrichten im Mid-Sourcing-Modus zu senden. Optional. <a href="../../installation/using/mid-sourcing-server.md">Mehr erfahren</a> <br /> </td> 
   <td> Marketing </td> 
  </tr> 
  <tr> 
   <td> Mid-Sourcing-Plattform<br /> </td> 
   <td> Diese Konfiguration ist eine optimale Zwischenlösung zwischen einer gehosteten (ASP)-Konfiguration und der Internalisierung. Die nach außen gerichteten Ausführungskomponenten werden auf einem "Mid-Sourcing"-Server ausgeführt, der in Adobe Campaign gehostet wird. Optional. <a href="../../installation/using/mid-sourcing-server.md">Mehr erfahren</a> <br /> </td> 
   <td> Mid-Sourcing </td> 
  </tr> 
  <tr> 
   <td> AMP-Unterstützung<br /> </td> 
   <td> Ermöglicht die Verwendung des neuen interaktiven AMP für das E-Mail-Format und das Senden dynamischer E-Mails. Optional. <a href="../../delivery/using/defining-interactive-content.md">Mehr erfahren</a> <br /> </td> 
   <td> Alle </td> 
  </tr> 
  <tr> 
   <td> ACS Connector (nicht mehr unterstützt)<br /> </td> 
   <td> Bridges Adobe Campaign v7 and Adobe Campaign Standard. Hierbei handelt es sich um eine integrierte Funktion in Campaign v7, mit der Daten automatisch in Campaign Standard repliziert werden, sodass die Vorzüge beider Anwendungen kombiniert werden können. Optional.<br /> </td> 
   <td> Marketing </td> 
  </tr> 
 </tbody> 
</table>

### Message Center Package {#message-center-package}

Sie müssen Versandkanäle (E-Mail, Mobile-Kanal, Mobile-App-Kanal, LINE usw.) installieren. vor der Installation von Transaktionsnachrichten (Message Center-Package). Wenn Sie ein E-Mail-spezifisches Message-Center-Projekt gestartet haben und danach einen neuen Kanal hinzufügen müssen, müssen Sie die folgenden Schritte ausführen:

1. Installieren Sie den neuen Kanal, z. B. den **Mobile-Kanal**, mithilfe des Package-Import-Assistenten ( **[!UICONTROL Tools > Erweitert > Package importieren > Adobe Campaign-Package]**).
1. Importieren Sie die Datei ( **[!UICONTROL Tools > Erweitert > Package importieren > Datei]**) und wählen Sie Folgendes aus:

   ```
   \datakit\nms\[Your language]\package\messageCenter.xml
   ```

1. Behalten Sie im zu importierenden **[!UICONTROL XML-Dateninhalt]** nur die Message Center-Versandvorlage bei, die dem zugehörigen Kanal entspricht. Wenn Sie beispielsweise den Kanal **Mobil** hinzugefügt haben, behalten Sie nur das Element **entitäten** bei, das der Vorlage **[!UICONTROL Mobile Transaktionsnachricht]** (smsTriggerMessage) entspricht. Wenn Sie den **Mobile-App-Kanal** hinzugefügt haben, behalten Sie nur die Vorlagen für die **iOS-Transaktionsnachricht** (iosTriggerMessage) und die **Android-Transaktionsnachricht** (androidTriggerMessage) bei.

   ![](assets/messagecenter_install_channel.png)


### [!DNL LINE] Kanaleinrichtung{#line-package}

Um den Kanal [!DNL LINE] einzurichten, müssen Sie zunächst das Paket [!DNL LINE] installieren.

Im Kontext einer Mid-Sourcing-Konfiguration müssen Sie:

* Installieren Sie das Paket [!DNL LINE] sowohl auf der Marketing- als auch auf der MID-Instanz

* Richten Sie das externe Konto [!DNL LINE] auf der Mkt-Instanz so ein, dass es auf die Mid-Instanz verweist, indem Sie den Versandmodus ändern. [Weitere Informationen](../../delivery/using/line-channel.md#configure-line-external)

* Richten Sie die Anmeldedaten für [!DNL LINE] im externen Konto auf der MID-Instanz ein.

>[!CAUTION]
>
>Die Message-Center-Versandvorlagen für den Kanal [!DNL LINE] sind nicht verfügbar, wenn die Message-Center-Packages vor [!DNL LINE] installiert sind.