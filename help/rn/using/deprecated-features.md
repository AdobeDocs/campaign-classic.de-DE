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
discoiquuid: null
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: be148d7cd55097b9014d2f4d3b095c65a5ca8c54
workflow-type: tm+mt
source-wordcount: '1389'
ht-degree: 97%

---


# Eingestellte und entfernte Funktionen {#deprecated-and-removed-features}

Adobe evaluiert laufend die Funktionen seiner Produkte, um ältere Funktionen durch neuere Alternativen zu ersetzen. Auf diese Weise kann der Kundennutzen unter sorgfältiger Berücksichtigung der Abwärtskompatibilität verbessert werden. Da Adobe Campaign Classic mit Tools von Drittanbietern arbeitet, wird die Kompatibilität regelmäßig aktualisiert, um nur unterstützte Versionen zu implementieren. Versionen, die nicht mehr mit Adobe Campaign Classic kompatibel sind, werden im Folgenden aufgeführt.

Bei der Mitteilung einer bevorstehenden Entfernung/Ersetzung von Campaign Classic-Funktionen gelten die folgenden Regeln:

* Zuerst wird die Entfernung der Funktion angekündigt. Auch wenn nicht mehr unterstützte Funktionen für bestehende Benutzer weiterhin verfügbar sind, werden sie weder weiter verbessert noch dokumentiert.
* Die eingestellten Funktionen werden frühestens in der folgenden Version entfernt. Das tatsächliche Zieldatum für die Entfernung wird auf dieser Seite angegeben.

Durch dieses Vorgehen erhält der Kunde mindestens einen Versionszyklus Zeit, um seine Implementierung an eine neue Version oder einen Nachfolger einer eingestellten Funktion anzupassen, bevor sie tatsächlich entfernt wird.

>[!NOTE]
>Die Versionen und neuen Funktionen von Adobe Campaign sind in den [Versionshinweisen](../../rn/using/latest-release.md) aufgeführt.


## Eingestellte Funktionen{#deprecated-features}

In diesem Abschnitt werden Funktionen aufgeführt, die bei den aktuellen Campaign Classic-Versionen als eingestellt gekennzeichnet wurden.

Im Allgemeinen werden Funktionen, die in einer zukünftigen Version entfernt werden sollen, zuerst als eingestellt gekennzeichnet, wobei eine Alternative bereitgestellt wird. Diese Funktionen sind für Neukunden von Campaign Classic entweder nicht mehr verfügbar oder sollten für keine neue Implementierung verwendet werden. Sie werden auch aus der Produktdokumentation entfernt.

Kunden wird empfohlen, die Nutzung der Funktion in ihrer aktuellen Bereitstellung zu prüfen und Pläne zur Änderung ihrer Implementierung zu erstellen, um die verfügbare Alternative zu nutzen. Achten Sie auf das geplante Datum für die Entfernung, um Ihre Umgebungs- und Projektaktualisierungen zu planen.

### Adobe Campaign-Version 18.6 {#ac-18-6-release}

<table> 
 <tbody> 
  <tr> 
   <td><strong>Bereich</strong></td>
   <td><strong>Funktion</strong></td> 
   <td><strong>Ersatz</strong></td> 
  </tr> 
   <tr> 
   <td>JavaScript-SDK – Sicherheit<br> </td>
   <td>decryptString<br> </td>
   <td><p>Aus Sicherheitsgründen ist die <em>decryptString</em>-API bei neuen Installationen standardmäßig nicht mehr verfügbar.</p> 
   <p>Im Zusammenhang mit einem Postupgrade auf Version 18.6 (und höher) ist diese API nicht mehr aktiv; sie wurde durch die <em>decryptPassword</em>-Funktion ersetzt.</p><br> </td>
  </tr> 
 </tbody> 
</table>

### Adobe Campaign-Version 18.4 {#ac-18-4-release}

