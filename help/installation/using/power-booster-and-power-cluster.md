---
product: campaign
title: Power Booster und Power Cluster
description: Power Booster und Power Cluster
feature: Installation, Instance Settings
badge-v7-only: label="v7" type="Informative" tooltip="Gilt nur für Campaign Classic v7"
audience: installation
content-type: reference
topic-tags: deployment-types-
exl-id: 59364cfc-9917-4057-ad5f-fbca7e261b07
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 7%

---

# Power Booster und Power Cluster{#power-booster-and-power-cluster}



## Übersicht {#overview}

Adobe Campaign bietet Ihnen zwei vorab verpackte Architekturoptionen zur Dimensionierung Ihrer Implementierung:

* **Power Booster**

  Diese Option unterstützt eine einzelne zusätzliche Ausführungsinstanz, die von der primären Adobe Campaign-Anwendungsinstanz entkoppelt ist. Dedizierte Ausführungsinstanzen können remote oder von einem Drittanbieter gehostet werden. Bei Implementierung werden E-Mail-Ausführung, -Tracking, Mirrorseiten und Bounce Messages unabhängig von den zentralen Anwendungsfunktionen verarbeitet.

* **Power Cluster**

  Diese Option unterstützt zwei bis N Clusterausführungsinstanzen, die von der primären Adobe Campaign-Anwendungsinstanz in Bezug auf eine bestimmte Anwendung entkoppelt sind. Cluster können remote, in verteilten Implementierungen und von Drittanbietern gehostet werden. Zusätzlich zu den Vorteilen der Prozessisolierung ermöglicht die Option Adobe Campaign Power Cluster Redundanz und das Ausskalieren von Strategien mithilfe von Rohstoffhardware für eine vereinfachte SLA- oder Performance-Entwicklung.

![](assets/architectural_options_diagram.png)

## Förderfähige Anträge {#eligible-applications}

Die Power Booster- und Power Cluster-Optionen können von den folgenden Anwendungen verwendet werden:

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
   <td> Mehr als 100 Millionen E-Mails pro Monat<br /> </td> 
  </tr> 
  <tr> 
   <td> Transaktionsnachrichten<br /> </td> 
   <td> 50.000 pro Stunde pro Ausführungsserver<br /> </td> 
   <td> 50.000 pro Stunde pro Ausführungsserver<br /> </td> 
   <td> 50.000 pro Stunde pro Ausführungsserver<br /> </td> 
  </tr> 
  <tr> 
   <td> Verfügbarkeit<br /> </td> 
   <td> der Primärdatenbank<br /> </td> 
   <td> 24/7 außer Wartungsfenster und Ausfallzeiten für die Ausführungsinstanz<br /> </td> 
   <td> 24/7/365 Service möglich<br /> </td> 
  </tr> 
  <tr> 
   <td> Sicherheit<br /> </td> 
   <td> Der Zugriff auf das Datamart ist potenziell über das öffentliche Internet möglich.<br /> </td> 
   <td> Datamart wird von frontalen, internetorientierten Komponenten isoliert<br /> </td> 
   <td> Datamart wird von frontalen, internetorientierten Komponenten isoliert<br /> </td> 
  </tr> 
  <tr> 
   <td> Bereitstellungsvorlage<br /> </td> 
   <td> Alle auf einer Site (kann lokal oder in der Cloud sein)<br /> </td> 
   <td> Marketing vor Ort mit Ausführung in der Cloud möglich<br /> </td> 
   <td> Marketing vor Ort mit Ausführung in der Cloud, Ausführung in verschiedenen Geos möglich<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Empfehlungen {#recommendations}

* Eine Ausführungsinstanz muss einem Dienst zugewiesen sein. Sie können kein Paket für einen Dienst installieren, für den Sie sich nicht angemeldet haben. Wenn Sie beispielsweise die **Power Booster** -Option für **Message Center** -Dienst, dürfen Sie nur die **[!UICONTROL Ausführung von Transaktionsnachrichten]** auf der dedizierten Ausführungsinstanz. Prüfen Sie diesbezüglich Ihren Lizenzvertrag.
* Da dedizierte Instanzen (oder Cluster) Adobe Campaign-Instanzen sind, sind die Empfehlungen mit denen einer Hauptinstanz identisch. Weitere Informationen hierzu finden Sie unter [dieses Dokuments](../../production/using/foreword.md).
* Wenden Sie sich an Adobe Campaign Professional Services, um die Instanz in einer Datenbank/Hardwarekomponente ordnungsgemäß zu konfigurieren.
