---
product: campaign
title: Kompatibilitätsmatrix für Campaign Classic
description: Campaign Classic – Kompatibilitätsmatrix
feature: Release Notes
role: User
level: Beginner
exl-id: b8c1f287-06f4-4c34-8cca-b0c7676abbc2
source-git-commit: b23632d0718d62d61e94e636937b93aa39bbe43f
workflow-type: ht
source-wordcount: '840'
ht-degree: 100%

---

# Kompatibilitätsmatrix {#compatibility-matrix}

Der [aktuelle Build](../../rn/using/latest-release.md) von Adobe Campaign Classic v7 ist mit allen Systemen und Tools kompatibel, die auf dieser Seite aufgelistet sind. Wenn bestimmte Versionen dieser Drittanbietersysteme und -Tools bei ihren Erstanbietern das Ende des Lebenszyklus (End of Life, EOL) erreichen, ist Adobe Campaign nicht mehr mit ihnen kompatibel. Diese Versionen werden daher mit der nächsten Produktversion aus unserer Kompatibilitätsmatrix entfernt. Um Probleme zu vermeiden, verwenden Sie ausschließlich unterstützte Versionen von Systemen, die in dieser Kompatibilitätsmatrix aufgeführt sind. Weitere Informationen über veraltete Elemente erhalten Sie auf [dieser Seite](../../rn/using/deprecated-features.md).

Sofern nicht anders angegeben, werden alle Nebenversionen unterstützt.

>[!CAUTION]
>
>Diese Matrix wird regelmäßig aktualisiert, wenn neue unterstützte Systeme und Tools hinzugefügt und veraltete Elemente entfernt werden.

## Betriebssysteme {#OperatingSystems}

Als On-Premise-/Hybrid-Kundin bzw. Kunde müssen Sie Adobe Campaign unter einem der unten aufgeführten Betriebssysteme installieren. Mehr über die Schritte bei der Installation von Campaign Classic v7 erfahren Sie auf [dieser Seite](../../installation/using/application-server.md).

<table> 
<tbody> 
<td><strong>Betriebssystem</strong></td>
<td><strong>Betriebssystemversion</strong></td>
<td><strong>Mindestens erforderliche Campaign-Version</strong></td>
<tr> 
<td>CentOs</td>
<td>
<p>7.x</p>
</td>
<td>
<p></p>
</td>
</tr>
<tr>
<td>Debian</td>
<td>
<p>11</p>
<p>10</p>
</td>
<td>
<p>v7.3</p>
<p></p>
</td>
</tr>
<tr>
<td>RHEL</td>
<td>
<p>9.x</p>
<p>8.x</p>
<p>7.x</p>
</td>
<td>
<p>v7.4</p>
<p></p>
<p></p>
</td>
</tr>
<tr>
<td>Windows Server</td>
<td>
<p>2022</p>
<p>2019</p>
<p>2016</p>
</td>
<td>
<p>v7.4</p>
<p>v7.2</p>
<p></p>
</td>
</tr>
</tbody>
</table>

