---
title: Stromverstärker und Stromverteiler
seo-title: Stromverstärker und Stromverteiler
description: Stromverstärker und Stromverteiler
seo-description: null
page-status-flag: never-activated
uuid: 4d23ed42-a368-4bd6-afaf-48452e253d19
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: deployment-types-
discoiquuid: 715d2b69-5b47-4890-8b7d-1dc0a0d4ead8
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: a5072ba55690d4d88c12ac7ff647f163deddbf32

---


# Stromverstärker und Stromverteiler{#power-booster-and-power-cluster}

## Übersicht {#overview}

Adobe Campaign bietet Ihnen zwei vorverpackte Architekturoptionen zur Dimensionierung Ihrer Bereitstellung:

* **Leistungsverstärker**

   Diese Option unterstützt eine einzelne zusätzliche Ausführungsinstanz, die von der primären Adobe Campaign-Anwendungsinstanz entkoppelt ist. Dedizierte Ausführungsinstanzen können remote oder von einem Drittanbieter gehostet werden. Bei Implementierung werden die E-Mail-Ausführung, Verfolgung, Spiegelseiten und Absprungmeldungen unabhängig von den zentralen Anwendungsfunktionen verarbeitet.

* **Stromverteiler**

   Diese Option unterstützt zwei bis N Clusterausführungsinstanzen, die von der primären Adobe Campaign-Anwendungsinstanz im Verhältnis zu einer bestimmten Anwendung entkoppelt sind. Cluster können remote, in verteilten Bereitstellungen und von Dritten gehostet werden. Zusätzlich zu den Vorteilen der Prozessisolierung ermöglicht die Option Adobe Campaign Power Cluster Redundanz- und Skalierungsstrategien mit Rohstoff-Hardware für eine vereinfachte Entwicklung von SLA oder Performance.

![](assets/architectural_options_diagram.png)

## Förderfähige Anträge {#eligible-applications}

Die Optionen &quot;Stromverstärker&quot;und &quot;Stromcluster&quot;können von folgenden Anwendungen verwendet werden:

* Campaign
* Leads
* Delivery
* Message Center

## Matrix von Architekturempfehlungen {#matrix-of-architectural-recommendations}

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
   <td> 24/7/365 Service möglich<br /> </td> 
  </tr> 
  <tr> 
   <td> Sicherheit<br /> </td> 
   <td> Der Zugang zum Datenverkehr ist potenziell über das öffentliche Internet möglich<br /> </td> 
   <td> Datenstrom wird von frontalen, internetorientierten Komponenten isoliert<br /> </td> 
   <td> Datenstrom wird von frontalen, internetorientierten Komponenten isoliert<br /> </td> 
  </tr> 
  <tr> 
   <td> Bereitstellungsvorlage<br /> </td> 
   <td> Alle auf einer Site (lokal oder in der Cloud)<br /> </td> 
   <td> Marketing vor Ort mit Ausführung in der Cloud möglich<br /> </td> 
   <td> Marketing vor Ort mit Ausführung in der Cloud; Ausführung in verschiedenen Gebieten möglich<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Empfehlungen {#recommendations}

* Eine Ausführungsinstanz muss einem Dienst zugewiesen sein. Sie können kein Paket für einen Dienst installieren, den Sie nicht abonniert haben. Wenn Sie beispielsweise die **Power Booster** -Option für den **Message Center** -Dienst abonnieren, dürfen Sie das Paket nur auf der dedizierten Ausführungsinstanz installieren **[!UICONTROL Execution of transactional messages]** . Prüfen Sie diesbezüglich Ihren Lizenzvertrag.
* Da dedizierte Instanzen (oder Cluster) Adobe Campaign-Instanzen sind, sind Empfehlungen dieselben wie für eine Hauptinstanz. For more on this, refer to [this document](../../production/using/foreword.md).
* Wenden Sie sich an Adobe Campaign Professional Services, um die Instanz unter dem Gesichtspunkt der Datenbank-/Hardwarekomponenten korrekt zu konfigurieren.

