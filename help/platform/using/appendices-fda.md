---
title: Anhänge
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
translation-type: ht
source-git-commit: e7cf3b189f328cd1ea6ca8b67a3fc4c0c0bddd84
workflow-type: ht
source-wordcount: '1417'
ht-degree: 100%

---


# Anhänge {#fda-appendices}

## Zusätzliche Teradata-Konfigurationen {#teradata-configuration}

### Kompatibilität {#teradata-compatibility}

**Basierend auf Unicode**

| Datenbankversion | Treiberversion | Erforderliche Mindest-Campaign-Version | Hinweis |
|:-:|:-:|:-:|:-:|
| 15 | 15 | Campaign Classic 17.9 | Unter Linux: Abfragen mit Zeitstempel schlagen möglicherweise fehl (in Build 8937 für Version 18.4 und 8977 für Version 18.10 behoben). Im Debug-Modus können Warnhinweise bezüglich einer schlechten Speichernutzung im Treiber auftreten. |
| 15 | 16 | Campaign Classic 17.9 | Empfohlene Installation für eine Teradata 15-Datenbank unter Linux. |
| 16 | 16 | Campaign Classic 18.10 | Unicode-Zeichen mit Ersatzpaaren werden nicht vollständig verarbeitet. Die Verwendung von Ersatzzeichen in Daten sollte funktionieren. Die Verwendung von Ersatzzeichen in einer Filterbedingung einer Abfrage funktioniert ohne diese Änderung nicht. |
| 16 | 15 | nicht unterstützt |   |

**Basierend auf Latin 1**

In Versionen vor Adobe Campaign Classic 17.9 wurde nur die Teradata Latin-1-Datenbank unterstützt.

Ab Adobe Campaign Classic 17.9 wird jetzt standardmäßig die Teradata-Datenbank in Unicode unterstützt.

Kunden mit einer Teradata Latin-1-Datenbank, die auf eine aktuelle Version von Campaign Classic migriert wird, müssen den Parameter APICharSize = 1 in den Optionen des externen Kontos hinzufügen.

### Datenbankkonfiguration {#database-configuration}

#### Benutzerkonfiguration {#user-configuration}

Die folgenden Rechte sind erforderlich: Erstellen/Löschen/Ausführen von benutzerdefinierten Verfahren, Erstellen/Löschen/Einfügen/Auswählen von Tabellen. Möglicherweise müssen Sie auch Benutzermodusfunktionen erstellen, wenn Sie die Funktionen md5 und sha2 in Ihrer Adobe Campaign-Instanz verwenden möchten.

Stellen Sie sicher, dass Sie die richtige Zeitzone konfigurieren. Sie sollte mit der Zeitzone übereinstimmen, die in dem externen Konto eingestellt wird, das in der Adobe Campaign-Instanz erstellt wurde.

Adobe Campaign legt keinen Schutzmodus (Fallback) für die Objekte fest, die in der Datenbank erstellt werden. Möglicherweise müssen Sie einen Standardwert für den Benutzer festlegen, über den sich Adobe Campaign mit der Teradata-Datenbank verbindet. Folgende Abfrage wird dabei verwendet:

| Standard-Fallback deaktivieren |
| :-: |
| ```MODIFY USER $login$ AS NO FALLBACK;``` |

#### MD5-Installation {#md5-installation}

