---
product: campaign
title: Zugriff auf Snowflake konfigurieren
description: Erfahren Sie, wie Sie den Zugriff auf Snowflake in FDA konfigurieren
audience: platform
content-type: reference
topic-tags: connectors
exl-id: bdb5e422-ecfe-42eb-bd15-39fe5ec0ff1d
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '513'
ht-degree: 72%

---

# Zugriff auf Snowflake konfigurieren {#configure-access-to-snowflake}

![](../../assets/v7-only.svg)

Verwenden von Campaign **Federated Data Access** (FDA), um in einer externen Datenbank gespeicherte Informationen zu verarbeiten. Gehen Sie wie folgt vor, um den Zugriff auf [!DNL Snowflake].

1. Konfigurieren [!DNL Snowflake] on [CentOS](#snowflake-centos), [Windows](#snowflake-windows) oder [Debian](#snowflake-debian)
1. Konfigurieren Sie die [!DNL Snowflake] [externes Konto](#snowflake-external) in Campaign


>[!NOTE]
>
>Der [!DNL Snowflake]-Connector ist für gehostete und On-Premise-Implementierungen verfügbar. Weitere Informationen hierzu finden Sie auf [dieser Seite](../../installation/using/capability-matrix.md).

![](assets/snowflake_3.png)

## Snowflake unter CentOS {#snowflake-centos}

So konfigurieren Sie [!DNL Snowflake] Gehen Sie unter CentOS wie folgt vor:

1. Laden Sie die ODBC-Treiber für [!DNL Snowflake] herunter. [Klicken Sie hier](https://sfc-repo.snowflakecomputing.com/odbc/linux/latest/snowflake-odbc-2.20.2.x86_64.rpm), um mit dem Herunterladen zu beginnen.
1. Installieren Sie anschließend die ODBC-Treiber mit folgendem Befehl in CentOS:

   ```
   rpm -Uvh unixodbc
   rpm -Uvh snowflake-odbc-2.20.2.x86_64.rpm
   ```

1. Nach dem Herunterladen und Installieren der ODBC-Treiber muss Campaign Classic neu gestartet werden. Führen Sie dazu den folgenden Befehl aus:

   ```
   /etc/init.d/nlserver6 stop
   /etc/init.d/nlserver6 start
   ```

1. In Campaign können Sie dann Ihre [!DNL Snowflake] externes Konto. Weitere Informationen zur Konfiguration Ihres externen Kontos finden Sie unter [diesem Abschnitt](#snowflake-external).

## Snowflake unter Windows {#snowflake-windows}

1. Laden Sie den [ODBC-Treiber für Windows](https://docs.snowflake.net/manuals/user-guide/odbc-download.html) herunter. Beachten Sie, dass Sie zum Installieren des Treibers Administratorrechte benötigen. Weiterführende Informationen hierzu finden Sie auf dieser [Seite](https://docs.snowflake.net/manuals/user-guide/admin-user-management.html)

1. Konfigurieren Sie den ODBC-Treiber. Weiterführende Informationen hierzu finden Sie auf dieser [Seite](https://docs.snowflake.net/manuals/user-guide/odbc-windows.html#step-2-configure-the-odbc-driver)

1. In Campaign können Sie dann Ihre [!DNL Snowflake] externes Konto. Weitere Informationen zur Konfiguration Ihres externen Kontos finden Sie unter [diesem Abschnitt](#snowflake-external).

## Snowflake unter Debian {#snowflake-debian}

1. Laden Sie die ODBC-Treiber für [!DNL Snowflake] herunter. [Klicken Sie hier](https://sfc-repo.snowflakecomputing.com/odbc/linux/latest/index.html), um mit dem Herunterladen zu beginnen.

1. Anschließend müssen Sie die ODBC-Treiber in Debian mit folgendem Befehl installieren:

   ```
   apt-get install unixodbc
   apt-get install snowflake-odbc-x.xx.x.x86_64.deb
   ```

1. Nach dem Herunterladen und Installieren der ODBC-Treiber müssen Sie Campaign Classic neu starten. Führen Sie dazu den folgenden Befehl aus:

   ```
   systemctl stop nlserver.service
   systemctl start nlserver.service
   ```

1. In Campaign können Sie dann Ihre [!DNL Snowflake] externes Konto. Weitere Informationen zur Konfiguration Ihres externen Kontos finden Sie unter [diesem Abschnitt](#snowflake-external).

## Externes Snowflake-Konto {#snowflake-external}

Sie müssen eine [!DNL Snowflake] externes Konto, um Ihre Campaign-Instanz mit Ihrer [!DNL Snowflake] externe Datenbank.

1. Von Campaign **[!UICONTROL Explorer]** klicken **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Plattform]** &#39;>&#39; **[!UICONTROL Externe Konten]**.

1. Wählen Sie **[!UICONTROL Neu]** aus.

1. Wählen Sie **[!UICONTROL Externe Datenbank]** als **[!UICONTROL Typ]** Ihres externen Kontos aus.

1. Konfigurieren Sie das externe **[!UICONTROL Snowflake]**-Konto; geben Sie dazu Folgendes an:

   * **[!UICONTROL Typ]**: [!DNL Snowflake]

   * **[!UICONTROL Server]**: URL des [!DNL Snowflake]-Servers

   * **[!UICONTROL Konto]**: Name des Benutzers

   * **[!UICONTROL Passwort]**: Passwort des Benutzerkontos

   * **[!UICONTROL Datenbank]**: Name der Datenbank

   ![](assets/snowflake.png)

1. Klicken Sie auf den Tab **[!UICONTROL Parameter]** und dann auf die Schaltfläche **[!UICONTROL Funktionen freigeben]**, um Funktionen zu erstellen.

   ![](assets/snowflake_2.png)

Der Connector unterstützt die folgenden Optionen:

| Option | Beschreibung  |
|---|---|
| workschema | Datenbankschema zur Verwendung mit Arbeitstabellen |
| warehouse | Name des zu verwendenden Standard-Warehouse. Dadurch wird die Standardeinstellung des Benutzers außer Kraft gesetzt. |
| TimeZoneName | Standardmäßig leer, d. h. die Systemzeitzone des Campaign Classic-App-Servers wird verwendet. Mit dieser Option können Sie den Sitzungsparameter TIMEZONE erzwingen. <br>Weiterführende Informationen hierzu finden Sie auf dieser [Seite](https://docs.snowflake.net/manuals/sql-reference/parameters.html#timezone). |
| WeekStart | Sitzungsparameter WEEK_START. Standardmäßig auf 0 gesetzt <br>Weiterführende Informationen hierzu finden Sie auf dieser [Seite](https://docs.snowflake.com/de/sql-reference/parameters.html#week-start). |
| UseCachedResult | Sitzungsparameter USE_CACHED_RESULTS. Standardmäßig ist TRUE festgelegt. Diese Option kann verwendet werden, um zwischengespeicherte Ergebnisse von Snowflake zu deaktivieren. <br>Weiterführende Informationen dazu finden Sie auf [dieser Seite](https://docs.snowflake.net/manuals/user-guide/querying-persisted-results.html). |
