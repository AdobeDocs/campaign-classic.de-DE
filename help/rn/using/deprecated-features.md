---
title: Funktionen, die nicht mehr unterstützt und entfernt werden
description: Diese Liste wurde eingestellt und Funktionen von Adobe Campaign Classic wurden entfernt.
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
source-git-commit: 10419ee0fb466bddd05ab67087ccdbfdda1e48c8

---


# Deprecated and removed features {#deprecated-and-removed-features}

Adobe evaluiert laufend die Funktionen seiner Produkte, um ältere Funktionen durch neuere Alternativen zu ersetzen. Auf diese Weise kann der Kundennutzen unter sorgfältiger Berücksichtigung der Abwärtskompatibilität verbessert werden. Da Adobe Campaign Classic mit Drittanbieterwerkzeugen arbeitet, wird die Kompatibilität regelmäßig aktualisiert, um nur unterstützte Versionen zu implementieren. Die Versionen, die nicht mehr mit Adobe Campaign Classic kompatibel sind, sind unten aufgeführt.

Für die Mitteilung der bevorstehenden Entfernung/Ersetzung von Campaign Classic-Funktionen gelten folgende Regeln:

* Zuerst wird die Entfernung der Funktion angekündigt. Auch wenn nicht mehr unterstützte Funktionen für bestehende Benutzer weiterhin verfügbar sind, werden sie weder weiter verbessert noch dokumentiert.
* Die eingestellten Funktionen werden frühestens in der folgenden Version entfernt. Das tatsächliche Zieldatum für die Entfernung wird auf dieser Seite angegeben.

Durch dieses Vorgehen erhält der Kunde mindestens einen Versionszyklus Zeit, um seine Implementierung an eine neue Version oder einen Nachfolger einer eingestellten Funktion anzupassen, bevor sie tatsächlich entfernt wird.

>[!NOTE]
>Die Versionen und neuen Funktionen von Adobe Campaign sind in den [Versionshinweisen](../../rn/using/latest-release.md) aufgeführt.


## Deprecated features {#deprecated-features}

In diesem Abschnitt werden Funktionen Liste, die mit den neuesten Campaign Classic-Versionen als veraltet gekennzeichnet wurden.

Im Allgemeinen werden Funktionen, die in einer zukünftigen Version entfernt werden sollen, zuerst als eingestellt gekennzeichnet, wobei eine Alternative bereitgestellt wird. Diese Funktionen sind für neue Campaign Standard-Kunden entweder nicht mehr verfügbar oder sollten für keine neue Implementierung verwendet werden. Sie werden auch aus der Produktdokumentation entfernt.

Kunden wird empfohlen, die Nutzung der Funktion in ihrer aktuellen Bereitstellung zu prüfen und Pläne zur Änderung ihrer Implementierung zu erstellen, um die verfügbare Alternative zu nutzen. Achten Sie auf das geplante Datum für die Entfernung, um Ihre Umgebungs- und Projektaktualisierungen zu planen.

### Adobe Campaign 18.6 {#ac-18-6-release}

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
   <td><p>Aus Sicherheitsgründen ist die decryptString-API bei neuen Installationen standardmäßig nicht mehr verfügbar.</p> 
   <p>Im Zusammenhang mit einer Nachaktualisierung auf 18.6 (und höher) wird diese API nicht mehr aktiviert und wurde durch die Funktion decryptPassword ersetzt.</p><br> </td>
  </tr> 
 </tbody> 
</table>

### Adobe Campaign 18.4 {#ac-18-4-release}

