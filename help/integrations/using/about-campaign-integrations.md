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
ht-degree: 100%

---

# Erste Schritte mit Adobe Campaign-Integrationen {#about-campaign-integrations}

Adobe Experience Cloud ist ein umfassender Satz marktführender integrierter Lösungen, die auf einer gemeinsamen Datenplattform mit gemeinsamen leistungsstarken Lösungen und Apps aufbauen.

Auf [dieser Seite](https://experienceleague.adobe.com/de/docs/core-services/interface/administration/integrations){_blank} erfahren Sie mehr über funktionale Integrationen, die zwischen Adobe Campaign- und Adobe Experience Cloud-Lösungen verfügbar sind.

Die vollständige Liste der Lösungen und App-Services von Adobe, die mit Adobe Campaign integriert werden können, sowie die zugehörige Dokumentation finden Sie in [diesem Abschnitt](#experience-cloud-integrations).

>[!CAUTION]
>
>Diese Integrationen erfordern die Implementierung von Adobe Identity Management System (IMS), um sich über eine Adobe ID anzumelden. [Weiterführende Informationen finden Sie auf dieser Seite](../../integrations/using/about-adobe-id.md).
>

## Verknüpfen der Lösungen {#working-with-experience-cloud-solutions}

Mehrere Lösungen können mit Adobe Experience Cloud verknüpft werden. Die **Organisation** ist die Kundenentität, mit der ein Administrator Gruppen und Benutzer konfigurieren und Single Sign-on (SSO) in Adobe Experience Cloud steuern kann. Die Organisation verhält sich wie ein Anmeldeunternehmen, das alle Experience Cloud-Produkte und -Lösungen abdeckt. Normalerweise besitzt eine Organisation den Namen ihres Unternehmens. Ein Unternehmen kann jedoch über mehrere Organisationen verfügen.

Die Verwaltung dieser Organisationen sowie die Verknüpfung von Konten mit Adobe Experience Cloud werden im [Hilfeportal von Adobe Experience Cloud](https://experienceleague.adobe.com/de/docs/core-services/interface/administration/organizations){_blank} erläutert.

## Identitäts- und Cookie-Verwaltung {#id-and-cookies}

Wenn Sie Adobe Campaign installieren oder eine bestehende Installation mit Adobe Experience Cloud integrieren, ist der [Adobe Experience Cloud Identity Service](https://experienceleague.adobe.com/de/docs/id-service/using/home){_blank} aktiviert. Dieser Dienst ersetzt das permanente Cookie, das von Adobe Campaign in erster Linie für seine Tracking-Funktionen verwendet wird.

Der ID-Dienst (Adobe Experience Cloud Identity Service) liefert eine universelle und dauerhafte ID, mit der Ihre Besucher in allen Experience Cloud-Lösungen identifiziert werden können.

Empfängern, die Trackinglogs generieren, wird eine eindeutige Visitor ID zugewiesen. Diese ID wird im Feld **[!UICONTROL Anforderer-UUID (@sourceID)]** der Tabelle **[!UICONTROL nms:trackingLogRcp]** gespeichert. **Die Tracking-Daten von Empfängern, die vor der Implementierung des Visitor ID-Diensts existierten, sind daher nicht mehr nutzbar**.

Unter der Voraussetzung, dass sie denselben CNAME aufweisen, erkennen die anderen Lösungen der Adobe Experience Cloud-Lösungen diese Kennung. [Weitere Informationen](https://experienceleague.adobe.com/de/docs/id-service/using/reference/analytics-reference/cname){_blank}.

## Experience Cloud-Integrationen {#experience-cloud-integrations}

Über die folgende Tabelle kann auf verfügbare Handbücher für die Experience Cloud-Integration zugegriffen werden.

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
   <td> Konfigurieren Sie die Integration zwischen Adobe Campaign und der Adobe Real-Time Customer Data Platform (RTCDP) zur Freigabe von Segmentdaten und zum Importieren von Zielgruppen in Adobe Campaign.<br /> <p><a href="../../integrations/using/get-started-sources-destinations.md">Erfahren Sie mehr</a> über die Integration zwischen Campaign und der Adobe Echtzeit-Kundendatenplattform.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Identity Management System (IMS) – Adobe ID</strong><br /> </td> 
   <td> Konfigurieren Sie Adobe IMS, um eine Verbindung zu Adobe Campaign mit derselben Adobe-ID herzustellen wie für die anderen Adobe Experience Cloud-Lösungen.<br /> Die Anmeldung mit einer Adobe ID ist notwendig, um gewisse mit den Adobe Experience Cloud-Integrationen einhergehende Funktionen nutzen zu können.<br /> <p><a href="../../integrations/using/about-adobe-id.md">Informationen</a> zur Implementierung von Adobe ID mit Adobe Campaign.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Experience Manager</strong><br /> </td> 
   <td> Konfigurieren Sie diese Integration, um E-Mail-Inhalte oder Formulare zu erstellen, die der Adobe Campaign-Datenbank direkt in <strong>Adobe Experience Manager</strong> zugeordnet sind.<br /> <p><a href="../../integrations/using/about-adobe-experience-manager.md">Informationen</a> zur Integration von Adobe Campaign mit Adobe Experience Manager.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Target</strong><br /> </td> 
   <td> Konfigurieren Sie diese Integration, um Bilder einzufügen, die von <strong>Adobe Target</strong> dynamisch berechnet wurden, wenn die von Adobe Campaign erstellte und versandte E-Mail geöffnet wird.<br /> <p>Erhalten Sie <a href="../../integrations/using/integrating-with-adobe-target.md">weitere Informationen</a> zur Integration von Adobe Campaign mit Adobe Target.</p><br /> </td> 
  </tr> 
  <tr> 
   <td><strong>Adobe Audience Manager</strong><br /> </td> 
   <td> Konfigurieren Sie diese Integration, um Zielgruppen zwischen den von Ihnen verwendeten Adobe Experience Cloud-Lösungen und -Anwendungen freizugeben.<br /> <p>Erhalten Sie <a href="../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md">weitere Informationen</a> zur Integration von Adobe Campaign mit Adobe Audience Manager.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Assets</strong><br /> </td> 
   <td> Konfigurieren Sie diese Integration, um Assets aus Ihrer Adobe Experience Cloud-Bibliothek in E-Mails und Landingpages einzufügen, die in Adobe Campaign erstellt wurden.<br /> <p>Erhalten Sie <a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-experience-cloud-assets">weitere Informationen</a> zu Adobe Campaign – Asset-Integration</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>AEM Assets</strong><br /> </td> 
   <td> Konfigurieren Sie diese Integration, um Assets aus Ihrer <strong>AEM Assets</strong>-Bibliothek in E-Mails und Landingpages einzufügen, die in Adobe Campaign erstellt wurden.<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-aem-assets">Informationen</a> zur Integration von Adobe Campaign mit AEM Assets.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Experience Cloud Triggers</strong><br /> </td> 
   <td> Konfigurieren Sie die Integration zwischen <strong>Adobe Experience Cloud Triggers</strong> und Adobe Campaign, um personalisierte E-Mails an Ihre Kundschaft als Reaktion auf bestimmte Verhaltensweisen zu senden, die auf Ihrer Website von Adobe Analytics verfolgt werden.<br /> <p>Erhalten Sie <a href="about-triggers.md">weitere Informationen</a> zur Integration von Adobe Campaign mit Experience Cloud Triggers.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Analytics-Connector</strong><br /> </td> 
   <td> Konfigurieren Sie diese Integration so, dass Adobe Campaign und Adobe Analytics über Segmente zum Benutzerverhalten nach einer E-Mail-Kampagne interagieren können. Umgekehrt sendet der Connector Indikatoren und Attribute von E-Mail-Kampagnen, die von Adobe Campaign bereitgestellt werden, an Adobe Analytics.<br /> <p><a href="../../integrations/using/gs-aa.md">Weitere Informationen</a> zur Connector-basierten Integration von Campaign und Analytics.</p><br /> </td> 
  </tr> 
 </tbody> 
</table>
