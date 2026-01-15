---
product: campaign
title: Eingestellte und entfernte Funktionen von Campaign Classic
description: Auf dieser Seite finden Sie eine Liste eingestellter und entfernter Funktionen von Adobe Campaign Classic
feature: Release Notes
role: User
level: Beginner
exl-id: d60d67de-6618-4f3b-be4a-ad7633ab5645
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: ht
source-wordcount: '1658'
ht-degree: 100%

---

# Eingestellte und entfernte Funktionen {#deprecated-and-removed-features}



Adobe wertet laufend die Funktionen seiner Produkte aus, um ältere Funktionen durch neuere Alternativen zu ersetzen. Auf diese Weise kann der Kundennutzen unter sorgfältiger Berücksichtigung der Abwärtskompatibilität verbessert werden. Da Adobe Campaign Classic mit Tools von Drittanbietern arbeitet, wird die Kompatibilität regelmäßig aktualisiert, um nur unterstützte Versionen zu implementieren. Versionen, die nicht mehr mit Adobe Campaign Classic kompatibel sind, sind im Folgenden und in der [Kompatibilitätsmatrix](../../rn/using/compatibility-matrix.md) aufgeführt.

Bei der Mitteilung einer bevorstehenden Entfernung/Ersetzung von Campaign Classic-Funktionen gelten die folgenden Regeln:

* Zuerst wird die Entfernung der Funktion angekündigt. Auch wenn nicht mehr unterstützte Funktionen weiter verfügbar sein und für bestehende Benutzer unterstützt werden können, werden sie weder weiter verbessert noch dokumentiert.
* Die eingestellten Funktionen werden frühestens in der folgenden Version entfernt. Das tatsächliche Zieldatum für die Entfernung wird auf dieser Seite angegeben.

Durch dieses Vorgehen erhält der Kunde mindestens einen Versionszyklus Zeit, um seine Implementierung an eine neue Version oder einen Nachfolger einer eingestellten Funktion anzupassen, bevor sie tatsächlich entfernt wird.

>[!NOTE]
>Die Versionen und neuen Funktionen von Adobe Campaign sind in den [Versionshinweisen](../../rn/using/latest-release.md) aufgeführt.

## Eingestellte Funktionen {#deprecated-features}

In diesem Abschnitt werden Funktionen aufgeführt, die bei den aktuellen Campaign Classic-Versionen als eingestellt gekennzeichnet wurden.

Im Allgemeinen werden Funktionen, die in einer zukünftigen Version entfernt werden sollen, zuerst als eingestellt gekennzeichnet. Diese Funktionen sind für neue Campaign Classic-Kunden entweder nicht mehr verfügbar oder sollten für keine neue Implementierung mehr verwendet werden. Sie werden auch aus der Produktdokumentation entfernt.

Kunden wird empfohlen, die Nutzung der Funktionen in ihrer aktuellen Bereitstellung zu prüfen und Pläne zur Änderung ihrer Bereitstellung zu erstellen. Achten Sie auf das geplante Datum für die Entfernung, um Ihre Umgebungs- und Projektaktualisierungen zu planen.

<table> 
 <tbody> 
   <tr>
   <td><strong>Funktion</strong></td>
   <td><strong>Details</strong></td>
  </tr>
  <tr>
 <td>Campaign-SDK-Vorgängerversion (Neolane)</td>
 <td><p>Das Campaign-SDK (Neolane) für mobile Anwendungen wird jetzt nicht mehr unterstützt. Verwenden Sie stattdessen das Adobe Experience Platform Mobile SDK, indem Sie die Adobe Campaign-Erweiterung in der Datenerfassungs-Benutzeroberfläche konfigurieren. Mit dem Adobe Experience Platform Mobile SDK können Sie die Experience Cloud-Lösungen und -Dienste von Adobe in Ihren mobilen Apps nutzen. Die SDK-Konfiguration wird über die Datenerfassungs-Benutzeroberfläche verwaltet, um eine flexible Konfiguration und erweiterbare, regelbasierte Integrationen zu ermöglichen. In der <a href="https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/send/push/push-settings">Dokumentation zu Campaign v8</a> erfahren Sie, wie Sie den Mobile App-Kanal konfigurieren.</p>
