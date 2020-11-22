---
solution: Campaign Classic
product: campaign
title: Zugriff auf Netezza konfigurieren
description: Erfahren Sie, wie Sie den Zugriff auf Netezza in FDA konfigurieren
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 80%

---


# Zugriff auf Netezza konfigurieren {#configure-access-to-netezza}

Verwenden Sie die Option &quot;Kampagne [Federated Data Access](../../installation/using/about-fda.md) (FDA)&quot;, um in externen Datenbanken gespeicherte Informationen zu verarbeiten. Gehen Sie wie folgt vor, um den Zugriff auf Netezza zu konfigurieren.

1. Installieren und Konfigurieren von [Netezza-Treibern](#netezza-config)
1. Netezza- [Externe Konto](#netezza-external) in Kampagne konfigurieren

## Netezza-Konfiguration {#netezza-config}

Die Verbindung zu einer externen Netezza-Datenbank über die FDA-Option erfordert die zusätzlichen unten aufgeführten Konfigurationen auf dem Adobe Campaign Server:

1. Installieren Sie die ODBC-Treiber für Netezza entsprechend dem verwendeten Betriebssystem:

   * **nz-linuxclient-v7.2.0.0.tar.gz für Linux: Wählen Sie den Ordner aus, der Ihrem Betriebssystem entspricht (linux oder linux64) und starten Sie den Entpacken-Befehl. Sie können die Installation im standardmäßig empfohlenen Verzeichnis ausführen: &quot;/usr/local/nz&quot;.**
   * **nz-winclient-v7.2.0.0.zip für Windows: Dekomprimieren Sie die Datei und führen Sie das jeweilige Script für Ihr Betriebssystem aus: nzodbcsetup.exe oder nzodbcsetup64.exe. Folgen Sie den Anweisungen des Assistenten, um die Treiber zu installieren.**

1. Konfigurieren sie den ODBC-Treiber. Die Konfiguration kann in den Standarddateien ausgeführt werden: **/etc/odbc.ini** für allgemeine Parameter und **/etc/odbcinst.ini** zur Deklarierung der Treiber.

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

   * **LD_LIBRARY_PATH**: /usr/local/nz/lib und /usr/local/nz/lib64. &quot;/usr/local/nz&quot; entspricht dem bei der Treiberinstallation standardmäßig angegebenen Installationsverzeichnis. Geben Sie hier das für die Installation ausgewählte Verzeichnis an.
   * **ODBCINI**: Pfad der odbc.ini-Datei (z. B. /etc/odbc.ini).
   * **NZ_ODBC_INI_PATH**: Pfad der Datei „odbc.ini“. In Netezza ist auch diese zweite Variable zur Verwendung der odbc.ini-Datei erforderlich.

## Netezza Externe Konto {#netezza-external}

Mit dem Netezza-Externe Konto können Sie die Instanz Ihrer Kampagne mit Ihrer externen Netezza-Datenbank verbinden.

1. From Campaign **[!UICONTROL Explorer]**, click **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

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
>Für den ersten im Schema definierten Index wird von der Tabelle die Bedingung **Organize on** verwendet. Da diese Bedingung bei Netezza auf 1 bis 4 Spalten beschränkt ist, kann dieser Index nur maximal 4 Spalten beinhalten.
