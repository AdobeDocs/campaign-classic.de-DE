---
product: campaign
title: Zugriff auf Vertica konfigurieren
description: Erfahren Sie, wie Sie den Zugriff auf Vertica über die FDA konfigurieren
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 8b2a9c73-807a-4936-9fd6-9d26c805a31f
source-git-commit: 0cfe8439007b56014eba497c511904c4f11b39ce
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 19%

---

# Zugriff auf Vertica konfigurieren {#configure-fda-vertica}

![](../../assets/v7-only.svg)

Verwenden von Campaign **Federated Data Access** (FDA), um in einer externen Datenbank gespeicherte Informationen zu verarbeiten. Gehen Sie wie folgt vor, um den Zugriff auf [!DNL Vertica].

1. Konfigurieren [!DNL Vertica] on [CentOS](#vertica-centos), [Windows](#vertica-windows) oder [Debian](#vertica-debian)
1. Konfigurieren Sie die [!DNL Vertica] [externes Konto](#vertica-external) in Campaign


>[!NOTE]
>
>[!DNL Vertica] Connector ist für hybride und On-Premise-Implementierungen verfügbar. Weitere Informationen hierzu finden Sie auf [dieser Seite](../../installation/using/capability-matrix.md).

![](assets/snowflake_3.png)

## Vertica auf CentOS {#vertica-centos}

So konfigurieren Sie [!DNL Vertica] Gehen Sie unter CentOS wie folgt vor:

1. Laden Sie die ODBC-Treiber für [!DNL Vertica] herunter. [Hier klicken](https://www.vertica.com/download/vertica/client-drivers/) und laden Sie den neuesten Linux RPM herunter.

1. Anschließend müssen Sie unixODBC mit dem folgenden Befehl installieren:

   ```
   yum search unixODBC
   yum install unixODBC.x86_64
   ```

1. Wenn Sie zuvor die [!DNL Vertica] Server wird bereits ein ODBC-Treiber installiert. Aktualisieren Sie in diesem Fall das Laufwerk wie folgt:

   ```
   #Switch to root
   sudo su
   
   #Install the package (add --force to update it)
   rpm -Uvh vertica-client-x.x.x-x.x86_64.rpm [--force]
   
   #Open odbcinst.ini
   vi /etc/odbcinst.ini
   
   #Add a section for Vertica and save
   [Vertica]
   Description = Vertica ODBC Driver
   Driver = /opt/vertica/lib64/libverticaodbc.so
   
   #Open odbc.ini
   vi /etc/odbc.ini
   
   #Add your DSN in ODBC Data Sources section, for example:
   [ODBC Data Sources]
   VMart = "VMart database on Vertica"
   
   #Add a DSN definition section below, for example:
   [VMart]
   Description = Vmart Database
   Driver = Vertica
   Database = VMart
   Servername = # The name of the server where Vertica is installed. Use localhost if Vertica is installed on the same machine.
   UID = dbadmin
   PWD = <password>
   Port = 5433
   
   #Cleanup
   #Remove the ODBC package
   rm vertica-client-x.x.x-x.x86_64.rpm
   ```

1. In Adobe Campaign können Sie dann Ihre [!DNL Vertica] externes Konto. Weitere Informationen zur Konfiguration Ihres externen Kontos finden Sie unter [diesem Abschnitt](#vertica-external).

## Vertikal unter Windows {#vertica-windows}

1. Laden Sie den [ODBC-Treiber für Windows](https://www.vertica.com/download/vertica/client-drivers/) herunter. Um den Treiber für Windows zu installieren, müssen Sie .NET Framework 3.5 aktivieren. Andernfalls versucht der Installationsassistent automatisch zu aktivieren und herunterzuladen.

1. Konfigurieren Sie den ODBC-Treiber unter Windows. Weiterführende Informationen hierzu finden Sie auf dieser [Seite](https://www.vertica.com/docs/9.2.x/HTML/Content/Authoring/ConnectingToVertica/ClientODBC/SettingUpADSN.htm)

1. In Adobe Campaign können Sie dann Ihre [!DNL Vertica] externes Konto. Weitere Informationen zur Konfiguration Ihres externen Kontos finden Sie unter [diesem Abschnitt](#vertical-external).

## Vertica auf Debian {#vertica-debian}

1. Laden Sie die ODBC-Treiber für [!DNL Vertica] herunter. [Klicken Sie hier](https://sfc-repo.snowflakecomputing.com/odbc/linux/latest/index.html), um mit dem Herunterladen zu beginnen.

1. Anschließend müssen Sie unixODBC mit dem folgenden Befehl installieren:

   ```
   apt-get install unixODBC
   ```

1. Wenn Sie zuvor die [!DNL Vertica] Server wird bereits ein ODBC-Treiber installiert. Aktualisieren Sie in diesem Fall das Laufwerk wie folgt:

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
   
   #Add a section for Vertica and save
   [Vertica]
   Description = Vertica ODBC Driver
   Driver = /opt/vertica/lib64/libverticaodbc.so
   
   #Open odbc.ini
   vi /etc/odbc.ini
   
   #Add your DSN in ODBC Data Sources section, for example:
   [ODBC Data Sources]
   VMart = "VMart database on Vertica"
   
   #Add a DSN definition section below, for example:
   [VMart]
   Description = Vmart Database
   Driver = Vertica
   Database = VMart
   Servername = # The name of the server where Vertica is installed. Use localhost if Vertica is installed on the same machine.
   UID = dbadmin
   PWD = <password>
   Port = 5433
   ```

1. In Adobe Campaign können Sie dann Ihre [!DNL Vertica] externes Konto. Weitere Informationen zur Konfiguration Ihres externen Kontos finden Sie unter [diesem Abschnitt](#vertica-external).

## Externes vertikales Konto {#vertica-external}

Sie müssen eine [!DNL Vertica] externes Konto, um Ihre Campaign-Instanz mit Ihrer [!DNL Vertica] externe Datenbank.

1. Von Campaign **[!UICONTROL Explorer]** klicken **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Plattform]** &#39;>&#39; **[!UICONTROL Externe Konten]**.

1. Wählen Sie **[!UICONTROL Neu]** aus.

1. Wählen Sie **[!UICONTROL Externe Datenbank]** als **[!UICONTROL Typ]** Ihres externen Kontos aus.

1. Konfigurieren Sie die **[!UICONTROL Vertikal]** externes Konto angeben:

   * **[!UICONTROL Typ]**: [!DNL Vertica Analytics]

   * **[!UICONTROL Server]**: URL des [!DNL Vertica]-Servers

   * **[!UICONTROL Konto]**: Name des Benutzers

   * **[!UICONTROL Passwort]**: Passwort des Benutzerkontos

   * **[!UICONTROL Datenbank]**: Name der Datenbank
   ![](assets/vertica.png)
