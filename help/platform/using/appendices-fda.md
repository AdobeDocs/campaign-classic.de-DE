---
title: Anlagen
seo-title: FDA-Anhänge
description: FDA-Anhänge
seo-description: null
page-status-flag: never-activated
uuid: 2596fabc-679a-45c8-a62a-165c221654b7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: a84a73a9-9930-449f-8b81-007a0e9d5233
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 353f5df040087175c9f211308704f1af1844ef2c
workflow-type: tm+mt
source-wordcount: '1418'
ht-degree: 1%

---


# Anlagen {#fda-appendices}

## Zusätzliche Teradata-Konfigurationen {#teradata-configuration}

### Kompatibilität {#teradata-compatibility}

**Basiert auf Unicode**

| Datenbankversion | Treiberversion | Minimale Kampagne erforderlich | Hinweis |
|:-:|:-:|:-:|:-:|
| 15 | 15 | Campaign Classic 17.9 | Unter Linux: Abfragen mit Zeitstempel können fehlschlagen (in Build 8937 für Version 18.4 und 8977 für Version 18.10 behoben) Im Debug-Modus können Warnungen in Bezug auf eine fehlerhafte Speicherbelegung im Treiber auftreten. |
| 15 | 16 | Campaign Classic 17.9 | Empfohlene Einrichtung für eine Teradata 15 Datenbank unter Linux. |
| 16 | 16 | Campaign Classic 18.10 | Unicode-Zeichen mit Ersatzpaaren werden nicht vollständig verarbeitet. Die Verwendung von Ersatzzeichen in Daten sollte funktionieren. Die Verwendung von Surrogaten in einer Filterbedingung einer Abfrage funktioniert ohne diese Änderung nicht. |
| 16 | 15 | nicht unterstützt |   |

**Auf Lateinisch1**

In früheren Versionen von Adobe Campaign Classic 17.9 wurde nur die Teradata Latin-1 Datenbank unterstützt.

Ab Adobe Campaign Classic 17.9 unterstützen wir jetzt standardmäßig die Teradata-Datenbank in Unicode.

Kunden mit einer Latein-1-Teradata-Datenbank, die zu einer kürzlich veröffentlichten Campaign Classic-Version migrieren, müssen den Parameter APICharSize=1 in die Optionen des Externen Kontos einfügen.

### Datenbankkonfiguration {#database-configuration}

#### Benutzerkonfiguration {#user-configuration}

Die folgenden Rechte sind erforderlich: Erstellen/Ablegen/Ausführen von benutzerdefinierten Prozeduren, Erstellen/Ablegen/Einfügen/Auswählen von Tabellen. Möglicherweise müssen Sie auch Benutzermodusfunktionen erstellen, wenn Sie die Funktionen md5 und sha2 in Ihrer Adobe Campaign-Instanz verwenden möchten.

Stellen Sie sicher, dass Sie die richtige Zeitzone konfigurieren. Es sollte mit dem übereinstimmen, was in dem in der Adobe Campaign-Instanz erstellten Externe Konto festgelegt wird.

Adobe Campaign stellt keinen Schutzmodus (Fallback) für die Objekte ein, die es in der Datenbank erstellen wird. Möglicherweise müssen Sie eine Standardeinstellung für den Benutzer festlegen, der von Adobe Campaign verwendet wird, um mithilfe der folgenden Abfrage eine Verbindung zur Teradata-Datenbank herzustellen:

| Standard-Ausweichmöglichkeit deaktivieren |
| :-: |
| ```MODIFY USER $login$ AS NO FALLBACK;``` |

#### MD5-Installation {#md5-installation}

