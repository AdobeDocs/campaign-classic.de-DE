---
title: Kompatibilitätsmatrix
description: Kompatibilitätsmatrix
page-status-flag: never-activated
uuid: 269d590c-5a6d-40b9-a879-02f5033863fc
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rns
content-type: reference
topic-tags: latest-release-notes
discoiquuid: 5df34f55-135a-4ea8-afc2-f9427ce5ae7b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 5e8598fd445f6e2ebd891af1e15c07eb836cd647
workflow-type: tm+mt
source-wordcount: '621'
ht-degree: 40%

---


# Kompatibilitätsmatrix{#compatibility-matrix}

This document lists all systems and components supported for the latest build of **Adobe Campaign Classic (v6.11 and v7)**. Produkte und Versionen, die nicht in dieser Liste enthalten sind, sind nicht mit Adobe Campaign kompatibel.

## Wichtige Hinweise{#important-notes}

Diese Matrix wird regelmäßig aktualisiert, wenn neue unterstützte Elemente hinzugefügt und veraltete Elemente entfernt werden.

Sofern nicht anders angegeben, werden alle Nebenversionen unterstützt.

Adobe Campaign Classic ist mit allen auf dieser Seite aufgeführten Systemen und Tools kompatibel. Da bestimmte Versionen dieser Drittanbietersysteme und -werkzeuge mit ihren jeweiligen Erstellern das Ende der Lebensdauer erreichen, ist Adobe Campaign nicht mehr mit diesen Versionen kompatibel und wird in der darauffolgenden Produktversion aus unserer Kompatibilitätsmatrix entfernt. Verwenden Sie, um Probleme zu vermeiden, ausschließlich unterstützte Versionen von Systemen, die in der Kompatibilitätsmatrix aufgeführt sind.

Weitere Informationen zu veralteten Artikeln finden Sie auf [dieser Seite](../../rn/using/deprecated-features.md).

## Betriebssysteme{#OperatingSystems}

<table> 
<tbody> 
<tr> 
<td>CentOs</td>
<td>
<p>7.x (64 Bit)</p>
</td>
</tr>
<tr>
<td>Debian</td>
<td>
<p>8 (64 Bit)</p>
<p>9 (64 Bit)</p>
<p>10 (64 Bit)</p>
</td>
</tr>
<tr>
<td>RHEL</td>
<td>
<p>7.x (64 Bit)</p>
<p><strong>Wichtig:</strong> Wenn Sie RHEL verwenden, müssen Sie bereit sein, SELinux zu deaktivieren oder Ihre Architekten benutzerdefinierte SELinux-Regeln schreiben zu lassen, um zu überprüfen, ob ein aktiviertes SELinux keine Probleme mit Kampagnen-Operationen verursacht.</p>
</td>
</tr>
<tr>
<td>Windows Server</td>
<td>
<p>2012</p>
<p>R2 2012</p>
<p>2016</p>
</td>
</tr>
</tbody>
</table>

## Web Servers{#WebServers}

<table>
<tbody>
<tr>
<td>Microsoft IIS</td>
<td>
<p>8.0 auf Windows-Server 2012 – Windows 8</p>
<p>8.5 unter Windows Server 2012 R2</p>
<p>10.0 unter Windows Server 2016</p>
</td>
</tr>
<tr>
<td>Apache</td>
<td>
<p>2.4 für RHEL 7– CentOS 7, Debian 8/9, Windows (64 Bit)</p>
</td>
</tr>
</tbody>
</table>

## Tools{#Tools}

<table>
<tbody>
<tr>
<td>Java Development Kit (JDK)</td>
<td>
<p>8</p>
<p>9</p>
<p>Die Anwendung wurde für das Java Development Kit (JDK) von Oracle sowie für OpenJDK genehmigt.</p>
</td>
</tr>
<tr>
<td>Libre Office</td>
<td>
<p>6 (und frühere Versionen, falls in Ihr System eingebettet)</p>
</td>
</tr>
<tr>
<td>SpamAssassin</td>
<td>
<p>3.4.x</p>
</td>
</tr>
</tbody>
</table>

## RDBMS-Treiber{#RDBMSdrivers}

Die folgenden RDBMS-Treiber werden unterstützt:

* Oracle SQL*Net 11

* Oracle SQL*Net 12

* PostgreSQL (libpq)

* SQLServer

* DB2 (ODBC-Treiber)


>[!NOTE]
>
>Der RDBMS-Treiber muss mit der RDBMS-Serverversion übereinstimmen.

## RDBMS-Server{#RDBMSservers}

<table>
<tbody>
<tr>
<td>Oracle</td>
<td>
<p>11g R2</p>
<p>12c</p>
<p>18c</p>
<p>19c</p>
</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>9.4.x</p>
<p>9.5.x</p>
<p>9.6.x</p>
<p>10.x</p>
<p>11.x</p>
<p>Hinweis: Sie können auch Amazon RDS für PostgreSQL mit den oben angegebenen Versionen verwenden.</p>
</td>
</tr>
<tr>
<td>SQL Server</td>
<td>
<p>2012 – SP1 und SP2</p>
<p>2014</p>
<p>2016</p>
<p>2017</p>
<p>Warnung: Microsoft SQL Server wird nicht als primäre Datenbank unterstützt, wenn der Kampagne-Server unter Linux ausgeführt wird. Refer to the <a href="https://docs.campaign.adobe.com/doc/AC/en/INS_Prerequisites_and_recommendations__Database.html#Microsoft_SQL_Server">Installation guide</a>.</p>
</td>
</tr>
</tbody>
</table>

