---
product: campaign
title: Zugriff auf Microsoft SQL Server konfigurieren
description: Erfahren Sie, wie Sie den Zugriff auf Microsoft SQL Server konfigurieren
feature: Installation, Federated Data Access
exl-id: 65ab4577-3126-4579-8fcc-e93772ebd1e8
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '507'
ht-degree: 8%

---

# Zugriff auf Microsoft SQL Server konfigurieren {#configure-fda-sql}



Verwenden Sie die **-Option (Federated Data Access** (FDA) von Campaign, um Informationen zu verarbeiten, die in einer externen Microsoft SQL Server-Datenbank gespeichert sind. Gehen Sie wie folgt vor, um den Zugriff auf [!DNL Microsoft SQL Server] zu konfigurieren.

1. Konfigurieren Sie [!DNL Microsoft SQL Server] auf [CentOS](#sql-centos).
1. Konfigurieren Sie [!DNL Microsoft SQL Server] unter [Linux](#sql-linux).
1. Konfigurieren von [!DNL Microsoft SQL Server] unter [Windows](#sql-windows).
1. Konfigurieren des [!DNL Microsoft SQL Server] [externen Kontos](#sql-external) in Campaign

## Microsoft SQL Server unter CentOS {#sql-centos}

>[!NOTE]
>
> [!DNL Microsoft SQL Server] ist unter CentOS 7 und 6 verfügbar.

Gehen Sie wie folgt vor, um [!DNL Microsoft SQL Server] auf CentOS zu konfigurieren:

1. Herunterladen und Installieren des SQL ODBC-Treibers mit dem folgenden Befehl:

   ```
   sudo su
   curl https://packages.microsoft.com/config/rhel/7/prod.repo > /etc/yum.repos.d/mssql-release.repo
   exit
   sudo yum remove unixODBC-utf16 unixODBC-utf16-devel #to avoid conflicts
   sudo ACCEPT_EULA=Y yum install msodbcsql
   ```

1. In Adobe Campaign können Sie dann Ihr externes [!DNL Microsoft SQL Server]-Konto konfigurieren. Weiterführende Informationen zur Konfiguration Ihres externen Kontos finden Sie in [diesem Abschnitt](#sql-external).

## Microsoft SQL Server unter Linux {#sql-linux}

>[!NOTE]
>
> Wenn Sie eine ältere Version von Adobe Campaign (vor 7.2.1) verwenden, müssen Sie `unix ODBC drivers` installieren.

1. Laden Sie den MS ODBC-Treiber von [dieser Seite](https://packages.microsoft.com/ubuntu/16.04/prod/pool/main/m/msodbcsql17/) herunter.

1. Führen Sie den folgenden Befehl als Root-Benutzer aus:

   ```
   # install the mssql odbc that was downloaded
   dpkg -i msodbcsql17_17.7.1.1-1_amd64.deb
   # accept the license terms
   ```

1. In Adobe Campaign können Sie dann Ihr externes [!DNL Microsoft SQL Server]-Konto konfigurieren. Weiterführende Informationen zur Konfiguration Ihres externen Kontos finden Sie in [diesem Abschnitt](#sql-external).

## Microsoft SQL Server unter Windows {#sql-windows}

So konfigurieren Sie [!DNL Microsoft SQL Server] unter Windows:

1. Klicken Sie unter Windows auf **[!UICONTROL Systemsteuerung]** &#39;>&#39; **[!UICONTROL System und Sicherheit]** &#39;>&#39; **[!UICONTROL Verwaltungstools]**&#39;>&#39; **[!UICONTROL ODBC-Datenquellen (64 Bit)]**.

1. Klicken Sie im **[!UICONTROL ODBC-Datenquellen (64-Bit]**-Fenster auf **[!UICONTROL Hinzufügen…]**.

1. Überprüfen Sie, ob der SQL Server Native Client v11 im Fenster **[!UICONTROL Neue Daten-Source erstellen]** aufgeführt ist.

1. Wenn der native SQL Server-Client nicht aufgeführt ist, können Sie ihn auf [dieser Seite) &#x200B;](https://www.microsoft.com/en-my/download/details.aspx?id=36434).

1. In Adobe Campaign können Sie dann Ihr externes [!DNL Microsoft SQL Server]-Konto konfigurieren. Weiterführende Informationen zur Konfiguration Ihres externen Kontos finden Sie in [diesem Abschnitt](#sql-external).

## Externes Microsoft SQL Server-Konto {#sql-external}

Sie müssen ein [!DNL Microsoft SQL Server] externes Konto erstellen, um Ihre Campaign-Instanz mit Ihrer [!DNL Microsoft SQL Server] externen Datenbank zu verbinden.

1. Klicken Sie **[!UICONTROL Campaign-]** auf **[!UICONTROL Administration]** &quot;>&quot; **[!UICONTROL Plattform]** &quot;>&quot; **[!UICONTROL Externe Konten]**.

1. Wählen Sie **[!UICONTROL Neu]** aus.

1. Wählen Sie **[!UICONTROL Externe Datenbank]** als **[!UICONTROL Typ]** Ihres externen Kontos aus.

1. Wählen **[!UICONTROL unter &quot;]**&quot; [!DNL Microsoft SQL Server] aus der Dropdown **[!UICONTROL Typ]** aus.

   ![](assets/sql.png)

1. Konfigurieren Sie die Authentifizierung des externen Microsoft SQL Server **-Kontos:**

   * **[!UICONTROL Server]**: URL des [!DNL Microsoft SQL Server].

   * **[!UICONTROL Konto]**: Name des Benutzers.

   * **[!UICONTROL Password]**: Kennwort für Benutzerkonto.

   * **[!UICONTROL Datenbank]**: Name der Datenbank (optional).

   * **[!UICONTROL Zeitzone]**: Die Zeitzone wird in [!DNL Microsoft SQL Server] festgelegt. [Weitere Informationen](https://docs.microsoft.com/en-us/sql/t-sql/functions/current-timezone-transact-sql?view=sql-server-ver15)

1. Klicken Sie auf den Tab **[!UICONTROL Parameter]** und dann auf die Schaltfläche **[!UICONTROL Funktionen bereitstellen]**, um Funktionen zu erstellen.

   >[!NOTE]
   >
   >Damit alle Funktionen verfügbar sind, müssen Sie die Adobe Campaign SQL-Funktionen in der Remote-Datenbank erstellen. Weiterführende Informationen dazu finden Sie auf dieser [Seite](../../configuration/using/adding-additional-sql-functions.md).

1. Klicken Sie **[!UICONTROL Speichern]** wenn Ihre Konfiguration abgeschlossen ist.

Der Connector unterstützt die folgenden Optionen:

| Option | Beschreibung  |
|---|---|
| Authentifizierung | Vom Connector unterstützte Authentifizierungstyp. Aktuell unterstützter Wert: ActiveDirectoryMSI. <br> Weiterführende Informationen hierzu finden Sie in Beispiel 8 der [Dokumentation zu Microsoft](https://docs.microsoft.com/en-us/sql/connect/odbc/using-azure-active-directory?view=sql-server-ver15#example-connection-strings). |
| Verschlüsseln | Gibt an, ob Verbindungen die TLS-Verschlüsselung über das Netzwerk verwenden. Mögliche Werte sind **ja/obligatorisch (18.0 und höher)**, **nein/optional (18.0 und höher)** und **streng (18.0 und höher)**. Der Standardwert ist in Version 18.0 **Ja** und in früheren Versionen **Nein** festgelegt. <br>Weitere Informationen hierzu finden Sie in der [Dokumentation zu Microsoft](https://docs.microsoft.com/en-us/sql/connect/odbc/dsn-connection-string-attribute?view=azure-sqldw-latest#encrypt). |
| TrustServerCertificate | Aktiviert die Verschlüsselung mit einem selbstsignierten Serverzertifikat bei Verwendung mit **Encrypt**. <br>Akzeptierte Werte: **ja** oder **nein** (Standardwert, was bedeutet, dass das Serverzertifikat validiert wird). |
