---
product: campaign
title: Über Campaign-Integrationen
description: Verwenden anderer Lösungen von Adobe und Kombinieren ihrer verschiedenen Funktionen mit Campaign
feature: Overview
badge-v8: label="Also applies to v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: integrations
content-type: reference
level: Intermediate, Experienced
topic-tags: campaign-integrations
exl-id: ceb584da-bc97-4b71-9499-59df5e6d10c3
TQID: 'https://experienceleague.adobe.com/PUFoWjnwax8oHM3dH-FJDH7b26p4qNBMaJfm2qWGNz0'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: d5ef99fa-df0c-4153-bf94-105ad0724167
    internal-label: Integrations
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: cbcf4d90-26be-46e2-b16a-aebc529dc41e
    internal-label: Analytics integration
  - id: df0d6518-6f49-46e2-b46e-3bcc513f553f
    internal-label: Experience Manager integration
  - id: eb007b6d-6e57-46ab-9485-3f24d6102304
    internal-label: Experience Platform integration
  - id: b1fd1501-3105-4d6b-b4d4-9af53126df75
    internal-label: Target integration
  - id: e8d937ec-9046-41b5-834b-d22a624e0d37
    internal-label: Campaign overview
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
    internal-label: Intermediate
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
topic_v2:
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
    internal-label: Administration
source-git-commit: 368b67eeb68b0944be5db674fd6a18914dea86ad
workflow-type: tm+mt
source-wordcount: '794'
ht-degree: 64%
---
# Erste Schritte mit Adobe Campaign-Integrationen {#about-campaign-integrations}

[!DNL Adobe CX Enterprise] ist ein umfassendes Set erstklassiger, integrierter Lösungen, die auf einer gemeinsamen Datenplattform mit einem gemeinsamen Satz leistungsstarker Lösungen und Apps basieren.