>[!IMPORTANT]
>
>Wenn Sie RHEL verwenden, müssen Sie [SELinux](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#selinux) deaktivieren. Andernfalls können Ihre Programmierer und Programmiererinnen auch benutzerdefinierte SELinux-Regeln verfassen, mit denen sichergestellt werden kann, dass ein aktiviertes SELinux keine Probleme mit Campaign-Vorgängen verursacht.

## Webserver {#WebServers}

Als On-Premise-/Hybrid-Kundin bzw. Kunde müssen Sie je nach Betriebssystem Campaign in einen der unten aufgeführten Webserver integrieren. Weitere Informationen zu den Konfigurationsschritten für Webserver finden Sie auf [dieser Seite](../../installation/using/integration-into-a-web-server-for-windows.md) (für Windows) und auf [dieser Seite](../../installation/using/integration-into-a-web-server-for-linux.md) (für Linux).

<table>
<tbody>
<tr>
<td>Microsoft IIS</td>
<td>
<p>10.0 auf Windows-Server</p>
</td>
</tr>
<tr>
<td>Apache</td>
<td>
<p>2,4</p>
</td>
</tr>
</tbody>
</table>

## Tools {#Tools}

Als On-Premise-/Hybrid-Kundin bzw. Kunde müssen Sie die unten aufgeführten Tools installieren und konfigurieren. [Weitere Informationen](../../installation/using/application-server.md).

<table>
<tbody>
<td><strong>Tool</strong></td>
<td><strong>Version</strong></td>
<td><strong>Mindestens erforderliche Campaign-Version</strong></td>
<tr>
<td><p>Java Development Kit (JDK)</p>
<p>Weitere Informationen finden Sie auf <a href="../../installation/using/application-server.md#jdk" target="_blank">dieser Seite</a>.</p>
</td>
<td>
<p>11</p>
<p>9</p>
<p>8</p>
<p></p>
</td>
<td>
<p>erforderlich ab v7.4.1</p>
<p>bis v7.4.1</p>
<p>bis v7.4.1</p>
</tr>
<tr>
<td><p>Libre Office</p></td>
<td>
<p>7 (und frühere Versionen, sofern in Ihrem System vorhanden)</p>
</td>
<td>
<p></p>
</td>
</tr>
<tr>
<td><p>SpamAssassin</p></td>
<td>
<p>3.4.x</p>
</td>
<td>
<p></p>
</td>
</tbody>
</table>

## Relation Database Management Systems (RDBMS) {#RDBMSservers}

Als On-Premise-/Hybrid-Kundin bzw. Kunde müssen Sie eine der unten aufgeführten Datenbanken installieren und konfigurieren. [Weitere Informationen](../../installation/using/creating-and-configuring-the-database.md).


<table>
<tbody>
<td><strong>Datenbanksystem</strong></td>
<td><strong>Datenbankversion</strong></td>
<td><strong>Mindestens erforderliche Campaign-Version</strong></td>
<tr>
<td>Oracle</td>
<td>
<p>23c</p>
<p>19c</p>
<p>18c</p>
<p>12c</p>
<p>11g R2</p>
</td>
<td>
<p>v7.4</p>
<p></p>
<p></p>
<p></p>
<p></p>
</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>14.x</p>
<p>13.x</p>
<p>12.x</p>
<p>11.x</p>
</td>
<td>
<p>v7.3.2</p>
<p></p>
<p></p>
<p></p>
</td>
</tr>
<tr>
<td>Microsoft SQL Server</td>
<td>
<p>2022</p>
<p>2019</p>
<p>2017</p>
<p>2016</p>
<p>2014</p>
</td>
<td>
<p>v7.4</p>
<p></p>
<p></p>
<p></p>
<p></p>
</td>
</tr>
</tbody>
</table>

>[!NOTE]
>
>* RDBMS-Treiber muss der RDBMS-Serverversion entsprechen.
>
>* Microsoft SQL Server wird nicht als primäre Datenbank unterstützt, wenn der Campaign-Server auf Linux läuft. [Weitere Informationen](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#database-access-layers).
>
>* Sie können für PostgreSQL auch Amazon RDS mit den oben angegebenen Versionen verwenden.
>
>* PostgreSQL ist das RDBMS für gehostete/Managed Cloud Services-Umgebungen.


## CRM-Connectoren {#CRMconnectors}

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

Die externen Datenbanken, die mit dem [Federated Data Access-Modul](../../installation/using/about-fda.md) von Adobe Campaign kompatibel sind, werden nachfolgend gelistet. Die Kompatibilität hängt von Ihrem [Hosting-Modell](../../installation/using/hosting-models.md) ab.

**Managed Services** (gehostet), **Hybrid**- und **On-Premise**-Umgebungen können Campaign mit den folgenden externen Datenbanksystemen verbinden:

<table>
<tbody>
<td><strong>Datenbanksystem</strong></td>
<td><strong>Datenbankversion</strong></td>
<td><strong>Mindestens erforderliche Campaign-Version</strong></td>
<tr>
<td>Amazon Redshift</td>
<td><p> </p>
<td>v7.0 19.1.4</td>
</td>
</tr>
<tr>
<td>Google BigQuery</td>
<td> </td>
<td>v7.2</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>14.x</p>
<p>13.x</p>
<p>12.x</p>
<p>11.x</p>
</td>
<td>v7.0 19.1.4</td>
</tr>
<tr>
<td>Snowflake</td>
<td> </td>
<td>v7.2</td>
</tr>
<tr>
<td>Vertica Analytics</td>
<td> </td>
<td>v7.0 19.1.4 </td>
</tr>
</tbody>
</table>

Ferner kann Campaign in **Hybrid**- und **On-Premise**-Umgebungen auch mit den folgenden externen Datenbanksystemen verbunden werden. Diese Systeme sind **nicht kompatibel** mit Campaign **Managed Services** in (gehosteten) Umgebungen.

<table>
<tbody>
<td><strong>Datenbanksystem</strong></td>
<td><strong>Datenbankversion</strong></td>
<td><strong>Mindestens erforderliche Campaign-Version</strong></td>
<tr>
<td>Microsoft Azure Synapse Analytics</td>
<td> </td>
<td></td>
</tr>
<tr><td>MySQL</td>
<td>
<p>8</p>
<p>5.7</p>
</td>
<td>
<p>v7.3</p>
<p></p>
</td>
</tr>
<tr>
<td>Netezza</td>
<td>
<p>v7.2</p>
</td>
<td></td>
</tr>
<tr>
<td>Oracle</td>
<td>
<p>23c</p>
<p>19c</p>
<p>18c</p>
<p>12c</p>
<p>11g</p>
</td>
<td>
<p>v7.4</p>
<p></p>
<p></p>
<p></p>
<p></p>
</td>
</tr>
<tr>
<td>SAP HANA</td>
<td>
<p>Version 1 SPS 12</p>
</td>
<td></td>
</tr>
<tr><td>SQL Server</td>
<td>
<p>2022 (ab Campaign v7.4)</p>
<p>2019</p>
<p>2017</p>
<p>2016</p>
<p>2014</p>
<p>2012 SP1 und SP2</p>
</td>
<td></td>
</tr>
<tr>
<td>Sybase</td>
<td>
<p>IQ 16</p>
<p>ASE 15.7</p>
</td>
<td></td>
</tr>
<tr>
<td>Teradata</td>
<td>
<p>17.x</p>
<p>16.x (letzte Version)</p>
</td>
<td></td>
</tr>
<tr><td>Hadoop über HiveSQL</td>
<td>
<p>HortonWorks HDP 2.4.X, 2.5.x, 2.6.x</p>
<p>HDInsight 3.4 (HDP 2.4), 3.5 (HDP 2.5), 3.6 (HDP 2.6)</p>
<p>Cloudera CDH6.x</p>
</td>
<td></td>
</tr>
</tbody>
</table>


## Client-Konsole {#ClientOS}

Für die Verwendung der [Campaign-Client-Konsole](../../installation/using/installing-the-client-console.md) sind die folgenden Betriebssysteme und Browser **erforderlich**.

### Betriebssysteme

<table>
<tbody>
<td><strong>System</strong></td>
<td><strong>Betriebssystemversion</strong></td>
<td><strong>Mindestens erforderliche Campaign-Version</strong></td>
<tr>
<td>Microsoft Windows</td>
<td>
<p>11</p>
<p>10</p>
</td>
<td>
<p>v7.3</p>
<p></p>
<p></p>
</tr>
<tr>
<td>Microsoft Windows Server</td>
<td>
<p>2022</p>
<p>2019</p>
<p>2016</p>
</td>
<td>
<p>v7.4.1</p>
<p>v7.2.1</p>
<p></p>
</tbody>
</table>

### Microsoft WebView2 Runtime {#webview}

Die neueste Version von Microsoft Edge WebView2 Runtime ist für die Campaign-Client-Konsole erforderlich.

Microsoft Edge WebView2 kann von der [Microsoft-Entwickler-Site](https://www.adobe.com/go/acc-ms-webview2-runtime-download_de) heruntergeladen werden


## Mobile SDK {#MobileSDK}

Sie können Campaign zum [Senden von Push-Benachrichtigungen](../../delivery/using/about-mobile-app-channel.md) über das Adobe Experience Platform Mobile SDK verwenden, indem Sie die Adobe Campaign-Erweiterung in der Datenerfassungs-Benutzeroberfläche konfigurieren.

Das Campaign SDK ist ab Campaign v7.4 [veraltet](deprecated-features.md). Um einen reibungslosen Übergang für bestehende Implementierungen zum AEP Mobile SDK zu gewährleisten, können Sie es weiterhin auf den unten aufgeführten Betriebssystemen verwenden<!--, using the associated [mobile SDK](../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md)-->.


<table>
<tbody>
<tr>
<td>Google Android</td>
<td>
<p>7 bis 14</p>
<p>mit Mobile SDK Build 1.1.1.</p>
<p>Android 13 und 14 werden ab Campaign v7.4 unterstützt.</p>
<p>Android 12 wird ab Campaign v7.3 unterstützt.</p>
</td>
</tr>
<tr>
<td>Apple iOS</td>
<td>
<p>iOS 9 bis 17</p>
<p>mit Mobile SDK Build 1.0.26.</p>
<p>Apple iOS 15 wird ab Campaign v7.3 unterstützt. </p>
<p>Apple iOS 16 und 17 werden ab Campaign v7.4 unterstützt.</p>
</td>
</tr>
</tbody>
</table>

## Browser {#Browsers}

Die folgenden Browser sind in der jeweils aktuellen Version mit Campaign für den [Web-Zugriff](../../campaign/using/accessing-marketing-campaigns.md#using-the-web-interface-) kompatibel.

* Google Chrome
* Microsoft Edge
* Mozilla Firefox
* Safari



>[!MORELIKETHIS]
>
>* [Versionshinweise zu Campaign Classic](../../rn/using/latest-release.md)
>* [Campaign – allgemeine Architektur](../../installation/using/general-architecture.md)
>* [Empfehlungen zur Hardware-Dimensionierung](../../technotes/using/hardware-sizing.md)
>* [Veraltete Funktionen und Systeme](../../rn/using/deprecated-features.md)
>* [Vorgehen beim Build-Upgrade](../../production/using/build-upgrade.md)
