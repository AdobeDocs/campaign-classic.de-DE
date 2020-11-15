---
title: Zugriff auf Hadoop konfigurieren
description: Erfahren Sie, wie Sie den Zugriff auf Hadoop in FDA konfigurieren
page-status-flag: never-activated
uuid: b84359b9-c584-431d-80d5-71146d9b6854
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dd3d14cc-5153-428d-a98a-32b46f0fe811
translation-type: tm+mt
source-git-commit: 9bbde65aea6735e30e95e75c2b6ae5445d4a2bdd
workflow-type: tm+mt
source-wordcount: '619'
ht-degree: 84%

---


# Zugriff auf Hadoop konfigurieren {#configure-access-to-hadoop}

Verwenden Sie die Option &quot;Kampagne **Federated Data Access** (FDA)&quot;, um in externen Datenbanken gespeicherte Informationen zu verarbeiten. Gehen Sie wie folgt vor, um den Zugriff auf Hadoop zu konfigurieren.

1. Konfigurieren der [Hadoop-Datenbank](#configuring-hadoop)
1. Konfigurieren des Hadoop- [Externen Kontos](#hadoop-external) in der Kampagne

## Konfigurieren von Hadoop 3.0 {#configuring-hadoop}

Die Verbindung mit einer externen Hadoop-Datenbank über die FDA-Option erfordert folgende Konfigurationen auf dem Adobe Campaign-Server. Beachten Sie, dass diese Konfiguration für sowohl Windows als auch Linux verfügbar ist.

1. Laden Sie je nach Betriebssystemversion die ODBC-Treiber für Hadoop herunter. Treiber finden Sie auf [dieser Seite](https://www.cloudera.com/downloads.html).

1. Anschließend müssen Sie die ODBC-Treiber installieren und einen DSN für Ihre Hive-Verbindung einrichten. Anweisungen dazu finden Sie auf [dieser Seite](https://docs.cloudera.com/documentation/other/connectors/hive-odbc/2-6-5/Cloudera-ODBC-Driver-for-Apache-Hive-Install-Guide.pdf).

1. Nach dem Herunterladen und Installieren der ODBC-Treiber müssen Sie Campaign Classic neu starten. Führen Sie dazu den folgenden Befehl aus:

   ```
   systemctl stop nlserver.service
   systemctl start nlserver.service
   ```

1. In Campaign Classic können Sie dann Ihr externes [!DNL Hadoop]-Konto konfigurieren. For more on how to configure your external account, refer to [this section](#hadoop-external).

## Externes Hadoop-Konto {#hadoop-external}

Über das externe [!DNL Hadoop]-Konto können Sie Ihre Campaign-Instanz mit Ihrer externen Hadoop-Datenbank verbinden.

1. Konfigurieren Sie in Campaign Classic Ihr externes [!DNL Hadoop]-Konto. Klicken Sie im **[!UICONTROL Explorer]** auf **[!UICONTROL Administration]** > **[!UICONTROL Plattform]** > **[!UICONTROL Externe Konten]**.

1. Wählen Sie **[!UICONTROL Neu]** aus.

1. Wählen Sie **[!UICONTROL Externe Datenbank]** als **[!UICONTROL Typ]** Ihres externen Kontos aus.

1. Konfigurieren Sie das externe **[!UICONTROL Hadoop]**-Konto. Geben Sie dazu Folgendes an:

   * **[!UICONTROL Typ]**: ODBC (Sybase ASE, Sybase IQ)

   * **[!UICONTROL Server]**: Name des DNS

   * **[!UICONTROL Konto]**: Name des Benutzers

   * **[!UICONTROL Passwort]**: Passwort des Benutzerkontos

   * **[!UICONTROL Datenbank]**: Name Ihrer Datenbank, falls nicht im DSN angegeben. Kann leer bleiben, wenn im DSN angegeben

   * **[!UICONTROL Zeitzone]**: Zeitzone des Servers

   ![](assets/hadoop3.png)

Der Connector unterstützt die folgenden ODBC-Optionen:

| Name | Wert |
|---|---|
| ODBCMgr | iODBC |
| warehouse | 1/2/4 |

Der Connector unterstützt außerdem die folgenden Hive-Optionen:

| Name | Wert | Beschreibung |
|---|---|---|
| bulkKey | Azur Blob- oder DataLake-Zugriffsschlüssel | Für wasb://- oder wasbs://-Bulk-Loader (z. B. wenn das Bulk-Load-Tool mit wasb:// oder wasbs:// beginnt). <br>Das ist der Zugriffsschlüssel für den Blob- oder DataLake-Bucket bei Bulk Loads. |
| hdfsPort | Port-Nummer <br>standardmäßig auf 8020 gesetzt | Bei HDFS-Bulk-Load (d. h. wenn das Bulk-Load-Tool mit webhdfs:// oder webhdfss:// beginnt). |
| bucketsNumber | 20 | Anzahl der Buckets beim Erstellen einer Cluster-Tabelle. |
| fileFormat | PARQUET | Standarddateiformat für Arbeitstabellen. |


## Konfigurieren von Hadoop 2.1 {#configure-access-hadoop-2}

Wenn Sie eine Verbindung zu Hadoop 2.1 herstellen müssen, befolgen Sie die unten beschriebenen Schritte für [Windows](#for-windows) oder [Linux](#for-linux).

### Hadoop 2.1 für Windows {#for-windows}

1. Installieren Sie die ODBC- und [Azure HD Insight](https://www.microsoft.com/en-us/download/details.aspx?id=40886)-Treiber für Windows.
1. Erstellen Sie den DSN (Data Source Name), indem Sie das Tool ODBC DataSource Administrator ausführen. Dort finden Sie ein Beispiel für einen System-DSN für Hive, das Sie anpassen können.

   ```
   Description: vorac (or any name you like)
   Host: vorac.azurehdinsight.net
   Port: 443
   Database: sm_tst611 (or your database name)
   Mechanism: Azure HDInsight Service
   User/Password: admin/<your password here>
   ```

1. Create the Hadoop external account, as detailed in [this section](#hadoop-external).

### Hadoop 2.1 für Linux {#for-linux}

1. Installieren Sie unixodbc für Linux.

   ```
   apt-get install unixodbc
   ```

1. Laden Sie ODBC-Treiber für Apache Hive von HortonWorks herunter und installieren Sie sie: [https://www.hortonworks.com/downloads/](https://www.hortonworks.com/downloads/).

   ```
   dpkg -i hive-odbc-native_2.1.10.1014-2_amd64.deb
   ```

1. Sehen Sie nach, wo die ODBC-Dateien gespeichert sind.

   ```
   root@campadpac71:/tmp# odbcinst -j
   unixODBC 2.3.1
   DRIVERS............: /etc/odbcinst.ini
   SYSTEM DATA SOURCES: /etc/odbc.ini
   FILE DATA SOURCES..: /etc/ODBCDataSources
   USER DATA SOURCES..: /root/.odbc.ini
   SQLULEN Size.......: 8
   SQLLEN Size........: 8
   SQLSETPOSIROW Size.: 8
   ```

1. Erstellen Sie den DSN (Data Source Name) und bearbeiten Sie die Datei odbc.ini. Erstellen Sie dann einen DSN für Ihre Hive-Verbindung.

   Hier ist ein Beispiel für HDInsight zur Herstellung einer Verbindung mit der Bezeichnung &quot;viral&quot;:

   ```
   [ODBC Data Sources]
   vorac 
   
   [vorac]
   Driver=/usr/lib/hive/lib/native/Linux-amd64-64/libhortonworkshiveodbc64.so
   HOST=vorac.azurehdinsight.net
   PORT=443
   Schema=sm_tst611
   HiveServerType=2
   AuthMech=6
   UID=admin
   PWD=<your password here>
   HTTPPath=
   UseNativeQuery=1
   ```

   >[!NOTE]
   >
   >Der Parameter **UseNativeQuery** ist dabei sehr wichtig. Campaign unterstützt Hive und funktioniert nur dann ordnungsgemäß, wenn UseNativeQuery eingerichtet ist. Üblicherweise formuliert der Treiber oder Hive SQL Connector Abfragen um und ändert die Spaltenanordnung.

   Die Authentifizierungseinrichtung hängt von der Konfiguration von Hive/Hadoop ab. Verwenden Sie z. B. für HD Insight AuthMech=6 für die Benutzer-/Passwort-Authentifizierung entsprechend [dieser Beschreibung](https://www.simba.com/products/Spark/doc/ODBC_InstallGuide/unix/content/odbc/hi/configuring/authenticating/azuresvc.htm).

1. Exportieren Sie die Variablen.

   ```
   export ODBCINI=/etc/myodbc.ini
   export ODBCSYSINI=/etc/myodbcinst.ini
   ```

1. Richten Sie Hortonworks-Treiber über /usr/lib/hive/lib/native/Linux-amd64-64/hortonworks.hiveodbc.ini ein.

   Sie müssen UTF-16 verwenden, um eine Verbindung mit Campaign und unix-odbc (libodbcinst) herstellen zu können.

   ```
   [Driver]
   
   DriverManagerEncoding=UTF-16
   ErrorMessagesPath=/usr/lib/hive/lib/native/hiveodbc/ErrorMessages/
   LogLevel=0
   LogPath=/tmp/hive
   SwapFilePath=/tmp
   
   ODBCInstLib=libodbcinst.so
   ```

1. Jetzt können Sie Ihre Verbindung unter Verwendung von isql testen.

   ```
   isql vorac
   isql vorac -v
   ```

1. Create the Hadoop external account, as detailed in [this section](#hadoop-external).

