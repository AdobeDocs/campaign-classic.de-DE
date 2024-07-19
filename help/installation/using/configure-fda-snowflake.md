---
product: campaign
title: Zugriff auf Snowflake konfigurieren
description: Erfahren Sie, wie Sie den Zugriff auf Snowflake in FDA konfigurieren
feature: Installation, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: bdb5e422-ecfe-42eb-bd15-39fe5ec0ff1d
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '518'
ht-degree: 34%

---

# Zugriff auf Snowflake konfigurieren {#configure-access-to-snowflake}

Verwenden Sie die Option Campaign **Federated Data Access** (FDA) , um in einer externen Datenbank gespeicherte Informationen zu verarbeiten. Gehen Sie wie folgt vor, um den Zugriff auf [!DNL Snowflake] zu konfigurieren.

1. Konfigurieren Sie [!DNL Snowflake] für [Linux](#snowflake-linux).
1. Konfigurieren des externen [!DNL Snowflake] [Kontos](#snowflake-external) in Campaign

>[!NOTE]
>
>Der [!DNL Snowflake]-Connector ist für gehostete und On-Premise-Bereitstellungen verfügbar. Weitere Informationen hierzu finden Sie auf [dieser Seite](../../installation/using/capability-matrix.md).

![](assets/snowflake_3.png)

## Snowflake unter Linux {#snowflake-linux}

Gehen Sie wie folgt vor, um [!DNL Snowflake] unter Linux zu konfigurieren:

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

1. Bevor Sie das Skript ausführen, können Sie mit der Option `--help` auf weitere Informationen zugreifen:

   ```
   cd /usr/local/neolane/nl6/bin/fda-setup-scripts/
   ./snowflake_odbc-setup.sh --help
   ```

1. Rufen Sie den Ordner auf, in dem sich das Skript befindet, und führen Sie das folgende Skript als Stammbenutzer aus:

   ```
   cd /usr/local/neolane/nl6/bin/fda-setup-scripts
   ./snowflake_odbc-setup.sh
   ```

1. Nach der Installation der ODBC-Treiber müssen Sie Campaign Classic neu starten. Führen Sie dazu den folgenden Befehl aus:

   ```
   systemctl stop nlserver.service
   systemctl start nlserver.service
   ```

1. In Campaign können Sie dann Ihr externes [!DNL Snowflake] -Konto konfigurieren. Weiterführende Informationen zur Konfiguration Ihres externen Kontos finden Sie in [diesem Abschnitt](#snowflake-external).

## Externes Snowflake-Konto {#snowflake-external}

Sie müssen ein externes [!DNL Snowflake] -Konto erstellen, um Ihre Campaign-Instanz mit Ihrer externen [!DNL Snowflake] -Datenbank zu verbinden.

1. Klicken Sie in Campaign **[!UICONTROL Explorer]** auf **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Plattform]** &#39;>&#39; **[!UICONTROL Externe Konten]**.

1. Wählen Sie **[!UICONTROL Neu]** aus.

1. Wählen Sie **[!UICONTROL Externe Datenbank]** als **[!UICONTROL Typ]** Ihres externen Kontos aus.

1. Wählen Sie unter **[!UICONTROL Konfiguration]** [!DNL Snowflake] aus der Dropdown-Liste **[!UICONTROL Typ]** aus.

   ![](assets/snowflake_5.png)

1. Fügen Sie Ihre **[!UICONTROL Server]**-URL und Ihre **[!UICONTROL Datenbank]** hinzu.

1. Konfigurieren Sie die Authentifizierung des externen **[!UICONTROL Snowflake]** -Kontos:

   * Für die Konto-/Kennwortauthentifizierung müssen Sie Folgendes angeben:

      * **[!UICONTROL Konto]**: Name des Benutzers

      * **[!UICONTROL Kennwort]**: Kennwort für Benutzerkonten.

     ![](assets/snowflake.png)

   * Klicken Sie für die Keypair-Authentifizierung auf die Registerkarte **[!UICONTROL Keypair Auth]** , um Ihren **[!UICONTROL privaten Schlüssel]** zum Authentifizieren und Kopieren Ihres **[!UICONTROL privaten Schlüssels]** zu verwenden.

     ![](assets/snowflake_4.png)

1. Klicken Sie auf den Tab **[!UICONTROL Parameter]** und dann auf die Schaltfläche **[!UICONTROL Funktionen bereitstellen]**, um Funktionen zu erstellen.

   >[!NOTE]
   >
   >Damit alle Funktionen verfügbar sind, müssen Sie die SQL-Funktionen von Adobe Campaign in der Remote-Datenbank erstellen. Weiterführende Informationen dazu finden Sie auf dieser [Seite](../../configuration/using/adding-additional-sql-functions.md).

   ![](assets/snowflake_2.png)

1. Klicken Sie auf **[!UICONTROL Speichern]** , wenn Ihre Konfiguration abgeschlossen ist.

Der Connector unterstützt die folgenden Optionen:

| Option | Beschreibung  |
|---|---|
| workschema | Datenbankschema zur Verwendung mit Arbeitstabellen |
| warehouse | Name des zu verwendenden Standard-Warehouse. Dadurch wird die Standardeinstellung des Benutzers außer Kraft gesetzt. |
| TimeZoneName | Standardmäßig leer, d. h. die Systemzeitzone des Campaign Classic-App-Servers wird verwendet. Mit dieser Option können Sie den Sitzungsparameter TIMEZONE erzwingen. <br>Weiterführende Informationen hierzu finden Sie auf dieser [Seite](https://docs.snowflake.net/manuals/sql-reference/parameters.html#timezone). |
| WeekStart | Sitzungsparameter WEEK_START. Standardmäßig auf 0 gesetzt <br>Weiterführende Informationen hierzu finden Sie auf dieser [Seite](https://docs.snowflake.com/de/sql-reference/parameters.html#week-start). |
| UseCachedResult | Sitzungsparameter USE_CACHED_RESULTS. Standardmäßig ist TRUE festgelegt. Diese Option kann verwendet werden, um zwischengespeicherte Ergebnisse von Snowflake zu deaktivieren. <br>Weiterführende Informationen hierzu finden Sie auf dieser [Seite](https://docs.snowflake.net/manuals/user-guide/querying-persisted-results.html). |
| bulkThreads | Anzahl der Threads, die für Snowflake-Bulk-Loader verwendet werden sollen, mehr Threads bedeuten eine bessere Leistung bei größeren Bulk-Ladungen. Standardmäßig auf 1 gesetzt Die Zahl kann je nach Anzahl der Maschinenthread angepasst werden. |
| chunkSize | Bestimmt die Dateigröße des Stapels für Ladegeräte. Standardmäßig auf 128 MB eingestellt. Kann für eine optimale Leistung geändert werden, wenn BulkThreads verwendet werden. Gleichzeitigere aktive Threads bedeuten eine bessere Leistung. <br>Weitere Informationen hierzu finden Sie in der [Snowflake-Dokumentation](https://docs.snowflake.net/manuals/sql-reference/sql/put.html). |
| StageName | Name des vorab bereitgestellten internen Schritts. Sie wird bei Bulk Load verwendet, anstatt eine neue temporäre Phase zu erstellen. |