Wenn Sie md5-Funktionen in Ihrer Adobe Campaign-Instanz verwenden möchten, müssen Sie die Benutzermodusfunktion auf Ihrer Teradata-Datenbank von dieser [Seite](https://downloads.teradata.com/download/extensibility/md5-message-digest-udf) installieren (md5_20080530.zip).

Die Datei &quot;sha1&quot;der heruntergeladenen Datei lautet wie folgt: 65cc0bb6935f72fcd84fef1ebcd64c00115dfd1e.

So installieren Sie md5:

1. Dekomprimieren Sie die Datei &quot;md5_20080530.zip&quot;.

1. Wechseln Sie zum Ordner &quot;md5/src&quot;.

1. Stellen Sie eine Verbindung zu Ihrer Teradata-Datenbank mit bteq her.

1. Führen Sie den folgenden Befehl bteq aus:

   ```
   .run file = hash_md5.btq
   ```

#### SHA2-Installation {#sha2-installation}

Wenn Sie die sha2-Funktionen in Ihrer Adobe Campaign-Instanz verwenden möchten, müssen Sie die Benutzermodusfunktion auf Ihrer Teradata-Datenbank von dieser [Seite](https://github.com/akuroda/teradata-udf-sha2/archive/v1.0.zip) installieren (teradata-udf-sha2-1.0.zip).

Die Datei &quot;sha1&quot;der heruntergeladenen Datei lautet wie folgt: e87438d37424836358bd3902cf1adeb629349780.

So installieren Sie sha2:

1. Dekomprimieren Sie die Datei &quot;teradata-udf-sha2-1.0.zip&quot;.

1. Wechseln Sie zum Ordner teradata-udf-sha2-1.0/src.

1. Stellen Sie eine Verbindung zu Ihrer Teradata-Datenbank mit bteq her.

1. Führen Sie die beiden folgenden bteq-Befehle aus:

   ```
   .run file = hash_sha256.sql
   .run file = hash_sha512.sql
   ```

#### UDF_UTF16TO8-Installation {#UDF-UTF16TO8-installation}

Wenn Sie die Funktionen &quot;udf_utf16to8&quot;in Ihrer Adobe Campaign-Instanz verwenden möchten, müssen Sie die Benutzermodusfunktion aus dem **Teradata Unicode-Tool-Kit** dieser [Seite](https://downloads.teradata.com/download/tools/unicode-tool-kit) (utk_release1.7.0.0.zip) in Ihrer Teradata-Datenbank installieren.

Die Datei &quot;sha1&quot;der heruntergeladenen Datei lautet wie folgt: e58235f434f52c71316a577cb48e20b97d24f470.

So installieren Sie udf_utf16to8:

1. Dekomprimieren Sie die Datei &quot;utk_release1.7.0.0.zip&quot;.

1. Suchen Sie in den extrahierten Dateien nach &quot;udf_utf16to8.o&quot;und navigieren Sie zu dem Ordner, der die Datei enthält. Es sollte den Namen utk_release1.7.0.0/utk_release1.7.0.0/04 TranslationUDFs/01 Teradata UDFs/suselinux-x8664/udf_installation/ haben.

1. Stellen Sie eine Verbindung zu Ihrer Teradata-Datenbank mit bteq her.

1. Geben Sie den folgenden bteq-Befehl ein:

   ```
   REPLACE FUNCTION udf_utf16to8 (
   inputString VARCHAR(8000) CHARACTER SET UNICODE
   ) RETURNS VARCHAR(16000) CHARACTER SET LATIN
   LANGUAGE C
   NO SQL
   EXTERNAL NAME 'CO!i18n103!udf_utf16to8.o!F!udf_utf16to8'
   PARAMETER STYLE SQL;
   
   -- Test: should return 410042
   SELECT CAST(Char2HexInt(UDF_UTF16to8(_UNICODE'004100000042'XC)) AS VARCHAR(100));
   
### Kampagne Serverkonfiguration für Linux {#campaign-server-linux}

Für die Treiberinstallation ist Folgendes erforderlich:

* Teradata ODBC-Treiber, der auf dieser [Seite zu finden ist](https://downloads.teradata.com/download/connectivity/odbc-driver/linux)

* Teradata Tools and Utilities (für die Massenladung), die auf dieser [Seite zu finden sind](https://downloads.teradata.com/download/tools/teradata-tools-and-utilities-linux-installation-package-0)

Dateinamen und sha1:

* tdodbc1620__linux_indep.16.20.00.00-1.tar.gz 121fdd978b56fe1304fc5cb7819741b0847f 44 fd

* TeradataToolsAndUtilitiesBase__linux_indep.16.20.01.00.tar.gz b 29d0af5ffd8dcf68a9dbbaa6f8639387b19c563

Wenn es kein Paket für Ihre Linux-Distribution gibt, können Sie wie auf einem CentOS 7 beschrieben installieren (z. B. mit Docker) und dann den Inhalt der /opt/teradata auf Ihrem Adobe Campaign-Server kopieren.

#### ODBC-Treiberinstallation {#odbc-installation}

Installieren des ODBC-Treibers

1. Extrahieren Sie die Datei &quot;tdodbc1620__linux_indep.16.20.00.00-1.tar.gz&quot;.

1. Wechseln Sie zum Ordner &quot;tdodbc1620&quot;.

1. Möglicherweise müssen Sie das Setup-Skript reparieren:

   ```
   "sed -i s/16.10/16.20/ setup_wrapper.sh".
   ```

1. Führen Sie die Datei setup_wrapper.sh aus.

#### Installation von Teradata-Werkzeugen und -Hilfsprogrammen {#teradata-tools-installation}

So installieren Sie Tools:

1. Extrahieren Sie die Datei &quot;TeradataToolsAndUtilitiesBase__linux_indep.16.20.01.00.tar.gz&quot;.

1. Wechseln Sie zum Ordner TeradataToolsAndUtilitiesBase/Linux/i386-x8664/tdicu.

1. Führen Sie die Datei setup_wrapper.sh aus.

1. Wechseln Sie zum Ordner TeradataToolsAndUtilitiesBase/Linux/i386-x8664/cliv2.

1. Führen Sie die Datei setup_wrapper.sh aus.

1. Wechseln Sie zum Ordner TeradataToolsAndUtilitiesBase/Linux/i386-x8664/tptbase.

1. Führen Sie die Datei setup_wrapper.sh aus.

1. Eine Datei libtelapi.so sollte in /opt/teradata/client/16.20/lib64 verfügbar sein.

#### Treiberkonfiguration {#driver-configuration}

To learn more on driver configuration, refer to this [section](../../platform/using/legacy-connectors.md#configure-access-to-teradata).

#### Umgebung {#environment-varaiables}

Weitere Informationen zu den Umgebung des Adobe Campaign-Servers finden Sie in diesem [Abschnitt](../../platform/using/legacy-connectors.md#configure-access-to-teradata).

### Konfiguration des Kampagne-Servers für Windows #Kampagne-server-windows

Zunächst müssen Sie Teradata Tools und Hilfsprogramme für Windows herunterladen. Sie können es von dieser [Seite herunterladen](https://downloads.teradata.com/download/tools/teradata-tools-and-utilities-windows-installation-package)

Installieren Sie unbedingt den ODBC-Treiber und die Teradata Parallel Transporter Base. Es wird telapi.dll installieren, das zum Laden von Massen in die Teradata Datenbank verwendet wird.

Stellen Sie sicher, dass sich der Pfad des Treibers und der Dienstprogramme in der PATH-Variablen befindet, die nlserver während der Ausführung haben wird. Der Standardpfad lautet C:\Program Files (x86)\Teradata\Client\15.10\bin on Windows 32 bits or C:\Programm Files\Teradata\Client\15.10\bin on 64 bit).

### Fehlerbehebung bei Externen Konti {#external-account-troubleshooting}

Wenn beim Testen der Verbindung **TIM-030008 Date 2 der folgende Fehler angezeigt wird: fehlende Zeichen (iRc=-53)** stellen sicher, dass der ODBC-Treiber korrekt installiert ist und dass LD_LIBRARY_PATH (Linux) / PATH (Windows) für den Kampagne-Server eingestellt ist.

Der Fehler **ODB-240000 ODBC-Fehler:[Microsoft][ODBC Driver Manager]Data source name not found and no default driver specified.** unter Windows, wenn Sie einen 16.X-Treiber verwenden. Adobe Campaign erwartet, dass die Teradaten in odbcinst.ini den Namen &#39;{teradata}&#39; erhalten.
Wenn Sie eine Serverversion von 18.10 Adobe Campaign haben, können Sie ODBCDRiverName=&quot;Teradata Database ODBC Driver 16.10&quot; in den Optionen des Externen Kontos hinzufügen. Die Versionsnummer kann sich ändern, der genaue Name kann gefunden werden, indem Sie odbcad32.exe ausführen und auf die Registerkarte Treiber zugreifen.
Für eine Version unter 18.10 müssen Sie den Abschnitt &quot;Teradata&quot;von odbcinst.ini kopieren, der von der Treiberinstallation erstellt wurde, in einen neuen Abschnitt namens Teradata,regedit kann in diesem Fall verwendet werden.

Wenn Ihre Basis in latin1 ist, müssen Sie APICharSize=1 in den Optionen hinzufügen.

### Time zone {#timezone}

Teradata verwendet Zeitzonennamen, die nicht Standard sind, können Sie die Liste auf der [Teradata-Site](https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/oGKvgl7gCeBMTGrp59BnwA)finden. Adobe Campaign wird versuchen, die in der externen Konfiguration angegebene Zeitzone in etwas zu konvertieren, das Teradata versteht. Wenn keine Korrespondenz gefunden wird, wird die Zeitzone GMT+X (oder GMT-X) für die Sitzung mit einer Warnung im Protokoll gefunden.

Die Konvertierung erfolgt mit dem Lesen einer Datei namens teradata_timezones.txt, die sich im folgenden Datenverzeichnis befinden sollte: /usr/local/neolane/nl6/datakit unter linux. Wenn Sie diese Datei bearbeiten, wenden Sie sich an das Adobe Campaign-Team, um die Änderungen im Quellcode vorzunehmen. Andernfalls wird diese Datei während der nächsten Kampagne überschrieben.

Die Zeitzone, die für die Verbindung verwendet wird, wird angezeigt, wenn nlserver mit dem -verbose-Switch ausgeführt wird, z. B.:

```
15:04:04 >   ODB-240007 Teradata: will use 'Europe Central' as session time zone.
```

Wenn die verwendete Zeitzone nicht die richtige ist, kann eine Option mit dem Namen &quot;TimeZoneName&quot;im Externe Konto hinzugefügt werden. Verwenden Sie in diesem Fall den Wert &quot;Teradata&quot;, z. B. &quot;TimeZoneName=Europe Central&quot;.

Bei der Verwendung von Massenladung oder &quot;Fast Load&quot;in Teradata-Dokumenten kann die Kampagne die Zeitzone nicht angeben. Es wird daher empfohlen, die Standardzeitzone des Benutzers festzulegen, über den die Kampagne eine Verbindung herstellt:

```
MODIFY USER $login$ AS TIME ZONE = 'Europe Central';
```

## MySQL 5.7-Konfiguration {#mysql-57-configuration}

### Serverkonfiguration {#server-configuration-mysql}

Für die Serverkonfiguration sind keine spezifischen Installationsschritte erforderlich. Adobe Campaign sollte mit einer latin1-Datenbank, einer MySQL-Standarddatenbank oder einer Unicode-Datenbank verwendet werden.

### Treiberinstallation {#driver-installation-mysql}

#### Debian {#debian-mysql}

Laden Sie mysql-apt-config.deb von dieser [Seite herunter](https://dev.mysql.com/doc/mysql-apt-repo-quick-guide/en).

Client-Bibliothek installieren:

```
$ dpkg -i mysql-apt-config_*_all.deb # choose mysql-5.7 in the configuration menu
$ apt update
$ apt install libmysqlclient20
```

#### Windows [#windows-mysql}

Laden Sie den C-Connector von dieser [Seite](https://dev.mysql.com/downloads/connector/c)herunter. Es wird empfohlen, Version 5.7 herunterzuladen.

Vergewissern Sie sich, dass der Ordner mit &quot;libmysqlclient.dll&quot;der von nlserver zu verwendenden Variablen &quot;PATH-Umgebung&quot;hinzugefügt wird.

#### CentOS {#centos-mysql}

Laden Sie mysql57-community-release.noarch.rpm von dieser [Seite](https://dev.mysql.com/downloads/repo/yum)herunter.

Client-Bibliothek installieren:

$ yum install mysql57-community-release-el7-9.noarch.rpm$ yum install mysql-community-libs

### Externe Konto-Konfiguration {#external-account-mysql}

Die Konfiguration des Externen Kontos erfordert keine spezifischen Schritte. Stellen Sie sicher, dass die Zeitzone und die Verwendung von Unicode-Daten gemäß Ihrer Datenbank eingestellt sind.
