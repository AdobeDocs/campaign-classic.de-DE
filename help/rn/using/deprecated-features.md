---
product: campaign
title: Eingestellte und entfernte Funktionen von Campaign Classic
description: Auf dieser Seite finden Sie eine Liste eingestellter und entfernter Funktionen von Adobe Campaign Classic
feature: Übersicht
role: User
level: Beginner
exl-id: d60d67de-6618-4f3b-be4a-ad7633ab5645
source-git-commit: 6c28e6cd78ce7a8ee5c0dc7e671de780787b9f57
workflow-type: tm+mt
source-wordcount: '1634'
ht-degree: 99%

---

# Eingestellte und entfernte Funktionen {#deprecated-and-removed-features}

Adobe evaluiert laufend die Funktionen seiner Produkte, um ältere Funktionen durch neuere Alternativen zu ersetzen. Auf diese Weise kann der Kundennutzen unter sorgfältiger Berücksichtigung der Abwärtskompatibilität verbessert werden. Da Adobe Campaign Classic mit Tools von Drittanbietern arbeitet, wird die Kompatibilität regelmäßig aktualisiert, um nur unterstützte Versionen zu implementieren. Versionen, die nicht mehr mit Adobe Campaign Classic kompatibel sind, sind im Folgenden und in der [Kompatibilitätsmatrix](../../rn/using/compatibility-matrix.md) aufgeführt.

Bei der Mitteilung einer bevorstehenden Entfernung/Ersetzung von Campaign Classic-Funktionen gelten die folgenden Regeln:

* Zuerst wird die Entfernung der Funktion angekündigt. Auch wenn nicht mehr unterstützte Funktionen weiter verfügbar sein und für bestehende Benutzer unterstützt werden können, werden sie weder weiter verbessert noch dokumentiert.
* Die eingestellten Funktionen werden frühestens in der folgenden Version entfernt. Das tatsächliche Zieldatum für die Entfernung wird auf dieser Seite angegeben.

Durch dieses Vorgehen erhält der Kunde mindestens einen Versionszyklus Zeit, um seine Implementierung an eine neue Version oder einen Nachfolger einer eingestellten Funktion anzupassen, bevor sie tatsächlich entfernt wird.

>[!NOTE]
>Die Versionen und neuen Funktionen von Adobe Campaign sind in den [Versionshinweisen](../../rn/using/latest-release.md) aufgeführt.

## Eingestellte Funktionen {#deprecated-features}

In diesem Abschnitt werden Funktionen aufgeführt, die bei den aktuellen Campaign Classic-Versionen als eingestellt gekennzeichnet wurden.

Im Allgemeinen werden Funktionen, die in einer zukünftigen Version entfernt werden sollen, zuerst als eingestellt gekennzeichnet. Diese Funktionen sind für neue Campaign Standard-Kunden entweder nicht mehr verfügbar oder sollten für keine neue Implementierung mehr verwendet werden. Sie werden auch aus der Produktdokumentation entfernt.

Kunden wird empfohlen, die Nutzung der Funktionen in ihrer aktuellen Implementierung zu prüfen und Pläne zur Änderung ihrer Implementierung zu erstellen. Achten Sie auf das geplante Datum für die Entfernung, um Ihre Umgebungs- und Projektaktualisierungen zu planen.

