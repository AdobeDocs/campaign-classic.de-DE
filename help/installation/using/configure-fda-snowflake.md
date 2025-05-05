---
product: campaign
title: Zugriff auf Snowflake konfigurieren
description: Erfahren Sie, wie Sie den Zugriff auf Snowflake in FDA konfigurieren
feature: Installation, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: bdb5e422-ecfe-42eb-bd15-39fe5ec0ff1d
source-git-commit: 22420452d4df2e8161c91a42ad0d20ceb4796e82
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 33%

---

# Zugriff auf Snowflake konfigurieren {#configure-access-to-snowflake}

Verwenden Sie die **-Option (Federated Data Access** (FDA) von Campaign, um in einer externen Datenbank gespeicherte Informationen zu verarbeiten. Gehen Sie wie folgt vor, um den Zugriff auf [!DNL Snowflake] zu konfigurieren.

1. Konfigurieren Sie [!DNL Snowflake] unter [Linux](#snowflake-linux).
1. Konfigurieren des [!DNL Snowflake] [externen Kontos](#snowflake-external) in Campaign

>[!CAUTION]
>
>* Der [!DNL Snowflake]-Connector ist für gehostete und On-Premise-Bereitstellungen verfügbar. Weitere Informationen hierzu finden Sie auf [dieser Seite](../../installation/using/capability-matrix.md).
>
>* Die minimal unterstützte Version des [!DNL Snowflake] ODBC-Treibers ist **.24.4**.
>

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

1. Vor Ausführung des Skripts können Sie mit der Option `--help` auf weitere Informationen zugreifen:

   ```
   cd /usr/local/neolane/nl6/bin/fda-setup-scripts/
   ./snowflake_odbc-setup.sh --help
   ```

1. Greifen Sie auf das Verzeichnis zu, in dem sich das Skript befindet, und führen Sie das folgende Skript als Root-Benutzer aus:

   ```
   cd /usr/local/neolane/nl6/bin/fda-setup-scripts
   ./snowflake_odbc-setup.sh
   ```

1. Nach der Installation der ODBC-Treiber müssen Sie Campaign Classic neu starten. Führen Sie dazu den folgenden Befehl aus:

   ```
   systemctl stop nlserver.service
   systemctl start nlserver.service
   ```

1. In Campaign können Sie dann Ihr [!DNL Snowflake] externes Konto konfigurieren. Weiterführende Informationen zur Konfiguration Ihres externen Kontos finden Sie in [diesem Abschnitt](#snowflake-external).

## Externes Snowflake-Konto {#snowflake-external}

Sie müssen ein [!DNL Snowflake] externes Konto erstellen, um Ihre Campaign-Instanz mit Ihrer [!DNL Snowflake] externen Datenbank zu verbinden.

1. Klicken Sie **[!UICONTROL Campaign-]** auf **[!UICONTROL Administration]** &quot;>&quot; **[!UICONTROL Plattform]** &quot;>&quot; **[!UICONTROL Externe Konten]**.

1. Wählen Sie **[!UICONTROL Neu]** aus.

1. Wählen Sie **[!UICONTROL Externe Datenbank]** als **[!UICONTROL Typ]** Ihres externen Kontos aus.

1. Wählen **[!UICONTROL unter &quot;]**&quot; [!DNL Snowflake] aus der Dropdown **[!UICONTROL Typ]** aus.

   ![](assets/snowflake_5.png)

1. Fügen Sie Ihre **[!UICONTROL Server]**-URL und **[!UICONTROL Datenbank]** hinzu.

1. Konfigurieren der Authentifizierung für das externe Snowflake **-Konto:**

   * Für die Konto-/Kennwortauthentifizierung müssen Sie Folgendes angeben:

      * **[!UICONTROL Konto]**: Name des Benutzers

      * **[!UICONTROL Password]**: Kennwort für Benutzerkonto.

     ![](assets/snowflake.png)

   * Klicken Sie für die Schlüsselpaar-Authentifizierung auf die Registerkarte **[!UICONTROL Schlüsselpaar-Auth]** , um Ihren **[!UICONTROL privaten Schlüssel]** zur Authentifizierung zu verwenden und Ihren **[!UICONTROL privaten Schlüssel]** zu kopieren und einzufügen.

     ![](assets/snowflake_4.png)

1. Klicken Sie auf den Tab **[!UICONTROL Parameter]** und dann auf die Schaltfläche **[!UICONTROL Funktionen bereitstellen]**, um Funktionen zu erstellen.

   >[!NOTE]
   >
   >Damit alle Funktionen verfügbar sind, müssen Sie die Adobe Campaign SQL-Funktionen in der Remote-Datenbank erstellen. Weiterführende Informationen dazu finden Sie auf dieser [Seite](../../configuration/using/adding-additional-sql-functions.md).

   ![](assets/snowflake_2.png)

1. Klicken Sie **[!UICONTROL Speichern]** wenn Ihre Konfiguration abgeschlossen ist.

Der Connector unterstützt die folgenden Optionen:

| Option | Beschreibung  |
|---|---|
| workschema | Datenbankschema zur Verwendung mit Arbeitstabellen |
| warehouse | Name des zu verwendenden Standard-Warehouse. Dadurch wird die Standardeinstellung des Benutzers außer Kraft gesetzt. |
| TimeZoneName | Standardmäßig leer, d. h. die Systemzeitzone des Campaign Classic-App-Servers wird verwendet. Mit dieser Option können Sie den Sitzungsparameter TIMEZONE erzwingen. <br>Weiterführende Informationen hierzu finden Sie auf dieser [Seite](https://docs.snowflake.net/manuals/sql-reference/parameters.html#timezone). |
| WeekStart | Sitzungsparameter WEEK_START. Standardmäßig auf 0 gesetzt <br>Weiterführende Informationen hierzu finden Sie auf dieser [Seite](https://docs.snowflake.com/de/sql-reference/parameters.html#week-start). |
| UseCachedResult | Sitzungsparameter USE_CACHED_RESULTS. Standardmäßig ist TRUE festgelegt. Diese Option kann verwendet werden, um zwischengespeicherte Ergebnisse von Snowflake zu deaktivieren. <br>Weiterführende Informationen hierzu finden Sie auf dieser [Seite](https://docs.snowflake.net/manuals/user-guide/querying-persisted-results.html). |
| bulkThreads | Anzahl der Threads, die für den Snowflake-Bulk-Loader verwendet werden sollen. Mehr Threads bedeuten eine bessere Leistung für größere Bulk-Loads. Standardmäßig auf 1 gesetzt Die Zahl kann in Abhängigkeit von der Maschinengewindeanzahl angepasst werden. |
| chunkSize | Bestimmt die Dateigröße des Blocks des Bulk-Loaders. Standardmäßig ist dieser Wert auf 128 MB festgelegt. Kann geändert werden, um eine optimale Leistung zu erzielen, wenn es mit bulkThreads verwendet wird. Mehr gleichzeitige aktive Threads bedeuten eine bessere Leistung. <br>Weitere Informationen hierzu finden Sie in der [Dokumentation zu Snowflake](https://docs.snowflake.net/manuals/sql-reference/sql/put.html). |
| Staging-Name | Name des vorab bereitgestellten internen Schritts. Sie wird beim Massenladen verwendet, anstatt ein neues temporäres Stadium zu erstellen. |
