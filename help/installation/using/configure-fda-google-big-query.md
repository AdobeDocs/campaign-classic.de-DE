---
product: campaign
title: Zugriff auf Google BigQuery konfigurieren
description: Erfahren Sie, wie Sie den Zugriff auf Google BigQuery in FDA konfigurieren
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: platform
content-type: reference
topic-tags: connectors
exl-id: ebaad59f-0607-4090-92d0-e457fbf9a348
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '845'
ht-degree: 9%

---

# Zugriff auf Google BigQuery konfigurieren {#configure-fda-google-big-query}



Verwenden von Adobe Campaign Classic **Federated Data Access** (FDA), um in einer externen Datenbank gespeicherte Informationen zu verarbeiten. Gehen Sie wie folgt vor, um den Zugriff auf [!DNL Google BigQuery].

1. Konfigurieren [!DNL Google BigQuery] on [Windows](#google-windows) oder [Linux](#google-linux)
1. Konfigurieren Sie die [!DNL Google BigQuery] [externes Konto](#google-external) in Adobe Campaign Classic
1. Einrichten [!DNL Google BigQuery] Bulk-Load des Connectors [Windows](#bulk-load-windows) oder [Linux](#bulk-load-linux)

>[!NOTE]
>
> [!DNL Google BigQuery] Connector ist für gehostete, hybride und On-Premise-Implementierungen verfügbar. Weitere Informationen hierzu finden Sie auf [dieser Seite](../../installation/using/capability-matrix.md).

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

Beachten Sie vor dem Einrichten des Treibers, dass Skript und Befehle vom Root-Benutzer ausgeführt werden müssen. Es wird außerdem empfohlen, während der Skripterstellung das Google DNS 8.8.8.8 zu verwenden.

So konfigurieren Sie [!DNL Google BigQuery] Gehen Sie unter Linux wie folgt vor:

1. Überprüfen Sie vor der ODBC-Installation, ob die folgenden Pakete auf Ihrer Linux-Distribution installiert sind:

   * Für Red Hat/CentOS:

     ```
     yum update
     yum upgrade
     yum install -y grep sed tar wget perl curl
     ```

   * Für Debian:

     ```
     apt-get update
     apt-get upgrade
     apt-get install -y grep sed tar wget perl curl
     ```

1. Aktualisieren Sie das System vor der Installation:

   * Für Red Hat/CentOS:

     ```
     # install unixODBC driver manager
     yum install -y unixODBC
     ```

   * Für Debian:

     ```
     # install unixODBC driver manager
     apt-get install -y odbcinst1debian2 libodbc1 odbcinst unixodbc
     ```

1. Bevor Sie das Skript ausführen, können Sie weitere Informationen abrufen, indem Sie das —help-Argument angeben:

   ```
   cd /usr/local/neolane/nl6/bin/fda-setup-scripts
   ./bigquery_odbc-setup.sh --help
   ```

1. Rufen Sie den Ordner auf, in dem sich das Skript befindet, und führen Sie das folgende Skript als Stammbenutzer aus:

   ```
   cd /usr/local/neolane/nl6/bin/fda-setup-scripts
   ./bigquery_odbc-setup.sh
   ```

### Massenladeeinrichtung unter Linux {#bulk-load-linux}

>[!NOTE]
>
>Damit das Google Cloud SDK funktioniert, muss Python installiert sein.
>
>Wir empfehlen die Verwendung von Python3, siehe dies [page](https://www.python.org/downloads/).

Das Bulk Load-Dienstprogramm ermöglicht eine schnellere Übertragung, die über das Google Cloud SDK erreicht wird.

1. Überprüfen Sie vor der ODBC-Installation, ob die folgenden Pakete auf Ihrer Linux-Distribution installiert sind:

   * Für Red Hat/CentOS:

     ```
     yum update
     yum upgrade
     yum install -y python3
     ```

   * Für Debian:

     ```
     apt-get update
     apt-get upgrade
     apt-get install -y python3
     ```

1. Rufen Sie den Ordner auf, in dem sich das Skript befindet, und führen Sie das folgende Skript aus:

   ```
   cd /usr/local/neolane/nl6/bin/fda-setup-scripts
   ./bigquery_sdk-setup.sh
   ```

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

Der Connector unterstützt die folgenden Optionen:

| Option | Beschreibung  |
|:-:|:-:|
| ProxyType | Typ des Proxys, der verwendet wird, um über ODBC- und SDK-Connectoren eine Verbindung zu BigQuery herzustellen. </br>HTTP (Standard), http_no_tunnel, socks4 und socks5 werden derzeit unterstützt. |
| ProxyHost | Hostname oder IP-Adresse, an der der Proxy erreicht werden kann. |
| ProxyPort | Anschlussnummer, auf der der Proxy ausgeführt wird, z. B. 8080 |
| ProxyUid | Benutzername, der für den authentifizierten Proxy verwendet wird |
| ProxyPwd | ProxyUid-Kennwort |
| bqpath | Beachten Sie, dass dies nur für Tools mit Massenladevorgang (Cloud SDK) gilt. </br> Um die Verwendung der PATH-Variablen zu vermeiden oder den Ordner google-cloud-sdk an einen anderen Speicherort zu verschieben, können Sie mit dieser Option den genauen Pfad zum Ordner &quot;cloud sdk bin&quot;auf dem Server angeben. |
