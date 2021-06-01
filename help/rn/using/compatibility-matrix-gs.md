---
product: campaign
title: Kompatibilitätsmatrix für Campaign [!DNL Gold Standard]
description: Campaign Classic-Kompatibilitätsmatrix für die  [!DNL Gold Standard] -Version
feature: Übersicht
role: Business Practitioner
level: Beginner
exl-id: 5c0ccaf6-7f82-4e4b-9247-261dbd0f127c
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 100%

---

# [!DNL Gold Standard]-Kompatibilitätsmatrix{#compatibility-matrix-gs}

In diesem Dokument sind alle Systeme und Komponenten aufgeführt, die für Builds der **Adobe Campaign Classic[!DNL Gold Standard]**-Version 19.1 unterstützt werden. Produkte und Versionen, die nicht in dieser Liste enthalten sind, sind nicht mit dieser Version von Adobe Campaign kompatibel.

## Wichtige Hinweise{#important-notes-gs}

Sofern nicht anders angegeben, werden alle Nebenversionen unterstützt.

Adobe Campaign Classic ist mit allen Systemen und Tools kompatibel, die auf dieser Seite aufgelistet sind. Wenn bestimmte Versionen dieser Drittanbietersysteme und -Tools bei ihren Erstanbietern das Ende des Lebenszyklus (End of Life, EOL) erreichen, ist Adobe Campaign nicht mehr mit ihnen kompatibel. Diese Versionen werden daher mit der nächsten Produktversion aus unserer Kompatibilitätsmatrix entfernt. Verwenden Sie, um Probleme zu vermeiden, ausschließlich unterstützte Versionen von Systemen, die in der Kompatibilitätsmatrix aufgeführt sind.

## Betriebssysteme{#OperatingSystems-gs}

<table> 
<tbody> 
<tr> 
<td>CentOs</td>
<td>
<p>8.x (64 Bit)</p>
<p>7.x (64 Bit)</p>
</td>
</tr>
<tr>
<td>Debian</td>
<td>
<p>9 (64 Bit)</p>
<p>8 (64 Bit)</p>
</td>
</tr>
<tr>
<td>RHEL</td>
<td>
<p>7.x (64 Bit)</p>
<p><strong>Wichtig:</strong> Wenn Sie RHEL verwenden, müssen Sie SELinux deaktivieren oder Ihre Programmierer benutzerdefinierte SELinux-Regeln schreiben lassen, um zu überprüfen, ob ein aktiviertes SELinux keine Probleme mit Campaign-Vorgängen verursacht.</p>
</td>
</tr>
<tr>
<td>Windows Server</td>
<td>
<p>2016</p>
<p>2012 R2</p>
<p>2012</p>
</td>
</tr>
</tbody>
</table>

## Webserver{#WebServers-gs}

<table>
<tbody>
<tr>
<td>Microsoft IIS</td>
<td>
<p>10.0 auf Windows-Server 2016</p>
<p>8.5 auf Windows-Server 2012 R2</p>
<p>8.0 auf Windows-Server 2012 – Windows 8</p>
</td>
</tr>
<tr>
<td>Apache</td>
<td>
<p>2.4 für RHEL 7– CentOS 7, Debian 8/9, Windows (64 Bit)</p>
<p>2.2 nur für RHEL6 – nur CentOS 6 (64 Bit)</p>
</td>
</tr>
</tbody>
</table>

## Tools{#Tools-gs}

<table>
<tbody>
<tr>
<td>Java Development Kit (JDK)</td>
<td>
<p>8</p>
<p>Die Anwendung wurde für das Java Development Kit (JDK), das von Oracle entwickelt wurde, sowie für OpenJDK genehmigt.</p>
</td>
</tr>
<tr>
<td>Libre Office</td>
<td>
<p>6 (und frühere Versionen, sofern in Ihrem System eingebettet)</p>
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

## RDBMS-Server{#RDBMSservers-gs}

>[!NOTE]
>
>RDBMS-Treiber muss der RDBMS-Server-Version entsprechen.

<table>
<tbody>
<tr>
<td>Oracle</td>
<td>
<p>18c</p>
<p>12c</p>
<p>11g R2</p>
</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>11.x</p>
<p>10.x</p>
<p>9.6.x</p>
<p>9.5.x</p>
<p>9.4.x</p>
<p>Hinweis: Sie können für PostgreSQL auch Amazon RDS mit den oben angegebenen Versionen verwenden.</p>
</td>
</tr>
<tr>
<td>SQL-Server</td>
<td>
<p>2019</p>
<p>2017</p>
<p>2016</p>
<p>2014</p>
<p>2012 – SP1 und SP2</p>
<p>Warnung: Microsoft SQL Server wird nicht als primäre Datenbank unterstützt, wenn der Campaign-Server auf Linux läuft.</p>
</td>
</tr>
<tr>
<td>DB2 UDB</td>
<td>
<p>9.7</p>
<p>Warnung: DB2 UDB ist für Neuinstallationen nicht zulässig.</p>
</td>
</tr>
</tbody>
</table>

