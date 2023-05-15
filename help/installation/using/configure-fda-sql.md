---
product: campaign
title: Zugriff auf Microsoft SQL Server konfigurieren
description: Erfahren Sie, wie Sie den Zugriff auf Microsoft SQL Server konfigurieren
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
exl-id: 65ab4577-3126-4579-8fcc-e93772ebd1e8
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '536'
ht-degree: 10%

---

# Zugriff auf Microsoft SQL Server konfigurieren {#configure-fda-sql}



Verwenden von Campaign **Federated Data Access** (FDA), um in einer externen Microsoft SQL Server-Datenbank gespeicherte Informationen zu verarbeiten. Gehen Sie wie folgt vor, um den Zugriff auf [!DNL Microsoft SQL Server].

1. Konfigurieren [!DNL Microsoft SQL Server] on [CentOS](#sql-centos).
1. Konfigurieren [!DNL Microsoft SQL Server] on [Linux](#sql-linux).
1. Konfigurieren [!DNL Microsoft SQL Server] on [Windows](#sql-windows).
1. Konfigurieren Sie die [!DNL Microsoft SQL Server] [externes Konto](#sql-external) in Campaign

## Microsoft SQL Server unter CentOS {#sql-centos}

>[!NOTE]
>
> [!DNL Microsoft SQL Server] ist auf CentOS 7 und 6 verfügbar.

So konfigurieren Sie [!DNL Microsoft SQL Server] Gehen Sie unter CentOS wie folgt vor:

1. Laden Sie den SQL ODBC-Treiber mit dem folgenden Befehl herunter und installieren Sie ihn:

   ```
   sudo su
   curl https://packages.microsoft.com/config/rhel/7/prod.repo > /etc/yum.repos.d/mssql-release.repo
   exit
   sudo yum remove unixODBC-utf16 unixODBC-utf16-devel #to avoid conflicts
   sudo ACCEPT_EULA=Y yum install msodbcsql
   ```

1. In Adobe Campaign können Sie dann Ihre [!DNL Microsoft SQL Server] externes Konto. Weitere Informationen zur Konfiguration Ihres externen Kontos finden Sie unter [diesem Abschnitt](#sql-external).

## Microsoft SQL Server unter Linux {#sql-linux}

>[!NOTE]
>
> Wenn Sie eine ältere Version von Adobe Campaign (vor 7.2.1) ausführen, müssen Sie `unix ODBC drivers`.

1. Laden Sie den MS ODBC-Treiber von herunter. [diese Seite](https://packages.microsoft.com/ubuntu/16.04/prod/pool/main/m/msodbcsql17/).

1. Führen Sie den folgenden Befehl als Root-Benutzer aus:

   ```
   # install the mssql odbc that was downloaded
   dpkg -i msodbcsql17_17.7.1.1-1_amd64.deb
   # accept the license terms
   ```

1. In Adobe Campaign können Sie dann Ihre [!DNL Microsoft SQL Server] externes Konto. Weitere Informationen zur Konfiguration Ihres externen Kontos finden Sie unter [diesem Abschnitt](#sql-external).

## Microsoft SQL Server unter Windows {#sql-windows}

So konfigurieren Sie [!DNL Microsoft SQL Server] unter Windows:

1. Klicken Sie unter Windows auf **[!UICONTROL Control Panel]** &#39;>&#39; **[!UICONTROL System und Sicherheit]** &#39;>&#39; **[!UICONTROL Administrationstools]**&#39;>&#39; **[!UICONTROL ODBC-Datenquellen (64 Bit)]**.

1. Aus dem **[!UICONTROL ODBC-Datenquellen (64 Bit)]** neues Fenster, klicken Sie auf **[!UICONTROL Hinzufügen...]**.

1. Überprüfen Sie, ob SQL Server Native Client v11 im Abschnitt **[!UICONTROL Neue Datenquelle erstellen]** Fenster.

1. Wenn der native SQL Server-Client nicht aufgeführt ist, können Sie ihn hier herunterladen: [diese Seite](https://www.microsoft.com/en-my/download/details.aspx?id=36434).

1. In Adobe Campaign können Sie dann Ihre [!DNL Microsoft SQL Server] externes Konto. Weitere Informationen zur Konfiguration Ihres externen Kontos finden Sie unter [diesem Abschnitt](#sql-external).

## Externes Microsoft SQL Server-Konto {#sql-external}

Sie müssen eine [!DNL Microsoft SQL Server] externes Konto, um Ihre Campaign-Instanz mit Ihrer [!DNL Microsoft SQL Server] externe Datenbank.

1. Von Campaign **[!UICONTROL Explorer]** klicken **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Plattform]** &#39;>&#39; **[!UICONTROL Externe Konten]**.

1. Wählen Sie **[!UICONTROL Neu]** aus.

1. Wählen Sie **[!UICONTROL Externe Datenbank]** als **[!UICONTROL Typ]** Ihres externen Kontos aus.

1. under **[!UICONTROL Konfiguration]** auswählen [!DNL Microsoft SQL Server] von **[!UICONTROL Typ]** Dropdown-Liste.

   ![](assets/sql.png)

1. Konfigurieren Sie die **[!UICONTROL Microsoft SQL Server]** Externe Kontoauthentifizierung:

   * **[!UICONTROL Server]**: URL des [!DNL Microsoft SQL Server]-Servers.

   * **[!UICONTROL Konto]**: Name des Benutzers.

   * **[!UICONTROL Passwort]**: Passwort des Benutzerkontos.

   * **[!UICONTROL Datenbank]**: Name der Datenbank (optional).

   * **[!UICONTROL Zeitzone]**: Zeitzone festgelegt in [!DNL Microsoft SQL Server]. [Weitere Informationen](https://docs.microsoft.com/en-us/sql/t-sql/functions/current-timezone-transact-sql?view=sql-server-ver15)

1. Klicken Sie auf den Tab **[!UICONTROL Parameter]** und dann auf die Schaltfläche **[!UICONTROL Funktionen bereitstellen]**, um Funktionen zu erstellen.

   >[!NOTE]
   >
   >Damit alle Funktionen verfügbar sind, müssen Sie die SQL-Funktionen von Adobe Campaign in der Remote-Datenbank erstellen. Weiterführende Informationen dazu finden Sie auf dieser [Seite](../../configuration/using/adding-additional-sql-functions.md).

1. Klicken **[!UICONTROL Speichern]** wenn Ihre Konfiguration abgeschlossen ist.

Der Connector unterstützt die folgenden Optionen:

| Option | Beschreibung  |
|---|---|
| Authentifizierung | Vom Connector unterstützte Authentifizierungstyp. Aktuell unterstützter Wert: ActiveDirectoryMSI. <br> Weitere Informationen hierzu finden Sie in Beispiel 8 von [Microsoft-Dokumentation](https://docs.microsoft.com/en-us/sql/connect/odbc/using-azure-active-directory?view=sql-server-ver15#example-connection-strings). |
| Verschlüsseln | Gibt an, ob Verbindungen die TLS-Verschlüsselung über das Netzwerk verwenden. Mögliche Werte sind **ja/obligatorisch (18.0 und höher)**, **no/optional (18.0 und höher)** und **strict (18.0 und höher)**. Der Standardwert ist auf **yes** in Version 18.0 und höher und **no** in früheren Versionen. <br>Weitere Informationen hierzu finden Sie unter [Microsoft-Dokumentation](https://docs.microsoft.com/en-us/sql/connect/odbc/dsn-connection-string-attribute?view=azure-sqldw-latest#encrypt). |
| TrustServerCertificate | Aktiviert die Verschlüsselung mit einem selbstsignierten Serverzertifikat bei Verwendung mit **Verschlüsseln**. <br>Akzeptierte Werte: **yes** oder **no** (Standardwert, d. h. das Serverzertifikat wird validiert). |
