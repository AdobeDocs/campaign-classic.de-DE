---
solution: Campaign Classic
product: campaign
title: Power Booster und Power Cluster
description: Power Booster und Power Cluster
audience: installation
content-type: reference
topic-tags: deployment-types-
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 7%

---


# Power Booster und Power Cluster{#power-booster-and-power-cluster}

## Übersicht {#overview}

Adobe Campaign bietet Ihnen zwei vordefinierte Architekturoptionen zur Dimensionierung Ihrer Bereitstellung:

* **Leistungsverstärker**

   Diese Option unterstützt eine einzelne zusätzliche Ausführungsinstanz, die von der primären Anwendungsinstanz des Adobe Campaigns entkoppelt ist. Dedizierte Ausführungsinstanzen können remote oder von einem Drittanbieter gehostet werden. Bei Implementierung werden E-Mail-Ausführung, Verfolgung, Mirrorseiten und Absprungmeldungen unabhängig von den zentralen Anwendungsfunktionen verarbeitet.

* **Stromverteiler**

   Diese Option unterstützt 2 bis N geclusterte Ausführungsinstanzen, die von der primären Anwendungsinstanz des Adobe Campaigns in Bezug auf eine bestimmte Anwendung entkoppelt sind. Cluster können remote, in verteilten Bereitstellungen und von Dritten gehostet werden. Zusätzlich zu den Vorteilen der Prozessisolierung ermöglicht die Adobe Campaign Power Cluster-Option Redundanz- und Ausbaustrategien mithilfe von Warenhardware für eine vereinfachte SLA- oder Performance-Entwicklung.

![](assets/architectural_options_diagram.png)

## Förderfähige Anwendungen {#eligible-applications}

Die Optionen &quot;Stromverstärker&quot;und &quot;Stromcluster&quot;können von folgenden Anwendungen verwendet werden:

* Campaign
* Versand
* Message Center

## Matrix der architektonischen Empfehlungen {#matrix-of-architectural-recommendations}

<table> 
 <tbody> 
  <tr> 
   <td> </td> 
   <td> <strong>Standardarchitektur</strong><br /> </td> 
   <td> <strong>Leistungsverstärker</strong><br /> </td> 
   <td> <strong>Stromverteiler</strong><br /> </td> 
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
   <td> 24/7/365 Dienst möglich<br /> </td> 
  </tr> 
  <tr> 
   <td> Sicherheit<br /> </td> 
   <td> Data Mart ist potenziell über das öffentliche Internet zugänglich<br /> </td> 
   <td> Data Mart wird von frontalen, internetorientierten Komponenten isoliert<br /> </td> 
   <td> Data Mart wird von frontalen, internetorientierten Komponenten isoliert<br /> </td> 
  </tr> 
  <tr> 
   <td> Bereitstellungsvorlage<br /> </td> 
   <td> Alle auf einer Site (lokal oder in der Cloud)<br /> </td> 
   <td> Marketing vor Ort mit Ausführung in der Cloud möglich<br /> </td> 
   <td> Marketing vor Ort mit Ausführung in der Cloud; Ausführung in verschiedenen Geos möglich<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Empfehlungen {#recommendations}

* Eine Ausführungsinstanz muss einem Dienst gewidmet sein. Sie können kein Paket für einen Dienst installieren, den Sie nicht abonniert haben. Wenn Sie z. B. die Option **Power Booster** für den **Message Center**-Dienst abonnieren, dürfen Sie nur das **[!UICONTROL Execution of Transaktionsnachrichten]**-Paket auf der dedizierten Ausführungsinstanz installieren. Prüfen Sie diesbezüglich Ihren Lizenzvertrag.
* Da dedizierte Instanzen (oder Cluster) Adobe Campaign-Instanzen sind, sind Empfehlungen dieselben wie für eine Hauptinstanz. Weitere Informationen finden Sie in [diesem Dokument](../../production/using/foreword.md).
* Wenden Sie sich an Adobe Campaign Professional Services, um die Instanz über einen Datenbankkomponenten-/Hardwarekomponenten-Punkt der Ansicht korrekt zu konfigurieren.

