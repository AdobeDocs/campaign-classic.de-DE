---
product: campaign
title: Zugriff auf Netezza konfigurieren
description: Erfahren Sie, wie Sie den Zugriff auf Netezza in FDA konfigurieren
feature: Installation, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: b148d34b-4060-4c54-9cb2-9e712a7c17d7
TQID: https://experienceleague.adobe.com/HiTQ6eoYcjp8pLqNmqLhiDTNhplE4ipnYlWuRFOZvog
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
subfeature_v2: id: cfc95e9b-b035-4403-a6a9-b27a8a053a37
topic_v2: id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 391
ht-degree: 36%

---

# Zugriff auf Netezza konfigurieren {#configure-access-to-netezza}



Verwenden Sie die [-Option (Federated Data Access](../../installation/using/about-fda.md) (FDA) von Campaign, um in einer externen Datenbank gespeicherte Informationen zu verarbeiten. Gehen Sie wie folgt vor, um den Zugriff auf Netezza zu konfigurieren.

1. [Netezza-Treiber installieren und konfigurieren](#netezza-config)
1. Konfigurieren des Netezza [externen Kontos](#netezza-external) in Campaign

## Netezza-Konfiguration {#netezza-config}

Die Verbindung zu einer externen Netezza-Datenbank über die FDA-Option erfordert die zusätzlichen unten aufgeführten Konfigurationen auf dem Adobe Campaign Server:

1. Installieren Sie die ODBC-Treiber für Netezza entsprechend dem verwendeten Betriebssystem:

   * **nz-linuxclient-v7.2.0.0.tar.gz** für Linux Wählen Sie den Ordner aus, der Ihrem Betriebssystem (Linux oder Linux64) entspricht, und starten Sie den Entpackbefehl. Sie können die Installation im Repository durchführen lassen, das standardmäßig vorgeschlagen wird: &quot;/usr/local/nz“.
   * **nz-winclient-v7.2.0.0.zip** für Windows. Entpacken Sie die Datei und starten Sie das ausführbare Skript, das Ihrem Betriebssystem entspricht: nzodbcsetup.exe oder nzodbcsetup64.exe. Folgen Sie den Anweisungen des Assistenten, um die Installation der Treiber abzuschließen.

1. Konfigurieren Sie den ODBC-Treiber. Die Konfiguration kann in den Standarddateien ausgeführt werden: **/etc/odbc.ini** für allgemeine Parameter und **/etc/odbcinst.ini** für deklarierende Treiber.

   * **/etc/odbc.ini**

     ```
     [ODBC]
     InstallDir=/etc/
     ```

     &quot;InstallDir&quot; entspricht dem Pfad der odbcinst.ini-Datei.

   * **/etc/odbcinst.ini**

     ```
     [ODBC Drivers]
     NetezzaSQL = Installed
     
     [NetezzaSQL]
     Driver           = /usr/local/nz/lib/libnzsqlodbc3.so
     Setup            = /usr/local/nz/lib/libnzsqlodbc3.so
     APILevel         = 1
     ConnectFunctions = YYN
     Description      = Netezza ODBC driver
     DriverODBCVer    = 03.51
     DebugLogging     = false
     LogPath          = /tmp
     UnicodeTranslationOption = utf8
     CharacterTranslationOption = all
     PreFetch         = 256
     Socket           = 16384
     ```

1. Spezifizieren Sie die Umgebungsvariablen des Adobe Campaign-Servers:

   * **LD_LIBRARY_PATH**: /usr/local/nz/lib und /usr/local/nz/lib64. &quot;/usr/local/nz“ entspricht dem standardmäßig bei der Installation der Treiber angebotenen Installations-Repository. Hier müssen Sie das Repository angeben, das Sie für die Installation ausgewählt haben.
   * **ODBCINI**: Pfad der odbc.ini-Datei (z. B. /etc/odbc.ini).
   * **NZ_ODBC_INI_PATH**: Speicherort der Datei odbc.ini. Netezza benötigt diese zweite Variable auch für die Verwendung der Datei odbc.ini.

## Externes Netezza-Konto {#netezza-external}

Über das externe Konto „Netezza“ können Sie Ihre Campaign-Instanz mit Ihrer externen Netezza-Datenbank verbinden.

1. Klicken Sie **[!UICONTROL Campaign-]** auf **[!UICONTROL Administration]** &quot;>&quot; **[!UICONTROL Plattform]** &quot;>&quot; **[!UICONTROL Externe Konten]**.

1. Klicken Sie auf **[!UICONTROL Neu]** und wählen Sie **[!UICONTROL Externe Datenbank]** als **[!UICONTROL Typ]** aus.

1. Zum Konfigurieren des externen **[!UICONTROL Netezza]**-Kontos müssen Sie Folgendes angeben:

   * **[!UICONTROL Typ]**: Netezza

   * **[!UICONTROL Server]**: URL des Netezza-Servers

   * **[!UICONTROL Konto]**: Name des Benutzers

   * **[!UICONTROL Passwort]**: Passwort des Benutzerkontos

   * **[!UICONTROL Datenbank]**: Name der Datenbank

>[!NOTE]
>
>Vorgänge, die Schemata betreffen und automatisch erstellte Primärschlüssel enthalten, werden hierbei nicht berücksichtigt.
>
>Die Tabelle verwendet die **Organize On**-Klausel für den ersten im Schema definierten Index. Da dieser Abschnitt bei Netezza auf 1 bis 4 Spalten beschränkt ist, darf dieser Index nicht mehr als 4 Spalten enthalten.