<p>Geplantes Entfernungsdatum: 31. Juli 2025 </p>
</td>
</tr>
<tr>
 <td>Social-Media-Marketing mit Facebook</td>
 <td><p>Social-Media-Marketing mit Facebook wird jetzt nicht mehr unterstützt. Sie können die Integration von X (früher bekannt als Twitter) verwenden, um in den sozialen Medien zu posten, oder in Zusammenarbeit mit Adobe einen benutzerdefinierten Kanal zu erstellen.</p>
  <!--p>Target removal date: End of 2023</p-->
  </td>
</tr>
<tr>
 <td>ACS-Connector</td>
 <td><p>ACS-Connector (Prime-Angebot) wird jetzt nicht mehr unterstützt. Sie können die Export-/Importfunktionen von Campaign verwenden, um Daten in beide Produkte einzufügen und sie aus ihnen zu extrahieren.</p>
  <!--p>Target removal date: End of 2023</p-->
  </td>
</tr>
 </tbody> 
</table>

## Entfernte Funktionen {#removed-features}

In diesem Abschnitt werden Funktionen und Leistungsmerkmale aufgelistet, die aus Campaign Classic entfernt wurden.

<table> 
 <tbody>
  <tr> 
   <td><strong>Funktion</strong></td>
   <td><strong>Details</strong></td>
  <tr>  
      <tr>
  <td>Adobe Analytics Data Connector<br></td>
   <td><p>Der Adobe Analytics Data Connector wurde am 17. August 2022 entfernt. Er wurde mit Campaign-Version 21.1.3 eingestellt.</p>
   <p>Wenn Sie diesen Connector nutzen, müssen Sie Ihre Implementierung entsprechend anpassen. <a href="../../integrations/using/gs-aa.md">Weitere Informationen</a></p>
  </td>
 </tr>
    <tr>
  <td>Bericht zum technischen Zustellbarkeits-Monitoring<br></td>
   <td><p>Der Bericht zum technischen Zustellbarkeits-Monitoring ist nicht mehr verfügbar. Er wurde mit Campaign-Version 21.1.3 eingestellt.</p>
   <!--p>If needed, you can receive this report daily by email until the feature removal date. To request it, open a specific <a href="https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html">Support Case</a> and specify the name of the instance and the email address(es) to send the report to.</p--> 
  </td>
 </tr>
  <tr>
  <td>OAuth-Authentifizierung (OAuth und JWT)<br></td>
  <td><p> Die Authentifizierung für die Triggers-Integration, die ursprünglich auf dem OAuth-Authentifizierungs-Setup für den Zugriff auf die Pipeline basierte, wurde nun geändert und zu Adobe I/O verschoben. Dieser Authentifizierungsmodus wurde mit der Campaign-Version 20.3 eingestellt.<p>
  <p>Wenn Sie die Triggers-Integration verwenden, erfahren Sie <a href="../../integrations/using/about-triggers.md#implement">auf dieser Seite</a>, wie Sie Ihre Implementierung anpassen können.</p> 
  <p>Weitere Informationen zur Einstellung der OAuth-Authentifizierung finden Sie auf dieser <a href="https://github.com/AdobeDocs/analytics-1.4-apis/blob/master/docs/APIEOL.md">Seite</a>.</p> 
  <!--p><em>Target removal date: October 20, 2021. Hosted environments benefit from an extension until May 25, 2022. </em></p-->
  </td>
  </tr>
   <td>Reporting<br></td>
   <td><p>Nach dem End-of-Life von Adobe Flash Player sind der Tacho-Bericht und die Rendering-Engine für Grafiken nicht mehr verfügbar. <a href="../../reporting/using/creating-a-new-report.md">Weitere Informationen</a>   </p>
  </tr>
  <tr>  
   <td>Fax-Kanal<br></td>
   <td><p>Ab Campaign Version 21.1.3 ist der Fax-Kanal nicht mehr verfügbar. <a href="https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/create-message.html?lang=de" target="_blank">Weitere Informationen finden Sie in der Dokumentation zu Adobe Campaign v8</a></p>
  </tr>
  <tr>
  <td>Demdex-Domain<br></td>
  <td><p> Ab Campaign Version 21.1.3 wird die Demdex-Domain, die zum Importieren und Exportieren von Zielgruppen nach Adobe Experience Cloud verwendet wird, nicht mehr unterstützt. <a href="../../integrations/using/configuring-shared-audiences-integration-in-adobe-campaign.md">Weitere Informationen</a></p> 
  </td>
  </tr>
   <tr> 
   <td>Windows NT-Authentifizierung<br></td>
   <td><p>Ab Campaign-Version 20.3 wurde die Windows NT-Authentifizierung bei der Konfiguration einer neuen Datenbank mit einem Microsoft SQL Server aus den verfügbaren Authentifizierungsmechanismen entfernt. <a href="../../installation/using/creating-and-configuring-the-database.md#step-1---selecting-the-database-engine">Weitere Informationen</a></p></td>
  </tr>
   <tr> 
   <td>Dateibasierte E-Mail-Archivierung<br></td>
   <td><p>Ab Campaign-Version 20.2 ist dateibasierte E-Mail-Archivierung nicht mehr verfügbar. E-Mail-Archivierung ist jetzt über eine dedizierte BCC-E-Mail-Adresse verfügbar. <a href="../../installation/using/email-archiving.md">Weitere Informationen</a></p></td>
  </tr> 
   <tr> 
   <td>Leadmanagement</td>
   <td><p>Ab Campaign-Version 20.2 ist das Package "Leadmanagement" nicht mehr verfügbar. Ähnliche Funktionen können über andere native Workflow-Aktivitäten und Änderungen am Datenmodell implementiert werden.</p></td>
   </tr>
   <tr>
   <td>Dokumentation zu Campaign-APIs – Jsapi.chm-Datei</td>
   <td>Ab Campaign-Version 19.1 sind Campaign Classic-APIs auf einer dedizierten Seite verfügbar. Wenn Sie die Legacy-Datei "jsapi.chm" verwendet haben, sollten Sie jetzt auf <a href="https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=de">die neue Online-Version</a> verweisen.</td>
  </tr> 
  <tr> 
   <td>Kampagnenorchestrierung – Predictive Marketing</td>
   <td>Ab Campaign-Version 18.10 sind die Funktionen für Predictive Marketing nicht mehr verfügbar.</td>
  </tr> 
  <tr> 
   <td>Web-Anwendungen – Microsites</td>
   <td>Ab Campaign-Version 18.10 sind Microsites nicht mehr verfügbar. Sie können die Sicherheit erhöhen, indem Sie den Zugriff auf dedizierte Domains in Adobe Campaign-Konfigurationsdateien beschränken und in Campaign unter Verwendung von DNS-Aliassen personalisierte URLs verwenden.</td>
  </tr> 
  <tr> 
   <td>Push-Benachrichtigungen – iOS Binary Connector</td>
   <td>Auf Empfehlung von Apple hat Adobe die alte Version des iOS Binary-Connectors ab Campaign-Version 18.10 entfernt. Der leistungsfähigere und effizientere HTTP/2-basierte Connector ist bereits verfügbar.</td>
  </tr> 
  <tr> 
   <td>decryptString-API</td>
   <td><p>Ab Campaign-Version 18.6 ist die <em>decryptString</em>-API bei neuen Installationen aus Sicherheitsgründen standardmäßig nicht mehr verfügbar.</p> 
   <p>Im Zusammenhang mit einem Postupgrade auf Version 18.6 (und höher) ist diese API nicht mehr aktiv; sie wurde durch die <em>decryptPassword</em>-Funktion ersetzt. <a href="https://experienceleague.adobe.com/developer/campaign-api/api/f-decryptPassword.html?lang=de&hl=decrypt">Weitere Informationen</a></p></td>
  </tr> 
   <tr> 
   <td>Mobiler Kanal – MMS- und WAP-Push-Benachrichtigungen</td>
   <td>Ab Campaign-Version 18.4 sind die Kanäle MMS und WAP Push nicht mehr verfügbar. Als Ersatz können Sie <a href="../../delivery/using/sms-channel.md">SMS</a>- und <a href="../../delivery/using/about-mobile-app-channel.md">Push</a>-Nachrichten nutzen.</td>
  </tr> 
   <tr> 
   <td>Mobiler Kanal – LINE v1</td>
   <td>Ab Campaign-Version 18.4 ist das LINE Connect-Package nicht mehr verfügbar. Adobe empfiehlt, das neue LINE Channel-Package als Ersatz zu verwenden. <a href="../../delivery/using/line-channel.md">Weitere Informationen</a></td>
  </tr>
 </tbody> 
