---
title: Zugriff auf SAP HANA konfigurieren
description: Erfahren Sie, wie Sie den Zugriff auf SAP HANA in FDA konfigurieren
page-status-flag: never-activated
uuid: b84359b9-c584-431d-80d5-71146d9b6854
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dd3d14cc-5153-428d-a98a-32b46f0fe811
translation-type: tm+mt
source-git-commit: 9bbde65aea6735e30e95e75c2b6ae5445d4a2bdd
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 71%

---


# Zugriff auf SAP HANA konfigurieren {#configure-access-to-sap-hana}

Verwenden Sie die Option &quot;Kampagne [Federated Data Access](../../installation/using/about-fda.md) (FDA)&quot;, um in externen Datenbanken gespeicherte Informationen zu verarbeiten. Gehen Sie wie folgt vor, um den Zugriff auf SAP HANA zu konfigurieren.

1. [SAP HANA-Datenbank konfigurieren](#sap-config)
1. SAP HANA- [Externe Konto](#sap-external) in Kampagne konfigurieren

## SAP HANA-Treiber {#sap-config}

Die Verbindung mit einer externen SAP-HANA-Datenbank über die FDA-Option erfordert gewisse zusätzliche Konfigurationen auf dem Adobe-Campaign-Server:

1. Installieren Sie entsprechend dem verwendeten Betriebssystem die nötigen ODBC-Treiber für SAP HANA:

   * **hdb_client_linux.tgz für Linux: Dekomprimieren Sie die Datei, führen Sie den hdbinst-Befehl aus und folgen Sie der Anleitung zur Installation der Treiber.**
   * **hdb_client_windows.zip** für Windows: Dekomprimieren Sie die Datei und führen Sie die ausführbare Datei **hdbinst.exe** aus. Folgen Sie den Anweisungen des Assistenten zur Installation der Treiber.

1. Konfigurieren sie den ODBC-Treiber. Die Konfiguration kann in den Standarddateien ausgeführt werden: /etc/odbc.ini für allgemeine Parameter und /etc/odbcinst.ini zur Deklarierung der Treiber.

   * **/etc/odbc.ini**

      ```
      [ODBC]
      InstallDir=/etc/
      
      [HDB]
      Driver=HDBODBC
      servernode=localhost:39013 (this value depend of your server)
      User:SYSTEM
      ```

      &quot;InstallDir&quot; entspricht dem Pfad der Datei **odbcinst.ini**.

   * **/etc/odbcinst.ini**

      ```
      [HDBODBC]
      Description = "SmartCloudPT HANA"
      Driver = /usr/sap/hdbclient/libodbcHDB.so
      ```

1. Spezifizieren Sie die Umgebungsvariablen des Adobe Campaign-Servers:

   * **LD_LIBRARY_PATH**: Diese Variable sollte die Verknüpfung zu Ihrem SAP Hana Client enthalten (standardmäßig /usr/sap/hdbclient/libodbcHDB.so).
   * **ODBCINI**: Pfad der odbc.ini-Datei (z. B. /etc/odbc.ini).

## SAP HANA Externe Konto{#sap-external}

Mit dem SAP HANA-Externe Konto können Sie die Instanz Ihrer Kampagne mit Ihrer externen SAP HANA-Datenbank verbinden.

1. From Campaign **[!UICONTROL Explorer]**, click **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Klicken Sie auf **[!UICONTROL Neu]** und wählen Sie **[!UICONTROL Externe Datenbank]** als **[!UICONTROL Typ]** aus.

1. Zur Konfiguration des externen **[!UICONTROL SAP Hana]**-Kontos müssen Sie Folgendes angeben:

   * **[!UICONTROL Typ]**: SAP Hana

   * **[!UICONTROL Server]**: URL des SAP Hana-Servers

   * **[!UICONTROL Konto]**: Name des Benutzers

   * **[!UICONTROL Passwort]**: Passwort des Benutzerkontos
