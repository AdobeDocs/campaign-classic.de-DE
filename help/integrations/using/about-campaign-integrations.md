---
solution: Campaign Classic
product: campaign
title: Über Campaign-Integrationen
description: Verwenden Sie andere Lösungen von Adobe und kombinieren Sie deren verschiedenen Funktionen mit Campaign.
audience: integrations
content-type: reference
topic-tags: campaign-integrations
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '788'
ht-degree: 71%

---


# Get started with Adobe Campaign integrations {#about-campaign-integrations}

Adobe Experience Cloud ist ein umfassendes Set hervorragender integrierter Lösungen, die auf einer gemeinsamen Datenplattform mit gemeinsamen leistungsstarken Core Services aufbauen.

Hier erfahren Sie mehr über die funktionalen Integrationen zwischen Adobe Campaign und den verschiedenen [Adobe Experience Cloud-Lösungen](https://docs.adobe.com/content/help/de-DE/core-services/interface/marketing-cloud-integrations.html) sowie [Core Services](https://docs.adobe.com/content/help/de-DE/core-services/interface/about-core-services/core-services.html). Anschließend können Sie Ihre Lösungsimplementierungen modernisieren und Experience Cloud einrichten, sodass Sie Funktionen wie beispielsweise Kundenattribute und Audiences verwenden können.

![](assets/ExCloud-solutions.png)

Die vollständige Liste der Adobe-Lösungen und Core Services, die mit Adobe Campaign integriert werden können, sowie das entsprechende Handbuch finden Sie in [diesem Abschnitt](#experience-cloud-integrations).

>[!CAUTION]
>
>Die meisten dieser Integrationen erfordern die Implementierung von Adobe Identity Management System (IMS), um sich über ein Adobe ID anzumelden. [Weiterführende Informationen finden Sie auf dieser Seite](../../integrations/using/about-adobe-id.md).


## Verknüpfen der Lösungen {#working-with-experience-cloud-solutions}

Mehrere Lösungen können mit Adobe Experience Cloud verknüpft werden. The **organization** is the customer entity that enables an administrator to configure groups and users, and to control single sign-on (SSO) in Adobe Experience Cloud. Das Unternehmen agiert wie eine Firma zur Anmeldung, die alle Experience Cloud-Produkte und -Lösungen umfasst. Normalerweise besitzt eine Organisation den Namen Ihres Unternehmens. Ein Unternehmen kann jedoch über mehrere Organisationen verfügen.

Die Verwaltung dieser Organisationen sowie die Verknüpfung von Konten mit Adobe Experience Cloud werden im [Hilfeportal von Adobe Experience Cloud](https://docs.adobe.com/content/help/de-DE/core-services/interface/manage-users-and-products/organizations.html) erläutert.

## Identitäts- und Cookie-Verwaltung {#id-and-cookies}

Wenn Sie Adobe Campaign installieren oder eine bestehende Installation mit Adobe Experience Cloud integrieren, ist der [Adobe Experience Cloud-Identitätsdienst](https://docs.adobe.com/content/help/de-DE/id-service/using/home.html) aktiviert. Dieser Dienst ersetzt das permanente Cookie, das in erster Linie für seine Tracking-Funktionen von Adobe Campaign verwendet wird.

Der Adobe Experience Cloud Identity Service (ID-Dienst) stellt eine universelle, beständige ID bereit, die Ihre Besucher in allen Lösungen des Experience Cloud identifiziert.

Empfängern, die Trackinglogs generieren, wird eine eindeutige Besucher-ID zugewiesen. Diese ID wird im Feld UUID **[!UICONTROL anfordern (@sourceID)]** der Tabelle **[!UICONTROL nms:trackingLogRcp]** gespeichert. **Die Verfolgungsdaten von Empfängern, die vor der Implementierung des Besucher-ID-Diensts existierten, sind daher nicht mehr nutzbar**.

Unter der Voraussetzung, dass sie denselben [CNAME](https://docs.adobe.com/content/help/de-DE/id-service/using/reference/analytics-reference/cname.html) aufweisen, erkennen die anderen Lösungen der Adobe-Experience-Cloud-Lösungen diese Kennung.

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
   <td> <strong>Adobe Echtzeit-Kundendatenplattform (RTCDP)</strong><br /> </td> 
   <td> The integration between Adobe Campaign and Adobe Real-time Customer Data Platform (RTCDP) allows you to share segments data and import audiences to Adobe Campaign.<br /> <p><a href="https://docs.adobe.com/content/help/de-DE/experience-platform/rtcdp/destinations/destinations-cat/adobe-destinations/adobe-campaign-destination.html">Erfahren Sie mehr</a> über die Integration zwischen Campaign und Adobe Echtzeit-Kundendatenplattform.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Identity Management System (IMS) - Adobe ID</strong><br /> </td> 
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
   <td> Durch die Integration von Adobe Campaign mit dem <strong>Triggers Core Service</strong> können Sie Ihren Kunden personalisierte E-Mails senden, die auf bestimmte Verhaltensweisen abgestimmt sind, die auf Ihrer Webseite mithilfe von Adobe Analytics ermittelt wurden.<br /> <p><a href="https://helpx.adobe.com/de/campaign/kb/triggers-and-campaign.html">Informationen</a> zur Integration von Adobe Campaign mit Experience Cloud Triggers.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Analytics – Data Connector</strong><br /> </td> 
   <td> Der <strong>Data Connector</strong> (vormals Adobe-Genesis-Connector) ermöglicht Adobe Campaign und Adobe Analytics die Interaktion über Segmente zum Nutzerverhalten nach einer E-Mail-Kampagne. Im Gegenzug werden Indikatoren und Attribute von E-Mail-Kampagnen von Adobe Campaign an Adobe Analytics – Data Connector gesendet.<br /> <p><a href="../../platform/using/adobe-analytics-data-connector.md">Informationen</a> zur Integration von Campaign mit Data Connector.</p><br /> </td> 
  </tr> 
 </tbody> 
</table>