</table>

<!--## Deprecated compatibility {#deprecated-compatibility}

The following systems are deprecated for Campaign Classic. Please refer to the [Compatibility matrix](../../rn/using/compatibility-matrix.md) to upgrade to a newer version or move to a new system before the compatibility ends.-->

## Ende der Kompatibilität {#end-of-compatibility}

>[!CAUTION]
>
>Adobe Campaign Classic ist mit allen in der [Kompatibilitätsmatrix](../../rn/using/compatibility-matrix.md) aufgeführten Systemen und Tools kompatibel. Wenn bestimmte Versionen dieser Drittanbietersysteme und -Tools bei ihren Erstanbietern das Ende des Lebenszyklus (End of Life, EOL) erreichen, ist Adobe Campaign nicht mehr mit diesen Versionen kompatibel: Sie werden als eingestellt angekündigt und dann mit der folgenden Produktversion aus unserer Kompatibilitätsmatrix entfernt. Verwenden Sie, um Probleme zu vermeiden, ausschließlich unterstützte Versionen von Systemen, die in der Kompatibilitätsmatrix aufgeführt sind.

### Client-Konsole {#client-console-eol}

Die Client Console von Adobe Campaign Classic kann in den folgenden Systemen nicht mehr ausgeführt werden, da sie von ihrem Anbieter eingestellt wurden. Kunden, die die Campaign Client Console in einer dieser Versionen ausführen, müssen vor dem geplanten Entfernungsdatum auf die aktuelle Version aktualisieren. Siehe [Kompatibilitätsmatrix](../../rn/using/compatibility-matrix.md).

