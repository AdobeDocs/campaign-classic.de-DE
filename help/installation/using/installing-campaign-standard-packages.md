---
product: campaign
title: Installieren von integrierten Campaign Classic-Packages
description: Erfahren Sie, wie Sie integrierte Campaign-Pakete installieren
feature: Installation, Application Settings
badge-v7-prem: label="Nur On-Premise/Hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Gilt nur für Hybrid- und On-Premise-Bereitstellungen"
exl-id: 2bc077c4-ed65-4157-bfc9-df5d0442f476
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '1305'
ht-degree: 11%

---

# Installieren von integrierten Campaign Classic-Packages{#installing-campaign-standard-packages}



## Über integrierte Pakete {#campaign-standard-packages}

Integrierte Pakete enthalten eine Reihe von Funktionen, die je nach Bedarf und nach Vertrag installiert werden können. Die vollständige Liste der in Campaign integrierten Packages ist unten verfügbar.

>[!CAUTION]
>
>Sie dürfen nur Pakete installieren, die den in Ihrer Lizenzvereinbarung genannten Optionen entsprechen.
>
>Die Installation eines neuen Pakets kann sich auf Ihre gesamte Plattform auswirken: Es muss vor der endgültigen Bereitstellung getestet und validiert werden.
>
>Nachdem ein Paket installiert wurde, können Sie es nicht mehr deinstallieren.
>
>Wenn Sie gehosteter oder Hybrid-Kunde sind, kontaktieren Sie Adobe , um ein neues integriertes Paket bereitzustellen.

So installieren Sie ein integriertes Paket:

1. Greifen Sie über **[!UICONTROL Werkzeuge > Erweitert > Package-Import]** in der Adobe Campaign-Client-Konsole auf den Package-Import-Assistenten zu.
1. Wählen Sie **[!UICONTROL Standard-Package installieren]** aus.
1. Aktivieren Sie in der Paketliste die Pakete, die Sie installieren möchten.
   >[!NOTE]
   >
   >Wenn ein Paket ausgegraut ist, bedeutet dies, dass es bereits installiert ist oder nicht mit Ihrer -Instanz kompatibel ist. Die Kompatibilität wird in der folgenden Tabelle beschrieben.
1. Klicken Sie auf **[!UICONTROL Weiter]** und dann auf **[!UICONTROL Starten]**, um die Package-Installation zu starten.

   Sobald die Packages installiert sind, wird in der Fortschrittsleiste **100 %** angezeigt. Folgende Meldung wird in den Installationsprotokollen angezeigt: **[!UICONTROL Die Installation der Packages wurde erfolgreich beendet]**.

1. **[!UICONTROL Schließen]** Sie das Installationsfenster.

Die Pakete sind jetzt installiert.

### Liste der vordefinierten Pakete {#list-of-standard-packages}

In der folgenden Tabelle sind alle nativen Campaign-Packages aufgeführt.

