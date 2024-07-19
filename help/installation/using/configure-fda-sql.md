---
product: campaign
title: Zugriff auf Microsoft SQL Server konfigurieren
description: Informationen zum Konfigurieren des Zugriffs auf Microsoft SQL Server
feature: Installation, Federated Data Access
exl-id: 65ab4577-3126-4579-8fcc-e93772ebd1e8
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '507'
ht-degree: 8%

---

# Zugriff auf Microsoft SQL Server konfigurieren {#configure-fda-sql}



Verwenden Sie die Option Campaign **Federated Data Access** (FDA) , um in einer externen Microsoft SQL Server-Datenbank gespeicherte Informationen zu verarbeiten. Gehen Sie wie folgt vor, um den Zugriff auf [!DNL Microsoft SQL Server] zu konfigurieren.

1. Konfigurieren Sie [!DNL Microsoft SQL Server] für [CentOS](#sql-centos).
1. Konfigurieren Sie [!DNL Microsoft SQL Server] für [Linux](#sql-linux).
1. Konfigurieren Sie [!DNL Microsoft SQL Server] unter [Windows](#sql-windows).
1. Konfigurieren des externen [!DNL Microsoft SQL Server] [Kontos](#sql-external) in Campaign

## Microsoft SQL Server unter CentOS {#sql-centos}

>[!NOTE]
>
> [!DNL Microsoft SQL Server] ist unter CentOS 7 und 6 verfügbar.

Gehen Sie wie folgt vor, um [!DNL Microsoft SQL Server] für CentOS zu konfigurieren:

1. Laden Sie den SQL ODBC-Treiber mit dem folgenden Befehl herunter und installieren Sie ihn:

   ```
   sudo su
   curl https://packages.microsoft.com/config/rhel/7/prod.repo > /etc/yum.repos.d/mssql-release.repo
   exit
   sudo yum remove unixODBC-utf16 unixODBC-utf16-devel #to avoid conflicts
   sudo ACCEPT_EULA=Y yum install msodbcsql
   ```

1. In Adobe Campaign können Sie dann Ihr externes [!DNL Microsoft SQL Server] -Konto konfigurieren. Weiterführende Informationen zur Konfiguration Ihres externen Kontos finden Sie in [diesem Abschnitt](#sql-external).

## Microsoft SQL Server unter Linux {#sql-linux}

>[!NOTE]
>
> Wenn Sie eine ältere Version von Adobe Campaign (vor 7.2.1) ausführen, müssen Sie `unix ODBC drivers` installieren.

1. Laden Sie den MS ODBC-Treiber von [dieser Seite](https://packages.microsoft.com/ubuntu/16.04/prod/pool/main/m/msodbcsql17/) herunter.

1. Führen Sie den folgenden Befehl als Root-Benutzer aus:

   ```
   # install the mssql odbc that was downloaded
   dpkg -i msodbcsql17_17.7.1.1-1_amd64.deb
   # accept the license terms
   ```

1. In Adobe Campaign können Sie dann Ihr externes [!DNL Microsoft SQL Server] -Konto konfigurieren. Weiterführende Informationen zur Konfiguration Ihres externen Kontos finden Sie in [diesem Abschnitt](#sql-external).

## Microsoft SQL Server unter Windows {#sql-windows}

So konfigurieren Sie [!DNL Microsoft SQL Server] unter Windows:

1. Klicken Sie unter Windows auf **[!UICONTROL Systemsteuerung]** &#39;>&#39; **[!UICONTROL System und Sicherheit]** &#39;>&#39; **[!UICONTROL Verwaltung der Tools]**&#39;>&#39; **[!UICONTROL ODBC-Datenquellen (64 Bit)]**.

1. Klicken Sie im neuen Fenster **[!UICONTROL ODBC-Datenquellen (64 Bit)]** auf **[!UICONTROL Hinzufügen...]**.

1. Überprüfen Sie, ob SQL Server Native Client v11 im Fenster **[!UICONTROL Neue Daten erstellen - Source]** aufgeführt ist.

1. Wenn der native SQL Server-Client nicht aufgeführt ist, können Sie ihn auf [dieser Seite](https://www.microsoft.com/en-my/download/details.aspx?id=36434) herunterladen.

1. In Adobe Campaign können Sie dann Ihr externes [!DNL Microsoft SQL Server] -Konto konfigurieren. Weiterführende Informationen zur Konfiguration Ihres externen Kontos finden Sie in [diesem Abschnitt](#sql-external).

## Externes Microsoft SQL Server-Konto {#sql-external}

Sie müssen ein externes [!DNL Microsoft SQL Server] -Konto erstellen, um Ihre Campaign-Instanz mit Ihrer externen [!DNL Microsoft SQL Server] -Datenbank zu verbinden.

1. Klicken Sie in Campaign **[!UICONTROL Explorer]** auf **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Plattform]** &#39;>&#39; **[!UICONTROL Externe Konten]**.

1. Wählen Sie **[!UICONTROL Neu]** aus.

1. Wählen Sie **[!UICONTROL Externe Datenbank]** als **[!UICONTROL Typ]** Ihres externen Kontos aus.

1. Wählen Sie unter **[!UICONTROL Konfiguration]** [!DNL Microsoft SQL Server] aus der Dropdown-Liste **[!UICONTROL Typ]** aus.

   ![](assets/sql.png)

1. Konfigurieren Sie die Authentifizierung des externen Microsoft SQL Server ]**-Kontos:**[!UICONTROL 

   * **[!UICONTROL Server]**: URL des [!DNL Microsoft SQL Server] -Servers.

   * **[!UICONTROL Konto]**: Name des Benutzers.

   * **[!UICONTROL Kennwort]**: Kennwort für Benutzerkonten.

   * **[!UICONTROL Datenbank]**: Name der Datenbank (optional).

   * **[!UICONTROL Zeitzone]**: Zeitzone festgelegt in [!DNL Microsoft SQL Server]. [Weitere Informationen](https://docs.microsoft.com/en-us/sql/t-sql/functions/current-timezone-transact-sql?view=sql-server-ver15)

1. Klicken Sie auf den Tab **[!UICONTROL Parameter]** und dann auf die Schaltfläche **[!UICONTROL Funktionen bereitstellen]**, um Funktionen zu erstellen.

   >[!NOTE]
   >
   >Damit alle Funktionen verfügbar sind, müssen Sie die SQL-Funktionen von Adobe Campaign in der Remote-Datenbank erstellen. Weiterführende Informationen dazu finden Sie auf dieser [Seite](../../configuration/using/adding-additional-sql-functions.md).

1. Klicken Sie auf **[!UICONTROL Speichern]** , wenn Ihre Konfiguration abgeschlossen ist.

Der Connector unterstützt die folgenden Optionen:

| Option | Beschreibung  |
|---|---|
| Authentifizierung | Vom Connector unterstützte Authentifizierungstyp. Aktuell unterstützter Wert: ActiveDirectoryMSI. <br> Weitere Informationen hierzu finden Sie in Beispiel 8 der Dokumentation zu [Microsoft](https://docs.microsoft.com/en-us/sql/connect/odbc/using-azure-active-directory?view=sql-server-ver15#example-connection-strings). |
| Verschlüsseln | Gibt an, ob Verbindungen die TLS-Verschlüsselung über das Netzwerk verwenden. Mögliche Werte sind **ja/mandatory (18.0 und höher)**, **no/optional (18.0 und höher)** und **strict (18.0 und höher)**. Der Standardwert ist in Version 18.0 und höher auf **yes** und in früheren Versionen auf **no** festgelegt. <br>Weitere Informationen hierzu finden Sie in der [Microsoft-Dokumentation](https://docs.microsoft.com/en-us/sql/connect/odbc/dsn-connection-string-attribute?view=azure-sqldw-latest#encrypt). |
| TrustServerCertificate | Aktiviert die Verschlüsselung mit einem selbstsignierten Serverzertifikat bei Verwendung mit **Verschlüsselung**. <br>Akzeptierte Werte: **yes** oder **no** (Standardwert, d. h. das Serverzertifikat wird validiert). |