>[!NOTE]
>
>PostgreSQL ist der Standarddatenbankserver für gehostete Umgebungen.

## CRM-Connectoren{#CRMconnectors}

<table>
<tbody>
<tr>
<td>Salesforce Connector API</td>
<td>
<p>API-Version 37</p>
</td>
</tr>
<tr>
<td>SFDC-API</td>
<td>
<p>API-Version 15</p>
<p>API-Version 21</p>
</td>
</tr>
<tr><td>Oracle On Demand API</td>
<td>
<p>Web Services v1.0 API</p>
</td>
</tr>
<tr>
<td>MS Dynamics</td>
<td>
<p>SOAP-API - On-Premise: 2007, 2015, 2016</p>
<p>SOAP-API - Online: 2015, 2016</p>
<p>Web-API - On-Premise und Online: Aktualisierung 365, 2016, 2016 1</p>
</td>
</tr>
</tbody>
</table>

## Federated Data Access (FDA){#FederatedDataAccessFDA}

<table>
<tbody>
<tr>
<td>Microsoft Azure Synapse Analytics</td>
<td> </td>
</tr>
<tr>
<td>Amazon Redshift</td>
<td><p> </p>
</td>
</tr>
<tr>
<td>Oracle</td>
<td>
<p>11g</p>
<p>12c</p>
<p>18c</p>
</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>9.4.x</p>
<p>9.5.x</p>
<p>9.6.x</p>
<p>10.x</p>
<p>11.x</p>
</td>
</tr>
<tr><td>SQL Server</td>
<td>
<p>2012 SP1 und SP2</p>
<p>2014</p>
<p>2016</p>
<p>2017</p>
</td>
</tr>
<tr><td>MySQL</td>
<td>
<p>5.7</p>
</td>
</tr>
<tr>
<td>Teradata</td>
<td>
<p>15.0</p>
<p>15.10</p>
<p>16</p>
<p>16.20</p>
</td>
</tr>
<tr>
<td>Netezza</td>
<td>
<p>7.2</p>
</td>
</tr>
<tr>
<td>Sybase</td>
<td>
<p>IQ 16</p>
<p>ASE 15.7</p>
</td>
</tr>
<tr>
<td>SAP HANA</td>
<td>
<p>Version 1 SP12 oder höher</p>
</td>
</tr>
<tr><td>Hadoop über HiveSQL</td>
<td>
<p>HortonWorks HDP 2.4.X, 2.5.x, 2.6.x</p>
<p>HDInsight 3.4 (HDP 2.4), 3.5 (HDP 2.5), 3.6 (HDP 2.6)</p>
<p>Cloudera CDH6.x</p>
</td>
</tr>
<tr>
<td>Snowflake</td>
<td> </td>
</tr>
</tbody>
</table>

## Client Console-Betriebssysteme{#ClientConsoleoperatingsystems}

<table>
<tbody>
<tr>
<td>Windows Server</td>
<td>
<p>2012</p>
<p>2016</p>
</td>
</tr>
<tr>
<td>Windows</td>
<td>
<p>8</p>
<p>10 (empfohlen für japanische Instanzen)</p>
</td>
</tr>
</tbody>
</table>

## Mobile SDK{#MobileSDK}

<table>
<tbody>
<tr>
<td>Android</td>
<td>
<p>7.x</p>
<p>8.x</p>
<p>9.0</p>
<p>mit Mobile SDK Build 1.0.27.</p>
</td>
</tr>
<tr>
<td>iOS</td>
<td>
<p>iOS 9</p>
<p>iOS 10</p>
<p>iOS 11</p>
<p>iOS 12</p>
<p>iOS 13</p>
<p>mit SDK Build 1.0.26 für Mobilgeräte, kompatibel mit 32- und 64-Bit-Versionen.</p>
</td>
</tr>
</tbody>
</table>

## Browser{#Browsers}

Version 11 von Internet Explorer wird unterstützt.

Für die folgenden Browser wird die neueste Version unterstützt:

* Microsoft Edge

* Firefox

* Chrome

* Safari

## Experience Cloud-Integrationen{#ExperienceCloudintegrations}

For integrations with Adobe solutions, refer to this [section](https://docs.adobe.com/content/help/de-DE/campaign-classic/using/integrating-with-adobe-experience-cloud/about-campaign-integrations.html#experience-cloud-integrations).

## Mehr dazu{#Morelikethis}

* [Versionshinweise zu Campaign Classic](https://docs.adobe.com/content/help/de-DE/campaign-classic/using/release-notes/latest-release.html)
* [Installationsanleitung](https://docs.adobe.com/content/help/de-DE/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/general-architecture.html)
* [Veraltete Funktionen und Systeme](https://helpx.adobe.com/de/campaign/kb/deprecated-and-removed-features.html)
* [Vorgehen beim Build-Upgrade](https://helpx.adobe.com/de/campaign/kb/acc-build-upgrade.html)
* [Campaign Classic-Kompatibilitätsmatrix für Version 19.0](https://helpx.adobe.com/de/campaign/kb/compatibility-matrix-19-0.html)
* [Campaign Classic-Kompatibilitätsmatrix für Version 19.1](https://helpx.adobe.com/de/campaign/kb/compatibility-matrix-19-1.html)