<table> 
 <thead> 
  <tr> 
   <th> Package </th> 
   <th> Beschreibung </th> 
   <th> Instanzentyp </th>
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Versand<br /> </td> 
   <td> Überwacht Sendungen und eventuell auftretende Probleme beim Versand von Nachrichten. <a href="../../delivery/using/about-delivery-monitoring.md">Weitere Informationen</a><br /> </td> 
   <td> Alle</td> 
  </tr> 
  <tr> 
   <td> Marketing-Kampagnen (Campaign)<br /> </td> 
   <td> Definiert, optimiert, führt aus und analysiert Kommunikations- und Marketing-Kampagnen. <a href="https://experienceleague.adobe.com/docs/campaign/campaign-v8/campaigns/campaigns.html?lang=de" target="_blank">Weitere Informationen</a><br /> </td> 
   <td> Marketing</td>
  </tr> 
  <tr> 
   <td> Marketing-Ressourcen (MRM)<br /> </td> 
   <td> Steuert Marketing-Aktionen im kollaborativen Modus durch Verwaltung und Verfolgung von Aufgaben, Budgets und Marketing-Ressourcen. <a href="https://experienceleague.adobe.com/docs/campaign/automation/mrm/about-marketing-resource-management.html?lang=de" target="_blank">Weitere Informationen</a> <br /> </td> 
   <td> Marketing</td> 
  </tr> 
  <tr> 
   <td> Angebotsmodul (Interaction)<br /> </td> 
   <td> Reagiert in Echtzeit während einer Interaktion mit einem bestimmten Kontakt (einem Kunden oder einer Zielgruppe), indem es ihm ein oder mehrere angepasste Angebote unterbreitet.  Optional. <a href="../../interaction/using/interaction-and-offer-management.md#packages-configuration">Weitere Informationen</a> <br /> </td> 
   <td> Alle<br /> </td> 
  </tr> 
  <tr> 
   <td> Steuerung des Angebotsmoduls mit der Ausführungsinstanz Optional.<br /> </td> 
   <td> Auf der Kontrollinstanz zu installierendes Package für das Angebotsmodul (Interaction) <a href="../../interaction/using/distributed-architectures.md#packages-configuration">Weitere Informationen</a> </td> 
   <td> Marketing<br /> </td>  
  </tr> 
  <tr> 
   <td> Angebotsmodul für Ausführungsinstanzen Optional.<br /> </td> 
   <td> Auf den Ausführungsinstanzen zu installierendes Package für das Angebotsmodul (Interaction) <a href="../../interaction/using/distributed-architectures.md">Weitere Informationen</a> </td> 
   <td> MID, <br /> </td>  
  </tr> 
  <!--tr> 
   <td> Lead Management (Leads) (deprecated)<br /> </td> 
   <td> Simplifies the process of building and maintaining the entire leads management life cycle. <br /> </td> 
   <td> Yes<br /> </td> 
   <td> Optional, <a href="https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html">Learn More</a> </td> 
  </tr--> 
  <tr> 
   <td> Soziale Netzwerke (Social Marketing) <br /> </td> 
   <td> Synchronisiert Adobe Campaign mit X (ehemals Twitter) und Facebook. <a href="../../social/using/about-social-marketing.md">Weitere Informationen</a> <br /> </td> 
   <td> Alle</td> 
  </tr> 
  <tr> 
   <td> Transaktionsnachrichten-Kontrolle (Message Center - Kontrolle)<br /> </td> 
   <td> Verwaltet Trigger-Nachrichten, die von durch Informationssysteme ausgelösten Ereignissen generiert werden. Optional. <a href="../../message-center/using/about-transactional-messaging.md">Weitere Informationen</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Ausführung von Transaktionsnachrichten (Message Center - Ausführung) <br /> </td> 
   <td> Stellt höhere Verfügbarkeit und besseres Load-Management sicher. Optional. <a href="../../message-center/using/about-transactional-messaging.md">Weitere Informationen</a><br /> </td> 
   <td> Ausführung<br /> </td>
  </tr> 
  <tr> 
   <td> LINE-Kanal<br /> </td> 
   <td> Versendet Sendungen mithilfe des LINE-Kanals mit Adobe Campaign. Optional. Transaktionsnachrichten (Message-Center-Paket) sind obligatorisch. <a href="../../delivery/using/line-channel.md">Weitere Informationen</a> <br /> </td> 
   <td> Alle<br /> </td> 
  </tr> 
  <tr> 
   <td> Briefpost-Kanal<br /> </td> 
   <td> Versendet Sendungen über den Briefpostkanal mit Adobe Campaign. Optional. <a href="../../delivery/using/about-direct-mail-channel.md">Weitere Informationen</a><br /> </td> 
   <td> Alle<br /> </td>
  </tr> 
  <tr> 
   <td> Mobile-Kanal (SMS)-<br /> </td> 
   <td> Versendet Sendungen über den Mobile-/SMS-Kanal mit Adobe Campaign. Optional. <a href="../../delivery/using/sms-channel.md">Weitere Informationen</a> <br /> </td> 
   <td> Alle<br /> </td> 
  </tr> 
   <tr> 
   <td> Telefonkanal<br /> </td> 
   <td> Versendet Sendungen über den Telefonkanal mit Adobe Campaign. Wird für Callcenter verwendet. Optional. <a href="../../delivery/using/communication-channels.md">Weitere Informationen</a> <br /> </td> 
   <td> Alle<br /> </td> 
  </tr> 
  <tr> 
   <td> Mobile-App-Kanal (Mobile App Channel)<br /> </td> 
   <td> Verwendet die Adobe Campaign-Plattform zum Senden personalisierter Benachrichtigungen über Apps an iOS- und Android-Terminals. Optional. <a href="../../delivery/using/about-mobile-app-channel.md">Weitere Informationen</a> <br /> </td> 
   <td> Alle<br /> </td> 
  </tr> 
  <tr> 
   <td> Content Manager<br /> </td> 
   <td> Erstellt wiederkehrende Newsletter oder Websites und validiert und veröffentlicht Ihre Nachrichten. <a href="../../delivery/using/about-content-management.md">Weitere Informationen</a> <br /> </td> 
   <td> </td>
  </tr> 
  <tr> 
   <td> Online-Umfragen (Survey Manager)<br /> </td> 
   <td> Erstellt und verwaltet Online-Formulare zum Hinzufügen oder Ändern von Profilinformationen, zum Abonnieren, Abmelden oder Teilnehmen an einem Gewinnspiel. Optional. <a href="../../surveys/using/about-surveys.md">Weitere Informationen</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Marketing-Analyse<br /> </td> 
   <td> Ermöglicht die Analyse und Messung von Daten, die Berechnung von Statistiken sowie die Vereinfachung und Optimierung der Berichterstellung. Außerdem können Sie Berichte erstellen und Zielpopulationen erstellen. Optional. <a href="../../reporting/using/ac-cubes.md">Weitere Informationen</a><br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Reaktionsverwaltung<br /> </td> 
   <td> Misst den Erfolg und die Rentabilität von Marketing-Kampagnen oder Angebotsvorschlägen für alle Kommunikationskanäle.  Optional. <a href="../../response/using/about-response-manager.md">Weitere Informationen</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Zugriff auf externe Daten (Federated Data Access)<br /> </td> 
   <td> Bietet die Option Federated Data Access (FDA) , um in einer oder mehreren externen Datenbanken gespeicherte Informationen zu verarbeiten, sodass Sie auf externe Daten zugreifen können, ohne die Datenstruktur in Adobe Campaign zu ändern.  Optional. <a href="https://experienceleague.adobe.com/docs/campaign/automation/workflows/advanced-management/accessing-an-external-database-fda.html" target="_blank">Weitere Informationen</a> <br /> </td> 
   <td> Alle<br /> </td> 
  </tr> 
  <tr> 
   <td> Kampagnenoptimierung (Campaign Optimization)<br /> </td> 
   <td> Steuert, filtert und überwacht den Versand von Nachrichten, damit die gesendeten Nachrichten gemäß den Kommunikationsrichtlinien des Unternehmens den Anforderungen und Erwartungen der Kunden entsprechen. Optional. <a href="https://experienceleague.adobe.com/docs/campaign/automation/campaign-optimization/campaign-typologies.html?lang=de" target="_blank">Weitere Informationen</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Zustellbarkeits-Monitoring (Email Deliverability)<br /> </td> 
   <td> Misst, wie erfolgreich Ihre Kampagnen den Posteingang Ihrer Empfänger erreichen, ohne dass sie zurückgeschickt werden oder als Spam gekennzeichnet werden. Optional. <a href="../../delivery/using/about-deliverability.md">Weitere Informationen</a> <br /> </td> 
   <td> Alle </td> 
  </tr> 
  <tr> 
   <td> Couponverwaltung<br /> </td> 
   <td> Erstellt einen Couponsatz, der künftigen Marketing-Angeboten hinzugefügt wird. Optional. <a href="../../delivery/using/personalized-coupons.md">Weitere Informationen</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Inbox Rendering (IR)<br /> </td> 
   <td> Ermöglicht die Vorschau der gesendeten Nachricht in den verschiedenen Kontexten, in denen sie empfangen werden kann, und die Überprüfung der Kompatibilität in den wichtigsten Desktops und Anwendungen. Optional. <a href="../../delivery/using/inbox-rendering.md">Weitere Informationen</a><br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Zentrales/lokales Marketing (dezentrales Marketing)<br /> </td> 
   <td> Implementiert Kooperationskampagnen zwischen zentralen Entitäten (Hauptsitz, Marketing-Abteilungen usw.) und lokalen Entitäten (Verkaufsstellen, regionale Agenturen usw.). Optional. <a href="https://experienceleague.adobe.com/docs/campaign/automation/distributed-marketing/about-distributed-marketing.html?lang=de" target="_blank">Weitere Informationen</a><br /> </td> 
   <td> Marketing </td> 
  </tr> 
  <tr> 
   <td> CRM-Connectoren<br /> </td> 
   <td> bietet verschiedene CRM-Connectoren für die Verknüpfung Ihrer Adobe Campaign-Plattform mit Ihren Drittanbietersystemen.  <a href="../../platform/using/crm-connectors.md">Weitere Informationen</a> <br /> </td> 
   <td> Marketing</td> 
  </tr> 
  <tr> 
   <td> Web Analytics-Connectoren<br /> </td> 
   <td> Ermöglicht die Interaktion von Adobe Campaign und Adobe Analytics über das Package Web-Analytics-Connectoren . Nicht kompatibel mit Transaktionsnachrichten (Message Center-Paket). <a href="../../integrations/using/gs-aa.md">Weitere Informationen</a><br /> </td> 
   <td> Marketing </td> 
  </tr> 
  <tr> 
   <td> AEM-Integration<br /> </td> 
   <td> Mit können Sie den Inhalt Ihrer E-Mail-Sendungen und Ihrer Formulare direkt in Adobe Experience Manager verwalten, um von den Inhaltsbearbeitungsfunktionen von AEM sowie den Versandkapazitäten von Adobe Campaign zu profitieren. <a href="../../integrations/using/about-adobe-experience-manager.md">Weitere Informationen</a> <br /> </td> 
   <td> Marketing</td> 
  </tr> 
  <tr> 
   <td> Integration mit freigegebenen Adobe Experience Cloud-Zielgruppen<br /> </td> 
   <td> Ermöglicht den Austausch und die Freigabe von Audiences/Segmenten mit Adobe Experience Cloud-Lösungen und -Programmen. IMS erforderlich. <a href="../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md">Weitere Informationen</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Integration mit Adobe Experience Cloud<br /> </td> 
   <td> Ermöglicht den Import und Export von Audiences/Segmenten aus verschiedenen Adobe Experience Cloud-Lösungen in Adobe Campaign. Optional. <a href="../../integrations/using/configuring-ims.md#installing-the-package">Weitere Informationen</a> </td> 
   <td> Marketing</td> 
  </tr> 
  <tr> 
   <td> Datenschutzbestimmung<br /> </td> 
   <td> Enthält zusätzliche Funktionen, die Sie bei der Einhaltung von Datenschutzbestimmungen in Campaign Classic unterstützen. <a href="https://helpx.adobe.com/de/campaign/kb/acc-privacy.html">Weitere Informationen</a> <br /> </td> 
   <td> Alle</td> 
  </tr> 
  <tr> 
   <td> Weiterleitung an Mid-Sourcing-<br /> </td> 
   <td> Beschreibt die Installation und Konfiguration eines Mid-Sourcing-Servers sowie die Bereitstellung einer Instanz, die es Dritten ermöglicht, Nachrichten im Mid-Sourcing-Modus zu senden. Optional. <a href="../../installation/using/mid-sourcing-server.md">Weitere Informationen</a> <br /> </td> 
   <td> Marketing </td> 
  </tr> 
  <tr> 
   <td> Mid-Sourcing-Plattform<br /> </td> 
   <td> Diese Konfiguration ist eine optimale Zwischenlösung zwischen einer gehosteten (ASP)-Konfiguration und der Internalisierung. Die nach außen gerichteten Ausführungskomponenten werden auf einem bei Adobe Campaign gehosteten „Mid-Sourcing“-Server ausgeführt. Optional. <a href="../../installation/using/mid-sourcing-server.md">Weitere Informationen</a> <br /> </td> 
   <td> Mid-Sourcing </td> 
  </tr> 
  <tr> 
   <td> AMP-<br /> </td> 
   <td> Ermöglicht die Verwendung des neuen interaktiven AMP für das E-Mail-Format und das Senden dynamischer E-Mails. Optional. <a href="https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/send/emails/defining-interactive-content" target="_blank">Weitere Informationen</a> <br /> </td> 
   <td> Alle </td> 
  </tr> 
  <tr> 
   <td> ACS-Connector (veraltet)<br /> </td> 
   <td> Verbindet Adobe Campaign v7 und Adobe Campaign Standard. Hierbei handelt es sich um eine integrierte Funktion in Campaign v7, mit der Daten automatisch in Campaign Standard repliziert werden, sodass die Vorzüge beider Anwendungen kombiniert werden können. Optional.<br /> </td> 
   <td> Marketing </td> 
  </tr> 
 </tbody> 