<table> 
 <tbody> 
   <tr>
   <td><strong>Funktion</strong></td>
   <td><strong>Ersatz</strong></td>
  </tr>
    <tr>
  <td>Adobe Analytics Data Connector<br></td>
   <td><p>Ab Campaign Version 21.1.3 wird der Adobe Analytics Data Connector nicht mehr unterstützt.</p>
   <p>Wenn Sie diesen Connector nutzen, müssen Sie Ihre Implementierung entsprechend anpassen. <a href="../../platform/using/adobe-analytics-connector.md">Mehr dazu</a></p>
  <p><em>Geplantes Entfernungsdatum: 1. März 2022</em></p>
  </td>
 </tr>
    <tr>
  <td>Bericht zum technischen Zustellbarkeits-Monitoring<br></td>
   <td><p>Ab Campaign-Version 21.1 wird der Bericht zum technischen Zustellbarkeits-Monitoring nicht mehr unterstützt.</p>
   <p>Bei Bedarf können Sie diesen Bericht bis zum Datum der Entfernung der Funktion täglich per E-Mail erhalten. Erstellen Sie zum Anfordern ein entsprechendes <a href="https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html">Support-Ticket</a> und geben Sie den Namen der Instanz und die E-Mail-Adresse(n) an, an die der Bericht gesendet werden soll.</p> 
   <p>Adobe empfiehlt Ihnen, sich mit dem Zustellbarkeits-Team in Verbindung zu setzen, um die besten Tools zur Überwachung der Zustellbarkeit Ihrer Instanz zu finden.</p>
  <p><em>Geplantes Datum für die Entfernung: Ende 2021</em></p>
  </td>
 </tr>
  <tr>
  <td>OAuth-Authentifizierung (OAuth und JWT)<br></td>
  <td><p> Ab Campaign-Version 20.3 wurde die Authentifizierung für die Triggers-Integration, die ursprünglich auf der oAUTH-Authentifizierung basierte und für den Zugriff auf die Pipeline eingerichtet wurde, geändert und in Adobe I/O verschoben <p>
  <p>Wenn Sie die Triggers-Integration nutzen, müssen Sie Ihre Implementierung entsprechend anpassen. <a href="../../integrations/using/configuring-adobe-io.md">Weitere Infos</a></p> 
  <p>Weitere Informationen zur Einstellung der OAuth-Authentifizierung finden Sie auf dieser <a href="https://github.com/AdobeDocs/analytics-1.4-apis/blob/master/docs/APIEOL.md">Seite</a>.</p> 
  <p><em>Geplantes Datum für die Entfernung: November 2021</em></p>
  </td>
  </tr>
 </tbody> 
</table>

## Entfernte Funktionen {#removed-features}

In diesem Abschnitt werden Funktionen und Leistungsmerkmale aufgelistet, die aus Campaign Standard entfernt wurden.

