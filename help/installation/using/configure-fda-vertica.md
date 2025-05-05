---
product: campaign
title: Konfiguration des Zugriffs auf  [!DNL Vertica Analytics]
description: Erfahren Sie, wie Sie den Zugriff auf  [!DNL Vertica Analytics]  FDA konfigurieren
feature: Installation, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 8b2a9c73-807a-4936-9fd6-9d26c805a31f
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 23%

---

# Zugriff auf [!DNL Vertica Analytics] konfigurieren {#configure-fda-vertica}



Verwenden Sie die **-Option (Federated Data Access** (FDA) von Campaign, um in einer externen Datenbank gespeicherte Informationen zu verarbeiten. Gehen Sie wie folgt vor, um den Zugriff auf [!DNL Vertica Analytics] zu konfigurieren.

1. [!DNL Vertica Analytics] auf [CentOS](#vertica-centos), [Windows](#vertica-windows) oder [Debian](#vertica-debian)
1. Konfigurieren des [!DNL Vertica Analytics] [externen Kontos](#vertica-external) in Campaign

![](assets/snowflake_3.png)

## [!DNL Vertica Analytics] auf CentOS {#vertica-centos}

Gehen Sie wie folgt vor, um [!DNL Vertica Analytics] auf CentOS zu konfigurieren:

1. Laden Sie die ODBC-Treiber für [!DNL Vertica Analytics] herunter. [Hier klicken](https://www.vertica.com/download/vertica/client-drivers/) und das neueste Linux RPM herunterladen.

1. Sie müssen dann unixODBC mit dem folgenden Befehl installieren:

   ```
   yum search unixODBC
   yum install unixODBC.x86_64
   ```

1. Wenn Sie den [!DNL Vertica Analytics] Server bereits installiert haben, ist bereits ein ODBC-Treiber installiert. Aktualisieren Sie in diesem Fall das Laufwerk wie folgt:

   ```
   #Switch to root
   sudo su
   
   #Install the package (add --force to update it)
   rpm -Uvh vertica-client-x.x.x-x.x86_64.rpm [--force]
   
   #Open odbcinst.ini
   vi /etc/odbcinst.ini
   
   #Add a section for Vertica Analytics and save
   [VerVertica Analyticstica]
   Description = Vertica Analytics ODBC Driver
   Driver = /opt/vertica/lib64/libverticaodbc.so
   
   #Open odbc.ini
   vi /etc/odbc.ini
   
   #Add your DSN in ODBC Data Sources section, for example:
   [ODBC Data Sources]
   VMart = "VMart database on Vertica Analytics"
   
   #Add a DSN definition section below, for example:
   [VMart]
   Description = Vmart Database
   Driver = Vertica Analytics
   Database = VMart
   Servername = # The name of the server where Vertica Analytics is installed. Use localhost if Vertica Analytics is installed on the same machine.
   UID = dbadmin
   PWD = <password>
   Port = 5433
   
   #Cleanup
   #Remove the ODBC package
   rm vertica-client-x.x.x-x.x86_64.rpm
   ```

1. In Adobe Campaign können Sie dann Ihr externes [!DNL Vertica Analytics]-Konto konfigurieren. Weiterführende Informationen zur Konfiguration Ihres externen Kontos finden Sie in [diesem Abschnitt](#vertica-external).

## [!DNL Vertica Analytics] unter Windows {#vertica-windows}

1. Laden Sie den [ODBC-Treiber für Windows](https://www.vertica.com/download/vertica/client-drivers/) herunter. Um den Treiber für Windows zu installieren, müssen Sie .NET Framework 3.5 aktivieren, oder der Installationsassistent versucht, ihn automatisch zu aktivieren und herunterzuladen.

1. Konfigurieren Sie den ODBC-Treiber unter Windows. Weiterführende Informationen hierzu finden Sie auf dieser [Seite](https://www.vertica.com/docs/9.2.x/HTML/Content/Authoring/ConnectingToVertica/ClientODBC/SettingUpADSN.htm)

1. In Adobe Campaign können Sie dann Ihr externes [!DNL Vertica Analytics]-Konto konfigurieren. Weiterführende Informationen zur Konfiguration Ihres externen Kontos finden Sie in [diesem Abschnitt](#vertical-external).

## [!DNL Vertica Analytics] auf Debian {#vertica-debian}

1. Laden Sie die ODBC-Treiber für [!DNL Vertica Analytics] herunter. [Klicken Sie hier](https://sfc-repo.snowflakecomputing.com/odbc/linux/latest/index.html), um mit dem Herunterladen zu beginnen.

1. Sie müssen dann unixODBC mit dem folgenden Befehl installieren:

   ```
   apt-get install unixODBC
   ```

1. Wenn Sie den [!DNL Vertica Analytics] Server bereits installiert haben, ist bereits ein ODBC-Treiber installiert. Aktualisieren Sie in diesem Fall das Laufwerk wie folgt:

   ```
   #Switch to root
   sudo su
   
   #Move or copy the downloaded file and change to /root
   mv vertica_9.3..xx_odbc_x86_64_linux.tar.gz /
   cd /
   
   #Uncompress the file you downloaded
   tar vzxf vertica_9.3..xx_odbc_x86_64_linux.tar.gz
   
   #Remove the tar.gz since it is not needed anymore
   rm vertica_9.3..xx_odbc_x86_64_linux.tar.gz
   
   #Open odbcinst.ini
   vi /etc/odbcinst.ini
   
   #Add a section for Vertica Analytics and save
   [Vertica Analytics]
   Description = Vertica Analytics ODBC Driver
   Driver = /opt/vertica/lib64/libverticaodbc.so
   
   #Open odbc.ini
   vi /etc/odbc.ini
   
   #Add your DSN in ODBC Data Sources section, for example:
   [ODBC Data Sources]
   VMart = "VMart database on Vertica Analytics"
   
   #Add a DSN definition section below, for example:
   [VMart]
   Description = Vmart Database
   Driver = Vertica Analytics
   Database = VMart
   Servername = # The name of the server where Vertica Analytics is installed. Use localhost if Vertica Analytics is installed on the same machine.
   UID = dbadmin
   PWD = <password>
   Port = 5433
   ```

1. In Adobe Campaign können Sie dann Ihr externes [!DNL Vertica Analytics]-Konto konfigurieren. Weiterführende Informationen zur Konfiguration Ihres externen Kontos finden Sie in [diesem Abschnitt](#vertica-external).

## Externes Konto [!DNL Vertica Analytics] {#vertica-external}

Sie müssen ein [!DNL Vertica Analytics] externes Konto erstellen, um Ihre Campaign-Instanz mit Ihrer [!DNL Vertica Analytics] externen Datenbank zu verbinden.

1. Klicken Sie **[!UICONTROL Campaign-]** auf **[!UICONTROL Administration]** &quot;>&quot; **[!UICONTROL Plattform]** &quot;>&quot; **[!UICONTROL Externe Konten]**.

1. Wählen Sie **[!UICONTROL Neu]** aus.

1. Wählen Sie **[!UICONTROL Externe Datenbank]** als **[!UICONTROL Typ]** Ihres externen Kontos aus.

1. Konfigurieren Sie das externe Konto {**}Vertica Analytics. Sie müssen Folgendes angeben:**

   * **[!UICONTROL Typ]**: [!DNL Vertica Analytics]

   * **[!UICONTROL Server]**: URL des [!DNL Vertica Analytics]-Servers

   * **[!UICONTROL Konto]**: Name des Benutzers

   * **[!UICONTROL Passwort]**: Passwort des Benutzerkontos

   * **[!UICONTROL Datenbank]**: Name der Datenbank

   ![](assets/vertica.png)

Der Connector unterstützt die folgenden Optionen:

| Option | Beschreibung  |
|---|---|
| TimeZoneName | Standardmäßig leer, d. h. die Systemzeitzone des Campaign Classic-App-Servers wird verwendet. Mit der Option können Sie den Sitzungsparameter TIMEZONE erzwingen. |