* Windows Server 2003, 2008, 2008 R2
* Windows 7, XP, Vista

>[!NOTE]
>Ab Campaign-Version 20.1 ist Campaign Classic Client Console (32 Bit) nicht mehr mit den aktuellen Campaign-Versionen kompatibel. Sie müssen Client Console mit 64 Bit verwenden.

### Betriebssysteme {#o-s-eol}

* Ab Version 7.3.1 ist Adobe Campaign nicht mehr mit Windows 8 und Windows Server 2012 kompatibel.

* Ab Version 22.1 ist Adobe Campaign nicht mehr mit CentOs 8.x (64 Bit) kompatibel. CentOS Linux 8 hat am 31. Dezember 2021 das Ende seiner Lebensdauer (EOL) erreicht. [Weitere Informationen](https://www.centos.org/centos-linux-eol/).

  Wenn Sie dieses Betriebssystem verwenden, passen Sie Ihre Implementierung entsprechend an. CentOS 7.x (64 Bit) und RHEL 8.x/7.x (64 Bit) werden weiterhin unterstützt.

* Ab Version 21.1.3 ist Adobe Campaign nicht mehr mit Debian 8 kompatibel.

* Ab Version 19.1 ist Adobe Campaign nicht mehr mit den folgenden Betriebssystemen kompatibel.

   * CentOS 6. [Weitere Informationen](https://wiki.centos.org/Download)
   * Debian 7. [Weitere Informationen](https://wiki.debian.org/DebianReleases)
   * RHEL 6.x. [Weitere Infos](https://access.redhat.com/support/policy/updates/errata)
   * Windows Server 2008. [Weitere Informationen](https://support.microsoft.com/en-us/lifecycle/search/1163)
   * SLES 11. [Weitere Informationen](https://www.suse.com/lifecycle)

### Webserver {#web-server-eol}

Ab der Frühlingsversion 19.1 ist Adobe Campaign nicht mehr mit dem folgenden Webserver kompatibel.

* Apache 2.2. [Weitere Infos](https://httpd.apache.org/)
* Microsoft IIS 7. [Weitere Informationen](https://support.microsoft.com/de-de/lifecycle/search/810)

### Tools {#tools-eol}

Ab der Frühlingsversion 19.1 ist Adobe Campaign nicht mehr mit den folgenden Tools kompatibel.

* Java JDK 7. [Weitere Informationen](https://www.oracle.com/technetwork/java/javase/eol-135779.html)
* Libre Office 3.5 / 4.3 / 5.x, außer wenn in ein anderes Tool eingebettet. [Weitere Informationen](https://wiki.documentfoundation.org/ReleasePlan/Archive#End-of-Life_Releases)

### Datenbank-Engines {#dbe-eol}

Adobe unterstützt die folgenden Datenbank-Engines nicht mehr, da sie von ihrem Anbieter eingestellt wurden. Kunden, die mit diesen Versionen arbeiten, müssen auf die aktuelle Version aktualisieren oder zu einer anderen Engine wechseln.

Konsultieren Sie die [Campaign-Kompatibilitätsmatrix](../../rn/using/compatibility-matrix.md), um sich die Liste kompatibler Versionen anzusehen.

**FEDERATED DATA ACCESS (FDA)**

Ab Version 20.2 ist Adobe Campaign nicht mehr mit den folgenden FDA-Servern kompatibel:

* DB2 UDB 10.5

Ab der Frühlingsversion 19.1 ist Adobe Campaign nicht mehr mit den folgenden FDA-Servern kompatibel:

* PostgreSQL 9.3.
* MySQL 5.5.
* DB2 9.5.
* Teradata 14 – 14.1.

Campaign Classic ist mit den folgenden Servern in Federated Data Access (FDA) nicht mehr kompatibel. Bitte aktuellere Versionen oder Systeme verwenden.

* DB2 UDB 9.5, 9.7.
* Oracle 9i, 10G R2.
* PostgreSQL-Versionen bis 9.6 haben das Ende des Lebenszyklus erreicht.
* MSSQL 2000, 2005, 2008 R2.
* MySQL 5.1.
* InfiniDB hat das Ende des Lebenszyklus erreicht.
* Teradata 13, 13.1.
* Netezza 6.02, 7.0. Netezza hat das Ende des Lebenszyklus erreicht.
* AsterData 5.0. AsterData hat das Ende des Lebenszyklus erreicht.
* Sybase IQ 15.2, 15.4, 15.5 und Sybase ASE 15.0.
* Hadoop über HiveSQL: Hadoop 2.7.3, HiveSQL 1.2.1. Adobe Campaign Classic unterstützt die aufgelisteten Versionen von Hadoop über HiveSQL durch Federated Data Access (FDA) weiterhin, aber diese Versionen werden zusammengeführt mit: HortonWorks (HDP 2.4.x, 2.5.x, 2.6.x) und HDInsight 3.4 (HDP 2.4), 3.5 (HDP 2.5), 3.6 (HDP 2.6)

**RDBMS-SERVER**

Ab der Frühlingsversion 19.1 ist Adobe Campaign nicht mehr mit den folgenden RDBMS-Servern kompatibel:

* Oracle 10GR2
* PostgreSQL 9.0 bis 9.3
* SQL Server 2005
* MySQL 5.1
* DB2 UDB 9.7

PostgreSQL-Versionen bis 9.6 haben das Ende des Lebenszyklus erreicht. Sie werden daher von Adobe Campaign nicht unterstützt.

### SMS-Connectoren {#sms-eol}

Ab Version 20.2 werden alte SMS-Connectoren eingestellt. Adobe Campaign ist nicht kompatibel mit:

* Generic SMPP (SMPP-Version 3.4 mit Unterstützung für Binärmodus)
* Sybase365 (SAP SMS 365)
* CLX Communications
* Tele2
* O2
* iOS

### CRM-Connectoren {#crm-connectors}

Ab Campaign-Version 21.1 werden folgende CRM-Connectoren in Campaign eingestellt.

* Soap-API – On-Premise: 2007, 2015, 2016
* Soap-API – Online: 2015, 2016
* Web API – Microsoft Dynamics CRM 2016
* Web API – Microsoft Dynamics CRM 2016 Update 1
* Oracle On Demand-API