Weitere Informationen zu funktionalen Integrationen zwischen Adobe Campaign- und [!DNL CX Enterprise]-Lösungen finden Sie [dieser Seite](https://experienceleague.adobe.com/de/docs/core-services/interface/administration/integrations){_blank}.

Die vollständige Liste der Lösungen und App-Services von Adobe, die mit Adobe Campaign integriert werden können, sowie die zugehörige Dokumentation finden Sie in [diesem Abschnitt](#experience-cloud-integrations).

>[!NOTE]
>
>Im Zuge der Umstellung von Campaign v7 auf v8 wurde die Campaign Classic-Dokumentation optimiert und neu organisiert. Allgemeine Funktionen sind jetzt nur noch in der Dokumentation zu Campaign v8 verfügbar. Weitere Informationen zum Verbinden von Campaign mit Ihren Lösungen finden Sie in der [ zu Campaign v8](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/connect/integration){target=_blank}.
>
>[![Bild](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/connect/integration){target="_blank"}

>[!CAUTION]
>
>Diese Integrationen erfordern die Implementierung des Adobe-Identitäts-Management-Systems (IMS), um sich über eine Adobe ID anzumelden. [Weiterführende Informationen finden Sie auf dieser Seite](../../integrations/using/about-adobe-id.md).
>

## Verknüpfen der Lösungen {#working-with-experience-cloud-solutions}

Mehrere Lösungen können mit [!DNL CX Enterprise] verknüpft werden. Die **Organisation** ist die Kundenentität, mit der ein Administrator Gruppen und Benutzer konfigurieren und Single Sign-on (SSO) in [!DNL CX Enterprise] steuern kann. Die Organisation agiert als zentrale Anmeldestelle, die sämtliche [!DNL CX Enterprise] Produkte und Lösungen umfasst. Normalerweise besitzt eine Organisation den Namen ihres Unternehmens. Ein Unternehmen kann jedoch über mehrere Organisationen verfügen.

Die Verwaltung von Organisationen und die Verknüpfung von [!DNL CX Enterprise]-Konten werden im [Adobe Experience Cloud-Hilfeportal“ ](https://experienceleague.adobe.com/de/docs/core-services/interface/administration/organizations){_blank}.

## Identitäts- und Cookie-Verwaltung {#id-and-cookies}

Bei der Installation von Adobe Campaign oder der Integration einer bestehenden Installation mit [!DNL CX Enterprise] ist [Adobe Experience Cloud Identity Service](https://experienceleague.adobe.com/de/docs/id-service/using/home){_blank} aktiviert. Dieser Dienst ersetzt das permanente Cookie, das von Adobe Campaign in erster Linie für seine Tracking-Funktionen verwendet wird.

Der Adobe Experience Cloud Identity Service (ID-Dienst) bietet eine universelle, beständige ID zum Identifizieren Ihrer Besucher über alle Lösungen hinweg in der [!DNL CX Enterprise].

Empfängern, die Trackinglogs generieren, wird eine Unique-Visitor-ID zugewiesen. Diese ID wird im Feld **[!UICONTROL Anforderer-UUID (@sourceID)]** der **[!UICONTROL nms:trackingLogRcp]**-Tabelle gespeichert. **Die Tracking-Daten von Empfängern, die vor der Implementierung des Visitor ID-Diensts existierten, sind daher nicht mehr nutzbar**.

Die ID wird dann von den anderen [!DNL CX Enterprise] Lösungen mit demselben CNAME erkannt. [Weitere Informationen](https://experienceleague.adobe.com/de/docs/id-service/using/reference/analytics-reference/cname){_blank}.

## [!DNL CX Enterprise] Integrationen {#experience-cloud-integrations}

Die folgende Tabelle bietet Zugriff auf die verfügbare Dokumentation zur [!DNL CX Enterprise].

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
   <td> <strong>Adobe-Identitäts-Management-System (IMS) – Adobe ID</strong><br /> </td> 
   <td> Konfigurieren Sie Adobe IMS so, dass die Verbindung zu Adobe Campaign mit derselben Adobe ID hergestellt wird wie für die anderen CX Enterprise-Lösungen.<br /> Um bestimmte mit den CX Enterprise-Integrationen verknüpfte Funktionen nutzen zu können, muss zur Anmeldung eine Adobe ID verwendet werden.<br /> <p><a href="../../integrations/using/about-adobe-id.md">Informationen</a> zur Implementierung von Adobe ID mit Adobe Campaign.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Experience Manager</strong><br /> </td> 
   <td> Konfigurieren Sie diese Integration, um E-Mail-Inhalte oder Formulare zu erstellen, die der Adobe Campaign-Datenbank direkt in <strong>Adobe Experience Manager</strong> zugeordnet sind.<br /> <p><a href="https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/connect/ac-aem" target="_blank">Weitere Informationen</a> (Dokumentation zu Campaign v8) zur Integration von Adobe Campaign mit Adobe Experience Manager.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Target</strong><br /> </td> 
   <td> Konfigurieren Sie diese Integration, um Bilder einzufügen, die von <strong>Adobe Target</strong> dynamisch berechnet wurden, wenn die von Adobe Campaign erstellte und versandte E-Mail geöffnet wird.<br /> <p><a href="https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/connect/ac-at" target="_blank">Weitere Informationen</a> (Dokumentation zu Campaign v8) zur Integration von Adobe Campaign mit Adobe Target.</p><br /> </td> 
  </tr> 
  <tr> 
   <td><strong>Adobe Audience Manager</strong><br /> </td> 
   <td> Konfigurieren Sie diese Integration, um Zielgruppen für die von Ihnen verwendeten CX Enterprise-Lösungen und -Programme freizugeben.<br /> <p>Erhalten Sie <a href="../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md">weitere Informationen</a> zur Integration von Adobe Campaign mit Adobe Audience Manager.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Assets</strong><br /> </td> 
   <td> Konfigurieren Sie diese Integration, um Assets aus Ihrer CX Enterprise-Bibliothek in mit Adobe Campaign erstellte E-Mails und Landingpages einzufügen.<br /> <p>Erhalten Sie <a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-experience-cloud-assets">weitere Informationen</a> zu Adobe Campaign – Asset-Integration</p><br /> </td> 
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
