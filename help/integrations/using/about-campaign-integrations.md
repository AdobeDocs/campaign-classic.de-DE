---
product: campaign
title: Über Campaign-Integrationen
description: Verwenden anderer Lösungen von Adobe und Kombinieren ihrer verschiedenen Funktionen mit Campaign
feature: Overview
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
audience: integrations
content-type: reference
topic-tags: campaign-integrations
exl-id: ceb584da-bc97-4b71-9499-59df5e6d10c3
source-git-commit: 597d24fa780a324507c56c55a5309b6ee1cf46eb
workflow-type: tm+mt
source-wordcount: '709'
ht-degree: 46%

---

# Erste Schritte mit Adobe Campaign-Integrationen {#about-campaign-integrations}

Adobe Experience Cloud ist ein umfassender Satz erstklassiger integrierter Lösungen, die auf einer gemeinsamen Datenplattform mit gemeinsamen leistungsstarken Lösungen und Apps basieren.

Erfahren Sie mehr über funktionale Integrationen, die zwischen Adobe Campaign- und Adobe Experience Cloud-Lösungen verfügbar sind in [diese Seite](https://experienceleague.adobe.com/en/docs/core-services/interface/administration/integrations){_blank}.

Die vollständige Liste der Adobe-Lösungen und -Apps, die in Adobe Campaign integriert werden können, sowie die zugehörige Dokumentation finden Sie unter [diesem Abschnitt](#experience-cloud-integrations).

>[!CAUTION]
>
>Diese Integrationen erfordern die Implementierung von Adobe Identity Management System (IMS), um sich über eine Adobe ID anzumelden. [Weiterführende Informationen finden Sie auf dieser Seite](../../integrations/using/about-adobe-id.md).
>

## Verknüpfen der Lösungen {#working-with-experience-cloud-solutions}

Mehrere Lösungen können mit Adobe Experience Cloud verknüpft werden. Die **Organisation** ist die Kundenentität, mit der ein Administrator Gruppen und Benutzer konfigurieren und Single Sign-on (SSO) in Adobe Experience Cloud steuern kann. Die Organisation verhält sich wie ein Anmeldeunternehmen, das alle Experience Cloud-Produkte und -Lösungen abdeckt. Normalerweise besitzt eine Organisation den Namen ihres Unternehmens. Ein Unternehmen kann jedoch über mehrere Organisationen verfügen.

Die Verwaltung und Verknüpfung der Konten der Adobe Experience Cloud wird im Abschnitt [Adobe Experience Cloud-Hilfsportal](https://experienceleague.adobe.com/en/docs/core-services/interface/administration/organizations){_blank}.

## Identitäts- und Cookie-Verwaltung {#id-and-cookies}

Wenn Sie Adobe Campaign installieren oder eine bestehende Installation mit Adobe Experience Cloud integrieren, wird die [Adobe Experience Cloud Identity-Dienst](https://experienceleague.adobe.com/en/docs/id-service/using/home){_blank} aktiviert ist. Dieser Dienst ersetzt das permanente Cookie, das von Adobe Campaign in erster Linie für seine Tracking-Funktionen verwendet wird.

Der ID-Dienst (Adobe Experience Cloud Identity Service) liefert eine universelle und dauerhafte ID, mit der Ihre Besucher in allen Experience Cloud-Lösungen identifiziert werden können.

Empfängern, die Trackinglogs generieren, wird eine eindeutige Visitor ID zugewiesen. Diese ID wird im Feld **[!UICONTROL Anforderer-UUID (@sourceID)]** der Tabelle **[!UICONTROL nms:trackingLogRcp]** gespeichert. **Die Tracking-Daten von Empfängern, die vor der Implementierung des Visitor ID-Diensts existierten, sind daher nicht mehr nutzbar**.

Unter der Voraussetzung, dass sie denselben CNAME aufweisen, erkennen die anderen Lösungen der Adobe Experience Cloud-Lösungen diese Kennung. [Weitere Infos](https://experienceleague.adobe.com/en/docs/id-service/using/reference/analytics-reference/cname){_blank}.

## Experience Cloud-Integrationen {#experience-cloud-integrations}

Über die folgende Tabelle kann auf verfügbare Handbücher für die Experience-Cloud-Integration zugegriffen werden.

<table> 
 <thead> 
  <tr> 
   <th> Lösungen und Apps<br /> </th> 
   <th> Anwendungsbeispiele<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <strong>Adobe Echtzeit-Kundendatenplattform (RTCDP)</strong><br /> </td> 
   <td> Konfigurieren Sie die Integration zwischen Adobe Campaign und Adobe Real-time Customer Data Platform (RTCDP), um Segmentdaten freizugeben und Zielgruppen in Adobe Campaign zu importieren.<br /> <p><a href="../../integrations/using/get-started-sources-destinations.md">Erfahren Sie mehr</a> über die Integration zwischen Campaign und der Adobe Echtzeit-Kundendatenplattform.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Identity Management System (IMS) – Adobe ID</strong><br /> </td> 
   <td> Konfigurieren Sie Adobe IMS für die Verbindung mit Adobe Campaign mit derselben Adobe ID wie für die anderen Adobe Experience Cloud-Lösungen.<br /> Die Anmeldung mit einer Adobe ID ist erforderlich, um gewisse mit den Adobe Experience Cloud-Integrationen verknüpfte Funktionen nutzen zu können.<br /> <p><a href="../../integrations/using/about-adobe-id.md">Informationen</a> zur Implementierung von Adobe ID mit Adobe Campaign.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Experience Manager</strong><br /> </td> 
   <td> Konfigurieren Sie diese Integration, um E-Mail-Inhalte oder mit der Adobe Campaign-Datenbank verknüpfte Formulare direkt in zu erstellen. <strong>Adobe Experience Manager</strong>.<br /> <p><a href="../../integrations/using/about-adobe-experience-manager.md">Informationen</a> zur Integration von Adobe Campaign mit Adobe Experience Manager.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Target</strong><br /> </td> 
   <td> Konfigurieren Sie diese Integration, um dynamisch von <strong>Adobe Target</strong> wenn die von Adobe Campaign erstellte und gesendete E-Mail geöffnet wird.<br /> <p><a href="../../integrations/using/integrating-with-adobe-target.md">Informationen</a> zur Integration von Adobe Campaign mit Adobe Target.</p><br /> </td> 
  </tr> 
  <tr> 
   <td><strong>Adobe Audience Manager</strong><br /> </td> 
   <td> Konfigurieren Sie diese Integration, um Zielgruppen zwischen den von Ihnen verwendeten Adobe Experience Cloud-Lösungen und -Apps freizugeben.<br /> <p><a href="../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md">Weitere Infos</a> Informationen zu Integrationen von Adobe Campaign mit Adobe Audience Manager.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Assets</strong><br /> </td> 
   <td> Konfigurieren Sie diese Integration, um Assets aus Ihrer Adobe Experience Cloud-Bibliothek in in Adobe Campaign erstellte E-Mails und Landingpages einzufügen.<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-experience-cloud-assets">Weitere Infos</a> Über die Integration von Adobe Campaign mit Assets</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>AEM Assets</strong><br /> </td> 
   <td> Konfigurieren Sie diese Integration, um Assets aus Ihrem <strong>AEM Assets</strong> -Bibliothek in in Adobe Campaign erstellten E-Mails und Landingpages.<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-aem-assets">Informationen</a> zur Integration von Adobe Campaign mit AEM Assets.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Experience Cloud Triggers</strong><br /> </td> 
   <td> Integration konfigurieren zwischen <strong>Adobe Experience Cloud Triggers</strong> und Adobe Campaign , um Ihren Kunden personalisierte E-Mails zu senden, die auf bestimmte Verhaltensweisen abgestimmt sind, die auf Ihrer Website von Adobe Analytics beobachtet werden.<br /> <p><a href="about-triggers.md">Informationen</a> zur Integration von Adobe Campaign mit Experience Cloud Triggers.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Analytics-Connector</strong><br /> </td> 
   <td> Konfigurieren Sie diese Integration, damit Adobe Campaign und Adobe Analytics über Segmente zum Benutzerverhalten nach einer E-Mail-Kampagne interagieren können. Umgekehrt sendet der Connector Indikatoren und Attribute von E-Mail-Kampagnen, die von Adobe Campaign bereitgestellt werden, an Adobe Analytics.<br /> <p><a href="../../integrations/using/gs-aa.md">Weitere Informationen</a> zur Connector-basierten Integration von Campaign und Analytics.</p><br /> </td> 
  </tr> 
 </tbody> 
</table>
