---
product: campaign
title: Zugriff auf SAP HANA konfigurieren
description: Erfahren Sie, wie Sie den Zugriff auf SAP HANA in FDA konfigurieren
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 39bfe775-e182-4a0b-ad3c-b7a901297c90
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 71%

---

# Zugriff auf SAP HANA konfigurieren {#configure-access-to-sap-hana}

![](../../assets/v7-only.svg)

Verwenden von Campaign [Federated Data Access](../../installation/using/about-fda.md) (FDA), um in externen Datenbanken gespeicherte Informationen zu verarbeiten. Gehen Sie wie folgt vor, um den Zugriff auf SAP HANA zu konfigurieren.

1. Konfigurieren [SAP HANA-Datenbank](#sap-config)
1. SAP HANA konfigurieren [externes Konto](#sap-external) in Campaign

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

## Externes SAP HANA-Konto{#sap-external}

Mit dem externen SAP HANA-Konto können Sie Ihre Campaign-Instanz mit Ihrer externen SAP HANA-Datenbank verbinden.

1. Von Campaign **[!UICONTROL Explorer]** klicken **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Plattform]** &#39;>&#39; **[!UICONTROL Externe Konten]**.

1. Klicken Sie auf **[!UICONTROL Neu]** und wählen Sie **[!UICONTROL Externe Datenbank]** als **[!UICONTROL Typ]** aus.

1. Zur Konfiguration des externen **[!UICONTROL SAP Hana]**-Kontos müssen Sie Folgendes angeben:

   * **[!UICONTROL Typ]**: SAP Hana

   * **[!UICONTROL Server]**: URL des SAP Hana-Servers

   * **[!UICONTROL Konto]**: Name des Benutzers

   * **[!UICONTROL Passwort]**: Passwort des Benutzerkontos
