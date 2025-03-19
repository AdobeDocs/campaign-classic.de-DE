---
product: campaign
title: Zugriff auf Sybase IQ konfigurieren
description: Erfahren Sie, wie Sie den Zugriff auf Sybase IQ in FDA konfigurieren
feature: Installation, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 0fdf8259-5cab-4a9d-adb3-6c55ec5c8851
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 66%

---

# Zugriff auf Sybase IQ konfigurieren {#configure-access-to-sybase-iq}



Verwenden Sie die **-Option (Federated Data Access** (FDA) von Campaign, um in einer externen Datenbank gespeicherte Informationen zu verarbeiten. Gehen Sie wie folgt vor, um den Zugriff auf Sybase IQ zu konfigurieren.

1. [Sybase IQ-Datenbank konfigurieren](#configuring-sybase)
1. Konfigurieren des Sybase IQ [externen Kontos](#sybase-external) in Campaign

## Sybase IQ-Konfiguration {#configuring-sybase}

Für die Verbindung mit einer externen Sybase IQ-Datenbank in FDA sind zusätzliche Konfigurationen unten auf dem Adobe Campaign-Server erforderlich.

>[!NOTE]
>
>Stellen Sie vor dem Start sicher **dass sich das Paket** unixodbc“ auf dem Server befindet.

1. Installieren Sie **iq_odbc**. Nach Abschluss der Installation wird möglicherweise ein Fehler angezeigt, der ignoriert werden kann.

1. Installieren Sie **iq_client_common**. Nach Abschluss der Installation wird möglicherweise ein Java-Fehler angezeigt, der ignoriert werden kann.

1. Konfigurieren sie den ODBC-Treiber. Die Konfiguration kann in den Standarddateien ausgeführt werden: /etc/odbc.ini für allgemeine Parameter und /etc/odbcinst.ini zur Deklarierung der Treiber:

   * **/etc/odbc.ini** (ersetzen Sie Werte wie `<server_alias>`-Zeichen durch Ihre eigenen):

     ```
     [ODBC Data Sources]
     <server_alias>=libdbodbc.so
     
     [<server_alias>]
     Driver=/opt/sybase/IQ-16_0/lib64/libdbodbc16.so
     Description=<description>
     Username=<username>
     Password=<password>
     ServerName=<server_name>
     CommLinks=tcpip(host=<host>)
     ```

   * **/etc/odbcinst.ini**

     ```
     [ODBC DRIVERS]
     SAP SybaseIQ=Installed
     
     [SAP SybaseIQ]
     Driver=/opt/sybase/IQ-16_0/lib64/libdbodbc16.so
     ```

1. Fügen Sie den Pfad für die neue Bibliothek libodbc16.so in der Variablen LD_LIBRARY_PATH hinzu. Gehen Sie dazu folgendermaßen vor:

   * Wenn Sie eine customer.sh-Datei verwenden, um Ihren Pfad zu deklarieren: Fügen Sie den Pfad /opt/sybase/IQ-16_0/lib64 für die Variable LD_LIBRARY_PATH hinzu.
   * Verwenden Sie ansonsten einen Unix-Befehl.

## Externes Sybase IQ-Konto {#sybase-external}

Mit dem externen Konto Sybase IQ können Sie Ihre Campaign-Instanz mit Ihrer externen Sybase IQ-Datenbank verbinden.

1. Klicken Sie **[!UICONTROL Campaign-]** auf **[!UICONTROL Administration]** &quot;>&quot; **[!UICONTROL Plattform]** &quot;>&quot; **[!UICONTROL Externe Konten]**.

1. Klicken Sie auf **[!UICONTROL Neu]** und wählen Sie **[!UICONTROL Externe Datenbank]** als **[!UICONTROL Typ]** aus.

1. Zum Konfigurieren des externen **[!UICONTROL Sybase IQ]**-Kontos müssen Sie Folgendes angeben:

   * **[!UICONTROL Typ]**: ODBC (Sybase ASE, Sybase IQ)

   * **[!UICONTROL Server]**: Entspricht der ODBC-Verbindung (`<server_alias>`), die in Schritt 5 definiert wird. Es handelt sich dabei nicht unbedingt um den Namen des Servers selbst.

   * **[!UICONTROL Konto]**: Name des Benutzers

   * **[!UICONTROL Passwort]**: Passwort des Benutzerkontos

   * **[!UICONTROL Datenbank]**: Name der Datenbank

>[!NOTE]
>
>Unter Windows müssen Sie den Sybase IQ-Client auf dem Adobe Campaign-Server installieren und eine ODBC-Verbindung einrichten. Stellen Sie sicher, dass Sie eine Systemdatenquelle erstellen, wenn der Adobe Campaign-Server (nlserver) in Windows als Dienst ausgeführt wird.
