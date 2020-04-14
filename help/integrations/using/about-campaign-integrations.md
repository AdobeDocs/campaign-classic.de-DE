---
title: Über Campaign-Integrationen
description: Hier erfahren Sie mehr über die funktionalen Integrationen der vorliegenden Adobe Campaign-Version mit den verschiedenen Lösungen aus Adobe Experience Cloud.
page-status-flag: never-activated
uuid: 087abdf0-b4b2-45e6-be21-b03bf85ddf83
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: campaign-integrations
discoiquuid: 0af1fd96-48ef-43c9-a03b-0f9a6e0e02fe
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0a4272ae13b469c7c17b8c3afa9748cbfbcf07ff

---


# Über Campaign-Integrationen {#about-campaign-integrations}

Adobe Experience Cloud ist ein umfassendes Set hervorragender integrierter Lösungen, die auf einer gemeinsamen Datenplattform mit gemeinsamen leistungsstarken Core Services aufbauen.

Learn about functional integrations available between Adobe Campaign and [Adobe Experience Cloud solutions](https://docs.adobe.com/content/help/en/core-services/interface/marketing-cloud-integrations.html) and [core services](https://docs.adobe.com/content/help/en/core-services/interface/about-core-services/core-services.html). Anschließend können Sie Ihre Lösungsimplementierungen modernisieren und die Experience Cloud implementieren, sodass Sie Funktionen wie Kundenattribute und Audiencen verwenden können.

The full list of Adobe solutions and core services which can be integrated with Adobe Campaign, as well as associated documentation, is available in [this section](#experience-cloud-integrations).

![](assets/ExCloud-solutions.png)


>[!CAUTION]
>
>Die meisten Integrationen erfordern die Anmeldung mit einer Adobe-ID (IMS). Weiterführende Informationen zu dieser Implementierung finden Sie auf [dieser Seite](../../integrations/using/about-adobe-id.md).
>
>Beachten Sie, dass die IMS-Implementierung ein komplexer Prozess ist, der lang sein kann. Es ist ausschließlich technischen Administratoren von Adobe vorbehalten.

## Verknüpfen von Lösungen {#working-with-experience-cloud-solutions}

In Ihrer Arbeitsumgebung verfügen Sie unter Umständen über verschiedene Lösungen der Adobe Experience Cloud. Diese sind miteinander über s. g. Organisationen verbunden. Eine **Organisation** ist die Entität, mit der ein Administrator Gruppen und Benutzer konfigurieren und Anmeldungen in der Experience Cloud steuern kann. Eine Organisation ist wie eine Unternehmensanmeldung bei allen Produkten und Lösungen, die in der Experience Cloud enthalten sind. Normalerweise besitzt eine Organisation den Namen Ihres Unternehmens. Ein Unternehmen kann jedoch über mehrere Organisationen verfügen.

Die Verwaltung dieser Organisationen sowie die Verknüpfung von Konten mit Adobe Experience Cloud werden im [Hilfeportal von Adobe Experience Cloud](https://marketing.adobe.com/resources/help/de_DE/mcloud/organizations.html) erläutert.

>[!CAUTION]
>
>Bei der Neuinstallation von Adobe Campaign oder der Integration einer bereits existierenden Installation mit Adobe Experience Cloud wird der [Experience-Cloud-ID-Service](https://marketing.adobe.com/resources/help/de_DE/mcvid/) aktiviert, welcher den von Adobe Campaign standardmäßig für Tracking-Funktionen eingesetzten Cookie ersetzt.
>
>Empfängern, die Trackinglogs generieren, wird dann eine eindeutige Besucher-ID zugewiesen. Diese ID wird im **[!UICONTROL Requester UUID (@sourceID)]** Feld der **[!UICONTROL nms:trackingLogRcp]** Tabelle gespeichert. Die Verfolgungsdaten von Empfängern, die vor der Implementierung des Besucher-ID-Diensts existierten, können daher nicht mehr verwendet werden.
>
>Unter der Voraussetzung, dass sie denselben [CNAME](https://marketing.adobe.com/resources/help/de_DE/mcvid/mcvid_cname.html) aufweisen, erkennen die anderen Lösungen der Adobe-Experience-Cloud-Lösungen diese Kennung.

## Experience Cloud-Integrationen {#experience-cloud-integrations}

Über die folgende Tabelle kann auf verfügbare Handbücher für die Experience-Cloud-Integration zugegriffen werden.

<table> 
 <thead> 
  <tr> 
   <th> Lösung &amp; Core Services<br /> </th> 
   <th> Anwendungsbeispiele<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <strong>Adobe Echtzeit-Kundendatenplattform</strong><br /> </td> 
   <td> Die Integration zwischen Adobe Campaign und Adobe Echtzeit-Kundendatenplattform ermöglicht das Freigeben von Segmentdaten und das Importieren von Audiences in Adobe Campaign.<br /> <p><a href="https://docs.adobe.com/content/help/en/experience-platform/rtcdp/destinations/destinations-cat/adobe-destinations/adobe-campaign-destination.html">Erfahren Sie mehr</a> über die Integration zwischen Campaign und Adobe Echtzeit-Kundendatenplattform.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>IMS - Adobe ID</strong><br /> </td> 
   <td> Ermöglicht die Verwendung derselben Adobe ID zur Verbindung mit Adobe Campaign und den anderen Adobe-Experience-Cloud-Lösungen.<br /> Die Anmeldung mit einer Adobe ID ist notwendig, um gewisse mit den Adobe-Experience-Cloud-Integrationen einhergehende Funktionen, insbesondere die Core Services, nutzen zu können.<br /> <p><a href="../../integrations/using/about-adobe-id.md">Informationen</a> zur Implementierung von Adobe ID mit Adobe Campaign.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Experience Manager</strong><br /> </td> 
   <td> Dient der direkten Erstellung von E-Mail-Inhalten und mit der Adobe-Campaign-Datenbank verknüpften Formularen in <strong>Adobe Experience Manager</strong>.<br /> <p><a href="../../integrations/using/about-adobe-experience-manager.md">Informationen</a> zur Integration von Adobe Campaign mit Adobe Experience Manager.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Target</strong><br /> </td> 
   <td> Dient bei der Öffnung einer mit Adobe Campaign erstellten und gesendeten E-Mail dem Einfügen von durch <strong>Adobe Target</strong> dynamisch berechneten Bildern.<br /> <p><a href="../../integrations/using/integrating-with-adobe-target.md">Informationen</a> zur Integration von Adobe Campaign mit Adobe Target.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>People core service</strong><br /> <strong>Adobe Audience Manager</strong><br /> </td> 
   <td> Ermöglicht die gemeinsame Nutzung von Audiences in den Adobe-Experience-Cloud-Lösungen und Core.<br /> <p><a href="../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md">Informationen</a> zu Integrationen von Adobe Campaign mit People Core Service und Adobe Audience Manager.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Assets Core Service</strong><br /> </td> 
   <td> Dient dem Einfügen von Assets aus Ihrer Adobe-Experience-Cloud-Bibliothek in mit Adobe Campaign erstellte E-Mails und Landingpages.<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-experience-cloud-assets">Informationen</a> zur Integration von Adobe Campaign mit Assets Core Service.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>AEM Assets</strong><br /> </td> 
   <td> Dient dem Einfügen von Assets aus Ihrer <strong>AEM-Assets</strong>-Bibliothek in mit Adobe Campaign erstellte E-Mails und Landingpages.<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-aem-assets">Informationen</a> zur Integration von Adobe Campaign mit AEM Assets.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Experience Cloud Triggers</strong><br /> </td> 
   <td> Integration between <strong>Triggers core service</strong> and Adobe Campaign allows you to send personalized emails to your customers as a reaction to specific behaviors that are tracked on your website by Adobe Analytics.<br /> <p><a href="https://helpx.adobe.com/de/campaign/kb/triggers-and-campaign.html">Informationen</a> zur Integration von Adobe Campaign mit Experience Cloud Triggers.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Analytics – Data Connector</strong><br /> </td> 
   <td> Der <strong>Data Connector</strong> (vormals Adobe-Genesis-Connector) ermöglicht Adobe Campaign und Adobe Analytics die Interaktion über Segmente zum Nutzerverhalten nach einer E-Mail-Kampagne. Im Gegenzug werden Indikatoren und Attribute von E-Mail-Kampagnen von Adobe Campaign an Adobe Analytics – Data Connector gesendet.<br /> <p><a href="../../platform/using/adobe-analytics-data-connector.md">Informationen</a> zur Integration von Campaign mit Data Connector.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Campaign Standard</strong> (Prime-Angebot)<br /> </td> 
   <td> Ermöglicht die Replikation von Daten nach <strong>Campaign Standard</strong>, wodurch die Vorzüge beider Anwendungen genutzt werden können. Campaign Classic v7 verfügt über fortschrittliche Tools zur Verwaltung der primären Marketing-Datenbank. Durch die Replikation der Daten von Campaign Classic v7 können diese in der benutzerfreundlichen Umgebung von Campaign Standard verwendet werden.<br /><p> <a href="../../integrations/using/acs-connector-principles-and-data-cycle.md">Informationen</a> zur Integration von Adobe Campaign Classic mit Adobe Campaign Standard.</p><br /></td> 
  </tr> 
 </tbody> 
</table>

