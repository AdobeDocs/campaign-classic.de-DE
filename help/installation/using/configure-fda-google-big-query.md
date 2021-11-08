---
product: campaign
title: Zugriff auf Google BigQuery konfigurieren
description: Erfahren Sie, wie Sie den Zugriff auf Google BigQuery in FDA konfigurieren
audience: platform
content-type: reference
topic-tags: connectors
exl-id: ebaad59f-0607-4090-92d0-e457fbf9a348
source-git-commit: 6d53ba957fb567a9a921544418a73a9bde37c97b
workflow-type: tm+mt
source-wordcount: '955'
ht-degree: 7%

---

# Zugriff auf Google BigQuery konfigurieren {#configure-fda-google-big-query}

![](../../assets/v7-only.svg)

Verwenden von Adobe Campaign Classic **Federated Data Access** (FDA), um in einer externen Datenbank gespeicherte Informationen zu verarbeiten. Gehen Sie wie folgt vor, um den Zugriff auf [!DNL Google BigQuery].

1. Konfigurieren [!DNL Google BigQuery] on [Windows](#google-windows) oder [Linux](#google-linux)
1. Konfigurieren Sie die [!DNL Google BigQuery] [externes Konto](#google-external) in Adobe Campaign Classic
1. Einrichten [!DNL Google BigQuery] Bulk-Load des Connectors [Windows](#bulk-load-windows) oder [Linux](#bulk-load-linux)

>[!NOTE]
>
> [!DNL Google BigQuery] Connector ist für hybride und On-Premise-Implementierungen verfügbar. Weitere Informationen hierzu finden Sie auf [dieser Seite](../../installation/using/capability-matrix.md).

![](assets/snowflake_3.png)

## Google BigQuery unter Windows {#google-windows}

### Treiber unter Windows eingerichtet {#driver-window}

1. Laden Sie den [ODBC-Treiber für Windows](https://cloud.google.com/bigquery/docs/reference/odbc-jdbc-drivers) herunter.

1. Konfigurieren Sie den ODBC-Treiber unter Windows. Weitere Informationen hierzu finden Sie auf [dieser Seite](https://storage.googleapis.com/simba-bq-release/jdbc/Simba%20JDBC%20Driver%20for%20Google%20BigQuery%20Install%20and%20Configuration%20Guide.pdf).

1. Für [!DNL Google BigQuery] -Connector verwenden, erfordert Adobe Campaign Classic die folgenden Parameter für die Verbindung:

   * **[!UICONTROL Projekt]**: ein vorhandenes Projekt erstellen oder verwenden.

      Weiterführende Informationen dazu finden Sie auf dieser [Seite](https://cloud.google.com/resource-manager/docs/creating-managing-projects).

   * **[!UICONTROL Dienstkonto]**: ein Dienstkonto erstellen.

      Weiterführende Informationen dazu finden Sie auf dieser [Seite](https://cloud.google.com/iam/docs/creating-managing-service-accounts).

   * **[!UICONTROL Pfad der Schlüsseldatei]**: die **[!UICONTROL Dienstkonto]** erfordert **[!UICONTROL Schlüsseldatei]** für [!DNL Google BigQuery] Verbindung über ODBC.

      Weiterführende Informationen dazu finden Sie auf dieser [Seite](https://cloud.google.com/iam/docs/creating-managing-service-account-keys).

   * **[!UICONTROL Datensatz]**: **[!UICONTROL Datensatz]** ist für eine ODBC-Verbindung optional. Da jede Abfrage den Datensatz bereitstellen muss, in dem sich die Tabelle befindet, muss eine **[!UICONTROL Datensatz]** ist zwingend erforderlich für [!DNL Google BigQuery] FDA-Connector in Adobe Campaign Classic.

      Weiterführende Informationen dazu finden Sie auf dieser [Seite](https://cloud.google.com/bigquery/docs/datasets).

1. In Adobe Campaign Classic können Sie dann Ihre [!DNL Google BigQuery] externes Konto. Weitere Informationen zur Konfiguration Ihres externen Kontos finden Sie unter [diesem Abschnitt](#google-external).

### Massenladeeinrichtung unter Windows {#bulk-load-window}

>[!NOTE]
>
>Damit das Google Cloud SDK funktioniert, muss Python installiert sein.
>
>Wir empfehlen die Verwendung von Python3, siehe dies [page](https://www.python.org/downloads/).

Das Bulk Load-Dienstprogramm ermöglicht eine schnellere Übertragung, die über das Google Cloud SDK erreicht wird.

1. Laden Sie das 64-Bit-Archiv für Windows (x86_64) von diesem herunter [page](https://cloud.google.com/sdk/docs/downloads-versioned-archives) und extrahieren Sie sie in das entsprechende Verzeichnis.

1. Führen Sie die `google-cloud-sdk\install.sh` Skript. Sie müssen die Einstellung der Pfadvariablen akzeptieren.

1. Überprüfen Sie nach der Installation, ob die Pfadvariable `...\google-cloud-sdk\bin` festgelegt ist. Wenn nicht, fügen Sie es manuell hinzu.

1. Im  `..\google-cloud-sdk\bin\bq.cmd` -Datei, fügen Sie die `CLOUDSDK_PYTHON` lokale Variable, die zum Speicherort der Python-Installation umleitet.

   Beispiel:

   ![](assets/google-big-query_1.png)

1. Starten Sie Adobe Campaign Classic neu, damit die Änderungen berücksichtigt werden.

## Google BigQuery unter Linux {#google-linux}

### Treiber für Linux eingerichtet {#driver-linux}

1. Vor der Installation des ODBC-Treibers müssen Sie Ihr System aktualisieren. Führen Sie unter Linux oder CentOS den folgenden Befehl aus:

   ```
   yum update
   # install unixODBC driver manager
   yum install unixODBC
   ```

1. Anschließend müssen Sie den UnixODBC-Treiber-Manager mit dem folgenden Befehl installieren:

   ```
   # switch to root user
   sudo su
   ```

   Unter Debian:

   ```
   apt-get update
   apt-get upgrade
   # install unixODBC driver manager
   apt-get install unixODBC
   ```

1. Laden Sie die [Magnitude Simba Linux ODBC-Treiber (.tar.gz)](https://cloud.google.com/bigquery/docs/reference/odbc-jdbc-drivers). Übertragen Sie dann die Tarball-Datei in einen temporären Ordner auf Ihrem Computer oder verwenden Sie den Befehl wget :

   ```
   # in this example driver version is 2.3.1.1001
   wget https://storage.googleapis.com/simba-bq-release/odbc/SimbaODBCDriverforGoogleBigQuery_[Version]-Linux.tar.gz
   ```

1. Extrahieren Sie die Tarball-Hauptdatei wie folgt: **TarballName** ist der Name des tarball-Pakets, das den Treiber enthält:

   ```
   tar --directory=/tmp -zxvf [TarballName]
   ```

1. Rufen Sie den Ordner auf, den Sie extrahiert haben, und extrahieren Sie die innere Tarball-Datei, die der Version des Treibers entspricht. Installieren Sie es in einen anderen temporären Ordner, im folgenden Beispiel BigQueryDriver:

   ```
   mkdir /tmp/BigQueryDriver/
   cd /tmp/SimbaODBCDriverforGoogleBigQuery_[Version]-Linux/
   tar --directory=/tmp/BigQueryDriver/ -zxvf SimbaODBCDriverforGoogleBigQuery[Bitness]_[Version].tar.gz
   ```

1. Rufen Sie den temporären Speicherort auf, an dem die Haupt-Tarball-Datei extrahiert wurde, und kopieren Sie die `GoogleBigQueryODBC.did` und `setup/simba.googlebigqueryodbc.ini` Dateien in den neuen Ordner, der im vorherigen Schritt erstellt wurde:

   ```
   cd /tmp/SimbaODBCDriverforGoogleBigQuery_[Version]-Linux/
   cp GoogleBigQueryODBC.did /tmp/BigQueryDriver/SimbaODBCDriverforGoogleBigQuery[Bitness]_[Version]/lib/
   cp setup/simba.googlebigqueryodbc.ini /tmp/BigQueryDriver/SimbaODBCDriverforGoogleBigQuery[Bitness]_[Version]/lib/
   ```

1. Erstellen Sie den Installationsordner wie folgt:

   ```
   mkdir -p /opt/simba/googlebigqueryodbc/
   ```

1. Kopieren Sie den Inhalt des Ordners in den neuen Installationsordner:

   ```
   cp -r /tmp/BigQueryDriver/SimbaODBCDriverforGoogleBigQuery[Bitness]_[Version]/* /opt/simba/googlebigqueryodbc/
   ```

1. Ersetzen `<INSTALLDIR>` mit `/opt/simba/googlebigqueryodbc` in `simba.googlebigqueryodbc.ini` im Installationsverzeichnis:

   ```
   cd /opt/simba/googlebigqueryodbc/lib/
   sed -i 's/<INSTALLDIR>/\/opt\/simba\/googlebigqueryodbc/g' simba.googlebigqueryodbc.ini
   ```

1. Ändern Sie die `DriverManagerEncoding` auf UTF-16 und `SwapFilePath` in `simba.googlebigqueryodbc.ini`. Bei Bedarf können Sie auch die Protokollierungseinstellungen ändern.

   Im Folgenden finden Sie ein Beispiel für eine aktualisierte Konfigurationsdatei für den gesamten Treiber:

   ```
   # /opt/simba/googlebigqueryodbc/lib/simba.googlebigqueryodbc.ini
   [Driver]
   DriverManagerEncoding=UTF-16
   ErrorMessagesPath=opt/simba/googlebigqueryodbc/ErrorMessages
   LogLevel=6
   LogPath=/tmp
   SwapFilePath=/tmp
   ```

1. Wenn Sie eine Treiberdatei für das System oder eine aktuelle `odbcinst.ini` Datei, konfigurieren `/etc/odbcinst.ini` , um auf den Google BigQuery-Treiber-Speicherort zu verweisen `/opt/simba/googlebigqueryodbc/lib/libgooglebigqueryodbc_sb[Bitness].so`.

   Beispiel:

   ```
   # /etc/odbcinst.ini
   # Make sure to use Simba ODBC Driver for Google BigQuery as a driver name.
   
   [ODBC Drivers]
   Simba ODBC Driver for Google BigQuery=Installed
   
   [Simba ODBC Driver for Google BigQuery]
   Description=Simba ODBC Driver for Google BigQuery(64-bit)
   Driver=/opt/simba/googlebigqueryodbc/lib/libgooglebigqueryodbc_sb64.so
   ```

1. Suchen Sie den Speicherort der UnixODBC-Treiber-Manager-Bibliotheken und fügen Sie die `unixODBC` und `googlebigqueryodbc` Bibliothekspfade zu `LD_LIBRARY_PATH environment` -Variable.

   ```
   find / -name 'lib*odbc*.so*' -print
   #output:
   /usr/lib/x86_64-linux-gnu/libodbccr.so.2
   /usr/lib/x86_64-linux-gnu/libodbcinst.so.2.0.0
   /usr/lib/x86_64-linux-gnu/libodbccr.so.1
   .
   .
   /opt/simba/googlebigqueryodbc/lib/libgooglebigqueryodbc_sb64.so
   
   #the command would look like this
   export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/opt/simba/googlebigqueryodbc:/usr/lib
   ```

1. In Adobe Campaign Classic können Sie dann Ihre [!DNL Google BigQuery] externes Konto. Weitere Informationen zur Konfiguration Ihres externen Kontos finden Sie unter [diesem Abschnitt](#google-external).

### Massenladeeinrichtung unter Linux {#bulk-load-linux}

>[!NOTE]
>
>Damit das Google Cloud SDK funktioniert, muss Python installiert sein.
>
>Wir empfehlen die Verwendung von Python3, siehe dies [page](https://www.python.org/downloads/).

Das Bulk Load-Dienstprogramm ermöglicht eine schnellere Übertragung, die über das Google Cloud SDK erreicht wird.

1. Laden Sie das 64-Bit-Archiv von Linux (x86_64) in dieses [page](https://cloud.google.com/sdk/docs/downloads-versioned-archives) und im entsprechenden Verzeichnis extrahieren.

1. Führen Sie die `google-cloud-sdk\install.sh` Skript. Sie müssen die Einstellung der Pfadvariablen akzeptieren.

1. Überprüfen Sie nach der Installation, ob die Pfadvariable `...\google-cloud-sdk\bin` festgelegt ist. Wenn nicht, fügen Sie es manuell hinzu.

1. Wenn Sie die Verwendung der `PATH` oder wenn Sie die Variable `google-cloud-sdk` Verzeichnis an einen anderen Speicherort verweisen, verwenden Sie die `bqpath` Optionswert beim Konfigurieren der **[!UICONTROL Externes Konto]** um den genauen Pfad zum Ordner &quot;bin&quot;auf Ihrem System anzugeben.

1. Starten Sie Adobe Campaign Classic neu, damit die Änderungen berücksichtigt werden.

## Externes Google BigQuery-Konto {#google-external}

Sie müssen eine [!DNL Google BigQuery] Externes Konto zum Verbinden Ihrer Adobe Campaign Classic-Instanz mit Ihrer [!DNL Google BigQuery] externe Datenbank.

1. Aus Adobe Campaign Classic **[!UICONTROL Explorer]** klicken **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Plattform]** &#39;>&#39; **[!UICONTROL Externe Konten]**.

1. Wählen Sie **[!UICONTROL Neu]** aus.

1. Wählen Sie **[!UICONTROL Externe Datenbank]** als **[!UICONTROL Typ]** Ihres externen Kontos aus.

1. Konfigurieren Sie das externe [!DNL Google BigQuery]-Konto; geben Sie dazu Folgendes an:

   * **[!UICONTROL Typ]**: [!DNL Google BigQuery]

   * **[!UICONTROL Dienstkonto]**: E-Mail Ihrer **[!UICONTROL Dienstkonto]**. Weitere Informationen hierzu finden Sie unter [Dokumentation zu Google Cloud](https://cloud.google.com/iam/docs/creating-managing-service-accounts).

   * **[!UICONTROL Projekt]**: Name Ihres **[!UICONTROL Projekt]**. Weitere Informationen hierzu finden Sie unter [Dokumentation zu Google Cloud](https://cloud.google.com/resource-manager/docs/creating-managing-projects).

   * **[!UICONTROL Pfad der Schlüsseldatei]**:
      * **[!UICONTROL Laden Sie die Schlüsseldatei auf den Server hoch]**: select **[!UICONTROL Hier klicken zum Hochladen]** , wenn Sie den Schlüssel über Adobe Campaign Classic hochladen möchten.

      * **[!UICONTROL Geben Sie den Pfad der Schlüsseldatei manuell ein]**: Kopieren/fügen Sie Ihren absoluten Pfad in dieses Feld ein, wenn Sie einen bereits vorhandenen Schlüssel verwenden möchten.
   * **[!UICONTROL Datensatz]**: Name Ihres **[!UICONTROL Datensatz]**. Weitere Informationen hierzu finden Sie unter [Dokumentation zu Google Cloud](https://cloud.google.com/bigquery/docs/datasets-intro).
   ![](assets/google-big-query.png)