</table>

### Message-Center-Paket {#message-center-package}

Sie müssen vor der Installation von Transaktionsnachrichten (Message-Center-Paket) Versandkanäle (E-Mail, Mobile-Kanal, Mobile-App-Kanal, LINE usw.) installieren. Wenn Sie ein reines E-Mail-Message-Center-Projekt gestartet haben und anschließend einen neuen Kanal hinzufügen müssen, müssen Sie die folgenden Schritte ausführen:

1. Installieren Sie den neuen Kanal, z. B. **Mobile-Kanal** mithilfe des Package Import-Assistenten ( **[!UICONTROL Tools > Erweitert > Package importieren > Adobe Campaign-Paket]**).
1. Importieren Sie die Datei **[!UICONTROL Tools > Erweitert > Paket importieren > Datei]** und wählen Sie:

   ```
   \datakit\nms\[Your language]\package\messageCenter.xml
   ```

1. Behalten Sie unter **[!UICONTROL Zu importierender XML-Dateninhalt]** nur die Message-Center-Versandvorlage bei, die dem zugehörigen Kanal entspricht. Wenn Sie beispielsweise den Kanal **Mobile** hinzugefügt haben, behalten Sie nur das Element **entities** bei, das der Vorlage **[!UICONTROL Mobile-Transaktionsnachricht]** (smsTriggerMessage) entspricht. Wenn Sie den **Mobile-App-Kanal** hinzugefügt haben, behalten Sie nur die Vorlagen **iOS-Transaktionsnachricht** (iosTriggerMessage) und **Android-Transaktionsnachricht** (androidTriggerMessage) bei.

   ![](assets/messagecenter_install_channel.png)


### [!DNL LINE] Kanaleinrichtung{#line-package}

Um den [!DNL LINE] Kanal einzurichten, müssen Sie zunächst das [!DNL LINE] installieren.

Im Kontext einer Mid-Sourcing-Konfiguration ist Folgendes erforderlich:

* Installieren Sie das [!DNL LINE]-Paket sowohl auf der Marketing- als auch auf der MID-Instanz

* Richten Sie das externe [!DNL LINE]-Konto auf der MKT-Instanz so ein, dass es auf die MID-Instanz verweist, indem Sie den Versandmodus ändern. [Weitere Informationen](../../delivery/using/line-channel.md#configure-line-external)

* Richten Sie die [!DNL LINE] Anmeldeinformationen im externen Konto auf der MID-Instanz ein.

>[!CAUTION]
>
>Die Message-Center-Versandvorlagen für [!DNL LINE] Kanal sind nicht verfügbar, wenn die Message-Center-Pakete vor dem [!DNL LINE] installiert wurden.