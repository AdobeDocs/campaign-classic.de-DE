---
product: campaign
title: Zugriff auf Vertica analytics konfigurieren
description: Erfahren Sie, wie Sie den Zugriff auf Vertica analytics in FDA konfigurieren
feature: Installation, Federated Data Access
badge-v7-only: label="v7" type="Informative" tooltip="Gilt nur für Campaign Classic v7"
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 8b2a9c73-807a-4936-9fd6-9d26c805a31f
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 26%

---

# Zugriff auf Vertica analytics konfigurieren {#configure-fda-vertica}



Verwenden von Campaign **Federated Data Access** (FDA), um in einer externen Datenbank gespeicherte Informationen zu verarbeiten. Gehen Sie wie folgt vor, um den Zugriff auf [!DNL Vertica Analytics].

1. Konfigurieren [!DNL Vertica Analytics] on [CentOS](#vertica-centos), [Windows](#vertica-windows) oder [Debian](#vertica-debian)
1. Konfigurieren Sie die [!DNL Vertica Analytics] [externes Konto](#vertica-external) in Campaign

![](assets/snowflake_3.png)

## Vertica analytics auf CentOS {#vertica-centos}

So konfigurieren Sie [!DNL Vertica Analytics] Gehen Sie unter CentOS wie folgt vor:

1. Laden Sie die ODBC-Treiber für [!DNL Vertica Analytics] herunter. [Hier klicken](https://www.vertica.com/download/vertica/client-drivers/) und laden Sie den neuesten Linux RPM herunter.

1. Anschließend müssen Sie unixODBC mit dem folgenden Befehl installieren:

   ```
   yum search unixODBC
   yum install unixODBC.x86_64
   ```

1. Wenn Sie zuvor die [!DNL Vertica Analytics] Server wird bereits ein ODBC-Treiber installiert. Aktualisieren Sie in diesem Fall das Laufwerk wie folgt:

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

1. In Adobe Campaign können Sie dann Ihre [!DNL Vertica Analytics] externes Konto. Weitere Informationen zur Konfiguration Ihres externen Kontos finden Sie unter [diesem Abschnitt](#vertica-external).

## Vertica analytics unter Windows {#vertica-windows}

1. Laden Sie den [ODBC-Treiber für Windows](https://www.vertica.com/download/vertica/client-drivers/) herunter. Um den Treiber für Windows zu installieren, müssen Sie .NET Framework 3.5 aktivieren. Andernfalls versucht der Installationsassistent automatisch zu aktivieren und herunterzuladen.

1. Konfigurieren Sie den ODBC-Treiber unter Windows. Weiterführende Informationen hierzu finden Sie auf dieser [Seite](https://www.vertica.com/docs/9.2.x/HTML/Content/Authoring/ConnectingToVertica/ClientODBC/SettingUpADSN.htm)

1. In Adobe Campaign können Sie dann Ihre [!DNL Vertica Analytics] externes Konto. Weitere Informationen zur Konfiguration Ihres externen Kontos finden Sie unter [diesem Abschnitt](#vertical-external).

## Vertica analytics auf Debian {#vertica-debian}

1. Laden Sie die ODBC-Treiber für [!DNL Vertica Analytics] herunter. [Klicken Sie hier](https://sfc-repo.snowflakecomputing.com/odbc/linux/latest/index.html), um mit dem Herunterladen zu beginnen.

1. Anschließend müssen Sie unixODBC mit dem folgenden Befehl installieren:

   ```
   apt-get install unixODBC
   ```

1. Wenn Sie zuvor die [!DNL Vertica Analytics] Server wird bereits ein ODBC-Treiber installiert. Aktualisieren Sie in diesem Fall das Laufwerk wie folgt:

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

1. In Adobe Campaign können Sie dann Ihre [!DNL Vertica Analytics] externes Konto. Weitere Informationen zur Konfiguration Ihres externen Kontos finden Sie unter [diesem Abschnitt](#vertica-external).

## Externes Konto der vertica analytics {#vertica-external}

Sie müssen eine [!DNL Vertica Analytics] externes Konto, um Ihre Campaign-Instanz mit Ihrer [!DNL Vertica Analytics] externe Datenbank.

1. Von Campaign **[!UICONTROL Explorer]** klicken **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Plattform]** &#39;>&#39; **[!UICONTROL Externe Konten]**.

1. Wählen Sie **[!UICONTROL Neu]** aus.

1. Wählen Sie **[!UICONTROL Externe Datenbank]** als **[!UICONTROL Typ]** Ihres externen Kontos aus.

1. Konfigurieren Sie die **[!UICONTROL Vertica analytics]** externes Konto angeben:

   * **[!UICONTROL Typ]**: [!DNL Vertica Analytics]

   * **[!UICONTROL Server]**: URL des [!DNL Vertica Analytics]-Servers

   * **[!UICONTROL Konto]**: Name des Benutzers

   * **[!UICONTROL Passwort]**: Passwort des Benutzerkontos

   * **[!UICONTROL Datenbank]**: Name der Datenbank

   ![](assets/vertica.png)

Der Connector unterstützt die folgenden Optionen:

| Option | Beschreibung  |
|---|---|
| TimeZoneName | Standardmäßig leer, d. h. die Systemzeitzone des Campaign Classic-App-Servers wird verwendet. Mit dieser Option können Sie den Sitzungsparameter TIMEZONE erzwingen. |

