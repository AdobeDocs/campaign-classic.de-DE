---
product: campaign
title: Kompatibilitätsmatrix für Campaign Classic
description: Campaign Classic – Kompatibilitätsmatrix
feature: Overview
role: User
level: Beginner
exl-id: b8c1f287-06f4-4c34-8cca-b0c7676abbc2
source-git-commit: 8610d29a3df1080f1622a2cb3685c0961fb40092
workflow-type: tm+mt
source-wordcount: '720'
ht-degree: 90%

---

# Kompatibilitätsmatrix{#compatibility-matrix}

![](../../assets/v7-only.svg)

In diesem Dokument werden alle Systeme und Komponenten aufgelistet, die für den [aktuellen Build](../../rn/using/latest-release.md) von **Adobe Campaign Classic v7** unterstützt werden. Produkte und Versionen, die nicht in dieser Liste enthalten sind, sind nicht mit Adobe Campaign kompatibel.

Wenn Sie ein [!DNL Gold Standard]-Benutzer sind, sehen Sie in der [[!DNL Gold Standard] -Kompatibilitätsmatrix](../../rn/using/gold-standard.md#compatibility-matrix-gs) nach.

## Wichtige Hinweise{#important-notes}

Sofern nicht anders angegeben, werden alle Nebenversionen unterstützt.

Der [aktuelle Build](../../rn/using/latest-release.md) von Adobe Campaign Classic ist mit allen Systemen und Tools kompatibel, die auf dieser Seite aufgelistet sind. Wenn bestimmte Versionen dieser Drittanbietersysteme und -Tools bei ihren Erstanbietern das Ende des Lebenszyklus (End of Life, EOL) erreichen, ist Adobe Campaign nicht mehr mit ihnen kompatibel. Diese Versionen werden daher mit der nächsten Produktversion aus unserer Kompatibilitätsmatrix entfernt. Verwenden Sie, um Probleme zu vermeiden, ausschließlich unterstützte Versionen von Systemen, die in der Kompatibilitätsmatrix aufgeführt sind.

Weitere Informationen über veraltete Elemente erhalten Sie auf [dieser Seite](../../rn/using/deprecated-features.md).

>[!CAUTION]
>
>Diese Matrix wird regelmäßig aktualisiert, wenn neue unterstützte Elemente hinzugefügt und veraltete Elemente entfernt werden.

## Betriebssysteme{#OperatingSystems}

<table> 
<tbody> 
<tr> 
<td>CentOs</td>
<td>
<p>8.x (64 Bit) </br><strong>Wichtig:</strong> CentOS Linux 8 wird am 31. Dezember 2021 das Ende der Lebensdauer (End of Life, EOL) erreichen. Weiterführende Informationen dazu finden Sie auf der Seite <a href="../../rn/using/deprecated-features.md">Eingestellte Funktionen</a>.</p>
<p>7.x (64 Bit)</p>
<p><strong>Wichtig:</strong> Wenn Sie RHEL verwenden, müssen Sie SELinux deaktivieren oder Ihre Programmierer benutzerdefinierte SELinux-Regeln schreiben lassen, um zu überprüfen, ob ein aktiviertes SELinux keine Probleme mit Campaign-Vorgängen verursacht.</p>
</td>
</tr>
<tr>
<td>Debian</td>
<td>
<p>10 (64 Bit)</p>
<p>9 (64 Bit)</p>
</td>
</tr>
<tr>
<td>RHEL</td>
<td>
<p>8.x (64 Bit)</p>
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

## Webserver{#WebServers}

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
<p>11</p>
<p>9</p>
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

## Relation Database Management Systems (RDBMS){#RDBMSservers}

<table>
<tbody>
<tr>
<td>Oracle</td>
<td>
<p>19c</p>
<p>18c</p>
<p>12c</p>
<p>11g R2</p>
</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>13.x</p>
<p>12.x</p>
<p>11.x</p>
<p>10.x</p>
<p>9.6.x</p>
<p><strong>Hinweis:</strong> Sie können für PostgreSQL auch Amazon RDS mit den oben angegebenen Versionen verwenden.</p>
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
<p><strong>Wichtig:</strong> Microsoft SQL Server wird nicht als primäre Datenbank unterstützt, wenn der Campaign-Server auf Linux läuft. <a href="../../installation/using/prerequisites-of-campaign-installation-in-linux.md#database-access-layers">Weitere Informationen</a>.</p>
</td>
</tr>
</tbody>
</table>

>[!NOTE]
>
>* RDBMS-Treiber muss der RDBMS-Server-Version entsprechen.
>
>* PostgreSQL ist das RDBMS für gehostete Umgebungen.


## CRM-Connectoren{#CRMconnectors}

Unten finden Sie die mit Adobe Campaign kompatiblen CRM-Systeme (Customer Relationship Management). [Weitere Informationen](../../platform/using/crm-connectors.md) zu CRM-Connectoren für Campaign.

<table>
<tbody>
<tr>
<td>Salesforce Connector-API</td>
<td>
<p>API-Version 49</p>
</td>
</tr>
<tr>
<td>Microsoft Dynamics-Connector</td>
<td>
<p>Web-API</p>
</td>
</tr>
</tbody>
</table>

## Federated Data Access (FDA){#FederatedDataAccessFDA}

Die folgenden externen Datenbanken sind mit dem [Federated Data Access-Modul](../../installation/using/about-fda.md) von Adobe Campaign kompatibel: Die Kompatibilität hängt von Ihrer [Hosting-Modell](../../installation/using/hosting-models.md).

**Managed Services** (gehostet), **Hybrid** und **On-Premise** Umgebungen können Campaign mit den folgenden externen Datenbanksystemen verbinden:

<table>
<tbody>
<td><strong>Datenbanksystem</strong></td>
<td><strong>Datenbankversion</strong></td>
<td><strong>Campaign-Version</strong></td>
<tr>
<tr>
<td>Snowflake</td>
<td> </td>
<td>7.2.1 Minimum</td>
</tr>
<tr>
<td>Google BigQuery</td>
<td> </td>
<td>7.2.1 Minimum</td>
</tr>
<tr>
<td>Amazon Redshift</td>
<td><p> </p>
<td>v7.0 19.1.4 Minimum</td>
</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>13.x</p>
<p>12.x</p>
<p>11.x</p>
<p>10.x</p>
<p>9.6.x</p>
<p>9.5.x</p>
<p>9.4.x</p>
</td>
<td>mindestens v7.0 19.1.4</td>
</tr>
</tbody>
</table>

Darüber hinaus **Hybrid** und **On-Premise** Umgebungen können Campaign auch mit folgenden Geräten verbinden:

<table>
<tbody>
<td><strong>Datenbanksystem</strong></td>
<td><strong>Datenbankversion</strong></td>
<td><strong>Campaign-Version</strong></td>
<tr>
<td>Vertica</td>
<td> </td>
<td>mindestens v7.0 19.1.4</td>
</tr>
<tr>
<td>Microsoft Azure Synapse Analytics</td>
<td> </td>
<td>mindestens v7.0 19.1.4</td>
</tr>
<tr>
<td>Oracle</td>
<td>
<p>19c</p>
<p>18c</p>
<p>12c</p>
<p>11g</p>
</td>
<td>Mindestens v7.0</td>
</tr>
<tr><td>SQL-Server</td>
<td>
<p>2019</p>
<p>2017</p>
<p>2016</p>
<p>2014</p>
<p>2012 SP1 und SP2</p>
</td>
<td>Mindestens v7.0</td>
</tr>
<tr><td>MySQL</td>
<td>
<p>5.7</p>
</td>
<td>Mindestens v7.0</td>
</tr>
<tr>
<td>Teradata</td>
<td>
<p>16.20</p>
<p>16</p>
<p>15.10</p>
<p>15.0</p>
</td>
<td>Mindestens v7.0</td>
</tr>
<tr>
<td>Netezza</td>
<td>
<p>7.2</p>
</td>
<td>Mindestens v7.0</td>
</tr>
<tr>
<td>Sybase</td>
<td>
<p>IQ 16</p>
<p>ASE 15.7</p>
</td>
<td>Mindestens v7.0</td>
</tr>
<tr>
<td>SAP HANA</td>
<td>
<p>Version 1 SPS 12</p>
</td>
<td>Mindestens v7.0</td>
</tr>
<tr><td>Hadoop über HiveSQL</td>
<td>
<p>HortonWorks HDP 2.4.X, 2.5.x, 2.6.x</p>
<p>HDInsight 3.4 (HDP 2.4), 3.5 (HDP 2.5), 3.6 (HDP 2.6)</p>
<p>Cloudera CDH6.x</p>
</td>
<td>Mindestens v7.0</td>
</tr>
</tbody>
</table>





## Client-Konsole {#ClientConsoleoperatingsystems}

Für die Verwendung der [Campaign-Client-Konsole](../../installation/using/installing-the-client-console.md) sind die folgenden Betriebssysteme und Browser **erforderlich**.

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

Sie können Campaign verwenden, um [Push-Benachrichtigungen](../../delivery/using/about-mobile-app-channel.md) auf den unten aufgeführten Betriebssystemen zu senden, indem Sie das zugehörige [mobile SDK](../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md) verwenden.

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

Die folgenden Browser sind mit Campaign für [Web-Zugriff](../../campaign/using/accessing-marketing-campaigns.md#using-the-web-interface-) kompatibel.

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


## Ähnliche Themen{#Morelikethis}

* [Versionshinweise zu Campaign Classic](../../rn/using/latest-release.md)
* [Campaign – allgemeine Architektur](../../installation/using/general-architecture.md)
* [Empfehlungen zur Hardware-Dimensionierung](../../technotes/using/hardware-sizing.md)
* [Veraltete Funktionen und Systeme](../../rn/using/deprecated-features.md)
* [Vorgehen beim Build-Upgrade](../../production/using/build-upgrade.md)