<table> 
 <tbody>
  <tr> 
   <td><strong>Bereich – Funktion</strong></td>
   <td><strong>Ersatz</strong></td> 
  </tr>
  <tr>  
   <td>Fax-Kanal<br></td>
   <td><p>Ab Campaign Version 21.1.3 ist der Fax-Kanal nicht mehr verfügbar. <a href="../../delivery/using/steps-about-delivery-creation-steps.md">Mehr dazu</a></p>
  <tr>
  <td>Demdex-Domain<br></td>
  <td><p> Ab Campaign Version 21.1.3 wird die Demdex-Domain, die zum Importieren und Exportieren von Audiences nach Adobe Experience Cloud verwendet wird, nicht mehr unterstützt. <a href="../../integrations/using/configuring-shared-audiences-integration-in-adobe-campaign.md">Mehr dazu</a></p> 
  </td>
  </td>
  </tr>
   <tr> 
   <td>Windows NT-Authentifizierung<br></td>
   <td><p>Ab Campaign-Version 20.3 wurde die Windows NT-Authentifizierung bei der Konfiguration einer neuen Datenbank mit einem Microsoft SQL Server aus den verfügbaren Authentifizierungsmechanismen entfernt. <a href="../../installation/using/creating-and-configuring-the-database.md#step-1---selecting-the-database-engine">Weitere Infos</a></p></td>
  </tr>
   <tr> 
   <td>Dateibasierte E-Mail-Archivierung<br></td>
   <td><p>Ab Campaign-Version 20.2 ist dateibasierte E-Mail-Archivierung nicht mehr verfügbar. E-Mail-Archivierung ist jetzt über eine dedizierte BCC-E-Mail-Adresse verfügbar. <a href="../../installation/using/email-archiving.md">Weitere Infos</a></p></td>
  </tr> 
   <tr> 
   <td>Leadmanagement</td>
   <td><p>Ab Campaign-Version 20.2 ist das Package "Leadmanagement" nicht mehr verfügbar. Ähnliche Funktionen können über andere native Workflow-Aktivitäten und Änderungen am Datenmodell implementiert werden.</p></td>
   </tr>
   <tr>
   <td>Dokumentation zu Campaign-APIs – Jsapi.chm-Datei</td>
   <td>Ab Campaign-Version 19.1 sind Campaign Classic-APIs auf einer dedizierten Seite verfügbar. Wenn Sie die Legacy-Datei "jsapi.chm" verwendet haben, sollten Sie jetzt auf <a href="https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html">die neue Online-Version</a> verweisen.</td>
  </tr> 
  <tr> 
   <td>Kampagnenorchestrierung – Predictive Marketing</td>
   <td>Ab Campaign-Version 18.10 sind die Funktionen für Predictive Marketing nicht mehr verfügbar.</td>
  </tr> 
  <tr> 
   <td>Web-Anwendungen – Microsites</td>
   <td>Ab Campaign-Version 18.10 sind Microsites nicht mehr verfügbar. Sie können die Sicherheit erhöhen, indem Sie den Zugriff auf dedizierte Domains in Adobe Campaign-Konfigurationsdateien beschränken und in Campaign unter Verwendung von DNS-Aliassen personalisierte URLs verwenden. <a href="https://helpx.adobe.com/de/campaign/kb/domain-name-delegation.html">Weitere Infos</a></td>
  </tr> 
  <tr> 
   <td>Push-Benachrichtigungen – iOS Binary Connector</td>
   <td>Auf Empfehlung von Apple hat Adobe die alte Version des iOS Binary-Connectors ab Campaign-Version 18.10 entfernt. Der leistungsfähigere und effizientere HTTP/2-basierte Connector ist bereits verfügbar.</td>
  </tr> 
  <tr> 
   <td>decryptString-API</td>
   <td><p>Ab Campaign-Version 18.6 ist die <em>decryptString</em>-API bei neuen Installationen aus Sicherheitsgründen standardmäßig nicht mehr verfügbar.</p> 
   <p>Im Zusammenhang mit einem Postupgrade auf Version 18.6 (und höher) ist diese API nicht mehr aktiv; sie wurde durch die <em>decryptPassword</em>-Funktion ersetzt. <a href="https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/f-decryptPassword.html?hl=decrypt">Weitere Infos</a></p></td>
  </tr> 
   <tr> 
   <td>Mobiler Kanal – MMS- und WAP-Push-Benachrichtigungen</td>
   <td>Ab Campaign-Version 18.4 sind die Kanäle MMS und WAP Push nicht mehr verfügbar. Als Ersatz können Sie <a href="../../delivery/using/sms-channel.md">SMS</a>- und <a href="../../delivery/using/about-mobile-app-channel.md">Push</a>-Nachrichten nutzen.</td>
  </tr> 
   <tr> 
   <td>Mobiler Kanal – LINE v1</td>
   <td>Ab Campaign-Version 18.4 ist das LINE Connect-Package nicht mehr verfügbar. Adobe empfiehlt, das neue LINE Channel-Package als Ersatz zu verwenden. <a href="../../delivery/using/line-channel.md">Weitere Infos</a></td>
  </tr>
 </tbody> 
</table>

## Eingestellte Kompatibilität {#deprecated-compatibility}

Die folgenden Systeme werden für Campaign Classic jetzt nicht mehr unterstützt. Konsultieren Sie die [Kompatibilitätsmatrix](../../rn/using/compatibility-matrix.md), wenn Sie ein Upgrade auf eine neuere Version durchführen oder auf ein neues System umsteigen möchten, bevor die Kompatibilität endet.

### Adobe Campaign-Version 20.2 {#compat-20-2-release}

