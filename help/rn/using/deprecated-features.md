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
source-git-commit: e46325ab8f68a0b71198aee9cf04f2b1eb97fdd3
workflow-type: tm+mt
source-wordcount: '1468'
ht-degree: 67%

---


# Eingestellte und entfernte Funktionen {#deprecated-and-removed-features}

Adobe evaluiert laufend die Funktionen seiner Produkte, um ältere Funktionen durch neuere Alternativen zu ersetzen. Auf diese Weise kann der Kundennutzen unter sorgfältiger Berücksichtigung der Abwärtskompatibilität verbessert werden. Da Adobe Campaign Classic mit Tools von Drittanbietern arbeitet, wird die Kompatibilität regelmäßig aktualisiert, um nur unterstützte Versionen zu implementieren. Versionen, die nicht mehr mit Adobe Campaign Classic kompatibel sind, sind unten und in der [Kompatibilitätsmatrix](https://helpx.adobe.com/de/campaign/kb/compatibility-matrix.html)aufgeführt.

Bei der Mitteilung einer bevorstehenden Entfernung/Ersetzung von Campaign Classic-Funktionen gelten die folgenden Regeln:

* Zuerst wird die Entfernung der Funktion angekündigt. Obwohl veraltete Funktionen für bestehende Benutzer weiterhin verfügbar und unterstützt werden können, werden sie nicht weiter verbessert oder dokumentiert.
* Die eingestellten Funktionen werden frühestens in der folgenden Version entfernt. Das tatsächliche Zieldatum für die Entfernung wird auf dieser Seite angegeben.

Durch dieses Vorgehen erhält der Kunde mindestens einen Versionszyklus Zeit, um seine Implementierung an eine neue Version oder einen Nachfolger einer eingestellten Funktion anzupassen, bevor sie tatsächlich entfernt wird.

>[!NOTE]
>Die Versionen und neuen Funktionen von Adobe Campaign sind in den [Versionshinweisen](../../rn/using/latest-release.md) aufgeführt.

## Eingestellte Funktionen{#deprecated-features}

In diesem Abschnitt werden Funktionen aufgeführt, die bei den aktuellen Campaign Classic-Versionen als eingestellt gekennzeichnet wurden.

Im Allgemeinen werden Funktionen, die in einer zukünftigen Version entfernt werden sollen, zuerst auf &quot;Veraltet&quot;eingestellt. Diese Funktionen sind für Neukunden von Campaign Classic entweder nicht mehr verfügbar oder sollten für keine neue Implementierung verwendet werden. Sie werden auch aus der Produktdokumentation entfernt.

Kunden wird empfohlen, zu prüfen, ob sie die Funktion/Funktion in ihrer aktuellen Bereitstellung nutzen, und Pläne zur Änderung ihrer Implementierung zu erstellen. Achten Sie auf das geplante Datum für die Entfernung, um Ihre Umgebungs- und Projektaktualisierungen zu planen.

<table> 
 <tbody> 
   <tr>
   <td><strong>Funktion</strong></td>
   <td><strong>Ersatz</strong></td> 
  </tr>
   <tr>
  <td>SMS-Anschlüsse<br></td>
  <td><p> Ab Version 20.2 werden die folgenden SMS-Connectors nicht mehr unterstützt.<p>
   <ul>
   <li>NetSize</li>
   <li>Generisches SMPP (SMPP Version 3.4 unterstützt Binärmodus)</li>
   <li>Sybase365 (SAP SMS 365)</li>
   <li>CLX Communications</li>
   <li>Tele2</li>
   <li>O2</li>
   <li>iOS</li>
   </ul>
  <p>Wenn Sie einen dieser Connectors verwenden, müssen Sie Ihre Implementierung entsprechend anpassen. <a href="../../delivery/using/sms-channel.md">Mehr dazu</a></p> 
  <p>Erfahren Sie, wie Legacy-Connectors in <a href="https://helpx.adobe.com/campaign/kb/sms-connector.html">dieser TechNote</a>migriert werden.</p>
  <p><em>Zielgruppen-Entfernungsdatum: 2021</em></p>
  </td> 
 </tr>
  <tr>  
   <td>Fax-Kanal<br></td>
   <td><p>Ab Version 20.2 wird der Fax-Kanal nicht mehr unterstützt.</p> 
   <p>Wenn Sie diesen Kanal verwenden, müssen Sie Ihre Implementierung entsprechend anpassen. <a href="../../delivery/using/communication-channels.md">Erfahren Sie mehr</a> über die Kanäle der Kampagne.</p>
   <p><em>Zielgruppen-Entfernungsdatum: 2021</em></p></td>
  </tr>
 </tbody> 
</table>

## Entfernte Funktionen {#removed-features}

In diesem Abschnitt werden Funktionen Liste, die aus Campaign Classic entfernt wurden.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Bereich – Funktion</strong></td>
   <td><strong>Ersatz</strong></td> 
  </tr> 
   <tr> 
   <td>Dateibasierte E-Mail-Archivierung<br></td>
   <td><p>Ab Kampagne 20.2 ist die dateibasierte E-Mail-Archivierung nicht mehr verfügbar. E-Mail-Archivierung ist jetzt über eine dedizierte BCC-E-Mail-Adresse verfügbar. <a href="../../installation/using/email-archiving.md">Mehr dazu</a></p></td>
  </tr> 
   <tr> 
   <td>Leadmanagement</td>
   <td><p>Ab Kampagne 20.2 ist das Leads-Management-Paket nicht mehr verfügbar. Ähnliche Funktionen können über andere native Workflow-Aktivitäten und Änderungen am Datenmodell implementiert werden.</p></td>
   </tr>
   <tr>
   <td>Dokumentation zu Campaign-APIs – Jsapi.chm-Datei</td>
   <td>Ab Kampagne 19.1 sind Campaign Classic-APIs auf einer dedizierten Seite verfügbar. Wenn Sie die Legacy-Datei "jsapi.chm"verwendet haben, sollten Sie sich jetzt auf <a href="https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html">die neue Onlineversion</a>beziehen.</td>
  </tr> 
  <tr> 
   <td>Kampagnenorchestrierung – Predictive Marketing</td>
   <td>Ab Kampagne 18.10 sind die Prognosefunktionen für das Marketing nicht mehr verfügbar.</td>
  </tr> 
  <tr> 
   <td>Web-Anwendungen – Microsites</td>
   <td>Ab Kampagne 18.10 sind Microsites nicht mehr verfügbar. Sie können die Sicherheit verbessern, indem Sie den Zugriff auf dedizierte Domänen in Adobe Campaign-Konfigurationsdateien einschränken und personalisierte URLs in Kampagne mit DNS-Aliase verwenden. <a href="https://helpx.adobe.com/de/campaign/kb/domain-name-delegation.html">Mehr dazu</a></td>
  </tr> 
  <tr> 
   <td>Push-Benachrichtigungen – iOS Binary Connector</td>
   <td>Auf Empfehlung von Apple hat Adobe die ältere Version von iOS Binary Connector ab Kampagne 18.10 entfernt. Der leistungsfähigere und effizientere HTTP/2-basierte Connector ist bereits verfügbar.</td>
  </tr> 
  <tr> 
   <td>decryptString-API</td>
   <td><p>Starting Campaign 18.6 release, for security reasons, <em>decryptString</em> API is no longer available by default for new installations.</p> 
   <p>Im Zusammenhang mit einem Postupgrade auf Version 18.6 (und höher) ist diese API nicht mehr aktiv; sie wurde durch die <em>decryptPassword</em>-Funktion ersetzt. <a href="https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/f-decryptPassword.html?hl=decrypt">Mehr dazu</a></p></td>
  </tr> 
   <tr> 
   <td>Mobiler Kanal – MMS- und WAP-Push-Benachrichtigungen</td>
   <td>Ab Kampagne 18.4 sind die Kanal MMS und Wap Push nicht mehr verfügbar. Als Ersatz können Sie <a href="../../delivery/using/sms-channel.md">SMS</a>- und <a href="../../delivery/using/about-mobile-app-channel.md">Push</a>-Nachrichten nutzen.</td>
  </tr> 
   <tr> 
   <td>Mobiler Kanal – LINE v1</td>
   <td>Ab Kampagne 18.4 ist das LINE Connect-Paket nicht mehr verfügbar. Adobe empfiehlt, das neue LINE Kanal-Paket als Ersatz zu verwenden. <a href="../../delivery/using/line-channel.md">Mehr dazu</a></td>
  </tr> 
 </tbody> 
</table>

## Eingestellte Kompatibilität {#deprecated-compatibility}

Die folgenden Systeme werden zum Campaign Classic nicht mehr unterstützt. Please refer to the [Compatibility matrix](https://helpx.adobe.com/de/campaign/kb/compatibility-matrix.html) to upgrade to a newer version or move to a new system before the compatibility ends.

### Adobe Campaign-Version 20.2 {#compat-20-2-release}

Ab Version 20.2 wird das folgende System zum Campaign Classic nicht mehr unterstützt. Die Kompatibilität endet in Release 20.3 - September 2020.

* Client-Konsole: Windows 7
* Legacy-SMS-Connectors (siehe Abschnitt zu veralteten Funktionen unten)

### Adobe Campaign-Version 19.2  {#compat-19-2-release}

Ab Version 19.2 werden die folgenden Betriebssysteme zum Campaign Classic nicht mehr unterstützt. Die Kompatibilität endet Ende des Jahres 2020.

* Webserver: Apache 2.2.
* Betriebssystem: CentOS 6.

Bitte konsultieren Sie die [Kompatibilitätsmatrix](https://helpx.adobe.com/de/campaign/kb/compatibility-matrix.html), wenn Sie ein Upgrade auf eine neuere Version durchführen oder auf ein neues System umsteigen möchten.

## Ende der Kompatibilität {#end-of-compatibility}

>[!CAUTION]
>
>Adobe Campaign Classic ist mit allen in der [Kompatibilitätsmatrix](https://helpx.adobe.com/de/campaign/kb/compatibility-matrix.html) aufgeführten Systemen und Tools kompatibel. Wenn bestimmte Versionen dieser Drittanbietersysteme und -Tools bei ihren Erstanbietern das Ende des Lebenszyklus (End of Life, EOL) erreichen, ist Adobe Campaign nicht mehr mit diesen Versionen kompatibel: Sie werden als eingestellt angekündigt und dann mit der folgenden Produktversion aus unserer Kompatibilitätsmatrix entfernt. Verwenden Sie, um Probleme zu vermeiden, ausschließlich unterstützte Versionen von Systemen, die in der Kompatibilitätsmatrix aufgeführt sind.

### Client Console {#client-console-eol}

Die Client Console von Adobe Campaign Classic kann in den folgenden Systemen nicht mehr ausgeführt werden, da sie von ihrem Anbieter eingestellt wurden. Kunden, die die Campaign Client Console in einer dieser Versionen ausführen, müssen vor dem geplanten Entfernungsdatum auf die neueste Version aktualisieren. Siehe [Kompatibilitätsmatrix](https://helpx.adobe.com/de/campaign/kb/compatibility-matrix.html).

* Windows Server 2003, 2008, 2008 R2
* Windows XP, Vista

>[!NOTE]
>Ab Kampagne 20.1 sind Campaign Classic Client Console 32 Bit nicht mehr mit den neuesten Kampagnen kompatibel. Sie müssen die 64-Bit-Client-Konsole verwenden.


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
* MySQL 5.5. [Weitere Informationen](http://www.fromdual.com/support-for-mysql-from-oracle)
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