<table> 
 <tbody> 
  <tr> 
   <td><strong>Bereich</strong></td>
   <td><strong>Funktion</strong></td> 
   <td><strong>Ersatz</strong></td> 
  </tr> 
   <tr> 
   <td>E-Mail-Archivierung<br> </td>
   <td>Dateibasierte Archivierung<br> </td>
   <td><p>E-Mail-Archivierung ist jetzt über eine dedizierte BCC-E-Mail-Adresse verfügbar. <a href="../../installation/using/email-archiving.md">Mehr dazu</a>.</p> 
   <p><em>Geplantes Entfernungsdatum: Campaign-Version 20.2 – Juni 2020</em></p><br> </td>
  </tr> 
   <tr> 
   <td>Leadmanagement<br> </td>
   <td>Leads<br> </td>
   <td><p>Das Leadmanagement-Paket in Adobe Campaign Classic hat die Einrichtung und Verwaltung des gesamten Leadmanagement-Lebenszyklus vereinfacht. Ähnliche Funktionen können über andere native Workflow-Aktivitäten und Änderungen am Datenmodell implementiert werden.</p> 
   <p><em>Geplantes Entfernungsdatum: Campaign-Version 20.2 – Juni 2020</em></p><br> </td>
  </tr> 
 </tbody> 
</table>


## Eingestellte Kompatibilität {#deprecated-compatibility}

### Adobe Campaign-Version 20.1 {#compat-20-1-release}

Ab Version 20.1 (Februar) wird das folgende System für Campaign Classic nicht mehr unterstützt. Die Kompatibilität endet mit Version 20.2 (Juni 2020).

<table> 
 <tbody> 
  <tr> 
   <td><strong>Bereich</strong></td>
   <td><strong>Ersatz</strong></td> 
  </tr> 
   <tr> 
   <td>Campaign Classic Client Console – 32 Bit<br> </td>
   <td><p>Campaign Classic Client Console – 64 Bit</p><br> </td>
  </tr> 
 </tbody> 
</table>

### Adobe Campaign-Version 19.2  {#compat-19-2-release}

Ab der Herbstversion 19.2 ist Campaign Classic nicht mehr mit den folgenden Betriebssystemen kompatibel. Die Kompatibilität endet Ende des Jahres 2020.