Wenn Sie MD5-Funktionen in Ihrer Adobe Campaign-Instanz verwenden möchten, müssen Sie die Benutzermodusfunktion in Ihrer Teradata-Datenbank von dieser [Seite](https://downloads.teradata.com/download/extensibility/md5-message-digest-udf) aus installieren (md5_20080530.zip).

Der sha1-Wert der heruntergeladenen Datei lautet wie folgt: 65cc0bb6935f72fcd84fef1ebcd64c00115dfd1e.

Installieren von MD5:

1. Entpacken Sie die Datei md5_20080530.zip.

1. Wechseln Sie zum Verzeichnis „md5/src“.

1. Stellen Sie mit BTEQ eine Verbindung zu Ihrer Teradata-Datenbank her.

1. Führen Sie den folgenden bteq-Befehl aus:

   ```
   .run file = hash_md5.btq
   ```

#### SHA-2-Installation {#sha2-installation}

Wenn Sie SHA-2-Funktionen in Ihrer Adobe Campaign-Instanz verwenden möchten, müssen Sie die Benutzermodusfunktion in Ihrer Teradata-Datenbank von dieser [Seite](https://github.com/akuroda/teradata-udf-sha2/archive/v1.0.zip) aus installieren (teradata-udf-sha2-1.0.zip).

Der SHA-1-Wert der heruntergeladenen Datei lautet wie folgt: e87438d37424836358bd3902cf1adeb629349780.

Installieren von SHA-2:

1. Entpacken Sie die Datei teradata-udf-sha2-1.0.zip.

1. Wechseln Sie zum Verzeichnis „teradata-udf-sha2-1.0/src“.

1. Stellen Sie mit BTEQ eine Verbindung zu Ihrer Teradata-Datenbank her.

1. Führen Sie die beiden folgenden BTEQ-Befehle aus:

   ```
   .run file = hash_sha256.sql
   .run file = hash_sha512.sql
   ```

#### UDF_UTF16TO8-Installation {#UDF-UTF16TO8-installation}

Wenn Sie udf_utf16to8-Funktionen in Ihrer Adobe Campaign-Instanz verwenden möchten, müssen Sie die Benutzermodusfunktion in Ihrer Teradata-Datenbank über das **Teradata-Unicode-Toolkit** auf dieser [Seite](https://downloads.teradata.com/download/tools/unicode-tool-kit) installieren (utk_release1.7.0.0.zip).

Der SHA-1-Wert der heruntergeladenen Datei lautet wie folgt: e58235f434f52c71316a577cb48e20b97d24f470.

Installieren von udf_utf16to8:

1. Entpacken Sie die Datei utk_release1.7.0.0.zip.

1. Suchen Sie in den extrahierten Dateien nach udf_utf16to8.o und navigieren Sie zum Verzeichnis, das die Datei enthält. Es sollte diesen Namen aufweisen: utk_release1.7.0.0/utk_release1.7.0.0/04 TranslationUDFs/01 Teradata UDFs/suselinux-x8664/udf_installation/.

1. Stellen Sie mit BTEQ eine Verbindung zu Ihrer Teradata-Datenbank her.

1. Geben Sie den folgenden BTEQ-Befehl ein:

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
   ```

### Campaign-Serverkonfiguration für Linux {#campaign-server-linux}

Für die Treiberinstallation ist Folgendes erforderlich:

* Teradata-ODBC-Treiber, den Sie auf dieser [Seite](https://downloads.teradata.com/download/connectivity/odbc-driver/linux) finden

* Teradata-Tools und -Dienstprogramme (für Massenladevorgänge), die Sie auf dieser [Seite](https://downloads.teradata.com/download/tools/teradata-tools-and-utilities-linux-installation-package-0) finden

Dateinamen und SHA-1:

* tdodbc1620__linux_indep.16.20.00.00-1.tar.gz 121fdd978b56fe1304fc5cb7819741b0847f44fd

* TeradataToolsAndUtilitiesBase__linux_indep.16.20.01.00.tar.gz b 29d0af5ffd8dcf68a9dbbaa6f8639387b19c563

Wenn für Ihre Linux-Distribution kein Paket vorhanden ist, können Sie die Installation wie beschrieben auf einem CentOS 7 vornehmen (z. B. mit Docker) und dann den Inhalt von „/opt/teradata“ auf Ihren Adobe Campaign-Server kopieren.

#### ODBC-Treiberinstallation {#odbc-installation}

Installieren des ODBC-Treibers:

1. Entpacken Sie die Datei tdodbc1620__linux_indep.16.20.00.00-1.tar.gz.

1. Wechseln Sie zum Verzeichnis „tdodbc1620“.

1. Möglicherweise müssen Sie das Setup-Skript korrigieren:

   ```
   "sed -i s/16.10/16.20/ setup_wrapper.sh".
   ```

1. Führen Sie setup_wrapper.sh aus.

#### Installation von Teradata-Tools und -Dienstprogrammen {#teradata-tools-installation}

Installieren der Tools:

1. Entpacken Sie die Datei TeradataToolsAndUtilitiesBase__linux_indep.16.20.01.00.tar.gz.

1. Wechseln Sie zum Verzeichnis „TeradataToolsAndUtilitiesBase/Linux/i386-x8664/tdicu“.

1. Führen Sie setup_wrapper.sh aus.

1. Wechseln Sie zum Verzeichnis „TeradataToolsAndUtilitiesBase/Linux/i386-x8664/cliv2“.

1. Führen Sie setup_wrapper.sh aus.

1. Wechseln Sie zum Verzeichnis „TeradataToolsAndUtilitiesBase/Linux/i386-x8664/tptbase“.

1. Führen Sie setup_wrapper.sh aus.

1. In „/opt/teradata/client/16.20/lib64“ sollte die Datei libtelapi.so verfügbar sein.

#### Treiberkonfiguration {#driver-configuration}

Weitere Informationen zur Treiberkonfiguration finden Sie in diesem [Abschnitt](../../platform/using/legacy-connectors.md#configure-access-to-teradata).

#### Umgebungsvariablen {#environment-varaiables}

Weitere Informationen zu den Umgebungsvariablen des Adobe Campaign-Servers finden Sie in diesem [Abschnitt](../../platform/using/legacy-connectors.md#configure-access-to-teradata).

### Campaign-Serverkonfiguration für Windows #campaign-server-Windows}

Zunächst müssen Sie Teradata-Tools und Dienstprogramme für Windows herunterladen. Sie können sie von dieser [Seite](https://downloads.teradata.com/download/tools/teradata-tools-and-utilities-windows-installation-package) herunterladen.

Installieren Sie unbedingt den ODBC-Treiber und die Teradata Parallel Transporter Base. telapi.dll wird installiert, was für Massenladevorgänge in die Teradata-Datenbank verwendet wird.

Stellen Sie sicher, dass der Pfad des Treibers und der Dienstprogramme in der PATH-Variablen steht, die während der Ausführung von nlserver verwendet wird. Der Standardpfad lautet „C:\Program Files (x86)\Teradata\Client\15.10\bin“ unter Windows 32 Bit oder „C:\Program Files\Teradata\Client\15.10\bin“ unter Windows 64 Bit.

### Fehlerbehebung bei externen Konten {#external-account-troubleshooting}

Wenn beim Testen der Verbindung der Fehler **TIM-030008 Datum &#39;2&#39;: fehlende Zeichen (iRc = -53)** auftritt, stellen Sie sicher, dass der ODBC-Treiber korrekt installiert ist und LD_LIBRARY_PATH (Linux)/PATH (Windows) für den Campaign-Server festlegt wurde.

Der Fehler **ODB-240000 ODBC-Fehler:[Microsoft][ODBC Driver Manager]-Datenquellenname nicht gefunden und kein Standardtreiber angegeben.** tritt unter Windows auf, wenn Sie einen 16.X-Treiber verwenden. Adobe Campaign erwartet, dass Teradata in odbcinst.ini den Namen „{teradata}“ hat.
Wenn die Version Ihres Adobe Campaign-Servers 18.10 lautet, können Sie ODBCDriverName=&quot;Teradata Database ODBC Driver 16.10&quot; in den Optionen des externen Kontos hinzufügen. Die Versionsnummer kann sich ändern. Führen Sie odbcad32.exe aus und gehen Sie zum Treiber-Tab, um den genauen Namen abzurufen.
Für Versionen älter als 18.10 müssen Sie den Teradata-Abschnitt der odbcinst.ini, der durch die Treiberinstallation erstellt wurde, in einen neuen Abschnitt mit dem Namen Teradata kopieren. In diesem Fall kann regedit verwendet werden.

Wenn Sie eine Latin-1-Datenbank verwenden, müssen Sie APICharSize=1 in den Optionen hinzufügen.

### Zeitzone {#timezone}

Teradata verwendet Zeitzonennamen, die nicht dem Standard entsprechen. Sie finden die Liste auf der [Teradata-Website](https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/oGKvgl7gCeBMTGrp59BnwA). Adobe Campaign versucht, die in der externen Konfiguration angegebene Zeitzone so umzuwandeln, dass sie von Teradata verstanden wird. Wenn keine Entsprechung gefunden wird, wird nach der nächstgelegenen GMT+X- (oder GMT-X)-Zeitzone für die Sitzung gesucht und eine Warnung im Protokoll vermerkt.

Die Konvertierung erfolgt durch Lesen einer Datei namens teradata_timezones.txt, die sich im folgenden datakit-Verzeichnis befinden sollte: /usr/local/neolane/nl6/datakit under Linux. Wenn Sie diese Datei bearbeiten, wenden Sie sich an das Adobe Campaign-Team, um die Änderungen im Quellcode vorzunehmen. Andernfalls wird diese Datei bei der nächsten Campaign-Aktualisierung überschrieben.

Die für die Verbindung verwendete Zeitzone wird angezeigt, wenn nlserver mit -verbose ausgeführt wird, z. B.:

```
15:04:04 >   ODB-240007 Teradata: will use 'Europe Central' as session time zone.
```

Wenn die verwendete Zeitzone nicht die richtige ist, kann eine Option mit dem Namen &quot;TimeZoneName&quot; im externen Konto hinzugefügt werden. Verwenden Sie in diesem Fall den Wert von Teradata, z. B. &quot;TimeZoneName=Europe Central&quot;.

Bei Massenladevorgängen oder Schnellladevorgängen (Fast Load) in Teradata-Dokumenten kann Campaign die Zeitzone nicht angeben. Es wird daher empfohlen, die Standardzeitzone des Benutzers festzulegen, über den Campaign die Verbindung herstellt:

```
MODIFY USER $login$ AS TIME ZONE = 'Europe Central';
```

## MySQL 5.7-Konfiguration {#mysql-57-configuration}

### Serverkonfiguration {#server-configuration-mysql}

Für die Serverkonfiguration sind keine spezifischen Installationsschritte erforderlich. Adobe Campaign sollte mit einer Latin-1-Datenbank (standardmäßig MySQL) oder einer Unicode-Datenbank verwendet werden.

### Treiberinstallation {#driver-installation-mysql}

#### Debian {#debian-mysql}

Laden Sie mysql-apt-config.deb von dieser [Seite](https://dev.mysql.com/doc/mysql-apt-repo-quick-guide/en) herunter.

Installieren Sie die Client-Bibliothek:

```
$ dpkg -i mysql-apt-config_*_all.deb # choose mysql-5.7 in the configuration menu
$ apt update
$ apt install libmysqlclient20
```

#### Windows {#windows-mysql}

Laden Sie den C-Connector von dieser [Seite](https://dev.mysql.com/downloads/connector/c) herunter. Es wird empfohlen, Version 5.7 herunterzuladen.

Stellen Sie sicher, dass das Verzeichnis, das libmysqlclient.dll enthält, der Umgebungsvariablen PATH hinzugefügt wird, die von nlserver verwendet werden wird.

#### CentOS {#centos-mysql}

Laden Sie mysql57-community-release.noarch.rpm von dieser [Seite](https://dev.mysql.com/downloads/repo/yum) herunter.

Installieren Sie die Client-Bibliothek:

$ yum install mysql57-community-release-el7-9.noarch.rpm
$ yum install mysql-community-libs

### Konfiguration des externen Kontos {#external-account-mysql}

Für die Konfiguration des externen Kontos sind keine spezifischen Schritte erforderlich. Stellen Sie sicher, dass die Zeitzone und die Verwendung von Unicode-Daten entsprechend Ihrer Datenbank eingestellt sind.
