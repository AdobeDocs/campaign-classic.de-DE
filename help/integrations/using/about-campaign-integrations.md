---
product: campaign
title: Über Campaign-Integrationen
description: Verwenden anderer Lösungen von Adobe und Kombinieren ihrer verschiedenen Funktionen mit Campaign
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: integrations
content-type: reference
topic-tags: campaign-integrations
exl-id: ceb584da-bc97-4b71-9499-59df5e6d10c3
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '762'
ht-degree: 100%

---

# Erste Schritte mit Adobe Campaign-Integrationen {#about-campaign-integrations}



Adobe Experience Cloud ist ein umfassendes Set hervorragender integrierter Lösungen, die auf einer gemeinsamen Datenplattform mit gemeinsamen leistungsstarken Core Services aufbauen.

Hier erfahren Sie mehr über die funktionalen Integrationen zwischen Adobe Campaign und den verschiedenen [Adobe Experience Cloud-Lösungen](https://experienceleague.adobe.com/docs/core-services/interface/marketing-cloud-integrations.html?lang=de) sowie [Core Services](https://experienceleague.adobe.com/docs/core-services/interface/about-core-services/core-services.html?lang=de). Anschließend können Sie Ihre Lösungsimplementierungen modernisieren und Experience Cloud einrichten, sodass Sie Funktionen wie beispielsweise Kundenattribute und Audiences verwenden können.

![](assets/ExCloud-solutions.png)

Die vollständige Liste der Adobe-Lösungen und Core Services, die mit Adobe Campaign integriert werden können, sowie das entsprechende Handbuch finden Sie in [diesem Abschnitt](#experience-cloud-integrations).

>[!CAUTION]
>
>Die meisten dieser Integrationen erfordern die Implementierung von Adobe Identity Management System (IMS), um sich über eine Adobe ID anzumelden. [Weiterführende Informationen finden Sie auf dieser Seite](../../integrations/using/about-adobe-id.md).
>

## Verknüpfen der Lösungen {#working-with-experience-cloud-solutions}

Mehrere Lösungen können mit Adobe Experience Cloud verknüpft werden. Die **Organisation** ist die Kundenentität, mit der ein Administrator Gruppen und Benutzer konfigurieren und Single Sign-on (SSO) in Adobe Experience Cloud steuern kann. Die Organisation verhält sich wie ein Anmeldeunternehmen, das alle Experience Cloud-Produkte und -Lösungen abdeckt. Normalerweise besitzt eine Organisation den Namen ihres Unternehmens. Ein Unternehmen kann jedoch über mehrere Organisationen verfügen.

Die Verwaltung dieser Organisationen sowie die Verknüpfung von Konten mit Adobe Experience Cloud werden im [Hilfeportal von Adobe Experience Cloud](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/organizations.html?lang=de) erläutert.

## Identitäts- und Cookie-Verwaltung {#id-and-cookies}

Wenn Sie Adobe Campaign installieren oder eine bestehende Installation mit Adobe Experience Cloud integrieren, ist der [Adobe Experience Cloud Identity Service](https://experienceleague.adobe.com/docs/id-service/using/home.html?lang=de) aktiviert. Dieser Dienst ersetzt das permanente Cookie, das von Adobe Campaign in erster Linie für seine Tracking-Funktionen verwendet wird.

Der ID-Dienst (Adobe Experience Cloud Identity Service) liefert eine universelle und dauerhafte ID, mit der Ihre Besucher in allen Experience Cloud-Lösungen identifiziert werden können.

Empfängern, die Trackinglogs generieren, wird eine eindeutige Visitor ID zugewiesen. Diese ID wird im Feld **[!UICONTROL Anforderer-UUID (@sourceID)]** der Tabelle **[!UICONTROL nms:trackingLogRcp]** gespeichert. **Die Tracking-Daten von Empfängern, die vor der Implementierung des Visitor ID-Diensts existierten, sind daher nicht mehr nutzbar**.

Unter der Voraussetzung, dass sie denselben CNAME aufweisen, erkennen die anderen Lösungen der Adobe Experience Cloud-Lösungen diese Kennung. [Mehr dazu](https://experienceleague.adobe.com/docs/id-service/using/reference/analytics-reference/cname.html?lang=de)

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
   <td> Die Integration zwischen Adobe Campaign und Adobe Echtzeit-Kundendatenplattform (RTCDP) ermöglicht das Freigeben von Segmentdaten und das Importieren von Audiences in Adobe Campaign.<br /> <p><a href="../../integrations/using/get-started-sources-destinations.md">Erfahren Sie mehr</a> über die Integration zwischen Campaign und der Adobe Echtzeit-Kundendatenplattform.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Identity Management System (IMS) – Adobe ID</strong><br /> </td> 
   <td> Ermöglicht die Verwendung derselben Adobe ID zur Verbindung mit Adobe Campaign und den anderen Adobe Experience Cloud-Lösungen.<br /> Die Anmeldung mit einer Adobe ID ist notwendig, um gewisse mit den Adobe Experience Cloud-Integrationen einhergehende Funktionen, insbesondere die Core Services, nutzen zu können.<br /> <p><a href="../../integrations/using/about-adobe-id.md">Informationen</a> zur Implementierung von Adobe ID mit Adobe Campaign.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Experience Manager</strong><br /> </td> 
   <td> Dient der direkten Erstellung von E-Mail-Inhalten und mit der Adobe Campaign-Datenbank verknüpften Formularen in <strong>Adobe Experience Manager</strong>.<br /> <p><a href="../../integrations/using/about-adobe-experience-manager.md">Informationen</a> zur Integration von Adobe Campaign mit Adobe Experience Manager.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Target</strong><br /> </td> 
   <td> Dient bei der Öffnung einer mit Adobe Campaign erstellten und gesendeten E-Mail dem Einfügen von durch <strong>Adobe Target</strong> dynamisch berechneten Bildern.<br /> <p><a href="../../integrations/using/integrating-with-adobe-target.md">Informationen</a> zur Integration von Adobe Campaign mit Adobe Target.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>People core service</strong><br /> <strong>Adobe Audience Manager</strong><br /> </td> 
   <td> Ermöglicht die gemeinsame Nutzung von Audiences in den Adobe Experience Cloud-Lösungen und Core.<br /> <p><a href="../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md">Informationen</a> zu Integrationen von Adobe Campaign mit People Core Service und Adobe Audience Manager.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Assets Core Service</strong><br /> </td> 
   <td> Dient dem Einfügen von Assets aus Ihrer Adobe Experience Cloud-Bibliothek in mit Adobe Campaign erstellte E-Mails und Landingpages.<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-experience-cloud-assets">Informationen</a> zur Integration von Adobe Campaign mit Assets Core Service.</p><br /> </td> 
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
   <td> <strong>Adobe Analytics-Connector</strong><br /> </td> 
   <td> Der <strong>Adobe Analytics-Connector</strong> ermöglicht es Adobe Campaign, nach einer E-Mail-Kampagne mithilfe von Segmenten zum Benutzerverhalten mit Adobe Analytics zu interagieren. Umgekehrt sendet der Connector Indikatoren und Attribute von E-Mail-Kampagnen, die von Adobe Campaign bereitgestellt werden, an Adobe Analytics.<br /> <p><a href="../../platform/using/adobe-analytics-connector.md">Weitere Informationen</a> zur Connector-basierten Integration von Campaign und Analytics.</p><br /> </td> 
  </tr> 
 </tbody> 
</table>