<table> 
 <tbody> 
  <tr> 
   <td><strong>Bereich</strong></td>
   <td><strong>Funktion</strong></td> 
   <td><strong>Ersatz</strong></td> 
  </tr> 
   <tr> 
   <td>E-Mail-Archivierung<br> </td>
   <td>Dateibasierte Archivierung<br></td>
   <td><p>Die E-Mail-Archivierung ist jetzt über eine dedizierte BCC-E-Mail-Adresse verfügbar. <a href="../../installation/using/email-archiving.md">Mehr dazu</a>.</p> 
   <p><em>Zielgruppen-Entfernungsdatum: Version 20.2 der Kampagne - Juni 2020</em></p><br> </td>
  </tr> 
   <tr> 
   <td>Interessentenverwaltung<br></td>
   <td>Leads<br> </td>
   <td><p>Das Leads Management Paket in Adobe Campaign Classic hat den Aufbau und die Aufrechterhaltung des gesamten Leads Management Lebenszyklus vereinfacht. Ähnliche Funktionen können über andere native Workflow-Aktivitäten und Datenmodelländerungen implementiert werden.</p> 
   <p><em>Zielgruppen-Entfernungsdatum: Version 20.2 der Kampagne - Juni 2020</em></p><br> </td>
  </tr> 
 </tbody> 
</table>


## Veraltete Kompatibilität {#deprecated-compatibility}

### Version Adobe Campaign 20.1 {#compat-20-1-release}

Ab Version 20.1 (Februar) wird das folgende System für Campaign Classic nicht mehr unterstützt. Die Kompatibilität endet in Release 20.2 - Juni 2020.

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

### Version 19.2 von Adobe Campaign {#compat-19-2-release}

Ab der Herbstversion 19.2 ist Campaign Classic nicht mehr mit den folgenden Betriebssystemen kompatibel. Die Kompatibilität endet Ende des Jahres 2020.

