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



Verwenden Sie die Option Adobe Campaign Classic **Federated Data Access** (FDA), um in einer externen Datenbank gespeicherte Informationen zu verarbeiten. Gehen Sie wie folgt vor, um den Zugriff auf [!DNL Google BigQuery] zu konfigurieren.

1. Konfigurieren Sie [!DNL Google BigQuery] für [Windows](#google-windows) oder [Linux](#google-linux)
1. Konfigurieren des externen [!DNL Google BigQuery] [-Kontos](#google-external) in Adobe Campaign Classic
1. Richten Sie [!DNL Google BigQuery] Massenladevorgänge des Connectors unter [Windows](#bulk-load-windows) oder [Linux](#bulk-load-linux) ein.

>[!NOTE]
>
> Der [!DNL Google BigQuery]-Connector ist für gehostete, hybride und On-Premise-Implementierungen verfügbar. Weitere Informationen hierzu finden Sie auf [dieser Seite](../../installation/using/capability-matrix.md).

![](assets/snowflake_3.png)

## Google BigQuery unter Windows {#google-windows}

### Treiber unter Windows eingerichtet {#driver-window}

1. Laden Sie den ODBC-Treiber für Windows](https://cloud.google.com/bigquery/docs/reference/odbc-jdbc-drivers) herunter.[

1. Konfigurieren Sie den ODBC-Treiber unter Windows. Weitere Informationen hierzu finden Sie auf [dieser Seite](https://storage.googleapis.com/simba-bq-release/jdbc/Simba%20JDBC%20Driver%20for%20Google%20BigQuery%20Install%20and%20Configuration%20Guide.pdf).

1. Damit der [!DNL Google BigQuery] -Connector funktioniert, müssen für Adobe Campaign Classic die folgenden Parameter für die Verbindung verwendet werden:

   * **[!UICONTROL Projekt]**: Erstellen oder Verwenden eines vorhandenen Projekts.

     Weiterführende Informationen dazu finden Sie auf dieser [Seite](https://cloud.google.com/resource-manager/docs/creating-managing-projects).

   * **[!UICONTROL Dienstkonto]**: Erstellen Sie ein Dienstkonto.

     Weiterführende Informationen dazu finden Sie auf dieser [Seite](https://cloud.google.com/iam/docs/creating-managing-service-accounts).

   * **[!UICONTROL Pfad der Schlüsseldatei]**: Für das **[!UICONTROL Dienstkonto]** ist eine **[!UICONTROL Schlüsseldatei]** für eine [!DNL Google BigQuery]-Verbindung über ODBC erforderlich.

     Weiterführende Informationen dazu finden Sie auf dieser [Seite](https://cloud.google.com/iam/docs/creating-managing-service-account-keys).

   * **[!UICONTROL Datensatz]**: **[!UICONTROL Datensatz]** ist für eine ODBC-Verbindung optional. Da jede Abfrage den Datensatz bereitstellen muss, in dem sich die Tabelle befindet, ist die Angabe eines **[!UICONTROL Datensatzes]** für den [!DNL Google BigQuery] FDA-Connector in Adobe Campaign Classic obligatorisch.

     Weiterführende Informationen dazu finden Sie auf dieser [Seite](https://cloud.google.com/bigquery/docs/datasets).

1. In Adobe Campaign Classic können Sie dann Ihr externes [!DNL Google BigQuery] -Konto konfigurieren. Weiterführende Informationen zur Konfiguration Ihres externen Kontos finden Sie in [diesem Abschnitt](#google-external).

### Massenladeeinrichtung unter Windows {#bulk-load-window}

>[!NOTE]
>
>Damit das Google Cloud SDK funktioniert, muss Python installiert sein.
>
>Wir empfehlen die Verwendung von Python3, siehe diese [Seite](https://www.python.org/downloads/).

Das Bulk Load-Dienstprogramm ermöglicht eine schnellere Übertragung, die über das Google Cloud SDK erreicht wird.

1. Laden Sie das 64-Bit-Archiv für Windows (x86_64) von dieser [Seite](https://cloud.google.com/sdk/docs/downloads-versioned-archives) herunter und extrahieren Sie es in das entsprechende Verzeichnis.

1. Führen Sie das Skript `google-cloud-sdk\install.sh` aus. Sie müssen die Einstellung der Pfadvariablen akzeptieren.

1. Überprüfen Sie nach der Installation, ob die Pfadvariable `...\google-cloud-sdk\bin` festgelegt ist. Wenn nicht, fügen Sie es manuell hinzu.

1. Fügen Sie in der Datei `..\google-cloud-sdk\bin\bq.cmd` die lokale Variable `CLOUDSDK_PYTHON` hinzu, die zum Speicherort der Python-Installation umgeleitet wird.

   Beispiel:

   ![](assets/google-big-query_1.png)

1. Starten Sie Adobe Campaign Classic neu, damit die Änderungen berücksichtigt werden.

## Google BigQuery unter Linux {#google-linux}

### Treiber für Linux eingerichtet {#driver-linux}

Beachten Sie vor dem Einrichten des Treibers, dass Skript und Befehle vom Root-Benutzer ausgeführt werden müssen. Es wird außerdem empfohlen, während der Skripterstellung das Google DNS 8.8.8.8 zu verwenden.

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
>Wir empfehlen die Verwendung von Python3, siehe diese [Seite](https://www.python.org/downloads/).

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

Sie müssen ein externes [!DNL Google BigQuery] -Konto erstellen, um Ihre Adobe Campaign Classic-Instanz mit Ihrer externen [!DNL Google BigQuery]-Datenbank zu verbinden.

1. Klicken Sie in Adobe Campaign Classic **[!UICONTROL Explorer]** auf **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Plattform]** &#39;>&#39; **[!UICONTROL Externe Konten]**.

1. Wählen Sie **[!UICONTROL Neu]** aus.

1. Wählen Sie **[!UICONTROL Externe Datenbank]** als **[!UICONTROL Typ]** Ihres externen Kontos aus.

1. Konfigurieren Sie das externe [!DNL Google BigQuery]-Konto; geben Sie dazu Folgendes an:

   * **[!UICONTROL Typ]**: [!DNL Google BigQuery]

   * **[!UICONTROL Dienstkonto]**: E-Mail Ihres **[!UICONTROL Dienstkontos]**. Weitere Informationen hierzu finden Sie in der [Dokumentation zur Google Cloud](https://cloud.google.com/iam/docs/creating-managing-service-accounts).

   * **[!UICONTROL Projekt]**: Name Ihres **[!UICONTROL Projekts]**. Weitere Informationen hierzu finden Sie in der [Dokumentation zur Google Cloud](https://cloud.google.com/resource-manager/docs/creating-managing-projects).

   * **[!UICONTROL Pfad der Schlüsseldatei]**:
      * **[!UICONTROL Laden Sie die Schlüsseldatei auf den Server hoch]**: Wählen Sie **[!UICONTROL Hier klicken, um den Schlüssel hochzuladen]** , wenn Sie den Schlüssel über Adobe Campaign Classic hochladen möchten.

      * **[!UICONTROL Geben Sie den Pfad der Schlüsseldatei manuell ein]**: Kopieren/fügen Sie Ihren absoluten Pfad in dieses Feld ein, wenn Sie einen bereits vorhandenen Schlüssel verwenden möchten.

   * **[!UICONTROL Datensatz]**: Name Ihres **[!UICONTROL Datensatzes]**. Weitere Informationen hierzu finden Sie in der [Dokumentation zur Google Cloud](https://cloud.google.com/bigquery/docs/datasets-intro).

   ![](assets/google-big-query.png)

Der Connector unterstützt die folgenden Optionen:

| Option | Beschreibung  |
|:-:|:-:|
| ProxyType | Typ des Proxys, der für die Verbindung mit BigQuery über ODBC- und SDK-Connectoren verwendet wird. </br>HTTP (Standard), http_no_tunnel, socks4 und socks5 werden derzeit unterstützt. |
| ProxyHost | Hostname oder IP-Adresse, an der der Proxy erreicht werden kann. |
| ProxyPort | Anschlussnummer, auf der der Proxy ausgeführt wird, z. B. 8080 |
| ProxyUid | Benutzername für den authentifizierten Proxy |
| ProxyPwd | ProxyUid-Kennwort |
| bqpath | Beachten Sie, dass dies nur für Tools mit Massenladevorgang (Cloud SDK) gilt. </br> Um die Verwendung der PATH-Variablen zu vermeiden oder den Ordner google-cloud-sdk an einen anderen Speicherort zu verschieben, können Sie mit dieser Option den genauen Pfad zum Ordner &quot;cloud sdk bin&quot;auf dem Server angeben. |
| GCloudConfigName | Beachten Sie, dass dies ab Version 7.3.4 und nur für Tools mit Massenladevorgang (Cloud SDK) gilt.</br> Das Google Cloud-SDK verwendet Konfigurationen zum Laden von Daten in BigQuery-Tabellen. Die Konfiguration mit dem Namen `accfda` speichert die Parameter zum Laden der Daten. Mit dieser Option können Benutzer jedoch einen anderen Namen für die Konfiguration angeben. |
| GCloudDefaultConfigName | Beachten Sie, dass dies ab Version 7.3.4 und nur für Tools mit Massenladevorgang (Cloud SDK) gilt.</br> Die aktive Google Cloud SDK-Konfiguration kann nicht gelöscht werden, ohne dass das aktive Tag zuerst in eine neue Konfiguration übertragen wird. Diese temporäre Konfiguration ist erforderlich, um die Hauptkonfiguration für das Laden von Daten neu zu erstellen. Der Standardname für die temporäre Konfiguration ist `default`. Dieser kann bei Bedarf geändert werden. |
| GCloudRecreateConfig | Beachten Sie, dass dies ab Version 7.3.4 und nur für Tools mit Massenladevorgang (Cloud SDK) gilt.</br> Wenn der Wert auf `false` festgelegt ist, verhindert der Mechanismus zum Laden von Massengütern nicht den Versuch, die Google Cloud SDK-Konfigurationen neu zu erstellen, zu löschen oder zu ändern. Stattdessen wird das Laden der Daten mit der vorhandenen Konfiguration auf dem Computer fortgesetzt. Diese Funktion ist nützlich, wenn andere Vorgänge von Google Cloud SDK-Konfigurationen abhängig sind. </br> Wenn der Benutzer diese Engine-Option ohne ordnungsgemäße Konfiguration aktiviert, gibt der Massenlademechanismus eine Warnmeldung aus: `No active configuration found. Please either create it manually or remove the GCloudRecreateConfig option`. Um weitere Fehler zu vermeiden, wird dann der standardmäßige ODBC-Array-Einfügemechanismus für Massen-Ladevorgänge verwendet. |

