---
product: campaign
title: Power Booster und Power Cluster
description: Power Booster und Power Cluster
audience: installation
content-type: reference
topic-tags: deployment-types-
exl-id: 59364cfc-9917-4057-ad5f-fbca7e261b07
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 7%

---

# Power Booster und Power Cluster{#power-booster-and-power-cluster}

![](../../assets/v7-only.svg)

## Überblick {#overview}

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
   <td> Bis zu ca. 30 Millionen E-Mails pro Monat<br /> </td> 
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
   <td> Die primäre Datenbank<br /> </td> 
   <td> 24/7 außer Wartungsfenster und Ausfallzeiten für die Ausführungsinstanz<br /> </td> 
   <td> 24/7/365 Service possible<br /> </td> 
  </tr> 
  <tr> 
   <td> Sicherheit<br /> </td> 
   <td> Der Zugriff auf das Datamart ist potenziell über das öffentliche Internet möglich<br /> </td> 
   <td> Datamart wird von frontalen, internetorientierten Komponenten isoliert<br /> </td> 
   <td> Datamart wird von frontalen, internetorientierten Komponenten isoliert<br /> </td> 
  </tr> 
  <tr> 
   <td> Bereitstellungsvorlage<br /> </td> 
   <td> Alle auf einer Site (kann On-Premise oder in der Cloud sein)<br /> </td> 
   <td> Marketing vor Ort mit Ausführung in der Cloud möglich<br /> </td> 
   <td> Marketing vor Ort mit Ausführung in der Cloud; Ausführung in verschiedenen Geos möglich<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Empfehlungen {#recommendations}

* Eine Ausführungsinstanz muss einem Dienst zugewiesen sein. Sie können kein Paket für einen Dienst installieren, für den Sie sich nicht angemeldet haben. Wenn Sie beispielsweise die Option **Power Booster** für den Dienst **Message Center** abonnieren, dürfen Sie nur das Package **[!UICONTROL Ausführung von Transaktionsnachrichten]** auf der dedizierten Ausführungsinstanz installieren. Prüfen Sie diesbezüglich Ihren Lizenzvertrag.
* Da dedizierte Instanzen (oder Cluster) Adobe Campaign-Instanzen sind, sind die Empfehlungen mit denen einer Hauptinstanz identisch. Weitere Informationen hierzu finden Sie in [diesem Dokument](../../production/using/foreword.md).
* Wenden Sie sich an Adobe Campaign Professional Services, um die Instanz in einer Datenbank/Hardwarekomponente ordnungsgemäß zu konfigurieren.
