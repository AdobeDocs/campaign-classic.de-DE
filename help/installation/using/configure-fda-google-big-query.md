---
product: campaign
title: Zugriff auf Google BigQuery konfigurieren
description: Erfahren Sie, wie Sie den Zugriff auf Google BigQuery in FDA konfigurieren
feature: Installation, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: ebaad59f-0607-4090-92d0-e457fbf9a348
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '1010'
ht-degree: 7%

---

# Zugriff auf Google BigQuery konfigurieren {#configure-fda-google-big-query}



Verwenden Sie **Option „Federated Data Access** (FDA) von Adobe Campaign Classic, um in einer externen Datenbank gespeicherte Informationen zu verarbeiten. Gehen Sie wie folgt vor, um den Zugriff auf [!DNL Google BigQuery] zu konfigurieren.

1. Konfigurieren von [!DNL Google BigQuery] unter [Windows](#google-windows) oder [Linux](#google-linux)
1. Konfigurieren des [!DNL Google BigQuery] [externen Kontos](#google-external) in Adobe Campaign Classic
1. Einrichten [!DNL Google BigQuery] Massenladevorgangs des Connectors unter [Windows](#bulk-load-windows) oder [Linux](#bulk-load-linux)

>[!NOTE]
>
> [!DNL Google BigQuery] Connector ist für gehostete, Hybrid- und On-Premise-Bereitstellungen verfügbar. Weitere Informationen hierzu finden Sie auf [dieser Seite](../../installation/using/capability-matrix.md).

![](assets/snowflake_3.png)

## Google BigQuery unter Windows {#google-windows}

### Treibereinrichtung unter Windows {#driver-window}

1. Laden Sie den [ODBC-Treiber für Windows](https://cloud.google.com/bigquery/docs/reference/odbc-jdbc-drivers) herunter.

1. Konfigurieren Sie den ODBC-Treiber unter Windows. Weitere Informationen hierzu finden Sie auf [dieser Seite](https://storage.googleapis.com/simba-bq-release/jdbc/Simba%20JDBC%20Driver%20for%20Google%20BigQuery%20Install%20and%20Configuration%20Guide.pdf).

1. Damit der [!DNL Google BigQuery]-Connector funktioniert, erfordert Adobe Campaign Classic die folgenden Parameter, um eine Verbindung herzustellen:

   * **[!UICONTROL Projekt]**: Erstellen oder verwenden Sie ein vorhandenes Projekt.

     Weiterführende Informationen dazu finden Sie auf dieser [Seite](https://cloud.google.com/resource-manager/docs/creating-managing-projects).

   * **[!UICONTROL Service-Konto]**: Erstellen eines Service-Kontos.

     Weiterführende Informationen dazu finden Sie auf dieser [Seite](https://cloud.google.com/iam/docs/creating-managing-service-accounts).

   * **[!UICONTROL Key File Path]**: Das **[!UICONTROL Service-]** erfordert eine **[!UICONTROL Key File]** für eine [!DNL Google BigQuery] Verbindung über ODBC.

     Weiterführende Informationen dazu finden Sie auf dieser [Seite](https://cloud.google.com/iam/docs/creating-managing-service-account-keys).

   * **[!UICONTROL Dataset]**: **[!UICONTROL Dataset]** ist für eine ODBC-Verbindung optional. Da jede Abfrage den Datensatz bereitstellen muss, in dem sich die Tabelle befindet, ist die Angabe eines **[!UICONTROL Datensatzes]** für [!DNL Google BigQuery] FDA-Connector in Adobe Campaign Classic obligatorisch.

     Weiterführende Informationen dazu finden Sie auf dieser [Seite](https://cloud.google.com/bigquery/docs/datasets).

1. In Adobe Campaign Classic können Sie dann Ihr externes [!DNL Google BigQuery]-Konto konfigurieren. Weiterführende Informationen zur Konfiguration Ihres externen Kontos finden Sie in [diesem Abschnitt](#google-external).

### Massenladeeinrichtung unter Windows {#bulk-load-window}

>[!NOTE]
>
>Damit Google Cloud SDK funktioniert, muss Python installiert sein.
>
>Wir empfehlen die Verwendung von Python3, siehe diese [Seite](https://www.python.org/downloads/).

Das Dienstprogramm für das Massenladen ermöglicht eine schnellere Übertragung, die durch Google Cloud SDK erreicht wird.

1. Laden Sie das Windows 64-Bit-Archiv (x86_64) von dieser [Seite](https://cloud.google.com/sdk/docs/downloads-versioned-archives) herunter und extrahieren Sie es in das entsprechende Verzeichnis.

1. Ausführen des `google-cloud-sdk\install.sh`. Sie müssen die Einstellung der Pfadvariablen akzeptieren.

1. Überprüfen Sie nach der Installation, ob die Pfadvariable `...\google-cloud-sdk\bin` festgelegt ist. Falls nicht, fügen Sie sie manuell hinzu.

1. Fügen Sie in der `..\google-cloud-sdk\bin\bq.cmd`-Datei die `CLOUDSDK_PYTHON` lokale Variable hinzu, die zum Speicherort der Python-Installation umgeleitet wird.

   Beispiel:

   ![](assets/google-big-query_1.png)

1. Starten Sie Adobe Campaign Classic neu, damit die Änderungen berücksichtigt werden.

## Google BigQuery unter Linux {#google-linux}

### Treibereinrichtung unter Linux {#driver-linux}

Beachten Sie vor dem Einrichten des Treibers, dass Skript und Befehle vom Root-Benutzer ausgeführt werden müssen. Es wird außerdem empfohlen, beim Ausführen des Skripts Google-DNS-8.8.8.8 zu verwenden.

Gehen Sie wie folgt vor, um [!DNL Google BigQuery] unter Linux zu konfigurieren:

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

1. System vor der Installation aktualisieren:

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

1. Bevor Sie das Skript ausführen, können Sie weitere Informationen erhalten, indem Sie das Argument —help angeben:

   ```
   cd /usr/local/neolane/nl6/bin/fda-setup-scripts
   ./bigquery_odbc-setup.sh --help
   ```

1. Greifen Sie auf das Verzeichnis zu, in dem sich das Skript befindet, und führen Sie das folgende Skript als Root-Benutzer aus:

   ```
   cd /usr/local/neolane/nl6/bin/fda-setup-scripts
   ./bigquery_odbc-setup.sh
   ```

### Massenladeeinrichtung unter Linux {#bulk-load-linux}

>[!NOTE]
>
>Damit Google Cloud SDK funktioniert, muss Python installiert sein.
>
>Wir empfehlen die Verwendung von Python3, siehe diese [Seite](https://www.python.org/downloads/).

Das Dienstprogramm für das Massenladen ermöglicht eine schnellere Übertragung, die durch Google Cloud SDK erreicht wird.

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

1. Greifen Sie auf das Verzeichnis zu, in dem sich das Skript befindet, und führen Sie das folgende Skript aus:

   ```
   cd /usr/local/neolane/nl6/bin/fda-setup-scripts
   ./bigquery_sdk-setup.sh
   ```

## Externes Google BigQuery-Konto {#google-external}

Sie müssen ein [!DNL Google BigQuery] externes Konto erstellen, um Ihre Adobe Campaign Classic-Instanz mit Ihrer [!DNL Google BigQuery] externen Datenbank zu verbinden.

1. Adobe Campaign Classic Klicken Sie im **[!UICONTROL Explorer]** auf **[!UICONTROL Administration]** &quot;>&quot; **[!UICONTROL Plattform]** &quot;>&quot; **[!UICONTROL Externe Konten]**.

1. Wählen Sie **[!UICONTROL Neu]** aus.

1. Wählen Sie **[!UICONTROL Externe Datenbank]** als **[!UICONTROL Typ]** Ihres externen Kontos aus.

1. Konfigurieren Sie das externe [!DNL Google BigQuery]-Konto; geben Sie dazu Folgendes an:

   * **[!UICONTROL Typ]**: [!DNL Google BigQuery]

   * **[!UICONTROL Service-]**: E-Mail Ihres **[!UICONTROL Service-Kontos]**. Weiterführende Informationen dazu finden Sie in der [Dokumentation zu Google Cloud](https://cloud.google.com/iam/docs/creating-managing-service-accounts).

   * **[!UICONTROL Projekt]**: Name Ihres **[!UICONTROL Projekts]**. Weiterführende Informationen dazu finden Sie in der [Dokumentation zu Google Cloud](https://cloud.google.com/resource-manager/docs/creating-managing-projects).

   * **[!UICONTROL Schlüsseldateipfad]**:
      * **[!UICONTROL Schlüsseldatei auf den Server hochladen]**: Wählen Sie **[!UICONTROL Zum Hochladen hier klicken]** aus, wenn Sie den Schlüssel über Adobe Campaign Classic hochladen möchten.

      * **[!UICONTROL Manuelles Eingeben des Pfads der Schlüsseldatei]**: Kopieren Sie Ihren absoluten Pfad in dieses Feld, wenn Sie einen bereits vorhandenen Schlüssel verwenden möchten.

   * **[!UICONTROL Datensatz]**: Name Ihres **[!UICONTROL Datensatzes]**. Weiterführende Informationen dazu finden Sie in der [Dokumentation zu Google Cloud](https://cloud.google.com/bigquery/docs/datasets-intro).

   ![](assets/google-big-query.png)

Der Connector unterstützt die folgenden Optionen:

| Option | Beschreibung  |
|:-:|:-:|
| ProxyType | Proxy-Typ, der zum Herstellen einer Verbindung mit BigQuery über ODBC- und SDK-Connectoren verwendet wird. </br>HTTP (Standard), http_no_tunnel, socks4 und socks5 werden derzeit unterstützt. |
| ProxyHost | Hostname oder IP-Adresse, unter der der Proxy erreichbar ist. |
| ProxyPort | Portnummer, auf der der Proxy ausgeführt wird, z. B. 8080 |
| ProxyUid | Benutzername für den authentifizierten Proxy |
| proxyPwd | ProxyUid-Kennwort |
| bqpath | Beachten Sie, dass dies nur für das Tool für Massenladevorgänge gilt (Cloud SDK). </br> Um die Verwendung der PATH-Variablen zu vermeiden oder wenn der Ordner „google-cloud-sdk“ an einen anderen Speicherort verschoben werden muss, können Sie mit dieser Option den genauen Pfad zum Ordner „bin“ des Cloud-SDK auf dem Server angeben. |
| GCloudConfigName | Beachten Sie, dass dies ab Version 7.3.4 gilt und nur für das Tool für Massenladevorgänge (Cloud SDK).</br> Die Google Cloud SDK verwendet Konfigurationen zum Laden von Daten in BigQuery-Tabellen. Die Konfiguration mit dem Namen `accfda` speichert die Parameter zum Laden der Daten. Diese Option ermöglicht es Benutzenden jedoch, einen anderen Namen für die Konfiguration anzugeben. |
| GCloudDefaultConfigName | Beachten Sie, dass dies ab Version 7.3.4 gilt und nur für das Tool für Massenladevorgänge (Cloud SDK).</br> Die aktive Google Cloud SDK-Konfiguration kann nicht gelöscht werden, ohne das aktive Tag zuerst an eine neue Konfiguration zu übertragen. Diese temporäre Konfiguration ist erforderlich, um die Hauptkonfiguration zum Laden von Daten neu zu erstellen. Der Standardname für die temporäre Konfiguration lautet `default`. Dieser kann bei Bedarf geändert werden. |
| GCloudRecreateConfig | Beachten Sie, dass dies ab Version 7.3.4 gilt und nur für das Tool für Massenladevorgänge (Cloud SDK).</br> Bei Festlegung auf `false` versucht der Massenlademechanismus nicht, die Google Cloud SDK-Konfigurationen neu zu erstellen, zu löschen oder zu ändern. Stattdessen werden die Daten unter Verwendung der auf dem Computer vorhandenen Konfiguration geladen. Diese Funktion ist nützlich, wenn andere Vorgänge von Google Cloud SDK-Konfigurationen abhängen. </br> Wenn der Benutzer diese Engine-Option ohne ordnungsgemäße Konfiguration aktiviert, gibt der Massenlademechanismus eine Warnmeldung aus: `No active configuration found. Please either create it manually or remove the GCloudRecreateConfig option`. Um weitere Fehler zu vermeiden, wird auf die Verwendung des standardmäßigen Massenlademechanismus zum Einfügen von ODBC-Arrays zurückgegriffen. |

