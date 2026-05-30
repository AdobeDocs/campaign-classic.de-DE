---
product: campaign
title: Zugriff auf SAP HANA konfigurieren
description: Erfahren Sie, wie Sie den Zugriff auf SAP HANA in FDA konfigurieren
feature: Installation, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 39bfe775-e182-4a0b-ad3c-b7a901297c90
TQID: https://experienceleague.adobe.com/m2ibPllvRz-0vRS80bsktgY2qKdxL-fH9UEmHDgokT8
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2: id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
feature_v2: []
subfeature_v2: []
source-git-commit: bb41e9407ab5853b0194bb325bbf3f17bc3ea232
workflow-type: tm+mt
source-wordcount: 272
ht-degree: 55%

---

# Zugriff auf SAP HANA konfigurieren {#configure-access-to-sap-hana}



Verwenden Sie die [-Option (Federated Data Access](../../installation/using/about-fda.md) (FDA) von Campaign, um in einer externen Datenbank gespeicherte Informationen zu verarbeiten. Gehen Sie wie folgt vor, um den Zugriff auf SAP HANA zu konfigurieren.

1. [SAP HANA-Datenbank konfigurieren](#sap-config)
1. Konfigurieren des SAP HANA [externen Kontos](#sap-external) in Campaign

## SAP HANA-Treiber {#sap-config}

Die Verbindung mit einer externen SAP-HANA-Datenbank über die FDA-Option erfordert gewisse zusätzliche Konfigurationen auf dem Adobe Campaign-Server:

1. Installieren Sie entsprechend dem verwendeten Betriebssystem die nötigen ODBC-Treiber für SAP HANA:

   * **hdb_client_linux.tgz** für Linux Nach dem Entpacken starten Sie den Befehl hdbinst und folgen den Anweisungen, um die Installation der Treiber abzuschließen.
   * **hdb_client_windows.zip** für Windows. Entpacken Sie die Datei und starten Sie die ausführbare Datei: **hdbinst.exe**. Folgen Sie den Anweisungen des Assistenten, um die Installation der Treiber abzuschließen.

1. Konfigurieren Sie den ODBC-Treiber. Die Konfiguration kann in den Standarddateien durchgeführt werden: /etc/odbc.ini für allgemeine Parameter und /etc/odbcinst.ini für deklarierende Treiber.

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

Über das externe Konto „SAP HANA“ können Sie Ihre Campaign-Instanz mit Ihrer externen SAP HANA-Datenbank verbinden.

1. Klicken Sie **[!UICONTROL Campaign-]** auf **[!UICONTROL Administration]** &quot;>&quot; **[!UICONTROL Plattform]** &quot;>&quot; **[!UICONTROL Externe Konten]**.

1. Klicken Sie auf **[!UICONTROL Neu]** und wählen Sie **[!UICONTROL Externe Datenbank]** als **[!UICONTROL Typ]** aus.

1. Zur Konfiguration des externen **[!UICONTROL SAP Hana]**-Kontos müssen Sie Folgendes angeben:

   * **[!UICONTROL Typ]**: SAP Hana

   * **[!UICONTROL Server]**: URL des SAP Hana-Servers

   * **[!UICONTROL Konto]**: Name des Benutzers

   * **[!UICONTROL Passwort]**: Passwort des Benutzerkontos