* Webserver: Apache 2.2. Weitere [Informationen](https://wiki.centos.org/About/Product)
* Betriebssystem: CentOS 6. [mehr dazu](https://wiki.centos.org/About/Product)

Bitte konsultieren Sie die [Kompatibilitätsmatrix](https://helpx.adobe.com/de/campaign/kb/compatibility-matrix.html), wenn Sie ein Upgrade auf eine neuere Version durchführen oder auf ein neues System umsteigen möchten.

## Entfernte Funktionen {#removed-features}

In diesem Abschnitt werden Funktionen Liste, die aus Campaign Standard entfernt wurden.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Bereich - Funktion</strong></td>
   <td><strong>Ersatz</strong></td> 
   <td><strong>Version</strong></td> 
  </tr> 
   <tr> 
   <td>Dokumentation zu Kampagne-APIs - Datei<br>"jsapi.chm"</td>
   <td>Campaign Classic APIs are now available in a dedicated page. If you were using the jsapi.chm file, you should now refer to <a href="https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html">the new online version</a>.</td>
   <td>&lt;19.1</td>
  </tr> 
  <tr> 
   <td>Kampagne Orchestrierung - Predictive Marketing</td>
   <td>Ein großer Teil der Prognosemöglichkeiten für das Marketing in Adobe Campaign Classic war der Einsatz von Prognosemodellen. Obwohl die Aktivität des prognostischen Marketingarbeitsablaufs in einer kommenden Version entfernt wird, unterstützt Adobe Campaign weiterhin die Nutzung und Verwendung von Prognosemodellen aus externen Quellen über andere Workflow-Aktivitäten.</td>
   <td>18.10</td>
  </tr> 
  <tr> 
   <td>Webanwendungen - Microsites</td>
   <td>Verbessern Sie die Sicherheit, indem Sie den Zugriff auf nur dedizierte Domänen in Adobe Campaign-Konfigurationsdateien einschränken. Sie können in der Kampagne immer noch personalisierte URLs mit DNS-Aliasnamen verwenden. <a href="https://helpx.adobe.com/de/campaign/kb/domain-name-delegation.html">Mehr dazu</a>.</td>
   <td>18.10</td>
  </tr> 
  <tr> 
   <td>Push-Benachrichtigungen - iOS Binary Connector<br></td>
   <td>Gemäß der Empfehlung von Apple entfernt Adobe den alten iOS Binary Connector. Der leistungsfähigere und effizientere HTTP/2-basierte Connector ist bereits verfügbar.</td>
   <td>18.10</td>
  </tr> 
   <tr> 
   <td>Mobile Kanal - MMS- und WAP-Push-Nachrichten</td>
   <td>MMS- und Wap Push-Kanal sind nicht mehr verfügbar. Als Ersatz können Sie <a href="../../delivery/using/sms-channel.md">SMS</a> - und <a href="../../delivery/using/about-mobile-app-channel.md">Push</a> -Versand nutzen.</td>
   <td>18.4</td>
  </tr> 
   <tr> 
   <td>Mobile Kanal - LINE v1</td>
   <td>Das LINE Connect-Paket steht nicht mehr zur Installation in Adobe Campaign Classic zur Verfügung. Adobe empfiehlt die Verwendung des neuen LINE Kanal-Pakets zum Senden von LINE-Nachrichten. <a href="../../delivery/using/line-channel.md">Mehr dazu</a>.</td>
   <td>18.4</td>
  </tr> 
 </tbody> 
</table>

## Ende der Kompatibilität {#end-of-compatibility}

>[!CAUTION]
>
>Adobe Campaign Classic ist mit allen in der [Kompatibilitätsmatrix](https://helpx.adobe.com/de/campaign/kb/compatibility-matrix.html)aufgeführten Systemen und Tools kompatibel. Wenn bestimmte Versionen dieser Drittanbietersysteme und -werkzeuge mit ihren jeweiligen Erstellern das Lebenszyklusende (End of Life, EOL) erreichen, ist Adobe Campaign nicht mehr mit diesen Versionen kompatibel: werden sie als veraltet angekündigt und dann in der folgenden Produktversion aus unserer Kompatibilitätsmatrix entfernt. Bitte stellen Sie sicher, dass Sie sich auf unterstützten Versionen aller in der Kompatibilitätsmatrix aufgelisteten Systeme befinden, um Probleme zu vermeiden.

### Client-Konsole {#client-console-eol}

Die Adobe Campaign Classic Client Console kann nicht mehr auf den folgenden Systemen ausgeführt werden, da sie von ihrem Editor nicht mehr unterstützt werden. Kunden, die Kampagne Client Console auf einer dieser Versionen ausführen, müssen vor dem Zeitpunkt des Löschvorgangs der Zielgruppe auf die neueste Version aktualisieren. Siehe [Kompatibilitätsmatrix](https://helpx.adobe.com/de/campaign/kb/compatibility-matrix.html).

* Windows Server 2003, 2008, 2008 R2
* Windows XP, Vista

### Betriebssysteme {#o-s-eol}

Ab Version 19.1 ist Adobe Campaign nicht mehr mit den folgenden Betriebssystemen kompatibel.

* Debian 7. [Mehr dazu](https://wiki.debian.org/DebianReleases).
* RHEL 6.x. Weitere [Informationen](https://access.redhat.com/support/policy/updates/errata).
* Windows Server 2008. [Mehr dazu](https://support.microsoft.com/en-us/lifecycle/search/1163).
* DATEI 11. [Mehr dazu](https://www.suse.com/lifecycle).

### Webserver {#web-server-eol}

Ab der Frühjahrsversion 19.1 ist Adobe Campaign nicht mehr mit dem folgenden Webserver kompatibel.

* Microsoft IIS 7. [Mehr dazu](https://support.microsoft.com/en-us/lifecycle/search/810).

### Werkzeuge {#tools-eol}

Ab Version 19.1 Frühjahr ist Adobe Campaign nicht mehr mit den folgenden Werkzeugen kompatibel.

* Java JDK 7. [Mehr dazu](http://www.oracle.com/technetwork/java/javase/eol-135779.html).
* Libre Office 3.5 / 4.3 / 5.x, außer wenn in ein anderes Tool eingebettet. [Mehr dazu](https://wiki.documentfoundation.org/ReleasePlan/Archive#End-of-Life_Releases).

### Datenbankmotoren {#dbe-eol}

Adobe unterstützt die folgenden Datenbankmaschinen nicht, da sie von ihrem Editor nicht mehr unterstützt werden. Kunden, die mit diesen Versionen arbeiten, müssen auf die neueste Version aktualisieren oder zu einer anderen wechseln.

Lesen Sie die [Campaign Classic-Kompatibilitätsmatrix](https://helpx.adobe.com/de/campaign/kb/compatibility-matrix.html) , um auf die Liste kompatibler Versionen zuzugreifen.

**FEDERATED DATA ACCESS (FDA)**

Ab der Frühjahrsversion 19.1 ist Adobe Campaign nicht mehr mit den folgenden FDA-Servern kompatibel.

* Oracle 11G. [Mehr dazu](http://www.oracle.com/us/support/library/lifetime-support-technology-069183.pdf).
* PostgreSQL 9.3. Weitere [Informationen](https://www.postgresql.org/support/versioning).
* MySQL 5.5. &lt;[Mehr dazu](http://www.fromdual.com/support-for-mysql-from-oracle).
* DB2 9.5. Weitere [Informationen](http://www-01.ibm.com/support/docview.wss?uid=swg21168270).
* Teradata 14 - 14.1. Weitere [Informationen](https://community.teradata.com/t5/Database/Teradata-Database-Product-Life-Cycle/td-p/35068).

Campaign Classic ist mit den folgenden Servern in Federated Data Access (FDA) nicht kompatibel.

* DB2 UDB 9.5, 9.7. Die neuere Version von DB2 wird über Federated Data Access (FDA) unterstützt. [Mehr dazu](http://www-01.ibm.com/support/docview.wss?uid=swg21168270).
* Oracle 9i, 10G R2. Neuere Versionen von Oracle werden von Federated Data Access (FDA) unterstützt. [Mehr dazu](http://www.oracle.com/us/support/library/lifetime-support-technology-069183.pdf).
* PostgreSQL 8.3, 8.4, 9.0, 9.1, 9.2. Neuere Versionen von PostgreSQL werden von Federated Data Access (FDA) unterstützt. [Mehr dazu](https://www.postgresql.org/support/versioning).
* MSSQL 2000, 2005, 2008 R2. Neuere Versionen von SQL Server werden von Federated Data Access (FDA) unterstützt. [Mehr dazu](https://support.microsoft.com/en-us/lifecycle/search/1044).
* MySQL 5.1. Neuere Versionen von MySQL werden von Federated Data Access (FDA) unterstützt. [Mehr dazu](https://en.wikipedia.org/wiki/InfiniDB).
* InfiniDB hat das Ende des Lebens erreicht. [Mehr dazu](https://www.mysql.com/support).
* Teradata 13, 13.1. Neuere Versionen von Teradata werden durch Federated Data Access (FDA) unterstützt. [Mehr dazu](https://www.info.teradata.com/download.cfm?ItemID=1007255).
* Netezza 6.02, 7.0. Netezza hat das Ende des Lebens erreicht. [Mehr dazu](https://en.wikipedia.org/wiki/Netezza).
* AsterData 5.0. AsterData hat das Ende des Lebens erreicht. [Mehr dazu](https://en.wikipedia.org/wiki/Aster_Data_Systems).
* Sybase IQ 15.2, 15.4, 15.5 und Sybase ASE 15.0. Neuere Versionen von Sybase werden über Federated Data Access (FDA) unterstützt. [Mehr dazu](https://sites.google.com/site/dbatipsandtricks/time-tracker).
* Hadoop über HiveSQL: Hadoop 2.7.3, HiveSQL 1.2.1. Adobe Campaign Classic unterstützt weiterhin die aufgelisteten Versionen von Hadoop über HiveSQL über Federated Data Access (FDA), aber diese Versionen werden wie folgt zusammengeführt: HortonWorks (HDP 2.4.X, 2.5.x, 2.6.x) und HDInsight 3.4 (HDP 2.4), 3.5 (HDP 2.5), 3.6 (HDP 2.6)

**RDBMS-SERVER**

Adobe Campaign ist nicht mit den folgenden RDBMS-Servern kompatibel:
* Oracle 10GR2, 11G
* PostgreSQL 9.0 bis 9.3
* SQL Server 2005
* MySQL 5.1
* DB2 UDB 9.7