* Webserver: Apache 2.2. [Mehr dazu](https://wiki.centos.org/About/Product)
* Betriebssystem: CentOS 6. [Mehr dazu](https://wiki.centos.org/About/Product)

Bitte konsultieren Sie die [Kompatibilitätsmatrix](https://helpx.adobe.com/de/campaign/kb/compatibility-matrix.html), wenn Sie ein Upgrade auf eine neuere Version durchführen oder auf ein neues System umsteigen möchten.

## Entfernte Funktionen {#removed-features}

In diesem Abschnitt werden Funktionen Liste, die aus Campaign Classic entfernt wurden.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Bereich – Funktion</strong></td>
   <td><strong>Ersatz</strong></td> 
   <td><strong>Version</strong></td> 
  </tr> 
   <tr> 
   <td>Dokumentation zu Campaign-APIs – Jsapi.chm-Datei<br> </td>
   <td>Campaign-Classic-APIs sind jetzt auf einer eigenen Seite verfügbar. Wenn Sie die Jsapi.chm-Datei verwendet haben, sollten Sie jetzt <a href="https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html">die neue Online-Version</a> nutzen.</td>
   <td>19.1</td>
  </tr> 
  <tr> 
   <td>Kampagnenorchestrierung – Predictive Marketing</td>
   <td>Ein Großteil der Predictive-Marketing-Funktionen in Adobe Campaign Classic besteht aus dem Einsatz von Prognosemodellen. Zwar wird die Workflow-Aktivität für Predictive Marketing in einer kommenden Version entfernt, doch wird Adobe Campaign die Nutzung von Prognosemodellen aus externen Quellen über andere Workflow-Aktivitäten weiter unterstützen.</td>
   <td>18.10</td>
  </tr> 
  <tr> 
   <td>Web-Anwendungen – Microsites</td>
   <td>Erhöhen Sie die Sicherheit, indem Sie Zugriff auf dedizierte Domains in Adobe Campaign-Konfigurationsdateien beschränken. Sie können in Campaign weiterhin personalisierte URLs mit DNS-Aliassen verwenden. <a href="https://helpx.adobe.com/de/campaign/kb/domain-name-delegation.html">Mehr dazu</a>.</td>
   <td>18.10</td>
  </tr> 
  <tr> 
   <td>Push-Benachrichtigungen – iOS Binary Connector<br> </td>
   <td>Gemäß der Empfehlung von Apple wird Adobe den alten iOS Binary Connector entfernen. Der leistungsfähigere und effizientere HTTP/2-basierte Connector ist bereits verfügbar.</td>
   <td>18.10</td>
  </tr> 
   <tr> 
   <td>Mobiler Kanal – MMS- und WAP-Push-Benachrichtigungen</td>
   <td>MMS- und WAP Push-Kanäle sind nicht mehr verfügbar. Als Ersatz können Sie <a href="../../delivery/using/sms-channel.md">SMS</a>- und <a href="../../delivery/using/about-mobile-app-channel.md">Push</a>-Nachrichten nutzen.</td>
   <td>18.4</td>
  </tr> 
   <tr> 
   <td>Mobiler Kanal – LINE v1</td>
   <td>Das LINE Connect-Package ist nicht mehr zur Installation in Adobe Campaign Classic verfügbar. Adobe empfiehlt die Verwendung des neuen LINE Channel-Packages zum Senden von LINE-Nachrichten. <a href="../../delivery/using/line-channel.md">Mehr dazu</a>.</td>
   <td>18.4</td>
  </tr> 
 </tbody> 
</table>

## Ende der Kompatibilität {#end-of-compatibility}

>[!CAUTION]
>
>Adobe Campaign Classic ist mit allen in der [Kompatibilitätsmatrix](https://helpx.adobe.com/de/campaign/kb/compatibility-matrix.html) aufgeführten Systemen und Tools kompatibel. Wenn bestimmte Versionen dieser Drittanbietersysteme und -Tools bei ihren Erstanbietern das Ende des Lebenszyklus (End of Life, EOL) erreichen, ist Adobe Campaign nicht mehr mit diesen Versionen kompatibel: Sie werden als eingestellt angekündigt und dann mit der folgenden Produktversion aus unserer Kompatibilitätsmatrix entfernt. Verwenden Sie, um Probleme zu vermeiden, ausschließlich unterstützte Versionen von Systemen, die in der Kompatibilitätsmatrix aufgeführt sind.

### Client Console {#client-console-eol}

Die Client Console von Adobe Campaign Classic kann in den folgenden Systemen nicht mehr ausgeführt werden, da sie von ihrem Anbieter eingestellt wurden. Kunden, die die Campaign Client Console in einer dieser Versionen ausführen, müssen vor dem geplanten Entfernungsdatum auf die neueste Version aktualisieren. Siehe [Kompatibilitätsmatrix](https://helpx.adobe.com/de/campaign/kb/compatibility-matrix.html).

* Windows Server 2003, 2008, 2008 R2
* Windows XP, Vista

### Betriebssysteme {#o-s-eol}

Ab Version 19.1 ist Adobe Campaign nicht mehr mit den folgenden Betriebssystemen kompatibel.

* Debian 7. [Mehr dazu](https://wiki.debian.org/DebianReleases).
* RHEL 6.x. [Mehr dazu](https://access.redhat.com/support/policy/updates/errata).
* Windows Server 2008. [Mehr dazu](https://support.microsoft.com/en-us/lifecycle/search/1163).
* SLES 11. [Mehr dazu](ttps://www.suse.com/lifecycle).

### Webserver {#web-server-eol}

Ab der Frühlingsversion 19.1 ist Adobe Campaign nicht mehr mit dem folgenden Webserver kompatibel.

* Microsoft IIS 7. [Mehr dazu](https://support.microsoft.com/en-us/lifecycle/search/810).

### Tools {#tools-eol}

Ab der Frühlingsversion 19.1 ist Adobe Campaign nicht mehr mit den folgenden Tools kompatibel.

* Java JDK 7. [Mehr dazu](http://www.oracle.com/technetwork/java/javase/eol-135779.html).
* Libre Office 3.5 / 4.3 / 5.x, außer wenn in ein anderes Tool eingebettet. [Mehr dazu](https://wiki.documentfoundation.org/ReleasePlan/Archive#End-of-Life_Releases).

### Datenbank-Engines {#dbe-eol}

Adobe unterstützt die folgenden Datenbank-Engines nicht mehr, da sie von ihrem Anbieter eingestellt wurden. Kunden, die mit diesen Versionen arbeiten, müssen auf die neueste Version aktualisieren oder zu einer anderen Engine wechseln.

Konsultieren Sie die [Campaign Classic-Kompatibilitätsmatrix](https://helpx.adobe.com/de/campaign/kb/compatibility-matrix.html), um sich die Liste kompatibler Versionen anzusehen.

**FEDERATED DATA ACCESS (FDA)**

Ab der Frühlingsversion 19.1 ist Adobe Campaign nicht mehr mit den folgenden FDA-Servern kompatibel.

* Oracle 11G. [Mehr dazu](http://www.oracle.com/us/support/library/lifetime-support-technology-069183.pdf).
* PostgreSQL 9.3. [Mehr dazu](https://www.postgresql.org/support/versioning).
* MySQL 5.5. &lt;[Mehr dazu](http://www.fromdual.com/support-for-mysql-from-oracle).
* DB2 9.5. [Mehr dazu](http://www-01.ibm.com/support/docview.wss?uid=swg21168270).
* Teradata 14 – 14.1. [Mehr dazu](https://community.teradata.com/t5/Database/Teradata-Database-Product-Life-Cycle/td-p/35068).

Campaign Classic ist mit den folgenden Servern in Federated Data Access (FDA) nicht mehr kompatibel.

* DB2 UDB 9.5, 9.7. Neuere Versionen von DB2 werden über Federated Data Access (FDA) unterstützt. [Mehr dazu](http://www-01.ibm.com/support/docview.wss?uid=swg21168270).
* Oracle 9i, 10G R2. Neuere Versionen von Oracle werden über Federated Data Access (FDA) unterstützt. [Mehr dazu](http://www.oracle.com/us/support/library/lifetime-support-technology-069183.pdf).
* PostgreSQL 8.3, 8.4, 9.0, 9.1, 9.2. Neuere Versionen von PostgreSQL werden über Federated Data Access (FDA) unterstützt. [Mehr dazu](https://www.postgresql.org/support/versioning).
* MSSQL 2000, 2005, 2008 R2. Neuere Versionen von SQL Server werden über Federated Data Access (FDA) unterstützt. [Mehr dazu](https://support.microsoft.com/en-us/lifecycle/search/1044).
* MySQL 5.1. Neuere Versionen von MySQL werden über Federated Data Access (FDA) unterstützt. [Mehr dazu](https://en.wikipedia.org/wiki/InfiniDB).
* InfiniDB hat das Ende des Lebenszyklus erreicht. [Mehr dazu](https://www.mysql.com/support).
* Teradata 13, 13.1. Neuere Versionen von Teradata werden über Federated Data Access (FDA) unterstützt. [Mehr dazu](https://www.info.teradata.com/download.cfm?ItemID=1007255).
* Netezza 6.02, 7.0. Netezza hat das Ende des Lebenszyklus erreicht. [Mehr dazu](https://en.wikipedia.org/wiki/Netezza).
* AsterData 5.0. AsterData hat das Ende des Lebenszyklus erreicht. [Mehr dazu](https://en.wikipedia.org/wiki/Aster_Data_Systems).
* Sybase IQ 15.2, 15.4, 15.5 und Sybase ASE 15.0. Neuere Versionen von Sybase werden über Federated Data Access (FDA) unterstützt. [Mehr dazu](https://sites.google.com/site/dbatipsandtricks/time-tracker).
* Hadoop via HiveSQL: Hadoop 2.7.3, HiveSQL 1.2.1. Adobe Campaign Classic wird die aufgelisteten Versionen von Hadoop via HiveSQL über Federated Data Access (FDA) weiter unterstützen, die Versionen werden jedoch zusammengeführt mit: HortonWorks (HDP 2.4.x, 2.5.x, 2.6.x) und HDInsight 3.4 (HDP 2.4), 3.5 (HDP 2.5), 3.6 (HDP 2.6).

**RDBMS-SERVER**

Adobe Campaign ist mit den folgenden RDBMS-Servern nicht mehr kompatibel:
* Oracle 10GR2, 11G
* PostgreSQL 9.0 bis 9.3
* SQL Server 2005
* MySQL 5.1
* DB2 UDB 9.7
