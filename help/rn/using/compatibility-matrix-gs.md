---
title: Gold Standard-Kompatibilitätsmatrix
description: Campaign Classic-Kompatibilitätsmatrix für die Gold Standard-Version
page-status-flag: never-activated
uuid: 269d590c-5a6d-40b9-a879-02f5033863fd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rns
content-type: reference
topic-tags: latest-release-notes
discoiquuid: 5df34f55-135a-4ea8-afc2-f9427ce5ae7p
translation-type: ht
source-git-commit: e615b2420d126cd42ed52257491282b36975f9ff
workflow-type: ht
source-wordcount: '512'
ht-degree: 100%

---


# Gold Standard-Kompatibilitätsmatrix{#compatibility-matrix-gs}

In diesem Dokument sind alle Systeme und Komponenten aufgeführt, die für Builds der **Adobe Campaign Classic Gold Standard**-Version 19.1 unterstützt werden. Produkte und Versionen, die nicht in dieser Liste enthalten sind, sind nicht mit Adobe Campaign kompatibel.

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
<td>SQL Server</td>
<td>
<p>2018</p>
<p>2018 R2</p>
<p>2017</p>
<p>2016</p>
<p>2014</p>
<p>2012 – SP1 und SP2</p>
<p>Warnung: Microsoft SQL Server wird nicht als primäre Datenbank unterstützt, wenn der Campaign-Server auf Linux läuft. <a href="https://docs.adobe.com/content/help/de-DE/campaign-classic/using/installing-campaign-classic/prerequisites-and-recommendations-/database.html#Microsoft_SQL_Server">Mehr dazu</a>.</p>
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
<td>MS Dynamics</td>
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
<tr><td>SQL Server</td>
<td>
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
<p>Version 1 SP12 oder höher</p>
</td>
</tr>
<tr><td>Hadoop über HiveSQL</td>
<td>
<p>HortonWorks HDP 2.4.X, 2.5.x, 2.6.x</p>
<p>HDInsight 3.4 (HDP 2.4), 3.5 (HDP 2.5), 3.6 (HDP 2.6)</p>
</td>
</tr>
<tr>
<td>Snowflake</td>
<td> </td>
</tr>
</tbody>
</table>

## Betriebssysteme der Clientkonsole{#ClientConsoleoperatingsystems-gs}

<table>
<tbody>
<tr>
<td>Windows Server</td>
<td>
<p>2016</p>
<p>2012</p>
</td>
</tr>
<tr>
<td>Windows</td>
<td>
<p>Sieben</p>
<p>8</p>
<p>10 (empfohlen für japanische Instanzen)</p>
</td>
</tr>
</tbody>
</table>

## Mobile SDK{#MobileSDK-gs}

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
<p>iOS 9 bis 12</p>
<p>mit Mobile SDK (Build 1.0.25), kompatibel mit 32- und 64-Bit-Versionen.</p>
</td>
</tr>
</tbody>
</table>

## Browser{#Browsers-gs}

Bei den folgenden Browsern wird die aktuelle Version unterstützt: Microsoft Edge, Mozilla Firefox, Google Chrome, Safari.

Internet Explorer 11 wird unterstützt.

## Mehr dazu{#Morelikethis-gs}

* [Versionshinweise zu Campaign Classic](../../rn/using/latest-release.md)
* [Installationsanleitung](../../installation/using/general-architecture.md)
* [Veraltete Funktionen und Systeme](../../rn/using/deprecated-features.md)
* [Vorgehen beim Build-Upgrade](https://helpx.adobe.com/de/campaign/kb/acc-build-upgrade.html)
