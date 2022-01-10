---
product: campaign
title: Zugriff auf Snowflake konfigurieren
description: Erfahren Sie, wie Sie den Zugriff auf Snowflake in FDA konfigurieren
audience: platform
content-type: reference
topic-tags: connectors
exl-id: bdb5e422-ecfe-42eb-bd15-39fe5ec0ff1d
source-git-commit: 6cecc81135afd067712e51ec9c1ad3239170702e
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 46%

---

# Zugriff auf Snowflake konfigurieren {#configure-access-to-snowflake}

![](../../assets/v7-only.svg)

Verwenden von Campaign **Federated Data Access** (FDA), um in einer externen Datenbank gespeicherte Informationen zu verarbeiten. Gehen Sie wie folgt vor, um den Zugriff auf [!DNL Snowflake].

1. Konfigurieren [!DNL Snowflake] on [Linux](#snowflake-linux).
1. Konfigurieren Sie die [!DNL Snowflake] [externes Konto](#snowflake-external) in Campaign

>[!NOTE]
>
>Der [!DNL Snowflake]-Connector ist für gehostete und On-Premise-Implementierungen verfügbar. Weitere Informationen hierzu finden Sie auf [dieser Seite](../../installation/using/capability-matrix.md).

![](assets/snowflake_3.png)

## Snowflake unter Linux {#snowflake-linux}

So konfigurieren Sie [!DNL Snowflake] Gehen Sie unter Linux wie folgt vor:

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

1. Bevor Sie das Skript ausführen, können Sie mit der `--help` Option:

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

1. In Campaign können Sie dann Ihre [!DNL Snowflake] externes Konto. Weitere Informationen zur Konfiguration Ihres externen Kontos finden Sie unter [diesem Abschnitt](#snowflake-external).

## Externes Snowflake-Konto {#snowflake-external}

Sie müssen eine [!DNL Snowflake] externes Konto, um Ihre Campaign-Instanz mit Ihrer [!DNL Snowflake] externe Datenbank.

1. Von Campaign **[!UICONTROL Explorer]** klicken **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Plattform]** &#39;>&#39; **[!UICONTROL Externe Konten]**.

1. Wählen Sie **[!UICONTROL Neu]** aus.

1. Wählen Sie **[!UICONTROL Externe Datenbank]** als **[!UICONTROL Typ]** Ihres externen Kontos aus.

1. under **[!UICONTROL Konfiguration]** auswählen [!DNL Snowflake] von **[!UICONTROL Typ]** Dropdown-Liste.

   ![](assets/snowflake_5.png)

1. Fügen Sie Ihre **[!UICONTROL Server]** URL und **[!UICONTROL Datenbank]**.

1. Konfigurieren Sie die **[!UICONTROL Snowflake]** Externe Kontoauthentifizierung:

   * Für die Konto-/Kennwortauthentifizierung müssen Sie Folgendes angeben:

      * **[!UICONTROL Konto]**: Name des Benutzers

      * **[!UICONTROL Passwort]**: Passwort des Benutzerkontos.

      ![](assets/snowflake.png)

   * Klicken Sie für die Keypair-Authentifizierung auf die **[!UICONTROL Keypair Auth]** Registerkarte zur Verwendung Ihrer **[!UICONTROL Privater Schlüssel]** , um sich zu authentifizieren und Ihre **[!UICONTROL Privater Schlüssel]**.

      ![](assets/snowflake_4.png)


1. Klicken Sie auf den Tab **[!UICONTROL Parameter]** und dann auf die Schaltfläche **[!UICONTROL Funktionen freigeben]**, um Funktionen zu erstellen.

   >[!NOTE]
   >
   >Damit alle Funktionen verfügbar sind, müssen Sie die SQL-Funktionen von Adobe Campaign in der Remote-Datenbank erstellen. Weiterführende Informationen dazu finden Sie auf dieser [Seite](../../configuration/using/adding-additional-sql-functions.md).

   ![](assets/snowflake_2.png)

1. Klicken **[!UICONTROL Speichern]** wenn Ihre Konfiguration abgeschlossen ist.

Der Connector unterstützt die folgenden Optionen:

| Option | Beschreibung  |
|---|---|
| workschema | Datenbankschema zur Verwendung mit Arbeitstabellen |
| warehouse | Name des zu verwendenden Standard-Warehouse. Dadurch wird die Standardeinstellung des Benutzers außer Kraft gesetzt. |
| TimeZoneName | Standardmäßig leer, d. h. die Systemzeitzone des Campaign Classic-App-Servers wird verwendet. Mit dieser Option können Sie den Sitzungsparameter TIMEZONE erzwingen. <br>Weiterführende Informationen hierzu finden Sie auf dieser [Seite](https://docs.snowflake.net/manuals/sql-reference/parameters.html#timezone). |
| WeekStart | Sitzungsparameter WEEK_START. Standardmäßig auf 0 gesetzt <br>Weiterführende Informationen hierzu finden Sie auf dieser [Seite](https://docs.snowflake.com/de/sql-reference/parameters.html#week-start). |
| UseCachedResult | Sitzungsparameter USE_CACHED_RESULTS. Standardmäßig ist TRUE festgelegt. Diese Option kann verwendet werden, um zwischengespeicherte Ergebnisse von Snowflake zu deaktivieren. <br>Weiterführende Informationen dazu finden Sie auf [dieser Seite](https://docs.snowflake.net/manuals/user-guide/querying-persisted-results.html). |
