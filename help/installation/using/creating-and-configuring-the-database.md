---
product: campaign
title: Erstellen und Konfigurieren der Vorlagen
description: Erstellen und Konfigurieren der Vorlagen
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: f40bab8c-5064-40d9-beed-101a9f22c094
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '1342'
ht-degree: 1%

---

# Erstellen und Konfigurieren der Vorlagen{#creating-and-configuring-the-database}

Beim Erstellen einer Datenbank bietet Adobe Campaign zwei verschiedene Optionen:

1. Erstellen oder Recycling einer Datenbank: Wählen Sie diese Optionen aus, wenn Sie eine neue Datenbank erstellen oder eine bestehende wiederverwenden möchten. Siehe [1. Fall: Erstellen/Recycling einer Datenbank](#case-1--creating-recycling-a-database).
1. Verwenden einer vorhandenen Datenbank: Wählen Sie diese Option, wenn Ihr Administrator bereits eine leere Datenbank erstellt hat und Sie sie verwenden möchten. oder um die Struktur einer vorhandenen Datenbank zu erweitern. Siehe [2. Fall: Verwenden einer vorhandenen Datenbank](#case-2--using-an-existing-database).

Die Konfigurationsschritte werden nachfolgend beschrieben.

>[!CAUTION]
>
>Namen von Datenbanken, Benutzern und Schemata dürfen nicht mit einer Zahl beginnen oder Sonderzeichen enthalten.
>
>Nur die **interne**-Kennung kann diese Vorgänge ausführen. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../installation/using/configuring-campaign-server.md#internal-identifier).

## 1. Fall: Erstellen/Recycling einer Datenbank {#case-1--creating-recycling-a-database}

Die Schritte zum Erstellen einer Datenbank oder zum Recycling einer vorhandenen Datenbank werden nachfolgend beschrieben. Einige Konfigurationen hängen von der verwendeten Datenbank-Engine ab:

Folgende Schritte sind erforderlich:

* [Schritt 1: Auswählen der Datenbank-Engine](#step-1---selecting-the-database-engine),
* [Schritt 2: Herstellen einer Verbindung zum Server](#step-2---connecting-to-the-server),
* [3. Schritt - Verbindung und Merkmale der Datenbank](#step-3---connection-and-characteristics-of-the-database),
* [Schritt 4: Zu installierende](#step-4---packages-to-install) Pakete,
* [Schritt 5: Erstellungsschritte](#step-5---creation-steps),
* [6. Schritt - Erstellung der Datenbank](#step-6---creating-the-database).

### Schritt 1: Auswählen der Datenbank-Engine {#step-1---selecting-the-database-engine}

Wählen Sie aus der Dropdown-Liste die Datenbank-Engine aus.

![](assets/s_ncs_install_db_select_engine.png)

Die unterstützten Datenbanken werden in Campaign unter [Kompatibilitätsmatrix](../../rn/using/compatibility-matrix.md) aufgeführt.

Identifizieren Sie den Server und wählen Sie den auszuführenden Vorgangstyp aus. In diesem Fall **[!UICONTROL Erstellen oder recyceln Sie eine Datenbank]**.

![](assets/s_ncs_install_db_oracle_creation01.png)

Je nach ausgewählter Datenbank-Engine können die Informationen zur Serveridentifizierung variieren.

* Geben Sie für eine **Oracle**-Engine den **TNS-Namen** ein, der für den Anwendungsserver definiert ist.
* Bei der Engine **PostgreSQL** oder **DB2** müssen Sie den DNS-Namen (oder die IP-Adresse) angeben, der auf dem Anwendungsserver definiert ist, um auf den Datenbankserver zuzugreifen.
* Für eine **Microsoft SQL Server**-Engine müssen Sie Folgendes definieren: den DNS-Namen (oder die IP-Adresse), der auf dem Anwendungsserver für den Zugriff auf den Datenbankserver definiert ist: **DNS** oder **DNS`\<instance>`** (Instanzmodus),

   >[!CAUTION]
   >
   > Ab Version 20.3 wird die Windows NT-Authentifizierung eingestellt. **[!UICONTROL Die SQL Server-]** Authentifizierung ist jetzt der einzige Authentifizierungsmodus, der für Microsoft SQL Server verfügbar ist. [Mehr dazu](../../rn/using/deprecated-features.md)

   ![](assets/s_ncs_install_db_mssql_creation01.png)

### Schritt 2: Herstellen einer Verbindung zum Server {#step-2---connecting-to-the-server}

Definieren Sie im Fenster **[!UICONTROL Server access]** den Datenbankserver-Zugriff.

![](assets/s_ncs_install_db_oracle_creation02.png)

Geben Sie dazu den Namen und das Kennwort eines **Administrationssystem-Kontos** ein, das Zugriff auf die Datenbanken hat, d. h.:

* **** -System für eine Oracle-Datenbank,
* **** für eine Microsoft SQL Server-Datenbank verwenden,
* **** Postgression für eine PostgreSQL-Datenbank,
* **db2inst1**  für eine DB2-Datenbank.

### Schritt 3: Verbindung und Merkmale der Datenbank {#step-3---connection-and-characteristics-of-the-database}

Im folgenden Schritt können Sie die Einstellungen für die Anmeldung bei der Datenbank konfigurieren.

![](assets/s_ncs_install_db_oracle_creation03.png)

Sie müssen die folgenden Einstellungen definieren:

* Geben Sie den Namen der zu erstellenden Datenbank an.

   >[!NOTE]
   >
   >Bei einer DB2-Datenbank darf der Name der Datenbank 8 Zeichen nicht überschreiten.

* Geben Sie das Kennwort des mit dieser Datenbank verknüpften Kontos ein.
* Geben Sie an, ob die Datenbank in Unicode vorliegen muss oder nicht.

   Mit der Option **[!UICONTROL Unicode-Datenbank]** können Sie alle Zeichentypen unabhängig von der Sprache in Unicode speichern.

   >[!NOTE]
   >
   >Bei einer Oracle-Datenbank können Sie mit der Option **[!UICONTROL Unicode-Speicher]** die Typen **NCLOB** und **NVARCHAR** verwenden.
   > 
   >Wenn Sie diese Option nicht auswählen, muss der Zeichensatz (Zeichensatz) der Oracle-Datenbank die Datenspeicherung in allen Sprachen aktivieren (empfohlen wird AL32UTF8).

* Wählen Sie eine Zeitzone für die Datenbank aus und geben Sie an, ob sie in UTC vorliegen soll (sofern verfügbar).

   Weitere Informationen hierzu finden Sie unter [Zeitzonen-Management](../../installation/using/time-zone-management.md).

### Schritt 4: Zu installierende Pakete {#step-4---packages-to-install}

Wählen Sie die Pakete aus, die Sie installieren möchten.

Überprüfen Sie in Ihrem Lizenzvertrag, welche Lösungen und Optionen Sie installieren dürfen, z. B. &quot;Interaction&quot;oder &quot;Social Marketing&quot;.

![](assets/s_ncs_install_modules.png)

### Schritt 5: Erstellungsschritte {#step-5---creation-steps}

Im Fenster **[!UICONTROL Erstellungsschritte]** können Sie das SQL-Skript anzeigen und bearbeiten, das zum Erstellen der Tabellen verwendet wird.

![](assets/s_ncs_install_db_oracle_creation04.png)

* Für eine Oracle-, Microsoft SQL Server- oder PostgreSQL-Datenbank kann der Administrator auch die **Speicherparameter** definieren, die beim Erstellen von Datenbankobjekten verwendet werden sollen.

   Diese Parameter erhalten die genauen Tablespace-Namen (Warnung: Groß-/Kleinschreibung beachten). Sie werden jeweils im Knoten **[!UICONTROL Administration > Plattform > Optionen]** der folgenden Optionen gespeichert (siehe [diesen Abschnitt](../../installation/using/configuring-campaign-options.md#database)):

   * **WdbcOptions_TableSpaceUser**: Benutzertabellen basierend auf einem Schema
   * **WdbcOptions_TableSpaceIndex**: Index der Benutzertabellen basierend auf einem Schema
   * **WdbcOptions_TableSpaceWork**: Arbeitstabellen ohne Schema
   * **WdbcOptions_TableSpaceWorkIndex**: Index der Arbeitstabellen ohne Schema

* Für eine Oracle-Datenbank muss der Adobe Campaign-Benutzer Zugriff auf die Oracle-Bibliotheken haben, normalerweise als Mitglied der Gruppe **oinstall** .
* Mit der Option **[!UICONTROL Administratorkennwort festlegen]** können Sie das mit dem Adobe Campaign-Benutzer verknüpfte Kennwort mit Administratorrechten eingeben.

   Es wird empfohlen, aus Sicherheitsgründen ein Kennwort für den Adobe Campaign-Kontoadministrator zu definieren.

### 6. Schritt - Erstellung der Datenbank {#step-6---creating-the-database}

Im letzten Schritt des Assistenten können Sie die Datenbank erstellen. Klicken Sie zur Bestätigung auf **[!UICONTROL Start]** .

![](assets/s_ncs_install_db_oracle_creation06.png)

Nachdem die Datenbank erstellt wurde, können Sie die Verbindung wiederherstellen, um die Instanzkonfiguration abzuschließen.

Sie müssen jetzt den Softwareverteilungs-Assistenten starten, um die Konfiguration der Instanz abzuschließen. Siehe [Softwareverteilungs-Assistent](../../installation/using/deploying-an-instance.md#deployment-wizard).

Die Verbindungseinstellungen für die mit der Instanz verknüpfte Datenbank werden in der Datei **`/conf/config-<instance>.xml`** gespeichert, die sich im Installationsverzeichnis von Adobe Campaign befindet.

Beispiel einer Microsoft SQL Server-Konfiguration für die Datenbank base61, die mit dem &#39;campaign&#39;-Konto und seinem verschlüsselten Kennwort verknüpft ist:

```
<dbcnx encrypted="1" login="campaign:myBase" password="myPassword" provider="DB" server="dbServer"/>
```

## 2. Fall: Verwenden einer vorhandenen Datenbank {#case-2--using-an-existing-database}

Die Datenbank sowie der Benutzer müssen vom Datenbankadministrator erstellt und die Zugriffsberechtigungen korrekt konfiguriert worden sein.

Für eine Oracle-Datenbank sind beispielsweise folgende Mindestberechtigungen erforderlich: CONNECT, RESSOURCE UND UNBEGRENZTER TABLESPACE.

Gehen Sie zur Verwendung einer vorhandenen Datenbank wie folgt vor:

* [1. Schritt - Datenbank-Engine](#step-1---choosing-the-database-engine) auswählen,
* [Schritt 2: Einstellungen](#step-2---database-connection-settings) für die Datenbankverbindung
* [Schritt 3: Zu installierende](#step-3---packages-to-install) Pakete,
* [Schritt 4: Erstellungsschritte](#step-4---creation-steps),
* [5. Schritt - Erstellung der Datenbank](#step-5---creating-the-database).

### Schritt 1: Auswählen der Datenbank-Engine {#step-1---choosing-the-database-engine}

Wählen Sie die Datenbank-Engine aus der Dropdown-Liste aus.

![](assets/s_ncs_install_db_select_engine.png)

Identifizieren Sie den Server und wählen Sie den Vorgangstyp aus, den Sie ausführen möchten. In diesem Fall **[!UICONTROL Verwenden Sie eine vorhandene Datenbank]**.

![](assets/s_ncs_install_db_oracle_exists_01.png)

Je nach ausgewählter Datenbank-Engine können die Informationen zur Serveridentifizierung variieren.

* Geben Sie für eine **Oracle**-Engine den **TNS-Namen** ein, der für den Anwendungsserver definiert ist.
* Bei der Engine **PostgreSQL** oder **DB2** müssen Sie den DNS-Namen (oder die IP-Adresse) angeben, der auf dem Anwendungsserver definiert ist, um auf den Datenbankserver zuzugreifen.
* Für eine **Microsoft SQL Server**-Engine müssen Sie Folgendes definieren:

   1. den DNS-Namen (oder die IP-Adresse), der auf dem Anwendungsserver für den Zugriff auf den Datenbankserver definiert ist,
   1. die Sicherheitsmethode für den Zugriff auf Microsoft SQL Server: **[!UICONTROL SQL Server-Authentifizierung]** oder **[!UICONTROL Windows NT-Authentifizierung]**.

      ![](assets/s_ncs_install_db_mssql_exists_01.png)

### Schritt 2: Datenbankverbindungseinstellungen {#step-2---database-connection-settings}

Definieren Sie im Fenster **[!UICONTROL Database]** die Einstellungen für die Datenbankverbindung.

![](assets/s_ncs_install_db_oracle_exists_02.png)

Sie müssen die folgenden Einstellungen definieren:

* Geben Sie den Namen der zu verwendenden Datenbank an,
* Geben Sie den Namen und das Kennwort des dieser Datenbank zugeordneten Kontos ein;

   >[!NOTE]
   >
   >Stellen Sie sicher, dass sowohl der Schemaname als auch der Benutzername übereinstimmen. Die empfohlene Methode zum Erstellen einer Datenbank wird über den Kampagnenkonsole-Client empfohlen.
   >Bei einer Oracle-Datenbank ist die Angabe des Kontonamens nicht erforderlich.

* Geben Sie an, ob die Datenbank Unicode sein soll oder nicht.

### Schritt 3: Zu installierende Pakete {#step-3---packages-to-install}

Wählen Sie die Pakete aus, die Sie installieren möchten.

Überprüfen Sie in Ihrem Lizenzvertrag, welche Lösungen und Optionen Sie installieren dürfen, z. B. &quot;Interaction&quot;oder &quot;Leads&quot;.

![](assets/s_ncs_install_modules.png)

### Schritt 4: Erstellungsschritte {#step-4---creation-steps}

Im Fenster **[!UICONTROL Erstellungsschritte]** können Sie das SQL-Skript anzeigen und bearbeiten, das zum Erstellen der Tabellen verwendet wird.

![](assets/s_ncs_install_db_oracle_creation04.png)

* Für Oracle-, Microsoft SQL Server- oder PostgreSQL-Datenbanken kann der Administrator die **Speicherparameter** definieren, die beim Erstellen von Datenbankobjekten verwendet werden sollen.
* Für eine Oracle-Datenbank muss der Adobe Campaign-Benutzer Zugriff auf die Oracle-Bibliotheken haben, normalerweise als Mitglied der Gruppe **oinstall** .
* Mit der Option **[!UICONTROL Administratorkennwort festlegen]** können Sie das mit dem Adobe Campaign-Benutzer verknüpfte Kennwort mit Administratorrechten eingeben.

   Es wird empfohlen, aus Sicherheitsgründen ein Kennwort für den Adobe Campaign-Kontoadministrator zu definieren.

### 5. Schritt - Erstellung der Datenbank {#step-5---creating-the-database}

Im letzten Schritt des Assistenten können Sie die Datenbank erstellen. Klicken Sie zur Bestätigung auf **[!UICONTROL Start]** .

![](assets/s_ncs_install_db_oracle_creation06.png)

Sobald die Datenbankerstellung abgeschlossen ist, können Sie die Verbindung wiederherstellen, um die Instanzkonfiguration abzuschließen.

Sie müssen jetzt den Softwareverteilungs-Assistenten starten, um die Konfiguration der Instanz abzuschließen. Siehe [Softwareverteilungs-Assistent](../../installation/using/deploying-an-instance.md#deployment-wizard).

Die Verbindungseinstellungen für die mit der Instanz verknüpfte Datenbank werden in der Datei **`/conf/config-<instance>.xml`** gespeichert, die sich im Installationsverzeichnis von Adobe Campaign befindet.

Beispiel einer Microsoft SQL Server-Konfiguration für die Datenbank base61, die mit dem &#39;campaign&#39;-Konto und seinem verschlüsselten Kennwort verknüpft ist:

```
<dbcnx encrypted="1" login="campaign:myBase" password="myPassword" provider="DB" server="dbServer"/>
```
