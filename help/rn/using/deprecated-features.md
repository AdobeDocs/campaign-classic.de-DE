---
title: Eingestellte und entfernte Funktionen von Campaign Classic
description: Auf dieser Seite finden Sie eingestellte und entfernte Funktionen von Adobe Campaign Classic
page-status-flag: never-activated
uuid: null
contentOwner: simonetn
products: SG_CAMPAIGN/CLASSIC
audience: rn
content-type: reference
topic-tags: campaign-classic-deprecated-features
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 63f07746d39fff22a98b3cd4ab7f2294da778ab3
workflow-type: tm+mt
source-wordcount: '1468'
ht-degree: 100%

---


# Eingestellte und entfernte Funktionen {#deprecated-and-removed-features}

Adobe evaluiert laufend die Funktionen seiner Produkte, um ältere Funktionen durch neuere Alternativen zu ersetzen. Auf diese Weise kann der Kundennutzen unter sorgfältiger Berücksichtigung der Abwärtskompatibilität verbessert werden. Da Adobe Campaign Classic mit Tools von Drittanbietern arbeitet, wird die Kompatibilität regelmäßig aktualisiert, um nur unterstützte Versionen zu implementieren. Versionen, die nicht mehr mit Adobe Campaign Classic kompatibel sind, sind im Folgenden und in der [Kompatibilitätsmatrix](https://helpx.adobe.com/de/campaign/kb/compatibility-matrix.html) aufgeführt.

Bei der Mitteilung einer bevorstehenden Entfernung/Ersetzung von Campaign Classic-Funktionen gelten die folgenden Regeln:

* Zuerst wird die Entfernung der Funktion angekündigt. Auch wenn nicht mehr unterstützte Funktionen weiter verfügbar sein und für bestehende Benutzer unterstützt werden können, werden sie weder weiter verbessert noch dokumentiert.
* Die eingestellten Funktionen werden frühestens in der folgenden Version entfernt. Das tatsächliche Zieldatum für die Entfernung wird auf dieser Seite angegeben.

Durch dieses Vorgehen erhält der Kunde mindestens einen Versionszyklus Zeit, um seine Implementierung an eine neue Version oder einen Nachfolger einer eingestellten Funktion anzupassen, bevor sie tatsächlich entfernt wird.

>[!NOTE]
>Die Versionen und neuen Funktionen von Adobe Campaign sind in den [Versionshinweisen](../../rn/using/latest-release.md) aufgeführt.

## Eingestellte Funktionen{#deprecated-features}

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
  <td>SMS-Connectoren<br></td>
  <td><p> Ab Version 20.2 werden folgende SMS-Connectoren eingestellt.<p>
   <ul>
   <li>NetSize</li>
   <li>Generic SMPP (SMPP-Version 3.4 mit Unterstützung für Binärmodus)</li>
   <li>Sybase365 (SAP SMS 365)</li>
   <li>CLX Communications</li>
   <li>Tele2</li>
   <li>O2</li>
   <li>iOS</li>
   </ul>
  <p>Wenn Sie einen dieser Connectoren verwenden, müssen Sie Ihre Implementierung entsprechend anpassen. <a href="../../delivery/using/sms-channel.md">Mehr dazu</a></p> 
  <p>Erfahren Sie in <a href="https://helpx.adobe.com/de/campaign/kb/sms-connector.html">diesem technischen Hinweis</a>, wie Sie alte Connectoren migrieren können.</p>
  <p><em>Geplantes Datum für die Entfernung: 2021.</em></p>
  </td> 
 </tr>
  <tr>  
   <td>Fax-Kanal<br></td>
   <td><p>Ab Version 20.2 wird der Fax-Kanal nicht mehr unterstützt.</p> 
   <p>Wenn Sie diesen Kanal nutzen, müssen Sie Ihre Implementierung entsprechend anpassen. <a href="../../delivery/using/steps-about-delivery-creation-steps.md">Erfahren Sie mehr</a> über Campaign-Kanäle.</p>
   <p><em>Geplantes Datum für die Entfernung: 2021.</em></p></td>
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
   <td>Dateibasierte E-Mail-Archivierung<br></td>
   <td><p>Ab Campaign-Version 20.2 ist dateibasierte E-Mail-Archivierung nicht mehr verfügbar. E-Mail-Archivierung ist jetzt über eine dedizierte BCC-E-Mail-Adresse verfügbar. <a href="../../installation/using/email-archiving.md">Mehr dazu</a></p></td>
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
   <td>Ab Campaign-Version 18.10 sind Microsites nicht mehr verfügbar. Sie können die Sicherheit erhöhen, indem Sie den Zugriff auf dedizierte Domains in Adobe Campaign-Konfigurationsdateien beschränken und in Campaign unter Verwendung von DNS-Aliassen personalisierte URLs verwenden. <a href="https://helpx.adobe.com/de/campaign/kb/domain-name-delegation.html">Mehr dazu</a></td>
  </tr> 
  <tr> 
   <td>Push-Benachrichtigungen – iOS Binary Connector</td>
   <td>Auf Empfehlung von Apple hat Adobe die alte Version des iOS Binary-Connectors ab Campaign-Version 18.10 entfernt. Der leistungsfähigere und effizientere HTTP/2-basierte Connector ist bereits verfügbar.</td>
  </tr> 
  <tr> 
   <td>decryptString-API</td>
   <td><p>Ab Campaign-Version 18.6 ist die <em>decryptString</em>-API bei neuen Installationen aus Sicherheitsgründen standardmäßig nicht mehr verfügbar.</p> 
   <p>Im Zusammenhang mit einem Postupgrade auf Version 18.6 (und höher) ist diese API nicht mehr aktiv; sie wurde durch die <em>decryptPassword</em>-Funktion ersetzt. <a href="https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/f-decryptPassword.html?hl=decrypt">Mehr dazu</a></p></td>
  </tr> 
   <tr> 
   <td>Mobiler Kanal – MMS- und WAP-Push-Benachrichtigungen</td>
   <td>Ab Campaign-Version 18.4 sind die Kanäle MMS und WAP Push nicht mehr verfügbar. Als Ersatz können Sie <a href="../../delivery/using/sms-channel.md">SMS</a>- und <a href="../../delivery/using/about-mobile-app-channel.md">Push</a>-Nachrichten nutzen.</td>
  </tr> 
   <tr> 
   <td>Mobiler Kanal – LINE v1</td>
   <td>Ab Campaign-Version 18.4 ist das LINE Connect-Package nicht mehr verfügbar. Adobe empfiehlt, das neue LINE Channel-Package als Ersatz zu verwenden. <a href="../../delivery/using/line-channel.md">Mehr dazu</a></td>
  </tr> 
 </tbody> 
</table>

## Eingestellte Kompatibilität {#deprecated-compatibility}

Die folgenden Systeme werden für Campaign Classic jetzt nicht mehr unterstützt. Konsultieren Sie die [Kompatibilitätsmatrix](https://helpx.adobe.com/de/campaign/kb/compatibility-matrix.html), wenn Sie ein Upgrade auf eine neuere Version durchführen oder auf ein neues System umsteigen möchten, bevor die Kompatibilität endet.

### Adobe Campaign-Version 20.2 {#compat-20-2-release}

Ab Version 20.2 wird das folgende System für Campaign Classic nicht mehr unterstützt. Die Kompatibilität endet mit Version 20.3 (September 2020).

* Client Console: Windows 7
* Legacy-SMS-Connectoren (siehe Abschnitt zu eingestellten Funktionen unten)

### Adobe Campaign-Version 19.2  {#compat-19-2-release}

Ab Version 19.2 ist Campaign Classic nicht mehr mit folgenden Betriebssystemen kompatibel. Die Kompatibilität endet mit Ende des Jahres 2020.

* Webserver: Apache 2.2.
* Betriebssystem: CentOS 6.

Konsultieren Sie die [Kompatibilitätsmatrix](https://helpx.adobe.com/de/campaign/kb/compatibility-matrix.html), wenn Sie ein Upgrade auf eine neuere Version durchführen oder auf ein neues System umsteigen möchten.

## Ende der Kompatibilität {#end-of-compatibility}

>[!CAUTION]
>
>Adobe Campaign Classic ist mit allen in der [Kompatibilitätsmatrix](https://helpx.adobe.com/de/campaign/kb/compatibility-matrix.html) aufgeführten Systemen und Tools kompatibel. Wenn bestimmte Versionen dieser Drittanbietersysteme und -Tools bei ihren Erstanbietern das Ende des Lebenszyklus (End of Life, EOL) erreichen, ist Adobe Campaign nicht mehr mit diesen Versionen kompatibel: Sie werden als eingestellt angekündigt und dann mit der folgenden Produktversion aus unserer Kompatibilitätsmatrix entfernt. Verwenden Sie, um Probleme zu vermeiden, ausschließlich unterstützte Versionen von Systemen, die in der Kompatibilitätsmatrix aufgeführt sind.

### Client Console {#client-console-eol}

Die Client Console von Adobe Campaign Classic kann in den folgenden Systemen nicht mehr ausgeführt werden, da sie von ihrem Anbieter eingestellt wurden. Kunden, die die Campaign Client Console in einer dieser Versionen ausführen, müssen vor dem geplanten Entfernungsdatum auf die neueste Version aktualisieren. Siehe [Kompatibilitätsmatrix](https://helpx.adobe.com/de/campaign/kb/compatibility-matrix.html).

* Windows Server 2003, 2008, 2008 R2
* Windows XP, Vista

>[!NOTE]
>Ab Campaign-Version 20.1 ist Campaign Classic Client Console (32 Bit) nicht mehr mit den neuesten Campaign-Versionen kompatibel. Sie müssen Client Console mit 64 Bit verwenden.


### Betriebssysteme {#o-s-eol}

Ab Version 19.1 ist Adobe Campaign nicht mehr mit den folgenden Betriebssystemen kompatibel.

* Debian 7. [Mehr dazu](https://wiki.debian.org/DebianReleases)
* RHEL 6.x. [Mehr dazu](https://access.redhat.com/support/policy/updates/errata)
* Windows Server 2008. [Mehr dazu](https://support.microsoft.com/en-us/lifecycle/search/1163)
* SLES 11. [Mehr dazu](ttps://www.suse.com/lifecycle)

### Webserver {#web-server-eol}

Ab der Frühlingsversion 19.1 ist Adobe Campaign nicht mehr mit dem folgenden Webserver kompatibel.

* Microsoft IIS 7. [Mehr dazu](https://support.microsoft.com/en-us/lifecycle/search/810)

### Tools {#tools-eol}

Ab der Frühlingsversion 19.1 ist Adobe Campaign nicht mehr mit den folgenden Tools kompatibel.

* Java JDK 7. [Mehr dazu](http://www.oracle.com/technetwork/java/javase/eol-135779.html)
* Libre Office 3.5 / 4.3 / 5.x, außer wenn in ein anderes Tool eingebettet. [Mehr dazu](https://wiki.documentfoundation.org/ReleasePlan/Archive#End-of-Life_Releases)

### Datenbank-Engines {#dbe-eol}

Adobe unterstützt die folgenden Datenbank-Engines nicht mehr, da sie von ihrem Anbieter eingestellt wurden. Kunden, die mit diesen Versionen arbeiten, müssen auf die neueste Version aktualisieren oder zu einer anderen Engine wechseln.

Konsultieren Sie die [Campaign Classic-Kompatibilitätsmatrix](https://helpx.adobe.com/de/campaign/kb/compatibility-matrix.html), um sich die Liste kompatibler Versionen anzusehen.

**FEDERATED DATA ACCESS (FDA)**

Ab der Frühlingsversion 19.1 ist Adobe Campaign nicht mehr mit den folgenden FDA-Servern kompatibel.

* PostgreSQL 9.3. [Mehr dazu](https://www.postgresql.org/support/versioning)
* MySQL 5.5. [Mehr dazu](http://www.fromdual.com/support-for-mysql-from-oracle)
* DB2 9.5. [Mehr dazu](http://www-01.ibm.com/support/docview.wss?uid=swg21168270)
* Teradata 14 – 14.1. [Mehr dazu](https://community.teradata.com/t5/Database/Teradata-Database-Product-Life-Cycle/td-p/35068)

Campaign Classic ist mit den folgenden Servern in Federated Data Access (FDA) nicht mehr kompatibel.

* DB2 UDB 9.5, 9.7. Neuere Versionen von DB2 werden über Federated Data Access (FDA) unterstützt. [Mehr dazu](http://www-01.ibm.com/support/docview.wss?uid=swg21168270)
* Oracle 9i, 10G R2. Neuere Versionen von Oracle werden über Federated Data Access (FDA) unterstützt. [Mehr dazu](http://www.oracle.com/us/support/library/lifetime-support-technology-069183.pdf)
* PostgreSQL 8.3, 8.4, 9.0, 9.1, 9.2. Neuere Versionen von PostgreSQL werden über Federated Data Access (FDA) unterstützt. [Mehr dazu](https://www.postgresql.org/support/versioning)
* MSSQL 2000, 2005, 2008 R2. Neuere Versionen von SQL Server werden über Federated Data Access (FDA) unterstützt. [Mehr dazu](https://support.microsoft.com/en-us/lifecycle/search/1044)
* MySQL 5.1. Neuere Versionen von MySQL werden über Federated Data Access (FDA) unterstützt. [Mehr dazu](https://en.wikipedia.org/wiki/InfiniDB)
* InfiniDB hat das Ende des Lebenszyklus erreicht. [Mehr dazu](https://www.mysql.com/support)
* Teradata 13, 13.1. Neuere Versionen von Teradata werden über Federated Data Access (FDA) unterstützt. [Mehr dazu](https://www.info.teradata.com/download.cfm?ItemID=1007255)
* Netezza 6.02, 7.0. Netezza hat das Ende des Lebenszyklus erreicht. [Mehr dazu](https://en.wikipedia.org/wiki/Netezza)
* AsterData 5.0. AsterData hat das Ende des Lebenszyklus erreicht. [Mehr dazu](https://en.wikipedia.org/wiki/Aster_Data_Systems)
* Sybase IQ 15.2, 15.4, 15.5 und Sybase ASE 15.0. Neuere Versionen von Sybase werden über Federated Data Access (FDA) unterstützt. [Mehr dazu](https://sites.google.com/site/dbatipsandtricks/time-tracker)
* Hadoop via HiveSQL: Hadoop 2.7.3, HiveSQL 1.2.1. Adobe Campaign Classic wird die aufgelisteten Versionen von Hadoop via HiveSQL über Federated Data Access (FDA) weiter unterstützen, die Versionen werden jedoch zusammengeführt mit: HortonWorks (HDP 2.4.x, 2.5.x, 2.6.x) und HDInsight 3.4 (HDP 2.4), 3.5 (HDP 2.5), 3.6 (HDP 2.6).

**RDBMS-SERVER**

Adobe Campaign ist mit den folgenden RDBMS-Servern nicht mehr kompatibel:
* Oracle 10GR2
* PostgreSQL 9.0 bis 9.3
* SQL Server 2005
* MySQL 5.1
* DB2 UDB 9.7