Ab Version 20.2 werden alte SMS-Connectoren eingestellt. Weitere Informationen finden Sie im Abschnitt [Eingestellte Funktionen](#deprecated-features).

## Ende der Kompatibilität {#end-of-compatibility}

>[!CAUTION]
>
>Adobe Campaign Classic ist mit allen in der [Kompatibilitätsmatrix](../../rn/using/compatibility-matrix.md) aufgeführten Systemen und Tools kompatibel. Wenn bestimmte Versionen dieser Drittanbietersysteme und -Tools bei ihren Erstanbietern das Ende des Lebenszyklus (End of Life, EOL) erreichen, ist Adobe Campaign nicht mehr mit diesen Versionen kompatibel: Sie werden als eingestellt angekündigt und dann mit der folgenden Produktversion aus unserer Kompatibilitätsmatrix entfernt. Verwenden Sie, um Probleme zu vermeiden, ausschließlich unterstützte Versionen von Systemen, die in der Kompatibilitätsmatrix aufgeführt sind.

### Client Console {#client-console-eol}

Die Client Console von Adobe Campaign Classic kann in den folgenden Systemen nicht mehr ausgeführt werden, da sie von ihrem Anbieter eingestellt wurden. Kunden, die die Campaign Client Console in einer dieser Versionen ausführen, müssen vor dem geplanten Entfernungsdatum auf die aktuelle Version aktualisieren. Siehe [Kompatibilitätsmatrix](../../rn/using/compatibility-matrix.md).

* Windows Server 2003, 2008, 2008 R2
* Windows 7, XP, Vista

>[!NOTE]
>Ab Campaign-Version 20.1 ist Campaign Classic Client Console (32 Bit) nicht mehr mit den aktuellen Campaign-Versionen kompatibel. Sie müssen Client Console mit 64 Bit verwenden.

### Betriebssysteme {#o-s-eol}

Ab Version 21.1.3 wird Debian 8 nicht mehr unterstützt.

Ab Version 19.1 ist Adobe Campaign nicht mehr mit den folgenden Betriebssystemen kompatibel.

* CentOS 6 [Weitere Infos](https://wiki.centos.org/Download)
* Debian 7. [Weitere Infos](https://wiki.debian.org/DebianReleases)
* RHEL 6.x. [Weitere Infos](https://access.redhat.com/support/policy/updates/errata)
* Windows Server 2008. [Weitere Infos](https://support.microsoft.com/en-us/lifecycle/search/1163)
* SLES 11. [Weitere Infos](https://www.suse.com/lifecycle)

### Webserver {#web-server-eol}

Ab der Frühlingsversion 19.1 ist Adobe Campaign nicht mehr mit dem folgenden Webserver kompatibel.

* Apache 2.2. [Weitere Infos](https://httpd.apache.org/)
* Microsoft IIS 7. [Weitere Infos](https://support.microsoft.com/en-us/lifecycle/search/810)

### Tools {#tools-eol}

Ab der Frühlingsversion 19.1 ist Adobe Campaign nicht mehr mit den folgenden Tools kompatibel.

* Java JDK 7. [Weitere Infos](http://www.oracle.com/technetwork/java/javase/eol-135779.html)
* Libre Office 3.5 / 4.3 / 5.x, außer wenn in ein anderes Tool eingebettet. [Weitere Informationen](https://wiki.documentfoundation.org/ReleasePlan/Archive#End-of-Life_Releases)

### Datenbank-Engines {#dbe-eol}

Adobe unterstützt die folgenden Datenbank-Engines nicht mehr, da sie von ihrem Anbieter eingestellt wurden. Kunden, die mit diesen Versionen arbeiten, müssen auf die aktuelle Version aktualisieren oder zu einer anderen Engine wechseln.

Konsultieren Sie die [Campaign-Kompatibilitätsmatrix](../../rn/using/compatibility-matrix.md), um sich die Liste kompatibler Versionen anzusehen.

**FEDERATED DATA ACCESS (FDA)**

Ab Version 20.2 ist Adobe Campaign nicht mehr mit den folgenden FDA-Servern kompatibel:

* DB2 UDB 10.5

Ab der Frühlingsversion 19.1 ist Adobe Campaign nicht mehr mit den folgenden FDA-Servern kompatibel:

* PostgreSQL 9.3. [Weitere Infos](https://www.postgresql.org/support/versioning)
* MySQL 5.5. [Weitere Infos](http://www.fromdual.com/support-for-mysql-from-oracle)
* DB2 9.5. [Weitere Infos](http://www-01.ibm.com/support/docview.wss?uid=swg21168270)
* Teradata 14 – 14.1. [Weitere Infos](https://community.teradata.com/t5/Database/Teradata-Database-Product-Life-Cycle/td-p/35068)

Campaign Classic ist mit den folgenden Servern in Federated Data Access (FDA) nicht mehr kompatibel.

* DB2 UDB 9.5, 9.7. Neuere Versionen von DB2 werden über Federated Data Access (FDA) unterstützt. [Weitere Infos](http://www-01.ibm.com/support/docview.wss?uid=swg21168270)
* Oracle 9i, 10G R2. Neuere Versionen von Oracle werden über Federated Data Access (FDA) unterstützt. [Weitere Infos](http://www.oracle.com/us/support/library/lifetime-support-technology-069183.pdf)
* PostgreSQL 8.3, 8.4, 9.0, 9.1, 9.2. Neuere Versionen von PostgreSQL werden über Federated Data Access (FDA) unterstützt. [Weitere Infos](https://www.postgresql.org/support/versioning)
* MSSQL 2000, 2005, 2008 R2. Neuere Versionen von SQL Server werden über Federated Data Access (FDA) unterstützt. [Weitere Infos](https://support.microsoft.com/en-us/lifecycle/search/1044)
* MySQL 5.1. Neuere Versionen von MySQL werden über Federated Data Access (FDA) unterstützt. [Weitere Infos](https://en.wikipedia.org/wiki/InfiniDB)
* InfiniDB hat das Ende des Lebenszyklus erreicht. [Weitere Infos](https://www.mysql.com/support)
* Teradata 13, 13.1. Neuere Versionen von Teradata werden über Federated Data Access (FDA) unterstützt. [Weitere Infos](https://www.info.teradata.com/download.cfm?ItemID=1007255)
* Netezza 6.02, 7.0. Netezza hat das Ende des Lebenszyklus erreicht. [Weitere Infos](https://en.wikipedia.org/wiki/Netezza)
* AsterData 5.0. AsterData hat das Ende des Lebenszyklus erreicht. [Weitere Infos](https://en.wikipedia.org/wiki/Aster_Data_Systems)
* Sybase IQ 15.2, 15.4, 15.5 und Sybase ASE 15.0. Neuere Versionen von Sybase werden über Federated Data Access (FDA) unterstützt. [Weitere Infos](https://sites.google.com/site/dbatipsandtricks/time-tracker)
* Hadoop via HiveSQL: Hadoop 2.7.3, HiveSQL 1.2.1. Adobe Campaign Classic wird die aufgelisteten Versionen von Hadoop via HiveSQL über Federated Data Access (FDA) weiter unterstützen, die Versionen werden jedoch zusammengeführt mit: HortonWorks (HDP 2.4.x, 2.5.x, 2.6.x) und HDInsight 3.4 (HDP 2.4), 3.5 (HDP 2.5), 3.6 (HDP 2.6).
* Soap-API – On-Premise: 2007, 2015, 2016
* Soap-API – Online: 2015, 2016
* Web API – Microsoft Dynamics CRM On-Premise: 2016, Aktualisierung 1 2016
* Web API – Microsoft Dynamics CRM Online: 2016, Aktualisierung 1 2016
* Oracle On Demand-API

**RDBMS-SERVER**

Ab der Frühlingsversion 19.1 ist Adobe Campaign nicht mehr mit den folgenden RDBMS-Servern kompatibel:

* Oracle 10GR2
* PostgreSQL 9.0 bis 9.3
* SQL Server 2005
* MySQL 5.1
* DB2 UDB 9.7

### SMS-Connectoren {#sms-eol}

Adobe Campaign ist mit den folgenden SMS-Connectoren nicht mehr kompatibel:

* Generic SMPP (SMPP-Version 3.4 mit Unterstützung für Binärmodus)
* Sybase365 (SAP SMS 365)
* CLX Communications
* Tele2
* O2
* iOS