>[!NOTE]
>
>PostgreSQL ist der Standarddatenbankserver für gehostete Umgebungen.

## CRM-Connectoren{#CRMconnectors-gs}

<table>
<tbody>
<tr>
<td>Salesforce Connector-API</td>
<td>
<p>API-Version 37</p>
</td>
</tr>
<tr>
<td>SFDC-API</td>
<td>
<p>API-Version 21</p>
<p>API-Version 15</p>
</td>
</tr>
<tr><td>Oracle On Demand-API</td>
<td>
<p>Web-Services-API v1.0</p>
</td>
</tr>
<tr>
<td>Microsoft Dynamics</td>
<td>
<p>Soap-API – On-Premise: 2007, 2015, 2016</p>
<p>Soap-API – Online: 2015, 2016</p>
<p>Web-API – On-Premise und Online: 365, 2016, 2016 Update 1</p>
</td>
</tr>
</tbody>
</table>

## Federated Data Access (FDA){#FederatedDataAccessFDA-gs}

<table>
<tbody>
<tr>
<td>Amazon Redshift</td>
<td><p> </p>
</td>
</tr>
<tr>
<td>Oracle</td>
<td>
<p>12c</p>
<p>11g</p>
</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>11.x</p>
<p>10.x</p>
<p>9.6.x</p>
<p>9.4.x</p>
</td>
</tr>
<tr><td>SQL-Server</td>
<td>
<p>2019</p>
<p>2017</p>
<p>2016</p>
<p>2014</p>
<p>2012 SP1 und SP2</p>
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
<p>16.20</p>
<p>16</p>
<p>15.10</p>
<p>15.0</p>
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
<p>Version 1 SPS 12</p>
</td>
</tr>
<tr><td>Hadoop über HiveSQL</td>
<td>
<p>HortonWorks HDP 2.4.X, 2.5.x, 2.6.x</p>
<p>HDInsight 3.4 (HDP 2.4), 3.5 (HDP 2.5), 3.6 (HDP 2.6)</p>
</td>
</tr>
</tbody>
</table>


## Client-Konsole {#ClientConsoleoperatingsystems}

:Warnung: Für die Verwendung der Campaign-Client-Konsole sind die folgenden Betriebssysteme und Browser erforderlich.

### Betriebssysteme

<table>
<tbody>
<tr>
<td>Microsoft Windows Server</td>
<td>
<p>2016</p>
<p>2012</p>
</td>
</tr>
<tr>
<td>Microsoft Windows</td>
<td>
<p>8</p>
<p>10 (empfohlen für japanische Instanzen)</p>
</td>
</tr>
</tbody>
</table>

### Browser

<table>
<tbody>
<tr>
<td>
<p>Microsoft Internet Explorer</p>
</td>
<td>
<p>11</p>
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
<p>7.x, 8.x, 9.0</p>
<p>mit Mobile SDK Build 1.0.27.</p>
</td>
</tr>
<tr>
<td>iOS</td>
<td>
<p>iOS 9 bis 14</p>
<p>mit Mobile SDK (Build 1.0.26), kompatibel mit 32- und 64-Bit-Versionen.</p>
</td>
</tr>
</tbody>
</table>

## Browser{#Browsers}

Die folgenden Browser sind mit Campaign für Web-Zugriff kompatibel.

<table>
<tbody>
<tr>
<td>
<p>Microsoft Edge</p>
</td>
<td>
<p>Neueste Version</p>
</td>
</tr>
<tr>
<td>
<p>Mozilla Firefox</p>
</td>
<td>
<p>Neueste Version</p>
</td>
</tr>
<tr>
<td>
<p>Google Chrome</p>
</td>
<td>
<p>Neueste Version</p>
</td>
</tr>
<tr>
<td>
<p>Safari</p>
</td>
<td>
<p>Neueste Version</p>
</td>
</tr>
<tr>
<td>
<p>Microsoft Internet Explorer</p>
</td>
<td>
<p>11</p>
</td>
</tr>
</tbody>
</table>

## Ähnliche Themen{#Morelikethis-gs}

* [Versionshinweise zu Campaign Classic](../../rn/using/latest-release.md)
* [Installationsanleitung](../../installation/using/general-architecture.md)
* [Veraltete Funktionen und Systeme](../../rn/using/deprecated-features.md)
* [Vorgehen beim Build-Upgrade](https://helpx.adobe.com/de/campaign/kb/acc-build-upgrade.html)
