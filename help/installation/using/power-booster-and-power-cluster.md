---
product: campaign
title: Power Booster und Power Cluster
description: Power Booster und Power Cluster
feature: Installation, Instance Settings
audience: installation
content-type: reference
topic-tags: deployment-types-
exl-id: 59364cfc-9917-4057-ad5f-fbca7e261b07
TQID: https://experienceleague.adobe.com/lcr5Xfipd9cDuglWBqBsiVXJUUZqQxLEmzzZPrAEhHU
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: a075b2c1-7748-4328-b7f6-343aa314616aid: a7760dfc-5c44-4d77-bb68-c50b1e265c93
subfeature_v2: id: ac9c0a9c-8a76-4419-bd64-9c34c5782666id: fb2a841f-c522-491f-9901-a1b939d252df
topic_v2: id: d095671a-1355-40aa-8b5f-06c33c68080bid: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 416
ht-degree: 6%

---

# Power Booster und Power Cluster{#power-booster-and-power-cluster}



## Übersicht {#overview}

Adobe Campaign bietet zwei vorkonfigurierte Architekturoptionen für die Dimensionierung Ihrer Bereitstellung:

* **Power Booster**

  Diese Option bietet Unterstützung für eine einzelne zusätzliche Ausführungsinstanz, die von der primären Adobe Campaign-Anwendungsinstanz entkoppelt ist. Dedizierte Ausführungsinstanzen können remote oder von einem Dritten gehostet werden. Nach der Implementierung werden E-Mail-Ausführung, Tracking, Mirror-Seiten und Bounce-Nachrichten unabhängig von den zentralen Anwendungsfunktionen verarbeitet.

* **Power Cluster**

  Diese Option bietet Unterstützung für 2 bis N geclusterte Ausführungsinstanzen, die von der primären Adobe Campaign-Anwendungsinstanz in Bezug auf eine bestimmte Anwendung entkoppelt sind. Cluster können remote, in verteilten Bereitstellungen und von Dritten gehostet werden. Zusätzlich zu den Vorteilen der Prozessisolierung ermöglicht die Option Adobe Campaign Power Cluster Redundanz- und Scale-Out-Strategien mit Standard-Hardware für eine vereinfachte Weiterentwicklung von SLA oder Performance.

![](assets/architectural_options_diagram.png)

## Geeignete Anwendungen {#eligible-applications}

Die Optionen „Power Booster“ und „Power Cluster“ können von den folgenden Anwendungen verwendet werden:

* Campaign
* Versand
* Message Center

## Matrix von Architekturempfehlungen {#matrix-of-architectural-recommendations}

<table> 
 <tbody> 
  <tr> 
   <td> </td> 
   <td> <strong>Standardarchitektur</strong><br /> </td> 
   <td> <strong>Power Booster</strong><br /> </td> 
   <td> <strong>Power Cluster</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> E-Mail-Kampagnen und ausgehende Interaktionen<br /> </td> 
   <td> Bis zu 30 Millionen E-Mails pro Monat<br /> </td> 
   <td> 30 bis 100 Millionen E-Mails pro Monat<br /> </td> 
   <td> Über 100 Millionen E-Mails pro Monat<br /> </td> 
  </tr> 
  <tr> 
   <td> Transaktionsnachrichten<br /> </td> 
   <td> 50.000 pro Stunde und Ausführungsserver<br /> </td> 
   <td> 50.000 pro Stunde und Ausführungsserver<br /> </td> 
   <td> 50.000 pro Stunde und Ausführungsserver<br /> </td> 
  </tr> 
  <tr> 
   <td> Verfügbarkeit<br /> </td> 
   <td> Die der primären Datenbank<br /> </td> 
   <td> 24/7 außer Wartungsfenstern und Ausfallzeiten für die Ausführungsinstanz<br /> </td> 
   <td> 24/7/365 Service möglich<br /> </td> 
  </tr> 
  <tr> 
   <td> <br /> </td> 
   <td> Data Mart ist potenziell über das öffentliche Internet zugänglich<br /> </td> 
   <td> Data Mart ist von frontalen, auf das Internet ausgerichteten Komponenten isoliert<br /> </td> 
   <td> Data Mart ist von frontalen, auf das Internet ausgerichteten Komponenten isoliert<br /> </td> 
  </tr> 
  <tr> 
   <td> Bereitstellungsvorlage<br /> </td> 
   <td> Alles auf einer Site (kann On-Premise oder in der Cloud sein)<br /> </td> 
   <td> Marketing On-Premise mit Ausführung in der Cloud möglich<br /> </td> 
   <td> Marketing On-Premise mit Ausführung in der Cloud; Ausführung in verschiedenen Orten möglich<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Empfehlungen {#recommendations}

* Eine Ausführungsinstanz muss einem Service vorbehalten sein. Sie können kein Paket für einen Dienst installieren, den Sie nicht abonniert haben. Wenn Sie beispielsweise die Option **Power Booster** für den Service **Message Center** abonnieren, können Sie das Package **[!UICONTROL Ausführung von Transaktionsnachrichten]** nur auf der dedizierten Ausführungsinstanz installieren. Prüfen Sie diesbezüglich Ihren Lizenzvertrag.
* Da dedizierte Instanzen (oder Cluster) Adobe Campaign-Instanzen sind, sind die Empfehlungen dieselben wie für eine Hauptinstanz. Weiterführende Informationen hierzu finden Sie in [diesem Dokument](../../production/using/foreword.md).
* Wenden Sie sich an Adobe Campaign Professional Services, um die Instanz aus Sicht der Datenbank-/Hardwarekomponenten ordnungsgemäß zu konfigurieren.
